

##### Grade
---

GradeId              UUID PRIMARY KEY
GradeCode            VARCHAR(20) UNIQUE
GradeName            VARCHAR(100)


##### UserProfile
--------------
EmployeeKey          UUID PRIMARY KEY

Email                VARCHAR UNIQUE

FirstName            VARCHAR

LastName             VARCHAR

GradeId              UUID FK -> Grade

CreatedAt

UpdatedAt


##### UserAccount
-----------
EmployeeKey          UUID FK -> UserProfile

PasswordHash

CreatedAt


##### Role
---------
RoleId               UUID PRIMARY KEY

RoleKey              VARCHAR UNIQUE

Description


##### UserRoleMap
----------------

EmployeeKey          FK

RoleId               FK

PRIMARY KEY(EmployeeKey, RoleId)


##### Permission
--------------

PermissionId         UUID PRIMARY KEY

PermissionKey        VARCHAR UNIQUE

Description

##### RolePermissionMap
-------------------

RoleId              FK

PermissionId        FK

PRIMARY KEY(RoleId, PermissionId)


##### Skill
------------

SkillId             UUID PRIMARY KEY

SkillName           VARCHAR UNIQUE

IsActive            BOOLEAN

CreatedAt

UpdatedAt


##### MentorProfile
-------------------

MentorProfileId     UUID PRIMARY KEY

EmployeeKey         FK

Designation

About

ExperienceYears

Capacity

IsAcceptingRequests

StatusMessage

IsPublished

LastUpdated


##### MentorSkillMap
-------------------

MentorProfileId

SkillId

PRIMARY KEY(MentorProfileId, SkillId)

##### MenteeProfile
-------------------

MenteeProfileId

EmployeeKey

About

CurrentFocusArea

LastUpdated


##### MenteeSoughtSkillMap
-------------------

MenteeProfileId

SkillId

PRIMARY KEY(MenteeProfileId, SkillId)

##### SkillSuggestion
------------------

SuggestionId

EmployeeKey

SuggestedSkillName

Reason

Status

CreatedAt

ReviewedBy

ReviewedAt


##### Configuration
------------------

ConfigKey

ConfigValue

Description

###### EXAMPLE

DEFAULT_CAPACITY = 5

MIN_GRADE_TO_BE_MENTOR = gradecode

PENDING_REQUEST_LIMIT = 10

PROFILE_FRESHNESS_DAYS = 180

DESIRED_CADENCE = MONTHLY



### Permissions

VIEW_SKILLS
CREATE_SKILL
UPDATE_SKILL
DELETE_UNUSED_SKILL
ACTIVATE_SKILL
DEACTIVATE_SKILL

VIEW_SKILL_SUGGESTIONS
APPROVE_SKILL_SUGGESTION
REJECT_SKILL_SUGGESTION

VIEW_CONFIGURATION
UPDATE_CONFIGURATION

VIEW_USERS
VIEW_ALL_PROFILES

VIEW_AUDIT_LOG
EXPORT_AUDIT_LOG

VIEW_PROGRAM_ANALYTICS
EXPORT_REPORTS