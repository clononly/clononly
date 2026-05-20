<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CLON</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;600&family=Bebas+Neue&family=DM+Mono:wght@300;400&display=swap" rel="stylesheet">
<style>
  :root {
    --navy: #0b1f3a;
    --navy-mid: #0f2748;
    --white: #f5f5f0;
    --white-dim: rgba(245,245,240,0.55);
    --white-faint: rgba(245,245,240,0.08);
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background-color: var(--navy);
    color: var(--white);
    font-family: 'DM Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed;
    width: 8px; height: 8px;
    background: var(--white);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s ease, width 0.3s ease, height 0.3s ease, opacity 0.3s;
  }
  .cursor-ring {
    position: fixed;
    width: 36px; height: 36px;
    border: 1px solid rgba(245,245,240,0.4);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: transform 0.18s ease, width 0.3s ease, height 0.3s ease, border-color 0.3s;
  }
  body:hover .cursor { opacity: 1; }

  /* Grain overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 1;
    opacity: 0.6;
  }

  /* Ambient glow */
  .glow {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
  }
  .glow-1 {
    width: 600px; height: 600px;
    background: rgba(255,255,255,0.025);
    top: -200px; right: -100px;
    animation: drift1 18s ease-in-out infinite alternate;
  }
  .glow-2 {
    width: 400px; height: 400px;
    background: rgba(255,255,255,0.015);
    bottom: 100px; left: -100px;
    animation: drift2 22s ease-in-out infinite alternate;
  }

  @keyframes drift1 { to { transform: translate(-60px, 80px); } }
  @keyframes drift2 { to { transform: translate(80px, -60px); } }

  /* Hero */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: clamp(3rem, 8vw, 8rem) clamp(2rem, 8vw, 8rem);
    z-index: 2;
  }

  .hero-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.3em;
    color: var(--white-dim);
    text-transform: uppercase;
    margin-bottom: 2.5rem;
    opacity: 0;
    animation: fadeUp 1s 0.3s forwards;
  }

  .hero-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(7rem, 22vw, 22rem);
    line-height: 0.88;
    letter-spacing: -0.02em;
    color: var(--white);
    opacity: 0;
    animation: fadeUp 1s 0.5s forwards;
    position: relative;
  }

  .hero-name span {
    display: block;
    position: relative;
  }

  /* Vertical rule */
  .v-rule {
    position: absolute;
    right: clamp(2rem, 8vw, 8rem);
    top: 50%;
    transform: translateY(-50%);
    width: 1px;
    height: 0;
    background: linear-gradient(to bottom, transparent, var(--white-dim), transparent);
    animation: growLine 1.4s 0.8s forwards;
  }
  @keyframes growLine { to { height: 60vh; } }

  .scroll-hint {
    position: absolute;
    bottom: 3rem;
    left: clamp(2rem, 8vw, 8rem);
    display: flex;
    align-items: center;
    gap: 1rem;
    opacity: 0;
    animation: fadeUp 1s 1.2s forwards;
  }
  .scroll-hint span {
    font-size: 0.6rem;
    letter-spacing: 0.3em;
    color: var(--white-dim);
    text-transform: uppercase;
  }
  .scroll-line {
    width: 40px;
    height: 1px;
    background: var(--white-dim);
    position: relative;
    overflow: hidden;
  }
  .scroll-line::after {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 100%; height: 100%;
    background: var(--white);
    animation: slide 2s 1.5s ease-in-out infinite;
  }
  @keyframes slide { 0%{left:-100%} 50%{left:100%} 100%{left:100%} }

  /* Section base */
  section {
    position: relative;
    z-index: 2;
    padding: clamp(5rem, 10vw, 10rem) clamp(2rem, 8vw, 8rem);
  }

  .section-label {
    font-size: 0.6rem;
    letter-spacing: 0.4em;
    color: var(--white-dim);
    text-transform: uppercase;
    margin-bottom: 4rem;
    display: flex;
    align-items: center;
    gap: 1.5rem;
  }
  .section-label::before {
    content: '';
    display: inline-block;
    width: 30px;
    height: 1px;
    background: var(--white-dim);
  }

  /* Streaming links */
  .links-section {
    border-top: 1px solid var(--white-faint);
  }

  .link-list {
    display: flex;
    flex-direction: column;
    gap: 0;
  }

  .link-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 2.2rem 0;
    border-bottom: 1px solid var(--white-faint);
    text-decoration: none;
    color: var(--white);
    position: relative;
    overflow: hidden;
    transition: color 0.3s;
    cursor: none;
  }

  .link-item::before {
    content: '';
    position: absolute;
    left: -100%;
    top: 0;
    width: 100%;
    height: 100%;
    background: var(--white-faint);
    transition: left 0.5s cubic-bezier(0.16,1,0.3,1);
  }
  .link-item:hover::before { left: 0; }

  .link-left {
    display: flex;
    align-items: center;
    gap: 2rem;
    position: relative;
    z-index: 1;
  }

  .link-num {
    font-size: 0.6rem;
    letter-spacing: 0.2em;
    color: var(--white-dim);
    width: 2ch;
  }

  .link-platform {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(1.8rem, 4vw, 3.2rem);
    letter-spacing: 0.05em;
    transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
  }
  .link-item:hover .link-platform { transform: translateX(8px); }

  .link-arrow {
    position: relative;
    z-index: 1;
    font-size: 1.2rem;
    opacity: 0.4;
    transition: opacity 0.3s, transform 0.4s cubic-bezier(0.16,1,0.3,1);
  }
  .link-item:hover .link-arrow {
    opacity: 1;
    transform: translate(6px, -6px);
  }

  /* Platform icons */
  .link-icon {
    width: 20px;
    height: 20px;
    opacity: 0.5;
    flex-shrink: 0;
    transition: opacity 0.3s;
  }
  .link-item:hover .link-icon { opacity: 1; }

  /* Newsletter */
  .newsletter-section {
    border-top: 1px solid var(--white-faint);
  }

  .newsletter-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }

  .newsletter-heading {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(2.5rem, 5vw, 5rem);
    line-height: 1.1;
    letter-spacing: -0.01em;
  }

  .newsletter-heading em {
    font-style: italic;
    color: var(--white-dim);
  }

  .newsletter-right {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-top: 1rem;
  }

  .newsletter-sub {
    font-size: 0.68rem;
    letter-spacing: 0.15em;
    color: var(--white-dim);
    line-height: 1.8;
    margin-bottom: 3rem;
    text-transform: uppercase;
  }

  .email-form {
    display: flex;
    flex-direction: column;
    gap: 0;
    border: 1px solid rgba(245,245,240,0.2);
    position: relative;
    overflow: hidden;
  }

  .email-input {
    background: transparent;
    border: none;
    color: var(--white);
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    letter-spacing: 0.15em;
    padding: 1.4rem 1.6rem;
    outline: none;
    width: 100%;
  }

  .email-input::placeholder {
    color: var(--white-dim);
    font-size: 0.7rem;
  }

  .email-divider {
    height: 1px;
    background: rgba(245,245,240,0.2);
  }

  .submit-btn {
    background: transparent;
    border: none;
    color: var(--white);
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1rem;
    letter-spacing: 0.25em;
    padding: 1.4rem 1.6rem;
    cursor: none;
    text-align: left;
    position: relative;
    overflow: hidden;
    transition: color 0.4s;
  }

  .submit-btn::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--white);
    transform: translateX(-100%);
    transition: transform 0.5s cubic-bezier(0.16,1,0.3,1);
  }

  .submit-btn:hover { color: var(--navy); }
  .submit-btn:hover::before { transform: translateX(0); }

  .submit-btn span {
    position: relative;
    z-index: 1;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .success-msg {
    display: none;
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    color: var(--white-dim);
    text-transform: uppercase;
    margin-top: 1.5rem;
  }

  /* Footer */
  footer {
    position: relative;
    z-index: 2;
    padding: 3rem clamp(2rem, 8vw, 8rem);
    border-top: 1px solid var(--white-faint);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  footer span {
    font-size: 0.6rem;
    letter-spacing: 0.3em;
    color: var(--white-dim);
    text-transform: uppercase;
  }

  /* Animations */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.9s cubic-bezier(0.16,1,0.3,1), transform 0.9s cubic-bezier(0.16,1,0.3,1);
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* Responsive */
  @media (max-width: 768px) {
    .newsletter-inner {
      grid-template-columns: 1fr;
      gap: 3rem;
    }
    .v-rule { display: none; }
    .hero-name { font-size: clamp(6rem, 28vw, 10rem); }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<div class="glow glow-1"></div>
<div class="glow glow-2"></div>

<!-- Hero -->
<div class="hero">
  <p class="hero-label">Artist · Music</p>
  <h1 class="hero-name">
    <span>CLON</span>
  </h1>
  <div class="v-rule"></div>
  <div class="scroll-hint">
    <div class="scroll-line"></div>
    <span>Explore</span>
  </div>
</div>

<!-- Streaming -->
<section class="links-section">
  <p class="section-label reveal">Stream</p>
  <div class="link-list">

    <a href="https://music.apple.com/tz/artist/clon/1726079036" target="_blank" rel="noopener" class="link-item reveal">
      <div class="link-left">
        <span class="link-num">01</span>
        <svg class="link-icon" viewBox="0 0 24 24" fill="currentColor">
          <path d="M18.71 19.5C17.88 20.74 17 21.95 15.66 21.97C14.32 22 13.89 21.18 12.37 21.18C10.84 21.18 10.37 21.95 9.1 22C7.78 22.05 6.8 20.68 5.96 19.47C4.25 17 2.94 12.45 4.7 9.39C5.57 7.87 7.13 6.91 8.82 6.88C10.1 6.86 11.32 7.75 12.11 7.75C12.89 7.75 14.37 6.68 15.92 6.84C16.57 6.87 18.39 7.1 19.56 8.82C19.47 8.88 17.39 10.1 17.41 12.63C17.44 15.65 20.06 16.66 20.09 16.67C20.06 16.74 19.67 18.11 18.71 19.5ZM13 3.5C13.73 2.67 14.94 2.04 15.94 2C16.07 3.17 15.6 4.35 14.9 5.19C14.21 6.04 13.07 6.7 11.95 6.61C11.8 5.46 12.36 4.26 13 3.5Z"/>
        </svg>
        <span class="link-platform">Apple Music</span>
      </div>
      <span class="link-arrow">↗</span>
    </a>

    <a href="https://open.spotify.com/artist/0dAoBT13AT860vuvz4Bzip?si=WHXtyCZeSBuA8aJdnfPmvQ" target="_blank" rel="noopener" class="link-item reveal">
      <div class="link-left">
        <span class="link-num">02</span>
        <svg class="link-icon" viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 0C5.4 0 0 5.4 0 12s5.4 12 12 12 12-5.4 12-12S18.66 0 12 0zm5.521 17.34c-.24.359-.66.48-1.021.24-2.82-1.74-6.36-2.101-10.561-1.141-.418.122-.779-.179-.899-.539-.12-.421.18-.78.54-.9 4.56-1.021 8.52-.6 11.64 1.32.42.18.479.659.301 1.02zm1.44-3.3c-.301.42-.841.6-1.262.3-3.239-1.98-8.159-2.58-11.939-1.38-.479.12-1.02-.12-1.14-.6-.12-.48.12-1.021.6-1.141C9.6 9.9 15 10.561 18.72 12.84c.361.181.54.78.241 1.2zm.12-3.36C15.24 8.4 8.82 8.16 5.16 9.301c-.6.179-1.2-.181-1.38-.721-.18-.601.18-1.2.72-1.381 4.26-1.26 11.28-1.02 15.721 1.621.539.3.719 1.02.419 1.56-.299.421-1.02.599-1.559.3z"/>
        </svg>
        <span class="link-platform">Spotify</span>
      </div>
      <span class="link-arrow">↗</span>
    </a>

    <a href="https://youtube.com/@clononly" target="_blank" rel="noopener" class="link-item reveal">
      <div class="link-left">
        <span class="link-num">03</span>
        <svg class="link-icon" viewBox="0 0 24 24" fill="currentColor">
          <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/>
        </svg>
        <span class="link-platform">YouTube</span>
      </div>
      <span class="link-arrow">↗</span>
    </a>

  </div>
</section>

<!-- Newsletter -->
<section class="newsletter-section" id="newsletter">
  <p class="section-label reveal">Newsletter</p>
  <div class="newsletter-inner">
    <div class="reveal">
      <h2 class="newsletter-heading">
        Stay<br>
        <em>close</em><br>
        to the sound.
      </h2>
    </div>
    <div class="newsletter-right reveal">
      <p class="newsletter-sub">Updates delivered directly.<br>No noise. Just signal.</p>
      <div class="email-form">
        <input type="email" class="email-input" id="emailInput" placeholder="YOUR EMAIL ADDRESS" autocomplete="off">
        <div class="email-divider"></div>
        <button class="submit-btn" onclick="handleSubscribe()">
          <span>Subscribe <span>→</span></span>
        </button>
      </div>
      <p class="success-msg" id="successMsg">✓ &nbsp;You're in. Watch your inbox.</p>
    </div>
  </div>
</section>

<!-- Footer -->
<footer>
  <span>Clon</span>
  <span>© 2026</span>
</footer>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
  });

  function animRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animRing);
  }
  animRing();

  document.querySelectorAll('a, button, input').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.width = '16px';
      cursor.style.height = '16px';
      ring.style.width = '56px';
      ring.style.height = '56px';
      ring.style.borderColor = 'rgba(245,245,240,0.6)';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.width = '8px';
      cursor.style.height = '8px';
      ring.style.width = '36px';
      ring.style.height = '36px';
      ring.style.borderColor = 'rgba(245,245,240,0.4)';
    });
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));

  // Newsletter
  function handleSubscribe() {
    const input = document.getElementById('emailInput');
    const success = document.getElementById('successMsg');
    const val = input.value.trim();
    if (!val || !val.includes('@')) {
      input.style.borderBottom = '1px solid rgba(245,245,240,0.5)';
      input.placeholder = 'ENTER A VALID EMAIL';
      return;
    }
    input.parentElement.style.opacity = '0.4';
    input.parentElement.style.pointerEvents = 'none';
    success.style.display = 'block';
    setTimeout(() => { success.style.opacity = '1'; }, 10);
  }

  // Keyboard: Enter on input
  document.getElementById('emailInput').addEventListener('keydown', e => {
    if (e.key === 'Enter') handleSubscribe();
  });
</script>
</body>
</html>
