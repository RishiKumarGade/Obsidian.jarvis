<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Complete AI Researcher Guide</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Space+Grotesk:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;font-size:15px}
body{font-family:'Inter',sans-serif;background:#09090f;color:#d8d8e8;line-height:1.75}
:root{
  --bg:#09090f;--bg2:#0e0e16;--surf:#12121c;--surf2:#171726;--surf3:#1c1c2e;
  --b1:#232336;--b2:#2c2c48;--text:#d8d8e8;--muted:#8080a0;--dim:#404060;
  --v:#6c63f5;--g:#05c49b;--b:#38b6f8;--a:#f0a000;--r:#f04060;--p:#9b6cf0;
  --font-mono:'JetBrains Mono',monospace;--font-disp:'Space Grotesk',sans-serif;
}
.wrap{max-width:1080px;margin:0 auto;padding:0 28px}

/* HERO */
.hero{position:relative;overflow:hidden;padding:90px 28px 68px;text-align:center;border-bottom:1px solid var(--b1)}
.hero-bg{position:absolute;inset:0;pointer-events:none;
  background:radial-gradient(ellipse 900px 500px at 50% -80px,rgba(108,99,245,.2) 0%,transparent 65%),
  radial-gradient(ellipse 500px 400px at 10% 110%,rgba(5,196,155,.08) 0%,transparent 55%),
  radial-gradient(ellipse 400px 350px at 90% 110%,rgba(240,160,0,.07) 0%,transparent 55%)}
.eyebrow{font-family:var(--font-mono);font-size:11px;letter-spacing:.2em;text-transform:uppercase;color:var(--v);opacity:.85;margin-bottom:20px}
.hero h1{font-family:var(--font-disp);font-size:clamp(34px,5.5vw,60px);font-weight:700;letter-spacing:-.03em;line-height:1.08;color:#fff;margin-bottom:20px}
.hero h1 em{font-style:normal;color:var(--v)}
.hero-sub{font-size:16.5px;color:var(--muted);max-width:620px;margin:0 auto 36px;line-height:1.65}
.hero-note{display:inline-block;background:rgba(108,99,245,.1);border:1px solid rgba(108,99,245,.3);border-radius:12px;padding:14px 22px;font-size:13.5px;color:#b0aaff;line-height:1.6;max-width:580px}
.hero-note strong{color:#d0ccff}

/* NAV */
.snav{position:sticky;top:0;z-index:200;background:rgba(9,9,15,.93);backdrop-filter:blur(16px);border-bottom:1px solid var(--b1)}
.snav-inner{display:flex;overflow-x:auto;padding:0 28px;max-width:1080px;margin:0 auto;scrollbar-width:none;gap:0}
.snav-inner::-webkit-scrollbar{display:none}
.nl{display:flex;align-items:center;gap:7px;padding:0 14px;height:48px;white-space:nowrap;font-size:12px;font-weight:500;color:var(--muted);text-decoration:none;border-bottom:2px solid transparent;transition:color .15s,border-color .15s;flex-shrink:0}
.nl:hover{color:var(--text)}.nl.nv:hover,.nl.nv.active{color:var(--v);border-color:var(--v)}
.nl.ng:hover,.nl.ng.active{color:var(--g);border-color:var(--g)}.nl.nb:hover,.nl.nb.active{color:var(--b);border-color:var(--b)}
.nl.na:hover,.nl.na.active{color:var(--a);border-color:var(--a)}.nl.nr:hover,.nl.nr.active{color:var(--r);border-color:var(--r)}
.nl.np:hover,.nl.np.active{color:var(--p);border-color:var(--p)}.nl.nm:hover,.nl.nm.active{color:#aaa;border-color:#aaa}
.ndot{width:6px;height:6px;border-radius:50%;flex-shrink:0}

/* PHASE SECTIONS */
.ps{padding:76px 0 56px;border-bottom:1px solid var(--b1)}
.ph{display:flex;align-items:flex-start;gap:20px;margin-bottom:48px}
.pnum{flex-shrink:0;width:56px;height:56px;border-radius:14px;display:flex;align-items:center;justify-content:center;font-family:var(--font-mono);font-size:12px;font-weight:500;border:1px solid}
.p0 .pnum{background:rgba(108,99,245,.1);color:var(--v);border-color:rgba(108,99,245,.3)}
.p1 .pnum{background:rgba(5,196,155,.1);color:var(--g);border-color:rgba(5,196,155,.3)}
.p2 .pnum{background:rgba(56,182,248,.1);color:var(--b);border-color:rgba(56,182,248,.3)}
.p3 .pnum{background:rgba(240,160,0,.1);color:var(--a);border-color:rgba(240,160,0,.3)}
.p4 .pnum{background:rgba(240,64,96,.1);color:var(--r);border-color:rgba(240,64,96,.3)}
.p5 .pnum{background:rgba(155,108,240,.1);color:var(--p);border-color:rgba(155,108,240,.3)}
.ph h2{font-family:var(--font-disp);font-size:28px;font-weight:700;letter-spacing:-.022em;color:#fff;line-height:1.15}
.ptl{font-family:var(--font-mono);font-size:11px;color:var(--muted);margin-top:6px;letter-spacing:.02em}
.ptag{font-size:15px;color:var(--muted);margin-top:9px;max-width:700px;line-height:1.6}

/* SECTION LABEL */
.sl{font-family:var(--font-mono);font-size:10px;letter-spacing:.16em;text-transform:uppercase;color:var(--dim);margin-bottom:14px;display:flex;align-items:center;gap:10px}
.sl::after{content:'';flex:1;height:1px;background:var(--b1)}

/* MINDSET PULL */
.mpull{background:var(--surf2);border:1px solid var(--b2);border-radius:12px;padding:22px 26px;margin-bottom:22px}
.mpull .mq{font-family:var(--font-disp);font-size:18px;font-weight:600;color:#fff;line-height:1.4;margin-bottom:12px}
.mpull .mq::before{content:'"';color:var(--v);margin-right:2px}
.mpull .mq::after{content:'"';color:var(--v);margin-left:2px}
.mpull p{font-size:13.5px;color:var(--muted);line-height:1.7;margin-top:8px}
.mpull p strong{color:var(--text);font-weight:500}

/* GRID */
.g2{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.g3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:13px}
.g4{display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:12px}
@media(max-width:760px){.g2,.g3,.g4{grid-template-columns:1fr}}

/* CARD */
.card{background:var(--surf);border:1px solid var(--b1);border-radius:14px;padding:20px}
.card h3{font-family:var(--font-disp);font-size:13.5px;font-weight:600;color:#fff;margin-bottom:13px;display:flex;align-items:center;gap:7px}
.card p{font-size:13px;color:var(--muted);line-height:1.65}

/* PILLS */
.pw{display:flex;flex-wrap:wrap;gap:7px}
.pill{font-family:var(--font-mono);font-size:11.5px;padding:3px 9px;border-radius:20px;border:1px solid var(--b2);color:var(--muted);background:var(--surf2)}
.pill.v{border-color:rgba(108,99,245,.4);color:#b0a8ff;background:rgba(108,99,245,.07)}
.pill.g{border-color:rgba(5,196,155,.4);color:#5adfc5;background:rgba(5,196,155,.07)}
.pill.b{border-color:rgba(56,182,248,.4);color:#7ad4f8;background:rgba(56,182,248,.07)}
.pill.a{border-color:rgba(240,160,0,.4);color:#f5c842;background:rgba(240,160,0,.07)}
.pill.r{border-color:rgba(240,64,96,.4);color:#f47895;background:rgba(240,64,96,.07)}
.pill.p{border-color:rgba(155,108,240,.4);color:#c095f8;background:rgba(155,108,240,.07)}

/* DEPTH BLOCKS */
.drow{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:14px}
.di{flex:1;min-width:175px;border-radius:10px;padding:14px 15px;font-size:13px;line-height:1.55}
.di .dl{font-family:var(--font-mono);font-size:9.5px;letter-spacing:.12em;text-transform:uppercase;font-weight:600;margin-bottom:8px;display:block}
.di ul{list-style:none}.di ul li{padding:2px 0 2px 12px;position:relative;color:inherit;font-size:12.5px}
.di ul li::before{content:'→';position:absolute;left:0;font-size:9px;top:4px;opacity:.55}
.dm{background:rgba(108,99,245,.07);border:1px solid rgba(108,99,245,.22);color:#b8b4e8}.dm .dl{color:var(--v)}
.do{background:rgba(5,196,155,.06);border:1px solid rgba(5,196,155,.18);color:#a0d8cc}.do .dl{color:var(--g)}
.ds{background:var(--surf);border:1px solid var(--b1);color:var(--dim)}.ds .dl{color:var(--dim)}

/* PROJECT CARDS */
.pc{background:var(--surf2);border:1px solid var(--b1);border-radius:12px;padding:19px 21px;margin-bottom:11px;position:relative;overflow:hidden}
.pc::before{content:'';position:absolute;left:0;top:0;bottom:0;width:3px}
.p0 .pc::before{background:var(--v)}.p1 .pc::before{background:var(--g)}.p2 .pc::before{background:var(--b)}
.p3 .pc::before{background:var(--a)}.p4 .pc::before{background:var(--r)}.p5 .pc::before{background:var(--p)}
.pc-top{display:flex;justify-content:space-between;align-items:flex-start;gap:12px;margin-bottom:8px}
.pc .pti{font-family:var(--font-disp);font-size:14.5px;font-weight:600;color:#fff;flex:1}
.badge{font-family:var(--font-mono);font-size:10px;letter-spacing:.05em;text-transform:uppercase;padding:3px 8px;border-radius:20px;white-space:nowrap;font-weight:500;flex-shrink:0}
.bd{background:rgba(240,64,96,.13);color:#f47895;border:1px solid rgba(240,64,96,.28)}
.bm{background:rgba(240,160,0,.1);color:#f5c842;border:1px solid rgba(240,160,0,.25)}
.bl{background:rgba(5,196,155,.1);color:#5adfc5;border:1px solid rgba(5,196,155,.25)}
.pc p{font-size:13px;color:var(--muted);line-height:1.65;margin-bottom:10px}
.pc p strong{color:var(--text);font-weight:500}
.pm{display:flex;flex-wrap:wrap;gap:6px}
.mt{font-family:var(--font-mono);font-size:10.5px;padding:2px 8px;border-radius:4px;border:1px solid var(--b1);color:var(--dim);background:var(--surf)}
.why{background:var(--surf);border-radius:7px;padding:9px 12px;margin:8px 0;font-size:12.5px;color:var(--muted);line-height:1.55;border-left:2px solid var(--b2)}
.why strong{color:#a0a0c0;font-weight:500}

/* PAPERS */
.pbox{background:var(--surf);border:1px solid var(--b1);border-radius:12px;overflow:hidden}
.pr{display:grid;grid-template-columns:26px 1fr auto;gap:12px;padding:15px 18px;border-bottom:1px solid var(--b1);transition:background .12s;align-items:start}
.pr:last-child{border-bottom:none}.pr:hover{background:var(--surf2)}
.pn{font-family:var(--font-mono);font-size:10.5px;color:var(--dim);padding-top:2px}
.pb .pt{font-size:13.5px;font-weight:500;color:var(--text);line-height:1.4}
.pb .pa{font-size:11px;color:var(--dim);margin:3px 0 5px;font-family:var(--font-mono)}
.pb .pw2{font-size:12.5px;color:var(--muted);line-height:1.5}
.pd{font-family:var(--font-mono);font-size:9.5px;letter-spacing:.04em;text-transform:uppercase;padding:3px 7px;border-radius:4px;white-space:nowrap;align-self:flex-start;margin-top:2px}
.pdf{background:rgba(240,64,96,.1);color:#f47895;border:1px solid rgba(240,64,96,.22)}
.pdc{background:rgba(240,160,0,.09);color:#f5c842;border:1px solid rgba(240,160,0,.22)}
.pds{background:rgba(5,196,155,.09);color:#5adfc5;border:1px solid rgba(5,196,155,.22)}
.pdr{background:var(--surf2);color:var(--dim);border:1px solid var(--b1)}

/* RESOURCES */
.res-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
@media(max-width:640px){.res-grid{grid-template-columns:1fr}}
.res-item{background:var(--surf2);border:1px solid var(--b1);border-radius:10px;padding:13px 15px;display:flex;align-items:flex-start;gap:11px}
.res-icon{font-size:18px;flex-shrink:0;margin-top:1px}
.res-body .rt{font-size:13px;font-weight:500;color:var(--text);margin-bottom:3px}
.res-body .rd{font-size:12px;color:var(--muted);line-height:1.45}
.res-body a{color:var(--v);text-decoration:none;font-size:11px;font-family:var(--font-mono)}
.res-body a:hover{text-decoration:underline}

/* EXPECT GRID */
.eg{display:grid;grid-template-columns:repeat(auto-fill,minmax(195px,1fr));gap:11px}
.ei{background:var(--surf2);border:1px solid var(--b1);border-radius:10px;padding:14px 16px}
.ei .el{font-family:var(--font-mono);font-size:9.5px;letter-spacing:.12em;text-transform:uppercase;color:var(--dim);margin-bottom:6px;font-weight:600}
.ei p{font-size:12.5px;color:var(--muted);line-height:1.5}.ei p strong{color:var(--text);font-weight:500}

/* ADVICE */
.ag{display:grid;grid-template-columns:1fr 1fr;gap:10px}
@media(max-width:580px){.ag{grid-template-columns:1fr}}
.ai{background:var(--surf2);border:1px solid var(--b1);border-radius:10px;padding:13px 16px;font-size:13px;color:var(--muted);line-height:1.6}
.ai strong{display:block;font-size:13px;color:var(--text);font-weight:500;margin-bottom:4px}

/* INSIGHT */
.ins{border-left:3px solid var(--v);background:rgba(108,99,245,.06);border-radius:0 10px 10px 0;padding:13px 17px;margin-bottom:20px;font-size:13.5px;color:#b0b0d0;line-height:1.65}
.ins strong{color:#d0d0f0;font-weight:500}
.ins.g{border-color:var(--g);background:rgba(5,196,155,.05);color:#a0c8c0}.ins.g strong{color:#c0e0d8}
.ins.a{border-color:var(--a);background:rgba(240,160,0,.05);color:#c0b080}.ins.a strong{color:#e0d090}
.ins.r{border-color:var(--r);background:rgba(240,64,96,.05);color:#c09098}.ins.r strong{color:#e0b0b8}

/* RULE GRID */
.rg{display:grid;grid-template-columns:1fr 1fr;gap:9px}
@media(max-width:560px){.rg{grid-template-columns:1fr}}
.rule{border-radius:10px;padding:13px 15px;font-size:12.5px;line-height:1.55}
.rule .rl{font-family:var(--font-mono);font-size:9.5px;letter-spacing:.1em;text-transform:uppercase;font-weight:600;margin-bottom:5px;display:block}
.rdo{background:rgba(5,196,155,.07);border:1px solid rgba(5,196,155,.18);color:#9ad8cc}.rdo .rl{color:var(--g)}
.rdont{background:rgba(240,64,96,.07);border:1px solid rgba(240,64,96,.18);color:#d89098}.rdont .rl{color:var(--r)}

/* BAND */
.band{background:var(--surf2);border:1px solid var(--b1);border-radius:10px;padding:15px 18px;font-size:13.5px;color:var(--muted);line-height:1.65;margin-bottom:14px}
.band strong{color:var(--text);font-weight:500}

/* TRACK GRID */
.tg{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:11px}
.tc{background:var(--surf);border:1px solid var(--b1);border-radius:12px;padding:17px 19px}
.tc .tn{font-family:var(--font-disp);font-size:13.5px;font-weight:600;color:#fff;margin-bottom:10px}
.tc ul{list-style:none}.tc ul li{font-size:12.5px;color:var(--muted);padding:3px 0 3px 12px;position:relative;line-height:1.45}
.tc ul li::before{content:'·';position:absolute;left:0;color:var(--dim)}
.tc ul li.hot{color:#c0b8f0}.tc ul li.note{color:var(--dim);font-size:11.5px;margin-top:5px;font-style:italic}

/* LAB GRID */
.lg{display:grid;grid-template-columns:repeat(3,1fr);gap:13px}
@media(max-width:700px){.lg{grid-template-columns:1fr}}
.lc{background:var(--surf);border:1px solid var(--b1);border-radius:14px;padding:20px}
.lc .ln{font-family:var(--font-disp);font-size:15px;font-weight:700;color:#fff;margin-bottom:13px;padding-bottom:11px;border-bottom:1px solid var(--b1)}
.lc ul{list-style:none}.lc ul li{font-size:12.5px;color:var(--muted);padding:4px 0 4px 14px;position:relative;line-height:1.5}
.lc ul li::before{content:'→';position:absolute;left:0;color:var(--dim);font-size:9px;top:6px}
.lc ul li strong{color:var(--text);font-weight:500}

/* TIMELINE */
.tl{position:relative;padding-left:26px}.tl::before{content:'';position:absolute;left:7px;top:8px;bottom:8px;width:1px;background:var(--b1)}
.tli{position:relative;margin-bottom:22px}.tli::before{content:'';position:absolute;left:-22px;top:6px;width:8px;height:8px;border-radius:50%;background:var(--surf2);border:1.5px solid var(--b2)}
.tli.act::before{background:var(--v);border-color:var(--v)}
.tli .tt{font-size:13.5px;font-weight:500;color:var(--text);margin-bottom:4px}
.tli .td{font-size:12.5px;color:var(--muted);line-height:1.6}

/* FORMULA */
.fbox{background:var(--surf);border:1px solid var(--b2);border-radius:18px;padding:42px;text-align:center;margin:0 0 0}
.fbox h2{font-family:var(--font-disp);font-size:21px;font-weight:700;color:#fff;margin-bottom:28px}
.fi-wrap{display:flex;flex-wrap:wrap;justify-content:center;align-items:center}
.fi{font-family:var(--font-disp);font-size:13px;font-weight:600;padding:8px 15px;border-radius:8px;background:var(--surf2);border:1px solid var(--b2);color:#fff;margin:4px}
.fop{font-size:18px;color:var(--dim);padding:0 4px;font-weight:300}
.feq{font-size:18px;color:var(--v);padding:0 5px}
.fr{font-family:var(--font-disp);font-size:14px;font-weight:700;padding:11px 20px;border-radius:8px;background:rgba(108,99,245,.14);border:1px solid rgba(108,99,245,.38);color:var(--v);width:100%;margin-top:10px;display:block}
.loop{background:var(--surf2);border:1px solid var(--b2);border-radius:12px;padding:20px 24px;margin-top:28px;font-size:14.5px;font-weight:500;color:#d0d0e8;text-align:center;line-height:1.7}
.loop span{color:var(--v)}

/* UTILS */
.mt8{margin-top:8px}.mt12{margin-top:12px}.mt16{margin-top:16px}.mt24{margin-top:24px}.mt32{margin-top:32px}.mt48{margin-top:48px}
.divider{height:1px;background:var(--b1);margin:28px 0}
footer{padding:36px 28px;text-align:center;color:var(--dim);font-size:12.5px;border-top:1px solid var(--b1)}
::-webkit-scrollbar{width:5px;height:5px}::-webkit-scrollbar-track{background:var(--bg)}::-webkit-scrollbar-thumb{background:var(--b2);border-radius:3px}
.btt{position:fixed;bottom:22px;right:22px;z-index:300;width:38px;height:38px;border-radius:50%;background:var(--surf2);border:1px solid var(--b2);display:flex;align-items:center;justify-content:center;color:var(--muted);cursor:pointer;font-size:15px;transition:all .15s;text-decoration:none;opacity:0;pointer-events:none}
.btt.vis{opacity:1;pointer-events:all}.btt:hover{color:var(--text)}
code{font-family:var(--font-mono);font-size:.85em;background:var(--surf2);border:1px solid var(--b1);border-radius:4px;padding:1px 5px;color:#b0c8f0}
.scratch-box{display:grid;grid-template-columns:1fr 1fr 1fr;border:1px solid var(--b1);border-radius:12px;overflow:hidden}
@media(max-width:620px){.scratch-box{grid-template-columns:1fr}}
.sc{padding:16px 17px}.sc+.sc{border-left:1px solid var(--b1)}
.sc .scl{font-family:var(--font-mono);font-size:9.5px;letter-spacing:.12em;text-transform:uppercase;font-weight:600;margin-bottom:11px}
.sc ul{list-style:none}.sc ul li{font-size:12.5px;padding:3px 0;line-height:1.45;color:var(--muted)}
.scm{background:rgba(108,99,245,.07)}.scm .scl{color:var(--v)}
.sco{background:rgba(5,196,155,.05)}.sco .scl{color:var(--g)}
.scn{background:var(--surf)}.scn .scl{color:var(--dim)}.scn ul li{color:var(--dim)}

/* phase flow */
.pf{display:flex;overflow-x:auto;padding-bottom:6px;gap:0}
.pf-it{display:flex;align-items:center;flex-shrink:0}
.pf-box{padding:8px 14px;border-radius:8px;font-size:12px;font-weight:500;background:var(--surf2);border:1px solid var(--b1);color:var(--muted);white-space:nowrap;margin:3px}
.pf-arr{font-size:13px;color:var(--dim);padding:0 3px;flex-shrink:0}
</style>
</head>
<body>
<a href="#top" class="btt" id="btt">↑</a>
<div id="top">
<div class="hero">
<div class="hero-bg"></div>
<div class="eyebrow">// the complete honest guide — no filler, no padding</div>
<h1>Becoming a <em>World-Class</em><br>AI Researcher</h1>
<p class="hero-sub">Everything you need. Calibrated depth. The specific resources, videos, websites, papers, and projects — phase by phase — from zero to frontier lab ready.</p>
<div class="hero-note"><strong>The principle everything follows:</strong> Does the mechanism itself encode the insight? If yes — implement it yourself. If not — understand it conceptually and use the library. This cuts wasted effort in half and doubles your depth where it counts.</div>
</div>
</div>

<!-- NAV -->
<nav class="snav">
<div class="snav-inner">
<a href="#overview" class="nl nm"><span class="ndot" style="background:#888"></span>Overview</a>
<a href="#p0" class="nl nv"><span class="ndot" style="background:var(--v)"></span>P0 · Foundations</a>
<a href="#p1" class="nl ng"><span class="ndot" style="background:var(--g)"></span>P1 · Core ML</a>
<a href="#p2" class="nl nb"><span class="ndot" style="background:var(--b)"></span>P2 · Deep Learning</a>
<a href="#p3" class="nl na"><span class="ndot" style="background:var(--a)"></span>P3 · Transformers</a>
<a href="#p4" class="nl nr"><span class="ndot" style="background:var(--r)"></span>P4 · RL & Generative</a>
<a href="#p5" class="nl np"><span class="ndot" style="background:var(--p)"></span>P5 · Specialize & Publish</a>
<a href="#labs" class="nl nm"><span class="ndot" style="background:#888"></span>Lab Prep</a>
<a href="#mindset" class="nl nm"><span class="ndot" style="background:#888"></span>Mindset</a>
</div>
</nav>

<!-- OVERVIEW -->
<section id="overview" class="ps">
<div class="wrap">
<div class="sl">Before you start — read this first</div>
<div class="g2 mt16">
<div>
<h2 style="font-family:var(--font-disp);font-size:25px;font-weight:700;color:#fff;letter-spacing:-.02em;line-height:1.25;margin-bottom:14px">The one rule that changes everything</h2>
<p style="font-size:15px;color:var(--muted);line-height:1.7;margin-bottom:12px">Every other roadmap treats all knowledge as equally worth implementing from scratch. That's wrong. <strong style="color:var(--text)">Some mechanisms must be felt in your hands. Most things you just need to understand well enough to use and reason about.</strong></p>
<p style="font-size:14px;color:var(--muted);line-height:1.7;margin-bottom:12px">Before implementing anything, ask: "Does the mechanism itself encode the insight?" Backpropagation: yes — implementing it once gives you a mental model that changes how you debug forever. SVD: no — you need to know what it does geometrically, not re-implement LAPACK. The transformer's multi-head attention: yes — every paper you'll read for 5 years assumes you understand it at the gradient level.</p>
<p style="font-size:14px;color:var(--muted);line-height:1.7">This single principle saves you hundreds of hours and sharpens the things that actually matter.</p>
</div>
<div>
<div class="scratch-box">
<div class="sc scm"><div class="scl">Must implement</div><ul><li>Backpropagation</li><li>Transformer attention</li><li>A small GPT from scratch</li><li>Diffusion model (DDPM)</li><li>ResNet with ablations</li><li>PPO if doing RL track</li><li>Gradient descent on toy loss</li></ul></div>
<div class="sc sco"><div class="scl">Once, then library</div><ul><li>Logistic regression</li><li>K-means clustering</li><li>Simple CNN on CIFAR</li><li>Basic LSTM cell</li><li>A gradient boosting tree</li><li>Simple data augmentation</li><li>BPE tokenizer</li></ul></div>
<div class="sc scn"><div class="scl">Never implement</div><ul><li>SVD / eigendecomposition</li><li>XGBoost internals</li><li>CUDA kernels</li><li>Distributed comms</li><li>Tokenizer from scratch</li><li>Docker setup</li><li>Sorting algorithms</li></ul></div>
</div>
</div>
</div>

<div class="sl mt48">The full journey</div>
<div class="pf mt16">
<div class="pf-it"><div class="pf-box" style="border-color:rgba(108,99,245,.4);color:#b0a8ff">P0 · Math &amp; Code<br><span style="font-weight:400;font-size:10.5px;color:var(--dim)">3–4 months</span></div><div class="pf-arr">→</div></div>
<div class="pf-it"><div class="pf-box" style="border-color:rgba(5,196,155,.4);color:#5adfc5">P1 · Core ML<br><span style="font-weight:400;font-size:10.5px;color:var(--dim)">3–5 months</span></div><div class="pf-arr">→</div></div>
<div class="pf-it"><div class="pf-box" style="border-color:rgba(56,182,248,.4);color:#7ad4f8">P2 · Deep Learning<br><span style="font-weight:400;font-size:10.5px;color:var(--dim)">5–8 months</span></div><div class="pf-arr">→</div></div>
<div class="pf-it"><div class="pf-box" style="border-color:rgba(240,160,0,.4);color:#f5c842">P3 · Transformers &amp; LLMs<br><span style="font-weight:400;font-size:10.5px;color:var(--dim)">6–9 months</span></div><div class="pf-arr">→</div></div>
<div class="pf-it"><div class="pf-box" style="border-color:rgba(240,64,96,.4);color:#f47895">P4 · RL &amp; Generative<br><span style="font-weight:400;font-size:10.5px;color:var(--dim)">8–14 months</span></div><div class="pf-arr">→</div></div>
<div class="pf-it"><div class="pf-box" style="border-color:rgba(155,108,240,.4);color:#c095f8">P5 · Specialize &amp; Publish<br><span style="font-weight:400;font-size:10.5px;color:var(--dim)">ongoing</span></div></div>
</div>

<div class="sl mt48">What top labs actually want</div>
<div class="eg mt16">
<div class="ei"><div class="el">Research taste</div><p>Knowing <strong>which problems matter</strong> and why — not just solving what's given to you. Identifying gaps others missed.</p></div>
<div class="ei"><div class="el">First-author papers</div><p>NeurIPS / ICML / ICLR. Not reproductions — <strong>original contributions</strong> you can defend under adversarial questioning.</p></div>
<div class="ei"><div class="el">Implementation speed</div><p>Ideas reach clean PyTorch code <strong>within hours</strong>, not days. Rapid iteration is how research moves fast.</p></div>
<div class="ei"><div class="el">Scientific rigor</div><p><strong>Hypothesis before experiment</strong>, always. Ablation-backed claims. Honest limitations. Results that survive replication.</p></div>
<div class="ei"><div class="el">Communication</div><p>30s, 3min, 30min versions of your work <strong>ready and practiced</strong>. Writing clear enough for anyone at the lab.</p></div>
<div class="ei"><div class="el">Specialization</div><p>A <strong>recognizable identity</strong> in one area — interpretability, post-training, RL, multimodal. Not general breadth.</p></div>
</div>
</div>
</section>

<!-- PHASE 0 -->
<section id="p0" class="ps p0">
<div class="wrap">
<div class="ph"><div class="pnum">P0</div><div><h2>Mathematical &amp; Systems Foundations</h2><div class="ptl">⏱ Months 1–4 · 10–15 hrs/week · Do not rush this phase</div><p class="ptag">Every model you'll ever build rests on what you internalize here. The only phase where gaps compound against you later at the worst possible moment.</p></div></div>

<div class="sl">The honest take</div>
<div class="mpull">
<div class="mq">Don't ask which library. Ask why this works.</div>
<p>Math maturity — the ability to read, write, and reason through mathematical arguments fluidly — is what frontier lab interviewers identify as the first filter. Not coding skill. Not paper count. <strong>Can you derive gradient descent? Can you explain SVD geometrically? Can you read a loss function and immediately understand what it's optimizing?</strong></p>
<p>This does NOT mean implementing SVD from scratch in Python. It means knowing what SVD does — finds the best low-rank approximation of a matrix — why PCA is a special case, and what happens to the eigenspectrum when you regularize. Conceptual depth first, implementation only where the mechanism is the insight.</p>
</div>

<div class="sl mt32">Mathematics — what to actually cover</div>
<div class="g3 mt16">
<div class="card"><h3>📐 Linear Algebra</h3><div class="pw"><span class="pill v">Vectors & matrices</span><span class="pill v">Matrix multiplication</span><span class="pill v">Rank & nullspace</span><span class="pill v">Eigenvalues/vectors</span><span class="pill v">SVD — what it means</span><span class="pill v">Orthogonality</span><span class="pill v">PCA as eigendecomp</span><span class="pill v">Dot product = projection</span></div><p class="mt12">Watch 3Blue1Brown's Essence of Linear Algebra (16 videos, ~3hrs) before any textbook. The visual intuition it builds is irreplaceable.</p></div>
<div class="card"><h3>∂ Calculus & Optimization</h3><div class="pw"><span class="pill v">Derivatives & partials</span><span class="pill v">Chain rule — reflex level</span><span class="pill v">Jacobians</span><span class="pill v">Gradient descent — implement</span><span class="pill v">SGD & momentum</span><span class="pill v">Adam update rule</span><span class="pill v">Convexity intuition</span><span class="pill v">Learning rate schedules</span></div><p class="mt12">Implement gradient descent on a toy 2D loss surface and visualize it before reading any optimization paper.</p></div>
<div class="card"><h3>📊 Probability & Statistics</h3><div class="pw"><span class="pill v">Bayes' theorem</span><span class="pill v">Gaussian distribution</span><span class="pill v">Expectation & variance</span><span class="pill v">MLE derivation</span><span class="pill v">KL divergence</span><span class="pill v">Conditional probability</span><span class="pill v">Central limit theorem</span><span class="pill v">Confidence intervals</span></div><p class="mt12">Derive the logistic regression loss from the Bernoulli MLE. This single derivation connects probability theory to machine learning concretely.</p></div>
</div>

<div class="sl mt32">Reference materials — specifically what to use</div>
<div class="res-grid mt16">
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">3Blue1Brown — Essence of Linear Algebra</div><div class="rd">16 short videos. Watch these before ANY textbook. The geometric intuition you build here makes every subsequent ML paper easier to parse.</div><a href="https://youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab">youtube.com/3b1b-linalg</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">3Blue1Brown — Essence of Calculus</div><div class="rd">11 videos. Chain rule video is mandatory — watch it the same day you implement backprop. The connection will cement both.</div><a href="https://youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr">youtube.com/3b1b-calculus</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Mathematics for Machine Learning (Deisenroth, Faisal, Ong)</div><div class="rd">Free PDF. Best single book covering all math needed. Chapters 2 (Linear Algebra), 5 (Vector Calculus), 6 (Probability) are your core.</div><a href="https://mml-book.github.io">mml-book.github.io</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">Gilbert Strang — MIT 18.06 Linear Algebra</div><div class="rd">The gold standard university course. OCW has all lectures free. After 3Blue1Brown, these lectures add the formal depth. Lectures 1–14 are essential.</div><a href="https://ocw.mit.edu/18-06sc-fall-2011">ocw.mit.edu/18-06</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">Andrew Ng — Machine Learning Specialization (Coursera)</div><div class="rd">Do this alongside Phase 0. Not for depth — for breadth and motivation. It shows you what the math you're learning is for. Free to audit.</div><a href="https://coursera.org/specializations/machine-learning-introduction">coursera.org/ml-specialization</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Pattern Recognition and Machine Learning (Bishop)</div><div class="rd">Chapters 1–2 only at this stage: Introduction and Probability Theory. Dense but precise. The probability chapter is the best self-contained reference for ML probability.</div><a href="https://www.microsoft.com/en-us/research/uploads/prod/2006/01/Bishop-Pattern-Recognition-and-Machine-Learning-2006.pdf">Free PDF available</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">fast.ai — Practical Deep Learning Part 1</div><div class="rd">Start this in parallel with Phase 0/1. Jeremy Howard's top-down teaching style builds motivation before mathematical depth. Counterintuitively valuable.</div><a href="https://course.fast.ai">course.fast.ai</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">StatQuest with Josh Starmer</div><div class="rd">Best YouTube channel for statistics and basic ML. Unusually clear explanations with animations. Watch the probability and statistics playlist before Phase 1.</div><a href="https://youtube.com/@statquest">youtube.com/@statquest</a></div></div>
</div>

<div class="sl mt32">Programming — tool fluency, not expertise</div>
<div class="g2 mt16">
<div class="card"><h3>💻 Python — what you actually need</h3><div class="pw"><span class="pill">List comprehensions</span><span class="pill">Classes & OOP basics</span><span class="pill">NumPy — broadcasting</span><span class="pill">Matplotlib — basic plots</span><span class="pill">Pandas — basic ops</span><span class="pill">Jupyter notebooks</span><span class="pill">Git — add/commit/push/branch</span><span class="pill">Virtual environments</span></div><p class="mt12">Learn Python by doing projects, not tutorials. The fastest path: start coding your neural network project in Week 2 even if your Python is incomplete. Fix gaps as they appear.</p></div>
<div class="card"><h3>📚 Python resources</h3><div class="res-grid" style="grid-template-columns:1fr;gap:7px"><div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">Python for Everybody (Coursera / Dr. Chuck)</div><div class="rd">Free. Best beginner Python course. Chapters 1–9 are enough to start your ML projects.</div></div></div><div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">NumPy documentation — quickstart</div><div class="rd">30-minute quickstart tutorial. After that, learn by using it. Broadcasting rules are the most important thing to deeply understand.</div></div></div><div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Kaggle Learn — Python, Pandas, Matplotlib</div><div class="rd">Free micro-courses. 3–5 hours each. Clean exercises with immediate feedback. Fastest path to tool fluency.</div><a href="https://kaggle.com/learn">kaggle.com/learn</a></div></div></div></div>
</div>

<div class="sl mt32">Build exactly two things</div>
<div class="pc">
<div class="pc-top"><div class="pti">Neural network from scratch — MNIST</div><span class="badge bd">Must build — no exceptions</span></div>
<p>Forward propagation, backpropagation, and SGD in raw NumPy. Zero PyTorch. Zero autograd. Write every matrix operation yourself. Add <strong>gradient checking</strong> — perturb each weight by epsilon and compare analytical vs numerical gradients. Debug until they match to 5 decimal places.</p>
<div class="why"><strong>Why this is non-negotiable:</strong> The physical act of indexing into weight matrices, accumulating gradients layer by layer, watching loss decrease — builds a mental model you cannot get from reading. When a transformer fails in Phase 3, you'll trace the issue to a specific attention projection in minutes. Everyone else guesses.</div>
<p><strong>What to care about:</strong> Not accuracy. The process. Get to 97%+ on MNIST, but spend most of your time on gradient checking, the debugging journey, and understanding why each layer's gradient has the shape it does.</p>
<div class="pm"><span class="mt">NumPy only</span><span class="mt">MNIST dataset</span><span class="mt">Gradient checking required</span><span class="mt">Target 97%+ accuracy</span><span class="mt">~2 weeks</span></div>
</div>
<div class="pc">
<div class="pc-top"><div class="pti">Loss landscape visualizer</div><span class="badge bl">3 days, high value</span></div>
<p>Plot the loss surface for linear and logistic regression. Overlay gradient descent paths for three different learning rates — one that converges, one that oscillates, one that diverges. This single visualization makes every subsequent optimization paper make intuitive sense immediately.</p>
<div class="pm"><span class="mt">Matplotlib + NumPy</span><span class="mt">Synthetic 2D dataset</span><span class="mt">3 LR variants</span><span class="mt">~3 days</span></div>
</div>

<div class="sl mt32">Papers — Phase 0 reading list</div>
<div class="pbox mt16">
<div class="pr"><div class="pn">01</div><div class="pb"><div class="pt">Backpropagation (Rumelhart, Hinton & Williams, 1986)</div><div class="pa">Nature — the paper that made neural networks trainable</div><div class="pw2">Read this AFTER implementing backprop yourself. Your implementation is the first exposure — reading it beforehand shortcuts the learning. After implementing, read to confirm your understanding. Derive every equation alongside the text.</div></div><span class="pd pdf">Line by line</span></div>
<div class="pr"><div class="pn">02</div><div class="pb"><div class="pt">A Few Useful Things to Know About Machine Learning</div><div class="pa">Pedro Domingos, 2012 — best single-paper overview of the field</div><div class="pw2">Read this FIRST before anything else. Then re-read it at the end of Phase 1. The gap between your first and second reading measures your growth exactly. The 12 lessons are surprisingly durable — you'll cite them in research discussions years later. The section on the curse of dimensionality alone is worth the read.</div></div><span class="pd pdf">Read twice</span></div>
<div class="pr"><div class="pn">03</div><div class="pb"><div class="pt">Efficient Backprop (LeCun, Bottou, Orr & Müller)</div><div class="pa">Practical optimization wisdom that has aged unusually well</div><div class="pw2">Initialization, learning rate, input preprocessing — these practical insights still appear in modern training recipes. Focus on the sections about normalization and learning rate adaptation. Most people skip this; reading it gives you intuition others lack about why modern techniques work.</div></div><span class="pd pdc">Key sections</span></div>
</div>

<div class="sl mt32">Phase 0 performance expectations</div>
<div class="eg mt16">
<div class="ei"><div class="el">Derivation</div><p>Derive MSE and cross-entropy gradient updates <strong>from scratch, without notes</strong></p></div>
<div class="ei"><div class="el">Implementation</div><p>Implement a 2-layer network in NumPy from memory including backprop and gradient check</p></div>
<div class="ei"><div class="el">Conceptual</div><p>Explain eigenvalues, SVD, and PCA <strong>geometrically</strong> to someone who just started learning</p></div>
<div class="ei"><div class="el">Debugging</div><p>Given a broken gradient computation, identify whether error is in forward pass, backward, or update step</p></div>
</div>

<div class="sl mt32">Practical advice</div>
<div class="ag mt16">
<div class="ai"><strong>3Blue1Brown before textbooks.</strong>Watch all 16 linear algebra videos and 11 calculus videos before opening any textbook. The geometric intuition they build makes formalism click in a fraction of the time. This is not optional.</div>
<div class="ai"><strong>Don't rush past the math.</strong>A weak foundation makes Phase 3 (Transformers) nearly incomprehensible. Spend real weeks here — not days. Andrew Ng's ML Specialization + Mathematics for Machine Learning book are the right combination.</div>
<div class="ai"><strong>Start your research log immediately.</strong>A text file or Notion page. Every session: what you tried, what broke, what you learned, one question you now have. This habit is one of the highest-leverage things in the entire guide. By Phase 5 it's your primary research tool.</div>
<div class="ai"><strong>10–15 hrs/week minimum.</strong>Consistency beats intensity. Daily practice with derivatives and probability compounds faster than weekend cramming. Build the habit now — you'll need it in Phase 4 when experiments run overnight and you iterate on results every morning.</div>
</div>
</div>
</section>

<!-- PHASE 1 -->
<section id="p1" class="ps p1">
<div class="wrap">
<div class="ph"><div class="pnum">P1</div><div><h2>Classical Machine Learning</h2><div class="ptl">⏱ Months 4–9 · Target: strong ML engineer level</div><p class="ptag">Master the classical toolkit. But the real lesson isn't algorithms — it's experimental discipline and evaluation rigor. These habits define researchers.</p></div></div>

<div class="mpull">
<div class="mq">Baselines before novelty. Ablations before announcements.</div>
<p>Before running any experiment, write your hypothesis and null hypothesis. What result would falsify your hypothesis? If you can't answer that, you're not running an experiment — you're running a demo. This single discipline separates research from engineering.</p>
<p><strong>On implementing from scratch:</strong> Implement gradient boosting once, manually, to understand what "fit the residuals" means. Then use XGBoost forever. The learning is in understanding the mechanism well enough to reason about when it fails — not rebuilding what 50 engineers optimized for years.</p>
</div>

<div class="sl mt24">Core topics — calibrated depth</div>
<div class="drow mt16">
<div class="di dm"><span class="dl">Understand deeply</span><ul><li>Bias-variance tradeoff — never stops being useful</li><li>Cross-validation and data leakage — career-critical</li><li>Decision trees → RF → Gradient boosting: the why of each step</li><li>When linear models beat trees (and vice versa)</li><li>Calibration — why 70% confidence should mean 70% accuracy</li><li>t-SNE: what it shows AND what it doesn't (crucial — most people misread it)</li><li>Class imbalance — why accuracy is misleading</li><li>ROC-AUC vs PR-AUC — when each applies</li></ul></div>
<div class="di do"><span class="dl">Implement once, then library</span><ul><li>Gradient boosting (manually, on a toy dataset)</li><li>Logistic regression gradient update</li><li>K-means with random restarts</li><li>PCA via covariance matrix</li><li>Simple decision tree splitting</li></ul></div>
<div class="di ds"><span class="dl">Use fluently, don't reimplement</span><ul><li>XGBoost / LightGBM / CatBoost</li><li>Scikit-learn pipelines</li><li>UMAP for visualization</li><li>SHAP for feature importance</li><li>Bootstrap confidence intervals</li><li>t-test, Mann-Whitney U</li></ul></div>
</div>

<div class="sl mt24">Topic reference — what to study</div>
<div class="g3 mt16">
<div class="card"><h3>📈 Supervised Learning</h3><div class="pw"><span class="pill g">Linear regression (OLS + gradient)</span><span class="pill g">Logistic regression</span><span class="pill g">Ridge & Lasso</span><span class="pill g">SVMs — margin intuition</span><span class="pill g">Decision trees — Gini & entropy</span><span class="pill g">Random forests — why bagging reduces variance</span><span class="pill g">Gradient boosting</span><span class="pill g">XGBoost</span></div></div>
<div class="card"><h3>🔍 Unsupervised Learning</h3><div class="pw"><span class="pill g">K-means</span><span class="pill g">DBSCAN</span><span class="pill g">Gaussian Mixture Models</span><span class="pill g">PCA</span><span class="pill g">t-SNE — and its limits</span><span class="pill g">UMAP</span><span class="pill g">Hierarchical clustering</span></div></div>
<div class="card"><h3>📊 Evaluation & Statistics</h3><div class="pw"><span class="pill g">Train/val/test splits</span><span class="pill g">K-fold cross-validation</span><span class="pill g">Leakage detection</span><span class="pill g">Calibration curves</span><span class="pill g">ROC-AUC & PR-AUC</span><span class="pill g">Bootstrap CI</span><span class="pill g">Hypothesis testing</span><span class="pill g">Statistical significance</span></div></div>
</div>

<div class="sl mt32">Reference materials</div>
<div class="res-grid mt16">
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">The Elements of Statistical Learning (Hastie, Tibshirani, Friedman)</div><div class="rd">Free PDF. Chapters 2 (Statistical Learning Theory), 7 (Model Assessment), 8 (Boosting) are essential. The bias-variance chapter alone justifies the book. Don't read front to back — use as reference.</div><a href="https://hastie.su.domains/ElemStatLearn/">hastie.su.domains/ElemStatLearn</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Hands-On Machine Learning (Aurélien Géron)</div><div class="rd">Best practical ML book. Chapters 1–8 cover everything in Phase 1 with good code. Use alongside the ESL textbook for implementation context.</div><a href="https://github.com/ageron/handson-ml3">github.com/ageron/handson-ml3</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">fast.ai — Practical Deep Learning for Coders</div><div class="rd">Jeremy Howard's course is unusually good at building top-down intuition. Part 1 covers DL in a way that complements Phase 1's classical foundation.</div><a href="https://course.fast.ai">course.fast.ai</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Kaggle Learn — ML Explainability, Feature Engineering</div><div class="rd">Free micro-courses. The ML Explainability course (SHAP values) is particularly good for developing error analysis instincts.</div><a href="https://kaggle.com/learn">kaggle.com/learn</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">StatQuest — Decision Trees, Random Forests, XGBoost playlists</div><div class="rd">Josh Starmer's playlists on these specific topics are the clearest explanations available. Watch the XGBoost series (4 videos) before reading the XGBoost paper.</div><a href="https://youtube.com/@statquest">youtube.com/@statquest</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">CS229 — Stanford Machine Learning (Andrew Ng, lecture notes)</div><div class="rd">The lecture notes (free PDF) are cleaner than the video course for mathematical foundations. The notes on SVMs and EM algorithm are best-in-class.</div><a href="https://cs229.stanford.edu">cs229.stanford.edu</a></div></div>
</div>

<div class="sl mt32">One project done properly</div>
<div class="band mt16"><strong>Why only one project?</strong> Doing one thing with real depth — written up with a proper failure analysis — is worth five shallow demos. A single project with rigorous evaluation and honest error analysis signals researcher-level thinking. Five quick notebooks signals student thinking. Depth compounds. Breadth doesn't.</div>
<div class="pc">
<div class="pc-top"><div class="pti">End-to-end ML pipeline with rigorous evaluation</div><span class="badge bm">The core project</span></div>
<p>Pick any tabular problem you find interesting (fraud detection, churn prediction, medical diagnosis). The goal is NOT accuracy — it's evaluation discipline. Establish a proper train/val/test split. Compare four model families: linear, tree, random forest, gradient boosting. For each: calibration curve, ROC-AUC, confusion matrix at optimal threshold.</p>
<p>Then the part most people skip: <strong>error analysis</strong>. Take the 50 most confidently wrong predictions. What do they have in common? What does this tell you about the model's assumptions? Write this as a "Failure Analysis" section. This is what research scientists actually do — not hyperparameter tuning.</p>
<div class="why"><strong>Why this specific discipline:</strong> Error analysis is the core researcher skill. Interviewers will ask "what types of examples does your model fail on and why?" A researcher has a specific, insightful answer. An engineer says "I tried different hyperparameters." Build this habit on simple tabular data now, when the complexity is low.</div>
<div class="pm"><span class="mt">Any Kaggle tabular dataset</span><span class="mt">4+ model families</span><span class="mt">Calibration curves</span><span class="mt">Written error analysis</span><span class="mt">Bootstrap CIs on metrics</span><span class="mt">~3 weeks</span></div>
</div>

<div class="sl mt32">Papers — Phase 1</div>
<div class="pbox mt16">
<div class="pr"><div class="pn">01</div><div class="pb"><div class="pt">XGBoost: A Scalable Tree Boosting System</div><div class="pa">Chen & Guestrin, KDD 2016</div><div class="pw2">Read the first three sections: regularized objective, tree structure scoring, and the split-finding algorithm. Skip the distributed systems sections. The core insight is the second-order gradient approximation — understand why that's better than first-order only.</div></div><span class="pd pdc">First 3 sections</span></div>
<div class="pr"><div class="pn">02</div><div class="pb"><div class="pt">The Elements of Statistical Learning — Chapters 2, 7, 8</div><div class="pa">Hastie, Tibshirani & Friedman</div><div class="pw2">Not a paper but essential. Chapter 7 (Model Assessment and Selection) is the most important — bias-variance decomposition done rigorously. Chapter 8 gives you boosting theory. Use as reference throughout Phase 1.</div></div><span class="pd pdf">Ch.2, 7, 8 fully</span></div>
<div class="pr"><div class="pn">03</div><div class="pb"><div class="pt">A Few Useful Things to Know About ML — re-read</div><div class="pa">Pedro Domingos — you first read this in Phase 0</div><div class="pw2">Re-reading a paper you've already seen, after gaining real experience, is one of the most efficient learning techniques almost no one uses. What you couldn't understand in Phase 0 will be obvious. What seemed obvious will now have deeper meaning. The gap between readings measures your growth exactly.</div></div><span class="pd pdf">Full re-read</span></div>
<div class="pr"><div class="pn">04</div><div class="pb"><div class="pt">Random Forests (Breiman, 2001)</div><div class="pa">Machine Learning journal</div><div class="pw2">Understand why bagging reduces variance but not bias, why random feature selection reduces correlation between trees, and why out-of-bag error is a valid estimate. The mathematical intuition is more important than the implementation details here.</div></div><span class="pd pdc">Core sections</span></div>
</div>

<div class="sl mt32">Performance expectations</div>
<div class="eg mt16">
<div class="ei"><div class="el">Algorithms</div><p>Explain bias-variance tradeoff; derive OLS solution; explain why random forests reduce variance but not bias</p></div>
<div class="ei"><div class="el">Evaluation</div><p>Build proper pipeline — no leakage, calibrated probabilities, bootstrap confidence intervals on every metric</p></div>
<div class="ei"><div class="el">Error analysis</div><p>Given a trained classifier, produce written analysis of what it fails on and a hypothesis for why</p></div>
<div class="ei"><div class="el">Debugging</div><p>Given good val / bad test performance, diagnose leakage vs distribution shift vs overfitting</p></div>
</div>
<div class="ag mt16">
<div class="ai"><strong>Use Kaggle as a tool, not a competition.</strong>Don't chase ranks. Write up your analysis as a paper section — problem statement, approach, results, failure analysis. This is the habit you're building for Phase 5 publications.</div>
<div class="ai"><strong>Start your public GitHub now.</strong>Your Phase 1 project should have a clean README, evaluation results table, and your error analysis written up. Future researchers will look at this. Start the habit of honest, documented work now.</div>
<div class="ai"><strong>Always report confidence intervals.</strong>Never claim Model A beats Model B from a single evaluation. Run bootstrap comparison. Report 95% CI of the delta. This becomes critical when reviewers ask for it on your Phase 5 papers.</div>
<div class="ai"><strong>Re-read Domingos actively.</strong>For each of his 12 lessons, write one paragraph in your own words and one concrete example from your Phase 1 project. Forces synthesis, not passive recognition.</div>
</div>
</div>
</section>

<!-- PHASE 2 -->
<section id="p2" class="ps p2">
<div class="wrap">
<div class="ph"><div class="pnum">P2</div><div><h2>Deep Learning Foundations</h2><div class="ptl">⏱ Months 9–17 · Target: strong deep learning engineer</div><p class="ptag">Become fluent enough in PyTorch that ideas reach code within hours. Develop the ability to read a training curve and immediately form a diagnosis.</p></div></div>

<div class="mpull">
<div class="mq">When you look at a neural network, don't see a black box. See a computational graph.</div>
<p>The researchers who debug fastest trace gradient flow mentally. When loss spikes on epoch 47: is it the data pipeline? The LR schedule? A gradient explosion? A numerical issue? Each has a specific diagnostic. <strong>This systematic debugging protocol comes from having implemented backprop manually in Phase 0 — now you apply that mental model to modern architectures.</strong></p>
<p>Every architectural choice is a testable hypothesis. Skip connections exist because someone hypothesized they'd improve gradient flow and proved it with ablations. When you read about any new component, first ask: what problem is this solving, and how would I verify that it solves it?</p>
</div>

<div class="sl mt24">Core topics</div>
<div class="drow mt16">
<div class="di dm"><span class="dl">Understand deeply + implement</span><ul><li>Backprop through CNNs — trace mentally</li><li>Why ResNets work — the gradient flow argument</li><li>Batch normalization — what it does to the loss landscape</li><li>PyTorch autograd — computational graph construction</li><li>Overfitting diagnostics — train vs val gap analysis</li><li>Adam vs SGD — when each wins</li><li>Mixed precision — why BF16 is faster AND safer</li><li>Diffusion model math — ELBO derivation, DDPM</li><li>Vanishing/exploding gradients — detect and fix</li></ul></div>
<div class="di do"><span class="dl">Implement once, then use library</span><ul><li>ResNet — once from scratch, then torchvision</li><li>LSTM cell — understand gating, then use nn.LSTM</li><li>DDPM diffusion model — derive + implement</li><li>Custom PyTorch Dataset + DataLoader</li><li>Training loop with LR warmup + clipping</li></ul></div>
<div class="di ds"><span class="dl">Understand, don't spend weeks on</span><ul><li>GAN training — learn dynamics, don't debug one for weeks</li><li>CUDA kernels — know what they are, use FlashAttention</li><li>Distributed training — learn basics when you need scale</li><li>U-Net — understand the pattern; implement if doing vision research</li></ul></div>
</div>

<div class="sl mt24">Architecture deep-dives</div>
<div class="g3 mt16">
<div class="card"><h3>🧱 CNN Architectures</h3><div class="pw"><span class="pill b">AlexNet — the 2012 breakthrough</span><span class="pill b">VGG — depth matters</span><span class="pill b">ResNet — skip connections</span><span class="pill b">DenseNet — all-to-all connections</span><span class="pill b">EfficientNet — compound scaling</span></div><p class="mt12">Understand the progression: each architecture solved the previous one's failure mode. Implement ResNet. Understand the others conceptually — their key insight and what they improved over the prior SOTA.</p></div>
<div class="card"><h3>🔄 Sequence Models</h3><div class="pw"><span class="pill b">RNN — vanishing gradient problem</span><span class="pill b">LSTM — cell state solution</span><span class="pill b">GRU — simpler variant</span><span class="pill b">Seq2Seq — encoder-decoder</span><span class="pill b">Attention (Bahdanau) — precursor to transformers</span></div><p class="mt12">Implement LSTM once. Understanding why it beats vanilla RNN (cell state highway) is essential for understanding why transformers then beat LSTMs (parallel attention instead of sequential state).</p></div>
<div class="card"><h3>🎨 Generative Models</h3><div class="pw"><span class="pill b">GAN — min-max training dynamics</span><span class="pill b">VAE — latent space + ELBO</span><span class="pill b">DDPM — diffusion process</span><span class="pill b">DDIM — faster sampling</span><span class="pill b">Score matching — connection to diffusion</span></div><p class="mt12">Implement DDPM. The math — ELBO, score matching — appears constantly in Phase 4 generative research. GANs: understand training dynamics, don't build a production one.</p></div>
</div>

<div class="sl mt24">PyTorch — the deep dive</div>
<div class="g2 mt16">
<div class="card"><h3>⚙️ What to master in PyTorch</h3><div class="pw"><span class="pill b">Autograd + computational graphs</span><span class="pill b">torch.compile</span><span class="pill b">Mixed precision (autocast + GradScaler)</span><span class="pill b">Custom Dataset & DataLoader</span><span class="pill b">gradient_checkpointing</span><span class="pill b">Memory profiling (torch.profiler)</span><span class="pill b">DDP basics</span><span class="pill b">Learning rate schedulers</span><span class="pill b">Gradient clipping</span><span class="pill b">Model checkpointing</span></div><p class="mt12">Build one reusable training loop skeleton with: YAML config, wandb/tensorboard logging, LR warmup, gradient clipping, mixed precision, and checkpoint saving. This skeleton starts every Phase 3–5 project.</p></div>
<div class="card"><h3>📉 Training curve diagnostics</h3><p style="margin-bottom:10px">Learn to diagnose these patterns on sight:</p><div class="pw"><span class="pill b">Loss spike → LR too high or bad batch</span><span class="pill b">Val rises while train falls → overfitting</span><span class="pill b">Both plateau → LR too low / wrong architecture</span><span class="pill b">NaN loss → gradient explosion / bad init</span><span class="pill b">Val better than train → data leakage</span><span class="pill b">Slow convergence → LR warmup needed</span><span class="pill b">Loss oscillates → LR too high for optimizer</span></div><p class="mt12">Log gradient norms AND weight norms in addition to loss. These metrics catch problems that loss curves miss entirely.</p></div>
</div>

<div class="sl mt32">Reference materials</div>
<div class="res-grid mt16">
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Deep Learning (Goodfellow, Bengio, Courville)</div><div class="rd">Free online. Chapters 6 (Deep Feedforward Networks), 8 (Optimization), 9 (CNNs), 10 (Sequence Models) are essential. The best mathematical treatment of deep learning fundamentals available.</div><a href="https://deeplearningbook.org">deeplearningbook.org</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">CS231n — Stanford (Convolutional Neural Networks for Visual Recognition)</div><div class="rd">Karpathy's course. The best university DL course ever made. Assignment 2 (backprop) and Assignment 3 (RNNs, attention) are essential implementation exercises.</div><a href="https://cs231n.github.io">cs231n.github.io</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Andrej Karpathy — Neural Networks: Zero to Hero (YouTube)</div><div class="rd">The single best tutorial series for this phase. "Makemore" builds character-level LMs from scratch, ending with a transformer. Karpathy's code is exceptionally clean. Watch all 7 videos.</div><a href="https://youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ">youtube.com/karpathy-zero-to-hero</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">PyTorch official tutorials — full suite</div><div class="rd">Start with "Learn the Basics," then "Training a Classifier," then "Visualizing Models, Data, and Training." The autograd tutorial is mandatory — understand it, not just use it.</div><a href="https://pytorch.org/tutorials">pytorch.org/tutorials</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Yannic Kilcher — paper explanations (YouTube)</div><div class="rd">Best YouTube channel for research paper walkthroughs. Watch his ResNet, BatchNorm, and DDPM videos alongside reading the papers. His explanations are unusually precise.</div><a href="https://youtube.com/@YannicKilcher">youtube.com/@YannicKilcher</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Dive into Deep Learning (d2l.ai)</div><div class="rd">Free interactive book with code in PyTorch, JAX, and MXNet. The best single reference for implementation alongside theory. Chapters on CNNs, RNNs, and Attention are excellent.</div><a href="https://d2l.ai">d2l.ai</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Weights & Biases — guides and reports</div><div class="rd">Learn wandb for experiment tracking. The W&B guides on hyperparameter sweeps and model debugging are practical and immediately useful. Free for personal use.</div><a href="https://docs.wandb.ai/guides">docs.wandb.ai/guides</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">fast.ai Part 2 — Deep Learning from the Foundations</div><div class="rd">Jeremy Howard goes deep on PyTorch internals, building from scratch. Pairs perfectly with Phase 2. The diffusion model lectures are particularly strong.</div><a href="https://course.fast.ai/Lessons/part2.html">course.fast.ai/part2</a></div></div>
</div>

<div class="sl mt32">Two core projects</div>
<div class="pc">
<div class="pc-top"><div class="pti">ResNet from scratch with ablation study</div><span class="badge bd">Build from scratch</span></div>
<p>Implement ResNet in PyTorch from the paper. Train on CIFAR-10. Run four ablations: <strong>(1)</strong> remove skip connections — watch it fail past ~15 layers. <strong>(2)</strong> remove batch norm — watch training destabilize. <strong>(3)</strong> vary depth — 20 vs 32 vs 56 layers. <strong>(4)</strong> compare augmentation strategies.</p>
<div class="why"><strong>Why ablations are the entire point:</strong> When you turn off skip connections and watch a 20-layer network fail to beat a 5-layer one, you understand the gradient degradation problem viscerally — not abstractly. That understanding helps you reason about every deep architecture for the rest of your career. This is research methodology: one variable at a time, everything else fixed.</div>
<div class="pm"><span class="mt">CIFAR-10</span><span class="mt">Top-1 accuracy</span><span class="mt">4 ablation variants</span><span class="mt">Gradient norm logging</span><span class="mt">Results table required</span><span class="mt">~2–3 weeks</span></div>
</div>
<div class="pc">
<div class="pc-top"><div class="pti">Diffusion model (DDPM) — derive the math then implement</div><span class="badge bm">Implement to understand</span></div>
<p>Before writing any code: derive the ELBO yourself. Write out q(xₜ|x₀), p_θ(xₜ₋₁|xₜ), and the simplified loss. Then implement. Compare linear vs cosine noise schedules. Compare DDPM vs DDIM sampling — understand why DDIM is faster without retraining.</p>
<div class="why"><strong>Why diffusion specifically:</strong> Diffusion math — score matching, Langevin dynamics, the ELBO — appears constantly in Phase 4 research. Flow matching, consistency models, and scientific ML applications all build on it. Building one now means those Phase 4 papers are immediately accessible.</div>
<div class="pm"><span class="mt">MNIST → CIFAR</span><span class="mt">FID score</span><span class="mt">Linear vs cosine schedule</span><span class="mt">DDPM vs DDIM</span><span class="mt">~2 weeks</span></div>
</div>

<div class="sl mt32">Papers — Phase 2</div>
<div class="pbox mt16">
<div class="pr"><div class="pn">01</div><div class="pb"><div class="pt">Deep Residual Learning for Image Recognition</div><div class="pa">He, Zhang, Ren & Sun (Microsoft Research), CVPR 2016</div><div class="pw2">Read before implementing. Let the paper's motivation section inform your code. Derive the gradient flow argument (skip connections create a gradient highway) yourself before reading their explanation. Then compare your argument to theirs.</div></div><span class="pd pdf">Every section</span></div>
<div class="pr"><div class="pn">02</div><div class="pb"><div class="pt">Batch Normalization: Accelerating Deep Network Training</div><div class="pa">Ioffe & Szegedy (Google), ICML 2015</div><div class="pw2">Focus on why it works. The loss landscape smoothing interpretation (from Santurkar et al. 2018 — also read that) is the key insight. After reading, explain in your own words why batch norm enables higher learning rates.</div></div><span class="pd pdf">Full + Santurkar 2018</span></div>
<div class="pr"><div class="pn">03</div><div class="pb"><div class="pt">Denoising Diffusion Probabilistic Models (DDPM)</div><div class="pa">Ho, Jain & Abbeel (UC Berkeley), NeurIPS 2020</div><div class="pw2">Read after your implementation — every equation should be familiar from your own derivation. The paper should feel like confirmation, not instruction. Pay attention to the simplified loss and why it outperforms the full ELBO.</div></div><span class="pd pdf">Every equation</span></div>
<div class="pr"><div class="pn">04</div><div class="pb"><div class="pt">Adam: A Method for Stochastic Optimization</div><div class="pa">Kingma & Ba, ICLR 2015</div><div class="pw2">Derive the update rule yourself first. Understand first/second moment estimates, bias correction, and why they matter for sparse gradients. Also understand when Adam fails and SGD+momentum wins — unconditional Adam use signals practitioner mindset, not researcher mindset.</div></div><span class="pd pdf">Derive + full read</span></div>
<div class="pr"><div class="pn">05</div><div class="pb"><div class="pt">How Does Batch Normalization Help Optimization? (Santurkar et al., 2018)</div><div class="pa">NeurIPS 2018 — correction/extension to the original BN paper</div><div class="pw2">The original BN paper's explanation (internal covariate shift reduction) was later shown to be wrong. This paper finds the real mechanism: loss landscape smoothing. Reading both papers teaches you to question even highly cited explanations.</div></div><span class="pd pdc">Core sections</span></div>
<div class="pr"><div class="pn">06</div><div class="pb"><div class="pt">Neural Machine Translation by Jointly Learning to Align and Translate (Bahdanau et al., 2015)</div><div class="pa">The attention mechanism precursor to transformers</div><div class="pw2">The paper that introduced attention. Understanding why attention was needed (fixed-length bottleneck in seq2seq) makes the transformer's design choices obvious. Read before Phase 3.</div></div><span class="pd pdc">Core idea</span></div>
</div>

<div class="sl mt32">Performance expectations</div>
<div class="eg mt16">
<div class="ei"><div class="el">Implementation</div><p>Implement multi-head attention from memory; build ResNet from scratch; train diffusion model</p></div>
<div class="ei"><div class="el">Diagnostics</div><p>Given a failed training run, diagnose whether issue is optimization, data, architecture, or objective within minutes</p></div>
<div class="ei"><div class="el">Systems</div><p>Comfortable with GPU training, mixed precision, memory profiling, and gradient norm logging</p></div>
<div class="ei"><div class="el">Portfolio</div><p>ResNet ablation study on GitHub — clean code, results table, logged experiments, written analysis</p></div>
</div>
<div class="ag mt16">
<div class="ai"><strong>Watch Karpathy's Zero to Hero series first.</strong>All 7 videos, in order, before anything else in Phase 2. He builds from micrograd to a GPT — the cleanest possible path through this material. His code style is what top lab interviewers expect.</div>
<div class="ai"><strong>Use wandb from Day 1.</strong>Log everything: loss, gradient norms, weight norms, learning rate, sample images. You can't debug what you can't see. Wandb is free for personal use and is the standard tool at most labs.</div>
<div class="ai"><strong>Build one reusable training skeleton.</strong>A generic training loop with config files (YAML), wandb logging, LR warmup, gradient clipping, mixed precision, and checkpointing. Every Phase 3–5 project starts from this. Building it once properly saves you hours repeatedly.</div>
<div class="ai"><strong>Post your ablation study publicly.</strong>A ResNet ablation with clean logging and honest analysis gets noticed. This is exactly the kind of work that signals researcher-level thinking to people who might refer you later.</div>
</div>
</div>
</section>

<!-- PHASE 3 -->
<section id="p3" class="ps p3">
<div class="wrap">
<div class="ph"><div class="pnum">P3</div><div><h2>Transformers &amp; Large Language Models</h2><div class="ptl">⏱ Months 17–26 · This is where the split happens</div><p class="ptag">This phase separates ML engineers from AI researchers. The transformer is the substrate of everything. If you haven't felt attention in your hands, you're reasoning about a box you've never opened.</p></div></div>

<div class="mpull">
<div class="mq">Build a GPT. Not because everyone says to — because every paper you'll read for 5 years assumes you understand this architecture at the level of its gradients.</div>
<p>The transformer attention mechanism is the most important architectural idea in AI right now. But don't spend weeks reimplementing RoPE from scratch. <strong>Know what it does, know why it's better than learned positional embeddings, know the mathematical intuition. Then use the reference implementation.</strong></p>
<p>The key mental model: every transformer component is answering a specific question. Multi-head attention: how should information flow between tokens? Layer normalization: how do we keep activations stable during deep forward passes? The residual stream: how do we preserve information while allowing each layer to add to it? When you can answer these fluently, you can reason about every variant as a specific answer to these same questions.</p>
</div>

<div class="sl mt24">Transformer architecture — deep knowledge required</div>
<div class="g3 mt16">
<div class="card"><h3>🔧 Attention Mechanisms</h3><div class="pw"><span class="pill a">Scaled dot-product attention</span><span class="pill a">Multi-head attention — implement this</span><span class="pill a">Grouped-query attention (GQA)</span><span class="pill a">Multi-query attention (MQA)</span><span class="pill a">Cross-attention</span><span class="pill a">Causal masking</span><span class="pill a">KV cache — inference optimization</span><span class="pill a">FlashAttention — intuition</span></div><p class="mt12">Implement MHA from memory. Understand GQA vs MHA tradeoffs — GQA reduces KV cache memory with minimal quality loss. Know why that matters at inference scale.</p></div>
<div class="card"><h3>🏗️ Modern Components</h3><div class="pw"><span class="pill a">RoPE — rotary position embeddings</span><span class="pill a">ALiBi — linear bias</span><span class="pill a">RMSNorm vs LayerNorm</span><span class="pill a">SwiGLU / GLU variants</span><span class="pill a">BPE tokenization</span><span class="pill a">SentencePiece</span><span class="pill a">Mixture of Experts (MoE)</span><span class="pill a">Sliding window attention</span></div><p class="mt12">Implement RoPE once to understand the rotation matrix math. Know what each other component does and why modern LLMs chose it. Use libraries for implementation.</p></div>
<div class="card"><h3>📏 Scaling Laws & Training</h3><div class="pw"><span class="pill a">Kaplan power laws</span><span class="pill a">Chinchilla — compute optimal</span><span class="pill a">Loss vs parameters</span><span class="pill a">Loss vs data tokens</span><span class="pill a">Loss vs FLOP budget</span><span class="pill a">FSDP / DDP</span><span class="pill a">DeepSpeed ZeRO</span><span class="pill a">Gradient checkpointing</span></div><p class="mt12">Run your own mini scaling experiment — train 3 GPT sizes and plot loss vs compute. The intuition this builds cannot come from reading alone.</p></div>
</div>

<div class="sl mt24">LLM architectures — canonical models to know</div>
<div class="g2 mt16">
<div class="card"><h3>📚 Model families to understand</h3><div class="pw"><span class="pill a">GPT-2/3 — decoder-only autoregressive</span><span class="pill a">BERT — encoder-only bidirectional</span><span class="pill a">T5 — encoder-decoder, text-to-text</span><span class="pill a">Llama / Llama-2/3 — modern open LLM</span><span class="pill a">Mistral — sliding window + GQA</span><span class="pill a">Mixtral — sparse MoE</span><span class="pill a">Gemma — Google lightweight</span><span class="pill a">Phi — small but capable</span></div><p class="mt12">Don't implement all of these. Build GPT-style (decoder-only) and BERT-style (encoder-only) from scratch. Read the Llama 2 paper as the reference for how a production LLM is assembled.</p></div>
<div class="card"><h3>🔑 Post-training paradigms</h3><div class="pw"><span class="pill a">Supervised Fine-Tuning (SFT)</span><span class="pill a">RLHF pipeline</span><span class="pill a">Direct Preference Optimization (DPO)</span><span class="pill a">Constitutional AI</span><span class="pill a">LoRA / QLoRA — parameter-efficient FT</span><span class="pill a">Instruction tuning</span><span class="pill a">System prompts &amp; chat templates</span><span class="pill a">PEFT methods</span></div><p class="mt12">Understand the SFT → reward model → RL pipeline conceptually at this stage. You'll implement it properly in Phase 4. Know what LoRA does mathematically — it's now the standard fine-tuning approach.</p></div>
</div>

<div class="sl mt32">Reference materials</div>
<div class="res-grid mt16">
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Andrej Karpathy — "Let's build GPT from scratch" (YouTube)</div><div class="rd">2 hours 13 minutes. Karpathy builds a GPT character-by-character from the "Attention Is All You Need" paper. Watch this before implementing your own. His code is the reference implementation.</div><a href="https://youtube.com/watch?v=kCc8FmEb1nY">youtube.com/watch?v=kCc8FmEb1nY</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Andrej Karpathy — nanoGPT</div><div class="rd">The cleanest GPT implementation available. Study every line. Fork it and add your own components (RoPE, RMSNorm, GQA) to understand the engineering behind modern LLMs.</div><a href="https://github.com/karpathy/nanoGPT">github.com/karpathy/nanoGPT</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">The Illustrated Transformer (Jay Alammar)</div><div class="rd">The best visual explanation of the transformer architecture. Read this alongside the Vaswani et al. paper. The attention visualization is particularly helpful for building the right mental model.</div><a href="https://jalammar.github.io/illustrated-transformer/">jalammar.github.io/illustrated-transformer</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">Stanford CS224N — NLP with Deep Learning</div><div class="rd">Best university NLP/LLM course. Lecture 9 (Transformers) and Lecture 11 (LLMs) are essential. All lecture slides and notes are free online.</div><a href="https://web.stanford.edu/class/cs224n/">web.stanford.edu/class/cs224n</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Hugging Face — Transformers documentation + course</div><div class="rd">Learn to use the Transformers library (load models, tokenizers, fine-tune). The free HF course covers it well. Knowing HF is practical requirement for research work today.</div><a href="https://huggingface.co/course">huggingface.co/course</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Sebastian Raschka — "Build LLMs from Scratch" series</div><div class="rd">Accompanies his free book. Very thorough implementation from scratch. Covers tokenization, pre-training, fine-tuning, and RLHF in a coherent sequence.</div><a href="https://github.com/rasbt/LLMs-from-scratch">github.com/rasbt/LLMs-from-scratch</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Lit-GPT (Lightning AI)</div><div class="rd">Clean, well-documented implementations of Llama, Mistral, Gemma etc. Study the architecture files to understand how modern LLMs differ from vanilla GPT.</div><a href="https://github.com/Lightning-AI/litgpt">github.com/Lightning-AI/litgpt</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Chip Huyen — "Designing Machine Learning Systems"</div><div class="rd">Best book on ML systems in production. Chapter on training infrastructure and serving is important for understanding the gap between research and production.</div><a href="https://www.oreilly.com/library/view/designing-machine-learning/9781098107956/">oreilly.com (free with subscription)</a></div></div>
</div>

<div class="sl mt32">Two flagship projects</div>
<div class="pc">
<div class="pc-top"><div class="pti">GPT from scratch — then use it as a research vehicle</div><span class="badge bd">The defining project of this phase</span></div>
<p>Build the full architecture: BPE tokenizer (or use tiktoken), token + positional embeddings, N transformer blocks (MHA + MLP + LayerNorm + residual), language modeling head. Train on TinyStories — small enough to iterate fast but large enough to show real language modeling.</p>
<p>Then <strong>turn it into a research vehicle:</strong> train three variants at 10M, 50M, and 150M parameters. Plot loss vs training compute. Run a mini scaling law experiment. At what step does in-context learning emerge? Can you find the exact transition where the model starts generalizing rather than memorizing? Write this up as a short paper section.</p>
<div class="why"><strong>Why this teaches what no paper can:</strong> Watching loss curves change as you scale from 10M to 150M builds intuition for scaling that reading Kaplan et al. never gives you. You'll have an answer grounded in your own observation, not just citation. This is what "research taste" means in practice.</div>
<div class="pm"><span class="mt">TinyStories / OpenWebText-small</span><span class="mt">3 model sizes</span><span class="mt">Perplexity tracked</span><span class="mt">Scaling curve plotted</span><span class="mt">ICL emergence analyzed</span><span class="mt">~4–5 weeks</span></div>
</div>
<div class="pc">
<div class="pc-top"><div class="pti">RAG system — evaluation-focused</div><span class="badge bm">Applied + evaluation design</span></div>
<p>Build a retrieval-augmented QA system with FAISS vector retrieval. The system itself is not the point — the evaluation is. Measure: hallucination rate (how often does the model assert things not in retrieved context?), Recall@K (does the right doc get retrieved?), faithfulness, and latency. Design an evaluation suite you'd feel comfortable publishing. This builds evaluation science instincts that matter enormously in Phase 5.</p>
<div class="pm"><span class="mt">FAISS</span><span class="mt">TriviaQA or NQ</span><span class="mt">Hallucination audit</span><span class="mt">Recall@1,5,10</span><span class="mt">~1–2 weeks</span></div>
</div>

<div class="sl mt32">Papers — the transformer canon</div>
<div class="pbox mt16">
<div class="pr"><div class="pn">01</div><div class="pb"><div class="pt">Attention Is All You Need</div><div class="pa">Vaswani et al. (Google Brain), NeurIPS 2017</div><div class="pw2">Read every equation. Implement each component as you read — don't finish then implement; implement each section immediately. The one paper in AI where line-by-line with simultaneous implementation is the only acceptable mode. Pay attention to positional encoding choices and projection matrix dimensions — most common implementation mistakes come from misunderstanding these.</div></div><span class="pd pdf">Every equation + implement</span></div>
<div class="pr"><div class="pn">02</div><div class="pb"><div class="pt">Language Models are Few-Shot Learners (GPT-3)</div><div class="pa">Brown et al. (OpenAI), NeurIPS 2020</div><div class="pw2">Focus on Sections 2 (approach) and 3 (results). Understand in-context learning: why does providing examples in the prompt help without gradient updates? The meta-learning interpretation is the key insight. The scaling results are the empirical foundation of scaling law research.</div></div><span class="pd pdc">Sections 2, 3, 4</span></div>
<div class="pr"><div class="pn">03</div><div class="pb"><div class="pt">Scaling Laws for Neural Language Models</div><div class="pa">Kaplan, McCandlish et al. (OpenAI), 2020</div><div class="pw2">Understand the power law relationships. Read alongside your own mini scaling experiment — compare your observations to Kaplan's predictions. Note what Chinchilla later corrects.</div></div><span class="pd pdf">Full + your experiment</span></div>
<div class="pr"><div class="pn">04</div><div class="pb"><div class="pt">Training Compute-Optimal Large Language Models (Chinchilla)</div><div class="pa">Hoffmann et al. (DeepMind), NeurIPS 2022</div><div class="pw2">The key correction to Kaplan: most large models are undertrained. Given a fixed compute budget, train a smaller model on more data. This shapes every modern training run. Read the experimental methodology carefully — this is how you design experiments to answer a specific empirical question.</div></div><span class="pd pdf">Full — methodology especially</span></div>
<div class="pr"><div class="pn">05</div><div class="pb"><div class="pt">BERT: Pre-training of Deep Bidirectional Transformers</div><div class="pa">Devlin et al. (Google AI), NAACL 2019</div><div class="pw2">Understand bidirectional vs unidirectional pretraining. The masked LM objective is important for interpretability research (what do attention heads attend to?). The fine-tuning paradigm BERT established still underlies instruction-tuned models.</div></div><span class="pd pdc">Sections 1–4</span></div>
<div class="pr"><div class="pn">06</div><div class="pb"><div class="pt">FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness</div><div class="pa">Dao, Fu, Ermon & Ré (Stanford), NeurIPS 2022</div><div class="pw2">Read to understand IO-awareness: the algorithm is O(N²) FLOPs but O(N) memory reads by tiling. You don't need to implement it — but knowing why it's 2–4× faster (memory bandwidth, not compute) is essential for reasoning about long-context model costs.</div></div><span class="pd pds">Motivation + intuition</span></div>
<div class="pr"><div class="pn">07</div><div class="pb"><div class="pt">Llama 2: Open Foundation and Fine-Tuned Chat Models</div><div class="pa">Touvron et al. (Meta AI), 2023</div><div class="pw2">A modern open LLM with full architecture details. Study the training recipe: RoPE, RMSNorm, SwiGLU, GQA, RLHF pipeline. Best single document for understanding how a production LLM is actually assembled. Read after your own GPT implementation — every choice will make sense in context.</div></div><span class="pd pdf">Full technical sections</span></div>
<div class="pr"><div class="pn">08</div><div class="pb"><div class="pt">RoFormer: Enhanced Transformer with Rotary Position Embedding</div><div class="pa">Su et al., 2021</div><div class="pw2">RoPE is now standard in every modern LLM. Understand the rotation matrix formulation and why it preserves relative position information better than learned embeddings. Implement once to understand the math, then use the library version.</div></div><span class="pd pdc">Core method</span></div>
</div>

<div class="sl mt32">Performance expectations</div>
<div class="eg mt16">
<div class="ei"><div class="el">Implementation</div><p>Implement multi-head attention from memory in PyTorch; build GPT from scratch</p></div>
<div class="ei"><div class="el">Tradeoffs</div><p>Explain GQA vs MHA vs MQA tradeoffs; know when KV cache becomes the bottleneck</p></div>
<div class="ei"><div class="el">Scaling</div><p>Explain Chinchilla's implication for model design; run and interpret your own scaling experiment</p></div>
<div class="ei"><div class="el">Systems</div><p>Understand FSDP vs DDP vs pipeline parallelism — when to use each</p></div>
</div>
<div class="ag mt16">
<div class="ai"><strong>Anthropic CodeSignal — start preparing now.</strong>The Anthropic assessment requires 520+/600. Architecture-first system design coding with increasing complexity. Not LeetCode. Clean, well-structured Python solutions to systems problems. Speed and quality both matter.</div>
<div class="ai"><strong>Fork nanoGPT and modify it.</strong>Add RoPE, replace LayerNorm with RMSNorm, add GQA. The process of modifying a working implementation teaches architectural choices faster than building from scratch.</div>
<div class="ai"><strong>Run a real scaling experiment.</strong>Three GPT sizes on TinyStories. Plot loss vs compute. The intuition from your own experiment is qualitatively different from absorbing Kaplan's results by reading.</div>
<div class="ai"><strong>Read the Llama 2 technical report cover to cover.</strong>It's the reference architecture for modern LLMs. Every architectural choice has a reason. Understanding those reasons is what lets you make informed architectural decisions in your own research.</div>
</div>
</div>
</section>

<!-- PHASE 4 -->
<section id="p4" class="ps p4">
<div class="wrap">
<div class="ph"><div class="pnum">P4</div><div><h2>Reinforcement Learning &amp; Advanced Generative Models</h2><div class="ptl">⏱ Months 26–42 · Target: PhD-level depth in your chosen domain</div><p class="ptag">The phase where you start thinking like a DeepMind researcher. RL for reasoning, RLHF pipelines, diffusion at scale, multimodal systems, and mechanistic interpretability.</p></div></div>

<div class="mpull">
<div class="mq">You are no longer a student. You are a scientist. Formulate a hypothesis before every experiment.</div>
<p>The mental model shifts entirely. You're not absorbing knowledge — you're generating it. Before every experiment: write your hypothesis in one sentence and your null hypothesis in another. What result would make you discard the hypothesis? If you can't answer that, redesign the experiment.</p>
<p><strong>On failure:</strong> 90% of experiments fail — not "produce worse results than expected," they fail to provide evidence for your hypothesis. This is normal. Each failure is a data point. A researcher who produces 10 failed experiments and learns from each is more valuable than one who produces two successes without understanding why they worked.</p>
</div>

<div class="sl mt24">Reinforcement Learning — full curriculum</div>
<div class="drow mt16">
<div class="di dm"><span class="dl">Foundational RL — understand deeply</span><ul><li>Markov Decision Processes (MDPs)</li><li>Bellman equations — derive them</li><li>Value functions V(s) and Q(s,a)</li><li>Policy gradients — REINFORCE derivation</li><li>Actor-Critic methods</li><li>Advantage estimation (GAE)</li><li>Q-learning and DQN</li><li>Experience replay & target networks</li><li>Exploration vs exploitation</li><li>Temporal difference learning</li></ul></div>
<div class="di do"><span class="dl">Modern RL — know deeply</span><ul><li>PPO — implement from scratch</li><li>SAC (Soft Actor-Critic)</li><li>TD3 (Twin Delayed DDPG)</li><li>RLHF pipeline (SFT → RM → PPO)</li><li>Reward modeling</li><li>KL penalty in PPO objective</li><li>DreamerV3 — world models</li><li>MuZero — model-based planning</li><li>RLVR for reasoning (DeepSeek-R1 style)</li></ul></div>
<div class="di ds"><span class="dl">Know what they are</span><ul><li>Multi-agent RL</li><li>Hierarchical RL</li><li>Offline RL / conservative Q-learning</li><li>Inverse RL / imitation learning</li><li>Meta-RL</li></ul></div>
</div>

<div class="sl mt24">RL reference materials</div>
<div class="res-grid mt16">
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Reinforcement Learning: An Introduction (Sutton & Barto)</div><div class="rd">The canonical RL textbook. Free PDF. Chapters 1–7 cover tabular methods; Chapters 9–13 cover function approximation and policy gradients. Read alongside implementation.</div><a href="http://incompleteideas.net/book/the-book-2nd.html">incompleteideas.net/book</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">David Silver — UCL RL Course (DeepMind / YouTube)</div><div class="rd">10 lectures by the AlphaGo creator. Still the best structured RL course. Lectures 4–7 on model-free prediction, control, and function approximation are the core.</div><a href="https://youtube.com/playlist?list=PLqYmG7hTraZDM-OYHWgPebj2MfCFzFObQ">youtube.com/david-silver-rl</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">Spinning Up in Deep RL (OpenAI)</div><div class="rd">OpenAI's free RL educational resource. Covers key algorithms (VPG, PPO, SAC, TD3) with clean PyTorch implementations and explanations. The best starting point for deep RL implementation.</div><a href="https://spinningup.openai.com">spinningup.openai.com</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">CleanRL — clean single-file RL implementations</div><div class="rd">Every major RL algorithm (PPO, SAC, DQN, TD3) in a single readable Python file with wandb integration. Best reference for "what does a correct PPO implementation actually look like?"</div><a href="https://github.com/vwxyzjn/cleanrl">github.com/vwxyzjn/cleanrl</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Hugging Face — Deep RL Course</div><div class="rd">Free course covering DQN, Policy Gradients, PPO, and RLHF with implementations. Particularly good on RLHF section and how RL connects to LLM alignment.</div><a href="https://huggingface.co/learn/deep-rl-course">huggingface.co/learn/deep-rl-course</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Lilian Weng's blog — RL posts</div><div class="rd">The best free blog for RL theory. Her posts on policy gradients, model-based RL, and exploration are the clearest technical summaries available anywhere.</div><a href="https://lilianweng.github.io">lilianweng.github.io</a></div></div>
</div>

<div class="sl mt24">Advanced Generative Models — full curriculum</div>
<div class="g2 mt16">
<div class="card"><h3>🎨 Generative model landscape</h3><div class="pw"><span class="pill r">VAE — ELBO, reparameterization trick</span><span class="pill r">GAN variants — WGAN, StyleGAN</span><span class="pill r">DDPM — already implemented</span><span class="pill r">DDIM — deterministic sampling</span><span class="pill r">Classifier-free guidance (CFG)</span><span class="pill r">Score matching</span><span class="pill r">Flow matching (Lipman et al.)</span><span class="pill r">Consistency models</span><span class="pill r">Stable Diffusion architecture</span><span class="pill r">DiT — diffusion transformers</span></div></div>
<div class="card"><h3>🤝 Multimodal Systems</h3><div class="pw"><span class="pill r">CLIP — contrastive image-text training</span><span class="pill r">Flamingo — few-shot multimodal</span><span class="pill r">BLIP / BLIP-2</span><span class="pill r">LLaVA — vision-language</span><span class="pill r">DALL-E / Stable Diffusion</span><span class="pill r">ImageBind — cross-modal embedding</span><span class="pill r">GPT-4V / Claude Vision</span><span class="pill r">Video understanding (VideoLLaMA)</span></div></div>
</div>

<div class="sl mt24">Mechanistic Interpretability — full curriculum</div>
<div class="card mt16">
<h3>🔬 Interpretability — especially if targeting Anthropic</h3>
<div class="pw"><span class="pill r">Residual stream — information flow model</span><span class="pill r">Attention head analysis</span><span class="pill r">MLP neurons as key-value memories</span><span class="pill r">Superposition hypothesis</span><span class="pill r">Sparse autoencoders (SAEs)</span><span class="pill r">Circuit discovery — attention head circuits</span><span class="pill r">Activation patching</span><span class="pill r">Path patching</span><span class="pill r">Causal tracing (ROME / MEMIT)</span><span class="pill r">Logit lens</span><span class="pill r">Feature visualization</span><span class="pill r">Probing classifiers</span><span class="pill r">Knowledge editing</span></div>
<p class="mt12"><strong>Tools:</strong> TransformerLens (Neel Nanda) is the standard library. circuitsvis for visualization. The Alignment Forum and Anthropic's interpretability team blog are the primary literature sources.</p>
</div>

<div class="sl mt24">Interpretability reference materials</div>
<div class="res-grid mt16">
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Neel Nanda — TransformerLens tutorials (YouTube)</div><div class="rd">Neel Nanda (interpretability researcher, ex-Anthropic/DeepMind) has a full YouTube tutorial series on mechanistic interpretability using TransformerLens. The best starting point for this field.</div><a href="https://youtube.com/@neelnanda-io">youtube.com/@neelnanda-io</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">TransformerLens (Neel Nanda)</div><div class="rd">The standard library for mechanistic interpretability. Built specifically for studying GPT-2 and similar models. Has hooks into every activation, attention pattern, and MLP layer.</div><a href="https://github.com/neelnanda-io/TransformerLens">github.com/neelnanda-io/TransformerLens</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Anthropic's Transformer Circuits Thread</div><div class="rd">The series of papers from Anthropic's interpretability team. Start with "A Mathematical Framework for Transformer Circuits" then "In-context Learning and Induction Heads." These define the field.</div><a href="https://transformer-circuits.pub">transformer-circuits.pub</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Alignment Forum — interpretability posts</div><div class="rd">Primary venue for interpretability research preprints. Follow Neel Nanda, Chris Olah, Tom Lieberum. The quality of discussion here often exceeds what appears in conference papers.</div><a href="https://alignmentforum.org">alignmentforum.org</a></div></div>
</div>

<div class="sl mt24">Representation Learning</div>
<div class="g2 mt16">
<div class="card"><h3>🧩 Self-supervised & Contrastive Learning</h3><div class="pw"><span class="pill r">SimCLR — contrastive loss</span><span class="pill r">MoCo / MoCo-v2</span><span class="pill r">BYOL — no negative pairs</span><span class="pill r">DINO — knowledge distillation</span><span class="pill r">MAE — masked autoencoders</span><span class="pill r">CLIP — cross-modal</span><span class="pill r">Data2Vec — unified SSL</span></div><p class="mt12">Implement CLIP at small scale to understand contrastive training. The idea of a joint embedding space for image and text is the foundation of all modern multimodal models.</p></div>
<div class="card"><h3>📈 Post-Training Methods</h3><div class="pw"><span class="pill r">SFT — supervised fine-tuning</span><span class="pill r">RLHF — full pipeline</span><span class="pill r">DPO — direct preference optimization</span><span class="pill r">KTO — Kahneman-Tversky optimization</span><span class="pill r">GRPO — group relative policy optimization</span><span class="pill r">LoRA / QLoRA</span><span class="pill r">ORPO — odds ratio preference optimization</span></div><p class="mt12">Implement an end-to-end RLHF pipeline on a toy LM: SFT → reward model → PPO fine-tuning. Compare against DPO on the same preference dataset. This is the highest-demand research area at all frontier labs.</p></div>
</div>

<div class="sl mt32">Reference materials — advanced generative & multimodal</div>
<div class="res-grid mt16">
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Lilian Weng's blog — diffusion and generative models</div><div class="rd">Her posts on "What are Diffusion Models?" and "Score-Based Generative Modeling" are the best free technical summaries. Dense but precise. Read alongside the DDPM and score matching papers.</div><a href="https://lilianweng.github.io">lilianweng.github.io</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Yannic Kilcher — DDPM, AlphaFold, CLIP paper walkthroughs</div><div class="rd">His video walkthroughs of these specific papers are exceptionally clear. Watch the DDPM video after your own implementation, the AlphaFold video before reading the paper.</div><a href="https://youtube.com/@YannicKilcher">youtube.com/@YannicKilcher</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">Berkeley Deep Unsupervised Learning course (CS294-158)</div><div class="rd">Best university course on generative models. Covers VAEs, flows, GANs, diffusion, and autoregressive models. All lectures free on YouTube. Peter Abbeel's lectures are particularly strong.</div><a href="https://sites.google.com/view/berkeley-cs294-158-sp24">CS294-158 course page</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Diffusers (Hugging Face)</div><div class="rd">The standard library for diffusion models. Study the source code for DDPM and DDIM schedulers — they're clean enough to learn from. Use it for all Phase 4 diffusion experiments.</div><a href="https://github.com/huggingface/diffusers">github.com/huggingface/diffusers</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">TRL (Hugging Face) — RLHF / DPO / PPO library</div><div class="rd">Standard library for post-training research. Implements DPO, PPO, KTO, GRPO. Study the trainer source code before using it — understanding the implementation catches subtle bugs in your own work.</div><a href="https://github.com/huggingface/trl">github.com/huggingface/trl</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">The RLHF Book (Nathan Lambert et al.)</div><div class="rd">Free online. Most comprehensive treatment of RLHF, DPO, and post-training methods available. Written by a researcher (Nathan Lambert, formerly Anthropic/HuggingFace). Updated regularly.</div><a href="https://rlhfbook.com">rlhfbook.com</a></div></div>
</div>

<div class="sl mt32">Core projects for Phase 4</div>
<div class="pc">
<div class="pc-top"><div class="pti">PPO from scratch → Atari (RL track)</div><span class="badge bd">Track-specific build</span></div>
<p>Implement PPO from the original Schulman et al. paper. Train on CartPole first to verify correctness (convergence within 300 episodes). Scale to Atari (Breakout or Pong). Measure sample efficiency. Compare against DQN baseline on the same game. Document hyperparameter sensitivity — PPO is notoriously sensitive to clip ratio, entropy coefficient, and learning rate.</p>
<div class="pm"><span class="mt">OpenAI Gym</span><span class="mt">CartPole → Atari</span><span class="mt">Sample efficiency comparison vs DQN</span><span class="mt">HP sensitivity analysis</span><span class="mt">~2–3 weeks</span></div>
</div>
<div class="pc">
<div class="pc-top"><div class="pti">RLHF pipeline on a toy LM</div><span class="badge bd">Highest-demand skill</span></div>
<p>End-to-end RLHF: start with a pretrained small LM → SFT on instruction data → reward model training on preference pairs → PPO fine-tuning with KL penalty. Then implement DPO on the same preference dataset. Compare win rates. Understand empirically where DPO breaks (highly skewed preference data) vs where it's more stable than PPO.</p>
<div class="why"><strong>Why this is the single most important Phase 4 project:</strong> Post-training is the hottest research area at every frontier lab. An implemented RLHF pipeline you can talk about in depth — including its failure modes — is a major signal in research interviews. The HuggingFace TRL library is your starting reference.</div>
<div class="pm"><span class="mt">Anthropic-HH or UltraFeedback dataset</span><span class="mt">Win rate vs baseline</span><span class="mt">KL divergence from base model</span><span class="mt">PPO vs DPO comparison</span><span class="mt">~3–4 weeks</span></div>
</div>
<div class="pc">
<div class="pc-top"><div class="pti">Sparse autoencoder for LLM interpretability (interp track)</div><span class="badge bm">Track-specific</span></div>
<p>Train sparse autoencoders on residual stream activations from GPT-2-small or a small Llama. Identify interpretable features — features that respond to semantically coherent inputs. Use activation patching to verify that specific features causally influence outputs. Document what you find: which features are interpretable, which aren't, what does the monosemanticity ratio look like? Write up as a short interpretability report.</p>
<div class="pm"><span class="mt">GPT-2-small</span><span class="mt">TransformerLens</span><span class="mt">Feature interpretability score</span><span class="mt">Causal effect verification</span><span class="mt">~3 weeks</span></div>
</div>
<div class="pc">
<div class="pc-top"><div class="pti">CLIP reproduction at small scale (multimodal track)</div><span class="badge bm">Track-specific</span></div>
<p>Reproduce CLIP's contrastive image-text training on a smaller dataset (MSCOCO). Evaluate zero-shot classification and image-text retrieval. Analyze which types of captions improve alignment. Compare CLIP vs ALIGN-style training. This gives you hands-on experience with the paradigm underlying every modern VLM.</p>
<div class="pm"><span class="mt">MSCOCO</span><span class="mt">Recall@K retrieval</span><span class="mt">Zero-shot accuracy on ImageNet</span><span class="mt">~2–3 weeks</span></div>
</div>

<div class="sl mt32">Papers — Phase 4 (by subdomain)</div>
<div class="pbox mt16">
<div class="pr"><div class="pn">RL01</div><div class="pb"><div class="pt">Playing Atari with Deep Reinforcement Learning (DQN)</div><div class="pa">Mnih et al. (DeepMind), 2015</div><div class="pw2">The bridge between deep learning and RL. Experience replay and target networks are the two key insights. Implement this before PPO to understand why on-policy methods (PPO) were developed in response to DQN's sample inefficiency.</div></div><span class="pd pdf">Full</span></div>
<div class="pr"><div class="pn">RL02</div><div class="pb"><div class="pt">Proximal Policy Optimization Algorithms (PPO)</div><div class="pa">Schulman et al. (OpenAI), 2017</div><div class="pw2">Implement this. Understand the clipped surrogate objective — why it prevents large policy updates. Know the difference between PPO-Clip and PPO-Penalty. This is used in RLHF and is the workhorse RL algorithm at every frontier lab.</div></div><span class="pd pdf">Implement</span></div>
<div class="pr"><div class="pn">RL03</div><div class="pb"><div class="pt">Training Language Models to Follow Instructions (InstructGPT / RLHF)</div><div class="pa">Ouyang et al. (OpenAI), NeurIPS 2022</div><div class="pw2">The RLHF paper. SFT → RM → PPO pipeline in full detail. Understand the KL penalty in the PPO objective, reward model training, and why the three-stage pipeline produces instruction-following behavior. Know its limitations.</div></div><span class="pd pdf">Every section</span></div>
<div class="pr"><div class="pn">RL04</div><div class="pb"><div class="pt">Direct Preference Optimization (DPO)</div><div class="pa">Rafailov et al. (Stanford), NeurIPS 2023</div><div class="pw2">Reparameterizes the reward function in terms of the policy, eliminating explicit RM and RL training. Understand the mathematical derivation — how DPO connects to the optimal RLHF solution. Know where it fails: highly skewed preferences, distribution shift at inference.</div></div><span class="pd pdf">Full + derive</span></div>
<div class="pr"><div class="pn">RL05</div><div class="pb"><div class="pt">Mastering the Game of Go without Human Knowledge (AlphaGo Zero)</div><div class="pa">Silver et al. (DeepMind), Nature 2017</div><div class="pw2">First-principles innovation in RL. Self-play + MCTS + value/policy network. The paper DeepMind interviewers know you've read. Focus on how the inductive bias (tree search) was integrated with neural networks.</div></div><span class="pd pdf">Full</span></div>
<div class="pr"><div class="pn">GEN01</div><div class="pb"><div class="pt">Denoising Diffusion Probabilistic Models (already read in P2)</div><div class="pa">Ho et al. — revisit at a deeper level</div><div class="pw2">Re-read now with focus on the score matching connection. Understand why the simplified loss (predicting epsilon) works better than the full ELBO. This connection to Tweedie's formula is what makes modern samplers like DDIM possible.</div></div><span class="pd pdc">Score matching focus</span></div>
<div class="pr"><div class="pn">GEN02</div><div class="pb"><div class="pt">Flow Matching for Generative Modeling</div><div class="pa">Lipman et al. (Meta AI), ICLR 2023</div><div class="pw2">The next generation after diffusion. Simpler training objective (vector field regression), straight-line probability paths, faster sampling. This is the architecture behind Stable Diffusion 3 and Flux. Understand how it relates to DDPM.</div></div><span class="pd pdc">Core method</span></div>
<div class="pr"><div class="pn">MM01</div><div class="pb"><div class="pt">Learning Transferable Visual Models (CLIP)</div><div class="pa">Radford et al. (OpenAI), ICML 2021</div><div class="pw2">Contrastive learning at scale for image-text pairs. The joint embedding space enables zero-shot transfer. Understand why contrastive training with large batches works, and what ImageNet zero-shot performance reveals about learned representations.</div></div><span class="pd pdf">Full</span></div>
<div class="pr"><div class="pn">INT01</div><div class="pb"><div class="pt">Towards Monosemanticity: Decomposing Language Models with Dictionary Learning</div><div class="pa">Templeton et al. (Anthropic), 2023</div><div class="pw2">The state-of-the-art interpretability paper. Superposition hypothesis, why neurons are polysemantic, how SAEs extract monosemantic features. If this paper excites you more than the RL papers — interpretability is your track. Read appendices for implementation details.</div></div><span class="pd pdf">Interp track: everything</span></div>
<div class="pr"><div class="pn">SCI01</div><div class="pb"><div class="pt">Highly Accurate Protein Structure Prediction with AlphaFold</div><div class="pa">Jumper et al. (DeepMind), Nature 2021 — Nobel Prize 2024</div><div class="pw2">Even if not doing scientific ML, read the introduction to understand how domain-specific inductive bias (evolutionary covariation) was engineered into the architecture. This is what research taste looks like: finding the right inductive bias for a specific problem.</div></div><span class="pd pds">All tracks: intro + architecture</span></div>
</div>

<div class="sl mt32">Performance expectations</div>
<div class="eg mt16">
<div class="ei"><div class="el">Research depth</div><p>Identify limitations in recent papers in your track; have original hypotheses about what to try next</p></div>
<div class="ei"><div class="el">Implementation</div><p>Implement PPO from scratch; build RLHF pipeline; implement sparse autoencoders (if interp track)</p></div>
<div class="ei"><div class="el">Safety fluency</div><p>Explain Constitutional AI and its limitations; discuss scalable oversight problem; know DPO vs RLHF tradeoffs</p></div>
<div class="ei"><div class="el">Research log</div><p>Detailed log of all experiments: hypothesis, design, result, interpretation. Every failure documented.</p></div>
</div>
<div class="ag mt16">
<div class="ai"><strong>Lab-specific preparation begins here.</strong>Anthropic: safety + interpretability. OpenAI: shipping velocity + AGI framing. DeepMind: mathematical rigor + research taste. Prepare for the specific lab you're targeting, not generic "ML interviews."</div>
<div class="ai"><strong>Warm introductions matter far more than cold applications.</strong>Publish on arXiv. Contribute to TransformerLens, Diffusers, or TRL. Post about your findings. Be findable by the researchers doing work you want to join.</div>
<div class="ai"><strong>Lilian Weng's blog is your best free resource.</strong>Her technical summaries of RL, diffusion, and alignment are the best available anywhere. Read every post in your track. Then read her other posts — the breadth is valuable context.</div>
<div class="ai"><strong>Subscribe to arXiv alerts for your track.</strong>Set up alerts for cs.LG, cs.AI, and your specific topic (e.g., "reinforcement learning from human feedback"). Read every abstract. Flag the ones worth going deeper on. Build your reading habit now.</div>
</div>
</div>
</section>

<!-- PHASE 5 -->
<section id="p5" class="ps p5">
<div class="wrap">
<div class="ph"><div class="pnum">P5</div><div><h2>Specialization, Publication &amp; Research Identity</h2><div class="ptl">⏱ Months 42+ · Ongoing — this phase doesn't end</div><p class="ptag">Build a recognizable identity. Publish work the field engages with. Become someone who sets directions, not just follows them.</p></div></div>

<div class="mpull">
<div class="mq">Depth matters more than novelty scattered across many domains. One research identity, made recognizable.</div>
<p>Publication is the primary currency of research credibility, but the goal isn't publication count — it's publications that matter. A single strong paper at NeurIPS or ICML that people read, cite, and build on is worth more than five workshop papers no one engages with. Quality over quantity, always.</p>
<p><strong>The publication workflow:</strong> Read 100 papers in your area → Reproduce 20 → Identify limitations in 5 → Form hypotheses about 3 → Run ablations on 2 → Write up 1. The funnel is steep. 90% of experiments fail. That's the research process, not a failure of the researcher.</p>
<p><strong>On negative results:</strong> Aim for high-quality negative results with honest limitations when evidence doesn't support your hypothesis. These are publishable and respected — they save others from dead ends. Reviewers can spot p-hacking and post-hoc rationalization; intellectual honesty is a competitive advantage.</p>
</div>

<div class="sl mt24">Choose one specialization track — and commit</div>
<div class="ins r mt16"><strong>The most common mistake:</strong> trying to be a generalist because you're afraid of missing out. Every frontier lab researcher has a track. The question isn't whether to specialize — it's which track to commit to. Look back at your Phase 3–4 projects: which papers did you read past the abstract? Which experiments excited you most? That's where your specialization is.</div>

<div class="tg mt16">
<div class="tc"><div class="tn">🔍 Mechanistic Interpretability</div><ul><li class="hot">Sparse autoencoders at scale</li><li class="hot">Circuit discovery in large models</li><li class="hot">Superposition and polysemanticity</li><li>Feature steering / activation editing</li><li>Causal tracing across layers</li><li>Probing and behavioral benchmarks</li><li class="note">Best track for Anthropic. Hottest area in safety research right now.</li></ul></div>
<div class="tc"><div class="tn">⚡ Post-Training &amp; Alignment</div><ul><li class="hot">RLHF / DPO / KTO / GRPO variants</li><li class="hot">Reward model quality and calibration</li><li class="hot">Preference data quality research</li><li>Sycophancy and reward hacking</li><li>Constitutional AI variants</li><li>Refusal calibration</li><li class="note">Highest demand at all frontier labs. Very competitive.</li></ul></div>
<div class="tc"><div class="tn">🧮 Reasoning &amp; RL for LLMs</div><ul><li class="hot">RLVR for math / code reasoning</li><li class="hot">Inference-time compute scaling (o1/R1 style)</li><li class="hot">Process reward models (PRMs)</li><li>Chain-of-thought training</li><li>DeepSeek-R1 style self-play</li><li>Tree search + LLMs</li><li class="note">Exploding area after DeepSeek-R1, o1, and Gemini Thinking.</li></ul></div>
<div class="tc"><div class="tn">🖼️ Multimodal Systems</div><ul><li class="hot">Vision-language alignment</li><li class="hot">Video understanding</li><li>VLA models for robotics</li><li>Cross-modal fine-tuning</li><li>Audio-visual-text models</li><li class="note">Strong at Google DeepMind and Meta AI.</li></ul></div>
<div class="tc"><div class="tn">🎨 Generative Models</div><ul><li class="hot">Flow matching (Flux / SD3 style)</li><li class="hot">Consistency models</li><li>Video generation (Sora-style)</li><li>3D generation</li><li>Diffusion for scientific data</li><li class="note">Strong at Stability AI, Adobe Research, academic labs.</li></ul></div>
<div class="tc"><div class="tn">⚙️ Efficient AI</div><ul><li>Quantization (AWQ, GPTQ, FP8)</li><li>Speculative decoding</li><li>Sparse MoE architectures</li><li>Knowledge distillation at scale</li><li>vLLM / PagedAttention systems</li><li class="note">High value for production roles. Less prestigious for pure RS.</li></ul></div>
<div class="tc"><div class="tn">🔬 Scientific ML</div><ul><li>Protein structure (AlphaFold style)</li><li>Drug discovery / molecular modeling</li><li>Materials science</li><li>Climate / physics modeling</li><li>Graph neural networks</li><li class="note">DeepMind speciality. Nobel Prize-level impact potential.</li></ul></div>
<div class="tc"><div class="tn">🤖 Agents &amp; Tool Use</div><ul><li class="hot">LLM agents with tool use</li><li class="hot">Multi-agent systems</li><li>Long-horizon task completion</li><li>Memory and retrieval in agents</li><li>Code generation agents</li><li class="note">Fast-growing. OpenAI and Anthropic both hiring heavily here.</li></ul></div>
</div>

<div class="sl mt32">What publication-quality research looks like</div>
<div class="g2 mt16">
<div class="card">
<h3>📝 Structure of a strong paper</h3>
<div class="tl mt8">
<div class="tli act"><div class="tt">A clear, specific problem statement</div><div class="td">Not "improve LLM alignment" — "reward models trained on human preferences show systematic sycophancy on long-context inputs; we propose and evaluate a mitigation." Specificity is everything.</div></div>
<div class="tli act"><div class="tt">A hypothesis with a falsifiable test</div><div class="td">Before any experiment: what result would cause you to reject this hypothesis? If you can't answer, redesign the experiment. This is the line between science and demo.</div></div>
<div class="tli act"><div class="tt">Strong baselines, properly implemented</div><div class="td">The most common reviewer complaint. Run every baseline at its best configuration, not its defaults. A weak baseline inflates your apparent contribution.</div></div>
<div class="tli act"><div class="tt">Ablation studies that isolate each component</div><div class="td">Remove one component at a time. If your method has three novel pieces and they're always used together, reviewers cannot evaluate your contribution.</div></div>
<div class="tli act"><div class="tt">Honest limitations section</div><div class="td">Where does your method fail? Being honest about this increases credibility — it signals you understand your own work. Reviewers who discover your limitations for you will be hostile.</div></div>
<div class="tli act"><div class="tt">Reproducibility artifacts</div><div class="td">Code, model weights, evaluation data, random seeds. Top venues increasingly require this. Your replication score affects long-term reputation significantly.</div></div>
</div>
</div>
<div class="card">
<h3>🎯 Venue targeting strategy</h3>
<p style="font-size:13px;color:var(--muted);margin-bottom:12px">Match your work to the venue's identity and review standards:</p>
<div class="pw"><span class="pill p">NeurIPS — broad ML, theory + empirical</span><span class="pill p">ICML — theory-heavy, methods</span><span class="pill p">ICLR — DL, representations, open review</span><span class="pill p">ACL / EMNLP — NLP-specific</span><span class="pill p">CVPR / ICCV — computer vision</span><span class="pill p">ICRA / CoRL — robotics</span><span class="pill p">FAccT / AIES — fairness and safety</span></div>
<p class="mt12" style="font-size:12.5px;color:var(--muted)"><strong style="color:var(--text)">Workshop strategy:</strong> Submit to NeurIPS/ICML/ICLR workshops first. Lower bar, real review experience, a publication line, and a deadline that forces completion. Your first full conference paper will be better for having been through a workshop review cycle.</p>
<p class="mt8" style="font-size:12.5px;color:var(--muted)"><strong style="color:var(--text)">For Anthropic:</strong> SoLaR (Socially Responsible Language Modeling), AISafety workshops. <strong style="color:var(--text)">For DeepMind:</strong> NeurIPS or ICML main track. <strong style="color:var(--text)">For OpenAI:</strong> Any strong venue in your specialization.</p>
</div>
</div>

<div class="sl mt32">High-value project ideas — pick one to drive to a paper</div>
<div class="pc">
<div class="pc-top"><div class="pti">Reproduce a recent paper — then find its hole</div><span class="badge bd">The research loop in miniature</span></div>
<p>Pick a paper from the last 12 months in your chosen track. <strong>Reproduce its main result exactly</strong> — not approximately, exactly. Get the same numbers within noise. This alone is underrated: fewer than 10% of people who read a paper can fully reproduce it. The debugging journey teaches you more than the paper itself.</p>
<p>Then: careful ablation to identify one limitation the authors didn't fully explore. Form a hypothesis. Run the experiment. If positive — core of a workshop paper. If negative — well-documented negative result the field benefits from knowing. Either way, you have a submission.</p>
<div class="why"><strong>The research loop:</strong> Read → Understand every design choice → Reproduce exactly → Identify one unexplored question → Hypothesize → Ablate → Write. This loop done well on one paper produces more learning than shallowly skimming 50. It's also how publications happen.</div>
<div class="pm"><span class="mt">Track-specific paper from last 12 months</span><span class="mt">Full reproduction with matching numbers</span><span class="mt">One ablation-driven contribution</span><span class="mt">Aim for workshop submission</span><span class="mt">~6–10 weeks</span></div>
</div>

<div class="pc">
<div class="pc-top"><div class="pti">Novel post-training method targeting a specific failure mode</div><span class="badge bd">Highest demand area</span></div>
<p>Design a method that addresses one well-documented failure mode of DPO or RLHF: sycophancy in reward models, distribution shift between SFT and RL phases, reward hacking in math reasoning (RLVR), or KL collapse during PPO. The key is specificity — don't try to improve post-training "in general." One failure mode. One targeted intervention. Ablations against DPO and KTO baselines. Careful measurement.</p>
<div class="pm"><span class="mt">Anthropic-HH / UltraFeedback / MATH dataset</span><span class="mt">Win rate vs DPO baseline</span><span class="mt">AlpacaEval 2.0</span><span class="mt">Ablation study mandatory</span></div>
</div>

<div class="pc">
<div class="pc-top"><div class="pti">Evaluation benchmark for a specific reliability problem</div><span class="badge bm">High citation potential</span></div>
<p>The field needs better evaluation. Design a benchmark testing one specific reliability problem — hallucination on multi-hop reasoning, calibration under adversarial perturbations, consistency across paraphrased inputs, or sycophancy in preference elicitation. Validate with human agreement ≥0.8. Release with full contamination analysis and code. Good evaluation work has extremely high citation rates because everyone in the field needs it.</p>
<div class="pm"><span class="mt">Custom dataset with human validation</span><span class="mt">Human agreement score ≥0.8</span><span class="mt">Contamination analysis</span><span class="mt">Public release with full documentation</span></div>
</div>

<div class="pc">
<div class="pc-top"><div class="pti">Mechanistic interpretability: circuit for a specific capability</div><span class="badge bm">Core Anthropic track</span></div>
<p>Identify and verify the circuit in a small LLM responsible for a specific capability: indirect object identification, greater-than comparison, grammatical agreement, or modular arithmetic. Use activation patching, path patching, and attention head analysis. Document every step. Apply the methodology from Anthropic's published work (TransformerLens, causal tracing) to a capability they haven't studied yet.</p>
<div class="pm"><span class="mt">GPT-2-small</span><span class="mt">TransformerLens</span><span class="mt">Causal effect size documented</span><span class="mt">Circuit diagram verified</span></div>
</div>

<div class="sl mt32">Advanced papers — frontier research</div>
<div class="pbox mt16">
<div class="pr"><div class="pn">01</div><div class="pb"><div class="pt">Constitutional AI: Harmlessness from AI Feedback</div><div class="pa">Bai et al. (Anthropic), 2022</div><div class="pw2">Must-read for Anthropic candidates. The RLHF-from-AI-feedback mechanism: constitutional principles guide a feedback model, which trains the policy. Know limitations: over-refusal, value specification challenges, bootstrap reliability. Interviewers test whether you've genuinely engaged with this.</div></div><span class="pd pdf">Alignment track: every section</span></div>
<div class="pr"><div class="pn">02</div><div class="pb"><div class="pt">Chain-of-Thought Prompting Elicits Reasoning in Large Language Models</div><div class="pa">Wei et al. (Google Brain), NeurIPS 2022</div><div class="pw2">Why step-by-step reasoning improves accuracy. The emergent behavior claim (only works above a certain scale) has been contested — understand both the original claims and Mirzadeh et al.'s 2024 critique showing CoT helps even small models. Reasoning track: read every paper that cites this.</div></div><span class="pd pdf">Reasoning track: full + followup</span></div>
<div class="pr"><div class="pn">03</div><div class="pb"><div class="pt">Toolformer: Language Models Can Teach Themselves to Use Tools</div><div class="pa">Schick et al. (Meta AI), NeurIPS 2023</div><div class="pw2">Self-supervised tool use: model generates API call candidates, executes them, keeps calls that reduce perplexity. Elegant bootstrap procedure. Understand the limitations — poor generalization to novel tools. Essential for agents track.</div></div><span class="pd pdc">Agents track: full. Others: method only</span></div>
<div class="pr"><div class="pn">04</div><div class="pb"><div class="pt">DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning</div><div class="pa">DeepSeek AI, 2025</div><div class="pw2">The paper that showed RL (GRPO) alone, applied to reasoning tasks, can produce chain-of-thought reasoning without supervised CoT data. Study the GRPO algorithm, the format reward, and why the model develops "thinking" behavior. This is the current state-of-the-art direction for reasoning research.</div></div><span class="pd pdf">Reasoning track: every section</span></div>
<div class="pr"><div class="pn">05</div><div class="pb"><div class="pt">Segment Anything (SAM)</div><div class="pa">Kirillov et al. (Meta AI), ICCV 2023</div><div class="pw2">Foundation model approach applied to segmentation. Even if not doing vision, read the data engine section — the process of using the model to annotate more data for itself is a paradigm appearing across domains. The promptable model interface is architecturally important.</div></div><span class="pd pds">Data engine + methodology</span></div>
<div class="pr"><div class="pn">06</div><div class="pb"><div class="pt">DreamerV3: Mastering Diverse Domains through World Models</div><div class="pa">Hafner et al. (DeepMind), ICML 2023</div><div class="pw2">World models for RL across completely different domains (Atari, continuous control, Minecraft) with the same hyperparameters. The generality is the contribution. Essential for RL track; shows what "research taste" looks like in practice — finding one algorithmic idea that generalizes broadly.</div></div><span class="pd pdc">RL track essential</span></div>
<div class="pr"><div class="pn">07</div><div class="pb"><div class="pt">Scalable Oversight: Supervising AI Systems Using AI Assistance</div><div class="pa">Bowman et al. (OpenAI / Anthropic), 2022</div><div class="pw2">The scalable oversight problem: how do you supervise AI systems that can outperform human evaluators? Debate protocol, amplification, and consistency checking. Understanding this problem is expected for any safety-focused research interview at Anthropic.</div></div><span class="pd pdc">Alignment track</span></div>
<div class="pr"><div class="pn">08</div><div class="pb"><div class="pt">Technical reports: Claude 3, GPT-4, Gemini 1.5 (match to target lab)</div><div class="pa">Anthropic / OpenAI / Google DeepMind, 2023–2024</div><div class="pw2">Read the technical report of the model you'd be working with. DeepMind interviewers assume you've read the Gemini report. Anthropic interviewers assume you've read the Claude reports. Know their evaluation methodologies, training procedures, and stated limitations. These are the systems you'd be improving.</div></div><span class="pd pdf">Match to target lab</span></div>
<div class="pr"><div class="pn">09</div><div class="pb"><div class="pt">NeurIPS / ICML / ICLR best paper shortlist — current year</div><div class="pa">Annual — check proceedings for your specialization</div><div class="pw2">Every year: read every paper on the best paper shortlist in your subfield. These set the community's research agenda for the next 12–24 months. Understanding why each was considered exceptional — not just what it does, but why the community valued it — is how research taste develops.</div></div><span class="pd pdf">Annual must-read</span></div>
</div>

<div class="sl mt32">Phase 5 reference materials</div>
<div class="res-grid mt16">
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">The Alignment Forum</div><div class="rd">Primary venue for alignment, interpretability, and safety research preprints. Follow: Neel Nanda, Paul Christiano, Buck Shlegeris, Adam Jermyn. Quality often exceeds conference papers in this area.</div><a href="https://alignmentforum.org">alignmentforum.org</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">arXiv — cs.LG, cs.AI, cs.CL, stat.ML</div><div class="rd">Set up email alerts for your subfield keywords. Read abstracts daily. Flag papers worth going deeper on. This is non-optional at Phase 5 — staying current is a full-time requirement.</div><a href="https://arxiv.org/list/cs.LG/recent">arxiv.org/list/cs.LG/recent</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Lilian Weng's blog — everything</div><div class="rd">Read every post. Her technical summaries are the best free resource for staying current across RL, LLMs, diffusion, and alignment. Each post is graduate-seminar quality.</div><a href="https://lilianweng.github.io">lilianweng.github.io</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Andrej Karpathy's blog</div><div class="rd">"The Unreasonable Effectiveness of Recurrent Neural Networks," "Software 2.0," and his recent posts are excellent. More architectural insight per word than most papers.</div><a href="https://karpathy.github.io">karpathy.github.io</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Papers With Code</div><div class="rd">Find state-of-the-art results for any benchmark. Track method performance over time. Identify which benchmarks are saturating (find new ones) and where there's still room to contribute.</div><a href="https://paperswithcode.com">paperswithcode.com</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Connected Papers</div><div class="rd">Visualize a paper's citation network. Find related work you'd otherwise miss. Use this when starting a new research direction to map the landscape quickly.</div><a href="https://connectedpapers.com">connectedpapers.com</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">MATS Fellowship (ML Alignment Theory Scholars)</div><div class="rd">Structured research program for alignment-focused researchers. Strong signal for Anthropic. The connections and mentorship formed are extremely valuable. Applications open twice a year.</div><a href="https://matsprogram.org">matsprogram.org</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">ARENA — Alignment Research Engineer Accelerator</div><div class="rd">Free structured curriculum specifically for mechanistic interpretability research. If targeting Anthropic's interpretability team, ARENA is the most direct preparation available.</div><a href="https://arena.education">arena.education</a></div></div>
</div>

<div class="sl mt32">Performance expectations</div>
<div class="eg mt16">
<div class="ei"><div class="el">Publications</div><p>3+ first-author papers at NeurIPS/ICML/ICLR — "table stakes" for a DeepMind RS role. Workshop papers are legitimate stepping stones.</p></div>
<div class="ei"><div class="el">Research vision</div><p>A coherent 3-year agenda that builds on prior work and connects to the lab's mission. Articulate this in 3 minutes without notes.</p></div>
<div class="ei"><div class="el">Open source</div><p>Meaningful contributions to tools researchers use: TransformerLens, Diffusers, TRL, vLLM. Visible and cited by others.</p></div>
<div class="ei"><div class="el">Reputation</div><p>Researchers at your target lab have heard of your work — via arXiv, GitHub, Twitter/X, or conference interactions. Warm introductions are not optional at this stage.</p></div>
</div>
<div class="ag mt16">
<div class="ai"><strong>Build a research portfolio website — not a CV.</strong>A narrative. Summarize papers in 2 paragraphs each. State your research vision. Link your best code. Describe what you're working on now. Researchers at labs will Google you before and after interviews.</div>
<div class="ai"><strong>Open-source contributions compound visibility.</strong>A meaningful contribution to a library thousands of researchers use keeps your name in front of the community. It also demonstrates you can write code others can use — a different skill from research code.</div>
<div class="ai"><strong>Practice three versions of your research story.</strong>30 seconds: "I research X, specifically Y, and recently showed Z." 3 minutes: problem, approach, key result, why it matters. 30 minutes: full research talk. All three effortless before any interview.</div>
<div class="ai"><strong>Consider MATS if targeting Anthropic alignment/interpretability.</strong>The program provides mentorship, structured curriculum, and direct connections to the Anthropic team. Many Anthropic hires in the safety org come through MATS.</div>
</div>
</div>
</section>

<!-- LAB PREP -->
<section id="labs" class="ps">
<div class="wrap">
<div class="sl">Lab-specific interview preparation</div>
<div class="ins mt16"><strong>The most important advice in this entire guide:</strong> Most rejections don't come from lack of skill. They come from preparing for the wrong interview. Each lab has a different structure, different values, and different hiring signals. Generic ML interview prep fails all three.</div>

<div class="lg mt24">
<div class="lc"><div class="ln">🔵 Anthropic</div><ul>
<li><strong>Safety round is the gatekeeper.</strong> Not a formality — the filter that eliminates most candidates. Prepare deep explanations of Constitutional AI, scalable oversight, and interpretability. Know every limitation.</li>
<li><strong>CodeSignal: 520+/600.</strong> Architecture-first system design with increasing complexity. Not LeetCode. Clean, well-structured Python. Speed and quality both matter equally.</li>
<li><strong>Mechanistic interpretability</strong> is a core research pillar. An implemented project is a meaningful signal.</li>
<li><strong>PhD required</strong> for 90%+ of RS hires. Without one: publication-quality open-source or MATS fellowship.</li>
<li><strong>Apply general RS pool</strong> then team-match. Know which teams exist and which aligns with your track.</li>
<li><strong>MATS fellowship</strong> is a recognized pipeline into Anthropic safety roles.</li>
</ul></div>
<div class="lc"><div class="ln">🟢 OpenAI</div><ul>
<li><strong>Paper discussion round.</strong> Paper sent 24–48 hrs in advance. Prepare detailed critique: key contribution, key limitation, what experiment next. Not a summary — an analysis.</li>
<li><strong>Emphasizes shipping velocity.</strong> Show evidence of driving projects from hypothesis to result to paper. Completeness matters as much as quality.</li>
<li><strong>Most flexible on PhD</strong> requirement. Strong publications, shipped products, or high-quality open source can substitute.</li>
<li><strong>Coding-intensive</strong> for RS roles. Implement ML algorithms cleanly under time pressure in the interview itself.</li>
<li><strong>AGI-focus framing.</strong> Be ready to discuss your view on what AGI means and what you think the path to it is.</li>
</ul></div>
<div class="lc"><div class="ln">🔴 Google DeepMind</div><ul>
<li><strong>PhD-defense depth.</strong> Rapid-fire math quiz standard — re-derive algorithms on the spot. Practice deriving gradient updates for custom objectives from first principles.</li>
<li><strong>Research taste primary signal.</strong> Not coding speed, not paper count — the ability to identify which problems matter and why.</li>
<li><strong>"Googleyness" and leadership</strong> heavily weighted. Collaboration ability and mentoring evidence matter to the hiring committee.</li>
<li><strong>Fully liquid GOOG equity</strong> — significant financial advantage over private company options at Anthropic/OpenAI. Factor into negotiation.</li>
<li><strong>Scientific rigor first.</strong> Engineering-oriented background: be prepared to defend every architectural choice.</li>
</ul></div>
</div>

<div class="sl mt48">What each interview actually tests</div>
<div class="g2 mt16">
<div class="card">
<h3>📋 Four interview dimensions — all labs</h3>
<div class="tl mt8">
<div class="tli act"><div class="tt">Coding — fast, clean, production-quality</div><div class="td">Implement ML primitives from memory in PyTorch. Multi-head attention, a training loop with proper logging, a custom loss function. Speed and code quality both matter. Practice implementing things like attention, layer norm, and Adam from scratch in 30 minutes.</div></div>
<div class="tli act"><div class="tt">ML Theory — derive on demand</div><div class="td">Ready to derive gradient updates for any standard loss, explain any architecture choice, discuss training dynamics. No notes, no hesitation. Practice: set a 10-minute timer and derive the PPO objective from scratch.</div></div>
<div class="tli act"><div class="tt">Research Discussion — critique, not summarize</div><div class="td">For any paper given: key contribution, key limitation, what experiment you'd run next. Don't summarize — analyze. Practice this for every paper you read at Phase 5 depth.</div></div>
<div class="tli act"><div class="tt">Project Defense — 3 versions ready</div><div class="td">30 seconds, 3 minutes, 30 minutes. Every project needs: clear problem, your specific contribution, and honest limitations. The 30-second version is the hardest and most important — practice it until effortless.</div></div>
</div>
</div>
<div class="card">
<h3>⚠️ Common failure modes</h3>
<div class="tl mt8">
<div class="tli"><div class="tt">Generic ML interview prep</div><div class="td">LeetCode grinding and generic "ML interview" courses are misaligned with what frontier labs actually test. Most of that prep is wasted effort for RS roles specifically.</div></div>
<div class="tli"><div class="tt">Defensive about limitations</div><div class="td">The fastest way to fail a research interview. Interviewers test intellectual honesty deliberately. When challenged, say "that's a good point — here's how I'd address that limitation in follow-up work."</div></div>
<div class="tli"><div class="tt">Summarizing papers instead of critiquing them</div><div class="td">"They do X and achieve Y" is wrong. "The key insight is X, but the main limitation is Y because Z" is right. Practice this mode of engagement with every paper you read.</div></div>
<div class="tli"><div class="tt">No research vision</div><div class="td">If you can't articulate what you want to work on for the next 3 years and why it matters, labs will wonder whether you're a researcher or an implementer. Have this ready.</div></div>
<div class="tli"><div class="tt">Preparing for the wrong lab</div><div class="td">The overlap between Anthropic, OpenAI, and DeepMind interviews is smaller than you think. Prepare specifically for each lab you're targeting, not for "big tech ML."</div></div>
</div>
</div>
</div>

<div class="sl mt48">Systems knowledge required for all labs</div>
<div class="card mt16">
<h3>⚙️ Infrastructure topics you must know</h3>
<div class="pw"><span class="pill">Data parallelism (DDP)</span><span class="pill">Fully Sharded Data Parallel (FSDP)</span><span class="pill">Pipeline parallelism</span><span class="pill">Tensor parallelism</span><span class="pill">DeepSpeed ZeRO stages 1/2/3</span><span class="pill">FlashAttention — why it works</span><span class="pill">Gradient checkpointing — memory/compute tradeoff</span><span class="pill">vLLM / PagedAttention</span><span class="pill">Quantization (GPTQ, AWQ, FP8)</span><span class="pill">Speculative decoding</span><span class="pill">Continuous batching</span><span class="pill">KV cache optimization</span><span class="pill">torch.compile</span><span class="pill">Mixed precision BF16</span><span class="pill">Benchmark contamination testing</span><span class="pill">Responsible AI principles</span></div>
<p class="mt12">Know when to use each. The interview question isn't "implement FSDP" — it's "given a 70B parameter model you need to fine-tune on 8 A100s, what parallelism strategy would you use and why?"</p>
</div>

<div class="sl mt32">Compensation reality</div>
<div class="band mt16"><strong>Acceptance rates at frontier labs hover below 0.5%.</strong> Total annual compensation ranges from $350K to over $1.4M at senior levels. Don't reveal salary expectations early — let them make an offer first. Negotiate the full package: base, equity type and grant size, signing bonus, and research autonomy (which projects, publication rights, compute budget). Fully liquid GOOG equity at DeepMind is a significant advantage over unvested options at private companies.</div>
</div>
</section>

<!-- MINDSET -->
<section id="mindset" class="ps">
<div class="wrap">
<div class="sl">The researcher's mindset — what no phase teaches explicitly</div>
<div class="mpull">
<div class="mq">The goal is not to know every model. It's to become someone who can create, test, and explain new ones credibly.</div>
<p>The researchers who get hired at frontier labs aren't the ones who read the most papers or built the most projects. They're the ones who ran the research loop — read, hypothesize, implement, test, write — hundreds of times and got genuinely good at every step. Breadth is a side effect of depth, not a strategy.</p>
</div>

<div class="sl mt24">The rules that actually matter</div>
<div class="rg mt16">
<div class="rule rdo"><div class="rl">do</div>Write your hypothesis before running any experiment, every time. What would falsify it?</div>
<div class="rule rdont"><div class="rl">don't</div>Run experiments and rationalize the result afterward. That's storytelling, not science.</div>
<div class="rule rdo"><div class="rl">do</div>Implement the mechanism, not the plumbing. Backprop: yes. SVD: no. Know the difference.</div>
<div class="rule rdont"><div class="rl">don't</div>Implement everything from scratch. That's a ritual, not a strategy. It signals student thinking at the Phase 4+ level.</div>
<div class="rule rdo"><div class="rl">do</div>One project per phase, done with real depth, written up with honest failure analysis.</div>
<div class="rule rdont"><div class="rl">don't</div>Five shallow demos. Volume doesn't build reputation. Rigor compounds.</div>
<div class="rule rdo"><div class="rl">do</div>Read papers at three depths: abstract-only, core results, line-by-line. Match depth to relevance to your work.</div>
<div class="rule rdont"><div class="rl">don't</div>Read every paper the same way. At line-by-line depth for every paper, you'd read 3/month. That's not enough throughput.</div>
<div class="rule rdo"><div class="rl">do</div>Pick one specialization track by Phase 4. Build a recognizable identity. Be the person who works on X.</div>
<div class="rule rdont"><div class="rl">don't</div>Try to be expert in everything. No one gets hired for "broad ML knowledge." Labs want a specialist with range.</div>
<div class="rule rdo"><div class="rl">do</div>Document every failed experiment. They narrow the search space. 90% of research experiments fail. That's normal.</div>
<div class="rule rdont"><div class="rl">don't</div>Treat failed experiments as wasted time. They're the most information-dense events in research.</div>
<div class="rule rdo"><div class="rl">do</div>Build GitHub + arXiv presence + online visibility from Phase 1 onward, continuously.</div>
<div class="rule rdont"><div class="rl">don't</div>Wait until you have "enough" to be visible. Researchers discover each other through work in progress, not finished products.</div>
<div class="rule rdo"><div class="rl">do</div>Prepare three versions of your story: 30s, 3min, 30min. Practice until effortless.</div>
<div class="rule rdont"><div class="rl">don't</div>Wing the research talk. The 30-minute talk is your primary hiring document at top labs. Treat it like your thesis defense.</div>
</div>

<div class="sl mt48">Time allocation</div>
<div class="g3 mt24">
<div class="card" style="text-align:center"><div style="font-family:var(--font-disp);font-size:38px;font-weight:700;color:var(--v);margin-bottom:8px">70%</div><h3 style="justify-content:center">Deep work</h3><p>Core skills, active experiments, implementation, writing. Protect this time aggressively — it's where research is actually done. No interruptions.</p></div>
<div class="card" style="text-align:center"><div style="font-family:var(--font-disp);font-size:38px;font-weight:700;color:var(--g);margin-bottom:8px">20%</div><h3 style="justify-content:center">Reading &amp; reproducing</h3><p>Paper reading, reproductions, staying current. Essential for knowing what exists and where the gaps are. Daily arXiv habit.</p></div>
<div class="card" style="text-align:center"><div style="font-family:var(--font-disp);font-size:38px;font-weight:700;color:var(--a);margin-bottom:8px">10%</div><h3 style="justify-content:center">Network &amp; visibility</h3><p>Conferences, Twitter/X, GitHub, reading groups. Underinvested by almost everyone. Warm introductions are how top lab offers actually happen.</p></div>
</div>

<div class="sl mt48">Essential resources — master list</div>
<div class="res-grid mt16">
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Lilian Weng's Blog — lilianweng.github.io</div><div class="rd">The single best free resource for staying current across all of ML. Every post is graduate-seminar quality. Read everything she's written.</div><a href="https://lilianweng.github.io">lilianweng.github.io</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Andrej Karpathy — Neural Networks: Zero to Hero</div><div class="rd">7 videos. micrograd → makemore → GPT. The best sequential tutorial in existence. All code on GitHub. Watch before Phase 2.</div><a href="https://youtube.com/@AndrejKarpathy">youtube.com/@AndrejKarpathy</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Yannic Kilcher — Paper Walkthroughs</div><div class="rd">Unusually precise paper walkthroughs. Watch his videos on: ResNet, DDPM, GPT-3, AlphaFold, RLHF, DPO. Best supplementary resource per paper.</div><a href="https://youtube.com/@YannicKilcher">youtube.com/@YannicKilcher</a></div></div>
<div class="res-item"><div class="res-icon">🎥</div><div class="res-body"><div class="rt">Two Minute Papers</div><div class="rd">Fast summaries of new papers. Good for breadth awareness and staying current. Watch the ones in your track weekly.</div><a href="https://youtube.com/@TwoMinutePapers">youtube.com/@TwoMinutePapers</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Papers With Code</div><div class="rd">Track SOTA results, find implementations, discover papers by benchmark. Essential for knowing the current competitive landscape in your track.</div><a href="https://paperswithcode.com">paperswithcode.com</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Semantic Scholar</div><div class="rd">Better than Google Scholar for finding papers. The "Highly Influential Citations" feature is particularly useful for finding the papers that actually matter in a subfield.</div><a href="https://semanticscholar.org">semanticscholar.org</a></div></div>
<div class="res-item"><div class="res-icon">🎓</div><div class="res-body"><div class="rt">CS229 / CS231n / CS224N / CS294 (Stanford/Berkeley)</div><div class="rd">ML foundations (CS229), CNNs/DL (CS231n), NLP/LLMs (CS224N), Generative models (CS294). All free. These four courses cover Phases 0–4 comprehensively.</div><a href="https://cs229.stanford.edu">cs229 / cs231n / cs224n / cs294</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">GitHub — Anthropic / OpenAI / Google DeepMind repos</div><div class="rd">Follow the official repos of your target labs. Study their code style, tooling choices, and published implementations. Many publish partial code from their papers.</div><a href="https://github.com/anthropics">github.com/anthropics</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">Jay Alammar's Blog — Illustrated Guides</div><div class="rd">Best visual explanations of transformer, BERT, GPT, stable diffusion. "The Illustrated Transformer" alone has been read by millions. Bookmark and refer back repeatedly.</div><a href="https://jalammar.github.io">jalammar.github.io</a></div></div>
<div class="res-item"><div class="res-icon">📖</div><div class="res-body"><div class="rt">The Gradient — Research Blog</div><div class="rd">High-quality research blog covering recent developments. Interviews with researchers, deep dives, and opinion pieces. Good for staying calibrated on where the field is heading.</div><a href="https://thegradient.pub">thegradient.pub</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Hugging Face Hub + Datasets</div><div class="rd">Your primary interface with pretrained models and datasets throughout Phases 3–5. Learn to use efficiently: model cards, dataset documentation, spaces for demos.</div><a href="https://huggingface.co">huggingface.co</a></div></div>
<div class="res-item"><div class="res-icon">🛠️</div><div class="res-body"><div class="rt">Weights &amp; Biases (wandb)</div><div class="rd">The standard experiment tracking tool at most research labs. Free for personal use. Every training run from Phase 2 onward should use wandb. Builds the logging habit that makes research reproducible.</div><a href="https://wandb.ai">wandb.ai</a></div></div>
</div>

<div class="sl mt48">What no roadmap tells you</div>
<div class="pbox mt16">
<div class="pr" style="grid-template-columns:24px 1fr"><div class="pn">→</div><div class="pb"><div class="pt">A PhD is table stakes for DeepMind, near-required for Anthropic. OpenAI is most flexible.</div><div class="pw2">If you don't have a PhD and aren't getting one: publication-quality open-source work, strong arXiv preprints, and MATS fellowship can partially substitute. They compound the same way but take longer. The MATS program is probably the fastest path into Anthropic without a PhD.</div></div></div>
<div class="pr" style="grid-template-columns:24px 1fr"><div class="pn">→</div><div class="pb"><div class="pt">The global pool of elite AI researchers is approximately 2,000 people. Reputation travels fast.</div><div class="pw2">One strong paper, one well-known open-source contribution, or one highly cited blog post can make you visible to most of the people who matter in your track. The community is small enough that reputation — good and bad — travels within months. Build it deliberately.</div></div></div>
<div class="pr" style="grid-template-columns:24px 1fr"><div class="pn">→</div><div class="pb"><div class="pt">The most dangerous trap is tutorial hell — consuming endlessly without creating.</div><div class="pw2">At some point (ideally Phase 2), you must stop consuming tutorials and start producing things. Research is generative. Every week you spend watching another course instead of running experiments is a week your competition spends building a track record. The consuming vs creating ratio should be roughly 20% / 80% by Phase 4.</div></div></div>
<div class="pr" style="grid-template-columns:24px 1fr"><div class="pn">→</div><div class="pb"><div class="pt">Spend most of your time one level above your current comfort zone.</div><div class="pw2">One foot in implementation (to stay grounded), one foot in papers (to stretch toward the frontier). The right challenge level is where you're struggling a meaningful fraction of the time — not so much you can't make progress, but enough that every day pushes your frontier. This is deliberate practice for research.</div></div></div>
<div class="pr" style="grid-template-columns:24px 1fr"><div class="pn">→</div><div class="pb"><div class="pt">The research loop is the only thing you need to internalize from this entire guide.</div><div class="pw2">Read one paper → implement the key idea → write one paragraph about what surprised you → find one thing the paper doesn't answer → design an experiment. That's it. The researchers who join frontier labs are the ones who did this loop hundreds of times and got genuinely good at each step. Everything in this guide is preparation for that loop.</div></div></div>
</div>
</div>
</section>

<!-- FORMULA -->
<section style="padding:60px 0 50px;border-bottom:1px solid var(--b1)">
<div class="wrap">
<div class="fbox">
<h2>The world-class researcher profile</h2>
<div class="fi-wrap">
<div class="fi">Strong software engineer</div><div class="fop">+</div>
<div class="fi">Mathematical depth</div><div class="fop">+</div>
<div class="fi">PyTorch systems expert</div><div class="fop">+</div>
<div class="fi">Experimental scientist</div><div class="fop">+</div>
<div class="fi">Voracious paper reader</div><div class="fop">+</div>
<div class="fi">Open source contributor</div><div class="fop">+</div>
<div class="fi">Research publications</div><div class="fop">+</div>
<div class="fi">Original ideas</div>
<div class="feq" style="width:100%;margin:12px 0 0">=</div>
<span class="fr">Frontier AI Researcher</span>
</div>
<div class="loop">
The researchers who get hired aren't the ones who know the most.<br>
They're the ones who ran the loop — <span>read → hypothesize → build → test → write</span> — hundreds of times, and got good at every step.
</div>
</div>
</div>
</section>

<footer>
<div style="max-width:1080px;margin:0 auto">
The Honest AI Researcher Guide · Built from frontier lab hiring practices, researcher interviews, and real research workflows<br>
Targeting OpenAI · Google DeepMind · Anthropic · Meta AI · Google Brain<br><br>
<span style="color:var(--muted)">Build with rigor. Specialize early. Publish honestly. Run the loop.</span>
</div>
</footer>

<script>
const btt=document.getElementById('btt');
window.addEventListener('scroll',()=>btt.classList.toggle('vis',window.scrollY>500));
document.querySelectorAll('a[href^="#"]').forEach(a=>a.addEventListener('click',e=>{
  e.preventDefault();
  const t=document.querySelector(a.getAttribute('href'));
  if(t)t.scrollIntoView({behavior:'smooth',block:'start'});
}));
const sections=document.querySelectorAll('[id]');
const links=document.querySelectorAll('.nl[href^="#"]');
const io=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      links.forEach(l=>l.classList.remove('active'));
      const a=document.querySelector(`.nl[href="#${e.target.id}"]`);
      if(a)a.classList.add('active');
    }
  });
},{threshold:0.2,rootMargin:'-48px 0px -40% 0px'});
sections.forEach(s=>io.observe(s));
</script>
</body>
</html>