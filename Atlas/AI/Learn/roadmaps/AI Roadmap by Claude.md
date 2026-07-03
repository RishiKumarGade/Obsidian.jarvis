
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>World-Class AI Researcher Roadmap</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap');

  :root {
    --bg: #09090f;
    --surface: #111118;
    --surface2: #16161f;
    --border: #1e1e2e;
    --border-bright: #2a2a40;
    --text: #e2e2f0;
    --text-muted: #8888aa;
    --text-dim: #4a4a6a;
    --accent: #7c6af7;
    --accent-glow: rgba(124, 106, 247, 0.15);
    --accent2: #06c6a4;
    --accent2-glow: rgba(6, 198, 164, 0.12);
    --amber: #f59e0b;
    --amber-glow: rgba(245, 158, 11, 0.12);
    --rose: #f43f5e;
    --rose-glow: rgba(244, 63, 94, 0.12);
    --sky: #38bdf8;
    --sky-glow: rgba(56, 189, 248, 0.12);
    --phase0: #7c6af7;
    --phase1: #06c6a4;
    --phase2: #38bdf8;
    --phase3: #f59e0b;
    --phase4: #f43f5e;
    --phase5: #a78bfa;
    --phase6: #34d399;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Inter', sans-serif;
    background: var(--bg);
    color: var(--text);
    line-height: 1.7;
    font-size: 15px;
  }

  /* ── HERO ── */
  .hero {
    position: relative;
    overflow: hidden;
    padding: 80px 40px 60px;
    text-align: center;
    border-bottom: 1px solid var(--border);
  }
  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 900px 500px at 50% -100px, rgba(124,106,247,0.18) 0%, transparent 70%),
      radial-gradient(ellipse 600px 400px at 80% 100%, rgba(6,198,164,0.08) 0%, transparent 60%);
    pointer-events: none;
  }
  .hero-eyebrow {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.2em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 20px;
    opacity: 0.85;
  }
  .hero h1 {
    font-family: 'Space Grotesk', sans-serif;
    font-size: clamp(32px, 5vw, 56px);
    font-weight: 700;
    letter-spacing: -0.03em;
    line-height: 1.1;
    color: #fff;
    margin-bottom: 20px;
  }
  .hero h1 span { color: var(--accent); }
  .hero-sub {
    font-size: 17px;
    color: var(--text-muted);
    max-width: 680px;
    margin: 0 auto 36px;
    line-height: 1.6;
  }
  .hero-stats {
    display: flex;
    justify-content: center;
    gap: 40px;
    flex-wrap: wrap;
  }
  .hero-stat {
    text-align: center;
  }
  .hero-stat .val {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 28px;
    font-weight: 700;
    color: var(--accent);
  }
  .hero-stat .lbl {
    font-size: 12px;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.08em;
    margin-top: 2px;
  }

  /* ── LAYOUT ── */
  .container { max-width: 1100px; margin: 0 auto; padding: 0 32px; }

  /* ── NAV STRIP ── */
  .phase-nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(9,9,15,0.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    padding: 0 32px;
    overflow-x: auto;
    white-space: nowrap;
  }
  .phase-nav ul {
    display: inline-flex;
    list-style: none;
    gap: 0;
    height: 48px;
    align-items: stretch;
  }
  .phase-nav a {
    display: flex;
    align-items: center;
    gap: 7px;
    padding: 0 16px;
    text-decoration: none;
    font-size: 12.5px;
    font-weight: 500;
    color: var(--text-muted);
    transition: color 0.15s;
    border-bottom: 2px solid transparent;
    white-space: nowrap;
  }
  .phase-nav a:hover { color: var(--text); }
  .phase-nav li.p0 a { border-color: transparent; }
  .phase-nav li.p0 a:hover, .phase-nav li.p0 a.active { color: var(--phase0); border-color: var(--phase0); }
  .phase-nav li.p1 a:hover, .phase-nav li.p1 a.active { color: var(--phase1); border-color: var(--phase1); }
  .phase-nav li.p2 a:hover, .phase-nav li.p2 a.active { color: var(--phase2); border-color: var(--phase2); }
  .phase-nav li.p3 a:hover, .phase-nav li.p3 a.active { color: var(--phase3); border-color: var(--phase3); }
  .phase-nav li.p4 a:hover, .phase-nav li.p4 a.active { color: var(--phase4); border-color: var(--phase4); }
  .phase-nav li.p5 a:hover, .phase-nav li.p5 a.active { color: var(--phase5); border-color: var(--phase5); }
  .phase-nav li.p6 a:hover, .phase-nav li.p6 a.active { color: var(--phase6); border-color: var(--phase6); }

  .dot {
    width: 7px; height: 7px; border-radius: 50%; display: inline-block; flex-shrink: 0;
  }

  /* ── SECTION ── */
  .phase-section {
    padding: 72px 0 48px;
    border-bottom: 1px solid var(--border);
  }
  .phase-header {
    display: flex;
    align-items: flex-start;
    gap: 24px;
    margin-bottom: 48px;
  }
  .phase-badge {
    flex-shrink: 0;
    width: 56px;
    height: 56px;
    border-radius: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    font-weight: 500;
    border: 1px solid;
  }
  .phase-header-text h2 {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 28px;
    font-weight: 700;
    letter-spacing: -0.02em;
    color: #fff;
    line-height: 1.2;
  }
  .phase-header-text .timeline {
    font-size: 12.5px;
    color: var(--text-muted);
    margin-top: 6px;
    font-family: 'JetBrains Mono', monospace;
  }
  .phase-goal {
    font-size: 16px;
    color: var(--text-muted);
    margin-top: 10px;
    max-width: 720px;
  }

  /* Phase color variants */
  .ph0 .phase-badge { background: rgba(124,106,247,0.1); color: var(--phase0); border-color: rgba(124,106,247,0.3); }
  .ph1 .phase-badge { background: rgba(6,198,164,0.1); color: var(--phase1); border-color: rgba(6,198,164,0.3); }
  .ph2 .phase-badge { background: rgba(56,189,248,0.1); color: var(--phase2); border-color: rgba(56,189,248,0.3); }
  .ph3 .phase-badge { background: rgba(245,158,11,0.1); color: var(--phase3); border-color: rgba(245,158,11,0.3); }
  .ph4 .phase-badge { background: rgba(244,63,94,0.1); color: var(--phase4); border-color: rgba(244,63,94,0.3); }
  .ph5 .phase-badge { background: rgba(167,139,250,0.1); color: var(--phase5); border-color: rgba(167,139,250,0.3); }
  .ph6 .phase-badge { background: rgba(52,211,153,0.1); color: var(--phase6); border-color: rgba(52,211,153,0.3); }

  /* ── GRID ── */
  .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
  .grid-3 { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 20px; }
  @media(max-width: 800px) { .grid-2, .grid-3 { grid-template-columns: 1fr; } }

  /* ── CARD ── */
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
  }
  .card-full { grid-column: 1 / -1; }
  .card h3 {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 15px;
    font-weight: 600;
    color: #fff;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .card h3 .icon {
    font-size: 16px;
  }

  /* ── TOPIC PILLS ── */
  .topic-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .pill {
    font-size: 12.5px;
    padding: 4px 11px;
    border-radius: 20px;
    border: 1px solid var(--border-bright);
    color: var(--text-muted);
    background: var(--surface2);
    font-family: 'JetBrains Mono', monospace;
  }
  .pill.hi { border-color: rgba(124,106,247,0.4); color: #b0a6ff; background: rgba(124,106,247,0.08); }
  .pill.green { border-color: rgba(6,198,164,0.4); color: #5be8cf; background: rgba(6,198,164,0.08); }
  .pill.sky { border-color: rgba(56,189,248,0.4); color: #7dd3fc; background: rgba(56,189,248,0.08); }
  .pill.amber { border-color: rgba(245,158,11,0.4); color: #fcd34d; background: rgba(245,158,11,0.08); }
  .pill.rose { border-color: rgba(244,63,94,0.4); color: #fb7185; background: rgba(244,63,94,0.08); }

  /* ── LIST ── */
  .bullet-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 9px;
  }
  .bullet-list li {
    font-size: 13.5px;
    color: var(--text-muted);
    padding-left: 18px;
    position: relative;
    line-height: 1.5;
  }
  .bullet-list li::before {
    content: '→';
    position: absolute;
    left: 0;
    color: var(--text-dim);
    font-size: 11px;
    top: 2px;
  }
  .bullet-list li strong { color: var(--text); font-weight: 500; }

  /* ── PROJECT CARDS ── */
  .project-card {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 18px 20px;
    position: relative;
    overflow: hidden;
  }
  .project-card::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 3px;
    border-radius: 3px 0 0 3px;
  }
  .ph0 .project-card::before { background: var(--phase0); }
  .ph1 .project-card::before { background: var(--phase1); }
  .ph2 .project-card::before { background: var(--phase2); }
  .ph3 .project-card::before { background: var(--phase3); }
  .ph4 .project-card::before { background: var(--phase4); }
  .ph5 .project-card::before { background: var(--phase5); }
  .ph6 .project-card::before { background: var(--phase6); }
  .project-card .proj-title {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 14px;
    font-weight: 600;
    color: #fff;
    margin-bottom: 6px;
  }
  .project-card p {
    font-size: 13px;
    color: var(--text-muted);
    line-height: 1.5;
    margin-bottom: 10px;
  }
  .proj-meta {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
  }
  .proj-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    padding: 2px 8px;
    border-radius: 4px;
    background: var(--surface);
    border: 1px solid var(--border);
    color: var(--text-dim);
  }

  /* ── PAPER LIST ── */
  .paper-item {
    display: flex;
    gap: 14px;
    padding: 12px 0;
    border-bottom: 1px solid var(--border);
    align-items: flex-start;
  }
  .paper-item:last-child { border-bottom: none; }
  .paper-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--text-dim);
    flex-shrink: 0;
    padding-top: 2px;
    width: 24px;
  }
  .paper-body .paper-title {
    font-size: 13.5px;
    font-weight: 500;
    color: var(--text);
    line-height: 1.4;
  }
  .paper-body .paper-why {
    font-size: 12px;
    color: var(--text-muted);
    margin-top: 3px;
  }

  /* ── MINDSET BOX ── */
  .mindset-box {
    background: var(--surface2);
    border: 1px solid var(--border-bright);
    border-radius: 12px;
    padding: 20px 22px;
  }
  .mindset-box .mq {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 17px;
    font-weight: 600;
    color: #fff;
    line-height: 1.4;
    margin-bottom: 10px;
  }
  .mindset-box .mq::before { content: '"'; color: var(--accent); margin-right: 2px; }
  .mindset-box .mq::after { content: '"'; color: var(--accent); margin-left: 2px; }
  .mindset-box p {
    font-size: 13.5px;
    color: var(--text-muted);
    line-height: 1.6;
  }

  /* ── EXPECTATION BADGES ── */
  .expect-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 12px;
  }
  .expect-item {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px 16px;
  }
  .expect-item .expect-label {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--text-dim);
    margin-bottom: 6px;
    font-family: 'JetBrains Mono', monospace;
  }
  .expect-item p {
    font-size: 13px;
    color: var(--text-muted);
    line-height: 1.4;
  }

  /* ── SECTION LABEL ── */
  .section-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10.5px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--text-dim);
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── PRACTICAL ADVICE ── */
  .advice-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  @media(max-width:650px) { .advice-grid { grid-template-columns: 1fr; } }
  .advice-item {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px 16px;
    font-size: 13px;
    color: var(--text-muted);
    line-height: 1.5;
  }
  .advice-item strong {
    display: block;
    font-size: 13px;
    color: var(--text);
    margin-bottom: 4px;
    font-weight: 500;
  }

  /* ── FORMULA BLOCK ── */
  .formula-block {
    background: var(--surface);
    border: 1px solid var(--border-bright);
    border-radius: 16px;
    padding: 36px;
    text-align: center;
    margin: 48px 0;
  }
  .formula-block h3 {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 18px;
    font-weight: 600;
    color: #fff;
    margin-bottom: 28px;
  }
  .formula-items {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    gap: 0;
  }
  .formula-item {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 14px;
    font-weight: 600;
    padding: 10px 18px;
    border-radius: 8px;
    background: var(--surface2);
    border: 1px solid var(--border-bright);
    color: #fff;
  }
  .formula-plus {
    font-size: 22px;
    color: var(--text-dim);
    padding: 0 10px;
    font-weight: 300;
  }
  .formula-equals {
    font-size: 22px;
    color: var(--accent);
    padding: 0 10px;
    font-weight: 300;
  }
  .formula-result {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 15px;
    font-weight: 700;
    padding: 12px 20px;
    border-radius: 8px;
    background: rgba(124,106,247,0.15);
    border: 1px solid rgba(124,106,247,0.4);
    color: var(--accent);
    margin-top: 12px;
    width: 100%;
  }
  @media(max-width:700px) { .formula-items { flex-direction: column; } }

  /* ── HIRING SECTION ── */
  .hiring-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
  }
  @media(max-width:700px) { .hiring-grid { grid-template-columns: 1fr; } }
  .hiring-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 22px;
  }
  .hiring-card .lab-name {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 16px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 14px;
    padding-bottom: 12px;
    border-bottom: 1px solid var(--border);
  }

  /* ── SPACER ── */
  .mt8 { margin-top: 8px; }
  .mt12 { margin-top: 12px; }
  .mt16 { margin-top: 16px; }
  .mt24 { margin-top: 24px; }
  .mt32 { margin-top: 32px; }

  /* ── FOOTER ── */
  footer {
    padding: 40px 32px;
    text-align: center;
    color: var(--text-dim);
    font-size: 13px;
    border-top: 1px solid var(--border);
  }
  footer span { color: var(--text-muted); }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 6px; height: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border-bright); border-radius: 3px; }

  /* ── HIGHLIGHT STRIP ── */
  .highlight-strip {
    background: linear-gradient(90deg, rgba(124,106,247,0.08) 0%, rgba(6,198,164,0.05) 100%);
    border: 1px solid rgba(124,106,247,0.2);
    border-radius: 12px;
    padding: 20px 24px;
    margin-bottom: 24px;
    font-size: 14px;
    color: var(--text-muted);
    line-height: 1.6;
  }
  .highlight-strip strong { color: var(--text); font-weight: 500; }
