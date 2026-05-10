# CV-web-site
özgeçmişimi web sitesine çevirdiğim
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cansu Ayten | Veri Bilimci</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&family=Quicksand:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
* { margin:0; padding:0; box-sizing:border-box; }

:root {
  --emotion: #FFD700;
  --emotion-glow: rgba(255,215,0,0.18);
  --emotion-soft: rgba(255,215,0,0.07);
  --joy:#FFD700; --joy-glow:rgba(255,215,0,0.22); --joy-soft:rgba(255,215,0,0.07);
  --sad:#4A90D9; --sad-glow:rgba(74,144,217,0.22); --sad-soft:rgba(74,144,217,0.07);
  --angry:#E84545; --angry-glow:rgba(232,69,69,0.22); --angry-soft:rgba(232,69,69,0.07);
  --disgust:#5DBB63; --disgust-glow:rgba(93,187,99,0.22); --disgust-soft:rgba(93,187,99,0.07);
  --fear:#9B59B6; --fear-glow:rgba(155,89,182,0.22); --fear-soft:rgba(155,89,182,0.07);
  --bing:#FF9EBC;
  --text:#F0F4FF; --muted:rgba(240,244,255,0.62);
  --panel:rgba(255,255,255,0.055);
  --border:rgba(255,255,255,0.12);
  --bg-base:#080c28;
}

body {
  background: var(--bg-base);
  font-family:'Quicksand',sans-serif;
  color:var(--text);
  overflow-x:hidden;
  min-height:100vh;
  transition: background 1.2s ease;
}

/* ── DYNAMIC BG NEBULA ── */
#nebula {
  position:fixed; inset:0; pointer-events:none; z-index:0;
  transition: opacity 1.2s ease;
}
#nebula::before, #nebula::after {
  content:'';
  position:absolute;
  border-radius:50%;
  filter:blur(80px);
  transition: background 1.2s ease, opacity 1.2s ease;
}
#nebula::before {
  width:60vw; height:60vw;
  top:-10vw; left:-10vw;
  background: radial-gradient(circle, var(--emotion-glow) 0%, transparent 70%);
  animation: drift1 18s ease-in-out infinite alternate;
}
#nebula::after {
  width:50vw; height:50vw;
  bottom:-10vw; right:-10vw;
  background: radial-gradient(circle, var(--emotion-glow) 0%, transparent 70%);
  animation: drift2 14s ease-in-out infinite alternate;
}
@keyframes drift1 { from{transform:translate(0,0) scale(1)} to{transform:translate(5vw,3vw) scale(1.1)} }
@keyframes drift2 { from{transform:translate(0,0) scale(1)} to{transform:translate(-4vw,-5vw) scale(1.08)} }

/* Stars */
#stars {
  position:fixed; inset:0; pointer-events:none; z-index:0;
  background-image:
    radial-gradient(1px 1px at 12% 18%, rgba(255,255,255,.8) 0%,transparent 100%),
    radial-gradient(1px 1px at 78% 9%, rgba(255,255,255,.6) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 45% 55%, rgba(255,255,255,.7) 0%,transparent 100%),
    radial-gradient(1px 1px at 22% 75%, rgba(255,255,255,.5) 0%,transparent 100%),
    radial-gradient(1px 1px at 65% 40%, rgba(255,255,255,.6) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 88% 62%, rgba(255,255,255,.5) 0%,transparent 100%),
    radial-gradient(1px 1px at 33% 88%, rgba(255,255,255,.7) 0%,transparent 100%),
    radial-gradient(2px 2px at 55% 20%, rgba(255,255,255,.4) 0%,transparent 100%),
    radial-gradient(1px 1px at 5% 45%, rgba(255,255,255,.6) 0%,transparent 100%),
    radial-gradient(1.5px 1.5px at 95% 30%, rgba(255,255,255,.5) 0%,transparent 100%);
  animation: twinkle 5s ease-in-out infinite alternate;
}
@keyframes twinkle{ from{opacity:.6} to{opacity:1} }

/* Orbs */
#orbs { position:fixed; inset:0; pointer-events:none; z-index:0; overflow:hidden; }
.orb {
  position:absolute; border-radius:50%;
  opacity:.11; filter:blur(1.5px);
  animation:float-orb linear infinite;
}
@keyframes float-orb {
  0%{transform:translateY(110vh) rotate(0deg); opacity:0}
  10%{opacity:.11}
  90%{opacity:.11}
  100%{transform:translateY(-20vh) rotate(720deg); opacity:0}
}

/* ── LAYOUT ── */
.wrapper { position:relative; z-index:1; max-width:940px; margin:0 auto; padding:0 1.5rem 5rem; }

/* ── HERO ── */
.hero {
  min-height:100vh; display:flex; flex-direction:column;
  align-items:center; justify-content:center;
  text-align:center; padding:4rem 0 2rem;
}

.console-label {
  background:rgba(255,255,255,0.06);
  border:1px solid rgba(255,255,255,0.13);
  border-radius:100px;
  padding:.35rem 1.4rem;
  font-size:.72rem; font-weight:700;
  letter-spacing:.18em; text-transform:uppercase;
  color:rgba(200,210,255,.75);
  margin-bottom:2.2rem;
}

