# salsamentariasofiii

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Salsamentaría, Empaques &amp; Desechables Sofi | Proyecto TICs SENA Tocaima</title>
  <link rel="icon" href="logo.jpg" sizes="32x32" type="image/jpeg">
  <meta name="description" content="Salsamentaría, Charcutería, Empaques de Comidas Rápidas y Desechables Sofi en Tocaima, Cundinamarca. Todo en carnes frías, quesos, cajas de hamburguesas, vasos, servilletas y bolsas. Pedidos por WhatsApp." />

  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,600;0,700;0,900;1,400;1,700&family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=Pacifico&display=swap" rel="stylesheet" />

  <!-- Leaflet CSS (Mapa interactivo) -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />

  <!-- Font Awesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />

  <!-- Chart.js para gráfica del Marco Teórico / Encuesta del PDF -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <style>
    /* ==========================================================
       VARIABLES Y SISTEMA DE DISEÑO GOURMET & DISTRIBUIDORA
    ========================================================== */
    :root {
      --primary: #8B181B;         /* Rojo Borgoña / Vino Tinto artesanal */
      --primary-dark: #630C0E;    /* Granate profundo */
      --primary-light: #FDE8E9;   /* Rosado suave */
      --accent: #C88A2E;          /* Dorado Mostaza Premium */
      --accent-light: #FFF8EB;    /* Crema dorado */
      --accent-hover: #AA7120;
      --dark: #1A1615;            /* Carbón ahumado */
      --dark-soft: #38312E;       /* Café oscuro suave */
      --gray: #6C6663;            /* Gris neutro */
      --gray-light: #F7F5F2;      /* Fondo hueso / mármol */
      --gray-border: #E5DFC5;     /* Borde cálido */
      --white: #FFFFFF;
      --green-wpp: #25D366;
      --green-dark: #128C7E;
      --shadow-sm: 0 4px 15px rgba(0, 0, 0, 0.05);
      --shadow-md: 0 10px 30px rgba(139, 24, 27, 0.12);
      --shadow-lg: 0 20px 50px rgba(26, 22, 21, 0.15);
      --radius-sm: 10px;
      --radius-md: 18px;
      --radius-lg: 32px;
      --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background: #FAF8F5;
      color: var(--dark);
      overflow-x: hidden;
      line-height: 1.6;
    }

    h1, h2, h3, .font-serif {
      font-family: 'Playfair Display', serif;
    }

    /* Scrollbar */
    ::-webkit-scrollbar { width: 9px; }
    ::-webkit-scrollbar-track { background: #FAF8F5; }
    ::-webkit-scrollbar-thumb {
      background: linear-gradient(var(--primary), var(--accent));
      border-radius: 6px;
    }

    /* ==========================================================
       BARRA DE AVISO SUPERIOR (PROYECTO SENA)
    ========================================================== */
    .top-bar-sena {
      background: linear-gradient(90deg, var(--primary-dark) 0%, #30080A 100%);
      color: #F8E7BE;
      font-size: 0.8rem;
      font-weight: 700;
      padding: 7px 20px;
      text-align: center;
      display: flex;
      justify-content: space-between;
      align-items: center;
      letter-spacing: 0.5px;
    }

    /* ==========================================================
       NAVBAR
    ========================================================== */
    #navbar {
      position: sticky;
      top: 0;
      z-index: 1000;
      padding: 0 40px;
      height: 78px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: rgba(255, 255, 255, 0.95);
      backdrop-filter: blur(14px);
      box-shadow: 0 2px 20px rgba(0, 0, 0, 0.06);
      transition: var(--transition);
    }
    #navbar.scrolled {
      height: 68px;
      background: rgba(255, 255, 255, 0.98);
      box-shadow: 0 4px 25px rgba(0, 0, 0, 0.1);
    }

    .nav-brand {
      display: flex;
      align-items: center;
      gap: 12px;
      text-decoration: none;
    }
    .nav-logo-badge {
      width: 46px;
      height: 46px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--primary), var(--accent));
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.4rem;
      box-shadow: 0 4px 12px rgba(139, 24, 27, 0.3);
      border: 2px solid white;
    }
    .nav-logo-text {
      display: flex;
      flex-direction: column;
    }
    .nav-logo-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.4rem;
      font-weight: 900;
      color: var(--primary);
      line-height: 1.1;
      letter-spacing: -0.5px;
    }
    .nav-logo-sub {
      font-size: 0.68rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      color: var(--accent-hover);
    }

    .nav-links {
      display: flex;
      gap: 6px;
      list-style: none;
      align-items: center;
    }
    .nav-links a {
      text-decoration: none;
      color: var(--dark-soft);
      font-weight: 700;
      font-size: 0.92rem;
      padding: 8px 16px;
      border-radius: var(--radius-lg);
      transition: var(--transition);
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }
    .nav-links a:hover,
    .nav-links a.active {
      background: var(--primary);
      color: var(--white);
      transform: translateY(-2px);
      box-shadow: 0 4px 15px rgba(139, 24, 27, 0.25);
    }

    .nav-actions {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    #cart-btn {
      position: relative;
      background: linear-gradient(135deg, var(--primary), var(--primary-dark));
      color: white;
      border: none;
      width: 48px;
      height: 48px;
      border-radius: 50%;
      font-size: 1.2rem;
      cursor: pointer;
      transition: var(--transition);
      box-shadow: 0 4px 15px rgba(139, 24, 27, 0.35);
      display: flex;
      align-items: center;
      justify-content: center;
    }
    #cart-btn:hover {
      transform: scale(1.08) rotate(-4deg);
      box-shadow: 0 6px 20px rgba(139, 24, 27, 0.5);
    }
    #cart-count {
      position: absolute;
      top: -4px;
      right: -4px;
      background: var(--accent);
      color: var(--dark);
      font-size: 0.72rem;
      font-weight: 900;
      width: 22px;
      height: 22px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 2px 6px rgba(0,0,0,0.2);
      border: 2px solid white;
    }

    .mobile-menu-btn {
      display: none;
      background: none;
      border: none;
      font-size: 1.6rem;
      color: var(--dark);
      cursor: pointer;
      padding: 6px;
    }

    /* Mobile Nav Drawer */
    .mobile-nav-overlay {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.5);
      backdrop-filter: blur(4px);
      z-index: 1001;
    }
    .mobile-nav-overlay.open { display: block; }
    .mobile-nav-drawer {
      position: fixed;
      top: 0;
      right: -320px;
      width: 300px;
      height: 100vh;
      background: white;
      z-index: 1002;
      box-shadow: -5px 0 30px rgba(0,0,0,0.2);
      display: flex;
      flex-direction: column;
      padding: 30px 24px;
      transition: right 0.35s ease;
    }
    .mobile-nav-drawer.open { right: 0; }
    .mobile-drawer-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 24px;
      border-bottom: 1px solid var(--gray-border);
      padding-bottom: 14px;
    }
    .mobile-drawer-links {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .mobile-drawer-links a {
      text-decoration: none;
      color: var(--dark);
      font-weight: 700;
      font-size: 1rem;
      padding: 12px 16px;
      border-radius: var(--radius-sm);
      display: flex;
      align-items: center;
      gap: 12px;
      transition: var(--transition);
    }
    .mobile-drawer-links a:hover {
      background: var(--primary-light);
      color: var(--primary);
    }

    /* ==========================================================
       CARRITO MODAL / DROPDOWN
    ========================================================== */
    #cart-dropdown {
      position: fixed;
      top: 85px;
      right: 30px;
      width: 440px;
      max-width: calc(100vw - 30px);
      background: white;
      border-radius: var(--radius-md);
      box-shadow: var(--shadow-lg);
      z-index: 1050;
      overflow: hidden;
      max-height: 0;
      opacity: 0;
      pointer-events: none;
      transition: max-height 0.4s ease, opacity 0.3s ease;
      border: 1px solid rgba(0,0,0,0.08);
    }
    #cart-dropdown.open {
      max-height: 90vh;
      opacity: 1;
      pointer-events: all;
    }
    .cart-header {
      background: linear-gradient(135deg, var(--primary), var(--primary-dark));
      padding: 18px 24px;
      color: white;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .cart-header h3 {
      font-size: 1.15rem;
      font-weight: 800;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .cart-header button {
      background: rgba(255, 255, 255, 0.2);
      border: none;
      color: white;
      width: 32px;
      height: 32px;
      border-radius: 50%;
      cursor: pointer;
      font-size: 1rem;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: var(--transition);
    }
    .cart-header button:hover { background: rgba(255, 255, 255, 0.35); }

    #cart-items {
      max-height: 270px;
      overflow-y: auto;
      padding: 16px;
    }
    #cart-items::-webkit-scrollbar { width: 5px; }
    #cart-items::-webkit-scrollbar-thumb { background: var(--primary); border-radius: 3px; }

    .cart-item {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 10px 12px;
      border-radius: var(--radius-sm);
      background: var(--gray-light);
      margin-bottom: 8px;
      border: 1px solid var(--gray-border);
    }
    .cart-item-img {
      width: 48px;
      height: 48px;
      border-radius: 8px;
      object-fit: cover;
      border: 1px solid var(--gray-border);
      flex-shrink: 0;
    }
    .cart-item-emoji { font-size: 1.6rem; flex-shrink: 0; }
    .cart-item-info { flex: 1; }
    .cart-item-name { font-weight: 800; font-size: 0.92rem; color: var(--dark); line-height: 1.2; margin-bottom: 2px; }
    .cart-item-portion { font-size: 0.74rem; color: var(--gray); }
    .cart-item-price { color: var(--primary); font-weight: 800; font-size: 0.88rem; }

    .cart-item-controls {
      display: flex;
      align-items: center;
      gap: 6px;
    }
    .qty-btn {
      background: white;
      border: 1.5px solid var(--primary);
      color: var(--primary);
      width: 26px;
      height: 26px;
      border-radius: 50%;
      cursor: pointer;
      font-weight: 900;
      font-size: 0.85rem;
      transition: var(--transition);
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .qty-btn:hover { background: var(--primary); color: white; }
    .qty-num { font-weight: 800; font-size: 0.9rem; min-width: 20px; text-align: center; }

    .cart-empty {
      text-align: center;
      padding: 30px 20px;
      color: var(--gray);
    }
    .cart-empty i { font-size: 2.8rem; margin-bottom: 10px; color: #D1D5DB; }

    .cart-footer {
      border-top: 1px solid var(--gray-border);
      padding: 16px 20px 20px;
      background: #FCFAF7;
    }
    .cart-total {
      display: flex;
      justify-content: space-between;
      font-weight: 900;
      font-size: 1.2rem;
      margin-bottom: 12px;
      color: var(--dark);
    }
    .cart-total span:last-child { color: var(--primary); }

    .cart-order-form {
      margin-bottom: 12px;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .cart-input, .cart-select {
      width: 100%;
      padding: 9px 12px;
      border: 1.5px solid var(--gray-border);
      border-radius: 8px;
      font-family: inherit;
      font-size: 0.85rem;
      outline: none;
      transition: var(--transition);
      background: white;
    }
    .cart-input:focus, .cart-select:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(139, 24, 27, 0.1);
    }

    #btn-send-whatsapp {
      width: 100%;
      background: linear-gradient(135deg, var(--green-wpp), var(--green-dark));
      color: white;
      border: none;
      padding: 13px;
      border-radius: var(--radius-lg);
      font-weight: 800;
      font-size: 0.95rem;
      cursor: pointer;
      transition: var(--transition);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      box-shadow: 0 4px 15px rgba(37, 211, 102, 0.35);
      text-decoration: none;
    }
    #btn-send-whatsapp:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 25px rgba(37, 211, 102, 0.45);
    }

    .cart-phone-display {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      background: #F0FFF4;
      border: 1px dashed var(--green-wpp);
      border-radius: var(--radius-sm);
      padding: 8px 12px;
      margin-top: 8px;
      font-weight: 800;
      font-size: 0.88rem;
      color: var(--green-dark);
      text-decoration: none;
      transition: var(--transition);
    }
    .cart-phone-display:hover { background: #E6FFFA; }

    #btn-clear-cart {
      width: 100%;
      background: transparent;
      border: none;
      color: #94A3B8;
      padding: 6px;
      font-weight: 700;
      font-size: 0.8rem;
      cursor: pointer;
      margin-top: 6px;
      transition: var(--transition);
    }
    #btn-clear-cart:hover { color: #EF4444; }

    /* ==========================================================
       HERO SECTION
    ========================================================== */
    #inicio {
      min-height: 92vh;
      position: relative;
      display: flex;
      align-items: center;
      overflow: hidden;
      padding: 60px 80px;
      background: #190E0D;
    }
    .hero-bg-overlay {
      position: absolute;
      inset: 0;
      background:
        radial-gradient(circle at 80% 20%, rgba(200, 138, 46, 0.25) 0%, transparent 50%),
        radial-gradient(circle at 20% 80%, rgba(139, 24, 27, 0.4) 0%, transparent 60%),
        linear-gradient(135deg, rgba(26, 14, 13, 0.94) 0%, rgba(45, 18, 19, 0.88) 100%);
      z-index: 1;
    }
    .hero-grid {
      position: relative;
      z-index: 2;
      display: grid;
      grid-template-columns: 1.15fr 0.85fr;
      gap: 50px;
      align-items: center;
      max-width: 1300px;
      margin: 0 auto;
      width: 100%;
    }
    .hero-content {
      color: white;
    }
    .hero-badges-row {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      margin-bottom: 22px;
    }
    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(255, 255, 255, 0.12);
      backdrop-filter: blur(10px);
      color: #FFF2D6;
      padding: 6px 16px;
      border-radius: var(--radius-lg);
      font-size: 0.84rem;
      font-weight: 700;
      border: 1px solid rgba(255, 255, 255, 0.2);
    }
    .hero-badge.status-open {
      background: rgba(37, 211, 102, 0.2);
      border-color: #25D366;
      color: #B4F8C8;
    }
    .hero-title {
      font-size: clamp(2.6rem, 5vw, 4.2rem);
      line-height: 1.12;
      margin-bottom: 18px;
      color: #FFFFFF;
      font-weight: 900;
    }
    .hero-title .highlight-gold {
      background: linear-gradient(135deg, #FDE68A 0%, #F59E0B 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .hero-subtitle {
      font-size: 1.1rem;
      color: #E2D9D2;
      line-height: 1.7;
      margin-bottom: 32px;
      font-weight: 500;
      max-width: 580px;
    }
    .hero-buttons {
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
    }
    .btn-hero-primary {
      background: linear-gradient(135deg, var(--accent), var(--accent-hover));
      color: #1A1615;
      text-decoration: none;
      padding: 14px 32px;
      border-radius: var(--radius-lg);
      font-weight: 800;
      font-size: 1rem;
      transition: var(--transition);
      box-shadow: 0 8px 25px rgba(200, 138, 46, 0.4);
      display: inline-flex;
      align-items: center;
      gap: 10px;
    }
    .btn-hero-primary:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 35px rgba(200, 138, 46, 0.55);
      background: linear-gradient(135deg, #E6A23C, #C88A2E);
    }
    .btn-hero-secondary {
      background: rgba(255, 255, 255, 0.12);
      color: white;
      text-decoration: none;
      padding: 14px 28px;
      border-radius: var(--radius-lg);
      font-weight: 700;
      font-size: 1rem;
      transition: var(--transition);
      border: 1.5px solid rgba(255, 255, 255, 0.3);
      display: inline-flex;
      align-items: center;
      gap: 10px;
      backdrop-filter: blur(8px);
    }
    .btn-hero-secondary:hover {
      background: rgba(255, 255, 255, 0.22);
      transform: translateY(-3px);
    }

    /* Hero Card Visual */
    .hero-card-preview {
      background: rgba(255, 255, 255, 0.06);
      backdrop-filter: blur(16px);
      border: 1px solid rgba(255, 255, 255, 0.15);
      border-radius: var(--radius-md);
      padding: 24px;
      box-shadow: var(--shadow-lg);
    }
    .hero-promo-badge {
      display: flex;
      align-items: center;
      gap: 12px;
      background: linear-gradient(135deg, var(--primary), var(--primary-dark));
      padding: 16px;
      border-radius: var(--radius-sm);
      color: white;
      margin-bottom: 20px;
    }
    .hero-promo-icon { font-size: 2rem; }
    .hero-quick-list {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }
    .hero-quick-item {
      background: rgba(255, 255, 255, 0.08);
      border-radius: var(--radius-sm);
      padding: 14px;
      display: flex;
      align-items: center;
      gap: 12px;
      color: white;
      border: 1px solid rgba(255, 255, 255, 0.1);
      transition: var(--transition);
    }
    .hero-quick-item:hover {
      background: rgba(200, 138, 46, 0.2);
      border-color: var(--accent);
      transform: translateY(-2px);
    }
    .hero-quick-emoji { font-size: 1.8rem; }
    .hero-quick-title { font-weight: 800; font-size: 0.92rem; }
    .hero-quick-sub { font-size: 0.76rem; color: #D1D5DB; }

    /* ==========================================================
       SECTION COMMONS
    ========================================================== */
    section {
      padding: 85px 80px;
    }
    .section-header {
      text-align: center;
      margin-bottom: 48px;
    }
    .section-tag {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: var(--primary-light);
      color: var(--primary);
      padding: 6px 18px;
      border-radius: var(--radius-lg);
      font-size: 0.82rem;
      font-weight: 800;
      letter-spacing: 1px;
      text-transform: uppercase;
      margin-bottom: 12px;
      border: 1px solid rgba(139, 24, 27, 0.15);
    }
    .section-title {
      font-size: clamp(2rem, 3.8vw, 2.8rem);
      color: var(--dark);
      margin-bottom: 12px;
      font-weight: 900;
    }
    .section-sub {
      color: var(--gray);
      font-size: 1.05rem;
      max-width: 680px;
      margin: 0 auto;
      font-weight: 500;
    }
    .divider {
      width: 70px;
      height: 4px;
      background: linear-gradient(135deg, var(--primary), var(--accent));
      border-radius: 2px;
      margin: 16px auto 0;
    }

    /* ==========================================================
       SECCIÓN 1: PROYECTO TICS SENA (CUMPLIMIENTO PDF)
    ========================================================== */
    #proyecto-sena {
      background: #FFFFFF;
      border-top: 1px solid var(--gray-border);
      border-bottom: 1px solid var(--gray-border);
    }
    .sena-card-main {
      background: linear-gradient(135deg, #FFFBF5 0%, #FFF5F5 100%);
      border: 1.5px solid #F0D9D9;
      border-radius: var(--radius-md);
      padding: 36px;
      margin-bottom: 40px;
      box-shadow: var(--shadow-sm);
    }
    .sena-header-info {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 20px;
      padding-bottom: 24px;
      border-bottom: 1.5px dashed #E2C0C0;
      margin-bottom: 26px;
    }
    .sena-badge-pill {
      background: var(--primary);
      color: white;
      padding: 6px 16px;
      border-radius: var(--radius-lg);
      font-weight: 800;
      font-size: 0.85rem;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }
    .sena-title-h3 {
      font-size: 1.5rem;
      color: var(--primary-dark);
      font-weight: 900;
      margin-top: 6px;
    }
    .sena-location-tag {
      display: flex;
      align-items: center;
      gap: 8px;
      color: var(--dark-soft);
      font-weight: 700;
      font-size: 0.95rem;
      background: white;
      padding: 8px 16px;
      border-radius: var(--radius-sm);
      border: 1px solid var(--gray-border);
    }

    /* Grid de Objetivos y Planteamiento del PDF */
    .sena-pdf-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 24px;
    }
    .sena-box {
      background: white;
      border-radius: var(--radius-sm);
      padding: 24px;
      border: 1px solid var(--gray-border);
      box-shadow: var(--shadow-sm);
      transition: var(--transition);
    }
    .sena-box:hover {
      transform: translateY(-4px);
      box-shadow: var(--shadow-md);
      border-color: var(--primary);
    }
    .sena-box-icon {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      background: var(--primary-light);
      color: var(--primary);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.2rem;
      margin-bottom: 14px;
    }
    .sena-box h4 {
      font-size: 1.15rem;
      font-weight: 800;
      color: var(--dark);
      margin-bottom: 8px;
    }
    .sena-box p {
      color: var(--dark-soft);
      font-size: 0.92rem;
      line-height: 1.6;
    }
    .sena-box ul {
      list-style: none;
      margin-top: 8px;
    }
    .sena-box ul li {
      position: relative;
      padding-left: 22px;
      margin-bottom: 8px;
      font-size: 0.9rem;
      color: var(--dark-soft);
    }
    .sena-box ul li::before {
      content: '✔';
      position: absolute;
      left: 0;
      color: var(--primary);
      font-weight: 900;
    }

    /* Marco Teórico & Gráfica SENA */
    .sena-chart-wrapper {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 30px;
      align-items: center;
      margin-top: 30px;
      background: white;
      padding: 30px;
      border-radius: var(--radius-md);
      border: 1px solid var(--gray-border);
    }
    .sena-stat-big {
      font-size: 3.5rem;
      font-weight: 900;
      color: var(--primary);
      line-height: 1;
      font-family: 'Playfair Display', serif;
      margin-bottom: 10px;
    }

    /* ==========================================================
       SECCIÓN 2: CATÁLOGO DE PRODUCTOS (SALSAMENTARÍA & DESECHABLES)
    ========================================================== */
    #productos {
      background: #FAF8F5;
    }

    /* Controles de Búsqueda y Filtro */
    .catalog-controls {
      max-width: 1040px;
      margin: 0 auto 35px;
      display: flex;
      flex-direction: column;
      gap: 20px;
    }
    .search-box-wrap {
      position: relative;
      width: 100%;
    }
    .search-box-input {
      width: 100%;
      padding: 15px 20px 15px 50px;
      border-radius: var(--radius-lg);
      border: 2px solid var(--gray-border);
      background: white;
      font-family: inherit;
      font-size: 0.98rem;
      font-weight: 600;
      outline: none;
      transition: var(--transition);
      box-shadow: var(--shadow-sm);
    }
    .search-box-input:focus {
      border-color: var(--primary);
      box-shadow: 0 6px 20px rgba(139, 24, 27, 0.15);
    }
    .search-icon-pos {
      position: absolute;
      left: 20px;
      top: 50%;
      transform: translateY(-50%);
      color: var(--gray);
      font-size: 1.15rem;
    }

    /* Pestañas de categorías */
    .category-tabs {
      display: flex;
      justify-content: center;
      gap: 8px;
      flex-wrap: wrap;
    }
    .cat-tab {
      padding: 10px 18px;
      border-radius: var(--radius-lg);
      border: 1.5px solid var(--gray-border);
      background: white;
      cursor: pointer;
      font-family: inherit;
      font-weight: 800;
      font-size: 0.86rem;
      transition: var(--transition);
      display: flex;
      align-items: center;
      gap: 6px;
      color: var(--dark-soft);
    }
    .cat-tab:hover, .cat-tab.active {
      border-color: transparent;
      background: var(--primary);
      color: white;
      transform: translateY(-2px);
      box-shadow: 0 6px 18px rgba(139, 24, 27, 0.25);
    }

    /* Grid de Productos */
    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(290px, 1fr));
      gap: 28px;
    }
    .product-card {
      background: white;
      border-radius: var(--radius-md);
      overflow: hidden;
      box-shadow: var(--shadow-sm);
      transition: var(--transition);
      display: flex;
      flex-direction: column;
      border: 1px solid rgba(0,0,0,0.06);
      position: relative;
    }
    .product-card:hover {
      transform: translateY(-6px);
      box-shadow: var(--shadow-md);
      border-color: #E2B4B6;
    }
    .product-img-wrap {
      position: relative;
      height: 220px;
      overflow: hidden;
      background: #F2EFE9;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .product-img-wrap img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.5s ease;
    }
    .product-card:hover .product-img-wrap img {
      transform: scale(1.08);
    }
    .product-badge-flag {
      position: absolute;
      top: 12px;
      left: 12px;
      background: linear-gradient(135deg, var(--primary), var(--primary-dark));
      color: white;
      padding: 5px 12px;
      border-radius: var(--radius-lg);
      font-size: 0.72rem;
      font-weight: 800;
      letter-spacing: 0.5px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.2);
    }
    .product-badge-flag.gold {
      background: linear-gradient(135deg, var(--accent), var(--accent-hover));
      color: #1A1615;
    }
    .product-emoji-icon {
      position: absolute;
      top: 12px;
      right: 12px;
      font-size: 1.4rem;
      background: rgba(255, 255, 255, 0.92);
      backdrop-filter: blur(4px);
      width: 38px;
      height: 38px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 3px 8px rgba(0,0,0,0.12);
    }

    .product-body {
      padding: 22px;
      display: flex;
      flex-direction: column;
      flex: 1;
    }
    .product-title {
      font-size: 1.12rem;
      font-weight: 800;
      color: var(--dark);
      margin-bottom: 6px;
      line-height: 1.3;
    }
    .product-portion-tag {
      display: inline-block;
      font-size: 0.75rem;
      font-weight: 800;
      color: var(--accent-hover);
      text-transform: uppercase;
      letter-spacing: 0.8px;
      margin-bottom: 10px;
    }
    .product-desc {
      color: var(--gray);
      font-size: 0.88rem;
      line-height: 1.5;
      margin-bottom: 18px;
      flex: 1;
    }

    .product-footer {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-top: auto;
      padding-top: 14px;
      border-top: 1px solid var(--gray-border);
    }
    .product-price-box {
      display: flex;
      flex-direction: column;
    }
    .product-price-label {
      font-size: 0.72rem;
      color: var(--gray);
      font-weight: 700;
      text-transform: uppercase;
    }
    .product-price {
      font-size: 1.3rem;
      font-weight: 900;
      color: var(--primary);
    }
    .btn-add-cart {
      background: linear-gradient(135deg, var(--primary), var(--primary-dark));
      color: white;
      border: none;
      padding: 10px 18px;
      border-radius: var(--radius-lg);
      font-weight: 800;
      font-size: 0.88rem;
      cursor: pointer;
      transition: var(--transition);
      display: flex;
      align-items: center;
      gap: 6px;
      font-family: inherit;
    }
    .btn-add-cart:hover {
      transform: scale(1.05);
      box-shadow: 0 4px 15px rgba(139, 24, 27, 0.35);
    }
    .btn-add-cart.added {
      background: linear-gradient(135deg, var(--green-wpp), var(--green-dark));
      box-shadow: 0 4px 12px rgba(37, 211, 102, 0.35);
    }

    /* ==========================================================
       SECCIÓN 3: COTIZADOR INTERACTIVO DE TABLAS GOURMET
========================================================== */
    #cotizador {
      background: linear-gradient(135deg, #231211 0%, #150B0A 100%);
      color: white;
      position: relative;
    }
    .customizer-box {
      max-width: 960px;
      margin: 0 auto;
      background: rgba(255, 255, 255, 0.05);
      backdrop-filter: blur(14px);
      border: 1px solid rgba(255, 255, 255, 0.12);
      border-radius: var(--radius-md);
      padding: 36px;
      box-shadow: var(--shadow-lg);
    }
    .customizer-steps-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
      margin-bottom: 30px;
    }
    .cust-step-card {
      background: rgba(255, 255, 255, 0.07);
      border-radius: var(--radius-sm);
      padding: 18px;
      border: 1px solid rgba(255, 255, 255, 0.1);
    }
    .cust-step-title {
      font-weight: 800;
      font-size: 1rem;
      color: var(--accent);
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .cust-checkbox-label {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 0.88rem;
      color: #E2D9D2;
      margin-bottom: 8px;
      cursor: pointer;
    }
    .cust-checkbox-label input {
      accent-color: var(--accent);
      width: 16px;
      height: 16px;
    }
    .cust-total-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: rgba(200, 138, 46, 0.15);
      border: 1px solid var(--accent);
      padding: 20px 24px;
      border-radius: var(--radius-sm);
      flex-wrap: wrap;
      gap: 16px;
    }
    .cust-total-price {
      font-size: 1.8rem;
      font-weight: 900;
      color: #FDE68A;
      font-family: 'Playfair Display', serif;
    }

    /* ==========================================================
       SECCIÓN 4: NOSOTROS (HISTORIA & CALIDAD)
========================================================== */
    #nosotros {
      background: white;
    }
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1.1fr;
      gap: 60px;
      align-items: center;
      max-width: 1200px;
      margin: 0 auto;
    }
    .about-img-container {
      position: relative;
    }
    .about-main-img {
      width: 100%;
      height: 420px;
      object-fit: cover;
      border-radius: var(--radius-md);
      box-shadow: var(--shadow-lg);
    }
    .about-floating-card {
      position: absolute;
      bottom: -20px;
      right: -20px;
      background: linear-gradient(135deg, var(--primary), var(--primary-dark));
      color: white;
      padding: 20px 26px;
      border-radius: var(--radius-md);
      text-align: center;
      box-shadow: var(--shadow-md);
      border: 3px solid white;
    }
    .about-num { font-size: 2.2rem; font-weight: 900; line-height: 1; }
    .about-label { font-size: 0.8rem; font-weight: 700; text-transform: uppercase; }

    .about-text-content h3 {
      font-size: 2.2rem;
      color: var(--primary-dark);
      margin-bottom: 16px;
      font-weight: 900;
    }
    .about-text-content p {
      color: var(--dark-soft);
      font-size: 0.98rem;
      line-height: 1.7;
      margin-bottom: 20px;
    }

    .about-pillars {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
      margin-top: 24px;
    }
    .pillar-card {
      background: var(--gray-light);
      padding: 18px;
      border-radius: var(--radius-sm);
      border-left: 4px solid var(--primary);
    }
    .pillar-card h4 { font-weight: 800; font-size: 1rem; color: var(--dark); margin-bottom: 4px; }
    .pillar-card p { font-size: 0.85rem; color: var(--gray); margin-bottom: 0; line-height: 1.4; }

    /* ==========================================================
       SECCIÓN 5: UBICACIÓN, CONTACTO & MAPA EN TOCAIMA
========================================================== */
    #contacto {
      background: #FAF8F5;
    }
    .contact-grid {
      display: grid;
      grid-template-columns: 1fr 1.3fr;
      gap: 50px;
      max-width: 1200px;
      margin: 0 auto;
      align-items: start;
    }
    .contact-card-box {
      background: white;
      padding: 32px;
      border-radius: var(--radius-md);
      box-shadow: var(--shadow-sm);
      border: 1px solid var(--gray-border);
    }
    .contact-item-row {
      display: flex;
      align-items: flex-start;
      gap: 16px;
      margin-bottom: 20px;
      padding-bottom: 16px;
      border-bottom: 1px solid var(--gray-light);
    }
    .contact-icon-bubble {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      background: var(--primary-light);
      color: var(--primary);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.1rem;
      flex-shrink: 0;
    }
    .contact-text-wrap h5 { font-weight: 800; font-size: 0.95rem; color: var(--dark); margin-bottom: 2px; }
    .contact-text-wrap p { font-size: 0.88rem; color: var(--gray); margin: 0; }

    .map-box-wrap {
      background: white;
      border-radius: var(--radius-md);
      overflow: hidden;
      box-shadow: var(--shadow-md);
      border: 1px solid var(--gray-border);
    }
    .map-header-status {
      padding: 14px 20px;
      background: var(--dark);
      color: white;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.88rem;
      font-weight: 700;
    }
    #map {
      height: 380px;
      width: 100%;
      z-index: 10;
    }

    /* ==========================================================
       SECCIÓN 6: EQUIPO DE TRABAJO SENA (DEL PDF)
========================================================== */
    #equipo {
      background: linear-gradient(135deg, #FFF9F9 0%, #FAF5ED 100%);
      border-top: 1px solid var(--gray-border);
    }
    .team-grid {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 22px;
      max-width: 1240px;
      margin: 0 auto;
    }
    .team-member-card {
      background: white;
      border-radius: var(--radius-md);
      padding: 24px 16px;
      text-align: center;
      box-shadow: var(--shadow-sm);
      border: 1px solid var(--gray-border);
      transition: var(--transition);
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .team-member-card:hover {
      transform: translateY(-8px);
      box-shadow: var(--shadow-md);
      border-color: var(--primary);
    }
    .team-avatar-container {
      position: relative;
      width: 110px;
      height: 110px;
      margin-bottom: 16px;
    }
    .team-avatar-ring {
      position: absolute;
      inset: -4px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--primary), var(--accent));
    }
    .team-avatar-inner {
      position: absolute;
      inset: 3px;
      border-radius: 50%;
      overflow: hidden;
      background: #EDE8E1;
      border: 3px solid white;
    }
    .team-avatar-inner img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .team-avatar-fallback {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      background: linear-gradient(135deg, var(--primary), var(--accent));
      color: white;
    }
    .team-student-name {
      font-weight: 900;
      font-size: 0.95rem;
      color: var(--dark);
      margin-bottom: 4px;
      line-height: 1.2;
    }
    .team-student-role {
      font-size: 0.78rem;
      font-weight: 800;
      color: var(--primary);
      text-transform: uppercase;
      letter-spacing: 0.5px;
      margin-bottom: 6px;
    }
    .team-student-tag {
      font-size: 0.72rem;
      color: var(--gray);
      background: var(--gray-light);
      padding: 3px 10px;
      border-radius: 12px;
      font-weight: 700;
    }

    /* ==========================================================
       FOOTER
    ========================================================== */
    footer {
      background: #150E0E;
      color: white;
      padding: 60px 80px 24px;
      border-top: 3px solid var(--accent);
    }
    .footer-grid {
      display: grid;
      grid-template-columns: 1.8fr 1fr 1fr 1.2fr;
      gap: 40px;
      max-width: 1240px;
      margin: 0 auto 40px;
    }
    .footer-brand h3 {
      font-size: 1.8rem;
      color: var(--accent);
      margin-bottom: 12px;
      font-weight: 900;
    }
    .footer-desc {
      color: #A8A29E;
      font-size: 0.88rem;
      line-height: 1.6;
      margin-bottom: 20px;
    }
    .footer-social-links {
      display: flex;
      gap: 10px;
    }
    .footer-social-links a {
      width: 38px;
      height: 38px;
      border-radius: 50%;
      background: rgba(255, 255, 255, 0.08);
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      text-decoration: none;
      transition: var(--transition);
    }
    .footer-social-links a:hover {
      background: var(--primary);
      transform: translateY(-3px);
    }
    .footer-col h4 {
      font-size: 1rem;
      font-weight: 800;
      color: #F5E8D3;
      margin-bottom: 18px;
      position: relative;
      padding-bottom: 8px;
    }
    .footer-col h4::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 32px;
      height: 2.5px;
      background: var(--accent);
    }
    .footer-col ul { list-style: none; }
    .footer-col ul li { margin-bottom: 10px; }
    .footer-col ul li a {
      color: #A8A29E;
      text-decoration: none;
      font-size: 0.88rem;
      transition: var(--transition);
      display: flex;
      align-items: center;
      gap: 6px;
    }
    .footer-col ul li a:hover {
      color: var(--accent);
      padding-left: 4px;
    }
    .footer-bottom {
      border-top: 1px solid rgba(255, 255, 255, 0.1);
      padding-top: 24px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
      max-width: 1240px;
      margin: 0 auto;
      font-size: 0.82rem;
      color: #78716C;
    }

    /* Toast Notification */
    #toast {
      position: fixed;
      bottom: 30px;
      right: 30px;
      background: linear-gradient(135deg, var(--dark), var(--primary-dark));
      color: white;
      padding: 14px 22px;
      border-radius: var(--radius-md);
      font-weight: 800;
      font-size: 0.9rem;
      box-shadow: var(--shadow-lg);
      z-index: 9999;
      display: flex;
      align-items: center;
      gap: 10px;
      transform: translateX(140%);
      transition: transform 0.35s cubic-bezier(0.68, -0.55, 0.265, 1.55);
      border-left: 4px solid var(--accent);
    }
    #toast.show { transform: translateX(0); }

    /* Back to top button */
    #back-top {
      position: fixed;
      bottom: 30px;
      left: 30px;
      width: 46px;
      height: 46px;
      background: var(--primary);
      color: white;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      font-size: 1.05rem;
      box-shadow: var(--shadow-md);
      transition: var(--transition);
      opacity: 0;
      pointer-events: none;
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 900;
    }
    #back-top.visible { opacity: 1; pointer-events: all; }
    #back-top:hover { transform: translateY(-4px); background: var(--primary-dark); }

    /* ==========================================================
       RESPONSIVE DESIGN
    ========================================================== */
    @media (max-width: 1100px) {
      .team-grid { grid-template-columns: repeat(3, 1fr); }
      .footer-grid { grid-template-columns: 1fr 1fr; }
      .hero-grid { grid-template-columns: 1fr; }
      .about-grid { grid-template-columns: 1fr; gap: 40px; }
      .sena-pdf-grid { grid-template-columns: 1fr; }
      .sena-chart-wrapper { grid-template-columns: 1fr; }
      .customizer-steps-grid { grid-template-columns: 1fr; }
    }
    @media (max-width: 850px) {
      section { padding: 65px 24px; }
      #navbar { padding: 0 20px; }
      .nav-links { display: none; }
      .mobile-menu-btn { display: block; }
      #inicio { padding: 50px 24px; }
      .contact-grid { grid-template-columns: 1fr; }
      .team-grid { grid-template-columns: repeat(2, 1fr); }
      footer { padding: 50px 24px 20px; }
    }
    @media (max-width: 540px) {
      .team-grid { grid-template-columns: 1fr; }
      .footer-grid { grid-template-columns: 1fr; }
      .about-pillars { grid-template-columns: 1fr; }
      #cart-dropdown { width: 100vw; right: 0; top: 68px; border-radius: 0 0 var(--radius-md) var(--radius-md); }
    }
    </style>