</style>
</head>
<body>

<!-- HERO -->
<div class="hero">
  <div class="hero-eyebrow">// the definitive guide</div>
  <h1>Become a <span>World-Class</span><br>AI Researcher</h1>
  <p class="hero-sub">A structured, phased roadmap from mathematical foundations to frontier research — targeting OpenAI, DeepMind, Anthropic, Meta AI, and Google Brain.</p>
  <div class="hero-stats">
    <div class="hero-stat"><div class="val">7</div><div class="lbl">Phases</div></div>
    <div class="hero-stat"><div class="val">4–7yr</div><div class="lbl">Timeline</div></div>
    <div class="hero-stat"><div class="val">&lt;0.5%</div><div class="lbl">Acceptance Rate</div></div>
    <div class="hero-stat"><div class="val">~2,000</div><div class="lbl">Elite Researchers Globally</div></div>
  </div>
</div>

<!-- STICKY NAV -->
<nav class="phase-nav">
  <ul>
    <li class="p0"><a href="#phase0"><span class="dot" style="background:var(--phase0)"></span>Phase 0: Foundations</a></li>
    <li class="p1"><a href="#phase1"><span class="dot" style="background:var(--phase1)"></span>Phase 1: Core ML</a></li>
    <li class="p2"><a href="#phase2"><span class="dot" style="background:var(--phase2)"></span>Phase 2: Deep Learning</a></li>
    <li class="p3"><a href="#phase3"><span class="dot" style="background:var(--phase3)"></span>Phase 3: Transformers</a></li>
    <li class="p4"><a href="#phase4"><span class="dot" style="background:var(--phase4)"></span>Phase 4: Advanced Research</a></li>
    <li class="p5"><a href="#phase5"><span class="dot" style="background:var(--phase5)"></span>Phase 5: Specialization</a></li>
    <li class="p6"><a href="#phase6"><span class="dot" style="background:var(--phase6)"></span>Phase 6: Lab Readiness</a></li>
  </ul>
</nav>

<!-- ═══════════════════════════════════════════
     PHASE 0
