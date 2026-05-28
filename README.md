<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Infinity Sports | Ropa Deportiva & Equipos de Fútbol</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&family=Montserrat:wght@400;500;600;700;800;900&display=swap" rel="stylesheet" />
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet" />
  <style>
    /* ============ CSS VARIABLES ============ */
    :root {
      --blue: #1E3A8A;
      --blue-light: #2d52b8;
      --blue-dark: #162d6e;
      --orange: #F97316;
      --orange-light: #fb923c;
      --orange-dark: #ea6c0a;
      --white: #FFFFFF;
      --gray-light: #F3F4F6;
      --gray: #9CA3AF;
      --gray-dark: #374151;
      --text: #1F2937;
      --shadow: 0 4px 24px rgba(30,58,138,0.10);
      --shadow-lg: 0 8px 40px rgba(30,58,138,0.16);
      --radius: 16px;
      --radius-sm: 10px;
      --transition: 0.35s cubic-bezier(.4,0,.2,1);
    }

    /* ============ RESET & BASE ============ */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      font-family: 'Poppins', sans-serif;
      color: var(--text);
      background: var(--white);
      overflow-x: hidden;
    }
    a { text-decoration: none; color: inherit; }
    img { max-width: 100%; display: block; }
    ul { list-style: none; }

    /* ============ SCROLLBAR ============ */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--gray-light); }
    ::-webkit-scrollbar-thumb { background: var(--blue); border-radius: 3px; }

    /* ============ UTILITY ============ */
    .container { max-width: 1200px; margin: 0 auto; padding: 0 24px; }
    .section-tag {
      display: inline-block;
      background: rgba(249,115,22,.12);
      color: var(--orange);
      font-size: 0.78rem;
      font-weight: 700;
      letter-spacing: 2px;
      text-transform: uppercase;
      padding: 6px 18px;
      border-radius: 50px;
      margin-bottom: 14px;
    }
    .section-title {
      font-family: 'Montserrat', sans-serif;
      font-size: clamp(1.8rem, 3.5vw, 2.6rem);
      font-weight: 800;
      color: var(--blue-dark);
      line-height: 1.2;
      margin-bottom: 16px;
    }
    .section-title span { color: var(--orange); }
    .section-subtitle {
      font-size: 1rem;
      color: var(--gray-dark);
      max-width: 560px;
      line-height: 1.7;
    }
    .btn {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 14px 32px;
      border-radius: 50px;
      font-family: 'Poppins', sans-serif;
      font-weight: 600;
      font-size: 0.95rem;
      cursor: pointer;
      border: none;
      transition: var(--transition);
      text-decoration: none;
    }
    .btn-primary {
      background: var(--orange);
      color: var(--white);
      box-shadow: 0 4px 20px rgba(249,115,22,.35);
    }
    .btn-primary:hover {
      background: var(--orange-dark);
      transform: translateY(-2px);
      box-shadow: 0 8px 28px rgba(249,115,22,.45);
    }
    .btn-secondary {
      background: transparent;
      color: var(--white);
      border: 2px solid rgba(255,255,255,0.6);
    }
    .btn-secondary:hover {
      background: rgba(255,255,255,0.12);
      border-color: var(--white);
      transform: translateY(-2px);
    }
    .btn-blue {
      background: var(--blue);
      color: var(--white);
      box-shadow: 0 4px 20px rgba(30,58,138,.3);
    }
    .btn-blue:hover {
      background: var(--blue-dark);
      transform: translateY(-2px);
      box-shadow: 0 8px 28px rgba(30,58,138,.4);
    }

    /* ============ SCROLL ANIMATIONS ============ */
    .reveal {
      opacity: 0;
      transform: translateY(40px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }
    .reveal-left {
      opacity: 0;
      transform: translateX(-40px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal-left.visible { opacity: 1; transform: translateX(0); }
    .reveal-right {
      opacity: 0;
      transform: translateX(40px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal-right.visible { opacity: 1; transform: translateX(0); }

    /* ============ HEADER / NAVBAR ============ */
    #navbar {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 1000;
      padding: 18px 0;
      transition: background 0.4s, box-shadow 0.4s, padding 0.4s;
    }
    #navbar.scrolled {
      background: rgba(255,255,255,0.97);
      box-shadow: 0 2px 24px rgba(30,58,138,.10);
      padding: 12px 0;
    }
    #navbar.scrolled .nav-logo-text { color: var(--blue); }
    #navbar.scrolled .nav-links a { color: var(--text); }
    #navbar.scrolled .nav-links a:hover { color: var(--orange); }
    #navbar.scrolled .nav-links a.active { color: var(--orange); }

    .nav-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .nav-logo {
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .nav-logo-icon {
      width: 46px; height: 46px;
      border-radius: 10px;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 12px rgba(30,58,138,.3);
      background: #0a0a0a;
      flex-shrink: 0;
    }
    .nav-logo-icon img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
    }
    .nav-logo-text {
      font-family: 'Montserrat', sans-serif;
      font-weight: 800;
      font-size: 1.3rem;
      color: var(--white);
      letter-spacing: -0.5px;
      transition: color 0.4s;
    }
    .nav-logo-text span { color: var(--orange); }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 36px;
    }
    .nav-links a {
      font-size: 0.88rem;
      font-weight: 600;
      color: rgba(255,255,255,0.85);
      letter-spacing: 0.3px;
      transition: color var(--transition);
      position: relative;
    }
    .nav-links a::after {
      content: '';
      position: absolute;
      bottom: -4px; left: 0;
      width: 0; height: 2px;
      background: var(--orange);
      border-radius: 2px;
      transition: width var(--transition);
    }
    .nav-links a:hover::after,
    .nav-links a.active::after { width: 100%; }
    .nav-links a:hover { color: var(--orange); }

    .nav-cta { display: flex; align-items: center; gap: 12px; }

    .hamburger {
      display: none;
      flex-direction: column;
      gap: 5px;
      cursor: pointer;
      padding: 4px;
    }
    .hamburger span {
      display: block;
      width: 26px; height: 2.5px;
      background: var(--white);
      border-radius: 2px;
      transition: var(--transition);
    }
    #navbar.scrolled .hamburger span { background: var(--blue); }
    .hamburger.open span:nth-child(1) { transform: translateY(7.5px) rotate(45deg); }
    .hamburger.open span:nth-child(2) { opacity: 0; }
    .hamburger.open span:nth-child(3) { transform: translateY(-7.5px) rotate(-45deg); }

    /* Mobile menu */
    .mobile-menu {
      display: none;
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: rgba(30,58,138,0.98);
      z-index: 999;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 32px;
      padding: 40px;
    }
    .mobile-menu.open { display: flex; }
    .mobile-menu a {
      font-family: 'Montserrat', sans-serif;
      font-size: 1.6rem;
      font-weight: 700;
      color: white;
      transition: color var(--transition);
    }
    .mobile-menu a:hover { color: var(--orange); }
    .mobile-menu-close {
      position: absolute;
      top: 24px; right: 24px;
      background: none;
      border: none;
      color: white;
      font-size: 1.8rem;
      cursor: pointer;
    }

    /* ============ HERO ============ */
    #hero {
      min-height: 100vh;
      background: linear-gradient(135deg, var(--blue-dark) 0%, var(--blue) 50%, #1a4db5 100%);
      position: relative;
      display: flex;
      align-items: center;
      overflow: hidden;
    }
    .hero-bg-shapes {
      position: absolute;
      inset: 0;
      pointer-events: none;
      overflow: hidden;
    }
    .hero-bg-shapes .shape {
      position: absolute;
      border-radius: 50%;
      opacity: 0.07;
    }
    .shape-1 {
      width: 600px; height: 600px;
      background: var(--orange);
      top: -200px; right: -100px;
      animation: float 8s ease-in-out infinite;
    }
    .shape-2 {
      width: 400px; height: 400px;
      background: white;
      bottom: -150px; left: -100px;
      animation: float 10s ease-in-out infinite reverse;
    }
    .shape-3 {
      width: 200px; height: 200px;
      background: var(--orange);
      top: 40%; left: 30%;
      animation: float 6s ease-in-out infinite;
    }
    .hero-grid-lines {
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
      background-size: 60px 60px;
    }
    @keyframes float {
      0%, 100% { transform: translateY(0) scale(1); }
      50% { transform: translateY(-30px) scale(1.05); }
    }
    .hero-content {
      position: relative;
      z-index: 2;
      max-width: 680px;
    }
    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(249,115,22,.18);
      border: 1px solid rgba(249,115,22,.35);
      color: #fbbf7a;
      font-size: 0.8rem;
      font-weight: 600;
      letter-spacing: 1px;
      padding: 8px 18px;
      border-radius: 50px;
      margin-bottom: 28px;
      animation: fadeDown 0.7s ease both;
    }
    .hero-badge i { color: var(--orange); }
    .hero-title {
      font-family: 'Montserrat', sans-serif;
      font-size: clamp(2.4rem, 5.5vw, 4rem);
      font-weight: 900;
      color: var(--white);
      line-height: 1.1;
      margin-bottom: 20px;
      animation: fadeUp 0.8s ease 0.1s both;
    }
    .hero-title span {
      color: var(--orange);
      position: relative;
    }
    .hero-subtitle {
      font-size: clamp(1rem, 2vw, 1.2rem);
      color: rgba(255,255,255,0.75);
      line-height: 1.7;
      margin-bottom: 40px;
      animation: fadeUp 0.8s ease 0.2s both;
    }
    .hero-actions {
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
      animation: fadeUp 0.8s ease 0.3s both;
    }
    .hero-stats {
      display: flex;
      gap: 40px;
      margin-top: 56px;
      animation: fadeUp 0.8s ease 0.4s both;
      flex-wrap: wrap;
    }
    .hero-stat-item { text-align: center; }
    .hero-stat-num {
      font-family: 'Montserrat', sans-serif;
      font-size: 2rem;
      font-weight: 900;
      color: var(--orange);
    }
    .hero-stat-label {
      font-size: 0.78rem;
      color: rgba(255,255,255,0.6);
      font-weight: 500;
      letter-spacing: 0.5px;
    }

    .hero-image-side {
      position: absolute;
      right: 0; top: 0; bottom: 0;
      width: 45%;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 80px 40px 40px;
    }
    .hero-visual {
      position: relative;
      width: 100%;
      max-width: 440px;
      animation: fadeLeft 1s ease 0.5s both;
    }
    .hero-card-main {
      background: rgba(255,255,255,0.10);
      backdrop-filter: blur(20px);
      border: 1px solid rgba(255,255,255,0.15);
      border-radius: 24px;
      padding: 28px;
      box-shadow: 0 20px 60px rgba(0,0,0,0.3);
    }
    .hero-card-icons {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 12px;
      margin-bottom: 20px;
    }
    .hero-icon-box {
      background: rgba(255,255,255,0.1);
      border-radius: 14px;
      padding: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      transition: var(--transition);
      cursor: default;
    }
    .hero-icon-box:hover {
      background: rgba(249,115,22,0.3);
      transform: translateY(-4px);
    }
    .hero-icon-box i {
      font-size: 1.8rem;
      color: var(--orange);
    }
    .hero-icon-box span {
      font-size: 0.7rem;
      color: rgba(255,255,255,0.8);
      font-weight: 600;
      text-align: center;
    }
    .hero-progress-section {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .hero-progress-item { }
    .hero-progress-header {
      display: flex;
      justify-content: space-between;
      font-size: 0.78rem;
      color: rgba(255,255,255,0.8);
      font-weight: 500;
      margin-bottom: 5px;
    }
    .hero-progress-bar {
      height: 6px;
      background: rgba(255,255,255,0.15);
      border-radius: 3px;
      overflow: hidden;
    }
    .hero-progress-fill {
      height: 100%;
      background: linear-gradient(90deg, var(--orange), #fbbf24);
      border-radius: 3px;
      transition: width 1.5s ease;
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeDown {
      from { opacity: 0; transform: translateY(-20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeLeft {
      from { opacity: 0; transform: translateX(40px); }
      to { opacity: 1; transform: translateX(0); }
    }

    /* ============ NOSOTROS ============ */
    #nosotros {
      padding: 100px 0;
      background: var(--gray-light);
    }
    .nosotros-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: center;
    }
    .nosotros-text .section-subtitle { margin-bottom: 32px; }
    .historia-text {
      font-size: 0.95rem;
      color: var(--gray-dark);
      line-height: 1.8;
      margin-bottom: 32px;
    }
    .mv-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }
    .mv-card {
      background: var(--white);
      border-radius: var(--radius-sm);
      padding: 22px;
      box-shadow: var(--shadow);
      transition: var(--transition);
      border-left: 4px solid var(--blue);
    }
    .mv-card:hover {
      transform: translateY(-4px);
      box-shadow: var(--shadow-lg);
      border-left-color: var(--orange);
    }
    .mv-card-icon {
      width: 44px; height: 44px;
      background: linear-gradient(135deg, var(--blue), var(--orange));
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.2rem;
      margin-bottom: 12px;
    }
    .mv-card h4 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      font-size: 0.9rem;
      color: var(--blue);
      margin-bottom: 6px;
    }
    .mv-card p {
      font-size: 0.82rem;
      color: var(--gray-dark);
      line-height: 1.6;
    }

    .valores-side { }
    .valores-title {
      font-family: 'Montserrat', sans-serif;
      font-size: 1.3rem;
      font-weight: 800;
      color: var(--blue-dark);
      margin-bottom: 24px;
    }
    .valor-item {
      display: flex;
      align-items: flex-start;
      gap: 18px;
      padding: 20px;
      background: var(--white);
      border-radius: var(--radius-sm);
      box-shadow: var(--shadow);
      margin-bottom: 16px;
      transition: var(--transition);
    }
    .valor-item:hover {
      transform: translateX(6px);
      box-shadow: var(--shadow-lg);
    }
    .valor-icon {
      width: 50px; height: 50px;
      flex-shrink: 0;
      background: linear-gradient(135deg, rgba(30,58,138,0.1), rgba(249,115,22,0.1));
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.4rem;
      color: var(--orange);
      transition: var(--transition);
    }
    .valor-item:hover .valor-icon {
      background: linear-gradient(135deg, var(--blue), var(--orange));
      color: white;
    }
    .valor-content h4 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      font-size: 0.95rem;
      color: var(--blue);
      margin-bottom: 4px;
    }
    .valor-content p {
      font-size: 0.83rem;
      color: var(--gray-dark);
      line-height: 1.55;
    }

    /* ============ PRODUCTOS ============ */
    #productos {
      padding: 100px 0;
      background: var(--white);
    }
    .productos-header {
      text-align: center;
      margin-bottom: 50px;
    }
    .productos-header .section-subtitle { margin: 0 auto 32px; }

    .filter-tabs {
      display: flex;
      justify-content: center;
      gap: 12px;
      flex-wrap: wrap;
      margin-bottom: 44px;
    }
    .filter-btn {
      padding: 10px 26px;
      border-radius: 50px;
      font-family: 'Poppins', sans-serif;
      font-size: 0.85rem;
      font-weight: 600;
      cursor: pointer;
      border: 2px solid var(--gray-light);
      background: var(--white);
      color: var(--gray-dark);
      transition: var(--transition);
    }
    .filter-btn:hover,
    .filter-btn.active {
      background: var(--blue);
      color: var(--white);
      border-color: var(--blue);
    }

    .productos-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 28px;
    }
    .product-card {
      background: var(--white);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      overflow: hidden;
      transition: var(--transition);
      position: relative;
    }
    .product-card:hover {
      transform: translateY(-8px);
      box-shadow: var(--shadow-lg);
    }
    .product-card-img {
      height: 220px;
      position: relative;
      overflow: hidden;
      background: var(--gray-light);
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .product-card-img .product-emoji {
      font-size: 5rem;
      transition: transform 0.4s ease;
    }
    .product-card:hover .product-emoji { transform: scale(1.15) rotate(-5deg); }
    .product-badge {
      position: absolute;
      top: 14px; left: 14px;
      background: var(--orange);
      color: white;
      font-size: 0.72rem;
      font-weight: 700;
      padding: 4px 12px;
      border-radius: 50px;
      letter-spacing: 0.5px;
    }
    .product-wishlist {
      position: absolute;
      top: 12px; right: 14px;
      width: 34px; height: 34px;
      background: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      transition: var(--transition);
      border: none;
      color: var(--gray);
      font-size: 0.9rem;
    }
    .product-wishlist:hover { color: #ef4444; transform: scale(1.1); }
    .product-wishlist.active { color: #ef4444; }
    .product-body { padding: 20px; }
    .product-category {
      font-size: 0.72rem;
      font-weight: 600;
      color: var(--orange);
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-bottom: 6px;
    }
    .product-name {
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      font-size: 1rem;
      color: var(--text);
      margin-bottom: 8px;
    }
    .product-rating {
      display: flex;
      align-items: center;
      gap: 4px;
      margin-bottom: 12px;
    }
    .product-rating .stars { color: #fbbf24; font-size: 0.8rem; }
    .product-rating .count { font-size: 0.75rem; color: var(--gray); }
    .product-footer {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .product-price {
      font-family: 'Montserrat', sans-serif;
      font-weight: 800;
      font-size: 1.2rem;
      color: var(--blue);
    }
    .product-price .old-price {
      font-size: 0.8rem;
      color: var(--gray);
      text-decoration: line-through;
      font-weight: 500;
      display: block;
      margin-bottom: 2px;
    }
    .product-add-btn {
      width: 38px; height: 38px;
      background: var(--blue);
      color: white;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      border: none;
      font-size: 1rem;
      transition: var(--transition);
    }
    .product-add-btn:hover {
      background: var(--orange);
      transform: scale(1.1);
    }
    .product-card.hidden { display: none; }

    /* ============ SERVICIOS ============ */
    #servicios {
      padding: 100px 0;
      background: linear-gradient(135deg, var(--blue-dark), var(--blue));
      position: relative;
      overflow: hidden;
    }
    #servicios::before {
      content: '';
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
      background-size: 50px 50px;
    }
    .servicios-header {
      text-align: center;
      margin-bottom: 56px;
      position: relative;
    }
    .servicios-header .section-title { color: var(--white); }
    .servicios-header .section-subtitle { color: rgba(255,255,255,0.65); margin: 0 auto; }

    .servicios-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 28px;
      position: relative;
    }
    .servicio-card {
      background: rgba(255,255,255,0.07);
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255,255,255,0.12);
      border-radius: var(--radius);
      padding: 36px 28px;
      text-align: center;
      transition: var(--transition);
    }
    .servicio-card:hover {
      background: rgba(255,255,255,0.13);
      border-color: rgba(249,115,22,0.5);
      transform: translateY(-8px);
      box-shadow: 0 20px 40px rgba(0,0,0,0.2);
    }
    .servicio-icon {
      width: 72px; height: 72px;
      background: linear-gradient(135deg, rgba(249,115,22,0.25), rgba(249,115,22,0.05));
      border-radius: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      color: var(--orange);
      margin: 0 auto 20px;
      transition: var(--transition);
    }
    .servicio-card:hover .servicio-icon {
      background: var(--orange);
      color: white;
      transform: rotate(-8deg) scale(1.1);
    }
    .servicio-card h3 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      font-size: 1.05rem;
      color: var(--white);
      margin-bottom: 12px;
    }
    .servicio-card p {
      font-size: 0.85rem;
      color: rgba(255,255,255,0.6);
      line-height: 1.7;
    }

    /* ============ COTIZACION ============ */
    #cotizaciones {
      padding: 100px 0;
      background: var(--gray-light);
    }
    .cotizacion-grid {
      display: grid;
      grid-template-columns: 1fr 1.2fr;
      gap: 60px;
      align-items: start;
    }
    .cotizacion-info h2 {
      font-family: 'Montserrat', sans-serif;
      font-size: 2rem;
      font-weight: 800;
      color: var(--blue-dark);
      margin-bottom: 16px;
      line-height: 1.2;
    }
    .cotizacion-info h2 span { color: var(--orange); }
    .cotizacion-info p {
      font-size: 0.95rem;
      color: var(--gray-dark);
      line-height: 1.7;
      margin-bottom: 32px;
    }
    .cotizacion-feature {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 14px;
    }
    .cotizacion-feature-icon {
      width: 36px; height: 36px;
      background: rgba(249,115,22,0.12);
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--orange);
      font-size: 0.9rem;
      flex-shrink: 0;
    }
    .cotizacion-feature span {
      font-size: 0.9rem;
      font-weight: 500;
      color: var(--gray-dark);
    }

    .cotizacion-form-card {
      background: var(--white);
      border-radius: 24px;
      padding: 40px;
      box-shadow: var(--shadow-lg);
    }
    .cotizacion-form-card h3 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      font-size: 1.2rem;
      color: var(--blue);
      margin-bottom: 6px;
    }
    .cotizacion-form-card .form-subtitle {
      font-size: 0.85rem;
      color: var(--gray);
      margin-bottom: 28px;
    }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
    .form-group { margin-bottom: 18px; }
    .form-group label {
      display: block;
      font-size: 0.82rem;
      font-weight: 600;
      color: var(--text);
      margin-bottom: 6px;
    }
    .form-group input,
    .form-group select,
    .form-group textarea {
      width: 100%;
      padding: 12px 16px;
      border: 1.5px solid #E5E7EB;
      border-radius: var(--radius-sm);
      font-family: 'Poppins', sans-serif;
      font-size: 0.88rem;
      color: var(--text);
      background: var(--white);
      transition: border-color var(--transition);
      outline: none;
    }
    .form-group input:focus,
    .form-group select:focus,
    .form-group textarea:focus {
      border-color: var(--blue);
      box-shadow: 0 0 0 3px rgba(30,58,138,0.08);
    }
    .form-group textarea { resize: vertical; min-height: 100px; }
    .form-submit {
      width: 100%;
      padding: 15px;
      background: linear-gradient(135deg, var(--blue), var(--blue-light));
      color: white;
      border: none;
      border-radius: 50px;
      font-family: 'Poppins', sans-serif;
      font-weight: 700;
      font-size: 0.98rem;
      cursor: pointer;
      transition: var(--transition);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      margin-top: 8px;
    }
    .form-submit:hover {
      background: linear-gradient(135deg, var(--blue-dark), var(--blue));
      transform: translateY(-2px);
      box-shadow: 0 8px 28px rgba(30,58,138,.35);
    }
    .form-success {
      display: none;
      text-align: center;
      padding: 32px 0;
    }
    .form-success .success-icon {
      font-size: 4rem;
      margin-bottom: 16px;
      animation: bounceIn 0.6s ease;
    }
    .form-success h4 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      font-size: 1.3rem;
      color: var(--blue);
      margin-bottom: 8px;
    }
    .form-success p {
      font-size: 0.9rem;
      color: var(--gray-dark);
    }
    @keyframes bounceIn {
      0% { transform: scale(0); }
      60% { transform: scale(1.2); }
      100% { transform: scale(1); }
    }

    /* ============ TESTIMONIOS ============ */
    #testimonios {
      padding: 100px 0;
      background: var(--white);
    }
    .testimonios-header { text-align: center; margin-bottom: 52px; }
    .testimonios-header .section-subtitle { margin: 0 auto; }
    .testimonios-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 28px;
    }
    .testimonio-card {
      background: var(--gray-light);
      border-radius: var(--radius);
      padding: 32px;
      position: relative;
      transition: var(--transition);
    }
    .testimonio-card:hover {
      background: var(--white);
      box-shadow: var(--shadow-lg);
      transform: translateY(-6px);
    }
    .quote-icon {
      font-size: 3rem;
      color: rgba(249,115,22,0.2);
      font-family: Georgia, serif;
      line-height: 1;
      margin-bottom: 16px;
    }
    .testimonio-text {
      font-size: 0.9rem;
      color: var(--gray-dark);
      line-height: 1.75;
      margin-bottom: 24px;
      font-style: italic;
    }
    .testimonio-author {
      display: flex;
      align-items: center;
      gap: 14px;
    }
    .author-avatar {
      width: 48px; height: 48px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--blue), var(--orange));
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-weight: 700;
      font-size: 1rem;
      flex-shrink: 0;
    }
    .author-name {
      font-weight: 700;
      font-size: 0.9rem;
      color: var(--text);
    }
    .author-role {
      font-size: 0.78rem;
      color: var(--gray);
    }
    .testimonio-stars { color: #fbbf24; font-size: 0.8rem; margin-top: 3px; }

    /* ============ CONTACTO ============ */
    #contacto {
      padding: 100px 0;
      background: var(--gray-light);
    }
    .contacto-grid {
      display: grid;
      grid-template-columns: 1.1fr 1fr;
      gap: 60px;
      align-items: start;
    }
    .contacto-form-card {
      background: var(--white);
      border-radius: 24px;
      padding: 40px;
      box-shadow: var(--shadow);
    }
    .contacto-info { }
    .contacto-info-title {
      font-family: 'Montserrat', sans-serif;
      font-size: 1.8rem;
      font-weight: 800;
      color: var(--blue-dark);
      line-height: 1.2;
      margin-bottom: 16px;
    }
    .contacto-info-title span { color: var(--orange); }
    .contacto-info-desc {
      font-size: 0.95rem;
      color: var(--gray-dark);
      line-height: 1.7;
      margin-bottom: 36px;
    }
    .contact-item {
      display: flex;
      align-items: flex-start;
      gap: 16px;
      margin-bottom: 22px;
    }
    .contact-item-icon {
      width: 50px; height: 50px;
      background: linear-gradient(135deg, var(--blue), var(--orange));
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.1rem;
      flex-shrink: 0;
    }
    .contact-item-text h4 {
      font-weight: 700;
      font-size: 0.88rem;
      color: var(--blue);
      margin-bottom: 3px;
    }
    .contact-item-text p {
      font-size: 0.85rem;
      color: var(--gray-dark);
      line-height: 1.5;
    }
    .social-links {
      display: flex;
      gap: 12px;
      margin-top: 32px;
    }
    .social-link {
      width: 44px; height: 44px;
      border-radius: 12px;
      background: var(--white);
      box-shadow: var(--shadow);
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--blue);
      font-size: 1.1rem;
      transition: var(--transition);
      text-decoration: none;
    }
    .social-link:hover {
      background: var(--blue);
      color: white;
      transform: translateY(-4px);
      box-shadow: var(--shadow-lg);
    }

    /* ============ FOOTER ============ */
    footer {
      background: var(--blue-dark);
      color: rgba(255,255,255,0.7);
      padding: 64px 0 0;
    }
    .footer-grid {
      display: grid;
      grid-template-columns: 1.5fr 1fr 1fr 1fr;
      gap: 48px;
      margin-bottom: 48px;
    }
    .footer-brand .nav-logo { margin-bottom: 18px; }
    .footer-brand p {
      font-size: 0.85rem;
      line-height: 1.7;
      color: rgba(255,255,255,0.55);
      margin-bottom: 24px;
    }
    .footer-col h4 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      font-size: 0.9rem;
      color: white;
      margin-bottom: 18px;
      letter-spacing: 0.5px;
    }
    .footer-col ul li {
      margin-bottom: 10px;
    }
    .footer-col ul li a {
      font-size: 0.84rem;
      color: rgba(255,255,255,0.55);
      transition: color var(--transition);
    }
    .footer-col ul li a:hover { color: var(--orange); }
    .footer-bottom {
      border-top: 1px solid rgba(255,255,255,0.1);
      padding: 22px 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 12px;
    }
    .footer-bottom p { font-size: 0.82rem; }
    .footer-bottom span { color: var(--orange); }

    /* ============ FLOATING CART ============ */
    .cart-bubble {
      position: fixed;
      bottom: 30px; right: 30px;
      width: 58px; height: 58px;
      background: linear-gradient(135deg, var(--blue), var(--orange));
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.4rem;
      cursor: pointer;
      box-shadow: 0 8px 28px rgba(249,115,22,0.4);
      z-index: 500;
      transition: var(--transition);
      border: none;
    }
    .cart-bubble:hover { transform: scale(1.12); box-shadow: 0 12px 36px rgba(249,115,22,0.5); }
    .cart-count {
      position: absolute;
      top: -4px; right: -4px;
      width: 22px; height: 22px;
      background: #ef4444;
      color: white;
      border-radius: 50%;
      font-size: 0.72rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      justify-content: center;
      border: 2px solid white;
      display: none;
    }

    /* ============ BACK TO TOP ============ */
    .back-to-top {
      position: fixed;
      bottom: 100px; right: 30px;
      width: 44px; height: 44px;
      background: var(--white);
      color: var(--blue);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
      cursor: pointer;
      box-shadow: var(--shadow);
      z-index: 500;
      transition: var(--transition);
      border: none;
      opacity: 0;
      pointer-events: none;
    }
    .back-to-top.visible { opacity: 1; pointer-events: all; }
    .back-to-top:hover { background: var(--blue); color: white; transform: translateY(-4px); }

    /* ============ NOTIFICATION ============ */
    .notification {
      position: fixed;
      top: 90px; right: 24px;
      background: var(--white);
      border-radius: 14px;
      padding: 16px 20px;
      box-shadow: 0 8px 32px rgba(0,0,0,0.15);
      z-index: 1100;
      display: flex;
      align-items: center;
      gap: 14px;
      max-width: 300px;
      transform: translateX(120%);
      transition: transform 0.4s cubic-bezier(.4,0,.2,1);
      border-left: 4px solid var(--orange);
    }
    .notification.show { transform: translateX(0); }
    .notification-icon { font-size: 1.5rem; }
    .notification-text strong {
      display: block;
      font-size: 0.88rem;
      color: var(--text);
      margin-bottom: 2px;
    }
    .notification-text span {
      font-size: 0.78rem;
      color: var(--gray);
    }

    /* ============ RESPONSIVE ============ */
    @media (max-width: 1024px) {
      .nosotros-grid { grid-template-columns: 1fr; gap: 48px; }
      .cotizacion-grid { grid-template-columns: 1fr; }
      .contacto-grid { grid-template-columns: 1fr; }
      .footer-grid { grid-template-columns: 1fr 1fr; }
      .hero-image-side { display: none; }
    }
    @media (max-width: 768px) {
      .nav-links, .nav-cta { display: none; }
      .hamburger { display: flex; }
      .hero-stats { gap: 24px; }
      .form-row { grid-template-columns: 1fr; }
      .footer-grid { grid-template-columns: 1fr; gap: 32px; }
      .footer-bottom { flex-direction: column; text-align: center; }
      .mv-grid { grid-template-columns: 1fr; }
    }
    @media (max-width: 480px) {
      .hero-actions { flex-direction: column; align-items: flex-start; }
      .cotizacion-form-card { padding: 24px; }
      .contacto-form-card { padding: 24px; }
    }
  </style>
