<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="icon" type="image/png" href="uploads/ikonka1.png">
    <title>RahatVPN</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #0F447E;
            --primary-dark: #0A3362;
            --primary-light: #1A5A9A;
            --secondary-color: #FF6B35;
            --text-color: #333;
            --light-text: #666;
            --lighter-text: #888;
            --background-color: #fff;
            --section-bg: #f8fafc;
            --border-color: #e2e8f0;
            --shadow: 0 4px 12px rgba(15, 68, 126, 0.08);
            --shadow-hover: 0 8px 24px rgba(15, 68, 126, 0.15);
            --transition: all 0.3s ease;
            --border-radius: 12px;
            --container-padding: 0 5%;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background-color: var(--background-color);
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Загрузочный экран */
        .loader-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: var(--primary-color);
            z-index: 9999;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            transition: opacity 0.5s ease;
        }

        .loader {
            width: 80px;
            height: 80px;
            position: relative;
            margin-bottom: 10px;
        }

        .loader-shield {
            width: 100%;
            height: 100%;
            background-color: white;
            clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
            display: flex;
            justify-content: center;
            align-items: center;
            animation: pulse 1.5s infinite;
        }

        .loader-shield i {
            font-size: 36px;
            color: var(--primary-color);
        }

        .loader-text {
            color: white;
            font-size: 24px;
            font-weight: 600;
            text-align: center;
        }

        .loader-subtext {
            color: rgba(255, 255, 255, 0.8);
            font-size: 16px;
        }

        /* Частицы */
        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            z-index: -1;
        }

        /* Header и навигация */
        header {
            padding: 20px 0;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            background-color: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            background-color: var(--primary-color);
            border-radius: 8px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .logo-icon i {
            color: white;
            font-size: 20px;
        }

        .logo-text {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary-color);
        }

        /* Десктопное меню */
        nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        nav a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 500;
            transition: var(--transition);
            position: relative;
        }

        nav a:hover {
            color: var(--primary-color);
        }

        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background-color: var(--primary-color);
            transition: var(--transition);
        }

        nav a:hover::after {
            width: 100%;
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 24px;
            color: var(--primary-color);
            cursor: pointer;
            z-index: 1001;
        }

        /* Затемнение фона при открытом меню */
        .menu-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 998;
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
        }

        .menu-overlay.active {
            opacity: 1;
            visibility: visible;
        }

        /* Герой-секция */
        .hero {
            padding: 160px 0 100px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .hero h1 {
            font-size: 48px;
            font-weight: 700;
            line-height: 1.2;
            margin-bottom: 20px;
            color: var(--primary-color);
        }

        .hero p {
            font-size: 20px;
            color: var(--light-text);
            margin-bottom: 20px;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }

        .cta-button {
            display: inline-block;
            padding: 10px 40px;
            background-color: var(--primary-color);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            font-size: 18px;
            transition: var(--transition);
            border: 2px solid var(--primary-color);
            box-shadow: var(--shadow);
        }

        .cta-button:hover {
            background-color: var(--primary-dark);
            transform: translateY(-3px);
            box-shadow: var(--shadow-hover);
        }

        .hero-image {
            margin-top: 60px;
            position: relative;
        }

        .vpn-animation {
            width: 100%;
            max-width: 800px;
            margin: 0 auto;
            height: 300px;
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .server {
            width: 120px;
            height: 120px;
            background-color: var(--primary-color);
            border-radius: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            box-shadow: var(--shadow);
        }

        .server i {
            color: white;
            font-size: 50px;
        }

        .device {
            width: 80px;
            height: 80px;
            background-color: var(--section-bg);
            border-radius: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            position: absolute;
            box-shadow: var(--shadow);
        }

        .device i {
            color: var(--primary-color);
            font-size: 30px;
        }

        .device-1 {
            left: 10%;
            top: 20%;
            animation: float 4s ease-in-out infinite;
        }

        .device-2 {
            right: 10%;
            top: 10%;
            animation: float 4s ease-in-out infinite 0.5s;
        }

        .device-3 {
            left: 15%;
            bottom: 10%;
            animation: float 4s ease-in-out infinite 1s;
        }

        .device-4 {
            right: 17%;
            bottom: 20%;
            animation: float 4s ease-in-out infinite 1.5s;
        }

        .connection-line {
            position: absolute;
            background-color: var(--primary-color);
            opacity: 0.3;
        }

        /* Секция загрузки */
        .download-section {
            padding: 10px 0;
            background-color: var(--section-bg);
        }

        .section-title {
            text-align: center;
            font-size: 36px;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 20px;
        }

        .os-detection {
            border: 2px solid var(--primary-color);
            background-color: white;
            padding: 25px 10px;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            max-width: 600px;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            gap: 10px;
            animation: fadeInUp 0.8s ease-out;
        }

        .os-icon {
            width: 70px;
            height: 70px;
            background-color: var(--section-bg);
            border-radius: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-shrink: 0;
        }

        .os-icon i {
            font-size: 36px;
            color: var(--primary-color);
        }

        .os-info h3 {
            font-size: 20px;
            margin-bottom: 5px;
            color: var(--text-color);
        }

        .os-info p {
            color: var(--light-text);
        }

        .download-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 25px;
        }

        .download-card {
            background-color: white;
            padding: 25px 10px;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            text-align: center;
            transition: var(--transition);
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .download-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
        }

        .download-icon {
            width: 80px;
            height: 80px;
            background-color: var(--section-bg);
            border-radius: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 10px;
        }

        .download-icon i {
            font-size: 40px;
            color: var(--primary-color);
        }

        .download-card h3 {
            font-size: 22px;
            margin-bottom: 5px;
            color: var(--text-color);
        }

        .download-card p {
            color: var(--light-text);
            margin-bottom: 10px;
        }

        .download-btn {
            display: inline-block;
            padding: 12px 60px;
            background-color: var(--primary-color);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: var(--transition);
            margin-top: auto;
        }

        .download-btn:hover {
            background-color: var(--primary-dark);
        }

        .instructions-link {
            text-align: center;
            margin: 20px 10px;
        }

        .instructions-link a {
            color: var(--primary-color);
            text-decoration: none;
            font-weight: 600;
            font-size: 18px;
            border-bottom: 2px dotted var(--primary-color);
            padding-bottom: 3px;
            transition: var(--transition);
        }

        .instructions-link a:hover {
            color: var(--primary-dark);
            border-bottom: 2px solid var(--primary-dark);
        }

        /* Секция цен */
        .pricing-section {
            padding: 10px 0;
        }

        .pricing-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 15px;
        }

        .pricing-card {
            border: 2px solid var(--primary-color);
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            padding: 40px 30px;
            text-align: center;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .pricing-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
        }

        .pricing-card.popular {
            border: 2px solid var(--primary-color);
            transform: scale(1.05);
        }

        .pricing-card.popular:hover {
            transform: scale(1.05) translateY(-10px);
        }

        .popular-badge {
            position: absolute;
            top: 0;
            right: 0;
            background-color: #0f447e;
            color: white;
            padding: 8px 20px;
            font-size: 14px;
            font-weight: 600;
            border-bottom-left-radius: 15px;
        }

        .pricing-title {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 10px;
            color: var(--text-color);
        }

        .pricing-price {
            margin-bottom: 10px;
        }

        .original-price {
            text-decoration: line-through;
            color: var(--lighter-text);
            font-size: 18px;
        }

        .current-price {
            font-size: 42px;
            font-weight: 700;
            color: var(--primary-color);
            line-height: 1;
            margin: 10px 0;
        }

        .month-price {
            color: var(--light-text);
            font-size: 16px;
        }

        .discount {
            display: inline-block;
            background-color: rgba(255, 107, 53, 0.1);
            color: var(--secondary-color);
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: 600;
            margin-bottom: 10px;
        }

        .pricing-features {
            list-style: none;
            margin-bottom: 10px;
            text-align: left;
        }

        .pricing-features li {
            padding: 10px 0;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            align-items: center;
        }

        .pricing-features li i {
            color: var(--primary-color);
            margin-right: 10px;
        }

        .pricing-features li:last-child {
            border-bottom: none;
        }

        .pricing-button {
            display: inline-block;
            padding: 15px 40px;
            background-color: var(--primary-color);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            font-size: 18px;
            transition: var(--transition);
            width: 100%;
            border: 2px solid var(--primary-color);
        }

        .pricing-button:hover {
            background-color: white;
            color: var(--primary-color);
        }

        /* FAQ секция */
        .faq-section {
            padding: 10px 0;
            background-color: var(--section-bg);
        }

        .faq-container {
            max-width: 800px;
            margin: 0 auto;
        }

        .faq-item {
            background-color: white;
            border-radius: var(--border-radius);
            margin-bottom: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }

        .faq-question {
            padding: 25px 30px;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: 600;
            font-size: 18px;
            transition: var(--transition);
        }

        .faq-question:hover {
            background-color: rgba(15, 68, 126, 0.05);
        }

        .faq-question.active {
            color: var(--primary-color);
            background-color: rgb(255 255 255 / 5%);
        }

        .faq-icon {
            color: var(--primary-color);
            transition: transform 0.3s ease;
        }

        .faq-question.active .faq-icon {
            transform: rotate(45deg);
        }

        .faq-answer {
            padding: 0 30px;
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease, padding 0.3s ease;
        }

        .faq-answer.open {
            padding: 0 30px 30px;
            max-height: 500px;
        }

        /* Footer */
        footer {
            background-color: var(--primary-dark);
            color: white;
            padding: 20px 0 20px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 10px;
        }

        .footer-logo {
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 20px;
        }

        .footer-logo span {
            color: var(--secondary-color);
        }

        .footer-about p {
            opacity: 0.8;
            margin-bottom: 15px;
        }

        .social-links {
            display: flex;
            gap: 15px;
        }

        .social-link {
            width: 40px;
            height: 40px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            text-decoration: none;
            transition: var(--transition);
        }

        .social-link:hover {
            background-color: var(--secondary-color);
            transform: translateY(-3px);
        }

        .footer-links h3 {
            font-size: 20px;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
        }

        .footer-links h3::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background-color: var(--secondary-color);
        }

        .footer-links ul {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 12px;
        }

        .footer-links a {
            color: rgba(255, 255, 255, 0.8);
            text-decoration: none;
            transition: var(--transition);
        }

        .footer-links a:hover {
            color: white;
            padding-left: 5px;
        }

        .copyright {
            text-align: center;
            padding-top: 15px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            opacity: 0.7;
            font-size: 14px;
        }

        /* Анимации */
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
            100% { transform: translateY(0px); }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Адаптивность */
        @media (max-width: 992px) {
            .hero h1 {
                font-size: 40px;
            }
            
            .pricing-grid {
                grid-template-columns: 1fr;
                max-width: 500px;
                margin: 0 auto;
            }
            
            .pricing-card.popular {
                transform: none;
            }
            
            .pricing-card.popular:hover {
                transform: translateY(-10px);
            }
        }

        @media (max-width: 768px) {
            .header-container {
                padding: 0 20px;
            }
            
            /* Мобильное меню */
            nav {
                position: fixed;
                top: -75px;
                right: -470px; /* Меню скрыто за пределами экрана */
                width: 280px;
                height: 10000%;
                background-color: white;
                box-shadow: -5px 0 20px rgba(0, 0, 0, 0.1);
                padding: 100px 30px 30px;
                transition: all 0.4s ease;
                z-index: 999;
                overflow-y: auto;
            }
            
            nav.active {
                right: 0; /* Меню появляется справа */
            }
            
            nav ul {
                flex-direction: column;
                gap: 0;
            }
            
            nav a {
                text-align: center;
                display: block;
                padding: 18px 0;
                font-size: 18px;
                border-bottom: 1px solid var(--border-color);
                color: var(--text-color);
            }
            
            nav a::after {
                display: none;
            }
            
            nav a:hover {
                color: var(--primary-color);
                background-color: rgba(15, 68, 126, 0.05);
                padding-left: 15px;
            }
            
            nav a i {
                width: 25px;
                margin-right: 10px;
                text-align: center;
                color: var(--primary-color);
            }
            
            .mobile-menu-btn {
                display: block;
            }
            
            .hero {
                padding: 100px 0 80px;
            }
            
            .hero h1 {
                font-size: 32px;
            }
            
            .hero p {
                font-size: 18px;
            }
            
            .section-title {
                font-size: 30px;
            }
            
            .device-1, .device-2, .device-3, .device-4 {
                width: 60px;
                height: 60px;
            }
            
            .device i {
                font-size: 24px;
            }
            
            .server {
                width: 100px;
                height: 100px;
            }
            
            .server i {
                font-size: 40px;
            }
            
            .download-grid {
                grid-template-columns: 1fr;
            }
            
            .os-detection {
                flex-direction: column;
                text-align: center;
            }
        }

        @media (max-width: 480px) {
            .hero h1 {
                font-size: 28px;
            }
            
            .current-price {
                font-size: 36px;
            }
            
            .pricing-card {
                padding: 25px 30px;
            }
            
            .faq-question {
                padding: 20px;
                font-size: 16px;
            }
            
            nav {
                width: 95%;
            }
        }
    </style>
