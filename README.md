<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Mahesh Hansaka — Dev Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Fira+Code:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #050510;
    --surface: #0c0c1e;
    --card: #10102a;
    --border: rgba(120,80,255,0.18);
    --accent: #7c4dff;
    --accent2: #00e5ff;
    --accent3: #ff4081;
    --text: #e8e8ff;
    --muted: #8888aa;
    --glow: 0 0 30px rgba(124,77,255,0.4);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Fira Code', monospace;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.1s ease;
    box-shadow: 0 0 20px var(--accent), 0 0 40px var(--accent);
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1.5px solid rgba(124,77,255,0.5);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9998;
    transition: transform 0.15s ease, width 0.2s, height 0.2s;
  }

  /* Starfield */
  #stars {
    position: fixed; inset: 0;
    pointer-events: none;
    z-index: 0;
    overflow: hidden;
  }
  .star {
    position: absolute;
    background: white;
    border-radius: 50%;
    animation: twinkle var(--d) ease-in-out infinite;
    opacity: 0;
  }
  @keyframes twinkle {
    0%,100% { opacity: 0; transform: scale(0.5); }
    50% { opacity: var(--op); transform: scale(1); }
  }

  /* Grid lines bg */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(124,77,255,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(124,77,255,0.04) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* Floating orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    z-index: 0;
    animation: orbFloat 12s ease-in-out infinite;
  }
  .orb1 { width: 500px; height: 500px; background: rgba(124,77,255,0.12); top: -150px; right: -100px; animation-delay: 0s; }
  .orb2 { width: 400px; height: 400px; background: rgba(0,229,255,0.08); bottom: 10%; left: -150px; animation-delay: -4s; }
  .orb3 { width: 300px; height: 300px; background: rgba(255,64,129,0.07); top: 40%; right: 20%; animation-delay: -8s; }
  @keyframes orbFloat {
    0%,100% { transform: translate(0,0) scale(1); }
    33% { transform: translate(30px,-20px) scale(1.05); }
    66% { transform: translate(-20px,15px) scale(0.95); }
  }

  /* Layout */
  main { position: relative; z-index: 1; max-width: 900px; margin: 0 auto; padding: 0 24px 80px; }

  /* ========== HERO ========== */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center; align-items: center;
    text-align: center;
    padding: 60px 0 40px;
    position: relative;
  }

  .avatar-ring {
    position: relative;
    width: 130px; height: 130px;
    margin-bottom: 32px;
    animation: fadeSlideDown 0.8s ease both;
  }
  .avatar-ring::before, .avatar-ring::after {
    content: '';
    position: absolute; inset: -6px;
    border-radius: 50%;
    border: 2px solid transparent;
    background: linear-gradient(var(--bg), var(--bg)) padding-box,
                linear-gradient(135deg, var(--accent), var(--accent2), var(--accent3)) border-box;
    animation: spin 4s linear infinite;
  }
  .avatar-ring::after { inset: -12px; opacity: 0.4; animation-duration: 8s; animation-direction: reverse; }
  @keyframes spin { to { transform: rotate(360deg); } }

  .avatar-inner {
    width: 130px; height: 130px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    display: flex; align-items: center; justify-content: center;
    font-size: 52px;
    box-shadow: var(--glow);
  }

  .status-dot {
    position: absolute; bottom: 8px; right: 8px;
    width: 18px; height: 18px;
    background: #00e676;
    border-radius: 50%;
    border: 3px solid var(--bg);
    box-shadow: 0 0 12px #00e676;
    animation: pulse-dot 2s infinite;
    z-index: 2;
  }
  @keyframes pulse-dot {
    0%,100% { box-shadow: 0 0 12px #00e676; }
    50% { box-shadow: 0 0 24px #00e676, 0 0 40px #00e676; }
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(42px, 8vw, 72px);
    font-weight: 800;
    letter-spacing: -1px;
    line-height: 1;
    background: linear-gradient(135deg, #fff 0%, var(--accent) 50%, var(--accent2) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: fadeSlideDown 0.8s 0.1s ease both;
  }

  .hero-title {
    margin-top: 12px;
    font-size: 14px;
    color: var(--muted);
    letter-spacing: 3px;
    text-transform: uppercase;
    animation: fadeSlideDown 0.8s 0.2s ease both;
  }

  /* Typewriter */
  .typewriter-wrap {
    margin-top: 20px;
    font-size: 18px;
    font-weight: 500;
    animation: fadeSlideDown 0.8s 0.3s ease both;
  }
  .typewriter-prefix { color: var(--accent2); }
  .typewriter-text {
    color: var(--accent);
    border-right: 2px solid var(--accent);
    padding-right: 4px;
    animation: blink 0.8s step-end infinite;
  }
  @keyframes blink { 0%,100% { border-color: var(--accent); } 50% { border-color: transparent; } }

  .hero-badges {
    display: flex; flex-wrap: wrap; gap: 10px;
    justify-content: center;
    margin-top: 28px;
    animation: fadeSlideDown 0.8s 0.4s ease both;
  }
  .badge {
    padding: 6px 16px;
    border-radius: 999px;
    font-size: 12px;
    font-weight: 500;
    border: 1px solid;
    transition: all 0.3s;
    cursor: default;
  }
  .badge:hover { transform: translateY(-2px); box-shadow: 0 4px 20px currentColor; }
  .badge-purple { border-color: var(--accent); color: var(--accent); background: rgba(124,77,255,0.1); }
  .badge-cyan { border-color: var(--accent2); color: var(--accent2); background: rgba(0,229,255,0.08); }
  .badge-pink { border-color: var(--accent3); color: var(--accent3); background: rgba(255,64,129,0.08); }
  .badge-green { border-color: #00e676; color: #00e676; background: rgba(0,230,118,0.08); }

  .hero-links {
    display: flex; gap: 14px;
    margin-top: 32px;
    animation: fadeSlideDown 0.8s 0.5s ease both;
  }
  .hero-link {
    display: flex; align-items: center; gap: 8px;
    padding: 12px 24px;
    border-radius: 10px;
    font-size: 14px;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.3s;
    font-family: 'Fira Code', monospace;
  }
  .hero-link-primary {
    background: linear-gradient(135deg, var(--accent), #5f35d4);
    color: white;
    box-shadow: 0 4px 24px rgba(124,77,255,0.4);
  }
  .hero-link-primary:hover { transform: translateY(-3px); box-shadow: 0 8px 32px rgba(124,77,255,0.6); }
  .hero-link-secondary {
    border: 1px solid var(--border);
    color: var(--text);
    background: rgba(255,255,255,0.04);
  }
  .hero-link-secondary:hover { border-color: var(--accent); background: rgba(124,77,255,0.1); transform: translateY(-3px); }

  .scroll-hint {
    position: absolute; bottom: 30px;
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    color: var(--muted); font-size: 11px; letter-spacing: 2px;
    animation: fadeIn 1s 1.5s ease both, bobble 2s 2.5s ease-in-out infinite;
  }
  .scroll-arrow { font-size: 20px; }
  @keyframes bobble { 0%,100% { transform: translateY(0); } 50% { transform: translateY(6px); } }

  /* ========== SECTIONS ========== */
  section {
    margin-top: 80px;
    animation: fadeSlideUp 0.6s ease both;
  }

  .section-label {
    display: flex; align-items: center; gap: 12px;
    margin-bottom: 28px;
  }
  .section-label-line {
    flex: 1; height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }
  .section-label-text {
    font-family: 'Syne', sans-serif;
    font-size: 20px; font-weight: 700;
    white-space: nowrap;
  }
  .section-label-num {
    font-size: 13px; color: var(--accent);
    font-weight: 400;
  }

  /* ========== ABOUT CARD ========== */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }
  @media (max-width: 600px) { .about-grid { grid-template-columns: 1fr; } }

  .code-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
  }
  .code-card:hover { border-color: rgba(124,77,255,0.4); transform: translateY(-2px); }

  .code-card-header {
    display: flex; align-items: center; gap: 8px;
    padding: 12px 16px;
    background: rgba(0,0,0,0.3);
    border-bottom: 1px solid var(--border);
    font-size: 12px; color: var(--muted);
  }
  .dot-r { width: 10px; height: 10px; border-radius: 50%; background: #ff5f57; }
  .dot-y { width: 10px; height: 10px; border-radius: 50%; background: #febc2e; }
  .dot-g { width: 10px; height: 10px; border-radius: 50%; background: #28c840; }

  .code-card-body {
    padding: 18px 20px;
    font-size: 13px;
    line-height: 1.9;
  }
  .cl { color: var(--muted); }
  .ck { color: var(--accent); }
  .cs { color: var(--accent2); }
  .cn { color: #ff9e64; }
  .cv { color: #9ece6a; }
  .cb { color: var(--accent3); }

  /* ========== SKILLS ========== */
  .skills-tabs {
    display: flex; flex-wrap: wrap; gap: 8px;
    margin-bottom: 20px;
  }
  .tab-btn {
    padding: 7px 18px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: transparent;
    color: var(--muted);
    font-family: 'Fira Code', monospace;
    font-size: 12px;
    cursor: pointer;
    transition: all 0.2s;
  }
  .tab-btn:hover, .tab-btn.active {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(124,77,255,0.1);
  }

  .tab-panel { display: none; }
  .tab-panel.active { display: flex; flex-wrap: wrap; gap: 10px; }

  .skill-pill {
    display: flex; align-items: center; gap: 8px;
    padding: 8px 16px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    font-size: 13px;
    transition: all 0.25s;
    cursor: default;
  }
  .skill-pill:hover {
    border-color: var(--accent);
    background: rgba(124,77,255,0.12);
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(124,77,255,0.2);
  }
  .skill-icon { font-size: 18px; }

  /* ========== STATS ========== */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
  }
  @media (max-width: 600px) { .stats-grid { grid-template-columns: 1fr; } }

  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px 20px;
    text-align: center;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }
  .stat-card::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(124,77,255,0.05), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .stat-card:hover::before { opacity: 1; }
  .stat-card:hover { border-color: rgba(124,77,255,0.4); transform: translateY(-4px); }

  .stat-value {
    font-family: 'Syne', sans-serif;
    font-size: 40px; font-weight: 800;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .stat-label { font-size: 12px; color: var(--muted); margin-top: 4px; letter-spacing: 1px; }

  /* ========== ROADMAP ========== */
  .roadmap {
    position: relative;
    padding-left: 32px;
  }
  .roadmap::before {
    content: '';
    position: absolute; left: 10px; top: 8px; bottom: 8px;
    width: 2px;
    background: linear-gradient(to bottom, var(--accent), var(--accent2), var(--accent3));
    border-radius: 2px;
  }

  .roadmap-item {
    position: relative;
    padding: 0 0 28px 24px;
  }
  .roadmap-item::before {
    content: '';
    position: absolute; left: -28px; top: 6px;
    width: 12px; height: 12px;
    border-radius: 50%;
    background: var(--accent);
    box-shadow: 0 0 12px var(--accent);
    border: 2px solid var(--bg);
  }
  .roadmap-item.done::before { background: #00e676; box-shadow: 0 0 12px #00e676; }
  .roadmap-item.active-item::before {
    background: var(--accent2); box-shadow: 0 0 16px var(--accent2);
    animation: pulse-node 2s infinite;
  }
  @keyframes pulse-node {
    0%,100% { box-shadow: 0 0 12px var(--accent2); }
    50% { box-shadow: 0 0 24px var(--accent2), 0 0 40px rgba(0,229,255,0.4); }
  }

  .roadmap-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700; font-size: 15px;
    margin-bottom: 4px;
  }
  .roadmap-desc { font-size: 12px; color: var(--muted); line-height: 1.6; }
  .tag-done { color: #00e676; font-size: 11px; margin-left: 8px; }
  .tag-active { color: var(--accent2); font-size: 11px; margin-left: 8px; animation: blink 1.5s step-end infinite; }
  .tag-soon { color: var(--muted); font-size: 11px; margin-left: 8px; }

  /* ========== PROJECTS ========== */
  .projects-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  @media (max-width: 600px) { .projects-grid { grid-template-columns: 1fr; } }

  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
    text-decoration: none;
    color: var(--text);
    display: block;
  }
  .project-card::after {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(124,77,255,0.06), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .project-card:hover { border-color: rgba(124,77,255,0.5); transform: translateY(-4px); box-shadow: 0 8px 32px rgba(124,77,255,0.15); }
  .project-card:hover::after { opacity: 1; }

  .project-icon { font-size: 32px; margin-bottom: 12px; }
  .project-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700; font-size: 16px;
    margin-bottom: 6px;
  }
  .project-desc { font-size: 12px; color: var(--muted); line-height: 1.6; margin-bottom: 14px; }
  .project-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .project-tag {
    padding: 3px 10px;
    background: rgba(124,77,255,0.15);
    border: 1px solid rgba(124,77,255,0.3);
    border-radius: 6px;
    font-size: 11px;
    color: var(--accent);
  }
  .project-card.coming .project-tag { background: rgba(0,229,255,0.1); border-color: rgba(0,229,255,0.3); color: var(--accent2); }

  /* ========== CONNECT ========== */
  .connect-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
  @media (max-width: 480px) { .connect-grid { grid-template-columns: 1fr; } }

  .connect-card {
    display: flex; align-items: center; gap: 14px;
    padding: 18px 20px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    text-decoration: none;
    color: var(--text);
    transition: all 0.3s;
  }
  .connect-card:hover { border-color: var(--accent); background: rgba(124,77,255,0.1); transform: translateY(-3px); }
  .connect-card svg { flex-shrink: 0; }
  .connect-name { font-weight: 600; font-size: 14px; }
  .connect-handle { font-size: 12px; color: var(--muted); }

  /* ========== FOOTER ========== */
  footer {
    margin-top: 80px;
    padding: 32px 0;
    text-align: center;
    border-top: 1px solid var(--border);
    font-size: 12px;
    color: var(--muted);
    position: relative; z-index: 1;
  }
  .footer-glow {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 800;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 8px;
  }

  /* Animations */
  @keyframes fadeSlideDown {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; } to { opacity: 1; }
  }

  .reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .reveal.visible { opacity: 1; transform: translateY(0); }
</style>
</head>
<body>

<!-- Cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Stars -->
<div id="stars"></div>

<!-- Floating orbs -->
<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<main>

  <!-- ===== HERO ===== -->
  <section class="hero">
    <div class="avatar-ring">
      <div class="avatar-inner">👨‍💻</div>
      <div class="status-dot"></div>
    </div>

    <h1 class="hero-name">Mahesh Hansaka</h1>
    <p class="hero-title">Software Engineer &nbsp;·&nbsp; Sri Lanka 🇱🇰</p>

    <div class="typewriter-wrap">
      <span class="typewriter-prefix">$ </span>
      <span class="typewriter-text" id="typewriter"></span>
    </div>

    <div class="hero-badges">
      <span class="badge badge-purple">Full Stack Dev</span>
      <span class="badge badge-cyan">AI / ML Engineer</span>
      <span class="badge badge-pink">Deep Learning</span>
      <span class="badge badge-green">Open to Work</span>
    </div>

    <div class="hero-links">
      <a class="hero-link hero-link-primary" href="https://github.com/HansakaV" target="_blank">
        <svg width="16" height="16" fill="currentColor" viewBox="0 0 16 16"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.012 8.012 0 0 0 16 8c0-4.42-3.58-8-8-8z"/></svg>
        GitHub
      </a>
      <a class="hero-link hero-link-secondary" href="https://www.linkedin.com/in/mahesh-hansaka-1069a3310/" target="_blank">
        <svg width="16" height="16" fill="#0077b5" viewBox="0 0 16 16"><path d="M0 1.146C0 .513.526 0 1.175 0h13.65C15.474 0 16 .513 16 1.146v13.708c0 .633-.526 1.146-1.175 1.146H1.175C.526 16 0 15.487 0 14.854V1.146zm4.943 12.248V6.169H2.542v7.225h2.401zm-1.2-8.212c.837 0 1.358-.554 1.358-1.248-.015-.709-.52-1.248-1.342-1.248-.822 0-1.359.54-1.359 1.248 0 .694.521 1.248 1.327 1.248h.016zm4.908 8.212V9.359c0-.216.016-.432.08-.586.173-.431.568-.878 1.232-.878.869 0 1.216.662 1.216 1.634v3.865h2.401V9.25c0-2.22-1.184-3.252-2.764-3.252-1.274 0-1.845.7-2.165 1.193v.025h-.016a5.54 5.54 0 0 1 .016-.025V6.169h-2.4c.03.678 0 7.225 0 7.225h2.4z"/></svg>
        LinkedIn
      </a>
    </div>

    <div class="scroll-hint">
      <div class="scroll-arrow">↓</div>
      <span>scroll</span>
    </div>
  </section>

  <!-- ===== ABOUT ===== -->
  <section class="reveal">
    <div class="section-label">
      <span class="section-label-num">01</span>
      <h2 class="section-label-text">// about_me</h2>
      <div class="section-label-line"></div>
    </div>

    <div class="about-grid">
      <div class="code-card">
        <div class="code-card-header">
          <div class="dot-r"></div><div class="dot-y"></div><div class="dot-g"></div>
          <span>profile.json</span>
        </div>
        <div class="code-card-body">
          <span class="cl">{</span><br/>
          &nbsp;&nbsp;<span class="ck">"name"</span>: <span class="cs">"Mahesh Hansaka"</span>,<br/>
          &nbsp;&nbsp;<span class="ck">"role"</span>: <span class="cs">"Full Stack Engineer"</span>,<br/>
          &nbsp;&nbsp;<span class="ck">"education"</span>: <span class="cs">"IJSE"</span>,<br/>
          &nbsp;&nbsp;<span class="ck">"location"</span>: <span class="cs">"Sri Lanka 🇱🇰"</span>,<br/>
          &nbsp;&nbsp;<span class="ck">"status"</span>: <span class="cv">"learning & building"</span>,<br/>
          &nbsp;&nbsp;<span class="ck">"coffee"</span>: <span class="cn">true</span><br/>
          <span class="cl">}</span>
        </div>
      </div>

      <div class="code-card">
        <div class="code-card-header">
          <div class="dot-r"></div><div class="dot-y"></div><div class="dot-g"></div>
          <span>goals.py</span>
        </div>
        <div class="code-card-body">
          <span class="ck">goals</span> <span class="cl">=</span> [<br/>
          &nbsp;&nbsp;<span class="cs">"Master Full Stack"</span>,<br/>
          &nbsp;&nbsp;<span class="cs">"Build AI systems"</span>,<br/>
          &nbsp;&nbsp;<span class="cs">"Ship real products"</span>,<br/>
          &nbsp;&nbsp;<span class="cs">"Contribute to OSS"</span>,<br/>
          ]<br/>
          <span class="cl"># currently focused on:</span><br/>
          <span class="cb">focus</span> <span class="cl">=</span> <span class="cs">"Deep Learning 🧠"</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== SKILLS ===== -->
  <section class="reveal">
    <div class="section-label">
      <span class="section-label-num">02</span>
      <h2 class="section-label-text">// tech_stack</h2>
      <div class="section-label-line"></div>
    </div>

    <div class="skills-tabs">
      <button class="tab-btn active" data-tab="ai">🤖 AI / ML</button>
      <button class="tab-btn" data-tab="backend">⚙️ Backend</button>
      <button class="tab-btn" data-tab="frontend">🎨 Frontend</button>
      <button class="tab-btn" data-tab="data">📊 Data</button>
      <button class="tab-btn" data-tab="tools">🛠️ Tools</button>
    </div>

    <div class="tab-panel active" id="tab-ai">
      <div class="skill-pill"><span class="skill-icon">🔥</span>TensorFlow</div>
      <div class="skill-pill"><span class="skill-icon">🔦</span>PyTorch</div>
      <div class="skill-pill"><span class="skill-icon">🧠</span>Keras</div>
      <div class="skill-pill"><span class="skill-icon">🤗</span>HuggingFace</div>
      <div class="skill-pill"><span class="skill-icon">📐</span>scikit-learn</div>
      <div class="skill-pill"><span class="skill-icon">🐍</span>Python</div>
      <div class="skill-pill"><span class="skill-icon">📊</span>NumPy</div>
      <div class="skill-pill"><span class="skill-icon">🐼</span>Pandas</div>
      <div class="skill-pill"><span class="skill-icon">👁️</span>OpenCV</div>
      <div class="skill-pill"><span class="skill-icon">📓</span>Jupyter</div>
      <div class="skill-pill"><span class="skill-icon">🚀</span>FastAPI</div>
      <div class="skill-pill"><span class="skill-icon">☁️</span>MLOps</div>
    </div>
    <div class="tab-panel" id="tab-backend">
      <div class="skill-pill"><span class="skill-icon">☕</span>Java</div>
      <div class="skill-pill"><span class="skill-icon">🍃</span>Spring Boot</div>
      <div class="skill-pill"><span class="skill-icon">🌐</span>Node.js</div>
      <div class="skill-pill"><span class="skill-icon">⚡</span>Express.js</div>
      <div class="skill-pill"><span class="skill-icon">🐬</span>MySQL</div>
      <div class="skill-pill"><span class="skill-icon">🍃</span>MongoDB</div>
      <div class="skill-pill"><span class="skill-icon">🐘</span>PostgreSQL</div>
      <div class="skill-pill"><span class="skill-icon">🔑</span>REST APIs</div>
      <div class="skill-pill"><span class="skill-icon">🔒</span>JWT Auth</div>
    </div>
    <div class="tab-panel" id="tab-frontend">
      <div class="skill-pill"><span class="skill-icon">⚛️</span>React</div>
      <div class="skill-pill"><span class="skill-icon">🟨</span>JavaScript</div>
      <div class="skill-pill"><span class="skill-icon">🔷</span>TypeScript</div>
      <div class="skill-pill"><span class="skill-icon">🌊</span>Tailwind CSS</div>
      <div class="skill-pill"><span class="skill-icon">🅱️</span>Bootstrap</div>
      <div class="skill-pill"><span class="skill-icon">🌐</span>HTML5</div>
      <div class="skill-pill"><span class="skill-icon">🎨</span>CSS3</div>
    </div>
    <div class="tab-panel" id="tab-data">
      <div class="skill-pill"><span class="skill-icon">📊</span>Matplotlib</div>
      <div class="skill-pill"><span class="skill-icon">🔬</span>Seaborn</div>
      <div class="skill-pill"><span class="skill-icon">📈</span>Data Visualization</div>
      <div class="skill-pill"><span class="skill-icon">🧹</span>Data Preprocessing</div>
      <div class="skill-pill"><span class="skill-icon">🔍</span>EDA</div>
      <div class="skill-pill"><span class="skill-icon">🧮</span>Statistics</div>
    </div>
    <div class="tab-panel" id="tab-tools">
      <div class="skill-pill"><span class="skill-icon">🐙</span>Git & GitHub</div>
      <div class="skill-pill"><span class="skill-icon">🐳</span>Docker</div>
      <div class="skill-pill"><span class="skill-icon">💡</span>IntelliJ IDEA</div>
      <div class="skill-pill"><span class="skill-icon">💙</span>VS Code</div>
      <div class="skill-pill"><span class="skill-icon">📮</span>Postman</div>
      <div class="skill-pill"><span class="skill-icon">🐧</span>Linux</div>
      <div class="skill-pill"><span class="skill-icon">🏗️</span>Maven</div>
    </div>
  </section>

  <!-- ===== STATS ===== -->
  <section class="reveal">
    <div class="section-label">
      <span class="section-label-num">03</span>
      <h2 class="section-label-text">// github_stats</h2>
      <div class="section-label-line"></div>
    </div>

    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-value" data-count="5">0</div>
        <div class="stat-label">REPOSITORIES</div>
      </div>
      <div class="stat-card">
        <div class="stat-value" data-count="3">0</div>
        <div class="stat-label">PROJECTS SHIPPED</div>
      </div>
      <div class="stat-card">
        <div class="stat-value" data-count="100">0</div>
        <div class="stat-label">COMMITS THIS YEAR</div>
      </div>
    </div>

    <br/>

    <!-- GitHub contrib bar -->
    <div class="code-card" style="margin-top:0">
      <div class="code-card-header">
        <div class="dot-r"></div><div class="dot-y"></div><div class="dot-g"></div>
        <span>contribution_streak.sh</span>
      </div>
      <div class="code-card-body">
        <div style="color:var(--muted);font-size:12px;margin-bottom:10px"># languages used (estimated)</div>
        <div style="margin-bottom:10px">
          <div style="display:flex;justify-content:space-between;font-size:12px;margin-bottom:5px">
            <span style="color:#ED8B00">Java</span><span>40%</span>
          </div>
          <div style="background:rgba(255,255,255,0.06);border-radius:4px;height:6px;overflow:hidden">
            <div style="width:40%;height:100%;background:linear-gradient(90deg,#ED8B00,#f5a623);border-radius:4px;animation:barGrow 1.2s ease both"></div>
          </div>
        </div>
        <div style="margin-bottom:10px">
          <div style="display:flex;justify-content:space-between;font-size:12px;margin-bottom:5px">
            <span style="color:#F7DF1E">JavaScript</span><span>30%</span>
          </div>
          <div style="background:rgba(255,255,255,0.06);border-radius:4px;height:6px;overflow:hidden">
            <div style="width:30%;height:100%;background:linear-gradient(90deg,#F7DF1E,#ffe066);border-radius:4px;animation:barGrow 1.4s ease both"></div>
          </div>
        </div>
        <div style="margin-bottom:10px">
          <div style="display:flex;justify-content:space-between;font-size:12px;margin-bottom:5px">
            <span style="color:#3670A0">Python</span><span>20%</span>
          </div>
          <div style="background:rgba(255,255,255,0.06);border-radius:4px;height:6px;overflow:hidden">
            <div style="width:20%;height:100%;background:linear-gradient(90deg,#3670A0,#4a90d9);border-radius:4px;animation:barGrow 1.6s ease both"></div>
          </div>
        </div>
        <div>
          <div style="display:flex;justify-content:space-between;font-size:12px;margin-bottom:5px">
            <span style="color:#1572B6">CSS / HTML</span><span>10%</span>
          </div>
          <div style="background:rgba(255,255,255,0.06);border-radius:4px;height:6px;overflow:hidden">
            <div style="width:10%;height:100%;background:linear-gradient(90deg,#1572B6,#61dafb);border-radius:4px;animation:barGrow 1.8s ease both"></div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== AI/ML ROADMAP ===== -->
  <section class="reveal">
    <div class="section-label">
      <span class="section-label-num">04</span>
      <h2 class="section-label-text">// ai_ml_journey</h2>
      <div class="section-label-line"></div>
    </div>

    <div class="roadmap">
      <div class="roadmap-item done">
        <div class="roadmap-title">Python Foundations <span class="tag-done">✓ done</span></div>
        <div class="roadmap-desc">Data types, OOP, file handling, libraries ecosystem</div>
      </div>
      <div class="roadmap-item done">
        <div class="roadmap-title">Mathematics for ML <span class="tag-done">✓ done</span></div>
        <div class="roadmap-desc">Linear algebra, calculus, probability & statistics</div>
      </div>
      <div class="roadmap-item active-item">
        <div class="roadmap-title">Classical Machine Learning <span class="tag-active">⚡ active</span></div>
        <div class="roadmap-desc">Regression, classification, clustering, model evaluation with scikit-learn</div>
      </div>
      <div class="roadmap-item active-item">
        <div class="roadmap-title">Deep Learning & Neural Networks <span class="tag-active">⚡ active</span></div>
        <div class="roadmap-desc">CNNs, RNNs, transformers with TensorFlow & PyTorch</div>
      </div>
      <div class="roadmap-item">
        <div class="roadmap-title">Computer Vision <span class="tag-soon">→ soon</span></div>
        <div class="roadmap-desc">Image classification, object detection, segmentation with OpenCV</div>
      </div>
      <div class="roadmap-item">
        <div class="roadmap-title">Natural Language Processing <span class="tag-soon">→ soon</span></div>
        <div class="roadmap-desc">LLMs, fine-tuning, RAG systems with HuggingFace & LangChain</div>
      </div>
      <div class="roadmap-item">
        <div class="roadmap-title">MLOps & Deployment <span class="tag-soon">→ future</span></div>
        <div class="roadmap-desc">Model serving with FastAPI, Docker, cloud deployment, monitoring</div>
      </div>
    </div>
  </section>

  <!-- ===== PROJECTS ===== -->
  <section class="reveal">
    <div class="section-label">
      <span class="section-label-num">05</span>
      <h2 class="section-label-text">// projects</h2>
      <div class="section-label-line"></div>
    </div>

    <div class="projects-grid">
      <a class="project-card" href="https://github.com/HansakaV" target="_blank">
        <div class="project-icon">🛍️</div>
        <div class="project-name">E-Commerce Platform</div>
        <div class="project-desc">Full-stack web app with auth, product management, cart & order system</div>
        <div class="project-tags">
          <span class="project-tag">Spring Boot</span>
          <span class="project-tag">React</span>
          <span class="project-tag">MySQL</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/HansakaV" target="_blank">
        <div class="project-icon">📱</div>
        <div class="project-name">POS System</div>
        <div class="project-desc">Point of Sale with inventory management, billing & reporting dashboard</div>
        <div class="project-tags">
          <span class="project-tag">Java</span>
          <span class="project-tag">JavaFX</span>
          <span class="project-tag">MySQL</span>
        </div>
      </a>

      <div class="project-card coming" style="cursor:default">
        <div class="project-icon">🤖</div>
        <div class="project-name">ML Classifier API</div>
        <div class="project-desc">Deep learning image classifier served as a REST API with live demo</div>
        <div class="project-tags">
          <span class="project-tag">TensorFlow</span>
          <span class="project-tag">FastAPI</span>
          <span class="project-tag">Docker</span>
        </div>
      </div>

      <div class="project-card coming" style="cursor:default">
        <div class="project-icon">💬</div>
        <div class="project-name">NLP Sentiment Tool</div>
        <div class="project-desc">Real-time sentiment analysis using transformer models with React frontend</div>
        <div class="project-tags">
          <span class="project-tag">HuggingFace</span>
          <span class="project-tag">Python</span>
          <span class="project-tag">React</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== CONNECT ===== -->
  <section class="reveal">
    <div class="section-label">
      <span class="section-label-num">06</span>
      <h2 class="section-label-text">// connect</h2>
      <div class="section-label-line"></div>
    </div>

    <div class="connect-grid">
      <a class="connect-card" href="https://github.com/HansakaV" target="_blank">
        <svg width="28" height="28" fill="#aaa" viewBox="0 0 16 16"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.012 8.012 0 0 0 16 8c0-4.42-3.58-8-8-8z"/></svg>
        <div>
          <div class="connect-name">GitHub</div>
          <div class="connect-handle">@HansakaV</div>
        </div>
      </a>
      <a class="connect-card" href="https://www.linkedin.com/in/mahesh-hansaka-1069a3310/" target="_blank">
        <svg width="28" height="28" fill="#0077b5" viewBox="0 0 16 16"><path d="M0 1.146C0 .513.526 0 1.175 0h13.65C15.474 0 16 .513 16 1.146v13.708c0 .633-.526 1.146-1.175 1.146H1.175C.526 16 0 15.487 0 14.854V1.146zm4.943 12.248V6.169H2.542v7.225h2.401zm-1.2-8.212c.837 0 1.358-.554 1.358-1.248-.015-.709-.52-1.248-1.342-1.248-.822 0-1.359.54-1.359 1.248 0 .694.521 1.248 1.327 1.248h.016zm4.908 8.212V9.359c0-.216.016-.432.08-.586.173-.431.568-.878 1.232-.878.869 0 1.216.662 1.216 1.634v3.865h2.401V9.25c0-2.22-1.184-3.252-2.764-3.252-1.274 0-1.845.7-2.165 1.193v.025h-.016a5.54 5.54 0 0 1 .016-.025V6.169h-2.4c.03.678 0 7.225 0 7.225h2.4z"/></svg>
        <div>
          <div class="connect-name">LinkedIn</div>
          <div class="connect-handle">Mahesh Hansaka</div>
        </div>
      </a>
    </div>
  </section>

</main>

<footer>
  <div class="footer-glow">Mahesh Hansaka</div>
  <p>Building the future, one commit at a time 🚀</p>
  <p style="margin-top:8px;font-size:11px">Made with ❤️ &nbsp;·&nbsp; Full Stack & AI Engineer</p>
</footer>

<style>
@keyframes barGrow {
  from { width: 0 !important; }
}
</style>

<script>
// Cursor
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursorRing');
let mx = 0, my = 0, rx = 0, ry = 0;
document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; cursor.style.transform = `translate(${mx-6}px,${my-6}px)`; });
function animateRing() {
  rx += (mx - rx - 18) * 0.12;
  ry += (my - ry - 18) * 0.12;
  ring.style.transform = `translate(${rx}px,${ry}px)`;
  requestAnimationFrame(animateRing);
}
animateRing();

// Stars
const starsEl = document.getElementById('stars');
for (let i = 0; i < 120; i++) {
  const s = document.createElement('div');
  s.className = 'star';
  const size = Math.random() * 2.5 + 0.5;
  s.style.cssText = `
    width:${size}px; height:${size}px;
    left:${Math.random()*100}%;
    top:${Math.random()*100}%;
    --d:${2 + Math.random()*4}s;
    --op:${0.3 + Math.random()*0.7};
    animation-delay:${Math.random()*6}s;
  `;
  starsEl.appendChild(s);
}

// Typewriter
const phrases = [
  'building AI systems 🤖',
  'learning deep learning 🧠',
  'crafting full stack apps 🌐',
  'exploring NLP models 💬',
  'shipping cool projects 🚀',
];
let pIdx = 0, cIdx = 0, deleting = false;
const tw = document.getElementById('typewriter');
function type() {
  const current = phrases[pIdx];
  if (!deleting) {
    tw.textContent = current.slice(0, ++cIdx);
    if (cIdx === current.length) { deleting = true; setTimeout(type, 1800); return; }
  } else {
    tw.textContent = current.slice(0, --cIdx);
    if (cIdx === 0) { deleting = false; pIdx = (pIdx + 1) % phrases.length; setTimeout(type, 300); return; }
  }
  setTimeout(type, deleting ? 40 : 70);
}
type();

// Tabs
document.querySelectorAll('.tab-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.querySelectorAll('.tab-panel').forEach(p => p.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('tab-' + btn.dataset.tab).classList.add('active');
  });
});

// Scroll reveal
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.1 });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

// Count-up stats
function countUp(el) {
  const target = parseInt(el.dataset.count);
  let current = 0;
  const step = Math.ceil(target / 40);
  const interval = setInterval(() => {
    current = Math.min(current + step, target);
    el.textContent = current + (target >= 100 ? '+' : '');
    if (current >= target) clearInterval(interval);
  }, 30);
}
const statObserver = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.querySelectorAll('.stat-value').forEach(countUp);
      statObserver.unobserve(e.target);
    }
  });
});
document.querySelector('.stats-grid') && statObserver.observe(document.querySelector('.stats-grid'));
</script>
</body>
</html>