</head>
<body>

<!-- ===== NOTIFICATION ===== -->
<div class="notification" id="notification">
  <div class="notification-icon">🛒</div>
  <div class="notification-text">
    <strong id="notif-title">Producto agregado</strong>
    <span id="notif-sub">Se añadió al carrito</span>
  </div>
</div>

<!-- ===== NAVBAR ===== -->
<nav id="navbar">
  <div class="container">
    <div class="nav-inner">
      <a href="#inicio" class="nav-logo">
        <div class="nav-logo-icon"><img src="data:image/png;base64,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fQiquSxlstLKfaUjEHmU1II0RmN826PjG/8drVFgWnm5tBnlCKWndF+S56xAMmP1zNC3xsSlUqfTUUoppaSUaZrecMMN77ji7UVReJ43NjY2Z84cAOPj47t27br00kuffPLJer2utdZap2nqdoNj8EEYuiCe53me52AWUlar1Ze//OVuGfI8bzabbksR0cqVK9etW/fHl146MDg4OTkZBIGUspMkSusTTjjhD//wD88999y5c+e2Wq3BOYOFsYFW1pjvfPtbn/jEJ771rW+lWQHII4459olNo2ec++r/9b4Prjx28XgLF/35e35414+x+NjBpUcEMuiv9Nsk4TztTI/v2vYY59O2M4lkGmkbRQFmQEBEkApKwNOIq9HQ/Nr8FfHA4qnMF34tLZCnnZKPagnZ9J76rkfSx78Dsw861ZxyzoHWSpSTohBSWvUU9MXToO+4ChGVSqV2uw3mFx9//Pr168PA63Q6LiUSUbPZHB0dPeecc3bv3u3gVkr5vu95nsNaKs8Y42iSk3dcwkw7nUpfX5ZleZatXrPmsssuW7NmTavViqIoDMOdO3cefvjho6Ojr3zlK11SsdZedNFFF1544fDw8Pbt2/ft2+eSwe59Y8uXL1+2ZPHceXNqlSpg161b95WvfOUr//zVpJMdcczKnzz4oNRo5/B9bNjUOOW4kzGy/MUnrY3DSt5MH97wYDa1D/u2gTtAG8jAGUBKytDzlA6m28VMASwY0Aj6MLg4qC2cv+yElokyjqBCCCIqFPKKrO+8/59Rfxy2IWUubaFZSpQyIiGlVQWrFAKCIBnClg6KvhNtXKos8hzADR/96DvecTl13ywKa+3GjRvf8pa3PPTQQ2EYep6X53nmZJBZyLQXdEOZy8+OcQZB4BSegcHBoigAnH322RdddNHIyMjY2NjAwECr1XIM9Yorrti8efPq1avb7fb4+PjExIS11qUlJlJBaPN86dLD3/mX77jkwovCOOAi7+TF1772tf/9gb8+4b+deNs/3GYBw2BgvIUlC46IFy5fvODwXzyxOdu2A319L1q2aM/OX+SdScUJmzabFKYAuQaksiLQXqA9aYk6eQHSEGWI/trKkzmap8vz4felJAtiKF1VjWL7vfUt96G5DV6hbYYCSkaWFYSYQd+JSQxho4NHHmudC7dbrSAMh4aGfvazn0VR5GnpUqWjgGvX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" alt="Infinity Sports Logo" /></div>
        <span class="nav-logo-text">Infinity <span>Sports</span></span>
      </a>
      <ul class="nav-links">
        <li><a href="#inicio" class="active">Inicio</a></li>
        <li><a href="#nosotros">Nosotros</a></li>
        <li><a href="#productos">Productos</a></li>
        <li><a href="#servicios">Servicios</a></li>
        <li><a href="#cotizaciones">Cotizaciones</a></li>
        <li><a href="#contacto">Contacto</a></li>
      </ul>
      <div class="nav-cta">
        <a href="#cotizaciones" class="btn btn-primary" style="padding:10px 22px;font-size:0.85rem;">
          <i class="fas fa-file-invoice"></i> Solicitar Cotización
        </a>
      </div>
      <button class="hamburger" id="hamburger" aria-label="Menú">
        <span></span><span></span><span></span>
      </button>
    </div>
  </div>
