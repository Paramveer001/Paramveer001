<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Paramveer Singh – Frontend Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #060810;
    --surface: #0d1120;
    --card: #111827;
    --border: rgba(99,210,255,0.12);
    --accent: #63d2ff;
    --accent2: #a78bfa;
    --accent3: #34d399;
    --text: #e2eaf5;
    --muted: #7a8ea8;
    --glow: rgba(99,210,255,0.25);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* ---- NOISE TEXTURE ---- */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 0; opacity: 0.5;
  }

  /* ---- GRID BG ---- */
  .grid-bg {
    position: fixed; inset: 0; z-index: 0; pointer-events: none;
    background-image:
      linear-gradient(rgba(99,210,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(99,210,255,0.03) 1px, transparent 1px);
    background-size: 48px 48px;
  }

  /* ---- ORBS ---- */
  .orb {
    position: fixed; border-radius: 50%; filter: blur(90px); pointer-events: none; z-index: 0;
  }
  .orb-1 { width: 500px; height: 500px; top: -100px; left: -150px; background: radial-gradient(circle, rgba(99,210,255,0.12), transparent 70%); }
  .orb-2 { width: 400px; height: 400px; top: 40%; right: -100px; background: radial-gradient(circle, rgba(167,139,250,0.12), transparent 70%); }
  .orb-3 { width: 350px; height: 350px; bottom: -80px; left: 30%; background: radial-gradient(circle, rgba(52,211,153,0.08), transparent 70%); }

  /* ---- WRAPPER ---- */
  .wrapper { position: relative; z-index: 1; max-width: 860px; margin: 0 auto; padding: 0 24px 80px; }

  /* ---- HERO ---- */
  .hero {
    padding: 90px 0 60px;
    text-align: center;
    position: relative;
  }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(99,210,255,0.07);
    border: 1px solid rgba(99,210,255,0.2);
    border-radius: 999px;
    padding: 6px 18px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 28px;
    animation: fadeUp 0.6s ease both;
  }
  .hero-badge .dot {
    width: 7px; height: 7px; border-radius: 50%;
    background: var(--accent3);
    box-shadow: 0 0 8px var(--accent3);
    animation: pulse 2s ease infinite;
  }
  @keyframes pulse { 0%,100%{ opacity:1; transform:scale(1); } 50%{ opacity:0.6; transform:scale(0.85); } }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.8rem, 6vw, 4.2rem);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -0.03em;
    background: linear-gradient(135deg, #fff 0%, var(--accent) 60%, var(--accent2) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
    animation: fadeUp 0.7s 0.1s ease both;
  }
  .hero-sub {
    margin-top: 16px;
    font-size: 1.05rem;
    color: var(--muted);
    max-width: 480px; margin-left: auto; margin-right: auto;
    animation: fadeUp 0.7s 0.2s ease both;
  }
  .hero-ctas {
    margin-top: 36px;
    display: flex; justify-content: center; gap: 14px; flex-wrap: wrap;
    animation: fadeUp 0.7s 0.3s ease both;
  }
  .btn-primary {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--accent); color: #040810;
    font-family: 'Syne', sans-serif; font-weight: 700; font-size: 0.85rem;
    letter-spacing: 0.06em; text-transform: uppercase;
    padding: 12px 28px; border-radius: 6px; text-decoration: none;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 0 24px rgba(99,210,255,0.3);
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 4px 32px rgba(99,210,255,0.45); }
  .btn-ghost {
    display: inline-flex; align-items: center; gap: 8px;
    border: 1px solid var(--border); color: var(--text);
    font-family: 'Syne', sans-serif; font-weight: 600; font-size: 0.85rem;
    letter-spacing: 0.06em; text-transform: uppercase;
    padding: 12px 28px; border-radius: 6px; text-decoration: none;
    transition: border-color 0.2s, color 0.2s, background 0.2s;
    background: rgba(255,255,255,0.03);
  }
  .btn-ghost:hover { border-color: var(--accent); color: var(--accent); background: rgba(99,210,255,0.06); }

  /* ---- SECTION ---- */
  .section { margin-top: 80px; }
  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--accent); margin-bottom: 14px;
    display: flex; align-items: center; gap: 10px;
  }
  .section-label::after { content: ''; flex: 1; height: 1px; background: var(--border); }
  .section-title {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: clamp(1.6rem, 3.5vw, 2.2rem);
    letter-spacing: -0.02em; line-height: 1.1;
    margin-bottom: 10px;
  }
  .section-desc { color: var(--muted); max-width: 560px; margin-bottom: 36px; }

  /* ---- ABOUT CARDS ---- */
  .about-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 16px;
  }
  .about-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px; padding: 22px 20px;
    position: relative; overflow: hidden;
    transition: transform 0.2s, border-color 0.2s;
    cursor: default;
  }
  .about-card::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(99,210,255,0.04), transparent);
    opacity: 0; transition: opacity 0.25s;
  }
  .about-card:hover { transform: translateY(-4px); border-color: rgba(99,210,255,0.3); }
  .about-card:hover::before { opacity: 1; }
  .about-card .icon { font-size: 1.6rem; margin-bottom: 10px; }
  .about-card h4 { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 0.88rem; margin-bottom: 5px; }
  .about-card p { font-size: 0.78rem; color: var(--muted); line-height: 1.5; }

  /* ---- TECH STACK ---- */
  .tech-grid {
    display: flex; flex-wrap: wrap; gap: 10px;
  }
  .tech-pill {
    display: flex; align-items: center; gap: 8px;
    background: var(--card); border: 1px solid var(--border);
    border-radius: 8px; padding: 10px 16px;
    font-family: 'Space Mono', monospace; font-size: 12px; color: var(--text);
    transition: border-color 0.2s, color 0.2s, transform 0.2s;
    cursor: default;
  }
  .tech-pill:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }
  .tech-pill .tech-dot {
    width: 6px; height: 6px; border-radius: 50%;
  }

  /* ---- PROJECT CARDS ---- */
  .projects-grid { display: grid; gap: 20px; }
  .project-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 28px 28px 24px;
    position: relative; overflow: hidden;
    transition: transform 0.25s, border-color 0.25s;
  }
  .project-card::after {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    opacity: 0; transition: opacity 0.25s;
  }
  .project-card:hover { transform: translateY(-5px); border-color: rgba(99,210,255,0.25); }
  .project-card:hover::after { opacity: 1; }

  .project-header { display: flex; align-items: flex-start; justify-content: space-between; gap: 16px; margin-bottom: 12px; }
  .project-meta { flex: 1; }
  .project-tag {
    font-family: 'Space Mono', monospace; font-size: 10px; letter-spacing: 0.15em;
    text-transform: uppercase; color: var(--accent2);
    background: rgba(167,139,250,0.1); border: 1px solid rgba(167,139,250,0.15);
    border-radius: 4px; padding: 3px 9px; display: inline-block; margin-bottom: 10px;
  }
  .project-title {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: 1.3rem; letter-spacing: -0.02em; margin-bottom: 4px;
  }
  .project-subtitle { color: var(--muted); font-size: 0.82rem; }
  .project-links { display: flex; gap: 8px; flex-shrink: 0; margin-top: 4px; }
  .project-link {
    display: inline-flex; align-items: center; justify-content: center;
    width: 34px; height: 34px; border-radius: 8px;
    border: 1px solid var(--border); background: rgba(255,255,255,0.03);
    color: var(--muted); text-decoration: none; font-size: 14px;
    transition: border-color 0.2s, color 0.2s, background 0.2s;
  }
  .project-link:hover { border-color: var(--accent); color: var(--accent); background: rgba(99,210,255,0.08); }

  .project-desc { color: var(--muted); font-size: 0.88rem; margin-bottom: 18px; line-height: 1.6; }

  .feature-list {
    display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 20px;
  }
  .feature-chip {
    font-size: 0.76rem; color: var(--text); background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08); border-radius: 5px;
    padding: 4px 10px;
  }

  .stack-row { display: flex; flex-wrap: wrap; gap: 7px; }
  .stack-tag {
    font-family: 'Space Mono', monospace; font-size: 10px;
    color: var(--accent3); background: rgba(52,211,153,0.08);
    border: 1px solid rgba(52,211,153,0.15);
    border-radius: 4px; padding: 3px 9px; letter-spacing: 0.06em;
  }

  /* ---- STATS ---- */
  .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 16px; }
  .stat-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 12px; overflow: hidden;
  }
  .stat-card img { width: 100%; display: block; }

  /* ---- DELIVER ---- */
  .deliver-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 14px; }
  .deliver-item {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 10px; padding: 18px 16px;
    display: flex; align-items: flex-start; gap: 12px;
    transition: border-color 0.2s, transform 0.2s;
  }
  .deliver-item:hover { border-color: var(--accent3); transform: translateY(-3px); }
  .deliver-check {
    width: 20px; height: 20px; border-radius: 50%; flex-shrink: 0; margin-top: 2px;
    background: rgba(52,211,153,0.15); border: 1px solid rgba(52,211,153,0.3);
    display: flex; align-items: center; justify-content: center;
    color: var(--accent3); font-size: 11px;
  }
  .deliver-item span { font-size: 0.84rem; line-height: 1.5; }

  /* ---- CONNECT ---- */
  .connect-bar {
    margin-top: 80px;
    background: var(--card); border: 1px solid var(--border);
    border-radius: 20px; padding: 48px 40px;
    text-align: center; position: relative; overflow: hidden;
  }
  .connect-bar::before {
    content: '';
    position: absolute; top: -60px; left: 50%; transform: translateX(-50%);
    width: 300px; height: 200px;
    background: radial-gradient(circle, rgba(99,210,255,0.12), transparent 70%);
    pointer-events: none;
  }
  .connect-bar h2 {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: clamp(1.4rem, 3vw, 2rem); letter-spacing: -0.02em;
    margin-bottom: 10px;
  }
  .connect-bar p { color: var(--muted); margin-bottom: 28px; }
  .connect-links { display: flex; justify-content: center; gap: 14px; flex-wrap: wrap; }
  .connect-link {
    display: inline-flex; align-items: center; gap: 9px;
    background: rgba(255,255,255,0.04); border: 1px solid var(--border);
    border-radius: 8px; padding: 11px 22px; text-decoration: none;
    color: var(--text); font-size: 0.85rem; font-weight: 500;
    transition: border-color 0.2s, color 0.2s, transform 0.2s;
  }
  .connect-link:hover { transform: translateY(-2px); border-color: var(--accent); color: var(--accent); }
  .connect-link svg { width: 16px; height: 16px; }

  /* ---- FOOTER ---- */
  footer {
    text-align: center; padding: 32px 0 0;
    font-family: 'Space Mono', monospace; font-size: 11px;
    color: var(--muted); letter-spacing: 0.08em;
  }
  footer a { color: var(--accent); text-decoration: none; }

  /* ---- ANIM ---- */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .reveal { opacity: 0; transform: translateY(22px); transition: opacity 0.55s ease, transform 0.55s ease; }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ---- SCROLLBAR ---- */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: rgba(99,210,255,0.2); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: rgba(99,210,255,0.4); }

  @media (max-width: 600px) {
    .wrapper { padding: 0 16px 60px; }
    .hero { padding: 60px 0 40px; }
    .connect-bar { padding: 36px 24px; }
    .project-card { padding: 20px; }
  }
