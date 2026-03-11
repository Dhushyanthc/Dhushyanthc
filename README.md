<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Dhushyanth C — GitHub Profile Preview</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;700;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --void: #050508;
    --deep: #0d0d18;
    --surface: #12121f;
    --card: #1a1a2e;
    --border: #2a2a45;
    --accent: #7B61FF;
    --cyan: #00D4AA;
    --coral: #FF6B6B;
    --text: #e8e8ff;
    --muted: #7878a0;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--void);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    overflow-x: hidden;
    min-height: 100vh;
  }

  /* PARTICLE CANVAS */
  #canvas {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 0;
    pointer-events: none;
  }

  .page { position: relative; z-index: 1; max-width: 900px; margin: 0 auto; padding: 0 20px 80px; }

  /* HEADER */
  .hero {
    text-align: center;
    padding: 80px 20px 60px;
    position: relative;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: 0; left: 50%;
    transform: translateX(-50%);
    width: 600px; height: 600px;
    background: radial-gradient(ellipse, rgba(123,97,255,0.12) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-tag {
    display: inline-block;
    font-size: 11px;
    letter-spacing: 3px;
    color: var(--cyan);
    text-transform: uppercase;
    border: 1px solid rgba(0,212,170,0.3);
    padding: 6px 16px;
    border-radius: 20px;
    margin-bottom: 24px;
    animation: fadeSlideDown 0.8s ease both;
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(48px, 8vw, 90px);
    font-weight: 800;
    line-height: 1;
    letter-spacing: -2px;
    background: linear-gradient(135deg, #ffffff 0%, #a78bff 50%, #00D4AA 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: fadeSlideDown 0.8s 0.1s ease both;
    margin-bottom: 16px;
  }

  .hero-role {
    font-size: 14px;
    color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    animation: fadeSlideDown 0.8s 0.2s ease both;
    margin-bottom: 32px;
  }

  /* TYPING EFFECT */
  .typing-wrap {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(123,97,255,0.08);
    border: 1px solid rgba(123,97,255,0.25);
    border-radius: 8px;
    padding: 10px 20px;
    margin-bottom: 36px;
    animation: fadeSlideDown 0.8s 0.3s ease both;
  }

  .prompt { color: var(--cyan); font-size: 13px; }
  .typing-text { color: var(--text); font-size: 13px; }
  .cursor {
    width: 2px; height: 16px;
    background: var(--accent);
    animation: blink 1s step-end infinite;
  }

  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* SOCIAL BADGES */
  .badges {
    display: flex; flex-wrap: wrap; justify-content: center; gap: 10px;
    animation: fadeSlideDown 0.8s 0.4s ease both;
    margin-bottom: 8px;
  }

  .badge {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 8px 16px;
    border-radius: 8px;
    font-size: 12px;
    font-weight: 600;
    text-decoration: none;
    transition: transform 0.2s, box-shadow 0.2s;
    border: 1px solid transparent;
  }
  .badge:hover { transform: translateY(-3px); box-shadow: 0 8px 25px rgba(0,0,0,0.4); }
  .badge-linkedin { background: #0077B5; color: white; }
  .badge-gmail { background: #D14836; color: white; }
  .badge-github { background: #161b22; color: white; border-color: var(--border); }
  .badge-location { background: rgba(255,107,107,0.12); color: var(--coral); border-color: rgba(255,107,107,0.3); }

  /* DIVIDER */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), var(--cyan), transparent);
    margin: 50px 0;
    position: relative;
    overflow: visible;
  }
  .divider::after {
    content: '';
    position: absolute;
    top: -4px; left: 50%;
    transform: translateX(-50%);
    width: 8px; height: 8px;
    background: var(--accent);
    border-radius: 50%;
    box-shadow: 0 0 12px var(--accent);
  }

  /* SECTIONS */
  .section-label {
    font-size: 11px;
    letter-spacing: 3px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 28px;
    font-weight: 800;
    color: var(--text);
    margin-bottom: 28px;
  }

  /* CODE BLOCK */
  .code-block {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    margin-bottom: 40px;
    animation: fadeSlideUp 0.6s ease both;
  }

  .code-header {
    display: flex; align-items: center; gap: 8px;
    padding: 12px 16px;
    background: var(--card);
    border-bottom: 1px solid var(--border);
  }

  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot-r { background: #FF5F57; }
  .dot-y { background: #FEBC2E; }
  .dot-g { background: #28C840; }
  .code-filename { font-size: 12px; color: var(--muted); margin-left: 8px; }

  .code-body { padding: 24px; font-size: 13px; line-height: 1.8; overflow-x: auto; }
  .kw { color: #ff79c6; }
  .fn { color: var(--cyan); }
  .str { color: #f1fa8c; }
  .ty { color: #8be9fd; }
  .cm { color: #6272a4; }
  .vr { color: var(--text); }
  .pk { color: var(--coral); }

  /* TECH GRID */
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    gap: 12px;
    margin-bottom: 40px;
  }

  .tech-chip {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px 8px;
    text-align: center;
    font-size: 11px;
    color: var(--muted);
    transition: all 0.25s;
    cursor: default;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
  }

  .tech-chip:hover {
    border-color: var(--accent);
    color: var(--text);
    background: rgba(123,97,255,0.1);
    transform: translateY(-4px);
    box-shadow: 0 8px 20px rgba(123,97,255,0.15);
  }

  .tech-icon { font-size: 22px; }

  /* PROJECT CARDS */
  .project-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin-bottom: 40px; }

  @media(max-width: 600px) { .project-grid { grid-template-columns: 1fr; } }

  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 24px;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
    cursor: pointer;
    text-decoration: none;
    color: inherit;
    display: block;
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--accent), var(--cyan));
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s;
  }

  .project-card:hover { border-color: rgba(123,97,255,0.4); transform: translateY(-6px); box-shadow: 0 20px 50px rgba(0,0,0,0.5); }
  .project-card:hover::before { transform: scaleX(1); }

  .project-icon { font-size: 32px; margin-bottom: 12px; }
  .project-name { font-family: 'Syne', sans-serif; font-size: 18px; font-weight: 700; color: var(--text); margin-bottom: 8px; }
  .project-desc { font-size: 12px; color: var(--muted); line-height: 1.7; margin-bottom: 16px; }
  .project-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag {
    font-size: 10px;
    padding: 3px 10px;
    border-radius: 20px;
    font-weight: 600;
  }
  .tag-go { background: rgba(0,173,216,0.15); color: #00ADD8; border: 1px solid rgba(0,173,216,0.3); }
  .tag-py { background: rgba(55,118,171,0.15); color: #61A5D5; border: 1px solid rgba(55,118,171,0.3); }
  .tag-react { background: rgba(97,218,251,0.15); color: #61DAFB; border: 1px solid rgba(97,218,251,0.3); }
  .tag-ieee { background: rgba(255,107,107,0.15); color: var(--coral); border: 1px solid rgba(255,107,107,0.3); }
  .tag-pg { background: rgba(65,105,225,0.15); color: #6B8EDF; border: 1px solid rgba(65,105,225,0.3); }
  .tag-ml { background: rgba(255,107,107,0.15); color: #FF9580; border: 1px solid rgba(255,107,107,0.3); }

  /* PROJECT FULL WIDTH */
  .project-card.full { grid-column: 1 / -1; }

  /* IEEE BADGE */
  .achievement {
    background: linear-gradient(135deg, #1a1a2e, #16213e);
    border: 1px solid rgba(255,215,0,0.3);
    border-radius: 16px;
    padding: 28px;
    display: flex;
    align-items: center;
    gap: 24px;
    margin-bottom: 40px;
    position: relative;
    overflow: hidden;
  }

  .achievement::before {
    content: '';
    position: absolute;
    top: -50%; right: -50%;
    width: 200%; height: 200%;
    background: radial-gradient(ellipse, rgba(255,215,0,0.04) 0%, transparent 60%);
  }

  .achievement-icon { font-size: 48px; flex-shrink: 0; }
  .achievement-title { font-family: 'Syne', sans-serif; font-size: 20px; font-weight: 800; color: gold; margin-bottom: 4px; }
  .achievement-sub { font-size: 12px; color: var(--muted); line-height: 1.6; }

  /* STATS */
  .stats-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; margin-bottom: 40px; }

  @media(max-width: 500px) { .stats-grid { grid-template-columns: 1fr 1fr; } }

  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px 16px;
    text-align: center;
    transition: all 0.3s;
  }

  .stat-card:hover { border-color: var(--accent); transform: scale(1.03); }
  .stat-num { font-family: 'Syne', sans-serif; font-size: 36px; font-weight: 800; color: var(--accent); }
  .stat-label { font-size: 11px; color: var(--muted); letter-spacing: 1px; margin-top: 4px; }

  /* CONNECT */
  .connect {
    text-align: center;
    padding: 60px 20px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    position: relative;
    overflow: hidden;
  }

  .connect::before {
    content: '';
    position: absolute;
    bottom: -60px; left: 50%;
    transform: translateX(-50%);
    width: 400px; height: 200px;
    background: radial-gradient(ellipse, rgba(123,97,255,0.15) 0%, transparent 70%);
  }

  .connect-title { font-family: 'Syne', sans-serif; font-size: 32px; font-weight: 800; margin-bottom: 8px; }
  .connect-sub { font-size: 13px; color: var(--muted); margin-bottom: 28px; }
  .connect-btns { display: flex; justify-content: center; flex-wrap: wrap; gap: 12px; position: relative; }

  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 12px 24px;
    border-radius: 10px;
    font-size: 13px;
    font-weight: 600;
    font-family: 'JetBrains Mono', monospace;
    text-decoration: none;
    transition: all 0.25s;
    border: 1px solid transparent;
  }

  .btn-primary { background: var(--accent); color: white; }
  .btn-primary:hover { background: #9b85ff; transform: translateY(-3px); box-shadow: 0 10px 30px rgba(123,97,255,0.4); }
  .btn-secondary { background: transparent; color: var(--text); border-color: var(--border); }
  .btn-secondary:hover { border-color: var(--cyan); color: var(--cyan); transform: translateY(-3px); }

  /* ANIMATIONS */
  @keyframes fadeSlideDown {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-8px); }
  }

  .float { animation: float 4s ease-in-out infinite; }

  /* SCROLL REVEAL */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }
</style>
</head>
<body>

<canvas id="canvas"></canvas>

<div class="page">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-tag">👋 Welcome to my profile</div>
    <h1 class="hero-name">Dhushyanth C</h1>
    <p class="hero-role">Backend Architect · Systems Thinker · Code Craftsman</p>

    <div class="typing-wrap">
      <span class="prompt">$</span>
      <span class="typing-text" id="typing"></span>
      <div class="cursor"></div>
    </div>

    <div class="badges">
      <a href="https://linkedin.com/in/dhushyanth-c-163ba1297/" class="badge badge-linkedin">💼 LinkedIn</a>
      <a href="mailto:dhushyanthc005@gmail.com" class="badge badge-gmail">📧 Gmail</a>
      <a href="https://github.com/Dhushyanthc" class="badge badge-github">🐙 GitHub</a>
      <span class="badge badge-location">📍 Bangalore, India</span>
    </div>
  </div>

  <div class="divider"></div>

  <!-- ABOUT -->
  <div class="reveal">
    <div class="section-label">01 / about</div>
    <div class="section-title">The Developer Behind The Code</div>

    <div class="code-block">
      <div class="code-header">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
        <span class="code-filename">whoami.go</span>
      </div>
      <div class="code-body"><pre><span class="kw">package</span> <span class="pk">main</span>

<span class="kw">type</span> <span class="ty">Developer</span> <span class="kw">struct</span> {
    Name      <span class="ty">string</span>
    Role      <span class="ty">string</span>
    Focus     []<span class="ty">string</span>
    Published <span class="ty">bool</span>
}

<span class="kw">func</span> <span class="fn">main</span>() {
    me := <span class="ty">Developer</span>{
        Name: <span class="str">"Dhushyanth C"</span>,
        Role: <span class="str">"Backend &amp; Full-Stack Developer"</span>,
        Focus: []<span class="ty">string</span>{
            <span class="str">"Scalable Architectures"</span>,
            <span class="str">"High-Performance Systems"</span>,
            <span class="str">"Go Microservices"</span>,
            <span class="str">"Real-Time Feeds"</span>,
        },
        Published: <span class="kw">true</span>, <span class="cm">// IEEE ICTBIG 2025 🏆</span>
    }
    fmt.<span class="fn">Println</span>(<span class="str">"Building systems that scale."</span>)
}</pre></div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- TECH STACK -->
  <div class="reveal">
    <div class="section-label">02 / arsenal</div>
    <div class="section-title">Tools I Wield</div>

    <div class="tech-grid">
      <div class="tech-chip"><span class="tech-icon">🐹</span>Go</div>
      <div class="tech-chip"><span class="tech-icon">🐍</span>Python</div>
      <div class="tech-chip"><span class="tech-icon">⚡</span>JavaScript</div>
      <div class="tech-chip"><span class="tech-icon">⚙️</span>C++</div>
      <div class="tech-chip"><span class="tech-icon">🟢</span>Node.js</div>
      <div class="tech-chip"><span class="tech-icon">🚀</span>FastAPI</div>
      <div class="tech-chip"><span class="tech-icon">🎯</span>Express</div>
      <div class="tech-chip"><span class="tech-icon">⚛️</span>React</div>
      <div class="tech-chip"><span class="tech-icon">🐘</span>PostgreSQL</div>
      <div class="tech-chip"><span class="tech-icon">🍃</span>MongoDB</div>
      <div class="tech-chip"><span class="tech-icon">🐳</span>Docker</div>
      <div class="tech-chip"><span class="tech-icon">🔱</span>Git</div>
      <div class="tech-chip"><span class="tech-icon">🐬</span>MySQL</div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- PROJECTS -->
  <div class="reveal">
    <div class="section-label">03 / projects</div>
    <div class="section-title">What I've Built</div>

    <div class="project-grid">
      <a class="project-card" href="https://github.com/Dhushyanthc" target="_blank">
        <div class="project-icon float">⚙️</div>
        <div class="project-name">Event Feed Engine</div>
        <div class="project-desc">High-concurrency backend simulating social media logic with fan-out feed generation, JWT auth, and efficient pagination.</div>
        <div class="project-tags">
          <span class="tag tag-go">Go</span>
          <span class="tag tag-pg">PostgreSQL</span>
        </div>
      </a>

      <a class="project-card" href="https://khaleezi-website.vercel.app/" target="_blank">
        <div class="project-icon float" style="animation-delay:0.5s">🛍️</div>
        <div class="project-name">Khaleezi E-Commerce</div>
        <div class="project-desc">Full-scale responsive storefront with custom ordering flow, dynamic React UI, and niche retail integration.</div>
        <div class="project-tags">
          <span class="tag tag-react">React</span>
          <span class="tag tag-react">Vercel</span>
        </div>
      </a>

      <div class="project-card full">
        <div class="project-icon float" style="animation-delay:1s">🛸</div>
        <div class="project-name">AI Astronaut Health Monitor</div>
        <div class="project-desc">Research-grade predictive model for detecting physiological risks in extreme space environments. Published at IEEE ICTBIG 2025 — a milestone in applying ML to astronaut safety systems.</div>
        <div class="project-tags">
          <span class="tag tag-py">Python</span>
          <span class="tag tag-ml">Machine Learning</span>
          <span class="tag tag-ieee">IEEE Published</span>
        </div>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- IEEE ACHIEVEMENT -->
  <div class="reveal">
    <div class="achievement">
      <div class="achievement-icon">🏆</div>
      <div>
        <div class="achievement-title">IEEE ICTBIG 2025 — Published Author</div>
        <div class="achievement-sub">
          <em>"AI-Powered Astronaut Health Monitoring System"</em><br/>
          Developed predictive models to detect physiological risks in extreme environments. Bridging machine learning with real-world safety critical applications.
        </div>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- STATS -->
  <div class="reveal">
    <div class="section-label">04 / numbers</div>
    <div class="section-title">By The Numbers</div>

    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num" data-target="3">0</div>
        <div class="stat-label">Key Projects</div>
      </div>
      <div class="stat-card">
        <div class="stat-num" data-target="1">0</div>
        <div class="stat-label">IEEE Publications</div>
      </div>
      <div class="stat-card">
        <div class="stat-num" data-target="14">0</div>
        <div class="stat-label">Technologies</div>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- CONNECT -->
  <div class="reveal">
    <div class="connect">
      <div class="connect-title">Let's Build Something Remarkable</div>
      <div class="connect-sub">Open to full-time roles, research collaborations, and interesting problems.</div>
      <div class="connect-btns">
        <a href="https://www.linkedin.com/in/dhushyanth-c-163ba1297/" class="btn btn-primary" target="_blank">💼 Connect on LinkedIn</a>
        <a href="mailto:dhushyanthc005@gmail.com" class="btn btn-secondary" target="_blank">📧 dhushyanthc005@gmail.com</a>
      </div>
    </div>
  </div>

</div>

<script>
// PARTICLE SYSTEM
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');
let W = canvas.width = window.innerWidth;
let H = canvas.height = window.innerHeight;
window.addEventListener('resize', () => { W = canvas.width = window.innerWidth; H = canvas.height = window.innerHeight; });

const particles = [];
const NUM = 80;

class Particle {
  constructor() { this.reset(); }
  reset() {
    this.x = Math.random() * W;
    this.y = Math.random() * H;
    this.size = Math.random() * 1.5 + 0.5;
    this.speedX = (Math.random() - 0.5) * 0.3;
    this.speedY = (Math.random() - 0.5) * 0.3;
    this.life = 0;
    this.maxLife = Math.random() * 300 + 100;
    this.color = Math.random() > 0.5 ? '123,97,255' : '0,212,170';
  }
  update() {
    this.x += this.speedX;
    this.y += this.speedY;
    this.life++;
    if (this.life > this.maxLife || this.x < 0 || this.x > W || this.y < 0 || this.y > H) this.reset();
  }
  draw() {
    const alpha = Math.sin((this.life / this.maxLife) * Math.PI) * 0.5;
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(${this.color},${alpha})`;
    ctx.fill();
  }
}

for (let i = 0; i < NUM; i++) particles.push(new Particle());

function drawConnections() {
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const dist = Math.sqrt(dx * dx + dy * dy);
      if (dist < 100) {
        ctx.beginPath();
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        ctx.strokeStyle = `rgba(123,97,255,${0.12 * (1 - dist / 100)})`;
        ctx.lineWidth = 0.5;
        ctx.stroke();
      }
    }
  }
}

function animate() {
  ctx.clearRect(0, 0, W, H);
  particles.forEach(p => { p.update(); p.draw(); });
  drawConnections();
  requestAnimationFrame(animate);
}
animate();

// TYPING EFFECT
const lines = [
  'Building high-perf backends...',
  'Go + PostgreSQL + Redis...',
  'Fan-out feeds at scale...',
  'IEEE Published Researcher...',
  'Open to opportunities...'
];
let li = 0, ci = 0, del = false;
const el = document.getElementById('typing');

function type() {
  const cur = lines[li];
  if (!del) {
    el.textContent = cur.slice(0, ++ci);
    if (ci === cur.length) { del = true; setTimeout(type, 2000); return; }
    setTimeout(type, 60);
  } else {
    el.textContent = cur.slice(0, --ci);
    if (ci === 0) { del = false; li = (li + 1) % lines.length; setTimeout(type, 400); return; }
    setTimeout(type, 30);
  }
}
type();

// SCROLL REVEAL
const reveals = document.querySelectorAll('.reveal');
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); } });
}, { threshold: 0.1 });
reveals.forEach(r => obs.observe(r));

// COUNT UP ANIMATION
function countUp(el, target) {
  let count = 0;
  const step = target / 40;
  const interval = setInterval(() => {
    count = Math.min(count + step, target);
    el.textContent = Math.ceil(count);
    if (count >= target) clearInterval(interval);
  }, 40);
}

const statObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      const nums = e.target.querySelectorAll('.stat-num[data-target]');
      nums.forEach(n => countUp(n, +n.dataset.target));
      statObs.unobserve(e.target);
    }
  });
}, { threshold: 0.5 });

document.querySelectorAll('.stats-grid').forEach(g => statObs.observe(g));
</script>
</body>
</html>
