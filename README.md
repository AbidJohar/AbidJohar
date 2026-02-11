 <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Abid Johar — Backend Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:ital,wght@0,300;0,400;0,500;1,400&family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,700;1,9..144,300&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0c0c0e;
    --surface: #111114;
    --border: #1e1e24;
    --accent: #e8ff5a;
    --accent2: #ff6b35;
    --muted: #4a4a5a;
    --text: #d4d4e0;
    --text-dim: #7a7a90;
    --white: #f0f0f8;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    font-size: 14px;
    line-height: 1.7;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(var(--border) 1px, transparent 1px),
      linear-gradient(90deg, var(--border) 1px, transparent 1px);
    background-size: 48px 48px;
    opacity: 0.4;
    pointer-events: none;
    z-index: 0;
  }

  /* Glow blob */
  body::after {
    content: '';
    position: fixed;
    top: -200px;
    right: -200px;
    width: 600px;
    height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(232,255,90,0.06) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }

  .wrap {
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 32px 100px;
    position: relative;
    z-index: 1;
  }

  /* ── HEADER ── */
  .header {
    border: 1px solid var(--border);
    padding: 48px 40px;
    margin-bottom: 2px;
    position: relative;
    background: var(--surface);
    animation: fadeUp 0.7s ease both;
  }

  .header::before {
    content: '01 — PROFILE';
    position: absolute;
    top: -1px; left: 32px;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--muted);
    background: var(--surface);
    padding: 0 8px;
    transform: translateY(-50%);
  }

  .status-dot {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 11px;
    color: var(--text-dim);
    letter-spacing: 0.1em;
    margin-bottom: 24px;
  }

  .status-dot span {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: #4ade80;
    box-shadow: 0 0 8px #4ade80;
    animation: pulse 2s ease infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.4; }
  }

  h1 {
    font-family: 'Fraunces', serif;
    font-size: clamp(38px, 6vw, 58px);
    font-weight: 700;
    color: var(--white);
    line-height: 1.1;
    letter-spacing: -0.02em;
    margin-bottom: 8px;
  }

  h1 em {
    font-style: italic;
    color: var(--accent);
  }

  .tagline {
    font-size: 13px;
    color: var(--text-dim);
    letter-spacing: 0.05em;
    margin-bottom: 28px;
    border-left: 2px solid var(--accent);
    padding-left: 12px;
  }

  .bio {
    font-size: 15px;
    color: var(--text);
    line-height: 1.8;
    max-width: 580px;
  }

  .bio strong { color: var(--accent); font-weight: 500; }

  /* ── GRID SECTIONS ── */
  .grid-2 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    margin-bottom: 2px;
  }

  .panel {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 32px 36px;
    position: relative;
    animation: fadeUp 0.7s ease both;
  }

  .panel:nth-child(1) { animation-delay: 0.1s; }
  .panel:nth-child(2) { animation-delay: 0.2s; }

  .panel-label {
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .panel-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── WHAT I BUILD ── */
  .build-list {
    list-style: none;
  }

  .build-list li {
    padding: 10px 0;
    border-bottom: 1px solid var(--border);
    color: var(--text);
    font-size: 13px;
    display: flex;
    align-items: flex-start;
    gap: 12px;
  }

  .build-list li:last-child { border-bottom: none; }

  .build-list li .idx {
    color: var(--accent);
    font-size: 11px;
    min-width: 24px;
    opacity: 0.7;
    padding-top: 1px;
  }

  /* ── STACK ── */
  .stack-section {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 32px 36px;
    margin-bottom: 2px;
    animation: fadeUp 0.7s ease 0.3s both;
  }

  .stack-group { margin-bottom: 20px; }
  .stack-group:last-child { margin-bottom: 0; }

  .stack-category {
    font-size: 10px;
    letter-spacing: 0.15em;
    color: var(--accent2);
    margin-bottom: 10px;
    text-transform: uppercase;
  }

  .tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .tag {
    border: 1px solid var(--border);
    padding: 5px 12px;
    font-size: 12px;
    color: var(--text);
    letter-spacing: 0.03em;
    transition: all 0.2s;
    cursor: default;
  }

  .tag:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(232,255,90,0.04);
  }

  .tag.highlight {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(232,255,90,0.06);
  }

  /* ── NOW + OPEN ── */
  .now-open {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    margin-bottom: 2px;
    animation: fadeUp 0.7s ease 0.4s both;
  }

  .now-item {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 28px 32px;
  }

  .now-item h3 {
    font-family: 'Fraunces', serif;
    font-size: 18px;
    font-weight: 300;
    font-style: italic;
    color: var(--white);
    margin-bottom: 16px;
  }

  .progress-item {
    margin-bottom: 14px;
  }

  .progress-label {
    font-size: 11px;
    color: var(--text-dim);
    margin-bottom: 5px;
    letter-spacing: 0.05em;
  }

  .progress-bar {
    height: 2px;
    background: var(--border);
    position: relative;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    background: var(--accent);
    transform-origin: left;
    animation: grow 1.2s cubic-bezier(0.4,0,0.2,1) 0.8s both;
  }

  @keyframes grow {
    from { transform: scaleX(0); }
    to   { transform: scaleX(1); }
  }

  .open-pill {
    display: block;
    border: 1px solid var(--border);
    padding: 10px 16px;
    margin-bottom: 8px;
    font-size: 12px;
    color: var(--text);
    transition: all 0.2s;
    position: relative;
  }

  .open-pill:hover {
    border-color: var(--accent);
    padding-left: 24px;
  }

  .open-pill::before {
    content: '→';
    position: absolute;
    left: 6px;
    color: var(--accent);
    opacity: 0;
    transition: opacity 0.2s;
  }

  .open-pill:hover::before { opacity: 1; }

  /* ── CONNECT ── */
  .connect {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 36px 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 24px;
    animation: fadeUp 0.7s ease 0.5s both;
  }

  .connect-left h2 {
    font-family: 'Fraunces', serif;
    font-size: 28px;
    font-weight: 300;
    font-style: italic;
    color: var(--white);
    margin-bottom: 6px;
  }

  .connect-left p {
    font-size: 12px;
    color: var(--text-dim);
  }

  .connect-links {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .connect-link {
    display: flex;
    align-items: center;
    gap: 12px;
    text-decoration: none;
    color: var(--text);
    font-size: 12px;
    letter-spacing: 0.03em;
    transition: color 0.2s;
    border: 1px solid transparent;
    padding: 8px 14px;
  }

  .connect-link:hover { color: var(--accent); border-color: var(--accent); }

  .connect-link .icon {
    width: 28px; height: 28px;
    border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    font-size: 13px;
    flex-shrink: 0;
    transition: border-color 0.2s;
  }

  .connect-link:hover .icon { border-color: var(--accent); }

  /* ── FOOTER ── */
  .footer {
    margin-top: 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
    flex-wrap: wrap;
    gap: 12px;
  }

  .footer-sig {
    font-family: 'Fraunces', serif;
    font-style: italic;
    font-size: 13px;
    color: var(--text-dim);
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @media (max-width: 620px) {
    .grid-2, .now-open { grid-template-columns: 1fr; }
    .connect { flex-direction: column; }
    .header { padding: 32px 24px; }
    .wrap { padding: 32px 16px 60px; }
  }
</style>
</head>
<body>
<div class="wrap">

  <!-- HEADER -->
  <div class="header">
    <div class="status-dot"><span></span> AVAILABLE FOR WORK</div>
    <h1>Abid <em>Johar</em></h1>
    <p class="tagline">Backend Engineer · Node.js · Systems that scale</p>
    <p class="bio">
      I don't just write code — I architect systems. While most developers chase trends,
      I focus on what matters: <strong>clean APIs</strong>, <strong>secure auth flows</strong>,
      and <strong>databases that don't break at 3am</strong>. Backend is where the real product lives.
    </p>
  </div>

  <!-- WHAT I BUILD + PHILOSOPHY -->
  <div class="grid-2">
    <div class="panel">
      <div class="panel-label">02 — What I Build</div>
      <ul class="build-list">
        <li><span class="idx">01</span>REST APIs that other developers enjoy using</li>
        <li><span class="idx">02</span>Auth systems — JWT, OTP, sessions, done right</li>
        <li><span class="idx">03</span>MongoDB schemas built for real-world scale</li>
        <li><span class="idx">04</span>File upload pipelines with S3 + validation</li>
        <li><span class="idx">05</span>AWS deployments (EC2) that stay alive</li>
        <li><span class="idx">06</span>React frontends when the backend needs a face</li>
      </ul>
    </div>
    <div class="panel">
      <div class="panel-label">03 — My Engineering POV</div>
      <p style="color:var(--text-dim);font-size:13px;line-height:1.9;margin-bottom:16px;">
        A slow API is a broken API. An inconsistent response schema is a broken contract. I treat the backend like infrastructure — invisible when it works, catastrophic when it doesn't.
      </p>
      <p style="color:var(--text-dim);font-size:13px;line-height:1.9;">
        My code reviews ask one question: <span style="color:var(--accent)">what happens when this fails at scale?</span>
      </p>
    </div>
  </div>

  <!-- STACK -->
  <div class="stack-section">
    <div class="panel-label">04 — Tech Stack</div>
    <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:24px;">
      <div class="stack-group">
        <div class="stack-category">Core Backend</div>
        <div class="tags">
          <span class="tag highlight">Node.js</span>
          <span class="tag highlight">Express.js</span>
          <span class="tag">REST APIs</span>
          <span class="tag">JWT Auth</span>
        </div>
      </div>
      <div class="stack-group">
        <div class="stack-category">Data Layer</div>
        <div class="tags">
          <span class="tag highlight">MongoDB</span>
          <span class="tag highlight">Mongoose</span>
          <span class="tag">Schema Design</span>
          <span class="tag">Aggregation</span>
        </div>
      </div>
      <div class="stack-group">
        <div class="stack-category">Cloud & Infra</div>
        <div class="tags">
          <span class="tag">AWS EC2</span>
          <span class="tag">AWS S3</span>
          <span class="tag">Git</span>
          <span class="tag">GitHub</span>
        </div>
      </div>
      <div class="stack-group">
        <div class="stack-category">Frontend (when needed)</div>
        <div class="tags">
          <span class="tag">React.js</span>
          <span class="tag">Redux</span>
          <span class="tag">Tailwind CSS</span>
        </div>
      </div>
    </div>
  </div>

  <!-- NOW + OPEN TO -->
  <div class="now-open">
    <div class="now-item">
      <h3>Currently deep in...</h3>
      <div class="progress-item">
        <div class="progress-label">Backend Architecture Patterns</div>
        <div class="progress-bar"><div class="progress-fill" style="width:82%"></div></div>
      </div>
      <div class="progress-item">
        <div class="progress-label">System Design at Scale</div>
        <div class="progress-bar"><div class="progress-fill" style="width:68%;animation-delay:0.9s"></div></div>
      </div>
      <div class="progress-item">
        <div class="progress-label">Advanced AWS Deployments</div>
        <div class="progress-bar"><div class="progress-fill" style="width:55%;animation-delay:1s"></div></div>
      </div>
    </div>
    <div class="now-item">
      <h3>Open to...</h3>
      <div class="open-pill">Backend Engineer (Node.js)</div>
      <div class="open-pill">Full Stack — Backend-Focused</div>
      <div class="open-pill">OSS Collaboration on APIs</div>
       
    </div>
  </div>

  <!-- CONNECT -->
  <div class="connect">
    <div class="connect-left">
      <h2>Let's build something.</h2>
      <p>I respond within 24 hours. Always.</p>
    </div>
    <div class="connect-links">
      <a class="connect-link" href="mailto:abidjohar786@gmail.com">
        <div class="icon">✉</div>
        abidjohar786@gmail.com
      </a>
      <a class="connect-link" href="https://github.com/AbidJohar" target="_blank">
        <div class="icon">⌥</div>
        github.com/AbidJohar
      </a>
      <a class="connect-link" href="https://www.linkedin.com/in/abid-johar786/" target="_blank">
        <div class="icon">↗</div>
        linkedin.com/in/abid-johar786
      </a>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <span>ABID JOHAR · BACKEND ENGINEER · 2025</span>
    <span class="footer-sig">Always building. Always shipping.</span>
  </div>

</div>
</body>
</html>