</head>
<body>
    <!-- Загрузочный экран -->
    <div class="loader-overlay" id="loader">
        <div class="loader">
            <div class="loader-shield">
                <i class="fas fa-shield-alt"></i>
            </div>
        </div>
        <div class="loader-text">RahatVPN</div>
        <div class="loader-subtext">Подключаем безопасную сеть...</div>
    </div>

    <!-- Частицы -->
    <div id="particles-js"></div>

    <!-- Header -->
    <header>
        <div class="container header-container">
            <div class="logo">
                <div class="logo-icon">
                    <i class="fas fa-shield-alt"></i>
                </div>
                <div class="logo-text">Rahat<span>VPN</span></div>
            </div>
            
            <button class="mobile-menu-btn" id="mobileMenuBtn">
                <i class="fas fa-bars"></i>
            </button>
            
            <nav id="mainNav">
                <ul>
                    <li><a href="#home"><i class="fas fa-home"></i> Главная</a></li>
                    <li><a href="#download"><i class="fas fa-download"></i> Скачать</a></li>
                    <li><a href="#pricing"><i class="fas fa-tags"></i> Тарифы</a></li>
                    <li><a href="#faq"><i class="fas fa-question-circle"></i> FAQ</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Оверлей для закрытия меню -->
    <div class="menu-overlay" id="menuOverlay"></div>

    <!-- Главный экран -->
    <section class="hero" id="home">
        <div class="container">
            <div class="hero-content">
                <h1>Безопасный и быстрый VPN-сервис</h1>
                <p>RahatVPN обеспечивает полную защиту ваших данных, анонимность в сети. Ваша конфиденциальность - наш приоритет.</p>
                <a href="#download" class="cta-button">Начать использовать</a>
                
                <div class="hero-image">
                    <div class="vpn-animation">
                        <div class="server">
                            <i class="fas fa-server"></i>
                        </div>
                        <div class="device device-1">
                            <i class="fab fa-android"></i>
                        </div>
                        <div class="device device-2">
                            <i class="fab fa-apple"></i>
                        </div>
                        <div class="device device-3">
                            <i class="fab fa-windows"></i>
                        </div>
                        <div class="device device-4">
                            <i class="fas fa-desktop"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Секция загрузки -->
    <section class="download-section" id="download">
        <div class="container">
            <h2 class="section-title">Скачать RahatVPN</h2>
            
            <div class="os-detection" id="osDetection">
                <div class="os-icon">
                    <i class="fas fa-question-circle"></i>
                </div>
                <div class="os-info">
                    <h3>Определяем вашу операционную систему...</h3>
                    <p>Пожалуйста, подождите</p>
                </div>
            </div>
            
            <div class="download-grid">
                <div class="download-card">
                    <div class="download-icon">
                        <i class="fab fa-android"></i>
                    </div>
                    <h3>Android</h3>
                    <p>Для смартфонов на базе Android</p>
                    <a href="https://play.google.com/store/apps/details?id=org.outline.android.client" class="download-btn" target="_blank">Скачать</a>
                </div>
                
                <div class="download-card">
                    <div class="download-icon">
                        <i class="fab fa-apple"></i>
                    </div>
                    <h3>iOS</h3>
                    <p>Для iPhone и iPad</p>
                    <a href="https://apps.apple.com/us/app/outline-app/id1356177741" class="download-btn" target="_blank">Скачать</a>
                </div>
                
                <div class="download-card">
                    <div class="download-icon">
                        <i class="fab fa-windows"></i>
                    </div>
                    <h3>Windows</h3>
                    <p>Для Windows 7/8/10/11</p>
                    <a href="https://drive.usercontent.google.com/download?id=15kg3quZq_4DiQ6IrBBzBrWxBtzs9RqLL&export=download&authuser=0&confirm=t&uuid=7184a95d-a0a7-4b40-b818-bd4f8884d40e&at=APcXIO3QoVElwVaWAl_U7Nz_xPLP:1770192171286" class="download-btn" target="_blank">Скачать</a>
                </div>
                
                <div class="download-card">
                    <div class="download-icon">
                        <i class="fab fa-apple"></i>
                    </div>
                    <h3>macOS</h3>
                    <p>Для Apple Mac</p>
                    <a href="https://itunes.apple.com/us/app/outline-app/id1356178125" class="download-btn" target="_blank">Скачать</a>
                </div>
                
                <div class="download-card">
                    <div class="download-icon">
                        <i class="fab fa-chrome"></i>
                    </div>
                    <h3>Chrome</h3>
                    <p>Для браузера Chrome</p>
                    <a href="https://chromewebstore.google.com/detail/outline-vpn/ocebpninopeofhphnnkdaaloiejfeool" class="download-btn" target="_blank">Установить</a>
                </div>
                
                <div class="download-card">
                    <div class="download-icon">
                        <i class="fab fa-linux"></i>
                    </div>
                    <h3>Linux</h3>
                    <p>Для дистрибутивов Linux</p>
                    <a href="https://s3.amazonaws.com/outline-releases/client/linux/stable/Outline-Client.AppImage" class="download-btn" target="_blank">Скачать</a>
                </div>
            </div>
            
            <div class="instructions-link">
                <a href="https://telegra.ph/Polnoe-rukovodstvo-po-ustanovke-i-podklyucheniyu-Outline-VPN-02-02" target="_blank">Полная инструкция по установке и подключению для всех ОС</a>
            </div>
        </div>
    </section>

    <!-- Секция цен -->
    <section class="pricing-section" id="pricing">
        <div class="container">
            <h2 class="section-title">Наши тарифы</h2>
            <p style="text-align: center; color: var(--light-text); max-width: 800px; margin: 0 auto 20px; font-size: 18px;">Все наши тарифы включают полный доступ ко всем функциям, неограниченную скорость и трафик</p>
            
            <div class="pricing-grid">
                <div class="pricing-card">
                    <div class="pricing-title">1 месяц</div>
                    <div class="discount">Скидка - 10%</div>
                    <div class="pricing-price">
                        <div class="original-price">119₽</div>
                        <div class="current-price">99 ₽</div>
                        <div class="month-price">в месяц</div>
                    </div>
                    <ul class="pricing-features">
                        <li><i class="fas fa-check"></i> Полный доступ ко всем функциям</li>
                        <li><i class="fas fa-check"></i> Скорость без ограничений</li>
                        <li><i class="fas fa-check"></i> Поддержка 24/7</li>
                        <li><i class="fas fa-check"></i> Цена за месяц</li>
                    </ul>
                    <a href="https://t.me/PAXATVPNModer" class="pricing-button">Купить сейчас</a>
                </div>
                
                <div class="pricing-card popular">
                    <div class="popular-badge">ХИТ ПРОДАЖ</div>
                    <div class="pricing-title">3 месяца</div>
                    <div class="discount">Скидка - 20%</div>
                    <div class="pricing-price">
                        <div class="original-price">297₽</div>
                        <div class="current-price">239 ₽</div>
                        <div class="month-price">79 ₽ в месяц</div>
                    </div>
                    <ul class="pricing-features">
                        <li><i class="fas fa-check"></i> Полный доступ ко всем функциям</li>
                        <li><i class="fas fa-check"></i> Скорость без ограничений</li>
                        <li><i class="fas fa-check"></i> Поддержка 24/7</li>
                        <li><i class="fas fa-check"></i> Экономия 58₽</li>
                    </ul>
                    <a href="https://t.me/PAXATVPNModer" class="pricing-button">Купить сейчас</a>
                </div>
                
                <div class="pricing-card">
                    <div class="pricing-title">1 год</div>
                    <div class="discount">Скидка - 30%</div>
                    <div class="pricing-price">
                        <div class="original-price">1188₽</div>
                        <div class="current-price">990 ₽</div>
                        <div class="month-price">82 ₽ в месяц</div>
                    </div>
                    <ul class="pricing-features">
                        <li><i class="fas fa-check"></i> Полный доступ ко всем функциям</li>
                        <li><i class="fas fa-check"></i> Скорость без ограничений</li>
                        <li><i class="fas fa-check"></i> Поддержка 24/7</li>
                        <li><i class="fas fa-check"></i> Экономия 198₽</li>
                    </ul>
                    <a href="https://t.me/PAXATVPNModer" class="pricing-button">Купить сейчас</a>
                </div>
            </div>
        </div>
    </section>

    <!-- FAQ секция -->
    <section class="faq-section" id="faq">
        <div class="container">
            <h2 class="section-title">Часто задаваемые вопросы</h2>
            
            <div class="faq-container">
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Что такое VPN и зачем он нужен?</span>
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        <p>VPN (Virtual Private Network) - это технология, которая создает защищенное соединение между вашим устройством и интернетом. VPN скрывает ваш реальный IP-адрес, шифрует все передаваемые данные и позволяет обходить географические ограничения, обеспечивая полную конфиденциальность и безопасность в сети.</p>
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Насколько безопасен RahatVPN?</span>
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        <p>RahatVPN использует современные протоколы шифрования AES-256, что соответствует уровню защиты, используемому банками и правительственными учреждениями. Мы не ведем журналы вашей активности, поэтому ваши данные остаются полностью конфиденциальными.</p>
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Сколько устройств можно подключить?</span>
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        <p>На всех наших тарифах вы можете подключить строго 1 устройсто. Это означает, что вы можете использовать RahatVPN на своем телефоне, планшете, ноутбуке и других устройствах но в разное время.</p>
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Есть ли ограничение по скорости?</span>
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        <p>Нет, все наши тарифы предоставляют неограниченную скорость и трафик. Вы можете смотреть видео в высоком качестве, играть в онлайн-игры и скачивать файлы без каких-либо ограничений.</p>
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Какой способ оплаты вы принимаете?</span>
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        <p>Мы принимаем банковские карты, электронные деньги, а также криптовалюту. Все платежи защищены и обрабатываются через безопасные платежные системы.</p>
                    </div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Можно ли вернуть деньги?</span>
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        <p>Да, мы предлагаем 7-дневную гарантию возврата денег. Если вы не удовлетворены работой нашего сервиса, вы можете запросить полный возврат средств в течение 7 дней с момента покупки.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-about">
                    <div class="footer-logo">Rahat<span>VPN</span></div>
                    <p>Мы обеспечиваем безопасный и анонимный доступ в интернет для пользователей по всему миру. Ваша конфиденциальность - наш главный приоритет.</p>
                    <div class="social-links">
                        <a href="https://t.me/PAXAT_VPN" class="social-link"><i class="fas fa-bullhorn"></i></a>
                        <a href="https://t.me/PAXATVPNModer" class="social-link"><i class="fab fa-telegram"></i></a>
                        <a href="https://t.me/PAXATVPNModer" class="social-link"><i class="far fa-comments"></i></a>
                    </div>
                </div>
                
                <div class="footer-links">
                    <h3>Ссылки</h3>
                    <ul>
                        <li><a href="#home">Главная</a></li>
                        <li><a href="#download">Скачать</a></li>
                        <li><a href="#pricing">Тарифы</a></li>
                        <li><a href="#faq">FAQ</a></li>
                    </ul>
                </div>
                
                <div class="footer-links">
                    <h3>Поддержка</h3>
                    <ul>
                        <li><a href="https://telegra.ph/Polnoe-rukovodstvo-po-ustanovke-i-podklyucheniyu-Outline-VPN-02-02" target="_blank">Инструкция по установке</a></li>
                        <li><a href="https://t.me/PAXATVPNModer">Центр поддержки</a></li>
                        <li><a href="https://telegra.ph/Kontakty-dlya-svyazi-02-04">Контакты</a></li>
                        <li><a href="https://telegra.ph/Politika-konfidencialnosti-RahatVPN-02-04">Политика конфиденциальности</a></li>
                    </ul>
                </div>
            </div>
            
            <div class="copyright">
                &copy; 2026 RahatVPN. Все права защищены.
            </div>
        </div>
    </footer>

    <!-- Скрипты -->
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
    <script>
        // Загрузочный экран
        window.addEventListener('load', function() {
            setTimeout(function() {
                document.getElementById('loader').style.opacity = '0';
                setTimeout(function() {
                    document.getElementById('loader').style.display = 'none';
                }, 500);
            }, 1500);
        });

        // Частицы
        particlesJS('particles-js', {
            particles: {
                number: { value: 80, density: { enable: true, value_area: 800 } },
                color: { value: "#0F447E" },
                shape: { type: "circle" },
                opacity: { value: 0.3, random: true },
                size: { value: 3, random: true },
                line_linked: {
                    enable: true,
                    distance: 150,
                    color: "#0F447E",
                    opacity: 0.2,
                    width: 1
                },
                move: {
                    enable: true,
                    speed: 2,
                    direction: "none",
                    random: true,
                    straight: false,
                    out_mode: "out",
                    bounce: false
                }
            },
            interactivity: {
                detect_on: "canvas",
                events: {
                    onhover: { enable: true, mode: "repulse" },
                    onclick: { enable: true, mode: "push" },
                    resize: true
                }
            },
            retina_detect: true
        });

        // Мобильное меню
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');
        const mainNav = document.getElementById('mainNav');
        const menuOverlay = document.getElementById('menuOverlay');

        // Открытие/закрытие меню
        mobileMenuBtn.addEventListener('click', function(e) {
            e.stopPropagation();
            mainNav.classList.toggle('active');
            menuOverlay.classList.toggle('active');
            mobileMenuBtn.innerHTML = mainNav.classList.contains('active') 
                ? '<i class="fas fa-times"></i>' 
                : '<i class="fas fa-bars"></i>';
        });

        // Закрытие меню при клике на оверлей
        menuOverlay.addEventListener('click', function() {
            mainNav.classList.remove('active');
            menuOverlay.classList.remove('active');
            mobileMenuBtn.innerHTML = '<i class="fas fa-bars"></i>';
        });

        // Закрытие меню при клике на ссылку
        document.querySelectorAll('nav a').forEach(link => {
            link.addEventListener('click', function() {
                mainNav.classList.remove('active');
                menuOverlay.classList.remove('active');
                mobileMenuBtn.innerHTML = '<i class="fas fa-bars"></i>';
            });
        });

        // Закрытие меню при клике вне его
        document.addEventListener('click', function(e) {
            if (!mainNav.contains(e.target) && !mobileMenuBtn.contains(e.target) && mainNav.classList.contains('active')) {
                mainNav.classList.remove('active');
                menuOverlay.classList.remove('active');
                mobileMenuBtn.innerHTML = '<i class="fas fa-bars"></i>';
            }
        });

        // Определение ОС
        function detectOS() {
            const userAgent = navigator.userAgent || navigator.vendor || window.opera;
            const osDetection = document.getElementById('osDetection');
            const osIcon = osDetection.querySelector('.os-icon i');
            const osTitle = osDetection.querySelector('.os-info h3');
            const osText = osDetection.querySelector('.os-info p');
            
            let osName = 'Неизвестная ОС';
            let osIconClass = 'fas fa-question-circle';
            
            // Определяем операционную систему
            if (/android/i.test(userAgent)) {
                osName = 'Android';
                osIconClass = 'fab fa-android';
            } else if (/iPad|iPhone|iPod/.test(userAgent) && !window.MSStream) {
                osName = 'iOS';
                osIconClass = 'fab fa-apple';
            } else if (/windows/i.test(userAgent)) {
                osName = 'Windows';
                osIconClass = 'fab fa-windows';
            } else if (/mac/i.test(userAgent)) {
                osName = 'macOS';
                osIconClass = 'fab fa-apple';
            } else if (/linux/i.test(userAgent)) {
                osName = 'Linux';
                osIconClass = 'fab fa-linux';
            } else if (/cros/i.test(userAgent)) {
                osName = 'Chrome OS';
                osIconClass = 'fab fa-chrome';
            }
            
            // Обновляем информацию
            setTimeout(() => {
                osIcon.className = osIconClass;
                osTitle.textContent = `Определена ваша ОС: ${osName}`;
                osText.textContent = 'Рекомендуем скачать приложение для вашей системы из списка ниже';
                
                // Добавляем анимацию
                osDetection.style.animation = 'none';
                setTimeout(() => {
                    osDetection.style.animation = 'fadeInUp 0.8s ease-out';
                }, 10);
            }, 1000);
        }
        
        // Запускаем определение ОС после загрузки страницы
        setTimeout(detectOS, 1800);

        // FAQ аккордеон
        document.querySelectorAll('.faq-question').forEach(question => {
            question.addEventListener('click', () => {
                const answer = question.nextElementSibling;
                const isOpen = answer.classList.contains('open');
                
                // Закрываем все ответы
                document.querySelectorAll('.faq-answer').forEach(ans => {
                    ans.classList.remove('open');
                });
                
                // Убираем активный класс со всех вопросов
                document.querySelectorAll('.faq-question').forEach(q => {
                    q.classList.remove('active');
                });
                
                // Если ответ был закрыт, открываем его
                if (!isOpen) {
                    answer.classList.add('open');
                    question.classList.add('active');
                }
            });
        });

        // Плавная прокрутка для ссылок
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Анимация при скролле
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Наблюдаем за элементами, которые нужно анимировать
        document.querySelectorAll('.download-card, .pricing-card, .faq-item').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>
