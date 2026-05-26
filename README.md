<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Petek Fuar – Fuar Standı Tasarım ve Uygulama</title>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;700;900&family=Raleway:wght@400;600&display=swap" rel="stylesheet">
<style>
  :root {
    --yellow: #FFD700;
    --gray: #6B6B6B;
    --dark: #1a1a1a;
    --light: #f5f5f5;
    --white: #fff;
    --accent: #E8B800;
  }
  * { margin:0; padding:0; box-sizing:border-box; }
  html { scroll-behavior: smooth; }
  body { font-family:'Raleway',sans-serif; background:#fff; color:#333; }

  /* ===== HEADER ===== */
  header {
    position:fixed; top:0; left:0; right:0; z-index:1000;
    background:rgba(255,255,255,0.97);
    box-shadow:0 2px 20px rgba(0,0,0,0.1);
    display:flex; align-items:center; justify-content:space-between;
    padding:0 40px; height:70px;
  }
  .logo-area { display:flex; align-items:center; gap:12px; cursor:pointer; }
  /* SVG Logo */
  .logo-svg { width:54px; height:44px; }
  .logo-text h1 { font-family:'Montserrat',sans-serif; font-weight:700; font-size:1.5rem; color:#555; letter-spacing:1px; }
  .logo-text p { font-size:0.6rem; color:#888; letter-spacing:2px; text-transform:uppercase; margin-top:-2px; }

  nav { display:flex; gap:30px; align-items:center; }
  nav a {
    font-family:'Montserrat',sans-serif; font-size:0.82rem; font-weight:600;
    color:#555; text-decoration:none; letter-spacing:1px; text-transform:uppercase;
    transition:color .3s; position:relative;
  }
  nav a::after {
    content:''; position:absolute; bottom:-4px; left:0; right:0; height:2px;
    background:var(--yellow); transform:scaleX(0); transition:transform .3s;
  }
  nav a:hover { color:#222; }
  nav a:hover::after { transform:scaleX(1); }

  .header-search { position:relative; }
  .header-search input {
    border:2px solid #e0e0e0; border-radius:25px; padding:7px 35px 7px 15px;
    font-family:'Raleway',sans-serif; font-size:0.82rem; outline:none; width:200px;
    transition:border-color .3s, width .3s;
  }
  .header-search input:focus { border-color:var(--yellow); width:250px; }
  .header-search button {
    position:absolute; right:10px; top:50%; transform:translateY(-50%);
    background:none; border:none; cursor:pointer; color:#888; font-size:1rem;
  }

  /* ===== HERO ===== */
  #hero {
    margin-top:70px; height:calc(100vh - 70px);
    background:linear-gradient(135deg,#1a1a1a 0%,#2d2d2d 50%,#1a1a1a 100%);
    display:flex; align-items:center; justify-content:center;
    text-align:center; position:relative; overflow:hidden;
  }
  .hero-bg-pattern {
    position:absolute; inset:0;
    background-image: repeating-linear-gradient(45deg, transparent, transparent 40px, rgba(255,215,0,0.03) 40px, rgba(255,215,0,0.03) 80px);
  }
  .hero-content { position:relative; z-index:2; }
  .hero-tag {
    display:inline-block; background:var(--yellow); color:#1a1a1a;
    font-family:'Montserrat',sans-serif; font-weight:700; font-size:0.72rem;
    letter-spacing:3px; text-transform:uppercase; padding:6px 20px; border-radius:2px; margin-bottom:25px;
  }
  .hero-content h2 {
    font-family:'Montserrat',sans-serif; font-weight:900; font-size:clamp(2.5rem,6vw,4.5rem);
    color:#fff; line-height:1.1; margin-bottom:20px;
  }
  .hero-content h2 span { color:var(--yellow); }
  .hero-content p { color:#aaa; font-size:1.1rem; max-width:600px; margin:0 auto 35px; line-height:1.7; }
  .btn-primary {
    display:inline-block; background:var(--yellow); color:#1a1a1a;
    font-family:'Montserrat',sans-serif; font-weight:700; font-size:0.85rem;
    letter-spacing:2px; text-transform:uppercase; padding:15px 40px; border-radius:3px;
    text-decoration:none; border:none; cursor:pointer; transition:transform .2s, box-shadow .2s;
  }
  .btn-primary:hover { transform:translateY(-2px); box-shadow:0 8px 25px rgba(255,215,0,0.4); }
  .btn-outline {
    display:inline-block; background:transparent; color:#fff;
    font-family:'Montserrat',sans-serif; font-weight:600; font-size:0.85rem;
    letter-spacing:2px; text-transform:uppercase; padding:14px 35px; border-radius:3px;
    text-decoration:none; border:2px solid rgba(255,255,255,0.3); cursor:pointer;
    margin-left:15px; transition:border-color .3s;
  }
  .btn-outline:hover { border-color:var(--yellow); color:var(--yellow); }

  /* ===== STATS BAR ===== */
  .stats-bar {
    background:var(--yellow); padding:25px 40px;
    display:flex; justify-content:center; gap:80px; flex-wrap:wrap;
  }
  .stat { text-align:center; }
  .stat-num { font-family:'Montserrat',sans-serif; font-weight:900; font-size:2rem; color:#1a1a1a; }
  .stat-label { font-size:0.75rem; font-weight:600; color:#555; letter-spacing:2px; text-transform:uppercase; margin-top:3px; }

  /* ===== SECTION ===== */
  section { padding:90px 40px; }
  .section-header { text-align:center; margin-bottom:60px; }
  .section-tag {
    display:inline-block; color:var(--yellow); font-family:'Montserrat',sans-serif;
    font-weight:700; font-size:0.72rem; letter-spacing:3px; text-transform:uppercase; margin-bottom:15px;
  }
  .section-header h2 {
    font-family:'Montserrat',sans-serif; font-weight:900; font-size:2.5rem; color:#1a1a1a; margin-bottom:15px;
  }
  .section-header p { color:#777; font-size:1rem; max-width:550px; margin:0 auto; line-height:1.7; }

  /* ===== SERVICES ===== */
  #hizmetler { background:#f8f8f8; }
  .services-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(260px,1fr)); gap:25px; max-width:1200px; margin:0 auto; }
  .service-card {
    background:#fff; border-radius:8px; padding:35px 30px;
    border-bottom:4px solid transparent; transition:all .3s; cursor:default;
    box-shadow:0 2px 15px rgba(0,0,0,0.06);
  }
  .service-card:hover { border-bottom-color:var(--yellow); transform:translateY(-5px); box-shadow:0 10px 30px rgba(0,0,0,0.12); }
  .service-icon { font-size:2.5rem; margin-bottom:20px; }
  .service-card h3 { font-family:'Montserrat',sans-serif; font-weight:700; font-size:1.1rem; color:#1a1a1a; margin-bottom:12px; }
  .service-card p { color:#777; font-size:0.88rem; line-height:1.7; }

  /* ===== PORTFOLIO ===== */
  #projeler { background:#fff; }
  .portfolio-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(300px,1fr)); gap:20px; max-width:1200px; margin:0 auto; }
  .portfolio-card {
    border-radius:8px; overflow:hidden; position:relative; cursor:pointer;
    background:linear-gradient(135deg,#2d2d2d,#1a1a1a); height:220px;
    display:flex; align-items:flex-end; padding:25px;
    transition:transform .3s;
  }
  .portfolio-card:hover { transform:scale(1.02); }
  .portfolio-card .overlay {
    position:absolute; inset:0;
    background:linear-gradient(to top,rgba(0,0,0,0.8) 0%,transparent 60%);
  }
  .portfolio-card .p-num {
    position:absolute; top:20px; right:20px;
    font-family:'Montserrat',sans-serif; font-weight:900; font-size:3rem;
    color:rgba(255,215,0,0.15); line-height:1;
  }
  .portfolio-info { position:relative; z-index:2; }
  .portfolio-info h4 { font-family:'Montserrat',sans-serif; font-weight:700; font-size:1rem; color:#fff; margin-bottom:6px; }
  .portfolio-info span { font-size:0.75rem; color:var(--yellow); letter-spacing:2px; text-transform:uppercase; }
  .port-badge {
    position:absolute; top:15px; left:15px; z-index:2;
    background:var(--yellow); color:#1a1a1a; font-family:'Montserrat',sans-serif;
    font-weight:700; font-size:0.65rem; letter-spacing:1px; padding:4px 10px; border-radius:2px; text-transform:uppercase;
  }

  /* ===== CONTACT ===== */
  #iletisim { background:#1a1a1a; }
  #iletisim .section-header h2 { color:#fff; }
  #iletisim .section-tag { color:var(--yellow); }
  #iletisim .section-header p { color:#aaa; }
  .contact-grid { display:grid; grid-template-columns:1fr 1fr; gap:60px; max-width:1000px; margin:0 auto; }
  .contact-info { color:#aaa; }
  .contact-info h3 { font-family:'Montserrat',sans-serif; font-weight:700; color:#fff; font-size:1.3rem; margin-bottom:25px; }
  .contact-item { display:flex; gap:15px; margin-bottom:22px; align-items:flex-start; }
  .contact-item .icon { font-size:1.3rem; margin-top:2px; }
  .contact-item div span { display:block; font-family:'Montserrat',sans-serif; font-weight:600; color:#fff; font-size:0.85rem; margin-bottom:3px; }
  .contact-item div p { color:#888; font-size:0.83rem; line-height:1.5; }
  .contact-form input, .contact-form textarea {
    width:100%; background:rgba(255,255,255,0.05); border:1px solid rgba(255,255,255,0.1);
    border-radius:5px; padding:13px 16px; color:#fff; font-family:'Raleway',sans-serif; font-size:0.88rem;
    margin-bottom:15px; outline:none; transition:border-color .3s;
  }
  .contact-form input:focus, .contact-form textarea:focus { border-color:var(--yellow); }
  .contact-form textarea { height:120px; resize:none; }
  .contact-form input::placeholder, .contact-form textarea::placeholder { color:#555; }

  /* ===== FOOTER ===== */
  footer {
    background:#111; color:#555; text-align:center; padding:25px;
    font-size:0.8rem; letter-spacing:1px;
    border-top:3px solid var(--yellow);
  }
  footer span { color:var(--yellow); font-weight:700; }

  /* ===== FLOATING BUTTONS ===== */
  .floating-buttons {
    position:fixed; right:22px; bottom:90px; z-index:999;
    display:flex; flex-direction:column; gap:12px; align-items:flex-end;
  }
  .fab {
    width:52px; height:52px; border-radius:50%; border:none; cursor:pointer;
    display:flex; align-items:center; justify-content:center; font-size:1.4rem;
    box-shadow:0 4px 18px rgba(0,0,0,0.25); transition:transform .2s, box-shadow .2s;
    text-decoration:none; position:relative;
  }
  .fab:hover { transform:scale(1.12); box-shadow:0 6px 22px rgba(0,0,0,0.35); }
  .fab-wa { background:#25D366; color:#fff; }
  .fab-chat { background:var(--yellow); color:#1a1a1a; }
  .fab-call { background:#007AFF; color:#fff; }
  .fab-tooltip {
    position:absolute; right:62px; background:#1a1a1a; color:#fff;
    font-family:'Montserrat',sans-serif; font-size:0.7rem; font-weight:600; letter-spacing:1px;
    padding:5px 12px; border-radius:4px; white-space:nowrap; opacity:0; pointer-events:none; transition:opacity .2s;
  }
  .fab:hover .fab-tooltip { opacity:1; }

  /* ===== LIVE CHAT POPUP ===== */
  #chat-popup {
    position:fixed; right:22px; bottom:160px; width:320px; z-index:1001;
    background:#fff; border-radius:16px; box-shadow:0 10px 50px rgba(0,0,0,0.2);
    overflow:hidden; display:none; flex-direction:column;
    animation:slideUp .3s ease;
  }
  @keyframes slideUp { from{opacity:0;transform:translateY(20px)} to{opacity:1;transform:translateY(0)} }
  .chat-header {
    background:linear-gradient(135deg,#1a1a1a,#2d2d2d);
    padding:18px 20px; display:flex; align-items:center; gap:12px;
  }
  .chat-avatar {
    width:40px; height:40px; border-radius:50%; background:var(--yellow);
    display:flex; align-items:center; justify-content:center; font-size:1.2rem;
  }
  .chat-header-info h4 { font-family:'Montserrat',sans-serif; font-weight:700; color:#fff; font-size:0.9rem; }
  .chat-header-info p { color:#aaa; font-size:0.72rem; }
  .chat-close {
    margin-left:auto; background:none; border:none; color:#aaa; font-size:1.2rem; cursor:pointer;
  }
  .chat-messages { padding:20px; min-height:150px; background:#f8f8f8; }
  .chat-msg {
    background:#fff; border-radius:12px 12px 12px 0; padding:10px 14px;
    font-size:0.82rem; color:#333; box-shadow:0 2px 8px rgba(0,0,0,0.08);
    max-width:90%; line-height:1.5; margin-bottom:10px;
    border-left:3px solid var(--yellow);
  }
  .chat-input-area { display:flex; padding:12px; gap:8px; border-top:1px solid #eee; }
  .chat-input-area input {
    flex:1; border:1px solid #e0e0e0; border-radius:25px; padding:9px 15px;
    font-family:'Raleway',sans-serif; font-size:0.82rem; outline:none;
  }
  .chat-input-area input:focus { border-color:var(--yellow); }
  .chat-send {
    width:38px; height:38px; border-radius:50%; background:var(--yellow); border:none;
    cursor:pointer; display:flex; align-items:center; justify-content:center; font-size:1rem;
    transition:transform .2s;
  }
  .chat-send:hover { transform:scale(1.1); }

  /* ===== SEARCH MODAL ===== */
  #search-modal {
    position:fixed; inset:0; z-index:2000; background:rgba(0,0,0,0.85);
    display:none; align-items:flex-start; justify-content:center; padding-top:120px;
    backdrop-filter:blur(8px);
  }
  .search-box { width:600px; max-width:90vw; }
  .search-box input {
    width:100%; background:rgba(255,255,255,0.1); border:2px solid var(--yellow);
    border-radius:8px; padding:18px 25px; color:#fff;
    font-family:'Montserrat',sans-serif; font-size:1.2rem; outline:none;
  }
  .search-box input::placeholder { color:rgba(255,255,255,0.4); }
  .search-results { margin-top:20px; }
  .search-result-item {
    background:rgba(255,255,255,0.08); border-radius:8px; padding:15px 20px;
    margin-bottom:10px; cursor:pointer; transition:background .2s;
    border-left:3px solid var(--yellow);
  }
  .search-result-item:hover { background:rgba(255,255,255,0.15); }
  .search-result-item h4 { color:#fff; font-family:'Montserrat',sans-serif; font-size:0.9rem; margin-bottom:4px; }
  .search-result-item p { color:#aaa; font-size:0.78rem; }

  /* ===== ADMIN PANEL ===== */
  #admin-panel {
    position:fixed; inset:0; z-index:3000; background:#0f0f0f;
    display:none; flex-direction:column; overflow:auto;
  }
  .admin-header {
    background:#1a1a1a; padding:18px 30px; display:flex; align-items:center;
    justify-content:space-between; border-bottom:3px solid var(--yellow);
  }
  .admin-header h2 { font-family:'Montserrat',sans-serif; font-weight:900; color:#fff; font-size:1.3rem; }
  .admin-header h2 span { color:var(--yellow); }
  .admin-close {
    background:var(--yellow); color:#1a1a1a; border:none; border-radius:5px; padding:8px 20px;
    font-family:'Montserrat',sans-serif; font-weight:700; cursor:pointer; font-size:0.85rem;
  }
  .admin-body { display:flex; flex:1; }
  .admin-sidebar {
    width:220px; background:#151515; padding:25px 0; border-right:1px solid #2a2a2a;
  }
  .admin-menu-item {
    padding:13px 25px; color:#888; font-family:'Montserrat',sans-serif; font-size:0.8rem;
    font-weight:600; letter-spacing:1px; cursor:pointer; transition:all .2s;
    display:flex; align-items:center; gap:10px; border-left:3px solid transparent;
  }
  .admin-menu-item.active, .admin-menu-item:hover {
    color:#fff; background:rgba(255,215,0,0.08); border-left-color:var(--yellow);
  }
  .admin-content { flex:1; padding:35px; }
  .admin-cards { display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:20px; margin-bottom:40px; }
  .admin-card {
    background:#1a1a1a; border-radius:10px; padding:25px;
    border-top:3px solid var(--yellow);
  }
  .admin-card h4 { color:#888; font-family:'Montserrat',sans-serif; font-size:0.75rem; letter-spacing:2px; text-transform:uppercase; margin-bottom:12px; }
  .admin-card .num { color:#fff; font-family:'Montserrat',sans-serif; font-weight:900; font-size:2.2rem; }
  .admin-card .trend { color:#4ade80; font-size:0.78rem; margin-top:5px; }
  .admin-table { background:#1a1a1a; border-radius:10px; overflow:hidden; }
  .admin-table-header {
    background:#2a2a2a; padding:18px 25px; display:flex; align-items:center; justify-content:space-between;
  }
  .admin-table-header h3 { color:#fff; font-family:'Montserrat',sans-serif; font-size:0.9rem; font-weight:700; }
  .admin-add-btn {
    background:var(--yellow); color:#1a1a1a; border:none; border-radius:5px;
    padding:8px 16px; font-family:'Montserrat',sans-serif; font-weight:700; font-size:0.78rem; cursor:pointer;
  }
  table { width:100%; border-collapse:collapse; }
  table th { padding:12px 20px; text-align:left; color:#888; font-family:'Montserrat',sans-serif; font-size:0.72rem; letter-spacing:1px; text-transform:uppercase; border-bottom:1px solid #2a2a2a; }
  table td { padding:14px 20px; color:#ccc; font-size:0.84rem; border-bottom:1px solid #1f1f1f; }
  table tr:hover td { background:rgba(255,255,255,0.03); }
  .badge { display:inline-block; padding:3px 10px; border-radius:20px; font-size:0.7rem; font-weight:700; font-family:'Montserrat',sans-serif; }
  .badge-green { background:rgba(74,222,128,0.15); color:#4ade80; }
  .badge-yellow { background:rgba(255,215,0,0.15); color:var(--yellow); }
  .badge-red { background:rgba(248,113,113,0.15); color:#f87171; }
  .admin-login {
    position:fixed; inset:0; z-index:4000; background:#0f0f0f;
    display:flex; align-items:center; justify-content:center;
  }
  .login-box { background:#1a1a1a; border-radius:16px; padding:50px 40px; width:380px; text-align:center; border-top:4px solid var(--yellow); }
  .login-box h2 { font-family:'Montserrat',sans-serif; font-weight:900; color:#fff; font-size:1.6rem; margin-bottom:8px; }
  .login-box p { color:#888; font-size:0.82rem; margin-bottom:35px; }
  .login-box input {
    width:100%; background:#252525; border:1px solid #333; border-radius:8px;
    padding:13px 16px; color:#fff; font-family:'Raleway',sans-serif; font-size:0.9rem;
    outline:none; margin-bottom:15px; transition:border-color .3s;
  }
  .login-box input:focus { border-color:var(--yellow); }
  .login-error { color:#f87171; font-size:0.78rem; margin-bottom:15px; min-height:20px; }

  /* ===== ADMIN TRIGGER (hidden link) ===== */
  #admin-trigger {
    position:fixed; bottom:0; right:0; width:60px; height:60px; cursor:pointer; z-index:998;
  }

  /* ===== SCROLL TO TOP ===== */
  #scroll-top {
    position:fixed; left:22px; bottom:22px; z-index:999;
    width:46px; height:46px; border-radius:50%; background:var(--yellow); border:none;
    cursor:pointer; font-size:1.2rem; box-shadow:0 4px 15px rgba(0,0,0,0.2);
    display:none; align-items:center; justify-content:center; transition:transform .2s;
  }
  #scroll-top:hover { transform:translateY(-3px); }

  /* ===== NAV BURGER (mobile) ===== */
  .burger { display:none; flex-direction:column; gap:5px; cursor:pointer; background:none; border:none; }
  .burger span { display:block; width:24px; height:2px; background:#555; transition:all .3s; }

  @media(max-width:768px) {
    header { padding:0 20px; }
    nav { display:none; }
    .burger { display:flex; }
    .header-search { display:none; }
    .stats-bar { gap:40px; }
    .contact-grid { grid-template-columns:1fr; }
    section { padding:70px 20px; }
    .admin-body { flex-direction:column; }
    .admin-sidebar { width:100%; display:flex; overflow-x:auto; padding:10px; border-right:none; border-bottom:1px solid #2a2a2a; }
    .admin-menu-item { border-left:none; border-bottom:3px solid transparent; white-space:nowrap; }
    .admin-menu-item.active, .admin-menu-item:hover { border-left-color:transparent; border-bottom-color:var(--yellow); }
  }
</style>
</head>
<body>

<!-- ===== HEADER ===== -->
<header>
  <div class="logo-area" onclick="scrollTo({top:0,behavior:'smooth'})">
    <!-- SVG Logo (Petek Fuar stilinde) -->
    <svg class="logo-svg" viewBox="0 0 60 50" fill="none" xmlns="http://www.w3.org/2000/svg">
      <rect x="0" y="0" width="25" height="25" fill="#8c8c8c"/>
      <rect x="28" y="0" width="25" height="25" fill="#8c8c8c" opacity="0.5"/>
      <rect x="0" y="27" width="25" height="10" fill="#FFD700"/>
      <rect x="0" y="40" width="40" height="10" fill="#FFD700"/>
      <rect x="14" y="27" width="25" height="10" fill="#8c8c8c" opacity="0.6"/>
    </svg>
    <div class="logo-text">
      <h1>Petek Fuar</h1>
      <p>Fuar Standı Tasarım ve Uygulama</p>
    </div>
  </div>

  <nav>
    <a href="#hero">Ana Sayfa</a>
    <a href="#hizmetler">Hizmetler</a>
    <a href="#projeler">Projeler</a>
    <a href="#hakkimizda">Hakkımızda</a>
    <a href="#iletisim">İletişim</a>
  </nav>

  <div class="header-search">
    <input type="text" placeholder="Ara..." id="header-search-input">
    <button onclick="openSearch()">🔍</button>
  </div>

  <button class="burger" onclick="toggleMobileNav()">
    <span></span><span></span><span></span>
  </button>
</header>

<!-- ===== HERO ===== -->
<section id="hero">
  <div class="hero-bg-pattern"></div>
  <div class="hero-content">
    <div class="hero-tag">⚡ Türkiye'nin Önde Gelen Fuar Stand Firması</div>
    <h2>Fuarda <span>Fark</span> Yaratın<br>Standınızla Öne Çıkın</h2>
    <p>Tasarımdan uygulamaya, montajdan dekorasyona kadar eksiksiz fuar standı çözümleri. 15+ yıllık deneyimle hayalinizdeki standı gerçeğe dönüştürüyoruz.</p>
    <a href="#projeler" class="btn-primary">Projelerimizi Gör</a>
    <a href="#iletisim" class="btn-outline">Teklif Al</a>
  </div>
</section>

<!-- ===== STATS ===== -->
<div class="stats-bar">
  <div class="stat"><div class="stat-num">850+</div><div class="stat-label">Tamamlanan Proje</div></div>
  <div class="stat"><div class="stat-num">15+</div><div class="stat-label">Yıllık Deneyim</div></div>
  <div class="stat"><div class="stat-num">200+</div><div class="stat-label">Mutlu Müşteri</div></div>
  <div class="stat"><div class="stat-num">30+</div><div class="stat-label">Fuar Fuarı</div></div>
</div>

<!-- ===== HİZMETLER ===== -->
<section id="hizmetler">
  <div class="section-header">
    <div class="section-tag">Hizmetlerimiz</div>
    <h2>Ne Sunuyoruz?</h2>
    <p>Fuarın her aşamasında yanınızdayız. Konsept geliştirmeden son vidayı sıkıncaya kadar.</p>
  </div>
  <div class="services-grid">
    <div class="service-card">
      <div class="service-icon">🏗️</div>
      <h3>Stand Tasarımı</h3>
      <p>Markanızı yansıtan özgün, dikkat çekici stand konseptleri. 3D görselleştirme ile beğeninize sunulur.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">🔨</div>
      <h3>Uygulama & Montaj</h3>
      <p>Profesyonel ekibimiz ile hızlı, güvenli montaj. Zamana ve bütçeye tam uyum.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">🎨</div>
      <h3>Grafik & Baskı</h3>
      <p>Yüksek çözünürlüklü grafik tasarım ve geniş format baskı hizmetleri.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">💡</div>
      <h3>Aydınlatma</h3>
      <p>LED ve özel aydınlatma çözümleri ile standınızı parlak ve davetkar yapın.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">📦</div>
      <h3>Taşıma & Depolama</h3>
      <p>Stand malzemelerinin güvenli taşıması ve fuar arası dönemde depolama hizmeti.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">🌍</div>
      <h3>Yurt Dışı Fuarlar</h3>
      <p>Avrupa ve Orta Doğu'daki uluslararası fuarlarda stand hizmetleri.</p>
    </div>
  </div>
</section>

<!-- ===== PROJELERİMİZ ===== -->
<section id="projeler">
  <div class="section-header">
    <div class="section-tag">Portfolyo</div>
    <h2>Seçkin Projelerimiz</h2>
    <p>Her projeye özel yaklaşım, her müşteriye benzersiz deneyim.</p>
  </div>
  <div class="portfolio-grid">
    <div class="portfolio-card" style="background:linear-gradient(135deg,#2d1a00,#4a2e00)">
      <div class="overlay"></div>
      <div class="p-num">01</div>
      <div class="port-badge">Tamamlandı</div>
      <div class="portfolio-info"><h4>CNR Expo — Mobilya Fuarı</h4><span>İstanbul, 2024</span></div>
    </div>
    <div class="portfolio-card" style="background:linear-gradient(135deg,#0a1a2d,#0d2a40)">
      <div class="overlay"></div>
      <div class="p-num">02</div>
      <div class="port-badge">Tamamlandı</div>
      <div class="portfolio-info"><h4>Win — İnşaat Fuarı</h4><span>Ankara, 2024</span></div>
    </div>
    <div class="portfolio-card" style="background:linear-gradient(135deg,#1a0d2d,#2d1a4a)">
      <div class="overlay"></div>
      <div class="p-num">03</div>
      <div class="port-badge">Tamamlandı</div>
      <div class="portfolio-info"><h4>TÜYAP — Otomotiv Fuarı</h4><span>İstanbul, 2023</span></div>
    </div>
    <div class="portfolio-card" style="background:linear-gradient(135deg,#0d2d1a,#1a4a2d)">
      <div class="overlay"></div>
      <div class="p-num">04</div>
      <div class="port-badge">Tamamlandı</div>
      <div class="portfolio-info"><h4>Hannover Messe</h4><span>Almanya, 2023</span></div>
    </div>
    <div class="portfolio-card" style="background:linear-gradient(135deg,#2d2d00,#4a4a00)">
      <div class="overlay"></div>
      <div class="p-num">05</div>
      <div class="port-badge">Devam Ediyor</div>
      <div class="portfolio-info"><h4>Expo Türkiye — Gıda Fuarı</h4><span>İzmir, 2025</span></div>
    </div>
    <div class="portfolio-card" style="background:linear-gradient(135deg,#2d0d0d,#4a1a1a)">
      <div class="overlay"></div>
      <div class="p-num">06</div>
      <div class="port-badge">Planlama</div>
      <div class="portfolio-info"><h4>Dubai Expo — Teknoloji</h4><span>Dubai, 2025</span></div>
    </div>
  </div>
</section>

<!-- ===== HAKKIMIZDA ===== -->
<section id="hakkimizda" style="background:#f8f8f8;">
  <div style="max-width:900px;margin:0 auto;text-align:center;">
    <div class="section-tag">Hakkımızda</div>
    <h2 style="font-family:'Montserrat',sans-serif;font-weight:900;font-size:2.2rem;margin:15px 0 25px;">Petek Fuar Kimdir?</h2>
    <p style="color:#666;font-size:1rem;line-height:1.9;margin-bottom:30px;">
      2009 yılında kurulan Petek Fuar, 15 yılı aşkın tecrübesiyle Türkiye'nin en güvenilir fuar standı tasarım ve uygulama firmalarından biri olmuştur. 
      İstanbul merkezli firmamız, ülke genelindeki 30'dan fazla fuarda 850'yi aşkın proje teslim etmiştir. 
      Her projede müşterinin markasını en iyi şekilde temsil eden, fonksiyonel ve estetik standlar tasarlamayı ilke edinmiş bir ekibiz.
    </p>
    <a href="#iletisim" class="btn-primary" style="text-decoration:none;">Bizimle Çalışın</a>
  </div>
</section>

<!-- ===== İLETİŞİM ===== -->
<section id="iletisim">
  <div class="section-header">
    <div class="section-tag">İletişim</div>
    <h2>Bize Ulaşın</h2>
    <p>Projeniz için ücretsiz teklif alın. 24 saat içinde dönüş garantisi.</p>
  </div>
  <div class="contact-grid">
    <div class="contact-info">
      <h3>İletişim Bilgileri</h3>
      <div class="contact-item">
        <span class="icon">📍</span>
        <div><span>Adres</span><p>Bağcılar, İstanbul, Türkiye</p></div>
      </div>
      <div class="contact-item">
        <span class="icon">📞</span>
        <div><span>Telefon</span><p>+90 212 XXX XX XX</p></div>
      </div>
      <div class="contact-item">
        <span class="icon">📧</span>
        <div><span>E-posta</span><p>info@petekfuar.com</p></div>
      </div>
      <div class="contact-item">
        <span class="icon">⏰</span>
        <div><span>Çalışma Saatleri</span><p>Pzt-Cum: 09:00 – 18:00</p></div>
      </div>
      <a href="https://wa.me/905XXXXXXXXX" target="_blank" class="btn-primary" style="display:inline-flex;align-items:center;gap:10px;text-decoration:none;margin-top:20px;">
        <span>WhatsApp ile Yaz</span>
      </a>
    </div>
    <div class="contact-form">
      <input type="text" placeholder="Adınız Soyadınız" id="cf-name">
      <input type="email" placeholder="E-posta Adresiniz" id="cf-email">
      <input type="text" placeholder="Konu" id="cf-subject">
      <textarea placeholder="Mesajınız..." id="cf-msg"></textarea>
      <button class="btn-primary" onclick="sendForm()" style="width:100%;border:none;cursor:pointer;">Gönder →</button>
    </div>
  </div>
</section>

<!-- ===== FOOTER ===== -->
<footer>
  <p>© 2025 <span>Petek Fuar</span> — Fuar Standı Tasarım ve Uygulama | Tüm Hakları Saklıdır</p>
  <p style="margin-top:8px;font-size:0.72rem;">Admin paneline erişmek için sağ alta tıklayın.</p>
</footer>

<!-- ===== FLOATING BUTTONS ===== -->
<div class="floating-buttons">
  <a href="https://wa.me/905XXXXXXXXX" target="_blank" class="fab fab-wa">
    <svg width="22" height="22" viewBox="0 0 24 24" fill="white"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.127.557 4.126 1.532 5.864L0 24l6.305-1.654A11.945 11.945 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.818c-1.937 0-3.74-.524-5.28-1.435l-.379-.225-3.923 1.029 1.047-3.821-.247-.393A9.818 9.818 0 012.182 12c0-5.422 4.396-9.818 9.818-9.818S21.818 6.578 21.818 12 17.422 21.818 12 21.818z"/></svg>
    <span class="fab-tooltip">WhatsApp</span>
  </a>
  <a href="tel:+902XXXXXXXXX" class="fab fab-call">
    📞
    <span class="fab-tooltip">Bizi Arayın</span>
  </a>
  <button class="fab fab-chat" onclick="toggleChat()">
    💬
    <span class="fab-tooltip">Canlı Destek</span>
  </button>
</div>

<!-- ===== LIVE CHAT ===== -->
<div id="chat-popup">
  <div class="chat-header">
    <div class="chat-avatar">👤</div>
    <div class="chat-header-info">
      <h4>Petek Fuar Destek</h4>
      <p>🟢 Çevrimiçi — Ortalama yanıt süresi: 2dk</p>
    </div>
    <button class="chat-close" onclick="toggleChat()">✕</button>
  </div>
  <div class="chat-messages" id="chat-messages">
    <div class="chat-msg">Merhaba! 👋 Petek Fuar'a hoş geldiniz. Size nasıl yardımcı olabiliriz?</div>
  </div>
  <div class="chat-input-area">
    <input type="text" id="chat-input" placeholder="Mesajınızı yazın..." onkeydown="if(event.key==='Enter')sendChat()">
    <button class="chat-send" onclick="sendChat()">➤</button>
  </div>
</div>

<!-- ===== SEARCH MODAL ===== -->
<div id="search-modal" onclick="if(event.target===this)closeSearch()">
  <div class="search-box">
    <input type="text" id="search-input" placeholder="Ne aramak istersiniz?" oninput="doSearch(this.value)" onkeydown="if(event.key==='Escape')closeSearch()">
    <div class="search-results" id="search-results"></div>
  </div>
</div>

<!-- ===== ADMIN TRIGGER (invisible corner) ===== -->
<div id="admin-trigger" onclick="openAdminLogin()"></div>

<!-- ===== ADMIN LOGIN ===== -->
<div class="admin-login" id="admin-login" style="display:none;">
  <div class="login-box">
    <h2>🔐 Admin <span style="color:var(--yellow)">Paneli</span></h2>
    <p>Devam etmek için giriş yapın</p>
    <input type="text" id="admin-user" placeholder="Kullanıcı Adı">
    <input type="password" id="admin-pass" placeholder="Şifre" onkeydown="if(event.key==='Enter')checkLogin()">
    <div class="login-error" id="login-error"></div>
    <button class="btn-primary" onclick="checkLogin()" style="width:100%;border:none;cursor:pointer;font-size:0.9rem;padding:14px;">Giriş Yap</button>
    <p style="margin-top:20px;color:#555;font-size:0.75rem;cursor:pointer;" onclick="closeAdminLogin()">← Siteye Dön</p>
  </div>
</div>

<!-- ===== ADMIN PANEL ===== -->
<div id="admin-panel">
  <div class="admin-header">
    <h2>Petek Fuar — <span>Admin Panel</span></h2>
    <button class="admin-close" onclick="closeAdmin()">✕ Çıkış</button>
  </div>
  <div class="admin-body">
    <div class="admin-sidebar">
      <div class="admin-menu-item active" onclick="showAdminTab('dashboard',this)">📊 Dashboard</div>
      <div class="admin-menu-item" onclick="showAdminTab('projeler',this)">🏗️ Projeler</div>
      <div class="admin-menu-item" onclick="showAdminTab('mesajlar',this)">💬 Mesajlar</div>
      <div class="admin-menu-item" onclick="showAdminTab('hizmetler',this)">⚙️ Hizmetler</div>
      <div class="admin-menu-item" onclick="showAdminTab('ayarlar',this)">🔧 Ayarlar</div>
    </div>
    <div class="admin-content" id="admin-content">
      <!-- Dashboard -->
      <div id="tab-dashboard">
        <h3 style="color:#fff;font-family:'Montserrat',sans-serif;margin-bottom:25px;font-size:1.1rem;">Genel Bakış</h3>
        <div class="admin-cards">
          <div class="admin-card"><h4>Toplam Proje</h4><div class="num">850</div><div class="trend">↑ 12 bu ay</div></div>
          <div class="admin-card"><h4>Yeni Mesaj</h4><div class="num">7</div><div class="trend">↑ 3 bugün</div></div>
          <div class="admin-card"><h4>Aktif Proje</h4><div class="num">4</div><div class="trend">Devam ediyor</div></div>
          <div class="admin-card"><h4>Ziyaretçi</h4><div class="num">1.2K</div><div class="trend">↑ Bu hafta</div></div>
        </div>
        <div class="admin-table">
          <div class="admin-table-header"><h3>Son Projeler</h3><button class="admin-add-btn" onclick="addProject()">+ Ekle</button></div>
          <table>
            <thead><tr><th>Proje Adı</th><th>Müşteri</th><th>Fuar</th><th>Durum</th></tr></thead>
            <tbody id="projects-tbody">
              <tr><td>CNR Expo Stand</td><td>Mobilya A.Ş.</td><td>CNR Expo 2024</td><td><span class="badge badge-green">Tamamlandı</span></td></tr>
              <tr><td>Win İnşaat</td><td>İnşaat Ltd.</td><td>Win 2024</td><td><span class="badge badge-green">Tamamlandı</span></td></tr>
              <tr><td>Expo Gıda</td><td>Gıda Şirketi</td><td>Expo İzmir 2025</td><td><span class="badge badge-yellow">Devam Ediyor</span></td></tr>
              <tr><td>Dubai Expo</td><td>Tech Corp</td><td>Dubai 2025</td><td><span class="badge badge-red">Planlama</span></td></tr>
            </tbody>
          </table>
        </div>
      </div>
      <!-- Mesajlar -->
      <div id="tab-mesajlar" style="display:none;">
        <h3 style="color:#fff;font-family:'Montserrat',sans-serif;margin-bottom:25px;font-size:1.1rem;">Gelen Mesajlar</h3>
        <div class="admin-table">
          <div class="admin-table-header"><h3>Form Mesajları</h3></div>
          <table>
            <thead><tr><th>Ad</th><th>E-posta</th><th>Konu</th><th>Durum</th></tr></thead>
            <tbody id="messages-tbody">
              <tr><td>Ahmet Yılmaz</td><td>ahmet@example.com</td><td>Stand Teklifi</td><td><span class="badge badge-yellow">Bekliyor</span></td></tr>
              <tr><td>Fatma Kaya</td><td>fatma@example.com</td><td>Fiyat Bilgisi</td><td><span class="badge badge-green">Yanıtlandı</span></td></tr>
            </tbody>
          </table>
        </div>
      </div>
      <!-- Diğer tablar -->
      <div id="tab-projeler" style="display:none;">
        <h3 style="color:#fff;font-family:'Montserrat',sans-serif;margin-bottom:25px;">Proje Yönetimi</h3>
        <div class="admin-table">
          <div class="admin-table-header"><h3>Tüm Projeler</h3><button class="admin-add-btn" onclick="addProject()">+ Yeni Proje</button></div>
          <table>
            <thead><tr><th>Proje</th><th>Tarih</th><th>Bütçe</th><th>Durum</th></tr></thead>
            <tbody>
              <tr><td>CNR Expo</td><td>Mar 2024</td><td>₺45.000</td><td><span class="badge badge-green">Tamamlandı</span></td></tr>
              <tr><td>Hannover</td><td>Eki 2023</td><td>€12.000</td><td><span class="badge badge-green">Tamamlandı</span></td></tr>
              <tr><td>Dubai Expo</td><td>Tem 2025</td><td>₺120.000</td><td><span class="badge badge-red">Planlama</span></td></tr>
            </tbody>
          </table>
        </div>
      </div>
      <div id="tab-hizmetler" style="display:none;">
        <h3 style="color:#fff;font-family:'Montserrat',sans-serif;margin-bottom:25px;">Hizmet Yönetimi</h3>
        <p style="color:#888;">Hizmet kartlarını buradan düzenleyebilirsiniz.</p>
      </div>
      <div id="tab-ayarlar" style="display:none;">
        <h3 style="color:#fff;font-family:'Montserrat',sans-serif;margin-bottom:25px;">Site Ayarları</h3>
        <div style="background:#1a1a1a;border-radius:10px;padding:30px;max-width:500px;">
          <div style="margin-bottom:20px;">
            <label style="color:#888;font-size:0.78rem;font-family:'Montserrat',sans-serif;letter-spacing:1px;display:block;margin-bottom:8px;">SİTE BAŞLIĞI</label>
            <input type="text" value="Petek Fuar" style="width:100%;background:#252525;border:1px solid #333;border-radius:6px;padding:11px 14px;color:#fff;font-family:'Raleway',sans-serif;outline:none;">
          </div>
          <div style="margin-bottom:20px;">
            <label style="color:#888;font-size:0.78rem;font-family:'Montserrat',sans-serif;letter-spacing:1px;display:block;margin-bottom:8px;">WHATSAPP NUMARASI</label>
            <input type="text" value="+90 5XX XXX XX XX" style="width:100%;background:#252525;border:1px solid #333;border-radius:6px;padding:11px 14px;color:#fff;font-family:'Raleway',sans-serif;outline:none;">
          </div>
          <div style="margin-bottom:25px;">
            <label style="color:#888;font-size:0.78rem;font-family:'Montserrat',sans-serif;letter-spacing:1px;display:block;margin-bottom:8px;">ADMIN ŞİFRESİ</label>
            <input type="password" placeholder="Yeni şifre" style="width:100%;background:#252525;border:1px solid #333;border-radius:6px;padding:11px 14px;color:#fff;font-family:'Raleway',sans-serif;outline:none;">
          </div>
          <button class="btn-primary" style="border:none;cursor:pointer;font-size:0.85rem;">Kaydet</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ===== SCROLL TOP ===== -->
<button id="scroll-top" onclick="window.scrollTo({top:0,behavior:'smooth'})">▲</button>

<script>
// ============ SCROLL TOP ============
window.addEventListener('scroll',()=>{
  const btn=document.getElementById('scroll-top');
  btn.style.display=window.scrollY>400?'flex':'none';
});

// ============ MOBILE NAV ============
function toggleMobileNav(){
  const nav=document.querySelector('nav');
  if(nav.style.display==='flex'&&nav.style.flexDirection==='column'){
    nav.style.display='none';
  } else {
    nav.style.cssText='display:flex;flex-direction:column;position:fixed;top:70px;left:0;right:0;background:#fff;padding:20px 30px;gap:20px;box-shadow:0 10px 30px rgba(0,0,0,0.1);z-index:999;';
  }
}

// ============ SEARCH ============
const searchData=[
  {title:'Stand Tasarımı',desc:'Özgün stand konsept tasarımı hizmeti'},
  {title:'Montaj Hizmeti',desc:'Profesyonel ekiple hızlı montaj'},
  {title:'Grafik & Baskı',desc:'Yüksek kalite baskı çözümleri'},
  {title:'CNR Expo Projesi',desc:'İstanbul, 2024 – Mobilya Fuarı'},
  {title:'Hannover Messe',desc:'Almanya, 2023 – Uluslararası proje'},
  {title:'İletişim',desc:'Bize ulaşın, teklif alın'},
  {title:'Hakkımızda',desc:'15 yıllık deneyim, 850+ proje'},
];
function openSearch(){
  document.getElementById('search-modal').style.display='flex';
  setTimeout(()=>document.getElementById('search-input').focus(),100);
}
function closeSearch(){ document.getElementById('search-modal').style.display='none'; }
function doSearch(q){
  const res=document.getElementById('search-results');
  if(!q){res.innerHTML='';return;}
  const filtered=searchData.filter(x=>x.title.toLowerCase().includes(q.toLowerCase())||x.desc.toLowerCase().includes(q.toLowerCase()));
  res.innerHTML=filtered.map(x=>`<div class="search-result-item"><h4>${x.title}</h4><p>${x.desc}</p></div>`).join('')||'<div class="search-result-item"><h4>Sonuç bulunamadı</h4><p>Farklı bir kelime deneyin.</p></div>';
}
document.getElementById('header-search-input').addEventListener('focus',openSearch);
document.addEventListener('keydown',e=>{if(e.key==='Escape')closeSearch();});

// ============ CHAT ============
let chatOpen=false;
function toggleChat(){
  chatOpen=!chatOpen;
  const popup=document.getElementById('chat-popup');
  popup.style.display=chatOpen?'flex':'none';
  if(chatOpen) document.getElementById('chat-input').focus();
}
function sendChat(){
  const input=document.getElementById('chat-input');
  const msg=input.value.trim();
  if(!msg)return;
  const msgs=document.getElementById('chat-messages');
  const userMsg=document.createElement('div');
  userMsg.style.cssText='background:var(--yellow);color:#1a1a1a;border-radius:12px 12px 0 12px;padding:10px 14px;font-size:0.82px;max-width:90%;margin-left:auto;margin-bottom:10px;font-family:Raleway,sans-serif;font-size:0.82rem;';
  userMsg.textContent=msg;
  msgs.appendChild(userMsg);
  input.value='';
  msgs.scrollTop=msgs.scrollHeight;
  setTimeout(()=>{
    const auto=document.createElement('div');
    auto.className='chat-msg';
    auto.textContent='Mesajınız alındı! En kısa sürede size dönüş yapacağız. 📞';
    msgs.appendChild(auto);
    msgs.scrollTop=msgs.scrollHeight;
  },1000);
}

// ============ FORM ============
function sendForm(){
  const name=document.getElementById('cf-name').value;
  const email=document.getElementById('cf-email').value;
  const msg=document.getElementById('cf-msg').value;
  if(!name||!email||!msg){alert('Lütfen tüm alanları doldurun.');return;}
  // Admin mesajlar tabına ekle
  const tbody=document.getElementById('messages-tbody');
  const row=document.createElement('tr');
  row.innerHTML=`<td>${name}</td><td>${email}</td><td>${document.getElementById('cf-subject').value||'Genel'}</td><td><span class="badge badge-yellow">Bekliyor</span></td>`;
  tbody.appendChild(row);
  alert('Mesajınız gönderildi! En kısa sürede size dönüş yapacağız.');
  ['cf-name','cf-email','cf-subject','cf-msg'].forEach(id=>document.getElementById(id).value='');
}

// ============ ADMIN ============
function openAdminLogin(){
  document.getElementById('admin-login').style.display='flex';
}
function closeAdminLogin(){
  document.getElementById('admin-login').style.display='none';
  document.getElementById('login-error').textContent='';
}
function checkLogin(){
  const u=document.getElementById('admin-user').value;
  const p=document.getElementById('admin-pass').value;
  // Kullanıcı adı: admin | Şifre: petekfuar2025
  if(u==='admin'&&p==='petekfuar2025'){
    document.getElementById('admin-login').style.display='none';
    document.getElementById('admin-panel').style.display='flex';
  } else {
    document.getElementById('login-error').textContent='Hatalı kullanıcı adı veya şifre.';
  }
}
function closeAdmin(){
  document.getElementById('admin-panel').style.display='none';
}
function showAdminTab(tab,el){
  document.querySelectorAll('[id^="tab-"]').forEach(t=>t.style.display='none');
  document.getElementById('tab-'+tab).style.display='block';
  document.querySelectorAll('.admin-menu-item').forEach(m=>m.classList.remove('active'));
  el.classList.add('active');
}
function addProject(){
  const name=prompt('Proje adı:');
  if(!name)return;
  const client=prompt('Müşteri adı:');
  const fair=prompt('Fuar adı:');
  const tbody=document.getElementById('projects-tbody');
  const row=document.createElement('tr');
  row.innerHTML=`<td>${name}</td><td>${client||'-'}</td><td>${fair||'-'}</td><td><span class="badge badge-yellow">Yeni</span></td>`;
  tbody.prepend(row);
  alert('Proje eklendi!');
}
</script>
</body>
</html>
