
- Mentorship Platform - Sprint 1 schema
- PostgreSQL 13+ (gen_random_uuid() is built into core).



CREATE EXTENSION IF NOT EXISTS pg_trgm;   -- backs ILIKE mentor search (FTR-08)

-- ---------------------------------------------------------------------
Reference / RBAC
-- ---------------------------------------------------------------------

CREATE TABLE grade (
    grade_id          UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    grade_code        VARCHAR(20)  NOT NULL UNIQUE,
    grade_name        VARCHAR(100) NOT NULL,
    -- Eligible-set model for "who may be a mentor" (maintained like the skill list).
    -- Simpler than a min-grade rank and avoids ordering grades. Used by Sprint 2 REQ-011.
    is_mentor_eligible BOOLEAN     NOT NULL DEFAULT FALSE,
    created_at        TIMESTAMPTZ  NOT NULL DEFAULT now(),
    updated_at        TIMESTAMPTZ  NOT NULL DEFAULT now()
);

CREATE TABLE app_role (
    role_id     UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    role_key    VARCHAR(50)  NOT NULL UNIQUE,   -- MENTEE, MENTOR, PROGRAMME_OWNER
    description VARCHAR(255)
);

CREATE TABLE permission (
    permission_id  UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    permission_key VARCHAR(60) NOT NULL UNIQUE,
    description    VARCHAR(255)
);

CREATE TABLE role_permission (
    role_id       UUID NOT NULL REFERENCES app_role(role_id) ON DELETE CASCADE,
    permission_id UUID NOT NULL REFERENCES permission(permission_id) ON DELETE CASCADE,
    PRIMARY KEY (role_id, permission_id)
);

-- ---------------------------------------------------------------------
- Identity
-  employee_key is the stable, IdP-agnostic principal id. In Phase 2 the
- sso.pal.tech token's subject/email maps to this row (JIT provisioning); nothing downstream changes.
-- ---------------------------------------------------------------------