</style>
</head>
<body>
<div class="grid-bg"></div>
<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<div class="wrapper">

  <!-- HERO -->
  <section class="hero">
    <div class="hero-badge"><span class="dot"></span> Open to Frontend Roles</div>
    <h1>Paramveer Singh<br>Pundhir</h1>
    <p class="hero-sub">Frontend Developer crafting <strong style="color:#fff">high-performance</strong> UI with Next.js, React &amp; Tailwind CSS — pixel-perfect, scalable, real-world ready.</p>
    <div class="hero-ctas">
      <a href="https://www.linkedin.com/in/paramveer-singh-pundhir-psp/" class="btn-primary" target="_blank">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
      </a>
      <a href="mailto:paramveersinghpundhir001@gmail.com" class="btn-ghost" target="_blank">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
        Email Me
      </a>
    </div>
  </section>

  <!-- ABOUT -->
  <section class="section reveal">
    <p class="section-label">About</p>
    <h2 class="section-title">What I Bring to the Table</h2>
    <p class="section-desc">Focused on building clean, scalable interfaces that perform as good as they look — with attention to every detail from Core Web Vitals to accessibility.</p>
    <div class="about-grid">
      <div class="about-card">
        <div class="icon">⚛️</div>
        <h4>React & Next.js</h4>
        <p>Strong foundation in component-driven architecture and SSR/SSG patterns.</p>
      </div>
      <div class="about-card">
        <div class="icon">🎨</div>
        <h4>Pixel-Perfect UI</h4>
        <p>Translating Figma designs into flawless, responsive interfaces with Tailwind.</p>
      </div>
      <div class="about-card">
        <div class="icon">⚡</div>
        <h4>Performance First</h4>
        <p>Core Web Vitals optimized — lazy loading, code splitting, minimal bundle size.</p>
      </div>
      <div class="about-card">
        <div class="icon">📱</div>
        <h4>Mobile-First</h4>
        <p>Every project starts responsive — fluid layouts from 320px to 4K.</p>
      </div>
      <div class="about-card">
        <div class="icon">♿</div>
        <h4>SEO & A11y</h4>
        <p>Semantic HTML, ARIA, and meta-tag best practices baked in from day one.</p>
      </div>
      <div class="about-card">
        <div class="icon">🔗</div>
        <h4>Full-Stack Aware</h4>
        <p>Comfortable integrating REST APIs, Node.js backends, and MongoDB data layers.</p>
      </div>
    </div>
  </section>

  <!-- TECH STACK -->
  <section class="section reveal">
    <p class="section-label">Stack</p>
    <h2 class="section-title">Technologies I Use</h2>
    <p class="section-desc">Day-to-day tools that power every project I ship.</p>
    <div class="tech-grid">
      <div class="tech-pill"><span class="tech-dot" style="background:#e44d26"></span>HTML5</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#264de4"></span>CSS3</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#f0db4f"></span>JavaScript</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#61dafb"></span>React.js</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#fff"></span>Next.js</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#38bdf8"></span>Tailwind CSS</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#68a063"></span>Node.js</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#4ea94b"></span>MongoDB</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#f05033"></span>Git</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#333"></span>GitHub</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#007acc"></span>VS Code</div>
      <div class="tech-pill"><span class="tech-dot" style="background:#a259ff"></span>Figma</div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section class="section reveal">
    <p class="section-label">Projects</p>
    <h2 class="section-title">Featured Work</h2>
    <p class="section-desc">Real-world projects built and shipped with modern web technologies.</p>
    <div class="projects-grid">

      <!-- SiyaEdu -->
      <div class="project-card">
        <div class="project-header">
          <div class="project-meta">
            <span class="project-tag">Full-Stack</span>
            <div class="project-title">SiyaEdu</div>
            <div class="project-subtitle">Education Platform – course info, student inquiries & email notifications</div>
          </div>
          <div class="project-links">
            <a href="https://www.siyaedu.in/" class="project-link" target="_blank" title="Live Demo">
              <svg viewBox="0 0 24 24" width="15" height="15" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
            </a>
            <a href="https://github.com/Paramveer001" class="project-link" target="_blank" title="GitHub">
              <svg viewBox="0 0 24 24" width="15" height="15" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
            </a>
          </div>
        </div>
        <p class="project-desc">Modern education platform for course discovery and student inquiries, with automated email notifications and a RESTful backend.</p>
        <div class="feature-list">
          <span class="feature-chip">Interactive course pages</span>
          <span class="feature-chip">Contact & inquiry forms</span>
          <span class="feature-chip">Nodemailer notifications</span>
          <span class="feature-chip">REST API + MongoDB</span>
        </div>
        <div class="stack-row">
          <span class="stack-tag">MongoDB</span>
          <span class="stack-tag">Express.js</span>
          <span class="stack-tag">React.js</span>
          <span class="stack-tag">Node.js</span>
          <span class="stack-tag">Nodemailer</span>
          <span class="stack-tag">Tailwind CSS</span>
        </div>
      </div>

      <!-- Task Management -->
      <div class="project-card">
        <div class="project-header">
          <div class="project-meta">
            <span class="project-tag">Frontend</span>
            <div class="project-title">Task Management Software</div>
            <div class="project-subtitle">Modern dashboard UI for task tracking & team workflow</div>
          </div>
          <div class="project-links">
            <a href="https://taskmanagement.drishtiinfotech.net/" class="project-link" target="_blank" title="Live Demo">
              <svg viewBox="0 0 24 24" width="15" height="15" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
            </a>
            <a href="https://github.com/Paramveer001/task-management-frontend" class="project-link" target="_blank" title="GitHub">
              <svg viewBox="0 0 24 24" width="15" height="15" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
            </a>
          </div>
        </div>
        <p class="project-desc">A clean, reusable component-driven dashboard with task creation, status tracking, and fully responsive layout — optimized with Next.js rendering strategies.</p>
        <div class="feature-list">
          <span class="feature-chip">Task creation & status</span>
          <span class="feature-chip">Reusable components</span>
          <span class="feature-chip">Responsive layout</span>
          <span class="feature-chip">Next.js rendering</span>
        </div>
        <div class="stack-row">
          <span class="stack-tag">Next.js</span>
          <span class="stack-tag">Tailwind CSS</span>
          <span class="stack-tag">React</span>
        </div>
      </div>

      <!-- Swiftopay -->
      <div class="project-card">
        <div class="project-header">
          <div class="project-meta">
            <span class="project-tag">Fintech UI</span>
            <div class="project-title">Swiftopay</div>
            <div class="project-subtitle">Clean & professional payment platform frontend</div>
          </div>
          <div class="project-links">
            <a href="https://www.swiftopay.com/" class="project-link" target="_blank" title="Live Demo">
              <svg viewBox="0 0 24 24" width="15" height="15" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
            </a>
            <a href="https://github.com/Paramveer001/swiftopay-frontend" class="project-link" target="_blank" title="GitHub">
              <svg viewBox="0 0 24 24" width="15" height="15" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
            </a>
          </div>
        </div>
        <p class="project-desc">Fintech-grade UI with a modern design system, mobile-first layout, and fast routing — built to inspire trust and conversion in the payments space.</p>
        <div class="feature-list">
          <span class="feature-chip">Fintech design system</span>
          <span class="feature-chip">Mobile-first</span>
          <span class="feature-chip">Fast routing</span>
        </div>
        <div class="stack-row">
          <span class="stack-tag">Next.js</span>
          <span class="stack-tag">Tailwind CSS</span>
          <span class="stack-tag">React</span>
        </div>
      </div>

      <!-- Debt Settlement -->
      <div class="project-card">
        <div class="project-header">
          <div class="project-meta">
            <span class="project-tag">Corporate UI</span>
            <div class="project-title">Debt Settlement Website</div>
            <div class="project-subtitle">Professional finance & debt resolution platform UI</div>
          </div>
          <div class="project-links">
            <a href="https://www.debtsettelment.com/" class="project-link" target="_blank" title="Live Demo">
              <svg viewBox="0 0 24 24" width="15" height="15" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
            </a>
            <a href="https://github.com/Paramveer001/debt-settlement-frontend" class="project-link" target="_blank" title="GitHub">
              <svg viewBox="0 0 24 24" width="15" height="15" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
            </a>
          </div>
        </div>
        <p class="project-desc">Corporate-style layout with SEO-optimized informational pages, clean typography, and performance-tuned frontend targeting finance industry standards.</p>
        <div class="feature-list">
          <span class="feature-chip">Corporate layout</span>
          <span class="feature-chip">SEO-friendly pages</span>
          <span class="feature-chip">Responsive design</span>
          <span class="feature-chip">Optimized performance</span>
        </div>
        <div class="stack-row">
          <span class="stack-tag">Next.js</span>
          <span class="stack-tag">Tailwind CSS</span>
          <span class="stack-tag">React</span>
        </div>
      </div>

    </div>
  </section>

  <!-- GITHUB STATS -->
  <section class="section reveal">
    <p class="section-label">Stats</p>
    <h2 class="section-title">GitHub Activity</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api?username=Paramveer001&show_icons=true&theme=react&hide_border=true&bg_color=111827&title_color=63d2ff&icon_color=63d2ff&text_color=e2eaf5" alt="GitHub Stats"/>
      </div>
      <div class="stat-card">
        <img src="https://github-readme-streak-stats.herokuapp.com/?user=Paramveer001&theme=react&hide_border=true&background=111827&ring=63d2ff&fire=a78bfa&currStreakLabel=63d2ff" alt="GitHub Streak"/>
      </div>
    </div>
    <div style="margin-top:14px" class="stat-card">
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Paramveer001&layout=compact&theme=react&hide_border=true&bg_color=111827&title_color=63d2ff&text_color=e2eaf5" alt="Top Languages" style="width:100%;display:block"/>
    </div>
  </section>

  <!-- WHAT I DELIVER -->
  <section class="section reveal">
    <p class="section-label">Value</p>
    <h2 class="section-title">What I Deliver</h2>
    <div class="deliver-grid">
      <div class="deliver-item"><div class="deliver-check">✓</div><span>Clean & scalable frontend architecture</span></div>
      <div class="deliver-item"><div class="deliver-check">✓</div><span>High-performance Next.js UI</span></div>
      <div class="deliver-item"><div class="deliver-check">✓</div><span>SEO & accessibility best practices</span></div>
      <div class="deliver-item"><div class="deliver-check">✓</div><span>Pixel-perfect responsive designs</span></div>
    </div>
  </section>

  <!-- CONNECT -->
  <div class="connect-bar reveal">
    <h2>Let's Build Something Together</h2>
    <p>Open to Frontend / React / Next.js Developer roles — reach out and let's talk.</p>
    <div class="connect-links">
      <a href="https://www.linkedin.com/in/paramveer-singh-pundhir-psp/" class="connect-link" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
      </a>
      <a href="mailto:paramveersinghpundhir001@gmail.com" class="connect-link" target="_blank">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
        Gmail
      </a>
      <a href="https://github.com/Paramveer001" class="connect-link" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
        GitHub
      </a>
    </div>
  </div>

  <footer>
    <p>Built with ❤️ by <a href="https://github.com/Paramveer001">Paramveer Singh Pundhir</a> &nbsp;·&nbsp; Frontend Developer</p>
  </footer>

</div>

<script>
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); } });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>
