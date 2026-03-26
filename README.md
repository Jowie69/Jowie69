<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Jowie Flores — Full-Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Space+Mono:wght@400;700&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --blue-deep: #020b18;
    --blue-dark: #050f1f;
    --blue-mid: #0a1f3d;
    --blue-bright: #1a6eff;
    --blue-glow: #3d8bff;
    --blue-neon: #00c6ff;
    --accent: #00e5ff;
    --text-primary: #e8f4ff;
    --text-secondary: #7db8e8;
    --text-muted: #3a6b99;
    --glass-bg: rgba(10, 31, 61, 0.55);
    --glass-border: rgba(0, 198, 255, 0.15);
    --card-glow: rgba(29, 110, 255, 0.12);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--blue-deep);
    color: var(--text-primary);
    font-family: 'Inter', sans-serif;
    overflow-x: hidden;
    min-height: 100vh;
  }

  /* ANIMATED BACKGROUND */
  .bg-canvas {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 0;
    pointer-events: none;
  }

  .orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.18;
    animation: drift 20s ease-in-out infinite alternate;
  }
  .orb-1 { width: 600px; height: 600px; background: radial-gradient(circle, #1a6eff, transparent); top: -10%; left: -10%; animation-duration: 25s; }
  .orb-2 { width: 400px; height: 400px; background: radial-gradient(circle, #00c6ff, transparent); bottom: 10%; right: -5%; animation-duration: 18s; animation-delay: -8s; }
  .orb-3 { width: 300px; height: 300px; background: radial-gradient(circle, #0056cc, transparent); top: 40%; left: 50%; animation-duration: 22s; animation-delay: -4s; }

  @keyframes drift {
    from { transform: translate(0, 0) scale(1); }
    to { transform: translate(40px, 30px) scale(1.08); }
  }

  /* GRID PATTERN */
  .grid-bg {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 0;
    background-image:
      linear-gradient(rgba(0, 198, 255, 0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0, 198, 255, 0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
  }

  /* PARTICLE CANVAS */
  #particles { position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none; }

  /* LAYOUT */
  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 60px 24px 80px;
  }

  /* HERO */
  .hero {
    text-align: center;
    padding: 0 0 60px;
    animation: fadeUp 0.9s ease both;
  }

  .badge-row {
    display: flex;
    justify-content: center;
    gap: 8px;
    margin-bottom: 28px;
    flex-wrap: wrap;
  }

  .badge {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.12em;
    padding: 5px 14px;
    border-radius: 100px;
    border: 1px solid var(--glass-border);
    background: rgba(0, 198, 255, 0.07);
    color: var(--blue-neon);
    text-transform: uppercase;
    animation: pulse-border 3s ease-in-out infinite;
  }

  @keyframes pulse-border {
    0%, 100% { border-color: rgba(0, 198, 255, 0.15); }
    50% { border-color: rgba(0, 198, 255, 0.45); }
  }

  .avatar-wrap {
    position: relative;
    display: inline-block;
    margin-bottom: 28px;
  }

  .avatar-ring {
    position: absolute;
    inset: -8px;
    border-radius: 50%;
    border: 2px solid transparent;
    background: conic-gradient(from 0deg, var(--blue-neon), var(--blue-bright), transparent, var(--blue-neon)) border-box;
    -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: destination-out;
    mask-composite: exclude;
    animation: spin 6s linear infinite;
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .avatar {
    width: 110px;
    height: 110px;
    border-radius: 50%;
    background: linear-gradient(135deg, #1a3a6e, #0a1f3d);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 36px;
    font-weight: 800;
    color: var(--blue-neon);
    letter-spacing: -1px;
  }

  .greeting {
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--blue-neon);
    letter-spacing: 0.2em;
    margin-bottom: 12px;
    opacity: 0.85;
  }

  h1.name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(42px, 8vw, 72px);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -2px;
    margin-bottom: 12px;
    background: linear-gradient(135deg, #ffffff 0%, #80c8ff 50%, var(--blue-neon) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: shimmer 4s linear infinite;
    background-size: 200% auto;
  }

  @keyframes shimmer {
    from { background-position: 0% center; }
    to { background-position: 200% center; }
  }

  .title-line {
    font-size: 17px;
    font-weight: 300;
    color: var(--text-secondary);
    letter-spacing: 0.04em;
    margin-bottom: 28px;
  }
  .title-line span {
    color: var(--text-primary);
    font-weight: 500;
  }

  .hero-links {
    display: flex;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
  }

  .btn {
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    letter-spacing: 0.08em;
    padding: 11px 24px;
    border-radius: 8px;
    text-decoration: none;
    display: inline-flex;
    align-items: center;
    gap: 8px;
    transition: all 0.25s ease;
    cursor: pointer;
  }

  .btn-primary {
    background: var(--blue-bright);
    color: #fff;
    border: 1px solid var(--blue-bright);
    box-shadow: 0 0 20px rgba(26, 110, 255, 0.35);
  }
  .btn-primary:hover {
    background: var(--blue-glow);
    box-shadow: 0 0 35px rgba(26, 110, 255, 0.6);
    transform: translateY(-2px);
  }

  .btn-ghost {
    background: var(--glass-bg);
    color: var(--text-secondary);
    border: 1px solid var(--glass-border);
    backdrop-filter: blur(10px);
  }
  .btn-ghost:hover {
    background: rgba(0, 198, 255, 0.1);
    color: var(--blue-neon);
    border-color: rgba(0, 198, 255, 0.4);
    transform: translateY(-2px);
  }

  /* SECTION */
  section { margin-bottom: 56px; animation: fadeUp 0.8s ease both; }
  section:nth-child(2) { animation-delay: 0.1s; }
  section:nth-child(3) { animation-delay: 0.2s; }
  section:nth-child(4) { animation-delay: 0.3s; }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--blue-neon);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, rgba(0, 198, 255, 0.3), transparent);
  }

  /* CARDS */
  .card {
    background: var(--glass-bg);
    border: 1px solid var(--glass-border);
    border-radius: 16px;
    padding: 24px 28px;
    backdrop-filter: blur(12px);
    position: relative;
    overflow: hidden;
    transition: transform 0.25s ease, box-shadow 0.25s ease, border-color 0.25s ease;
  }
  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(0, 198, 255, 0.5), transparent);
  }
  .card:hover {
    transform: translateY(-4px);
    box-shadow: 0 20px 60px rgba(0, 26, 80, 0.6), 0 0 30px rgba(0, 198, 255, 0.08);
    border-color: rgba(0, 198, 255, 0.3);
  }

  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 16px;
  }

  /* STATUS ITEMS */
  .status-item {
    display: flex;
    align-items: flex-start;
    gap: 14px;
    padding: 16px 0;
    border-bottom: 1px solid rgba(0, 198, 255, 0.07);
  }
  .status-item:last-child { border-bottom: none; padding-bottom: 0; }

  .status-dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--blue-neon);
    margin-top: 6px;
    flex-shrink: 0;
    box-shadow: 0 0 8px var(--blue-neon);
    animation: blink 2s ease-in-out infinite;
  }
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
  }
  .status-dot.amber { background: #f0b429; box-shadow: 0 0 8px #f0b429; }
  .status-dot.green { background: #00e676; box-shadow: 0 0 8px #00e676; animation: none; }

  .status-label {
    font-size: 12px;
    font-family: 'Space Mono', monospace;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-bottom: 4px;
  }
  .status-value {
    font-size: 14px;
    color: var(--text-primary);
    font-weight: 400;
    line-height: 1.5;
  }
  .status-value a {
    color: var(--blue-neon);
    text-decoration: none;
  }
  .status-value a:hover { text-decoration: underline; }

  /* SKILLS GRID */
  .skills-cloud {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .skill-tag {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.06em;
    padding: 6px 14px;
    border-radius: 6px;
    border: 1px solid rgba(0, 198, 255, 0.12);
    background: rgba(10, 31, 61, 0.8);
    color: var(--text-secondary);
    transition: all 0.2s ease;
    cursor: default;
  }
  .skill-tag:hover {
    background: rgba(26, 110, 255, 0.2);
    border-color: rgba(0, 198, 255, 0.4);
    color: var(--blue-neon);
    transform: translateY(-2px);
  }
  .skill-tag.featured {
    background: rgba(26, 110, 255, 0.15);
    border-color: rgba(26, 110, 255, 0.35);
    color: #80c8ff;
  }

  .category-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--text-muted);
    margin: 16px 0 8px;
  }
  .category-label:first-child { margin-top: 0; }

  /* SOCIAL GRID */
  .social-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 12px;
  }

  .social-card {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 14px 18px;
    background: rgba(10, 31, 61, 0.6);
    border: 1px solid var(--glass-border);
    border-radius: 10px;
    text-decoration: none;
    transition: all 0.2s ease;
  }
  .social-card:hover {
    background: rgba(26, 110, 255, 0.15);
    border-color: rgba(0, 198, 255, 0.35);
    transform: translateY(-2px);
  }

  .social-icon {
    width: 36px; height: 36px;
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px;
    flex-shrink: 0;
  }
  .social-icon.blue { background: rgba(26, 110, 255, 0.2); }
  .social-icon.pink { background: rgba(200, 50, 120, 0.2); }
  .social-icon.green { background: rgba(0, 200, 100, 0.2); }
  .social-icon.orange { background: rgba(255, 140, 0, 0.2); }

  .social-name {
    font-size: 13px;
    color: var(--text-primary);
    font-weight: 500;
  }
  .social-handle {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--text-muted);
    margin-top: 2px;
  }

  /* FOOTER */
  .footer {
    text-align: center;
    padding-top: 20px;
    border-top: 1px solid rgba(0, 198, 255, 0.08);
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--text-muted);
    letter-spacing: 0.1em;
  }

  .footer span {
    color: var(--blue-neon);
  }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--blue-deep); }
  ::-webkit-scrollbar-thumb { background: rgba(0, 198, 255, 0.25); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: rgba(0, 198, 255, 0.45); }

  /* TYPEWRITER */
  .typewriter {
    display: inline-block;
    overflow: hidden;
    border-right: 2px solid var(--blue-neon);
    white-space: nowrap;
    animation: typing 2.5s steps(30, end) 0.5s both, blink-caret 0.7s step-end infinite;
    max-width: 0;
  }
  @keyframes typing {
    from { max-width: 0; }
    to { max-width: 500px; }
  }
  @keyframes blink-caret {
    from, to { border-color: transparent; }
    50% { border-color: var(--blue-neon); }
  }

  /* PROFILE VIEWS BADGE */
  .views-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--text-muted);
    letter-spacing: 0.1em;
    margin-bottom: 16px;
    padding: 4px 12px;
    background: rgba(0, 198, 255, 0.04);
    border: 1px solid rgba(0, 198, 255, 0.1);
    border-radius: 100px;
  }
  .views-dot {
    width: 5px; height: 5px;
    border-radius: 50%;
    background: var(--blue-neon);
    box-shadow: 0 0 6px var(--blue-neon);
    animation: blink 1.5s ease-in-out infinite;
  }