═══════════════════════════════════════════ -->
<section class="phase-section ph0" id="phase0">
<div class="container">
  <div class="phase-header">
    <div class="phase-badge">P0</div>
    <div class="phase-header-text">
      <h2>Mathematical & Systems Foundations</h2>
      <div class="timeline">⏱ Months 1–4 · ~10–15 hrs/week</div>
      <p class="phase-goal">Build rock-solid mathematical fluency and programming instincts. Every model you build later rests entirely on what you internalize here.</p>
    </div>
  </div>

  <div class="section-label">Core Topics</div>
  <div class="grid-2 mt16">
    <div class="card">
      <h3><span class="icon">📐</span> Mathematics</h3>
      <div class="topic-grid">
        <span class="pill hi">Vectors & Matrices</span><span class="pill hi">Matrix Multiplication</span><span class="pill hi">Eigenvalues & SVD</span><span class="pill hi">PCA</span><span class="pill hi">Orthogonality</span><span class="pill hi">Partial Derivatives</span><span class="pill hi">Chain Rule</span><span class="pill hi">Jacobians & Hessians</span><span class="pill hi">Bayes' Theorem</span><span class="pill hi">MLE</span><span class="pill hi">KL Divergence</span><span class="pill hi">Gradient Descent</span><span class="pill hi">SGD & Adam</span><span class="pill hi">Convexity</span><span class="pill hi">Lagrange Multipliers</span>
      </div>
    </div>
    <div class="card">
      <h3><span class="icon">💻</span> Programming & Systems</h3>
      <div class="topic-grid">
        <span class="pill">Python</span><span class="pill">NumPy</span><span class="pill">SciPy</span><span class="pill">Pandas</span><span class="pill">Matplotlib</span><span class="pill">Git</span><span class="pill">Linux</span><span class="pill">Docker</span><span class="pill">Unit Tests</span><span class="pill">Profiling</span><span class="pill">Complexity Analysis</span><span class="pill">Hash Maps</span><span class="pill">Dynamic Programming</span><span class="pill">Graphs & Trees</span>
      </div>
    </div>
  </div>

  <div class="section-label mt32">Mindset & Thinking Framework</div>
  <div class="mindset-box mt16">
    <div class="mq">Don't ask which library to use. Ask why this works.</div>
    <p>At this stage, internalize mathematical notation and concepts from first principles. Why does gradient descent converge? Derive backpropagation from scratch. Derive logistic regression from scratch. This "math maturity" — the ability to handle proofs and abstract reasoning — is what frontier lab leads like Vladimir Feinberg (DeepMind Gemini Pre-training) identify as a key differentiator before anything else. Avoid memorization; chase understanding.</p>
  </div>

  <div class="section-label mt32">Performance Expectations</div>
  <div class="expect-grid mt16">
    <div class="expect-item"><div class="expect-label">Derivation</div><p>Derive gradients for MSE loss from scratch; explain matrix inverse geometrically</p></div>
    <div class="expect-item"><div class="expect-label">Implementation</div><p>Implement core ML primitives from scratch in pure Python/NumPy — no frameworks</p></div>
    <div class="expect-item"><div class="expect-label">Communication</div><p>Explain data, assumptions, and tradeoffs with precision; no vague claims</p></div>
    <div class="expect-item"><div class="expect-label">Reproducibility</div><p>Clean code, logged experiments, and reproducible results from day one</p></div>
  </div>

  <div class="section-label mt32">Project Ideas</div>
  <div class="grid-2 mt16">
    <div class="project-card">
      <div class="proj-title">Matrix Library from Scratch</div>
      <p>Implement matrix multiplication, inverse, SVD, and PCA using only raw Python — zero NumPy. Forces true understanding of linear algebra operations.</p>
      <div class="proj-meta"><span class="proj-tag">Pure Python</span><span class="proj-tag">Correctness vs NumPy</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Neural Network from Scratch</div>
      <p>Build forward propagation, backprop, and SGD manually. No PyTorch. Add gradient checking to verify correctness.</p>
      <div class="proj-meta"><span class="proj-tag">MNIST</span><span class="proj-tag">Accuracy</span><span class="proj-tag">Gradient Check</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Loss Landscape Visualizer</div>
      <p>Plot loss surfaces for linear/logistic regression. Overlay gradient descent paths for different learning rates and visualize convergence behavior.</p>
      <div class="proj-meta"><span class="proj-tag">Matplotlib</span><span class="proj-tag">Synthetic Data</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">PCA + KMeans Explorer</div>
      <p>Apply PCA and K-Means on Fashion-MNIST. Compare t-SNE and UMAP. Visualize cluster quality and dimensionality reduction effects.</p>
      <div class="proj-meta"><span class="proj-tag">Fashion-MNIST</span><span class="proj-tag">Silhouette Score</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Paper-Reading Repository</div>
      <p>Create a public GitHub repo with structured summaries of every paper: problem, method, claim, evidence, limitations, and your implementation notes.</p>
      <div class="proj-meta"><span class="proj-tag">GitHub</span><span class="proj-tag">Markdown</span></div>
    </div>
  </div>

  <div class="section-label mt32">Seminal Papers to Read</div>
  <div class="card mt16">
    <div class="paper-item"><div class="paper-num">01</div><div class="paper-body"><div class="paper-title">Perceptron (Rosenblatt, 1958)</div><div class="paper-why">Understand the origins of neural learning — conceptual grounding before modern complexity</div></div></div>
    <div class="paper-item"><div class="paper-num">02</div><div class="paper-body"><div class="paper-title">Backpropagation (Rumelhart et al., 1986)</div><div class="paper-why">The foundational paper on gradient flow in networks — derive every equation yourself</div></div></div>
    <div class="paper-item"><div class="paper-num">03</div><div class="paper-body"><div class="paper-title">Efficient Backprop (LeCun)</div><div class="paper-why">Practical optimization insights that still matter: initialization, learning rate schedules, input preprocessing</div></div></div>
    <div class="paper-item"><div class="paper-num">04</div><div class="paper-body"><div class="paper-title">LeNet-5 / Gradient-Based Learning Applied to Document Recognition (LeCun, 1998)</div><div class="paper-why">Birth of CNNs — understand the full pipeline from raw pixels to classification</div></div></div>
    <div class="paper-item"><div class="paper-num">05</div><div class="paper-body"><div class="paper-title">A Few Useful Things to Know About Machine Learning (Domingos, 2012)</div><div class="paper-why">Essential practical intuition for the entire field — read it now and re-read it in every phase</div></div></div>
  </div>

  <div class="section-label mt32">Practical Advice</div>
  <div class="advice-grid mt16">
    <div class="advice-item"><strong>Don't rush this phase.</strong>A weak mathematical foundation makes every subsequent paper incomprehensible. Spend real time here.</div>
    <div class="advice-item"><strong>Resources: Andrew Ng's ML Course + Mathematics for ML Specialization.</strong> Pair with the Bishop PRML textbook (chapters on probability and inference).</div>
    <div class="advice-item"><strong>10–15 hrs/week minimum.</strong>Consistency beats intensity. Daily practice with derivations compounds faster than weekend cramming.</div>
    <div class="advice-item"><strong>Start your research log now.</strong>Document failed attempts, observations, and "aha" moments — this habit will matter enormously in Phases 4–6.</div>
  </div>
</div>
</section>

<!-- ═══════════════════════════════════════════
     PHASE 1
═══════════════════════════════════════════ -->
<section class="phase-section ph1" id="phase1">
<div class="container">
  <div class="phase-header">
    <div class="phase-badge">P1</div>
    <div class="phase-header-text">
      <h2>Classical Machine Learning</h2>
      <div class="timeline">⏱ Months 4–9 · Build to strong ML engineer level</div>
      <p class="phase-goal">Master the classical ML toolkit and experimental discipline. Develop an instinct for baselines, rigorous evaluation, and the bias-variance tradeoff.</p>
    </div>
  </div>

  <div class="section-label">Core Topics</div>
  <div class="grid-3 mt16">
    <div class="card">
      <h3>Supervised Learning</h3>
      <div class="topic-grid">
        <span class="pill green">Linear Regression</span><span class="pill green">Logistic Regression</span><span class="pill green">Ridge & Lasso</span><span class="pill green">SVMs</span><span class="pill green">Decision Trees</span><span class="pill green">Random Forests</span><span class="pill green">XGBoost</span>
      </div>
    </div>
    <div class="card">
      <h3>Unsupervised Learning</h3>
      <div class="topic-grid">
        <span class="pill green">K-Means</span><span class="pill green">DBSCAN</span><span class="pill green">GMM</span><span class="pill green">PCA</span><span class="pill green">t-SNE</span><span class="pill green">UMAP</span><span class="pill green">Naive Bayes</span><span class="pill green">HMM</span>
      </div>
    </div>
    <div class="card">
      <h3>Evaluation & Statistics</h3>
      <div class="topic-grid">
        <span class="pill green">Bias-Variance Tradeoff</span><span class="pill green">Cross-Validation</span><span class="pill green">Leakage Detection</span><span class="pill green">Calibration</span><span class="pill green">Hypothesis Testing</span><span class="pill green">Bootstrap</span><span class="pill green">ROC-AUC</span>
      </div>
    </div>
  </div>

  <div class="section-label mt32">Mindset & Thinking Framework</div>
  <div class="mindset-box mt16">
    <div class="mq">Baselines before novelty. Ablations before announcements.</div>
    <p>Start every problem by asking: what is the simplest model that could work? Then beat it systematically. When reading papers, always ask whether the improvement is algorithmic, data-related, or compute-related — most claimed gains collapse under scrutiny. Implement the "From Scratch Rule": to truly understand an algorithm, implement it from scratch using NumPy before touching Scikit-learn. This is how you internalize gradient updates at the level top labs expect.</p>
  </div>

  <div class="section-label mt32">Performance Expectations</div>
  <div class="expect-grid mt16">
    <div class="expect-item"><div class="expect-label">Derivation</div><p>Derive closed-form solution for linear regression; explain SVM margin geometrically</p></div>
    <div class="expect-item"><div class="expect-label">Debugging</div><p>Reason about model failures from gradients, loss surfaces, and data distributions</p></div>
    <div class="expect-item"><div class="expect-label">Evaluation</div><p>Build rigorous evaluation pipelines with proper splits, seeds, and confidence intervals</p></div>
    <div class="expect-item"><div class="expect-label">Portfolio</div><p>GitHub with clean, documented from-scratch implementations — your "real resume"</p></div>
  </div>

  <div class="section-label mt32">Project Ideas</div>
  <div class="grid-2 mt16">
    <div class="project-card">
      <div class="proj-title">ML From Scratch Repository</div>
      <p>Build a clean GitHub repo with NumPy implementations of Linear Regression, Logistic Regression, KNN, K-Means, PCA, and Random Forests. Structure it like a documented library with tests.</p>
      <div class="proj-meta"><span class="proj-tag">NumPy only</span><span class="proj-tag">UCI Datasets</span><span class="proj-tag">GitHub</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Rebuild XGBoost Core</div>
      <p>Implement gradient boosting with decision tree weak learners from scratch. Compare against XGBoost on Kaggle competition datasets. Analyze where your implementation breaks.</p>
      <div class="proj-meta"><span class="proj-tag">House Prices</span><span class="proj-tag">RMSE</span><span class="proj-tag">Feature Importance</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Bias-Variance Empirical Analysis</div>
      <p>Design an experiment on synthetic data systematically varying model complexity. Plot train/test error curves with confidence intervals. Identify the sweet spot and explain why it moves.</p>
      <div class="proj-meta"><span class="proj-tag">Synthetic Data</span><span class="proj-tag">Bootstrap CI</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Fraud Detection with Calibration</div>
      <p>Build a complete fraud detection pipeline with calibrated probabilities, threshold tuning, and ROC/PR analysis. Write up root cause analysis of every false positive cluster.</p>
      <div class="proj-meta"><span class="proj-tag">Credit Fraud Dataset</span><span class="proj-tag">ROC-AUC</span><span class="proj-tag">Calibration Curve</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Recommendation System</div>
      <p>Build a MovieLens recommender using matrix factorization. Compare collaborative filtering, content-based, and hybrid approaches with proper evaluation.</p>
      <div class="proj-meta"><span class="proj-tag">MovieLens</span><span class="proj-tag">RMSE</span><span class="proj-tag">MAP@K</span></div>
    </div>
  </div>

  <div class="section-label mt32">Papers to Read</div>
  <div class="card mt16">
    <div class="paper-item"><div class="paper-num">01</div><div class="paper-body"><div class="paper-title">Random Forests (Breiman, 2001)</div><div class="paper-why">The definitive paper on ensemble learning — understand bagging, feature randomness, and why ensembles generalize</div></div></div>
    <div class="paper-item"><div class="paper-num">02</div><div class="paper-body"><div class="paper-title">XGBoost: A Scalable Tree Boosting System (Chen & Guestrin, 2016)</div><div class="paper-why">Engineering and algorithmic masterclass — learn how theoretical insights become practical systems</div></div></div>
    <div class="paper-item"><div class="paper-num">03</div><div class="paper-body"><div class="paper-title">The Elements of Statistical Learning (Hastie et al.) — Ch. 1–7</div><div class="paper-why">The definitive reference for classical ML. Read these chapters for deep mathematical grounding</div></div></div>
    <div class="paper-item"><div class="paper-num">04</div><div class="paper-body"><div class="paper-title">Visualizing Data using t-SNE (Van der Maaten, 2008)</div><div class="paper-why">Understand manifold learning and the subtleties of high-dimensional visualization (and its limitations)</div></div></div>
    <div class="paper-item"><div class="paper-num">05</div><div class="paper-body"><div class="paper-title">Matrix Factorization Techniques for Recommender Systems (Netflix Prize)</div><div class="paper-why">A landmark applied ML paper — understand how latent factor models work in practice</div></div></div>
    <div class="paper-item"><div class="paper-num">06</div><div class="paper-body"><div class="paper-title">PageRank (Brin & Page, 1998)</div><div class="paper-why">Classic application of linear algebra to graph structure — develops systems thinking</div></div></div>
  </div>

  <div class="section-label mt32">Practical Advice</div>
  <div class="advice-grid mt16">
    <div class="advice-item"><strong>Kaggle as a learning tool, not a competition.</strong>Reproduce top solutions with full validation discipline and document every failure mode you discover.</div>
    <div class="advice-item"><strong>Start networking now.</strong>Attend local meetups or virtual seminars. Present your from-scratch implementations and ask for critique.</div>
    <div class="advice-item"><strong>Error analysis is a core skill.</strong>For every misclassified example, ask why. This habit defines good researchers.</div>
    <div class="advice-item"><strong>Use statistical significance tests.</strong>Never report a "better" result without a confidence interval or bootstrap comparison.</div>
  </div>
