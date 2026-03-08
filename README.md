<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>TORNADO</title>

  <link rel="icon" type="image/jpeg" href="assets/logo-tornado.png">

  <!-- Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

  <!-- Swiper -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css"/>

  <style>
    :root{
      --container: 1180px;
      --bg:#ffffff;
      --soft:#f5f7fb;
      --line:#e5e7eb;

      --text:#0f172a;
      --muted:#64748b;

      --blue-900:#0b1f3a;
      --blue-800:#0f2c53;
      --blue-700:#153b6f;
      --blue-600:#1d4ed8;
      --cyan-500:#06b6d4;

      --shadow: 0 18px 45px rgba(15, 23, 42, .10);
      --shadow2: 0 10px 30px rgba(15, 23, 42, .08);
      --radius: 16px;

      --t: .22s ease;
    }

    *{box-sizing:border-box;margin:0;padding:0}
    html{scroll-behavior:smooth}
    body{
      font-family: sans-serif; /* ✅ REQUIRED */
      color:var(--text);
      background:var(--bg);
      line-height:1.6;
    }
    a{color:inherit;text-decoration:none}
    img{max-width:100%;display:block}
    .container{max-width:var(--container); margin:0 auto; padding:0 16px;}
    .section{padding:84px 0;}
    .soft{background:var(--soft);}
    .grid{display:grid; gap:18px;}

    .btn{
      display:inline-flex; align-items:center; gap:10px;
      border:1px solid transparent;
      padding:12px 16px; border-radius:12px;
      font-weight:700; cursor:pointer;
      transition: transform var(--t), box-shadow var(--t), background var(--t), border-color var(--t), color var(--t);
      user-select:none;
    }
    .btn:active{transform:translateY(1px)}
    .btn-primary{background:var(--blue-600); color:#fff; box-shadow:0 14px 28px rgba(29,78,216,.24);}
    .btn-primary:hover{transform:translateY(-2px); box-shadow:0 18px 34px rgba(29,78,216,.28);}
    .btn-ghost{background:rgba(255,255,255,.10); border-color:rgba(255,255,255,.25); color:#fff;}
    .btn-ghost:hover{background:rgba(255,255,255,.14); transform:translateY(-2px);}

    .pill{
      display:inline-flex; gap:8px; align-items:center;
      padding:8px 12px;
      border-radius:999px;
      background:rgba(6,182,212,.12);
      color:#0b5160;
      border:1px solid rgba(6,182,212,.22);
      font-size:13px;
      font-weight:700;
    }
    .kicker{color:var(--muted); font-size:14px;}
    .h2{
      font-size:34px;
      line-height:1.2;
      letter-spacing:-.5px;
    }
    .lead{color:var(--muted); margin-top:10px;}
    .card{
      background:#fff;
      border:1px solid var(--line);
      border-radius:var(--radius);
      box-shadow: var(--shadow2);
      overflow:hidden;
    }
    .card-pad{padding:18px;}
    .hover-up{transition: transform var(--t), box-shadow var(--t), border-color var(--t);}
    .hover-up:hover{
      transform: translateY(-6px);
      box-shadow: var(--shadow);
      border-color: rgba(29,78,216,.20);
    }

    /* ===== Topbar ===== */
    .topbar{
      background: linear-gradient(90deg, var(--blue-900), var(--blue-700));
      color:#eaf2ff;
      font-size:13px;
      padding:8px 0;
    }
    .topbar .row{
      display:flex; align-items:center; justify-content:space-between;
      gap:12px;
    }
    .topbar .left, .topbar .right{
      display:flex; align-items:center; gap:14px; flex-wrap:wrap;
    }
    .topbar a{opacity:.95}
    .topbar a:hover{opacity:1; text-decoration:underline}

    /* ===== Header ===== */
    header.site-header{
      position: sticky;
      top:0;
      z-index:999;
      backdrop-filter: blur(10px);
      background: rgba(255,255,255,.78);
      border-bottom: 1px solid rgba(229,231,235,.65);
      transition: box-shadow var(--t), background var(--t);
    }
    header.site-header.scrolled{
      background: rgba(255,255,255,.92);
      box-shadow: 0 10px 28px rgba(15,23,42,.08);
    }
    .navwrap{
      display:flex; align-items:center; justify-content:space-between;
      padding:14px 0;
      gap:14px;
    }

    .brand{
      display:flex; align-items:center; gap:10px;
      font-weight:900;
      letter-spacing:.5px;
      color:var(--blue-900);
      min-width: 140px;
    }
    .brand-logo{
      width:44px; height:44px;
      object-fit:contain;
      border-radius:10px;
      background:#fff;
      padding:4px;
      border:1px solid rgba(229,231,235,.85);
    }
    .brand-text{font-weight:900;}

    nav.main-nav{
      display:flex; align-items:center; gap:16px;
    }
    nav.main-nav a{
      font-weight:700;
      color:#1f2a44;
      padding:10px 10px;
      border-radius:10px;
      transition: background var(--t), color var(--t), transform var(--t);
      white-space:nowrap;
    }
    nav.main-nav a:hover{
      background: rgba(29,78,216,.08);
      color: var(--blue-600);
      transform: translateY(-1px);
    }
    nav.main-nav a.active{
      background: rgba(29,78,216,.12);
      color: var(--blue-600);
    }

    .actions{display:flex; align-items:center; gap:10px;}
    .search{
      display:flex; align-items:center; gap:8px;
      background:#fff;
      border:1px solid var(--line);
      border-radius:12px;
      padding:10px 12px;
      box-shadow: 0 10px 22px rgba(15,23,42,.06);
      min-width: 270px;
    }
    .search i{color:#94a3b8}
    .search input{
      border:none; outline:none; width:100%;
      font-family:inherit; font-size:14px;
      color:var(--text);
    }
    .hamburger{
      display:none;
      width:44px; height:44px;
      border-radius:12px;
      border:1px solid var(--line);
      background:#fff;
      box-shadow: 0 10px 22px rgba(15,23,42,.06);
      cursor:pointer;
    }

    .mobile-panel{display:none; padding:12px 0 16px;}
    .mobile-panel .mnav{display:grid; gap:8px; padding:10px 0 0;}
    .mobile-panel .mnav a{
      padding:12px 12px;
      border:1px solid var(--line);
      background:#fff;
      border-radius:12px;
      font-weight:700;
    }
    .mobile-panel .mnav a:hover{border-color: rgba(29,78,216,.25)}
    .mobile-panel .msearch{margin-top:10px;}

    /* ===== HERO SLIDER (moving board + slide-in text) ===== */
    .hero.hero-swiper{
      position:relative;
      padding:0;
      min-height: 520px;
      overflow:hidden;
      color:#fff;
    }
    .hero-slide{
      position:relative;
      min-height: 520px;
      display:flex;
      align-items:center;
    }
    .hero-bg{
      position:absolute;
      inset:0;
      background-size:cover;
      background-position:center;
      transform: scale(1.08);
    }
    .hero-slide::after{
      content:"";
      position:absolute;
      inset:0;
      background: linear-gradient(90deg, rgba(11,31,58,.88), rgba(11,31,58,.45), rgba(11,31,58,.10));
    }
    .hero-inner{
      position:relative;
      z-index:2;
      max-width: 660px;
      padding: 80px 0;
    }
    .hero-small{
      font-size:12px;
      letter-spacing:.18em;
      opacity:.88;
      margin-bottom:10px;
      text-transform:uppercase;
    }
    .hero-title{
      font-size:52px;
      line-height:1.06;
      font-weight:900;
      letter-spacing:-1px;
    }
    .hero-desc{
      margin-top:14px;
      max-width: 56ch;
      opacity:.86;
    }
    .hero-actions{
      margin-top:22px;
      display:flex;
      gap:12px;
      flex-wrap:wrap;
      align-items:center;
    }

    /* text slide-in */
    .hero-anim{
      opacity:0;
      transform: translateX(-40px);
      transition: opacity .55s ease, transform .55s ease;
    }
    .animate-on-slide.is-animate .hero-anim{
      opacity:1;
      transform: translateX(0);
    }

    /* moving background (Ken Burns) */
    @keyframes kenburnsMove{
      from { transform: scale(1.08) translateX(0px); }
      to   { transform: scale(1.15) translateX(-30px); }
    }
    .swiper-slide-active .hero-bg{
      animation: kenburnsMove 7.5s ease-in-out both;
    }

    /* Right vertical dots */
    .hero-pagination{
      position:absolute;
      right:22px;
      top:50%;
      transform: translateY(-50%);
      z-index:3;
      display:flex;
      flex-direction:column;
      gap:10px;
    }
    .hero-pagination .swiper-pagination-bullet{
      width:34px;
      height:34px;
      border-radius:999px;
      opacity:1;
      background: rgba(255,255,255,.18);
      border:1px solid rgba(255,255,255,.25);
      position:relative;
    }
    .hero-pagination .swiper-pagination-bullet::after{
      content:"";
      position:absolute;
      inset:10px;
      border-radius:999px;
      background: rgba(255,255,255,.35);
      opacity:.65;
    }
    .hero-pagination .swiper-pagination-bullet-active{
      background: rgba(29,78,216,.85);
      border-color: rgba(29,78,216,.95);
    }
    .hero-pagination .swiper-pagination-bullet-active::after{
      background:#fff;
      opacity:1;
    }

    /* ===== About ===== */
    .about-grid{grid-template-columns: 1fr 1fr; align-items:center; gap:22px;}
    .about-visual{
      border-radius: 22px;
      overflow:hidden;
      position:relative;
      box-shadow: var(--shadow);
      border: 1px solid rgba(229,231,235,.8);
      background:
        linear-gradient(120deg, rgba(29,78,216,.10), rgba(6,182,212,.08)),
        url("https://images.unsplash.com/photo-1550751827-4bd374c3f58b?auto=format&fit=crop&w=2000&q=70");
      background-size: cover;
      background-position:center;
      min-height: 340px;
    }
    .about-visual .chip{
      position:absolute; left:16px; bottom:16px;
      padding:12px 14px;
      border-radius: 16px;
      background: rgba(255,255,255,.92);
      border:1px solid rgba(229,231,235,.8);
      box-shadow: var(--shadow2);
      display:flex; gap:10px; align-items:center;
      font-weight:800;
    }
    .about-visual .chip i{color: var(--blue-600)}
    .bullets{margin-top:16px; display:grid; gap:10px;}
    .bullets .b{display:flex; gap:10px; align-items:flex-start; color:var(--muted);}
    .bullets .b i{margin-top:3px; color: var(--blue-600);}

    /* ===== Services ===== */
    .services-grid{grid-template-columns: repeat(3, 1fr); margin-top:18px;}
    .service .icon{
      width:48px; height:48px;
      border-radius:16px;
      display:grid; place-items:center;
      background: rgba(29,78,216,.10);
      border:1px solid rgba(29,78,216,.14);
      color: var(--blue-600);
      margin-bottom:12px;
      font-size:18px;
    }
    .service h3{font-size:18px; line-height:1.25}
    .service p{color: var(--muted); margin-top:8px; font-size:14px}
    .service a.more{
      display:inline-flex; align-items:center; gap:8px;
      margin-top:12px;
      color: var(--blue-600);
      font-weight:800;
      font-size:14px;
    }

    /* ===== Projects slider ===== */
    .projects-head{
      display:flex; align-items:flex-end; justify-content:space-between; gap:16px;
      margin-bottom:14px; flex-wrap:wrap;
    }
    .swiper.projects{padding: 8px 4px 26px;}
    .project-card{
      border-radius: 22px;
      overflow:hidden;
      border:1px solid rgba(229,231,235,.85);
      box-shadow: var(--shadow2);
      background:#fff;
    }
    .project-card .thumb{
      height: 210px;
      background-size: cover;
      background-position:center;
      position:relative;
    }
    .project-card .thumb::after{
      content:"";
      position:absolute; inset:0;
      background: linear-gradient(180deg, transparent, rgba(15,23,42,.55));
      opacity:.92;
    }
    .project-card .tag{
      position:absolute;
      left:14px; top:14px;
      padding:7px 10px;
      border-radius:999px;
      background: rgba(255,255,255,.90);
      border:1px solid rgba(229,231,235,.8);
      font-size:12px;
      font-weight:800;
      color: var(--blue-900);
      z-index:2;
    }
    .project-card .meta{padding:14px 14px 16px;}
    .project-card h4{font-size:16px; line-height:1.25; margin-bottom:8px;}
    .project-card p{color:var(--muted); font-size:13px;}

    .swiper-nav{display:flex; gap:10px; align-items:center;}
    .navbtn{
      width:44px; height:44px;
      border-radius:14px;
      border:1px solid var(--line);
      background:#fff;
      box-shadow: var(--shadow2);
      display:grid; place-items:center;
      cursor:pointer;
      transition: transform var(--t), box-shadow var(--t), border-color var(--t);
    }
    .navbtn:hover{
      transform: translateY(-2px);
      border-color: rgba(29,78,216,.22);
      box-shadow: var(--shadow);
    }

    /* ===== Pricing ===== */
    .pricing-grid{margin-top:18px; grid-template-columns: repeat(3, 1fr);}
    .price{position:relative;}
    .price .top{padding:18px; border-bottom:1px solid var(--line);}
    .price h3{font-size:18px}
    .price .money{
      font-size:34px;
      font-weight:900;
      letter-spacing:-.5px;
      margin-top:8px;
      color: var(--blue-900);
    }
    .price .money span{font-size:14px; font-weight:700; color: var(--muted);}
    .price ul{
      list-style:none;
      padding:16px 18px 18px;
      display:grid; gap:10px;
      color: var(--muted);
      font-size:14px;
    }
    .price li{display:flex; gap:10px; align-items:flex-start;}
    .price li i{color: var(--blue-600); margin-top:3px}
    .price .act{padding:0 18px 18px;}
    .price.featured{
      border-color: rgba(29,78,216,.22);
      box-shadow: var(--shadow);
      transform: translateY(-6px);
    }
    .ribbon{
      position:absolute;
      right:14px; top:14px;
      padding:7px 10px;
      border-radius:999px;
      background: rgba(29,78,216,.12);
      border:1px solid rgba(29,78,216,.18);
      color: var(--blue-600);
      font-weight:900;
      font-size:12px;
    }

    /* ===== Stats (Counter) ===== */
    .stats-grid{margin-top:18px; grid-template-columns: repeat(4, 1fr);}
    .stat{text-align:center; padding:18px 14px;}
    .circle{
      width:92px; height:92px;
      margin:0 auto 10px;
      border-radius:999px;
      border:8px solid rgba(29,78,216,.15);
      position:relative;
      display:grid; place-items:center;
      background: rgba(6,182,212,.06);
    }
    .circle::after{
      content:"";
      position:absolute; inset:10px;
      border-radius:999px;
      border:2px dashed rgba(6,182,212,.35);
      opacity:.75;
    }
    .stat .num{
      font-size:26px;
      font-weight:900;
      letter-spacing:-.5px;
      color: var(--blue-900);
      position:relative;
      z-index:1;
    }
    .stat p{color: var(--muted); font-size:13px; margin-top:4px;}

    /* ===== Newsletter ===== */
    .newsletter{
      background: linear-gradient(90deg, var(--blue-900), var(--blue-700));
      color:#fff;
      border-radius: 26px;
      padding:26px;
      display:grid;
      grid-template-columns: 1.1fr .9fr;
      gap:16px;
      align-items:center;
      box-shadow: var(--shadow);
      border:1px solid rgba(255,255,255,.10);
      overflow:hidden;
      position:relative;
    }
    .newsletter::before{
      content:"";
      position:absolute;
      right:-120px; top:-120px;
      width:320px; height:320px;
      border-radius:999px;
      background: radial-gradient(circle at 30% 30%, rgba(6,182,212,.55), rgba(6,182,212,0) 65%);
    }
    .newsletter h3{font-size:22px; line-height:1.2; position:relative}
    .newsletter p{color: rgba(255,255,255,.80); margin-top:8px; font-size:14px; position:relative}
    .nform{display:flex; gap:10px; align-items:center; position:relative;}
    .nform input{
      flex:1;
      padding:14px 14px;
      border-radius: 14px;
      border:1px solid rgba(255,255,255,.22);
      background: rgba(255,255,255,.10);
      color:#fff;
      outline:none;
      font-family:inherit;
    }
    .nform input::placeholder{color: rgba(255,255,255,.70)}
    .nform button{
      white-space:nowrap;
      background: #fff;
      color: var(--blue-900);
      border:1px solid rgba(255,255,255,.6);
      box-shadow: 0 14px 28px rgba(0,0,0,.18);
    }
    .nform button:hover{transform: translateY(-2px)}

    /* ===== Footer ===== */
    footer{
      background: #071529;
      color: rgba(255,255,255,.86);
      padding:56px 0 24px;
    }
    .footer-grid{
      display:grid;
      grid-template-columns: 1.2fr 1fr 1fr 1fr;
      gap:18px;
      padding-bottom: 22px;
      border-bottom: 1px solid rgba(255,255,255,.12);
    }
    footer h4{font-size:14px; letter-spacing:.3px; color:#fff; margin-bottom:10px}
    footer p{color: rgba(255,255,255,.72); font-size:13px}
    .f-links{display:grid; gap:8px}
    .f-links a{
      color: rgba(255,255,255,.74);
      font-size:13px;
      transition: color var(--t), transform var(--t);
    }
    .f-links a:hover{color:#fff; transform: translateX(2px)}
    .social{margin-top:12px; display:flex; gap:10px; flex-wrap:wrap;}
    .social a{
      width:40px; height:40px;
      border-radius:14px;
      display:grid; place-items:center;
      border:1px solid rgba(255,255,255,.14);
      background: rgba(255,255,255,.06);
      color:#fff;
      transition: transform var(--t), background var(--t), border-color var(--t);
    }
    .social a:hover{
      transform: translateY(-2px);
      background: rgba(255,255,255,.10);
      border-color: rgba(255,255,255,.22);
    }
    .copyright{
      padding-top:16px;
      color: rgba(255,255,255,.60);
      font-size:12px;
      display:flex; justify-content:space-between; gap:10px;
      flex-wrap:wrap;
    }

    /* ===== Back to top ===== */
    .toTop{
      position:fixed;
      right:18px; bottom:18px;
      width:48px; height:48px;
      border-radius:16px;
      border:1px solid rgba(229,231,235,.9);
      background:#fff;
      box-shadow: var(--shadow2);
      display:grid; place-items:center;
      cursor:pointer;
      opacity:0;
      transform: translateY(10px);
      pointer-events:none;
      transition: opacity var(--t), transform var(--t);
      z-index:1200;
    }
    .toTop.show{opacity:1; transform: translateY(0); pointer-events:auto;}
    .toTop i{color: var(--blue-600)}

    /* ===== Responsive ===== */
    @media (max-width: 1024px){
      .search{min-width: 210px}
      .hero-title{font-size:44px}
      .services-grid{grid-template-columns: repeat(2, 1fr)}
      .pricing-grid{grid-template-columns: repeat(2, 1fr)}
      .stats-grid{grid-template-columns: repeat(2, 1fr)}
      .footer-grid{grid-template-columns: 1.2fr 1fr 1fr}
    }
    @media (max-width: 860px){
      nav.main-nav{display:none}
      .search{display:none}
      .hamburger{display:grid; place-items:center}
      .mobile-panel{display:block}
      .about-grid{grid-template-columns: 1fr}
      .newsletter{grid-template-columns: 1fr}
      .pricing-grid{grid-template-columns: 1fr}
      .services-grid{grid-template-columns: 1fr}
      .footer-grid{grid-template-columns: 1fr 1fr}
      .hero-title{font-size:40px}
      .hero-inner{padding:70px 0}
    }
    @media (max-width: 520px){
      .topbar .row{justify-content:center}
      .topbar .right{display:none}
      .hero-title{font-size:32px}
      .footer-grid{grid-template-columns: 1fr}
      .copyright{justify-content:center}
      .hero-pagination{right:10px}
    }
  </style>
</head>
<body>

  <!-- Topbar -->
  <div class="topbar">
    <div class="container">
      <div class="row">
        <div class="left">
          <span><i class="fa-solid fa-phone"></i> +84 900 000 000</span>
          <span><i class="fa-solid fa-envelope"></i> contact@tornado.vn</span>
        </div>
        <div class="right">
          <a href="#projects"><i class="fa-solid fa-diagram-project"></i> Projects</a>
          <a href="#contact"><i class="fa-solid fa-headset"></i> Support</a>
        </div>
      </div>
    </div>
  </div>

  <!-- Header -->
  <header class="site-header" id="top">
    <div class="container">
      <div class="navwrap">
        <!-- ✅ Logo from Google Drive (direct link) -->
        <a class="brand" href="#top" aria-label="TORNADO Home">
          <img class="brand-logo"
               src="assets/logo-tornado.jpg"
               alt="TORNADO logo"
               onerror="this.style.display='none'; this.nextElementSibling.textContent='TORNADO';" />
          <span class="brand-text"></span>
        </a>

        <nav class="main-nav" aria-label="Main navigation">
          <a href="#home" class="active">Home</a>
          <a href="#about">About</a>
          <a href="#services">Solutions</a>
          <a href="#projects">Projects</a>
          <a href="#pricing">Pricing</a>
          <a href="#stats">Stats</a>
          <a href="#contact">Contact</a>
        </nav>

        <div class="actions">
          <div class="search" role="search">
            <i class="fa-solid fa-magnifying-glass"></i>
            <input id="searchInput" type="search" placeholder="Quick search: projects, pricing, contact..." aria-label="Search"/>
          </div>
          <a class="btn btn-primary" href="#contact"><i class="fa-solid fa-bolt"></i> Get a Quote</a>
          <button class="hamburger" id="hamburger" aria-label="Open menu" aria-expanded="false">
            <i class="fa-solid fa-bars"></i>
          </button>
        </div>
      </div>

      <!-- Mobile panel -->
      <div class="mobile-panel" id="mobilePanel" style="display:none;">
        <div class="search msearch" role="search">
          <i class="fa-solid fa-magnifying-glass"></i>
          <input id="searchInputMobile" type="search" placeholder="Quick search..." aria-label="Search mobile"/>
        </div>
        <div class="mnav" aria-label="Mobile navigation">
          <a href="#home">Home</a>
          <a href="#about">About</a>
          <a href="#services">Solutions</a>
          <a href="#projects">Projects</a>
          <a href="#pricing">Pricing</a>
          <a href="#stats">Stats</a>
          <a href="#contact">Contact</a>
        </div>
      </div>
    </div>
  </header>

  <!-- ✅ HERO (moving background + slide-in text like video) -->
  <section class="hero hero-swiper" id="home">
    <div class="swiper" id="heroSwiper">
      <div class="swiper-wrapper">

        <div class="swiper-slide hero-slide">
          <div class="hero-bg" style="background-image:url('https://images.unsplash.com/photo-1551434678-e076c223a692?auto=format&fit=crop&w=2400&q=70');"></div>
          <div class="container">
            <div class="hero-inner animate-on-slide">
              <div class="hero-small hero-anim" style="transition-delay:.05s;">BEST IT COMPANY</div>
              <h1 class="hero-title hero-anim" style="transition-delay:.15s;">
                Best IT Solution<br/>Agency For Your<br/>Business
              </h1>
              <p class="hero-desc hero-anim" style="transition-delay:.25s;">
                Modern websites, internal systems, and security hardening with clean UI and fast performance.
              </p>
              <div class="hero-actions hero-anim" style="transition-delay:.35s;">
                <a class="btn btn-primary" href="#services"><i class="fa-solid fa-layer-group"></i> View Solutions</a>
                <a class="btn btn-ghost" href="#projects"><i class="fa-solid fa-diagram-project"></i> See Projects</a>
              </div>
            </div>
          </div>
        </div>

        <div class="swiper-slide hero-slide">
          <div class="hero-bg" style="background-image:url('https://images.unsplash.com/photo-1551434678-e076c223a692?auto=format&fit=crop&w=2400&q=70');"></div>
          <div class="container">
            <div class="hero-inner animate-on-slide">
              <div class="hero-small hero-anim" style="transition-delay:.05s;">SECURITY & PERFORMANCE</div>
              <h1 class="hero-title hero-anim" style="transition-delay:.15s;">
                Secure, Fast<br/>Scalable Digital<br/>Infrastructure
              </h1>
              <p class="hero-desc hero-anim" style="transition-delay:.25s;">
                SSL, backups, monitoring, and SEO-friendly structure for real business results.
              </p>
              <div class="hero-actions hero-anim" style="transition-delay:.35s;">
                <a class="btn btn-primary" href="#pricing"><i class="fa-solid fa-tags"></i> View Pricing</a>
                <a class="btn btn-ghost" href="#contact"><i class="fa-solid fa-paper-plane"></i> Contact</a>
              </div>
            </div>
          </div>
        </div>

        <div class="swiper-slide hero-slide">
          <div class="hero-bg" style="background-image:url('https://images.unsplash.com/photo-1556761175-4b46a572b786?auto=format&fit=crop&w=2400&q=70');"></div>
          <div class="container">
            <div class="hero-inner animate-on-slide">
              <div class="hero-small hero-anim" style="transition-delay:.05s;">BUSINESS READY</div>
              <h1 class="hero-title hero-anim" style="transition-delay:.15s;">
                Build Your<br/>Website Like a<br/>Pro
              </h1>
              <p class="hero-desc hero-anim" style="transition-delay:.25s;">
                Responsive layout, smooth transitions, and sections that match your assignment requirements.
              </p>
              <div class="hero-actions hero-anim" style="transition-delay:.35s;">
                <a class="btn btn-primary" href="#contact"><i class="fa-solid fa-bolt"></i> Get a Quote</a>
                <a class="btn btn-ghost" href="#about"><i class="fa-solid fa-circle-info"></i> About Us</a>
              </div>
            </div>
          </div>
        </div>

      </div>

      <div class="hero-pagination" id="heroPagination"></div>
    </div>
  </section>

  <!-- About -->
  <section class="section" id="about">
    <div class="container">
      <div class="grid about-grid">
        <div>
          <div class="kicker">About us</div>
          <h2 class="h2">Design, deploy, and operate modern systems</h2>
          <p class="lead">
            We focus on solutions that are easy to use, secure, and scalable — from corporate websites to internal dashboards.
          </p>

          <div class="bullets">
            <div class="b"><i class="fa-solid fa-circle-check"></i><span>Modern UI/UX aligned with your brand</span></div>
            <div class="b"><i class="fa-solid fa-circle-check"></i><span>Fast loading, SEO-friendly structure</span></div>
            <div class="b"><i class="fa-solid fa-circle-check"></i><span>Security baseline + advanced options</span></div>
            <div class="b"><i class="fa-solid fa-circle-check"></i><span>Support, updates, and backups</span></div>
          </div>

          <div style="margin-top:18px; display:flex; gap:10px; flex-wrap:wrap;">
            <a class="btn btn-primary" href="#projects"><i class="fa-solid fa-diagram-project"></i> View projects</a>
            <a class="btn" href="#pricing" style="background:#fff; border:1px solid var(--line); box-shadow:var(--shadow2);">
              <i class="fa-solid fa-tags"></i> View pricing
            </a>
          </div>
        </div>

        <div>
          <div class="about-visual" aria-label="Visual">
            <div class="chip">
              <i class="fa-solid fa-award"></i>
              <div>
                <div style="font-size:12px; color:var(--muted); font-weight:800;">Deployment experience</div>
                <div style="font-size:14px;">Web / System / Security</div>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- Services -->
  <section class="section soft" id="services">
    <div class="container">
      <div class="kicker">Solutions</div>
      <div style="display:flex; justify-content:space-between; gap:16px; flex-wrap:wrap; align-items:flex-end;">
        <h2 class="h2">Featured services</h2>
        <p class="lead" style="max-width:60ch;margin:0;">
          Flexible packages based on your goals: branding, lead generation, or internal operations.
        </p>
      </div>

      <div class="grid services-grid">
        <div class="card card-pad hover-up service">
          <div class="icon"><i class="fa-solid fa-palette"></i></div>
          <h3>Website Design</h3>
          <p>Landing pages and corporate sites with modern UI, mobile-first layout, speed optimization.</p>
          <a class="more" href="#contact">Talk to us <i class="fa-solid fa-arrow-right"></i></a>
        </div>

        <div class="card card-pad hover-up service">
          <div class="icon"><i class="fa-solid fa-shield"></i></div>
          <h3>Security & Backup</h3>
          <p>SSL, WAF baseline, server hardening, scheduled backups, and monitoring.</p>
          <a class="more" href="#contact">Learn more <i class="fa-solid fa-arrow-right"></i></a>
        </div>

        <div class="card card-pad hover-up service">
          <div class="icon"><i class="fa-solid fa-chart-line"></i></div>
          <h3>SEO & Tracking</h3>
          <p>Technical SEO, Search Console, Analytics, conversion tracking, performance reporting.</p>
          <a class="more" href="#contact">Get a quote <i class="fa-solid fa-arrow-right"></i></a>
        </div>
      </div>
    </div>
  </section>

  <!-- Projects Slider -->
  <section class="section" id="projects">
    <div class="container">
      <div class="projects-head">
        <div>
          <div class="kicker">Projects</div>
          <h2 class="h2">Selected work</h2>
          <p class="lead" style="max-width:70ch">This is your “slider section”. Replace images/text as needed.</p>
        </div>
        <div class="swiper-nav">
          <button class="navbtn" id="prevBtn" aria-label="Previous"><i class="fa-solid fa-chevron-left"></i></button>
          <button class="navbtn" id="nextBtn" aria-label="Next"><i class="fa-solid fa-chevron-right"></i></button>
        </div>
      </div>

      <div class="swiper projects" id="projectSwiper">
        <div class="swiper-wrapper">
          <div class="swiper-slide">
            <div class="project-card hover-up">
              <div class="thumb" style="background-image:url('https://images.unsplash.com/photo-1556155092-8707de31f9c4?auto=format&fit=crop&w=1600&q=70');">
                <span class="tag">Web</span>
              </div>
              <div class="meta">
                <h4>Corporate website</h4>
                <p>Modern UI, optimized speed, clean SEO-ready structure.</p>
              </div>
            </div>
          </div>

          <div class="swiper-slide">
            <div class="project-card hover-up">
              <div class="thumb" style="background-image:url('https://images.unsplash.com/photo-1556761175-4b46a572b786?auto=format&fit=crop&w=1600&q=70');">
                <span class="tag">System</span>
              </div>
              <div class="meta">
                <h4>Internal dashboard</h4>
                <p>Reports, role-based access, exports and management.</p>
              </div>
            </div>
          </div>

          <div class="swiper-slide">
            <div class="project-card hover-up">
              <div class="thumb" style="background-image:url('https://images.unsplash.com/photo-1563986768609-322da13575f3?auto=format&fit=crop&w=1600&q=70');">
                <span class="tag">Security</span>
              </div>
              <div class="meta">
                <h4>Security operations</h4>
                <p>SSL, backups, hardening, monitoring alerts.</p>
              </div>
            </div>
          </div>

          <div class="swiper-slide">
            <div class="project-card hover-up">
              <div class="thumb" style="background-image:url('https://images.unsplash.com/photo-1545239351-1141bd82e8a6?auto=format&fit=crop&w=1600&q=70');">
                <span class="tag">Brand</span>
              </div>
              <div class="meta">
                <h4>Campaign landing</h4>
                <p>Lead forms, tracking, CTAs, conversion optimization.</p>
              </div>
            </div>
          </div>

          <div class="swiper-slide">
            <div class="project-card hover-up">
              <div class="thumb" style="background-image:url('https://images.unsplash.com/photo-1555066931-4365d14bab8c?auto=format&fit=crop&w=1600&q=70');">
                <span class="tag">Dev</span>
              </div>
              <div class="meta">
                <h4>API integration</h4>
                <p>Auth, CRM, forms, webhooks, data syncing.</p>
              </div>
            </div>
          </div>
        </div>

        <div class="swiper-pagination"></div>
      </div>
    </div>
  </section>

  <!-- Pricing -->
  <section class="section soft" id="pricing">
    <div class="container">
      <div class="kicker">Pricing</div>
      <div style="display:flex; justify-content:space-between; gap:16px; flex-wrap:wrap; align-items:flex-end;">
        <h2 class="h2">Choose the right plan</h2>
        <p class="lead" style="max-width:70ch; margin:0;">
          3-column pricing section. Update prices and features to match your homework.
        </p>
      </div>

      <div class="grid pricing-grid">
        <div class="card price hover-up">
          <div class="top">
            <h3>Starter</h3>
            <div class="money">$99 <span>/ project</span></div>
            <div class="kicker">Best for a simple landing page</div>
          </div>
          <ul>
            <li><i class="fa-solid fa-check"></i> 1 landing page</li>
            <li><i class="fa-solid fa-check"></i> Responsive layout</li>
            <li><i class="fa-solid fa-check"></i> Basic optimization</li>
            <li><i class="fa-solid fa-check"></i> 1 month warranty</li>
          </ul>
          <div class="act">
            <a class="btn btn-primary" href="#contact" style="width:100%; justify-content:center;">
              <i class="fa-solid fa-cart-shopping"></i> Select plan
            </a>
          </div>
        </div>

        <div class="card price featured">
          <span class="ribbon">Popular</span>
          <div class="top">
            <h3>Standard</h3>
            <div class="money">$249 <span>/ project</span></div>
            <div class="kicker">Corporate website package</div>
          </div>
          <ul>
            <li><i class="fa-solid fa-check"></i> 5 pages (Home / About / Projects / Pricing / Contact)</li>
            <li><i class="fa-solid fa-check"></i> Hero slider + animations</li>
            <li><i class="fa-solid fa-check"></i> Basic technical SEO</li>
            <li><i class="fa-solid fa-check"></i> 6 months warranty</li>
          </ul>
          <div class="act">
            <a class="btn btn-primary" href="#contact" style="width:100%; justify-content:center;">
              <i class="fa-solid fa-bolt"></i> Select plan
            </a>
          </div>
        </div>

        <div class="card price hover-up">
          <div class="top">
            <h3>Premium</h3>
            <div class="money">$499 <span>/ project</span></div>
            <div class="kicker">Dashboard / integrations</div>
          </div>
          <ul>
            <li><i class="fa-solid fa-check"></i> Advanced UI/UX</li>
            <li><i class="fa-solid fa-check"></i> Basic admin panel</li>
            <li><i class="fa-solid fa-check"></i> API integrations</li>
            <li><i class="fa-solid fa-check"></i> 12 months warranty</li>
          </ul>
          <div class="act">
            <a class="btn btn-primary" href="#contact" style="width:100%; justify-content:center;">
              <i class="fa-solid fa-star"></i> Select plan
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Stats (Counter) -->
  <section class="section" id="stats">
    <div class="container">
      <div class="kicker">Stats</div>
      <div style="display:flex; justify-content:space-between; gap:16px; flex-wrap:wrap; align-items:flex-end;">
        <h2 class="h2">Results & numbers</h2>
        <p class="lead" style="max-width:70ch;margin:0;">
          This section uses a counter animation when it becomes visible.
        </p>
      </div>

      <div class="grid stats-grid" id="statsGrid">
        <div class="card stat hover-up">
          <div class="circle"><div class="num"><span class="count" data-target="25">0</span>+</div></div>
          <p>Projects delivered</p>
        </div>
        <div class="card stat hover-up">
          <div class="circle"><div class="num"><span class="count" data-target="97">0</span>%</div></div>
          <p>Client satisfaction</p>
        </div>
        <div class="card stat hover-up">
          <div class="circle"><div class="num"><span class="count" data-target="8">0</span>K</div></div>
          <p>Monthly visits</p>
        </div>
        <div class="card stat hover-up">
          <div class="circle"><div class="num"><span class="count" data-target="19">0</span>K</div></div>
          <p>Qualified leads</p>
        </div>
      </div>

      <!-- Newsletter -->
      <div class="section" style="padding:54px 0 0;">
        <div class="newsletter">
          <div>
            <h3>Get updates & templates</h3>
            <p>Leave your email to receive a checklist and sample templates.</p>
          </div>
          <form class="nform" id="newsletterForm">
            <input type="email" name="email" placeholder="Your email..." required>
            <button class="btn" type="submit"><i class="fa-solid fa-envelope"></i> Subscribe</button>
          </form>
        </div>
      </div>

    </div>
  </section>

  <!-- Contact -->
  <section class="section soft" id="contact">
    <div class="container">
      <div class="kicker">Contact</div>
      <div style="display:flex; justify-content:space-between; gap:16px; flex-wrap:wrap; align-items:flex-end;">
        <h2 class="h2">Request a consultation</h2>
        <p class="lead" style="max-width:70ch;margin:0;">
          Demo form (shows an alert). Connect backend later if you want.
        </p>
      </div>

      <div class="grid" style="grid-template-columns: 1fr 1fr; margin-top:18px;">
        <div class="card card-pad hover-up">
          <h3 style="font-size:18px;">Contact details</h3>
          <p style="color:var(--muted); margin-top:8px;">
            <i class="fa-solid fa-location-dot"></i> Hongkong, Hongkong<br/>
            <i class="fa-solid fa-phone"></i> +852 900 000 000<br/>
            <i class="fa-solid fa-envelope"></i> contact@tornado.hk
          </p>
          <div class="social" style="margin-top:14px;">
            <a href="#" aria-label="Facebook"><i class="fa-brands fa-facebook-f"></i></a>
            <a href="#" aria-label="YouTube"><i class="fa-brands fa-youtube"></i></a>
            <a href="#" aria-label="LinkedIn"><i class="fa-brands fa-linkedin-in"></i></a>
            <a href="#" aria-label="Chat"><i class="fa-solid fa-comment-dots"></i></a>
          </div>
        </div>

        <div class="card card-pad hover-up">
          <h3 style="font-size:18px;">Send a message</h3>
          <form id="contactForm" style="margin-top:10px; display:grid; gap:10px;">
            <div style="display:grid; grid-template-columns: 1fr 1fr; gap:10px;">
              <input required name="name" placeholder="Full name" style="padding:12px 12px; border-radius:12px; border:1px solid var(--line); outline:none; font-family:inherit;">
              <input required name="phone" placeholder="Phone number" style="padding:12px 12px; border-radius:12px; border:1px solid var(--line); outline:none; font-family:inherit;">
            </div>
            <input name="email" placeholder="Email (optional)" style="padding:12px 12px; border-radius:12px; border:1px solid var(--line); outline:none; font-family:inherit;">
            <textarea name="message" rows="4" placeholder="Your message..." style="padding:12px 12px; border-radius:12px; border:1px solid var(--line); outline:none; font-family:inherit; resize:vertical;"></textarea>
            <button class="btn btn-primary" type="submit" style="justify-content:center;">
              <i class="fa-solid fa-paper-plane"></i> Send request
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <div class="container">
      <div class="footer-grid">
        <div>
          <div style="display:flex; align-items:center; gap:10px;">
            <img
              src="https://drive.google.com/uc?export=view&id=11zybCu-qj3NwTdReoXTivMelmX3JmGBl"
              alt="TORNADO logo"
              style="width:34px;height:34px;border-radius:10px;background:#fff;padding:3px;border:1px solid rgba(255,255,255,.14);"
              onerror="this.style.display='none';"
            />
            <div style="font-weight:900; color:#fff; letter-spacing:.4px;">TORNADO</div>
          </div>
          <p style="margin-top:10px;">
            Full one-page homework template: header, hero slider, projects slider, pricing, counter, newsletter, contact, footer.
          </p>
        </div>

        <div>
          <h4>Links</h4>
          <div class="f-links">
            <a href="#about">About</a>
            <a href="#services">Solutions</a>
            <a href="#projects">Projects</a>
            <a href="#pricing">Pricing</a>
          </div>
        </div>

        <div>
          <h4>Resources</h4>
          <div class="f-links">
            <a href="#stats">Stats</a>
            <a href="#contact">Support</a>
            <a href="#top">Back to top</a>
          </div>
        </div>

        <div>
          <h4>Contact</h4>
          <div class="f-links">
            <a href="#"><i class="fa-solid fa-location-dot"></i> Hanoi, Vietnam</a>
            <a href="#"><i class="fa-solid fa-phone"></i> +84 900 000 000</a>
            <a href="#"><i class="fa-solid fa-envelope"></i> contact@tornado.vn</a>
          </div>
        </div>
      </div>

      <div class="copyright">
        <span>© <span id="year"></span> TORNADO. All rights reserved.</span>
        <span>Single file • HTML + CSS + JS</span>
      </div>
    </div>
  </footer>

  <!-- Back to top -->
  <button class="toTop" id="toTop" aria-label="Back to top">
    <i class="fa-solid fa-arrow-up"></i>
  </button>

  <!-- Scripts -->
  <script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>

  <script>
    // Header shadow + back-to-top
    const header = document.querySelector("header.site-header");
    const toTop = document.getElementById("toTop");
    const onScroll = () => {
      const y = window.scrollY || document.documentElement.scrollTop;
      header.classList.toggle("scrolled", y > 10);
      toTop.classList.toggle("show", y > 420);
    };
    window.addEventListener("scroll", onScroll);
    onScroll();
    toTop.addEventListener("click", () => window.scrollTo({top: 0, behavior: "smooth"}));

    // Mobile menu
    const hamburger = document.getElementById("hamburger");
    const mobilePanel = document.getElementById("mobilePanel");
    let mobileOpen = false;

    hamburger.addEventListener("click", () => {
      mobileOpen = !mobileOpen;
      mobilePanel.style.display = mobileOpen ? "block" : "none";
      hamburger.setAttribute("aria-expanded", String(mobileOpen));
      hamburger.innerHTML = mobileOpen ? '<i class="fa-solid fa-xmark"></i>' : '<i class="fa-solid fa-bars"></i>';
    });

    mobilePanel.addEventListener("click", (e) => {
      const a = e.target.closest("a");
      if(!a) return;
      mobileOpen = false;
      mobilePanel.style.display = "none";
      hamburger.setAttribute("aria-expanded", "false");
      hamburger.innerHTML = '<i class="fa-solid fa-bars"></i>';
    });

    // Active nav highlight
    const navLinks = Array.from(document.querySelectorAll("nav.main-nav a"));
    const sections = ["home","about","services","projects","pricing","stats","contact"].map(id => document.getElementById(id));
    const setActiveLink = () => {
      const y = window.scrollY + 140;
      let currentId = "home";
      for(const s of sections){
        if(!s) continue;
        const top = s.offsetTop;
        const bottom = top + s.offsetHeight;
        if(y >= top && y < bottom){ currentId = s.id; break; }
      }
      navLinks.forEach(a => {
        const href = a.getAttribute("href").replace("#","");
        a.classList.toggle("active", href === currentId);
      });
    };
    window.addEventListener("scroll", setActiveLink);
    setActiveLink();

    // Search demo (scroll to section)
    function handleSearch(value){
      const q = (value || "").toLowerCase().trim();
      if(!q) return;
      const map = [
        { keys:["home","hero"], id:"home" },
        { keys:["about"], id:"about" },
        { keys:["solutions","services","service"], id:"services" },
        { keys:["projects","project"], id:"projects" },
        { keys:["price","pricing","plan"], id:"pricing" },
        { keys:["stats","numbers","counter"], id:"stats" },
        { keys:["contact","form"], id:"contact" }
      ];
      const found = map.find(m => m.keys.some(k => q.includes(k)));
      if(found){
        document.getElementById(found.id)?.scrollIntoView({behavior:"smooth", block:"start"});
      }else{
        alert("No matching section found. Try: projects, pricing, stats, contact...");
      }
    }
    const searchInput = document.getElementById("searchInput");
    const searchInputMobile = document.getElementById("searchInputMobile");
    [searchInput, searchInputMobile].forEach(inp => {
      if(!inp) return;
      inp.addEventListener("keydown", (e) => {
        if(e.key === "Enter"){
          e.preventDefault();
          handleSearch(inp.value);
        }
      });
    });

    // ✅ HERO Swiper (fade) + slide-in text effect
    const heroSwiper = new Swiper("#heroSwiper", {
      loop: true,
      effect: "fade",
      fadeEffect: { crossFade: true },
      speed: 900,
      autoplay: { delay: 4200, disableOnInteraction: false },
      pagination: { el: "#heroPagination", clickable: true }
    });

    function animateHeroText() {
      document.querySelectorAll(".animate-on-slide").forEach(el => el.classList.remove("is-animate"));
      const active = document.querySelector("#heroSwiper .swiper-slide-active .animate-on-slide");
      if(!active) return;
      void active.offsetWidth; // restart animation
      active.classList.add("is-animate");
    }
    heroSwiper.on("init", animateHeroText);
    heroSwiper.on("slideChangeTransitionStart", animateHeroText);
    animateHeroText();

    // Projects slider
    new Swiper("#projectSwiper", {
      slidesPerView: 1,
      spaceBetween: 16,
      loop: true,
      pagination: { el: "#projectSwiper .swiper-pagination", clickable: true },
      navigation: { nextEl: "#nextBtn", prevEl: "#prevBtn" },
      breakpoints: {
        640: { slidesPerView: 2 },
        1024: { slidesPerView: 3 }
      }
    });

    // Counter (simple, no library)
    const statsGrid = document.getElementById("statsGrid");
    let counted = false;

    function countUp(el, target, durationMs){
      const start = 0;
      const startTime = performance.now();
      const step = (now) => {
        const p = Math.min(1, (now - startTime) / durationMs);
        const val = Math.floor(start + (target - start) * (p));
        el.textContent = val.toLocaleString();
        if(p < 1) requestAnimationFrame(step);
      };
      requestAnimationFrame(step);
    }

    const io = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if(entry.isIntersecting && !counted){
          counted = true;
          document.querySelectorAll(".count").forEach(el => {
            const target = Number(el.dataset.target || 0);
            countUp(el, target, 1400);
          });
        }
      });
    }, { threshold: 0.35 });

    if(statsGrid) io.observe(statsGrid);

    // Forms demo
    document.getElementById("newsletterForm").addEventListener("submit", (e) => {
      e.preventDefault();
      const email = new FormData(e.target).get("email");
      alert("Subscribed: " + email);
      e.target.reset();
    });

    document.getElementById("contactForm").addEventListener("submit", (e) => {
      e.preventDefault();
      const fd = new FormData(e.target);
      alert(
        "Sent!\n\nName: " + (fd.get("name")||"") +
        "\nPhone: " + (fd.get("phone")||"") +
        "\nEmail: " + (fd.get("email")||"") +
        "\nMessage: " + (fd.get("message")||"")
      );
      e.target.reset();
    });

    // Year
    document.getElementById("year").textContent = new Date().getFullYear();
  </script>
</body>
</html>