</nav>

<!-- Mobile Menu -->
<div class="mobile-menu" id="mobileMenu">
  <button class="mobile-menu-close" id="mobileClose"><i class="fas fa-times"></i></button>
  <a href="#inicio" onclick="closeMobile()">Inicio</a>
  <a href="#nosotros" onclick="closeMobile()">Nosotros</a>
  <a href="#productos" onclick="closeMobile()">Productos</a>
  <a href="#servicios" onclick="closeMobile()">Servicios</a>
  <a href="#cotizaciones" onclick="closeMobile()">Cotizaciones</a>
  <a href="#contacto" onclick="closeMobile()">Contacto</a>
  <a href="#cotizaciones" class="btn btn-primary" onclick="closeMobile()">Solicitar Cotización</a>
</div>

<!-- ===== HERO ===== -->
<section id="inicio">
  <div id="hero">
    <div class="hero-bg-shapes">
      <div class="shape shape-1"></div>
      <div class="shape shape-2"></div>
      <div class="shape shape-3"></div>
    </div>
    <div class="hero-grid-lines"></div>
    <div class="container">
      <div class="hero-content">
        <div class="hero-badge">
          <i class="fas fa-star"></i>
          #1 en Distribución Deportiva
        </div>
        <h1 class="hero-title">
          Todo lo que necesitas para tu<br>
          <span>vida deportiva</span>
        </h1>
        <p class="hero-subtitle">
          Más de 10.000 productos disponibles. Ropa deportiva para hombre, mujer y equipos de fútbol de alta calidad a los mejores precios del mercado.
        </p>
        <div class="hero-actions">
          <a href="#productos" class="btn btn-primary">
            <i class="fas fa-th-large"></i> Ver Catálogo
          </a>
          <a href="#cotizaciones" class="btn btn-secondary">
            <i class="fas fa-file-invoice"></i> Solicitar Cotización
          </a>
        </div>
        <div class="hero-stats">
          <div class="hero-stat-item">
            <div class="hero-stat-num" data-count="10000">0</div>
            <div class="hero-stat-label">Productos</div>
          </div>
          <div class="hero-stat-item">
            <div class="hero-stat-num" data-count="5000">0</div>
            <div class="hero-stat-label">Clientes activos</div>
          </div>
          <div class="hero-stat-item">
            <div class="hero-stat-num" data-count="15">0</div>
            <div class="hero-stat-label">Años de experiencia</div>
          </div>
          <div class="hero-stat-item">
            <div class="hero-stat-num" data-count="98">0</div>
            <div class="hero-stat-label">% Satisfacción</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Hero side visual -->
    <div class="hero-image-side">
      <div class="hero-visual">
        <div class="hero-card-main">
          <div class="hero-card-icons">
            <div class="hero-icon-box">
              <i class="fas fa-running"></i>
              <span>Running</span>
            </div>
            <div class="hero-icon-box">
              <i class="fas fa-futbol"></i>
              <span>Fútbol</span>
            </div>
            <div class="hero-icon-box">
              <i class="fas fa-dumbbell"></i>
              <span>Gym</span>
            </div>
            <div class="hero-icon-box">
              <i class="fas fa-tshirt"></i>
              <span>Camisetas</span>
            </div>
            <div class="hero-icon-box">
              <i class="fas fa-shoe-prints"></i>
              <span>Calzado</span>
            </div>
            <div class="hero-icon-box">
              <i class="fas fa-socks"></i>
              <span>Accesorios</span>
            </div>
          </div>
          <div class="hero-progress-section">
            <div class="hero-progress-item">
              <div class="hero-progress-header"><span>Popularidad: Fútbol</span><span>92%</span></div>
              <div class="hero-progress-bar"><div class="hero-progress-fill" style="width:0" data-width="92%"></div></div>
            </div>
            <div class="hero-progress-item">
              <div class="hero-progress-header"><span>Popularidad: Running</span><span>78%</span></div>
              <div class="hero-progress-bar"><div class="hero-progress-fill" style="width:0" data-width="78%"></div></div>
            </div>
            <div class="hero-progress-item">
              <div class="hero-progress-header"><span>Popularidad: Gym</span><span>85%</span></div>
              <div class="hero-progress-bar"><div class="hero-progress-fill" style="width:0" data-width="85%"></div></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ===== NOSOTROS ===== -->