</div>
</section>

<!-- ═══════════════════════════════════════════
     PHASE 2
═══════════════════════════════════════════ -->
<section class="phase-section ph2" id="phase2">
<div class="container">
  <div class="phase-header">
    <div class="phase-badge">P2</div>
    <div class="phase-header-text">
      <h2>Deep Learning Foundations</h2>
      <div class="timeline">⏱ Months 9–17 · Strong deep learning engineer level</div>
      <p class="phase-goal">Become a "coding machine" — fluent in PyTorch, capable of implementing modern architectures from scratch, and able to read training curves like an instrument panel.</p>
    </div>
  </div>

  <div class="section-label">Core Topics</div>
  <div class="grid-3 mt16">
    <div class="card">
      <h3>Architectures</h3>
      <div class="topic-grid">
        <span class="pill sky">MLPs & Backprop</span><span class="pill sky">CNNs</span><span class="pill sky">AlexNet / VGG</span><span class="pill sky">ResNet</span><span class="pill sky">EfficientNet</span><span class="pill sky">RNNs & LSTMs</span><span class="pill sky">GRUs</span><span class="pill sky">Encoder-Decoder</span><span class="pill sky">U-Net</span><span class="pill sky">GANs</span>
      </div>
    </div>
    <div class="card">
      <h3>Optimization & Regularization</h3>
      <div class="topic-grid">
        <span class="pill sky">Batch Normalization</span><span class="pill sky">Dropout</span><span class="pill sky">Weight Decay</span><span class="pill sky">AdamW</span><span class="pill sky">LR Schedules</span><span class="pill sky">Initialization</span><span class="pill sky">Gradient Clipping</span><span class="pill sky">Mixed Precision</span>
      </div>
    </div>
    <div class="card">
      <h3>Systems</h3>
      <div class="topic-grid">
        <span class="pill sky">PyTorch Autograd</span><span class="pill sky">GPU Profiling</span><span class="pill sky">CUDA Basics</span><span class="pill sky">Distributed Training</span><span class="pill sky">torch.compile</span><span class="pill sky">Memory Optimization</span><span class="pill sky">Dataloaders</span>
      </div>
    </div>
  </div>

  <div class="section-label mt32">Mindset & Thinking Framework</div>
  <div class="mindset-box mt16">
    <div class="mq">Every architecture choice is a testable hypothesis. Every loss curve tells a story.</div>
    <p>When you look at a neural network, don't see a black box — see a computational graph. Debug by tracing gradient flow: where do gradients vanish or explode? Treat every architectural decision as an experiment: does skip connections improve training? Why? Measure it with ablations. This "gradient flow perspective" is how elite researchers think about deep learning systems. Read training curves like a scientist reads an instrument panel — divergence, plateaus, and overfitting onset all have specific causes you should be able to diagnose.</p>
  </div>

  <div class="section-label mt32">Performance Expectations</div>
  <div class="expect-grid mt16">
    <div class="expect-item"><div class="expect-label">Implementation</div><p>Implement and train modern architectures from scratch; implement multi-head attention from memory</p></div>
    <div class="expect-item"><div class="expect-label">Systems</div><p>Comfortable with GPU training, memory bottlenecks, mixed precision, and profiling</p></div>
    <div class="expect-item"><div class="expect-label">Diagnostics</div><p>Diagnose whether failure comes from optimization, data, architecture, or objective mismatch</p></div>
    <div class="expect-item"><div class="expect-label">Portfolio</div><p>Reproductions plus one or two genuine improvements on standard benchmarks</p></div>
  </div>

  <div class="section-label mt32">Project Ideas</div>
  <div class="grid-2 mt16">
    <div class="project-card">
      <div class="proj-title">ResNet from Scratch with Ablations</div>
      <p>Implement and train ResNet on CIFAR-10. Ablate depth, skip connections, batch norm, augmentation, and weight decay separately. Build a results table comparing each variant.</p>
      <div class="proj-meta"><span class="proj-tag">CIFAR-10</span><span class="proj-tag">Top-1 Accuracy</span><span class="proj-tag">Ablations</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Image Captioning (CNN + LSTM)</div>
      <p>Build an image captioning system with a CNN encoder and LSTM decoder. Implement beam search. Analyze failure cases where the model hallucinates or produces grammatically wrong captions.</p>
      <div class="proj-meta"><span class="proj-tag">MSCOCO</span><span class="proj-tag">BLEU Score</span><span class="proj-tag">Beam Search</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Diffusion Model on MNIST</div>
      <p>Implement a DDPM-style diffusion model. Experiment with different noise schedules (linear vs cosine). Evaluate sample quality with FID. Compare DDPM vs DDIM sampling.</p>
      <div class="proj-meta"><span class="proj-tag">MNIST / CIFAR</span><span class="proj-tag">FID Score</span><span class="proj-tag">Noise Schedules</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">GAN Training Deep-Dive</div>
      <p>Train a StyleGAN/DCGAN on CelebA. Study and document mode collapse behavior, training instability, and how architectural choices affect convergence. Add WGAN-GP variant.</p>
      <div class="proj-meta"><span class="proj-tag">CelebA</span><span class="proj-tag">FID</span><span class="proj-tag">Inception Score</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Neural Scaling Experiment</div>
      <p>Train a family of MLPs / small CNNs at different scales. Measure test loss vs model size, dataset size, and compute. Plot empirical scaling laws and compare to Kaplan et al.'s predictions.</p>
      <div class="proj-meta"><span class="proj-tag">CIFAR-100</span><span class="proj-tag">Loss vs Compute</span><span class="proj-tag">Log-log Plots</span></div>
    </div>
  </div>

  <div class="section-label mt32">Papers to Read</div>
  <div class="card mt16">
    <div class="paper-item"><div class="paper-num">01</div><div class="paper-body"><div class="paper-title">ImageNet Classification with Deep CNNs — AlexNet (Krizhevsky et al., 2012)</div><div class="paper-why">The paper that reignited deep learning — understand how GPU training and dropout enabled this breakthrough</div></div></div>
    <div class="paper-item"><div class="paper-num">02</div><div class="paper-body"><div class="paper-title">Deep Residual Learning for Image Recognition — ResNet (He et al., 2016)</div><div class="paper-why">Foundational paper on skip connections; understand the gradient flow argument from first principles</div></div></div>
    <div class="paper-item"><div class="paper-num">03</div><div class="paper-body"><div class="paper-title">Batch Normalization (Ioffe & Szegedy, 2015)</div><div class="paper-why">Understand why training stability matters and how normalization reshapes the loss landscape</div></div></div>
    <div class="paper-item"><div class="paper-num">04</div><div class="paper-body"><div class="paper-title">Generative Adversarial Networks (Goodfellow et al., 2014)</div><div class="paper-why">Classic paper that introduced min-max training for generative models; study the training dynamics carefully</div></div></div>
    <div class="paper-item"><div class="paper-num">05</div><div class="paper-body"><div class="paper-title">Adam: A Method for Stochastic Optimization (Kingma & Ba, 2015)</div><div class="paper-why">Derive the update rule and understand when Adam outperforms SGD and when it does not</div></div></div>
    <div class="paper-item"><div class="paper-num">06</div><div class="paper-body"><div class="paper-title">Denoising Diffusion Probabilistic Models (Ho et al., 2020)</div><div class="paper-why">Foundational diffusion paper — understand the forward/reverse process and the ELBO connection</div></div></div>
    <div class="paper-item"><div class="paper-num">07</div><div class="paper-body"><div class="paper-title">EfficientNet (Tan & Le, 2019)</div><div class="paper-why">Learn systematic compound scaling — a case study in using NAS and principled design together</div></div></div>
    <div class="paper-item"><div class="paper-num">08</div><div class="paper-body"><div class="paper-title">U-Net (Ronneberger et al., 2015)</div><div class="paper-why">Encoder-decoder with skip connections for dense prediction — essential architectural pattern</div></div></div>
  </div>

  <div class="section-label mt32">Practical Advice</div>
  <div class="advice-grid mt16">
    <div class="advice-item"><strong>Go deep on PyTorch.</strong> PyTorch appears in 42% of ML engineer job postings. Learn <code>torch.compile</code>, distributed training basics, and memory profiling — not just <code>nn.Module</code>.</div>
    <div class="advice-item"><strong>Build a GPU experiment budget habit.</strong>Track GPU hours per experiment. Learning to be efficient with compute now will matter enormously at scale.</div>
    <div class="advice-item"><strong>Reproduce before innovating.</strong>Pick one paper per month and reproduce its main result exactly. Only then propose an improvement.</div>
    <div class="advice-item"><strong>Share your work publicly.</strong>Post reproductions with clear README, results tables, and training logs. This is how researchers discover you.</div>
  </div>