</head>
<body>

<!-- BARRA DE AVISO SUPERIOR SENA -->
<div class="top-bar-sena">
  <span>🎓 <strong>PROYECTO TICS SENA 1102</strong> • Aplicación Informativa en Tocaima, Cundinamarca</span>
  <span><i class="fas fa-certificate" style="color:var(--accent);"></i> Salsamentaría, Empaques &amp; Desechables</span>
</div>

<!-- ==========================================================
     NAVBAR
========================================================== -->
<nav id="navbar">
  <a href="#inicio" class="nav-brand">
    <div class="nav-logo-badge">🥓</div>
    <div class="nav-logo-text">
      <span class="nav-logo-title">Sofi</span>
      <span class="nav-logo-sub">Salsamentaría &amp; Desechables</span>
    </div>
  </a>

  <ul class="nav-links">
    <li><a href="#inicio"><i class="fas fa-home"></i> Inicio</a></li>
    <li><a href="#proyecto-sena"><i class="fas fa-graduation-cap"></i> Proyecto SENA</a></li>
    <li><a href="#productos"><i class="fas fa-utensils"></i> Catálogo</a></li>
    <li><a href="#cotizador"><i class="fas fa-sliders-h"></i> Armar Tabla</a></li>
    <li><a href="#nosotros"><i class="fas fa-store"></i> Nosotros</a></li>
    <li><a href="#contacto"><i class="fas fa-map-marker-alt"></i> Tocaima</a></li>
    <li><a href="#equipo"><i class="fas fa-users"></i> Equipo</a></li>
  </ul>

  <div class="nav-actions">
    <button id="cart-btn" onclick="toggleCart()" aria-label="Ver Carrito de Compras" title="Mi Carrito">
      <i class="fas fa-shopping-basket"></i>
      <span id="cart-count">0</span>
    </button>
    <button class="mobile-menu-btn" onclick="toggleMobileMenu()" aria-label="Abrir Menú">
      <i class="fas fa-bars"></i>
    </button>
  </div>
