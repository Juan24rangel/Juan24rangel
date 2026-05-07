<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>GitHub Profile README</title>
  <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Fira+Code:wght@300;400;600&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --royal-blue: #1a3cff;
      --blue-dark: #0d1f8c;
      --blue-mid: #2855e0;
      --purple: #7c3aed;
      --purple-light: #a855f7;
      --purple-glow: #c084fc;
      --bg: #06050f;
      --bg2: #0d0b1e;
      --card-bg: rgba(26, 60, 255, 0.07);
      --border: rgba(124, 58, 237, 0.35);
      --text: #e2e0ff;
      --text-muted: #8b87c8;
      --glow-blue: 0 0 20px rgba(26, 60, 255, 0.55);
      --glow-purple: 0 0 20px rgba(168, 85, 247, 0.55);
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Fira Code', monospace;
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* ── Scanline overlay ── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background: repeating-linear-gradient(
        0deg,
        transparent,
        transparent 2px,
        rgba(26, 60, 255, 0.025) 2px,
        rgba(26, 60, 255, 0.025) 4px
      );
      pointer-events: none;
      z-index: 999;
    }

    /* ── Starfield canvas ── */
    #stars {
      position: fixed;
      inset: 0;
      z-index: 0;
    }

    .wrapper {
      position: relative;
      z-index: 1;
      max-width: 860px;
      margin: 0 auto;
      padding: 40px 24px 60px;
      display: flex;
      flex-direction: column;
      gap: 36px;
    }

    /* ══════════════ HEADER ══════════════ */
    .header {
      text-align: center;
      position: relative;
    }

    .header .pixel-title {
      font-family: 'Press Start 2P', monospace;
      font-size: clamp(14px, 3vw, 22px);
      background: linear-gradient(90deg, var(--royal-blue), var(--purple-light), var(--royal-blue));
      background-size: 200% auto;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      animation: shimmer 3s linear infinite;
      line-height: 1.7;
      letter-spacing: 2px;
    }

    @keyframes shimmer {
      to { background-position: 200% center; }
    }

    .header .typing-wrap {
      margin-top: 18px;
      font-size: 14px;
      color: var(--purple-glow);
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 6px;
    }

    .cursor {
      display: inline-block;
      width: 10px;
      height: 18px;
      background: var(--purple-light);
      animation: blink .7s steps(1) infinite;
    }
    @keyframes blink { 50% { opacity: 0; } }

    .header .badge-row {
      margin-top: 20px;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
    }

    .badge {
      padding: 5px 14px;
      border-radius: 4px;
      font-size: 11px;
      font-family: 'Press Start 2P', monospace;
      border: 1px solid var(--border);
      background: var(--card-bg);
      color: var(--purple-light);
      box-shadow: var(--glow-purple);
      letter-spacing: 1px;
    }

    .avatar-ring {
      width: 130px;
      height: 130px;
      border-radius: 50%;
      margin: 0 auto 18px;
      padding: 3px;
      background: linear-gradient(135deg, var(--royal-blue), var(--purple));
      box-shadow: var(--glow-blue), var(--glow-purple);
      animation: rotatering 4s linear infinite;
    }
    @keyframes rotatering {
      to { filter: hue-rotate(360deg); }
    }
    .avatar-ring img {
      width: 100%;
      height: 100%;
      border-radius: 50%;
      object-fit: cover;
      border: 3px solid var(--bg);
    }

    /* ══════════════ CARD ══════════════ */
    .card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 28px 32px;
      backdrop-filter: blur(4px);
      position: relative;
      overflow: hidden;
      transition: box-shadow .3s;
    }
    .card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--royal-blue), var(--purple-light));
    }
    .card:hover {
      box-shadow: var(--glow-blue);
    }

    .card-title {
      font-family: 'Press Start 2P', monospace;
      font-size: 11px;
      color: var(--purple-light);
      letter-spacing: 2px;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .card-title::after {
      content: '';
      flex: 1;
      height: 1px;
      background: linear-gradient(90deg, var(--border), transparent);
    }

    /* ══════════════ ABOUT ══════════════ */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 14px;
    }

    .about-item {
      display: flex;
      align-items: flex-start;
      gap: 10px;
      font-size: 13px;
      color: var(--text);
      line-height: 1.6;
    }
    .about-item .icon { font-size: 18px; flex-shrink: 0; }

    /* ══════════════ GIF GRID ══════════════ */
    .gif-banner {
      display: flex;
      justify-content: center;
      gap: 16px;
      flex-wrap: wrap;
    }
    .gif-item {
      border: 1px solid var(--border);
      border-radius: 10px;
      overflow: hidden;
      box-shadow: var(--glow-purple);
      transition: transform .3s, box-shadow .3s;
    }
    .gif-item:hover {
      transform: translateY(-4px) scale(1.03);
      box-shadow: 0 0 30px rgba(168, 85, 247, 0.7);
    }
    .gif-item img { display: block; height: 120px; width: auto; }

    /* ══════════════ TECH STACK ══════════════ */
    .tech-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }
    .tech-pill {
      display: flex;
      align-items: center;
      gap: 7px;
      padding: 7px 14px;
      border-radius: 6px;
      border: 1px solid var(--border);
      background: rgba(124, 58, 237, 0.1);
      font-size: 12px;
      color: var(--text);
      transition: all .25s;
      cursor: default;
    }
    .tech-pill:hover {
      background: rgba(26, 60, 255, 0.25);
      border-color: var(--royal-blue);
      box-shadow: var(--glow-blue);
      color: #fff;
      transform: translateY(-2px);
    }
    .tech-pill img { width: 18px; height: 18px; object-fit: contain; }

    /* ══════════════ STATS ══════════════ */
    .stats-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }
    .stats-grid img {
      width: 100%;
      border-radius: 8px;
      border: 1px solid var(--border);
    }

    /* ══════════════ SOCIAL LINKS ══════════════ */
    .social-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
      gap: 14px;
    }
    .social-card {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      padding: 20px 14px;
      border-radius: 10px;
      border: 1px solid var(--border);
      background: rgba(26, 60, 255, 0.06);
      text-decoration: none;
      color: var(--text);
      transition: all .3s;
      cursor: pointer;
    }
    .social-card:hover {
      background: rgba(124, 58, 237, 0.2);
      border-color: var(--purple-light);
      box-shadow: var(--glow-purple);
      transform: translateY(-4px);
    }
    .social-card img {
      width: 44px;
      height: 44px;
      object-fit: contain;
      filter: drop-shadow(0 0 6px rgba(168, 85, 247, 0.6));
    }
    .social-card .s-name {
      font-family: 'Press Start 2P', monospace;
      font-size: 8px;
      color: var(--purple-light);
      letter-spacing: 1px;
    }
    .social-card .s-handle {
      font-size: 11px;
      color: var(--text-muted);
    }

    /* ══════════════ STREAK / CONTRIBUTION ══════════════ */
    .streak-wrap {
      display: flex;
      justify-content: center;
    }
    .streak-wrap img {
      width: 100%;
      max-width: 560px;
      border-radius: 10px;
      border: 1px solid var(--border);
    }

    /* ══════════════ DINO FOOTER ══════════════ */
    .dino-section {
      text-align: center;
      padding: 20px 0 10px;
    }
    .dino-title {
      font-family: 'Press Start 2P', monospace;
      font-size: 9px;
      color: var(--text-muted);
      letter-spacing: 2px;
      margin-bottom: 16px;
      animation: flicker 4s infinite;
    }
    @keyframes flicker {
      0%,100%{opacity:1} 92%{opacity:1} 93%{opacity:.4} 94%{opacity:1} 96%{opacity:.4} 97%{opacity:1}
    }
    .dino-wrap {
      display: inline-block;
      border: 2px solid var(--border);
      border-radius: 12px;
      padding: 20px 32px;
      background: var(--card-bg);
      box-shadow: var(--glow-blue), var(--glow-purple);
      position: relative;
    }
    .dino-wrap::before {
      content: 'NO HAY INTERNET';
      position: absolute;
      top: -12px;
      left: 50%;
      transform: translateX(-50%);
      background: var(--bg);
      padding: 0 12px;
      font-family: 'Press Start 2P', monospace;
      font-size: 8px;
      color: var(--royal-blue);
      white-space: nowrap;
    }
    .dino-wrap img {
      height: 100px;
      image-rendering: pixelated;
      filter: drop-shadow(0 0 8px rgba(26,60,255,0.5));
    }
    .dino-sub {
      margin-top: 14px;
      font-size: 11px;
      color: var(--text-muted);
    }
    .dino-sub span {
      color: var(--purple-light);
    }

    /* ══════════════ PROGRESS BARS ══════════════ */
    .skill-bar { margin-bottom: 14px; }
    .skill-label {
      display: flex;
      justify-content: space-between;
      font-size: 12px;
      margin-bottom: 5px;
      color: var(--text-muted);
    }
    .bar-bg {
      height: 8px;
      background: rgba(255,255,255,0.07);
      border-radius: 4px;
      overflow: hidden;
    }
    .bar-fill {
      height: 100%;
      border-radius: 4px;
      background: linear-gradient(90deg, var(--royal-blue), var(--purple-light));
      box-shadow: 0 0 8px rgba(168,85,247,0.5);
      animation: growbar 1.5s cubic-bezier(.4,0,.2,1) both;
      transform-origin: left;
    }
    @keyframes growbar {
      from { transform: scaleX(0); }
      to   { transform: scaleX(1); }
    }

    /* ══════════════ SNAKE / CONTRIBUTION ANIMATION ══════════════ */
    .snake-note {
      font-size: 11px;
      color: var(--text-muted);
      text-align: center;
      margin-top: 10px;
    }

    @media (max-width: 560px) {
      .about-grid, .stats-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

<canvas id="stars"></canvas>

<div class="wrapper">

  <!-- ── HEADER ── -->
  <div class="header">
    <div class="avatar-ring">
      <img src="https://avatars.githubusercontent.com/u/9919?v=4" alt="Avatar"
           onerror="this.src='https://github.com/identicons/juan.png'"/>
    </div>

    <div class="pixel-title">
      &lt; JUAN DEV /&gt;
    </div>

    <div class="typing-wrap">
      <span id="typed"></span><span class="cursor"></span>
    </div>

    <div class="badge-row">
      <span class="badge">💻 FULLSTACK</span>
      <span class="badge">🎮 GAMER</span>
      <span class="badge">🚀 OPEN SOURCE</span>
    </div>
  </div>

  <!-- ── GIF BANNER ── -->
  <div class="gif-banner">
    <div class="gif-item">
      <img src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif" alt="Coding GIF"/>
    </div>
    <div class="gif-item">
      <img src="https://media.giphy.com/media/f3iwJFOVOwuy7K6FFw/giphy.gif" alt="Matrix GIF"/>
    </div>
    <div class="gif-item">
      <img src="https://media.giphy.com/media/LmNwrBhejkK9EFP504/giphy.gif" alt="Pixel GIF"/>
    </div>
  </div>

  <!-- ── ABOUT ME ── -->
  <div class="card">
    <div class="card-title">👾 SOBRE MÍ</div>
    <div class="about-grid">
      <div class="about-item"><span class="icon">🌎</span><span>Colombia, Bucaramanga</span></div>
      <div class="about-item"><span class="icon">🎓</span><span>Estudiante de Ingeniería</span></div>
      <div class="about-item"><span class="icon">⚡</span><span>Apasionado por el código limpio</span></div>
      <div class="about-item"><span class="icon">🎮</span><span>Gamer &amp; dev de tiempo completo</span></div>
      <div class="about-item"><span class="icon">🔭</span><span>Explorando IA y sistemas</span></div>
      <div class="about-item"><span class="icon">🌱</span><span>Aprendiendo cada día algo nuevo</span></div>
    </div>
  </div>

  <!-- ── TECH STACK ── -->
  <div class="card">
    <div class="card-title">🛠 TECH STACK</div>
    <div class="tech-grid">
      <div class="tech-pill">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python"/> Python
      </div>
      <div class="tech-pill">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt="JS"/> JavaScript
      </div>
      <div class="tech-pill">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="React"/> React
      </div>
      <div class="tech-pill">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" alt="Node"/> Node.js
      </div>
      <div class="tech-pill">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git"/> Git
      </div>
      <div class="tech-pill">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" alt="Docker"/> Docker
      </div>
      <div class="tech-pill">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" alt="Linux"/> Linux
      </div>
      <div class="tech-pill">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" alt="SQL"/> MySQL
      </div>
    </div>
  </div>

  <!-- ── SKILL LEVEL BARS ── -->
  <div class="card">
    <div class="card-title">📊 NIVEL DE HABILIDADES</div>
    <div class="skill-bar">
      <div class="skill-label"><span>🐍 Python</span><span>88%</span></div>
      <div class="bar-bg"><div class="bar-fill" style="width:88%"></div></div>
    </div>
    <div class="skill-bar">
      <div class="skill-label"><span>⚡ JavaScript</span><span>80%</span></div>
      <div class="bar-bg"><div class="bar-fill" style="width:80%"></div></div>
    </div>
    <div class="skill-bar">
      <div class="skill-label"><span>⚛️ React</span><span>72%</span></div>
      <div class="bar-bg"><div class="bar-fill" style="width:72%"></div></div>
    </div>
    <div class="skill-bar">
      <div class="skill-label"><span>🐋 Docker</span><span>65%</span></div>
      <div class="bar-bg"><div class="bar-fill" style="width:65%"></div></div>
    </div>
    <div class="skill-bar">
      <div class="skill-label"><span>🗄️ SQL</span><span>75%</span></div>
      <div class="bar-bg"><div class="bar-fill" style="width:75%"></div></div>
    </div>
  </div>

  <!-- ── GITHUB STATS ── -->
  <div class="card">
    <div class="card-title">📈 GITHUB STATS</div>
    <div class="stats-grid">
      <img src="https://github-readme-stats.vercel.app/api?username=TU_USUARIO&show_icons=true&theme=tokyonight&border_color=7c3aed&bg_color=06050f&title_color=a855f7&text_color=e2e0ff&icon_color=1a3cff&hide_border=false"
           alt="GitHub Stats" onerror="this.style.display='none'"/>
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=TU_USUARIO&layout=compact&theme=tokyonight&border_color=7c3aed&bg_color=06050f&title_color=a855f7&text_color=e2e0ff&hide_border=false"
           alt="Top Languages" onerror="this.style.display='none'"/>
    </div>
    <div class="streak-wrap" style="margin-top:16px">
      <img src="https://streak-stats.demolab.com?user=TU_USUARIO&theme=tokyonight&border=7c3aed&background=06050f&ring=a855f7&fire=1a3cff&currStreakLabel=a855f7"
           alt="Streak" onerror="this.style.display='none'"/>
    </div>
    <p class="snake-note">⚠️ Reemplaza <strong style="color:var(--purple-light)">TU_USUARIO</strong> con tu nombre de GitHub</p>
  </div>

  <!-- ── SOCIAL LINKS ── -->
  <div class="card">
    <div class="card-title">🌐 REDES SOCIALES</div>
    <div class="social-grid">

      <a class="social-card" href="https://github.com/TU_USUARIO" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="GitHub"/>
        <span class="s-name">GITHUB</span>
        <span class="s-handle">@TU_USUARIO</span>
      </a>

      <a class="social-card" href="https://linkedin.com/in/TU_PERFIL" target="_blank">
        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" alt="LinkedIn"/>
        <span class="s-name">LINKEDIN</span>
        <span class="s-handle">/in/tu-perfil</span>
      </a>

      <a class="social-card" href="https://twitter.com/TU_USUARIO" target="_blank">
        <img src="https://abs.twimg.com/icons/apple-touch-icon-192x192.png" alt="Twitter/X"
             style="border-radius:8px"/>
        <span class="s-name">TWITTER/X</span>
        <span class="s-handle">@TU_USUARIO</span>
      </a>

      <a class="social-card" href="https://instagram.com/TU_USUARIO" target="_blank">
        <img src="https://upload.wikimedia.org/wikipedia/commons/a/a5/Instagram_icon.png" alt="Instagram"/>
        <span class="s-name">INSTAGRAM</span>
        <span class="s-handle">@TU_USUARIO</span>
      </a>

      <a class="social-card" href="mailto:tuemail@gmail.com">
        <img src="https://upload.wikimedia.org/wikipedia/commons/7/7e/Gmail_icon_%282020%29.svg" alt="Email"/>
        <span class="s-name">EMAIL</span>
        <span class="s-handle">tuemail@gmail.com</span>
      </a>

      <a class="social-card" href="https://discord.com/users/TU_ID" target="_blank">
        <img src="https://assets-global.website-files.com/6257adef93867e50d84d30e2/636e0a6a49cf127bf92de1e2_icon_clyde_blurple_RGB.png"
             alt="Discord"/>
        <span class="s-name">DISCORD</span>
        <span class="s-handle">tu_usuario#0000</span>
      </a>

    </div>
  </div>

  <!-- ── DINOSAURIO FOOTER ── -->
  <div class="dino-section">
    <div class="dino-title">... cuando el WiFi se va ...</div>
    <div class="dino-wrap">
      <img src="https://media.giphy.com/media/3o7TKQna2enkznCKis/giphy.gif" alt="Dino GIF"
           onerror="this.src='https://media.giphy.com/media/26tn33aiTi1jkl6H6/giphy.gif'"/>
    </div>
    <div class="dino-sub">
      <span>ERROR 404</span> · No-Internet Mode Activated · <span>Ctrl+R para reintentar</span>
    </div>
  </div>

</div><!-- /wrapper -->

<!-- ── STARFIELD ── -->
<script>
  const canvas = document.getElementById('stars');
  const ctx = canvas.getContext('2d');
  let stars = [];

  function resize() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  }
  resize();
  window.addEventListener('resize', resize);

  for (let i = 0; i < 160; i++) {
    stars.push({
      x: Math.random() * window.innerWidth,
      y: Math.random() * window.innerHeight,
      r: Math.random() * 1.4 + 0.2,
      speed: Math.random() * 0.3 + 0.05,
      alpha: Math.random()
    });
  }

  function drawStars() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    stars.forEach(s => {
      s.alpha += (Math.random() - 0.5) * 0.04;
      s.alpha = Math.max(0.05, Math.min(1, s.alpha));
      s.y += s.speed;
      if (s.y > canvas.height) { s.y = 0; s.x = Math.random() * canvas.width; }
      ctx.beginPath();
      ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
      const hue = Math.random() > 0.5 ? '220' : '270';
      ctx.fillStyle = `hsla(${hue}, 90%, 75%, ${s.alpha})`;
      ctx.fill();
    });
    requestAnimationFrame(drawStars);
  }
  drawStars();

  // ── Typing effect ──
  const phrases = [
    '> Compilando sueños en código...',
    '> git commit -m "otro día épico"',
    '> while(alive) { learn(); build(); }',
    '> Nivel: Caffeinated Developer ☕',
    '> console.log("Hola, mundo! 🌎");'
  ];
  let pi = 0, ci = 0, deleting = false;
  const el = document.getElementById('typed');
  function type() {
    const phrase = phrases[pi];
    if (!deleting) {
      el.textContent = phrase.slice(0, ++ci);
      if (ci === phrase.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      el.textContent = phrase.slice(0, --ci);
      if (ci === 0) { deleting = false; pi = (pi + 1) % phrases.length; }
    }
    setTimeout(type, deleting ? 40 : 65);
  }
  type();
</script>

</body>
</html>