</div>
</section>

<!-- ═══════════════════════════════════════════
     PHASE 3
═══════════════════════════════════════════ -->
<section class="phase-section ph3" id="phase3">
<div class="container">
  <div class="phase-header">
    <div class="phase-badge">P3</div>
    <div class="phase-header-text">
      <h2>Transformers & Foundation Models</h2>
      <div class="timeline">⏱ Months 17–26 · Research Engineer level</div>
      <p class="phase-goal">This phase separates ordinary ML engineers from frontier AI researchers. Master every component of the transformer and understand how modern foundation models are built and scaled.</p>
    </div>
  </div>

  <div class="section-label">Core Topics</div>
  <div class="grid-3 mt16">
    <div class="card">
      <h3>Attention & Transformers</h3>
      <div class="topic-grid">
        <span class="pill amber">Self-Attention</span><span class="pill amber">Cross-Attention</span><span class="pill amber">Multi-Head Attention</span><span class="pill amber">Grouped-Query Attention</span><span class="pill amber">SwiGLU / GLU</span><span class="pill amber">RoPE</span><span class="pill amber">ALiBi</span><span class="pill amber">Encoder-only (BERT)</span><span class="pill amber">Decoder-only (GPT)</span><span class="pill amber">Encoder-Decoder (T5)</span>
      </div>
    </div>
    <div class="card">
      <h3>Language Models</h3>
      <div class="topic-grid">
        <span class="pill amber">BERT / GPT / T5</span><span class="pill amber">Llama Architecture</span><span class="pill amber">Mixture of Experts</span><span class="pill amber">BPE / SentencePiece</span><span class="pill amber">Scaling Laws</span><span class="pill amber">Chinchilla Compute Optimal</span><span class="pill amber">In-Context Learning</span><span class="pill amber">RMSNorm</span>
      </div>
    </div>
    <div class="card">
      <h3>Training Infrastructure</h3>
      <div class="topic-grid">
        <span class="pill amber">FSDP</span><span class="pill amber">DDP</span><span class="pill amber">DeepSpeed</span><span class="pill amber">FlashAttention</span><span class="pill amber">Gradient Checkpointing</span><span class="pill amber">Mixed Precision BF16</span><span class="pill amber">Tensor Parallelism</span>
      </div>
    </div>
  </div>

  <div class="section-label mt32">Mindset & Thinking Framework</div>
  <div class="mindset-box mt16">
    <div class="mq">Develop research taste: the intuitive ability to identify promising directions versus dead ends.</div>
    <p>This is where "research taste" begins to matter. When you read a new transformer variant, don't just ask "does it work" — ask "why would this mechanism help, given what we know about attention?" Start thinking about the information bottleneck: why does depth matter? Why does attention scale better than convolution for long sequences? Apply the gradient flow perspective from Phase 2 to transformers — trace attention patterns, KV cache behavior, and loss spikes to their architectural causes. DeepMind explicitly identifies research taste as a key interview signal.</p>
  </div>

  <div class="section-label mt32">Performance Expectations</div>
  <div class="expect-grid mt16">
    <div class="expect-item"><div class="expect-label">Implementation</div><p>Implement multi-head attention from memory in PyTorch or JAX; build a GPT from scratch</p></div>
    <div class="expect-item"><div class="expect-label">Tradeoffs</div><p>Explain GQA vs MHA vs MQA tradeoffs; know when each is appropriate</p></div>
    <div class="expect-item"><div class="expect-label">Scaling</div><p>Understand compute-optimal training; explain Chinchilla's implications for model design</p></div>
    <div class="expect-item"><div class="expect-label">Systems</div><p>Run distributed training; understand where compute is spent in a transformer forward pass</p></div>
  </div>

  <div class="section-label mt32">Project Ideas</div>
  <div class="grid-2 mt16">
    <div class="project-card">
      <div class="proj-title">GPT from Scratch</div>
      <p>Build a full GPT — tokenizer, embeddings, multi-head attention, MLP, LayerNorm — and train on TinyStories or OpenWebText. Measure perplexity vs model size. Study in-context learning emergence.</p>
      <div class="proj-meta"><span class="proj-tag">TinyStories</span><span class="proj-tag">Perplexity</span><span class="proj-tag">Scaling Curves</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">BERT Pretraining on WikiText</div>
      <p>Implement masked language modeling from scratch. Train on WikiText-103. Evaluate masked token prediction accuracy. Fine-tune on a classification task and analyze attention heads.</p>
      <div class="proj-meta"><span class="proj-tag">WikiText-103</span><span class="proj-tag">MLM Accuracy</span><span class="proj-tag">Fine-tuning</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Build Llama Architecture (RoPE + RMSNorm)</div>
      <p>Implement the Llama 2 architecture with RoPE positional embeddings, RMSNorm, SwiGLU, and GQA. Compare to vanilla transformer on perplexity and training speed.</p>
      <div class="proj-meta"><span class="proj-tag">OpenWebText</span><span class="proj-tag">Perplexity</span><span class="proj-tag">Throughput tokens/s</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Retrieval-Augmented Generation System</div>
      <p>Build an RAG system using FAISS for vector retrieval. Evaluate faithfulness, hallucination rate, Recall@K, and latency. Compare RAG vs vanilla generation on factual QA tasks.</p>
      <div class="proj-meta"><span class="proj-tag">NQ / TriviaQA</span><span class="proj-tag">Recall@K</span><span class="proj-tag">Hallucination Rate</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Vision Transformer on CIFAR-100</div>
      <p>Implement ViT from scratch. Compare to ResNet on CIFAR-100. Ablate patch size, number of heads, and depth. Visualize attention maps and explain what each head attends to.</p>
      <div class="proj-meta"><span class="proj-tag">CIFAR-100</span><span class="proj-tag">Top-1 Accuracy</span><span class="proj-tag">Attention Maps</span></div>
    </div>
  </div>

  <div class="section-label mt32">Papers to Read</div>
  <div class="card mt16">
    <div class="paper-item"><div class="paper-num">01</div><div class="paper-body"><div class="paper-title">Attention Is All You Need (Vaswani et al., 2017)</div><div class="paper-why">The foundational paper — understand every equation, every architectural choice, and why it replaced RNNs</div></div></div>
    <div class="paper-item"><div class="paper-num">02</div><div class="paper-body"><div class="paper-title">BERT (Devlin et al., 2018)</div><div class="paper-why">Understand bidirectional pretraining, masked LM, and how fine-tuning paradigms emerged</div></div></div>
    <div class="paper-item"><div class="paper-num">03</div><div class="paper-body"><div class="paper-title">Language Models are Few-Shot Learners — GPT-3 (Brown et al., 2020)</div><div class="paper-why">Understand in-context learning, scaling behavior, and the emergence of capabilities with model size</div></div></div>
    <div class="paper-item"><div class="paper-num">04</div><div class="paper-body"><div class="paper-title">Scaling Laws for Neural Language Models (Kaplan et al., 2020)</div><div class="paper-why">Core framework for understanding how loss scales with compute, parameters, and data</div></div></div>
    <div class="paper-item"><div class="paper-num">05</div><div class="paper-body"><div class="paper-title">Training Compute-Optimal Large Language Models — Chinchilla (Hoffmann et al., 2022)</div><div class="paper-why">Corrects Kaplan's scaling laws and defines compute-optimal training — essential for understanding modern model design</div></div></div>
    <div class="paper-item"><div class="paper-num">06</div><div class="paper-body"><div class="paper-title">FlashAttention (Dao et al., 2022)</div><div class="paper-why">Understand how IO-awareness and tiling enable 2–4× speedups — critical for production systems</div></div></div>
    <div class="paper-item"><div class="paper-num">07</div><div class="paper-body"><div class="paper-title">RoFormer (Su et al., 2021)</div><div class="paper-why">Foundational paper on Rotary Position Embeddings (RoPE) — now standard in every modern LLM</div></div></div>
    <div class="paper-item"><div class="paper-num">08</div><div class="paper-body"><div class="paper-title">Switch Transformers (Fedus et al., 2021)</div><div class="paper-why">Mixture of Experts at scale — understand sparse activation and routing mechanisms</div></div></div>
    <div class="paper-item"><div class="paper-num">09</div><div class="paper-body"><div class="paper-title">Llama 2 (Touvron et al., 2023)</div><div class="paper-why">Modern open-source LLM — study the full architecture and training recipe in detail</div></div></div>
  </div>

  <div class="section-label mt32">Practical Advice</div>
  <div class="advice-grid mt16">
    <div class="advice-item"><strong>Anthropic's CodeSignal Test.</strong>The Anthropic assessment requires 520+/600. It's an architecture-first system design coding problem — not LeetCode. Practice now.</div>
    <div class="advice-item"><strong>Read papers, not just tutorials.</strong>For every transformer variant, read the actual paper. Tutorials strip the nuance that matters in research interviews.</div>
    <div class="advice-item"><strong>Start applying for PhD internships.</strong>If you're a PhD student or postdoc, this is the right time to target summer internships at top labs. Research talks and connections formed here compound.</div>
    <div class="advice-item"><strong>Build a scaling experiment.</strong>Running even a small scaling experiment gives you intuition that no paper can fully convey — you'll see loss curves in your mind during any scaling discussion.</div>
  </div>
</div>
</section>

<!-- ═══════════════════════════════════════════
     PHASE 4