</nav>

<!-- Mobile Nav Drawer -->
<div class="mobile-nav-overlay" id="mobile-nav-overlay" onclick="toggleMobileMenu()"></div>
<div class="mobile-nav-drawer" id="mobile-nav-drawer">
  <div class="mobile-drawer-header">
    <div class="nav-logo-text">
      <span class="nav-logo-title" style="font-size:1.3rem;">Sofi 🥓</span>
      <span class="nav-logo-sub">Salsamentaría Tocaima</span>
    </div>
    <button onclick="toggleMobileMenu()" style="background:none;border:none;font-size:1.4rem;cursor:pointer;color:var(--dark);">✕</button>
  </div>
  <ul class="mobile-drawer-links">
    <li><a href="#inicio" onclick="toggleMobileMenu()"><i class="fas fa-home"></i> Inicio</a></li>
    <li><a href="#proyecto-sena" onclick="toggleMobileMenu()"><i class="fas fa-graduation-cap"></i> Proyecto TICs SENA</a></li>
    <li><a href="#productos" onclick="toggleMobileMenu()"><i class="fas fa-utensils"></i> Catálogo de Productos</a></li>
    <li><a href="#cotizador" onclick="toggleMobileMenu()"><i class="fas fa-sliders-h"></i> Armador de Tablas</a></li>
    <li><a href="#nosotros" onclick="toggleMobileMenu()"><i class="fas fa-store"></i> Sobre Nosotros</a></li>
    <li><a href="#contacto" onclick="toggleMobileMenu()"><i class="fas fa-map-marker-alt"></i> Ubicación &amp; Horarios</a></li>
    <li><a href="#equipo" onclick="toggleMobileMenu()"><i class="fas fa-users"></i> Equipo de Trabajo</a></li>
  </ul>
</div>

<!-- ==========================================================
     CARRITO DROPDOWN / MODAL
