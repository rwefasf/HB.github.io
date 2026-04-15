<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, maximum-scale=1.0">
  <title>🎨 Приглашение · Дарья</title>
  <style>
    /* ============================================
       АДАПТИВНАЯ ТИПОГРАФИКА + АНИМАЦИЯ ВСЕГО КОНВЕРТА
       ============================================ */
    :root {
      --bg-dark: #140202;
      --bg-card: #240606;
      --primary: #a32222;
      --primary-glow: #d44;
      --accent: #e6b800;
      --gold: #d4af37;
      --text-light: #ffe1e1;
      --text-dim: #c8a0a0;
      --shadow-heavy: 0 20px 30px rgba(0,0,0,0.8), 0 0 0 1px #5a1a1a inset;
      --border-glow: 0 0 15px #b33;
    }

    * { 
      margin: 0; 
      padding: 0; 
      box-sizing: border-box; 
    }

    body {
      min-height: 100vh;
      background: radial-gradient(circle at 20% 30%, #2c0a0a, #0a0101);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'Palatino', 'Palatino Linotype', 'Georgia', serif;
      padding: 12px;
    }

    /* Анимации */
    @keyframes floatGlow {
      0% { filter: drop-shadow(0 0 5px #a11); }
      50% { filter: drop-shadow(0 0 20px #f44); }
      100% { filter: drop-shadow(0 0 5px #a11); }
    }

    @keyframes cardReveal {
      0% { 
        opacity: 0; 
        transform: scale(0.7) rotate(-2deg); 
        filter: blur(8px); 
      }
      100% { 
        opacity: 1; 
        transform: scale(1) rotate(0deg); 
        filter: blur(0); 
      }
    }

    @keyframes stampPulse {
      0%,100% { transform: rotate(4deg) scale(1); }
      50% { transform: rotate(6deg) scale(1.02); }
    }

    /* Анимация всего конверта при открытии */
    @keyframes envelopeOpen {
      0% { 
        transform: scale(1) translateY(0);
        box-shadow: inset 0 -10px 0 #3c0808, inset 0 8px 12px #6b2222, 0 18px 0 #190101;
      }
      50% { 
        transform: scale(1.02) translateY(-5px);
        box-shadow: inset 0 -10px 0 #3c0808, inset 0 8px 12px #6b2222, 0 25px 0 #190101, 0 0 30px #d44;
      }
      100% { 
        transform: scale(1) translateY(0);
        box-shadow: inset 0 -10px 0 #3c0808, inset 0 8px 12px #6b2222, 0 18px 0 #190101, 0 0 20px #b44;
      }
    }

    /* Экраны */
    .screen {
      max-width: 520px;
      width: 100%;
      transition: opacity 0.35s;
      margin: 0 auto;
    }

    .hidden { display: none !important; }

    /* Карточка ввода */
    .vintage-card {
      background: #1f0505;
      padding: clamp(1.5rem, 5vw, 2.5rem) clamp(1rem, 4vw, 1.8rem);
      border-radius: 2.5rem 1rem 2.5rem 1rem;
      box-shadow: var(--shadow-heavy), 0 0 30px #3a0505 inset;
      border: 2px solid #731c1c;
      text-align: center;
      backdrop-filter: blur(3px);
      width: 100%;
      overflow: hidden;
    }

    .title-main {
      font-size: clamp(2rem, 10vw, 4.2rem);
      font-weight: 900;
      color: #f5d5d5;
      text-shadow: clamp(2px, 0.8vw, 5px) clamp(2px, 0.8vw, 5px) 0 #4a0000, 0 0 20px #c44;
      text-transform: uppercase;
      letter-spacing: clamp(2px, 1.5vw, 6px);
      line-height: 1.2;
      margin-bottom: 0.5rem;
      word-break: keep-all;
      white-space: nowrap;
    }

    /* Для мобильных — уменьшаем шрифт вместо переноса */
    @media (max-width: 480px) {
      .title-main {
        white-space: nowrap;
        font-size: clamp(1.5rem, 8vw, 2.5rem);
      }
    }

    @media (max-width: 360px) {
      .title-main {
        font-size: 1.3rem;
        letter-spacing: 2px;
      }
    }

    .title-sub {
      font-size: clamp(0.9rem, 3.5vw, 1.2rem);
      color: #dbb;
      text-transform: uppercase;
      letter-spacing: clamp(3px, 2vw, 6px);
      border-top: 1px solid #a33;
      border-bottom: 1px solid #a33;
      display: inline-block;
      padding: 0.5rem clamp(1rem, 3vw, 1.5rem);
      margin-bottom: clamp(1rem, 4vw, 2rem);
      word-break: keep-all;
      white-space: nowrap;
    }

    @media (max-width: 360px) {
      .title-sub {
        white-space: nowrap;
        font-size: 0.8rem;
        padding: 0.4rem 0.8rem;
      }
    }

    .dark-input {
      width: 100%;
      padding: clamp(0.8rem, 3vw, 1.2rem) clamp(0.5rem, 2vw, 1rem);
      font-size: clamp(1rem, 4vw, 1.4rem);
      text-align: center;
      background: #0c0101;
      border: 3px solid #8b2a2a;
      border-radius: 0;
      color: #fcc;
      font-weight: bold;
      text-transform: uppercase;
      letter-spacing: clamp(2px, 1.5vw, 5px);
      box-shadow: 0 6px 0 #3a0404, inset 0 0 15px #1a0000;
      outline: none;
      transition: all 0.15s;
      font-family: inherit;
      max-width: 100%;
    }

    .dark-input:focus {
      border-color: var(--gold);
      box-shadow: 0 6px 0 #5a1a1a, 0 0 25px #d44;
      background: #1e0202;
    }

    .dark-input::placeholder {
      font-size: clamp(0.8rem, 3vw, 1rem);
      letter-spacing: clamp(1px, 1vw, 3px);
    }

    .btn-gothic {
      margin-top: clamp(1.5rem, 5vw, 2.2rem);
      width: 100%;
      padding: clamp(0.8rem, 3vw, 1.2rem) clamp(0.5rem, 2vw, 1rem);
      background: #3d0b0b;
      border: 3px solid #b44;
      color: #ffdddd;
      font-size: clamp(1.2rem, 5vw, 1.6rem);
      font-weight: bold;
      text-transform: uppercase;
      letter-spacing: clamp(3px, 2vw, 8px);
      box-shadow: 0 8px 0 #1f0202, 0 0 20px #a22;
      cursor: pointer;
      transition: 0.08s linear;
      font-family: inherit;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    @media (max-width: 380px) {
      .btn-gothic {
        white-space: normal;
        word-break: keep-all;
        line-height: 1.3;
        font-size: 1rem;
        letter-spacing: 2px;
      }
    }

    .btn-gothic:active {
      transform: translateY(4px);
      box-shadow: 0 4px 0 #1f0202, 0 0 25px #f66;
    }

    /* --- КОНВЕРТ --- */
    .envelope-stage {
      max-width: 700px;
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 0 auto;
    }

    .envelope-wrapper {
      width: 100%;
      margin: 20px 0;
      filter: drop-shadow(0 20px 20px #00000080);
      cursor: pointer;
      transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
    }

    .envelope-wrapper:hover {
      transform: scale(1.01);
    }

    .envelope-wrapper:active { 
      transform: scale(0.98); 
    }

    .envelope {
      position: relative;
      background: #250808;
      padding: clamp(1rem, 4vw, 1.8rem) clamp(0.8rem, 3vw, 1.2rem) clamp(2rem, 6vw, 2.8rem);
      border-radius: 2rem 2rem 3rem 3rem;
      border: 4px solid #952a2a;
      box-shadow: inset 0 -10px 0 #3c0808, inset 0 8px 12px #6b2222, 0 18px 0 #190101;
      transition: all 0.3s ease;
      width: 100%;
      overflow: visible;
    }

    /* Анимация всего конверта при открытии */
    .envelope.open {
      animation: envelopeOpen 0.8s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
    }

    /* Клапан */
    .flap {
      position: absolute;
      top: -4px;
      left: -4px;
      right: -4px;
      height: clamp(70px, 15vw, 95px);
      background: linear-gradient(145deg, #bc3a3a, #6f1515);
      clip-path: polygon(0% 0%, 100% 0%, 50% 100%);
      border-radius: 1.5rem 1.5rem 0 0;
      border-bottom: 4px solid #e6b800;
      box-shadow: 0 8px 12px black;
      transform-origin: top;
      transition: transform 0.65s cubic-bezier(0.34, 1.56, 0.64, 1);
      z-index: 15;
      pointer-events: none;
    }

    .envelope.open .flap {
      transform: rotateX(180deg);
      box-shadow: 0 -8px 12px black;
    }

    /* Марка */
    .stamp {
      position: absolute;
      top: clamp(10px, 3vw, 15px);
      right: clamp(15px, 4vw, 25px);
      width: clamp(60px, 15vw, 80px);
      height: clamp(70px, 18vw, 90px);
      background: #1c0101;
      border: clamp(3px, 1vw, 5px) solid #b77;
      border-radius: 6px;
      box-shadow: 0 6px 0 #2b0000, inset 0 0 20px #600;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: #ecc;
      font-size: clamp(1.2rem, 5vw, 2rem);
      font-weight: 900;
      transform: rotate(5deg);
      z-index: 10;
      animation: stampPulse 2.8s infinite;
      line-height: 1.2;
      text-shadow: 2px 2px 0 #4a0000;
    }

    .stamp small {
      font-size: clamp(0.5rem, 2vw, 0.7rem);
      letter-spacing: clamp(1px, 1vw, 3px);
    }

    /* Адрес на конверте */
    .address-block {
      margin: clamp(35px, 10vw, 45px) clamp(2px, 1vw, 5px) clamp(2px, 1vw, 5px);
      text-align: center;
      width: 100%;
    }

    .recipient-name {
      font-size: clamp(1.8rem, 8vw, 3.2rem);
      font-weight: 900;
      color: #f3cfcf;
      text-shadow: clamp(2px, 1vw, 4px) clamp(2px, 1vw, 4px) 0 #630000;
      text-transform: uppercase;
      letter-spacing: clamp(2px, 1.5vw, 5px);
      word-break: break-word;
      hyphens: auto;
      line-height: 1.2;
      padding: 0 0.25rem;
    }

    .recipient-label {
      color: #c99;
      text-transform: uppercase;
      letter-spacing: clamp(2px, 2vw, 6px);
      font-size: clamp(0.7rem, 2.5vw, 0.9rem);
      margin-top: 4px;
      word-break: keep-all;
    }

    /* Открытка — скрыта, пока конверт не открыт */
    .card-inside {
      display: none;
      width: 100%;
    }

    .envelope.open .card-inside {
      display: block;
      animation: cardReveal 0.7s cubic-bezier(0.2, 0.9, 0.3, 1.2);
    }

    /* Стили внутренней открытки */
    .birthday-card {
      margin-top: 0.5rem;
      padding: clamp(1.2rem, 4vw, 2rem) clamp(0.8rem, 3vw, 1.5rem);
      background: linear-gradient(145deg, #2e0808, #140101);
      border-radius: 2.5rem 2.5rem 2rem 0.5rem;
      box-shadow: 0 14px 0 #2d0202, 0 0 30px #a33 inset, 0 0 15px #b44;
      border: 3px solid #b66;
      text-align: center;
      position: relative;
      z-index: 25;
      width: 100%;
      overflow: hidden;
    }

    .greeting {
      font-size: clamp(1.8rem, 6vw, 2.4rem);
      font-weight: 900;
      color: #ffbcbc;
      text-shadow: clamp(2px, 0.8vw, 4px) clamp(2px, 0.8vw, 4px) 0 #5f0000;
      text-transform: uppercase;
      margin-bottom: 0.5rem;
      word-break: break-word;
      hyphens: auto;
      line-height: 1.2;
    }

    .guest-highlight {
      font-size: clamp(2.2rem, 10vw, 4.5rem);
      font-weight: 900;
      background: #2f0303;
      display: inline-block;
      padding: 0.2rem clamp(1rem, 4vw, 2.5rem);
      border: 3px solid #d4af37;
      color: #ffe5b4;
      text-shadow: clamp(2px, 0.8vw, 3px) clamp(2px, 0.8vw, 3px) 0 #7a1f1f;
      margin: clamp(10px, 3vw, 20px) 0;
      text-transform: uppercase;
      letter-spacing: clamp(2px, 1.5vw, 4px);
      box-shadow: inset 0 0 20px #1e0000;
      word-break: break-word;
      hyphens: auto;
      max-width: 100%;
      line-height: 1.3;
    }

    .art-frame {
      margin: clamp(0.8rem, 3vw, 1.2rem) auto;
      padding: clamp(4px, 1.5vw, 8px);
      background: #3a0b0b;
      border-radius: 20px;
      box-shadow: inset 0 0 0 4px #6f1a1a, 0 12px 0 #1a0101;
      border: 2px solid #d4af37;
      max-width: 100%;
      width: fit-content;
    }

    .art-img {
      width: 100%;
      height: auto;
      display: block;
      border-radius: 12px;
      border: 2px solid black;
      box-shadow: 0 6px 15px black;
      aspect-ratio: 4/3;
      object-fit: cover;
      max-width: 380px;
    }

    .invite-details {
      display: inline-block;
      margin: clamp(0.8rem, 3vw, 1.2rem) 0 clamp(0.5rem, 2vw, 0.8rem);
      padding: clamp(0.5rem, 2vw, 0.8rem) clamp(1rem, 3vw, 1.8rem);
      background: #1a0101;
      border: 3px solid #b44;
      color: #ffd7b0;
      font-size: clamp(1rem, 3.5vw, 1.3rem);
      font-weight: bold;
      text-transform: uppercase;
      letter-spacing: clamp(1px, 1vw, 3px);
      box-shadow: inset 0 0 10px #3f0000;
      word-break: break-word;
      hyphens: auto;
      max-width: 100%;
      line-height: 1.5;
    }

    .signature {
      margin-top: clamp(1rem, 4vw, 1.5rem);
      font-size: clamp(2rem, 7vw, 2.6rem);
      font-weight: 900;
      color: #eebb88;
      text-shadow: 2px 2px 0 #4f0000, 0 0 20px #d44;
      text-transform: uppercase;
      word-break: break-word;
      letter-spacing: clamp(1px, 1vw, 2px);
    }

    .reset-link {
      margin-top: clamp(20px, 5vw, 30px);
      background: none;
      border: 2px solid #a65858;
      color: #deb;
      padding: clamp(8px, 2vw, 10px) clamp(15px, 4vw, 25px);
      font-size: clamp(1rem, 3.5vw, 1.2rem);
      text-transform: uppercase;
      letter-spacing: clamp(2px, 1.5vw, 4px);
      cursor: pointer;
      transition: 0.2s;
      box-shadow: 0 5px 0 #2c0303;
      font-weight: bold;
      background: #1e0404;
      white-space: nowrap;
      max-width: 100%;
    }

    @media (max-width: 380px) {
      .reset-link {
        white-space: normal;
        word-break: keep-all;
        font-size: 0.9rem;
        padding: 8px 15px;
      }
    }

    .reset-link:active {
      transform: translateY(3px);
      box-shadow: 0 2px 0 #2c0303;
    }

    .hint {
      margin-top: clamp(10px, 3vw, 15px);
      color: #b77;
      text-transform: uppercase;
      letter-spacing: clamp(1px, 1.5vw, 3px);
      font-size: clamp(0.7rem, 2.5vw, 0.8rem);
      animation: floatGlow 2.5s infinite;
      word-break: keep-all;
    }

    #confetti-canvas {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      pointer-events: none;
      z-index: 999;
    }

    /* Улучшенный фокус для доступности */
    :focus-visible {
      outline: 3px solid var(--accent);
      outline-offset: 2px;
    }
  </style>
</head>
<body>

<!-- ЭКРАН ВВОДА -->
<div id="nameScreen" class="screen">
  <div class="vintage-card">
    <div class="title-main">ПРИГЛАШЕНИЕ</div>
    <div class="title-sub">от Дарьи</div>
    
    <label for="guestNameInput" style="display:none;">Имя</label>
    <input type="text" id="guestNameInput" class="dark-input" placeholder="ВАШЕ ИМЯ" maxlength="25" autocomplete="off" inputmode="text">
    
    <button class="btn-gothic" id="openEnvelopeBtn">✟ ОТКРЫТЬ ✟</button>
  </div>
</div>

<!-- ЭКРАН КОНВЕРТА -->
<div id="envelopeStage" class="envelope-stage hidden">
  <div class="envelope-wrapper" id="envelopeClickArea" tabindex="0" role="button" aria-label="Нажмите чтобы открыть конверт">
    <div class="envelope" id="envelopeElement">
      <div class="flap" aria-hidden="true"></div>
      <div class="stamp" aria-hidden="true">🎨<small>ART</small></div>
      
      <div class="address-block">
        <div class="recipient-name" id="addressNamePreview">...</div>
        <div class="recipient-label">КОМУ: <span id="toNameSpan">ГОСТЬ</span></div>
      </div>
      
      <!-- ВНУТРЕННЯЯ ОТКРЫТКА -->
      <div class="card-inside">
        <div class="birthday-card">
          <div class="greeting">С ДНЁМ РОЖДЕНИЯ!</div>
          <div class="guest-highlight" id="cardGuestName">ДРУГ</div>
          
          <div class="art-frame">
            <img class="art-img" 
                 src="https://i.ibb.co/39sJvYNz/1.png" 
                 alt="Art Invitation" 
                 id="artworkImg"
                 loading="lazy"
                 width="400"
                 height="300">
          </div>
          
          <div class="invite-details">
            📍 19 АПРЕЛЯ · 18:00<br>
            Кафе «Кокороко»
          </div>
          
          <div class="signature">— ДАРЬЯ</div>
        </div>
      </div>
    </div>
  </div>
  
  <button class="reset-link" id="resetButton">← ДРУГОЕ ИМЯ</button>
  <div class="hint">✟ НАЖМИ НА КОНВЕРТ ✟</div>
</div>

<canvas id="confetti-canvas"></canvas>

<script>
  (function(){
    "use strict";

    // ---------- КОНФЕТТИ ----------
    const canvas = document.getElementById('confetti-canvas');
    const ctx = canvas.getContext('2d');
    let width, height;
    let particles = [];
    let animFrame = null;
    let active = false;

    const colors = ['#b33','#d44','#e6b800','#a11','#f66','#d4af37','#8b0000','#c44'];
    
    function resizeCanvas() {
      width = window.innerWidth;
      height = window.innerHeight;
      canvas.width = width;
      canvas.height = height;
    }

    function createConfetti() {
      particles = [];
      const cx = width/2, cy = height/2 - 40;
      for (let i=0; i<160; i++) {
        particles.push({
          x: cx + (Math.random()-0.5)*400,
          y: cy + Math.random()*200,
          vx: (Math.random()-0.5)*9,
          vy: (Math.random()-1.8)*6 - 1.5,
          size: Math.random()*14+5,
          color: colors[Math.floor(Math.random()*colors.length)],
          rot: Math.random()*Math.PI*2,
          rotSpeed: (Math.random()-0.5)*0.2,
          alpha: 1,
          fade: 0.006 + Math.random()*0.018,
          shape: Math.random()>0.4?'rect':'circle'
        });
      }
    }

    function drawConfetti() {
      ctx.clearRect(0,0,width,height);
      let alive = false;
      for (let p of particles) {
        p.x += p.vx;
        p.y += p.vy;
        p.vy += 0.13;
        p.vx *= 0.99;
        p.rot += p.rotSpeed;
        p.alpha -= p.fade;
        if (p.alpha <= 0.02 || p.y > height+60) continue;
        alive = true;
        ctx.save();
        ctx.translate(p.x,p.y);
        ctx.rotate(p.rot);
        ctx.globalAlpha = p.alpha;
        ctx.fillStyle = p.color;
        ctx.shadowColor = '#faa';
        ctx.shadowBlur = 15;
        if (p.shape==='rect') ctx.fillRect(-p.size/2,-p.size/2,p.size,p.size*1.4);
        else { ctx.beginPath(); ctx.arc(0,0,p.size/1.7,0,Math.PI*2); ctx.fill(); }
        ctx.restore();
      }
      if (alive) animFrame = requestAnimationFrame(drawConfetti);
      else { active = false; animFrame = null; }
    }

    function startConfetti() {
      if (animFrame) cancelAnimationFrame(animFrame);
      resizeCanvas();
      createConfetti();
      active = true;
      animFrame = requestAnimationFrame(drawConfetti);
    }

    function stopConfetti() {
      if (animFrame) { cancelAnimationFrame(animFrame); animFrame = null; }
      ctx.clearRect(0,0,width,height);
      active = false;
    }

    window.addEventListener('resize', () => { 
      if(active) { 
        stopConfetti(); 
        startConfetti(); 
      } 
    });

    // ---------- ЛОГИКА ПРИЛОЖЕНИЯ ----------
    const nameScreen = document.getElementById('nameScreen');
    const envelopeStage = document.getElementById('envelopeStage');
    const guestInput = document.getElementById('guestNameInput');
    const openBtn = document.getElementById('openEnvelopeBtn');
    const envelopeElem = document.getElementById('envelopeElement');
    const envelopeClickArea = document.getElementById('envelopeClickArea');
    const toNameSpan = document.getElementById('toNameSpan');
    const addressNamePreview = document.getElementById('addressNamePreview');
    const cardGuestName = document.getElementById('cardGuestName');
    const resetBtn = document.getElementById('resetButton');
    const artworkImg = document.getElementById('artworkImg');

    const DEFAULT_NAME = 'ГОСТЬ';
    let isOpen = false;

    // fallback изображения
    artworkImg.src = "https://i.ibb.co/39sJvYNz/1.png";
    artworkImg.onerror = () => { 
      artworkImg.src = "data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='300'%3E%3Crect width='400' height='300' fill='%23220000'/%3E%3Ctext x='200' y='170' font-size='28' fill='%23dbb' text-anchor='middle' font-family='serif'%3E🕯️ 19 АПРЕЛЯ 🕯️%3C/text%3E%3C/svg%3E"; 
    };

    function updateNameUI(name) {
      const display = name?.trim() || DEFAULT_NAME;
      toNameSpan.textContent = display;
      addressNamePreview.textContent = display;
      cardGuestName.textContent = display;
    }

    function setOpen(state) {
      isOpen = state;
      envelopeElem.classList.toggle('open', state);
      if (state) startConfetti(); else stopConfetti();
    }

    function showEnvelope(name) {
      updateNameUI(name);
      setOpen(false);
      nameScreen.classList.add('hidden');
      envelopeStage.classList.remove('hidden');
    }

    function showNameScreen() {
      setOpen(false);
      envelopeStage.classList.add('hidden');
      nameScreen.classList.remove('hidden');
      guestInput.value = '';
      guestInput.focus();
    }

    // События
    openBtn.addEventListener('click', ()=>{
      showEnvelope(guestInput.value.trim() || DEFAULT_NAME);
    });

    envelopeClickArea.addEventListener('click', (e)=>{
      // Предотвращаем срабатывание при клике на внутренние элементы
      if (!isOpen) setOpen(true);
    });
    
    envelopeClickArea.addEventListener('keydown', (e)=>{
      if ((e.key==='Enter'||e.key===' ') && !isOpen) { 
        e.preventDefault(); 
        setOpen(true); 
      }
    });

    resetBtn.addEventListener('click', showNameScreen);
    
    guestInput.addEventListener('keypress', (e)=>{ 
      if(e.key==='Enter'){ 
        e.preventDefault(); 
        showEnvelope(guestInput.value.trim()||DEFAULT_NAME); 
      }
    });

    // URL параметр ?name=
    const params = new URLSearchParams(window.location.search);
    const urlName = params.get('name')?.trim();
    if (urlName) {
      showEnvelope(urlName);
    } else {
      nameScreen.classList.remove('hidden');
      envelopeStage.classList.add('hidden');
      guestInput.focus();
    }

    window.addEventListener('pagehide', stopConfetti);
  })();
</script>
</body>
</html>
