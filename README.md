<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CardSwap - Ultimate Card Trading Platform</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #2cbe4e;
            --primary-dark: #218c3b;
            --secondary: #1a1f25;
            --accent: #ffcc00;
            --light: #f5f7fa;
            --text: #333333;
            --text-light: #777777;
            --border: #e1e5eb;
            --success: #4caf50;
            --warning: #ff9800;
            --danger: #f44336;
            --card-bg: #ffffff;
            --modal-bg: #ffffff;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            --border-radius: 10px;
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
        }

        body {
            background-color: #f0f2f5;
            color: var(--text);
            line-height: 1.6;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header Styles */
        header {
            background: var(--card-bg);
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.6rem;
            font-weight: 700;
            color: var(--primary);
        }

        .logo svg {
            width: 32px;
            height: 32px;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 25px;
        }

        nav a {
            color: var(--text);
            text-decoration: none;
            font-weight: 500;
            padding: 8px 12px;
            border-radius: 6px;
            transition: var(--transition);
        }

        nav a:hover, nav a.active {
            background: rgba(44, 190, 78, 0.1);
            color: var(--primary);
        }

        .auth-buttons {
            display: flex;
            gap: 12px;
        }

        .btn {
            padding: 10px 20px;
            border-radius: 6px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-size: 0.9rem;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-secondary {
            background: transparent;
            border: 1px solid var(--border);
            color: var(--text);
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        /* Main Content */
        .main-content {
            display: flex;
            gap: 30px;
            margin: 30px 0;
        }

        .sidebar {
            width: 250px;
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 25px;
            box-shadow: var(--shadow);
            height: fit-content;
        }

        .sidebar h3 {
            color: var(--primary);
            margin-bottom: 20px;
            font-size: 1.2rem;
        }

        .sidebar-menu {
            list-style: none;
        }

        .sidebar-menu li {
            margin-bottom: 15px;
        }

        .sidebar-menu a {
            color: var(--text);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 10px 12px;
            border-radius: 6px;
            transition: var(--transition);
        }

        .sidebar-menu a:hover, .sidebar-menu a.active {
            background: rgba(44, 190, 78, 0.1);
            color: var(--primary);
        }

        .content-area {
            flex: 1;
        }

        /* Page Title */
        .page-title {
            font-size: 1.8rem;
            margin-bottom: 25px;
            color: var(--text);
            display: flex;
            align-items: center;
            gap: 12px;
        }

        /* Homepage Styles */
        .hero {
            background: linear-gradient(135deg, #218c3b 0%, #2cbe4e 100%);
            color: white;
            border-radius: var(--border-radius);
            padding: 60px 40px;
            text-align: center;
            margin-bottom: 40px;
            box-shadow: var(--shadow);
        }

        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 30px;
        }

        .hero-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }

        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 50px;
        }

        .feature-card {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 30px;
            text-align: center;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }

        .feature-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }

        .feature-icon {
            font-size: 2.5rem;
            color: var(--primary);
            margin-bottom: 20px;
        }

        .feature-card h3 {
            font-size: 1.4rem;
            margin-bottom: 15px;
            color: var(--text);
        }

        /* Marketplace Filters */
        .marketplace-filters {
            display: flex;
            gap: 15px;
            margin-bottom: 25px;
            flex-wrap: wrap;
            background: var(--card-bg);
            padding: 20px;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
        }

        .filter-group {
            flex: 1;
            min-width: 180px;
        }

        .filter-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            font-size: 0.9rem;
            color: var(--text-light);
        }

        .form-control {
            width: 100%;
            padding: 12px 15px;
            border-radius: 6px;
            border: 1px solid var(--border);
            background: var(--card-bg);
            color: var(--text);
            font-size: 1rem;
        }

        /* Cards Grid */
        .cards-marketplace {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 25px;
        }

        .card-item {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            cursor: pointer;
        }

        .card-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.12);
        }

        .card-image {
            height: 180px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .card-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .card-image i {
            font-size: 4rem;
            color: var(--primary);
        }

        .card-badge {
            position: absolute;
            top: 12px;
            right: 12px;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
        }

        .card-info {
            padding: 20px;
        }

        .card-title {
            font-size: 1.1rem;
            margin-bottom: 8px;
            color: var(--text);
            font-weight: 600;
        }

        .card-meta {
            display: flex;
            justify-content: space-between;
            margin-bottom: 12px;
            font-size: 0.85rem;
            color: var(--text-light);
        }

        .card-price {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--primary);
            margin: 10px 0;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: var(--modal-bg);
            border-radius: var(--border-radius);
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            position: relative;
        }

        .modal-header {
            padding: 20px 25px;
            border-bottom: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .modal-title {
            font-size: 1.4rem;
            font-weight: 600;
            color: var(--text);
        }

        .close-modal {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-light);
        }

        .modal-body {
            padding: 25px;
        }

        .card-detail {
            display: flex;
            gap: 30px;
            margin-bottom: 30px;
        }

        .detail-image {
            flex: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            background: #f8f9fa;
            border-radius: var(--border-radius);
            padding: 20px;
        }

        .detail-image img {
            max-width: 100%;
            max-height: 300px;
            object-fit: contain;
        }

        .detail-info {
            flex: 1;
        }

        .detail-title {
            font-size: 1.6rem;
            margin-bottom: 10px;
            color: var(--text);
        }

        .detail-meta {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
            color: var(--text-light);
        }

        .detail-price {
            font-size: 2rem;
            font-weight: 700;
            color: var(--primary);
            margin: 15px 0;
        }

        .price-history {
            margin-top: 30px;
        }

        .price-history h3 {
            font-size: 1.2rem;
            margin-bottom: 15px;
            color: var(--text);
        }

        .history-table {
            width: 100%;
            border-collapse: collapse;
        }

        .history-table th {
            background: #f8f9fa;
            padding: 12px 15px;
            text-align: left;
            font-weight: 600;
            color: var(--text-light);
            font-size: 0.9rem;
        }

        .history-table td {
            padding: 12px 15px;
            border-bottom: 1px solid var(--border);
            font-size: 0.9rem;
        }

        .history-table tr:last-child td {
            border-bottom: none;
        }

        .price-up {
            color: var(--success);
        }

        .price-down {
            color: var(--danger);
        }

        .actions {
            display: flex;
            gap: 15px;
            margin-top: 25px;
        }

        /* Stats Cards */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 20px;
            box-shadow: var(--shadow);
            text-align: center;
        }

        .stat-value {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary);
            margin: 10px 0;
        }

        .stat-label {
            color: var(--text-light);
            font-size: 0.9rem;
        }

        /* Collections Section */
        .collections-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 25px;
        }

        .collection-card {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 20px;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }

        .collection-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.12);
        }

        .collection-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .collection-name {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--text);
        }

        .collection-stats {
            display: flex;
            justify-content: space-between;
            color: var(--text-light);
            font-size: 0.9rem;
            margin-top: 15px;
        }

        .collection-actions {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .btn-sm {
            padding: 8px 15px;
            font-size: 0.9rem;
        }

        /* Sell Card Form */
        .sell-form {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 30px;
            box-shadow: var(--shadow);
        }

        .form-row {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
        }

        .form-group {
            flex: 1;
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--text);
        }

        .form-group.full-width {
            width: 100%;
        }

        .image-upload {
            border: 2px dashed var(--border);
            border-radius: var(--border-radius);
            padding: 30px;
            text-align: center;
            margin-bottom: 20px;
        }

        .image-upload i {
            font-size: 3rem;
            color: var(--text-light);
            margin-bottom: 15px;
        }

        .image-upload p {
            margin-bottom: 15px;
            color: var(--text-light);
        }

        .terms {
            background: #fff8e1;
            border-left: 4px solid #ffc107;
            padding: 15px;
            border-radius: 0 4px 4px 0;
            margin: 20px 0;
        }

        .terms h4 {
            margin-bottom: 10px;
            color: #5d4037;
        }

        .terms ul {
            padding-left: 20px;
        }

        .terms li {
            margin-bottom: 8px;
        }

        /* Deck Builder */
        .deck-builder {
            display: flex;
            gap: 30px;
        }

        .deck-cards {
            flex: 2;
        }

        .deck-sidebar {
            flex: 1;
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 20px;
            box-shadow: var(--shadow);
        }

        .deck-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
        }

        .deck-stats {
            display: flex;
            gap: 20px;
            margin-bottom: 25px;
        }

        .stat-card-deck {
            background: #f8f9fa;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            flex: 1;
        }

        .stat-value-deck {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            margin: 10px 0;
        }

        .stat-label-deck {
            color: var(--text-light);
            font-size: 0.9rem;
        }

        .deck-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            gap: 15px;
        }

        .deck-card {
            background: #f8f9fa;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            transition: var(--transition);
        }

        .deck-card:hover {
            background: rgba(44, 190, 78, 0.1);
            transform: translateY(-3px);
        }

        .deck-card img {
            width: 80px;
            height: 110px;
            object-fit: contain;
            margin-bottom: 10px;
            border-radius: 4px;
        }

        .deck-card-name {
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 5px;
        }

        .deck-card-count {
            font-size: 0.8rem;
            color: var(--text-light);
        }

        /* Footer */
        footer {
            background: var(--secondary);
            color: white;
            padding: 40px 0 20px;
            margin-top: 50px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }

        .footer-column h3 {
            color: var(--accent);
            margin-bottom: 20px;
            font-size: 1.3rem;
        }

        .footer-column ul {
            list-style: none;
        }

        .footer-column ul li {
            margin-bottom: 12px;
        }

        .footer-column a {
            color: #ccc;
            text-decoration: none;
            transition: var(--transition);
        }

        .footer-column a:hover {
            color: var(--accent);
        }

        .copyright {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #aaa;
            font-size: 0.9rem;
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .main-content {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
            }
            
            .card-detail {
                flex-direction: column;
            }
            
            .deck-builder {
                flex-direction: column;
            }
            
            .form-row {
                flex-direction: column;
            }
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .marketplace-filters {
                flex-direction: column;
            }
            
            .filter-group {
                width: 100%;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <!-- Card-themed Logo with Arrows -->
                <svg viewBox="0 0 32 32">
                    <rect x="4" y="4" width="24" height="24" rx="4" fill="var(--primary)" />
                    <path d="M10 16 L6 12 M6 12 L6 20" stroke="white" stroke-width="2" fill="none"/>
                    <path d="M22 16 L26 12 M26 12 L26 20" stroke="white" stroke-width="2" fill="none"/>
                    <rect x="8" y="8" width="16" height="16" rx="2" fill="white" opacity="0.3"/>
                </svg>
                <span>CardSwap</span>
            </div>
            <nav>
                <ul>
                    <li><a href="#" class="active" data-page="home">Home</a></li>
                    <li><a href="#" data-page="marketplace">Marketplace</a></li>
                    <li><a href="#" data-page="collections">Collections</a></li>
                    <li><a href="#" data-page="sell">Sell Cards</a></li>
                    <li><a href="#" data-page="decks">Decks</a></li>
                </ul>
            </nav>
            <div class="auth-buttons">
                <button class="btn btn-secondary"><i class="fas fa-sign-in-alt"></i> Login</button>
                <button class="btn btn-primary"><i class="fas fa-user-plus"></i> Sign Up</button>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <div class="container main-content">
        <!-- Sidebar Navigation -->
        <aside class="sidebar">
            <h3>Navigation</h3>
            <ul class="sidebar-menu">
                <li><a href="#" class="active" data-page="home"><i class="fas fa-home"></i> Home</a></li>
                <li><a href="#" data-page="marketplace"><i class="fas fa-store"></i> Marketplace</a></li>
                <li><a href="#" data-page="collections"><i class="fas fa-book"></i> My Collections</a></li>
                <li><a href="#" data-page="sell"><i class="fas fa-tag"></i> Sell Cards</a></li>
                <li><a href="#" data-page="decks"><i class="fas fa-layer-group"></i> Deck Builder</a></li>
                <li><a href="#" data-page="profile"><i class="fas fa-user"></i> My Profile</a></li>
                <li><a href="#" data-page="settings"><i class="fas fa-cog"></i> Settings</a></li>
            </ul>
            
            <h3>Quick Actions</h3>
            <ul class="sidebar-menu">
                <li><a href="#" data-action="add-collection"><i class="fas fa-plus-circle"></i> Add Collection</a></li>
                <li><a href="#" data-action="trade-cards"><i class="fas fa-exchange-alt"></i> Trade Cards</a></li>
                <li><a href="#" data-action="view-wishlist"><i class="fas fa-heart"></i> Wishlist</a></li>
            </ul>
        </aside>

        <!-- Content Area -->
        <main class="content-area">
            <!-- Home Page -->
            <div id="home-page">
                <div class="hero">
                    <h1>Trade, Collect, and Connect</h1>
                    <p>The ultimate platform for buying, selling, and trading collectible cards. Join thousands of collectors worldwide!</p>
                    <div class="hero-buttons">
                        <button class="btn btn-primary" onclick="navigateTo('marketplace')"><i class="fas fa-search"></i> Browse Marketplace</button>
                        <button class="btn btn-secondary" onclick="navigateTo('sell')"><i class="fas fa-tag"></i> Sell Your Cards</button>
                    </div>
                </div>
                
                <div class="features">
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-store"></i>
                        </div>
                        <h3>Marketplace</h3>
                        <p>Browse thousands of cards from trusted sellers. Find rare cards at competitive prices with real-time market data.</p>
                    </div>
                    
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-layer-group"></i>
                        </div>
                        <h3>Deck Builder</h3>
                        <p>Create and manage your decks with our powerful builder. Analyze synergies and optimize your strategies.</p>
                    </div>
                    
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-chart-line"></i>
                        </div>
                        <h3>Market Insights</h3>
                        <p>Access real-time pricing data from TCGplayer to make informed buying and selling decisions.</p>
                    </div>
                </div>
                
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-value">12,480</div>
                        <div class="stat-label">Cards Listed</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">1,245</div>
                        <div class="stat-label">Active Sellers</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">$142,850</div>
                        <div class="stat-label">Volume This Month</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">98%</div>
                        <div class="stat-label">Satisfaction</div>
                    </div>
                </div>
            </div>
            
            <!-- Marketplace Page -->
            <div id="marketplace-page" style="display: none;">
                <h2 class="page-title"><i class="fas fa-store"></i> Marketplace</h2>
                
                <!-- Filters -->
                <div class="marketplace-filters">
                    <div class="filter-group">
                        <label for="category">Category</label>
                        <select id="category" class="form-control">
                            <option>All Categories</option>
                            <option>Pokémon</option>
                            <option>Magic: The Gathering</option>
                            <option>Sports Cards</option>
                            <option>Yu-Gi-Oh!</option>
                            <option>Other</option>
                        </select>
                    </div>
                    
                    <div class="filter-group">
                        <label for="price-range">Price Range</label>
                        <select id="price-range" class="form-control">
                            <option>All Prices</option>
                            <option>Under $10</option>
                            <option>$10 - $50</option>
                            <option>$50 - $100</option>
                            <option>Over $100</option>
                        </select>
                    </div>
                    
                    <div class="filter-group">
                        <label for="condition">Condition</label>
                        <select id="condition" class="form-control">
                            <option>All Conditions</option>
                            <option>Mint</option>
                            <option>Near Mint</option>
                            <option>Excellent</option>
                            <option>Good</option>
                        </select>
                    </div>
                    
                    <div class="filter-group">
                        <label for="sort">Sort By</label>
                        <select id="sort" class="form-control">
                            <option>Newest First</option>
                            <option>Price: Low to High</option>
                            <option>Price: High to Low</option>
                            <option>Most Popular</option>
                        </select>
                    </div>
                </div>
                
                <!-- Cards Grid -->
                <div class="cards-marketplace">
                    <!-- Pokemon Card -->
                    <div class="card-item" onclick="openModal('charizard')">
                        <div class="card-image">
                            <i class="fas fa-fire"></i>
                            <div class="card-badge">Pokémon</div>
                        </div>
                        <div class="card-info">
                            <h3 class="card-title">Charizard GX</h3>
                            <div class="card-meta">
                                <span>Mint Condition</span>
                                <span>Holofoil</span>
                            </div>
                            <div class="card-price">$850.00</div>
                        </div>
                    </div>
                    
                    <!-- Magic Card -->
                    <div class="card-item" onclick="openModal('blacklotus')">
                        <div class="card-image">
                            <i class="fas fa-star"></i>
                            <div class="card-badge">Magic</div>
                        </div>
                        <div class="card-info">
                            <h3 class="card-title">Black Lotus</h3>
                            <div class="card-meta">
                                <span>Near Mint</span>
                                <span>Vintage</span>
                            </div>
                            <div class="card-price">$25,000.00</div>
                        </div>
                    </div>
                    
                    <!-- Sports Card -->
                    <div class="card-item" onclick="openModal('baberuth')">
                        <div class="card-image">
                            <i class="fas fa-baseball-ball"></i>
                            <div class="card-badge">Sports</div>
                        </div>
                        <div class="card-info">
                            <h3 class="card-title">Babe Ruth Rookie</h3>
                            <div class="card-meta">
                                <span>Excellent</span>
                                <span>1916</span>
                            </div>
                            <div class="card-price">$12,500.00</div>
                        </div>
                    </div>
                    
                    <!-- Yugioh Card -->
                    <div class="card-item" onclick="openModal('blueeyes')">
                        <div class="card-image">
                            <i class="fas fa-dragon"></i>
                            <div class="card-badge">Yu-Gi-Oh!</div>
                        </div>
                        <div class="card-info">
                            <h3 class="card-title">Blue-Eyes Ultimate Dragon</h3>
                            <div class="card-meta">
                                <span>Mint</span>
                                <span>Limited Edition</span>
                            </div>
                            <div class="card-price">$3,200.00</div>
                        </div>
                    </div>
                    
                    <!-- Pokemon Card -->
                    <div class="card-item" onclick="openModal('pikachu')">
                        <div class="card-image">
                            <i class="fas fa-bolt"></i>
                            <div class="card-badge">Pokémon</div>
                        </div>
                        <div class="card-info">
                            <h3 class="card-title">Pikachu Illustrator</h3>
                            <div class="card-meta">
                                <span>Mint</span>
                                <span>Promo</span>
                            </div>
                            <div class="card-price">$180,000.00</div>
                        </div>
                    </div>
                    
                    <!-- Magic Card -->
                    <div class="card-item" onclick="openModal('timewalk')">
                        <div class="card-image">
                            <i class="fas fa-clock"></i>
                            <div class="card-badge">Magic</div>
                        </div>
                        <div class="card-info">
                            <h3 class="card-title">Time Walk</h3>
                            <div class="card-meta">
                                <span>Good</span>
                                <span>Alpha</span>
                            </div>
                            <div class="card-price">$7,800.00</div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Collections Page -->
            <div id="collections-page" style="display: none;">
                <h2 class="page-title"><i class="fas fa-book"></i> My Collections</h2>
                
                <div class="collections-grid">
                    <div class="collection-card">
                        <div class="collection-header">
                            <div class="collection-name">Pokémon Collection</div>
                            <div class="collection-count">42 cards</div>
                        </div>
                        <p>My main collection of Pokémon cards spanning all generations.</p>
                        <div class="collection-stats">
                            <span>Total Value: $1,250</span>
                            <span>Rarest: Charizard GX</span>
                        </div>
                        <div class="collection-actions">
                            <button class="btn btn-sm btn-primary">View</button>
                            <button class="btn btn-sm btn-secondary">Edit</button>
                        </div>
                    </div>
                    
                    <div class="collection-card">
                        <div class="collection-header">
                            <div class="collection-name">Magic: The Gathering</div>
                            <div class="collection-count">128 cards</div>
                        </div>
                        <p>Focus on Standard and Modern format cards.</p>
                        <div class="collection-stats">
                            <span>Total Value: $3,800</span>
                            <span>Rarest: Black Lotus</span>
                        </div>
                        <div class="collection-actions">
                            <button class="btn btn-sm btn-primary">View</button>
                            <button class="btn btn-sm btn-secondary">Edit</button>
                        </div>
                    </div>
                    
                    <div class="collection-card">
                        <div class="collection-header">
                            <div class="collection-name">Sports Cards</div>
                            <div class="collection-count">75 cards</div>
                        </div>
                        <p>Vintage and modern baseball cards.</p>
                        <div class="collection-stats">
                            <span>Total Value: $2,450</span>
                            <span>Rarest: Babe Ruth</span>
                        </div>
                        <div class="collection-actions">
                            <button class="btn btn-sm btn-primary">View</button>
                            <button class="btn btn-sm btn-secondary">Edit</button>
                        </div>
                    </div>
                    
                    <div class="collection-card">
                        <div class="collection-header">
                            <div class="collection-name">Yu-Gi-Oh! Deck</div>
                            <div class="collection-count">40 cards</div>
                        </div>
                        <p>Competitive Dragon deck for tournaments.</p>
                        <div class="collection-stats">
                            <span>Total Value: $850</span>
                            <span>Rarest: Blue-Eyes</span>
                        </div>
                        <div class="collection-actions">
                            <button class="btn btn-sm btn-primary">View</button>
                            <button class="btn btn-sm btn-secondary">Edit</button>
                        </div>
                    </div>
                </div>
                
                <div style="margin-top: 30px; text-align: center;">
                    <button class="btn btn-primary"><i class="fas fa-plus"></i> Create New Collection</button>
                </div>
            </div>
            
            <!-- Sell Cards Page -->
            <div id="sell-page" style="display: none;">
                <h2 class="page-title"><i class="fas fa-tag"></i> Sell Your Cards</h2>
                
                <div class="sell-form">
                    <div class="terms">
                        <h4><i class="fas fa-exclamation-triangle"></i> Important Seller Terms</h4>
                        <ul>
                            <li>You must ship purchased items within 3 business days</li>
                            <li>Failure to ship will result in account suspension and potential fines</li>
                            <li>All sales are final once shipped (buyer confirms receipt)</li>
                            <li>Misrepresentation of items may lead to permanent account ban</li>
                        </ul>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="storeName">Store/Business Name *</label>
                            <input type="text" id="storeName" class="form-control" placeholder="Enter your store name">
                        </div>
                        
                        <div class="form-group">
                            <label for="cardName">Card Name *</label>
                            <input type="text" id="cardName" class="form-control" placeholder="e.g. Charizard GX">
                        </div>
                    </div>
                    
                    <div class="image-upload">
                        <i class="fas fa-cloud-upload-alt"></i>
                        <p>Upload a clear photo of your card</p>
                        <p>(Max file size: 5MB, JPG/PNG only)</p>
                        <button class="btn btn-secondary"><i class="fas fa-camera"></i> Choose Image</button>
                        <input type="file" id="cardImage" accept="image/*" style="display: none;">
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="category">Category *</label>
                            <select id="category" class="form-control">
                                <option>Select category</option>
                                <option>Pokémon</option>
                                <option>Magic: The Gathering</option>
                                <option>Sports Cards</option>
                                <option>Yu-Gi-Oh!</option>
                                <option>Other</option>
                            </select>
                        </div>
                        
                        <div class="form-group">
                            <label for="condition">Condition *</label>
                            <select id="condition" class="form-control">
                                <option>Select condition</option>
                                <option>Mint</option>
                                <option>Near Mint</option>
                                <option>Excellent</option>
                                <option>Good</option>
                                <option>Fair</option>
                                <option>Poor</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="price">Price ($) *</label>
                            <input type="number" id="price" class="form-control" placeholder="0.00" min="0" step="0.01">
                        </div>
                        
                        <div class="form-group">
                            <label for="quantity">Quantity *</label>
                            <input type="number" id="quantity" class="form-control" placeholder="1" min="1">
                        </div>
                    </div>
                    
                    <div class="form-group full-width">
                        <label for="description">Description</label>
                        <textarea id="description" class="form-control" placeholder="Describe the card's condition, special features, etc." rows="4"></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label>
                            <input type="checkbox" id="agreement" required> 
                            I agree to the seller terms and understand that failure to ship will result in penalties
                        </label>
                    </div>
                    
                    <button type="submit" class="btn btn-primary" style="width: 100%; padding: 15px; font-size: 1.1rem;">
                        <i class="fas fa-plus-circle"></i> List Card for Sale
                    </button>
                </div>
            </div>
            
            <!-- Decks Page -->
            <div id="decks-page" style="display: none;">
                <h2 class="page-title"><i class="fas fa-layer-group"></i> Deck Builder</h2>
                
                <div class="deck-builder">
                    <div class="deck-cards">
                        <div class="deck-header">
                            <h3>Dragon Destruction Deck</h3>
                            <div>
                                <button class="btn btn-secondary"><i class="fas fa-save"></i> Save Deck</button>
                                <button class="btn btn-primary"><i class="fas fa-share-alt"></i> Share</button>
                            </div>
                        </div>
                        
                        <div class="deck-stats">
                            <div class="stat-card-deck">
                                <div class="stat-value-deck">40</div>
                                <div class="stat-label-deck">Total Cards</div>
                            </div>
                            <div class="stat-card-deck">
                                <div class="stat-value-deck">25</div>
                                <div class="stat-label-deck">Monsters</div>
                            </div>
                            <div class="stat-card-deck">
                                <div class="stat-value-deck">10</div>
                                <div class="stat-label-deck">Spells</div>
                            </div>
                            <div class="stat-card-deck">
                                <div class="stat-value-deck">5</div>
                                <div class="stat-label-deck">Traps</div>
                            </div>
                        </div>
                        
                        <div class="deck-list">
                            <div class="deck-card">
                                <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiNmZmNjMDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+RHJhZ29uPC90ZXh0Pjwvc3ZnPg==" alt="Dragon">
                                <div class="deck-card-name">Blue-Eyes White Dragon</div>
                                <div class="deck-card-count">×3</div>
                            </div>
                            
                            <div class="deck-card">
                                <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiNmZjAwMDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+RmlyZTwvdGV4dD48L3N2Zz4=" alt="Fire">
                                <div class="deck-card-name">Flame Swordsman</div>
                                <div class="deck-card-count">×2</div>
                            </div>
                            
                            <div class="deck-card">
                                <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiMwMDY2Y2MiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+TWFnaWM8L3RleHQ+PC9zdmc+" alt="Magic">
                                <div class="deck-card-name">Dark Magician</div>
                                <div class="deck-card-count">×2</div>
                            </div>
                            
                            <div class="deck-card">
                                <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiNmZmNjMDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+U3BlbGw8L3RleHQ+PC9zdmc+" alt="Spell">
                                <div class="deck-card-name">Monster Reborn</div>
                                <div class="deck-card-count">×1</div>
                            </div>
                            
                            <div class="deck-card">
                                <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiNmZjAwMDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+VHJhcDwvdGV4dD48L3N2Zz4=" alt="Trap">
                                <div class="deck-card-name">Mirror Force</div>
                                <div class="deck-card-count">×1</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="deck-sidebar">
                        <h3>Available Cards</h3>
                        <div class="form-group">
                            <input type="text" class="form-control" placeholder="Search cards...">
                        </div>
                        
                        <div class="deck-list">
                            <div class="deck-card">
                                <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiNmZmNjMDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+RHJhZ29uPC90ZXh0Pjwvc3ZnPg==" alt="Dragon">
                                <div class="deck-card-name">Red-Eyes B. Dragon</div>
                                <div class="deck-card-count">×2</div>
                            </div>
                            
                            <div class="deck-card">
                                <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiNmZjAwMDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+RmlyZTwvdGV4dD48L3N2Zz4=" alt="Fire">
                                <div class="deck-card-name">Inferno Fire Blast</div>
                                <div class="deck-card-count">×1</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>

    <!-- Card Detail Modal -->
    <div class="modal" id="cardModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="modal-title" id="modalTitle">Card Details</h2>
                <button class="close-modal" onclick="closeModal()">&times;</button>
            </div>
            <div class="modal-body">
                <div class="card-detail">
                    <div class="detail-image">
                        <img id="modalImage" src="" alt="Card Image">
                    </div>
                    <div class="detail-info">
                        <h2 class="detail-title" id="modalCardTitle">Card Name</h2>
                        <div class="detail-meta">
                            <span id="modalCategory">Category</span>
                            <span id="modalCondition">Condition</span>
                            <span id="modalSet">Set</span>
                        </div>
                        <p id="modalDescription">Card description will appear here.</p>
                        <div class="detail-price" id="modalPrice">$0.00</div>
                        <div class="actions">
                            <button class="btn btn-primary"><i class="fas fa-shopping-cart"></i> Buy Now</button>
                            <button class="btn btn-secondary"><i class="fas fa-exchange-alt"></i> Trade</button>
                        </div>
                    </div>
                </div>
                
                <div class="price-history">
                    <h3>Price History (Last 6 Months)</h3>
                    <table class="history-table">
                        <thead>
                            <tr>
                                <th>Date</th>
                                <th>Price</th>
                                <th>Change</th>
                                <th>Condition</th>
                            </tr>
                        </thead>
                        <tbody id="priceHistoryBody">
                            <!-- Price history rows will be inserted here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>CardSwap</h3>
                    <p>The ultimate platform for card collectors to buy, sell, and trade their favorite collectibles.</p>
                </div>
                
                <div class="footer-column">
                    <h3>Marketplace</h3>
                    <ul>
                        <li><a href="#" onclick="navigateTo('marketplace')">Browse Cards</a></li>
                        <li><a href="#" onclick="navigateTo('sell')">Sell Your Cards</a></li>
                        <li><a href="#" onclick="navigateTo('collections')">My Collections</a></li>
                        <li><a href="#" onclick="navigateTo('decks')">Deck Builder</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Resources</h3>
                    <ul>
                        <li><a href="#">Collector Guides</a></li>
                        <li><a href="#">Grading Services</a></li>
                        <li><a href="#">Price Guide</a></li>
                        <li><a href="#">Community Forums</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Support</h3>
                    <ul>
                        <li><a href="#">Help Center</a></li>
                        <li><a href="#">Contact Us</a></li>
                        <li><a href="#">Safety Tips</a></li>
                        <li><a href="#">Terms of Service</a></li>
                    </ul>
                </div>
            </div>
            
            <div class="copyright">
                <p>&copy; 2023 CardSwap. All rights reserved. Market data provided by TCGplayer. Deck builder inspired by Archidekt.</p>
            </div>
        </div>
    </footer>

    <script>
        // Card data
        const cardData = {
            charizard: {
                title: "Charizard GX",
                category: "Pokémon",
                condition: "Mint Condition",
                set: "Sun & Moon Series",
                description: "Shiny Charizard GX holographic card from Sun & Moon series. One of the most sought-after cards!",
                price: "$850.00",
                image: "data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiNmZjAwMDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmY2MwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+Q2hhcml6YXJkPC90ZXh0Pjwvc3ZnPg==",
                history: [
                    { date: "2023-10-15", price: "$820.00", change: "+3.7%", condition: "Mint" },
                    { date: "2023-09-22", price: "$790.00", change: "+2.6%", condition: "Mint" },
                    { date: "2023-08-30", price: "$770.00", change: "-1.3%", condition: "Mint" },
                    { date: "2023-07-18", price: "$780.00", change: "+4.0%", condition: "Mint" },
                    { date: "2023-06-05", price: "$750.00", change: "+5.6%", condition: "Mint" },
                    { date: "2023-05-12", price: "$710.00", change: "+2.9%", condition: "Mint" }
                ]
            },
            blacklotus: {
                title: "Black Lotus",
                category: "Magic: The Gathering",
                condition: "Near Mint",
                set: "Alpha Edition",
                description: "Alpha Black Lotus - one of the most valuable Magic cards ever printed. A true collector's item!",
                price: "$25,000.00",
                image: "data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiMwMDY2Y2MiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+QmxhY2sgTG90dXM8L3RleHQ+PC9zdmc+",
                history: [
                    { date: "2023-10-10", price: "$24,800.00", change: "+0.8%", condition: "Near Mint" },
                    { date: "2023-09-18", price: "$24,600.00", change: "+1.2%", condition: "Near Mint" },
                    { date: "2023-08-25", price: "$24,300.00", change: "-0.4%", condition: "Near Mint" },
                    { date: "2023-07-30", price: "$24,400.00", change: "+2.5%", condition: "Near Mint" },
                    { date: "2023-06-15", price: "$23,800.00", change: "+3.5%", condition: "Near Mint" },
                    { date: "2023-05-20", price: "$22,900.00", change: "+1.8%", condition: "Near Mint" }
                ]
            },
            baberuth: {
                title: "Babe Ruth Rookie",
                category: "Sports Cards",
                condition: "Excellent",
                set: "1916 Sporting News",
                description: "Original 1916 Sporting News Babe Ruth rookie card. Historical baseball memorabilia.",
                price: "$12,500.00",
                image: "data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiMwMDk5MDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iIzAwY2M2NiIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+QmFiZSBSdXRoPC90ZXh0Pjwvc3ZnPg==",
                history: [
                    { date: "2023-10-05", price: "$12,300.00", change: "+1.6%", condition: "Excellent" },
                    { date: "2023-09-12", price: "$12,100.00", change: "+0.8%", condition: "Excellent" },
                    { date: "2023-08-20", price: "$12,000.00", change: "+2.5%", condition: "Excellent" },
                    { date: "2023-07-25", price: "$11,700.00", change: "+3.5%", condition: "Excellent" },
                    { date: "2023-06-30", price: "$11,300.00", change: "+1.8%", condition: "Excellent" },
                    { date: "2023-05-15", price: "$11,100.00", change: "+2.8%", condition: "Excellent" }
                ]
            },
            blueeyes: {
                title: "Blue-Eyes Ultimate Dragon",
                category: "Yu-Gi-Oh!",
                condition: "Mint",
                set: "Limited Edition",
                description: "Limited edition Blue-Eyes Ultimate Dragon with foil treatment. Rare promotional card.",
                price: "$3,200.00",
                image: "data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiNmZmNjMDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+RHJhZ29uPC90ZXh0Pjwvc3ZnPg==",
                history: [
                    { date: "2023-10-12", price: "$3,150.00", change: "+1.6%", condition: "Mint" },
                    { date: "2023-09-19", price: "$3,100.00", change: "+2.5%", condition: "Mint" },
                    { date: "2023-08-27", price: "$3,025.00", change: "+1.7%", condition: "Mint" },
                    { date: "2023-07-31", price: "$2,975.00", change: "+3.4%", condition: "Mint" },
                    { date: "2023-06-18", price: "$2,875.00", change: "+2.7%", condition: "Mint" },
                    { date: "2023-05-22", price: "$2,800.00", change: "+4.0%", condition: "Mint" }
                ]
            },
            pikachu: {
                title: "Pikachu Illustrator",
                category: "Pokémon",
                condition: "Mint",
                set: "Promotional",
                description: "Extremely rare promotional card given to winners of Japanese illustration contests. Only 39 known to exist.",
                price: "$180,000.00",
                image: "data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiNmZmNjMDAiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+UGlrYWNodTwvdGV4dD48L3N2Zz4=",
                history: [
                    { date: "2023-10-01", price: "$178,000.00", change: "+1.1%", condition: "Mint" },
                    { date: "2023-09-15", price: "$176,000.00", change: "+2.3%", condition: "Mint" },
                    { date: "2023-08-22", price: "$172,000.00", change: "+1.8%", condition: "Mint" },
                    { date: "2023-07-28", price: "$169,000.00", change: "+3.1%", condition: "Mint" },
                    { date: "2023-06-10", price: "$164,000.00", change: "+2.5%", condition: "Mint" },
                    { date: "2023-05-18", price: "$160,000.00", change: "+4.0%", condition: "Mint" }
                ]
            },
            timewalk: {
                title: "Time Walk",
                category: "Magic: The Gathering",
                condition: "Good",
                set: "Alpha Edition",
                description: "Alpha Time Walk from the Power Nine set. Extremely rare vintage card.",
                price: "$7,800.00",
                image: "data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgMTAwIDE0MCI+PHJlY3Qgd2lkdGg9IjEwMCIgaGVpZ2h0PSIxNDAiIGZpbGw9IiMwMDY2Y2MiLz48Y2lyY2xlIGN4PSI1MCIgY3k9IjcwIiByPSIzMCIgZmlsbD0iI2ZmNjYwMCIvPjx0ZXh0IHg9IjUwIiB5PSI3NSIgZm9udC1mYW1pbHk9IkFyaWFsIiBmb250LXNpemU9IjEyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSI+VGltZSBXYWxrPC90ZXh0Pjwvc3ZnPg==",
                history: [
                    { date: "2023-10-08", price: "$7,650.00", change: "+2.0%", condition: "Good" },
                    { date: "2023-09-14", price: "$7,500.00", change: "+1.3%", condition: "Good" },
                    { date: "2023-08-19", price: "$7,400.00", change: "+2.8%", condition: "Good" },
                    { date: "2023-07-22", price: "$7,200.00", change: "+3.5%", condition: "Good" },
                    { date: "2023-06-28", price: "$6,950.00", change: "+2.2%", condition: "Good" },
                    { date: "2023-05-30", price: "$6,800.00", change: "+4.6%", condition: "Good" }
                ]
            }
        };

        // Open modal function
        function openModal(cardId) {
            const card = cardData[cardId];
            if (!card) return;
            
            document.getElementById('modalTitle').textContent = card.title;
            document.getElementById('modalCardTitle').textContent = card.title;
            document.getElementById('modalCategory').textContent = card.category;
            document.getElementById('modalCondition').textContent = card.condition;
            document.getElementById('modalSet').textContent = card.set;
            document.getElementById('modalDescription').textContent = card.description;
            document.getElementById('modalPrice').textContent = card.price;
            document.getElementById('modalImage').src = card.image;
            
            // Populate price history
            const historyBody = document.getElementById('priceHistoryBody');
            historyBody.innerHTML = '';
            
            card.history.forEach(item => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${item.date}</td>
                    <td>${item.price}</td>
                    <td class="${parseFloat(item.change) >= 0 ? 'price-up' : 'price-down'}">${item.change}</td>
                    <td>${item.condition}</td>
                `;
                historyBody.appendChild(row);
            });
            
            document.getElementById('cardModal').style.display = 'flex';
        }

        // Close modal function
        function closeModal() {
            document.getElementById('cardModal').style.display = 'none';
        }

        // Close modal when clicking outside
        window.onclick = function(event) {
            const modal = document.getElementById('cardModal');
            if (event.target === modal) {
                closeModal();
            }
        }

        // Navigation functionality
        function navigateTo(page) {
            // Hide all pages
            document.querySelectorAll('[id$="-page"]').forEach(page => {
                page.style.display = 'none';
            });
            
            // Show target page
            document.getElementById(`${page}-page`).style.display = 'block';
            
            // Update active state in navigation
            document.querySelectorAll('[data-page]').forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('data-page') === page) {
                    link.classList.add('active');
                }
            });
        }

        // Set up navigation event listeners
        document.querySelectorAll('[data-page]').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                const page = this.getAttribute('data-page');
                navigateTo(page);
            });
        });

        // Initial setup
        document.addEventListener('DOMContentLoaded', function() {
            // Set first sidebar link as active
            document.querySelector('.sidebar-menu a').classList.add('active');
        });
    </script>
</body>
</html>