</style>
</head>
<body>

<div class="bg-canvas">
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>
  <div class="orb orb-3"></div>
</div>
<div class="grid-bg"></div>
<canvas id="particles"></canvas>

<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="badge-row">
      <span class="badge">🇵🇭 Philippines</span>
      <span class="badge">Full-Stack Dev</span>
      <span class="badge">Open to Collab</span>
    </div>

    <div class="avatar-wrap">
      <div class="avatar-ring"></div>
      <div class="avatar">JF</div>
    </div>

    <div class="views-badge">
      <div class="views-dot"></div>
      profile active
    </div>

    <div class="greeting">// kumusta? &nbsp;·&nbsp; hello. &nbsp;·&nbsp; mabuhay.</div>

    <h1 class="name">Jowie<br>Flores</h1>

    <p class="title-line">
      Passionate <span>Full-Stack Web Developer</span><br>building at the intersection of design &amp; code
    </p>

    <div class="hero-links">
      <a href="https://flowres-automation.vercel.app/" class="btn btn-primary" target="_blank">
        ↗ My Projects
      </a>
      <a href="https://freelancer-jowie.vercel.app/" class="btn btn-ghost" target="_blank">
        View Experience
      </a>
      <a href="mailto:jowieflores032002@gmail.com" class="btn btn-ghost">
        Get in Touch
      </a>
    </div>
  </div>

  <!-- STATUS -->
  <section>
    <div class="section-label">// status.current</div>
    <div class="card">
      <div class="status-item">
        <div class="status-dot"></div>
        <div>
          <div class="status-label">Working On</div>
          <div class="status-value">
            <strong>J-Flow Services</strong> — building automation &amp; productivity tools
          </div>
        </div>
      </div>
      <div class="status-item">
        <div class="status-dot amber"></div>
        <div>
          <div class="status-label">Currently Learning</div>
          <div class="status-value typewriter">Always expanding the stack...</div>
        </div>
      </div>
      <div class="status-item">
        <div class="status-dot green"></div>
        <div>
          <div class="status-label">Projects Live At</div>
          <div class="status-value">
            <a href="https://flowres-automation.vercel.app/" target="_blank">flowres-automation.vercel.app</a>
          </div>
        </div>
      </div>
      <div class="status-item">
        <div class="status-dot green"></div>
        <div>
          <div class="status-label">Fun Fact</div>
          <div class="status-value">⚡ Constantly learning new skills — the stack never stops growing</div>
        </div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section>
    <div class="section-label">// tech.stack</div>
    <div class="card">

      <div class="category-label">Frontend</div>
      <div class="skills-cloud">
        <span class="skill-tag featured">HTML5</span>
        <span class="skill-tag featured">CSS3</span>
        <span class="skill-tag featured">JavaScript</span>
        <span class="skill-tag featured">TypeScript</span>
        <span class="skill-tag featured">Svelte</span>
        <span class="skill-tag">Bootstrap</span>
        <span class="skill-tag">Tailwind CSS</span>
        <span class="skill-tag">Sass</span>
      </div>

      <div class="category-label">Backend &amp; Frameworks</div>
      <div class="skills-cloud">
        <span class="skill-tag featured">Node.js</span>
        <span class="skill-tag featured">PHP</span>
        <span class="skill-tag featured">Laravel</span>
        <span class="skill-tag">Python</span>
        <span class="skill-tag">.NET / C#</span>
        <span class="skill-tag">Bash</span>
      </div>

      <div class="category-label">Mobile &amp; Cross-Platform</div>
      <div class="skills-cloud">
        <span class="skill-tag featured">Flutter</span>
        <span class="skill-tag featured">Dart</span>
        <span class="skill-tag">Kotlin</span>
        <span class="skill-tag">Android</span>
      </div>

      <div class="category-label">Data &amp; Databases</div>
      <div class="skills-cloud">
        <span class="skill-tag featured">MySQL</span>
        <span class="skill-tag featured">MongoDB</span>
        <span class="skill-tag">MATLAB</span>
        <span class="skill-tag">OpenCV</span>
      </div>

      <div class="category-label">Design, Tools &amp; Other</div>
      <div class="skills-cloud">
        <span class="skill-tag featured">Figma</span>
        <span class="skill-tag">Photoshop</span>
        <span class="skill-tag">Illustrator</span>
        <span class="skill-tag">Git</span>
        <span class="skill-tag">Arduino</span>
        <span class="skill-tag">Unity</span>
      </div>
    </div>
  </section>

  <!-- CONNECT -->
  <section>
    <div class="section-label">// connect.with_me</div>
    <div class="social-grid">
      <a href="mailto:jowieflores032002@gmail.com" class="social-card">
        <div class="social-icon blue">📧</div>
        <div>
          <div class="social-name">Email</div>
          <div class="social-handle">jowieflores032002@gmail.com</div>
        </div>
      </a>
      <a href="https://fb.com/jowie.flores.56" target="_blank" class="social-card">
        <div class="social-icon blue">👤</div>
        <div>
          <div class="social-name">Facebook</div>
          <div class="social-handle">jowie.flores.56</div>
        </div>
      </a>
      <a href="https://instagram.com/kuwerdas" target="_blank" class="social-card">
        <div class="social-icon pink">📸</div>
        <div>
          <div class="social-name">Instagram</div>
          <div class="social-handle">@kuwerdas</div>
        </div>
      </a>
      <a href="https://www.buymeacoffee.com/jowieflores" target="_blank" class="social-card">
        <div class="social-icon orange">☕</div>
        <div>
          <div class="social-name">Buy Me a Coffee</div>
          <div class="social-handle">Support my work</div>
        </div>
      </a>
    </div>
  </section>

  <div class="footer">
    built with <span>passion</span> &amp; <span>caffeine</span> &nbsp;·&nbsp; jowie flores &nbsp;·&nbsp; 🇵🇭 naga, bicol
  </div>

