<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Jack Foster</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;500;600&family=Barlow:wght@200;300;400;500&family=Barlow+Condensed:wght@300;400;500;600&display=swap" rel="stylesheet" />

  <style>
    :root {
      --gold:        #c9a84c;
      --gold-light:  #e2c47a;
      --gold-dim:    rgba(201,168,76,0.12);
      --white:       #f5f5f0;
      --white-soft:  rgba(245,245,240,0.7);
      --white-muted: rgba(245,245,240,0.35);
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      min-height: 100vh;
      font-family: 'Barlow', sans-serif;
      font-weight: 300;
      color: var(--white);
      background-color: #141414;
      background-image:
        repeating-linear-gradient(
          90deg,
          transparent, transparent 3px,
          rgba(255,255,255,0.018) 3px,
          rgba(255,255,255,0.018) 4px
        ),
        repeating-linear-gradient(
          0deg,
          transparent, transparent 3px,
          rgba(255,255,255,0.018) 3px,
          rgba(255,255,255,0.018) 4px
        ),
        repeating-linear-gradient(
          45deg,
          rgba(0,0,0,0.35) 0px,   rgba(0,0,0,0.35) 2px,
          rgba(30,30,30,0.6) 2px, rgba(30,30,30,0.6) 4px
        ),
        repeating-linear-gradient(
          135deg,
          rgba(0,0,0,0.35) 0px,   rgba(0,0,0,0.35) 2px,
          rgba(20,20,20,0.6) 2px, rgba(20,20,20,0.6) 4px
        );
      background-size: 4px 4px, 4px 4px, 8px 8px, 8px 8px;
      overflow-x: hidden;
    }

    body::after {
      content: '';
      position: fixed;
      inset: 0;
      background: radial-gradient(ellipse at 50% 0%, transparent 40%, rgba(0,0,0,0.55) 100%);
      pointer-events: none;
      z-index: 0;
    }

    body > * { position: relative; z-index: 1; }

    /* ── TOP GOLD RULE ── */
    .top-rule {
      width: 100%;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--gold) 30%, var(--gold-light) 50%, var(--gold) 70%, transparent);
      animation: fadeIn 1.4s ease both;
    }

    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 100px 24px 80px;
    }

    .avatar-wrap {
      position: relative;
      width: 164px;
      height: 164px;
      margin-bottom: 36px;
      animation: fadeUp 0.9s 0.2s ease both;
    }

    .avatar-ring {
      position: absolute;
      inset: -5px;
      border-radius: 50%;
      background: conic-gradient(
        var(--gold) 0deg,
        var(--gold-light) 90deg,
        var(--gold) 180deg,
        transparent 220deg,
        transparent 360deg
      );
      animation: spin 9s linear infinite;
    }

    .avatar-ring-bg {
      position: absolute;
      inset: -3px;
      border-radius: 50%;
      border: 1px solid rgba(201,168,76,0.2);
    }

    .avatar {
      position: relative;
      width: 164px;
      height: 164px;
      border-radius: 50%;
      overflow: hidden;
      background: #1c1c1c;
      z-index: 1;
    }

    .avatar img { width: 100%; height: 100%; object-fit: cover; display: block; }

    .avatar-placeholder {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'Cormorant Garamond', serif;
      font-size: 54px;
      font-weight: 300;
      color: var(--gold);
    }

    .hero-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(56px, 11vw, 104px);
      font-weight: 300;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      line-height: 1;
      color: var(--white);
      animation: fadeUp 0.9s 0.36s ease both;
    }

    .hero-name em {
      font-style: normal;
      color: var(--gold);
    }

    .hero-school {
      margin-top: 16px;
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 11px;
      font-weight: 400;
      letter-spacing: 0.3em;
      text-transform: uppercase;
      color: var(--white-muted);
      animation: fadeUp 0.9s 0.5s ease both;
    }

    .hero-email {
      margin-top: 10px;
      font-family: 'Barlow', sans-serif;
      font-size: 13px;
      font-weight: 300;
      color: var(--gold);
      text-decoration: none;
      letter-spacing: 0.07em;
      animation: fadeUp 0.9s 0.6s ease both;
      transition: color 0.2s;
      display: inline-block;
    }
    .hero-email:hover { color: var(--gold-light); }

    .scroll-hint {
      margin-top: 64px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      animation: fadeUp 0.9s 0.9s ease both;
    }
    .scroll-hint span {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 10px;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--white-muted);
    }
    .scroll-line {
      width: 1px;
      height: 42px;
      background: linear-gradient(to bottom, var(--gold), transparent);
      animation: scrollPulse 2.2s ease-in-out infinite;
    }

    /* ── BIO SECTION ── */
    .bio-section {
      max-width: 680px;
      margin: 0 auto;
      padding: 90px 32px 70px;
    }

    .section-rule {
      width: 36px;
      height: 1px;
      background: var(--gold);
      margin-bottom: 30px;
    }

    .bio-text {
      font-size: 16px;
      font-weight: 300;
      line-height: 1.9;
      color: var(--white-soft);
    }
    .bio-text strong { color: var(--white); font-weight: 400; }

    /* ── NAV BOXES ── */
    .nav-boxes {
      max-width: 680px;
      margin: 0 auto;
      padding: 0 32px 110px;
      display: flex;
      flex-direction: column;
      gap: 14px;
    }

    .nav-box {
      display: block;
      text-decoration: none;
      border: 1px solid rgba(201,168,76,0.28);
      padding: 38px 42px;
      position: relative;
      overflow: hidden;
      transition: border-color 0.3s, background 0.3s;
    }

    /* gold shimmer fill on hover */
    .nav-box::before {
      content: '';
      position: absolute;
      inset: 0;
      background: var(--gold-dim);
      opacity: 0;
      transition: opacity 0.3s;
    }
    .nav-box:hover { border-color: rgba(201,168,76,0.85); }
    .nav-box:hover::before { opacity: 1; }

    /* bottom-right corner brackets */
    .nav-box .corner-tl,
    .nav-box .corner-br {
      position: absolute;
      width: 14px; height: 14px;
      opacity: 0;
      transition: opacity 0.3s, width 0.3s, height 0.3s;
    }
    .nav-box .corner-tl {
      top: 0; left: 0;
      border-top: 1px solid var(--gold);
      border-left: 1px solid var(--gold);
    }
    .nav-box .corner-br {
      bottom: 0; right: 0;
      border-bottom: 1px solid var(--gold);
      border-right: 1px solid var(--gold);
    }
    .nav-box:hover .corner-tl,
    .nav-box:hover .corner-br { opacity: 1; width: 22px; height: 22px; }

    .nav-box-inner {
      position: relative;
      z-index: 1;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .nav-box-label {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 10px;
      font-weight: 400;
      letter-spacing: 0.28em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 8px;
    }

    .nav-box-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 38px;
      font-weight: 400;
      letter-spacing: 0.05em;
      color: var(--white);
    }

    .nav-box-desc {
      margin-top: 6px;
      font-size: 13px;
      font-weight: 300;
      color: var(--white-muted);
      letter-spacing: 0.03em;
    }

    .nav-box-arrow {
      font-size: 26px;
      color: var(--gold);
      opacity: 0.45;
      transition: opacity 0.3s, transform 0.3s;
      flex-shrink: 0;
      margin-left: 28px;
    }
    .nav-box:hover .nav-box-arrow { opacity: 1; transform: translateX(7px); }

    /* ── FOOTER ── */
    footer {
      border-top: 1px solid rgba(255,255,255,0.06);
      padding: 26px 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    footer p {
      font-family: 'Barlow Condensed', sans-serif;
      font-size: 10px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--white-muted);
    }
    .footer-line {
      width: 28px; height: 1px;
      background: var(--gold);
      opacity: 0.35;
    }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(22px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeIn {
      from { opacity: 0; } to { opacity: 1; }
    }
    @keyframes spin {
      from { transform: rotate(0deg); } to { transform: rotate(360deg); }
    }
    @keyframes scrollPulse {
      0%, 100% { opacity: 0.35; transform: scaleY(1); }
      50%       { opacity: 1;    transform: scaleY(1.12); }
    }

    .reveal {
      opacity: 0;
      transform: translateY(26px);
      transition: opacity 0.75s ease, transform 0.75s ease;
    }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    @media (max-width: 600px) {
      .nav-boxes { padding: 0 20px 80px; }
      .nav-box { padding: 28px 24px; }
      .nav-box-title { font-size: 30px; }
      footer { flex-direction: column; gap: 10px; }
    }
  </style>
</head>
<body>

  <div class="top-rule"></div>

  <!-- HERO -->
  <div class="hero">

    <div class="avatar-wrap">
      <div class="avatar-ring"></div>
      <div class="avatar-ring-bg"></div>
      <div class="avatar">
        <!-- To add your photo, replace the div below with:
             <img src="photo.jpg" alt="Jack Foster"> -->
        <div class="avatar-placeholder">JF</div>
      </div>
    </div>

    <h1 class="hero-name">Jack <em>Foster</em></h1>
    <p class="hero-school">Sixth Form &nbsp;·&nbsp; [Your School] &nbsp;·&nbsp; A-Levels</p>
    <a href="mailto:your@email.com" class="hero-email">your@email.com</a>

    <div class="scroll-hint">
      <span>Scroll</span>
      <div class="scroll-line"></div>
    </div>

  </div>

  <!-- BIO -->
  <div class="bio-section reveal">
    <div class="section-rule"></div>
    <p class="bio-text">
      I'm a sixth form student with a passion for <strong>engineering and motorsport</strong>,
      working towards a career in <strong>Formula 1</strong>. Outside the classroom I build
      things — robotics competition entries, design projects, and anything else that involves
      figuring out how stuff works. This site is where I document it all.
    </p>
  </div>

  <!-- NAV BOXES -->
  <div class="nav-boxes">

    <a href="links.html" class="nav-box reveal">
      <div class="corner-tl"></div>
      <div class="corner-br"></div>
      <div class="nav-box-inner">
        <div>
          <div class="nav-box-label">Find me elsewhere</div>
          <div class="nav-box-title">Links</div>
          <div class="nav-box-desc">LinkedIn · Instagram · GitHub &amp; more</div>
        </div>
        <div class="nav-box-arrow">→</div>
      </div>
    </a>

    <a href="projects.html" class="nav-box reveal">
      <div class="corner-tl"></div>
      <div class="corner-br"></div>
      <div class="nav-box-inner">
        <div>
          <div class="nav-box-label">What I've been building</div>
          <div class="nav-box-title">Projects</div>
          <div class="nav-box-desc">Engineering work, competition entries &amp; school projects</div>
        </div>
        <div class="nav-box-arrow">→</div>
      </div>
    </a>

  </div>

  <!-- FOOTER -->
  <footer>
    <p>Jack Foster</p>
    <div class="footer-line"></div>
    <p>Built from scratch</p>
  </footer>

  <script>
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('visible');
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.12 });
    reveals.forEach(el => observer.observe(el));
  </script>

</body>
</html>
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.12 });
    reveals.forEach(el => observer.observe(el));
  </script>

</body>
</html>
