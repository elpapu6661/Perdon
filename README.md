<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Te Amo Daniela 💕</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet">
  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      width: 100%;
      background: radial-gradient(ellipse at bottom, #0b0d1a 0%, #060712 100%);
      overflow: hidden;
      font-family: 'Great Vibes', cursive;
    }

    /* Fondo estrellado animado */
    .stars {
      position: absolute;
      width: 100%;
      height: 100%;
      background: transparent;
      z-index: 0;
    }

    .star {
      position: absolute;
      width: 2px;
      height: 2px;
      background: white;
      border-radius: 50%;
      opacity: 0.6;
      animation: twinkle 2s infinite ease-in-out;
    }

    @keyframes twinkle {
      0%, 100% { opacity: 0.2; transform: scale(1); }
      50% { opacity: 1; transform: scale(1.3); }
    }

    .calla {
      position: absolute;
      width: 120px;
      height: 220px;
      transform-origin: bottom center;
      opacity: 0;
      animation: bloom 1.2s ease-out forwards, breeze 6s ease-in-out infinite alternate;
      z-index: 1;
    }

    @keyframes bloom {
      from {
        transform: scale(0.2) translateY(100px) rotate(var(--rot));
        opacity: 0;
      }
      to {
        transform: scale(1) translateY(0) rotate(var(--rot));
        opacity: 1;
      }
    }

    @keyframes breeze {
      0% { transform: translateX(0) rotate(var(--rot)); }
      50% { transform: translateX(5px) rotate(calc(var(--rot) + 2deg)); }
      100% { transform: translateX(-5px) rotate(calc(var(--rot) - 2deg)); }
    }

    .message {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 42px;
      color: #ffcce0;
      text-shadow: 0 0 6px #ffb3d9;
      z-index: 2;
      white-space: nowrap;
    }
  </style>
</head>
<body>

  <!-- Estrellas irregulares -->
  <div class="stars" id="stars"></div>

  <!-- Mensaje romántico y poético -->
  <div class="message">Te amo mucho mi reina 💕</div>

  <script>
    const body = document.body;
    const starsContainer = document.getElementById("stars");

    // Crear estrellas con posiciones aleatorias y velocidades de parpadeo distintas
    for (let i = 0; i < 150; i++) {
      const star = document.createElement('div');
      star.className = 'star';
      star.style.top = Math.random() * 100 + 'vh';
      star.style.left = Math.random() * 100 + 'vw';
      star.style.animationDuration = (Math.random() * 2 + 1.5) + 's';
      starsContainer.appendChild(star);
    }

    // Crear calas con hojas
    const total = 80;
    for (let i = 0; i < total; i++) {
      const calla = document.createElement('div');
      calla.className = 'calla';

      const x = Math.random() * 100;
      const y = Math.random() * 90 + 5;
      const rot = (Math.random() - 0.5) * 20 + 'deg';
      const delay = (i * 0.2).toFixed(2) + 's';

      calla.style.left = x + 'vw';
      calla.style.top = y + 'vh';
      calla.style.setProperty('--rot', rot);
      calla.style.animationDelay = delay;

      calla.innerHTML = `
<svg viewBox="0 0 120 220" width="120" height="220">
  <defs>
    <linearGradient id="stemGrad" x1="0" y1="0" x2="0" y2="1">
      <stop offset="0%" stop-color="#2f5d2f"/>
      <stop offset="100%" stop-color="#4aae4a"/>
    </linearGradient>
    <radialGradient id="petalGrad" cx="0.4" cy="0.3" r="0.6">
      <stop offset="0%" stop-color="#ffffff"/>
      <stop offset="100%" stop-color="#dedede"/>
    </radialGradient>
    <radialGradient id="leafGrad" cx="0.5" cy="0.5" r="0.7">
      <stop offset="0%" stop-color="#55aa55"/>
      <stop offset="100%" stop-color="#225522"/>
    </radialGradient>
  </defs>

  <!-- Hoja izquierda -->
  <path d="M60,200 C30,180 30,160 60,170" fill="url(#leafGrad)" opacity="0.9"/>
  <!-- Hoja derecha -->
  <path d="M60,200 C90,180 90,160 60,170" fill="url(#leafGrad)" opacity="0.9"/>

  <!-- Tallo -->
  <path d="M60,220 C56,150 58,140 60,80" stroke="url(#stemGrad)" stroke-width="8" fill="none" stroke-linecap="round"/>

  <!-- Espádice -->
  <ellipse cx="60" cy="70" rx="6" ry="50" fill="gold" />

  <!-- Pétalo -->
  <path d="M60,80 C90,20 80,0 60,20 C40,0 30,20 60,80 Z" fill="url(#petalGrad)" stroke="#ddd" stroke-width="1"/>
  <path d="M60,80 C75,40 65,30 60,40 C55,30 45,40 60,80 Z" fill="rgba(200,200,200,0.3)"/>
</svg>
      `;
      body.appendChild(calla);
    }
  </script>

</body>
</html>