========================================================== -->
<div id="cart-dropdown">
  <div class="cart-header">
    <h3><i class="fas fa-shopping-basket"></i> Mi Canasta de Compras</h3>
    <button onclick="toggleCart()" aria-label="Cerrar">✕</button>
  </div>

  <div id="cart-items">
    <div class="cart-empty" id="cart-empty">
      <div><i class="fas fa-shopping-basket"></i></div>
      <p>¡Tu canasta está vacía!</p>
      <p style="font-size:0.8rem;margin-top:4px;">Elige carnes frías, quesos, cajas de comida o desechables para pedir 🥩🍔🧻</p>
    </div>
  </div>

  <div class="cart-footer">
    <div class="cart-total">
      <span>Total a Pagar:</span>
      <span id="cart-total-price">$0</span>
    </div>

    <!-- Formulario de despacho -->
    <div class="cart-order-form">
      <input type="text" id="order-client-name" class="cart-input" placeholder="Tu Nombre completo (Ej: Carlos Pérez)">
      <input type="text" id="order-client-address" class="cart-input" placeholder="Dirección en Tocaima o 'Para Recoger en Local'">
      <select id="order-payment-method" class="cart-select">
        <option value="Efectivo en Entrega">Método de Pago: Efectivo contra entrega</option>
        <option value="Transferencia Nequi">Método de Pago: Nequi</option>
        <option value="Transferencia Daviplata">Método de Pago: Daviplata</option>
        <option value="Transferencia Bancolombia">Método de Pago: Bancolombia</option>
      </select>
    </div>

    <!-- Botón Enviar a WhatsApp -->
    <button id="btn-send-whatsapp" onclick="sendToWhatsApp()">
      <i class="fab fa-whatsapp" style="font-size:1.2rem;"></i>
      Confirmar y Enviar Pedido a WhatsApp
    </button>

    <!-- Llamada telefónica directa -->
    <a href="tel:+573134292831" class="cart-phone-display">
      <i class="fas fa-phone-alt"></i>
      <span>Línea Telefónica Directa: 313 429 2831</span>
    </a>

    <button id="btn-clear-cart" onclick="clearCart()">
      <i class="fas fa-trash-alt"></i> Vaciar canasta
    </button>
  </div>
</div>

<!-- ==========================================================
     HERO SECTION
========================================================== -->
<section id="inicio">
  <div class="hero-bg-overlay"></div>

  <div class="hero-grid">
    <div class="hero-content">
      <div class="hero-badges-row">
        <div class="hero-badge">
          <span>👑</span> Calidad Premium &amp; Distribuidora
        </div>
        <div class="hero-badge status-open" id="business-status-badge">
          <span>🟢</span> <span id="business-status-text">Abierto Hoy • Tocaima, Cund.</span>
        </div>
      </div>

      <h1 class="hero-title">
        Salsamentaría,<br/>Empaques &amp;<br/>
        <span class="highlight-gold">Desechables</span>
      </h1>

      <p class="hero-subtitle">
        Descubre la más selecta variedad de carnes frías, jamones, quesos finos, cajas de hamburguesas, perros, pizzas y arepas, vasos térmicos, servilletas y bolsas en Tocaima. Todo para tu hogar, restaurante y eventos.
      </p>

      <div class="hero-buttons">
        <a href="#productos" class="btn-hero-primary">
          <i class="fas fa-utensils"></i> Explorar Catálogo
        </a>
        <a href="#proyecto-sena" class="btn-hero-secondary">
          <i class="fas fa-file-alt"></i> Ver Proyecto SENA
        </a>
      </div>
    </div>

    <!-- Card lateral destacada -->
    <div class="hero-card-preview">
      <div class="hero-promo-badge">
        <div class="hero-promo-icon">🍔</div>
        <div>
          <h4 style="font-weight:900;font-size:1.05rem;">Surtido Completo &amp; Fresco</h4>
          <p style="font-size:0.82rem;opacity:0.9;">Alimentos de salsamentaría y línea líder en desechables y empaques.</p>
        </div>
      </div>

      <div class="hero-quick-list">
        <div class="hero-quick-item">
          <div class="hero-quick-emoji">🥩</div>
          <div>
            <div class="hero-quick-title">Carnes Frías</div>
            <div class="hero-quick-sub">Jamones &amp; Embutidos</div>
          </div>
        </div>
        <div class="hero-quick-item">
          <div class="hero-quick-emoji">🧀</div>
          <div>
            <div class="hero-quick-title">Quesos Finos</div>
            <div class="hero-quick-sub">Madurados &amp; Frescos</div>
          </div>
        </div>
        <div class="hero-quick-item">
          <div class="hero-quick-emoji">🍔</div>
          <div>
            <div class="hero-quick-title">Cajas de Comida</div>
            <div class="hero-quick-sub">Hamburguesa, Perro &amp; Pizza</div>
          </div>
        </div>
        <div class="hero-quick-item">
          <div class="hero-quick-emoji">☕</div>
          <div>
            <div class="hero-quick-title">Vasos &amp; Cubiertos</div>
            <div class="hero-quick-sub">Térmicos, Vasos &amp; Guantes</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ==========================================================
     SECCIÓN 1: PROYECTO TICS SENA (ESTRUCTURA DEL PDF)
========================================================== -->
<section id="proyecto-sena">
  <div class="section-header">
    <span class="section-tag"><i class="fas fa-book-open"></i> Sustentación Académica</span>
    <h2 class="section-title">Proyecto TICs SENA</h2>
    <p class="section-sub">Estructura formal, objetivos y justificación de la aplicación web informativa para la salsamentaría en el municipio de Tocaima.</p>
    <div class="divider"></div>
  </div>

  <div class="sena-card-main">
    <div class="sena-header-info">
      <div>
        <span class="sena-badge-pill"><i class="fas fa-award"></i> Título del Proyecto (Según PDF)</span>
        <h3 class="sena-title-h3">
          Aplicación Informativa sobre los Productos y Servicios Ofrecidos por la Salsamentaría en el Municipio de Tocaima, Cundinamarca
        </h3>
      </div>
      <div class="sena-location-tag">
        <i class="fas fa-map-pin" style="color:var(--primary);"></i>
        <span>Tocaima, Cundinamarca • Ficha 1102</span>
      </div>
    </div>

    <!-- Grid de 4 Pilares del PDF -->
    <div class="sena-pdf-grid">
      <!-- 1. Objetivo General -->
      <div class="sena-box">
        <div class="sena-box-icon"><i class="fas fa-bullseye"></i></div>
        <h4>Objetivo General</h4>
        <p>
          Desarrollar una aplicación web informativa e interactiva para una salsamentaria que permita dar a conocer sus productos, precios y promociones en tiempo real, facilitar la comunicación con los clientes y fortalecer la presencia local del negocio en el municipio de Tocaima, mejorando así la experiencia de compra y el alcance comercial.
        </p>
      </div>

      <!-- 2. Objetivos Específicos -->
      <div class="sena-box">
        <div class="sena-box-icon"><i class="fas fa-tasks"></i></div>
        <h4>Objetivos Específicos</h4>
        <ul>
          <li><strong>01:</strong> Diseñar un catálogo digital con imágenes.</li>
          <li><strong>02:</strong> Implementar un módulo de promociones y novedades.</li>
          <li><strong>03:</strong> Integrar canales de contacto directo.</li>
        </ul>
      </div>

      <!-- 3. Planteamiento del Problema -->
      <div class="sena-box">
        <div class="sena-box-icon"><i class="fas fa-exclamation-triangle"></i></div>
        <h4>Planteamiento del Problema</h4>
        <p>
          Las salsamentaria de Tocaima solo venden en el punto físico y por voz a voz. Los clientes no conocen precios, productos ni promociones actuales si no van al local. Esto limita las ventas, hace perder turistas que buscan en internet y genera atrasos al atender pedidos solo por llamada. El negocio queda por fuera de los nuevos hábitos de compra digitales.
        </p>
      </div>

      <!-- 4. Justificación -->
      <div class="sena-box">
        <div class="sena-box-icon"><i class="fas fa-check-circle"></i></div>
        <h4>Justificación</h4>
        <p>
          Los clientes y turistas encuentran la salsamentaria en internet antes de comprar. Muestra precios y promos actualizadas sin tener que responder uno por uno. Facilita pedidos por WhatsApp y atrae gente que no pasa frente al local. Permite competir con negocios que ya usan redes y catálogos digitales.
        </p>
      </div>
    </div>

    <!-- Gráfica interactiva del Marco Teórico -->
    <div class="sena-chart-wrapper">
      <div>
        <span class="section-tag" style="background:#FFF0F0;">Marco Teórico - Salsamentaria Sofi</span>
        <div class="sena-stat-big">91%</div>
        <h4 style="font-weight:900;font-size:1.2rem;margin-bottom:8px;">Hogares que consumen nuestros productos</h4>
        <p style="color:var(--dark-soft);font-size:0.92rem;line-height:1.6;margin-bottom:14px;">
          La digitalización permite recuperar ventas perdidas, atraer nuevos clientes y capitalizar el alto reconocimiento de la marca en los hogares tocaimunos.
        </p>
        <ul style="color:var(--dark-soft);font-size:0.85rem;line-height:1.6;padding-left:1.5rem;">
          <li><strong>81%:</strong> Ventas dependen del cliente que ya conoce Salsamentaria Sofi.</li>
          <li><strong>62%:</strong> Turistas que no encuentra a Salsamentaria Sofi online y se pierden como clientes.</li>
          <li><strong>30%:</strong> Ventas perdidas que se pueden recuperar con información digital.</li>
          <li><strong>28%:</strong> Crecimiento potencial en clientes nuevos con la digitalización.</li>
        </ul>
      </div>
      <div>
        <!-- Reemplazamos la gráfica Chart.js anterior con una imagen o simplemente un diseño css para reflejar los datos -->
        <canvas id="senaChart" style="max-height: 240px;"></canvas>
      </div>
    </div>
  </div>
</section>

<!-- ==========================================================
     SECCIÓN 2: CATÁLOGO DE PRODUCTOS (SALSAMENTARÍA, EMPAQUES & DESECHABLES)
========================================================== -->
<section id="productos">
  <div class="section-header">
    <span class="section-tag"><i class="fas fa-tag"></i> Variedad, Frescura &amp; Insumos</span>
    <h2 class="section-title">Catálogo de Productos</h2>
    <p class="section-sub">Explora nuestras carnes frías, quesos, empaques para comidas rápidas, servilletas, vasos térmicos y desechables con fotos reales y precios transparentes.</p>
    <div class="divider"></div>
  </div>

  <div class="catalog-controls">
    <!-- Buscador en tiempo real -->
    <div class="search-box-wrap">
      <i class="fas fa-search search-icon-pos"></i>
      <input type="text" id="product-search" class="search-box-input" placeholder="Buscar por producto (ej: hamburguesa, perro, pizza, arepa, vaso, servilletas, queso, jamón, cubiertos)..." oninput="handleProductSearch()">
    </div>

    <!-- Pestañas de categorías -->
    <div class="category-tabs">
      <button class="cat-tab active" onclick="filterProducts('todos')" id="tab-todos">
        ✨ Todos
      </button>
      <button class="cat-tab" onclick="filterProducts('empaques')" id="tab-empaques">
        🍔 Empaques Comidas Rápidas
      </button>
      <button class="cat-tab" onclick="filterProducts('desechables')" id="tab-desechables">
        📦 Desechables, Servilletas &amp; Vasos
      </button>
      <button class="cat-tab" onclick="filterProducts('carnes')" id="tab-carnes">
        🥩 Carnes Frías &amp; Jamones
      </button>
      <button class="cat-tab" onclick="filterProducts('quesos')" id="tab-quesos">
        🧀 Quesos &amp; Lácteos
      </button>
      <button class="cat-tab" onclick="filterProducts('embutidos')" id="tab-embutidos">
        🥓 Embutidos &amp; Ahumados
      </button>
      <button class="cat-tab" onclick="filterProducts('salsas')" id="tab-salsas">
        🥫 Salsas &amp; Encurtidos
      </button>
      <button class="cat-tab" onclick="filterProducts('combos')" id="tab-combos">
        🧺 Tablas &amp; Combos
      </button>
    </div>
  </div>

  <!-- Rejilla de productos -->
  <div class="products-grid" id="products-grid"></div>
</section>

<!-- ==========================================================
     SECCIÓN 3: ARMADOR INTERACTIVO DE TABLAS GOURMET
========================================================== -->
<section id="cotizador">
  <div class="section-header" style="margin-bottom:30px;">
    <span class="section-tag" style="background:rgba(200,138,46,0.2);color:#FDE68A;border-color:var(--accent);"><i class="fas fa-magic"></i> Personalizador</span>
    <h2 class="section-title" style="color:white;">Arma tu Tabla de Charcutería</h2>
    <p class="section-sub" style="color:#D1D5DB;">Elige tus ingredientes favoritos y te la preparamos a la medida para tus reuniones en Tocaima.</p>
    <div class="divider"></div>
  </div>

  <div class="customizer-box">
    <div class="customizer-steps-grid">
      <!-- Paso 1: Tamaño -->
      <div class="cust-step-card">
        <div class="cust-step-title"><i class="fas fa-users"></i> 1. Tamaño de la Tabla</div>
        <label class="cust-checkbox-label">
          <input type="radio" name="cust-size" value="35000" checked onchange="calculateCustomTable()">
          <span>Personal / Pareja (2 pers.) — <strong>$35.000</strong></span>
        </label>
        <label class="cust-checkbox-label">
          <input type="radio" name="cust-size" value="65000" onchange="calculateCustomTable()">
          <span>Familiar (4-6 pers.) — <strong>$65.000</strong></span>
        </label>
        <label class="cust-checkbox-label">
          <input type="radio" name="cust-size" value="110000" onchange="calculateCustomTable()">
          <span>Evento Fiesta (8-10 pers.) — <strong>$110.000</strong></span>
        </label>
      </div>

      <!-- Paso 2: Selección de Carnes & Quesos -->
      <div class="cust-step-card">
        <div class="cust-step-title"><i class="fas fa-drumstick-bite"></i> 2. Carnes &amp; Quesos</div>
        <label class="cust-checkbox-label">
          <input type="checkbox" class="cust-extra" value="5000" checked onchange="calculateCustomTable()">
          <span>Jamón Serrano o Ahumado (+ $5.000)</span>
        </label>
        <label class="cust-checkbox-label">
          <input type="checkbox" class="cust-extra" value="4500" checked onchange="calculateCustomTable()">
          <span>Queso Madurado Tilsit (+ $4.500)</span>
        </label>
        <label class="cust-checkbox-label">
          <input type="checkbox" class="cust-extra" value="4000" onchange="calculateCustomTable()">
          <span>Salami Italiano con Pimienta (+ $4.000)</span>
        </label>
        <label class="cust-checkbox-label">
          <input type="checkbox" class="cust-extra" value="3500" checked onchange="calculateCustomTable()">
          <span>Queso Mozzarella en Cubos (+ $3.500)</span>
        </label>
      </div>

      <!-- Paso 3: Acompañamientos & Salsas -->
      <div class="cust-step-card">
        <div class="cust-step-title"><i class="fas fa-cookie"></i> 3. Acompañamientos</div>
        <label class="cust-checkbox-label">
          <input type="checkbox" class="cust-extra" value="3000" checked onchange="calculateCustomTable()">
          <span>Aceitunas y Pepinillos (+ $3.000)</span>
        </label>
        <label class="cust-checkbox-label">
          <input type="checkbox" class="cust-extra" value="3500" checked onchange="calculateCustomTable()">
          <span>Tostaditas &amp; Galletas Club (+ $3.500)</span>
        </label>
        <label class="cust-checkbox-label">
          <input type="checkbox" class="cust-extra" value="4000" onchange="calculateCustomTable()">
          <span>Frutos Secos &amp; Uvas (+ $4.000)</span>
        </label>
        <label class="cust-checkbox-label">
          <input type="checkbox" class="cust-extra" value="3000" checked onchange="calculateCustomTable()">
          <span>Salsa Tártara o BBQ de la Casa (+ $3.000)</span>
        </label>
      </div>
    </div>

    <div class="cust-total-bar">
      <div>
        <div style="font-size:0.85rem;color:#D1D5DB;text-transform:uppercase;letter-spacing:1px;font-weight:700;">Precio Estimado de la Tabla</div>
        <div class="cust-total-price" id="cust-total-display">$54.000</div>
      </div>
      <button class="btn-hero-primary" onclick="addCustomTableToCart()" style="border:none;cursor:pointer;">
        <i class="fas fa-cart-plus"></i> Agregar Tabla Personalizada al Pedido
      </button>
    </div>
  </div>
