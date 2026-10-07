<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Anurag Rastogi · 3D Developer Profile</title>
  <!-- Google Fonts & Font Awesome for icons -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700;14..32,800&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #0a0c10;
      background-image: radial-gradient(circle at 20% 30%, rgba(0, 198, 255, 0.08) 0%, transparent 30%),
                        radial-gradient(circle at 80% 70%, rgba(30, 58, 138, 0.15) 0%, transparent 40%),
                        linear-gradient(145deg, #0b0e14 0%, #0f131c 100%);
      font-family: 'Inter', sans-serif;
      color: #e5e9f0;
      padding: 2rem 1rem;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      perspective: 1200px;
    }

    .profile-container {
      max-width: 1280px;
      width: 100%;
      display: flex;
      flex-direction: column;
      gap: 2.5rem;
      transform-style: preserve-3d;
      animation: floatIn 1s ease-out;
    }

    /* 3D card base */
    .card-3d {
      background: rgba(18, 23, 33, 0.75);
      backdrop-filter: blur(8px);
      border: 1px solid rgba(255, 255, 255, 0.06);
      border-radius: 2rem;
      box-shadow: 0 30px 40px -20px rgba(0, 0, 0, 0.8), 0 0 0 1px rgba(255, 255, 255, 0.02) inset;
      padding: 2rem 2rem;
      transition: transform 0.25s ease, box-shadow 0.3s ease;
      transform-style: preserve-3d;
      transform: rotateX(0deg) rotateY(0deg);
    }

    .card-3d:hover {
      box-shadow: 0 40px 60px -20px rgba(0, 198, 255, 0.2), 0 0 0 1px rgba(0, 198, 255, 0.2) inset;
      transform: translateY(-4px) rotateX(0.5deg) rotateY(0.5deg);
    }

    /* headers */
    h2 {
      font-size: 1.8rem;
      font-weight: 700;
      letter-spacing: -0.02em;
      margin-bottom: 1.5rem;
      display: flex;
      align-items: center;
      gap: 0.6rem;
      color: #fff;
    }

    h2 i {
      color: #00c6ff;
      font-size: 1.8rem;
      text-shadow: 0 0 15px rgba(0, 198, 255, 0.6);
    }

    .section-divider {
      width: 100%;
      height: 1px;
      background: linear-gradient(90deg, transparent, rgba(0, 198, 255, 0.3), transparent);
      margin: 1.5rem 0;
    }

    /* Typography */
    .mono {
      font-family: 'JetBrains Mono', monospace;
    }

    /* HEADER SECTION – 3D name */
    .hero-3d {
      text-align: center;
      padding: 2rem 0.5rem 3rem;
      position: relative;
      transform-style: preserve-3d;
    }

    .hero-3d h1 {
      font-size: 5rem;
      font-weight: 800;
      letter-spacing: -0.03em;
      line-height: 1.1;
      background: linear-gradient(135deg, #fff 0%, #a0d8ff 40%, #00c6ff 80%);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      text-shadow: 0 0 30px rgba(0, 198, 255, 0.3);
      transform: translateZ(40px);
      animation: glitch 4s infinite alternate;
    }

    .hero-3d .subhead {
      font-size: 1.3rem;
      color: #9aa8b9;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-top: 0.5rem;
      transform: translateZ(20px);
      font-weight: 400;
    }

    /* Typing SVG replacement – animated text */
    .typing-demo {
      font-family: 'JetBrains Mono', monospace;
      font-size: 1.25rem;
      color: #00f7ff;
      margin-top: 1.5rem;
      min-height: 2.5rem;
      display: flex;
      justify-content: center;
      gap: 0.2rem;
      transform: translateZ(10px);
      text-shadow: 0 0 10px rgba(0, 247, 255, 0.5);
    }

    .typing-demo span {
      display: inline-block;
      overflow: hidden;
      white-space: nowrap;
      border-right: 2px solid #00f7ff;
      animation: blink 0.9s step-end infinite;
      padding-right: 4px;
    }

    @keyframes blink {
      0%, 100% { border-color: transparent; }
      50% { border-color: #00f7ff; }
    }

    /* stats badges 3d */
    .badge-group {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      transform-style: preserve-3d;
    }

    .badge-3d {
      background: rgba(0, 198, 255, 0.08);
      border: 1px solid rgba(0, 198, 255, 0.2);
      border-radius: 60px;
      padding: 0.5rem 1.5rem;
      font-weight: 600;
      font-size: 0.95rem;
      color: #b0e0ff;
      box-shadow: 0 15px 20px -10px rgba(0, 0, 0, 0.6), 0 0 0 1px rgba(0, 198, 255, 0.1) inset;
      transition: all 0.2s ease;
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      transform: translateZ(0px);
    }

    .badge-3d:hover {
      transform: translateY(-4px) scale(1.02) translateZ(10px);
      border-color: #00c6ff;
      box-shadow: 0 25px 30px -10px #00c6ff40;
    }

    /* Grid Layout */
    .grid-2 {
      display: grid;
      grid-template-columns: 1.2fr 0.8fr;
      gap: 2rem;
      align-items: center;
    }

    .grid-2-equal {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.8rem;
    }

    /* Terminal */
    .terminal-window {
      background: #0d1117;
      border-radius: 1.5rem;
      border: 1px solid #2d333b;
      box-shadow: 0 40px 50px -25px #000000, 0 0 0 1px #1e2530 inset;
      padding: 1.5rem 1.8rem;
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.95rem;
      color: #c9d1d9;
      line-height: 1.7;
      transform: rotateX(0.5deg) rotateY(-0.5deg);
      transition: transform 0.3s;
    }

    .terminal-window:hover {
      transform: rotateX(0deg) rotateY(0deg) scale(1.005);
    }

    .terminal-header {
      display: flex;
      gap: 0.5rem;
      margin-bottom: 1.2rem;
      color: #6e7681;
    }

    .terminal-header .dot {
      width: 14px;
      height: 14px;
      border-radius: 50%;
      background: #ff5f56;
    }

    .terminal-header .dot:nth-child(2) { background: #ffbd2e; }
    .terminal-header .dot:nth-child(3) { background: #27c93f; }

    .terminal-line {
      color: #8b949e;
    }

    .terminal-cmd {
      color: #00f7ff;
    }

    .terminal-out {
      color: #e5e9f0;
    }

    .progress-bar {
      display: inline-block;
      background: #2d333b;
      border-radius: 20px;
      height: 10px;
      width: 200px;
      margin-left: 12px;
      vertical-align: middle;
      overflow: hidden;
    }

    .progress-fill {
      height: 100%;
      background: linear-gradient(90deg, #00c6ff, #0072ff);
      border-radius: 20px;
      box-shadow: 0 0 12px #00c6ff;
    }

    /* Skill icons (simulated) */
    .skill-icons {
      display: flex;
      flex-wrap: wrap;
      gap: 0.8rem;
      justify-content: center;
      margin: 0.5rem 0 1rem;
    }

    .skill-icon-3d {
      background: #1a1f2b;
      border-radius: 16px;
      padding: 0.7rem 1rem;
      font-weight: 600;
      font-size: 0.9rem;
      color: #b0c4de;
      border: 1px solid #2f3745;
      box-shadow: 0 10px 15px -8px black;
      transition: all 0.2s;
      display: flex;
      align-items: center;
      gap: 0.4rem;
    }

    .skill-icon-3d i {
      color: #00c6ff;
      font-size: 1.2rem;
    }

    .skill-icon-3d:hover {
      transform: translateY(-5px) translateZ(8px);
      border-color: #00c6ff;
    }

    /* DSA progress list */
    .dsa-item {
      display: flex;
      align-items: center;
      gap: 0.8rem;
      font-size: 0.9rem;
      margin-bottom: 0.5rem;
      font-family: 'JetBrains Mono', monospace;
    }

    .dsa-bar {
      flex: 1;
      height: 8px;
      background: #1e2530;
      border-radius: 10px;
      overflow: hidden;
    }

    .dsa-fill {
      height: 100%;
      background: linear-gradient(90deg, #00c6ff, #3b82f6);
      border-radius: 10px;
    }

    /* project cards */
    .project-card {
      background: #11161f;
      border-radius: 1.5rem;
      padding: 1.8rem 1.5rem;
      border: 1px solid #222a36;
      box-shadow: 0 30px 30px -20px #000000;
      transition: all 0.25s;
      height: 100%;
      display: flex;
      flex-direction: column;
      transform-style: preserve-3d;
    }

    .project-card:hover {
      transform: translateY(-8px) rotateX(1deg) rotateY(-1deg);
      border-color: #00c6ff50;
      box-shadow: 0 40px 50px -20px #00c6ff30;
    }

    .project-card h3 {
      font-size: 1.4rem;
      margin-bottom: 0.7rem;
      color: #fff;
    }

    .project-card p {
      color: #9aa8b9;
      font-size: 0.95rem;
      line-height: 1.5;
      margin-bottom: 1.2rem;
      flex: 1;
    }

    .project-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
      margin-bottom: 1.4rem;
    }

    .project-tags span {
      background: #1e2530;
      border-radius: 40px;
      padding: 0.25rem 0.8rem;
      font-size: 0.7rem;
      font-weight: 600;
      color: #b0c4de;
      letter-spacing: 0.3px;
      border: 1px solid #2e3846;
    }

    .btn-view {
      background: transparent;
      border: 1.5px solid #00c6ff;
      color: #00c6ff;
      border-radius: 40px;
      padding: 0.5rem 1.2rem;
      font-weight: 600;
      font-size: 0.8rem;
      letter-spacing: 0.5px;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      transition: all 0.2s;
      align-self: flex-start;
    }

    .btn-view:hover {
      background: #00c6ff;
      color: #0a0c10;
      box-shadow: 0 0 20px #00c6ff;
      transform: translateZ(8px);
    }

    /* Github trophies / stats */
    .stats-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1.5rem;
      justify-content: center;
      margin: 1rem 0;
    }

    .stat-card {
      background: #0d1117;
      border-radius: 1.5rem;
      padding: 1.5rem 2rem;
      border: 1px solid #21262d;
      box-shadow: 0 30px 30px -20px black;
      text-align: center;
      flex: 1 1 180px;
    }

    .stat-card i {
      font-size: 2rem;
      color: #00c6ff;
      margin-bottom: 0.5rem;
    }

    /* road map */
    .roadmap {
      display: flex;
      flex-direction: column;
      align-items: center;
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.9rem;
      line-height: 1.6;
      background: #0b0f14;
      padding: 1.8rem;
      border-radius: 2rem;
      border: 1px solid #1e2530;
      color: #b0c4de;
    }

    /* mindset ascii */
    .mindset-pre {
      font-family: 'JetBrains Mono', monospace;
      white-space: pre;
      font-size: 0.75rem;
      line-height: 1.3;
      color: #7d8b9c;
      background: #0b0f14;
      padding: 1.5rem;
      border-radius: 1.8rem;
      overflow-x: auto;
      border: 1px solid #1e2530;
    }

    .mindset-pre .highlight {
      color: #00c6ff;
    }

    /* developer life */
    .dev-life {
      background: #0b0f14;
      padding: 1.8rem;
      border-radius: 1.8rem;
      border: 1px solid #1e2530;
      font-family: 'JetBrains Mono', monospace;
      color: #c9d1d9;
    }

    .dev-life pre {
      font-size: 0.9rem;
      line-height: 1.7;
    }

    /* Connect */
    .connect-buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      justify-content: center;
    }

    .connect-btn {
      background: #161b22;
      border: 1px solid #30363d;
      border-radius: 60px;
      padding: 0.8rem 2rem;
      font-weight: 600;
      color: #e5e9f0;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      gap: 0.8rem;
      transition: all 0.25s;
      box-shadow: 0 20px 20px -15px black;
    }

    .connect-btn i {
      font-size: 1.2rem;
      color: #00c6ff;
    }

    .connect-btn:hover {
      transform: translateY(-6px) translateZ(10px);
      border-color: #00c6ff;
      background: #1c2532;
      box-shadow: 0 30px 30px -15px #00c6ff40;
    }

    /* footer */
    .footer-note {
      text-align: center;
      color: #6e7681;
      font-size: 0.9rem;
      padding: 1.5rem 0 0.5rem;
      border-top: 1px solid #1e2530;
    }

    /* animations */
    @keyframes floatIn {
      0% { opacity: 0; transform: translateY(30px) rotateX(2deg); }
      100% { opacity: 1; transform: translateY(0) rotateX(0); }
    }

    @keyframes glitch {
      0% { text-shadow: 0 0 30px rgba(0, 198, 255, 0.3); }
      50% { text-shadow: 0 0 40px rgba(0, 198, 255, 0.6), 0 0 20px #0072ff; }
      100% { text-shadow: 0 0 30px rgba(0, 198, 255, 0.3); }
    }

    /* responsiveness */
    @media (max-width: 800px) {
      .grid-2, .grid-2-equal {
        grid-template-columns: 1fr;
      }
      .hero-3d h1 {
        font-size: 3rem;
      }
      .profile-container {
        gap: 1.5rem;
      }
      .card-3d {
        padding: 1.5rem;
      }
    }
  </style>
</head>
<body>
  <div class="profile-container">

    <!-- HERO 3D -->
    <div class="hero-3d">
      <h1>ANURAG RASTOGI</h1>
      <div class="subhead">Full Stack Developer · DSA Enthusiast</div>
      <div class="typing-demo">
        <span id="typing-text">B.Tech CSE Student 🎓</span>
      </div>
      <div style="margin-top: 1.8rem; display: flex; justify-content: center;">
        <div class="badge-3d"><i class="fas fa-eye"></i> PROFILE VIEWS 1.2K</div>
      </div>
    </div>

    <!-- ABOUT + GIF (3D card) -->
    <div class="card-3d">
      <div class="grid-2">
        <div>
          <h2><i class="fas fa-user-astronaut"></i> ABOUT ME</h2>
          <div class="mono" style="font-size: 0.95rem; line-height: 1.8; color: #b0c4de; white-space: pre-wrap;">
            ╭────────────────────────────────────────────╮<br>
            │  👋 Hi, I'm Anurag Rastogi                │<br>
            │  🎓 B.Tech CSE Student                    │<br>
            │  💻 Full Stack Developer                  │<br>
            │  🧠 DSA & Problem Solving Enthusiast       │<br>
            │  🚀 Building Real-World Applications       │<br>
            │  🌱 Currently Learning: Advanced DSA,      │<br>
            │     MERN Stack, Backend, System Design     │<br>
            │  ⚡ Goal: Become a Strong Software Engineer │<br>
            │  🔥 Philosophy: Learn → Build → Break → Fix │<br>
            ╰────────────────────────────────────────────╯
          </div>
        </div>
        <div style="text-align: center; transform: translateZ(15px);">
          <img src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif" alt="coding gif" style="max-width: 100%; border-radius: 1.5rem; box-shadow: 0 30px 30px -15px black; border: 1px solid #2d333b;">
        </div>
      </div>
    </div>

    <!-- TERMINAL SECTION -->
    <div class="card-3d">
      <h2><i class="fas fa-terminal"></i> DEVELOPER TERMINAL</h2>
      <div class="terminal-window">
        <div class="terminal-header">
          <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        </div>
        <div><span class="terminal-line">anurag@developer:~$</span> <span class="terminal-cmd">whoami</span></div>
        <div class="terminal-out">&gt; Full Stack Developer</div>
        <div class="terminal-out">&gt; C++ Problem Solver</div>
        <div class="terminal-out">&gt; DSA Enthusiast</div>
        <div class="terminal-out">&gt; Backend Developer</div>
        <br>
        <div><span class="terminal-line">anurag@developer:~$</span> <span class="terminal-cmd">skills</span></div>
        <div>C++        <span class="progress-bar"><span class="progress-fill" style="width:90%"></span></span> 90%</div>
        <div>JavaScript <span class="progress-bar"><span class="progress-fill" style="width:85%"></span></span> 85%</div>
        <div>React      <span class="progress-bar"><span class="progress-fill" style="width:80%"></span></span> 80%</div>
        <div>Node.js    <span class="progress-bar"><span class="progress-fill" style="width:80%"></span></span> 80%</div>
        <div>MongoDB    <span class="progress-bar"><span class="progress-fill" style="width:75%"></span></span> 75%</div>
        <br>
        <div><span class="terminal-line">anurag@developer:~$</span> <span class="terminal-cmd">./build_future.sh</span></div>
        <div>[████████████████████████████████] 100%</div>
        <div>✓ Learning &nbsp; ✓ Coding &nbsp; ✓ Building &nbsp; ✓ Solving</div>
        <div style="color:#00f7ff; margin-top: 6px;">STATUS: ONLINE 🚀</div>
      </div>
    </div>

    <!-- QUICK STATS BADGES -->
    <div class="card-3d">
      <h2><i class="fas fa-chart-simple"></i> QUICK STATS</h2>
      <div class="badge-group">
        <div class="badge-3d"><i class="fas fa-graduation-cap"></i> B.Tech CSE</div>
        <div class="badge-3d"><i class="fab fa-leetcode"></i> LeetCode 375+</div>
        <div class="badge-3d"><i class="fas fa-globe"></i> Full Stack Dev</div>
        <div class="badge-3d"><i class="fas fa-brain"></i> DSA Problem Solver</div>
      </div>
    </div>

    <!-- TECH STACK -->
    <div class="card-3d">
      <h2><i class="fas fa-code"></i> TECH STACK</h2>
      <div style="display: flex; flex-wrap: wrap; gap: 1.8rem; justify-content: space-between;">
        <div>
          <h3 style="color:#00c6ff; font-size: 1.1rem;">👨‍💻 Languages</h3>
          <div class="skill-icons">
            <div class="skill-icon-3d"><i class="fas fa-c"></i> C++</div>
            <div class="skill-icon-3d"><i class="fab fa-java"></i> Java</div>
            <div class="skill-icon-3d"><i class="fab fa-js"></i> JS</div>
            <div class="skill-icon-3d"><i class="fas fa-c"></i> C</div>
          </div>
        </div>
        <div>
          <h3 style="color:#00c6ff; font-size: 1.1rem;">🎨 Frontend</h3>
          <div class="skill-icons">
            <div class="skill-icon-3d"><i class="fab fa-html5"></i> HTML</div>
            <div class="skill-icon-3d"><i class="fab fa-css3-alt"></i> CSS</div>
            <div class="skill-icon-3d"><i class="fab fa-react"></i> React</div>
            <div class="skill-icon-3d"><i class="fas fa-wind"></i> Tailwind</div>
          </div>
        </div>
        <div>
          <h3 style="color:#00c6ff; font-size: 1.1rem;">⚙️ Backend & DB</h3>
          <div class="skill-icons">
            <div class="skill-icon-3d"><i class="fab fa-node"></i> Node</div>
            <div class="skill-icon-3d"><i class="fas fa-server"></i> Express</div>
            <div class="skill-icon-3d"><i class="fas fa-database"></i> MongoDB</div>
            <div class="skill-icon-3d"><i class="fas fa-database"></i> MySQL</div>
          </div>
        </div>
      </div>
    </div>

    <!-- DSA PROGRESS -->
    <div class="card-3d">
      <h2><i class="fas fa-puzzle-piece"></i> DSA & PROBLEM SOLVING</h2>
      <div class="badge-group" style="margin-bottom: 1.8rem;">
        <div class="badge-3d"><i class="fab fa-leetcode"></i> LeetCode 375+</div>
        <div class="badge-3d"><i class="fas fa-code"></i> GFG 100+</div>
      </div>
      <div class="grid-2-equal">
        <div class="dsa-item"><span>Arrays</span><div class="dsa-bar"><div class="dsa-fill" style="width:100%"></div></div></div>
        <div class="dsa-item"><span>Strings</span><div class="dsa-bar"><div class="dsa-fill" style="width:95%"></div></div></div>
        <div class="dsa-item"><span>Two Pointers</span><div class="dsa-bar"><div class="dsa-fill" style="width:100%"></div></div></div>
        <div class="dsa-item"><span>Sliding Window</span><div class="dsa-bar"><div class="dsa-fill" style="width:90%"></div></div></div>
        <div class="dsa-item"><span>Binary Search</span><div class="dsa-bar"><div class="dsa-fill" style="width:100%"></div></div></div>
        <div class="dsa-item"><span>Recursion</span><div class="dsa-bar"><div class="dsa-fill" style="width:90%"></div></div></div>
        <div class="dsa-item"><span>Linked List</span><div class="dsa-bar"><div class="dsa-fill" style="width:90%"></div></div></div>
        <div class="dsa-item"><span>Stack & Queue</span><div class="dsa-bar"><div class="dsa-fill" style="width:95%"></div></div></div>
        <div class="dsa-item"><span>Trees</span><div class="dsa-bar"><div class="dsa-fill" style="width:85%"></div></div></div>
        <div class="dsa-item"><span>BST</span><div class="dsa-bar"><div class="dsa-fill" style="width:85%"></div></div></div>
        <div class="dsa-item"><span>Graphs</span><div class="dsa-bar"><div class="dsa-fill" style="width:75%"></div></div></div>
        <div class="dsa-item"><span>Greedy</span><div class="dsa-bar"><div class="dsa-fill" style="width:60%"></div></div></div>
        <div class="dsa-item"><span>DP</span><div class="dsa-bar"><div class="dsa-fill" style="width:75%"></div></div></div>
      </div>
      <div style="text-align: center; margin-top: 1.5rem; font-size: 0.9rem; color: #00c6ff;">💡 Understand → Analyze → Code → Optimize → Repeat</div>
    </div>

    <!-- FEATURED PROJECTS -->
    <div class="card-3d">
      <h2><i class="fas fa-rocket"></i> FEATURED PROJECTS</h2>
      <div class="grid-2-equal">
        <div class="project-card">
          <h3>💻 Coding Platform</h3>
          <p>Online coding platform for solving programming problems and practicing DSA.</p>
          <div class="project-tags"><span>Node.js</span><span>Express</span><span>MongoDB</span><span>Socket.io</span></div>
          <a href="#" class="btn-view"><i class="fab fa-github"></i> VIEW PROJECT</a>
        </div>
        <div class="project-card">
          <h3>💰 Money Spending App</h3>
          <p>Expense tracking and budget management application with data visualization.</p>
          <div class="project-tags"><span>React</span><span>Node.js</span><span>MongoDB</span></div>
          <a href="#" class="btn-view"><i class="fab fa-github"></i> VIEW PROJECT</a>
        </div>
        <div class="project-card">
          <h3>🌐 Developer Portfolio</h3>
          <p>Modern personal portfolio showcasing skills, projects and development journey.</p>
          <div class="project-tags"><span>React</span><span>Tailwind</span></div>
          <a href="#" class="btn-view"><i class="fab fa-github"></i> VIEW PROJECT</a>
        </div>
        <div class="project-card">
          <h3>📝 Coding Notes App</h3>
          <p>Developer-focused platform for creating and organizing programming notes.</p>
          <div class="project-tags"><span>JavaScript</span><span>Node.js</span></div>
          <a href="#" class="btn-view"><i class="fab fa-github"></i> VIEW PROJECT</a>
        </div>
      </div>
    </div>

    <!-- TROPHIES & STATS -->
    <div class="card-3d">
      <h2><i class="fas fa-trophy"></i> GITHUB TROPHIES & ANALYTICS</h2>
      <div class="stats-grid">
        <div class="stat-card"><i class="fas fa-trophy"></i><div style="font-weight:700;">Trophy</div><div style="color:#8b949e;">Algolia</div></div>
        <div class="stat-card"><i class="fas fa-chart-line"></i><div style="font-weight:700;">1.2k commits</div><div style="color:#8b949e;">last year</div></div>
        <div class="stat-card"><i class="fas fa-code-branch"></i><div style="font-weight:700;">15+ repos</div><div style="color:#8b949e;">public</div></div>
      </div>
      <div style="background:#0b0f14; border-radius:1.5rem; padding:1.5rem; margin-top:0.8rem; text-align:center; border:1px solid #1e2530;">
        <span style="color:#00c6ff;">🔥 CONTRIBUTION ACTIVITY</span>
        <div style="height: 60px; display: flex; align-items: center; justify-content: center; color:#3a4a5a; font-size:0.9rem; border:1px dashed #2d333b; border-radius: 12px; margin-top: 0.8rem;">[ contribution graph placeholder – active streak ]</div>
      </div>
    </div>

    <!-- CURRENTLY LEARNING / ROADMAP -->
    <div class="card-3d">
      <h2><i class="fas fa-seedling"></i> CURRENTLY LEARNING</h2>
      <div class="roadmap">
        🚀 MY DEVELOPER JOURNEY<br>
        │<br>
        ├── 🧠 DSA (DP, Graph, Greedy)<br>
        ├── 🌐 MERN (React, Node, Mongo)<br>
        ├── ⚙️ BACKEND (REST, Auth, Security)<br>
        └── 🏗️ SYSTEM DESIGN → 💼 SOFTWARE ENGINEER
      </div>
    </div>

    <!-- MINDSET -->
    <div class="card-3d">
      <h2><i class="fas fa-cogs"></i> DEVELOPER MINDSET</h2>
      <div class="mindset-pre">
        ╔══════════════════════════════════════════════╗<br>
        ║                  PROBLEM                     ║<br>
        ║                     │                        ║<br>
        ║                     ▼                        ║<br>
        ║                  ANALYZE                     ║<br>
        ║                     │                        ║<br>
        ║                     ▼                        ║<br>
        ║                   DESIGN                     ║<br>
        ║                     │                        ║<br>
        ║                     ▼                        ║<br>
        ║                    CODE                      ║<br>
        ║                     │                        ║<br>
        ║                     ▼                        ║<br>
        ║                    TEST                      ║<br>
        ║                     │                        ║<br>
        ║                     ▼                        ║<br>
        ║                   DEBUG                      ║<br>
        ║                     │                        ║<br>
        ║                     ▼                        ║<br>
        ║                  OPTIMIZE                    ║<br>
        ║                     │                        ║<br>
        ║                     ▼                        ║<br>
        ║                   DEPLOY                     ║<br>
        ║                     │                        ║<br>
        ║                     ▼                        ║<br>
        ║                  REPEAT 🔥                   ║<br>
        ╚══════════════════════════════════════════════╝
      </div>
    </div>

    <!-- DEVELOPER LIFE -->
    <div class="card-3d">
      <h2><i class="fas fa-mug-hot"></i> DEVELOPER LIFE</h2>
      <div class="dev-life">
        <pre>
while(alive) {
    learn();
    code();
    solveProblems();
    buildProjects();
    if (bug) {
        debug();
        learn();
    }
    drinkCoffee();
}</pre>
        <div style="display:flex; gap: 1rem; margin-top: 1rem; flex-wrap: wrap;">
          <span class="badge-3d"><i class="fas fa-coffee"></i> COFFEE ∞</span>
          <span class="badge-3d"><i class="fas fa-bug"></i> BUGS FIXED EVENTUALLY</span>
          <span class="badge-3d"><i class="fas fa-code"></i> CODE ALWAYS</span>
        </div>
      </div>
    </div>

    <!-- CONNECT -->
    <div class="card-3d" style="text-align: center;">
      <h2 style="justify-content: center;"><i class="fas fa-globe"></i> LET'S CONNECT</h2>
      <div class="connect-buttons">
        <a href="#" class="connect-btn"><i class="fab fa-github"></i> GitHub</a>
        <a href="#" class="connect-btn"><i class="fab fa-linkedin-in"></i> LinkedIn</a>
        <a href="#" class="connect-btn"><i class="fas fa-envelope"></i> Email</a>
        <a href="#" class="connect-btn"><i class="fab fa-instagram"></i> Instagram</a>
      </div>
      <div style="margin-top: 2rem; color: #8b949e;">
        <h3 style="color: #00c6ff;">💙 Thanks for visiting!</h3>
        <p style="font-weight: 300;">Code. Learn. Build. Solve. Repeat. 🚀</p>
      </div>
    </div>

    <!-- FOOTER -->
    <div class="footer-note">
      <i class="fas fa-crown" style="color: #00c6ff;"></i> Anurag Rastogi · 3D profile · Always building
    </div>
  </div>

  <script>
    // typing animation
    const textElement = document.getElementById('typing-text');
    const phrases = [
      'B.Tech CSE Student 🎓',
      'Full Stack Developer 💻',
      'DSA | CP Enthusiast 🧠',
      'Building Real-World Apps 🚀',
      '375+ LeetCode Problems ⚡',
      'Learning | Building | Growing'
    ];
    let idx = 0;
    let charIdx = 0;
    let isDeleting = false;
    let currentText = '';

    function type() {
      const fullText = phrases[idx];
      if (isDeleting) {
        currentText = fullText.substring(0, charIdx - 1);
        charIdx--;
      } else {
        currentText = fullText.substring(0, charIdx + 1);
        charIdx++;
      }

      textElement.textContent = currentText;

      if (!isDeleting && charIdx === fullText.length) {
        isDeleting = true;
        setTimeout(type, 1800);
      } else if (isDeleting && charIdx === 0) {
        isDeleting = false;
        idx = (idx + 1) % phrases.length;
        setTimeout(type, 200);
      } else {
        const speed = isDeleting ? 40 : 80;
        setTimeout(type, speed);
      }
    }

    // start typing
    setTimeout(type, 400);

    // subtle parallax on cards
    const cards = document.querySelectorAll('.card-3d, .terminal-window, .project-card');
    document.addEventListener('mousemove', (e) => {
      const x = (e.clientX / window.innerWidth - 0.5) * 2;
      const y = (e.clientY / window.innerHeight - 0.5) * 2;
      cards.forEach(card => {
        if (card.closest('.profile-container')) {
          card.style.transform = `rotateY(${x * 0.5}deg) rotateX(${-y * 0.5}deg) translateZ(0)`;
        }
      });
    });

    // reset transform on mouse leave
    document.addEventListener('mouseleave', () => {
      cards.forEach(card => {
        card.style.transform = 'rotateY(0deg) rotateX(0deg)';
      });
    });
  </script>
</body>
</html>