</div>

<script>
const canvas = document.getElementById('particles');
const ctx = canvas.getContext('2d');
let W, H, particles = [];

function resize() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

class Particle {
  constructor() { this.reset(); }
  reset() {
    this.x = Math.random() * W;
    this.y = Math.random() * H;
    this.size = Math.random() * 1.5 + 0.3;
    this.vx = (Math.random() - 0.5) * 0.3;
    this.vy = (Math.random() - 0.5) * 0.3;
    this.alpha = Math.random() * 0.5 + 0.1;
    this.color = Math.random() > 0.5 ? `rgba(0, 198, 255,` : `rgba(26, 110, 255,`;
  }
  update() {
    this.x += this.vx;
    this.y += this.vy;
    if (this.x < 0 || this.x > W || this.y < 0 || this.y > H) this.reset();
  }
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
    ctx.fillStyle = `${this.color}${this.alpha})`;
    ctx.fill();
  }
}

for (let i = 0; i < 120; i++) particles.push(new Particle());

function drawLines() {
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const dist = Math.sqrt(dx * dx + dy * dy);
      if (dist < 100) {
        ctx.beginPath();
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        ctx.strokeStyle = `rgba(0, 198, 255, ${0.08 * (1 - dist / 100)})`;
        ctx.lineWidth = 0.5;
        ctx.stroke();
      }
    }
  }
}

function loop() {
  ctx.clearRect(0, 0, W, H);
  particles.forEach(p => { p.update(); p.draw(); });
  drawLines();
  requestAnimationFrame(loop);
}
loop();
</script>

</body>
</html>