<section id="nosotros">
  <div class="container">
    <div class="nosotros-grid">
      <div class="nosotros-text reveal-left">
        <span class="section-tag">Quiénes Somos</span>
        <h2 class="section-title">Nuestra <span>Historia</span></h2>
        <p class="historia-text">
          Infinity Sports nació en 2010 con la misión de democratizar el acceso a ropa deportiva de alta calidad. Lo que comenzó como una pequeña distribuidora local hoy es una empresa líder en el mercado con presencia en todo el país, respaldada por alianzas estratégicas con las mejores marcas del mundo.
        </p>
        <p class="historia-text">
          Durante más de 15 años hemos vestido a atletas, equipos amateur y profesionales, brindando soluciones integrales para todas las disciplinas deportivas y sus necesidades de indumentaria.
        </p>
        <div class="mv-grid">
          <div class="mv-card reveal" style="transition-delay:0.1s">
            <div class="mv-card-icon"><i class="fas fa-crosshairs"></i></div>
            <h4>Misión</h4>
            <p>Proveer ropa deportiva de calidad superior a precios accesibles, impulsando el deporte en todos los niveles.</p>
          </div>
          <div class="mv-card reveal" style="transition-delay:0.2s">
            <div class="mv-card-icon"><i class="fas fa-eye"></i></div>
            <h4>Visión</h4>
            <p>Ser el distribuidor deportivo número uno de Latinoamérica para 2030.</p>
          </div>
        </div>
      </div>

      <div class="valores-side reveal-right">
        <p class="valores-title">Nuestros <span style="color:var(--orange)">Valores</span></p>
        <div class="valor-item">
          <div class="valor-icon"><i class="fas fa-medal"></i></div>
          <div class="valor-content">
            <h4>Calidad</h4>
            <p>Cada producto pasa por rigurosos controles de calidad para garantizar durabilidad y rendimiento óptimos.</p>
          </div>
        </div>
        <div class="valor-item">
          <div class="valor-icon"><i class="fas fa-handshake"></i></div>
          <div class="valor-content">
            <h4>Confianza</h4>
            <p>Construimos relaciones de largo plazo basadas en la transparencia y el compromiso con nuestros clientes.</p>
          </div>
        </div>
        <div class="valor-item">
          <div class="valor-icon"><i class="fas fa-bolt"></i></div>
          <div class="valor-content">
            <h4>Innovación</h4>
            <p>Estamos siempre a la vanguardia de las tendencias y tecnologías en indumentaria deportiva.</p>
          </div>
        </div>
        <div class="valor-item">
          <div class="valor-icon"><i class="fas fa-leaf"></i></div>
          <div class="valor-content">
            <h4>Sostenibilidad</h4>
            <p>Apostamos por materiales sostenibles y procesos responsables con el medio ambiente.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ===== PRODUCTOS ===== -->