</section>

<!-- ==========================================================
     SECCIÓN 4: SOBRE NOSOTROS
========================================================== -->

<section id="nosotros">
  <div class="about-grid">
    <div class="about-img-container">
      <img src="https://images.unsplash.com/photo-1544025162-d76694265947?auto=format&fit=crop&w=800&q=80" alt="Tabla de quesos y carnes frías" class="about-main-img" onerror="this.src='logo.jpg'" />
      <div class="about-floating-card">
        <div class="about-num">100%</div>
        <div class="about-label">Frescura &amp; Calidad</div>
      </div>
    </div>

    <div class="about-text-content">
      <span class="section-tag"><i class="fas fa-heart"></i> Misión y Visión</span>
      <h3>Salsamentaria Sofi</h3>
      <div style="margin-bottom: 20px;">
        <h4 style="color:var(--primary); font-size: 1.1rem; margin-bottom: 8px;"><i class="fas fa-bullseye"></i> Misión</h4>
        <p>En Salsamentaria Sofi se trabaja para ofrecer productos frescos, de excelente calidad y al mejor precio, brindando una atención amable y confiable.</p>
      </div>
      <div style="margin-bottom: 20px;">
        <h4 style="color:var(--primary); font-size: 1.1rem; margin-bottom: 8px;"><i class="fas fa-eye"></i> Visión</h4>
        <p>Ser una salsamentaria reconocida por su calidad, compromiso y excelente atención al cliente.</p>
      </div>

      <div class="about-pillars">
        <div class="pillar-card">
          <h4><i class="fas fa-shield-alt" style="color:var(--primary);"></i> Higiene y Frescura</h4>
          <p>Cadena de frío continua y estricto control de salubridad en cada uno de nuestros alimentos.</p>
        </div>
        <div class="pillar-card">
          <h4><i class="fas fa-balance-scale" style="color:var(--primary);"></i> Pesaje Exacto y Precios Justos</h4>
          <p>Gramajes garantizados y precios accesibles para consentir tu paladar sin gastar de más.</p>
        </div>
        <div class="pillar-card">
          <h4><i class="fas fa-truck" style="color:var(--primary);"></i> Domicilios en Tocaima</h4>
          <p>Llevamos tu pedido fresco directamente a la puerta de tu hogar, negocio o finca campestre.</p>
        </div>
        <div class="pillar-card">
          <h4><i class="fas fa-boxes" style="color:var(--primary);"></i> Venta al por Mayor y Detal</h4>
          <p>Surtido permanente de cajas para hamburguesas, perros, pizzas, vasos y servilletas para negocios.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ==========================================================
     SECCIÓN 5: UBICACIÓN, CONTACTO & MAPA (TOCAIMA)
========================================================== -->
<section id="contacto">
  <div class="section-header">
    <span class="section-tag"><i class="fas fa-map-marker-alt"></i> Punto de Atención</span>
    <h2 class="section-title">Ubicación y Horarios</h2>
    <p class="section-sub">Encuéntranos en el sector comercial de Tocaima o solicita tu servicio a domicilio por WhatsApp.</p>
    <div class="divider"></div>
  </div>

  <div class="contact-grid">
    <div class="contact-card-box">
      <h3 style="font-size:1.4rem;font-weight:900;color:var(--primary);margin-bottom:20px;">Información de Contacto</h3>

      <div class="contact-item-row">
        <div class="contact-icon-bubble"><i class="fas fa-map-pin"></i></div>
        <div class="contact-text-wrap">
          <h5>Dirección del Establecimiento</h5>
          <p>Sector Comercial Centro, Tocaima, Cundinamarca</p>
        </div>
      </div>

      <div class="contact-item-row">
        <div class="contact-icon-bubble"><i class="fas fa-clock"></i></div>
        <div class="contact-text-wrap">
          <h5>Horario de Atención</h5>
          <p>Lunes a Sábado: 8:00 AM – 8:00 PM<br/>Domingos y Festivos: 8:00 AM – 6:00 PM</p>
        </div>
      </div>

      <div class="contact-item-row">
        <div class="contact-icon-bubble"><i class="fas fa-phone-alt"></i></div>
        <div class="contact-text-wrap">
          <h5>Teléfono y Domicilios</h5>
          <p>+57 313 429 2831</p>
        </div>
      </div>

      <div class="contact-item-row" style="border-bottom:none;margin-bottom:0;padding-bottom:0;">
        <div class="contact-icon-bubble"><i class="fab fa-whatsapp"></i></div>
        <div class="contact-text-wrap">
          <h5>Atención por WhatsApp</h5>
          <p>Respuestas inmediatas para pedidos de charcutería, cajas de comida y empaques desechables.</p>
        </div>
      </div>

      <div style="margin-top:24px;">
        <a href="https://wa.me/573134292831?text=Hola%20Salsamentar%C3%ADa%20La%20Especial,%20deseo%20hacer%20un%20pedido" target="_blank" id="btn-send-whatsapp" style="margin-bottom:10px;">
          <i class="fab fa-whatsapp"></i> Escribir a WhatsApp Ahora
        </a>
      </div>
    </div>

    <!-- Mapa Leaflet interactivo -->
    <div class="map-box-wrap">
      <div class="map-header-status">
        <span><i class="fas fa-map-marked-alt" style="color:var(--accent);"></i> Mapa Interactivo • Tocaima, Cundinamarca</span>
        <button onclick="centerMapTocaima()" style="background:rgba(255,255,255,0.15);border:none;color:white;padding:4px 10px;border-radius:4px;cursor:pointer;font-size:0.8rem;font-weight:700;">
          <i class="fas fa-crosshairs"></i> Centrar
        </button>
      </div>
      <div id="map"></div>
    </div>
  </div>
</section>

<!-- ==========================================================
     SECCIÓN 6: EQUIPO DE TRABAJO SENA (DEL PDF)
========================================================== -->
<section id="equipo">
  <div class="section-header">
    <span class="section-tag"><i class="fas fa-user-graduate"></i> Integrantes del Proyecto</span>
    <h2 class="section-title">Equipo de Trabajo SENA</h2>
    <p class="section-sub">Estudiantes investigadores y desarrolladores del Proyecto TICs SENA 1102.</p>
    <div class="divider"></div>
  </div>

  <div class="team-grid">
    <!-- 1. Liseth Ñañez -->
    <div class="team-member-card">
      <div class="team-avatar-container">
        <div class="team-avatar-ring"></div>
        <div class="team-avatar-inner">
          <img src="" alt="Liseth Ñañez" onerror="this.parentElement.innerHTML='<div class=\'team-avatar-fallback\'>👩‍💻</div>'" />
        </div>
      </div>
      <div class="team-student-name">LISETH ÑAÑEZ</div>
      <div class="team-student-role">Líder de Proyecto</div>
      <div class="team-student-tag">Desarrollo</div>
    </div>

    <!-- 2. Andrea Trujillo -->
    <div class="team-member-card">
      <div class="team-avatar-container">
        <div class="team-avatar-ring" style="background:linear-gradient(135deg, #E67E22, #F39C12);"></div>
        <div class="team-avatar-inner">
          <img src="" alt="Andrea Trujillo" onerror="this.parentElement.innerHTML='<div class=\'team-avatar-fallback\'>👩‍💼</div>'" />
        </div>
      </div>
      <div class="team-student-name">ANDREA TRUJILLO</div>
      <div class="team-student-role">Investigadora</div>
      <div class="team-student-tag">Gestión</div>
    </div>

    <!-- 3. Dana Carabali -->
    <div class="team-member-card">
      <div class="team-avatar-container">
        <div class="team-avatar-ring" style="background:linear-gradient(135deg, #8E44AD, #C0392B);"></div>
        <div class="team-avatar-inner">
          <img src="" alt="Dana Carabali" onerror="this.parentElement.innerHTML='<div class=\'team-avatar-fallback\'>🎨</div>'" />
        </div>
      </div>
      <div class="team-student-name">DANA CARABALI</div>
      <div class="team-student-role">Diseño</div>
      <div class="team-student-tag">UI/UX</div>
    </div>

    <!-- 4. Gabriela Alvarez -->
    <div class="team-member-card">
      <div class="team-avatar-container">
        <div class="team-avatar-ring" style="background:linear-gradient(135deg, #27AE60, #2ECC71);"></div>
        <div class="team-avatar-inner">
          <img src="" alt="Gabriela Alvarez" onerror="this.parentElement.innerHTML='<div class=\'team-avatar-fallback\'>👩‍💻</div>'" />
        </div>
      </div>
      <div class="team-student-name">GABRIELA ALVAREZ</div>
      <div class="team-student-role">Analista</div>
      <div class="team-student-tag">Documentación</div>
    </div>
  </div>
</section>

<!-- ==========================================================
     FOOTER
========================================================== -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <h3>Sofi 🥓</h3>
      <p class="footer-desc">
        Salsamentaría, Charcutería y Distribución de Empaques y Desechables en Tocaima, Cundinamarca. Todo en carnes frías, quesos, embutidos, cajas de hamburguesa, vasos térmicos y bolsas para tu hogar o negocio.
      </p>
      <div class="footer-social-links">
        <a href="https://wa.me/573134292831" target="_blank" aria-label="WhatsApp"><i class="fab fa-whatsapp"></i></a>
        <a href="tel:+573134292831" aria-label="Teléfono"><i class="fas fa-phone-alt"></i></a>
        <a href="#contacto" aria-label="Ubicación"><i class="fas fa-map-marker-alt"></i></a>
      </div>
    </div>

    <div class="footer-col">
      <h4>Categorías</h4>
      <ul>
        <li><a href="#productos" onclick="filterProducts('empaques')"><i class="fas fa-chevron-right"></i> Empaques Comidas Rápidas</a></li>
        <li><a href="#productos" onclick="filterProducts('desechables')"><i class="fas fa-chevron-right"></i> Desechables &amp; Vasos</a></li>
        <li><a href="#productos" onclick="filterProducts('carnes')"><i class="fas fa-chevron-right"></i> Carnes Frías &amp; Jamones</a></li>
        <li><a href="#productos" onclick="filterProducts('quesos')"><i class="fas fa-chevron-right"></i> Quesos &amp; Lácteos</a></li>
        <li><a href="#productos" onclick="filterProducts('embutidos')"><i class="fas fa-chevron-right"></i> Embutidos &amp; Ahumados</a></li>
      </ul>
    </div>

    <div class="footer-col">
      <h4>Navegación</h4>
      <ul>
        <li><a href="#inicio"><i class="fas fa-chevron-right"></i> Inicio</a></li>
        <li><a href="#proyecto-sena"><i class="fas fa-chevron-right"></i> Proyecto SENA</a></li>
        <li><a href="#productos"><i class="fas fa-chevron-right"></i> Catálogo</a></li>
        <li><a href="#cotizador"><i class="fas fa-chevron-right"></i> Armar Tabla</a></li>
        <li><a href="#equipo"><i class="fas fa-chevron-right"></i> Equipo Investigador</a></li>
      </ul>
    </div>

    <div class="footer-col">
      <h4>Atención Tocaima</h4>
      <ul>
        <li><a href="tel:+573134292831"><i class="fas fa-phone"></i> 313 429 2831</a></li>
    <li><a href="#contacto"><i class="fas fa-map-marker-alt"></i> Tocaima, Cundinamarca</a></li>
    <li><a href="#contacto"><i class="fas fa-clock"></i> Lun - Sáb: 8am a 8pm</a></li>
        <li><a href="mailto:salsamentarialaespecial@gmail.com"><i class="fas fa-envelope"></i> Contacto Comercial</a></li>
      </ul>
    </div>
  </div>

  <div class="footer-bottom">
    <p>© 2025 Salsamentaría, Empaques &amp; Desechables Sofi — Tocaima, Cundinamarca.</p>
    <p>Proyecto TICs SENA • Ficha 1102 • Desarrollado con dedicación</p>
  </div>
</footer>

<!-- Toast notification -->
<div id="toast"><i class="fas fa-check-circle" style="color:var(--accent);"></i> <span id="toast-msg">Producto agregado</span></div>

<!-- Back to top button -->
<button id="back-top" onclick="window.scrollTo({top:0,behavior:'smooth'})" aria-label="Volver arriba">
  <i class="fas fa-arrow-up"></i>
</button>