═══════════════════════════════════════════ -->
<section class="phase-section ph4" id="phase4">
<div class="container">
  <div class="phase-header">
    <div class="phase-badge">P4</div>
    <div class="phase-header-text">
      <h2>Advanced Research Domains</h2>
      <div class="timeline">⏱ Months 26–38 · PhD-level capability</div>
      <p class="phase-goal">Begin thinking like DeepMind researchers. Choose 1–2 domains to go deep in. Master reinforcement learning, generative models, multimodal systems, or mechanistic interpretability.</p>
    </div>
  </div>

  <div class="section-label">Core Topics by Domain</div>
  <div class="grid-2 mt16">
    <div class="card">
      <h3>🎮 Reinforcement Learning</h3>
      <div class="topic-grid">
        <span class="pill rose">MDP & Bellman Equations</span><span class="pill rose">Policy Gradients</span><span class="pill rose">Q-Learning & DQN</span><span class="pill rose">Actor-Critic</span><span class="pill rose">PPO</span><span class="pill rose">SAC / TD3</span><span class="pill rose">DreamerV3</span><span class="pill rose">MuZero</span><span class="pill rose">RLHF</span><span class="pill rose">RLVR</span>
      </div>
    </div>
    <div class="card">
      <h3>🎨 Generative Models</h3>
      <div class="topic-grid">
        <span class="pill rose">VAE & ELBO</span><span class="pill rose">Diffusion (DDPM/DDIM)</span><span class="pill rose">Flow Matching</span><span class="pill rose">Consistency Models</span><span class="pill rose">GAN Variants</span><span class="pill rose">Score Matching</span><span class="pill rose">Classifier-Free Guidance</span>
      </div>
    </div>
    <div class="card">
      <h3>🖼️ Multimodal & Representation Learning</h3>
      <div class="topic-grid">
        <span class="pill rose">CLIP</span><span class="pill rose">Flamingo</span><span class="pill rose">BLIP</span><span class="pill rose">SimCLR / MoCo</span><span class="pill rose">BYOL</span><span class="pill rose">MAE</span><span class="pill rose">DINO</span><span class="pill rose">Contrastive Learning</span>
      </div>
    </div>
    <div class="card">
      <h3>🔬 Mechanistic Interpretability</h3>
      <div class="topic-grid">
        <span class="pill rose">Sparse Autoencoders (SAEs)</span><span class="pill rose">Circuit Analysis</span><span class="pill rose">Activation Patching</span><span class="pill rose">Causal Tracing</span><span class="pill rose">Feature Visualization</span><span class="pill rose">Superposition</span>
      </div>
    </div>
  </div>

  <div class="section-label mt32">Mindset & Thinking Framework</div>
  <div class="mindset-box mt16">
    <div class="mq">You are no longer a student. You are a scientist. Formulate a hypothesis before every experiment.</div>
    <p>At this level, the shift is from "implementing papers" to "identifying gaps in papers." Before running any experiment, write down your hypothesis and the null hypothesis. When an experiment fails (and 90% do), treat the failure as a data point, not a setback. Top labs explicitly look for intellectual honesty — the ability to "discuss the limitations of your best paper without becoming defensive." Start subscribing to arXiv alerts for your subfield and reading new papers daily, focusing on weaknesses and what is interesting, not just results.</p>
  </div>

  <div class="section-label mt32">Performance Expectations</div>
  <div class="expect-grid mt16">
    <div class="expect-item"><div class="expect-label">Research Output</div><p>Working toward first-author publications; able to drive a project from hypothesis to result</p></div>
    <div class="expect-item"><div class="expect-label">Depth</div><p>Deep enough in your chosen domain to identify limitations in recent top-conference papers</p></div>
    <div class="expect-item"><div class="expect-label">Safety Fluency</div><p>For Anthropic: explain Constitutional AI and its limitations with genuine engagement</p></div>
    <div class="expect-item"><div class="expect-label">Collaboration</div><p>Shared repos, reproducible setups, good issue tracking, and code others can extend</p></div>
  </div>

  <div class="section-label mt32">Project Ideas</div>
  <div class="grid-2 mt16">
    <div class="project-card">
      <div class="proj-title">PPO from Scratch → Atari</div>
      <p>Implement Proximal Policy Optimization from the original paper. Train on CartPole, then scale to Atari games. Analyze sample efficiency vs DQN. Document hyperparameter sensitivity.</p>
      <div class="proj-meta"><span class="proj-tag">Atari / Gym</span><span class="proj-tag">Sample Efficiency</span><span class="proj-tag">Reward Curves</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">CLIP Reproduction</div>
      <p>Reproduce CLIP's contrastive image-text training on a smaller dataset. Evaluate zero-shot classification and image-text retrieval. Analyze which types of captions improve alignment.</p>
      <div class="proj-meta"><span class="proj-tag">MSCOCO</span><span class="proj-tag">Recall@K</span><span class="proj-tag">Zero-shot Accuracy</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Sparse Autoencoder for LLM Interpretability</div>
      <p>Train sparse autoencoders on Llama activations to identify interpretable features. Use activation patching to verify that specific features causally influence model outputs. Document what circuits emerge.</p>
      <div class="proj-meta"><span class="proj-tag">Llama / GPT-2</span><span class="proj-tag">Feature Recovery</span><span class="proj-tag">Causal Effect</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">RLHF Pipeline on Toy LM</div>
      <p>Implement an end-to-end RLHF pipeline: SFT → reward model training → PPO fine-tuning. Use synthetic or crowd-sourced preference data. Compare to DPO on the same preference dataset.</p>
      <div class="proj-meta"><span class="proj-tag">Synthetic Preferences</span><span class="proj-tag">Win Rate</span><span class="proj-tag">KL Divergence</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Diffusion Model with Ablations (CelebA)</div>
      <p>Train a full DDPM on CelebA. Ablate noise schedules (linear vs cosine), loss parameterizations (ε vs x₀), and sampling methods (DDPM vs DDIM). Measure FID for each variant.</p>
      <div class="proj-meta"><span class="proj-tag">CelebA</span><span class="proj-tag">FID</span><span class="proj-tag">Sampling Speed</span></div>
    </div>
  </div>

  <div class="section-label mt32">Papers to Read</div>
  <div class="card mt16">
    <div class="paper-item"><div class="paper-num">01</div><div class="paper-body"><div class="paper-title">Training Language Models to Follow Instructions with Human Feedback — InstructGPT (Ouyang et al., 2022)</div><div class="paper-why">Core RLHF paper — the methodology behind how modern LLMs are aligned with human preferences</div></div></div>
    <div class="paper-item"><div class="paper-num">02</div><div class="paper-body"><div class="paper-title">Direct Preference Optimization (Rafailov et al., 2023)</div><div class="paper-why">Simpler alternative to RLHF — understanding this is essential for any post-training role</div></div></div>
    <div class="paper-item"><div class="paper-num">03</div><div class="paper-body"><div class="paper-title">Constitutional AI (Anthropic, 2022)</div><div class="paper-why">Core paper for Anthropic's alignment approach — must understand deeply if applying to Anthropic</div></div></div>
    <div class="paper-item"><div class="paper-num">04</div><div class="paper-body"><div class="paper-title">DQN — Playing Atari with Deep RL (Mnih et al., 2015)</div><div class="paper-why">Foundational deep RL paper — the bridge between deep learning and reinforcement learning</div></div></div>
    <div class="paper-item"><div class="paper-num">05</div><div class="paper-body"><div class="paper-title">PPO — Proximal Policy Optimization (Schulman et al., 2017)</div><div class="paper-why">The workhorse RL algorithm — used in RLHF, robotic control, and game playing</div></div></div>
    <div class="paper-item"><div class="paper-num">06</div><div class="paper-body"><div class="paper-title">CLIP (Radford et al., 2021)</div><div class="paper-why">Landmark multimodal paper — contrastive training at scale enables powerful zero-shot transfer</div></div></div>
    <div class="paper-item"><div class="paper-num">07</div><div class="paper-body"><div class="paper-title">Masked Autoencoders (MAE) (He et al., 2021)</div><div class="paper-why">Self-supervised vision pretraining — scalable and surprisingly effective</div></div></div>
    <div class="paper-item"><div class="paper-num">08</div><div class="paper-body"><div class="paper-title">MuZero (Schrittwieser et al., 2020)</div><div class="paper-why">World models + planning — learn to master environments without knowing their rules</div></div></div>
    <div class="paper-item"><div class="paper-num">09</div><div class="paper-body"><div class="paper-title">AlphaFold 2 (Jumper et al., 2021)</div><div class="paper-why">Landmark scientific ML paper — Nobel Prize-winning work showing what AI can do for science</div></div></div>
  </div>

  <div class="section-label mt32">Practical Advice</div>
  <div class="advice-grid mt16">
    <div class="advice-item"><strong>Choose a domain identity.</strong>Depth matters more than breadth at this phase. Pick interpretability, RL, or multimodal and become known for it.</div>
    <div class="advice-item"><strong>Lab-specific preparation starts here.</strong>Anthropic emphasizes safety. OpenAI emphasizes shipping. DeepMind expects PhD-defense-level scientific rigor. Tailor accordingly.</div>
    <div class="advice-item"><strong>Read papers actively.</strong>Abstract → Figures → Methods → Experiments → Appendix. Reimplement the key idea. Only then read related work.</div>
    <div class="advice-item"><strong>Warm introductions matter far more than cold applications.</strong>Build relationships with researchers at target labs through conferences, GitHub, and Twitter/X engagement.</div>
  </div>
</div>
</section>

<!-- ═══════════════════════════════════════════
     PHASE 5
