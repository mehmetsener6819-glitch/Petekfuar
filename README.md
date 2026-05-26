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
    <button onclick="openS