<section id="productos">
  <div class="container">
    <div class="productos-header reveal">
      <span class="section-tag">Catálogo</span>
      <h2 class="section-title">Nuestros <span>Productos</span></h2>
      <p class="section-subtitle">Descubre nuestra colección completa de ropa deportiva para hombre, mujer y equipos de fútbol.</p>
    </div>

    <div class="filter-tabs reveal">
      <button class="filter-btn active" data-filter="all">Todos</button>
      <button class="filter-btn" data-filter="hombre">Hombre</button>
      <button class="filter-btn" data-filter="mujer">Mujer</button>
      <button class="filter-btn" data-filter="futbol">Fútbol</button>
      <button class="filter-btn" data-filter="accesorios">Accesorios</button>
    </div>

    <div class="productos-grid" id="productosGrid">
      <!-- Products injected by JS -->
    </div>
  </div>
</section>

<!-- ===== SERVICIOS ===== -->
<section id="servicios">
  <div class="container">
    <div class="servicios-header reveal">
      <span class="section-tag">Lo que ofrecemos</span>
      <h2 class="section-title">Nuestros <span>Servicios</span></h2>
      <p class="section-subtitle">Soluciones integrales para individuos, equipos y empresas que buscan excelencia deportiva.</p>
    </div>
    <div class="servicios-grid">
      <div class="servicio-card reveal" style="transition-delay:0s">
        <div class="servicio-icon"><i class="fas fa-truck"></i></div>
        <h3>Distribución Mayorista</h3>
        <p>Grandes volúmenes con precios preferenciales. Ideal para tiendas, gimnasios y clubes deportivos.</p>
      </div>
      <div class="servicio-card reveal" style="transition-delay:0.1s">
        <div class="servicio-icon"><i class="fas fa-paint-brush"></i></div>
        <h3>Uniformes Personalizados</h3>
        <p>Diseñamos y fabricamos uniformes a medida con el logo y colores de tu equipo o empresa.</p>
      </div>
      <div class="servicio-card reveal" style="transition-delay:0.2s">
        <div class="servicio-icon"><i class="fas fa-users"></i></div>
        <h3>Equipamiento de Equipos</h3>
        <p>Paquetes completos para equipos de fútbol: camisetas, shorts, medias, balones y más.</p>
      </div>
      <div class="servicio-card reveal" style="transition-delay:0.3s">
        <div class="servicio-icon"><i class="fas fa-tags"></i></div>
        <h3>Asesoría de Compra</h3>
        <p>Nuestros expertos te orientan para elegir los mejores productos según tu deporte y presupuesto.</p>
      </div>
      <div class="servicio-card reveal" style="transition-delay:0.4s">
        <div class="servicio-icon"><i class="fas fa-box-open"></i></div>
        <h3>Envío a Todo el País</h3>
        <p>Logística eficiente con entrega rápida y segura en cualquier ciudad del territorio nacional.</p>
      </div>
      <div class="servicio-card reveal" style="transition-delay:0.5s">
        <div class="servicio-icon"><i class="fas fa-headset"></i></div>
        <h3>Soporte Post-Venta</h3>
        <p>Atención al cliente personalizada y garantía de satisfacción en todos nuestros productos.</p>
      </div>
    </div>
  </div>