<!-- Leaflet JS -->
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
/* ==========================================================
   DATOS COMPLETOS DE PRODUCTOS (CON TODAS LAS FOTOS REALES)
========================================================== */
const products = [
  {
    id: 1000,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.02%20PM%20(1).jpeg'
  },
  {
    id: 1001,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.02%20PM.jpeg'
  },
  {
    id: 1002,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.03%20PM%20(1).jpeg'
  },
  {
    id: 1003,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.03%20PM%20(2).jpeg'
  },
  {
    id: 1004,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.03%20PM.jpeg'
  },
  {
    id: 1005,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.04%20PM%20(1).jpeg'
  },
  {
    id: 1006,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.04%20PM%20(2).jpeg'
  },
  {
    id: 1007,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.04%20PM.jpeg'
  },
  {
    id: 1008,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.05%20PM%20(1).jpeg'
  },
  {
    id: 1009,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.05%20PM%20(2).jpeg'
  },
  {
    id: 1010,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.05%20PM%20(3).jpeg'
  },
  {
    id: 1011,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.05%20PM.jpeg'
  },
  {
    id: 1012,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.06%20PM%20(1).jpeg'
  },
  {
    id: 1013,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.06%20PM%20(2).jpeg'
  },
  {
    id: 1014,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.06%20PM%20(3).jpeg'
  },
  {
    id: 1015,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.06%20PM.jpeg'
  },
  {
    id: 1016,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.07%20PM%20(1).jpeg'
  },
  {
    id: 1017,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.07%20PM%20(2).jpeg'
  },
  {
    id: 1018,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.07%20PM%20(3).jpeg'
  },
  {
    id: 1019,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.07%20PM%20(4).jpeg'
  },
  {
    id: 1020,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.07%20PM.jpeg'
  },
  {
    id: 1021,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.08%20PM%20(1).jpeg'
  },
  {
    id: 1022,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.08%20PM%20(2).jpeg'
  },
  {
    id: 1023,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.08%20PM%20(3).jpeg'
  },
  {
    id: 1024,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.08%20PM%20(4).jpeg'
  },
  {
    id: 1025,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.08%20PM.jpeg'
  },
  {
    id: 1026,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.09%20PM%20(1).jpeg'
  },
  {
    id: 1027,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.09%20PM%20(2).jpeg'
  },
  {
    id: 1028,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.09%20PM%20(3).jpeg'
  },
  {
    id: 1029,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.09%20PM.jpeg'
  },
  {
    id: 1030,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.10%20PM%20(1).jpeg'
  },
  {
    id: 1031,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.10%20PM%20(2).jpeg'
  },
  {
    id: 1032,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.10%20PM%20(3).jpeg'
  },
  {
    id: 1033,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.10%20PM%20(4).jpeg'
  },
  {
    id: 1034,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.10%20PM%20(5).jpeg'
  },
  {
    id: 1035,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.10%20PM.jpeg'
  },
  {
    id: 1036,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.11%20PM%20(1).jpeg'
  },
  {
    id: 1037,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.11%20PM%20(2).jpeg'
  },
  {
    id: 1038,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.11%20PM%20(3).jpeg'
  },
  {
    id: 1039,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.11%20PM.jpeg'
  },
  {
    id: 1040,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.12%20PM%20(1).jpeg'
  },
  {
    id: 1041,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.12%20PM%20(2).jpeg'
  },
  {
    id: 1042,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.12%20PM.jpeg'
  },
  {
    id: 1043,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.13%20PM%20(1).jpeg'
  },
  {
    id: 1044,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.13%20PM%20(2).jpeg'
  },
  {
    id: 1045,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.13%20PM.jpeg'
  },
  {
    id: 1046,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.14%20PM%20(1).jpeg'
  },
  {
    id: 1047,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.14%20PM%20(2).jpeg'
  },
  {
    id: 1048,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.14%20PM%20(3).jpeg'
  },
  {
    id: 1049,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.14%20PM%20(4).jpeg'
  },
  {
    id: 1050,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.14%20PM%20(5).jpeg'
  },
  {
    id: 1051,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.14%20PM.jpeg'
  },
  {
    id: 1052,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.15%20PM%20(1).jpeg'
  },
  {
    id: 1053,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.15%20PM%20(2).jpeg'
  },
  {
    id: 1054,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.15%20PM%20(3).jpeg'
  },
  {
    id: 1055,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.15%20PM%20(4).jpeg'
  },
  {
    id: 1056,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.15%20PM.jpeg'
  },
  {
    id: 1057,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.16%20PM%20(1).jpeg'
  },
  {
    id: 1058,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.16%20PM.jpeg'
  },
  {
    id: 1059,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.17%20PM%20(1).jpeg'
  },
  {
    id: 1060,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.17%20PM%20(2).jpeg'
  },
  {
    id: 1061,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.17%20PM%20(3).jpeg'
  },
  {
    id: 1062,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.17%20PM.jpeg'
  },
  {
    id: 1063,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.18%20PM%20(1).jpeg'
  },
  {
    id: 1064,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.18%20PM.jpeg'
  },
  {
    id: 1065,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.19%20PM%20(1).jpeg'
  },
  {
    id: 1066,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.19%20PM.jpeg'
  },
  {
    id: 1067,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.20%20PM%20(1).jpeg'
  },
  {
    id: 1068,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.20%20PM%20(2).jpeg'
  },
  {
    id: 1069,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.20%20PM.jpeg'
  },
  {
    id: 1070,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.21%20PM%20(1).jpeg'
  },
  {
    id: 1071,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.21%20PM%20(2).jpeg'
  },
  {
    id: 1072,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.21%20PM%20(3).jpeg'
  },
  {
    id: 1073,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.21%20PM.jpeg'
  },
  {
    id: 1074,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.22%20PM%20(1).jpeg'
  },
  {
    id: 1075,
    category: 'carnes',
    emoji: 'ðŸ“¸',
    name: 'Producto Especial',
    portion: 'Novedad',
    desc: 'Nuevos productos disponibles en nuestro catÃ¡logo. Â¡AcÃ©rcate a conocerlos!',
    price: 0,
    badge: 'Nuevo',
    badgeClass: 'gold',
    img: 'FOTOS SALSAMENTARIA/WhatsApp%20Image%202026-08-19%20at%202.46.22%20PM.jpeg'
  },
  // 1. EMPAQUES PARA COMIDAS RÁPIDAS (FOTOS REALES AGREGADAS)
  {
    id: 201,
    category: 'empaques',
    emoji: '🍔',
    name: 'Cajas de Hamburguesa de Cartón Biodegradable',
    portion: 'Paquete x 100 Unidades (Tamaño 11)',
    desc: 'Empaques de cartón 100% biodegradable "Hamburguer ¡Qué Rico Sabor!". Mantiene el calor, la estructura y presentación perfecta de hamburguesas gourmet y tradicionales.',
    price: 8500,
    badge: '🍔 Biodegradable',
    badgeClass: 'gold',
    img: 'cajas-hamburguesa-biodegradable.jpg'
  },
  {
    id: 202,
    category: 'empaques',
    emoji: '🌭',
    name: 'Cajas para Perro Caliente / Hot Dog',
    portion: 'Paquete x 100 Unidades',
    desc: 'Cajas de cartón ecológico "Hot Dog ¡Qué Rico Sabor!" con cierre práctico para perros calientes, choripanes y salchipapas para llevar.',
    price: 5500,
    badge: '🌭 Hot Dog',
    badgeClass: 'gold',
    img: 'cajas-perro-caliente.jpg'
  },
  {
    id: 203,
    category: 'empaques',
    emoji: '🍕',
    name: 'Cajas Triangulares para Porción de Pizza',
    portion: 'Paquete x 100 Unidades',
    desc: 'Cajas triangulares de cartón resistente "Pizza ¡Qué Rico Sabor!". Aislante de grasa y calor para despachar porciones individuales de pizza con total comodidad.',
    price: 9000,
    badge: '🍕 Porción Pizza',
    badgeClass: 'gold',
    img: 'cajas-pizza-triangular.jpg'
  },
  {
    id: 204,
    category: 'empaques',
    emoji: '🫓',
    name: 'Cajas para Arepa Rellena / Asados',
    portion: 'Paquete x 100 Unidades',
    desc: 'Empaques de cartón con diseño "Deliciosa Arepa" para arepas rellenas de queso, carne desmechada o pollo. Alta resistencia térmica y antigrasa.',
    price: 7500,
    badge: '🫓 Arepa Rellena',
    badgeClass: 'gold',
    img: 'cajas-arepa-rellena.jpg'
  },
  {
    id: 205,
    category: 'empaques',
    emoji: '🥘',
    name: 'Recipientes de Aluminio MIO Food Line (MIO / 04)',
    portion: 'Paquete con Tapas',
    desc: 'Bandejas rectangulares de aluminio MIO Food Line para lasaña, arroz especial, carnes al horno y domicilios calientes. Apto para horno convencional.',
    price: 14500,
    badge: '✨ Horneable',
    badgeClass: 'gold',
    img: 'recipientes-aluminio-mio.jpg'
  },

  // 2. DESECHABLES, SERVILLETAS, VASOS & INSUMOS (FOTOS REALES AGREGADAS)
  {
    id: 101,
    category: 'desechables',
    emoji: '🧻',
    name: 'Servilletas Familia Practi-diarias',
    portion: 'Paquete x 150 Servilletas',
    desc: 'Servilletas de hoja sencilla dobladas en 2 con sistema dispensa 1 a 1. Suavidad superior y máximo ahorro a tu alcance para tu hogar o negocio.',
    price: 3800,
    badge: '⭐ Familia',
    badgeClass: 'gold',
    img: 'servilletas-familia.jpg'
  },
  {
    id: 102,
    category: 'desechables',
    emoji: '🧻',
    name: 'Servilletas Nube MaxiAhorro',
    portion: 'Paquete x 300 Servilletas cortadas',
    desc: 'Servilletas cortadas de 11.8 cm x 25 cm, súper absorbentes y resistentes. Rinde más para restaurantes, salsamentarías y eventos familiares.',
    price: 5200,
    badge: '🔥 MaxiAhorro 300',
    badgeClass: 'gold',
    img: 'servilletas-nube.jpg'
  },
  {
    id: 108,
    category: 'desechables',
    emoji: '🧻',
    name: 'Toalla para Manos Sanitisu Professional ECO',
    portion: 'Paquete x 150 Toallas Doble Hoja',
    desc: 'Toallas de mano dobladas en Z (Z-FOLD) 2-PLY doble hoja (22.5 cm x 22 cm). Línea ecológica de alto rendimiento y resistencia para dispensadores de baño y cocina.',
    price: 6800,
    badge: '🌿 Sanitisu ECO',
    badgeClass: 'gold',
    img: 'toalla-manos-sanitisu.jpg'
  },
  {
    id: 109,
    category: 'desechables',
    emoji: '☕',
    name: 'Vasos Térmicos Darnel 8 Oz (237 ml)',
    portion: 'Paquete x 20 Vasos Espumados',
    desc: 'Vasos térmicos de foam espumado Darnel de 8 Oz. Aislante térmico perfecto para café con leche, chocolate caliente, avena o bebidas frías.',
    price: 4500,
    badge: '☕ Darnel 8 Oz',
    badgeClass: '',
    img: 'vasos-termicos-darnel-8oz.jpg'
  },
  {
    id: 110,
    category: 'desechables',
    emoji: '☕',
    name: 'Vasos Térmicos Darnel 4 Oz (118 ml)',
    portion: 'Paquete x 20 Vasos Espumados',
    desc: 'Vasos térmicos pequeños de foam Darnel de 4 Oz. El tamaño estándar preferido para tinto, espresso, aromáticas o degustaciones y salsas.',
    price: 3200,
    badge: '☕ Tinto 4 Oz',
    badgeClass: '',
    img: 'vasos-termicos-darnel-4oz.jpg'
  },
  {
    id: 206,
    category: 'desechables',
    emoji: '🥤',
    name: 'Vasos Plásticos Transparentes FRESH 9 Oz',
    portion: 'Paquete x 20 Unidades',
    desc: 'Vasos plásticos transparentes de 9 onzas FRESH de alta resistencia, fabricados higiénicamente para jugos, gaseosas y bebidas frías.',
    price: 2800,
    badge: '🥤 Fresh 9 Oz',
    badgeClass: '',
    img: 'vasos-fresh-9oz.jpg'
  },
  {
    id: 207,
    category: 'desechables',
    emoji: '🥃',
    name: 'Vasos Plásticos para Whisky / Licores (Verde)',
    portion: 'Paquete x 20 Unidades',
    desc: 'Vasos tipo whisky pequeños plásticos color verde brillante. Ideales para brindis, degustaciones, licores y celebraciones en Tocaima.',
    price: 3500,
    badge: '🥃 Fiesta',
    badgeClass: '',
    img: 'vasos-whisky-verde.jpg'
  },
  {
    id: 208,
    category: 'desechables',
    emoji: '🥤',
    name: 'Vasos Plásticos Sicodélico 100% Reciclables',
    portion: 'Paquete x 50 Unidades',
    desc: 'Vasos plásticos desechables transparentes marca Sicodélico ¡El único vaso que está en la onda! 100% reciclables para fiestas y eventos.',
    price: 4800,
    badge: '♻️ Sicodélico 50u',
    badgeClass: '',
    img: 'vasos-sicodelico-50und.jpg'
  },
  {
    id: 209,
    category: 'desechables',
    emoji: '🍴',
    name: 'Tenedores Plásticos Desechables FRESH',
    portion: 'Paquete x 100 Unidades',
    desc: 'Cubiertos desechables FRESH de alta resistencia, fabricados higiénicamente para almuerzos, comidas rápidas y eventos.',
    price: 4000,
    badge: '🍴 Fresh 100u',
    badgeClass: '',
    img: 'tenedores-fresh.jpg'
  },
  {
    id: 210,
    category: 'desechables',
    emoji: '🥄',
    name: 'Cucharitas Dulceras Desechables Chévere',
    portion: 'Paquete x 100 Unidades',
    desc: 'Cucharitas dulceras pequeñas marca Chévere para postres, helados, ensaladas de frutas, degustaciones y salsamentaría.',
    price: 3200,
    badge: '🍨 Chévere 100u',
    badgeClass: '',
    img: 'cucharitas-dulceras-chevere.jpg'
  },
  {
    id: 211,
    category: 'desechables',
    emoji: '🧤',
    name: 'Guantes de Manipulación Manoplast Multiusos',
    portion: 'Paquete x 100 Unidades (Talla Única)',
    desc: 'Guantes plásticos desechables Manoplast B&B para higiene y protección en la manipulación segura de alimentos, carnes y embutidos.',
    price: 4500,
    badge: '🛡️ Higiene',
    badgeClass: 'gold',
    img: 'guantes-manipulacion-manoplast.jpg'
  },
  {
    id: 212,
    category: 'desechables',
    emoji: '🍦',
    name: 'Palitos para Helados de Madera INCOMAD',
    portion: 'Paquete x 1000 Unidades aprox. (9.3 cm)',
    desc: 'Paletas populares de madera natural INCOMAD aptas para contacto con alimentos y bebidas. Rinde para heladerías, repostería y manualidades.',
    price: 8900,
    badge: '🍦 1000 Palitos',
    badgeClass: 'gold',
    img: 'palitos-helado-incomad.jpg'
  },
  {
    id: 103,
    category: 'desechables',
    emoji: '✨',
    name: 'Bolsa Aluminizada Térmica ArtilPlast L-17',
    portion: 'Paquete x 100 Unidades aprox.',
    desc: 'Bolsa térmica rectangular aluminizada de alta barrera para conservar la temperatura y frescura de pollos asados enteros, carnes calientes o alimentos refrigerados.',
    price: 18500,
    badge: '🔥 Térmica L-17',
    badgeClass: 'gold',
    img: 'bolsa-aluminizada-artilplast.jpg'
  },
  {
    id: 111,
    category: 'desechables',
    emoji: '🍗',
    name: 'Bolsa Aluminizada Triangular ArtilPlast P-25',
    portion: 'Paquete x 100 Unidades aprox.',
    desc: 'Bolsa aluminizada con diseño triangular ergonómico P-25, ideal para empacar presas individuales de pollo asado, porciones de carne y fritos manteniendo el calor.',
    price: 16000,
    badge: '🍗 Triangular P-25',
    badgeClass: 'gold',
    img: 'bolsa-aluminizada-p25.jpg'
  },
  {
    id: 104,
    category: 'desechables',
    emoji: '🥤',
    name: 'Tapas para Vaso Wau! 3.5, 6 y 7 Oz',
    portion: 'Paquete x 50 Unidades',
    desc: 'Tapas plásticas 100% reciclables compatibles con vasos de 3.5 Oz, 6 Oz y 7 Oz. Cierre hermético ¡Bien Servido! antiderrame para bebidas y salsas.',
    price: 4200,
    badge: '♻️ Reciclable',
    badgeClass: '',
    img: 'tapas-vaso-wau.jpg'
  },
  {
    id: 112,
    category: 'desechables',
    emoji: '🥤',
    name: 'Tapas para Vaso Wau! 13, 14 y 16 Oz',
    portion: 'Paquete x 50 Unidades Grandes',
    desc: 'Tapas plásticas herméticas para vasos grandes de 13, 14 y 16 Oz. Perfectas para jugos naturales, batidos, granizados y bebidas frías.',
    price: 5000,
    badge: '🥤 Vaso Grande',
    badgeClass: '',
    img: 'tapas-vaso-16oz.jpg'
  },
  {
    id: 113,
    category: 'desechables',
    emoji: '🛍️',
    name: 'Bolsas Plásticas Transparentes 6 Libras',
    portion: 'Paquete x 100 Unidades',
    desc: 'Bolsas plásticas transparentes de capacidad 6 libras. Ideales para el despacho de carnes, quesos grandes, víveres a granel y congelados.',
    price: 6500,
    badge: '⚖️ 6 Libras',
    badgeClass: '',
    img: 'bolsas-6libras.jpg'
  },
  {
    id: 105,
    category: 'desechables',
    emoji: '🛍️',
    name: 'Rollo de Bolsas Plásticas Transparentes (Verde)',
    portion: 'Rollo continuo x 100 unidades',
    desc: 'Bolsas plásticas transparentes de alta calidad para despacho de quesos, jamones, carnes frías porcionadas y frutas.',
    price: 4500,
    badge: '👌 Estándar',
    badgeClass: '',
    img: 'bolsas-rollo-verde.jpg'
  },
  {
    id: 106,
    category: 'desechables',
    emoji: '🛍️',
    name: 'Rollo de Bolsas Plásticas Blancas (Amarillo)',
    portion: 'Rollo x 100 unidades',
    desc: 'Bolsas plásticas calibre medio para empaque seguro de salsamentaría, lácteos y productos a granel.',
    price: 5000,
    badge: null,
    badgeClass: '',
    img: 'bolsas-rollo-amarillo.jpg'
  },
  {
    id: 107,
    category: 'desechables',
    emoji: '🛍️',
    name: 'Rollo de Bolsas Plásticas Reforzadas (Azul)',
    portion: 'Rollo resistente x 100 bolsas',
    desc: 'Bolsas plásticas reforzadas de mayor calibre para compras pesadas y despacho en salsamentarías y autoservicios.',
    price: 5500,
    badge: '💪 Reforzada',
    badgeClass: '',
    img: 'bolsas-rollo-azul.jpg'
  },

  // 3. CARNES FRÍAS & JAMONES
  {
    id: 1,
    category: 'carnes',
    emoji: '🥩',
    name: 'Jamón Pietrán de Cerdo Seleccionado',
    portion: 'Porción 250g / 500g',
    desc: 'Jamón de pierna seleccionado bajo en grasa y sodio, finamente tajado para sándwiches gourmet o tablas de carnes frías.',
    price: 9500,
    badge: '⭐ Más Vendido',
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1528735602780-2552fd46c7af?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 2,
    category: 'carnes',
    emoji: '🍗',
    name: 'Pechuga de Pavo Ahumada',
    portion: 'Porción 250g',
    desc: '100% pechuga de pavo curada con madera aromática. Sabor suave, textura jugosa y excelente aporte proteico.',
    price: 12500,
    badge: '👑 Gourmet',
    badgeClass: 'gold',
    img: 'https://images.unsplash.com/photo-1544025162-d76694265947?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 3,
    category: 'carnes',
    emoji: '🥓',
    name: 'Jamón Serrano Reserva Español',
    portion: 'Porción 150g en láminas',
    desc: 'Curación tradicional durante 12 meses. Notas intensas, vetas de grasa noble y aroma inconfundible de charcutería fina.',
    price: 18000,
    badge: '🇪🇸 Importado',
    badgeClass: 'gold',
    img: 'https://images.unsplash.com/photo-1509722747041-616f39b57569?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 4,
    category: 'carnes',
    emoji: '🥩',
    name: 'Mortadela con Pistachos Especial',
    portion: 'Porción 250g tajada',
    desc: 'Elaborada según receta italiana con trozos enteros de pistacho y especias finas. Suavidad y sabor garantizado.',
    price: 8500,
    badge: '👌 Tradicional',
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1541592106381-b31e9677c0e5?auto=format&fit=crop&w=600&q=80'
  },

  // 4. QUESOS & LÁCTEOS
  {
    id: 5,
    category: 'quesos',
    emoji: '🧀',
    name: 'Queso Doble Crema de Campo Tocaima',
    portion: 'Bloque 500g',
    desc: 'Queso hilado fresco elaborado con leche pura de la región del Alto Magdalena. Textura elástica y suave sabor lácteo.',
    price: 11000,
    badge: '⭐ Local Tocaima',
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1486297678162-eb2a19b0a32d?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 6,
    category: 'quesos',
    emoji: '🧀',
    name: 'Queso Mozzarella en Bloque o Tajado',
    portion: 'Porción 450g',
    desc: 'Ideal para fundir en pizzas, lasañas y gratinados. Alto punto de derretimiento y excelente elasticidad.',
    price: 12000,
    badge: null,
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1624806992066-5ffcf7ca186b?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 7,
    category: 'quesos',
    emoji: '🧀',
    name: 'Queso Costeño Artesanal Picado/Rallado',
    portion: 'Porción 500g',
    desc: 'Punto perfecto de sal y firmeza tradicional para arepas, buñuelos o consumo directo.',
    price: 13500,
    badge: '🧂 Sabor Criollo',
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1552767059-ce182ead6c1b?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 8,
    category: 'quesos',
    emoji: '🧀',
    name: 'Queso Tilsit / Gouda Madurado',
    portion: 'Cuña 250g',
    desc: 'Maduración controlada con notas suaves de frutos secos. Imprescindible en tablas de quesos y maridajes.',
    price: 16500,
    badge: '👑 Madurado',
    badgeClass: 'gold',
    img: 'https://images.unsplash.com/photo-1634487359989-3e90c9432133?auto=format&fit=crop&w=600&q=80'
  },

  // 5. EMBUTIDOS & AHUMADOS
  {
    id: 9,
    category: 'embutidos',
    emoji: '🌭',
    name: 'Chorizo Santarrosano Artesanal',
    portion: 'Paquete x 5 unidades (500g)',
    desc: 'Carne de cerdo 100% seleccionada, adobada con hierbas naturales y ahumada suavemente. Cero conservantes artificiales.',
    price: 15000,
    badge: '🔥 Asados',
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1597362925123-77861d3fbac7?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 10,
    category: 'embutidos',
    emoji: '🥓',
    name: 'Tocineta Ahumada Gruesa',
    portion: 'Porción 300g tajada',
    desc: 'Tocino curado con madera de nogal. Vetas equilibradas de carne y grasa crocante al freír o asar.',
    price: 14000,
    badge: '⭐ Crocante',
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1606851094655-b2593a9af63f?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 11,
    category: 'embutidos',
    emoji: '🥓',
    name: 'Salchichón Cervecero Gourmet',
    portion: 'Unidad 400g',
    desc: 'El pasaboca perfecto con limón y pimienta. Elaborado con condimentos que realzan el sabor de la carne curada.',
    price: 9000,
    badge: '🍺 Cervecero',
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1541592106381-b31e9677c0e5?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 12,
    category: 'embutidos',
    emoji: '🍕',
    name: 'Pepperoni Americano en Rodajas',
    portion: 'Porción 200g',
    desc: 'Sabor ligeramente picante con notas de pimentón español y especias. Dorado ideal al horno.',
    price: 11500,
    badge: null,
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1534308983496-4fabb1a015ee?auto=format&fit=crop&w=600&q=80'
  },

  // 6. SALSAS & ENCURTIDOS
  {
    id: 13,
    category: 'salsas',
    emoji: '🥫',
    name: 'Salsa Tártara Especial de la Casa',
    portion: 'Frasco 250g',
    desc: 'Elaborada artesanalmente con mayonesa casera, pepinillos picados, alcaparras y un toque fresco de perejil.',
    price: 6500,
    badge: '✨ De la Casa',
    badgeClass: 'gold',
    img: 'https://images.unsplash.com/photo-1472476443507-c7a5948772fc?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 14,
    category: 'salsas',
    emoji: '🥫',
    name: 'Salsa BBQ Ahumada Artesanal',
    portion: 'Frasco 300g',
    desc: 'Base de tomate especiado, melaza de caña y humo líquido natural. Ideal para costillas, chorizos y hamburguesas.',
    price: 7000,
    badge: null,
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1563729784474-d77dbb933a9e?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 15,
    category: 'salsas',
    emoji: '🥒',
    name: 'Pepinillos Agridulces en Rodajas',
    portion: 'Frasco 320g',
    desc: 'Pepinillos tiernos en salmuera con eneldo y vinagre de manzana. El acompañamiento crujiente perfecto.',
    price: 8000,
    badge: null,
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1594998893017-36147cbcae05?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 16,
    category: 'salsas',
    emoji: '🫒',
    name: 'Aceitunas Rellenas de Pimentón',
    portion: 'Frasco 280g',
    desc: 'Aceitunas manzanilla seleccionadas rellenas de pimiento morrón español, conservadas en aceite de oliva suave.',
    price: 9000,
    badge: '🫒 Importado',
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1563227812-0ea4c22e6cc8?auto=format&fit=crop&w=600&q=80'
  },

  // 7. TABLAS & COMBOS
  {
    id: 17,
    category: 'combos',
    emoji: '🧺',
    name: 'Tabla Picnic Charcutería (Para 2-3 personas)',
    portion: 'Tabla lista para servir',
    desc: 'Incluye: Jamón Pietrán, Salami italiano, Queso Tilsit, Queso doble crema, aceitunas, tostaditas y salsa tártara de la casa.',
    price: 38000,
    badge: '⭐ Muy Pedido',
    badgeClass: 'gold',
    img: 'https://images.unsplash.com/photo-1626082927389-6cd097cdc6ec?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 18,
    category: 'combos',
    emoji: '🧺',
    name: 'Tabla Suprema de Quesos & Carnes (Familiar 5-6 pers.)',
    portion: 'Presentación gourmet en madera',
    desc: 'Selección premium: Jamón Serrano, Pechuga de Pavo ahumada, Pepperoni, Queso Gouda, Queso Mozzarella, uvas, frutos secos y 2 salsas.',
    price: 75000,
    badge: '👑 Gran Evento',
    badgeClass: 'gold',
    img: 'https://images.unsplash.com/photo-1544025162-d76694265947?auto=format&fit=crop&w=600&q=80'
  },
  {
    id: 19,
    category: 'combos',
    emoji: '🔥',
    name: 'Combo Asado Parrillero Tocaimuno',
    portion: 'Rinde 4-5 personas',
    desc: 'Incluye: 5 Chorizos santarrosanos, 300g tocineta ahumada, 1 Salchichón cervecero, 1 bloque de queso costeño y salsa BBQ.',
    price: 48000,
    badge: '🔥 Fin de Semana',
    badgeClass: '',
    img: 'https://images.unsplash.com/photo-1555939594-58d7cb561ad1?auto=format&fit=crop&w=600&q=80'
  }
];

