# 1 portfolio
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Rico · Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=DM+Sans:wght@300;400;500&family=Space+Mono&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg:        #0d0d0d;
      --surface:   #181818;
      --border:    #2a2a2a;
      --copper:    #c97d55;
      --copper-lt: #e0a07a;
      --cream:     #f0e6d3;
      --text:      #d4c9b8;
      --muted:     #6b6055;
      --radius:    14px;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      overflow-x: hidden;
    }

    /* ── NOISE OVERLAY ── */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.035'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 9999;
      opacity: .5;
    }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.2rem 3rem;
      background: rgba(13,13,13,.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
    }
    .nav-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.15rem;
      color: var(--copper);
      letter-spacing: .08em;
    }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a {
      text-decoration: none; color: var(--muted);
      font-size: .85rem; letter-spacing: .06em; text-transform: uppercase;
      transition: color .25s;
    }
    .nav-links a:hover { color: var(--cream); }
    .nav-links a.active { color: var(--copper); }

    /* ── HERO ── */
    #home {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-template-areas: "left right";
      overflow: hidden;
    }

    .hero-left {
      grid-area: left;
      position: relative;
      background: var(--surface);
      display: flex; align-items: flex-end;
      padding: 5rem 3rem 4rem;
      overflow: hidden;
    }
    .hero-left::after {
      content: 'PORTFOLIO';
      position: absolute;
      bottom: -1.5rem; left: -1rem;
      font-family: 'Playfair Display', serif;
      font-size: 9rem; font-weight: 900;
      color: transparent;
      -webkit-text-stroke: 1px rgba(201,125,85,.18);
      white-space: nowrap;
      pointer-events: none;
      user-select: none;
    }
    .hero-tag {
      display: inline-block;
      background: var(--copper);
      color: #111;
      font-size: .7rem;
      letter-spacing: .12em;
      text-transform: uppercase;
      padding: .35rem .9rem;
      border-radius: 100px;
      margin-bottom: 1.5rem;
      font-weight: 500;
    }
    .hero-name {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.8rem, 5vw, 5rem);
      line-height: 1.05;
      color: var(--cream);
    }
    .hero-name span { color: var(--copper); }
    .hero-sub {
      margin-top: 1.2rem;
      font-size: .95rem;
      color: var(--muted);
      max-width: 320px;
      line-height: 1.7;
    }
    .hero-cta {
      margin-top: 2.5rem;
      display: flex; gap: 1rem; flex-wrap: wrap;
    }
    .btn {
      display: inline-block;
      padding: .85rem 2rem;
      border-radius: var(--radius);
      font-size: .88rem;
      font-weight: 500;
      cursor: pointer;
      text-decoration: none;
      transition: transform .2s, box-shadow .2s;
    }
    .btn:hover { transform: translateY(-2px); }
    .btn-primary {
      background: var(--copper);
      color: #111;
      box-shadow: 0 6px 24px rgba(201,125,85,.35);
    }
    .btn-primary:hover { box-shadow: 0 10px 32px rgba(201,125,85,.5); }
    .btn-outline {
      border: 1.5px solid var(--border);
      color: var(--text);
    }
    .btn-outline:hover { border-color: var(--copper); color: var(--copper); }

    .hero-right {
      grid-area: right;
      display: flex; align-items: center; justify-content: center;
      padding: 7rem 4rem 4rem;
      flex-direction: column;
      gap: 1.2rem;
    }
    .hero-photo-wrap {
      width: 100%; max-width: 340px;
      position: relative;
      border-radius: 16px;
      overflow: hidden;
      border: 1.5px solid var(--border);
      aspect-ratio: 3/4;
    }
    .hero-photo-wrap img {
      width: 100%; height: 100%;
      object-fit: cover;
      display: block;
    }
    .hero-photo-wrap .photo-placeholder {
      width: 100%; height: 100%;
      background: linear-gradient(145deg, #181818, #1e2a20);
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      gap: .8rem;
    }
    .photo-placeholder span { font-size: 4rem; }
    .photo-placeholder p { font-family: 'Space Mono', monospace; font-size: .75rem; color: var(--muted); }

    .hero-card {
      width: 100%; max-width: 340px;
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 2rem;
    }
    .hero-card-label {
      font-size: .72rem;
      letter-spacing: .12em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 1.2rem;
    }
    .card-row {
      background: rgba(201,125,85,.12);
      border: 1px solid rgba(201,125,85,.2);
      border-radius: 10px;
      padding: 1rem 1.4rem;
      font-size: .95rem;
      color: var(--cream);
      margin-bottom: .7rem;
      transition: background .2s, border-color .2s;
      cursor: default;
    }
    .card-row:hover {
      background: rgba(201,125,85,.22);
      border-color: var(--copper);
    }
    .card-row:last-child { margin-bottom: 0; }
    .card-row.muted { color: var(--muted); font-style: italic; }

    /* ── SECTIONS ── */
    section { padding: 7rem 3rem; max-width: 1100px; margin: 0 auto; }

    .section-header {
      display: flex; align-items: center; gap: 1.2rem;
      margin-bottom: 3.5rem;
    }
    .section-num {
      font-family: 'Space Mono', monospace;
      font-size: .8rem;
      color: var(--copper);
      opacity: .8;
    }
    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(1.8rem, 3vw, 2.6rem);
      color: var(--cream);
    }
    .section-line {
      flex: 1;
      height: 1px;
      background: var(--border);
    }

    /* ── ABOUT ── */
    .about-card-wrap {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 3rem;
    }
    .about-card-headline {
      font-family: 'Playfair Display', serif;
      font-size: clamp(1.6rem, 3vw, 2.2rem);
      color: var(--cream);
      font-weight: 900;
      margin-bottom: 1.8rem;
    }
    .about-card-body {
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 2rem;
      margin-bottom: 2rem;
    }
    .about-card-body p {
      line-height: 1.85;
      color: var(--text);
      margin-bottom: 1rem;
      font-size: .97rem;
    }
    .about-card-body p:last-child { margin-bottom: 0; }
    .about-stats {
      display: grid; grid-template-columns: repeat(4, 1fr); gap: 1.2rem;
    }
    .stat-card {
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.5rem;
      text-align: center;
      transition: border-color .2s;
    }
    .stat-card:hover { border-color: var(--copper); }
    .stat-num {
      font-family: 'Playfair Display', serif;
      font-size: 2.4rem;
      color: var(--copper);
    }
    .stat-label { font-size: .78rem; color: var(--muted); margin-top: .3rem; letter-spacing: .06em; }

    /* ── TECH ── */
    .tech-section {
      background: var(--surface);
      padding: 7rem 0;
    }
    .tech-section .inner {
      max-width: 1100px; margin: 0 auto; padding: 0 3rem;
    }
    .tech-headline {
      font-family: 'Playfair Display', serif;
      font-size: clamp(1.3rem, 2.5vw, 1.9rem);
      color: var(--cream);
      font-weight: 700;
      margin-bottom: 2.5rem;
    }
    .tech-categories {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 1.2rem;
    }
    .tech-category {
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 1.5rem;
      transition: border-color .2s;
    }
    .tech-category:hover { border-color: var(--copper); }
    .tech-cat-label {
      font-family: 'Space Mono', monospace;
      font-size: .75rem;
      color: var(--copper);
      letter-spacing: .1em;
      margin-bottom: 1.2rem;
    }
    .tech-cat-items { display: flex; flex-direction: column; gap: .8rem; }
    .tech-cat-item {
      display: flex; align-items: center; gap: .8rem;
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: .7rem 1rem;
      font-size: .88rem;
      color: var(--text);
      transition: border-color .2s, color .2s;
    }
    .tech-cat-item:hover { border-color: var(--copper); color: var(--cream); }
    .tci-icon { font-size: 1.3rem; }

    /* ── PROJECTS / TASK CARDS ── */
    .task-cards-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 1.5rem;
    }
    .task-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 1.5rem 1.2rem;
      display: flex; flex-direction: column;
      align-items: center; text-align: center;
      gap: 1rem;
      transition: border-color .25s, transform .2s;
    }
    .task-card:hover { border-color: var(--copper); transform: translateY(-4px); }
    .task-card-label {
      font-family: 'Space Mono', monospace;
      font-size: .72rem; color: var(--muted);
      letter-spacing: .08em; align-self: flex-start;
    }
    .task-num-circle {
      width: 90px; height: 90px;
      background: #111;
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-family: 'Playfair Display', serif;
      font-size: 2.4rem; font-weight: 900;
      color: var(--cream);
      border: 2px solid var(--border);
      flex-shrink: 0;
    }
    .task-num-gold {
      border-color: var(--copper);
      box-shadow: 0 0 18px rgba(201,125,85,.3);
      color: var(--copper);
    }
    .task-card-title {
      font-size: .88rem; color: var(--text);
      line-height: 1.6; flex: 1;
    }
    .task-card-buttons {
      display: flex; flex-direction: column;
      gap: .5rem; width: 100%;
    }
    .task-btn {
      display: block;
      padding: .45rem .8rem;
      border-radius: 8px;
      border: 1px solid var(--border);
      color: var(--text); text-decoration: none;
      font-size: .78rem;
      transition: all .2s;
    }
    .task-btn:hover { border-color: var(--copper); color: var(--copper); }
    .task-btn-main {
      background: var(--copper);
      color: #111; border-color: var(--copper);
      font-weight: 600; margin-top: .3rem;
    }
    .task-btn-main:hover { background: var(--copper-lt); color: #111; }

    /* ── CONTACT ── */
    .contact-section { background: var(--surface); padding: 7rem 0; }
    .contact-section .inner { max-width: 1100px; margin: 0 auto; padding: 0 3rem; }
    .contact-simple h3 {
      font-family: 'Playfair Display', serif;
      font-size: 1.6rem; color: var(--cream); margin-bottom: .8rem;
    }
    .contact-simple p { color: var(--muted); line-height: 1.8; font-size: .95rem; margin-bottom: 2rem; }
    .contact-list { display: flex; flex-direction: column; gap: 1rem; }
    .contact-item {
      display: flex; align-items: center; gap: 1rem;
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.1rem 1.4rem;
      font-size: .95rem; color: var(--text);
      text-decoration: none;
      transition: border-color .2s, color .2s;
      max-width: 420px;
    }
    .contact-item:hover { border-color: var(--copper); color: var(--copper); }
    .contact-icon {
      width: 36px; height: 36px;
      background: rgba(201,125,85,.1);
      border: 1px solid rgba(201,125,85,.2);
      border-radius: 8px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1rem; flex-shrink: 0;
    }

    /* ── FOOTER ── */
    footer {
      text-align: center;
      padding: 2.5rem;
      border-top: 1px solid var(--border);
      font-size: .82rem;
      color: var(--muted);
    }
    footer span { color: var(--copper); }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(28px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .hero-left > * { animation: fadeUp .7s ease both; }
    .hero-left .hero-tag   { animation-delay: .1s; }
    .hero-left .hero-name  { animation-delay: .22s; }
    .hero-left .hero-sub   { animation-delay: .34s; }
    .hero-left .hero-cta   { animation-delay: .46s; }
    .hero-right > *        { animation: fadeUp .7s ease both; animation-delay: .35s; }

    .reveal { opacity: 0; transform: translateY(24px); transition: opacity .6s ease, transform .6s ease; }
    .reveal.visible { opacity: 1; transform: none; }
    @media (prefers-reduced-motion: reduce) {
      .reveal { opacity: 1; transform: none; }
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 860px) {
      #home { grid-template-columns: 1fr; }
      .hero-right { padding: 3rem 2rem; flex-direction: column; }
      .hero-left { padding: 7rem 2rem 3rem; }
      .about-stats { grid-template-columns: 1fr 1fr; }
      .tech-categories { grid-template-columns: 1fr 1fr; }
      .contact-wrap { grid-template-columns: 1fr; }
      nav { padding: 1rem 1.5rem; }
      .nav-links { gap: 1.2rem; }
      section { padding: 5rem 1.5rem; }
      .tech-section .inner,
      .contact-section .inner { padding: 0 1.5rem; }
      .tech-section,
      .contact-section { padding: 5rem 0; }
      .about-card-wrap { padding: 1.8rem; }
      .task-cards-grid { grid-template-columns: repeat(2, 1fr); }
    }
    @media (max-width: 500px) {
      .nav-links a { font-size: .75rem; }
      .nav-links { gap: .8rem; }
      .about-stats { grid-template-columns: 1fr 1fr; }
      .tech-categories { grid-template-columns: 1fr 1fr; }
      .task-cards-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <div class="nav-logo">Rico · WS101</div>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#tech">Tech</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- ═══ HERO ═══ -->
  <section id="home" style="padding:0; max-width:100%; margin:0;">
    <div class="hero-left">
      <div>
        <div class="hero-tag">WS101 · BSIT Portfolio</div>
        <h1 class="hero-name">Hewwo,<br/><span>Rico!</span> 👋</h1>
        <p class="hero-sub">
          Gamer, motor rider, explorer — and a BSIT student who loves anything fun.
          Welcome to my WS101 portfolio where I document what I've built this semester.
        </p>
        <div class="hero-cta">
          <a href="#projects" class="btn btn-primary">View My Tasks</a>
          <a href="#contact" class="btn btn-outline">Contact Me</a>
        </div>
      </div>
    </div>

    <div class="hero-right">
      <div class="hero-photo-wrap">
        <img src="ric.jpg" alt="Rico"
          onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';"/>
        <div class="photo-placeholder">
          <span>🎮</span>
          <p>// add rico.jpeg</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ═══ ABOUT ═══ -->
  <section id="about">
    <div class="reveal">
      <div class="section-header">
        <span class="section-num">01 /</span>
        <h2 class="section-title">About</h2>
        <div class="section-line"></div>
      </div>
      <div class="about-card-wrap">
        <div class="about-card-headline">Passionate About Creating</div>
        <div class="about-card-body">
          <p>Heyy! I'm <strong style="color:var(--copper)">Rico</strong>, a fun-loving BSIT student who's always up for something exciting. Gaming is my main thing — always exploring new worlds, grinding ranked, and trying out whatever looks interesting.</p>
          <p>Outside the screen, you'll catch me on my motor riding around the city. Road trips, spontaneous detours, late-night rides — always down for it. I also love watching movies, series, anime, YouTube — basically anything worth watching.</p>
          <p>In WS101, I'm learning web development from the ground up — HTML, CSS, JavaScript — and building real projects along the way. This portfolio shows everything I've made this semester.</p>
        </div>
        <div class="about-stats">
          <div class="stat-card">
            <div class="stat-num">7</div>
            <div class="stat-label">Tasks Done</div>
          </div>
          <div class="stat-card">
            <div class="stat-num">BSIT</div>
            <div class="stat-label">Course</div>
          </div>
          <div class="stat-card">
            <div class="stat-num">∞</div>
            <div class="stat-label">Hours Gamed</div>
          </div>
          <div class="stat-card">
            <div class="stat-num">100%</div>
            <div class="stat-label">Fun Level</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ═══ TECH ═══ -->
  <div class="tech-section reveal" id="tech">
    <div class="inner">
      <div class="section-header">
        <span class="section-num">02 /</span>
        <h2 class="section-title">Tech I Used</h2>
        <div class="section-line"></div>
      </div>
      <div class="tech-headline">The tools and Technologies I use to bring ideas to life</div>
      <div class="tech-categories">

        <div class="tech-category">
          <div class="tech-cat-label">Front-End</div>
          <div class="tech-cat-items">
            <div class="tech-cat-item"><span class="tci-icon">🌐</span><span>HTML</span></div>
            <div class="tech-cat-item"><span class="tci-icon">🎨</span><span>CSS</span></div>
          </div>
        </div>

        <div class="tech-category">
          <div class="tech-cat-label">Back-End</div>
          <div class="tech-cat-items">
            <div class="tech-cat-item"><span class="tci-icon">🐍</span><span>Python</span></div>
            <div class="tech-cat-item"><span class="tci-icon">☕</span><span>Java</span></div>
          </div>
        </div>

        <div class="tech-category">
          <div class="tech-cat-label">Tools</div>
          <div class="tech-cat-items">
            <div class="tech-cat-item"><span class="tci-icon">🐙</span><span>GitHub</span></div>
          </div>
        </div>

        <div class="tech-category">
          <div class="tech-cat-label">Design</div>
          <div class="tech-cat-items">
            <div class="tech-cat-item"><span class="tci-icon">🎨</span><span>Canva</span></div>
            <div class="tech-cat-item"><span class="tci-icon">✏️</span><span>Figma</span></div>
          </div>
        </div>

      </div>
    </div>
  </div>

  <!-- ═══ PROJECTS ═══ -->
  <section id="projects">
    <div class="reveal">
      <div class="section-header">
        <span class="section-num">03 /</span>
        <h2 class="section-title">My Projects</h2>
        <div class="section-line"></div>
      </div>
      <div class="task-cards-grid">

        <!-- MIDTERM TASK 1 -->
        <div class="task-card">
          <div class="task-card-label">MidTermLab Task01</div>
          <div class="task-num-circle">1</div>
          <div class="task-card-title">Resume writing</div>
          <div class="task-card-buttons">
            <a href="https://hastebin.com/share/uberudulug.xml" class="task-btn">View Source Code</a>
            <a href="resume.html" class="task-btn task-btn-main">View Project</a>
          </div>
        </div>

        <!-- MIDTERM TASK 2 -->
        <div class="task-card">
          <div class="task-card-label">MidTermLab Task02</div>
          <div class="task-num-circle">2</div>
          <div class="task-card-title">HTML lists and table</div>
          <div class="task-card-buttons">
            <a href="https://hastebin.com/share/uwahezuvot.xml" class="task-btn">View Source Code</a>
            <a href="unordered list.html" class="task-btn task-btn-main">View Project</a>
          </div>
        </div>

        <!-- MIDTERM TASK 3 -->
        <div class="task-card">
          <div class="task-card-label">MidTermLab Task03</div>
          <div class="task-num-circle">3</div>
          <div class="task-card-title">HTML Forms</div>
          <div class="task-card-buttons">
            <a href="https://hastebin.com/share/quhuyocure.xml" class="task-btn">View Source Code</a>
            <a href="form.html" class="task-btn task-btn-main">View Project</a>
          </div>
        </div>

        <!-- MIDTERM TASK 4 -->
        <div class="task-card">
          <div class="task-card-label">MidTermLab Task04</div>
          <div class="task-num-circle">4</div>
          <div class="task-card-title">Image Maps</div>
          <div class="task-card-buttons">
            <a href="#" class="task-btn">View Source Code</a>
            <a href="#" class="task-btn task-btn-main">View Project</a>
          </div>
        </div>

        <!-- MIDTERM TASK 5 -->
        <div class="task-card">
          <div class="task-card-label">MidTermLab Task05</div>
          <div class="task-num-circle">5</div>
          <div class="task-card-title">Applying CSS To Resume</div>
          <div class="task-card-buttons">
            <a href="https://hastebin.com/share/eyozezobuz.xml" class="task-btn">View Source Code</a>
            <a href="resumecss.html" class="task-btn task-btn-main">View Project</a>
          </div>
        </div>

        <!-- MIDTERM TASK 6 -->
        <div class="task-card">
          <div class="task-card-label">MidTermLab Task06</div>
          <div class="task-num-circle">6</div>
          <div class="task-card-title">Using Divs and Elements</div>
          <div class="task-card-buttons">
            <a href="https://hastebin.com/share/xuqanuburu.xml" class="task-btn">View Source Code</a>
            <a href="layout using divs.html" class="task-btn task-btn-main">View Project</a>
          </div>
        </div>

        <!-- FINAL TASK 1 -->
        <div class="task-card">
          <div class="task-card-label">Final Task01</div>
          <div class="task-num-circle task-num-gold">1</div>
          <div class="task-card-title">Responsive Layout using Flex</div>
          <div class="task-card-buttons">
            <a href="https://hastebin.com/share/lulujafuwu.php-template" class="task-btn">View Source Code</a>
            <a href="responsive layout using flex.html" class="task-btn task-btn-main">View Project</a>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- ═══ CONTACT ═══ -->
  <div class="contact-section reveal" id="contact">
    <div class="inner">
      <div class="section-header">
        <span class="section-num">04 /</span>
        <h2 class="section-title">Contact Me</h2>
        <div class="section-line"></div>
      </div>
      <div class="contact-simple">
        <h3>Let's connect!</h3>
        <p>Have questions about my tasks, want to collaborate, or just want to say hi? Feel free to reach out!</p>
        <div class="contact-list">
          <a href="mailto:ricomusngi19@gmail.com" class="contact-item">
            <div class="contact-icon">📧</div>
            <span>ricomusngi19@gmail.com</span>
          </a>
          <a href="https://facebook.com/RicodanielMusngi" target="_blank" class="contact-item">
            <div class="contact-icon">📘</div>
            <span>facebook.com/RicodanielMusngi</span>
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <footer>
    <p>Built with <span>♥</span> by <span>Rico</span> · WS101 · BSIT · &copy; 2026</p>
  </footer>

  <script>
    // SCROLL REVEAL
    const obs = new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) { e.target.classList.add('visible'); obs.unobserve(e.target); }
      });
    }, { threshold: 0.01, rootMargin: '0px 0px -50px 0px' });
    document.querySelectorAll('.reveal').forEach(el => obs.observe(el));

    // Trigger on load for anything already in view
    window.addEventListener('load', () => {
      document.querySelectorAll('.reveal').forEach(el => {
        const r = el.getBoundingClientRect();
        if (r.top < window.innerHeight) el.classList.add('visible');
      });
    });

    // ACTIVE NAV HIGHLIGHT
    window.addEventListener('scroll', () => {
      ['home','about','tech','projects','contact'].forEach(id => {
        const el = document.getElementById(id);
        if (!el) return;
        const r = el.getBoundingClientRect();
        if (r.top <= 80 && r.bottom > 80) {
          document.querySelectorAll('.nav-links a').forEach(a => a.classList.remove('active'));
          const link = document.querySelector(`.nav-links a[href="#${id}"]`);
          if (link) link.classList.add('active');
        }
      });
    });
  </script>

</body>
</html>