</section>

<!-- ===== COTIZACION ===== -->
<section id="cotizaciones">
  <div class="container">
    <div class="cotizacion-grid">
      <div class="reveal-left">
        <span class="section-tag">Cotizaciones</span>
        <div class="cotizacion-info">
          <h2>¿Necesitas una <span>cotización</span> personalizada?</h2>
          <p>Completa el formulario y uno de nuestros asesores te contactará en menos de 24 horas con la mejor propuesta para tu equipo o negocio.</p>
          <div class="cotizacion-feature">
            <div class="cotizacion-feature-icon"><i class="fas fa-check"></i></div>
            <span>Respuesta en menos de 24 horas</span>
          </div>
          <div class="cotizacion-feature">
            <div class="cotizacion-feature-icon"><i class="fas fa-check"></i></div>
            <span>Precios especiales para pedidos en volumen</span>
          </div>
          <div class="cotizacion-feature">
            <div class="cotizacion-feature-icon"><i class="fas fa-check"></i></div>
            <span>Personalización de uniformes incluida</span>
          </div>
          <div class="cotizacion-feature">
            <div class="cotizacion-feature-icon"><i class="fas fa-check"></i></div>
            <span>Sin costo adicional por asesoría</span>
          </div>
          <div class="cotizacion-feature">
            <div class="cotizacion-feature-icon"><i class="fas fa-check"></i></div>
            <span>Envío gratis en pedidos mayores a $500.000</span>
          </div>
        </div>
      </div>

      <div class="reveal-right">
        <div class="cotizacion-form-card">
          <h3>Solicitar Cotización</h3>
          <p class="form-subtitle">Todos los campos son obligatorios</p>
          <div id="formContent">
            <div class="form-row">
              <div class="form-group">
                <label>Nombre</label>
                <input type="text" id="cot-nombre" placeholder="Tu nombre" />
              </div>
              <div class="form-group">
                <label>Apellido</label>
                <input type="text" id="cot-apellido" placeholder="Tu apellido" />
              </div>
            </div>
            <div class="form-group">
              <label>Correo Electrónico</label>
              <input type="email" id="cot-email" placeholder="tucorreo@ejemplo.com" />
            </div>
            <div class="form-group">
              <label>Teléfono / WhatsApp</label>
              <input type="tel" id="cot-tel" placeholder="+57 300 000 0000" />
            </div>
            <div class="form-row">
              <div class="form-group">
                <label>Tipo de Producto</label>
                <select id="cot-tipo">
                  <option value="">Seleccionar...</option>
                  <option>Ropa Hombre</option>
                  <option>Ropa Mujer</option>
                  <option>Equipos de Fútbol</option>
                  <option>Uniformes Personalizados</option>
                  <option>Accesorios</option>
                  <option>Paquete Completo</option>
                </select>
              </div>
              <div class="form-group">
                <label>Cantidad estimada</label>
                <select id="cot-cantidad">
                  <option value="">Seleccionar...</option>
                  <option>1-10 unidades</option>
                  <option>11-50 unidades</option>
                  <option>51-200 unidades</option>
                  <option>Más de 200</option>
                </select>
              </div>
            </div>
            <div class="form-group">
              <label>Mensaje / Detalles adicionales</label>
              <textarea id="cot-mensaje" placeholder="Cuéntanos más sobre tus necesidades, talla, colores, logos..."></textarea>
            </div>
            <button class="form-submit" onclick="submitCotizacion()">
              <i class="fas fa-paper-plane"></i> Enviar Cotización
            </button>
          </div>
          <div class="form-success" id="formSuccess">
            <div class="success-icon">✅</div>
            <h4>¡Cotización enviada!</h4>
            <p>Gracias por contactarnos. Un asesor se comunicará contigo en las próximas 24 horas.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ===== TESTIMONIOS ===== -->
<section id="testimonios">
  <div class="container">
    <div class="testimonios-header reveal">
      <span class="section-tag">Testimonios</span>
      <h2 class="section-title">Lo que dicen <span>nuestros clientes</span></h2>
      <p class="section-subtitle">Miles de clientes satisfechos en todo el país confían en Infinity Sports para sus necesidades deportivas.</p>
    </div>
    <div class="testimonios-grid" id="testimoniosGrid">
      <!-- Testimonios injected by JS -->
    </div>
  </div>
</section>

<!-- ===== CONTACTO ===== -->
<section id="contacto">
  <div class="container">
    <div class="contacto-grid">
      <div class="reveal-left">
        <div class="contacto-form-card">
          <h3 style="font-family:'Montserrat',sans-serif;font-weight:800;font-size:1.2rem;color:var(--blue);margin-bottom:6px;">Envíanos un Mensaje</h3>
          <p style="font-size:0.85rem;color:var(--gray);margin-bottom:26px;">Estamos listos para ayudarte</p>
          <div class="form-row">
            <div class="form-group">
              <label>Nombre</label>
              <input type="text" placeholder="Tu nombre" />
            </div>
            <div class="form-group">
              <label>Email</label>
              <input type="email" placeholder="tucorreo@mail.com" />
            </div>
          </div>
          <div class="form-group">
            <label>Asunto</label>
            <input type="text" placeholder="¿En qué podemos ayudarte?" />
          </div>
          <div class="form-group">
            <label>Mensaje</label>
            <textarea placeholder="Escribe tu mensaje aquí..."></textarea>
          </div>
          <button class="form-submit" onclick="submitContact(this)">
            <i class="fas fa-paper-plane"></i> Enviar Mensaje
          </button>
        </div>
      </div>

      <div class="contacto-info reveal-right">
        <span class="section-tag">Contacto</span>
        <h2 class="contacto-info-title">Hablemos sobre tu <span>proyecto</span></h2>
        <p class="contacto-info-desc">Nuestro equipo está disponible para atenderte de lunes a sábado. No dudes en contactarnos por el canal que prefieras.</p>
        <div class="contact-item">
          <div class="contact-item-icon"><i class="fas fa-map-marker-alt"></i></div>
          <div class="contact-item-text">
            <h4>Dirección</h4>
            <p>Calle 50 #30-15, Centro Comercial Deportivo<br>Bogotá, Colombia</p>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-item-icon"><i class="fas fa-phone"></i></div>
          <div class="contact-item-text">
            <h4>Teléfonos</h4>
            <p>+57 (1) 234-5678<br>+57 300 123 4567 (WhatsApp)</p>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-item-icon"><i class="fas fa-envelope"></i></div>
          <div class="contact-item-text">
            <h4>Email</h4>
            <p>info@sportpro.com.co<br>ventas@sportpro.com.co</p>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-item-icon"><i class="fas fa-clock"></i></div>
          <div class="contact-item-text">
            <h4>Horario de Atención</h4>
            <p>Lunes a Viernes: 8:00 AM - 6:00 PM<br>Sábados: 9:00 AM - 2:00 PM</p>
          </div>
        </div>
        <div class="social-links">
          <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
          <a href="#" class="social-link"><i class="fab fa-facebook"></i></a>
          <a href="#" class="social-link"><i class="fab fa-whatsapp"></i></a>
          <a href="#" class="social-link"><i class="fab fa-tiktok"></i></a>
          <a href="#" class="social-link"><i class="fab fa-youtube"></i></a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ===== FOOTER ===== -->
