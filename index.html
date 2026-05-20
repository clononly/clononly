<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>CLON</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cormorant+Garamond:ital,wght@0,300;1,300&family=DM+Mono:wght@300&display=swap" rel="stylesheet">
<style>
  :root {
    --navy: #0b1f3a;
    --white: #f4f4ef;
    --dim: rgba(244,244,239,0.5);
    --faint: rgba(244,244,239,0.07);
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html, body {
    background: var(--navy);
    color: var(--white);
    font-family: 'DM Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    -webkit-font-smoothing: antialiased;
  }

  /* Grain */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 100;
    opacity: 0.5;
  }

  /* Glow */
  .glow {
    position: fixed;
    border-radius: 50%;
    filter: blur(100px);
    pointer-events: none;
    z-index: 0;
    width: 400px; height: 400px;
    background: rgba(255,255,255,0.018);
    top: -100px; right: -80px;
    animation: drift 20s ease-in-out infinite alternate;
  }
  @keyframes drift { to { transform: translate(-40px, 60px); } }

  /* ── HERO ── */
  .hero {
    position: relative;
    z-index: 1;
    padding: 3.5rem 1.8rem 2.5rem;
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
  }

  .hero-tag {
    font-size: 0.58rem;
    letter-spacing: 0.35em;
    color: var(--dim);
    text-transform: uppercase;
    opacity: 0;
    animation: up 0.8s 0.2s forwards;
  }

  .hero-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(5.5rem, 28vw, 8rem);
    line-height: 0.9;
    letter-spacing: -0.01em;
    opacity: 0;
    animation: up 0.8s 0.35s forwards;
  }

  .hero-line {
    width: 100%;
    height: 1px;
    background: linear-gradient(to right, var(--dim), transparent);
    margin-top: 1.2rem;
    opacity: 0;
    animation: up 0.8s 0.5s forwards;
  }

  /* ── STREAM ── */
  .section {
    position: relative;
    z-index: 1;
    padding: 0 1.8rem;
  }

  .section-label {
    font-size: 0.55rem;
    letter-spacing: 0.4em;
    color: var(--dim);
    text-transform: uppercase;
    padding: 1.5rem 0 1rem;
    display: flex;
    align-items: center;
    gap: 1rem;
    opacity: 0;
    animation: up 0.8s 0.6s forwards;
  }
  .section-label::before {
    content: '';
    display: block;
    width: 20px;
    height: 1px;
    background: var(--dim);
    flex-shrink: 0;
  }

  .links {
    display: flex;
    flex-direction: column;
    border-top: 1px solid var(--faint);
  }

  .link {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1.1rem 0;
    border-bottom: 1px solid var(--faint);
    text-decoration: none;
    color: var(--white);
    position: relative;
    overflow: hidden;
    opacity: 0;
    animation: up 0.7s forwards;
    -webkit-tap-highlight-color: transparent;
  }
  .link:nth-child(1) { animation-delay: 0.7s; }
  .link:nth-child(2) { animation-delay: 0.82s; }
  .link:nth-child(3) { animation-delay: 0.94s; }

  .link::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--faint);
    transform: translateX(-100%);
    transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
  }
  .link:active::before { transform: translateX(0); }

  .link-left {
    display: flex;
    align-items: center;
    gap: 1rem;
    position: relative;
    z-index: 1;
  }

  .link-num {
    font-size: 0.55rem;
    letter-spacing: 0.15em;
    color: var(--dim);
    width: 2ch;
  }

  .link-icon {
    width: 16px;
    height: 16px;
    opacity: 0.55;
    flex-shrink: 0;
  }

  .link-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.7rem;
    letter-spacing: 0.06em;
  }

  .link-arrow {
    font-size: 0.9rem;
    opacity: 0.35;
    position: relative;
    z-index: 1;
    transition: transform 0.3s;
  }
  .link:active .link-arrow { transform: translate(4px, -4px); opacity: 1; }

  /* ── NEWSLETTER ── */
  .newsletter {
    margin-top: 2.5rem;
    border-top: 1px solid var(--faint);
    padding: 0 1.8rem 4rem;
    position: relative;
    z-index: 1;
    opacity: 0;
    animation: up 0.8s 1.1s forwards;
  }

  .nl-label {
    font-size: 0.55rem;
    letter-spacing: 0.4em;
    color: var(--dim);
    text-transform: uppercase;
    padding: 1.5rem 0 1.2rem;
    display: flex;
    align-items: center;
    gap: 1rem;
  }
  .nl-label::before {
    content: '';
    display: block;
    width: 20px; height: 1px;
    background: var(--dim);
  }

  .nl-heading {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(2rem, 9vw, 3rem);
    line-height: 1.15;
    margin-bottom: 1.8rem;
  }
  .nl-heading em {
    font-style: italic;
    color: var(--dim);
  }

  .nl-sub {
    font-size: 0.6rem;
    letter-spacing: 0.12em;
    color: var(--dim);
    line-height: 2;
    text-transform: uppercase;
    margin-bottom: 1.8rem;
  }

  .form-box {
    border: 1px solid rgba(244,244,239,0.18);
  }

  .form-input {
    display: block;
    width: 100%;
    background: transparent;
    border: none;
    outline: none;
    color: var(--white);
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.12em;
    padding: 1.1rem 1.2rem;
    -webkit-appearance: none;
  }
  .form-input::placeholder { color: var(--dim); }

  .form-divider {
    height: 1px;
    background: rgba(244,244,239,0.18);
  }

  .form-btn {
    display: block;
    width: 100%;
    background: transparent;
    border: none;
    color: var(--white);
    font-family: 'Bebas Neue', sans-serif;
    font-size: 0.95rem;
    letter-spacing: 0.3em;
    padding: 1.1rem 1.2rem;
    text-align: left;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: color 0.35s;
    -webkit-tap-highlight-color: transparent;
  }
  .form-btn::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--white);
    transform: translateX(-100%);
    transition: transform 0.45s cubic-bezier(0.16,1,0.3,1);
  }
  .form-btn:active { color: var(--navy); }
  .form-btn:active::before { transform: translateX(0); }

  .form-btn-inner {
    position: relative;
    z-index: 1;
    display: flex;
    justify-content: space-between;
  }

  .success {
    display: none;
    font-size: 0.58rem;
    letter-spacing: 0.2em;
    color: var(--dim);
    text-transform: uppercase;
    padding: 1rem 0 0;
  }

  /* Footer */
  footer {
    position: relative;
    z-index: 1;
    padding: 1.5rem 1.8rem;
    border-top: 1px solid var(--faint);
    display: flex;
    justify-content: space-between;
  }
  footer span {
    font-size: 0.55rem;
    letter-spacing: 0.3em;
    color: var(--dim);
    text-transform: uppercase;
  }

  @keyframes up {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
</style>
</head>
<body>

<div class="glow"></div>

<!-- Hero -->
<div class="hero">
  <p class="hero-tag">Artist · Music</p>
  <h1 class="hero-name">CLON</h1>
  <div class="hero-line"></div>
</div>

<!-- Stream -->
<div class="section">
  <p class="section-label">Stream</p>
  <div class="links">

    <a href="https://music.apple.com/tz/artist/clon/1726079036" target="_blank" rel="noopener" class="link">
      <div class="link-left">
        <span class="link-num">01</span>
        <svg class="link-icon" viewBox="0 0 24 24" fill="currentColor">
          <path d="M18.71 19.5C17.88 20.74 17 21.95 15.66 21.97C14.32 22 13.89 21.18 12.37 21.18C10.84 21.18 10.37 21.95 9.1 22C7.78 22.05 6.8 20.68 5.96 19.47C4.25 17 2.94 12.45 4.7 9.39C5.57 7.87 7.13 6.91 8.82 6.88C10.1 6.86 11.32 7.75 12.11 7.75C12.89 7.75 14.37 6.68 15.92 6.84C16.57 6.87 18.39 7.1 19.56 8.82C19.47 8.88 17.39 10.1 17.41 12.63C17.44 15.65 20.06 16.66 20.09 16.67C20.06 16.74 19.67 18.11 18.71 19.5ZM13 3.5C13.73 2.67 14.94 2.04 15.94 2C16.07 3.17 15.6 4.35 14.9 5.19C14.21 6.04 13.07 6.7 11.95 6.61C11.8 5.46 12.36 4.26 13 3.5Z"/>
        </svg>
        <span class="link-name">Apple Music</span>
      </div>
      <span class="link-arrow">↗</span>
    </a>

    <a href="https://open.spotify.com/artist/0dAoBT13AT860vuvz4Bzip?si=WHXtyCZeSBuA8aJdnfPmvQ" target="_blank" rel="noopener" class="link">
      <div class="link-left">
        <span class="link-num">02</span>
        <svg class="link-icon" viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 0C5.4 0 0 5.4 0 12s5.4 12 12 12 12-5.4 12-12S18.66 0 12 0zm5.521 17.34c-.24.359-.66.48-1.021.24-2.82-1.74-6.36-2.101-10.561-1.141-.418.122-.779-.179-.899-.539-.12-.421.18-.78.54-.9 4.56-1.021 8.52-.6 11.64 1.32.42.18.479.659.301 1.02zm1.44-3.3c-.301.42-.841.6-1.262.3-3.239-1.98-8.159-2.58-11.939-1.38-.479.12-1.02-.12-1.14-.6-.12-.48.12-1.021.6-1.141C9.6 9.9 15 10.561 18.72 12.84c.361.181.54.78.241 1.2zm.12-3.36C15.24 8.4 8.82 8.16 5.16 9.301c-.6.179-1.2-.181-1.38-.721-.18-.601.18-1.2.72-1.381 4.26-1.26 11.28-1.02 15.721 1.621.539.3.719 1.02.419 1.56-.299.421-1.02.599-1.559.3z"/>
        </svg>
        <span class="link-name">Spotify</span>
      </div>
      <span class="link-arrow">↗</span>
    </a>

    <a href="https://youtube.com/@clononly" target="_blank" rel="noopener" class="link">
      <div class="link-left">
        <span class="link-num">03</span>
        <svg class="link-icon" viewBox="0 0 24 24" fill="currentColor">
          <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/>
        </svg>
        <span class="link-name">YouTube</span>
      </div>
      <span class="link-arrow">↗</span>
    </a>

  </div>
</div>

<!-- Newsletter -->
<div class="newsletter">
  <p class="nl-label">Newsletter</p>
  <h2 class="nl-heading">Stay<br><em>close</em><br>to the sound.</h2>
  <p class="nl-sub">Updates direct.<br>No noise. Just signal.</p>
  <div class="form-box">
    <input type="email" class="form-input" id="email" placeholder="YOUR EMAIL" autocomplete="off">
    <div class="form-divider"></div>
    <button class="form-btn" onclick="subscribe()">
      <span class="form-btn-inner"><span>Subscribe</span><span>→</span></span>
    </button>
  </div>
  <p class="success" id="success">✓ &nbsp;You're in. Watch your inbox.</p>
</div>

<footer>
  <span>Clon</span>
  <span>© 2026</span>
</footer>

<script>
function subscribe() {
  const email = document.getElementById('email');
  const success = document.getElementById('success');
  if (!email.value || !email.value.includes('@')) {
    email.placeholder = 'ENTER VALID EMAIL';
    return;
  }
  email.parentElement.style.opacity = '0.4';
  email.parentElement.style.pointerEvents = 'none';
  success.style.display = 'block';
}
document.getElementById('email').addEventListener('keydown', e => {
  if (e.key === 'Enter') subscribe();
});
</script>
</body>
</html>