═══════════════════════════════════════════ -->
<section class="phase-section ph5" id="phase5">
<div class="container">
  <div class="phase-header">
    <div class="phase-badge">P5</div>
    <div class="phase-header-text">
      <h2>Specialization & Publication</h2>
      <div class="timeline">⏱ Months 38–52 · First-author publications stage</div>
      <p class="phase-goal">Go deep in one subfield. Identify gaps, formulate original hypotheses, run rigorous experiments, and publish. This is where research identity forms and hiring signals become decisive.</p>
    </div>
  </div>

  <div class="section-label">Choose Your Research Track</div>
  <div class="grid-3 mt16">
    <div class="card">
      <h3>🧠 LLMs & Post-Training</h3>
      <ul class="bullet-list mt8">
        <li>RLHF, DPO, KTO, GRPO</li>
        <li>Reasoning & chain-of-thought</li>
        <li>Tool use & agents</li>
        <li>Long context & memory</li>
        <li>Hallucination reduction</li>
      </ul>
    </div>
    <div class="card">
      <h3>🔍 Interpretability & Alignment</h3>
      <ul class="bullet-list mt8">
        <li>Mechanistic interpretability</li>
        <li>Scalable oversight</li>
        <li>Constitutional AI variants</li>
        <li>Representation probing</li>
        <li>Circuit discovery</li>
      </ul>
    </div>
    <div class="card">
      <h3>🤖 RL & Reasoning</h3>
      <ul class="bullet-list mt8">
        <li>World models (DreamerV3)</li>
        <li>RLVR for math reasoning</li>
        <li>Inference-time compute</li>
        <li>Planning & search</li>
        <li>Reward shaping</li>
      </ul>
    </div>
    <div class="card">
      <h3>🖼️ Multimodal & Vision</h3>
      <ul class="bullet-list mt8">
        <li>Video understanding</li>
        <li>Vision-language-action models</li>
        <li>Robotic manipulation</li>
        <li>3D scene understanding</li>
        <li>Cross-modal alignment</li>
      </ul>
    </div>
    <div class="card">
      <h3>⚡ Efficient AI</h3>
      <ul class="bullet-list mt8">
        <li>Quantization (AWQ, GPTQ)</li>
        <li>Speculative decoding</li>
        <li>Sparse MoE models</li>
        <li>Distillation techniques</li>
        <li>vLLM / PagedAttention</li>
      </ul>
    </div>
    <div class="card">
      <h3>🔬 Scientific ML</h3>
      <ul class="bullet-list mt8">
        <li>Protein structure prediction</li>
        <li>Physics-informed NNs</li>
        <li>Materials discovery</li>
        <li>Genomics & biology</li>
        <li>Graph neural networks</li>
      </ul>
    </div>
  </div>

  <div class="section-label mt32">Mindset & Thinking Framework</div>
  <div class="mindset-box mt16">
    <div class="mq">Start thinking like a paper author: identify a gap, a hypothesis, and a measurable contribution.</div>
    <p>The research workflow is: Read 100 papers → Reproduce 20 → Find limitations in 5 → Form hypotheses → Run ablations → Write. Negative results with honest limitations are publishable and respected — they save others from dead ends. Aim for high-quality contributions that survive adversarial scrutiny, not exciting but vague results. Every experiment should be able to answer: what would falsify this hypothesis? Publish when the result is clear, reproducible, and useful.</p>
  </div>

  <div class="section-label mt32">Performance Expectations</div>
  <div class="expect-grid mt16">
    <div class="expect-item"><div class="expect-label">Publications</div><p>3+ first-author papers at NeurIPS, ICML, ICLR, CVPR, or ACL — "table stakes" for DeepMind RS</p></div>
    <div class="expect-item"><div class="expect-label">Originality</div><p>Original ideas you can defend under adversarial questioning — not reproductions</p></div>
    <div class="expect-item"><div class="expect-label">Research Vision</div><p>Coherent 3-year research agenda that builds on prior work and aligns with a lab's mission</p></div>
    <div class="expect-item"><div class="expect-label">Writing</div><p>Clear, precise scientific writing — research impact depends entirely on being understood</p></div>
  </div>

  <div class="section-label mt32">Project Ideas</div>
  <div class="grid-2 mt16">
    <div class="project-card">
      <div class="proj-title">Novel Post-Training Algorithm</div>
      <p>Design a new post-training algorithm improving on RLHF/DPO for a specific failure mode (e.g., multi-step reasoning, hallucination, or refusal accuracy). Run ablations against DPO and KTO baselines.</p>
      <div class="proj-meta"><span class="proj-tag">Preference Datasets</span><span class="proj-tag">Win Rate</span><span class="proj-tag">AlpacaEval</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Mechanistic Interpretability: Circuit Discovery</div>
      <p>Reverse-engineer a specific capability in a small LLM (e.g., arithmetic, indirect object identification). Use activation patching and path patching to identify and verify the circuit. Submit to an interpretability workshop.</p>
      <div class="proj-meta"><span class="proj-tag">GPT-2 Small</span><span class="proj-tag">Causal Effect Size</span><span class="proj-tag">TransformerLens</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Evaluation Benchmark for Reasoning</div>
      <p>Design a benchmark that tests multi-step reasoning reliability while being robust to contamination. Verify with difficulty scaling, held-out test set, and human verification. Publish with full reproducibility.</p>
      <div class="proj-meta"><span class="proj-tag">Custom Dataset</span><span class="proj-tag">Human Agreement</span><span class="proj-tag">Contamination Analysis</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Reproduce + Improve a Top-Conference Paper</div>
      <p>Pick a recent NeurIPS/ICML paper, reproduce its main result exactly, identify one limitation through ablation analysis, then design and run an experiment that addresses it. Write this up as a submission.</p>
      <div class="proj-meta"><span class="proj-tag">Open Reproducibility</span><span class="proj-tag">Delta vs Baseline</span><span class="proj-tag">Ablation Study</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Scalable Oversight Experiment</div>
      <p>Design and run an experiment testing scalable oversight: use a strong model to supervise a weak model on tasks the supervisor cannot easily verify. Measure how supervision quality degrades with difficulty.</p>
      <div class="proj-meta"><span class="proj-tag">Custom Eval</span><span class="proj-tag">Accuracy vs Difficulty</span><span class="proj-tag">Safety Metrics</span></div>
    </div>
  </div>

  <div class="section-label mt32">Key Papers for Your Specialization</div>
  <div class="card mt16">
    <div class="paper-item"><div class="paper-num">01</div><div class="paper-body"><div class="paper-title">Constitutional AI: Harmlessness from AI Feedback (Anthropic, 2022)</div><div class="paper-why">The approach behind Claude's alignment — study the RLHF-from-AI-feedback mechanism carefully</div></div></div>
    <div class="paper-item"><div class="paper-num">02</div><div class="paper-body"><div class="paper-title">Chain-of-Thought Prompting Elicits Reasoning (Wei et al., 2022)</div><div class="paper-why">The paper that popularized reasoning chains — understand why step-by-step reasoning improves accuracy</div></div></div>
    <div class="paper-item"><div class="paper-num">03</div><div class="paper-body"><div class="paper-title">Toolformer (Schick et al., 2023)</div><div class="paper-why">How LLMs can teach themselves to use tools via self-supervised learning — essential for agent research</div></div></div>
    <div class="paper-item"><div class="paper-num">04</div><div class="paper-body"><div class="paper-title">Sparks of Artificial General Intelligence (Bubeck et al., 2023)</div><div class="paper-why">Broad capability analysis of GPT-4 — important for understanding where capability claims are supported vs speculative</div></div></div>
    <div class="paper-item"><div class="paper-num">05</div><div class="paper-body"><div class="paper-title">Segment Anything (Kirillov et al., 2023)</div><div class="paper-why">Foundation model approach applied to vision segmentation — study the prompting paradigm</div></div></div>
    <div class="paper-item"><div class="paper-num">06</div><div class="paper-body"><div class="paper-title">Flamingo (Alayrac et al., 2022)</div><div class="paper-why">Multimodal few-shot learning at scale — the architectural approach used in Gemini-style models</div></div></div>
    <div class="paper-item"><div class="paper-num">07</div><div class="paper-body"><div class="paper-title">NeurIPS / ICML / ICLR best-paper shortlist (current year)</div><div class="paper-why">Read the top papers from the most recent year in your specialization — stay current with the frontier</div></div></div>
  </div>

  <div class="section-label mt32">Practical Advice</div>
  <div class="advice-grid mt16">
    <div class="advice-item"><strong>Depth over breadth.</strong>Focus on one research identity that becomes recognizable. A specialist known for interpretability beats a generalist who touches everything.</div>
    <div class="advice-item"><strong>Consider MATS Fellowship.</strong>The ML Alignment Theory Scholars program is a strategic stepping stone, especially for Anthropic-focused candidates.</div>
    <div class="advice-item"><strong>Build a research portfolio website.</strong>Summarize your papers, projects, and research vision in a compelling narrative. Researchers at labs will Google you.</div>
    <div class="advice-item"><strong>Open-source contributions signal capability.</strong>Major contributions to PyTorch, Hugging Face, vLLM, or llama.cpp are powerful hiring signals that require no publication lag.</div>
  </div>
</div>
</section>

<!-- ═══════════════════════════════════════════
     PHASE 6
