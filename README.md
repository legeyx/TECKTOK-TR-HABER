<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TechTokTR - Teknoloji Haberleri</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #e74c3c;
            --primary-dark: #c0392b;
            --dark: #1a1a1a;
            --darker: #121212;
            --light: #f5f5f5;
            --gray: #777;
            --dark-gray: #333;
            --card-bg: #242424;
            --text: #e0e0e0;
            --border: #444;
            --success: #2ecc71;
            --warning: #f39c12;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--dark);
            color: var(--text);
            line-height: 1.6;
            transition: background 0.3s;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }
        
        /* Header Styles */
        header {
            background: var(--darker);
            box-shadow: 0 2px 10px rgba(0,0,0,0.3);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 1rem;
            gap: 1rem;
        }
        
        .logo {
            font-size: 2rem;
            font-weight: 800;
            color: var(--light);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .logo-icon {
            color: var(--primary);
        }
        
        .logo span {
            color: var(--primary);
        }
        
        .search-container {
            display: flex;
            flex: 1;
            max-width: 500px;
            margin: 0 1rem;
        }
        
        .search-input {
            flex: 1;
            padding: 0.5rem 1rem;
            border: 1px solid var(--border);
            border-radius: 4px 0 0 4px;
            background: var(--dark-gray);
            color: var(--text);
            outline: none;
            transition: border 0.3s;
        }
        
        .search-input:focus {
            border-color: var(--primary);
        }
        
        .search-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 0 1.2rem;
            border-radius: 0 4px 4px 0;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .search-btn:hover {
            background: var(--primary-dark);
        }
        
        .theme-toggle {
            background: none;
            border: none;
            color: var(--text);
            font-size: 1.2rem;
            cursor: pointer;
            transition: transform 0.3s;
        }
        
        .theme-toggle:hover {
            transform: rotate(30deg);
        }
        
        /* Navigation */
        nav {
            background: var(--darker);
            border-bottom: 1px solid var(--border);
        }
        
        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            overflow-x: auto;
            padding: 0 1rem;
            scrollbar-width: none;
        }
        
        .nav-container::-webkit-scrollbar {
            display: none;
        }
        
        .nav-link {
            color: var(--text);
            text-decoration: none;
            padding: 0.8rem 1rem;
            white-space: nowrap;
            transition: color 0.3s;
            position: relative;
        }
        
        .nav-link:hover, .nav-link.active {
            color: var(--primary);
        }
        
        .nav-link.active::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: var(--primary);
        }
        
        /* Main Content */
        main {
            flex: 1;
            padding: 2rem 0;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1rem;
        }
        
        .news-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 1.5rem;
        }
        
        /* News Card Styles */
        .news-card {
            background: var(--card-bg);
            border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
            position: relative;
            cursor: pointer;
            display: flex;
            flex-direction: column;
        }
        
        .news-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.3);
        }
        
        .news-image-container {
            position: relative;
            width: 100%;
            height: 200px;
            overflow: hidden;
        }
        
        .news-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }
        
        .news-card:hover .news-image {
            transform: scale(1.05);
        }
        
        .news-category {
            position: absolute;
            top: 0.5rem;
            left: 0.5rem;
            background: var(--primary);
            color: white;
            padding: 0.2rem 0.5rem;
            border-radius: 4px;
            font-size: 0.8rem;
            font-weight: bold;
        }
        
        .news-content {
            padding: 1.5rem;
            flex: 1;
            display: flex;
            flex-direction: column;
        }
        
        .news-title {
            font-size: 1.3rem;
            margin: 0 0 0.5rem 0;
            color: var(--light);
            transition: color 0.3s;
        }
        
        .news-card:hover .news-title {
            color: var(--primary);
        }
        
        .news-date {
            color: var(--gray);
            font-size: 0.85rem;
            margin-bottom: 1rem;
            display: block;
        }
        
        .news-text {
            margin: 0 0 1rem 0;
            color: var(--text);
            flex: 1;
        }
        
        .news-actions {
            margin-top: auto;
            padding-top: 1rem;
            border-top: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .read-more {
            color: var(--primary);
            text-decoration: none;
            font-weight: 600;
            transition: color 0.3s;
        }
        
        .read-more:hover {
            color: var(--light);
        }
        
        .comments-btn {
            background: none;
            border: none;
            color: var(--gray);
            cursor: pointer;
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 0.3rem;
            transition: color 0.3s;
        }
        
        .comments-btn:hover {
            color: var(--primary);
        }
        
        /* Breaking News Banner */
        .breaking-news {
            background: var(--primary);
            color: white;
            padding: 0.8rem;
            text-align: center;
            font-weight: bold;
            margin-bottom: 1.5rem;
            grid-column: 1 / -1;
            border-radius: 8px;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.8; }
            100% { opacity: 1; }
        }
        
        /* Footer Styles */
        footer {
            background: var(--darker);
            color: var(--gray);
            text-align: center;
            padding: 2rem 1rem;
            margin-top: 2rem;
            border-top: 1px solid var(--border);
        }
        
        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            text-align: left;
        }
        
        .footer-logo {
            font-size: 1.5rem;
            font-weight: 800;
            color: var(--light);
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .footer-about {
            margin-bottom: 1rem;
            line-height: 1.7;
        }
        
        .footer-links h3, .footer-contact h3 {
            color: var(--light);
            margin-bottom: 1rem;
            font-size: 1.2rem;
        }
        
        .footer-links ul {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 0.5rem;
        }
        
        .footer-links a {
            color: var(--gray);
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-links a:hover {
            color: var(--primary);
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 0.5rem;
        }
        
        .copyright {
            grid-column: 1 / -1;
            padding-top: 1.5rem;
            border-top: 1px solid var(--border);
            margin-top: 1.5rem;
            font-size: 0.9rem;
        }
        
        /* News Modal Styles */
        .news-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.3s;
            padding: 1rem;
        }
        
        .news-modal.active {
            opacity: 1;
            pointer-events: all;
        }
        
        .modal-content {
            background: var(--darker);
            border-radius: 8px;
            width: 100%;
            max-width: 900px;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
            box-shadow: 0 5px 30px rgba(0,0,0,0.5);
            border: 1px solid var(--border);
        }
        
        .modal-close {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: var(--primary);
            color: white;
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 2;
            transition: background 0.3s;
        }
        
        .modal-close:hover {
            background: var(--primary-dark);
        }
        
        .modal-image-container {
            width: 100%;
            height: 400px;
            overflow: hidden;
            position: relative;
        }
        
        .modal-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .modal-text-content {
            padding: 2rem;
        }
        
        .modal-title {
            font-size: 2rem;
            margin: 0 0 1rem 0;
            color: var(--light);
            line-height: 1.3;
        }
        
        .modal-meta {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
            color: var(--gray);
        }
        
        .modal-date {
            display: flex;
            align-items: center;
            gap: 0.3rem;
        }
        
        .modal-category {
            background: var(--primary);
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: bold;
        }
        
        .modal-text {
            line-height: 1.8;
            font-size: 1.1rem;
            margin-bottom: 2rem;
        }
        
        .modal-text p {
            margin-bottom: 1.5rem;
        }
        
        /* Comments Section */
        .comments-section {
            margin-top: 2rem;
            padding-top: 2rem;
            border-top: 1px solid var(--border);
        }
        
        .comments-title {
            font-size: 1.5rem;
            margin-bottom: 1.5rem;
            color: var(--light);
        }
        
        .comment-list {
            margin-bottom: 2rem;
        }
        
        .comment {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.5rem;
            padding-bottom: 1.5rem;
            border-bottom: 1px solid var(--border);
        }
        
        .comment:last-child {
            border-bottom: none;
            margin-bottom: 0;
            padding-bottom: 0;
        }
        
        .comment-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--dark-gray);
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            color: var(--primary);
            flex-shrink: 0;
        }
        
        .comment-content {
            flex: 1;
        }
        
        .comment-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
        }
        
        .comment-author {
            font-weight: bold;
            color: var(--primary);
        }
        
        .comment-date {
            color: var(--gray);
            font-size: 0.8rem;
        }
        
        .comment-text {
            line-height: 1.6;
        }
        
        .comment-form {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 8px;
            margin-top: 2rem;
        }
        
        .comment-form-title {
            font-size: 1.2rem;
            margin-bottom: 1rem;
            color: var(--light);
        }
        
        .form-row {
            margin-bottom: 1rem;
        }
        
        .form-input {
            width: 100%;
            padding: 0.8rem;
            background: var(--dark-gray);
            border: 1px solid var(--border);
            border-radius: 4px;
            color: var(--text);
            font-size: 1rem;
            transition: border 0.3s;
        }
        
        .form-input:focus {
            border-color: var(--primary);
            outline: none;
        }
        
        .form-textarea {
            min-height: 120px;
            resize: vertical;
        }
        
        .form-submit {
            background: var(--primary);
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.3s;
        }
        
        .form-submit:hover {
            background: var(--primary-dark);
        }
        
        /* Admin Panel Styles */
        .admin-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: var(--primary);
            color: white;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 2px 15px rgba(0,0,0,0.3);
            z-index: 100;
            transition: transform 0.3s;
        }
        
        .admin-btn:hover {
            transform: scale(1.1);
        }
        
        .admin-panel {
            position: fixed;
            bottom: 90px;
            right: 20px;
            width: 400px;
            background: var(--darker);
            border-radius: 8px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.4);
            padding: 1.5rem;
            z-index: 101;
            display: none;
            border: 1px solid var(--border);
            max-height: 70vh;
            overflow-y: auto;
        }
        
        .admin-panel.show {
            display: block;
            animation: fadeIn 0.3s;
        }
        
        .admin-panel h3 {
            color: var(--primary);
            margin-bottom: 1rem;
            font-size: 1.3rem;
        }
        
        .admin-tabs {
            display: flex;
            border-bottom: 1px solid var(--border);
            margin-bottom: 1.5rem;
        }
        
        .admin-tab {
            padding: 0.5rem 1rem;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.3s;
        }
        
        .admin-tab.active {
            border-bottom-color: var(--primary);
            color: var(--primary);
            font-weight: 600;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1rem;
            margin-bottom: 1.5rem;
        }
        
        .stat-card {
            background: var(--card-bg);
            padding: 1rem;
            border-radius: 8px;
            text-align: center;
        }
        
        .stat-value {
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--primary);
            margin-bottom: 0.3rem;
        }
        
        .stat-label {
            font-size: 0.9rem;
            color: var(--gray);
        }
        
        .news-select {
            width: 100%;
            padding: 0.8rem;
            background: var(--dark-gray);
            border: 1px solid var(--border);
            border-radius: 4px;
            color: var(--text);
            margin-bottom: 1rem;
            font-size: 1rem;
        }
        
        .admin-form .form-row {
            margin-bottom: 1rem;
        }
        
        .admin-form label {
            display: block;
            margin-bottom: 0.5rem;
            color: var(--text);
        }
        
        .btn-group {
            display: flex;
            gap: 0.5rem;
            margin-top: 1rem;
        }
        
        .btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.3s;
            flex: 1;
        }
        
        .btn:hover {
            background: var(--primary-dark);
        }
        
        .btn-danger {
            background: var(--warning);
        }
        
        .btn-danger:hover {
            background: #e67e22;
        }
        
        .btn-secondary {
            background: var(--dark-gray);
        }
        
        .btn-secondary:hover {
            background: var(--gray);
        }
        
        .hidden {
            display: none;
        }
        
        /* Notification */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--success);
            color: white;
            padding: 1rem 1.5rem;
            border-radius: 8px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.2);
            z-index: 1000;
            transform: translateX(200%);
            transition: transform 0.3s;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.error {
            background: var(--warning);
        }
        
        /* Loading Spinner */
        .spinner {
            width: 40px;
            height: 40px;
            border: 4px solid rgba(255,255,255,0.3);
            border-radius: 50%;
            border-top-color: var(--primary);
            animation: spin 1s ease-in-out infinite;
            margin: 2rem auto;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        /* No Results */
        .no-results {
            grid-column: 1 / -1;
            text-align: center;
            padding: 3rem;
            color: var(--gray);
        }
        
        /* Responsive Styles */
        @media (max-width: 992px) {
            .header-container {
                flex-wrap: wrap;
            }
            
            .search-container {
                order: 3;
                width: 100%;
                margin: 1rem 0 0 0;
            }
            
            .news-container {
                grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            }
        }
        
        @media (max-width: 768px) {
            .modal-image-container {
                height: 250px;
            }
            
            .modal-title {
                font-size: 1.5rem;
            }
            
            .admin-panel {
                width: calc(100% - 40px);
                right: 20px;
                left: 20px;
            }
            
            .footer-container {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 576px) {
            .news-container {
                grid-template-columns: 1fr;
            }
            
            .modal-text-content {
                padding: 1.5rem;
            }
            
            .modal-meta {
                flex-direction: column;
                align-items: flex-start;
                gap: 0.5rem;
            }
            
            .comment {
                flex-direction: column;
            }
            
            .comment-avatar {
                margin-bottom: 0.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header Section -->
    <header>
        <div class="header-container">
            <a href="#" class="logo">
                <i class="fas fa-bolt logo-icon"></i>
                TechTok<span>TR HABER</span>
            </a>
            
            <div class="search-container">
                <input type="text" class="search-input" id="searchInput" placeholder="Haber ara...">
                <button class="search-btn" id="searchBtn">
                    <i class="fas fa-search"></i>
                </button>
            </div>
            
            <button class="theme-toggle" id="themeToggle">
                <i class="fas fa-moon"></i>
            </button>
        </div>
    </header>
    
    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <a href="#" class="nav-link active">Ana Sayfa</a>
            <a href="#" class="nav-link">Teknoloji</a>
            <a href="#" class="nav-link">Bilim</a>
            <a href="#" class="nav-link">Oyun</a>
            <a href="#" class="nav-link">Donanım</a>
            <a href="#" class="nav-link">Yazılım</a>
            <a href="#" class="nav-link">Mobil</a>
            <a href="#" class="nav-link">İncelemeler</a>
        </div>
    </nav>
    
    <!-- Main Content -->
    <main>
        <div class="container">
            <div class="news-container" id="newsContainer">
                <div class="breaking-news">
                    <i class="fas fa-bolt"></i> SON DAKİKA: Yeni yapay zeka modeli GPT-5 resmen duyuruldu!
                </div>
                
                <!-- Haberler buraya dinamik olarak eklenecek -->
            </div>
        </div>
    </main>
    
    <!-- Footer -->
    <footer>
        <div class="footer-container">
            <div class="footer-about">
                <div class="footer-logo">
                    <i class="fas fa-bolt"></i>
                    TechTok<span>TR</span>
                </div>
                <p class="footer-about">
                    TechTokTR, teknoloji dünyasındaki en güncel haberleri, incelemeleri ve analizleri sunar.
                    Amacımız okuyucularımıza kaliteli ve doğru bilgi ulaştırmaktır.
                </p>
            </div>
            
            <div class="footer-links">
                <h3>Hızlı Linkler</h3>
                <ul>
                    <li><a href="#">Ana Sayfa</a></li>
                    <li><a href="#">Teknoloji Haberleri</a></li>
                    <li><a href="#">Ürün İncelemeleri</a></li>
                    <li><a href="#">Yazılım Geliştirme</a></li>
                    <li><a href="#">Donanım Rehberi</a></li>
                </ul>
            </div>
            
            <div class="footer-contact">
                <h3>İletişim</h3>
                <div class="contact-item">
                    <i class="fas fa-envelope"></i>
                    <span>info@techtoktr.com</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <span>+90 555 123 45 67</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <span>İstanbul, Türkiye</span>
                </div>
            </div>
            
            <div class="copyright">
                © 2025 TechTokTR | Tüm Hakları Saklıdır
            </div>
        </div>
    </footer>
    
    <!-- News Modal -->
    <div class="news-modal" id="newsModal">
        <div class="modal-content">
            <button class="modal-close" id="modalClose">
                <i class="fas fa-times"></i>
            </button>
            
            <div class="modal-image-container">
                <img id="modalImage" class="modal-image" src="" alt="">
                <div class="news-category" id="modalCategory">Teknoloji</div>
            </div>
            
            <div class="modal-text-content">
                <h1 id="modalTitle" class="modal-title"></h1>
                
                <div class="modal-meta">
                    <span class="modal-date">
                        <i class="far fa-clock"></i>
                        <span id="modalDate"></span>
                    </span>
                </div>
                
                <div class="modal-text" id="modalText"></div>
                
                <!-- Comments Section -->
                <div class="comments-section">
                    <h3 class="comments-title">Yorumlar</h3>
                    
                    <div class="comment-list" id="modalCommentList">
                        <!-- Yorumlar buraya eklenecek -->
                    </div>
                    
                    <div class="comment-form">
                        <h4 class="comment-form-title">Yorum Yap</h4>
                        <div class="form-row">
                            <input type="text" id="modalCommentAuthor" class="form-input" placeholder="Adınız">
                        </div>
                        <div class="form-row">
                            <textarea id="modalCommentInput" class="form-input form-textarea" placeholder="Yorumunuz..."></textarea>
                        </div>
                        <button class="form-submit" id="modalCommentSubmit">Yorum Gönder</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Admin Button -->
    <div class="admin-btn" id="adminBtn">
        <i class="fas fa-cog"></i>
    </div>
    
    <!-- Admin Panel -->
    <div class="admin-panel" id="adminPanel">
        <div id="loginForm">
            <h3>Admin Girişi</h3>
            <div class="form-row">
                <input type="password" id="adminPassword" class="form-input" placeholder="Şifre">
            </div>
            <button onclick="login()" class="btn">Giriş Yap</button>
        </div>
        
        <div id="adminControls" class="hidden">
            <div class="admin-tabs">
                <div class="admin-tab active" data-tab="news">Haberler</div>
                <div class="admin-tab" data-tab="stats">İstatistikler</div>
            </div>
            
            <div class="tab-content active" id="newsTab">
                <div class="form-row">
                    <select class="news-select" id="newsSelect">
                        <option value="">Yeni haber ekle</option>
                    </select>
                </div>
                
                <div class="admin-form">
                    <div class="form-row">
                        <label for="newsTitle">Haber Başlığı</label>
                        <input type="text" id="newsTitle" class="form-input" placeholder="Başlık">
                    </div>
                    <div class="form-row">
                        <label for="newsContent">Haber İçeriği</label>
                        <textarea id="newsContent" class="form-input form-textarea" placeholder="İçerik"></textarea>
                    </div>
                    <div class="form-row">
                        <label for="newsImage">Resim URL (isteğe bağlı)</label>
                        <input type="text" id="newsImage" class="form-input" placeholder="https://...">
                    </div>
                    <div class="form-row">
                        <label for="newsCategory">Kategori</label>
                        <select id="newsCategory" class="form-input">
                            <option value="Teknoloji">Teknoloji</option>
                            <option value="Bilim">Bilim</option>
                            <option value="Oyun">Oyun</option>
                            <option value="Donanım">Donanım</option>
                            <option value="Yazılım">Yazılım</option>
                            <option value="Mobil">Mobil</option>
                        </select>
                    </div>
                    
                    <div class="btn-group">
                        <button onclick="addNews()" class="btn" id="addNewsBtn">Haber Ekle</button>
                        <button onclick="updateNews()" class="btn hidden" id="updateNewsBtn">Güncelle</button>
                        <button onclick="deleteNews()" class="btn btn-danger hidden" id="deleteNewsBtn">Sil</button>
                        <button onclick="cancelEdit()" class="btn btn-secondary hidden" id="cancelEditBtn">İptal</button>
                    </div>
                </div>
            </div>
            
            <div class="tab-content" id="statsTab">
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-value" id="totalNews">0</div>
                        <div class="stat-label">Toplam Haber</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" id="totalComments">0</div>
                        <div class="stat-label">Toplam Yorum</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" id="todayNews">0</div>
                        <div class="stat-label">Bugün Eklenen</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" id="popularCategory">-</div>
                        <div class="stat-label">Popüler Kategori</div>
                    </div>
                </div>
                
                <h4>Son Eklenen Haberler</h4>
                <div id="recentNewsList">
                    <!-- Son haberler buraya eklenecek -->
                </div>
            </div>
        </div>
    </div>
    
    <!-- Notification -->
    <div class="notification hidden" id="notification">
        <i class="fas fa-check-circle"></i>
        <span id="notificationText">İşlem başarıyla tamamlandı</span>
    </div>
    
    <script>
        // Şifre
        const PASSWORD = "yusuf6767yu";
        let isLoggedIn = false;
        let currentEditingId = null;
        let currentModalNewsId = null;
        
        // Temayı kontrol et
        const themeToggle = document.getElementById("themeToggle");
        const prefersDark = window.matchMedia("(prefers-color-scheme: dark)").matches;
        let isDarkMode = prefersDark;
        
        // Haberler dizisi (localStorage'dan al veya örnek haberler ekle)
        let newsList = JSON.parse(localStorage.getItem("techTokTRNews")) || [
            {
                id: Date.now(),
                title: "Yeni iPhone Modeli Tanıtıldı",
                content: "Apple'ın yeni iPhone modeli dün gece düzenlenen özel etkinlikte tanıtıldı. Yeni modelde kamera sisteminde büyük iyileştirmeler bulunuyor ve işlemci olarak yeni A17 çipini kullanıyor.\n\n120Hz yenileme hızına sahip ekranı ve geliştirilmiş pil ömrü ile dikkat çeken cihaz, önümüzdeki hafta satışa sunulacak.\n\nApple CEO'su Tim Cook yaptığı açıklamada, 'Bu, şimdiye kadar ürettiğimiz en gelişmiş iPhone' dedi. Yeni modelin fiyatı 999 dolardan başlıyor ve 1TB depolama seçeneği ile 1599 dolara kadar çıkıyor.",
                image: "https://source.unsplash.com/random/800x400/?iphone",
                category: "Teknoloji",
                date: new Date().toLocaleString("tr-TR", {
                    day: 'numeric',
                    month: 'long',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit'
                }),
                comments: [
                    { 
                        author: "Ahmet Yılmaz", 
                        text: "Fiyatı çok yüksek olmuş, almayı düşünmüyorum.",
                        date: new Date(Date.now() - 3600000).toLocaleString("tr-TR")
                    },
                    { 
                        author: "Mehmet Kaya", 
                        text: "Kamera kalitesi gerçekten etkileyici!",
                        date: new Date(Date.now() - 7200000).toLocaleString("tr-TR")
                    }
                ]
            },
            {
                id: Date.now() + 1,
                title: "Yapay Zeka Yazılım Geliştiricilerin Yerini Alabilir mi?",
                content: "Son dönemde hızla gelişen yapay zeka modelleri, basit kodlama işlemlerini insanlardan daha hızlı yapabiliyor. GitHub'ın Copilot aracı ve OpenAI'nin Codex modeli, geliştiricilerin işini kolaylaştırmak için kullanılıyor.\n\nAncak uzmanlar, yapay zekanın tamamen insan geliştiricilerin yerini alamayacağını, sadece onların işlerini kolaylaştıracağını belirtiyor. 'Yapay zeka araçları, geliştiricilerin daha verimli çalışmasını sağlayacak, ancak yaratıcılık ve karmaşık problem çözme yeteneği hala insanlara özgü olacak' diyor Stanford Üniversitesi'nden Prof. Dr. Ali Tekin.\n\nÖte yandan, bazı temel seviye programlama işlerinin otomatikleşeceği ve bu alanda çalışanların kendilerini geliştirmesi gerekeceği de vurgulanıyor.",
                image: "https://source.unsplash.com/random/800x400/?ai",
                category: "Yazılım",
                date: new Date(Date.now() - 86400000).toLocaleString("tr-TR", {
                    day: 'numeric',
                    month: 'long',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit'
                }),
                comments: []
            },
            {
                id: Date.now() + 2,
                title: "Yeni Nesil Oyun Konsolları Performans Karşılaştırması",
                content: "Yeni nesil oyun konsolları PlayStation 5 ve Xbox Series X arasındaki performans farkları merak ediliyor. Yapılan testlerde iki konsolun da farklı alanlarda üstünlük sağladığı görülüyor.\n\nPlayStation 5, özel olarak geliştirilen SSD'si sayesinde yükleme sürelerinde belirgin bir avantaj sağlarken, Xbox Series X daha yüksek çözünürlükte oyun sunabiliyor. Grafik kalitesi açısından iki konsol da birbirine yakın performans sergiliyor.\n\nUzmanlar, hangi konsolu seçeceğinizin oyun kütüphanenize ve kişisel tercihlerinize bağlı olduğunu belirtiyor. Her iki konsol da 4K çözünürlük ve 60 FPS üzeri performans vaat ediyor.",
                image: "https://source.unsplash.com/random/800x400/?gaming",
                category: "Oyun",
                date: new Date(Date.now() - 172800000).toLocaleString("tr-TR", {
                    day: 'numeric',
                    month: 'long',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit'
                }),
                comments: [
                    { 
                        author: "Oyun Sever", 
                        text: "PS5'in özel oyunları daha çekici geliyor.",
                        date: new Date(Date.now() - 86400000).toLocaleString("tr-TR")
                    }
                ]
            }
        ];
        
        // Sayfa yüklendiğinde
        document.addEventListener('DOMContentLoaded', function() {
            updateTheme();
            displayNews();
            updateNewsDropdown();
            updateStats();
            setupEventListeners();
        });
        
        // Event listener'ları kur
        function setupEventListeners() {
            // Admin paneli butonları
            const adminBtn = document.getElementById("adminBtn");
            const adminPanel = document.getElementById("adminPanel");
            
            adminBtn.addEventListener("click", function(e) {
                e.stopPropagation();
                adminPanel.classList.toggle("show");
            });
            
            // Tema değiştirme butonu
            themeToggle.addEventListener("click", function() {
                isDarkMode = !isDarkMode;
                updateTheme();
            });
            
            // Arama butonu
            document.getElementById("searchBtn").addEventListener("click", searchNews);
            document.getElementById("searchInput").addEventListener("keypress", function(e) {
                if (e.key === "Enter") searchNews();
            });
            
            // Modal kapatma
            document.getElementById("modalClose").addEventListener("click", closeModal);
            
            // Modal yorum gönderme
            document.getElementById("modalCommentSubmit").addEventListener("click", addModalComment);
            
            // Admin tab'ları
            document.querySelectorAll(".admin-tab").forEach(tab => {
                tab.addEventListener("click", function() {
                    // Tüm tab'ları ve içerikleri pasif yap
                    document.querySelectorAll(".admin-tab").forEach(t => t.classList.remove("active"));
                    document.querySelectorAll(".tab-content").forEach(c => c.classList.remove("active"));
                    
                    // Tıklanan tab'ı aktif yap
                    this.classList.add("active");
                    const tabId = this.getAttribute("data-tab") + "Tab";
                    document.getElementById(tabId).classList.add("active");
                    
                    // İstatistik tab'ına tıklandığında istatistikleri güncelle
                    if (this.getAttribute("data-tab") === "stats") {
                        updateStats();
                    }
                });
            });
            
            // Dışarı tıklayınca paneli kapat
            document.addEventListener("click", function(e) {
                if (!adminPanel.contains(e.target) && !adminBtn.contains(e.target)) {
                    adminPanel.classList.remove("show");
                }
            });
            
            // Modal dışına tıklayınca kapat
            document.getElementById("newsModal").addEventListener("click", function(e) {
                if (e.target === this) {
                    closeModal();
                }
            });
        }
        
        // Temayı güncelle
        function updateTheme() {
            if (isDarkMode) {
                document.documentElement.style.setProperty("--dark", "#1a1a1a");
                document.documentElement.style.setProperty("--darker", "#121212");
                document.documentElement.style.setProperty("--card-bg", "#242424");
                document.documentElement.style.setProperty("--text", "#e0e0e0");
                document.documentElement.style.setProperty("--border", "#444");
                themeToggle.innerHTML = '<i class="fas fa-sun"></i>';
            } else {
                document.documentElement.style.setProperty("--dark", "#f5f5f5");
                document.documentElement.style.setProperty("--darker", "#e0e0e0");
                document.documentElement.style.setProperty("--card-bg", "#ffffff");
                document.documentElement.style.setProperty("--text", "#333333");
                document.documentElement.style.setProperty("--border", "#ddd");
                themeToggle.innerHTML = '<i class="fas fa-moon"></i>';
            }
        }
        
        // İstatistikleri güncelle
        function updateStats() {
            // Toplam haber sayısı
            document.getElementById("totalNews").textContent = newsList.length;
            
            // Toplam yorum sayısı
            const totalComments = newsList.reduce((total, news) => {
                return total + (news.comments ? news.comments.length : 0);
            }, 0);
            document.getElementById("totalComments").textContent = totalComments;
            
            // Bugün eklenen haber sayısı
            const today = new Date().toLocaleDateString();
            const todayNews = newsList.filter(news => {
                return new Date(news.date).toLocaleDateString() === today;
            }).length;
            document.getElementById("todayNews").textContent = todayNews;
            
            // Popüler kategori
            const categoryCounts = {};
            newsList.forEach(news => {
                categoryCounts[news.category] = (categoryCounts[news.category] || 0) + 1;
            });
            
            let popularCategory = "-";
            let maxCount = 0;
            for (const category in categoryCounts) {
                if (categoryCounts[category] > maxCount) {
                    maxCount = categoryCounts[category];
                    popularCategory = category;
                }
            }
            document.getElementById("popularCategory").textContent = popularCategory;
            
            // Son eklenen haberler
            const recentNewsList = document.getElementById("recentNewsList");
            recentNewsList.innerHTML = "";
            
            const sortedNews = [...newsList].sort((a, b) => new Date(b.date) - new Date(a.date));
            const recentNews = sortedNews.slice(0, 3);
            
            recentNews.forEach(news => {
                const newsItem = document.createElement("div");
                newsItem.className = "comment";
                newsItem.innerHTML = `
                    <div class="comment-content">
                        <div class="comment-header">
                            <span class="comment-author">${news.title.substring(0, 30)}${news.title.length > 30 ? '...' : ''}</span>
                            <span class="comment-date">${news.date}</span>
                        </div>
                        <div class="comment-text">${news.category} • ${news.comments ? news.comments.length : 0} yorum</div>
                    </div>
                `;
                recentNewsList.appendChild(newsItem);
            });
        }
        
        // Haberleri ekranda göster
        function displayNews(newsToShow = newsList) {
            const newsContainer = document.getElementById("newsContainer");
            newsContainer.innerHTML = `
                <div class="breaking-news">
                    <i class="fas fa-bolt"></i> SON DAKİKA: ZUR SERVETİNİ AÇIKLADI!
                </div>
            `;
            
            if (newsToShow.length === 0) {
                newsContainer.innerHTML += '<div class="no-results">Sonuç bulunamadı</div>';
                return;
            }
            
            // Haberleri ters sırada göster (en yeni üstte)
            newsToShow.slice().reverse().forEach(news => {
                const newsCard = document.createElement("div");
                newsCard.className = "news-card";
                newsCard.dataset.id = news.id;
                newsCard.innerHTML = `
                    <div class="news-image-container">
                        ${news.image ? `<img src="${news.image}" alt="${news.title}" class="news-image">` : ''}
                        <div class="news-category">${news.category}</div>
                    </div>
                    <div class="news-content">
                        <h2 class="news-title">${news.title}</h2>
                        <span class="news-date">${news.date}</span>
                        <p class="news-text">${news.content.substring(0, 150)}${news.content.length > 150 ? '...' : ''}</p>
                        
                        <div class="news-actions">
                            <a class="read-more" onclick="openNewsModal(${news.id})">Devamını Oku</a>
                            <button class="comments-btn" onclick="event.stopPropagation(); openNewsModal(${news.id})">
                                <i class="fas fa-comment"></i> ${news.comments ? news.comments.length : 0}
                            </button>
                        </div>
                    </div>
                `;
                
                newsCard.addEventListener("click", function() {
                    openNewsModal(news.id);
                });
                
                newsContainer.appendChild(newsCard);
            });
        }
        
        // Haber modalını aç
        function openNewsModal(newsId) {
            const newsItem = newsList.find(item => item.id === newsId);
            if (!newsItem) return;
            
            currentModalNewsId = newsId;
            
            document.getElementById("modalImage").src = newsItem.image || "";
            document.getElementById("modalTitle").textContent = newsItem.title;
            document.getElementById("modalDate").textContent = newsItem.date;
            document.getElementById("modalCategory").textContent = newsItem.category;
            
            // İçeriği paragraflara böl
            const contentParagraphs = newsItem.content.split('\n').filter(p => p.trim() !== '');
            const modalText = document.getElementById("modalText");
            modalText.innerHTML = "";
            
            contentParagraphs.forEach(paragraph => {
                const p = document.createElement("p");
                p.textContent = paragraph;
                modalText.appendChild(p);
            });
            
            // Yorumları yükle
            const commentList = document.getElementById("modalCommentList");
            commentList.innerHTML = "";
            
            if (newsItem.comments && newsItem.comments.length > 0) {
                // Yorumları tarihe göre sırala (yeni önce)
                const sortedComments = [...newsItem.comments].sort((a, b) => new Date(b.date) - new Date(a.date));
                
                sortedComments.forEach(comment => {
                    const commentEl = document.createElement("div");
                    commentEl.className = "comment";
                    
                    // Avatar için ilk harfi al
                    const avatarText = comment.author.charAt(0).toUpperCase();
                    
                    commentEl.innerHTML = `
                        <div class="comment-avatar">${avatarText}</div>
                        <div class="comment-content">
                            <div class="comment-header">
                                <span class="comment-author">${comment.author}</span>
                                <span class="comment-date">${comment.date}</span>
                            </div>
                            <div class="comment-text">${comment.text}</div>
                        </div>
                    `;
                    commentList.appendChild(commentEl);
                });
            } else {
                commentList.innerHTML = "<p>Henüz yorum yok. İlk yorumu siz yapın!</p>";
            }
            
            // Modalı göster
            document.getElementById("newsModal").classList.add("active");
            document.body.style.overflow = "hidden";
        }
        
        // Modalı kapat
        function closeModal() {
            document.getElementById("newsModal").classList.remove("active");
            document.body.style.overflow = "auto";
            currentModalNewsId = null;
        }
        
        // Modal yorum ekle
        function addModalComment() {
            if (!currentModalNewsId) return;
            
            const authorInput = document.getElementById("modalCommentAuthor");
            const commentInput = document.getElementById("modalCommentInput");
            const author = authorInput.value.trim();
            const commentText = commentInput.value.trim();
            
            if (!author || !commentText) {
                showNotification("Lütfen adınızı ve yorumunuzu girin!", true);
                return;
            }
            
            const newsItem = newsList.find(item => item.id === currentModalNewsId);
            if (!newsItem) return;
            
            if (!newsItem.comments) newsItem.comments = [];
            
            const newComment = {
                author,
                text: commentText,
                date: new Date().toLocaleString("tr-TR")
            };
            
            newsItem.comments.push(newComment);
            saveNews();
            updateStats();
            
            // Yorum listesini güncelle
            const commentList = document.getElementById("modalCommentList");
            
            // "Henüz yorum yok" mesajını kaldır
            if (commentList.querySelector("p")) {
                commentList.innerHTML = "";
            }
            
            const commentEl = document.createElement("div");
            commentEl.className = "comment";
            
            // Avatar için ilk harfi al
            const avatarText = author.charAt(0).toUpperCase();
            
            commentEl.innerHTML = `
                <div class="comment-avatar">${avatarText}</div>
                <div class="comment-content">
                    <div class="comment-header">
                        <span class="comment-author">${author}</span>
                        <span class="comment-date">${newComment.date}</span>
                    </div>
                    <div class="comment-text">${commentText}</div>
                </div>
            `;
            
            commentList.prepend(commentEl);
            
            // Input'ları temizle
            authorInput.value = "";
            commentInput.value = "";
            
            // Haber kartındaki yorum sayısını güncelle
            const newsCard = document.querySelector(`.news-card[data-id="${currentModalNewsId}"] .comments-btn`);
            if (newsCard) {
                newsCard.innerHTML = `<i class="fas fa-comment"></i> ${newsItem.comments.length}`;
            }
            
            showNotification("Yorumunuz başarıyla eklendi!");
        }
        
        // Haber ara
        function searchNews() {
            const searchTerm = document.getElementById("searchInput").value.toLowerCase();
            if (!searchTerm.trim()) {
                displayNews();
                return;
            }
            
            const filteredNews = newsList.filter(news => 
                news.title.toLowerCase().includes(searchTerm) || 
                news.content.toLowerCase().includes(searchTerm) ||
                news.category.toLowerCase().includes(searchTerm)
            );
            
            displayNews(filteredNews);
        }
        
        // Haber seçim dropdown'ını güncelle
        function updateNewsDropdown() {
            const select = document.getElementById("newsSelect");
            select.innerHTML = '<option value="">Yeni haber ekle</option>';
            
            newsList.forEach(news => {
                select.innerHTML += `<option value="${news.id}">${news.title.substring(0, 50)}${news.title.length > 50 ? '...' : ''}</option>`;
            });
            
            select.addEventListener("change", function() {
                const newsId = parseInt(this.value);
                if (!newsId) {
                    cancelEdit();
                    return;
                }
                
                const newsItem = newsList.find(item => item.id === newsId);
                if (newsItem) {
                    currentEditingId = newsId;
                    document.getElementById("newsTitle").value = newsItem.title;
                    document.getElementById("newsContent").value = newsItem.content;
                    document.getElementById("newsImage").value = newsItem.image || "";
                    document.getElementById("newsCategory").value = newsItem.category || "Teknoloji";
                    
                    // Butonları güncelle
                    document.getElementById("addNewsBtn").classList.add("hidden");
                    document.getElementById("updateNewsBtn").classList.remove("hidden");
                    document.getElementById("deleteNewsBtn").classList.remove("hidden");
                    document.getElementById("cancelEditBtn").classList.remove("hidden");
                }
            });
        }
        
        // Giriş yap
        function login() {
            const password = document.getElementById("adminPassword").value;
            
            if (password === PASSWORD) {
                isLoggedIn = true;
                document.getElementById("loginForm").classList.add("hidden");
                document.getElementById("adminControls").classList.remove("hidden");
                document.getElementById("adminPassword").value = "";
                updateStats();
                showNotification("Başarıyla giriş yapıldı!");
            } else {
                showNotification("Hatalı şifre! Lütfen tekrar deneyin.", true);
            }
        }
        
        // Yeni haber ekle
        function addNews() {
            if (!isLoggedIn) return;
            
            const title = document.getElementById("newsTitle").value.trim();
            const content = document.getElementById("newsContent").value.trim();
            const imageUrl = document.getElementById("newsImage").value.trim() || "https://source.unsplash.com/random/800x400/?technology";
            const category = document.getElementById("newsCategory").value;
            
            if (!title || !content) {
                showNotification("Lütfen başlık ve içerik girin!", true);
                return;
            }
            
            const newNews = {
                id: Date.now(),
                title,
                content,
                image: imageUrl,
                category,
                date: new Date().toLocaleString("tr-TR", {
                    day: 'numeric',
                    month: 'long',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit'
                }),
                comments: []
            };
            
            newsList.push(newNews);
            saveNews();
            displayNews();
            updateNewsDropdown();
            updateStats();
            
            // Formu temizle
            document.getElementById("newsTitle").value = "";
            document.getElementById("newsContent").value = "";
            document.getElementById("newsImage").value = "";
            
            showNotification("Haber başarıyla eklendi!");
        }
        
        // Haber güncelle
        function updateNews() {
            if (!currentEditingId) return;
            
            const title = document.getElementById("newsTitle").value.trim();
            const content = document.getElementById("newsContent").value.trim();
            const imageUrl = document.getElementById("newsImage").value.trim();
            const category = document.getElementById("newsCategory").value;
            
            if (!title || !content) {
                showNotification("Lütfen başlık ve içerik girin!", true);
                return;
            }
            
            const newsIndex = newsList.findIndex(item => item.id === currentEditingId);
            if (newsIndex !== -1) {
                // Yorumları ve tarihi koru
                const comments = newsList[newsIndex].comments || [];
                const originalDate = newsList[newsIndex].date;
                
                newsList[newsIndex] = {
                    id: currentEditingId,
                    title,
                    content,
                    image: imageUrl,
                    category,
                    date: originalDate,
                    comments
                };
                
                saveNews();
                displayNews();
                updateNewsDropdown();
                updateStats();
                cancelEdit();
                
                showNotification("Haber başarıyla güncellendi!");
            }
        }
        
        // Haber sil
        function deleteNews() {
            if (!currentEditingId) return;
            
            if (confirm("Bu haberi silmek istediğinizden emin misiniz? Bu işlem geri alınamaz!")) {
                newsList = newsList.filter(item => item.id !== currentEditingId);
                saveNews();
                displayNews();
                updateNewsDropdown();
                updateStats();
                cancelEdit();
                
                showNotification("Haber başarıyla silindi!");
            }
        }
        
        // Düzenlemeyi iptal et
        function cancelEdit() {
            currentEditingId = null;
            document.getElementById("newsSelect").value = "";
            document.getElementById("newsTitle").value = "";
            document.getElementById("newsContent").value = "";
            document.getElementById("newsImage").value = "";
            document.getElementById("newsCategory").value = "Teknoloji";
            
            document.getElementById("addNewsBtn").classList.remove("hidden");
            document.getElementById("updateNewsBtn").classList.add("hidden");
            document.getElementById("deleteNewsBtn").classList.add("hidden");
            document.getElementById("cancelEditBtn").classList.add("hidden");
        }
        
        // Haberleri localStorage'a kaydet
        function saveNews() {
            localStorage.setItem("techTokTRNews", JSON.stringify(newsList));
        }
        
        // Bildirim göster
        function showNotification(message, isError = false) {
            const notification = document.getElementById("notification");
            const notificationText = document.getElementById("notificationText");
            
            notificationText.textContent = message;
            notification.className = isError ? "notification error" : "notification";
            notification.classList.add("show");
            
            setTimeout(() => {
                notification.classList.remove("show");
            }, 3000);
        }
    </script>
</body>
</html>