<footer>
  <div class="container">
    <div class="footer-grid">
      <div class="footer-brand">
        <div class="nav-logo">
          <div class="nav-logo-icon"><img src="data:image/png;base64,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fQiquSxlstLKfaUjEHmU1II0RmN826PjG/8drVFgWnm5tBnlCKWndF+S56xAMmP1zNC3xsSlUqfTUUoppaSUaZrecMMN77ji7UVReJ43NjY2Z84cAOPj47t27br00kuffPLJer2utdZap2nqdoNj8EEYuiCe53me52AWUlar1Ze//OVuGfI8bzabbksR0cqVK9etW/fHl146MDg4OTkZBIGUspMkSusTTjjhD//wD88999y5c+e2Wq3BOYOFsYFW1pjvfPtbn/jEJ771rW+lWQHII4459olNo2ec++r/9b4Prjx28XgLF/35e35414+x+NjBpUcEMuiv9Nsk4TztTI/v2vYY59O2M4lkGmkbRQFmQEBEkApKwNOIq9HQ/Nr8FfHA4qnMF34tLZCnnZKPagnZ9J76rkfSx78Dsw861ZxyzoHWSpSTohBSWvUU9MXToO+4ChGVSqV2uw3mFx9//Pr168PA63Q6LiUSUbPZHB0dPeecc3bv3u3gVkr5vu95nsNaKs8Y42iSk3dcwkw7nUpfX5ZleZatXrPmsssuW7NmTavViqIoDMOdO3cefvjho6Ojr3zlK11SsdZedNFFF1544fDw8Pbt2/ft2+eSwe59Y8uXL1+2ZPHceXNqlSpg161b95WvfOUr//zVpJMdcczKnzz4oNRo5/B9bNjUOOW4kzGy/MUnrY3DSt5MH97wYDa1D/u2gTtAG8jAGUBKytDzlA6m28VMASwY0Aj6MLg4qC2cv+yElokyjqBCCCIqFPKKrO+8/59Rfxy2IWUubaFZSpQyIiGlVQWrFAKCIBnClg6KvhNtXKos8hzADR/96DvecTl13ywKa+3GjRvf8pa3PPTQQ2EYep6X53nmZJBZyLQXdEOZy8+OcQZB4BSegcHBoigAnH322RdddNHIyMjY2NjAwECr1XIM9Yorrti8efPq1avb7fb4+PjExIS11qUlJlJBaPN86dLD3/mX77jkwovCOOAi7+TF1772tf/9gb8+4b+deNs/3GYBw2BgvIUlC46IFy5fvODwXzyxOdu2A319L1q2aM/OX+SdScUJmzabFKYAuQaksiLQXqA9aYk6eQHSEGWI/trKkzmap8vz4felJAtiKF1VjWL7vfUt96G5DV6hbYYCSkaWFYSYQd+JSQxho4NHHmudC7dbrSAMh4aGfvazn0VR5GnpUqWjgGvX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" alt="Infinity Sports Logo" /></div>
          <span class="nav-logo-text" style="color:white">Infinity <span>Sports</span></span>
        </div>
        <p>Líderes en distribución de ropa deportiva y equipos de fútbol. Calidad, variedad y precio al servicio del deporte colombiano.</p>
        <div class="social-links">
          <a href="#" class="social-link" style="background:rgba(255,255,255,0.1);color:rgba(255,255,255,0.7)"><i class="fab fa-instagram"></i></a>
          <a href="#" class="social-link" style="background:rgba(255,255,255,0.1);color:rgba(255,255,255,0.7)"><i class="fab fa-facebook"></i></a>
          <a href="#" class="social-link" style="background:rgba(255,255,255,0.1);color:rgba(255,255,255,0.7)"><i class="fab fa-whatsapp"></i></a>
          <a href="#" class="social-link" style="background:rgba(255,255,255,0.1);color:rgba(255,255,255,0.7)"><i class="fab fa-tiktok"></i></a>
        </div>
      </div>
      <div class="footer-col">
        <h4>Navegación</h4>
        <ul>
          <li><a href="#inicio">Inicio</a></li>
          <li><a href="#nosotros">Nosotros</a></li>
          <li><a href="#productos">Productos</a></li>
          <li><a href="#servicios">Servicios</a></li>
          <li><a href="#cotizaciones">Cotizaciones</a></li>
          <li><a href="#contacto">Contacto</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Categorías</h4>
        <ul>
          <li><a href="#">Ropa Hombre</a></li>
          <li><a href="#">Ropa Mujer</a></li>
          <li><a href="#">Equipos Fútbol</a></li>
          <li><a href="#">Calzado</a></li>
          <li><a href="#">Accesorios</a></li>
          <li><a href="#">Uniformes</a></li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Legal</h4>
        <ul>
          <li><a href="#">Política de Privacidad</a></li>
          <li><a href="#">Términos y Condiciones</a></li>
          <li><a href="#">Política de Devoluciones</a></li>
          <li><a href="#">Garantías</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <p>© 2025 <span>Infinity Sports</span>. Todos los derechos reservados.</p>
      <p>Hecho con <span>♥</span> en Colombia 🇨🇴</p>
    </div>
  </div>
</footer>

<!-- Floating Cart -->
<button class="cart-bubble" id="cartBubble" onclick="openCart()" title="Ver carrito">
  <i class="fas fa-shopping-cart"></i>
  <span class="cart-count" id="cartCount">0</span>
</button>

<!-- Back to top -->
<button class="back-to-top" id="backToTop" onclick="window.scrollTo({top:0,behavior:'smooth'})">
  <i class="fas fa-chevron-up"></i>
</button>