═══════════════════════════════════════════ -->
<section class="phase-section ph6" id="phase6">
<div class="container">
  <div class="phase-header">
    <div class="phase-badge">P6</div>
    <div class="phase-header-text">
      <h2>Top-Lab Readiness & Interview Preparation</h2>
      <div class="timeline">⏱ Final 3–6 months · Target: OpenAI, DeepMind, Anthropic, Meta AI</div>
      <p class="phase-goal">The gap between academic excellence and a lab offer is about how you present yourself. Most rejections come not from lack of skill, but from preparing for the wrong interview.</p>
    </div>
  </div>

  <div class="section-label">Lab-Specific Preparation</div>
  <div class="hiring-grid mt16">
    <div class="hiring-card">
      <div class="lab-name">🔵 Anthropic</div>
      <ul class="bullet-list">
        <li><strong>Safety is the gatekeeper round.</strong> Explain Constitutional AI, scalable oversight, and RLHF limitations in depth.</li>
        <li><strong>CodeSignal 520+/600.</strong> System design coding problem — architecture-first, not LeetCode.</li>
        <li><strong>Mechanistic interpretability</strong> is a core pillar — have a genuine project to discuss.</li>
        <li>Apply to the general RS pool then team-match. PhD is required for 90%+ of hires.</li>
      </ul>
    </div>
    <div class="hiring-card">
      <div class="lab-name">🟢 OpenAI</div>
      <ul class="bullet-list">
        <li><strong>Paper discussion round.</strong> A paper is sent in advance — prepare a detailed critique, not a summary.</li>
        <li>Emphasizes <strong>shipping fast</strong> and AGI focus. Show evidence of driving projects to completion.</li>
        <li>Most <strong>flexible on PhD requirement</strong> — strong publication record or shipped products can substitute.</li>
        <li>Surprisingly coding-intensive for RS roles — practice implementation under time pressure.</li>
      </ul>
    </div>
    <div class="hiring-card">
      <div class="lab-name">🔴 Google DeepMind</div>
      <ul class="bullet-list">
        <li><strong>PhD defense-level scientific depth.</strong> Rapid-fire math quiz is standard — re-derive algorithms on the spot.</li>
        <li>Emphasizes <strong>research taste</strong> and mathematical rigor above all else.</li>
        <li>Hiring committee weighs <strong>"Googleyness" and leadership</strong> — collaboration and mentoring matter.</li>
        <li>Fully liquid GOOG equity is a major financial advantage versus private company stock.</li>
      </ul>
    </div>
  </div>

  <div class="section-label mt32">Interview Preparation Framework</div>
  <div class="grid-2 mt16">
    <div class="card">
      <h3>📋 Four Interview Dimensions</h3>
      <ul class="bullet-list mt8">
        <li><strong>Coding:</strong> Fast, clean Python; PyTorch implementation of ML primitives from memory; system design</li>
        <li><strong>ML Theory:</strong> Derive algorithms; explain architectures; discuss training dynamics</li>
        <li><strong>Research Discussion:</strong> Critique a paper; propose an experiment; defend your publications</li>
        <li><strong>Project Defense:</strong> 30-second, 3-minute, and 30-minute versions of your research ready</li>
      </ul>
    </div>
    <div class="card">
      <h3>🎯 Research Talk Strategy</h3>
      <ul class="bullet-list mt8">
        <li>Your research talk is not a conference presentation — it demonstrates <strong>research taste</strong></li>
        <li>Open with problem importance, not technical complexity</li>
        <li>Show you can <strong>scope projects</strong> and drive them to measurable completion</li>
        <li>Prepare honest limitations — interviewers test intellectual honesty deliberately</li>
        <li>End with a clear research vision, not just past contributions</li>
      </ul>
    </div>
  </div>

  <div class="section-label mt32">Systems & Scale Topics</div>
  <div class="card mt16">
    <div class="topic-grid">
      <span class="pill">3D Parallelism</span><span class="pill">Pipeline Parallelism</span><span class="pill">Tensor Parallelism</span><span class="pill">ZeRO Optimization</span><span class="pill">vLLM / PagedAttention</span><span class="pill">Quantization (GPTQ, AWQ)</span><span class="pill">Speculative Decoding</span><span class="pill">Distillation</span><span class="pill">Pruning</span><span class="pill">Benchmark Design</span><span class="pill">Contamination Testing</span><span class="pill">Adversarial Robustness</span><span class="pill">Responsible AI</span><span class="pill">Privacy-Preserving ML</span>
    </div>
  </div>

  <div class="section-label mt32">Final Projects</div>
  <div class="grid-2 mt16">
    <div class="project-card">
      <div class="proj-title">Submit a Workshop or Conference Paper</div>
      <p>Write and submit a full paper with reproducibility artifacts, clean code, and results tables. Treat the camera-ready submission as the minimum bar — not the submission itself.</p>
      <div class="proj-meta"><span class="proj-tag">NeurIPS / ICML / ICLR</span><span class="proj-tag">Open-source Code</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Benchmark Suite for Contamination & Memorization</div>
      <p>Build a suite that tests whether model gains are from memorization vs. generalization. Useful for the field and demonstrates evaluation science maturity.</p>
      <div class="proj-meta"><span class="proj-tag">Custom Dataset</span><span class="proj-tag">Membership Inference</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Reproduce a Recent Model with Smaller Budget</div>
      <p>Reproduce a recent frontier model release at a fraction of the compute cost. Provide a rigorous comparison and analyze where performance degrades. This demonstrates both systems knowledge and research rigor.</p>
      <div class="proj-meta"><span class="proj-tag">Open Weights Model</span><span class="proj-tag">Compute Budget</span></div>
    </div>
    <div class="project-card">
      <div class="proj-title">Throughput Optimization Analysis</div>
      <p>Profile a real model training run and identify where compute is spent. Optimize throughput using FlashAttention, torch.compile, and data pipeline improvements. Report before/after numbers.</p>
      <div class="proj-meta"><span class="proj-tag">tokens/sec</span><span class="proj-tag">GPU Utilization</span><span class="proj-tag">Profiler Trace</span></div>
    </div>
  </div>

  <div class="section-label mt32">Final Papers to Read</div>
  <div class="card mt16">
    <div class="paper-item"><div class="paper-num">01</div><div class="paper-body"><div class="paper-title">On the Opportunities and Risks of Foundation Models (Bommasani et al., 2021)</div><div class="paper-why">Broad framing of capabilities, risks, and research gaps — good for articulating research vision in interviews</div></div></div>
    <div class="paper-item"><div class="paper-num">02</div><div class="paper-body"><div class="paper-title">Technical Reports from DeepMind, OpenAI, Anthropic, Meta AI (current year)</div><div class="paper-why">Know the current frontier. Read Gemini, Claude, GPT, and Llama technical reports in full — interviewers assume you have</div></div></div>
    <div class="paper-item"><div class="paper-num">03</div><div class="paper-body"><div class="paper-title">Direct Preference Optimization (Rafailov et al., 2023)</div><div class="paper-why">The current standard for post-training alignment — understand the reward model connection deeply</div></div></div>
    <div class="paper-item"><div class="paper-num">04</div><div class="paper-body"><div class="paper-title">Mastering the Game of Go without Human Knowledge — AlphaGo Zero (Silver et al., 2017)</div><div class="paper-why">A showcase of first-principles innovation in RL — know this paper well for DeepMind interviews</div></div></div>
    <div class="paper-item"><div class="paper-num">05</div><div class="paper-body"><div class="paper-title">Chain-of-Thought Prompting (Wei et al., 2022)</div><div class="paper-why">Cited constantly in inference-time compute and reasoning research — know the evidence and its limits</div></div></div>
  </div>

  <div class="section-label mt32">Practical Advice</div>
  <div class="advice-grid mt16">
    <div class="advice-item"><strong>Use the 70/20/10 rule.</strong>70% deep work on core skills and research, 20% reproduction and paper reading, 10% networking and public visibility.</div>
    <div class="advice-item"><strong>Don't reveal salary expectations early.</strong>Understand the equity structures (RSUs vs. options). Fully liquid GOOG equity at DeepMind is a significant financial advantage.</div>
    <div class="advice-item"><strong>Prepare three versions of your research narrative.</strong>30 seconds (elevator), 3 minutes (recruiter screen), 30 minutes (research talk). Practice all three until they're effortless.</div>
    <div class="advice-item"><strong>Your GitHub is your real resume.</strong>Clean READMEs, reproducibility instructions, results tables, and clear commit history are what researchers actually check.</div>
  </div>
</div>
</section>

<!-- FORMULA BLOCK -->
<section style="padding: 40px 0 0; border-bottom: 1px solid var(--border);">
<div class="container">
  <div class="formula-block">
    <h3>The World-Class Researcher Profile</h3>
    <div class="formula-items">
      <div class="formula-item">Strong Software Engineer</div>
      <div class="formula-plus">+</div>
      <div class="formula-item">Mathematical Depth</div>
      <div class="formula-plus">+</div>
      <div class="formula-item">PyTorch Systems Expert</div>
      <div class="formula-plus">+</div>
      <div class="formula-item">Experimental Scientist</div>
      <div class="formula-plus">+</div>
      <div class="formula-item">Voracious Paper Reader</div>
      <div class="formula-plus">+</div>
      <div class="formula-item">Open Source Contributor</div>
      <div class="formula-plus">+</div>
      <div class="formula-item">Research Publications</div>
      <div class="formula-plus">+</div>
      <div class="formula-item">Original Ideas</div>
      <div class="formula-equals">=</div>
      <div class="formula-result">Frontier AI Researcher</div>
    </div>
  </div>

  <div class="section-label">Universal Practical Advice</div>
  <div class="advice-grid mt16" style="margin-bottom: 48px;">
    <div class="advice-item"><strong>One paper → one implementation → one write-up → one improvement.</strong>The tightest learning loop that compounds fastest.</div>
    <div class="advice-item"><strong>Build one strong portfolio project per phase</strong> rather than many shallow demos. Depth over breadth — always.</div>
    <div class="advice-item"><strong>Keep a public GitHub from Day 1.</strong>Clean READMEs, reproducibility instructions, and results tables. Treat it as a live CV.</div>
    <div class="advice-item"><strong>Join reading groups, Discord communities, and virtual seminars.</strong>Research careers are built on intellectual relationships as much as publications.</div>
    <div class="advice-item"><strong>The goal is not to know every model.</strong>It is to become someone who can create, test, and explain new ones credibly.</div>
    <div class="advice-item"><strong>Spend most of your time one level above your comfort zone.</strong>One foot in implementation, one foot in papers — always stretching forward.</div>
  </div>
</div>
</section>

<footer>
  <div class="container">
    Compiled from leading AI career resources and researcher insights &nbsp;·&nbsp; <span>Targeting OpenAI · Google DeepMind · Anthropic · Meta AI · Google Brain</span>
  </div>
</footer>

<script>
  // Smooth scroll behavior
  document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
      e.preventDefault();
      const target = document.querySelector(this.getAttribute('href'));
      if (target) {
        target.scrollIntoView({ behavior: 'smooth', block: 'start' });
      }
    });
  });

  // Active nav highlighting
  const sections = document.querySelectorAll('.phase-section');
  const navLinks = document.querySelectorAll('.phase-nav a');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        navLinks.forEach(link => link.classList.remove('active'));
        const activeLink = document.querySelector(`.phase-nav a[href="#${entry.target.id}"]`);
        if (activeLink) activeLink.classList.add('active');
      }
    });
  }, { threshold: 0.3 });
  sections.forEach(s => observer.observe(s));
</script>
</body>
</html>
```