/* ==========================================================
   ESTADO Y ALMACENAMIENTO DEL CARRITO
========================================================== */
let cart = JSON.parse(localStorage.getItem('salsamentaria_cart') || '[]');
let activeCategory = 'todos';
let searchQuery = '';

function saveCart() {
  localStorage.setItem('salsamentaria_cart', JSON.stringify(cart));
}

/* ==========================================================
   RENDERIZADO DE PRODUCTOS
========================================================== */
function renderProducts(category, search = '') {
  const grid = document.getElementById('products-grid');
  let filtered = products;

  if (category && category !== 'todos') {
    filtered = filtered.filter(p => p.category === category);
  }

  if (search.trim()) {
    const q = search.toLowerCase();
    filtered = filtered.filter(p =>
      p.name.toLowerCase().includes(q) ||
      p.desc.toLowerCase().includes(q) ||
      p.portion.toLowerCase().includes(q)
    );
  }

  grid.innerHTML = '';

  if (filtered.length === 0) {
    grid.innerHTML = `
      <div style="grid-column: 1 / -1; text-align: center; padding: 50px 20px; color: var(--gray);">
        <i class="fas fa-search" style="font-size: 2.8rem; margin-bottom: 12px; color: #CBD5E1;"></i>
        <p style="font-size: 1.15rem; font-weight: 800;">No encontramos productos con "${search}"</p>
        <p style="font-size: 0.9rem;">Prueba con otra palabra o explora nuestras categorías principales.</p>
      </div>
    `;
    return;
  }

  filtered.forEach(p => {
    const inCart = cart.find(c => c.id === p.id);
    const card = document.createElement('div');
    card.className = 'product-card';
    card.innerHTML = `
      <div class="product-img-wrap">
        <img src="${p.img}" alt="${p.name}" loading="lazy" onerror="this.src='logo.jpg'" />
        <div class="product-emoji-icon">${p.emoji}</div>
        ${p.badge ? `<div class="product-badge-flag ${p.badgeClass || ''}">${p.badge}</div>` : ''}
      </div>
      <div class="product-body">
        <span class="product-portion-tag"><i class="fas fa-box-open"></i> ${p.portion}</span>
        <h3 class="product-title">${p.name}</h3>
        <p class="product-desc">${p.desc}</p>
        <div class="product-footer">
          <div class="product-price-box">
            <span class="product-price-label">Precio</span>
            <span class="product-price">$${p.price.toLocaleString('es-CO')}</span>
          </div>
          <button class="btn-add-cart ${inCart ? 'added' : ''}" id="btn-add-${p.id}" onclick="addToCart(${p.id})">
            <i class="fas ${inCart ? 'fa-check' : 'fa-plus'}"></i>
            ${inCart ? 'Agregado' : 'Pedir'}
          </button>
        </div>
      </div>
    `;
    grid.appendChild(card);
  });
}