/* EMOTION SELECTOR */
.emotion-console {
  background:rgba(255,255,255,0.05);
  border:1px solid rgba(255,255,255,0.12);
  border-radius:24px;
  padding:1rem 1.5rem;
  margin-bottom:2.4rem;
  display:inline-flex;
  flex-direction:column;
  align-items:center;
  gap:.7rem;
}
.console-hint {
  font-size:.68rem; font-weight:700;
  text-transform:uppercase; letter-spacing:.12em;
  color:rgba(200,210,255,.5);
}
.emotion-row { display:flex; gap:.7rem; }

.emo-btn {
  display:flex; flex-direction:column; align-items:center; gap:.28rem;
  cursor:pointer; transition:transform .25s;
  border:none; background:none; color:inherit;
}
.emo-btn:hover { transform:scale(1.18) translateY(-3px); }
.emo-btn.active { transform:scale(1.2) translateY(-4px); }

.emo-face {
  width:50px; height:50px; border-radius:50%;
  display:flex; align-items:center; justify-content:center;
  font-size:1.5rem;
  border:2px solid rgba(255,255,255,.2);
  position:relative; overflow:hidden;
  transition:box-shadow .4s;
  animation:pulse-face 2.5s ease-in-out infinite;
}
.emo-face.joy    { background:radial-gradient(circle at 40% 35%,#ffe566,#e8a800); }
.emo-face.sad    { background:radial-gradient(circle at 40% 35%,#72b8f0,#1e5fa8); }
.emo-face.angry  { background:radial-gradient(circle at 40% 35%,#ff7878,#b81414); }
.emo-face.disgust{ background:radial-gradient(circle at 40% 35%,#7dd87f,#2a7a2c); }
.emo-face.fear   { background:radial-gradient(circle at 40% 35%,#c98fef,#6820a8); }

.emo-btn.active .emo-face { box-shadow: 0 0 22px currentColor; }
@keyframes pulse-face{ 0%,100%{transform:scale(1)} 50%{transform:scale(1.04)} }

.emo-label {
  font-size:.6rem; font-weight:700;
  text-transform:uppercase; letter-spacing:.1em;
  opacity:.65;
}

/* AVATAR */
.avatar-wrap { position:relative; width:148px; height:148px; margin:0 auto 1.4rem; }
.avatar-ring {
  position:absolute; inset:-5px; border-radius:50%;
  background:conic-gradient(var(--joy),var(--disgust),var(--sad),var(--fear),var(--angry),var(--joy));
  animation:spin-ring 7s linear infinite;
  transition: background 1.2s ease;
}
@keyframes spin-ring{ to{transform:rotate(360deg)} }
.avatar-inner {
  position:absolute; inset:5px; border-radius:50%;
  background:linear-gradient(135deg,#1a2070,#090e35);
  display:flex; align-items:center; justify-content:center;
  font-family:'Nunito',sans-serif; font-size:3.2rem; font-weight:900;
  color:var(--emotion); text-shadow:0 0 24px var(--emotion-glow);
  z-index:1; transition:color 1s ease, text-shadow 1s ease;
}

h1 {
  font-family:'Nunito',sans-serif;
  font-size:clamp(2.2rem,6vw,3.4rem);
  font-weight:900; line-height:1.1;
  background:linear-gradient(135deg,var(--emotion) 0%,#fff 60%,#a8d8ff 100%);
  -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text;
  margin-bottom:.45rem;
  transition:background 1.2s ease;
}
.subtitle { font-size:1rem; font-weight:600; color:rgba(180,200,255,.85); margin-bottom:.4rem; }
.location-pill {
  display:inline-flex; align-items:center; gap:.4rem;
  background:rgba(255,255,255,.07); border:1px solid rgba(255,255,255,.14);
  border-radius:100px; padding:.28rem 1rem;
  font-size:.78rem; color:var(--muted); margin-bottom:1.8rem;
}
.contact-links { display:flex; gap:.65rem; flex-wrap:wrap; justify-content:center; }
.c-link {
  display:inline-flex; align-items:center; gap:.38rem;
  padding:.45rem 1rem; border-radius:100px;
  font-size:.8rem; font-weight:700; text-decoration:none;
  border:1.5px solid; transition:all .25s;
}
.c-link:hover { background:rgba(255,255,255,.08); transform:translateY(-2px); }
.cl-joy    { color:var(--joy);    border-color:var(--joy);    }
.cl-sad    { color:var(--sad);    border-color:var(--sad);    }
.cl-fear   { color:var(--fear);   border-color:var(--fear);   }
.cl-bing   { color:var(--bing);   border-color:var(--bing);   }

.scroll-hint {
  margin-top:2.8rem;
  display:flex; flex-direction:column; align-items:center; gap:.45rem;
  color:var(--muted); font-size:.73rem;
  animation:float-hint 2.2s ease-in-out infinite;
}
@keyframes float-hint{ 0%,100%{transform:translateY(0);opacity:.7} 50%{transform:translateY(7px);opacity:1} }

/* ── SECTIONS ── */
.section {
  margin-bottom:2.8rem;
  opacity:0; transform:translateY(28px);
  transition:opacity .65s ease, transform .65s ease;
}
.section.visible { opacity:1; transform:translateY(0); }

.sec-header {
  display:flex; align-items:center; gap:.7rem; margin-bottom:1.4rem;
}
.sec-badge {
  width:36px; height:36px; border-radius:50%;
  display:flex; align-items:center; justify-content:center;
  font-size:1rem; flex-shrink:0;
}
.badge-joy    { background:radial-gradient(circle at 40% 35%,#ffe566,#e8a800); }
.badge-sad    { background:radial-gradient(circle at 40% 35%,#72b8f0,#1e5fa8); }
.badge-disgust{ background:radial-gradient(circle at 40% 35%,#7dd87f,#2a7a2c); }
.badge-fear   { background:radial-gradient(circle at 40% 35%,#c98fef,#6820a8); }
.badge-angry  { background:radial-gradient(circle at 40% 35%,#ff7878,#b81414); }
.badge-bing   { background:radial-gradient(circle at 40% 35%,#ffb8d0,#d95a80); }

.sec-title {
  font-family:'Nunito',sans-serif; font-size:1.25rem; font-weight:800;
}
.sec-sub {
  font-size:.7rem; font-weight:600; opacity:.42;
  text-transform:uppercase; letter-spacing:.12em; margin-left:.4rem;
}

.rdivider {
  height:2px;
  background:linear-gradient(90deg,var(--joy),var(--disgust),var(--sad),var(--fear),var(--angry));
  border-radius:2px; margin:2.6rem 0; opacity:.35;
}

/* ── ÖZET ORBS ── */
.orb-row { display:grid; grid-template-columns:repeat(auto-fit,minmax(220px,1fr)); gap:.9rem; }
.mem-orb {
  background:var(--panel); border:1px solid var(--border);
  border-radius:18px; padding:1.2rem;
  position:relative; overflow:hidden;
  transition:transform .3s, border-color .3s;
}
.mem-orb::before {
  content:''; position:absolute;
  top:-22px; right:-22px;
  width:80px; height:80px; border-radius:50%; opacity:.13;
}
.mem-orb.o-joy::before   { background:var(--joy); }
.mem-orb.o-sad::before   { background:var(--sad); }
.mem-orb.o-dig::before   { background:var(--disgust); }
.mem-orb:hover { transform:translateY(-4px); border-color:rgba(255,255,255,.25); }
.orb-icon { font-size:1.5rem; margin-bottom:.45rem; }
.orb-text { font-size:.86rem; line-height:1.65; color:var(--muted); }
.orb-text strong { color:var(--text); font-weight:700; }

/* ── EDUCATION ── */
.edu-card {
  background:var(--panel); border:1px solid var(--border);
  border-left:4px solid var(--sad); border-radius:18px;
  padding:1.4rem 1.6rem; position:relative; overflow:hidden;
}
.edu-card::after { content:'🎓'; position:absolute; right:1.4rem; top:50%; transform:translateY(-50%); font-size:2.4rem; opacity:.13; }
.edu-uni { font-family:'Nunito',sans-serif; font-size:1.05rem; font-weight:800; }
.edu-dept { font-size:.9rem; color:var(--sad); font-weight:700; margin:.18rem 0; }
.edu-date { font-size:.78rem; color:var(--muted); }
.course-row { display:flex; flex-wrap:wrap; gap:.35rem; margin-top:.75rem; }
.course-tag {
  background:rgba(74,144,217,.12); border:1px solid rgba(74,144,217,.28);
  border-radius:100px; padding:.18rem .7rem;
  font-size:.72rem; color:#a8d8ff; font-weight:600;
}

/* ── SKILLS ── */
.skills-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:.9rem; }
.sk-card {
  background:var(--panel); border:1px solid var(--border);
  border-radius:16px; padding:1.1rem;
  transition:transform .3s;
}
.sk-card:hover { transform:translateY(-3px); }
.sk-title {
  font-size:.69rem; font-weight:700; text-transform:uppercase;
  letter-spacing:.12em; margin-bottom:.65rem;
  display:flex; align-items:center; gap:.38rem;
}
.sk-title.joy    { color:var(--joy); }
.sk-title.sad    { color:var(--sad); }
.sk-title.dig    { color:var(--disgust); }
.sk-title.bing   { color:var(--bing); }
.pills { display:flex; flex-wrap:wrap; gap:.32rem; }
.pill {
  background:rgba(255,255,255,.07); border:1px solid rgba(255,255,255,.11);
  border-radius:100px; padding:.18rem .65rem;
  font-size:.74rem; color:var(--muted); font-weight:600;
  transition:all .2s;
}
.pill:hover { background:rgba(255,255,255,.14); color:var(--text); }

/* ── PROJECT CARDS ── */
.proj-card {
  background:var(--panel); border:1px solid var(--border);
  border-radius:20px; margin-bottom:1.1rem;
  overflow:hidden;
  transition:transform .3s, border-color .3s, box-shadow .3s;
}
.proj-card:hover {
  transform:translateY(-5px);
  border-color:rgba(255,255,255,.22);
}
.proj-card.cyber:hover { box-shadow:0 8px 40px rgba(93,187,99,.12); }
.proj-card.ecom:hover  { box-shadow:0 8px 40px rgba(255,215,0,.1); }
.proj-card.macro:hover { box-shadow:0 8px 40px rgba(74,144,217,.12); }

/* Colored top bar */
.proj-topbar {
  height:4px;
  border-radius:20px 20px 0 0;
}
.bar-cyber  { background:linear-gradient(90deg,#3a9e3f,#7dd87f); }
.bar-ecom   { background:linear-gradient(90deg,#c8940a,#FFD700); }
.bar-macro  { background:linear-gradient(90deg,#1a5fa8,#4A90D9); }

.proj-body { padding:1.4rem 1.6rem; }

.proj-head {
  display:flex; align-items:flex-start; gap:1rem; margin-bottom:1rem;
}
.proj-icon {
  width:46px; height:46px; border-radius:14px;
  display:flex; align-items:center; justify-content:center;
  font-size:1.4rem; flex-shrink:0;
}
.pi-cyber   { background:rgba(93,187,99,.18); border:1px solid rgba(93,187,99,.3); }
.pi-ecom    { background:rgba(255,215,0,.12); border:1px solid rgba(255,215,0,.25); }
.pi-macro   { background:rgba(74,144,217,.18); border:1px solid rgba(74,144,217,.3); }

.proj-meta { flex:1; }
.proj-title { font-family:'Nunito',sans-serif; font-size:1.05rem; font-weight:800; margin-bottom:.15rem; }
.proj-date  { font-size:.72rem; color:var(--muted); font-weight:600; }
.proj-badge {
  align-self:flex-start;
  background:rgba(255,255,255,.07); border:1px solid rgba(255,255,255,.12);
  border-radius:8px; padding:.15rem .55rem;
  font-size:.67rem; font-weight:700; color:var(--muted);
  text-transform:uppercase; letter-spacing:.07em; white-space:nowrap;
}

/* Stat row */
.stat-row { display:flex; flex-wrap:wrap; gap:.6rem; margin-bottom:1rem; }
.stat-chip {
  display:flex; align-items:center; gap:.35rem;
  border-radius:10px; padding:.4rem .75rem;
  font-size:.78rem; font-weight:700;
}
.sc-cyber  { background:rgba(93,187,99,.14); color:#7dd87f; border:1px solid rgba(93,187,99,.25); }
.sc-ecom   { background:rgba(255,215,0,.1);  color:#ffd700; border:1px solid rgba(255,215,0,.22); }
.sc-macro  { background:rgba(74,144,217,.14); color:#72b8f0; border:1px solid rgba(74,144,217,.25); }
.sc-gray   { background:rgba(255,255,255,.07); color:var(--muted); border:1px solid var(--border); }

/* Tech tags */
.tech-row { display:flex; flex-wrap:wrap; gap:.35rem; margin-bottom:.9rem; }
.tech-tag {
  background:rgba(255,255,255,.06); border:1px solid rgba(255,255,255,.1);
  border-radius:6px; padding:.15rem .55rem;
  font-size:.7rem; font-weight:700; color:var(--muted);
  font-family:monospace;
}

/* Steps */
.proj-steps { list-style:none; margin-bottom:.9rem; }
.proj-steps li {
  font-size:.86rem; color:var(--muted); line-height:1.65;
  padding:.25rem 0 .25rem 1.4rem; position:relative;
}
.proj-steps li::before {
  content:'▸';
  position:absolute; left:0; color:var(--muted); opacity:.5;
}
.proj-steps li strong { color:var(--text); font-weight:700; }
.proj-steps li em { font-style:normal; font-weight:700; }

.proj-footer {
  border-top:1px solid var(--border);
  padding-top:.85rem;
  display:flex; align-items:center; justify-content:space-between; flex-wrap:wrap; gap:.5rem;
}
.proj-link {
  display:inline-flex; align-items:center; gap:.38rem;
  font-size:.79rem; font-weight:700; text-decoration:none;
  padding:.38rem .9rem; border-radius:10px; border:1px solid;
  transition:all .25s;
}
.proj-link:hover { background:rgba(255,255,255,.07); transform:translateY(-1px); }
.pl-cyber { color:#7dd87f; border-color:rgba(93,187,99,.3); }
.pl-ecom  { color:#ffd700; border-color:rgba(255,215,0,.3); }
.pl-macro { color:#72b8f0; border-color:rgba(74,144,217,.3); }

.proj-lang { font-size:.73rem; color:var(--muted); display:flex; align-items:center; gap:.3rem; }
.lang-dot { width:8px; height:8px; border-radius:50%; }

/* ── VOLUNTEER ── */
.vol-card {
  background:var(--panel); border:1px solid var(--border);
  border-left:4px solid var(--bing); border-radius:16px;
  padding:1.25rem 1.5rem;
  display:flex; align-items:center; gap:1.1rem;
}
.vol-icon { font-size:2rem; }
.vol-org  { font-family:'Nunito',sans-serif; font-size:1rem; font-weight:800; }
.vol-role { font-size:.84rem; color:var(--muted); margin-top:.18rem; }
.vol-badge {
  margin-left:auto;
  background:rgba(255,158,188,.13); border:1px solid rgba(255,158,188,.28);
  border-radius:100px; padding:.22rem .85rem;
  font-size:.7rem; font-weight:700; color:var(--bing); white-space:nowrap;
}

/* ── FOOTER ── */
.footer {
  text-align:center; padding:2rem 0 1rem;
  border-top:1px solid var(--border);
  color:var(--muted); font-size:.78rem;
}
.footer-emos { font-size:1.4rem; margin-bottom:.7rem; display:flex; justify-content:center; gap:.5rem; }
</style>
</head>
<body>

<div id="nebula"></div>
<div id="stars"></div>
<div id="orbs"></div>

<div class="wrapper">

<!-- ═══════════ HERO ═══════════ -->
<section class="hero">
  <div class="console-label">⚙ Headquarters — Duygu Kontrol Merkezi ⚙</div>

  <!-- EMOTION CONSOLE -->
  <div class="emotion-console">
    <div class="console-hint">Duygu seç → arka planı değiştir</div>
    <div class="emotion-row">
      <button class="emo-btn active" data-emo="joy" onclick="setEmo(this)">
        <div class="emo-face joy" style="color:var(--joy)">😄</div>
        <div class="emo-label">Neşe</div>
      </button>
      <button class="emo-btn" data-emo="sad" onclick="setEmo(this)">
        <div class="emo-face sad" style="color:var(--sad)">😢</div>
        <div class="emo-label">Üzüntü</div>
      </button>
      <button class="emo-btn" data-emo="angry" onclick="setEmo(this)">
        <div class="emo-face angry" style="color:var(--angry)">😤</div>
        <div class="emo-label">Öfke</div>
      </button>
      <button class="emo-btn" data-emo="disgust" onclick="setEmo(this)">
        <div class="emo-face disgust" style="color:var(--disgust)">🙄</div>
        <div class="emo-label">İğrenme</div>
      </button>
      <button class="emo-btn" data-emo="fear" onclick="setEmo(this)">
        <div class="emo-face fear" style="color:var(--fear)">😰</div>
        <div class="emo-label">Korku</div>
      </button>
    </div>
  </div>

  <div class="avatar-wrap">
    <div class="avatar-ring"></div>
    <div class="avatar-inner" id="avatar-inner">CA</div>
  </div>

  <h1 id="hero-h1">Cansu Ayten</h1>
  <p class="subtitle">İstatistik Öğrencisi &amp; Veri Analisti</p>
  <div class="location-pill">📍 Konya, Türkiye</div>

  <div class="contact-links">
    <a href="mailto:cansuayten.2004@gmail.com" class="c-link cl-joy">✉ E-posta</a>
    <a href="https://linkedin.com/in/cansu-ayten-002a57299" class="c-link cl-sad" target="_blank">💼 LinkedIn</a>
    <a href="https://github.com/ayten2004" class="c-link cl-fear" target="_blank">🐙 GitHub</a>
    <a href="tel:05013235166" class="c-link cl-bing">📞 Ara</a>
  </div>

  <div class="scroll-hint">
    <span style="font-size:1.1rem">↓</span>
    <span>Hafıza kürelerini keşfet</span>
  </div>
</section>

<!-- ═══════════ ÖZET ═══════════ -->
<section class="section" id="s1">
  <div class="sec-header">
    <div class="sec-badge badge-joy">💡</div>
    <div class="sec-title">Çekirdek Hafıza <span class="sec-sub">// özet</span></div>
  </div>
  <div class="orb-row">
    <div class="mem-orb o-joy">
      <div class="orb-icon">🔬</div>
      <div class="orb-text"><strong>3. sınıf İstatistik</strong> öğrencisiyim. Python ve R kullanarak gerçek dünya veri setlerinde makine öğrenmesi projeleri geliştiriyorum.</div>
    </div>
    <div class="mem-orb o-sad">
      <div class="orb-icon">📊</div>
      <div class="orb-text">Regresyon analizi ve <strong>anomali tespiti</strong> yöntemleriyle veri setlerinden anlamlı istatistiksel içgörüler üretiyorum.</div>
    </div>
    <div class="mem-orb o-dig">
      <div class="orb-icon">🎯</div>
      <div class="orb-text">Veri odaklı karar süreçlerini destekleyen <strong>analitik modeller</strong> geliştirmeyi ve iş etkisi yaratmayı hedefliyorum.</div>
    </div>
  </div>
</section>

<div class="rdivider"></div>

<!-- ═══════════ EĞİTİM ═══════════ -->
<section class="section" id="s2">
  <div class="sec-header">
    <div class="sec-badge badge-sad">📚</div>
    <div class="sec-title">Öğrenme Anıları <span class="sec-sub">// eğitim</span></div>
  </div>
  <div class="edu-card">
    <div class="edu-uni">Necmettin Erbakan Üniversitesi</div>
    <div class="edu-dept">Lisans, İstatistik</div>
    <div class="edu-date">📅 Beklenen Mezuniyet: Haziran 2027 · Konya, Türkiye</div>
    <div class="course-row">
      <span class="course-tag">Doğrusal Regresyon Analizi</span>
      <span class="course-tag">Yöneylem Araştırması</span>
      <span class="course-tag">Matematiksel İstatistik</span>
    </div>
  </div>
</section>

<div class="rdivider"></div>

<!-- ═══════════ YETKİNLİKLER ═══════════ -->
<section class="section" id="s3">
  <div class="sec-header">
    <div class="sec-badge badge-disgust">⚡</div>
    <div class="sec-title">Güç Kaynakları <span class="sec-sub">// yetkinlikler</span></div>
  </div>
  <div class="skills-grid">
    <div class="sk-card">
      <div class="sk-title joy">💻 Programlama</div>
      <div class="pills">
        <span class="pill">Python</span><span class="pill">R</span>
        <span class="pill">MATLAB</span><span class="pill">SQL</span>
      </div>
    </div>
    <div class="sk-card">
      <div class="sk-title sad">🤖 Veri Bilimi</div>
      <div class="pills">
        <span class="pill">Makine Öğrenmesi</span><span class="pill">OLS / Ridge</span>
        <span class="pill">ANOVA</span><span class="pill">Hipotez Testleri</span>
        <span class="pill">Zaman Serileri</span>
      </div>
    </div>
    <div class="sk-card">
      <div class="sk-title dig">🛠 Araçlar</div>
      <div class="pills">
        <span class="pill">SPSS</span><span class="pill">Pandas</span>
        <span class="pill">Scikit-learn</span><span class="pill">Statsmodels</span>
        <span class="pill">Matplotlib</span><span class="pill">Excel</span>
      </div>
    </div>
    <div class="sk-card">
      <div class="sk-title bing">🌐 Bilişim</div>
      <div class="pills">
        <span class="pill">Cisco Networking Basics</span>
        <span class="pill">Industrial Networking</span>
      </div>
    </div>
  </div>
</section>

<div class="rdivider"></div>

<!-- ═══════════ PROJELER ═══════════ -->
<section class="section" id="s4">
  <div class="sec-header">
    <div class="sec-badge badge-angry">🚀</div>
    <div class="sec-title">Macera Adaları <span class="sec-sub">// projeler</span></div>
  </div>

  <!-- PROJE 1: NSL-KDD -->
  <div class="proj-card cyber">
    <div class="proj-topbar bar-cyber"></div>
    <div class="proj-body">
      <div class="proj-head">
        <div class="proj-icon pi-cyber">🛡️</div>
        <div class="proj-meta">
          <div class="proj-title">NSL-KDD Network Intrusion Detection</div>
          <div class="proj-date">Ocak 2026 · Bireysel Proje</div>
        </div>
        <div class="proj-badge">Siber Güvenlik</div>
      </div>

      <div class="stat-row">
        <div class="stat-chip sc-cyber">✅ %98 Accuracy</div>
        <div class="stat-chip sc-cyber">🎯 %96.44 İkili Sınıflama</div>
        <div class="stat-chip sc-gray">📦 NSL-KDD Veri Seti</div>
        <div class="stat-chip sc-gray">🔀 4 Saldırı Türü</div>
      </div>

      <div class="tech-row">
        <span class="tech-tag">Python</span><span class="tech-tag">Scikit-learn</span>
        <span class="tech-tag">Pandas</span><span class="tech-tag">Seaborn</span>
        <span class="tech-tag">Logistic Regression</span><span class="tech-tag">StandardScaler</span>
        <span class="tech-tag">Label Encoding</span>
      </div>

      <ul class="proj-steps">
        <li><strong>İstatistiksel Veri Temizliği:</strong> Eksik değer kontrolü ve kategorik değişkenlerin <em>Label Encoding</em> yöntemiyle sayısallaştırılması sağlandı.</li>
        <li><strong>Ölçeklendirme (Z-skoru):</strong> Tüm değişkenler <em>StandardScaler</em> ile normalize edilerek modelin öğrenim dengesi iyileştirildi.</li>
        <li><strong>Anomali Tespiti:</strong> Lojistik Regresyon ile ikili sınıflandırma yapıldı; <em>%96.44 başarı oranı</em> elde edildi — normal trafik vs. saldırı.</li>
        <li><strong>Çok Sınıflı Saldırı Tespiti:</strong> DoS, Probe, R2L, U2R türleri Multinomial Lojistik Regresyon ile ayrıştırıldı. Dengesiz sınıf sorunu <em>class_weight='balanced'</em> ile giderildi.</li>
        <li><strong>Genel Doğruluk:</strong> Model tüm sınıf kombinasyonunda <em>%98 accuracy</em> oranına ulaştı; confusion matrix ile detaylı hata analizi yapıldı.</li>
      </ul>

      <div class="proj-footer">
        <a href="https://github.com/ayten2004/NSL-KDD-Network-Intrusion-Detection" class="proj-link pl-cyber" target="_blank">🔗 GitHub'da Görüntüle</a>
        <div class="proj-lang">
          <div class="lang-dot" style="background:#f37626"></div>
          Jupyter Notebook %100
        </div>
      </div>
    </div>
  </div>

  <!-- PROJE 2: E-TİCARET -->
  <div class="proj-card ecom">
    <div class="proj-topbar bar-ecom"></div>
    <div class="proj-body">
      <div class="proj-head">
        <div class="proj-icon pi-ecom">📈</div>
        <div class="proj-meta">
          <div class="proj-title">E-Ticaret Kârlılık Analizi &amp; Risk Modellemesi</div>
          <div class="proj-date">Mart 2026 · Bireysel Proje</div>
        </div>
        <div class="proj-badge">Regresyon</div>
      </div>

      <div class="stat-row">
        <div class="stat-chip sc-ecom">📉 −222 TL Kâr / Birim</div>
        <div class="stat-chip sc-ecom">📊 p &lt; 0.01</div>
        <div class="stat-chip sc-gray">🗂 51.000 Satır</div>
        <div class="stat-chip sc-ecom">⬆ %15 Optimizasyon</div>
      </div>

      <div class="tech-row">
        <span class="tech-tag">Python</span><span class="tech-tag">Pandas</span>
        <span class="tech-tag">Statsmodels</span><span class="tech-tag">OLS Regresyon</span>
        <span class="tech-tag">Matplotlib</span><span class="tech-tag">Scikit-learn</span>
      </div>

      <ul class="proj-steps">
        <li><strong>Veri Seti:</strong> 51.000 satırlık gerçek e-ticaret verisi; ürün kategorisi, indirim oranı, satış miktarı, kâr gibi değişkenler işlendi.</li>
        <li><strong>Çoklu Doğrusal Regresyon (OLS):</strong> Bağımlı değişken olarak birim kâr alındı; indirim oranı, ürün kategorisi ve bölge bağımsız değişken olarak modellendi.</li>
        <li><strong>Ana Bulgu:</strong> İndirim oranındaki 1 birimlik artış, birim başına kârı <em>222 TL azalttığı</em> istatistiksel olarak kanıtlandı (p &lt; 0.01, %99 güven düzeyi).</li>
        <li><strong>Risk Modellemesi:</strong> Yüksek indirim + düşük hacim ürün segmentleri zarar bölgesi olarak etiketlenerek risk haritası oluşturuldu.</li>
        <li><strong>Strateji Önerisi:</strong> İndirim politikasının yeniden yapılandırılması ile <em>%15 kâr artışı</em> simülasyonu gerçekleştirildi ve raporlandı.</li>
      </ul>

      <div class="proj-footer">
        <a href="https://github.com/ayten2004" class="proj-link pl-ecom" target="_blank">🔗 GitHub'da Görüntüle</a>
        <div class="proj-lang">
          <div class="lang-dot" style="background:#f37626"></div>
          Jupyter Notebook
        </div>
      </div>
    </div>
  </div>

  <!-- PROJE 3: MAKROEKONOMİ -->
  <div class="proj-card macro">
    <div class="proj-topbar bar-macro"></div>
    <div class="proj-body">
      <div class="proj-head">
        <div class="proj-icon pi-macro">🌍</div>
        <div class="proj-meta">
          <div class="proj-title">Ülkelerin Verimlilik Düzeylerinin Makroekonomik Analizi</div>
          <div class="proj-date">2025 · Akademik Proje</div>
        </div>
        <div class="proj-badge">Akademik</div>
      </div>

      <div class="stat-row">
        <div class="stat-chip sc-macro">🌐 50 Ülke</div>
        <div class="stat-chip sc-macro">📉 %12 Hata Azaltma</div>
        <div class="stat-chip sc-gray">L₂ Regularization</div>
        <div class="stat-chip sc-gray">Chow + Glejser Test</div>
      </div>

      <div class="tech-row">
        <span class="tech-tag">R</span><span class="tech-tag">Ridge Regression</span>
        <span class="tech-tag">OLS</span><span class="tech-tag">Chow Test</span>
        <span class="tech-tag">Glejser Test</span><span class="tech-tag">VIF Analizi</span>
        <span class="tech-tag">SPSS</span>
      </div>

      <ul class="proj-steps">
        <li><strong>Veri:</strong> 50 ülkenin GSYH, işgücü verimliliği, enflasyon, beşeri sermaye gibi makroekonomik göstergeleri derlendi ve temizlendi.</li>
        <li><strong>Multicollinearity Tespiti:</strong> Bağımsız değişkenler arasında yüksek çoklu doğrusal bağıntı (VIF &gt; 10) tespit edildi; standart OLS güvenilirliği sorgulandı.</li>
        <li><strong>Ridge Regresyon (L₂):</strong> Düzenlileştirme parametresi (λ) çapraz doğrulama ile optimize edildi; model hata payı <em>%12 düşürüldü</em> ve aşırı öğrenme engellendi.</li>
        <li><strong>Yapısal Kırılma — Chow Testi:</strong> Gelişmiş ve gelişmekte olan ülkeler arasında istatistiksel olarak anlamlı yapısal farklılık tespit edildi.</li>
        <li><strong>Heteroskedastisite — Glejser Testi:</strong> Değişen varyans sorunu istatistiksel olarak belirlendi; ağırlıklı en küçük kareler (WLS) yaklaşımıyla giderildi.</li>
      </ul>

      <div class="proj-footer">
        <span class="proj-link pl-macro" style="cursor:default; opacity:.7">🔒 Akademik Proje</span>
        <div class="proj-lang">
          <div class="lang-dot" style="background:#276DC3"></div>
          R Language
        </div>
      </div>
    </div>
  </div>
</section>

<div class="rdivider"></div>

<!-- ═══════════ GÖNÜLLÜLÜK ═══════════ -->
<section class="section" id="s5">
  <div class="sec-header">
    <div class="sec-badge badge-bing">💜</div>
    <div class="sec-title">Aile Adası <span class="sec-sub">// gönüllülük</span></div>
  </div>
  <div class="vol-card">
    <div class="vol-icon">🌿</div>
    <div>
      <div class="vol-org">Türkiye Yeşilay Cemiyeti</div>
      <div class="vol-role">Bağımlılıkla mücadele farkındalık eğitimlerini tamamladım.</div>
    </div>
    <div class="vol-badge">2026 — Devam Ediyor</div>
  </div>
</section>

<!-- ═══════════ FOOTER ═══════════ -->
<footer class="footer section" id="s6">
  <div class="footer-emos">😄 😢 😤 🙄 😰</div>
  <p>Cansu Ayten'in Duygu Kontrol Merkezi'ne hoş geldiniz 🎈</p>
  <p style="margin-top:.4rem;font-size:.7rem;opacity:.4">cansuayten.2004@gmail.com · Konya, Türkiye</p>
</footer>

</div><!-- /wrapper -->

<script>
/* ── ORBS ── */
const orbsEl = document.getElementById('orbs');
const emoColors = ['#FFD700','#4A90D9','#E84545','#5DBB63','#9B59B6','#FF9EBC'];
for(let i=0;i<20;i++){
  const o=document.createElement('div');
  o.className='orb';
  const sz=Math.random()*55+18;
  o.style.cssText=`width:${sz}px;height:${sz}px;left:${Math.random()*100}%;background:${emoColors[Math.floor(Math.random()*emoColors.length)]};animation-duration:${Math.random()*18+14}s;animation-delay:${Math.random()*16}s;`;
  orbsEl.appendChild(o);
}

/* ── EMOTION SYSTEM ── */
const emoData = {
  joy:    { color:'#FFD700', glow:'rgba(255,215,0,0.22)',    soft:'rgba(255,215,0,0.07)',    bgBase:'#0d0a00', bg:'#120e01' },
  sad:    { color:'#4A90D9', glow:'rgba(74,144,217,0.22)',   soft:'rgba(74,144,217,0.07)',   bgBase:'#040c1c', bg:'#050e20' },
  angry:  { color:'#E84545', glow:'rgba(232,69,69,0.22)',    soft:'rgba(232,69,69,0.07)',    bgBase:'#1a0404', bg:'#1e0505' },
  disgust:{ color:'#5DBB63', glow:'rgba(93,187,99,0.22)',    soft:'rgba(93,187,99,0.07)',    bgBase:'#040e05', bg:'#04100a' },
  fear:   { color:'#9B59B6', glow:'rgba(155,89,182,0.22)',   soft:'rgba(155,89,182,0.07)',   bgBase:'#0a0414', bg:'#0c0518' },
};

function setEmo(btn){
  document.querySelectorAll('.emo-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  const e = emoData[btn.dataset.emo];
  const r = document.documentElement;
  r.style.setProperty('--emotion', e.color);
  r.style.setProperty('--emotion-glow', e.glow);
  r.style.setProperty('--emotion-soft', e.soft);
  document.body.style.background = e.bg;
  // update avatar glow
  document.getElementById('avatar-inner').style.color = e.color;
  document.getElementById('avatar-inner').style.textShadow = `0 0 28px ${e.glow}`;
  // update h1 gradient
  const h1 = document.getElementById('hero-h1');
  h1.style.background = `linear-gradient(135deg, ${e.color} 0%, #fff 60%, #a8d8ff 100%)`;
  h1.style.webkitBackgroundClip = 'text';
  h1.style.backgroundClip = 'text';
  h1.style.webkitTextFillColor = 'transparent';
}

/* ── SCROLL REVEAL ── */
const obs = new IntersectionObserver(entries=>{
  entries.forEach(e=>{ if(e.isIntersecting) e.target.classList.add('visible'); });
},{threshold:0.08});
document.querySelectorAll('.section').forEach(s=>obs.observe(s));
</script>
</body>
</html>