CREATE TABLE user_profile (
    employee_key         UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email                VARCHAR(255) NOT NULL UNIQUE,   -- login identifier
    first_name           VARCHAR(100) NOT NULL,
    last_name            VARCHAR(100) NOT NULL,
    department           VARCHAR(120),                   -- searchable (FTR-08)
    grade_id             UUID REFERENCES grade(grade_id),
    -- Self-reference for Sprint 2 reporting-chain checks (REQ-011). Nullable in Sprint 1.
    manager_employee_key UUID REFERENCES user_profile(employee_key),
    created_at           TIMESTAMPTZ NOT NULL DEFAULT now(),
    updated_at           TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE user_account (
    employee_key        UUID PRIMARY KEY REFERENCES user_profile(employee_key) ON DELETE CASCADE,
    password_hash       VARCHAR(255) NOT NULL,           -- BCrypt; unused once SSO takes over
    last_active_role_id UUID REFERENCES app_role(role_id), -- default role on next login (US-004)
    is_active           BOOLEAN NOT NULL DEFAULT TRUE,   -- Sprint 4 deactivation seam
    created_at          TIMESTAMPTZ NOT NULL DEFAULT now(),
    updated_at          TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE user_role (
    employee_key    UUID NOT NULL REFERENCES user_profile(employee_key) ON DELETE CASCADE,
    role_id         UUID NOT NULL REFERENCES app_role(role_id),
    selection_order INT  NOT NULL DEFAULT 0,   -- order roles were chosen; default = lowest (US-003)
    assigned_at     TIMESTAMPTZ NOT NULL DEFAULT now(),
    PRIMARY KEY (employee_key, role_id)
);

-- ---------------------------------------------------------------------
- Skills master + suggestions
-- ---------------------------------------------------------------------

CREATE TABLE skill (
    skill_id   UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    skill_name VARCHAR(100) NOT NULL UNIQUE,
    is_active  BOOLEAN NOT NULL DEFAULT TRUE,   -- retire = set FALSE (keeps it on existing profiles)
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE skill_suggestion (
    suggestion_id        UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    employee_key         UUID NOT NULL REFERENCES user_profile(employee_key),
    suggested_skill_name VARCHAR(100) NOT NULL,
    reason               VARCHAR(255),
    status               VARCHAR(20) NOT NULL DEFAULT 'PENDING', -- PENDING/APPROVED/REJECTED
    request_count        INT NOT NULL DEFAULT 1,                 -- merged duplicate requests
    created_at           TIMESTAMPTZ NOT NULL DEFAULT now(),
    reviewed_by          UUID REFERENCES user_profile(employee_key),
    reviewed_at          TIMESTAMPTZ
);

-- ---------------------------------------------------------------------
- Profiles
-- ---------------------------------------------------------------------

CREATE TABLE mentor_profile (
    mentor_profile_id     UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    employee_key          UUID NOT NULL UNIQUE REFERENCES user_profile(employee_key) ON DELETE CASCADE,
    designation           VARCHAR(100),
    about                 VARCHAR(500),           -- bio
    experience_years      INT,
    capacity              INT NOT NULL DEFAULT 3, -- mentee cap (1-20); default from app_config
    is_accepting_requests BOOLEAN NOT NULL DEFAULT TRUE,   -- availability toggle
    status_message        VARCHAR(150),
    is_published          BOOLEAN NOT NULL DEFAULT FALSE,  -- draft until published
    last_updated          TIMESTAMPTZ,
    version               BIGINT NOT NULL DEFAULT 0,       -- @Version: capacity race guard (US-012)
    created_at            TIMESTAMPTZ NOT NULL DEFAULT now(),
    updated_at            TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE mentor_skill (
    mentor_profile_id UUID NOT NULL REFERENCES mentor_profile(mentor_profile_id) ON DELETE CASCADE,
    skill_id          UUID NOT NULL REFERENCES skill(skill_id),
    PRIMARY KEY (mentor_profile_id, skill_id)
);

CREATE TABLE mentee_profile (
    mentee_profile_id  UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    employee_key       UUID NOT NULL UNIQUE REFERENCES user_profile(employee_key) ON DELETE CASCADE,
    about              VARCHAR(500),
    current_focus_area VARCHAR(150),
    last_updated       TIMESTAMPTZ,
    created_at         TIMESTAMPTZ NOT NULL DEFAULT now(),
    updated_at         TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE mentee_sought_skill (
    mentee_profile_id UUID NOT NULL REFERENCES mentee_profile(mentee_profile_id) ON DELETE CASCADE,
    skill_id          UUID NOT NULL REFERENCES skill(skill_id),
    PRIMARY KEY (mentee_profile_id, skill_id)
);

-- ---------------------------------------------------------------------
- Programme configuration (typed key-value; validated in the service layer)
-- ---------------------------------------------------------------------

CREATE TABLE app_config (
    config_key   VARCHAR(60) PRIMARY KEY,
    config_value VARCHAR(255) NOT NULL,
    data_type    VARCHAR(20)  NOT NULL DEFAULT 'STRING', -- INT / BOOLEAN / STRING
    description  VARCHAR(255),
    updated_at   TIMESTAMPTZ  NOT NULL DEFAULT now()
);

-- ---------------------------------------------------------------------
- Indexes
-- ---------------------------------------------------------------------

CREATE INDEX idx_user_profile_department  ON user_profile (department);
CREATE INDEX idx_user_profile_grade       ON user_profile (grade_id);
CREATE INDEX idx_mentor_profile_published ON mentor_profile (is_published);
CREATE INDEX idx_mentor_profile_available ON mentor_profile (is_accepting_requests);
CREATE INDEX idx_skill_suggestion_status  ON skill_suggestion (status);

-- Trigram indexes to keep ILIKE mentor search fast (name + designation).
CREATE INDEX idx_user_profile_name_trgm ON user_profile
    USING gin ((first_name || ' ' || last_name) gin_trgm_ops);
CREATE INDEX idx_mentor_designation_trgm ON mentor_profile
    USING gin (designation gin_trgm_ops);

-- ---------------------------------------------------------------------
- Seed data
-- ---------------------------------------------------------------------

INSERT INTO app_role (role_key, description) VALUES
    ('MENTEE',          'Seeks guidance and requests mentors'),
    ('MENTOR',          'Offers guidance; manages availability and capacity'),
    ('PROGRAMME_OWNER', 'Configures and governs the programme');

INSERT INTO permission (permission_key, description) VALUES
    ('CREATE_SKILL', NULL), ('UPDATE_SKILL', NULL), ('DELETE_UNUSED_SKILL', NULL),
    ('ACTIVATE_SKILL', NULL), ('DEACTIVATE_SKILL', NULL),
    ('VIEW_SKILL_SUGGESTIONS', NULL), ('APPROVE_SKILL_SUGGESTION', NULL), ('REJECT_SKILL_SUGGESTION', NULL),
    ('VIEW_CONFIGURATION', NULL), ('UPDATE_CONFIGURATION', NULL);

-- All governance permissions belong to PROGRAMME_OWNER in Sprint 1.
INSERT INTO role_permission (role_id, permission_id)
SELECT r.role_id, p.permission_id
FROM app_role r CROSS JOIN permission p
WHERE r.role_key = 'PROGRAMME_OWNER';

INSERT INTO app_config (config_key, config_value, data_type, description) VALUES
    ('DEFAULT_CAPACITY',       '3',  'INT', 'Default mentee capacity for a new mentor (1-20)'),
    ('PENDING_REQUEST_LIMIT',  '5',  'INT', 'Max pending match requests per mentee (Sprint 2)'),
    ('PROFILE_FRESHNESS_DAYS', '90', 'INT', 'Days after which a profile is considered stale'),
    ('DESIRED_CADENCE_WEEKS',  '4',  'INT', 'Target weeks between sessions (Sprint 4 cadence flag)');
-- Note: MIN_GRADE_TO_BE_MENTOR removed - eligibility now lives on grade.is_mentor_eligible.