function filterProducts(category) {
  activeCategory = category;
  document.querySelectorAll('.cat-tab').forEach(t => t.classList.remove('active'));
  const tabEl = document.getElementById('tab-' + category);
  if (tabEl) tabEl.classList.add('active');
  renderProducts(category, searchQuery);
}

function handleProductSearch() {
  searchQuery = document.getElementById('product-search').value;
  renderProducts(activeCategory, searchQuery);
}

/* ==========================================================
   OPERACIONES DEL CARRITO
========================================================== */
function addToCart(productId) {
  const product = products.find(p => p.id === productId);
  if (!product) return;

  const existing = cart.find(c => c.id === productId);
  if (existing) {
    existing.qty++;
  } else {
    cart.push({ ...product, qty: 1 });
  }

  saveCart();
  updateCartUI();
  showToast(`${product.emoji} ${product.name} agregado a la canasta`);

  const btn = document.getElementById('btn-add-' + productId);
  if (btn) {
    btn.classList.add('added');
    btn.innerHTML = '<i class="fas fa-check"></i> Agregado';
  }
}

function removeFromCart(productId) {
  const idx = cart.findIndex(c => c.id === productId);
  if (idx !== -1) {
    if (cart[idx].qty > 1) {
      cart[idx].qty--;
    } else {
      cart.splice(idx, 1);
    }
  }

  saveCart();
  updateCartUI();

  const inCart = cart.find(c => c.id === productId);
  if (!inCart) {
    const btn = document.getElementById('btn-add-' + productId);
    if (btn) {
      btn.classList.remove('added');
      btn.innerHTML = '<i class="fas fa-plus"></i> Pedir';
    }
  }
}

function clearCart() {
  cart = [];
  saveCart();
  updateCartUI();
  renderProducts(activeCategory, searchQuery);
  showToast('🗑️ Canasta vaciada');
}

function updateCartUI() {
  const totalItems = cart.reduce((s, i) => s + i.qty, 0);
  const totalPrice = cart.reduce((s, i) => s + i.price * i.qty, 0);

  document.getElementById('cart-count').textContent = totalItems;
  document.getElementById('cart-total-price').textContent = '$' + totalPrice.toLocaleString('es-CO');

  const cartItemsEl = document.getElementById('cart-items');

  if (cart.length === 0) {
    cartItemsEl.innerHTML = `
      <div class="cart-empty" id="cart-empty">
        <div><i class="fas fa-shopping-basket"></i></div>
        <p>¡Tu canasta está vacía!</p>
        <p style="font-size:0.8rem;margin-top:4px;">Elige carnes frías, quesos, cajas de comida o desechables para pedir 🥩🍔🧻</p>
      </div>
    `;
    return;
  }

  cartItemsEl.innerHTML = cart.map(item => `
    <div class="cart-item">
      ${item.img ? `<img src="${item.img}" alt="${item.name}" class="cart-item-img" onerror="this.style.display='none'">` : `<div class="cart-item-emoji">${item.emoji || '🥓'}</div>`}
      <div class="cart-item-info">
        <div class="cart-item-name">${item.name}</div>
        <div class="cart-item-portion">${item.portion || 'Porción seleccionada'}</div>
        <div class="cart-item-price">$${(item.price * item.qty).toLocaleString('es-CO')} ($${item.price.toLocaleString('es-CO')} c/u)</div>
      </div>
      <div class="cart-item-controls">
        <button class="qty-btn" onclick="removeFromCart(${item.id})" aria-label="Disminuir">−</button>
        <span class="qty-num">${item.qty}</span>
        <button class="qty-btn" onclick="addToCart(${item.id})" aria-label="Aumentar">+</button>
      </div>
    </div>
  `).join('');
}

function toggleCart() {
  const dropdown = document.getElementById('cart-dropdown');
  dropdown.classList.toggle('open');
}

function toggleMobileMenu() {
  const drawer = document.getElementById('mobile-nav-drawer');
  const overlay = document.getElementById('mobile-nav-overlay');
  drawer.classList.toggle('open');
  overlay.classList.toggle('open');
}

document.addEventListener('click', function(e) {
  const dropdown = document.getElementById('cart-dropdown');
  const cartBtn = document.getElementById('cart-btn');
  if (dropdown && cartBtn && !dropdown.contains(e.target) && !cartBtn.contains(e.target)) {
    dropdown.classList.remove('open');
  }
});

/* ==========================================================
   COTIZADOR DINÁMICO DE TABLAS
========================================================== */
function calculateCustomTable() {
  const baseSizeEl = document.querySelector('input[name="cust-size"]:checked');
  let basePrice = baseSizeEl ? parseInt(baseSizeEl.value) : 35000;

  const extras = document.querySelectorAll('.cust-extra:checked');
  let extraSum = 0;
  extras.forEach(ex => {
    extraSum += parseInt(ex.value);
  });

  const total = basePrice + extraSum;
  document.getElementById('cust-total-display').textContent = '$' + total.toLocaleString('es-CO');
  return total;
}

function addCustomTableToCart() {
  const total = calculateCustomTable();
  const baseSizeEl = document.querySelector('input[name="cust-size"]:checked');
  let sizeLabel = 'Tabla Personalizada';
  if (baseSizeEl.value === '35000') sizeLabel = 'Tabla Personal (2 pers.)';
  else if (baseSizeEl.value === '65000') sizeLabel = 'Tabla Familiar (4-6 pers.)';
  else sizeLabel = 'Tabla Fiesta Evento (8-10 pers.)';

  const customId = 9999 + Date.now() % 10000;
  const customItem = {
    id: customId,
    category: 'combos',
    emoji: '🧺',
    name: `${sizeLabel} Gourmet`,
    portion: 'Personalizada al Gusto',
    desc: 'Tabla armada a medida con selección de quesos finos, carnes frías y acompañamientos.',
    price: total,
    qty: 1,
    img: 'https://images.unsplash.com/photo-1544025162-d76694265947?auto=format&fit=crop&w=600&q=80'
  };

  cart.push(customItem);
  saveCart();
  updateCartUI();
  showToast(`🧺 ${customItem.name} agregada a la canasta`);
  toggleCart();
}

/* ==========================================================
   ENVIAR PEDIDO A WHATSAPP
========================================================== */
function sendToWhatsApp() {
  if (cart.length === 0) {
    showToast('⚠️ Tu canasta de compras está vacía');
    return;
  }

  const phone = '573134292831'; // Salsamentaría Tocaima
  const clientName = document.getElementById('order-client-name').value.trim() || 'Cliente';
  const clientAddress = document.getElementById('order-client-address').value.trim() || 'Entrega en Tocaima / Por acordar';
  const paymentMethod = document.getElementById('order-payment-method').value;

  let msg = `🥓 *PEDIDO - SALSAMENTARÍA, EMPAQUES & DESECHABLES Sofi*\n`;
  msg += `📍 *Tocaima, Cundinamarca*\n`;
  msg += `━━━━━━━━━━━━━━━━━━━━\n`;
  msg += `👤 *Cliente:* ${clientName}\n`;
  msg += `🏠 *Dirección/Entrega:* ${clientAddress}\n`;
  msg += `💳 *Método de Pago:* ${paymentMethod}\n`;
  msg += `━━━━━━━━━━━━━━━━━━━━\n`;
  msg += `📋 *PRODUCTOS SELECCIONADOS:*\n\n`;

  cart.forEach((item, index) => {
    msg += `${index + 1}. ${item.emoji || '📦'} *${item.name}*\n`;
    msg += `   Presentación: ${item.portion || 'Estándar'}\n`;
    msg += `   Cantidad: ${item.qty} | Subtotal: $${(item.price * item.qty).toLocaleString('es-CO')}\n\n`;
  });

  const total = cart.reduce((s, i) => s + i.price * i.qty, 0);
  msg += `━━━━━━━━━━━━━━━━━━━━\n`;
  msg += `💰 *TOTAL A PAGAR: $${total.toLocaleString('es-CO')}*\n\n`;
  msg += `¡Hola Salsamentaría Sofi! Quiero confirmar este pedido desde la página web. 😊🥓`;

  const url = `https://wa.me/${phone}?text=${encodeURIComponent(msg)}`;
  window.open(url, '_blank');
}

/* ==========================================================
   NOTIFICACIÓN TOAST
========================================================== */
function showToast(message) {
  const toast = document.getElementById('toast');
  document.getElementById('toast-msg').textContent = message;
  toast.classList.add('show');
  setTimeout(() => toast.classList.remove('show'), 2800);
}

/* ==========================================================
   SCROLL NAVBAR & BACK TO TOP
========================================================== */
window.addEventListener('scroll', function() {
  const navbar = document.getElementById('navbar');
  const backTop = document.getElementById('back-top');

  if (window.scrollY > 60) {
    navbar.classList.add('scrolled');
  } else {
    navbar.classList.remove('scrolled');
  }

  if (window.scrollY > 400) {
    backTop.classList.add('visible');
  } else {
    backTop.classList.remove('visible');
  }
});

/* ==========================================================
   ESTADO DE HORARIO EN VIVO
========================================================== */
function checkBusinessHours() {
  const now = new Date();
  const hour = now.getHours();
  const statusBadge = document.getElementById('business-status-badge');
  const statusText = document.getElementById('business-status-text');

  // Horario de atención: 8:00 AM a 8:00 PM (20:00)
  if (hour >= 8 && hour < 20) {
    statusBadge.className = 'hero-badge status-open';
    statusText.textContent = 'Abierto Ahora • 8am a 8pm';
  } else {
    statusBadge.className = 'hero-badge';
    statusText.textContent = 'Cerrado Ahora • Abre a las 8:00 AM';
  }
}

/* ==========================================================
   MAPA INTERACTIVO LEAFLET (TOCAIMA, CUNDINAMARCA)
========================================================== */
let map;
let marker;
const TOCAIMA_COORDS = [4.4589, -74.6335];

function initMap() {
  if (typeof L === 'undefined') return;

  map = L.map('map', { scrollWheelZoom: false }).setView(TOCAIMA_COORDS, 16);

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '© <a href="https://openstreetmap.org">OpenStreetMap</a>'
  }).addTo(map);

  const customIcon = L.divIcon({
    html: `<div style="
      background: linear-gradient(135deg, #8B181B, #C88A2E);
      width: 44px; height: 44px;
      border-radius: 50% 50% 50% 0;
      transform: rotate(-45deg);
      box-shadow: 0 4px 15px rgba(139,24,27,0.5);
      display: flex;
      align-items: center;
      justify-content: center;
      border: 3px solid white;
    ">
      <span style="transform: rotate(45deg); font-size:20px;">🥓</span>
    </div>`,
    className: '',
    iconSize: [44, 44],
    iconAnchor: [22, 44]
  });

  marker = L.marker(TOCAIMA_COORDS, { icon: customIcon })
    .addTo(map)
    .bindPopup('<strong>🥓 Salsamentaría &amp; Desechables Sofi</strong><br/>Sector Comercial, Tocaima, Cundinamarca<br/><em>¡Carnes frías, empaques y desechables!</em>')
    .openPopup();
}

function centerMapTocaima() {
  if (map) {
    map.flyTo(TOCAIMA_COORDS, 17, { duration: 1.2 });
    if (marker) marker.openPopup();
  }
}

/* ==========================================================
   GRÁFICA DEL MARCO TEÓRICO SENA (CHART.JS)
========================================================== */
function initSenaChart() {
  const ctx = document.getElementById('senaChart');
  if (!ctx || typeof Chart === 'undefined') return;

  new Chart(ctx, {
    type: 'doughnut',
    data: {
      labels: ['Con Página Web (10%)', 'Sin Presencia Web (90%)'],
      datasets: [{
        data: [10, 90],
        backgroundColor: ['#C88A2E', '#E5DFC5'],
        borderColor: ['#FFFFFF', '#FFFFFF'],
        borderWidth: 2
      }]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      plugins: {
        legend: {
          position: 'bottom',
          labels: {
            font: { family: "'Plus Jakarta Sans', sans-serif", weight: 'bold', size: 12 },
            color: '#1A1615'
          }
        },
        title: {
          display: true,
          text: 'Presencia Digital en Salsamentarías de Tocaima',
          font: { family: "'Playfair Display', serif", size: 14, weight: 'bold' },
          color: '#8B181B'
        }
      }
    }
  });
}

/* ==========================================================
   INICIALIZACIÓN AL CARGAR LA PÁGINA
========================================================== */
document.addEventListener('DOMContentLoaded', function() {
  renderProducts('todos');
  updateCartUI();
  checkBusinessHours();
  initMap();
  initSenaChart();
  calculateCustomTable();
});
</script>
</body>
</html>