<!-- ===== JAVASCRIPT ===== -->
<script>
  // ======== PRODUCTS DATA ========
  const products = [
    { id:1, name:'Camiseta Técnica Dri-Fit', category:'hombre', price:'89.900', oldPrice:'120.000', badge:'Nuevo', emoji:'👕', rating:5, reviews:42 },
    { id:2, name:'Short Deportivo Pro', category:'hombre', price:'65.900', oldPrice:'85.000', badge:'Oferta', emoji:'🩲', rating:4, reviews:28 },
    { id:3, name:'Leggins Compression', category:'mujer', price:'95.900', oldPrice:'130.000', badge:'Top', emoji:'🩱', rating:5, reviews:67 },
    { id:4, name:'Top Deportivo X-Fit', category:'mujer', price:'72.900', oldPrice:'95.000', badge:'Nuevo', emoji:'👙', rating:4, reviews:33 },
    { id:5, name:'Uniforme Equipo Completo', category:'futbol', price:'185.000', oldPrice:'240.000', badge:'Combo', emoji:'⚽', rating:5, reviews:89 },
    { id:6, name:'Camiseta Fútbol Sublimada', category:'futbol', price:'75.000', oldPrice:'100.000', badge:null, emoji:'🏆', rating:4, reviews:54 },
    { id:7, name:'Botines de Fútbol', category:'futbol', price:'220.000', oldPrice:'290.000', badge:'Hot', emoji:'👟', rating:5, reviews:112 },
    { id:8, name:'Medias Antideslizantes', category:'accesorios', price:'28.900', oldPrice:null, badge:null, emoji:'🧦', rating:4, reviews:19 },
    { id:9, name:'Guantes de Arquero', category:'accesorios', price:'110.000', oldPrice:'145.000', badge:'Pro', emoji:'🥅', rating:5, reviews:41 },
    { id:10, name:'Mochila Deportiva 30L', category:'accesorios', price:'135.000', oldPrice:'170.000', badge:null, emoji:'🎒', rating:4, reviews:36 },
    { id:11, name:'Chaqueta Windbreaker', category:'hombre', price:'195.000', oldPrice:'250.000', badge:'Nuevo', emoji:'🧥', rating:5, reviews:22 },
    { id:12, name:'Conjunto Yoga Premium', category:'mujer', price:'165.000', oldPrice:'210.000', badge:'Tendencia', emoji:'🧘', rating:5, reviews:78 },
  ];

  const testimonios = [
    { name:'Carlos Ramírez', role:'Entrenador FC Olimpia', text:'Infinity Sports nos equipó a todo el equipo con uniformes personalizados de excelente calidad. La atención fue impecable y los precios muy competitivos.', initials:'CR', rating:5 },
    { name:'María Gómez', role:'Atleta profesional', text:'Compro mis implementos deportivos aquí desde hace 3 años. La variedad es impresionante y siempre encuentro exactamente lo que necesito para mi entrenamiento.', initials:'MG', rating:5 },
    { name:'Liga Deportiva Norte', role:'Organización deportiva', text:'Excelente servicio mayorista. Nos hacen la cotización rápido y los envíos siempre llegan a tiempo. Muy recomendados para equipos y ligas.', initials:'LD', rating:5 },
    { name:'Andrés Torres', role:'Dueño de gimnasio', text:'Proveemos a todo nuestro gimnasio con Infinity Sports. La relación calidad-precio es inmejorable y el soporte post-venta es de primer nivel.', initials:'AT', rating:4 },
    { name:'Sandra Jiménez', role:'Corredora aficionada', text:'Me encanta la ropa para running que tienen. Los materiales son de alta calidad y las tallas son exactas. Siempre vuelvo por más.', initials:'SJ', rating:5 },
    { name:'Club Fútbol Estrellas', role:'Club amateur', text:'Nos uniformaron completos con camisetas sublimadas de nuestros colores. Quedamos sorprendidos por la calidad a un precio muy accesible.', initials:'CF', rating:5 },
  ];

  // ======== RENDER PRODUCTS ========
  function renderProducts(filter = 'all') {
    const grid = document.getElementById('productosGrid');
    grid.innerHTML = '';
    const filtered = filter === 'all' ? products : products.filter(p => p.category === filter);
    filtered.forEach((p, i) => {
      const stars = '★'.repeat(p.rating) + '☆'.repeat(5 - p.rating);
      grid.innerHTML += `
        <div class="product-card reveal" style="transition-delay:${i * 0.07}s" data-category="${p.category}">
          <div class="product-card-img">
            <span class="product-emoji">${p.emoji}</span>
            ${p.badge ? `<span class="product-badge">${p.badge}</span>` : ''}
            <button class="product-wishlist" onclick="toggleWishlist(this)" title="Favorito">
              <i class="far fa-heart"></i>
            </button>
          </div>
          <div class="product-body">
            <div class="product-category">${p.category.charAt(0).toUpperCase() + p.category.slice(1)}</div>
            <div class="product-name">${p.name}</div>
            <div class="product-rating">
              <span class="stars">${stars}</span>
              <span class="count">(${p.reviews})</span>
            </div>
            <div class="product-footer">
              <div class="product-price">
                ${p.oldPrice ? `<span class="old-price">$${p.oldPrice}</span>` : ''}
                $${p.price}
              </div>
              <button class="product-add-btn" onclick="addToCart('${p.name}')" title="Agregar al carrito">
                <i class="fas fa-plus"></i>
              </button>
            </div>
          </div>
        </div>`;
    });
    initReveal();
  }

  // ======== RENDER TESTIMONIOS ========
  function renderTestimonios() {
    const grid = document.getElementById('testimoniosGrid');
    testimonios.forEach((t, i) => {
      const stars = '★'.repeat(t.rating) + '☆'.repeat(5 - t.rating);
      grid.innerHTML += `
        <div class="testimonio-card reveal" style="transition-delay:${i * 0.1}s">
          <div class="quote-icon">"</div>
          <p class="testimonio-text">${t.text}</p>
          <div class="testimonio-author">
            <div class="author-avatar">${t.initials}</div>
            <div>
              <div class="author-name">${t.name}</div>
              <div class="author-role">${t.role}</div>
              <div class="testimonio-stars">${stars}</div>
            </div>
          </div>
        </div>`;
    });
  }

  // ======== FILTER ========
  document.querySelectorAll('.filter-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      renderProducts(btn.dataset.filter);
    });
  });

  // ======== CART ========
  let cartItems = JSON.parse(localStorage.getItem('is_cart') || '[]');
  function updateCartBadge() {
    const c = document.getElementById('cartCount');
    c.textContent = cartItems.length;
    c.style.display = cartItems.length > 0 ? 'flex' : 'none';
  }
  function addToCart(name) {
    cartItems.push({ name, ts: Date.now() });
    localStorage.setItem('is_cart', JSON.stringify(cartItems));
    updateCartBadge();
    showNotification('Producto agregado 🎉', name);
  }
  function openCart() {
    showNotification('Tu carrito', `${cartItems.length} producto(s) guardado(s)`);
  }

  // ======== WISHLIST ========
  function toggleWishlist(btn) {
    btn.classList.toggle('active');
    const icon = btn.querySelector('i');
    if (btn.classList.contains('active')) {
      icon.className = 'fas fa-heart';
      showNotification('Favorito agregado ❤️', 'Guardado en tus favoritos');
    } else {
      icon.className = 'far fa-heart';
    }
  }

  // ======== NOTIFICATIONS ========
  function showNotification(title, sub) {
    const n = document.getElementById('notification');
    document.getElementById('notif-title').textContent = title;
    document.getElementById('notif-sub').textContent = sub;
    n.classList.add('show');
    setTimeout(() => n.classList.remove('show'), 3000);
  }

  // ======== COTIZACION FORM ========
  function submitCotizacion() {
    const fields = ['cot-nombre','cot-apellido','cot-email','cot-tel','cot-tipo','cot-cantidad'];
    const values = {};
    let valid = true;
    fields.forEach(id => {
      const el = document.getElementById(id);
      if (!el.value.trim()) {
        el.style.borderColor = '#ef4444';
        valid = false;
      } else {
        el.style.borderColor = '#E5E7EB';
        values[id] = el.value.trim();
      }
    });
    if (!valid) { showNotification('⚠️ Campos requeridos', 'Por favor completa todos los campos'); return; }
    localStorage.setItem('sp_cotizacion', JSON.stringify({ ...values, ts: new Date().toISOString() }));
    document.getElementById('formContent').style.display = 'none';
    document.getElementById('formSuccess').style.display = 'block';
    showNotification('✅ ¡Enviado!', 'Cotización recibida correctamente');
  }

  // ======== CONTACT FORM ========
  function submitContact(btn) {
    btn.innerHTML = '<i class="fas fa-check"></i> ¡Mensaje enviado!';
    btn.style.background = 'linear-gradient(135deg,#16a34a,#22c55e)';
    setTimeout(() => {
      btn.innerHTML = '<i class="fas fa-paper-plane"></i> Enviar Mensaje';
      btn.style.background = '';
    }, 3000);
    showNotification('✅ Mensaje enviado', 'Te responderemos pronto');
  }

  // ======== NAVBAR SCROLL ========
  window.addEventListener('scroll', () => {
    const nav = document.getElementById('navbar');
    const btt = document.getElementById('backToTop');
    if (window.scrollY > 60) {
      nav.classList.add('scrolled');
      btt.classList.add('visible');
    } else {
      nav.classList.remove('scrolled');
      btt.classList.remove('visible');
    }
    // Active nav link
    const sections = ['inicio','nosotros','productos','servicios','cotizaciones','testimonios','contacto'];
    let current = '';
    sections.forEach(id => {
      const el = document.getElementById(id);
      if (el && window.scrollY >= el.offsetTop - 100) current = id;
    });
    document.querySelectorAll('.nav-links a').forEach(a => {
      a.classList.toggle('active', a.getAttribute('href') === `#${current}`);
    });
  });

  // ======== HAMBURGER MENU ========
  document.getElementById('hamburger').addEventListener('click', () => {
    document.getElementById('hamburger').classList.toggle('open');
    document.getElementById('mobileMenu').classList.toggle('open');
    document.body.style.overflow = document.getElementById('mobileMenu').classList.contains('open') ? 'hidden' : '';
  });
  document.getElementById('mobileClose').addEventListener('click', closeMobile);
  function closeMobile() {
    document.getElementById('hamburger').classList.remove('open');
    document.getElementById('mobileMenu').classList.remove('open');
    document.body.style.overflow = '';
  }

  // ======== SCROLL REVEAL ========
  function initReveal() {
    const els = document.querySelectorAll('.reveal, .reveal-left, .reveal-right');
    const obs = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('visible');
          obs.unobserve(e.target);
        }
      });
    }, { threshold: 0.12 });
    els.forEach(el => obs.observe(el));
  }

  // ======== COUNT-UP ANIMATION ========
  function startCountUp() {
    document.querySelectorAll('[data-count]').forEach(el => {
      const target = parseInt(el.dataset.count);
      const duration = 1800;
      const step = target / (duration / 16);
      let current = 0;
      const timer = setInterval(() => {
        current = Math.min(current + step, target);
        el.textContent = Math.floor(current).toLocaleString('es-CO') + (target >= 10000 ? '+' : target === 98 ? '%' : '+');
        if (current >= target) clearInterval(timer);
      }, 16);
    });
  }

  // ======== PROGRESS BARS ========
  function animateProgressBars() {
    document.querySelectorAll('.hero-progress-fill').forEach(bar => {
      setTimeout(() => { bar.style.width = bar.dataset.width; }, 800);
    });
  }

  // ======== INIT ========
  document.addEventListener('DOMContentLoaded', () => {
    renderProducts();
    renderTestimonios();
    updateCartBadge();
    initReveal();
    setTimeout(startCountUp, 400);
    setTimeout(animateProgressBars, 600);
  });
</script>
</body>
</html>
