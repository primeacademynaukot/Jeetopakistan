# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jeeto Pakistan - Premium Online Shopping</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-storage-compat.js"></script>
    <script src="https://widget.cloudinary.com/v2.0/global/all.js" type="text/javascript"></script>
    <style>
        :root {
    --pakistan-green: #01411C;
    --pakistan-white: #FFFFFF;
    --pakistan-black: #000000;
    --pakistan-accent: #F5F5F5;
    --pakistan-gold: #D4AF37;
    --pakistan-light-green: #00693E;
    --pakistan-dark-green: #003315;
    --primary: var(--pakistan-green);
    --secondary: var(--pakistan-white);
    --accent: var(--pakistan-accent);
    --background: var(--pakistan-white);
    --text-primary: var(--pakistan-black);
    --text-secondary: #4A4A4A;
    --white: var(--pakistan-white);
    --border: #E5E5E5;
    --success: #27AE60;
    --warning: #F39C12;
    --error: #E74C3C;
    --info: #3498DB;
    --shadow: 0 4px 20px rgba(1, 65, 28, 0.08);
    --shadow-lg: 0 8px 30px rgba(1, 65, 28, 0.12);
    --radius: 12px;
    --radius-lg: 16px;
    --glass: rgba(255, 255, 255, 0.9);
    --glass-border: rgba(1, 65, 28, 0.1);
    --header-height: 120px;
    
    /* ADD THIS LINE */
    --primary-light: rgba(1, 65, 28, 0.1);
}

        [data-theme="dark"] {
            --primary: #00693E;
            --secondary: #1A1A1A;
            --accent: #2A2A2A;
            --background: #121212;
            --text-primary: #FFFFFF;
            --text-secondary: #B0B0B0;
            --white: #1A1A1A;
            --border: #333333;
            --pakistan-green: #00693E;
            --pakistan-white: #1A1A1A;
            --pakistan-black: #FFFFFF;
            --pakistan-accent: #2A2A2A;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', sans-serif;
            transition: background-color 0.3s, color 0.3s;
        }

        body {
            background-color: var(--background);
            color: var(--text-primary);
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Pakistan Flag Header */
        .flag-header {
            height: 5px;
            background: linear-gradient(90deg, 
                var(--pakistan-green) 0%, 
                var(--pakistan-green) 33%, 
                var(--pakistan-white) 33%, 
                var(--pakistan-white) 66%, 
                var(--pakistan-black) 66%, 
                var(--pakistan-black) 100%);
        }

        /* Premium Header Styles */
        header {
            background: var(--white);
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 1000;
            backdrop-filter: blur(10px);
            background: var(--glass);
            border-bottom: 1px solid var(--glass-border);
        }

        .header-top {
            background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-dark-green));
            color: var(--pakistan-white);
            padding: 8px 0;
            font-size: 0.9rem;
        }

        .header-main {
            padding: 1rem 0;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
        }

        .logo-icon {
            font-size: 2rem;
            color: var(--primary);
        }

        .logo-text h1 {
            font-size: 1.8rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-light-green));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .logo-text p {
            font-size: 0.8rem;
            color: var(--text-secondary);
        }

        .search-bar {
            flex: 1;
            min-width: 300px;
            max-width: 600px;
            position: relative;
        }

        .search-bar input {
            width: 100%;
            padding: 12px 20px;
            border: 2px solid var(--border);
            border-radius: 50px;
            font-size: 1rem;
            transition: all 0.3s;
            background: var(--white);
            color: var(--text-primary);
        }

        .search-bar input:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(1, 65, 28, 0.1);
        }

        .search-bar button {
            position: absolute;
            right: 5px;
            top: 5px;
            background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-light-green));
            color: white;
            border: none;
            border-radius: 50px;
            padding: 7px 20px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .search-bar button:hover {
            transform: translateY(-1px);
            box-shadow: 0 4px 12px rgba(1, 65, 28, 0.3);
        }

        .header-actions {
            display: flex;
            gap: 0.5rem;
            align-items: center;
            flex-wrap: wrap;
        }

        .action-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
            background: none;
            border: none;
            color: var(--text-primary);
            cursor: pointer;
            transition: all 0.3s;
            font-size: 0.8rem;
            padding: 8px;
            border-radius: var(--radius);
            min-width: 70px;
            position: relative;
        }

        .action-btn i {
            font-size: 1.2rem;
            margin-bottom: 4px;
        }

        .action-btn:hover {
            color: var(--primary);
            background: rgba(1, 65, 28, 0.1);
            transform: translateY(-2px);
        }

        .seller-badge {
            background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-light-green));
            color: white;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 0.7rem;
            margin-left: 5px;
        }

        .cart-count, .notification-count {
            position: absolute;
            top: -5px;
            right: 0;
            background: var(--primary);
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.7rem;
            font-weight: bold;
        }

        .notification-count {
            background: var(--error);
        }

        .theme-toggle {
            background: none;
            border: none;
            color: var(--text-primary);
            cursor: pointer;
            font-size: 1.2rem;
            padding: 8px;
            border-radius: 50%;
            transition: all 0.3s;
        }

        .theme-toggle:hover {
            background: rgba(1, 65, 28, 0.1);
        }

        /* Premium Navigation */
        .main-nav {
            background: var(--white);
            border-top: 1px solid var(--border);
            overflow-x: auto;
            white-space: nowrap;
            -webkit-overflow-scrolling: touch;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 1rem;
            padding: 1rem 0;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-primary);
            font-weight: 500;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 5px;
            padding: 8px 16px;
            border-radius: var(--radius);
            white-space: nowrap;
        }

        .nav-links a:hover {
            color: var(--primary);
            background: rgba(1, 65, 28, 0.1);
        }

        /* Premium Hero Section - Pakistan Theme */
        .hero {
            margin: 2rem 0;
            border-radius: var(--radius-lg);
            overflow: hidden;
            box-shadow: var(--shadow-lg);
            position: relative;
            border: 3px solid var(--primary);
        }

        .hero-slider {
            position: relative;
            height: 400px;
        }

        .slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            transition: opacity 1s ease;
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            padding: 0 5%;
        }

        .slide.active {
            opacity: 1;
        }

        .slide-content {
            max-width: 500px;
            color: white;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
        }

        .slide-content h2 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            font-weight: 700;
        }

        .slide-content p {
            font-size: 1.1rem;
            margin-bottom: 2rem;
        }

        .btn {
            display: inline-block;
            padding: 12px 30px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
            border: none;
            cursor: pointer;
            font-size: 1rem;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-light-green));
            color: white;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(1, 65, 28, 0.3);
        }

        .btn-secondary {
            background: linear-gradient(135deg, var(--pakistan-black), #333);
            color: white;
        }

        .btn-secondary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(26, 26, 26, 0.3);
        }

        .btn-danger {
            background: linear-gradient(135deg, #E74C3C, #C0392B);
            color: white;
        }

        .btn-success {
            background: linear-gradient(135deg, #27AE60, #229954);
            color: white;
        }

        .btn-warning {
            background: linear-gradient(135deg, #F39C12, #D68910);
            color: white;
        }

        .btn-info {
            background: linear-gradient(135deg, #3498DB, #2980B9);
            color: white;
        }

        .btn-sm {
            padding: 8px 16px;
            font-size: 0.9rem;
        }

        /* Sections */
        .section {
            margin: 3rem 0;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .section-title {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--text-primary);
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 50px;
            height: 3px;
            background: var(--primary);
            border-radius: 2px;
        }

        .view-all {
            color: var(--primary);
            text-decoration: none;
            font-weight: 500;
            display: flex;
            align-items: center;
            gap: 5px;
            transition: all 0.3s;
        }

        .view-all:hover {
            transform: translateX(5px);
        }

        /* Categories Grid */
        .categories-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 1.5rem;
        }

        .category-card {
            background: var(--white);
            border-radius: var(--radius);
            padding: 1.5rem 1rem;
            text-align: center;
            box-shadow: var(--shadow);
            transition: all 0.3s;
            cursor: pointer;
            border: 1px solid var(--border);
            position: relative;
            overflow: hidden;
        }

        .category-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(135deg, var(--primary), var(--pakistan-light-green));
        }

        .category-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-lg);
            border-color: var(--primary);
        }

        .category-icon {
            font-size: 2rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .category-name {
            font-weight: 600;
            color: var(--text-primary);
        }

        /* Products Grid */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background: var(--white);
            border-radius: var(--radius);
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: all 0.3s;
            position: relative;
            border: 1px solid var(--border);
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-lg);
            border-color: var(--primary);
        }

        .product-badge {
            position: absolute;
            top: 10px;
            left: 10px;
            background: var(--primary);
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 0.8rem;
            font-weight: 600;
            z-index: 2;
        }

        .product-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
            transition: transform 0.3s;
        }

        .product-card:hover .product-image {
            transform: scale(1.05);
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-category {
            color: var(--text-secondary);
            font-size: 0.8rem;
            margin-bottom: 5px;
        }

        .product-name {
            font-weight: 600;
            margin-bottom: 0.5rem;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .product-rating {
            display: flex;
            align-items: center;
            gap: 5px;
            margin-bottom: 0.5rem;
            color: var(--warning);
        }

        .product-price {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 1rem;
        }

        .current-price {
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--primary);
        }

        .original-price {
            font-size: 1rem;
            color: var(--text-secondary);
            text-decoration: line-through;
        }

        .product-seller {
            font-size: 0.8rem;
            color: var(--text-secondary);
            margin-bottom: 1rem;
        }

        .product-actions {
            display: flex;
            gap: 10px;
        }

        .add-to-cart {
            flex: 1;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: 500;
            padding: 10px;
        }

        .add-to-cart:hover {
            background: var(--pakistan-light-green);
            transform: translateY(-1px);
        }

        /* Seller Registration */
        .seller-registration {
            padding: 3rem 0;
            min-height: calc(100vh - 200px);
        }

        .registration-steps {
            display: flex;
            justify-content: center;
            margin-bottom: 3rem;
            gap: 2rem;
            flex-wrap: wrap;
        }

        .step {
            display: flex;
            align-items: center;
            gap: 10px;
            color: var(--text-secondary);
        }

        .step.active {
            color: var(--primary);
        }

        .step-number {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background: var(--border);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
        }

        .step.active .step-number {
            background: var(--primary);
            color: white;
        }

        .seller-form-container {
            max-width: 800px;
            margin: 0 auto;
        }

        .form-step {
            display: none;
            animation: fadeIn 0.5s ease;
        }

        .form-step.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .glass-card {
            background: var(--glass);
            backdrop-filter: blur(10px);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-lg);
            padding: 2rem;
            box-shadow: var(--shadow-lg);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: var(--text-primary);
        }

        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid var(--border);
            border-radius: var(--radius);
            font-size: 1rem;
            transition: border 0.3s;
            background: var(--white);
            color: var(--text-primary);
        }

        .form-control:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(1, 65, 28, 0.1);
        }

        .form-row {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .form-row .form-group {
            flex: 1;
            margin-bottom: 0;
        }

        .password-input {
            position: relative;
        }

        .password-toggle {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            background: none;
            border: none;
            color: var(--text-secondary);
            cursor: pointer;
        }

        .otp-container {
            display: none;
        }

        .otp-container.active {
            display: block;
        }

        .otp-inputs {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin: 1rem 0;
        }

        .otp-input {
            width: 50px;
            height: 50px;
            text-align: center;
            font-size: 1.5rem;
            border: 2px solid var(--border);
            border-radius: var(--radius);
            background: var(--white);
            color: var(--text-primary);
        }

        .otp-input:focus {
            border-color: var(--primary);
            outline: none;
        }

        .form-actions {
            display: flex;
            justify-content: space-between;
            margin-top: 2rem;
            gap: 1rem;
        }

        /* Seller Panel */
        .seller-panel {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--background);
            z-index: 3000;
            overflow-y: auto;
        }

        .seller-header {
            background: var(--white);
            padding: 1rem 2rem;
            box-shadow: var(--shadow);
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 3px solid var(--primary);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .seller-main {
            display: flex;
            min-height: calc(100vh - 80px);
        }

        .seller-sidebar {
            width: 280px;
            background: var(--white);
            padding: 2rem 0;
            box-shadow: var(--shadow);
            border-right: 2px solid var(--border);
            position: sticky;
            top: 80px;
            height: calc(100vh - 80px);
            overflow-y: auto;
        }

        .seller-content {
            flex: 1;
            padding: 2rem;
            background: var(--accent);
            min-height: calc(100vh - 80px);
        }

        .seller-nav {
            list-style: none;
        }

        .seller-nav li {
            margin-bottom: 0.5rem;
        }

        .seller-nav a {
            display: block;
            padding: 1rem 2rem;
            color: var(--text-primary);
            text-decoration: none;
            transition: all 0.3s;
            border-left: 3px solid transparent;
        }

        .seller-nav a:hover,
        .seller-nav a.active {
            background: rgba(1, 65, 28, 0.1);
            border-left-color: var(--primary);
            color: var(--primary);
        }

        .seller-tab {
            display: none;
            animation: fadeIn 0.3s ease;
        }

        .seller-tab.active {
            display: block;
        }

        /* Dashboard Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .stat-card {
            background: var(--white);
            padding: 1.5rem;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            text-align: center;
            border-top: 4px solid var(--primary);
        }

        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }

        .stat-label {
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        /* Quick Actions */
        .quick-actions {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin: 2rem 0;
        }

        .quick-action-btn {
            background: var(--white);
            padding: 2rem;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            border: 2px solid transparent;
        }

        .quick-action-btn:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-lg);
            border-color: var(--primary);
        }

        .quick-action-icon {
            font-size: 3rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }

        /* Product Management */
        .product-management {
            background: var(--white);
            border-radius: var(--radius);
            padding: 2rem;
            box-shadow: var(--shadow);
        }

        .table-container {
            overflow-x: auto;
        }

        .product-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
        }

        .product-table th {
            background: var(--primary);
            color: white;
            padding: 1rem;
            text-align: left;
        }

        .product-table td {
            padding: 1rem;
            border-bottom: 1px solid var(--border);
        }

        .product-thumbnail {
            width: 60px;
            height: 60px;
            object-fit: cover;
            border-radius: var(--radius);
        }

        .status-badge {
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
        }

        .status-active {
            background: #d4edda;
            color: #155724;
        }

        .status-inactive {
            background: #f8d7da;
            color: #721c24;
        }

        .status-pending {
            background: #fff3cd;
            color: #856404;
        }

        /* Order Management */
        .order-card {
            background: var(--white);
            border-radius: var(--radius);
            padding: 1.5rem;
            margin-bottom: 1rem;
            box-shadow: var(--shadow);
            border-left: 4px solid var(--primary);
        }

        .order-locked {
            position: relative;
        }

        .order-locked::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(255, 255, 255, 0.9);
            z-index: 1;
            border-radius: var(--radius);
        }

        .order-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 1rem;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .order-items {
            margin: 1rem 0;
        }

        .order-item {
            display: flex;
            gap: 1rem;
            padding: 1rem 0;
            border-bottom: 1px solid var(--border);
        }

        .order-item:last-child {
            border-bottom: none;
        }

        .order-item-image {
            width: 80px;
            height: 80px;
            object-fit: cover;
            border-radius: var(--radius);
        }

        .order-actions {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
            flex-wrap: wrap;
        }

        .unlock-order-btn {
            position: relative;
            z-index: 2;
            background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-light-green));
            color: white;
            padding: 10px 20px;
            border-radius: var(--radius);
            border: none;
            cursor: pointer;
            font-weight: 500;
        }

        .unlock-order-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(1, 65, 28, 0.3);
        }

        /* Payment Verification Modal */
        .payment-verification {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 4000;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }

        .payment-verification.active {
            display: flex;
        }

        .verification-content {
            background: var(--white);
            padding: 2rem;
            border-radius: var(--radius-lg);
            max-width: 500px;
            width: 100%;
            box-shadow: var(--shadow-lg);
        }

        /* Invoice Modal */
        .invoice-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 4000;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }

        .invoice-modal.active {
            display: flex;
        }

        .invoice-content {
            background: var(--white);
            padding: 2rem;
            border-radius: var(--radius-lg);
            max-width: 800px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: var(--shadow-lg);
        }

        .invoice-header {
            text-align: center;
            margin-bottom: 2rem;
            border-bottom: 3px solid var(--primary);
            padding-bottom: 1rem;
        }

        .invoice-details {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .invoice-table {
            width: 100%;
            border-collapse: collapse;
            margin: 2rem 0;
        }

        .invoice-table th {
            background: var(--accent);
            padding: 1rem;
            text-align: left;
        }

        .invoice-table td {
            padding: 1rem;
            border-bottom: 1px solid var(--border);
        }

        .invoice-total {
            text-align: right;
            padding: 1rem;
            background: var(--accent);
            border-radius: var(--radius);
            margin-top: 2rem;
        }

        /* Toast Notifications */
        .toast-container {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 5000;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .toast {
            background: var(--white);
            padding: 1rem 1.5rem;
            border-radius: var(--radius);
            box-shadow: var(--shadow-lg);
            display: flex;
            align-items: center;
            gap: 10px;
            transform: translateX(400px);
            transition: transform 0.3s ease;
            border-left: 4px solid var(--primary);
        }

        .toast.show {
            transform: translateX(0);
        }

        .toast.success {
            border-left-color: var(--success);
        }

        .toast.error {
            border-left-color: var(--error);
        }

        .toast.info {
            border-left-color: var(--primary);
        }

        .toast.warning {
            border-left-color: var(--warning);
        }

        /* Chat Support */
        .chat-support {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1000;
        }

        .chat-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-light-green));
            color: white;
            border: none;
            cursor: pointer;
            box-shadow: var(--shadow-lg);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            transition: all 0.3s;
        }

        .chat-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 8px 25px rgba(1, 65, 28, 0.3);
        }

        /* Loading Spinner */
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255,255,255,.3);
            border-radius: 50%;
            border-top-color: var(--primary);
            animation: spin 1s ease-in-out infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 4000;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: var(--white);
            padding: 2rem;
            border-radius: var(--radius-lg);
            max-width: 500px;
            width: 100%;
            box-shadow: var(--shadow-lg);
        }

        /* Notification Panel */
        .notification-panel {
            position: fixed;
            top: 80px;
            right: 20px;
            width: 350px;
            background: var(--white);
            border-radius: var(--radius);
            box-shadow: var(--shadow-lg);
            z-index: 999;
            display: none;
            max-height: 400px;
            overflow-y: auto;
        }

        .notification-panel.active {
            display: block;
            animation: slideDown 0.3s ease;
        }

        @keyframes slideDown {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .notification-header {
            padding: 1rem;
            border-bottom: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .notification-item {
            padding: 1rem;
            border-bottom: 1px solid var(--border);
            transition: background 0.3s;
        }

        .notification-item:hover {
            background: var(--accent);
        }

        .notification-item.unread {
            background: rgba(1, 65, 28, 0.05);
        }

        /* User Menu */
        .user-menu {
            position: fixed;
            top: 80px;
            right: 20px;
            width: 250px;
            background: var(--white);
            border-radius: var(--radius);
            box-shadow: var(--shadow-lg);
            z-index: 999;
            display: none;
        }

        .user-menu.active {
            display: block;
            animation: slideDown 0.3s ease;
        }

        .user-menu-item {
            padding: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
            text-decoration: none;
            color: var(--text-primary);
            transition: background 0.3s;
        }

        .user-menu-item:hover {
            background: var(--accent);
        }

        /* Auth Modal Styles */
        .auth-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 4000;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }

        .auth-modal.active {
            display: flex;
        }

        .auth-tabs {
            display: flex;
            border-bottom: 2px solid var(--border);
            margin-bottom: 2rem;
        }

        .auth-tab {
            flex: 1;
            padding: 1rem;
            text-align: center;
            cursor: pointer;
            font-weight: 500;
            border-bottom: 3px solid transparent;
        }

        .auth-tab.active {
            border-bottom-color: var(--primary);
            color: var(--primary);
        }

        .auth-form {
            display: none;
        }

        .auth-form.active {
            display: block;
        }

        /* Buyer Profile Form */
        .buyer-profile-form {
            padding: 2rem;
            background: var(--white);
            border-radius: var(--radius-lg);
            box-shadow: var(--shadow);
        }

        .profile-field {
            margin-bottom: 1rem;
        }

        .profile-field label {
            display: block;
            font-weight: 500;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
        }

        .profile-field .field-value {
            padding: 0.8rem;
            background: var(--accent);
            border-radius: var(--radius);
            border: 1px solid var(--border);
        }

        /* Forgot Password Modal */
        .forgot-password-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 4000;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }

        .forgot-password-modal.active {
            display: flex;
        }

        /* Progress Bar */
        .tracking-progress {
            margin: 2rem 0;
        }

        .progress-steps {
            display: flex;
            justify-content: space-between;
            position: relative;
        }

        .progress-steps::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            height: 2px;
            background: var(--border);
            transform: translateY(-50%);
            z-index: 1;
        }

        .progress-bar {
            position: absolute;
            top: 50%;
            left: 0;
            height: 2px;
            background: var(--primary);
            transform: translateY(-50%);
            z-index: 2;
            transition: width 0.3s;
        }

        .step {
            display: flex;
            flex-direction: column;
            align-items: center;
            position: relative;
            z-index: 3;
            width: 100px;
        }

        .step-circle {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--white);
            border: 2px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 0.5rem;
            font-weight: 600;
            transition: all 0.3s;
        }

        .step.active .step-circle {
            background: var(--primary);
            border-color: var(--primary);
            color: white;
        }

        .step.completed .step-circle {
            background: var(--success);
            border-color: var(--success);
            color: white;
        }

        .step-label {
            font-size: 0.9rem;
            text-align: center;
        }

        /* Order Tracking */
        .tracking-card {
            background: var(--white);
            border-radius: var(--radius);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            box-shadow: var(--shadow);
            border-left: 4px solid var(--primary);
        }

        .tracking-timeline {
            margin-top: 1.5rem;
            padding-left: 1rem;
            border-left: 2px solid var(--border);
        }

        .timeline-item {
            margin-bottom: 1.5rem;
            position: relative;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -1.5rem;
            top: 0;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: var(--primary);
        }

        .timeline-date {
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        .timeline-content {
            margin-top: 0.25rem;
        }

        /* Settings Page */
        .settings-tabs {
            display: flex;
            border-bottom: 2px solid var(--border);
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .settings-tab {
            padding: 1rem 1.5rem;
            cursor: pointer;
            font-weight: 500;
            border-bottom: 3px solid transparent;
        }

        .settings-tab.active {
            border-bottom-color: var(--primary);
            color: var(--primary);
        }

        .settings-content {
            background: var(--white);
            border-radius: var(--radius);
            padding: 2rem;
            box-shadow: var(--shadow);
        }

        /* Order Status Badges */
        .order-status-badge {
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
            display: inline-block;
        }

        .status-pending-badge {
            background: #fff3cd;
            color: #856404;
        }

        .status-approved-badge {
            background: #d1ecf1;
            color: #0c5460;
        }

        .status-shipped-badge {
            background: #d4edda;
            color: #155724;
        }

        .status-delivered-badge {
            background: #28a745;
            color: white;
        }

        .status-cancelled-badge {
            background: #f8d7da;
            color: #721c24;
        }

        .status-locked-badge {
            background: #6c757d;
            color: white;
        }

        /* Message System */
        .message-system {
            background: var(--white);
            border-radius: var(--radius);
            padding: 2rem;
            box-shadow: var(--shadow);
            height: 600px;
            display: flex;
            flex-direction: column;
        }

        .chat-container {
            display: flex;
            flex: 1;
            border: 1px solid var(--border);
            border-radius: var(--radius);
            overflow: hidden;
        }

        .chat-sidebar {
            width: 300px;
            border-right: 1px solid var(--border);
            display: flex;
            flex-direction: column;
        }

        .chat-list {
            flex: 1;
            overflow-y: auto;
        }

        .chat-item {
            padding: 1rem;
            border-bottom: 1px solid var(--border);
            cursor: pointer;
            transition: background 0.3s;
        }

        .chat-item:hover, .chat-item.active {
            background: var(--accent);
        }

        .chat-content {
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .chat-header {
            padding: 1rem;
            border-bottom: 1px solid var(--border);
            background: var(--accent);
        }

        .chat-messages {
            flex: 1;
            padding: 1rem;
            overflow-y: auto;
        }

        .message {
            margin-bottom: 1rem;
            max-width: 70%;
        }

        .message.sent {
            margin-left: auto;
            background: var(--primary);
            color: white;
            padding: 0.75rem 1rem;
            border-radius: var(--radius);
            border-top-right-radius: 0;
        }

        .message.received {
            margin-right: auto;
            background: var(--accent);
            padding: 0.75rem 1rem;
            border-radius: var(--radius);
            border-top-left-radius: 0;
        }

        .chat-input {
            padding: 1rem;
            border-top: 1px solid var(--border);
            display: flex;
            gap: 0.5rem;
        }

        .chat-input input {
            flex: 1;
            padding: 0.75rem;
            border: 1px solid var(--border);
            border-radius: var(--radius);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
            }
            
            .search-bar {
                width: 100%;
                min-width: unset;
            }
            
            .header-actions {
                width: 100%;
                justify-content: center;
            }
            
            .seller-main {
                flex-direction: column;
            }
            
            .seller-sidebar {
                width: 100%;
                height: auto;
                position: static;
            }
            
            .seller-content {
                padding: 1rem;
            }
            
            .form-row {
                flex-direction: column;
                gap: 0;
            }
            
            .form-row .form-group {
                margin-bottom: 1.5rem;
            }
            
            .products-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
            
            .categories-grid {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            }
            
            .hero-slider {
                height: 300px;
            }
            
            .slide-content h2 {
                font-size: 2rem;
            }
            
            .progress-steps {
                flex-wrap: wrap;
            }
            
            .step {
                width: 80px;
                margin-bottom: 1rem;
            }
            
            .chat-container {
                flex-direction: column;
            }
            
            .chat-sidebar {
                width: 100%;
                height: 200px;
            }
        }

        @media (max-width: 480px) {
            .products-grid {
                grid-template-columns: 1fr;
            }
            
            .categories-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .header-actions .action-btn span {
                display: none;
            }
            
            .header-actions .action-btn {
                min-width: 50px;
            }
            
            .otp-input {
                width: 40px;
                height: 40px;
            }
            
            .settings-tabs {
                flex-direction: column;
            }
            
            .settings-tab {
                padding: 0.75rem;
            }
        }

        /* Image Slider */
        .product-image-slider {
            position: relative;
            width: 100%;
            height: 400px;
            overflow: hidden;
            border-radius: var(--radius);
        }

        .slider-image {
            width: 100%;
            height: 100%;
            object-fit: contain;
            background: var(--accent);
            display: none;
        }

        .slider-image.active {
            display: block;
        }

        .slider-nav {
            position: absolute;
            bottom: 20px;
            left: 0;
            right: 0;
            display: flex;
            justify-content: center;
            gap: 10px;
        }

        .slider-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: rgba(255,255,255,0.5);
            cursor: pointer;
            transition: background 0.3s;
        }

        .slider-dot.active {
            background: var(--primary);
        }

        .zoom-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 5000;
            display: none;
            align-items: center;
            justify-content: center;
        }

        .zoom-overlay.active {
            display: flex;
        }

        .zoomed-image {
            max-width: 90%;
            max-height: 90%;
            object-fit: contain;
        }

        /* Skeleton Loaders */
        .skeleton {
            background: linear-gradient(90deg, var(--accent) 25%, var(--border) 50%, var(--accent) 75%);
            background-size: 200% 100%;
            animation: loading 1.5s infinite;
            border-radius: var(--radius);
        }

        @keyframes loading {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }

        .skeleton-product {
            height: 350px;
            margin-bottom: 1rem;
        }

        .skeleton-text {
            height: 20px;
            margin-bottom: 10px;
        }

        .skeleton-text.short {
            width: 60%;
        }

        /* Pagination */
        .pagination {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 2rem;
            flex-wrap: wrap;
        }

        .page-btn {
            width: 40px;
            height: 40px;
            border-radius: var(--radius);
            border: 1px solid var(--border);
            background: var(--white);
            color: var(--text-primary);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
        }

        .page-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        .page-btn:hover:not(.active) {
            background: var(--accent);
        }

        /* Admin Panel */
        .admin-panel {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--background);
            z-index: 3000;
            overflow-y: auto;
        }

        .admin-tab {
            display: none;
            padding: 2rem;
        }

        .admin-tab.active {
            display: block;
        }

        /* Dispute Resolution */
        .dispute-card {
            background: var(--white);
            border-radius: var(--radius);
            padding: 1.5rem;
            margin-bottom: 1rem;
            box-shadow: var(--shadow);
            border-left: 4px solid var(--warning);
        }

        /* Refund System */
        .refund-request {
            background: var(--white);
            border-radius: var(--radius);
            padding: 1.5rem;
            margin-bottom: 1rem;
            box-shadow: var(--shadow);
            border: 2px solid var(--error);
        }

        /* Fraud Detection */
        .fraud-alert {
            background: linear-gradient(135deg, #ff6b6b, #c92a2a);
            color: white;
            padding: 1rem;
            border-radius: var(--radius);
            margin-bottom: 1rem;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.8; }
            100% { opacity: 1; }
        }

        /* QR Code Display */
        .qr-container {
            text-align: center;
            padding: 2rem;
            background: var(--white);
            border-radius: var(--radius);
            box-shadow: var(--shadow);
        }

        .qr-code {
            width: 200px;
            height: 200px;
            margin: 1rem auto;
            border: 1px solid var(--border);
            padding: 10px;
            background: white;
        }

        /* Payment Proof */
        .payment-proof {
            width: 100%;
            max-width: 300px;
            border-radius: var(--radius);
            border: 2px solid var(--primary);
        }
        
        /* Image Preview Styles */
        .image-preview {
            position: relative;
            width: 100px;
            height: 100px;
            border-radius: var(--radius);
            overflow: hidden;
            border: 2px solid var(--border);
        }
        
        .image-preview img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .remove-image {
            position: absolute;
            top: 5px;
            right: 5px;
            background: var(--error);
            color: white;
            border: none;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 12px;
        }

        /* Enhanced Product Image Slider */
        .enhanced-slider {
            position: relative;
            height: 500px;
            border-radius: var(--radius-lg);
            overflow: hidden;
            background: var(--accent);
            margin-bottom: 1rem;
        }

        .slider-container {
            width: 100%;
            height: 100%;
            position: relative;
        }

        .slider-item {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            transition: opacity 0.5s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            background: var(--white);
        }

        .slider-item.active {
            opacity: 1;
            z-index: 2;
        }

        .slider-item img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
            padding: 10px;
        }

        .slider-item video {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
            background: black;
        }

        .video-indicator {
            position: absolute;
            top: 15px;
            right: 15px;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            z-index: 3;
        }

        .video-indicator i {
            margin-right: 5px;
            color: var(--info);
        }

        /* Navigation Controls */
        .slider-nav-controls {
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            transform: translateY(-50%);
            display: flex;
            justify-content: space-between;
            padding: 0 20px;
            z-index: 10;
        }

        .nav-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.9);
            border: 2px solid var(--primary);
            color: var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 1.2rem;
            box-shadow: var(--shadow);
        }

        .nav-btn:hover {
            background: var(--primary);
            color: white;
            transform: scale(1.1);
        }

        /* Thumbnail Navigation */
        .thumbnail-nav {
            display: flex;
            gap: 10px;
            overflow-x: auto;
            padding: 10px 0;
            margin-top: 1rem;
            scrollbar-width: thin;
        }

        .thumbnail-item {
            flex: 0 0 auto;
            width: 80px;
            height: 80px;
            border-radius: var(--radius);
            overflow: hidden;
            cursor: pointer;
            border: 3px solid transparent;
            position: relative;
            transition: all 0.3s;
        }

        .thumbnail-item.active {
            border-color: var(--primary);
            transform: scale(1.05);
        }

        .thumbnail-item:hover {
            transform: scale(1.05);
        }

        .thumbnail-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .thumbnail-item.video-thumb::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
        }

        .thumbnail-item.video-thumb::after {
            content: '▶';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: white;
            font-size: 1.2rem;
            text-shadow: 0 2px 5px rgba(0,0,0,0.5);
        }

        /* Share Button Styles */
        .share-container {
            position: relative;
            display: inline-block;
        }

        .share-dropdown {
            position: absolute;
            top: 100%;
            right: 0;
            background: var(--white);
            border-radius: var(--radius);
            box-shadow: var(--shadow-lg);
            padding: 1rem;
            min-width: 300px;
            z-index: 1000;
            display: none;
            margin-top: 10px;
        }

        .share-dropdown.active {
            display: block;
            animation: slideDown 0.3s ease;
        }

        .share-options {
            display: flex;
            gap: 10px;
            margin: 1rem 0;
        }

        .share-btn {
            flex: 1;
            padding: 10px;
            border-radius: var(--radius);
            border: 1px solid var(--border);
            background: var(--white);
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
        }

        .share-btn:hover {
            background: var(--accent);
            transform: translateY(-2px);
        }

        .share-btn.facebook { color: #1877F2; }
        .share-btn.whatsapp { color: #25D366; }
        .share-btn.twitter { color: #1DA1F2; }
        .share-btn.copy { color: var(--primary); }

        .share-btn i {
            font-size: 1.5rem;
        }

        .share-link {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--border);
            border-radius: var(--radius);
            background: var(--accent);
            word-break: break-all;
            font-size: 0.9rem;
            margin-top: 1rem;
        }

        /* Product Card Enhancements */
        .product-card .video-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: var(--info);
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 0.8rem;
            z-index: 2;
        }

        .product-card .image-count {
            position: absolute;
            top: 10px;
            left: 10px;
            background: rgba(0,0,0,0.7);
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 0.8rem;
            z-index: 2;
        }
        
        /* Animation for share dropdown */
@keyframes slideDown {
    from {
        opacity: 0;
        transform: translateY(-10px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
} /* ADD THIS CLOSING BRACE */

/* Order Status Dropdown */
.status-dropdown {
            padding: 8px 12px;
            border-radius: var(--radius);
            border: 1px solid var(--border);
            background: var(--white);
            color: var(--text-primary);
            font-size: 0.9rem;
            cursor: pointer;
            min-width: 150px;
        }

        .status-dropdown:focus {
            outline: none;
            border-color: var(--primary);
        }

        /* Star Rating */
        .star-rating {
            display: flex;
            gap: 5px;
            cursor: pointer;
        }

        .star-rating i {
            font-size: 1.5rem;
            color: var(--border);
        }

        .star-rating i.active {
            color: var(--warning);
        }

        /* Payment Lock Badge */
        .payment-lock-badge {
            background: linear-gradient(135deg, #6c757d, #495057);
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 0.8rem;
            font-weight: 600;
            display: inline-block;
        }
        /* Enhanced Filter & Sort Styles */
        .filter-section h3 {
            color: var(--primary);
            margin-bottom: 1.5rem;
            font-size: 1.3rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

                 /* ============ FILTER SECTION STYLES - FIXED ============ */
        .filter-section {
            background: var(--white);
            padding: 2rem;
            border-radius: var(--radius-lg);
            box-shadow: var(--shadow-lg);
            margin-bottom: 2rem;
            border: 2px solid var(--primary-light);
        }

        .filter-section h3 {
            color: var(--primary);
            margin-bottom: 1.5rem;
            font-size: 1.5rem;
            display: flex;
            align-items: center;
            gap: 10px;
            padding-bottom: 1rem;
            border-bottom: 2px solid var(--border);
        }

        .filter-section h3 i {
            color: var(--primary);
        }

        .filter-row {
            display: flex;
            align-items: center;
            gap: 1.5rem;
            flex-wrap: wrap;
            padding: 1rem 0;
        }

        .filter-row > div:first-child {
            font-weight: 600;
            color: var(--primary);  /* CHANGED TO PRIMARY */
            min-width: 80px;
            font-size: 1.1rem;
        }

        .sort-options {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            flex: 1;
        }

        .sort-btn {
            padding: 12px 24px;
            border-radius: 50px;
            border: 2px solid var(--primary);
            background: white;
            color: var(--primary);  /* GREEN TEXT */
            cursor: pointer;
            transition: all 0.3s;
            font-weight: 600;
            font-size: 1rem;
            display: flex;
            align-items: center;
            gap: 8px;
            white-space: nowrap;
        }

        .sort-btn i {
            color: var(--primary);  /* GREEN ICONS */
            font-size: 1rem;
        }

        .sort-btn:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow);
            border-color: var(--primary);
            background: var(--primary);
            color: white;
        }

        .sort-btn:hover i {
            color: white;
        }

        .sort-btn.active {
            background: linear-gradient(135deg, var(--primary), var(--pakistan-light-green));
            color: white;
            border-color: var(--primary);
            box-shadow: 0 5px 15px rgba(1, 65, 28, 0.3);
        }

        .sort-btn.active i {
            color: white;
        }

        .btn-secondary {
            padding: 12px 24px;
            border-radius: 50px;
            background: var(--accent);
            border: 2px solid var(--primary);
            color: var(--primary);  /* GREEN TEXT */
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 1rem;
        }

        .btn-secondary i {
            color: var(--primary);  /* GREEN ICONS */
        }

        .btn-secondary:hover {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
            transform: translateY(-3px);
        }

        .btn-secondary:hover i {
            color: white;
        }

        .advanced-filter {
            display: none;
            margin-top: 1.5rem;
            padding-top: 1.5rem;
            border-top: 2px solid var(--border);
            animation: fadeIn 0.3s ease;
        }

        .advanced-filter.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .filter-group {
            margin-bottom: 1.5rem;
        }

        .filter-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--primary);  /* GREEN LABELS */
            font-size: 1.1rem;
        }

        .filter-group label i {
            color: var(--primary);  /* GREEN ICONS */
        }

        .price-range {
            display: flex;
            align-items: center;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .price-range input {
            width: 150px;
            padding: 12px;
            border: 2px solid var(--primary);
            border-radius: var(--radius);
            background: var(--white);
            color: var(--primary);  /* GREEN TEXT */
            font-weight: 600;
            font-size: 1rem;
        }

        .price-range input:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(1, 65, 28, 0.2);
        }

        .price-range span {
            color: var(--primary);  /* GREEN TEXT */
            font-weight: 600;
            font-size: 1.1rem;
        }

        select.form-control {
            width: 100%;
            padding: 12px;
            border: 2px solid var(--primary);
            border-radius: var(--radius);
            background: var(--white);
            color: var(--primary);  /* GREEN TEXT */
            cursor: pointer;
            font-weight: 600;
            font-size: 1rem;
        }

        select.form-control:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(1, 65, 28, 0.2);
        }

        .btn-sm {
            padding: 10px 20px;
            font-size: 0.95rem;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary), var(--pakistan-light-green));
            color: white;
            padding: 12px 30px;
            border-radius: 50px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            font-size: 1rem;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .btn-primary i {
            color: white;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(1, 65, 28, 0.3);
        }

        /* Messages Badge */
        .messages-badge {
            position: absolute;
            top: -5px;
            right: 0;
            background: var(--info);
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.7rem;
            font-weight: bold;
        }

        /* Video Preview */
        .video-preview {
            position: relative;
            width: 100px;
            height: 100px;
            border-radius: var(--radius);
            overflow: hidden;
            border: 2px solid var(--border);
            background: var(--accent);
        }
        
        .video-preview video {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .remove-video {
            position: absolute;
            top: 5px;
            right: 5px;
            background: var(--error);
            color: white;
            border: none;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 12px;
        }

        .advanced-filter {
    display: none;
    animation: fadeIn 0.3s ease;
    background: var(--accent);
    padding: 1.5rem;
    border-radius: var(--radius);
    margin-top: 1rem;
    border: 1px solid var(--border);
}

.advanced-filter.active {
    display: block;
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(-10px); }
    to { opacity: 1; transform: translateY(0); }
}
        .filter-group {
            margin-bottom: 1rem;
        }
        
        .filter-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }
        
        .price-range {
            display: flex;
            gap: 1rem;
            align-items: center;
        }
        
        .price-range input {
            flex: 1;
        }

        

        /* Message Button on Product */
        .message-seller-btn {
            position: absolute;
            bottom: 10px;
            right: 10px;
            background: var(--info);
            color: white;
            border: none;
            border-radius: 50%;
            width: 36px;
            height: 36px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 2;
        }

        /* Withdrawal Management */
        .withdrawal-card {
            background: var(--white);
            border-radius: var(--radius);
            padding: 1.5rem;
            margin-bottom: 1rem;
            box-shadow: var(--shadow);
            border-left: 4px solid var(--warning);
        }

        /* Invoice Lock */
        .invoice-lock {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(0,0,0,0.8);
            color: white;
            padding: 2rem;
            border-radius: var(--radius);
            text-align: center;
            z-index: 10;
        }

        /* Date Range Filter */
        .date-range-filter {
            display: flex;
            gap: 1rem;
            align-items: center;
            flex-wrap: wrap;
        }

        /* Review Images */
        .review-images {
            display: flex;
            gap: 10px;
            margin-top: 10px;
            flex-wrap: wrap;
        }

        .review-image {
            width: 100px;
            height: 100px;
            object-fit: cover;
            border-radius: var(--radius);
            cursor: pointer;
        }

        /* Admin Message System */
        .admin-message-system {
            height: 700px;
        }

        /* Tax Invoice Lock */
        .tax-invoice-lock {
            background: linear-gradient(135deg, #ff6b6b, #c92a2a);
            color: white;
            padding: 1rem;
            border-radius: var(--radius);
            margin: 1rem 0;
            text-align: center;
        }

        /* Withdrawal Status Badges */
        .withdrawal-status-pending {
            background: #fff3cd;
            color: #856404;
        }

        .withdrawal-status-approved {
            background: #d4edda;
            color: #155724;
        }

        .withdrawal-status-rejected {
            background: #f8d7da;
            color: #721c24;
        }

        .withdrawal-status-completed {
            background: #28a745;
            color: white;
        }

        /* File Upload Preview */
        .file-upload-preview {
            display: flex;
            gap: 10px;
            margin-top: 10px;
            flex-wrap: wrap;
        }

        .file-preview {
            position: relative;
            width: 100px;
            border-radius: var(--radius);
            overflow: hidden;
        }

        .file-preview img {
            width: 100%;
            height: 100px;
            object-fit: cover;
        }

        .file-preview video {
            width: 100%;
            height: 100px;
            object-fit: cover;
        }

        .remove-file {
            position: absolute;
            top: 5px;
            right: 5px;
            background: var(--error);
            color: white;
            border: none;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 10px;
        }

        /* Category Specific Form */
        .category-options {
            display: none;
            margin-top: 1rem;
            padding: 1rem;
            background: var(--accent);
            border-radius: var(--radius);
        }

        .category-options.active {
            display: block;
        }

        .option-group {
            margin-bottom: 1rem;
        }

        .option-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }

        .option-row {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .option-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        /* Enhanced Product Image Slider with Video */
        .enhanced-slider {
            position: relative;
            height: 500px;
            border-radius: var(--radius-lg);
            overflow: hidden;
            background: var(--accent);
            margin-bottom: 1rem;
        }

        .slider-container {
            width: 100%;
            height: 100%;
            position: relative;
        }

        .slider-item {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            transition: opacity 0.5s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            background: var(--white);
        }

        .slider-item.active {
            opacity: 1;
            z-index: 2;
        }

        .slider-item img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
            padding: 10px;
        }

        .slider-item video {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
            background: black;
        }

        .video-indicator {
            position: absolute;
            top: 15px;
            right: 15px;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            z-index: 3;
        }

        .video-indicator i {
            margin-right: 5px;
            color: var(--info);
        }

        /* Navigation Arrows */
        .slider-nav-controls {
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            transform: translateY(-50%);
            display: flex;
            justify-content: space-between;
            padding: 0 20px;
            z-index: 10;
        }

        .nav-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.9);
            border: 2px solid var(--primary);
            color: var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 1.2rem;
            box-shadow: var(--shadow);
        }

        .nav-btn:hover {
            background: var(--primary);
            color: white;
            transform: scale(1.1);
        }

        /* Thumbnail Navigation */
        .thumbnail-nav {
            display: flex;
            gap: 10px;
            overflow-x: auto;
            padding: 10px 0;
            margin-top: 1rem;
            scrollbar-width: thin;
        }

        .thumbnail-item {
            flex: 0 0 auto;
            width: 80px;
            height: 80px;
            border-radius: var(--radius);
            overflow: hidden;
            cursor: pointer;
            border: 3px solid transparent;
            position: relative;
            transition: all 0.3s;
        }

        .thumbnail-item.active {
            border-color: var(--primary);
            transform: scale(1.05);
        }

        .thumbnail-item:hover {
            transform: scale(1.05);
        }

        .thumbnail-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .thumbnail-item.video-thumb::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.3);
        }

        .thumbnail-item.video-thumb::after {
            content: '▶';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: white;
            font-size: 1.2rem;
            text-shadow: 0 2px 5px rgba(0,0,0,0.5);
        }
      
      <style>
./* Media Slider Styles */
.product-media-slider {
    position: relative;
    width: 100%;
    height: 400px;
    overflow: hidden;
    border-radius: var(--radius);
    background: var(--card-bg);
}

.slider-media-container {
    position: relative;
    width: 100%;
    height: 100%;
}

.slider-media {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
    transition: opacity 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--card-bg);
}

.slider-media.active {
    opacity: 1;
    z-index: 1;
}

.slider-media-item {
    max-width: 100%;
    max-height: 100%;
    object-fit: contain;
}

/* Slider Controls */
.slider-controls {
    position: absolute;
    top: 50%;
    left: 0;
    right: 0;
    transform: translateY(-50%);
    display: flex;
    justify-content: space-between;
    padding: 0 1rem;
    z-index: 10;
}

.slider-btn {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: rgba(0, 0, 0, 0.5);
    color: white;
    border: none;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.2s;
}

.slider-btn:hover {
    background: rgba(0, 0, 0, 0.8);
}

/* Slider Navigation Dots */
.slider-nav {
    position: absolute;
    bottom: 20px;
    left: 0;
    right: 0;
    display: flex;
    justify-content: center;
    gap: 10px;
    z-index: 10;
}

.slider-dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.5);
    cursor: pointer;
    transition: all 0.2s;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 8px;
    color: #fff;
}

.slider-dot.active {
    background: var(--primary);
    transform: scale(1.2);
}

/* Media Counter */
.media-counter {
    position: absolute;
    top: 20px;
    right: 20px;
    background: rgba(0, 0, 0, 0.7);
    color: white;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 14px;
    z-index: 10;
}
        <style>
        .badge-flash {
    background: #ff4757;
    color: white;
    padding: 2px 6px;
    border-radius: 4px;
    font-size: 0.7rem;
    font-weight: bold;
}
.old-price {
    text-decoration: line-through;
    color: #a4b0be;
    font-size: 0.8rem;
    margin-left: 5px;
}
<style>
/* Order Lock Styles */
.order-locked-overlay {
    background: #fff9e6;
    border: 2px dashed var(--warning);
    border-radius: var(--radius);
    padding: 20px;
    text-align: center;
    margin-bottom: 15px;
}
.blurred-info {
    filter: blur(5px);
    pointer-events: none;
    user-select: none;
}
.payment-icons img {
    width: 50px;
    margin: 10px;
    cursor: pointer;
    border-radius: 8px;
}
.payment-form {
    background: var(--white);
    padding: 15px;
    border-radius: var(--radius);
    margin-top: 15px;
    box-shadow: var(--shadow);
}
<style>
/* Seller Storefront Styles */
.seller-store-header {
    background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-dark-green));
    color: white;
    padding: 40px 0;
    margin-bottom: 30px;
    border-radius: 0 0 20px 20px;
}

.store-info-card {
    background: var(--white);
    border-radius: var(--radius-lg);
    padding: 20px;
    margin-top: -60px;
    box-shadow: var(--shadow-lg);
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 1px solid var(--border);
}

.store-profile-img {
    width: 80px;
    height: 80px;
    background: var(--accent);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    color: var(--primary);
    border: 3px solid var(--white);
}

.store-filters {
    background: var(--white);
    padding: 15px;
    border-radius: var(--radius);
    margin-bottom: 20px;
    display: flex;
    gap: 15px;
    align-items: center;
    border: 1px solid var(--border);
}

<style>
/* Custom Styles for Notifications */
#notificationsListFull {
    display: flex;
    flex-direction: column;
    gap: 15px; /* Adds space between lines */
    padding-bottom: 50px;
}

.notif-item {
    display: flex;
    align-items: center;
    gap: 15px;
    padding: 1.2rem;
    background: var(--white);
    border-radius: var(--radius);
    border: 1px solid var(--border);
    transition: transform 0.2s;
}

.notif-item.unread {
    border-left: 5px solid var(--primary); /* Green line for new ones */
    background: #f0fdf4;
}

.notif-icon {
    width: 45px;
    height: 45px;
    background: var(--primary-light);
    color: var(--primary);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
}
<style>
/* ==================== FOLLOWED STORES SECTION ==================== */
.followed-stores-section {
    margin: 3rem 0;
}

.followed-stores-container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    margin-top: 1.5rem;
}

.followed-store-item {
    display: flex;
    align-items: center;
    gap: 1.5rem;
    padding: 1.2rem 1.5rem;
    background: var(--white);
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow);
    border: 1px solid var(--border);
    transition: all 0.3s;
    cursor: pointer;
    position: relative;
    border-left: 4px solid var(--primary);
}

.followed-store-item:hover {
    transform: translateY(-3px);
    box-shadow: var(--shadow-lg);
    border-color: var(--primary);
}

.followed-store-item::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 4px;
    height: 100%;
    background: linear-gradient(135deg, var(--primary), var(--pakistan-light-green));
    border-radius: var(--radius) 0 0 var(--radius);
}

.store-avatar {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--primary), var(--pakistan-light-green));
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 1.5rem;
    flex-shrink: 0;
}

.store-avatar img {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    object-fit: cover;
}

.store-info {
    flex: 1;
}

.store-name {
    font-weight: 600;
    color: var(--text-primary);
    margin-bottom: 0.25rem;
    font-size: 1.1rem;
}

.store-meta {
    display: flex;
    gap: 1rem;
    align-items: center;
    margin-top: 0.5rem;
    font-size: 0.9rem;
    color: var(--text-secondary);
}

.store-meta-item {
    display: flex;
    align-items: center;
    gap: 5px;
}

.store-meta-item i {
    color: var(--primary);
}

.store-action {
    display: flex;
    gap: 0.5rem;
}

.follow-btn {
    padding: 8px 16px;
    border-radius: 50px;
    border: none;
    cursor: pointer;
    font-weight: 500;
    font-size: 0.9rem;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: all 0.3s;
    min-width: 100px;
}

.follow-btn.following {
    background: linear-gradient(135deg, var(--primary), var(--pakistan-light-green));
    color: white;
}

.follow-btn.following:hover {
    background: linear-gradient(135deg, var(--pakistan-light-green), var(--primary));
}

.follow-btn.not-following {
    background: var(--white);
    border: 2px solid var(--primary);
    color: var(--primary);
}

.follow-btn.not-following:hover {
    background: var(--primary);
    color: white;
}

.unfollow-btn {
    background: var(--error);
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 50px;
    cursor: pointer;
    font-size: 0.9rem;
    display: flex;
    align-items: center;
    gap: 5px;
}

.unfollow-btn:hover {
    background: #c0392b;
    transform: translateY(-2px);
}

/* Empty State */
.empty-followed-stores {
    text-align: center;
    padding: 3rem;
    background: var(--white);
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow);
    border: 2px dashed var(--border);
}

.empty-followed-icon {
    font-size: 4rem;
    color: var(--text-secondary);
    margin-bottom: 1rem;
    opacity: 0.5;
}

/* Store Preview Badge */
.store-preview-badge {
    position: absolute;
    top: -10px;
    right: 20px;
    background: var(--primary);
    color: white;
    padding: 5px 15px;
    border-radius: 50px;
    font-size: 0.8rem;
    font-weight: 600;
    box-shadow: 0 4px 10px rgba(1, 65, 28, 0.3);
}

/* Responsive */
@media (max-width: 768px) {
    .followed-store-item {
        flex-direction: column;
        text-align: center;
        gap: 1rem;
        padding: 1.5rem;
    }
    
    .store-meta {
        justify-content: center;
        flex-wrap: wrap;
    }
    
    .store-action {
        width: 100%;
        justify-content: center;
    }
    
    .follow-btn {
        min-width: 140px;
    }
}
<style>
/* Icons View for Followed Stores */
#followedStoresIconsGrid .category-card {
    text-align: center;
    padding: 1rem;
    min-height: 120px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    transition: all 0.3s;
    border: 2px solid transparent;
}

#followedStoresIconsGrid .category-card:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-lg);
    border-color: var(--primary);
}

#followedStoresIconsGrid .category-card img {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    object-fit: cover;
    border: 2px solid var(--primary);
    margin: 0 auto;
}

#followedStoresIconsGrid .category-card i {
    font-size: 2rem;
    color: var(--primary);
    margin-bottom: 0.5rem;
}

#followedStoresIconsGrid .category-name {
    font-size: 0.9rem;
    margin-top: 0.5rem;
    word-break: break-word;
    font-weight: 600;
}
<style>
/* Switch to Desktop Button Styles */
.switch-desktop-container {
    position: fixed;
    bottom: 80px; /* Above chat button */
    right: 20px;
    z-index: 1001;
    display: none; /* Hidden by default, shown only on mobile */
}

.switch-desktop-btn {
    background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-dark-green));
    color: white;
    border: none;
    border-radius: 50px;
    padding: 12px 20px;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 10px;
    box-shadow: var(--shadow-lg);
    transition: all 0.3s;
    font-weight: 600;
    font-size: 0.9rem;
    white-space: nowrap;
}

.switch-desktop-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(1, 65, 28, 0.4);
}

.switch-desktop-btn i {
    font-size: 1.1rem;
}

/* Mobile-specific: Show the button only on mobile */
@media (max-width: 768px) {
    .switch-desktop-container {
        display: block;
        animation: fadeInUp 0.5s ease;
    }
    
    /* When desktop view is active */
    .desktop-view-active .switch-desktop-container {
        bottom: 20px;
        right: 20px;
    }
    
    .desktop-view-active .switch-desktop-btn {
        background: linear-gradient(135deg, #6c757d, #495057);
    }
    
    .desktop-view-active .switch-desktop-btn span {
        content: "Mobile View";
    }
    
    /* Adjust chat button position when switch button is visible */
    .chat-support {
        bottom: 140px;
    }
    
    .desktop-view-active .chat-support {
        bottom: 80px;
    }
}

@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
<style>
/* ==================== FULL SCREEN SEARCH MODAL ==================== */
.full-screen-search-modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: var(--background);
    z-index: 9999;
    overflow-y: auto;
}

.full-screen-search-modal.active {
    display: block;
}

.search-modal-header {
    background: var(--white);
    padding: 1rem;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 1rem;
    position: sticky;
    top: 0;
    z-index: 100;
}

.back-to-home-btn {
    background: none;
    border: none;
    font-size: 1.5rem;
    color: var(--text-primary);
    cursor: pointer;
    padding: 0.5rem;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.back-to-home-btn:hover {
    background: var(--accent);
}

.search-input-container {
    flex: 1;
    background: var(--accent);
    border-radius: 50px;
    padding: 0.5rem 1rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
}

.search-input-container input {
    flex: 1;
    border: none;
    background: none;
    font-size: 1rem;
    color: var(--text-primary);
    outline: none;
    width: 100%;
}

.clear-search-btn {
    background: none;
    border: none;
    color: var(--text-secondary);
    cursor: pointer;
    padding: 0.25rem;
    font-size: 1rem;
}

.clear-search-btn:hover {
    color: var(--primary);
}

.search-modal-content {
    padding: 1.5rem;
}

.recent-searches-section {
    margin-bottom: 2rem;
}

.section-title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1rem;
}

.section-title h3 {
    color: var(--text-primary);
    font-size: 1.1rem;
}

.clear-all-btn {
    background: none;
    border: none;
    color: var(--primary);
    font-size: 0.9rem;
    cursor: pointer;
    padding: 0.25rem 0.5rem;
    border-radius: var(--radius);
}

.clear-all-btn:hover {
    background: var(--accent);
}

.recent-searches-list {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.recent-search-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background: var(--white);
    border-radius: var(--radius);
    cursor: pointer;
    transition: all 0.2s;
    border: 1px solid var(--border);
}

.recent-search-item:hover {
    background: var(--accent);
    transform: translateX(5px);
}

.recent-search-item i {
    color: var(--text-secondary);
    margin-right: 1rem;
}

.recent-search-text {
    flex: 1;
    color: var(--text-primary);
    font-size: 0.95rem;
}

.delete-search-item {
    background: none;
    border: none;
    color: var(--text-secondary);
    cursor: pointer;
    padding: 0.25rem;
    border-radius: 50%;
}

.delete-search-item:hover {
    background: var(--error);
    color: white;
}

.popular-searches-section h3 {
    color: var(--text-primary);
    font-size: 1.1rem;
    margin-bottom: 1rem;
}

.popular-searches-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
}

.popular-search-tag {
    background: var(--white);
    color: var(--text-primary);
    padding: 0.5rem 1rem;
    border-radius: 50px;
    font-size: 0.9rem;
    cursor: pointer;
    transition: all 0.2s;
    border: 1px solid var(--border);
}

.popular-search-tag:hover {
    background: var(--primary);
    color: white;
    border-color: var(--primary);
}

/* ==================== DARAZ-STYLE SEARCH SYSTEM ==================== */

/* Full Screen Search Home */
.full-screen-search-home {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: var(--background);
    z-index: 9999;
    overflow-y: auto;
    animation: slideInUp 0.3s ease;
}

.full-screen-search-home.active {
    display: block;
}

@keyframes slideInUp {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.search-home-header {
    background: var(--white);
    padding: 1rem;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 1rem;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.back-to-home-btn {
    background: none;
    border: none;
    font-size: 1.5rem;
    color: var(--text-primary);
    cursor: pointer;
    padding: 0.5rem;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.3s;
}

.back-to-home-btn:hover {
    background: var(--accent);
}

.search-home-input-container {
    flex: 1;
    background: var(--accent);
    border-radius: 25px;
    padding: 0.8rem 1.2rem;
    display: flex;
    align-items: center;
    gap: 0.8rem;
    border: 2px solid transparent;
    transition: border 0.3s;
}

.search-home-input-container:focus-within {
    border-color: var(--primary);
    background: var(--white);
}

.search-home-input-container i {
    color: var(--text-secondary);
    font-size: 1.1rem;
}

.search-home-input-container input {
    flex: 1;
    border: none;
    background: none;
    font-size: 1rem;
    color: var(--text-primary);
    outline: none;
    width: 100%;
    font-weight: 500;
}

.search-home-input-container input::placeholder {
    color: var(--text-secondary);
    font-weight: normal;
}

.clear-search-btn {
    background: none;
    border: none;
    color: var(--text-secondary);
    cursor: pointer;
    padding: 0.25rem;
    font-size: 1rem;
    transition: color 0.3s;
}

.clear-search-btn:hover {
    color: var(--primary);
}

.search-go-btn {
    background: var(--primary);
    color: white;
    border: none;
    border-radius: 50%;
    width: 45px;
    height: 45px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.3s;
}

.search-go-btn:hover {
    background: var(--pakistan-light-green);
    transform: scale(1.05);
}

.search-home-content {
    padding: 1.5rem;
    max-width: 800px;
    margin: 0 auto;
}

.search-section {
    margin-bottom: 2.5rem;
    animation: fadeIn 0.5s ease;
}

@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

.section-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1.2rem;
}

.section-header h3 {
    color: var(--text-primary);
    font-size: 1.2rem;
    display: flex;
    align-items: center;
    gap: 0.8rem;
    font-weight: 600;
}

.section-header h3 i {
    color: var(--primary);
}

.clear-all-btn {
    background: none;
    border: none;
    color: var(--primary);
    font-size: 0.9rem;
    cursor: pointer;
    padding: 0.5rem 1rem;
    border-radius: 20px;
    transition: all 0.3s;
    font-weight: 500;
}

.clear-all-btn:hover {
    background: rgba(1, 65, 28, 0.1);
}

.recent-searches-list {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.recent-search-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background: var(--white);
    border-radius: var(--radius);
    cursor: pointer;
    transition: all 0.3s;
    border: 1px solid var(--border);
}

.recent-search-item:hover {
    background: var(--accent);
    transform: translateX(5px);
    border-color: var(--primary);
}

.recent-search-item i {
    color: var(--text-secondary);
    margin-right: 1rem;
    font-size: 1rem;
}

.recent-search-text {
    flex: 1;
    color: var(--text-primary);
    font-size: 1rem;
    font-weight: 500;
}

.delete-search-item {
    background: none;
    border: none;
    color: var(--text-secondary);
    cursor: pointer;
    padding: 0.5rem;
    border-radius: 50%;
    transition: all 0.3s;
    display: flex;
    align-items: center;
    justify-content: center;
}

.delete-search-item:hover {
    background: var(--error);
    color: white;
}

.popular-searches-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.8rem;
}

.popular-search-tag {
    background: var(--white);
    color: var(--text-primary);
    padding: 0.7rem 1.2rem;
    border-radius: 25px;
    font-size: 0.95rem;
    cursor: pointer;
    transition: all 0.3s;
    border: 1px solid var(--border);
    font-weight: 500;
}

.popular-search-tag:hover {
    background: var(--primary);
    color: white;
    border-color: var(--primary);
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(1, 65, 28, 0.2);
}

.categories-search-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
}

@media (max-width: 768px) {
    .categories-search-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

.category-search-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 1.5rem 1rem;
    text-align: center;
    cursor: pointer;
    transition: all 0.3s;
    border: 1px solid var(--border);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.8rem;
}

.category-search-card:hover {
    background: var(--primary);
    color: white;
    transform: translateY(-5px);
    box-shadow: 0 5px 15px rgba(1, 65, 28, 0.2);
    border-color: var(--primary);
}

.category-search-card i {
    font-size: 2rem;
    color: var(--primary);
    transition: color 0.3s;
}

.category-search-card:hover i {
    color: white;
}

.category-search-card span {
    font-weight: 600;
    font-size: 0.95rem;
}

/* Search Results Page */
.full-screen-search-results {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: var(--background);
    z-index: 10000;
    overflow-y: auto;
}

.full-screen-search-results.active {
    display: block;
}

.search-results-header {
    background: var(--white);
    padding: 1rem;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 1rem;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.back-to-search-btn {
    background: none;
    border: none;
    font-size: 1.5rem;
    color: var(--text-primary);
    cursor: pointer;
    padding: 0.5rem;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.back-to-search-btn:hover {
    background: var(--accent);
}

.search-results-input-container {
    flex: 1;
    background: var(--accent);
    border-radius: 25px;
    padding: 0.8rem 1.2rem;
    display: flex;
    align-items: center;
    gap: 0.8rem;
}

.search-results-input-container i {
    color: var(--text-secondary);
}

.search-results-input-container input {
    flex: 1;
    border: none;
    background: none;
    font-size: 1rem;
    color: var(--text-primary);
    outline: none;
}

/* Search Filters Bar */
.search-filters-bar {
    background: var(--white);
    border-bottom: 1px solid var(--border);
    padding: 1rem;
    position: sticky;
    top: 68px; /* Header height */
    z-index: 90;
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

.filters-scroll {
    display: flex;
    gap: 0.8rem;
    overflow-x: auto;
    padding-bottom: 0.5rem;
    scrollbar-width: thin;
}

.filters-scroll::-webkit-scrollbar {
    height: 4px;
}

.filters-scroll::-webkit-scrollbar-track {
    background: var(--accent);
}

.filters-scroll::-webkit-scrollbar-thumb {
    background: var(--text-secondary);
    border-radius: 2px;
}

.filter-chip {
    background: var(--accent);
    color: var(--text-primary);
    border: 1px solid var(--border);
    padding: 0.6rem 1.2rem;
    border-radius: 25px;
    cursor: pointer;
    transition: all 0.3s;
    font-size: 0.9rem;
    font-weight: 500;
    white-space: nowrap;
    display: flex;
    align-items: center;
    gap: 0.5rem;
}

.filter-chip:hover {
    background: var(--primary);
    color: white;
    border-color: var(--primary);
}

.filter-chip.active {
    background: var(--primary);
    color: white;
    border-color: var(--primary);
}

.filter-chip i {
    font-size: 0.8rem;
}

/* Filter Dropdowns */
.filter-dropdown {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 1.5rem;
    margin-top: 0.5rem;
    box-shadow: var(--shadow-lg);
    z-index: 100;
    animation: slideDown 0.3s ease;
}

.filter-dropdown.active {
    display: block;
}

.filter-options {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.filter-option {
    display: flex;
    align-items: center;
    gap: 0.8rem;
    cursor: pointer;
    font-size: 0.95rem;
    color: var(--text-primary);
    transition: color 0.3s;
}

.filter-option:hover {
    color: var(--primary);
}

.filter-option input[type="checkbox"] {
    width: 18px;
    height: 18px;
    cursor: pointer;
}

.filter-option .stars {
    color: var(--warning);
    font-size: 1rem;
    letter-spacing: 2px;
}

.price-range-slider {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
}

.price-inputs {
    display: flex;
    align-items: center;
    gap: 1rem;
}

.price-inputs input {
    flex: 1;
    padding: 0.8rem;
    border: 1px solid var(--border);
    border-radius: var(--radius);
    font-size: 1rem;
    text-align: center;
}

.price-inputs span {
    color: var(--text-secondary);
    font-weight: 500;
}

.slider-container {
    position: relative;
    height: 6px;
    background: var(--border);
    border-radius: 3px;
    margin: 1rem 0;
}

.slider-container input[type="range"] {
    position: absolute;
    width: 100%;
    height: 6px;
    background: none;
    pointer-events: none;
    -webkit-appearance: none;
    appearance: none;
}

.slider-container input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 18px;
    height: 18px;
    background: var(--primary);
    border-radius: 50%;
    cursor: pointer;
    pointer-events: all;
    border: 2px solid white;
    box-shadow: 0 2px 5px rgba(0,0,0,0.2);
}

/* Search Results Content */
.search-results-content {
    padding: 1.5rem;
    max-width: 1200px;
    margin: 0 auto;
}

.results-info-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1.5rem;
    flex-wrap: wrap;
    gap: 1rem;
}

.results-count {
    color: var(--text-primary);
    font-size: 1rem;
}

.results-count strong {
    color: var(--primary);
    font-size: 1.2rem;
}

.results-count span {
    color: var(--primary);
    font-weight: 600;
}

.sort-options select {
    padding: 0.6rem 1rem;
    border: 1px solid var(--border);
    border-radius: var(--radius);
    background: var(--white);
    color: var(--text-primary);
    font-size: 0.9rem;
    cursor: pointer;
    min-width: 200px;
}

/* Search Products Grid (2 per row) */
.search-products-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr); /* Always 2 per row */
    gap: 1rem;
    margin-bottom: 2rem;
}

@media (min-width: 1024px) {
    .search-products-grid {
        grid-template-columns: repeat(2, 1fr); /* Still 2 per row on desktop */
        gap: 1.5rem;
    }
}

.search-product-card {
    background: var(--white);
    border-radius: var(--radius);
    overflow: hidden;
    box-shadow: var(--shadow);
    transition: all 0.3s;
    border: 1px solid var(--border);
    cursor: pointer;
    position: relative;
}

.search-product-card:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-lg);
    border-color: var(--primary);
}

.search-product-badge {
    position: absolute;
    top: 10px;
    left: 10px;
    background: var(--primary);
    color: white;
    padding: 5px 10px;
    border-radius: 4px;
    font-size: 0.75rem;
    font-weight: 600;
    z-index: 2;
}

.search-product-image-container {
    position: relative;
    width: 100%;
    height: 180px;
    overflow: hidden;
    background: var(--accent);
}

.search-product-image {
    width: 100%;
    height: 100%;
    object-fit: contain;
    transition: transform 0.3s;
    padding: 10px;
}

.search-product-card:hover .search-product-image {
    transform: scale(1.05);
}

.search-product-info {
    padding: 1rem;
}

.search-product-name {
    font-weight: 600;
    margin-bottom: 0.5rem;
    font-size: 0.95rem;
    color: var(--text-primary);
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
    height: 2.8rem;
    line-height: 1.4;
}

.search-product-price {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 0.5rem;
    flex-wrap: wrap;
}

.search-current-price {
    font-size: 1.2rem;
    font-weight: 700;
    color: var(--primary);
}

.search-original-price {
    font-size: 0.9rem;
    color: var(--text-secondary);
    text-decoration: line-through;
}

.search-product-discount {
    background: var(--error);
    color: white;
    padding: 2px 8px;
    border-radius: 3px;
    font-size: 0.75rem;
    font-weight: 600;
}

.search-product-rating {
    display: flex;
    align-items: center;
    gap: 5px;
    margin-bottom: 0.5rem;
}

.search-product-rating .stars {
    color: var(--warning);
    font-size: 0.9rem;
}

.search-product-rating .count {
    color: var(--text-secondary);
    font-size: 0.85rem;
}

.search-product-stock {
    font-size: 0.85rem;
    color: var(--success);
    margin-bottom: 0.5rem;
    display: flex;
    align-items: center;
    gap: 5px;
}

.search-product-stock.out-of-stock {
    color: var(--error);
}

.search-product-seller {
    font-size: 0.85rem;
    color: var(--text-secondary);
    margin-top: 0.5rem;
    display: flex;
    align-items: center;
    gap: 5px;
}

/* Loading State */
.search-loading-state {
    display: none;
    text-align: center;
    padding: 3rem;
    grid-column: 1 / -1;
}

.search-loading-state.active {
    display: block;
}

.loading-spinner {
    width: 50px;
    height: 50px;
    border: 3px solid var(--accent);
    border-top-color: var(--primary);
    border-radius: 50%;
    animation: spin 1s linear infinite;
    margin: 0 auto 1rem;
}

@keyframes spin {
    to { transform: rotate(360deg); }
}

/* No Results State */
.no-search-results {
    display: none;
    text-align: center;
    padding: 4rem 1rem;
    grid-column: 1 / -1;
}

.no-search-results.active {
    display: block;
}

.no-search-results i {
    font-size: 4rem;
    color: var(--text-secondary);
    margin-bottom: 1.5rem;
    opacity: 0.5;
}

.no-search-results h3 {
    color: var(--text-primary);
    margin-bottom: 0.8rem;
    font-size: 1.5rem;
}

.no-search-results p {
    color: var(--text-secondary);
    margin-bottom: 2rem;
}

/* Search Pagination */
.search-pagination {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0.8rem;
    flex-wrap: wrap;
    margin-top: 2rem;
    padding: 1.5rem;
    background: var(--white);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
}

.search-page-btn {
    min-width: 40px;
    height: 40px;
    border-radius: var(--radius);
    border: 1px solid var(--border);
    background: var(--white);
    color: var(--text-primary);
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s;
    font-weight: 500;
    padding: 0 0.5rem;
}

.search-page-btn:hover:not(:disabled) {
    background: var(--primary);
    color: white;
    border-color: var(--primary);
    transform: translateY(-2px);
}

.search-page-btn.active {
    background: var(--primary);
    color: white;
    border-color: var(--primary);
}

.search-page-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}

.search-page-info {
    color: var(--text-secondary);
    font-size: 0.9rem;
    margin: 0 1rem;
}

/* Mobile Responsive */
@media (max-width: 480px) {
    .search-products-grid {
        grid-template-columns: 1fr; /* 1 per row on very small screens */
        gap: 1rem;
    }
    
    .search-product-image-container {
        height: 160px;
    }
    
    .search-results-header {
        padding: 0.8rem;
    }
    
    .search-home-content {
        padding: 1rem;
    }
    
    .categories-search-grid {
        grid-template-columns: 1fr;
    }
}
        </style>
</head>
<body>

    <!-- Pakistan Flag Header -->
    <div class="flag-header"></div>

    <!-- Main Header -->
    <header>
        <div class="header-top">
            <div class="container">
                <div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 1rem;">
                    <div><i class="fas fa-truck"></i> Free Shipping on Orders Over Rs. 2000</div>
                    <div><i class="fas fa-phone"></i> Support: +92 335 332 1882</div>
                </div>
            </div>
        </div>

        <div class="header-main">
            <div class="container">
                <div class="header-content">
                    <div class="logo" onclick="showHomePage()">
                        <div class="logo-icon"><i class="fas fa-flag"></i></div>
                        <div class="logo-text">
                            <h1>Jeeto Pakistan</h1>
                            <p>Pakistan's Premier E-commerce Platform</p>
                        </div>
                    </div>
<div class="search-bar" onclick="openSearchHome()" style="cursor: pointer;">
    <input type="text" placeholder="Search in store..." readonly style="cursor: pointer;">
    <button onclick="openSearchHome()">
        <i class="fas fa-search"></i>
    </button>
</div>
<!-- ==================== FULL SCREEN SEARCH SYSTEM ==================== -->

<!-- Search Home Page -->
<div class="full-screen-search-home" id="fullScreenSearchHome">
    <div class="search-home-header">
        <button class="back-to-home-btn" onclick="closeSearchHome()">
            <i class="fas fa-arrow-left"></i>
        </button>
        <div class="search-home-input-container">
            <i class="fas fa-search"></i>
            <input type="text" id="searchHomeInput" 
                   placeholder="Search in store..."
                   autocomplete="off"
                   autofocus
                   oninput="handleSearchInput(this.value)"
                   onkeypress="if(event.key === 'Enter') performSearch(this.value)">
            <button class="clear-search-btn" id="clearSearchBtn" style="display: none;" onclick="clearSearchInput()">
                <i class="fas fa-times"></i>
            </button>
        </div>
        <button class="search-go-btn" onclick="performSearch(document.getElementById('searchHomeInput').value)">
            <i class="fas fa-search"></i>
        </button>
    </div>
    
    <div class="search-home-content" id="searchHomeContent">
        <!-- Recent Searches -->
        <div class="search-section" id="recentSearchesSection">
            <div class="section-header">
                <h3><i class="fas fa-history"></i> Recent Searches</h3>
                <button class="clear-all-btn" onclick="clearAllSearchHistory()">
                    Clear All
                </button>
            </div>
            <div class="recent-searches-list" id="recentSearchesList">
                <!-- Recent searches loaded here -->
            </div>
        </div>
        
        <!-- Popular Searches -->
        <div class="search-section">
            <div class="section-header">
                <h3><i class="fas fa-fire"></i> Popular Searches</h3>
            </div>
            <div class="popular-searches-list">
                <span class="popular-search-tag" onclick="searchKeyword('Mobile')">Mobile</span>
                <span class="popular-search-tag" onclick="searchKeyword('Laptop')">Laptop</span>
                <span class="popular-search-tag" onclick="searchKeyword('Shoes')">Shoes</span>
                <span class="popular-search-tag" onclick="searchKeyword('Watch')">Watch</span>
                <span class="popular-search-tag" onclick="searchKeyword('Headphone')">Headphone</span>
                <span class="popular-search-tag" onclick="searchKeyword('Shirt')">Shirt</span>
                <span class="popular-search-tag" onclick="searchKeyword('Book')">Book</span>
                <span class="popular-search-tag" onclick="searchKeyword('Cosmetic')">Cosmetic</span>
            </div>
        </div>
        
        <!-- Categories -->
        <div class="search-section">
            <div class="section-header">
                <h3><i class="fas fa-tags"></i> Browse Categories</h3>
            </div>
            <div class="categories-search-grid">
                <div class="category-search-card" onclick="searchByCategory('Electronics')">
                    <i class="fas fa-mobile-alt"></i>
                    <span>Electronics</span>
                </div>
                <div class="category-search-card" onclick="searchByCategory('Fashion')">
                    <i class="fas fa-tshirt"></i>
                    <span>Fashion</span>
                </div>
                <div class="category-search-card" onclick="searchByCategory('Home & Kitchen')">
                    <i class="fas fa-home"></i>
                    <span>Home & Kitchen</span>
                </div>
                <div class="category-search-card" onclick="searchByCategory('Sports')">
                    <i class="fas fa-dumbbell"></i>
                    <span>Sports</span>
                </div>
                <div class="category-search-card" onclick="searchByCategory('Beauty')">
                    <i class="fas fa-spa"></i>
                    <span>Beauty</span>
                </div>
                <div class="category-search-card" onclick="searchByCategory('Books')">
                    <i class="fas fa-book"></i>
                    <span>Books</span>
                </div>
            </div>
        </div>
    </div>
</div>

<!-- Search Results Page -->
<div class="full-screen-search-results" id="fullScreenSearchResults">
    <div class="search-results-header">
        <button class="back-to-search-btn" onclick="backToSearchPage()">
            <i class="fas fa-arrow-left"></i>
        </button>
        <div class="search-results-input-container">
            <i class="fas fa-search"></i>
            <input type="text" id="searchResultsInput" 
                   placeholder="Search..."
                   oninput="searchProductsInResults(this.value)"
                   onkeypress="if(event.key === 'Enter') searchProductsInResults(this.value)">
        </div>
        <button class="btn btn-secondary btn-sm" onclick="closeSearchAndGoHome()">
            <i class="fas fa-home"></i> Home
        </button>
    </div>
    
    <!-- Filters -->
    <div class="search-filters-bar" id="searchFiltersBar">
        <div class="filters-scroll">
            <button class="filter-chip active" data-filter="all" onclick="applySearchFilter('all')">
                All
            </button>
            <button class="filter-chip" data-filter="category" onclick="toggleFilterDropdown('category')">
                <i class="fas fa-tag"></i> Category
            </button>
            <button class="filter-chip" data-filter="price" onclick="toggleFilterDropdown('price')">
                <i class="fas fa-dollar-sign"></i> Price
            </button>
            <button class="filter-chip" onclick="resetAllFilters()">
                <i class="fas fa-redo"></i> Reset
            </button>
        </div>
        
        <!-- Category Filter Dropdown -->
        <div class="filter-dropdown" id="categoryFilterDropdown">
            <div class="filter-options">
                <label class="filter-option">
                    <input type="checkbox" value="Electronics" onchange="updateCategoryFilter()">
                    Electronics
                </label>
                <label class="filter-option">
                    <input type="checkbox" value="Fashion" onchange="updateCategoryFilter()">
                    Fashion
                </label>
                <label class="filter-option">
                    <input type="checkbox" value="Home & Kitchen" onchange="updateCategoryFilter()">
                    Home & Kitchen
                </label>
                <label class="filter-option">
                    <input type="checkbox" value="Sports" onchange="updateCategoryFilter()">
                    Sports
                </label>
                <label class="filter-option">
                    <input type="checkbox" value="Beauty" onchange="updateCategoryFilter()">
                    Beauty
                </label>
                <label class="filter-option">
                    <input type="checkbox" value="Books" onchange="updateCategoryFilter()">
                    Books
                </label>
            </div>
        </div>
        
        <!-- Price Filter Dropdown -->
        <div class="filter-dropdown" id="priceFilterDropdown">
            <div class="price-range-slider">
                <div class="price-inputs">
                    <input type="number" id="minPriceFilter" placeholder="Min" onchange="updatePriceFilter()">
                    <span>to</span>
                    <input type="number" id="maxPriceFilter" placeholder="Max" onchange="updatePriceFilter()">
                </div>
                <div class="slider-container">
                    <input type="range" min="0" max="100000" value="0" id="priceRangeMin" oninput="updatePriceRange()">
                    <input type="range" min="0" max="100000" value="100000" id="priceRangeMax" oninput="updatePriceRange()">
                </div>
            </div>
        </div>
    </div>
    
    <!-- Results Content -->
    <div class="search-results-content">
        <div class="results-info-bar">
            <div class="results-count" id="searchResultsCount">
                <strong id="resultsCount">0</strong> results for "<span id="currentSearchQuery"></span>"
            </div>
            <div class="sort-options">
                <select id="resultsSort" onchange="sortSearchResults(this.value)">
                    <option value="relevance">Sort by: Relevance</option>
                    <option value="price_low">Price: Low to High</option>
                    <option value="price_high">Price: High to Low</option>
                    <option value="rating">Customer Rating</option>
                    <option value="newest">Newest Arrivals</option>
                </select>
            </div>
        </div>
        
        <!-- Products Grid -->
        <div class="search-products-grid" id="searchProductsGrid">
            <!-- Products will be loaded here -->
        </div>
        
        <!-- Loading -->
        <div class="search-loading-state" id="searchLoading">
            <div class="loading-spinner"></div>
            <p>Searching products...</p>
        </div>
        
        <!-- No Results -->
        <div class="no-search-results" id="noSearchResults">
            <i class="fas fa-search"></i>
            <h3>No Products Found</h3>
            <p>Try different keywords or check spelling</p>
            <button class="btn btn-primary" onclick="backToSearchPage()">
                <i class="fas fa-search"></i> Search Again
            </button>
        </div>
        
        <!-- Pagination -->
        <div class="search-pagination" id="searchPagination"></div>
    </div>
</div>

                    <div class="header-actions">
                        <button class="theme-toggle" id="themeToggle">
                            <i class="fas fa-moon"></i>
                        </button>
                        <button class="action-btn" id="homeBtn">
                            <i class="fas fa-home"></i>
                            <span>Home</span>
                        </button>
                        <button class="action-btn" id="sellerBtn">
                            <i class="fas fa-store"></i>
                            <span>Seller</span>
                            <span class="seller-badge" id="sellerBadge" style="display: none;">PRO</span>
                        </button>
                        <button class="action-btn" id="notificationsBtn" onclick="showNotificationsFullPage()">
    <i class="fas fa-bell"></i>
    <span>Notifications</span>
    <span class="notification-count" id="notificationCount" style="display: none;">0</span>
</button>
                        <button class="action-btn" id="messagesBtn" onclick="showMessagesPage()">
                            <i class="fas fa-comments"></i>
                            <span>Messages</span>
                            <span class="messages-badge" id="messagesCount" style="display: none;">0</span>
                        </button>
                        <button class="action-btn" id="profileBtn">
                            <i class="fas fa-user"></i>
                            <span>Profile</span>
                        </button>
                        <button class="action-btn" id="loginBtn">
                            <i class="fas fa-user"></i>
                            <span id="userStatus">Login</span>
                        </button>
                        <button class="action-btn" id="wishlistBtn">
                            <i class="fas fa-heart"></i>
                            <span>Wishlist</span>
                        </button>
                        <button class="action-btn" id="cartBtn">
                            <i class="fas fa-shopping-cart"></i>
                            <span>Cart</span>
                            <span class="cart-count" id="cartCount">0</span>
                        </button>
                        <button class="action-btn" id="ordersBtn">
                            <i class="fas fa-box"></i>
                            <span>Orders</span>
                        </button>
                        <button class="action-btn" id="logoutBtn">
                            <i class="fas fa-sign-out-alt"></i>
                            <span>Logout</span>
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <div class="main-nav">
            <div class="container">
                <ul class="nav-links">
                    <li><a href="#" id="allProductsLink"><i class="fas fa-boxes"></i> All Products</a></li>
                    <li><a href="#" data-category="Electronics"><i class="fas fa-mobile-alt"></i> Electronics</a></li>
                    <li><a href="#" data-category="Fashion"><i class="fas fa-tshirt"></i> Fashion</a></li>
                    <li><a href="#" data-category="Home & Kitchen"><i class="fas fa-home"></i> Home & Kitchen</a></li>
                    <li><a href="#" data-category="Sports"><i class="fas fa-dumbbell"></i> Sports</a></li>
                    <li><a href="#" data-category="Beauty"><i class="fas fa-spa"></i> Beauty</a></li>
                    <li><a href="#" data-category="Books"><i class="fas fa-book"></i> Books</a></li>
                    <li><a href="#" id="todaysDealsLink"><i class="fas fa-percent"></i> Today's Deals</a></li>
                    <li><a href="#" id="customerSupportLink"><i class="fas fa-headset"></i> Support</a></li>
                </ul>
            </div>
        </div>
    </header>

    <!-- Notification Panel -->
    <div id="notificationsPage" class="container" style="display: none; padding-top: 2rem;">
    <div class="section-header">
        <h2 class="section-title"><i class="fas fa-bell"></i> Your Notifications</h2>
        <button class="btn btn-secondary btn-sm" onclick="showHomePage()">
            <i class="fas fa-arrow-left"></i> Back to Home
        </button>
    </div>
    <div id="notificationsListFull" class="mt-4">
        </div>
</div>

    <!-- User Menu -->
    <div class="user-menu" id="userMenu">
        <a href="#" class="user-menu-item" onclick="viewBuyerProfile()">
            <i class="fas fa-user"></i> My Profile
        </a>
        <a href="#" class="user-menu-item" onclick="viewOrders()">
            <i class="fas fa-box"></i> My Orders
        </a>
        <a href="#" class="user-menu-item" onclick="viewWishlist()">
            <i class="fas fa-heart"></i> Wishlist
        </a>
        <a href="#" class="user-menu-item" onclick="viewAddresses()">
            <i class="fas fa-map-marker-alt"></i> Addresses
        </a>
        <a href="#" class="user-menu-item" onclick="viewSettings()">
            <i class="fas fa-cog"></i> Settings
        </a>
        <a href="#" class="user-menu-item" onclick="showMessagesPage()">
            <i class="fas fa-comments"></i> Messages
        </a>
        <a href="#" class="user-menu-item" onclick="logout()">
            <i class="fas fa-sign-out-alt"></i> Logout
        </a>
    </div>

    <!-- Auth Modal -->
    <div class="auth-modal" id="authModal">
        <div class="modal-content">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                <h2 style="color: var(--primary);">Login / Register</h2>
                <button onclick="closeAuthModal()" style="background: none; border: none; font-size: 1.5rem; color: var(--text-secondary); cursor: pointer;">×</button>
            </div>
            
            <div class="auth-tabs">
                <div class="auth-tab active" data-tab="buyerLogin">Buyer Login</div>
                <div class="auth-tab" data-tab="sellerLogin">Seller Login</div>
                <div class="auth-tab" data-tab="buyerRegister">Register as Buyer</div>
                <div class="auth-tab" data-tab="sellerRegister">Register as Seller</div>
            </div>
            
            <!-- Buyer Login Form -->
            <div class="auth-form active" id="buyerLoginForm">
                <form id="buyerLoginFormElement">
                    <div class="form-group">
                        <label for="buyerLoginEmail">Email Address</label>
                        <input type="email" id="buyerLoginEmail" class="form-control" placeholder="Enter your email" required>
                    </div>
                    <div class="form-group">
                        <label for="buyerLoginPassword">Password</label>
                        <div class="password-input">
                            <input type="password" id="buyerLoginPassword" class="form-control" placeholder="Enter your password" required>
                            <button type="button" class="password-toggle" onclick="togglePassword('buyerLoginPassword', this)"><i class="far fa-eye"></i></button>
                        </div>
                    </div>
                    <div style="text-align: right; margin-bottom: 1rem;">
                        <a href="#" onclick="showForgotPassword()" style="color: var(--primary); text-decoration: none; font-size: 0.9rem;">
                            <i class="fas fa-key"></i> Forgot Password?
                        </a>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">
                        <i class="fas fa-sign-in-alt"></i> Login as Buyer
                    </button>
                </form>
                <div style="text-align: center; margin-top: 1rem;">
                    <p style="color: var(--text-secondary);">Or login with</p>
                    <button class="btn btn-secondary" onclick="loginWithGoogle('buyer')" style="margin-top: 0.5rem; width: 100%;">
                        <i class="fab fa-google"></i> Google
                    </button>
                </div>
            </div>
            
            <!-- Seller Login Form -->
            <div class="auth-form" id="sellerLoginForm">
                <form id="sellerLoginFormElement">
                    <div class="form-group">
                        <label for="sellerLoginEmail">Email Address</label>
                        <input type="email" id="sellerLoginEmail" class="form-control" placeholder="Enter your email" required>
                    </div>
                    <div class="form-group">
                        <label for="sellerLoginPassword">Password</label>
                        <div class="password-input">
                            <input type="password" id="sellerLoginPassword" class="form-control" placeholder="Enter your password" required>
                            <button type="button" class="password-toggle" onclick="togglePassword('sellerLoginPassword', this)"><i class="far fa-eye"></i></button>
                        </div>
                    </div>
                    <div style="text-align: right; margin-bottom: 1rem;">
                        <a href="#" onclick="showForgotPassword()" style="color: var(--primary); text-decoration: none; font-size: 0.9rem;">
                            <i class="fas fa-key"></i> Forgot Password?
                        </a>
                    </div>
                    <button type="submit" class="btn btn-success" style="width: 100%;">
                        <i class="fas fa-sign-in-alt"></i> Login as Seller
                    </button>
                </form>
            </div>
            
            <!-- Buyer Registration Form -->
            <div class="auth-form" id="buyerRegisterForm">
                <form id="buyerRegisterFormElement">
                    <div class="form-group">
                        <label for="buyerName">Full Name *</label>
                        <input type="text" id="buyerName" class="form-control" placeholder="Enter your full name" required>
                    </div>
                    <div class="form-group">
                        <label for="buyerEmail">Email Address *</label>
                        <input type="email" id="buyerEmail" class="form-control" placeholder="Enter your email" required>
                    </div>
                    <div class="form-group">
    <label for="buyerPhone">Phone Number *</label>
    <input type="tel" id="buyerPhone" class="form-control" placeholder="03XX-XXXXXXX" required oninput="formatPhoneNumber(this)">
    <small style="color: var(--warning);">
        <i class="fas fa-lock"></i> This number will be permanently locked and cannot be changed after registration
    </small>
</div>

                    <div class="form-group">
                        <label for="buyerAddress">Address *</label>
                        <textarea id="buyerAddress" class="form-control" rows="3" placeholder="Enter your complete address" required></textarea>
                    </div>
                    <div class="form-group">
                        <label for="buyerPassword">Password *</label>
                        <div class="password-input">
                            <input type="password" id="buyerPassword" class="form-control" placeholder="Create a strong password" required>
                            <button type="button" class="password-toggle" onclick="togglePassword('buyerPassword', this)"><i class="far fa-eye"></i></button>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="buyerConfirmPassword">Confirm Password *</label>
                        <div class="password-input">
                            <input type="password" id="buyerConfirmPassword" class="form-control" placeholder="Confirm your password" required>
                            <button type="button" class="password-toggle" onclick="togglePassword('buyerConfirmPassword', this)"><i class="far fa-eye"></i></button>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">
                        <i class="fas fa-user-plus"></i> Register as Buyer
                    </button>
                </form>
            </div>
            
            <!-- Seller Registration Form -->
            <div class="auth-form" id="sellerRegisterForm">
                <form id="sellerRegisterFormElement">
                    <div class="form-group">
                        <label for="sellerRegName">Seller Name *</label>
                        <input type="text" id="sellerRegName" class="form-control" placeholder="Enter your full name" required>
                    </div>
                    <div class="form-group">
                        <label for="sellerFatherName">Father's Name *</label>
                        <input type="text" id="sellerRegFatherName" class="form-control" placeholder="Enter father's name" required>
                    </div>
                    <div class="form-group">
                        <label for="sellerRegEmail">Email Address *</label>
                        <input type="email" id="sellerRegEmail" class="form-control" placeholder="Enter your email" required>
                    </div>
                 <div class="form-group">
    <label for="sellerRegPhone">Phone Number *</label>
    <input type="tel" id="sellerRegPhone" class="form-control" placeholder="03XX-XXXXXXX" required oninput="formatPhoneNumber(this)">
    <small style="color: var(--warning);">
        <i class="fas fa-lock"></i> This number will be permanently locked for security verification
    </small>
</div>
                    <div class="form-group">
                        <label for="sellerRegPassword">Password *</label>
                        <div class="password-input">
                            <input type="password" id="sellerRegPassword" class="form-control" placeholder="Create a strong password" required>
                            <button type="button" class="password-toggle" onclick="togglePassword('sellerRegPassword', this)"><i class="far fa-eye"></i></button>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="sellerConfirmPassword">Confirm Password *</label>
                        <div class="password-input">
                            <input type="password" id="sellerConfirmPassword" class="form-control" placeholder="Confirm your password" required>
                            <button type="button" class="password-toggle" onclick="togglePassword('sellerConfirmPassword', this)"><i class="far fa-eye"></i></button>
                        </div>
                    </div>
                    <button type="submit" class="btn btn-success" style="width: 100%;">
                        <i class="fas fa-store"></i> Register as Seller
                    </button>
                </form>
            </div>
        </div>
    </div>

    <!-- Forgot Password Modal -->
    <div class="forgot-password-modal" id="forgotPasswordModal">
        <div class="modal-content">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                <h2 style="color: var(--primary);">Forgot Password</h2>
                <button onclick="closeForgotPassword()" style="background: none; border: none; font-size: 1.5rem; color: var(--text-secondary); cursor: pointer;">×</button>
            </div>
            <form id="forgotPasswordForm">
                <div class="form-group">
                    <label for="forgotEmail">Email Address</label>
                    <input type="email" id="forgotEmail" class="form-control" placeholder="Enter your registered email" required>
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">
                    <i class="fas fa-paper-plane"></i> Send Reset Link
                </button>
            </form>
            <div style="text-align: center; margin-top: 1rem;">
                <a href="#" onclick="closeForgotPassword(); openAuthModal('buyerLogin')" style="color: var(--primary); text-decoration: none;">
                    <i class="fas fa-arrow-left"></i> Back to Login
                </a>
            </div>
        </div>
    </div>

    <!-- Main Content Area -->
    <main id="mainContent">
        <!-- Home Page -->
        <div class="container" id="homePage">
            <!-- Hero Slider -->
            <section class="hero">
                <div class="hero-slider">
                    <div class="slide active" style="background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-dark-green));">
                        <div class="slide-content">
                            <h2>Welcome to Jeeto Pakistan</h2>
                            <p>Shop Pakistan's best products with secure payments and fast delivery</p>
                            <button class="btn btn-primary" onclick="showAllProducts()">Explore Products</button>
                        </div>
                    </div>
                            <div class="slide" style="background: linear-gradient(135deg, var(--pakistan-black), #333);">
                        <div class="slide-content">
                            <h2>Fast & Secure Delivery</h2>
                            <p>Get your orders delivered across Pakistan with complete security</p>
                            <button class="btn btn-secondary" onclick="showAllProducts()">Shop Now</button>
                        </div>
                    </div>
                    <div class="slide" style="background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-black));">
                        <div class="slide-content">
                            <h2>Best Prices Guaranteed</h2>
                            <p>Get the best deals on thousands of products every day</p>
                            <button class="btn btn-primary" onclick="showAllProducts()">View Deals</button>
                        </div>
                    </div>
                </div>
            </section>

  
                   <!-- Filter Section -->
        <section class="filter-section" id="filterSection" style="display: none;">
            <h3><i class="fas fa-filter"></i> Filter & Sort</h3>
            <div class="filter-row">
                <div>Sort by:</div>
                <div class="sort-options">
                    <button class="sort-btn active" onclick="sortProducts('default')">
                        <i class="fas fa-sort"></i> Default
                    </button>
                    <button class="sort-btn" onclick="sortProducts('price-low')">
                        <i class="fas fa-sort-amount-down-alt"></i> Price: Low to High
                    </button>
                    <button class="sort-btn" onclick="sortProducts('price-high')">
                        <i class="fas fa-sort-amount-down"></i> Price: High to Low
                    </button>
                    <button class="sort-btn" onclick="sortProducts('newest')">
                        <i class="fas fa-calendar-plus"></i> Newest
                    </button>
                    <button class="sort-btn" onclick="sortProducts('rating')">
                        <i class="fas fa-star"></i> Top Rated
                    </button>
                </div>
                <button class="btn btn-secondary" onclick="toggleAdvancedFilter()">
                    <i class="fas fa-sliders-h"></i> Advanced Filter
                </button>
            </div>
            
            <div class="advanced-filter" id="advancedFilter">
                <div class="filter-row" style="border-bottom: 2px solid var(--border); padding-bottom: 1.5rem; margin-bottom: 1.5rem;">
                    <div class="filter-group">
                        <label><i class="fas fa-tag"></i> Price Range (PKR)</label>
                        <div class="price-range">
                            <input type="number" id="minPrice" class="form-control" placeholder="Min" min="0">
                            <span>to</span>
                            <input type="number" id="maxPrice" class="form-control" placeholder="Max" min="0">
                            <button class="btn btn-primary btn-sm" onclick="applyPriceFilter()">
                                <i class="fas fa-check"></i> Apply
                            </button>
                        </div>
                    </div>
                    <div class="filter-group">
                        <label><i class="fas fa-tags"></i> Category</label>
                        <select id="categoryFilter" class="form-control" onchange="applyCategoryFilter()">
                            <option value="">All Categories</option>
                            <option value="Electronics">Electronics</option>
                            <option value="Fashion">Fashion</option>
                            <option value="Home & Kitchen">Home & Kitchen</option>
                            <option value="Sports">Sports</option>
                            <option value="Beauty">Beauty</option>
                            <option value="Books">Books</option>
                        </select>
                    </div>
                    <div class="filter-group">
                        <label><i class="fas fa-star"></i> Rating</label>
                        <select id="ratingFilter" class="form-control" onchange="applyRatingFilter()">
                            <option value="">All Ratings</option>
                            <option value="5">5 Stars</option>
                            <option value="4">4+ Stars</option>
                            <option value="3">3+ Stars</option>
                            <option value="2">2+ Stars</option>
                            <option value="1">1+ Stars</option>
                        </select>
                    </div>
                </div>
            </div>
        </section>
            <!-- Categories Section -->
            <section class="section">
                <div class="section-header">
                    <h2 class="section-title">Shop By Category</h2>
                    <a href="#" class="view-all" onclick="showAllCategories()">View All <i class="fas fa-chevron-right"></i></a>
                </div>
                <div class="categories-grid" id="categoriesGrid">
                    <!-- Categories loaded dynamically -->
                </div>
            </section>

            <!-- Featured Products -->
            <section class="section">
                <div class="section-header">
                    <h2 class="section-title">Featured Products</h2>
                    <a href="#" class="view-all" onclick="showAllProducts()">View All <i class="fas fa-chevron-right"></i></a>
                </div>
                <div class="products-grid" id="featuredProducts">
                    <!-- Products loaded dynamically -->
                </div>
                <div class="pagination" id="productPagination"></div>
            </section>

            <!-- Flash Sale -->
            <section class="section">
                <div class="section-header">
                    <h2 class="section-title">Flash Sale <span style="color: var(--error);"><i class="fas fa-bolt"></i></span></h2>
                    <div style="display: flex; align-items: center; gap: 10px;">
                        <div style="font-weight: 600; color: var(--error);">Ends in:</div>
                        <div id="countdown" style="display: flex; gap: 5px; font-weight: 700;">
                            <span id="countdown-hours">02</span>:<span id="countdown-minutes">30</span>:<span id="countdown-seconds">00</span>
                        </div>
                    </div>
                </div>
                <div class="products-grid" id="flashSaleProducts">
                    <!-- Flash sale products loaded dynamically -->
                </div>
            </section>

            <!-- Followed Stores Section -->
<section class="section followed-stores-section">
    <div class="section-header">
        <h2 class="section-title">
            <i class="fas fa-heart" style="color: var(--primary);"></i> Your Followed Stores
        </h2>
        <div style="display: flex; gap: 10px; align-items: center;">
            <a href="#" class="view-all" onclick="showFollowingStores()">
                View All <i class="fas fa-chevron-right"></i>
            </a>
            <button class="btn btn-secondary btn-sm" onclick="showAllStores()">
                <i class="fas fa-store"></i> Browse Stores
            </button>
        </div>
    </div>
    
    <!-- Icons Only Grid -->
    <div class="categories-grid" id="followedStoresIconsGrid">
        <!-- Icons will be loaded here -->
        <div style="text-align: center; grid-column: 1/-1; padding: 2rem;">
            <i class="fas fa-store-slash" style="font-size: 3rem; color: var(--text-secondary); opacity: 0.5; margin-bottom: 1rem;"></i>
            <p>Follow stores to see them here!</p>
            <button class="btn btn-primary btn-sm" onclick="showAllStores()">
                <i class="fas fa-store"></i> Browse Stores
            </button>
        </div>
    </div>
</section>



            <!-- Customer Reviews -->
            <section class="section">
                <div class="section-header">
                    <h2 class="section-title">Customer Reviews</h2>
                </div>
                <div id="customerReviews">
                    <!-- Reviews loaded dynamically -->
                </div>
            </section>
        </div>

        <!-- Product Details Page -->
        <div class="container" id="productDetailsPage" style="display: none;">
            <div id="productDetailsContent"></div>
        </div>

        <!-- Cart Page -->
        <div class="container" id="cartPage" style="display: none;">
            <div id="cartContent"></div>
        </div>

        <!-- Checkout Page -->
        <div class="container" id="checkoutPage" style="display: none;">
            <div id="checkoutContent"></div>
        </div>

        <!-- Buyer Profile Page -->
        <div class="container" id="buyerProfilePage" style="display: none;">
            <div id="buyerProfileContent"></div>
        </div>

        <!-- Orders Page -->
        <div class="container" id="ordersPage" style="display: none;">
            <div id="ordersContent"></div>
        </div>

        <!-- Order Tracking Page -->
        <div class="container" id="orderTrackingPage" style="display: none;">
            <div id="orderTrackingContent"></div>
        </div>

        <!-- Wishlist Page -->
        <div class="container" id="wishlistPage" style="display: none;">
            <div id="wishlistContent"></div>
        </div>

        <!-- Address Book Page -->
        <div class="container" id="addressesPage" style="display: none;">
            <div id="addressesContent"></div>
        </div>

        <!-- Settings Page -->
        <div class="container" id="settingsPage" style="display: none;">
            <div id="settingsContent"></div>
        </div>

        <!-- Messages Page -->
        <div class="container" id="messagesPage" style="display: none;">
            <div id="messagesContent"></div>
        </div>

    <section class="section" id="searchResultsSection" style="display: none; background: #fff; min-height: 100vh;">
    <div class="container">
        <div style="display: grid; grid-template-columns: 280px 1fr; gap: 20px; padding-top: 20px;">
            
            <aside style="background: #f9f9f9; padding: 20px; border-radius: 8px; border: 1px solid #eee; height: fit-content;">
                <h3 style="font-size: 1.1rem; border-bottom: 2px solid var(--pakistan-green); padding-bottom: 10px; margin-bottom: 20px;">Filters</h3>
                
                <div style="margin-bottom: 25px;">
                    <label style="font-weight: 600; display: block; margin-bottom: 10px;">Sort By</label>
                    <select id="searchSort" class="form-control" onchange="applySearchFilters()" style="width: 100%; padding: 8px;">
                        <option value="default">Relevance</option>
                        <option value="price-low">Price: Low to High</option>
                        <option value="price-high">Price: High to Low</option>
                        <option value="top-rated">Top Rated</option>
                        <option value="discount">Flash Sale (Discount)</option>
                    </select>
                </div>

                <div style="margin-bottom: 25px;">
                    <label style="font-weight: 600; display: block; margin-bottom: 10px;">Related Categories</label>
                    <div id="searchCategoryList" style="display: flex; flex-direction: column; gap: 8px; font-size: 0.9rem; color: #555;">
                        </div>
                </div>
            </aside>

            <main>
                <div style="background: #f4f4f4; padding: 15px; border-radius: 8px; margin-bottom: 20px; display: flex; justify-content: space-between; align-items: center;">
                    <p style="margin:0;">Results for: <strong id="searchQueryLabel" style="color: var(--pakistan-green);"></strong></p>
                    <button class="btn btn-secondary btn-sm" onclick="showHomePage()">Back to Home</button>
                </div>
                <div id="searchResultsGrid" class="products-grid">
                    </div>
            </main>
        </div>
    </div>
</section>
    

    <!-- Seller Panel -->
    <div class="seller-panel" id="sellerPanel">
        <div class="seller-header">
            <h2><i class="fas fa-store"></i> Seller Dashboard</h2>
            <div style="display: flex; align-items: center; gap: 1rem;">
                <span id="sellerShopNameDisplay" style="font-weight: 500; color: var(--primary);"></span>
                <button class="btn btn-primary" id="closeSellerPanelBtn">
                    <i class="fas fa-times"></i> Close Panel
                </button>
            </div>
        </div>
        <div class="seller-main">
            <div class="seller-sidebar">
                <ul class="seller-nav">
                    <li><a href="#" class="active" data-tab="dashboard"><i class="fas fa-tachometer-alt"></i> Dashboard</a></li>
                    <li><a href="#" data-tab="profile"><i class="fas fa-user"></i> Profile</a></li>
                    <li><a href="#" data-tab="products"><i class="fas fa-box"></i> Product Management</a></li>
                    <li><a href="#" data-tab="addProduct"><i class="fas fa-plus-circle"></i> Add New Product</a></li>
                    <li><a href="#" data-tab="flashSaleManagement"><i class="fas fa-bolt"></i> Flash Sale Management</a></li>
                    <li><a href="#" data-tab="orders"><i class="fas fa-shopping-cart"></i> Orders Management</a></li>
                    <li><a href="#" data-tab="tracking"><i class="fas fa-truck"></i> Order Tracking</a></li>
                    <li><a href="#" data-tab="withdrawal"><i class="fas fa-money-bill-wave"></i> Withdrawal</a></li>
                    <li><a href="#" data-tab="taxInvoice"><i class="fas fa-file-invoice-dollar"></i> Tax Invoice</a></li>
                    <li><a href="#" data-tab="earnings"><i class="fas fa-chart-line"></i> Earnings</a></li>
                    <li><a href="#" data-tab="orderHistory"><i class="fas fa-history"></i> Order History</a></li>
                    <li><a href="#" data-tab="messages"><i class="fas fa-comments"></i> Messages</a></li>
                    <li><a href="#" data-tab="support"><i class="fas fa-headset"></i> Support</a></li>
                </ul>
            </div>
            <div class="seller-content">
                <!-- Dashboard -->
                <div class="seller-tab active" id="dashboardTab">
                    <h3>Dashboard Overview</h3>
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-number" id="sellerTotalProducts">0</div>
                            <div class="stat-label">Total Products</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" id="sellerTotalOrders">0</div>
                            <div class="stat-label">Total Orders</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" id="sellerPendingOrders">0</div>
                            <div class="stat-label">Pending Orders</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" id="sellerTotalEarnings">Rs. 0</div>
                            <div class="stat-label">Total Earnings</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" id="sellerAvailableBalance">Rs. 0</div>
                            <div class="stat-label">Available Balance</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number" id="sellerPendingWithdrawal">Rs. 0</div>
                            <div class="stat-label">Pending Withdrawal</div>
                        </div>
                    </div>

                    <div class="quick-actions">
                        <div class="quick-action-btn" onclick="switchSellerTab('addProduct')">
                            <div class="quick-action-icon">
                                <i class="fas fa-plus-circle"></i>
                            </div>
                            <h4>Add New Product</h4>
                            <p>List a new product for sale</p>
                        </div>
                        <div class="quick-action-btn" onclick="switchSellerTab('orders')">
                            <div class="quick-action-icon">
                                <i class="fas fa-box"></i>
                            </div>
                            <h4>Manage Orders</h4>
                            <p>View and process orders</p>
                        </div>
                        <div class="quick-action-btn" onclick="switchSellerTab('withdrawal')">
                            <div class="quick-action-icon">
                                <i class="fas fa-money-bill-wave"></i>
                            </div>
                            <h4>Request Withdrawal</h4>
                            <p>Withdraw your earnings</p>
                        </div>
                        <div class="quick-action-btn" onclick="switchSellerTab('taxInvoice')">
                            <div class="quick-action-icon">
                                <i class="fas fa-file-invoice-dollar"></i>
                            </div>
                            <h4>Tax Invoices</h4>
                            <p>Manage tax invoices</p>
                        </div>
                    </div>

                    <!-- Recent Orders -->
                    <div style="margin-top: 2rem;">
                        <h4>Recent Orders</h4>
                        <div id="sellerRecentOrders">
                            <p>No recent orders</p>
                        </div>
                    </div>
                </div>

                <!-- Profile -->
                <div class="seller-tab" id="profileTab">
                    <div class="product-management">
                        <h3>Seller Profile</h3>
                        <form id="sellerProfileForm">
                            <div class="form-row">
                                <div class="form-group">
                                    <label>Shop Name *</label>
                                    <input type="text" id="sellerShopName" class="form-control" required>
                                </div>
                                <div class="form-group">
                                    <label>Email *</label>
                                    <input type="email" id="sellerEmail" class="form-control" readonly>
                                </div>
                            </div>
                            <div class="form-row">
                                <div class="form-group">
                                    <label>Phone *</label>
                                    <input type="tel" id="sellerPhone" class="form-control" required>
                                </div>
                                <div class="form-group">
                                    <label>CNIC Number *</label>
                                    <input type="text" id="sellerCNIC" class="form-control" placeholder="XXXXX-XXXXXXX-X" required>
                                </div>
                            </div>
                            <div class="form-group">
                                <label>Shop Address *</label>
                                <textarea id="sellerAddress" class="form-control" rows="3" required></textarea>
                            </div>
                            <div class="form-row">
                                <div class="form-group">
                                    <label>City *</label>
                                    <input type="text" id="sellerCity" class="form-control" required>
                                </div>
                                <div class="form-group">
                                    <label>Postal Code</label>
                                    <input type="text" id="sellerPostalCode" class="form-control">
                                </div>
                            </div>
                            <div class="form-group">
                                <label>Shop Description</label>
                                <textarea id="sellerDescription" class="form-control" rows="4"></textarea>
                            </div>
                            <button type="submit" class="btn btn-primary">
                                <i class="fas fa-save"></i> Update Profile
                            </button>
                        </form>
                    </div>
                </div>

                <!-- Product Management Section -->
                <div class="seller-tab" id="productsTab">
                    <div class="product-management">
                        <h3>Product Management</h3>
                        <button class="btn btn-primary" onclick="switchSellerTab('addProduct')" style="margin-bottom: 1rem;">
                            <i class="fas fa-plus"></i> Add New Product
                        </button>
                        <div class="table-container">
                            <table class="product-table">
                                <thead>
                                    <tr>
                                        <th>Image</th>
                                        <th>Product Code</th>
                                        <th>Product Name</th>
                                        <th>Price</th>
                                        <th>Stock</th>
                                        <th>Status</th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody id="sellerProductsList">
                                    <tr><td colspan="7" style="text-align: center; padding: 2rem;">No products found. <a href="#" onclick="switchSellerTab('addProduct')" style="color: var(--primary);">Add your first product</a></td></tr>
                                </tbody>
                            </table>
                        </div>
                        <div class="pagination" id="sellerProductsPagination"></div>
                    </div>
                </div>

                <!-- Add Product Form with Category Specific Options -->
                <div class="seller-tab" id="addProductTab">
                    <div class="product-management">
                        <h3>Add New Product</h3>
                        <form id="addProductForm">
                            <div class="form-row">
                                <div class="form-group">
                                    <label for="productCode"><i class="fas fa-barcode"></i> Product Code *</label>
                                    <input type="text" id="productCode" class="form-control" placeholder="PRD-001" required>
                                </div>
                                <div class="form-group">
                                    <label for="productName"><i class="fas fa-box"></i> Product Name *</label>
                                    <input type="text" id="productName" class="form-control" placeholder="Enter product name" required>
                                </div>
                            </div>
                            
                            <div class="form-row">
                                <div class="form-group">
                                    <label for="productCategory"><i class="fas fa-tags"></i> Category *</label>
                                    <select id="productCategory" class="form-control" required onchange="showCategoryOptions()">
                                        <option value="">Select Category</option>
                                        <option value="Electronics">Electronics</option>
                                        <option value="Fashion">Fashion</option>
                                        <option value="Home & Kitchen">Home & Kitchen</option>
                                        <option value="Sports">Sports</option>
                                        <option value="Beauty">Beauty</option>
                                        <option value="Books">Books</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label for="productBrand"><i class="fas fa-trademark"></i> Brand</label>
                                    <input type="text" id="productBrand" class="form-control" placeholder="Enter brand name">
                                </div>
                            </div>
                            
                            <!-- Category Specific Options -->
                            <div id="categoryOptions" class="category-options">
                                <!-- Options will be loaded based on category selection -->
                            </div>
                            
                            <div class="form-row">
                                <div class="form-group">
                                    <label for="productPrice"><i class="fas fa-tag"></i> Price (Rs.) *</label>
                                    <input type="number" id="productPrice" class="form-control" min="1" placeholder="Enter price" required>
                                </div>
                                <div class="form-group">
                                    <label for="productQuantity"><i class="fas fa-cubes"></i> Quantity *</label>
                                    <input type="number" id="productQuantity" class="form-control" min="1" placeholder="Enter quantity" required>
                                </div>
                            </div>
                            
                            <div class="form-row">
                                <div class="form-group">
                                    <label for="productDiscount"><i class="fas fa-percent"></i> Discount (%)</label>
                                    <input type="number" id="productDiscount" class="form-control" min="0" max="100" placeholder="Enter discount percentage">
                                </div>
                                <div class="form-group">
                                    <label for="productWeight"><i class="fas fa-weight"></i> Weight (kg)</label>
                                    <input type="number" id="productWeight" class="form-control" min="0" step="0.1" placeholder="Enter product weight">
                                </div>
                            </div>
                            
                            <div class="form-group">
                                <label for="productDescription"><i class="fas fa-align-left"></i> Description *</label>
                                <textarea id="productDescription" class="form-control" rows="4" placeholder="Enter product description" required></textarea>
                            </div>
                            
                            <div class="form-group">
                                <label for="productSpecifications"><i class="fas fa-list-alt"></i> Specifications (JSON)</label>
                                <textarea id="productSpecifications" class="form-control" rows="3" placeholder='{"color": "red", "size": "M"}'></textarea>
                                <small>Enter product specifications in JSON format</small>
                            </div>
                            
                            <div class="form-group">
                                <label><i class="fas fa-images"></i> Product Images *</label>
                                <div style="border: 2px dashed var(--border); border-radius: var(--radius); padding: 2rem; text-align: center; cursor: pointer; margin-bottom: 1rem;" id="imageUploadArea" onclick="document.getElementById('productImages').click()">
                                    <i class="fas fa-cloud-upload-alt" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                                    <p>Click or drag images to upload (Max 8 images)</p>
                                    <p style="font-size: 0.8rem; color: var(--text-secondary);">Supported formats: JPG, PNG, WEBP | Max 5MB each</p>
                                </div>
                                <input type="file" id="productImages" multiple accept="image/*" style="display: none;" onchange="handleProductImageUpload(event)">
                                <div class="image-preview-container" id="imagePreviewContainer" style="display: flex; gap: 1rem; flex-wrap: wrap; margin-top: 1rem;"></div>
                            </div>
                            
                            <div class="form-group">
                                <label><i class="fas fa-video"></i> Product Video (Optional)</label>
                                <input type="file" id="productVideo" accept="video/*" class="form-control" onchange="handleProductVideoUpload(event)">
                                <div id="videoPreviewContainer" style="margin-top: 1rem;"></div>
                            </div>
                            
                            <div class="form-actions" style="margin-top: 2rem;">
                                <button type="reset" class="btn btn-secondary">
                                    <i class="fas fa-redo"></i> Reset
                                </button>
                                <button type="submit" class="btn btn-success" id="publishProductBtn">
                                    <i class="fas fa-upload"></i> Publish Product
                                </button>
                            </div>
                        </form>
                    </div>
                </div>

                <!-- Flash Sale Management -->
                <div class="seller-tab" id="flashSaleManagementTab">
                    <div class="product-management">
                        <h3><i class="fas fa-bolt"></i> Flash Sale Management</h3>
                        
                        <div style="background: var(--accent); padding: 1.5rem; border-radius: var(--radius); margin-bottom: 2rem;">
                            <h4 style="color: var(--primary); margin-bottom: 1rem;">Create New Flash Sale</h4>
                            <form id="createFlashSaleForm">
                                <div class="form-row">
                                    <div class="form-group">
                                        <label>Select Product *</label>
                                        <select id="flashSaleProduct" class="form-control" required>
                                            <option value="">Select Product</option>
                                        </select>
                                    </div>
                                    <div class="form-group">
                                        <label>Flash Sale Price (PKR) *</label>
                                        <input type="number" id="flashSalePrice" class="form-control" placeholder="Enter flash sale price" required min="1">
                                    </div>
                                </div>
                                
                                <div class="form-row">
                                    <div class="form-group">
                                        <label>Start Date *</label>
                                        <input type="datetime-local" id="flashSaleStart" class="form-control" required>
                                    </div>
                                    <div class="form-group">
                                        <label>End Date *</label>
                                        <input type="datetime-local" id="flashSaleEnd" class="form-control" required>
                                    </div>
                                </div>
                                
                                <div class="form-group">
                                    <label>Flash Sale Quantity *</label>
                                    <input type="number" id="flashSaleQuantity" class="form-control" placeholder="Available quantity for flash sale" required min="1">
                                </div>
                                
                                <button type="submit" class="btn btn-warning">
                                    <i class="fas fa-bolt"></i> Create Flash Sale
                                </button>
                            </form>
                        </div>
                        
                        <h4 style="color: var(--primary); margin-bottom: 1rem;">Active Flash Sales</h4>
                        <div class="table-container">
                            <table class="product-table">
                                <thead>
                                    <tr>
                                        <th>Product</th>
                                        <th>Original Price</th>
                                        <th>Flash Price</th>
                                        <th>Start Date</th>
                                        <th>End Date</th>
                                        <th>Status</th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody id="flashSalesList">
                                    <tr><td colspan="7" style="text-align: center; padding: 2rem;">No active flash sales</td></tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <!-- Orders Management -->
                <div class="seller-tab" id="ordersTab">
                    <div class="product-management">
                        <h3>Orders Management</h3>
                        <div id="sellerOrdersList">
                            <!-- Orders will be loaded here -->
                        </div>
                        <div class="pagination" id="sellerOrdersPagination"></div>
                    </div>
                </div>

                <!-- Order Tracking -->
                <div class="seller-tab" id="trackingTab">
                    <div class="product-management">
                        <h3>Order Tracking Management</h3>
                        <div id="sellerTrackingContent">
                            <div id="trackingOrdersList">
                                <!-- Orders for tracking will be loaded here -->
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Withdrawal Management -->
                <div class="seller-tab" id="withdrawalTab">
                    <div class="product-management">
                        <h3><i class="fas fa-money-bill-wave"></i> Withdrawal Management</h3>
                        
                        <div style="background: var(--accent); padding: 1.5rem; border-radius: var(--radius); margin-bottom: 2rem;">
                            <h4 style="color: var(--primary); margin-bottom: 1rem;">Request Withdrawal</h4>
                            <form id="withdrawalRequestForm">
                                <div class="form-group">
                                    <label>Available Balance</label>
                                    <div style="font-size: 1.5rem; font-weight: bold; color: var(--primary);">
                                        Rs. <span id="availableBalance">0</span>
                                    </div>
                                </div>
                                
                                <div class="form-group">
                                    <label>Withdrawal Amount (PKR) *</label>
                                    <input type="number" id="withdrawalAmount" class="form-control" placeholder="Enter amount" required min="500" max="100000">
                                    <small>Minimum withdrawal: Rs. 500</small>
                                </div>
                                
                                <div class="form-row">
                                    <div class="form-group">
                                        <label>Payment Method *</label>
                                        <select id="withdrawalMethod" class="form-control" required>
                                            <option value="">Select Method</option>
                                            <option value="easypaisa">EasyPaisa</option>
                                            <option value="jazzcash">JazzCash</option>
                                        </select>
                                    </div>
                                    <div class="form-group">
                                        <label>Account Number *</label>
                                        <input type="text" id="withdrawalAccount" class="form-control" placeholder="03XX-XXXXXXX" required>
                                    </div>
                                </div>
                                
                                <div class="form-group">
                                    <label>Account Holder Name *</label>
                                    <input type="text" id="withdrawalAccountName" class="form-control" placeholder="Enter account holder name" required>
                                </div>
                                
                                <div class="form-group">
                                    <label>CNIC Number *</label>
                                    <input type="text" id="withdrawalCNIC" class="form-control" placeholder="XXXXX-XXXXXXX-X" required>
                                </div>
                                
                                <button type="submit" class="btn btn-primary">
                                    <i class="fas fa-paper-plane"></i> Submit Withdrawal Request
                                </button>
                            </form>
                        </div>
                        
                        <h4 style="color: var(--primary); margin-bottom: 1rem;">Withdrawal History</h4>
                        <div class="table-container">
                            <table class="product-table">
                                <thead>
                                    <tr>
                                        <th>Request ID</th>
                                        <th>Amount</th>
                                        <th>Method</th>
                                        <th>Status</th>
                                        <th>Request Date</th>
                                        <th>Completion Date</th>
                                    </tr>
                                </thead>
                                <tbody id="withdrawalHistory">
                                    <tr><td colspan="6" style="text-align: center; padding: 2rem;">No withdrawal history</td></tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <!-- Tax Invoice Management -->
                <div class="seller-tab" id="taxInvoiceTab">
                    <div class="product-management">
                        <h3><i class="fas fa-file-invoice-dollar"></i> Tax Invoice Management</h3>
                        
                        <div id="taxInvoiceContent">
                            <div id="lockedInvoicesList">
                                <!-- Locked invoices will be loaded here -->
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Earnings -->
                <div class="seller-tab" id="earningsTab">
                    <div class="product-management">
                        <h3>Earnings Overview</h3>
                        <div id="earningsContent">
                            <!-- Earnings content loaded here -->
                        </div>
                    </div>
                </div>

                <!-- Order History -->
                <div class="seller-tab" id="orderHistoryTab">
                    <div class="product-management">
                        <h3>Order History</h3>
                        
                        <div style="background: var(--accent); padding: 1.5rem; border-radius: var(--radius); margin-bottom: 2rem;">
                            <h4 style="color: var(--primary); margin-bottom: 1rem;">Filter Orders</h4>
                            <div class="date-range-filter">
                                <div class="form-group">
                                    <label>From Date</label>
                                    <input type="date" id="orderHistoryFrom" class="form-control">
                                </div>
                                <div class="form-group">
                                    <label>To Date</label>
                                    <input type="date" id="orderHistoryTo" class="form-control">
                                </div>
                                <div class="form-group">
                                    <label>Status</label>
                                    <select id="orderHistoryStatus" class="form-control">
                                        <option value="">All Status</option>
                                        <option value="pending">Pending</option>
                                        <option value="confirmed">Confirmed</option>
                                        <option value="shipped">Shipped</option>
                                        <option value="delivered">Delivered</option>
                                        <option value="cancelled">Cancelled</option>
                                    </select>
                                </div>
                                <button class="btn btn-primary" onclick="filterOrderHistory()">
                                    <i class="fas fa-filter"></i> Apply Filter
                                </button>
                            </div>
                        </div>
                        
                        <div id="orderHistoryList">
                            <!-- Order history will be loaded here -->
                        </div>
                        <div class="pagination" id="orderHistoryPagination"></div>
                    </div>
                </div>

                <!-- Messages -->
                <div class="seller-tab" id="messagesTab">
                    <div class="product-management">
                        <h3>Messages</h3>
                        <div class="message-system" id="sellerMessagesSystem">
                            <div class="chat-container">
                                <div class="chat-sidebar">
                                    <div class="chat-list" id="sellerChatList">
                                        <!-- Chat list will be loaded here -->
                                    </div>
                                </div>
                                <div class="chat-content">
                                    <div class="chat-header" id="sellerChatHeader">
                                        <p>Select a conversation to start messaging</p>
                                    </div>
                                    <div class="chat-messages" id="sellerChatMessages">
                                        <!-- Messages will be loaded here -->
                                    </div>
                                    <div class="chat-input">
                                        <input type="text" id="sellerMessageInput" placeholder="Type your message..." disabled>
                                        <button class="btn btn-primary" id="sellerSendMessageBtn" disabled>
                                            <i class="fas fa-paper-plane"></i>
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Support -->
                <div class="seller-tab" id="supportTab">
                    <div class="product-management">
                        <h3>24/7 Support</h3>
                        <div class="message-system admin-message-system">
                            <div class="chat-container">
                                <div class="chat-sidebar">
                                    <div class="chat-list" id="adminChatList">
                                        <!-- Admin chat list will be loaded here -->
                                    </div>
                                </div>
                                <div class="chat-content">
                                    <div class="chat-header" id="adminChatHeader">
                                        <p>Chat with Admin Support</p>
                                    </div>
                                    <div class="chat-messages" id="adminChatMessages">
                                        <!-- Messages will be loaded here -->
                                    </div>
                                    <div class="chat-input">
                                        <input type="text" id="adminMessageInput" placeholder="Type your message...">
                                        <button class="btn btn-primary" id="adminSendMessageBtn">
                                            <i class="fas fa-paper-plane"></i>
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Order Lock Payment Modal -->
    
<div class="payment-verification" id="orderLockPaymentModal">
    <div class="verification-content">
        <h3><i class="fas fa-lock"></i> Order Payment Required</h3>
        <p>To unlock order <strong id="lockedOrderIdDisplay">#K6VFHy</strong>, please pay <strong>Rs. 50</strong> to the admin.</p>
        
        <form id="orderPaymentForm">
            <!-- Payment details section -->
            <div style="margin: 1.5rem 0; background: rgba(1, 65, 28, 0.1); padding: 1rem; border-radius: var(--radius);">
                <h4 style="color: var(--primary); margin-bottom: 0.5rem;">Payment Details:</h4>
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
                    <div>
                        <p><strong><i class="fas fa-mobile-alt"></i> EasyPaisa</strong></p>
                        <p>Account: 0332-2087563</p>
                        <p>Name: Muhammad Sadique</p>
                    </div>
                    <div>
                        <p><strong><i class="fas fa-wallet"></i> JazzCash</strong></p>
                        <p>Account: 0332-2087563</p>
                        <p>Name: Muhammad Sadique</p>
                    </div>
                </div>
            </div>
            
            <!-- Payment form fields -->
            <div class="form-group">
                <label for="orderTransactionId"><i class="fas fa-receipt"></i> Transaction ID *</label>
                <input type="text" id="orderTransactionId" class="form-control" placeholder="Enter transaction ID from payment" required>
            </div>
            
            <div class="form-group">
                <label for="paymentMethodSelect"><i class="fas fa-credit-card"></i> Payment Method *</label>
                <select id="paymentMethodSelect" class="form-control" required>
                    <option value="">Select Method</option>
                    <option value="easypaisa">EasyPaisa</option>
                    <option value="jazzcash">JazzCash</option>
                </select>
            </div>

            <div class="form-group">
                <label for="paymentHolderName"><i class="fas fa-user"></i> Your Name *</label>
                <input type="text" id="paymentHolderName" class="form-control" placeholder="Enter your name as on mobile account" required>
            </div>

            <div class="form-group">
                <label for="paymentPhoneNumber"><i class="fas fa-phone"></i> Your Phone Number *</label>
                <input type="tel" id="paymentPhoneNumber" class="form-control" placeholder="03XX-XXXXXXX" required>
            </div>

            <div class="form-group">
                <label for="paymentProofFile"><i class="fas fa-camera"></i> Payment Proof (Screenshot) *</label>
                <input type="file" id="paymentProofFile" accept="image/*" class="form-control" required onchange="previewPaymentProof(event)">
                <div id="paymentProofPreview" style="margin-top: 1rem;"></div>
            </div>
            
            <div style="display: flex; gap: 1rem; margin-top: 1.5rem;">
                <button type="button" class="btn btn-secondary" id="cancelPaymentBtn">
                    <i class="fas fa-times"></i> Cancel
                </button>
                <button type="button" class="btn btn-primary" id="submitPaymentProofBtn">
                    <i class="fas fa-check"></i> Submit Payment Proof
                </button>
            </div>
        </form>
    </div>
</div>
    <!-- Tax Invoice Payment Modal -->
    <div class="modal" id="taxInvoicePaymentModal">
        <div class="modal-content">
            <h3><i class="fas fa-file-invoice-dollar"></i> Unlock Tax Invoice</h3>
            <p>Pay <strong>Rs. 50</strong> to unlock invoice <span id="invoiceNumberDisplay"></span></p>
            
            <div class="form-group">
                <label>Payment Method *</label>
                <select id="taxPaymentMethod" class="form-control" required>
                    <option value="">Select Method</option>
                    <option value="easypaisa">EasyPaisa</option>
                    <option value="jazzcash">JazzCash</option>
                </select>
            </div>
            
            <div class="form-group">
                <label>Transaction ID *</label>
                <input type="text" id="taxTransactionId" class="form-control" placeholder="Enter transaction ID" required>
            </div>
            
            <div class="form-group">
                <label>Invoice Number *</label>
                <input type="text" id="taxInvoiceNumber" class="form-control" placeholder="Enter invoice number" required>
            </div>
            
            <div class="form-group">
                <label>Payment Proof (Screenshot)</label>
                <input type="file" id="taxPaymentProof" accept="image/*" class="form-control" onchange="handleTaxPaymentProofUpload(event)">
                <div id="taxPaymentProofPreview" style="margin-top: 1rem;"></div>
            </div>
            
            <div class="form-actions">
                <button type="button" class="btn btn-secondary" onclick="closeModal('taxInvoicePaymentModal')">Cancel</button>
                <button type="button" class="btn btn-primary" onclick="submitTaxPayment()">Submit Payment</button>
            </div>
        </div>
    </div>

    <!-- Seller Tracking Update Modal -->
    <div class="modal" id="trackingUpdateModal">
        <div class="modal-content">
            <h3><i class="fas fa-truck"></i> Update Order Tracking</h3>
            <form id="trackingUpdateForm">
                <input type="hidden" id="trackingOrderId">
                
                <div class="form-group">
                    <label for="trackingStatus">Status</label>
                    <select id="trackingStatus" class="form-control" required>
                        <option value="confirmed">Confirmed</option>
                        <option value="packed">Packed</option>
                        <option value="shipped">Shipped</option>
                        <option value="out_for_delivery">Out for Delivery</option>
                        <option value="delivered">Delivered</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="trackingNumber">Tracking Number (if shipped)</label>
                    <input type="text" id="trackingNumber" class="form-control" placeholder="Enter tracking number">
                </div>
                
                <div class="form-group">
                    <label for="trackingNote">Notes</label>
                    <textarea id="trackingNote" class="form-control" rows="3" placeholder="Add any notes about this update"></textarea>
                </div>
                
                <div class="form-actions">
                    <button type="button" class="btn btn-secondary" onclick="closeModal('trackingUpdateModal')">Cancel</button>
                    <button type="submit" class="btn btn-primary">Update Tracking</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Image Zoom Modal -->
    <div class="zoom-overlay" id="zoomOverlay">
        <img id="zoomedImage" class="zoomed-image" src="" alt="Zoomed Image">
    </div>

    <!-- Invoice Modal -->
    <div class="invoice-modal" id="invoiceModal">
        <div class="invoice-content">
            <div class="invoice-header">
                <h2><i class="fas fa-file-invoice"></i> ORDER INVOICE</h2>
                <p>Jeeto Pakistan - Official Invoice</p>
            </div>
            <div id="invoiceDetails">
                <!-- Invoice content loaded here -->
            </div>
            <div style="text-align: center; margin-top: 2rem;">
                <button class="btn btn-primary" id="printInvoiceBtn">
                    <i class="fas fa-print"></i> Print Invoice
                </button>
                <button class="btn btn-secondary" id="closeInvoiceBtn">
                    <i class="fas fa-times"></i> Close
                </button>
            </div>
        </div>
    </div>

    <!-- Review Modal -->
    <div class="modal" id="reviewModal">
        <div class="modal-content">
            <h3>Add Review</h3>
            <form id="reviewForm">
                <div class="form-group">
                    <label>Rating *</label>
                    <div class="star-rating" id="starRating">
                        <i class="far fa-star" data-rating="1"></i>
                        <i class="far fa-star" data-rating="2"></i>
                        <i class="far fa-star" data-rating="3"></i>
                        <i class="far fa-star" data-rating="4"></i>
                        <i class="far fa-star" data-rating="5"></i>
                    </div>
                </div>
                <div class="form-group">
                    <label for="reviewTitle">Review Title</label>
                    <input type="text" id="reviewTitle" class="form-control" placeholder="Summarize your review">
                </div>
                <div class="form-group">
                    <label for="reviewText">Review *</label>
                    <textarea id="reviewText" class="form-control" rows="4" placeholder="Share your experience" required></textarea>
                </div>
                <div class="form-group">
                    <label><i class="fas fa-images"></i> Upload Images (Optional, Max 5)</label>
                    <input type="file" id="reviewImages" multiple accept="image/*" class="form-control" onchange="handleReviewImagesUpload(event)">
                    <div class="file-upload-preview" id="reviewImagesPreview"></div>
                </div>
                <div class="form-group">
                    <label><i class="fas fa-video"></i> Upload Video (Optional)</label>
                    <input type="file" id="reviewVideo" accept="video/*" class="form-control" onchange="handleReviewVideoUpload(event)">
                    <div class="file-upload-preview" id="reviewVideoPreview"></div>
                </div>
                <div class="form-actions">
                    <button type="button" class="btn btn-secondary" onclick="closeModal('reviewModal')">Cancel</button>
                    <button type="submit" class="btn btn-primary">Submit Review</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Order Success Modal -->
    <div class="modal" id="orderSuccessModal">
        <div class="modal-content" style="text-align: center;">
            <div style="background: var(--success); color: white; width: 80px; height: 80px; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto 1.5rem; font-size: 2.5rem;">
                <i class="fas fa-check"></i>
            </div>
            <h3>Order Placed Successfully!</h3>
            <p>Your order has been received and is being processed.</p>
            <p><strong>Order ID:</strong> <span id="successOrderId"></span></p>
            <p>You will receive a confirmation email shortly.</p>
            <div style="margin-top: 2rem;">
                <button class="btn btn-primary" onclick="showOrders()">
                    <i class="fas fa-box"></i> View Orders
                </button>
                <button class="btn btn-secondary" onclick="showHomePage()">
                    <i class="fas fa-home"></i> Continue Shopping
                </button>
            </div>
        </div>
    </div>

    <!-- Message Seller Modal -->
    <div class="modal" id="messageSellerModal">
        <div class="modal-content">
            <h3><i class="fas fa-comments"></i> Message Seller</h3>
            <form id="messageSellerForm">
                <input type="hidden" id="messageSellerId">
                <input type="hidden" id="messageProductId">
                
                <div class="form-group">
                    <label>Subject</label>
                    <input type="text" id="messageSubject" class="form-control" placeholder="Subject of your message">
                </div>
                
                <div class="form-group">
                    <label>Message *</label>
                    <textarea id="messageText" class="form-control" rows="5" placeholder="Type your message here..." required></textarea>
                </div>
                
                <div class="form-group">
                    <label><i class="fas fa-paperclip"></i> Attach Files (Optional)</label>
                    <input type="file" id="messageFiles" multiple accept="image/*,video/*,.pdf,.doc,.docx" class="form-control" onchange="handleMessageFilesUpload(event)">
                    <div class="file-upload-preview" id="messageFilesPreview"></div>
                </div>
                
                <div class="form-actions">
                    <button type="button" class="btn btn-secondary" onclick="closeModal('messageSellerModal')">Cancel</button>
                    <button type="submit" class="btn btn-primary">Send Message</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Toast Container -->
    <div class="toast-container" id="toastContainer"></div>

<!-- Switch to Desktop Button (Mobile Only) -->
<div class="switch-desktop-container" id="switchDesktopContainer">
    <button class="switch-desktop-btn" id="switchDesktopBtn" title="Switch to Desktop View">
        <i class="fas fa-desktop"></i>
        <span>Desktop View</span>
    </button>
</div>

<script>
 /// Add this at the beginning of your script section
const CLOUDINARY_CONFIG = {
    CLOUD_NAME: 'dlualhpsa',
    API_KEY: '462654888563439',
    UPLOAD_PRESET: 'jeetopakistan',
    
    // Upload URLs
    IMAGE_UPLOAD_URL: 'https://api.cloudinary.com/v1_1/dlualhpsa/image/upload',
    VIDEO_UPLOAD_URL: 'https://api.cloudinary.com/v1_1/dlualhpsa/video/upload',
    
    SETTINGS: {
        OVERWRITE: false,
        USE_FILENAME: true,
        UNIQUE_FILENAME: true,
        RESOURCE_TYPE: 'auto'
    }
};

  // Firebase configuration
  const firebaseConfig = {
  apiKey: "AIzaSyALmyT7HrUKJ1-8H4qKaOYrrGjT0hP1njc",
  authDomain: "daraz-27bf4.firebaseapp.com",
  projectId: "daraz-27bf4",
  storageBucket: "daraz-27bf4.firebasestorage.app",
  messagingSenderId: "560093096542",
  appId: "1:560093096542:web:d303cd7f982fed0edbe2cf"
};

  // Initialize Firebase
  try {
    firebase.initializeApp(firebaseConfig);
    console.log("Firebase connected successfully!");
    
    // Initialize Firebase services
    const db = firebase.firestore();
    const auth = firebase.auth();
    const storage = firebase.storage();
    
    // Test connection
    db.collection("test").get().then(() => {
      console.log("Firestore connected!");
    }).catch(error => {
      console.error("Firestore error:", error);
    });
    
  } catch (error) {
    console.error("Firebase initialization error:", error);
  }



// Check Firebase connection
const db = firebase.firestore();
const auth = firebase.auth();
const storage = firebase.storage();

async function testFirestoreConnection() {
    try {
        console.log('🔍 Testing Firestore connection...');
        
        // Create a test document (temporarily - will be deleted)
        const testDoc = {
            timestamp: new Date(),
            test: 'connection_test',
            platform: 'Jeeto Pakistan'
        };
        
        // Try to write to Firestore
        await db.collection('testConnection').doc('test').set(testDoc);
        console.log('✅ Firestore write successful');
        
        // Try to read from Firestore
        const doc = await db.collection('testConnection').doc('test').get();
        if (doc.exists) {
            console.log('✅ Firestore read successful:', doc.data());
        }
        
        // Clean up - delete test document
        await db.collection('testConnection').doc('test').delete();
        console.log('✅ Test document cleaned up');
        
        return true;
        
    } catch (error) {
        console.error('❌ Firestore connection failed:', error.code, error.message);
        
        // Check specific error types
        if (error.code === 'permission-denied') {
            console.log('⚠️ Permission denied. Please check Firestore rules.');
            showToast('Database permissions issue. Please contact support.', 'warning');
        } else if (error.code === 'unavailable') {
            console.log('⚠️ Firestore service unavailable.');
            showToast('Database service temporarily unavailable.', 'warning');
        } else {
            console.log('⚠️ Other Firestore error:', error);
            showToast('Database connection error. Please refresh the page.', 'error');
        }
        
        return false;
    }
}

// Add this to your initialization
document.addEventListener('DOMContentLoaded', async function() {
    await testFirestoreConnection();
    // ... rest of your initialization code
});

    // Global State
    let searchMasterList = []; 
    let currentSearchQuery = "";
    let currentUser = null;
    let currentSeller = null;
    let currentUserProfile = null;
    let cartItems = JSON.parse(localStorage.getItem('cartItems')) || [];
    let wishlistItems = JSON.parse(localStorage.getItem('wishlistItems')) || [];
    let products = [];
    let categories = [];
    let sellers = [];
    let buyerOrders = [];
    let sellerProducts = [];
    let sellerOrders = [];
    let currentOrderId = null;
    let notifications = [];
    let selectedProductId = null;
    let selectedReviewProductId = null;
    let currentPage = 1;
    const productsPerPage = 12;
    let debounceTimer;
    let selectedPaymentMethod = 'cod';
    let cloudinaryImages = [];
    let cloudinaryVideo = null;
    let heroSliderInterval = null;
    let starRating = 0;
    let currentChatId = null;
    let messages = [];
    let unreadMessagesCount = 0;
    let currentSort = 'default';
    let currentFilterCategory = null;
    let affiliateBalance = 0;
    let referrerCode = null;
    let availableBalance = 0;
    let pendingWithdrawal = 0;
    let productImages = [];
    let productVideo = null;
    let reviewImages = [];
    let reviewVideo = null; 
    let messageFiles = [];
    let paymentProof = null;
    let taxPaymentProof = null;
    let categoryOptions = {
       
        'Fashion': ['Clothing', 'Shoes', 'Accessories', 'Bags'],
        'Electronics': ['Mobile Phones', 'Laptops', 'Tablets', 'Accessories'],
        'Home & Kitchen': ['Furniture', 'Appliances', 'Cookware', 'Decor'],
        'Sports': ['Fitness Equipment', 'Outdoor Gear', 'Team Sports', 'Sportswear'],
        'Beauty': ['Skincare', 'Makeup', 'Fragrances', 'Hair Care'],
        'Books': ['Fiction', 'Non-Fiction', 'Educational', 'Children']
    };

    // DOM Elements
    const mainContent = document.getElementById('mainContent');
    const homePage = document.getElementById('homePage');
    const sellerPanel = document.getElementById('sellerPanel');
    const orderLockPaymentModal = document.getElementById('orderLockPaymentModal');
    const invoiceModal = document.getElementById('invoiceModal');
    const toastContainer = document.getElementById('toastContainer');
    const notificationPanel = document.getElementById('notificationPanel');
    const userMenu = document.getElementById('userMenu');
    const authModal = document.getElementById('authModal');
    const forgotPasswordModal = document.getElementById('forgotPasswordModal');
    const notificationCount = document.getElementById('notificationCount');
    const cartCount = document.getElementById('cartCount');
    const messagesCount = document.getElementById('messagesCount');
    const zoomOverlay = document.getElementById('zoomOverlay');
    const filterSection = document.getElementById('filterSection');
    const searchResultsSection = document.getElementById('searchResultsSection');

    // ==================== HELPER FUNCTIONS ====================
    function escapeHtml(text) {
        const div = document.createElement('div');
        div.textContent = text;
        return div.innerHTML;
    }

    function showToast(message, type = 'info') {
        const toast = document.createElement('div');
        toast.className = `toast ${type}`;
        toast.innerHTML = `
            <i class="fas fa-${getToastIcon(type)}"></i>
            <span>${escapeHtml(message)}</span>
        `;
        
        toastContainer.appendChild(toast);
        
        setTimeout(() => {
            toast.classList.add('show');
        }, 10);
        
        setTimeout(() => {
            toast.classList.remove('show');
            setTimeout(() => {
                toast.remove();
            }, 300);
        }, 3000);
    }

    function getToastIcon(type) {
        switch(type) {
            case 'success': return 'check-circle';
            case 'error': return 'exclamation-circle';
            case 'warning': return 'exclamation-triangle';
            case 'info': return 'info-circle';
            default: return 'info-circle';
        }
    }

    function closeModal(modalId) {
        document.getElementById(modalId).classList.remove('active');
    }

    function openModal(modalId) {
        document.getElementById(modalId).classList.add('active');
    }

    function updateStarRating() {
        const stars = document.querySelectorAll('#starRating i');
        stars.forEach((star, index) => {
            star.className = index < starRating ? 'fas fa-star active' : 'far fa-star';
        });
    }

    function getStatusBadgeClass(status) {
        switch(status) {
            case 'pending': return 'status-pending-badge';
            case 'confirmed': return 'status-approved-badge';
            case 'shipped': return 'status-shipped-badge';
            case 'delivered': return 'status-delivered-badge';
            case 'cancelled': return 'status-cancelled-badge';
            case 'locked': return 'status-locked-badge';
            default: return 'status-pending-badge';
        }
    }

    function getStatusText(status) {
        switch(status) {
            case 'pending': return 'Pending';
            case 'confirmed': return 'Confirmed';
            case 'shipped': return 'Shipped';
            case 'delivered': return 'Delivered';
            case 'cancelled': return 'Cancelled';
            case 'locked': return 'Locked';
            default: return status;
        }
    }

    function getWithdrawalStatusBadge(status) {
        switch(status) {
            case 'pending': return 'withdrawal-status-pending';
            case 'approved': return 'withdrawal-status-approved';
            case 'rejected': return 'withdrawal-status-rejected';
            case 'completed': return 'withdrawal-status-completed';
            default: return 'withdrawal-status-pending';
        }
    }

    function getWithdrawalStatusText(status) {
        switch(status) {
            case 'pending': return 'Pending';
            case 'approved': return 'Approved';
            case 'rejected': return 'Rejected';
            case 'completed': return 'Completed';
            default: return status;
        }
    }

    function zoomImage(src) {
        document.getElementById('zoomedImage').src = src;
        zoomOverlay.classList.add('active');
    }

    // ==================== INITIALIZATION ====================
    document.addEventListener('DOMContentLoaded', function() {
        console.log('🚀 Jeeto Pakistan E-commerce Platform Loading...');
        
        try {
            if (!firebase.apps.length) {
                firebase.initializeApp(firebaseConfig);
            }
            console.log('✅ Firebase initialized');
        } catch (error) {
            console.error('Firebase error:', error);
        }
        
        auth.onAuthStateChanged(async function(user) {
    console.log('🔄 Auth state changed. User:', user ? user.email : 'No user');
    
    if (user) {
        currentUser = user;
        console.log('✅ User logged in:', user.email);
        
        try {
            await checkIfSeller(user.uid);
            await loadUserProfile(user.uid);
            updateUIForLoggedInUser();
            showToast('Welcome back!', 'success');
        } catch (error) {
            console.error('Error loading user data:', error);
            showToast('Error loading user data', 'error');
        }
        
    } else {
        console.log('User logged out');
        updateUIForLoggedOutUser();
    }
}); 
        
        initializeData();
        initializeEventListeners();
        startCountdownTimer();
        initializeHeroSlider();
        
        console.log('✅ Platform ready!');
    });

    // ==================== AUTHENTICATION FUNCTIONS ====================
    async function checkIfSeller(userId) {
        try {
            const sellerDoc = await db.collection('sellers').doc(userId).get();
            if (sellerDoc.exists) {
                currentSeller = { id: sellerDoc.id, ...sellerDoc.data() };
                console.log('🎯 SELLER FOUND:', currentSeller.name);
                return true;
            }
            console.log('User is not a seller');
            currentSeller = null;
            return false;
        } catch (error) {
            console.error('Error checking seller:', error);
            currentSeller = null;
            return false;
        }
    }

    async function updateUIForLoggedInUser() {
        console.log('🎨 Updating UI for logged in user');
        
        const userStatus = document.getElementById('userStatus');
        if (currentUser) {
            userStatus.textContent = currentUser.displayName || currentUser.email.split('@')[0];
        }
        
        document.getElementById('profileBtn').style.display = 'flex';
        document.getElementById('ordersBtn').style.display = 'flex';
        document.getElementById('logoutBtn').style.display = 'flex';
        document.getElementById('wishlistBtn').style.display = 'flex';
        document.getElementById('notificationsBtn').style.display = 'flex';
        document.getElementById('messagesBtn').style.display = 'flex';
        document.getElementById('loginBtn').style.display = 'none';
        
        const sellerBtn = document.getElementById('sellerBtn');
        const sellerBadge = document.getElementById('sellerBadge');
        
        if (currentSeller) {
            console.log('🛍️ SHOWING SELLER BUTTON');
            sellerBtn.style.display = 'flex';
            sellerBtn.disabled = false;
            
            if (currentSeller.verified) {
                sellerBadge.style.display = 'inline-block';
                sellerBadge.textContent = currentSeller.verified === 'premium' ? 'PREMIUM' : 'PRO';
            } else {
                sellerBadge.style.display = 'none';
            }
        } else {
            console.log('❌ Hiding seller button - not a seller');
            sellerBtn.style.display = 'none';
            sellerBadge.style.display = 'none';
        }
        
        updateCartCount();
        await loadNotifications();
    }

    async function loadUserProfile(userId) {
        try {
            const userDoc = await db.collection('users').doc(userId).get();
            if (userDoc.exists) {
                currentUserProfile = {
                    id: userDoc.id,
                    ...userDoc.data()
                };
                console.log('✅ User profile loaded:', currentUserProfile);
                
                // Load affiliate balance
                if (currentUserProfile.affiliateBalance) {
                    affiliateBalance = currentUserProfile.affiliateBalance;
                }
                
                // Load referrer code
                if (currentUserProfile.referrerCode) {
                    referrerCode = currentUserProfile.referrerCode;
                }
            } else {
                console.log('📝 User profile not found, creating new one');
                currentUserProfile = {
                    id: userId,
                    email: currentUser.email,
                    displayName: currentUser.displayName || '',
                    phone: '',
                    address: '',
                    city: '',
                    userType: 'buyer',
                    affiliateBalance: 0,
                    referrerCode: generateReferrerCode()
                };
                await db.collection('users').doc(userId).set(currentUserProfile);
            }
        } catch (error) {
            console.error('Error loading user profile:', error);
            currentUserProfile = {
                id: userId,
                email: currentUser.email,
                displayName: currentUser.displayName || '',
                phone: '',
                address: '',
                city: '',
                userType: 'buyer',
                affiliateBalance: 0,
                referrerCode: generateReferrerCode()
            };
        }
    }

    function generateReferrerCode() {
        return 'JP' + Math.random().toString(36).substr(2, 8).toUpperCase();
    }

    function updateUIForLoggedOutUser() {
        console.log('🔄 Resetting UI for logged out user');
        
        document.getElementById('userStatus').textContent = 'Login';
        document.getElementById('profileBtn').style.display = 'none';
        document.getElementById('ordersBtn').style.display = 'none';
        document.getElementById('logoutBtn').style.display = 'none';
        document.getElementById('wishlistBtn').style.display = 'none';
        document.getElementById('notificationsBtn').style.display = 'none';
        document.getElementById('messagesBtn').style.display = 'none';
        document.getElementById('sellerBtn').style.display = 'none';
        document.getElementById('sellerBadge').style.display = 'none';
        document.getElementById('loginBtn').style.display = 'flex';
        
        currentUser = null;
        currentSeller = null;
        currentUserProfile = null;
        affiliateBalance = 0;
        referrerCode = null;
    }

    // ==================== DATA LOADING ====================
    async function initializeData() {
        await loadCategories();
        await loadProducts();
        await loadSellers();
        await loadFlashSales();
        await loadCustomerReviews();
        updateCartCount();
        updateNotificationCount();
    }

    async function loadCategories() {
        try {
            const defaultCategories = [
                { name: 'Electronics', icon: 'mobile-alt', description: 'Smartphones, Laptops, Accessories' },
                { name: 'Fashion', icon: 'tshirt', description: 'Clothing, Shoes, Accessories' },
                { name: 'Home & Kitchen', icon: 'home', description: 'Furniture, Appliances, Decor' },
                { name: 'Sports', icon: 'dumbbell', description: 'Fitness, Outdoor, Equipment' },
                { name: 'Books', icon: 'book', description: 'Fiction, Education, Literature' },
                { name: 'Beauty', icon: 'spa', description: 'Cosmetics, Skincare, Fragrances' }
            ];

            categories = defaultCategories;
            displayCategories();
            populateCategorySelect();
            
        } catch (error) {
            console.error('Error loading categories:', error);
            categories = defaultCategories;
            displayCategories();
            populateCategorySelect();
        }
    }

    async function loadProducts() {
    try {
        const snapshot = await db.collection('products')
            .where('status', '==', 'active')
            .get();

        products = snapshot.docs.map(doc => ({
            id: doc.id,
            ...doc.data()
        }));

        console.log('✅ Products loaded:', products.length);
        displayProducts();

    } catch (err) {
        console.error('❌ Product load failed:', err);
    }
}

function updateSellerProductsUI() {
    const productsList = document.getElementById('sellerProductsList');

    // Safety checks
    if (!productsList) {
        console.error('❌ sellerProductsList element not found in DOM');
        return;
    }

    if (!Array.isArray(sellerProducts)) {
        console.error('❌ sellerProducts is not an array:', sellerProducts);
        productsList.innerHTML = `
            <tr>
                <td colspan="7" style="text-align:center; padding:2rem; color:var(--error);">
                    Invalid product data
                </td>
            </tr>
        `;
        return;
    }

    // Delegate rendering to the main UI function
    displaySellerProducts();
}
    async function loadFlashSales() {
    try {
        const now = new Date();
        
        // SIMPLIFIED QUERY - Only use status filter
        const snapshot = await db.collection('flashSales')
            .where('status', '==', 'active')
            .get();

        // Filter and sort manually in JavaScript
        flashSales = snapshot.docs
            .map(doc => ({
                id: doc.id,
                ...doc.data(),
                endDate: doc.data().endDate?.toDate ? 
                    doc.data().endDate.toDate() : 
                    new Date(doc.data().endDate)
            }))
            .filter(sale => sale.endDate > now) // Filter active sales
            .sort((a, b) => b.endDate - a.endDate) // Sort by end date
            .slice(0, 20); // Limit to 20

        console.log('✅ Flash Sales loaded:', flashSales.length);
        displayFlashSaleProducts();
        
    } catch (error) {
        console.error('❌ Error loading flash sales:', error);
        flashSales = [];
        displayFlashSaleProducts();
    }
}
    

    async function loadSellers() {
        try {
            const snapshot = await db.collection('sellers').limit(50).get();
            sellers = snapshot.docs.map(doc => ({
                id: doc.id,
                ...doc.data()
            }));
            console.log(`👥 Loaded ${sellers.length} sellers`);
        } catch (error) {
            console.error('Error loading sellers:', error);
            sellers = [];
        }
    }

    async function loadCustomerReviews() {
        try {
            const reviewsContainer = document.getElementById('customerReviews');
            reviewsContainer.innerHTML = `
                <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 2rem;">
                    <div style="background: var(--white); padding: 1.5rem; border-radius: var(--radius); box-shadow: var(--shadow);">
                        <div class="product-rating" style="margin-bottom: 1rem;">
                            <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                        </div>
                        <p>"Excellent service! Fast delivery and authentic products."</p>
                        <div style="margin-top: 1rem; display: flex; align-items: center; gap: 1rem;">
                            <div style="width: 40px; height: 40px; background: var(--primary); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white;">A</div>
                            <div>
                                <strong>Ali Raza</strong>
                                <p style="color: var(--text-secondary); font-size: 0.9rem;">Customer</p>
                            </div>
                        </div>
                    </div>
                    <div style="background: var(--white); padding: 1.5rem; border-radius: var(--radius); box-shadow: var(--shadow);">
                        <div class="product-rating" style="margin-bottom: 1rem;">
                            <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="far fa-star"></i>
                        </div>
                        <p>"Good quality products at reasonable prices. Will shop again!"</p>
                        <div style="margin-top: 1rem; display: flex; align-items: center; gap: 1rem;">
                            <div style="width: 40px; height: 40px; background: var(--primary); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white;">S</div>
                            <div>
                                <strong>Sara Khan</strong>
                                <p style="color: var(--text-secondary); font-size: 0.9rem;">Customer</p>
                            </div>
                        </div>
                    </div>
                    <div style="background: var(--white); padding: 1.5rem; border-radius: var(--radius); box-shadow: var(--shadow);">
                        <div class="product-rating" style="margin-bottom: 1rem;">
                            <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star-half-alt"></i>
                        </div>
                        <p>"Secure payment options and responsive customer support."</p>
                        <div style="margin-top: 1rem; display: flex; align-items: center; gap: 1rem;">
                            <div style="width: 40px; height: 40px; background: var(--primary); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white;">M</div>
                            <div>
                                <strong>Mohammad</strong>
                                <p style="color: var(--text-secondary); font-size: 0.9rem;">Customer</p>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        } catch (error) {
            console.error('Error loading reviews:', error);
        }
    }

    async function loadNotifications() {
        if (!currentUser) return;
        
        try {
            // Check this line in your loadNotifications function:
const snapshot = await db.collection('notifications')
    .where('userId', '==', currentUser.uid) // Is it 'userId' or 'Userid'?
    .orderBy('createdAt', 'desc')
    .get();
            
            notifications = snapshot.docs.map(doc => ({
                id: doc.id,
                ...doc.data()
            }));
            
            updateNotificationCount();
            displayNotifications();
        } catch (error) {
            console.error('Error loading notifications:', error);
            notifications = [
                {
                    id: '1',
                    title: 'Welcome to Jeeto Pakistan!',
                    message: 'Thank you for joining our platform. Start shopping now!',
                    read: false,
                    createdAt: new Date()
                }
            ];
            updateNotificationCount();
            displayNotifications();
        }
    }

    function updateNotificationCount() {
        const unreadCount = notifications.filter(n => !n.read).length;
        notificationCount.textContent = unreadCount;
        notificationCount.style.display = unreadCount > 0 ? 'flex' : 'none';
    }

    async function loadUnreadMessagesCount() {
        if (!currentUser) return;
        
        try {
            const snapshot = await db.collection('messages')
                .where('receiverId', '==', currentUser.uid)
                .where('read', '==', false)
                .get();
            
            unreadMessagesCount = snapshot.size;
            updateMessagesCount();
        } catch (error) {
            console.error('Error loading unread messages count:', error);
            unreadMessagesCount = 0;
            updateMessagesCount();
        }
    }

    function updateMessagesCount() {
        messagesCount.textContent = unreadMessagesCount;
        messagesCount.style.display = unreadMessagesCount > 0 ? 'flex' : 'none';
    }

   // ==================== EVENT LISTENERS (FULL & SAFE VERSION) ====================
function initializeEventListeners() {
    // Safety helper: prevents the "null" error if an element is missing from HTML
    const addSafeListener = (id, event, fn) => {
        const el = document.getElementById(id);
        if (el) {
            el.addEventListener(event, fn);
        }
    };

    // --- NAVIGATION ---
    addSafeListener('homeBtn', 'click', showHomePage);
    addSafeListener('sellerBtn', 'click', showSellerPanel);
    addSafeListener('logoutBtn', 'click', handleLogout);
    addSafeListener('profileBtn', 'click', toggleUserMenu);
    addSafeListener('notificationsBtn', 'click', showNotificationsFullPage); // Updated for full page
    addSafeListener('wishlistBtn', 'click', showWishlist);
    addSafeListener('ordersBtn', 'click', showOrders);
    addSafeListener('cartBtn', 'click', showCart);
    addSafeListener('themeToggle', 'click', toggleTheme);

    // --- LINKS (Prevent Default) ---
    const navLinks = [
        { id: 'allProductsLink', fn: showAllProducts },
        { id: 'todaysDealsLink', fn: showFlashSale },
        { id: 'customerSupportLink', fn: openChatSupport }
    ];
    navLinks.forEach(link => {
        const el = document.getElementById(link.id);
        if (el) {
            el.addEventListener('click', (e) => {
                e.preventDefault();
                link.fn();
            });
        }
    });

    // Inside initializeEventListeners()
addSafeListener('searchBtn', 'click', performSearch);
const searchInput = document.getElementById('searchInput');
if (searchInput) {
    searchInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') performSearch();
    });
}

    // --- LOGIN / USER MENU ---
    const loginBtn = document.getElementById('loginBtn');
    if (loginBtn) {
        loginBtn.addEventListener('click', () => {
            if (!currentUser) {
                openAuthModal('buyerLogin');
            } else {
                toggleUserMenu();
            }
        });
    }

    // --- CATEGORY NAVIGATION ---
    document.querySelectorAll('.nav-links a[data-category]').forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            const category = e.target.closest('a').getAttribute('data-category');
            filterProductsByCategory(category);
        });
    });

    // --- SELLER PANEL ---
    addSafeListener('closeSellerPanelBtn', 'click', closeSellerPanel);
    document.querySelectorAll('.seller-nav a').forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            const tab = e.target.closest('a').getAttribute('data-tab');
            switchSellerTab(tab);
        });
    });

    // --- FORMS (ALL ORIGINAL FEATURES) ---
    const allForms = [
        { id: 'addProductForm', fn: handleAddProduct },
        { id: 'createFlashSaleForm', fn: handleCreateFlashSale },
        { id: 'sellerProfileForm', fn: handleSellerProfileUpdate },
        { id: 'withdrawalRequestForm', fn: handleWithdrawalRequest },
        { id: 'trackingUpdateForm', fn: updateOrderTracking },
        { id: 'buyerLoginForm', fn: handleBuyerLogin },
        { id: 'sellerLoginForm', fn: handleSellerLogin },
        { id: 'buyerRegisterForm', fn: handleRegisterAsBuyer },
        { id: 'sellerRegisterForm', fn: handleRegisterAsSeller },
        { id: 'forgotPasswordFormElement', fn: handleForgotPassword },
        { id: 'reviewForm', fn: submitReview },
        { id: 'messageSellerForm', fn: handleMessageSeller }
    ];

    allForms.forEach(form => {
        const el = document.getElementById(form.id);
        if (el) {
            el.addEventListener('submit', function(e) {
                e.preventDefault();
                form.fn(e);
            });
        }
    });

    // --- AUTH TABS ---
    document.querySelectorAll('.auth-tab').forEach(tab => {
        tab.addEventListener('click', (e) => {
            const tabName = e.target.getAttribute('data-tab');
            switchAuthTab(tabName);
        });
    });

    // --- MISC BUTTONS ---
    addSafeListener('cancelPaymentBtn', 'click', cancelPayment);
    addSafeListener('submitPaymentProofBtn', 'click', submitPaymentProof);
    addSafeListener('printInvoiceBtn', 'click', printInvoice);
    addSafeListener('closeInvoiceBtn', 'click', closeInvoice);
    addSafeListener('chatSupportBtn', 'click', openChatSupport);

    // --- STAR RATING ---
    const starRatingEl = document.getElementById('starRating');
    if (starRatingEl) {
        starRatingEl.addEventListener('click', (e) => {
            if (e.target.classList.contains('fa-star')) {
                starRating = parseInt(e.target.getAttribute('data-rating'));
                updateStarRating();
            }
        });
    }

    // --- IMAGE ZOOM ---
    const zoomOverlay = document.getElementById('zoomOverlay'); // Ensure ID exists
    if (zoomOverlay) {
        zoomOverlay.addEventListener('click', () => {
            zoomOverlay.classList.remove('active');
        });
    }

    // --- DROPDOWN CLOSING ---
    document.addEventListener('click', (e) => {
        const notifPanel = document.getElementById('notificationPanel');
        const userMenu = document.getElementById('userMenu');
        if (!e.target.closest('.action-btn') && !e.target.closest('#notificationPanel') && !e.target.closest('#userMenu')) {
            if (notifPanel) notifPanel.classList.remove('active');
            if (userMenu) userMenu.classList.remove('active');
        }
    });

    // --- INITIALIZE THEME ---
    const savedTheme = localStorage.getItem('theme') || 'light';
    document.documentElement.setAttribute('data-theme', savedTheme);
    const themeIcon = document.querySelector('#themeToggle i');
    if (themeIcon) {
        themeIcon.className = savedTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
    }
}

    // ==================== CATEGORY SPECIFIC OPTIONS ====================
    function showCategoryOptions() {
        const category = document.getElementById('productCategory').value;
        const optionsContainer = document.getElementById('categoryOptions');
        
        if (!category) {
            optionsContainer.classList.remove('active');
            optionsContainer.innerHTML = '';
            return;
        }
        
        optionsContainer.classList.add('active');
        
        let optionsHTML = '<h4>Category Specific Options</h4>';
        
        switch(category) {
            case 'Fashion':
                optionsHTML += `
                    <div class="option-group">
                        <label>Product Type</label>
                        <div class="option-row">
                            <div class="option-item">
                                <input type="radio" id="type_clothing" name="productType" value="Clothing" checked>
                                <label for="type_clothing">Clothing</label>
                            </div>
                            <div class="option-item">
                                <input type="radio" id="type_shoes" name="productType" value="Shoes">
                                <label for="type_shoes">Shoes</label>
                            </div>
                            <div class="option-item">
                                <input type="radio" id="type_accessories" name="productType" value="Accessories">
                                <label for="type_accessories">Accessories</label>
                            </div>
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <label>Size</label>
                            <select id="fashionSize" class="form-control">
                                <option value="">Select Size</option>
                                <option value="XS">XS</option>
                                <option value="S">S</option>
                                <option value="M">M</option>
                                <option value="L">L</option>
                                <option value="XL">XL</option>
                                <option value="XXL">XXL</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label>Color</label>
                            <input type="text" id="fashionColor" class="form-control" placeholder="e.g., Red, Blue, Black">
                        </div>
                    </div>
                    <div class="form-group">
                        <label>Material</label>
                        <input type="text" id="fashionMaterial" class="form-control" placeholder="e.g., Cotton, Silk, Leather">
                    </div>
                `;
                break;
                
            case 'Electronics':
                optionsHTML += `
                    <div class="option-group">
                        <label>Product Type</label>
                        <div class="option-row">
                            <div class="option-item">
                                <input type="radio" id="type_mobile" name="productType" value="Mobile" checked>
                                <label for="type_mobile">Mobile Phone</label>
                            </div>
                            <div class="option-item">
                                <input type="radio" id="type_laptop" name="productType" value="Laptop">
                                <label for="type_laptop">Laptop</label>
                            </div>
                            <div class="option-item">
                                <input type="radio" id="type_tablet" name="productType" value="Tablet">
                                <label for="type_tablet">Tablet</label>
                            </div>
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <label>Brand</label>
                            <input type="text" id="electronicsBrand" class="form-control" placeholder="e.g., Samsung, Apple, Dell">
                        </div>
                        <div class="form-group">
                            <label>Model</label>
                            <input type="text" id="electronicsModel" class="form-control" placeholder="e.g., Galaxy S21, iPhone 13">
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <label>Storage</label>
                            <select id="electronicsStorage" class="form-control">
                                <option value="">Select Storage</option>
                                <option value="64GB">64GB</option>
                                <option value="128GB">128GB</option>
                                <option value="256GB">256GB</option>
                                <option value="512GB">512GB</option>
                                <option value="1TB">1TB</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label>RAM</label>
                            <select id="electronicsRAM" class="form-control">
                                <option value="">Select RAM</option>
                                <option value="4GB">4GB</option>
                                <option value="6GB">6GB</option>
                                <option value="8GB">8GB</option>
                                <option value="12GB">12GB</option>
                                <option value="16GB">16GB</option>
                            </select>
                        </div>
                    </div>
                `;
                break;
                
            case 'Home & Kitchen':
                optionsHTML += `
                    <div class="option-group">
                        <label>Product Type</label>
                        <div class="option-row">
                            <div class="option-item">
                                <input type="radio" id="type_furniture" name="productType" value="Furniture" checked>
                                <label for="type_furniture">Furniture</label>
                            </div>
                            <div class="option-item">
                                <input type="radio" id="type_appliance" name="productType" value="Appliance">
                                <label for="type_appliance">Appliance</label>
                            </div>
                            <div class="option-item">
                                <input type="radio" id="type_cookware" name="productType" value="Cookware">
                                <label for="type_cookware">Cookware</label>
                            </div>
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <label>Material</label>
                            <input type="text" id="homeMaterial" class="form-control" placeholder="e.g., Wood, Steel, Glass">
                        </div>
                        <div class="form-group">
                            <label>Dimensions (cm)</label>
                            <input type="text" id="homeDimensions" class="form-control" placeholder="L x W x H (e.g., 50x30x40)">
                        </div>
                    </div>
                    <div class="form-group">
                        <label>Power Consumption (for appliances)</label>
                        <input type="text" id="homePower" class="form-control" placeholder="e.g., 1500W, 5-star rating">
                    </div>
                `;
                break;
                
            default:
                optionsHTML = '<p>No specific options for this category.</p>';
        }
        
        optionsContainer.innerHTML = optionsHTML;
    }

    // ==================== FIXED IMAGE UPLOAD FUNCTION ====================


function handleProductImageUpload(event) {
    const files = event.target.files;
    const previewContainer = document.getElementById('imagePreviewContainer');
    
    if (!previewContainer) {
        console.error('Preview container not found');
        return;
    }
    
    // Clear existing previews
    previewContainer.innerHTML = '';
    productImages = [];
    
    // Limit to 8 images
    const fileCount = Math.min(files.length, 8);
    
    for (let i = 0; i < fileCount; i++) {
        const file = files[i];
        
        // Validate file type
        if (!file.type.startsWith('image/')) {
            showToast(`File ${file.name} is not an image`, 'error');
            continue;
        }
        
        // Validate file size (max 5MB)
        if (file.size > 5 * 1024 * 1024) {
            showToast(`Image ${file.name} is too large (max 5MB)`, 'error');
            continue;
        }
        
        const reader = new FileReader();
        
        reader.onload = function(e) {
            // Create preview element
            const previewDiv = document.createElement('div');
            previewDiv.className = 'image-preview';
            previewDiv.style.position = 'relative';
            previewDiv.style.width = '100px';
            previewDiv.style.height = '100px';
            previewDiv.style.margin = '5px';
            
            previewDiv.innerHTML = `
                <img src="${e.target.result}" 
                     alt="Preview ${i + 1}" 
                     style="width: 100%; height: 100%; object-fit: cover; border-radius: var(--radius);">
                <button type="button" 
                        class="remove-image" 
                        onclick="removeProductImage(${productImages.length})"
                        style="position: absolute; top: 5px; right: 5px; background: var(--error); color: white; border: none; border-radius: 50%; width: 24px; height: 24px; cursor: pointer;">
                    <i class="fas fa-times"></i>
                </button>
            `;
            
            previewContainer.appendChild(previewDiv);
            
            // Store the file
            productImages.push({
                file: file,
                url: e.target.result,
                name: file.name,
                type: file.type
            });
            
            console.log(`Image ${i + 1} added:`, file.name);
        };
        
        reader.onerror = function() {
            console.error(`Error reading file ${file.name}`);
        };
        
        reader.readAsDataURL(file);
    }
    
    console.log(`Total images: ${productImages.length}`);
}

// Remove image function
function removeProductImage(index) {
    if (index >= 0 && index < productImages.length) {
        productImages.splice(index, 1);
        updateProductImagePreview();
    }
}

function updateProductImagePreview() {
    const previewContainer = document.getElementById('imagePreviewContainer');
    if (!previewContainer) return;
    
    previewContainer.innerHTML = '';
    
    productImages.forEach((image, index) => {
        const previewDiv = document.createElement('div');
        previewDiv.className = 'image-preview';
        previewDiv.style.position = 'relative';
        previewDiv.style.width = '100px';
        previewDiv.style.height = '100px';
        previewDiv.style.margin = '5px';
        
        previewDiv.innerHTML = `
            <img src="${image.url}" 
                 alt="Preview ${index + 1}" 
                 style="width: 100%; height: 100%; object-fit: cover; border-radius: var(--radius);">
            ${image.existing ? 
                `<span style="position: absolute; top: 5px; left: 5px; background: var(--info); color: white; font-size: 0.7rem; padding: 2px 5px; border-radius: 3px;">Existing</span>` : 
                ''}
            <button type="button" 
                    class="remove-image" 
                    onclick="removeProductImage(${index})"
                    style="position: absolute; top: 5px; right: 5px; background: var(--error); color: white; border: none; border-radius: 50%; width: 24px; height: 24px; cursor: pointer; display: flex; align-items: center; justify-content: center;">
                <i class="fas fa-times"></i>
            </button>
        `;
        
        previewContainer.appendChild(previewDiv);
    });
}

// ==================== FIXED VIDEO UPLOAD FUNCTION ====================

function handleProductVideoUpload(event) {
    const file = event.target.files[0];
    const previewContainer = document.getElementById('videoPreviewContainer');
    
    if (!file) {
        productVideo = null;
        return;
    }
    
    // Validate file type
    if (!file.type.startsWith('video/')) {
        showToast('Please upload a video file', 'error');
        event.target.value = '';
        return;
    }
    
    // Validate file size (max 50MB)
    if (file.size > 50 * 1024 * 1024) {
        showToast('Video is too large (max 50MB)', 'error');
        event.target.value = '';
        return;
    }
    
    const reader = new FileReader();
    
    reader.onload = function(e) {
        if (!previewContainer) {
            console.error('Video preview container not found');
            return;
        }
        
        previewContainer.innerHTML = `
            <div class="video-preview" style="position: relative; width: 200px; height: 150px; border-radius: var(--radius); overflow: hidden; margin-top: 10px;">
                <video controls style="width: 100%; height: 100%; object-fit: cover;">
                    <source src="${e.target.result}" type="${file.type}">
                    Your browser does not support the video tag.
                </video>
                <button type="button" 
                        class="remove-video" 
                        onclick="removeProductVideo()"
                        style="position: absolute; top: 5px; right: 5px; background: var(--error); color: white; border: none; border-radius: 50%; width: 24px; height: 24px; cursor: pointer; display: flex; align-items: center; justify-content: center;">
                    <i class="fas fa-times"></i>
                </button>
            </div>
        `;
        
        productVideo = {
            file: file,
            url: e.target.result,
            type: file.type,
            name: file.name
        };
        
        console.log('Video added:', file.name);
    };
    
    reader.onerror = function() {
        console.error('Error reading video file');
        showToast('Error reading video file', 'error');
    };
    
    reader.readAsDataURL(file);
}

function removeProductVideo() {
    productVideo = null;
    const previewContainer = document.getElementById('videoPreviewContainer');
    if (previewContainer) {
        previewContainer.innerHTML = '';
    }
    const videoInput = document.getElementById('productVideo');
    if (videoInput) {
        videoInput.value = '';
    }
}
 async function handleAddProduct(e) {
    e.preventDefault();

    const publishBtn = document.getElementById('publishProductBtn');
    const originalBtnText = publishBtn.innerHTML;
    publishBtn.disabled = true;
    publishBtn.innerHTML = '⏳ Saving...';

    try {
        if (!currentSeller || !currentSeller.id) {
            throw new Error('Seller not logged in');
        }

        // ================= BASIC DATA =================
        const productData = {
            code: document.getElementById('productCode').value.trim(),
            name: document.getElementById('productName').value.trim(),
            category: document.getElementById('productCategory').value,
            brand: document.getElementById('productBrand').value.trim() || null,
            price: parseFloat(document.getElementById('productPrice').value),
            quantity: parseInt(document.getElementById('productQuantity').value),
            discount: parseFloat(document.getElementById('productDiscount').value) || 0,
            weight: parseFloat(document.getElementById('productWeight').value) || null,
            description: document.getElementById('productDescription').value.trim(),
            sellerId: currentSeller.id,
            sellerName: currentSeller.shopName || currentSeller.name,
            status: 'active',
            updatedAt: new Date()
        };

        // ================= SPECIFICATIONS =================
        try {
            const specs = document.getElementById('productSpecifications')?.value?.trim();
            productData.specifications = specs ? JSON.parse(specs) : {};
        } catch (err) {
            productData.specifications = {};
        }

        // ================= IMAGES UPLOAD =================
        const newImages = productImages.filter(i => i.file && !i.existing);
        const existingImages = productImages
            .filter(i => i.existing && i.url)
            .map(i => i.url);

        let uploadedImageUrls = [];
        if (newImages.length > 0) {
            uploadedImageUrls = await uploadImagesToCloudinary(newImages);
        }

        productData.images = [...existingImages, ...uploadedImageUrls];

        if (productData.images.length === 0) {
            throw new Error('At least one product image is required');
        }

        // ================= VIDEO UPLOAD =================
        if (productVideo?.file && !productVideo.existing) {
            const videoUrl = await uploadVideoToCloudinary(productVideo);
            productData.video = videoUrl;
            productData.hasVideo = true;
        } 
        else if (productVideo?.existing && productVideo.url) {
            productData.video = productVideo.url;
            productData.hasVideo = true;
        } 
        else {
            productData.video = null;
            productData.hasVideo = false;
        }

        // ================= FIRESTORE SAVE =================
        // FIXED: Added typeof check to prevent ReferenceError if variable isn't declared
        if (window.editingProductId && typeof editingProductId !== 'undefined' && editingProductId !== null) {
            // UPDATE PRODUCT
            await db.collection('products').doc(editingProductId).update(productData);
            showToast('✅ Product updated successfully', 'success');
        } else {
            // CREATE PRODUCT
            productData.createdAt = new Date();
            productData.rating = 0;
            productData.reviewsCount = 0;

            await db.collection('products').add(productData);
            showToast('✅ Product published successfully', 'success');
        }

        // ================= RESET =================
        resetProductForm();
        editingProductId = null; // Clear the ID after saving
        switchSellerTab('products');
        loadSellerProducts();

    } catch (error) {
        console.error('❌ Product save error:', error);
        showToast('Error saving product: ' + error.message, 'error');
    } finally {
        publishBtn.disabled = false;
        publishBtn.innerHTML = originalBtnText;
    }
}

// Reset product form function
function resetProductForm() {
    document.getElementById('addProductForm').reset();
    document.getElementById('imagePreviewContainer').innerHTML = '';
    document.getElementById('videoPreviewContainer').innerHTML = '';
    document.getElementById('categoryOptions').classList.remove('active');
    document.getElementById('categoryOptions').innerHTML = '';
    
    // Update button text
    document.getElementById('publishProductBtn').innerHTML = '<i class="fas fa-upload"></i> Publish Product';
    
    // Reset variables
    productImages = [];
    productVideo = null;
    editingProductId = null;
}
    async function uploadImagesToCloudinary(images) {
    const imageUrls = [];
    console.log(`📤 Uploading ${images.length} images to Cloudinary...`);
    
    for (let i = 0; i < images.length; i++) {
        const image = images[i];
        
        if (!image || !image.file) {
            console.log(`⚠️ Image ${i + 1} has no file, skipping`);
            continue;
        }
        
        try {
            console.log(`🔄 Uploading image ${i + 1}: ${image.name || 'image-' + Date.now()}`);
            
            const formData = new FormData();
            formData.append('file', image.file);
            formData.append('upload_preset', CLOUDINARY_CONFIG.UPLOAD_PRESET);
            formData.append('cloud_name', CLOUDINARY_CONFIG.CLOUD_NAME);
            
            const response = await fetch(CLOUDINARY_CONFIG.IMAGE_UPLOAD_URL, {
                method: 'POST',
                body: formData
            });
            
            if (!response.ok) {
                throw new Error(`Upload failed: ${response.status}`);
            }
            
            const data = await response.json();
            
            if (data.secure_url) {
                imageUrls.push(data.secure_url);
                console.log(`✅ Image ${i + 1} uploaded: ${data.secure_url}`);
            } else {
                console.log(`⚠️ No URL returned for image ${i + 1}, using fallback`);
                imageUrls.push('https://via.placeholder.com/400x400?text=Product+Image');
            }
            
        } catch (error) {
            console.error(`❌ Error uploading image ${i + 1}:`, error);
            imageUrls.push('https://via.placeholder.com/400x400?text=Image+Error');
        }
    }
    
    console.log(`✅ Total ${imageUrls.length} images uploaded successfully`);
    return imageUrls;
}

    async function uploadVideoToCloudinary(videoObj) {
    if (!videoObj || !videoObj.file) {
        console.log('No video to upload');
        return null;
    }
    
    try {
        console.log('📹 Uploading video to Cloudinary...');
        
        const formData = new FormData();
        formData.append('file', videoObj.file);
        formData.append('upload_preset', CLOUDINARY_CONFIG.UPLOAD_PRESET);
        formData.append('cloud_name', CLOUDINARY_CONFIG.CLOUD_NAME);
        
        const response = await fetch(CLOUDINARY_CONFIG.VIDEO_UPLOAD_URL, {
            method: 'POST',
            body: formData
        });
        
        if (!response.ok) {
            throw new Error(`Video upload failed: ${response.status}`);
        }
        
        const data = await response.json();
        
        if (data.secure_url) {
            console.log('✅ Video uploaded successfully:', data.secure_url);
            return data.secure_url;
        } else {
            console.log('⚠️ No video URL returned');
            return null;
        }
        
    } catch (error) {
        console.error('❌ Error uploading video:', error);
        return null;
    }
}

    // ==================== PAYMENT PROOF HANDLERS ====================
    function handlePaymentProofUpload(event) {
        const file = event.target.files[0];
        if (!file) return;
        
        const reader = new FileReader();
        reader.onload = function(e) {
            const previewContainer = document.getElementById('paymentProofPreview');
            previewContainer.innerHTML = `
                <div class="file-preview">
                    <img src="${e.target.result}" alt="Payment Proof" style="width: 200px;">
                    <button type="button" class="remove-file" onclick="removePaymentProof()">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
            `;
            paymentProof = {
                file: file,
                url: e.target.result
            };
        };
        reader.readAsDataURL(file);
    }

    function removePaymentProof() {
        paymentProof = null;
        document.getElementById('paymentProofPreview').innerHTML = '';
        document.getElementById('paymentProof').value = '';
    }

    function handleTaxPaymentProofUpload(event) {
        const file = event.target.files[0];
        if (!file) return;
        
        const reader = new FileReader();
        reader.onload = function(e) {
            const previewContainer = document.getElementById('taxPaymentProofPreview');
            previewContainer.innerHTML = `
                <div class="file-preview">
                    <img src="${e.target.result}" alt="Payment Proof" style="width: 200px;">
                    <button type="button" class="remove-file" onclick="removeTaxPaymentProof()">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
            `;
            taxPaymentProof = {
                file: file,
                url: e.target.result
            };
        };
        reader.readAsDataURL(file);
    }

    function removeTaxPaymentProof() {
        taxPaymentProof = null;
        document.getElementById('taxPaymentProofPreview').innerHTML = '';
        document.getElementById('taxPaymentProof').value = '';
    }

    // ==================== SUBMIT PAYMENT PROOF ====================
    async function submitPaymentProof() {
        const transactionId = document.getElementById('orderTransactionId').value;
        const paymentMethod = document.getElementById('paymentMethodSelect').value;
        
        if (!transactionId) {
            showToast('Please enter transaction ID', 'error');
            return;
        }
        
        if (!paymentProof) {
            showToast('Please upload payment proof', 'error');
            return;
        }
        
        try {
            // Upload payment proof to Cloudinary
            const formData = new FormData();
            formData.append('file', paymentProof.file);
            formData.append('upload_preset', uploadPreset);
            formData.append('cloud_name', cloudName);
            
            const response = await fetch(`https://api.cloudinary.com/v1_1/${cloudName}/image/upload`, {
                method: 'POST',
                body: formData
            });
            
            const data = await response.json();
            
            // Save payment verification to Firestore
            const paymentData = {
                orderId: currentOrderId,
                transactionId: transactionId,
                paymentMethod: paymentMethod,
                paymentProof: data.secure_url,
                status: 'pending',
                createdAt: new Date()
            };
            
            await db.collection('paymentVerifications').add(paymentData);
            
            // Update order status
            await db.collection('orders').doc(currentOrderId).update({
                paymentStatus: 'verified',
                invoiceLocked: false
            });
            
            showToast('Payment proof submitted successfully!', 'success');
            closeModal('orderLockPaymentModal');
            loadSellerOrders();
            
        } catch (error) {
            console.error('Error submitting payment proof:', error);
            showToast('Error submitting payment proof', 'error');
        }
    }

    // ==================== SUBMIT TAX PAYMENT ====================
    async function submitTaxPayment() {
        const transactionId = document.getElementById('taxTransactionId').value;
        const paymentMethod = document.getElementById('taxPaymentMethod').value;
        const invoiceNumber = document.getElementById('taxInvoiceNumber').value;
        
        if (!transactionId || !paymentMethod || !invoiceNumber) {
            showToast('Please fill all required fields', 'error');
            return;
        }
        
        if (!taxPaymentProof) {
            showToast('Please upload payment proof', 'error');
            return;
        }
        
        try {
            // Upload payment proof to Cloudinary
            const formData = new FormData();
            formData.append('file', taxPaymentProof.file);
            formData.append('upload_preset', uploadPreset);
            formData.append('cloud_name', cloudName);
            
            const response = await fetch(`https://api.cloudinary.com/v1_1/${cloudName}/image/upload`, {
                method: 'POST',
                body: formData
            });
            
            const data = await response.json();
            
            // Save tax payment to Firestore
            const taxPaymentData = {
                invoiceNumber: invoiceNumber,
                transactionId: transactionId,
                paymentMethod: paymentMethod,
                paymentProof: data.secure_url,
                status: 'pending',
                createdAt: new Date()
            };
            
            await db.collection('taxPayments').add(taxPaymentData);
            
            showToast('Tax payment submitted for verification!', 'success');
            closeModal('taxInvoicePaymentModal');
            
        } catch (error) {
            console.error('Error submitting tax payment:', error);
            showToast('Error submitting tax payment', 'error');
        }
    }

    // ==================== ORDER PLACEMENT WITH PAYMENT ====================
    async function placeOrderWithPayment(orderData) {
        try {
            // Save order to Firestore
            const orderRef = await db.collection('orders').add(orderData);
            
            // If payment method is EasyPaisa or JazzCash, show payment verification
            if (selectedPaymentMethod === 'easypaisa' || selectedPaymentMethod === 'jazzcash') {
                currentOrderId = orderRef.id;
                document.getElementById('orderTransactionId').value = '';
                document.getElementById('paymentMethodSelect').value = selectedPaymentMethod;
                paymentProof = null;
                document.getElementById('paymentProofPreview').innerHTML = '';
                openModal('orderLockPaymentModal');
            } else {
                // For COD, show success directly
                showOrderSuccess(orderRef.id);
            }
            
            // Clear cart
            cartItems = [];
            saveCart();
            updateCartCount();
            
        } catch (error) {
            console.error('Error placing order:', error);
            showToast('Error placing order', 'error');
        }
    }

    // ==================== MESSAGE SYSTEM ====================
    async function loadMessages() {
    try {
        if (!currentUser) return;
        
        console.log('📨 Loading messages for user:', currentUser.uid);
        
        // Method 1: Get all chats where user is participant
        const chatsSnapshot = await db.collection('chats')
            .where('participants', 'array-contains', currentUser.uid)
            .get();
        
        console.log('Found chats:', chatsSnapshot.size);
        
        let chats = [];
        let unreadCount = 0;
        
        chatsSnapshot.forEach(doc => {
            const chatData = {
                id: doc.id,
                ...doc.data()
            };
            
            // Check if there are unread messages
            if (chatData.lastMessage && chatData.lastMessage.senderId !== currentUser.uid && !chatData.lastMessage.read) {
                unreadCount++;
            }
            
            chats.push(chatData);
        });
        
        // Sort by lastMessageTime (in memory)
        chats.sort((a, b) => {
            const timeA = a.lastMessageTime?.toDate ? a.lastMessageTime.toDate() : new Date(a.lastMessageTime || 0);
            const timeB = b.lastMessageTime?.toDate ? b.lastMessageTime.toDate() : new Date(b.lastMessageTime || 0);
            return timeB - timeA; // Newest first
        });
        
        messages = chats;
        unreadMessagesCount = unreadCount;
        
        // Update UI
        updateMessagesCount();
        displayMessages();
        
        console.log('✅ Messages loaded successfully');
        
    } catch (error) {
        console.error('❌ Error loading messages:', error);
        
        // Fallback: Try simpler query
        if (error.code === 'failed-precondition') {
            console.log('Trying fallback query...');
            await loadMessagesFallback();
        } else {
            showToast('Error loading messages', 'error');
        }
    }
}

// Fallback function without complex queries
async function loadMessagesFallback() {
    try {
        // Simple query - just get all chats and filter locally
        const allChatsSnapshot = await db.collection('chats').limit(100).get();
        
        let userChats = [];
        
        allChatsSnapshot.forEach(doc => {
            const chatData = doc.data();
            if (chatData.participants && chatData.participants.includes(currentUser.uid)) {
                userChats.push({
                    id: doc.id,
                    ...chatData
                });
            }
        });
        
        // Sort locally
        userChats.sort((a, b) => {
            const timeA = a.lastMessageTime?.toDate ? a.lastMessageTime.toDate() : new Date(a.lastMessageTime || 0);
            const timeB = b.lastMessageTime?.toDate ? b.lastMessageTime.toDate() : new Date(b.lastMessageTime || 0);
            return timeB - timeA;
        });
        
        messages = userChats;
        updateMessagesCount();
        displayMessages();
        
    } catch (error) {
        console.error('Fallback also failed:', error);
        messages = [];
    }
}

    async function openChat(chatId, userId) {
        currentChatId = chatId;
        
        // Update chat header
        document.getElementById('sellerChatHeader').innerHTML = `
            <h4>Chat with Customer ${userId.slice(-6)}</h4>
        `;
        
        // Enable message input
        document.getElementById('sellerMessageInput').disabled = false;
        document.getElementById('sellerSendMessageBtn').disabled = false;
        
        // Load messages
        await loadChatMessages(chatId);
    }

    async function loadChatMessages(chatId) {
        try {
            const messagesQuery = await db.collection('chats').doc(chatId)
                .collection('messages')
                .orderBy('timestamp', 'asc')
                .get();
            
            const messagesContainer = document.getElementById('sellerChatMessages');
            messagesContainer.innerHTML = '';
            
            messagesQuery.forEach(doc => {
                const message = doc.data();
                const messageElement = document.createElement('div');
                messageElement.className = `message ${message.senderId === currentSeller.id ? 'sent' : 'received'}`;
                messageElement.innerHTML = `
                    <p>${escapeHtml(message.text)}</p>
                    <small style="opacity: 0.7;">${new Date(message.timestamp.toDate()).toLocaleTimeString()}</small>
                `;
                messagesContainer.appendChild(messageElement);
            });
            
            // Scroll to bottom
            messagesContainer.scrollTop = messagesContainer.scrollHeight;
            
        } catch (error) {
            console.error('Error loading messages:', error);
        }
    }

    async function sendSellerMessage() {
        const input = document.getElementById('sellerMessageInput');
        const messageText = input.value.trim();
        
        if (!messageText || !currentChatId || !currentSeller) return;
        
        try {
            // Add message to Firestore
            await db.collection('chats').doc(currentChatId).collection('messages').add({
                text: messageText,
                senderId: currentSeller.id,
                timestamp: new Date()
            });
            
            // Update chat last message
            await db.collection('chats').doc(currentChatId).update({
                lastMessage: messageText,
                lastMessageTime: new Date()
            });
            
            // Clear input
            input.value = '';
            
            // Reload messages
            await loadChatMessages(currentChatId);
            
        } catch (error) {
            console.error('Error sending message:', error);
            showToast('Error sending message', 'error');
        }
    }

    // ==================== UI FUNCTIONS ====================
    function showHomePage() {
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        homePage.style.display = 'block';
        sellerPanel.style.display = 'none';
        
        document.querySelectorAll('.modal.active, .payment-verification.active, .invoice-modal.active').forEach(modal => {
            modal.classList.remove('active');
        });
        
        notificationPanel.classList.remove('active');
        userMenu.classList.remove('active');
        authModal.classList.remove('active');
        forgotPasswordModal.classList.remove('active');
        zoomOverlay.classList.remove('active');
        
        // Hide filter and search sections by default
        filterSection.style.display = 'none';
        searchResultsSection.style.display = 'none';
        
        // Reset search input
        document.getElementById('searchInput').value = '';
    }

    function showAllProducts() {
        showHomePage();
        filterSection.style.display = 'block';
        const featuredContainer = document.getElementById('featuredProducts');
        if (products.length > 0) {
            featuredContainer.innerHTML = products.map(product => createProductCard(product)).join('');
        }
        updateSortButtons();
    }

let currentMediaIndex = 0;
let mediaItemsCount = 0;
let mediaItemsArray = [];

function initializeMediaSlider() {
    const sliderContainer = document.getElementById('sliderContainer');
    if (!sliderContainer) return;
    
    mediaItemsArray = Array.from(sliderContainer.querySelectorAll('.slider-item'));
    mediaItemsCount = mediaItemsArray.length;
    currentMediaIndex = 0;
    
    updateMediaCounter();
}

function previousMedia() {
    if (mediaItemsCount <= 1) return;
    
    currentMediaIndex = (currentMediaIndex - 1 + mediaItemsCount) % mediaItemsCount;
    goToMedia(currentMediaIndex);
}

function nextMedia() {
    if (mediaItemsCount <= 1) return;
    
    currentMediaIndex = (currentMediaIndex + 1) % mediaItemsCount;
    goToMedia(currentMediaIndex);
}

function goToMedia(index) {
    if (index < 0 || index >= mediaItemsCount) return;
    
    currentMediaIndex = index;
    
    // Update slider items
    mediaItemsArray.forEach((item, i) => {
        item.classList.toggle('active', i === index);
        
        // Pause videos when not active
        if (item.dataset.type === 'video') {
            const video = item.querySelector('video');
            if (video) {
                if (i === index) {
                    // Don't autoplay, let user click play
                } else {
                    video.pause();
                    video.currentTime = 0;
                }
            }
        }
    });
    
    // Update thumbnails
    document.querySelectorAll('.thumbnail-item').forEach((thumb, i) => {
        thumb.classList.toggle('active', i === index);
    });
    
    updateMediaCounter();
}

function updateMediaCounter() {
    const currentEl = document.getElementById('currentMedia');
    const totalEl = document.getElementById('totalMedia');
    
    if (currentEl) currentEl.textContent = currentMediaIndex + 1;
    if (totalEl) totalEl.textContent = mediaItemsCount;
}

function centerActiveThumbnail() {
    const thumbnailNav = document.getElementById('thumbnailNav');
    const activeThumb = thumbnailNav?.querySelector('.thumbnail-item.active');
    
    if (thumbnailNav && activeThumb) {
        const containerWidth = thumbnailNav.clientWidth;
        const thumbOffset = activeThumb.offsetLeft;
        const thumbWidth = activeThumb.clientWidth;
        
        thumbnailNav.scrollLeft = thumbOffset - (containerWidth / 2) + (thumbWidth / 2);
    }
}
    function showFlashSale() {
        showHomePage();
        filterSection.style.display = 'block';
        
        const featuredContainer = document.getElementById('featuredProducts');
        
        if (products.length > 0) {
            featuredContainer.innerHTML = products.map(product => createProductCard(product)).join('');
        }
        updateSortButtons();
    }

    function showAllCategories() {
        showHomePage();
        const grid = document.getElementById('categoriesGrid');
        grid.innerHTML = categories.map(category => `
            <div class="category-card" onclick="filterProductsByCategory('${category.name}')">
                <div class="category-icon">
                    <i class="fas fa-${category.icon}"></i>
                </div>
                <div class="category-name">${category.name}</div>
                <div style="font-size: 0.8rem; color: var(--text-secondary); margin-top: 0.5rem;">
                    ${category.description}
                </div>
            </div>
        `).join('');
    }

    function showTopSellers() {
        showHomePage();
        const featuredContainer = document.getElementById('featuredProducts');
        
        if (products.length > 0) {
            featuredContainer.innerHTML = products.map(product => createProductCard(product)).join('');
        }
        updateSortButtons();
    }

    function showSellerPanel() {
        if (!currentSeller) {
            showToast('You are not registered as a seller', 'error');
            return;
        }
        
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        sellerPanel.style.display = 'block';
        
        document.getElementById('sellerShopNameDisplay').textContent = currentSeller.shopName || currentSeller.name;
        loadSellerDashboard();
        switchSellerTab('dashboard');
    }

    function closeSellerPanel() {
        sellerPanel.style.display = 'none';
        showHomePage();
    }

    function switchSellerTab(tabName) {
        document.querySelectorAll('.seller-tab').forEach(tab => {
            tab.classList.remove('active');
        });
        
        document.querySelectorAll('.seller-nav a').forEach(link => {
            link.classList.remove('active');
        });
        
        const tabElement = document.getElementById(`${tabName}Tab`);
        if (tabElement) {
            tabElement.classList.add('active');
        }
        
        const navLink = document.querySelector(`.seller-nav a[data-tab="${tabName}"]`);
        if (navLink) {
            navLink.classList.add('active');
        }
        
        switch(tabName) {
            case 'dashboard':
                loadSellerDashboard();
                break;
            case 'profile':
                loadSellerProfile();
                break;
            case 'products':
                loadSellerProducts();
                break;
            case 'addProduct':
                populateCategorySelect();
                populateFlashSaleProductSelect();
                break;
            case 'flashSaleManagement':
                loadFlashSaleManagement();
                break;
            case 'orders':
                loadSellerOrders();
                break;
            case 'tracking':
                loadSellerTracking();
                break;
            case 'withdrawal':
                loadWithdrawalManagement();
                break;
            case 'taxInvoice':
                loadTaxInvoices();
                break;
            case 'earnings':
                loadSellerEarnings();
                break;
            case 'orderHistory':
                loadOrderHistory();
                break;
            case 'messages':
                loadSellerMessages();
                break;
            case 'support':
                loadAdminSupport();
                break;
        }
    }

    // In createProductCard function, add video indicator:
function createProductCard(product) {
    const finalPrice = calculateFinalPrice(product.price, product.discount || 0);
    
    return `
        <div class="product-card" onclick="viewProductDetails('${product.id}')">
            ${product.discount > 0 ? `<div class="product-badge">${product.discount}% OFF</div>` : ''}
            ${product.video ? `<div class="product-badge" style="background: var(--info); right: 10px; left: auto;"><i class="fas fa-video"></i></div>` : ''}
            
            <img src="${product.images && product.images.length > 0 ? product.images[0] : 'https://via.placeholder.com/400x400'}" 
                 alt="${escapeHtml(product.name)}" 
                 class="product-image">
            
            <!-- Rest of your product card HTML -->
        </div>
    `;
}

    function generateStarRating(rating) {
        let stars = '';
        for (let i = 1; i <= 5; i++) {
            if (i <= Math.floor(rating)) {
                stars += '<i class="fas fa-star"></i>';
            } else if (i === Math.ceil(rating) && rating % 1 !== 0) {
                stars += '<i class="fas fa-star-half-alt"></i>';
            } else {
                stars += '<i class="far fa-star"></i>';
            }
        }
        return stars;
    }

    // ==================== CART FUNCTIONS ====================
    function addToCart(productId) {
    const product = products.find(p => p.id === productId);
    if (!product) return;

    // CHECK FOR FLASH SALE PRICE
    const activeFlashSale = flashSales.find(fs => fs.productId === productId);
    const priceToCharge = activeFlashSale ? activeFlashSale.flashPrice : (product.discount ? product.price * (1 - product.discount / 100) : product.price);

    const cartItem = {
        id: product.id,
        name: product.name,
        price: priceToCharge, // This now uses the flash sale price
        image: product.images?.[0] || product.image,
        quantity: 1,
        isFlashSale: !!activeFlashSale
    };

    // Existing logic to push to cartItems...
    const existingItem = cartItems.find(item => item.id === productId);
    if (existingItem) {
        existingItem.quantity += 1;
    } else {
        cartItems.push(cartItem);
    }

    updateCartCount();
    showToast('Product added to cart', 'success');
}

    function saveCart() {
        localStorage.setItem('cartItems', JSON.stringify(cartItems));
    }
function saveCart() {
    localStorage.setItem('cartItems', JSON.stringify(cartItems));
}

// ==================== SHARE FUNCTIONS ====================

let shareDropdownVisible = false;

function toggleShareDropdown() {
    const shareDropdown = document.getElementById('shareDropdown');
    shareDropdownVisible = !shareDropdownVisible;
    
    if (shareDropdownVisible) {
        shareDropdown.classList.add('active');
        
        // Close when clicking outside
        setTimeout(() => {
            document.addEventListener('click', closeShareDropdownOutside);
        }, 10);
    } else {
        shareDropdown.classList.remove('active');
        document.removeEventListener('click', closeShareDropdownOutside);
    }
}

function closeShareDropdownOutside(e) {
    const shareContainer = document.querySelector('.share-container');
    const shareButton = document.getElementById('shareButton');
    
    if (!shareContainer.contains(e.target) && e.target !== shareButton) {
        shareDropdownVisible = false;
        document.getElementById('shareDropdown').classList.remove('active');
        document.removeEventListener('click', closeShareDropdownOutside);
    }
}

function generateShareLink(productId) {
    const baseUrl = window.location.origin;
    return `${baseUrl}/product/${productId}`;
}

function generateShareText(productName, description) {
    const maxLength = 100;
    let text = `Check out "${productName}" on Jeeto Pakistan!`;
    
    if (description) {
        const shortDesc = description.length > maxLength ? 
            description.substring(0, maxLength) + '...' : 
            description;
        text += `\n\n${shortDesc}`;
    }
    
    text += `\n\nAvailable at: ${generateShareLink(productId)}`;
    
    return encodeURIComponent(text);
}

async function shareOnFacebook(productId, productName) {
    const shareUrl = generateShareLink(productId);
    const text = generateShareText(productName, '');
    
    const facebookUrl = `https://www.facebook.com/sharer/sharer.php?u=${encodeURIComponent(shareUrl)}&quote=${text}`;
    
    window.open(facebookUrl, '_blank', 'width=600,height=400');
    showToast('Opening Facebook share...', 'info');
}

async function shareOnWhatsApp(productId, productName) {
    const shareUrl = generateShareLink(productId);
    const text = generateShareText(productName, '');
    
    const whatsappUrl = `https://wa.me/?text=${text}`;
    
    window.open(whatsappUrl, '_blank', 'width=600,height=400');
    showToast('Opening WhatsApp...', 'info');
}

async function shareOnTwitter(productId, productName) {
    const shareUrl = generateShareLink(productId);
    const text = generateShareText(productName, '');
    
    const twitterUrl = `https://twitter.com/intent/tweet?text=${text}&url=${encodeURIComponent(shareUrl)}`;
    
    window.open(twitterUrl, '_blank', 'width=600,height=400');
    showToast('Opening Twitter...', 'info');
}

async function copyProductLink(productId) {
    const shareUrl = generateShareLink(productId);
    
    try {
        await navigator.clipboard.writeText(shareUrl);
        showToast('Product link copied to clipboard!', 'success');
    } catch (err) {
        // Fallback for older browsers
        const textArea = document.createElement('textarea');
        textArea.value = shareUrl;
        document.body.appendChild(textArea);
        textArea.select();
        document.execCommand('copy');
        document.body.removeChild(textArea);
        
        showToast('Product link copied to clipboard!', 'success');
    }
}

// Function to share with images
async function shareProductWithImages(productId, productName, images) {
    if (!navigator.share) {
        showToast('Web Share API not supported in your browser', 'warning');
        return;
    }
    
    try {
        const shareUrl = generateShareLink(productId);
        const text = generateShareText(productName, '');
        
        const shareData = {
            title: productName,
            text: text,
            url: shareUrl
        };
        
        // Convert image URLs to files for sharing
        if (images && images.length > 0) {
            const imageFiles = [];
            
            // Note: This requires CORS-compatible images
            for (const imageUrl of images.slice(0, 3)) { // Limit to 3 images
                try {
                    const response = await fetch(imageUrl);
                    const blob = await response.blob();
                    const file = new File([blob], 'product-image.jpg', { type: blob.type });
                    imageFiles.push(file);
                } catch (error) {
                    console.log('Failed to fetch image:', imageUrl);
                }
            }
            
            if (imageFiles.length > 0) {
                shareData.files = imageFiles;
            }
        }
        
        await navigator.share(shareData);
        showToast('Product shared successfully!', 'success');
        
    } catch (error) {
        if (error.name !== 'AbortError') {
            console.error('Error sharing:', error);
            showToast('Failed to share product', 'error');
        }
    }
}

    function updateCartCount() {
        const totalItems = cartItems.reduce((sum, item) => sum + item.quantity, 0);
        cartCount.textContent = totalItems;
        cartCount.style.display = totalItems > 0 ? 'flex' : 'none';
    }

    // ==================== THEME TOGGLE ====================
    function toggleTheme() {
        const currentTheme = document.documentElement.getAttribute('data-theme');
        const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
        
        document.documentElement.setAttribute('data-theme', newTheme);
        localStorage.setItem('theme', newTheme);
        
        const themeIcon = document.querySelector('#themeToggle i');
        themeIcon.className = newTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        
        showToast(`${newTheme === 'dark' ? 'Dark' : 'Light'} mode activated`, 'info');
    }

    // ==================== COUNTDOWN TIMER ====================
    function startCountdownTimer() {
        const endTime = new Date();
        endTime.setHours(endTime.getHours() + 2);
        endTime.setMinutes(endTime.getMinutes() + 30);
        
        function updateCountdown() {
            const now = new Date();
            const diff = endTime - now;
            
            if (diff <= 0) {
                document.getElementById('countdown-hours').textContent = '00';
                document.getElementById('countdown-minutes').textContent = '00';
                document.getElementById('countdown-seconds').textContent = '00';
                return;
            }
            
            const hours = Math.floor(diff / (1000 * 60 * 60));
            const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((diff % (1000 * 60)) / 1000);
            
            document.getElementById('countdown-hours').textContent = hours.toString().padStart(2, '0');
            document.getElementById('countdown-minutes').textContent = minutes.toString().padStart(2, '0');
            document.getElementById('countdown-seconds').textContent = seconds.toString().padStart(2, '0');
        }
        
        updateCountdown();
        setInterval(updateCountdown, 1000);
    }

    // ==================== HERO SLIDER ====================
    function initializeHeroSlider() {
        const slides = document.querySelectorAll('.slide');
        let currentSlide = 0;
        
        function showSlide(index) {
            slides.forEach(slide => slide.classList.remove('active'));
            slides[index].classList.add('active');
        }
        
        function nextSlide() {
            currentSlide = (currentSlide + 1) % slides.length;
            showSlide(currentSlide);
        }
        
        showSlide(0);
        heroSliderInterval = setInterval(nextSlide, 5000);
    }

    // ==================== DISPLAY FUNCTIONS ====================
    function displayCategories() {
        const categoriesGrid = document.getElementById('categoriesGrid');
        categoriesGrid.innerHTML = categories.map(category => `
            <div class="category-card" onclick="filterProductsByCategory('${category.name}')">
                <div class="category-icon">
                    <i class="fas fa-${category.icon}"></i>
                </div>
                <div class="category-name">${category.name}</div>
            </div>
        `).join('');
    }

    function displayProducts() {
        const featuredContainer = document.getElementById('featuredProducts');
        const startIndex = (currentPage - 1) * productsPerPage;
        const endIndex = startIndex + productsPerPage;
        const productsToShow = products.slice(startIndex, endIndex);
        
        featuredContainer.innerHTML = productsToShow.map(product => createProductCard(product)).join('');
        
        updatePagination();
    }

    function displayFlashSaleProducts() {
        const flashSaleContainer = document.getElementById('flashSaleProducts');
        const flashSaleProducts = products.filter(product => 
            flashSales.some(fs => fs.productId === product.id)
        ).slice(0, 4);
        
        flashSaleContainer.innerHTML = flashSaleProducts.map(product => {
            const flashSale = flashSales.find(fs => fs.productId === product.id);
            const finalPrice = flashSale ? flashSale.flashPrice : product.price;
            
            return `
                <div class="product-card" onclick="viewProductDetails('${product.id}')">
                    <div class="product-badge" style="background: var(--error);">FLASH SALE</div>
                    <img src="${product.images[0]}" alt="${escapeHtml(product.name)}" class="product-image">
                    <div class="product-info">
                        <div class="product-category">${escapeHtml(product.category)}</div>
                        <div class="product-name">${escapeHtml(product.name)}</div>
                        <div class="product-price">
                            <span class="current-price">Rs. ${finalPrice.toLocaleString()}</span>
                            <span class="original-price">Rs. ${product.price.toLocaleString()}</span>
                        </div>
                        <div class="product-seller">Sold by: ${escapeHtml(product.sellerName)}</div>
                        <div class="product-actions">
                            // Inside your displayFlashSaleProducts loop:
<button clas(); addFlashSaleToCart('${item.id}', '${item.flashSale.id}')">
    <i class="fas fa-bolt"></i> Grab Deal
</button>
                        </div>
                    </div>
                </div>
            `;
        }).join('');
    }

    function displayTopSellers() {
        const topSellersGrid = document.getElementById('topSellersGrid');
        const uniqueSellers = [...new Set(products.map(p => p.sellerName))].slice(0, 6);
        
        topSellersGrid.innerHTML = uniqueSellers.map(seller => `
            <div class="category-card" onclick="filterProductsBySeller('${seller}')">
                <div class="category-icon">
                    <i class="fas fa-store"></i>
                </div>
                <div class="category-name">${escapeHtml(seller)}</div>
                <div style="font-size: 0.8rem; color: var(--text-secondary); margin-top: 0.5rem;">
                    Top Rated Seller
                </div>
            </div>
        `).join('');
    }

    function updatePagination() {
        const totalPages = Math.ceil(products.length / productsPerPage);
        const paginationContainer = document.getElementById('productPagination');
        
        if (totalPages <= 1) {
            paginationContainer.innerHTML = '';
            return;
        }
        
        let paginationHTML = '';
        
        // Previous button
        if (currentPage > 1) {
            paginationHTML += `<button class="page-btn" onclick="changePage(${currentPage - 1})"><i class="fas fa-chevron-left"></i></button>`;
        }
        
        // Page numbers
        for (let i = 1; i <= totalPages; i++) {
            if (i === currentPage) {
                paginationHTML += `<button class="page-btn active">${i}</button>`;
            } else if (i === 1 || i === totalPages || (i >= currentPage - 2 && i <= currentPage + 2)) {
                paginationHTML += `<button class="page-btn" onclick="changePage(${i})">${i}</button>`;
            } else if (i === currentPage - 3 || i === currentPage + 3) {
                paginationHTML += `<span class="page-btn" style="border: none; background: transparent;">...</span>`;
            }
        }
        
        // Next button
        if (currentPage < totalPages) {
            paginationHTML += `<button class="page-btn" onclick="changePage(${currentPage + 1})"><i class="fas fa-chevron-right"></i></button>`;
        }
        
        paginationContainer.innerHTML = paginationHTML;
    }

    function changePage(page) {
        currentPage = page;
        displayProducts();
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    // ==================== SEARCH FUNCTIONS ====================
    function performSearch() {
        const searchTerm = document.getElementById('searchInput').value.trim().toLowerCase();
        
        if (!searchTerm) {
            searchResultsSection.style.display = 'none';
            filterSection.style.display = 'none';
            return;
        }
        
        const searchResults = products.filter(product => 
            product.name.toLowerCase().includes(searchTerm) ||
            product.category.toLowerCase().includes(searchTerm) ||
            product.description.toLowerCase().includes(searchTerm) ||
            product.sellerName.toLowerCase().includes(searchTerm)
        );
        
        const searchResultsContainer = document.getElementById('searchResults');
        searchResultsContainer.innerHTML = searchResults.map(product => createProductCard(product)).join('');
        
        searchResultsSection.style.display = 'block';
        filterSection.style.display = 'block';
    }

    function clearSearch() {
        document.getElementById('searchInput').value = '';
        searchResultsSection.style.display = 'none';
        filterSection.style.display = 'none';
    }

    // ==================== FILTER FUNCTIONS ====================
    function filterProductsByCategory(category) {
        currentFilterCategory = category;
        const filteredProducts = products.filter(product => product.category === category);
        
        const featuredContainer = document.getElementById('featuredProducts');
        featuredContainer.innerHTML = filteredProducts.map(product => createProductCard(product)).join('');
        
        filterSection.style.display = 'block';
        document.getElementById('categoryFilter').value = category;
        
        showToast(`Showing ${category} products`, 'info');
    }

    function filterProductsBySeller(sellerName) {
        const filteredProducts = products.filter(product => product.sellerName === sellerName);
        
        const featuredContainer = document.getElementById('featuredProducts');
        featuredContainer.innerHTML = filteredProducts.map(product => createProductCard(product)).join('');
        
        filterSection.style.display = 'block';
        showToast(`Showing products from ${sellerName}`, 'info');
    }

    function sortProducts(sortType) {
        currentSort = sortType;
        let sortedProducts = [...products];
        
        switch(sortType) {
            case 'price-low':
                sortedProducts.sort((a, b) => {
                    const priceA = a.price - (a.price * (a.discount || 0) / 100);
                    const priceB = b.price - (b.price * (b.discount || 0) / 100);
                    return priceA - priceB;
                });
                break;
            case 'price-high':
                sortedProducts.sort((a, b) => {
                    const priceA = a.price - (a.price * (a.discount || 0) / 100);
                    const priceB = b.price - (b.price * (b.discount || 0) / 100);
                    return priceB - priceA;
                });
                break;
            case 'newest':
                sortedProducts.sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt));
                break;
            case 'rating':
                sortedProducts.sort((a, b) => b.rating - a.rating);
                break;
            default:
                sortedProducts = products;
        }
        
        const featuredContainer = document.getElementById('featuredProducts');
        featuredContainer.innerHTML = sortedProducts.map(product => createProductCard(product)).join('');
        
        updateSortButtons();
    }

    function updateSortButtons() {
        document.querySelectorAll('.sort-btn').forEach(btn => {
            btn.classList.remove('active');
            if (btn.textContent.toLowerCase().includes(currentSort.replace('-', ' '))) {
                btn.classList.add('active');
            }
        });
    }

    function toggleAdvancedFilter() {
        const advancedFilter = document.getElementById('advancedFilter');
        advancedFilter.classList.toggle('active');
    }

    function applyPriceFilter() {
        const minPrice = parseFloat(document.getElementById('minPrice').value) || 0;
        const maxPrice = parseFloat(document.getElementById('maxPrice').value) || Infinity;
        
        const filteredProducts = products.filter(product => {
            const finalPrice = product.price - (product.price * (product.discount || 0) / 100);
            return finalPrice >= minPrice && finalPrice <= maxPrice;
        });
        
        const featuredContainer = document.getElementById('featuredProducts');
        featuredContainer.innerHTML = filteredProducts.map(product => createProductCard(product)).join('');
        
        showToast(`Filtered products by price range`, 'info');
    }

    // ==================== WISHLIST FUNCTIONS ====================
    function addToWishlist(productId) {
        const product = products.find(p => p.id === productId);
        if (!product) return;
        
        if (!wishlistItems.find(item => item.id === productId)) {
            wishlistItems.push({
                id: product.id,
                name: product.name,
                price: product.price,
                image: product.images[0],
                category: product.category
            });
            
            localStorage.setItem('wishlistItems', JSON.stringify(wishlistItems));
            showToast('Added to wishlist!', 'success');
        } else {
            showToast('Already in wishlist', 'info');
        }
    }

    function showWishlist() {
        showHomePage();
        // Implementation for wishlist page
        showToast('Wishlist feature coming soon!', 'info');
    }

    // ==================== CHECKOUT FUNCTIONS ====================
    function showCart() {
        showHomePage();
        // Implementation for cart page
        showToast('Cart feature coming soon!', 'info');
    }

    function showOrders() {
        showHomePage();
        // Implementation for orders page
        showToast('Orders feature coming soon!', 'info');
    }

    // ==================== PROFILE FUNCTIONS ====================
    function toggleUserMenu() {
        userMenu.classList.toggle('active');
        notificationPanel.classList.remove('active');
    }

    function toggleNotifications() {
        notificationPanel.classList.toggle('active');
        userMenu.classList.remove('active');
    }

    function viewBuyerProfile() {
        showHomePage();
        // Implementation for buyer profile
        showToast('Profile feature coming soon!', 'info');
    }

    function viewSettings() {
        showHomePage();
        // Implementation for settings
        showToast('Settings feature coming soon!', 'info');
    }

    function showMessagesPage() {
        showHomePage();
        // Implementation for messages page
        showToast('Messages feature coming soon!', 'info');
    }

    // ==================== AUTH FUNCTIONS ====================
    function openAuthModal(tabName) {
        authModal.classList.add('active');
        switchAuthTab(tabName);
    }

    function closeAuthModal() {
        authModal.classList.remove('active');
    }

    function switchAuthTab(tabName) {
        document.querySelectorAll('.auth-form').forEach(form => {
            form.classList.remove('active');
        });
        
        document.querySelectorAll('.auth-tab').forEach(tab => {
            tab.classList.remove('active');
        });
        
        const form = document.getElementById(`${tabName}Form`);
        const tab = document.querySelector(`.auth-tab[data-tab="${tabName}"]`);
        
        if (form) form.classList.add('active');
        if (tab) tab.classList.add('active');
    }

    // ==================== ENHANCED AUTH UI FUNCTIONS ====================

function showLogin() {
    const loginForm = document.getElementById('loginForm');
    const registerForm = document.getElementById('registerForm');
    const forgotForm = document.getElementById('forgotPasswordForm');
    
    if (loginForm && registerForm && forgotForm) {
        loginForm.classList.add('active');
        registerForm.classList.remove('active');
        forgotForm.classList.remove('active');
        showBuyerLogin();
    }
}

function showRegister() {
    const loginForm = document.getElementById('loginForm');
    const registerForm = document.getElementById('registerForm');
    const forgotForm = document.getElementById('forgotPasswordForm');
    
    if (loginForm && registerForm && forgotForm) {
        registerForm.classList.add('active');
        loginForm.classList.remove('active');
        forgotForm.classList.remove('active');
        showBuyerRegister();
    }
}

function showForgotPassword(type) {
    const loginForm = document.getElementById('loginForm');
    const registerForm = document.getElementById('registerForm');
    const forgotForm = document.getElementById('forgotPasswordForm');
    const userTypeSelect = document.getElementById('forgotUserType');
    
    if (loginForm && registerForm && forgotForm) {
        forgotForm.classList.add('active');
        loginForm.classList.remove('active');
        registerForm.classList.remove('active');
        
        if (type && userTypeSelect) {
            userTypeSelect.value = type;
        }
    }
}

function showBuyerLogin() {
    const buyerForm = document.getElementById('buyerLoginFormElement');
    const sellerForm = document.getElementById('sellerLoginFormElement');
    
    if (buyerForm && sellerForm) {
        buyerForm.style.display = 'block';
        sellerForm.style.display = 'none';
        
        // Update tabs
        const buyerTab = document.querySelector('.auth-tab[data-tab="buyerLogin"]');
        const sellerTab = document.querySelector('.auth-tab[data-tab="sellerLogin"]');
        
        if (buyerTab) buyerTab.classList.add('active');
        if (sellerTab) sellerTab.classList.remove('active');
    }
}

function showSellerLogin() {
    const buyerForm = document.getElementById('buyerLoginFormElement');
    const sellerForm = document.getElementById('sellerLoginFormElement');
    
    if (buyerForm && sellerForm) {
        sellerForm.style.display = 'block';
        buyerForm.style.display = 'none';
        
        // Update tabs
        const buyerTab = document.querySelector('.auth-tab[data-tab="buyerLogin"]');
        const sellerTab = document.querySelector('.auth-tab[data-tab="sellerLogin"]');
        
        if (sellerTab) sellerTab.classList.add('active');
        if (buyerTab) buyerTab.classList.remove('active');
    }
}

function showBuyerRegister() {
    const buyerForm = document.getElementById('buyerRegisterFormElement');
    const sellerForm = document.getElementById('sellerRegisterFormElement');
    
    if (buyerForm && sellerForm) {
        buyerForm.style.display = 'block';
        sellerForm.style.display = 'none';
        
        // Update tabs
        const buyerTab = document.querySelector('.auth-tab[data-tab="buyerRegister"]');
        const sellerTab = document.querySelector('.auth-tab[data-tab="sellerRegister"]');
        
        if (buyerTab) buyerTab.classList.add('active');
        if (sellerTab) sellerTab.classList.remove('active');
    }
}

function showSellerRegister() {
    const buyerForm = document.getElementById('buyerRegisterFormElement');
    const sellerForm = document.getElementById('sellerRegisterFormElement');
    
    if (buyerForm && sellerForm) {
        sellerForm.style.display = 'block';
        buyerForm.style.display = 'none';
        
        // Update tabs
        const buyerTab = document.querySelector('.auth-tab[data-tab="buyerRegister"]');
        const sellerTab = document.querySelector('.auth-tab[data-tab="sellerRegister"]');
        
        if (sellerTab) sellerTab.classList.add('active');
        if (buyerTab) buyerTab.classList.remove('active');
    }
}

// Password strength checker
function checkPasswordStrength(password, type) {
    let strength = 0;
    const bar = document.getElementById(`${type}StrengthBar`);
    
    if (!bar) return;
    
    if (password.length >= 8) strength += 25;
    if (/[A-Z]/.test(password)) strength += 25;
    if (/[0-9]/.test(password)) strength += 25;
    if (/[^A-Za-z0-9]/.test(password)) strength += 25;
    
    bar.style.width = `${strength}%`;
    
    if (strength < 50) {
        bar.style.backgroundColor = "var(--error)";
    } else if (strength < 75) {
        bar.style.backgroundColor = "var(--warning)";
    } else {
        bar.style.backgroundColor = "var(--success)";
    }
}

// Phone number formatting (keep your existing formatPhoneNumber too)
function formatPhoneInput(input) {
    let value = input.value.replace(/\D/g, '');
    if (value.length > 0) {
        value = value.substring(0, 11);
        if (value.length <= 4) {
            input.value = value;
        } else {
            input.value = value.substring(0, 4) + '-' + value.substring(4);
        }
    }
}

// Initialize enhanced auth system
function initializeEnhancedAuth() {
    console.log('🔧 Initializing enhanced auth system...');
    
    // Password strength monitoring
    const buyerPassword = document.getElementById('buyerPassword');
    const sellerPassword = document.getElementById('sellerRegPassword');
    
    if (buyerPassword) {
        buyerPassword.addEventListener('input', function() {
            checkPasswordStrength(this.value, 'buyer');
        });
    }
    
    if (sellerPassword) {
        sellerPassword.addEventListener('input', function() {
            checkPasswordStrength(this.value, 'seller');
        });
    }
    
    // Input focus effects
    const inputs = document.querySelectorAll('.auth-modal .input input, .auth-modal .input textarea');
    inputs.forEach(input => {
        input.addEventListener('focus', function() {
            this.parentElement.style.transform = 'translateY(-5px)';
        });
        
        input.addEventListener('blur', function() {
            this.parentElement.style.transform = 'translateY(0)';
        });
    });
    
    // Phone input formatting (for new inputs)
    const phoneInputs = document.querySelectorAll('.auth-modal input[type="tel"]');
    phoneInputs.forEach(input => {
        input.addEventListener('input', function(e) {
            formatPhoneInput(this);
        });
    });
    
    console.log('✅ Enhanced auth system initialized');
}

// ==================== END OF ENHANCED UI FUNCTIONS ====================

    function showForgotPassword() {
        closeAuthModal();
        forgotPasswordModal.classList.add('active');
    }

    function closeForgotPassword() {
        forgotPasswordModal.classList.remove('active');
    }

    function togglePassword(inputId, button) {
        const input = document.getElementById(inputId);
        if (input.type === 'password') {
            input.type = 'text';
            button.innerHTML = '<i class="far fa-eye-slash"></i>';
        } else {
            input.type = 'password';
            button.innerHTML = '<i class="far fa-eye"></i>';
        }
    }

    function formatPhoneNumber(input) {
        let value = input.value.replace(/\D/g, '');
        if (value.startsWith('0')) {
            value = value.substring(1);
        }
        if (value.length > 10) {
            value = value.substring(0, 10);
        }
        
        if (value.length > 0) {
            input.value = '0' + value.replace(/(\d{3})(\d{7})/, '$1-$2');
        }
    }

    async function handleLogout() {
        try {
            await auth.signOut();
            showToast('Logged out successfully', 'success');
            showHomePage();
        } catch (error) {
            console.error('Logout error:', error);
            showToast('Logout failed', 'error');
        }
    }



    async function viewProductDetails(productId, inSellerPanel = false) {
    try {
        // 1. Find product with safety check
        const product = products.find(p => p.id === productId);
        if (!product) {
            console.error('Product not found:', productId);
            return;
        }

        selectedProductId = productId;

        // 2. Hide all other pages
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });

        // 3. Show and clear the details page
        const detailsPage = document.getElementById('productDetailsPage');
        const detailsContent = document.getElementById('productDetailsContent');
        detailsPage.style.display = 'block';
        detailsContent.innerHTML = ''; // Clear old content immediately

        // 4. Create safe media items (The "White Page" Fix)
        // This ensures that even if images are missing, the code doesn't crash
        const safeImages = Array.isArray(product.images) ? product.images : [];
        const finalPrice = typeof calculateFinalPrice === 'function' ? 
                           calculateFinalPrice(product.price, product.discount || 0) : 
                           product.price;

        let productHTML = `
            <div class="section">
                <div style="display: flex; gap: 2rem; margin-bottom: 2rem;">
                    <button class="btn btn-secondary" onclick="${inSellerPanel ? "switchSellerTab('products')" : "showHomePage()"}">
                        <i class="fas fa-arrow-left"></i> Back
                    </button>
                </div>
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 3rem;">
                    <div>
                        <div class="enhanced-slider" id="enhancedSlider">
                            <div class="slider-container" id="sliderContainer">
                                ${(() => {
                                    let html = '';
                                    if (safeImages.length > 0) {
                                        safeImages.forEach((img, index) => {
                                            html += `<div class="slider-item ${index === 0 ? 'active' : ''}">
                                                        <img src="${img}" alt="Product" onclick="zoomImage('${img}')" style="cursor: pointer; max-width:100%;">
                                                     </div>`;
                                        });
                                    } else {
                                        // Placeholder for products like 'Abdul' if they have no image
                                        html = `<div class="slider-item active"><img src="https://via.placeholder.com/400?text=No+Image"></div>`;
                                    }
                                    return html;
                                })()}
                            </div>
                        </div>
                    </div>
                    <div>
                        <h1 style="color: var(--primary); margin-bottom: 0.5rem;">${escapeHtml(product.name)}</h1>
                        <div class="product-price" style="margin: 1.5rem 0;">
                            <span class="current-price" style="font-size: 2rem;">Rs. ${finalPrice.toLocaleString()}</span>
                        </div>
                        <p style="color: var(--text-secondary); line-height: 1.8;">${escapeHtml(product.description || 'No description available.')}</p>
                        ${!inSellerPanel ? `
                            <button class="btn btn-primary btn-lg" style="width: 100%; margin-top: 2rem;" onclick="addToCart('${product.id}')">
                                <i class="fas fa-shopping-cart"></i> Add to Cart
                            </button>
                        ` : ''}
                    </div>
                </div>
            </div>
        `;

        detailsContent.innerHTML = productHTML;

        // 5. Initialize slider with a tiny delay
        setTimeout(() => {
            if (typeof initializeMediaSlider === 'function') initializeMediaSlider();
        }, 50);

    } catch (error) {
        console.error('CRITICAL ERROR:', error);
        showToast('Error loading details: ' + error.message, 'error');
    }
}
function createProductDetailsHTML(product, inSellerPanel = false) {
    // Safety check for price and discount
    const price = Number(product.price) || 0;
    const discount = Number(product.discount) || 0;
    const finalPrice = typeof calculateFinalPrice === 'function' ? 
                       calculateFinalPrice(price, discount) : price;

    // Safety check for images - this prevents the "White Window"
    const images = Array.isArray(product.images) ? product.images : [];
    const hasVideo = !!product.video;

    return `
        <div class="section">
            <div style="margin-bottom: 2rem;">
                <button class="btn btn-secondary" onclick="${inSellerPanel ? "switchSellerTab('products')" : "showHomePage()"}">
                    <i class="fas fa-arrow-left"></i> Back
                </button>
            </div>
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 3rem;">
                <div>
                    <div class="enhanced-slider" id="enhancedSlider">
                        <div class="slider-container" id="sliderContainer">
                            ${images.length > 0 ? images.map((img, i) => `
                                <div class="slider-item ${i === 0 ? 'active' : ''}" data-index="${i}" data-type="image">
                                    <img src="${img}" alt="Image ${i+1}" onclick="zoomImage('${img}')">
                                </div>
                            `).join('') : `<div class="slider-item active"><img src="https://via.placeholder.com/400?text=No+Image"></div>`}
                            
                            ${hasVideo ? `
                                <div class="slider-item" data-index="${images.length}" data-type="video">
                                    <video controls style="width:100%; height:100%;"><source src="${product.video}"></video>
                                </div>
                            ` : ''}
                        </div>
                    </div>
                </div>
                <div>
                    <h2>${product.name || 'Unnamed Product'}</h2>
                    <p class="current-price">Rs. ${finalPrice.toLocaleString()}</p>
                    <p>${product.description || 'No description available.'}</p>
                    ${!inSellerPanel ? `<button class="btn btn-primary" onclick="addToCart('${product.id}')">Add to Cart</button>` : ''}
                </div>
            </div>
        </div>
    `;
}
// Helper function for description and specs
function createDescriptionAndSpecsHTML(product) {
    return `
        <div style="background: var(--white); padding: 2rem; border-radius: var(--radius-lg); box-shadow: var(--shadow-lg);">
            <div style="display: grid; grid-template-columns: 2fr 1fr; gap: 2rem;">
                <!-- Description -->
                <div>
                    <h3><i class="fas fa-align-left"></i> Description</h3>
                    <div style="margin-top: 1rem; line-height: 1.6; white-space: pre-line;">
                        ${product.description || 'No description available.'}
                    </div>
                </div>
                
                <!-- Specifications -->
                <div>
                    <h3><i class="fas fa-list-alt"></i> Specifications</h3>
                    <div style="margin-top: 1rem;">
                        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
                            <div style="color: var(--text-secondary);">Product Code:</div>
                            <div><strong>${product.code || 'N/A'}</strong></div>
                            
                            <div style="color: var(--text-secondary);">Category:</div>
                            <div><strong>${product.category || 'N/A'}</strong></div>
                            
                            ${product.brand ? `
                                <div style="color: var(--text-secondary);">Brand:</div>
                                <div><strong>${product.brand}</strong></div>
                            ` : ''}
                            
                            ${product.weight ? `
                                <div style="color: var(--text-secondary);">Weight:</div>
                                <div><strong>${product.weight} kg</strong></div>
                            ` : ''}
                            
                            <div style="color: var(--text-secondary);">Seller:</div>
                            <div><strong>${product.sellerName}</strong></div>
                            
                            <div style="color: var(--text-secondary);">Status:</div>
                            <div>
                                <span class="status-badge ${product.status === 'active' ? 'status-active' : 'status-inactive'}">
                                    ${product.status || 'active'}
                                </span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    `;
}

// Helper function for product info
function createProductInfoHTML(product, finalPrice, inSellerPanel) {
    return `
        <!-- Rating -->
        <div class="product-rating" style="margin-bottom: 1.5rem;">
            ${generateStarRating(product.rating || 0)}
            <span style="color: var(--text-secondary); margin-left: 10px;">
                (${product.reviewsCount || 0} reviews)
            </span>
        </div>
        
        <!-- Price -->
        <div class="product-price" style="margin-bottom: 2rem;">
            <span class="current-price" style="font-size: 2rem;">
                Rs. ${finalPrice.toLocaleString()}
            </span>
            ${product.discount > 0 ? `
                <span class="original-price" style="font-size: 1.5rem;">
                    Rs. ${product.price.toLocaleString()}
                </span>
                <span style="color: var(--success); font-weight: 600;">
                    Save Rs. ${(product.price * product.discount / 100).toLocaleString()}
                </span>
            ` : ''}
        </div>
        
        <!-- Seller Info -->
        <div style="background: var(--accent); padding: 1rem; border-radius: var(--radius); margin-bottom: 2rem;">
            <h4><i class="fas fa-store"></i> Seller Information</h4>
            <p><strong>${product.sellerName}</strong></p>
            ${inSellerPanel ? `
                <p style="color: var(--text-secondary); font-size: 0.9rem;">This is your product</p>
            ` : `
                <div style="display: flex; gap: 1rem; margin-top: 0.5rem;">
                    <button class="btn btn-sm btn-info" onclick="messageSeller('${product.sellerId}', '${product.id}')">
                        <i class="fas fa-comment"></i> Message Seller
                    </button>
                    <button class="btn btn-sm btn-secondary" onclick="viewSellerProfile('${product.sellerId}')">
                        <i class="fas fa-store"></i> View Shop
                    </button>
                </div>
            `}
        </div>
        
        <!-- Seller Actions (only in seller panel) -->
        ${inSellerPanel ? `
            <div style="background: var(--primary-light); padding: 1rem; border-radius: var(--radius); margin-bottom: 2rem;">
                <h4><i class="fas fa-cog"></i> Seller Actions</h4>
                <div style="display: flex; gap: 1rem; margin-top: 1rem; flex-wrap: wrap;">
                    <button class="btn btn-warning" onclick="editProduct('${product.id}')">
                        <i class="fas fa-edit"></i> Edit Product
                    </button>
                    <button class="btn btn-info" onclick="switchSellerTab('flashSaleManagement')">
                        <i class="fas fa-bolt"></i> Add to Flash Sale
                    </button>
                    <button class="btn ${product.status === 'active' ? 'btn-secondary' : 'btn-success'}" 
                            onclick="toggleProductStatus('${product.id}', '${product.status}')">
                        <i class="fas fa-power-off"></i> ${product.status === 'active' ? 'Deactivate' : 'Activate'}
                    </button>
                    <button class="btn btn-danger" onclick="deleteProduct('${product.id}')">
                        <i class="fas fa-trash"></i> Delete
                    </button>
                </div>
            </div>
        ` : ''}
        
        <!-- Quantity & Actions (only for buyers) -->
        ${!inSellerPanel ? `
            <div style="margin-bottom: 2rem;">
                <label style="display: block; margin-bottom: 0.5rem; font-weight: 500;">
                    <i class="fas fa-cubes"></i> Quantity
                </label>
                <div style="display: flex; align-items: center; gap: 1rem;">
                    <div style="display: flex; align-items: center; border: 1px solid var(--border); border-radius: var(--radius); overflow: hidden;">
                        <button class="btn btn-sm" onclick="updateQuantity('decrease')" style="border-radius: 0; border: none; padding: 8px 12px;">
                            <i class="fas fa-minus"></i>
                        </button>
                        <input type="number" id="productQuantityInput" value="1" min="1" max="${product.quantity}" 
                               style="width: 60px; text-align: center; border: none; padding: 8px;">
                        <button class="btn btn-sm" onclick="updateQuantity('increase')" style="border-radius: 0; border: none; padding: 8px 12px;">
                            <i class="fas fa-plus"></i>
                        </button>
                    </div>
                    <div style="color: var(--text-secondary);">
                        ${product.quantity} items available
                    </div>
                </div>
            </div>
            
            <!-- Action Buttons -->
            <div style="display: flex; gap: 1rem; flex-wrap: wrap;">
                <button class="btn btn-primary" style="flex: 1;" onclick="addToCart('${product.id}')">
                    <i class="fas fa-shopping-cart"></i> Add to Cart
                </button>
                <button class="btn btn-secondary" onclick="addToWishlist('${product.id}')">
                    <i class="fas fa-heart"></i> Wishlist
                </button>
                <button class="btn btn-success" style="flex: 1;" onclick="buyNow('${product.id}')">
                    <i class="fas fa-bolt"></i> Buy Now
                </button>
            </div>
        ` : ''}
    `;
}

async function toggleProductStatus(productId, currentStatus) {
    if (!confirm(`Are you sure you want to ${currentStatus === 'active' ? 'deactivate' : 'activate'} this product?`)) {
        return;
    }
    
    try {
        const newStatus = currentStatus === 'active' ? 'inactive' : 'active';
        await db.collection('products').doc(productId).update({
            status: newStatus,
            updatedAt: new Date()
        });
        
        showToast(`Product ${newStatus === 'active' ? 'activated' : 'deactivated'} successfully`, 'success');
        
        // Reload products
        loadSellerProducts();
        
        // If viewing product details, reload them
        if (editingProductId === productId) {
            await viewProductDetails(productId, true);
        }
        
    } catch (error) {
        console.error('Error toggling product status:', error);
        showToast('Error updating product status', 'error');
    }
}

// Add this to your existing deleteProduct function
async function deleteProduct(productId) {
    if (!confirm('Are you sure you want to delete this product? This action cannot be undone.')) {
        return;
    }
    
    try {
        await db.collection('products').doc(productId).delete();
        showToast('Product deleted successfully', 'success');
        
        // Reset editing if deleting the product being edited
        if (editingProductId === productId) {
            resetProductForm();
        }
        
        // Reload products
        loadSellerProducts();
        
    } catch (error) {
        console.error('Error deleting product:', error);
        showToast('Error deleting product', 'error');
    }
}
function showProductDetailsPage() {
    document.querySelectorAll('#mainContent > div').forEach(page => {
        page.style.display = 'none';
    });
    document.getElementById('productDetailsPage').style.display = 'block';
}

function changeProductImage(index) {
    // Update main image
    document.querySelectorAll('.slider-image').forEach((img, i) => {
        img.classList.toggle('active', i === index);
    });
    
    // Update dots
    document.querySelectorAll('.slider-dot').forEach((dot, i) => {
        dot.classList.toggle('active', i === index);
    });
    
    // Update thumbnail borders
    document.querySelectorAll('#mainImageSlider ~ div img').forEach((thumb, i) => {
        thumb.style.borderColor = i === index ? 'var(--primary)' : 'transparent';
    });
}

function previewProductImage(src) {
    // Optional: Show larger preview on hover
    console.log('Previewing image:', src);
}

function initializeProductImageSlider() {
    let currentImageIndex = 0;
    const images = document.querySelectorAll('.slider-image');
    const dots = document.querySelectorAll('.slider-dot');
    
    if (images.length <= 1) return;
    
    // Auto-slide images
    setInterval(() => {
        currentImageIndex = (currentImageIndex + 1) % images.length;
        changeProductImage(currentImageIndex);
    }, 5000);
}

function calculateFinalPrice(price, discount) {
    return Math.round(price - (price * discount / 100));
}

    function changeProductImage(index) {
        document.querySelectorAll('.slider-image').forEach((img, i) => {
            img.classList.toggle('active', i === index);
        });
        document.querySelectorAll('.slider-dot').forEach((dot, i) => {
            dot.classList.toggle('active', i === index);
        });
    }

    function buyNow(productId) {
        addToCart(productId);
        showToast('Added to cart! Proceed to checkout.', 'success');
        // In a real implementation, this would redirect to checkout
    }

    function messageSeller(sellerId, productId) {
        if (!currentUser) {
            openAuthModal('buyerLogin');
            return;
        }
        
        document.getElementById('messageSellerId').value = sellerId;
        document.getElementById('messageProductId').value = productId;
        openModal('messageSellerModal');
    }

    // ==================== REVIEW FUNCTIONS ====================
    function openReviewModal(productId) {
        if (!currentUser) {
            openAuthModal('buyerLogin');
            return;
        }
        
        selectedReviewProductId = productId;
        starRating = 0;
        updateStarRating();
        document.getElementById('reviewTitle').value = '';
        document.getElementById('reviewText').value = '';
        document.getElementById('reviewImages').value = '';
        document.getElementById('reviewVideo').value = '';
        document.getElementById('reviewImagesPreview').innerHTML = '';
        document.getElementById('reviewVideoPreview').innerHTML = '';
        reviewImages = [];
        reviewVideo = null;
        
        openModal('reviewModal');
    }

    function handleReviewImagesUpload(event) {
        const files = event.target.files;
        const previewContainer = document.getElementById('reviewImagesPreview');
        
        for (let i = 0; i < Math.min(files.length, 5); i++) {
            const file = files[i];
            const reader = new FileReader();
            
            reader.onload = function(e) {
                const fileItem = document.createElement('div');
                fileItem.className = 'file-preview';
                fileItem.innerHTML = `
                    <img src="${e.target.result}" alt="Preview">
                    <button type="button" class="remove-file" onclick="removeReviewImage(${reviewImages.length})">
                        <i class="fas fa-times"></i>
                    </button>
                `;
                
                previewContainer.appendChild(fileItem);
                reviewImages.push({
                    file: file,
                    url: e.target.result,
                    type: file.type
                });
            };
            
            reader.readAsDataURL(file);
        }
    }

    function handleReviewVideoUpload(event) {
        const file = event.target.files[0];
        if (!file) return;
        
        const reader = new FileReader();
        reader.onload = function(e) {
            const previewContainer = document.getElementById('reviewVideoPreview');
            previewContainer.innerHTML = `
                <div class="file-preview">
                    <video controls style="width: 200px; height: 150px;">
                        <source src="${e.target.result}" type="${file.type}">
                    </video>
                    <button type="button" class="remove-file" onclick="removeReviewVideo()">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
            `;
            reviewVideo = {
                file: file,
                url: e.target.result,
                type: file.type
            };
        };
        reader.readAsDataURL(file);
    }

    function removeReviewImage(index) {
        reviewImages.splice(index, 1);
        updateReviewImagesPreview();
    }

    function removeReviewVideo() {
        reviewVideo = null;
        document.getElementById('reviewVideoPreview').innerHTML = '';
        document.getElementById('reviewVideo').value = '';
    }

    function updateReviewImagesPreview() {
        const previewContainer = document.getElementById('reviewImagesPreview');
        previewContainer.innerHTML = '';
        
        reviewImages.forEach((fileObj, index) => {
            const fileItem = document.createElement('div');
            fileItem.className = 'file-preview';
            fileItem.innerHTML = `
                <img src="${fileObj.url}" alt="Preview">
                <button type="button" class="remove-file" onclick="removeReviewImage(${index})">
                    <i class="fas fa-times"></i>
                </button>
            `;
            previewContainer.appendChild(fileItem);
        });
    }

    async function submitReview(e) {
        e.preventDefault();
        
        if (!currentUser || !selectedReviewProductId) return;
        
        if (starRating === 0) {
            showToast('Please select a rating', 'error');
            return;
        }
        
        const reviewTitle = document.getElementById('reviewTitle').value.trim();
        const reviewText = document.getElementById('reviewText').value.trim();
        
        if (!reviewText) {
            showToast('Please write your review', 'error');
            return;
        }
        
        try {
            // Upload review images
            const reviewImageUrls = [];
            for (const image of reviewImages) {
                const imageUrl = await uploadToCloudinary(image.file, 'image');
                if (imageUrl) reviewImageUrls.push(imageUrl);
            }
            
            // Upload review video
            let reviewVideoUrl = null;
            if (reviewVideo) {
                reviewVideoUrl = await uploadToCloudinary(reviewVideo.file, 'video');
            }
            
            // Save review to Firestore
            const reviewData = {
                productId: selectedReviewProductId,
                userId: currentUser.uid,
                userName: currentUser.displayName || currentUser.email.split('@')[0],
                rating: starRating,
                title: reviewTitle,
                text: reviewText,
                images: reviewImageUrls,
                video: reviewVideoUrl,
                createdAt: new Date(),
                updatedAt: new Date()
            };
            
            await db.collection('reviews').add(reviewData);
            
            // Update product rating
            const product = products.find(p => p.id === selectedReviewProductId);
            if (product) {
                const productRef = db.collection('products').doc(selectedReviewProductId);
                await productRef.update({
                    reviewsCount: firebase.firestore.FieldValue.increment(1),
                    // Update average rating (this is a simplified version)
                });
            }
            
            closeModal('reviewModal');
            showToast('Review submitted successfully!', 'success');
            
        } catch (error) {
            console.error('Error submitting review:', error);
            showToast('Error submitting review', 'error');
        }
    }

    // ==================== MESSAGE SELLER ====================
    async function handleMessageSeller(e) {
        e.preventDefault();
        
        if (!currentUser) return;
        
        const sellerId = document.getElementById('messageSellerId').value;
        const productId = document.getElementById('messageProductId').value;
        const subject = document.getElementById('messageSubject').value.trim();
        const messageText = document.getElementById('messageText').value.trim();
        
        if (!messageText) {
            showToast('Please write your message', 'error');
            return;
        }
        
        try {
            // Upload message files
            const messageFileUrls = [];
            for (const fileObj of messageFiles) {
                const fileUrl = await uploadToCloudinary(fileObj.file, 
                    fileObj.type.startsWith('image/') ? 'image' : 
                    fileObj.type.startsWith('video/') ? 'video' : 'raw');
                if (fileUrl) messageFileUrls.push({ url: fileUrl, type: fileObj.type });
            }
            
            // Find or create chat
            const chatQuery = await db.collection('chats')
                .where('participants', 'array-contains', currentUser.uid)
                .get();
            
            let chatId = null;
            let chatDoc = null;
            
            chatQuery.forEach(doc => {
                const chat = doc.data();
                if (chat.participants.includes(sellerId)) {
                    chatId = doc.id;
                    chatDoc = chat;
                }
            });
            
            if (!chatId) {
                // Create new chat
                const newChat = {
                    participants: [currentUser.uid, sellerId],
                    productId: productId,
                    lastMessage: messageText,
                    lastMessageTime: new Date(),
                    unreadCount: { [currentUser.uid]: 0, [sellerId]: 1 },
                    createdAt: new Date(),
                    updatedAt: new Date()
                };
                
                const chatRef = await db.collection('chats').add(newChat);
                chatId = chatRef.id;
            } else {
                // Update existing chat
                await db.collection('chats').doc(chatId).update({
                    lastMessage: messageText,
                    lastMessageTime: new Date(),
                    [`unreadCount.${sellerId}`]: firebase.firestore.FieldValue.increment(1)
                });
            }
            
            // Add message to chat
            await db.collection('chats').doc(chatId).collection('messages').add({
                text: messageText,
                subject: subject,
                senderId: currentUser.uid,
                files: messageFileUrls,
                timestamp: new Date(),
                read: false
            });
            
            closeModal('messageSellerModal');
            showToast('Message sent successfully!', 'success');
            
        } catch (error) {
            console.error('Error sending message:', error);
            showToast('Error sending message', 'error');
        }
    }

    function handleMessageFilesUpload(event) {
        const files = event.target.files;
        const previewContainer = document.getElementById('messageFilesPreview');
        
        for (let i = 0; i < files.length; i++) {
            const file = files[i];
            const reader = new FileReader();
            
            reader.onload = function(e) {
                const fileItem = document.createElement('div');
                fileItem.className = 'file-preview';
                
                if (file.type.startsWith('image/')) {
                    fileItem.innerHTML = `
                        <img src="${e.target.result}" alt="Preview">
                        <button type="button" class="remove-file" onclick="removeMessageFile(${messageFiles.length})">
                            <i class="fas fa-times"></i>
                        </button>
                    `;
                } else if (file.type.startsWith('video/')) {
                    fileItem.innerHTML = `
                        <video controls style="width: 100px; height: 100px;">
                            <source src="${e.target.result}" type="${file.type}">
                        </video>
                        <button type="button" class="remove-file" onclick="removeMessageFile(${messageFiles.length})">
                            <i class="fas fa-times"></i>
                        </button>
                    `;
                } else {
                    fileItem.innerHTML = `
                        <div style="width: 100px; height: 100px; background: var(--accent); display: flex; align-items: center; justify-content: center;">
                            <i class="fas fa-file" style="font-size: 2rem;"></i>
                        </div>
                        <button type="button" class="remove-file" onclick="removeMessageFile(${messageFiles.length})">
                            <i class="fas fa-times"></i>
                        </button>
                    `;
                }
                
                previewContainer.appendChild(fileItem);
                messageFiles.push({
                    file: file,
                    url: e.target.result,
                    type: file.type
                });
            };
            
            reader.readAsDataURL(file);
        }
    }

    function removeMessageFile(index) {
        messageFiles.splice(index, 1);
        updateMessageFilesPreview();
    }

    function updateMessageFilesPreview() {
        const previewContainer = document.getElementById('messageFilesPreview');
        previewContainer.innerHTML = '';
        
        messageFiles.forEach((fileObj, index) => {
            const fileItem = document.createElement('div');
            fileItem.className = 'file-preview';
            
            if (fileObj.type.startsWith('image/')) {
                fileItem.innerHTML = `
                    <img src="${fileObj.url}" alt="Preview">
                    <button type="button" class="remove-file" onclick="removeMessageFile(${index})">
                        <i class="fas fa-times"></i>
                    </button>
                `;
            } else if (fileObj.type.startsWith('video/')) {
                fileItem.innerHTML = `
                    <video controls style="width: 100px; height: 100px;">
                        <source src="${fileObj.url}" type="${fileObj.type}">
                    </video>
                    <button type="button" class="remove-file" onclick="removeMessageFile(${index})">
                        <i class="fas fa-times"></i>
                    </button>
                `;
            } else {
                fileItem.innerHTML = `
                    <div style="width: 100px; height: 100px; background: var(--accent); display: flex; align-items: center; justify-content: center;">
                        <i class="fas fa-file" style="font-size: 2rem;"></i>
                    </div>
                    <button type="button" class="remove-file" onclick="removeMessageFile(${index})">
                        <i class="fas fa-times"></i>
                    </button>
                `;
            }
            
            previewContainer.appendChild(fileItem);
        });
    }

    // ==================== CLOUDINARY UPLOAD HELPER ====================
    async function uploadToCloudinary(file, resourceType = 'image') {
        const formData = new FormData();
        formData.append('file', file);
        formData.append('upload_preset', uploadPreset);
        formData.append('cloud_name', cloudName);
        
        try {
            const endpoint = `https://api.cloudinary.com/v1_1/${cloudName}/${resourceType}/upload`;
            const response = await fetch(endpoint, {
                method: 'POST',
                body: formData
            });
            
            const data = await response.json();
            return data.secure_url;
        } catch (error) {
            console.error('Error uploading to Cloudinary:', error);
            return null;
        }
    }

    // ==================== POPULATE SELECT OPTIONS ====================
    function populateCategorySelect() {
        const categorySelect = document.getElementById('productCategory');
        categorySelect.innerHTML = '<option value="">Select Category</option>';
        
        categories.forEach(category => {
            const option = document.createElement('option');
            option.value = category.name;
            option.textContent = category.name;
            categorySelect.appendChild(option);
        });
    }

    async function populateFlashSaleProductSelect() {
        if (!currentSeller) return;
        
        try {
            const productSelect = document.getElementById('flashSaleProduct');
            productSelect.innerHTML = '<option value="">Select Product</option>';
            
            const snapshot = await db.collection('products')
                .where('sellerId', '==', currentSeller.id)
                .where('status', '==', 'active')
                .get();
            
            snapshot.docs.forEach(doc => {
                const product = doc.data();
                const option = document.createElement('option');
                option.value = doc.id;
                option.textContent = product.name + ` (Rs. ${product.price?.toLocaleString() || '0'})`;
                option.dataset.price = product.price || 0;
                productSelect.appendChild(option);
            });
            
        } catch (error) {
            console.error('Error populating flash sale product select:', error);
        }
    }

    // ==================== SELLER DASHBOARD FUNCTIONS ====================
    async function loadSellerDashboard() {
        if (!currentSeller) return;
        
        try {
            // Load products count
            const productsSnapshot = await db.collection('products')
                .where('sellerId', '==', currentSeller.id)
                .get();
            
            // Load orders count
            const ordersSnapshot = await db.collection('orders')
                .where('sellerId', '==', currentSeller.id)
                .get();
            
            const pendingOrders = ordersSnapshot.docs.filter(doc => 
                doc.data().status === 'pending'
            ).length;
            
            const totalEarnings = ordersSnapshot.docs.reduce((sum, doc) => {
                const order = doc.data();
                return sum + (order.totalAmount || 0);
            }, 0);
            
            // Update dashboard stats
            document.getElementById('sellerTotalProducts').textContent = productsSnapshot.size;
            document.getElementById('sellerTotalOrders').textContent = ordersSnapshot.size;
            document.getElementById('sellerPendingOrders').textContent = pendingOrders;
            document.getElementById('sellerTotalEarnings').textContent = `Rs. ${totalEarnings.toLocaleString()}`;
            
            // Load recent orders
            const recentOrders = ordersSnapshot.docs.slice(0, 5).map(doc => {
                const order = doc.data();
                return {
                    id: doc.id,
                    ...order,
                    date: order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt)
                };
            });
            
            const recentOrdersContainer = document.getElementById('sellerRecentOrders');
            if (recentOrders.length === 0) {
                recentOrdersContainer.innerHTML = '<p>No recent orders</p>';
            } else {
                recentOrdersContainer.innerHTML = recentOrders.map(order => `
                    <div style="background: var(--white); padding: 1rem; border-radius: var(--radius); margin-bottom: 0.5rem; border-left: 4px solid var(--primary);">
                        <div style="display: flex; justify-content: space-between; align-items: center;">
                            <div>
                                <strong>Order #${order.id.slice(-8)}</strong>
                                <p style="color: var(--text-secondary); font-size: 0.9rem; margin-top: 0.25rem;">
                                    ${order.date.toLocaleDateString()} • ${order.items?.length || 0} items
                                </p>
                            </div>
                            <div style="text-align: right;">
                                <div class="order-status-badge ${getStatusBadgeClass(order.status)}">
                                    ${getStatusText(order.status)}
                                </div>
                                <p style="margin-top: 0.25rem; font-weight: bold; color: var(--primary);">
                                    Rs. ${order.totalAmount?.toLocaleString() || '0'}
                                </p>
                            </div>
                        </div>
                    </div>
                `).join('');
            }
            
        } catch (error) {
            console.error('Error loading seller dashboard:', error);
        }
    }

async function loadSellerProducts() {
    if (!currentSeller) return;
    
    try {
        console.log('📦 Loading seller products...');
        
        // TEMPORARY FIX: Use a simpler query that doesn't require compound index
        const snapshot = await db.collection('products').get();
        
        // Filter products by sellerId on the client side
        sellerProducts = snapshot.docs
            .map(doc => {
                const data = doc.data();
                return {
                    id: doc.id,
                    ...data,
                    images: data.images || [],
                    video: data.video || null,
                    hasVideo: data.hasVideo || false,
                    status: data.status || 'active',
                    rating: data.rating || 0,
                    reviewsCount: data.reviewsCount || 0,
                    createdAt: data.createdAt ? data.createdAt.toDate() : new Date(),
                    updatedAt: data.updatedAt ? data.updatedAt.toDate() : new Date()
                };
            })
            .filter(product => product.sellerId === currentSeller.id)
            .sort((a, b) => b.createdAt - a.createdAt); // Sort by date manually
        
        console.log(`✅ Loaded ${sellerProducts.length} seller products`);
        displaySellerProducts();
        
    } catch (error) {
        console.error('❌ Error loading seller products:', error);
        showToast('Error loading products: ' + error.message, 'error');
        sellerProducts = [];
        displaySellerProducts();
    }
}


async function displaySellerProducts() {
    const productsList = document.getElementById('sellerProductsList');
    
    if (!sellerProducts || sellerProducts.length === 0) {
        productsList.innerHTML = `
            <tr>
                <td colspan="7" style="text-align: center; padding: 2rem;">
                    <i class="fas fa-box-open" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                    <p>No products found</p>
                    <button class="btn btn-sm btn-primary" onclick="switchSellerTab('addProduct')">
                        <i class="fas fa-plus"></i> Add Your First Product
                    </button>
                </td>
            </tr>
        `;
        return;
    }
    
    productsList.innerHTML = sellerProducts.map((product, index) => `
        <tr>
            <td>
                ${product.images && product.images.length > 0 ? 
                    `<img src="${product.images[0]}" alt="${product.name}" class="product-thumbnail">` :
                    `<div style="width: 60px; height: 60px; background: var(--accent); border-radius: var(--radius); display: flex; align-items: center; justify-content: center;">
                        <i class="fas fa-image" style="color: var(--text-secondary);"></i>
                    </div>`
                }
                ${product.video ? '<span style="color: var(--info); margin-left: 5px;"><i class="fas fa-video"></i></span>' : ''}
            </td>
            <td><strong>${product.code || 'N/A'}</strong></td>
            <td>
                <strong>${product.name}</strong><br>
                <small style="color: var(--text-secondary);">${product.category}</small>
            </td>
            <td>
                <strong style="color: var(--primary);">Rs. ${product.price.toLocaleString()}</strong>
                ${product.discount > 0 ? `<br><small style="color: var(--success);">${product.discount}% OFF</small>` : ''}
            </td>
            <td>
                <span class="${product.quantity > 0 ? 'status-active' : 'status-inactive'}" 
                      style="padding: 4px 8px; border-radius: 4px; font-size: 0.8rem;">
                    ${product.quantity} in stock
                </span>
            </td>
            <td>
                <span class="status-badge ${product.status === 'active' ? 'status-active' : product.status === 'inactive' ? 'status-inactive' : 'status-pending'}">
                    ${product.status || 'active'}
                </span>
            </td>
            <td>
                <div style="display: flex; gap: 5px;">
                    <button class="btn btn-sm btn-info" onclick="viewProductDetails('${product.id}', true)" title="View">
                        <i class="fas fa-eye"></i>
                    </button>
                    <button class="btn btn-sm btn-warning" onclick="editProduct('${product.id}')" title="Edit">
                        <i class="fas fa-edit"></i>
                    </button>
                    <button class="btn btn-sm btn-danger" onclick="deleteProduct('${product.id}')" title="Delete">
                        <i class="fas fa-trash"></i>
                    </button>
                </div>
            </td>
        </tr>
    `).join('');
}

    // Add this function to debug product loading
async function debugProductLoading() {
    console.log('=== DEBUG PRODUCT LOADING ===');
    console.log('1. Current Seller:', currentSeller);
    console.log('2. Seller ID:', currentSeller?.id);
    
    if (!currentSeller?.id) {
        console.log('❌ ERROR: No seller ID found');
        return;
    }
    
    try {
        console.log('3. Querying all products...');
        const snapshot = await db.collection('products').get();
        console.log(`4. Total products in database: ${snapshot.size}`);
        
        const allProducts = snapshot.docs.map(doc => ({
            id: doc.id,
            ...doc.data()
        }));
        
        console.log('5. All product IDs and seller IDs:');
        allProducts.forEach(product => {
            console.log(`   - ${product.id}: ${product.name} | Seller: ${product.sellerId}`);
        });
        
        const sellerProducts = allProducts.filter(p => p.sellerId === currentSeller.id);
        console.log(`6. Products for current seller: ${sellerProducts.length}`);
        
        if (sellerProducts.length === 0) {
            console.log('❌ No products found for this seller');
            console.log('Possible reasons:');
            console.log('   - Products were not saved with correct sellerId');
            console.log('   - sellerId mismatch');
            console.log('   - Products were deleted');
        }
        
    } catch (error) {
        console.error('Debug error:', error);
    }
}

    async function editProduct(productId) {
    try {
        const productRef = await db.collection('products').doc(productId).get();
        
        if (!productRef.exists) {
            showToast('Product not found', 'error');
            return;
        }
        
        const product = {
            id: productRef.id,
            ...productRef.data()
        };
        
        console.log('✏️ Editing product:', product.name);
        
        // Set editing mode
        editingProductId = productId;
        
        // Switch to add product tab
        switchSellerTab('addProduct');
        
        // Update button text
        document.getElementById('publishProductBtn').innerHTML = '<i class="fas fa-save"></i> Update Product';
        
        // Fill form with product data
        document.getElementById('productCode').value = product.code || '';
        document.getElementById('productName').value = product.name || '';
        document.getElementById('productCategory').value = product.category || '';
        document.getElementById('productBrand').value = product.brand || '';
        document.getElementById('productPrice').value = product.price || 0;
        document.getElementById('productQuantity').value = product.quantity || 0;
        document.getElementById('productDiscount').value = product.discount || 0;
        document.getElementById('productWeight').value = product.weight || '';
        document.getElementById('productDescription').value = product.description || '';
        
        // Handle specifications
        if (product.specifications) {
            document.getElementById('productSpecifications').value = 
                typeof product.specifications === 'string' ? 
                product.specifications : 
                JSON.stringify(product.specifications, null, 2);
        }
        
        // Load existing images
        productImages = [];
        if (product.images && product.images.length > 0) {
            productImages = product.images.map((url, index) => ({
                url: url,
                existing: true,
                name: `Image ${index + 1}`,
                type: 'image/jpeg'
            }));
        }
        updateProductImagePreview();
        
        // Load existing video if exists
        if (product.video) {
            productVideo = {
                url: product.video,
                existing: true,
                name: 'Existing Video',
                type: 'video/mp4'
            };
            
            const previewContainer = document.getElementById('videoPreviewContainer');
            previewContainer.innerHTML = `
                <div class="video-preview" style="position: relative; width: 200px; height: 150px; border-radius: var(--radius); overflow: hidden; margin-top: 10px;">
                    <video controls style="width: 100%; height: 100%; object-fit: cover;">
                        <source src="${product.video}" type="video/mp4">
                        Your browser does not support the video tag.
                    </video>
                    <button type="button" 
                            class="remove-video" 
                            onclick="removeProductVideo()"
                            style="position: absolute; top: 5px; right: 5px; background: var(--error); color: white; border: none; border-radius: 50%; width: 24px; height: 24px; cursor: pointer; display: flex; align-items: center; justify-content: center;">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
            `;
        }
        
        // Show category options if category is selected
        if (product.category) {
            showCategoryOptions();
        }
        
        showToast(`Editing: ${product.name}`, 'info');
        
    } catch (error) {
        console.error('❌ Error loading product for editing:', error);
        showToast('Error loading product for editing', 'error');
    }
}

async function deleteProduct(productId) {
    if (!confirm('Are you sure you want to delete this product? This action cannot be undone.')) {
        return;
    }
    
    try {
        await db.collection('products').doc(productId).delete();
        showToast('Product deleted successfully', 'success');
        loadSellerProducts();
    } catch (error) {
        console.error('Error deleting product:', error);
        showToast('Error deleting product', 'error');
    }
}

    async function updateProduct(productId) {
        if (!currentSeller) return;
        
        const publishBtn = document.getElementById('publishProductBtn');
        publishBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Updating...';
        publishBtn.disabled = true;
        
        try {
            const category = document.getElementById('productCategory').value;
            let specifications = {};
            
            // Get category specific options
            if (category === 'Fashion') {
                const productType = document.querySelector('input[name="productType"]:checked')?.value;
                const size = document.getElementById('fashionSize').value;
                const color = document.getElementById('fashionColor').value;
                const material = document.getElementById('fashionMaterial').value;
                
                specifications = {
                    type: productType,
                    size: size,
                    color: color,
                    material: material
                };
            } else if (category === 'Electronics') {
                const productType = document.querySelector('input[name="productType"]:checked')?.value;
                const brand = document.getElementById('electronicsBrand').value;
                const model = document.getElementById('electronicsModel').value;
                const storage = document.getElementById('electronicsStorage').value;
                const ram = document.getElementById('electronicsRAM').value;
                
                specifications = {
                    type: productType,
                    brand: brand,
                    model: model,
                    storage: storage,
                    ram: ram
                };
            } else if (category === 'Home & Kitchen') {
                const productType = document.querySelector('input[name="productType"]:checked')?.value;
                const material = document.getElementById('homeMaterial').value;
                const dimensions = document.getElementById('homeDimensions').value;
                const power = document.getElementById('homePower').value;
                
                specifications = {
                    type: productType,
                    material: material,
                    dimensions: dimensions,
                    power: power
                };
            }
            
            const productData = {
                code: document.getElementById('productCode').value.trim(),
                name: document.getElementById('productName').value.trim(),
                category: category,
                brand: document.getElementById('productBrand').value.trim() || null,
                price: parseFloat(document.getElementById('productPrice').value),
                quantity: parseInt(document.getElementById('productQuantity').value),
                discount: parseFloat(document.getElementById('productDiscount').value) || 0,
                weight: parseFloat(document.getElementById('productWeight').value) || null,
                description: document.getElementById('productDescription').value.trim(),
                specifications: JSON.stringify(specifications),
                updatedAt: new Date()
            };
            
            // Update product in Firestore
            await db.collection('products').doc(productId).update(productData);
            
            showToast('Product updated successfully!', 'success');
            
            // Reset form and button
            document.getElementById('addProductForm').reset();
            document.getElementById('imagePreviewContainer').innerHTML = '';
            document.getElementById('videoPreviewContainer').innerHTML = '';
            document.getElementById('categoryOptions').classList.remove('active');
            document.getElementById('categoryOptions').innerHTML = '';
            productImages = [];
            productVideo = null;
            
            publishBtn.innerHTML = '<i class="fas fa-upload"></i> Publish Product';
            publishBtn.disabled = false;
            publishBtn.onclick = handleAddProduct;
            
            // Reload products
            switchSellerTab('products');
            loadSellerProducts();
            
        } catch (error) {
            console.error('Error updating product:', error);
            showToast('Error updating product: ' + error.message, 'error');
            publishBtn.innerHTML = '<i class="fas fa-save"></i> Update Product';
            publishBtn.disabled = false;
        }
    }

    async function deleteProduct(productId) {
        if (!confirm('Are you sure you want to delete this product? This action cannot be undone.')) {
            return;
        }
        
        try {
            await db.collection('products').doc(productId).delete();
            
            // Remove from local array
            sellerProducts = sellerProducts.filter(p => p.id !== productId);
            
            // Update display
            displaySellerProducts();
            
            showToast('Product deleted successfully', 'success');
            
        } catch (error) {
            console.error('Error deleting product:', error);
            showToast('Error deleting product: ' + error.message, 'error');
        }
    }

    async function loadSellerOrders() {
    if (!currentSeller) return;

    try {
        // We remove the .orderBy() here to avoid the index requirement
        const snapshot = await db.collection('orders')
            .where('sellerId', '==', currentSeller.id)
            .get();

        // Convert the data to an array
        sellerOrders = snapshot.docs.map(doc => ({
            id: doc.id,
            ...doc.data(),
            // Ensure date is a valid JS Date object
            createdAt: doc.data().createdAt?.toDate ? doc.data().createdAt.toDate() : new Date(doc.data().createdAt || Date.now())
        }));

        // Sort manually by date: newest first (Descending)
        sellerOrders.sort((a, b) => b.createdAt - a.createdAt);

        displaySellerOrders();
    } catch (error) {
        console.error('Error loading seller orders:', error);
        sellerOrders = [];
        displaySellerOrders();
    }
}

    function displaySellerOrders() {
        const ordersList = document.getElementById('sellerOrdersList');
        
        if (sellerOrders.length === 0) {
            ordersList.innerHTML = `
                <div style="text-align: center; padding: 3rem;">
                    <i class="fas fa-box-open" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                    <h3>No Orders Yet</h3>
                    <p>You haven't received any orders yet.</p>
                </div>
            `;
            return;
        }
        
        ordersList.innerHTML = sellerOrders.map(order => {
            const orderDate = order.createdAt;
            const formattedDate = orderDate.toLocaleDateString('en-PK', {
                day: '2-digit',
                month: 'short',
                year: 'numeric'
            });
            
            return `
                <div class="order-card ${order.invoiceLocked ? 'order-locked' : ''}">
                    <div class="order-header">
                        <div>
                            <h3 style="color: var(--primary);">Order #${order.id.slice(-8)}</h3>
                            <p style="color: var(--text-secondary);">
                                <i class="far fa-calendar"></i> ${formattedDate} • 
                                <i class="fas fa-user"></i> ${escapeHtml(order.customerName || 'Customer')}
                            </p>
                            <p style="margin-top: 0.5rem;">
                                <strong>Status:</strong> 
                                <span class="order-status-badge ${getStatusBadgeClass(order.status)}">
                                    ${getStatusText(order.status)}
                                </span>
                            </p>
                            <p style="margin-top: 0.5rem;">
                                <strong>Payment:</strong> ${order.paymentMethod || 'COD'} • 
                                <span class="${order.paymentStatus === 'verified' ? 'status-active' : 'status-pending'}">
                                    ${order.paymentStatus || 'pending'}
                                </span>
                            </p>
                            ${order.invoiceLocked ? `
                                <div style="margin-top: 0.5rem; color: var(--warning);">
                                    <i class="fas fa-lock"></i> Invoice Locked - Payment Required
                                </div>
                            ` : ''}
                        </div>
                        <div style="text-align: right;">
                            <span class="current-price" style="font-size: 1.5rem;">
                                Rs. ${order.totalAmount?.toLocaleString() || '0'}
                            </span>
                            ${order.invoiceLocked ? `
                                <button class="unlock-order-btn" onclick="unlockInvoice('${order.id}')" style="margin-top: 0.5rem;">
                                    <i class="fas fa-unlock"></i> Unlock Invoice
                                </button>
                            ` : ''}
                        </div>
                    </div>
                    
                    <div class="order-items">
                        ${order.items?.map(item => `
                            <div class="order-item">
                                <img src="${item.image || 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'}" 
                                     class="order-item-image" 
                                     alt="${escapeHtml(item.productName || 'Product')}">
                                <div style="flex: 1;">
                                    <h4>${escapeHtml(item.productName || 'Product')}</h4>
                                    <p><strong>Quantity:</strong> ${item.quantity} | 
                                       <strong>Price:</strong> Rs. ${item.finalPrice?.toLocaleString() || '0'}</p>
                                    <p><strong>Total:</strong> Rs. ${((item.finalPrice || item.price || 0) * (item.quantity || 1)).toLocaleString()}</p>
                                </div>
                            </div>
                        `).join('')}
                    </div>
                    
                    <div class="order-actions">
                        <button class="btn btn-primary" onclick="updateOrderStatus('${order.id}')">
                            <i class="fas fa-edit"></i> Update Status
                        </button>
                        <button class="btn btn-secondary" onclick="viewOrderDetails('${order.id}')">
                            <i class="fas fa-eye"></i> View Details
                        </button>
                        <button class="btn btn-info" onclick="messageBuyer('${order.customerId}', '${order.id}')">
                            <i class="fas fa-comment"></i> Message Buyer
                        </button>
                        ${!order.invoiceLocked ? `
                            <button class="btn btn-warning" onclick="generateInvoice('${order.id}')">
                                <i class="fas fa-file-invoice"></i> Generate Invoice
                            </button>
                        ` : ''}
                    </div>
                </div>
            `;
        }).join('');
    }

    // ==================== UNLOCK INVOICE ====================
    function unlockInvoice(orderId) {
        const order = sellerOrders.find(o => o.id === orderId);
        if (!order) return;
        
        currentOrderId = orderId;
        document.getElementById('orderTransactionId').value = '';
        document.getElementById('paymentMethodSelect').value = '';
        paymentProof = null;
        document.getElementById('paymentProofPreview').innerHTML = '';
        openModal('orderLockPaymentModal');
    }

    function cancelPayment() {
        closeModal('orderLockPaymentModal');
    }

    // ==================== UPDATE ORDER STATUS ====================
    async function updateOrderStatus(orderId) {
        const order = sellerOrders.find(o => o.id === orderId);
        if (!order) return;
        
        const newStatus = prompt(`Current status: ${order.status}\n\nEnter new status (pending, confirmed, shipped, delivered, cancelled):`, order.status);
        
        if (newStatus && newStatus !== order.status) {
            try {
                await db.collection('orders').doc(orderId).update({
                    status: newStatus.toLowerCase(),
                    updatedAt: new Date(),
                    timeline: firebase.firestore.FieldValue.arrayUnion({
                        status: newStatus.toLowerCase(),
                        timestamp: new Date(),
                        note: `Status updated by seller`,
                        updatedBy: currentSeller.id
                    })
                });
                
                showToast('Order status updated successfully', 'success');
                loadSellerOrders();
                
            } catch (error) {
                console.error('Error updating order status:', error);
                showToast('Error updating order status', 'error');
            }
        }
    }

    // ==================== GENERATE INVOICE ====================
    async function generateInvoice(orderId) {
        const order = sellerOrders.find(o => o.id === orderId);
        if (!order) return;
        
        // Generate invoice HTML
        const invoiceHTML = `
            <div class="invoice-header">
                <h2><i class="fas fa-file-invoice"></i> TAX INVOICE</h2>
                <p>Invoice #INV-${orderId.slice(-8)}</p>
                <p>Date: ${new Date().toLocaleDateString()}</p>
            </div>
            
            <div class="invoice-details">
                <div>
                    <h4>Seller Details</h4>
                    <p><strong>${currentSeller.shopName || currentSeller.name}</strong></p>
                    <p>${currentSeller.address || 'Address not specified'}</p>
                    <p>Phone: ${currentSeller.phone || 'N/A'}</p>
                    <p>Email: ${currentSeller.email || 'N/A'}</p>
                </div>
                <div>
                    <h4>Buyer Details</h4>
                    <p><strong>${order.customerName || 'Customer'}</strong></p>
                    <p>${order.shippingAddress || 'Address not specified'}</p>
                    <p>Phone: ${order.customerPhone || 'N/A'}</p>
                    <p>Email: ${order.customerEmail || 'N/A'}</p>
                </div>
            </div>
            
            <table class="invoice-table">
                <thead>
                    <tr>
                        <th>Item</th>
                        <th>Quantity</th>
                        <th>Unit Price</th>
                        <th>Total</th>
                    </tr>
                </thead>
                <tbody>
                    ${order.items?.map(item => `
                        <tr>
                            <td>${escapeHtml(item.productName)}</td>
                            <td>${item.quantity}</td>
                            <td>Rs. ${(item.finalPrice || item.price || 0).toLocaleString()}</td>
                            <td>Rs. ${((item.finalPrice || item.price || 0) * (item.quantity || 1)).toLocaleString()}</td>
                        </tr>
                    `).join('')}
                </tbody>
                <tfoot>
                    <tr>
                        <td colspan="3" style="text-align: right;"><strong>Subtotal:</strong></td>
                        <td>Rs. ${order.subtotal?.toLocaleString() || '0'}</td>
                    </tr>
                    <tr>
                        <td colspan="3" style="text-align: right;"><strong>Shipping:</strong></td>
                        <td>Rs. ${order.shippingFee?.toLocaleString() || '0'}</td>
                    </tr>
                    <tr>
                        <td colspan="3" style="text-align: right;"><strong>Tax (if applicable):</strong></td>
                        <td>Rs. ${order.tax?.toLocaleString() || '0'}</td>
                    </tr>
                    <tr>
                        <td colspan="3" style="text-align: right;"><strong>Total:</strong></td>
                        <td><strong>Rs. ${order.totalAmount?.toLocaleString() || '0'}</strong></td>
                    </tr>
                </tfoot>
            </table>
            
            <div class="invoice-total">
                <h3>Total Amount: Rs. ${order.totalAmount?.toLocaleString() || '0'}</h3>
                <p>Payment Method: ${order.paymentMethod || 'COD'}</p>
                <p>Status: ${order.paymentStatus || 'Pending'}</p>
            </div>
            
            <div style="margin-top: 2rem; padding: 1rem; background: var(--accent); border-radius: var(--radius);">
                <p><strong>Notes:</strong></p>
                <p>• This is an official tax invoice for the above transaction</p>
                <p>• Please keep this invoice for your records</p>
                <p>• For any queries, contact seller support</p>
            </div>
        `;
        
        document.getElementById('invoiceDetails').innerHTML = invoiceHTML;
        openModal('invoiceModal');
    }

    function printInvoice() {
        const printWindow = window.open('', '_blank');
        printWindow.document.write(`
            <html>
                <head>
                    <title>Invoice - Order #${currentOrderId}</title>
                    <style>
                        body { font-family: Arial, sans-serif; margin: 20px; }
                        .invoice-header { text-align: center; margin-bottom: 30px; border-bottom: 2px solid #000; padding-bottom: 20px; }
                        .invoice-details { display: flex; justify-content: space-between; margin-bottom: 30px; }
                        table { width: 100%; border-collapse: collapse; margin: 20px 0; }
                        th, td { border: 1px solid #000; padding: 10px; text-align: left; }
                        th { background-color: #f0f0f0; }
                        .invoice-total { text-align: right; margin-top: 30px; }
                        @media print { button { display: none; } }
                    </style>
                </head>
                <body>
                    ${document.getElementById('invoiceDetails').innerHTML}
                    <div style="text-align: center; margin-top: 30px;">
                        <button onclick="window.print()">Print Invoice</button>
                        <button onclick="window.close()">Close</button>
                    </div>
                </body>
            </html>
        `);
        printWindow.document.close();
    }

    function closeInvoice() {
        closeModal('invoiceModal');
    }

    // ==================== WITHDRAWAL MANAGEMENT ====================
    async function loadWithdrawalManagement() {
        if (!currentSeller) return;
        
        try {
            // Load seller's available balance
            const sellerDoc = await db.collection('sellers').doc(currentSeller.id).get();
            const sellerData = sellerDoc.data();
            
            const available = sellerData.availableBalance || 0;
            document.getElementById('availableBalance').textContent = available.toLocaleString();
            
            // Load withdrawal history
            const withdrawalSnapshot = await db.collection('withdrawals')
                .where('sellerId', '==', currentSeller.id)
                .orderBy('createdAt', 'desc')
                .limit(20)
                .get();
            
            const withdrawalHistory = document.getElementById('withdrawalHistory');
            
            if (withdrawalSnapshot.empty) {
                withdrawalHistory.innerHTML = `
                    <tr><td colspan="6" style="text-align: center; padding: 2rem;">No withdrawal history</td></tr>
                `;
            } else {
                withdrawalHistory.innerHTML = withdrawalSnapshot.docs.map(doc => {
                    const withdrawal = doc.data();
                    const requestDate = withdrawal.createdAt?.toDate ? withdrawal.createdAt.toDate() : new Date(withdrawal.createdAt);
                    const completionDate = withdrawal.completedAt?.toDate ? withdrawal.completedAt.toDate() : null;
                    
                    return `
                        <tr>
                            <td>${doc.id.slice(-8)}</td>
                            <td>Rs. ${withdrawal.amount?.toLocaleString() || '0'}</td>
                            <td>${withdrawal.method || 'N/A'}</td>
                            <td>
                                <span class="${getWithdrawalStatusBadge(withdrawal.status)}">
                                    ${getWithdrawalStatusText(withdrawal.status)}
                                </span>
                            </td>
                            <td>${requestDate.toLocaleDateString()}</td>
                            <td>${completionDate ? completionDate.toLocaleDateString() : 'Pending'}</td>
                        </tr>
                    `;
                }).join('');
            }
            
        } catch (error) {
            console.error('Error loading withdrawal management:', error);
        }
    }

    async function handleWithdrawalRequest(e) {
        e.preventDefault();
        
        if (!currentSeller) return;
        
        const amount = parseFloat(document.getElementById('withdrawalAmount').value);
        const method = document.getElementById('withdrawalMethod').value;
        const account = document.getElementById('withdrawalAccount').value;
        const accountName = document.getElementById('withdrawalAccountName').value;
        const cnic = document.getElementById('withdrawalCNIC').value;
        
        // Validate amount
        if (amount < 500) {
            showToast('Minimum withdrawal amount is Rs. 500', 'error');
            return;
        }
        
        try {
            // Check available balance
            const sellerDoc = await db.collection('sellers').doc(currentSeller.id).get();
            const sellerData = sellerDoc.data();
            const availableBalance = sellerData.availableBalance || 0;
            
            if (amount > availableBalance) {
                showToast('Insufficient balance', 'error');
                return;
            }
            
            // Create withdrawal request
            const withdrawalData = {
                sellerId: currentSeller.id,
                sellerName: currentSeller.shopName || currentSeller.name,
                amount: amount,
                method: method,
                account: account,
                accountName: accountName,
                cnic: cnic,
                status: 'pending',
                createdAt: new Date(),
                updatedAt: new Date()
            };
            
            await db.collection('withdrawals').add(withdrawalData);
            
            // Update seller's balance
            await db.collection('sellers').doc(currentSeller.id).update({
                availableBalance: firebase.firestore.FieldValue.increment(-amount),
                pendingWithdrawal: firebase.firestore.FieldValue.increment(amount)
            });
            
            showToast('Withdrawal request submitted successfully!', 'success');
            document.getElementById('withdrawalRequestForm').reset();
            loadWithdrawalManagement();
            
        } catch (error) {
            console.error('Error submitting withdrawal request:', error);
            showToast('Error submitting withdrawal request', 'error');
        }
    }

    // ==================== LOAD TAX INVOICES ====================
    async function loadTaxInvoices() {
        if (!currentSeller) return;
        
        try {
            // Load orders with locked invoices
            const snapshot = await db.collection('orders')
                .where('sellerId', '==', currentSeller.id)
                .where('invoiceLocked', '==', true)
                .orderBy('createdAt', 'desc')
                .get();
            
            const invoicesList = document.getElementById('lockedInvoicesList');
            
            if (snapshot.empty) {
                invoicesList.innerHTML = `
                    <div style="text-align: center; padding: 3rem;">
                        <i class="fas fa-file-invoice" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                        <h3>No Locked Invoices</h3>
                        <p>All invoices are currently accessible.</p>
                    </div>
                `;
            } else {
                invoicesList.innerHTML = snapshot.docs.map(doc => {
                    const order = doc.data();
                    const orderDate = order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt);
                    
                    return `
                        <div class="order-card">
                            <div class="order-header">
                                <div>
                                    <h3 style="color: var(--primary);">Invoice #INV-${doc.id.slice(-8)}</h3>
                                    <p style="color: var(--text-secondary);">
                                        <i class="far fa-calendar"></i> ${orderDate.toLocaleDateString()}
                                    </p>
                                    <p><strong>Customer:</strong> ${escapeHtml(order.customerName || 'Customer')}</p>
                                    <p><strong>Amount:</strong> Rs. ${order.totalAmount?.toLocaleString() || '0'}</p>
                                </div>
                                <div>
                                    <div class="tax-invoice-lock">
                                        <i class="fas fa-lock"></i> Locked - Payment Required
                                    </div>
                                    <button class="btn btn-primary" onclick="payForTaxInvoice('${doc.id}')" style="margin-top: 1rem;">
                                        <i class="fas fa-unlock"></i> Pay to Unlock
                                    </button>
                                </div>
                            </div>
                            <div class="order-items">
                                ${order.items?.slice(0, 2).map(item => `
                                    <div class="order-item">
                                        <img src="${item.image || 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'}" 
                                             class="order-item-image" 
                                             alt="${escapeHtml(item.productName || 'Product')}">
                                        <div style="flex: 1;">
                                            <h4>${escapeHtml(item.productName || 'Product')}</h4>
                                            <p><strong>Quantity:</strong> ${item.quantity}</p>
                                        </div>
                                    </div>
                                `).join('')}
                                ${order.items?.length > 2 ? `
                                    <p style="text-align: center; color: var(--text-secondary);">
                                        + ${order.items.length - 2} more items
                                    </p>
                                ` : ''}
                            </div>
                        </div>
                    `;
                }).join('');
            }
            
        } catch (error) {
            console.error('Error loading tax invoices:', error);
        }
    }

    function payForTaxInvoice(orderId) {
        document.getElementById('invoiceNumberDisplay').textContent = `INV-${orderId.slice(-8)}`;
        document.getElementById('taxInvoiceNumber').value = `INV-${orderId.slice(-8)}`;
        document.getElementById('taxTransactionId').value = '';
        document.getElementById('taxPaymentMethod').value = '';
        taxPaymentProof = null;
        document.getElementById('taxPaymentProofPreview').innerHTML = '';
        openModal('taxInvoicePaymentModal');
    }

    // ==================== ORDER SUCCESS ====================
    function showOrderSuccess(orderId) {
        document.getElementById('successOrderId').textContent = orderId;
        openModal('orderSuccessModal');
    }

// ==================== DESKTOP VIEW SWITCHER ====================
function toggleDesktopView() {
    const isMobile = window.innerWidth <= 768;
    const container = document.getElementById('switchDesktopContainer');
    const button = document.getElementById('switchDesktopBtn');
    const body = document.body;
    
    if (isMobile) {
        // Toggle desktop view class
        body.classList.toggle('desktop-view-active');
        
        if (body.classList.contains('desktop-view-active')) {
            // Switch to desktop view
            button.innerHTML = '<i class="fas fa-mobile-alt"></i><span>Mobile View</span>';
            button.title = "Switch to Mobile View";
            
            // Force desktop viewport
            const viewportMeta = document.querySelector('meta[name="viewport"]');
            if (viewportMeta) {
                viewportMeta.setAttribute('content', 'width=1400, initial-scale=1');
            }
            
            // Add zoom effect for better visibility
            body.style.transform = 'scale(0.8)';
            body.style.transformOrigin = 'top left';
            body.style.overflowX = 'auto';
            
            showToast('Desktop view activated. Pinch to zoom if needed.', 'info');
        } else {
            // Switch back to mobile view
            button.innerHTML = '<i class="fas fa-desktop"></i><span>Desktop View</span>';
            button.title = "Switch to Desktop View";
            
            // Reset viewport
            const viewportMeta = document.querySelector('meta[name="viewport"]');
            if (viewportMeta) {
                viewportMeta.setAttribute('content', 'width=device-width, initial-scale=1.0, maximum-scale=1.0');
            }
            
            // Reset styles
            body.style.transform = '';
            body.style.transformOrigin = '';
            body.style.overflowX = '';
            
            showToast('Mobile view restored.', 'info');
        }
        
        // Adjust layout for any open modals or panels
        setTimeout(() => {
            if (typeof adjustLayoutForView === 'function') {
                adjustLayoutForView();
            }
        }, 300);
    } else {
        showToast('You are already on desktop.', 'info');
    }
}

// Initialize the switch button
function initDesktopSwitcher() {
    const switchBtn = document.getElementById('switchDesktopBtn');
    if (switchBtn) {
        switchBtn.addEventListener('click', toggleDesktopView);
    }
    
    // Also add it to the header for easy access
    const headerActions = document.querySelector('.header-actions');
    if (headerActions && window.innerWidth <= 768) {
        const mobileSwitchBtn = document.createElement('button');
        mobileSwitchBtn.className = 'action-btn';
        mobileSwitchBtn.innerHTML = '<i class="fas fa-desktop"></i><span>Desktop</span>';
        mobileSwitchBtn.title = 'Switch to Desktop View';
        mobileSwitchBtn.onclick = toggleDesktopView;
        mobileSwitchBtn.style.order = '1'; // Make it appear early
        
        // Insert after home button
        const homeBtn = document.getElementById('homeBtn');
        if (homeBtn) {
            homeBtn.parentNode.insertBefore(mobileSwitchBtn, homeBtn.nextSibling);
        }
    }
}

// Add this to your DOMContentLoaded event
document.addEventListener('DOMContentLoaded', function() {
    initDesktopSwitcher();
});

// Also detect orientation changes
window.addEventListener('resize', function() {
    const isMobile = window.innerWidth <= 768;
    const container = document.getElementById('switchDesktopContainer');
    const body = document.body;
    
    if (container) {
        if (isMobile) {
            container.style.display = 'block';
        } else {
            container.style.display = 'none';
            // Reset if switched to desktop size
            if (body.classList.contains('desktop-view-active')) {
                body.classList.remove('desktop-view-active');
                body.style.transform = '';
                body.style.transformOrigin = '';
                body.style.overflowX = '';
            }
        }
    }
});

    // ==================== VIEW ORDER DETAILS ====================
    async function viewOrderDetails(orderId) {
        const order = sellerOrders.find(o => o.id === orderId);
        if (!order) return;
        
        // Show order details in a modal
        const orderDate = order.createdAt;
        const formattedDate = orderDate.toLocaleString('en-PK', {
            day: '2-digit',
            month: 'short',
            year: 'numeric',
            hour: '2-digit',
            minute: '2-digit'
        });
        
        const detailsHTML = `
            <div class="modal active" id="orderDetailsModal">
                <div class="modal-content" style="max-width: 800px;">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                        <h2 style="color: var(--primary);">Order Details</h2>
                        <button onclick="closeModal('orderDetailsModal')" style="background: none; border: none; font-size: 1.5rem; color: var(--text-secondary); cursor: pointer;">×</button>
                    </div>
                    
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; margin-bottom: 2rem;">
                        <div>
                            <h4>Order Information</h4>
                            <div style="background: var(--accent); padding: 1rem; border-radius: var(--radius); margin-top: 0.5rem;">
                                <p><strong>Order ID:</strong> ${order.id.slice(-8)}</p>
                                <p><strong>Date:</strong> ${formattedDate}</p>
                                <p><strong>Status:</strong> 
                                    <span class="order-status-badge ${getStatusBadgeClass(order.status)}">
                                        ${getStatusText(order.status)}
                                    </span>
                                </p>
                                <p><strong>Payment Method:</strong> ${order.paymentMethod || 'COD'}</p>
                                <p><strong>Payment Status:</strong> ${order.paymentStatus || 'pending'}</p>
                            </div>
                        </div>
                        
                        <div>
                            <h4>Customer Information</h4>
                            <div style="background: var(--accent); padding: 1rem; border-radius: var(--radius); margin-top: 0.5rem;">
                                <p><strong>Name:</strong> ${escapeHtml(order.customerName || 'N/A')}</p>
                                <p><strong>Phone:</strong> ${order.customerPhone || 'N/A'}</p>
                                <p><strong>Email:</strong> ${order.customerEmail || 'N/A'}</p>
                                <p><strong>Address:</strong> ${escapeHtml(order.shippingAddress || 'N/A')}</p>
                                <p><strong>City:</strong> ${order.shippingCity || 'N/A'}</p>
                            </div>
                        </div>
                    </div>
                    
                    <h4>Order Items</h4>
                    <div style="margin-bottom: 2rem;">
                        <table style="width: 100%; border-collapse: collapse; margin-top: 0.5rem;">
                            <thead>
                                <tr style="background: var(--primary); color: white;">
                                    <th style="padding: 0.75rem; text-align: left;">Product</th>
                                    <th style="padding: 0.75rem; text-align: center;">Quantity</th>
                                    <th style="padding: 0.75rem; text-align: right;">Price</th>
                                    <th style="padding: 0.75rem; text-align: right;">Total</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${order.items?.map(item => `
                                    <tr style="border-bottom: 1px solid var(--border);">
                                        <td style="padding: 0.75rem;">
                                            <div style="display: flex; align-items: center; gap: 1rem;">
                                                <img src="${item.image || 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'}" 
                                                     style="width: 60px; height: 60px; object-fit: cover; border-radius: var(--radius);">
                                                <div>
                                                    <strong>${escapeHtml(item.productName || 'Product')}</strong>
                                                    <p style="color: var(--text-secondary); font-size: 0.9rem;">
                                                        ${item.sku || 'N/A'}
                                                    </p>
                                                </div>
                                            </div>
                                        </td>
                                        <td style="padding: 0.75rem; text-align: center;">${item.quantity || 1}</td>
                                        <td style="padding: 0.75rem; text-align: right;">Rs. ${(item.finalPrice || item.price || 0).toLocaleString()}</td>
                                        <td style="padding: 0.75rem; text-align: right;">Rs. ${((item.finalPrice || item.price || 0) * (item.quantity || 1)).toLocaleString()}</td>
                                    </tr>
                                `).join('')}
                            </tbody>
                            <tfoot>
                                <tr>
                                    <td colspan="3" style="padding: 0.75rem; text-align: right;"><strong>Subtotal:</strong></td>
                                    <td style="padding: 0.75rem; text-align: right;">Rs. ${order.subtotal?.toLocaleString() || '0'}</td>
                                </tr>
                                <tr>
                                    <td colspan="3" style="padding: 0.75rem; text-align: right;"><strong>Shipping:</strong></td>
                                    <td style="padding: 0.75rem; text-align: right;">Rs. ${order.shippingFee?.toLocaleString() || '0'}</td>
                                </tr>
                                <tr>
                                    <td colspan="3" style="padding: 0.75rem; text-align: right;"><strong>Total:</strong></td>
                                    <td style="padding: 0.75rem; text-align: right; font-weight: bold; color: var(--primary);">
                                        Rs. ${order.totalAmount?.toLocaleString() || '0'}
                                    </td>
                                </tr>
                            </tfoot>
                        </table>
                    </div>
                    
                    <div style="display: flex; gap: 1rem;">
                        <button class="btn btn-primary" onclick="updateOrderStatus('${order.id}')">
                            <i class="fas fa-edit"></i> Update Status
                        </button>
                        <button class="btn btn-secondary" onclick="closeModal('orderDetailsModal')">
                            <i class="fas fa-times"></i> Close
                        </button>
                    </div>
                </div>
            </div>
        `;
        
        const modalContainer = document.createElement('div');
        modalContainer.innerHTML = detailsHTML;
        document.body.appendChild(modalContainer.firstChild);
    }

    // ==================== MESSAGE BUYER ====================
    function messageBuyer(customerId, orderId) {
        if (!currentSeller) return;
        
        showToast('Opening conversation with buyer...', 'info');
        
        // In a real implementation, this would open a chat interface
        const message = prompt('Enter message for buyer:');
        if (message) {
            showToast('Message sent to buyer', 'success');
        }
    }

    // ==================== FLASH SALE FUNCTIONS ====================
    async function handleCreateFlashSale(e) {
        e.preventDefault();
        
        if (!currentSeller) return;
        
        const productId = document.getElementById('flashSaleProduct').value;
        const flashPrice = parseFloat(document.getElementById('flashSalePrice').value);
        const startDate = new Date(document.getElementById('flashSaleStart').value);
        const endDate = new Date(document.getElementById('flashSaleEnd').value);
        const quantity = parseInt(document.getElementById('flashSaleQuantity').value);
        
        // Validate dates
        if (startDate >= endDate) {
            showToast('End date must be after start date', 'error');
            return;
        }
        
        if (endDate <= new Date()) {
            showToast('End date must be in the future', 'error');
            return;
        }
        
        try {
            // Get product details
            const productDoc = await db.collection('products').doc(productId).get();
            if (!productDoc.exists) {
                showToast('Product not found', 'error');
                return;
            }
            
            const product = productDoc.data();
            
            // Validate flash price
            if (flashPrice >= product.price) {
                showToast('Flash price must be lower than original price', 'error');
                return;
            }
            
            const flashSaleData = {
                productId: productId,
                productName: product.name,
                originalPrice: product.price,
                flashPrice: flashPrice,
                startDate: startDate,
                endDate: endDate,
                quantity: quantity,
                soldQuantity: 0,
                sellerId: currentSeller.id,
                sellerName: currentSeller.shopName || currentSeller.name,
                status: 'active',
                createdAt: new Date(),
                updatedAt: new Date()
            };
            
            await db.collection('flashSales').add(flashSaleData);
            
            showToast('Flash sale created successfully!', 'success');
            document.getElementById('createFlashSaleForm').reset();
            
            // Reload flash sales
            loadFlashSales();
            
        } catch (error) {
            console.error('Error creating flash sale:', error);
            showToast('Error creating flash sale', 'error');
        }
    }

    // ==================== MISSING FLASH SALE FUNCTIONS ====================

async function loadFlashSaleManagement() {
    console.log("Loading Flash Sale Management...");
    
    if (!currentSeller) {
        console.error("No seller logged in");
        return;
    }

    const flashSalesList = document.getElementById('flashSalesList');
    
    // Show loading state
    flashSalesList.innerHTML = `<tr><td colspan="7" style="text-align:center; padding:2rem;">Loading flash sales...</td></tr>`;

    try {
        // Query your flash sales
        const snapshot = await db.collection('flashSales')
            .where('sellerId', '==', currentSeller.id)
            .get();

        if (snapshot.empty) {
            flashSalesList.innerHTML = `
                <tr>
                    <td colspan="7" style="text-align: center; padding: 2rem;">
                        <i class="fas fa-bolt" style="font-size: 2rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                        <p>No active flash sales found.</p>
                    </td>
                </tr>
            `;
            return;
        }

        // Render the list
        flashSalesList.innerHTML = snapshot.docs.map(doc => {
            const sale = doc.data();
            
            // Safe Date Conversion
            const startDate = sale.startDate?.toDate ? sale.startDate.toDate() : new Date(sale.startDate);
            const endDate = sale.endDate?.toDate ? sale.endDate.toDate() : new Date(sale.endDate);
            
            // Determine Status safely
            let statusBadge = 'status-active';
            let statusText = 'Active';
            const now = new Date();

            if (endDate < now) {
                statusBadge = 'status-inactive';
                statusText = 'Expired';
            } else if (startDate > now) {
                statusBadge = 'status-pending';
                statusText = 'Scheduled';
            }

            return `
                <tr>
                    <td>
                        <strong>${escapeHtml(sale.productName || 'Unknown Product')}</strong>
                    </td>
                    <td>Rs. ${sale.originalPrice?.toLocaleString() || 0}</td>
                    <td style="color: var(--error); font-weight:bold;">Rs. ${sale.flashPrice?.toLocaleString() || 0}</td>
                    <td>${startDate.toLocaleDateString()} ${startDate.toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})}</td>
                    <td>${endDate.toLocaleDateString()} ${endDate.toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})}</td>
                    <td>
                        <span class="status-badge ${statusBadge}">
                            ${statusText}
                        </span>
                    </td>
                    <td>
                        <button class="btn btn-sm btn-danger" onclick="deleteFlashSale('${doc.id}')" title="Delete Sale">
                            <i class="fas fa-trash"></i>
                        </button>
                    </td>
                </tr>
            `;
        }).join('');

    } catch (error) {
        console.error('Error loading flash sale management:', error);
        flashSalesList.innerHTML = `<tr><td colspan="7" style="text-align:center; color:red;">Error loading data: ${error.message}</td></tr>`;
    }
}

async function deleteFlashSale(saleId) {
    if (!confirm('Are you sure you want to delete this Flash Sale?')) return;

    try {
        await db.collection('flashSales').doc(saleId).delete();
        showToast('Flash sale deleted successfully', 'success');
        
        // Refresh the table
        loadFlashSaleManagement();
        
    } catch (error) {
        console.error('Error deleting flash sale:', error);
        showToast('Error deleting sale: ' + error.message, 'error');
    }
}
    
    // ==================== LOAD SELLER EARNINGS ====================
    async function loadSellerEarnings() {
        if (!currentSeller) return;
        
        try {
            const snapshot = await db.collection('orders')
                .where('sellerId', '==', currentSeller.id)
                .where('paymentStatus', '==', 'verified')
                .orderBy('createdAt', 'desc')
                .get();
            
            const earningsContainer = document.getElementById('earningsContent');
            
            let totalEarnings = 0;
            let monthlyEarnings = {};
            
            snapshot.docs.forEach(doc => {
                const order = doc.data();
                totalEarnings += order.totalAmount || 0;
                
                const orderDate = order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt);
                const monthYear = `${orderDate.getFullYear()}-${String(orderDate.getMonth() + 1).padStart(2, '0')}`;
                
                if (!monthlyEarnings[monthYear]) {
                    monthlyEarnings[monthYear] = 0;
                }
                monthlyEarnings[monthYear] += order.totalAmount || 0;
            });
            
            earningsContainer.innerHTML = `
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-number">Rs. ${totalEarnings.toLocaleString()}</div>
                        <div class="stat-label">Total Earnings</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">${snapshot.size}</div>
                        <div class="stat-label">Completed Orders</div>
                    </div>
                </div>
                
                <h4 style="margin-top: 2rem; margin-bottom: 1rem;">Monthly Breakdown</h4>
                <div style="background: var(--white); border-radius: var(--radius); padding: 1.5rem;">
                    ${Object.keys(monthlyEarnings).length > 0 ? `
                        <table style="width: 100%; border-collapse: collapse;">
                            <thead>
                                <tr style="border-bottom: 2px solid var(--border);">
                                    <th style="padding: 0.75rem; text-align: left;">Month</th>
                                    <th style="padding: 0.75rem; text-align: right;">Earnings</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${Object.entries(monthlyEarnings).map(([month, amount]) => {
                                    const [year, monthNum] = month.split('-');
                                    const monthNames = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
                                    return `
                                        <tr style="border-bottom: 1px solid var(--border);">
                                            <td style="padding: 0.75rem;">${monthNames[parseInt(monthNum) - 1]} ${year}</td>
                                            <td style="padding: 0.75rem; text-align: right;">Rs. ${amount.toLocaleString()}</td>
                                        </tr>
                                    `;
                                }).join('')}
                            </tbody>
                        </table>
                    ` : '<p>No earnings data available</p>'}
                </div>
            `;
            
        } catch (error) {
            console.error('Error loading seller earnings:', error);
            document.getElementById('earningsContent').innerHTML = '<p>Error loading earnings data</p>';
        }
    }

    // ==================== LOAD ORDER HISTORY ====================
    async function loadOrderHistory() {
        if (!currentSeller) return;
        
        try {
            const snapshot = await db.collection('orders')
                .where('sellerId', '==', currentSeller.id)
                .orderBy('createdAt', 'desc')
                .limit(50)
                .get();
            
            const orderHistoryList = document.getElementById('orderHistoryList');
            
            if (snapshot.empty) {
                orderHistoryList.innerHTML = `
                    <div style="text-align: center; padding: 3rem;">
                        <i class="fas fa-history" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                        <h3>No Order History</h3>
                        <p>You haven't received any orders yet.</p>
                    </div>
                `;
            } else {
                orderHistoryList.innerHTML = snapshot.docs.map(doc => {
                    const order = doc.data();
                    const orderDate = order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt);
                    const formattedDate = orderDate.toLocaleDateString('en-PK', {
                        day: '2-digit',
                        month: 'short',
                        year: 'numeric'
                    });
                    
                    return `
                        <div class="order-card">
                            <div class="order-header">
                                <div>
                                    <h4>Order #${doc.id.slice(-8)}</h4>
                                    <p style="color: var(--text-secondary); font-size: 0.9rem;">
                                        <i class="far fa-calendar"></i> ${formattedDate}
                                    </p>
                                    <p><strong>Customer:</strong> ${escapeHtml(order.customerName || 'Customer')}</p>
                                    <p><strong>Items:</strong> ${order.items?.length || 0} items</p>
                                </div>
                                <div style="text-align: right;">
                                    <div class="order-status-badge ${getStatusBadgeClass(order.status)}">
                                        ${getStatusText(order.status)}
                                    </div>
                                    <p style="margin-top: 0.5rem; font-weight: bold; color: var(--primary);">
                                        Rs. ${order.totalAmount?.toLocaleString() || '0'}
                                    </p>
                                </div>
                            </div>
                        </div>
                    `;
                }).join('');
            }
            
        } catch (error) {
            console.error('Error loading order history:', error);
            orderHistoryList.innerHTML = '<p>Error loading order history</p>';
        }
    }

    function filterOrderHistory() {
        const fromDate = document.getElementById('orderHistoryFrom').value;
        const toDate = document.getElementById('orderHistoryTo').value;
        const status = document.getElementById('orderHistoryStatus').value;
        
        // This would filter the order history in a real implementation
        showToast('Filter applied', 'info');
    }

    // ==================== LOAD ADMIN SUPPORT ====================
    async function loadAdminSupport() {
        // This would load admin support chat in a real implementation
        showToast('Admin support feature coming soon!', 'info');
    }

    // ==================== LOAD SELLER TRACKING ====================
    async function loadSellerTracking() {
        if (!currentSeller) return;
        
        try {
            const snapshot = await db.collection('orders')
                .where('sellerId', '==', currentSeller.id)
                .where('status', 'in', ['confirmed', 'shipped', 'out_for_delivery'])
                .orderBy('createdAt', 'desc')
                .get();
            
            const trackingList = document.getElementById('trackingOrdersList');
            
            if (snapshot.empty) {
                trackingList.innerHTML = `
                    <div style="text-align: center; padding: 3rem;">
                        <i class="fas fa-truck" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                        <h3>No Orders to Track</h3>
                        <p>All orders are either pending, delivered, or cancelled.</p>
                    </div>
                `;
            } else {
                trackingList.innerHTML = snapshot.docs.map(doc => {
                    const order = doc.data();
                    const orderDate = order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt);
                    
                    return `
                        <div class="tracking-card">
                            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1rem;">
                                <div>
                                    <h4>Order #${doc.id.slice(-8)}</h4>
                                    <p style="color: var(--text-secondary);">
                                        <i class="far fa-calendar"></i> ${orderDate.toLocaleDateString()}
                                    </p>
                                    <p><strong>Customer:</strong> ${escapeHtml(order.customerName || 'N/A')}</p>
                                    <p><strong>Total:</strong> Rs. ${order.totalAmount?.toLocaleString() || '0'}</p>
                                </div>
                                <div>
                                    <div class="order-status-badge ${getStatusBadgeClass(order.status)}">
                                        ${getStatusText(order.status)}
                                    </div>
                                    <button class="btn btn-primary" onclick="openTrackingUpdate('${doc.id}')" style="margin-top: 0.5rem;">
                                        <i class="fas fa-edit"></i> Update Tracking
                                    </button>
                                </div>
                            </div>
                        </div>
                    `;
                }).join('');
            }
            
        } catch (error) {
            console.error('Error loading seller tracking:', error);
            trackingList.innerHTML = '<p>Error loading tracking orders</p>';
        }
    }

    function openTrackingUpdate(orderId) {
        const order = sellerOrders.find(o => o.id === orderId);
        if (!order) return;
        
        document.getElementById('trackingOrderId').value = orderId;
        document.getElementById('trackingStatus').value = order.status;
        document.getElementById('trackingNumber').value = order.trackingNumber || '';
        document.getElementById('trackingNote').value = '';
        
        openModal('trackingUpdateModal');
    }

    // ==================== UPDATE ORDER TRACKING ====================
    async function updateOrderTracking(e) {
        e.preventDefault();
        
        const orderId = document.getElementById('trackingOrderId').value;
        const status = document.getElementById('trackingStatus').value;
        const trackingNumber = document.getElementById('trackingNumber').value.trim();
        const note = document.getElementById('trackingNote').value.trim();
        
        try {
            const updateData = {
                status: status,
                updatedAt: new Date()
            };
            
            if (trackingNumber) {
                updateData.trackingNumber = trackingNumber;
            }
            
            // Add to timeline
            const timelineEntry = {
                status: status,
                timestamp: new Date(),
                note: note || `Status updated to ${status}`,
                trackingNumber: trackingNumber || null
            };
            
            await db.collection('orders').doc(orderId).update({
                ...updateData,
                timeline: firebase.firestore.FieldValue.arrayUnion(timelineEntry)
            });
            
            closeModal('trackingUpdateModal');
            showToast('Order tracking updated successfully', 'success');
            loadSellerTracking();
            
        } catch (error) {
            console.error('Error updating order tracking:', error);
            showToast('Error updating order tracking', 'error');
        }
    }

    // ==================== LOAD SELLER PROFILE ====================
    async function loadSellerProfile() {
        if (!currentSeller) return;
        
        try {
            const sellerDoc = await db.collection('sellers').doc(currentSeller.id).get();
            const sellerData = sellerDoc.data();
            
            document.getElementById('sellerShopName').value = sellerData.shopName || '';
            document.getElementById('sellerEmail').value = sellerData.email || '';
            document.getElementById('sellerPhone').value = sellerData.phone || '';
            document.getElementById('sellerCNIC').value = sellerData.cnic || '';
            document.getElementById('sellerAddress').value = sellerData.address || '';
            document.getElementById('sellerCity').value = sellerData.city || '';
            document.getElementById('sellerPostalCode').value = sellerData.postalCode || '';
            document.getElementById('sellerDescription').value = sellerData.description || '';
            
        } catch (error) {
            console.error('Error loading seller profile:', error);
        }
    }

    async function handleSellerProfileUpdate(e) {
        e.preventDefault();
        
        if (!currentSeller) return;
        
        try {
            const profileData = {
                shopName: document.getElementById('sellerShopName').value.trim(),
                phone: document.getElementById('sellerPhone').value.trim(),
                cnic: document.getElementById('sellerCNIC').value.trim(),
                address: document.getElementById('sellerAddress').value.trim(),
                city: document.getElementById('sellerCity').value.trim(),
                postalCode: document.getElementById('sellerPostalCode').value.trim(),
                description: document.getElementById('sellerDescription').value.trim(),
                updatedAt: new Date()
            };
            
            await db.collection('sellers').doc(currentSeller.id).update(profileData);
            showToast('Profile updated successfully', 'success');
            
        } catch (error) {
            console.error('Error updating seller profile:', error);
            showToast('Error updating profile', 'error');
        }
    }

    // ==================== DISPLAY NOTIFICATIONS ====================
    function displayNotifications() {
        const notificationList = document.getElementById('notificationList');
        
        if (notifications.length === 0) {
            notificationList.innerHTML = '<p style="padding: 1rem; text-align: center; color: var(--text-secondary);">No notifications</p>';
            return;
        }
        
        notificationList.innerHTML = notifications.map(notification => `
            <div class="notification-item ${notification.read ? '' : 'unread'}" onclick="markNotificationAsRead('${notification.id}')">
                <strong>${escapeHtml(notification.title)}</strong>
                <p style="margin-top: 0.25rem; color: var(--text-secondary);">${escapeHtml(notification.message)}</p>
                <small style="color: var(--text-secondary);">${new Date(notification.createdAt).toLocaleDateString()}</small>
            </div>
        `).join('');
    }

    async function markNotificationAsRead(notificationId) {
        try {
            await db.collection('notifications').doc(notificationId).update({
                read: true
            });
            
            // Update local state
            const notification = notifications.find(n => n.id === notificationId);
            if (notification) {
                notification.read = true;
            }
            
            updateNotificationCount();
            displayNotifications();
            
        } catch (error) {
            console.error('Error marking notification as read:', error);
        }
    }
// Add these notification-related functions:

async function loadNotifications() {
    if (!currentUser) {
        console.log('No user logged in, skipping notifications');
        return;
    }
    
    try {
        console.log('Loading notifications for user:', currentUser.uid);
        
        const snapshot = await db.collection('notifications')
            .where('userId', '==', currentUser.uid)
            .orderBy('createdAt', 'desc')
            .limit(50)
            .get();
        
        notifications = snapshot.docs.map(doc => ({
            id: doc.id,
            ...doc.data(),
            createdAt: doc.data().createdAt?.toDate ? doc.data().createdAt.toDate() : new Date(doc.data().createdAt || new Date())
        }));
        
        console.log(`Loaded ${notifications.length} notifications`);
        updateNotificationCount();
        
        // Only display if the notifications page is active
        const notificationsPage = document.getElementById('notificationsPage');
        if (notificationsPage && notificationsPage.style.display !== 'none') {
            displayNotifications();
        }
        
    } catch (error) {
        console.error('Error loading notifications:', error);
        notifications = [];
        updateNotificationCount();
        
        // Don't try to display if there's an error
        showToast('Could not load notifications', 'error');
    }
}

function displayNotifications() {
    const notificationsList = document.getElementById('notificationsListFull');
    if (!notificationsList) return;
    
    if (notifications.length === 0) {
        notificationsList.innerHTML = `
            <div style="text-align: center; padding: 3rem;">
                <i class="fas fa-bell-slash" style="font-size: 3rem; color: var(--text-secondary); opacity: 0.3; margin-bottom: 1rem;"></i>
                <h3>No Notifications</h3>
                <p style="color: var(--text-secondary);">You don't have any notifications yet.</p>
            </div>
        `;
        return;
    }
    
    notificationsList.innerHTML = notifications.map(notif => `
        <div class="notif-item ${!notif.read ? 'unread' : ''}" onclick="markNotificationAsRead('${notif.id}')">
            <div class="notif-icon">
                <i class="fas ${getNotificationIcon(notif.type)}"></i>
            </div>
            <div style="flex: 1;">
                <h4 style="margin-bottom: 0.25rem;">${escapeHtml(notif.title)}</h4>
                <p style="color: var(--text-secondary); margin-bottom: 0.5rem;">${escapeHtml(notif.message)}</p>
                <small style="color: var(--text-secondary);">
                    ${formatTimeAgo(notif.createdAt)}
                </small>
            </div>
            ${!notif.read ? `
                <span style="width: 8px; height: 8px; background: var(--primary); border-radius: 50%;"></span>
            ` : ''}
        </div>
    `).join('');
}

function getNotificationIcon(type) {
    switch(type) {
        case 'order_update': return 'fa-box';
        case 'tracking_update': return 'fa-truck';
        case 'payment_update': return 'fa-credit-card';
        case 'message': return 'fa-comment';
        case 'flash_sale': return 'fa-bolt';
        default: return 'fa-bell';
    }
}

function formatTimeAgo(date) {
    const now = new Date();
    const diffInSeconds = Math.floor((now - date) / 1000);
    
    if (diffInSeconds < 60) return 'Just now';
    if (diffInSeconds < 3600) return `${Math.floor(diffInSeconds / 60)} minutes ago`;
    if (diffInSeconds < 86400) return `${Math.floor(diffInSeconds / 3600)} hours ago`;
    if (diffInSeconds < 604800) return `${Math.floor(diffInSeconds / 86400)} days ago`;
    
    return date.toLocaleDateString();
}

async function markNotificationAsRead(notificationId) {
    try {
        await db.collection('notifications').doc(notificationId).update({
            read: true,
            readAt: new Date()
        });
        
        // Update local state
        const notifIndex = notifications.findIndex(n => n.id === notificationId);
        if (notifIndex !== -1) {
            notifications[notifIndex].read = true;
            updateNotificationCount();
            displayNotifications();
        }
        
    } catch (error) {
        console.error('Error marking notification as read:', error);
    }
}
    // ==================== VIEW ADDRESSES ====================
    function viewAddresses() {
        showHomePage();
        showToast('Address book feature coming soon!', 'info');
    }

// New function specifically for Flash Sales
function addFlashSaleToCart(productId, flashSaleId) {
    const product = products.find(p => p.id === productId);
    const sale = flashSales.find(s => s.id === flashSaleId);

    if (!product || !sale) {
        showToast('Error adding flash sale item', 'error');
        return;
    }

    // Create a special cart item with the FLASH PRICE
    const cartItem = {
        id: product.id,
        name: product.name,
        price: Number(sale.flashPrice), // Use the SALE price, not original
        originalPrice: Number(product.price),
        image: product.images[0],
        quantity: 1,
        isFlashSale: true,
        flashSaleId: flashSaleId
    };

    addToCartLogic(cartItem);
}

// Helper logic to handle both normal and flash items
function addToCart(productId) {
    const product = products.find(p => p.id === productId);
    if (!product) return;

    // Fallback if seller data is missing in the database
    const sId = product.sellerId || "admin_main";
    const sName = product.sellerName || "Official Store";

    const existingItem = cartItems.find(item => item.id === productId);
    if (existingItem) {
        existingItem.quantity += 1;
    } else {
        cartItems.push({
            id: product.id,
            name: product.name,
            price: product.price,
            image: product.images ? product.images[0] : '',
            sellerId: sId,
            sellerName: sName,
            quantity: 1
        });
    }
    saveCart();
    updateCartCount();
    showToast('Added to cart!', 'success');
}

function formatTimeRemaining(endDate) {
    const now = new Date();
    const diff = endDate - now;
    
    if (diff <= 0) return 'Ended';
    
    const hours = Math.floor(diff / (1000 * 60 * 60));
    const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
    
    if (hours > 24) {
        const days = Math.floor(hours / 24);
        return `${days}d`;
    } else if (hours > 0) {
        return `${hours}h ${minutes}m`;
    } else {
        return `${minutes}m`;
    }
}

    async function deleteFlashSale(flashSaleId) {
        if (!confirm('Are you sure you want to delete this flash sale?')) return;
        
        try {
            await db.collection('flashSales').doc(flashSaleId).delete();
            showToast('Flash sale deleted successfully', 'success');
            loadFlashSaleManagement();
        } catch (error) {
            console.error('Error deleting flash sale:', error);
            showToast('Error deleting flash sale', 'error');
        }
    }

    // Update the seller's order management tab:

async function loadSellerOrders() {
    if (!currentSeller) return;
    
    try {
        const snapshot = await db.collection('orders')
            .where('sellerId', '==', currentSeller.id)
            .orderBy('createdAt', 'desc')
            .get();
        
        sellerOrders = snapshot.docs.map(doc => ({
            id: doc.id,
            ...doc.data(),
            createdAt: doc.data().createdAt?.toDate ? doc.data().createdAt.toDate() : new Date(doc.data().createdAt)
        }));
        
        displaySellerOrders();
        
    } catch (error) {
        console.error('Error loading seller orders:', error);
        showToast('Error loading orders', 'error');
    }
}

function displaySellerOrders() {
    const ordersList = document.getElementById('sellerOrdersList');
    if (!ordersList) return;
    
    if (sellerOrders.length === 0) {
        ordersList.innerHTML = `
            <div style="text-align: center; padding: 3rem;">
                <i class="fas fa-box-open" style="font-size: 3rem; color: var(--text-secondary); opacity: 0.3; margin-bottom: 1rem;"></i>
                <h3>No Orders Yet</h3>
                <p style="color: var(--text-secondary);">You haven't received any orders yet.</p>
            </div>
        `;
        return;
    }
    
    ordersList.innerHTML = sellerOrders.map(order => {
        // Filter out orders with pending payment verification
        if (order.paymentMethod !== 'cod' && order.paymentVerification !== 'approved') {
            return '';
        }
        
        const orderDate = order.createdAt;
        const formattedDate = orderDate.toLocaleDateString('en-PK', {
            day: 'numeric',
            month: 'short',
            year: 'numeric',
            hour: '2-digit',
            minute: '2-digit'
        });
        
        return `
            <div class="order-card ${order.paymentMethod !== 'cod' && order.paymentVerification !== 'approved' ? 'order-locked' : ''}" 
                 id="seller-order-${order.id}">
                <div class="order-header">
                    <div>
                        <h3>Order #${order.id.slice(-8)}</h3>
                        <p>Date: ${formattedDate}</p>
                        <p>Customer: ${escapeHtml(order.customerName)}</p>
                        <div style="display: flex; gap: 0.5rem; margin-top: 0.5rem; flex-wrap: wrap;">
                            <span class="order-status-badge ${getStatusBadgeClass(order.status)}">
                                ${getStatusText(order.status)}
                            </span>
                            <span class="order-status-badge ${order.paymentMethod === 'cod' ? 'status-pending-badge' : 'status-approved-badge'}">
                                ${order.paymentMethod === 'cod' ? 'COD' : 'Prepaid'}
                            </span>
                            ${order.flashSaleDiscount > 0 ? `
                                <span class="order-status-badge" style="background: #ff6b35; color: white;">
                                    <i class="fas fa-bolt"></i> Flash Sale
                                </span>
                            ` : ''}
                        </div>
                    </div>
                    
                    <div style="text-align: right;">
                        <h3 class="current-price">Rs. ${order.totalAmount?.toLocaleString()}</h3>
                        <p style="color: var(--text-secondary);">${order.items?.length || 0} items</p>
                    </div>
                </div>
                
                ${order.paymentMethod !== 'cod' && order.paymentVerification !== 'approved' ? `
                    <div class="order-locked-overlay">
                        <div style="text-align: center; padding: 1rem;">
                            <i class="fas fa-lock" style="font-size: 2rem; color: var(--warning); margin-bottom: 1rem;"></i>
                            <h4>Order Locked - Payment Verification Pending</h4>
                            <p>This order requires admin payment verification before processing.</p>
                            <p>Expected verification time: 24-48 hours</p>
                        </div>
                    </div>
                ` : ''}
                
                <div class="order-items">
                    ${order.items && order.items.map((item, index) => `
                        <div class="order-item">
                            <img src="${item.image || 'https://via.placeholder.com/80'}" 
                                 alt="${escapeHtml(item.productName)}" 
                                 class="order-item-image"
                                 onerror="this.src='https://via.placeholder.com/80'">
                            <div style="flex: 1;">
                                <p style="font-weight: 500;">${escapeHtml(item.productName)}</p>
                                <div style="display: flex; gap: 1rem; margin-top: 0.5rem; flex-wrap: wrap;">
                                    <span>Qty: ${item.quantity}</span>
                                    <span>
                                        Price: Rs. ${item.finalPrice?.toLocaleString()}
                                        ${item.originalPrice > item.finalPrice ? `
                                            <span style="text-decoration: line-through; color: var(--text-secondary);">
                                                (Rs. ${item.originalPrice?.toLocaleString()})
                                            </span>
                                        ` : ''}
                                    </span>
                                    <span>Total: Rs. ${((item.finalPrice || 0) * item.quantity).toLocaleString()}</span>
                                    ${item.isFlashSale ? `
                                        <span style="color: #ff6b35; font-weight: 500;">
                                            <i class="fas fa-bolt"></i> Flash Sale
                                        </span>
                                    ` : ''}
                                </div>
                            </div>
                        </div>
                    `).join('')}
                </div>
                
                <div class="order-actions">
                    ${order.paymentMethod !== 'cod' && order.paymentVerification !== 'approved' ? `
                        <button class="btn btn-secondary" disabled>
                            <i class="fas fa-lock"></i> Awaiting Payment Verification
                        </button>
                    ` : `
                        <select class="status-dropdown" onchange="updateSellerOrderStatus('${order.id}', this.value)" 
                                ${order.status === 'cancelled' || order.status === 'delivered' ? 'disabled' : ''}>
                            <option value="pending" ${order.status === 'pending' ? 'selected' : ''}>Pending</option>
                            <option value="confirmed" ${order.status === 'confirmed' ? 'selected' : ''}>Confirmed</option>
                            <option value="packed" ${order.status === 'packed' ? 'selected' : ''}>Packed</option>
                            <option value="shipped" ${order.status === 'shipped' ? 'selected' : ''}>Shipped</option>
                            <option value="out_for_delivery" ${order.status === 'out_for_delivery' ? 'selected' : ''}>Out for Delivery</option>
                            <option value="delivered" ${order.status === 'delivered' ? 'selected' : ''}>Delivered</option>
                            <option value="cancelled" ${order.status === 'cancelled' ? 'selected' : ''}>Cancelled</option>
                        </select>
                        
                        <button class="btn btn-primary btn-sm" onclick="openTrackingUpdateModal('${order.id}')">
                            <i class="fas fa-truck"></i> Update Tracking
                        </button>
                        
                        <button class="btn btn-secondary btn-sm" onclick="viewOrderDetails('${order.id}')">
                            <i class="fas fa-eye"></i> View Details
                        </button>
                        
                        <button class="btn btn-info btn-sm" onclick="sendMessageToBuyer('${order.id}')">
                            <i class="fas fa-comment"></i> Message Buyer
                        </button>
                        
                        ${order.invoiceLocked ? `
                            <button class="btn btn-warning btn-sm" onclick="unlockInvoice('${order.id}')">
                                <i class="fas fa-unlock"></i> Unlock Invoice (Rs. 50)
                            </button>
                        ` : `
                            <button class="btn btn-success btn-sm" onclick="generateInvoice('${order.id}')">
                                <i class="fas fa-file-invoice"></i> View Invoice
                            </button>
                        `}
                    `}
                </div>
            </div>
        `;
    }).join('');
}

async function updateSellerOrderStatus(orderId, newStatus) {
    try {
        const updateData = {
            status: newStatus,
            updatedAt: new Date()
        };
        
        // Add to timeline
        const timelineEvent = {
            status: newStatus,
            timestamp: new Date(),
            note: `Status changed to ${newStatus} by seller`,
            updatedBy: currentSeller.name || currentSeller.shopName
        };
        
        updateData.timeline = firebase.firestore.FieldValue.arrayUnion(timelineEvent);
        
        // If shipping, add shipped date
        if (newStatus === 'shipped') {
            updateData.shippedAt = new Date();
        }
        
        // If delivered, add delivered date
        if (newStatus === 'delivered') {
            updateData.deliveredAt = new Date();
        }
        
        await db.collection('orders').doc(orderId).update(updateData);
        
        // Update local state
        const orderIndex = sellerOrders.findIndex(o => o.id === orderId);
        if (orderIndex !== -1) {
            sellerOrders[orderIndex].status = newStatus;
            if (!sellerOrders[orderIndex].timeline) {
                sellerOrders[orderIndex].timeline = [];
            }
            sellerOrders[orderIndex].timeline.push(timelineEvent);
        }
        
        showToast(`Order status updated to ${getStatusText(newStatus)}`, 'success');
        
        // Refresh display
        displaySellerOrders();
        
        // Send notification to buyer
        await sendOrderStatusNotificationToBuyer(orderId, newStatus);
        
    } catch (error) {
        console.error('Error updating order status:', error);
        showToast('Error updating order status', 'error');
    }
}

function openTrackingUpdateModal(orderId) {
    const order = sellerOrders.find(o => o.id === orderId);
    if (!order) return;
    
    document.getElementById('trackingOrderId').value = orderId;
    document.getElementById('trackingStatus').value = order.status || 'confirmed';
    document.getElementById('trackingNumber').value = order.trackingNumber || '';
    document.getElementById('trackingNote').value = '';
    
    openModal('trackingUpdateModal');
}

async function updateOrderTracking(e) {
    e.preventDefault();
    
    const orderId = document.getElementById('trackingOrderId').value;
    const status = document.getElementById('trackingStatus').value;
    const trackingNumber = document.getElementById('trackingNumber').value;
    const note = document.getElementById('trackingNote').value;
    
    try {
        const updateData = {
            status: status,
            updatedAt: new Date()
        };
        
        if (trackingNumber) {
            updateData.trackingNumber = trackingNumber;
        }
        
        const timelineEvent = {
            status: status,
            timestamp: new Date(),
            note: note || `Tracking updated by seller`,
            updatedBy: currentSeller.name || currentSeller.shopName
        };
        
        if (trackingNumber) {
            timelineEvent.trackingNumber = trackingNumber;
            timelineEvent.note = `${note || 'Tracking number added'}: ${trackingNumber}`;
        }
        
        updateData.timeline = firebase.firestore.FieldValue.arrayUnion(timelineEvent);
        
        await db.collection('orders').doc(orderId).update(updateData);
        
        // Update local state
        const orderIndex = sellerOrders.findIndex(o => o.id === orderId);
        if (orderIndex !== -1) {
            sellerOrders[orderIndex].status = status;
            if (trackingNumber) {
                sellerOrders[orderIndex].trackingNumber = trackingNumber;
            }
            if (!sellerOrders[orderIndex].timeline) {
                sellerOrders[orderIndex].timeline = [];
            }
            sellerOrders[orderIndex].timeline.push(timelineEvent);
        }
        
        closeModal('trackingUpdateModal');
        showToast('Tracking information updated', 'success');
        displaySellerOrders();
        
        // Send notification to buyer
        await sendTrackingUpdateNotificationToBuyer(orderId, status, trackingNumber);
        
    } catch (error) {
        console.error('Error updating tracking:', error);
        showToast('Error updating tracking', 'error');
    }
}

async function sendOrderStatusNotificationToBuyer(orderId, newStatus) {
    try {
        const order = sellerOrders.find(o => o.id === orderId);
        if (!order) return;
        
        await db.collection('notifications').add({
            userId: order.customerId,
            title: 'Order Status Updated',
            message: `Your order #${orderId.slice(-8)} status changed to ${getStatusText(newStatus)}`,
            type: 'order_update',
            orderId: orderId,
            read: false,
            createdAt: new Date()
        });
        
    } catch (error) {
        console.error('Error sending notification:', error);
    }
}

async function sendTrackingUpdateNotificationToBuyer(orderId, status, trackingNumber) {
    try {
        const order = sellerOrders.find(o => o.id === orderId);
        if (!order) return;
        
        let message = `Your order #${orderId.slice(-8)} status: ${getStatusText(status)}`;
        if (trackingNumber) {
            message += ` | Tracking: ${trackingNumber}`;
        }
        
        await db.collection('notifications').add({
            userId: order.customerId,
            title: 'Order Tracking Updated',
            message: message,
            type: 'tracking_update',
            orderId: orderId,
            read: false,
            createdAt: new Date()
        });
        
    } catch (error) {
        console.error('Error sending tracking notification:', error);
    }
}
function unlockInvoice(orderId) {
    const order = sellerOrders.find(o => o.id === orderId);
    if (!order) return;
    
    if (confirm('Unlock this invoice? This will allow the buyer to download it.')) {
        showToast('Invoice unlocked successfully', 'success');
        // In real implementation, update Firestore
        order.invoiceLocked = false;
        displaySellerOrders();
    }
}

function viewOrderDetails(orderId) {
    const order = sellerOrders.find(o => o.id === orderId);
    if (!order) {
        showToast('Order not found', 'error');
        return;
    }
    
    // Show order details in a modal or alert
    const details = `
        Order ID: ${order.id}
        Customer: ${order.customerName}
        Date: ${order.createdAt.toLocaleString()}
        Status: ${order.status}
        Payment: ${order.paymentMethod} (${order.paymentStatus})
        Total: Rs. ${order.totalAmount?.toLocaleString()}
        Items: ${order.items?.map(item => `${item.quantity}x ${item.productName}`).join(', ')}
        Address: ${order.shippingAddress}, ${order.shippingCity}
    `;
    
    alert(details);
}

function messageBuyer(customerId, orderId) {
    if (!currentSeller) return;
    
    showToast('Opening conversation with buyer...', 'info');
    
    // In real implementation, open chat with buyer
    // For now, show a message
    const message = prompt('Enter message for buyer:');
    if (message) {
        showToast('Message sent to buyer', 'success');
    }
}

    function displaySellerOrders() {
        const ordersList = document.getElementById('sellerOrdersList');
        
        if (sellerOrders.length === 0) {
            ordersList.innerHTML = `
                <div style="text-align: center; padding: 3rem;">
                    <i class="fas fa-box-open" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                    <h3>No Orders Yet</h3>
                    <p>You haven't received any orders yet.</p>
                </div>
            `;
            return;
        }
        
        ordersList.innerHTML = sellerOrders.map(order => {
            // Replace the inside of ordersList.innerHTML = sellerOrders.map(order => { ... })
const isLocked = order.taxStatus !== 'unlocked';
const isCancelled = order.status === 'Cancelled';

return `
<div class="order-card" id="order-card-${order.id}">
    <div class="order-header">
        <h3>Order #${order.id.slice(-6)}</h3>
        <span class="status-badge status-${order.status.toLowerCase()}">${order.status}</span>
    </div>

    ${isLocked && !isCancelled ? `
        <div class="order-locked-overlay">
            <p><i class="fas fa-lock"></i> Invoice details are locked.</p>
            <p>Pay <strong>Rs. 30</strong> to Admin Account: <strong>0332-2085763</strong> to unlock.</p>
            <div class="payment-icons">
                <img src="https://upload.wikimedia.org/wikipedia/commons/f/ff/Easypaisa_logo.png" alt="Easypaisa">
                <img src="https://upload.wikimedia.org/wikipedia/en/3/36/JazzCash_logo.png" alt="JazzCash">
            </div>
            <div class="payment-form">
                <input type="text" id="name-${order.id}" class="form-control mb-2" placeholder="Easypaisa/JazzCash Holder Name">
                <input type="tel" id="phone-${order.id}" class="form-control mb-2" placeholder="Your Phone Number">
                <input type="file" id="file-${order.id}" class="form-control mb-2" accept="image/*">
                <button class="btn btn-primary w-100" onclick="handleTaxPayment('${order.id}')">Submit Payment Screenshot</button>
            </div>
        </div>
    ` : ''}

    <div class="${isLocked && !isCancelled ? 'blurred-info' : ''}">
        <p><strong>Customer:</strong> ${order.customerName}</p>
        <p><strong>Phone:</strong> ${order.customerPhone}</p>
        <p><strong>Address:</strong> ${order.shippingAddress}</p>
    </div>

    <div class="order-actions" style="margin-top:15px; display: flex; gap:10px;">
        ${!isCancelled ? `
            <select class="form-control" onchange="updateOrderStatus('${order.id}', this.value)">
                <option value="Pending" ${order.status === 'Pending' ? 'selected' : ''}>Pending</option>
                <option value="Shipped" ${order.status === 'Shipped' ? 'selected' : ''}>Shipped</option>
                <option value="Cancelled">Cancel Order</option>
            </select>
            ${!isLocked ? `
                <button class="btn btn-info btn-sm" onclick="messageBuyer('${order.customerId}')">Message Seller</button>
                <button class="btn btn-warning btn-sm" onclick="viewOrderDetails('${order.id}')">Update Status</button>
            ` : ''}
        ` : '<strong>Order Automatically Cancelled</strong>'}
    </div>
</div>
`;
        }).join('');
    }

    // ==================== ORDER MANAGEMENT FUNCTIONS ====================

async function updateOrderStatus(orderId, newStatus) {
    try {
        await db.collection('orders').doc(orderId).update({
            status: newStatus,
            // If cancelled, ensure the UI hides actions
            invoiceLocked: (newStatus === 'Cancelled' ? false : true) 
        });
        
        showToast(`Order status updated to ${newStatus}`, "success");
        loadSellerOrders(); // This re-renders the UI and hides buttons automatically
    } catch (error) {
        console.error("Error updating status:", error);
    }
}

async function viewOrderDetails(orderId) {
    console.log('Viewing order details for:', orderId);
    
    const order = sellerOrders.find(o => o.id === orderId);
    if (!order) {
        showToast('Order not found', 'error');
        return;
    }
    
    // Create a detailed view modal
    const orderDate = order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt);
    const formattedDate = orderDate.toLocaleString('en-PK', {
        day: '2-digit',
        month: 'short',
        year: 'numeric',
        hour: '2-digit',
        minute: '2-digit'
    });
    
    // Create modal HTML
    const modalHTML = `
        <div class="modal active" id="orderDetailsModal">
            <div class="modal-content" style="max-width: 800px;">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                    <h2 style="color: var(--primary);">Order Details</h2>
                    <button onclick="closeModal('orderDetailsModal')" style="background: none; border: none; font-size: 1.5rem; color: var(--text-secondary); cursor: pointer;">×</button>
                </div>
                
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; margin-bottom: 2rem;">
                    <div>
                        <h4>Order Information</h4>
                        <div style="background: var(--accent); padding: 1rem; border-radius: var(--radius); margin-top: 0.5rem;">
                            <p><strong>Order ID:</strong> ${order.id.slice(-8)}</p>
                            <p><strong>Date:</strong> ${formattedDate}</p>
                            <p><strong>Status:</strong> 
                                <span class="order-status-badge ${getStatusBadgeClass(order.status)}">
                                    ${getStatusText(order.status)}
                                </span>
                            </p>
                            <p><strong>Payment Method:</strong> ${order.paymentMethod || 'COD'}</p>
                            <p><strong>Payment Status:</strong> ${order.paymentStatus || 'pending'}</p>
                        </div>
                    </div>
                    
                    <div>
                        <h4>Customer Information</h4>
                        <div style="background: var(--accent); padding: 1rem; border-radius: var(--radius); margin-top: 0.5rem;">
                            <p><strong>Name:</strong> ${escapeHtml(order.customerName || 'N/A')}</p>
                            <p><strong>Phone:</strong> ${order.customerPhone || 'N/A'}</p>
                            <p><strong>Email:</strong> ${order.customerEmail || 'N/A'}</p>
                            <p><strong>Address:</strong> ${escapeHtml(order.shippingAddress || 'N/A')}</p>
                            <p><strong>City:</strong> ${order.shippingCity || 'N/A'}</p>
                        </div>
                    </div>
                </div>
                
                <h4>Order Items</h4>
                <div style="margin-bottom: 2rem;">
                    ${order.items && order.items.length > 0 ? `
                        <table style="width: 100%; border-collapse: collapse; margin-top: 0.5rem;">
                            <thead>
                                <tr style="background: var(--primary); color: white;">
                                    <th style="padding: 0.75rem; text-align: left;">Product</th>
                                    <th style="padding: 0.75rem; text-align: center;">Quantity</th>
                                    <th style="padding: 0.75rem; text-align: right;">Price</th>
                                    <th style="padding: 0.75rem; text-align: right;">Total</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${order.items.map(item => `
                                    <tr style="border-bottom: 1px solid var(--border);">
                                        <td style="padding: 0.75rem;">
                                            <div style="display: flex; align-items: center; gap: 1rem;">
                                                <img src="${item.image || 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'}" 
                                                     style="width: 60px; height: 60px; object-fit: cover; border-radius: var(--radius);">
                                                <div>
                                                    <strong>${escapeHtml(item.productName || 'Product')}</strong>
                                                    <p style="color: var(--text-secondary); font-size: 0.9rem;">
                                                        ${item.sku || 'N/A'}
                                                    </p>
                                                </div>
                                            </div>
                                        </td>
                                        <td style="padding: 0.75rem; text-align: center;">${item.quantity || 1}</td>
                                        <td style="padding: 0.75rem; text-align: right;">Rs. ${(item.finalPrice || item.price || 0).toLocaleString()}</td>
                                        <td style="padding: 0.75rem; text-align: right;">Rs. ${((item.finalPrice || item.price || 0) * (item.quantity || 1)).toLocaleString()}</td>
                                    </tr>
                                `).join('')}
                            </tbody>
                            <tfoot>
                                <tr>
                                    <td colspan="3" style="padding: 0.75rem; text-align: right;"><strong>Subtotal:</strong></td>
                                    <td style="padding: 0.75rem; text-align: right;">Rs. ${(order.subtotal || order.totalAmount || 0).toLocaleString()}</td>
                                </tr>
                                <tr>
                                    <td colspan="3" style="padding: 0.75rem; text-align: right;"><strong>Shipping:</strong></td>
                                    <td style="padding: 0.75rem; text-align: right;">Rs. ${(order.shippingFee || 0).toLocaleString()}</td>
                                </tr>
                                <tr>
                                    <td colspan="3" style="padding: 0.75rem; text-align: right;"><strong>Total:</strong></td>
                                    <td style="padding: 0.75rem; text-align: right; font-weight: bold; color: var(--primary);">
                                        Rs. ${(order.totalAmount || 0).toLocaleString()}
                                    </td>
                                </tr>
                            </tfoot>
                        </table>
                    ` : `<p>No items found</p>`}
                </div>
                
                ${order.timeline && order.timeline.length > 0 ? `
                    <h4>Order Timeline</h4>
                    <div style="margin-top: 1rem;">
                        <div class="tracking-timeline">
                            ${order.timeline.map(event => {
                                const eventDate = event.timestamp?.toDate ? 
                                    event.timestamp.toDate() : new Date(event.timestamp);
                                const formattedEventDate = eventDate.toLocaleString('en-PK', {
                                    day: '2-digit',
                                    month: 'short',
                                    year: 'numeric',
                                    hour: '2-digit',
                                    minute: '2-digit'
                                });
                                
                                return `
                                    <div class="timeline-item">
                                        <div class="timeline-date">${formattedEventDate}</div>
                                        <div class="timeline-content">
                                            <strong>${getStatusText(event.status)}</strong>
                                            ${event.note ? `<p style="margin-top: 0.25rem;">${escapeHtml(event.note)}</p>` : ''}
                                            ${event.trackingNumber ? `
                                                <p style="margin-top: 0.25rem;">
                                                    <strong>Tracking #:</strong> ${event.trackingNumber}
                                                </p>
                                            ` : ''}
                                        </div>
                                    </div>
                                `;
                            }).join('')}
                        </div>
                    </div>
                ` : ''}
                
                <div style="margin-top: 2rem; display: flex; gap: 1rem;">
                    <button class="btn btn-primary" onclick="updateOrderStatus('${order.id}')">
                        <i class="fas fa-edit"></i> Update Status
                    </button>
                    <button class="btn btn-secondary" onclick="closeModal('orderDetailsModal')">
                        <i class="fas fa-times"></i> Close
                    </button>
                </div>
            </div>
        </div>
    `;
    
    // Add modal to page
    const modalContainer = document.createElement('div');
    modalContainer.innerHTML = modalHTML;
    document.body.appendChild(modalContainer.firstChild);
}

async function handleTaxPayment(orderId) {
    const name = document.getElementById(`name-${orderId}`).value;
    const phone = document.getElementById(`phone-${orderId}`).value;
    const fileInput = document.getElementById(`file-${orderId}`);
    const file = fileInput.files[0];

    if (!name || !phone || !file) {
        showToast('Please fill all fields and upload a screenshot', 'error');
        return;
    }

    try {
        showToast('Uploading payment proof...', 'info');

        // 1. Upload Image (Using Firebase Storage)
        const storageRef = firebase.storage().ref(`tax_payments/${orderId}_${Date.now()}`);
        const snapshot = await storageRef.put(file);
        const screenshotUrl = await snapshot.ref.getDownloadURL();

        // 2. Update Order in Firestore
        await db.collection('orders').doc(orderId).update({
            taxStatus: 'pending', // This triggers the "Request Sent" box
            taxPaymentDetails: {
                senderName: name,
                senderPhone: phone,
                screenshot: screenshotUrl,
                submittedAt: new Date()
            }
        });

        // 3. Update local state so the UI refreshes
        const orderIndex = sellerOrders.findIndex(o => o.id === orderId);
        if (orderIndex !== -1) {
            sellerOrders[orderIndex].taxStatus = 'pending';
        }

        showToast('Payment submitted! Waiting for Admin approval.', 'success');
        displaySellerOrders(); // Refresh the list

    } catch (error) {
        console.error("Error submitting tax payment:", error);
        showToast('Failed to submit payment', 'error');
    }
}

// Function to message buyer (placeholder)
async function messageBuyer(customerId, orderId) {
    console.log('Messaging buyer:', customerId, 'for order:', orderId);
    
    if (!currentSeller) return;
    
    try {
        // Check if chat already exists
        const chatQuery = await db.collection('chats')
            .where('participants', 'array-contains', currentSeller.id)
            .get();
        
        let chatDoc = null;
        
        // Find existing chat with this buyer
        chatQuery.forEach(doc => {
            const chatData = doc.data();
            if (chatData.participants.includes(customerId)) {
                chatDoc = { id: doc.id, ...chatData };
            }
        });
        
        if (!chatDoc) {
            // Create new chat
            const newChat = {
                participants: [currentSeller.id, customerId],
                orderId: orderId,
                lastMessage: '',
                lastMessageTime: new Date(),
                unreadCount: { [currentSeller.id]: 0, [customerId]: 1 },
                createdAt: new Date(),
                updatedAt: new Date()
            };
            
            const chatRef = await db.collection('chats').add(newChat);
            chatDoc = { id: chatRef.id, ...newChat };
        }
        
        // Open chat modal
        openChatWithUser(chatDoc.id, customerId);
        
    } catch (error) {
        console.error('Error starting chat with buyer:', error);
        showToast('Error starting chat', 'error');
    }
}

function openChatWithUser(chatId, userId) {
    // Switch to messages tab
    showMessagesPage();
    
    // In real implementation, you would:
    // 1. Switch to messages page
    // 2. Load the specific chat
    // 3. Focus on the message input
    
    showToast('Opening chat with buyer...', 'info');
}
    async function updateOrderTracking(e) {
        e.preventDefault();
        
        const orderId = document.getElementById('trackingOrderId').value;
        const status = document.getElementById('trackingStatus').value;
        const trackingNumber = document.getElementById('trackingNumber').value.trim();
        const note = document.getElementById('trackingNote').value.trim();
        
        try {
            const updateData = {
                status: status,
                updatedAt: new Date()
            };
            
            if (trackingNumber) {
                updateData.trackingNumber = trackingNumber;
            }
            
            // Add to timeline
            updateData.timeline = firebase.firestore.FieldValue.arrayUnion({
                status: status,
                timestamp: new Date(),
                note: note || `Status updated to ${status}`,
                trackingNumber: trackingNumber || null
            });
            
            await db.collection('orders').doc(orderId).update(updateData);
            
            closeModal('trackingUpdateModal');
            showToast('Order status updated successfully', 'success');
            loadSellerOrders();
            
        } catch (error) {
            console.error('Error updating order tracking:', error);
            showToast('Error updating order status', 'error');
        }
    }

    async function loadSellerTracking() {
    if (!currentSeller) return;
    
    console.log('Loading tracking orders for seller:', currentSeller.id);
    
    const trackingList = document.getElementById('trackingOrdersList');
    
    try {
        // Try optimized query first
        const snapshot = await db.collection('orders')
            .where('sellerId', '==', currentSeller.id)
            .get();
        
        console.log('Total orders found:', snapshot.docs.length);
        
        // Filter manually in JavaScript
        const trackingOrders = snapshot.docs
            .map(doc => ({
                id: doc.id,
                ...doc.data(),
                createdAt: doc.data().createdAt?.toDate ? doc.data().createdAt.toDate() : new Date(doc.data().createdAt || Date.now())
            }))
            .filter(order => 
                ['confirmed', 'shipped', 'out_for_delivery', 'delivered'].includes(order.status)
            )
            .sort((a, b) => b.createdAt - a.createdAt); // Sort by date manually
        
        console.log('Tracking orders after filter:', trackingOrders.length);
        
        if (trackingOrders.length === 0) {
            trackingList.innerHTML = `
                <div style="text-align: center; padding: 3rem;">
                    <i class="fas fa-truck" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                    <h3>No Orders to Track</h3>
                    <p>All orders are either pending or cancelled.</p>
                    <button class="btn btn-primary" onclick="createSampleTrackingOrders()" style="margin-top: 1rem;">
                        <i class="fas fa-plus"></i> Create Sample Tracking Orders
                    </button>
                </div>
            `;
            return;
        }
        
        trackingList.innerHTML = trackingOrders.map(order => {
            const orderDate = order.createdAt;
            const formattedDate = orderDate.toLocaleDateString('en-PK', {
                day: '2-digit',
                month: 'short',
                year: 'numeric'
            });
            
            return `
                <div class="tracking-card">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1rem;">
                        <div>
                            <h4>Order #${order.id.slice(-8)}</h4>
                            <p style="color: var(--text-secondary);">
                                <i class="far fa-calendar"></i> ${formattedDate}
                            </p>
                            <p><strong>Customer:</strong> ${escapeHtml(order.customerName || 'N/A')}</p>
                            <p><strong>Total:</strong> Rs. ${order.totalAmount?.toLocaleString() || '0'}</p>
                        </div>
                        <div class="order-status-badge ${getStatusBadgeClass(order.status)}">
                            ${getStatusText(order.status)}
                        </div>
                    </div>
                    
                    ${order.timeline && order.timeline.length > 0 ? `
                        <div class="tracking-timeline">
                            <h5 style="margin-bottom: 1rem;">Tracking History</h5>
                            ${order.timeline.map(event => {
                                const eventDate = event.timestamp?.toDate ? 
                                    event.timestamp.toDate() : new Date(event.timestamp);
                                const formattedEventDate = eventDate.toLocaleString('en-PK', {
                                    day: '2-digit',
                                    month: 'short',
                                    year: 'numeric',
                                    hour: '2-digit',
                                    minute: '2-digit'
                                });
                                
                                return `
                                    <div class="timeline-item">
                                        <div class="timeline-date">
                                            ${formattedEventDate}
                                        </div>
                                        <div class="timeline-content">
                                            <strong>${getStatusText(event.status)}</strong>
                                            ${event.note ? `<p style="margin-top: 0.25rem;">${escapeHtml(event.note)}</p>` : ''}
                                            ${event.trackingNumber ? `
                                                <p style="margin-top: 0.25rem;">
                                                    <strong>Tracking #:</strong> ${event.trackingNumber}
                                                </p>
                                            ` : ''}
                                        </div>
                                    </div>
                                `;
                            }).join('')}
                        </div>
                    ` : `
                        <div style="text-align: center; padding: 1.5rem; background: var(--accent); border-radius: var(--radius); margin: 1rem 0;">
                            <i class="fas fa-clock" style="font-size: 2rem; color: var(--text-secondary); margin-bottom: 0.5rem;"></i>
                            <p>No tracking updates yet</p>
                        </div>
                    `}
                    
                    <div style="margin-top: 1rem; display: flex; gap: 0.5rem;">
                        <button class="btn btn-primary" onclick="updateOrderStatus('${order.id}')">
                            <i class="fas fa-edit"></i> Update Tracking
                        </button>
                        <button class="btn btn-secondary" onclick="viewOrderDetails('${order.id}')">
                            <i class="fas fa-eye"></i> View Details
                        </button>
                    </div>
                </div>
            `;
        }).join('');
        
    } catch (error) {
        console.error('Error loading tracking orders:', error);
        
        if (error.code === 'failed-precondition') {
            console.log('Index error, using sample data');
            createSampleTrackingOrders();
            showToast('Using sample tracking data', 'info');
        } else {
            showToast('Error loading tracking data: ' + error.message, 'error');
            createSampleTrackingOrders();
        }
    }
}

    async function loadWithdrawalManagement() {
    console.log('Loading withdrawal management...');
    
    if (!currentSeller) {
        console.error('No seller logged in');
        showToast('Please login as a seller first', 'error');
        return;
    }
    
    console.log('Seller ID:', currentSeller.id);
    
    try {
        // 1. Load seller data to get available balance
        const sellerDoc = await db.collection('sellers').doc(currentSeller.id).get();
        
        if (!sellerDoc.exists) {
            console.error('Seller document not found');
            showToast('Seller profile not found', 'error');
            return;
        }
        
        const sellerData = sellerDoc.data();
        console.log('Seller data:', sellerData);
        
        availableBalance = sellerData.availableBalance || 0;
        pendingWithdrawal = sellerData.pendingWithdrawal || 0;
        
        console.log('Available balance:', availableBalance);
        console.log('Pending withdrawal:', pendingWithdrawal);
        
        document.getElementById('availableBalance').textContent = availableBalance.toLocaleString();
        
        // 2. Try to load withdrawal history with simpler query
        let withdrawalHistory = [];
        
        try {
            // Try with ordering first (requires index)
            const snapshot = await db.collection('withdrawals')
                .where('sellerId', '==', currentSeller.id)
                .orderBy('requestDate', 'desc')
                .limit(50)
                .get();
            
            withdrawalHistory = snapshot.docs.map(doc => ({
                id: doc.id,
                ...doc.data()
            }));
            
            console.log('Withdrawals loaded with ordering:', withdrawalHistory.length);
            
        } catch (error) {
            console.error('Error with ordered query:', error);
            
            if (error.code === 'failed-precondition') {
                // Try without ordering
                console.log('Trying without ordering...');
                const snapshot = await db.collection('withdrawals')
                    .where('sellerId', '==', currentSeller.id)
                    .limit(50)
                    .get();
                
                withdrawalHistory = snapshot.docs.map(doc => ({
                    id: doc.id,
                    ...doc.data()
                }));
                
                // Sort manually in JavaScript
                withdrawalHistory.sort((a, b) => {
                    const dateA = a.requestDate?.toDate ? a.requestDate.toDate() : new Date(a.requestDate || 0);
                    const dateB = b.requestDate?.toDate ? b.requestDate.toDate() : new Date(b.requestDate || 0);
                    return dateB - dateA;
                });
                
                console.log('Withdrawals loaded without ordering:', withdrawalHistory.length);
            } else {
                throw error;
            }
        }
        
        // 3. Display withdrawal history
        const withdrawalHistoryElement = document.getElementById('withdrawalHistory');
        
        if (withdrawalHistory.length === 0) {
            withdrawalHistoryElement.innerHTML = `
                <tr>
                    <td colspan="6" style="text-align: center; padding: 2rem;">
                        <i class="fas fa-history" style="font-size: 2rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                        <p>No withdrawal history</p>
                    </td>
                </tr>
            `;
        } else {
            withdrawalHistoryElement.innerHTML = withdrawalHistory.map(withdrawal => {
                const requestDate = withdrawal.requestDate?.toDate ? 
                    withdrawal.requestDate.toDate() : new Date(withdrawal.requestDate);
                const completionDate = withdrawal.completionDate?.toDate ? 
                    withdrawal.completionDate.toDate() : null;
                
                const formattedRequestDate = requestDate.toLocaleDateString('en-PK', {
                    day: '2-digit',
                    month: 'short',
                    year: 'numeric'
                });
                
                const formattedCompletionDate = completionDate ? 
                    completionDate.toLocaleDateString('en-PK', {
                        day: '2-digit',
                        month: 'short',
                        year: 'numeric'
                    }) : 'N/A';
                
                return `
                    <tr>
                        <td style="padding: 0.75rem;">${withdrawal.id.slice(-8)}</td>
                        <td style="padding: 0.75rem;">Rs. ${(withdrawal.amount || 0).toLocaleString()}</td>
                        <td style="padding: 0.75rem;">
                            ${withdrawal.method === 'easypaisa' ? 
                                '<i class="fas fa-mobile-alt"></i> EasyPaisa' : 
                                '<i class="fas fa-wallet"></i> JazzCash'}
                        </td>
                        <td style="padding: 0.75rem;">
                            <span class="status-badge ${getWithdrawalStatusBadge(withdrawal.status || 'pending')}">
                                ${getWithdrawalStatusText(withdrawal.status || 'pending')}
                            </span>
                        </td>
                        <td style="padding: 0.75rem;">${formattedRequestDate}</td>
                        <td style="padding: 0.75rem;">${formattedCompletionDate}</td>
                    </tr>
                `;
            }).join('');
        }
        
        console.log('Withdrawal management loaded successfully');
        
    } catch (error) {
        console.error('Error loading withdrawal management:', error);
        
        // Create sample withdrawal data for demonstration
        createSampleWithdrawalData();
        showToast('Using sample withdrawal data for demonstration', 'info');
    }
}

// Helper function to create sample withdrawal data
function createSampleWithdrawalData() {
    console.log('Creating sample withdrawal data...');
    
    availableBalance = 15000;
    pendingWithdrawal = 5000;
    
    document.getElementById('availableBalance').textContent = availableBalance.toLocaleString();
    
    // Sample withdrawal history
    const sampleWithdrawals = [
        {
            id: 'WD-001',
            amount: 10000,
            method: 'easypaisa',
            status: 'completed',
            requestDate: new Date(Date.now() - 7 * 24 * 60 * 60 * 1000),
            completionDate: new Date(Date.now() - 6 * 24 * 60 * 60 * 1000)
        },
        {
            id: 'WD-002',
            amount: 5000,
            method: 'jazzcash',
            status: 'pending',
            requestDate: new Date(Date.now() - 2 * 24 * 60 * 60 * 1000),
            completionDate: null
        },
        {
            id: 'WD-003',
            amount: 8000,
            method: 'easypaisa',
            status: 'approved',
            requestDate: new Date(Date.now() - 1 * 24 * 60 * 60 * 1000),
            completionDate: null
        }
    ];
    
    const withdrawalHistoryElement = document.getElementById('withdrawalHistory');
    withdrawalHistoryElement.innerHTML = sampleWithdrawals.map(withdrawal => {
        const formattedRequestDate = withdrawal.requestDate.toLocaleDateString('en-PK', {
            day: '2-digit',
            month: 'short',
            year: 'numeric'
        });
        
        const formattedCompletionDate = withdrawal.completionDate ? 
            withdrawal.completionDate.toLocaleDateString('en-PK', {
                day: '2-digit',
                month: 'short',
                year: 'numeric'
            }) : 'N/A';
        
        return `
            <tr>
                <td style="padding: 0.75rem;">${withdrawal.id}</td>
                <td style="padding: 0.75rem;">Rs. ${withdrawal.amount.toLocaleString()}</td>
                <td style="padding: 0.75rem;">
                    ${withdrawal.method === 'easypaisa' ? 
                        '<i class="fas fa-mobile-alt"></i> EasyPaisa' : 
                        '<i class="fas fa-wallet"></i> JazzCash'}
                </td>
                <td style="padding: 0.75rem;">
                    <span class="status-badge ${getWithdrawalStatusBadge(withdrawal.status)}">
                        ${getWithdrawalStatusText(withdrawal.status)}
                    </span>
                </td>
                <td style="padding: 0.75rem;">${formattedRequestDate}</td>
                <td style="padding: 0.75rem;">${formattedCompletionDate}</td>
            </tr>
        `;
    }).join('');
}

    async function handleWithdrawalRequest(e) {
    e.preventDefault();
    console.log('Handling withdrawal request...');
    
    if (!currentSeller) {
        showToast('Please login as a seller first', 'error');
        return;
    }
    
    try {
        const amount = parseFloat(document.getElementById('withdrawalAmount').value);
        const method = document.getElementById('withdrawalMethod').value;
        const account = document.getElementById('withdrawalAccount').value.trim();
        const accountName = document.getElementById('withdrawalAccountName').value.trim();
        const cnic = document.getElementById('withdrawalCNIC').value.trim();
        
        console.log('Withdrawal details:', { amount, method, account, accountName, cnic });
        
        // Validate inputs
        if (!amount || amount <= 0) {
            showToast('Please enter a valid amount', 'error');
            return;
        }
        
        if (amount < 500) {
            showToast('Minimum withdrawal amount is Rs. 500', 'error');
            return;
        }
        
        if (amount > availableBalance) {
            showToast(`Insufficient balance. Available: Rs. ${availableBalance.toLocaleString()}`, 'error');
            return;
        }
        
        if (!method) {
            showToast('Please select a payment method', 'error');
            return;
        }
        
        if (!account) {
            showToast('Please enter account number', 'error');
            return;
        }
        
        if (!accountName) {
            showToast('Please enter account holder name', 'error');
            return;
        }
        
        if (!cnic) {
            showToast('Please enter CNIC number', 'error');
            return;
        }
        
        // Validate CNIC format (XXXXX-XXXXXXX-X)
        const cnicRegex = /^\d{5}-\d{7}-\d{1}$/;
        if (!cnicRegex.test(cnic)) {
            showToast('Please enter CNIC in format: XXXXX-XXXXXXX-X', 'error');
            return;
        }
        
        // Validate phone number if it's mobile wallet
        const phoneRegex = /^03\d{2}-\d{7}$/;
        if (method === 'easypaisa' || method === 'jazzcash') {
            if (!phoneRegex.test(account)) {
                showToast('Please enter phone number in format: 03XX-XXXXXXX', 'error');
                return;
            }
        }
        
        const withdrawalData = {
            sellerId: currentSeller.id,
            sellerName: currentSeller.shopName || currentSeller.name || 'Unknown Seller',
            amount: amount,
            method: method,
            accountNumber: account,
            accountName: accountName,
            cnic: cnic,
            status: 'pending',
            requestDate: new Date(),
            notes: '',
            createdAt: new Date(),
            updatedAt: new Date()
        };
        
        console.log('Creating withdrawal:', withdrawalData);
        
        // Create withdrawal request
        const withdrawalRef = await db.collection('withdrawals').add(withdrawalData);
        console.log('Withdrawal created with ID:', withdrawalRef.id);
        
        // Update seller's available balance
        await db.collection('sellers').doc(currentSeller.id).update({
            availableBalance: firebase.firestore.FieldValue.increment(-amount),
            pendingWithdrawal: firebase.firestore.FieldValue.increment(amount),
            updatedAt: new Date()
        });
        
        // Update local variables
        availableBalance -= amount;
        pendingWithdrawal += amount;
        
        showToast(`Withdrawal request submitted successfully for Rs. ${amount.toLocaleString()}. It will be processed within 24 hours.`, 'success');
        
        // Reset form
        document.getElementById('withdrawalRequestForm').reset();
        
        // Reload data
        setTimeout(() => {
            loadWithdrawalManagement();
            loadSellerDashboard();
        }, 1000);
        
    } catch (error) {
        console.error('Error submitting withdrawal request:', error);
        
        if (error.code === 'failed-precondition') {
            showToast('Firestore index needs to be created. Please try again in a moment.', 'error');
            
            // Create sample withdrawal locally for demonstration
            createSampleWithdrawal();
        } else {
            showToast('Error submitting withdrawal request: ' + error.message, 'error');
        }
    }
}

// Helper function to create sample withdrawal
function createSampleWithdrawal() {
    const amount = parseFloat(document.getElementById('withdrawalAmount').value);
    
    // Update local balance
    availableBalance -= amount;
    pendingWithdrawal += amount;
    
    // Update UI
    document.getElementById('availableBalance').textContent = availableBalance.toLocaleString();
    
    showToast(`Sample withdrawal created for Rs. ${amount.toLocaleString()}. Note: This is a demonstration only.`, 'warning');
    
    // Reset form
    document.getElementById('withdrawalRequestForm').reset();
    
    // Reload withdrawal management
    loadWithdrawalManagement();
}
    async function loadTaxInvoices() {
    console.log('Loading tax invoices...');
    
    if (!currentSeller) {
        console.error('No seller logged in');
        showToast('Please login as a seller first', 'error');
        return;
    }
    
    console.log('Seller ID:', currentSeller.id);
    
    try {
        let lockedInvoices = [];
        const invoicesList = document.getElementById('lockedInvoicesList');
        
        // Clear loading state
        invoicesList.innerHTML = `
            <div style="text-align: center; padding: 2rem;">
                <div class="loading" style="margin: 0 auto; width: 30px; height: 30px;"></div>
                <p style="margin-top: 1rem; color: var(--text-secondary);">Loading invoices...</p>
            </div>
        `;
        
        // First, let's check what orders we have for this seller
        const ordersSnapshot = await db.collection('orders')
            .where('sellerId', '==', currentSeller.id)
            .limit(20)
            .get();
        
        console.log('Total orders found:', ordersSnapshot.docs.length);
        
        // Log all orders to see their structure
        ordersSnapshot.docs.forEach((doc, index) => {
            console.log(`Order ${index + 1}:`, {
                id: doc.id,
                data: doc.data(),
                hasInvoiceLocked: 'invoiceLocked' in doc.data(),
                taxPaymentStatus: doc.data().taxPaymentStatus,
                taxPaymentSubmitted: doc.data().taxPaymentSubmitted
            });
        });
        
        // Method 1: Try to find invoices with specific tax fields
        try {
            // Try query with taxPaymentStatus field
            const taxSnapshot = await db.collection('orders')
                .where('sellerId', '==', currentSeller.id)
                .where('taxPaymentStatus', 'in', ['pending', 'locked', 'required'])
                .limit(10)
                .get();
            
            console.log('Found invoices via taxPaymentStatus:', taxSnapshot.docs.length);
            
            lockedInvoices = taxSnapshot.docs.map(doc => ({
                id: doc.id,
                ...doc.data(),
                invoiceLocked: true, // Mark as locked for display
                createdAt: doc.data().createdAt?.toDate ? doc.data().createdAt.toDate() : new Date(doc.data().createdAt || Date.now())
            }));
            
        } catch (error) {
            console.error('Error with taxPaymentStatus query:', error);
            
            // Method 2: Try to find invoices that need tax payment
            try {
                // Check for orders that might need tax invoices
                const allOrders = ordersSnapshot.docs.map(doc => ({
                    id: doc.id,
                    ...doc.data(),
                    createdAt: doc.data().createdAt?.toDate ? doc.data().createdAt.toDate() : new Date(doc.data().createdAt || Date.now())
                }));
                
                // Filter orders that are delivered/completed but don't have tax invoice generated
                lockedInvoices = allOrders.filter(order => {
                    const delivered = ['delivered', 'completed', 'shipped'].includes(order.status);
                    const hasTaxPayment = order.taxPaymentStatus || order.taxPaymentSubmitted || order.invoiceLocked;
                    return delivered && !hasTaxPayment;
                });
                
                console.log('Filtered invoices needing tax payment:', lockedInvoices.length);
                
            } catch (filterError) {
                console.error('Error filtering orders:', filterError);
                
                // Method 3: Create sample invoices for demonstration
                createSampleTaxInvoices();
                showToast('Using sample tax invoice data for demonstration', 'info');
                return;
            }
        }
        
        // Display the invoices
        if (lockedInvoices.length === 0) {
            invoicesList.innerHTML = `
                <div style="text-align: center; padding: 3rem;">
                    <i class="fas fa-file-invoice" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                    <h3>No Tax Invoices Required</h3>
                    <p>All your invoices are processed and paid.</p>
                    <button class="btn btn-primary" onclick="createSampleTaxInvoices()" style="margin-top: 1rem;">
                        <i class="fas fa-plus"></i> Create Sample Invoices for Testing
                    </button>
                </div>
            `;
            return;
        }
        
        // Sort by date (newest first)
        lockedInvoices.sort((a, b) => b.createdAt - a.createdAt);
        
        invoicesList.innerHTML = lockedInvoices.map(order => {
            const orderDate = order.createdAt;
            const formattedDate = orderDate.toLocaleDateString('en-PK', {
                day: '2-digit',
                month: 'short',
                year: 'numeric',
                hour: '2-digit',
                minute: '2-digit'
            });
            
            // Calculate tax amount (5% of order total)
            const taxAmount = Math.round(order.totalAmount * 0.05);
            const totalWithTax = order.totalAmount + taxAmount;
            
            return `
                <div class="order-card" style="position: relative;">
                    ${order.taxPaymentStatus === 'pending' ? `
                        <div class="tax-invoice-lock">
                            <i class="fas fa-clock"></i>
                            <h4>Tax Payment Pending Review</h4>
                            <p>Your Rs. 50 payment is being verified</p>
                        </div>
                    ` : `
                        <div class="tax-invoice-lock">
                            <i class="fas fa-lock"></i>
                            <h4>Tax Invoice Locked</h4>
                            <p>Pay Rs. 50 to unlock and generate tax invoice</p>
                        </div>
                    `}
                    
                    <div class="order-header">
                        <div>
                            <h3 style="color: var(--primary);">Order #${order.id.slice(-8)}</h3>
                            <p style="color: var(--text-secondary);">
                                <i class="far fa-calendar"></i> ${formattedDate}
                            </p>
                            <p><strong>Customer:</strong> ${escapeHtml(order.customerName || 'Customer')}</p>
                            <p><strong>Status:</strong> 
                                <span class="order-status-badge ${getStatusBadgeClass(order.status)}">
                                    ${getStatusText(order.status)}
                                </span>
                            </p>
                        </div>
                        <div style="text-align: right;">
                            <div>
                                <p><strong>Order Total:</strong> Rs. ${(order.totalAmount || 0).toLocaleString()}</p>
                                <p><strong>Tax (5%):</strong> Rs. ${taxAmount.toLocaleString()}</p>
                                <p><strong>Total with Tax:</strong> Rs. ${totalWithTax.toLocaleString()}</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="order-items">
                        ${order.items && order.items.length > 0 ? order.items.slice(0, 3).map(item => `
                            <div class="order-item">
                                <img src="${item.image || 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'}" 
                                     class="order-item-image" 
                                     alt="${escapeHtml(item.productName || 'Product')}"
                                     onerror="this.src='https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'">
                                <div style="flex: 1;">
                                    <h4>${escapeHtml(item.productName || 'Product')}</h4>
                                    <p><strong>Qty:</strong> ${item.quantity} | 
                                       <strong>Price:</strong> Rs. ${item.price?.toLocaleString() || '0'}</p>
                                </div>
                            </div>
                        `).join('') : `<p>No items found</p>`}
                        
                        ${order.items && order.items.length > 3 ? `
                            <div style="text-align: center; padding: 1rem; color: var(--text-secondary);">
                                <i class="fas fa-ellipsis-h"></i> 
                                And ${order.items.length - 3} more items
                            </div>
                        ` : ''}
                    </div>
                    
                    <div style="margin-top: 1rem; text-align: center;">
                        <button class="btn btn-warning" onclick="unlockTaxInvoice('${order.id}', ${order.totalAmount || 0})">
                            <i class="fas fa-unlock"></i> Generate & Unlock Tax Invoice (Rs. 50)
                        </button>
                        <button class="btn btn-secondary" onclick="viewOrderDetails('${order.id}')" style="margin-left: 0.5rem;">
                            <i class="fas fa-eye"></i> View Order
                        </button>
                    </div>
                    
                    ${order.taxPaymentSubmitted ? `
                        <div style="margin-top: 1rem; padding: 1rem; background: var(--info); color: white; border-radius: var(--radius); text-align: center;">
                            <i class="fas fa-check-circle"></i> Tax payment submitted. Waiting for admin verification.
                        </div>
                    ` : ''}
                </div>
            `;
        }).join('');
        
        console.log('Tax invoices loaded successfully:', lockedInvoices.length);
        
    } catch (error) {
        console.error('Error loading tax invoices:', error);
        
        // Show error and provide sample data
        invoicesList.innerHTML = `
            <div style="text-align: center; padding: 3rem;">
                <i class="fas fa-exclamation-triangle" style="font-size: 3rem; color: var(--warning); margin-bottom: 1rem;"></i>
                <h3>Error Loading Tax Invoices</h3>
                <p>${error.message || 'Could not load tax invoices'}</p>
                <div style="margin-top: 1rem;">
                    <button class="btn btn-primary" onclick="loadTaxInvoices()" style="margin: 0.25rem;">
                        <i class="fas fa-redo"></i> Try Again
                    </button>
                    <button class="btn btn-secondary" onclick="createSampleTaxInvoices()" style="margin: 0.25rem;">
                        <i class="fas fa-plus"></i> Use Sample Data
                    </button>
                </div>
            </div>
        `;
    }
}

// Helper function to create sample tax invoices
function createSampleTaxInvoices() {
    console.log('Creating sample tax invoices...');
    
    const invoicesList = document.getElementById('lockedInvoicesList');
    
    // Create sample invoices based on recent orders
    const sampleInvoices = [];
    
    if (sellerOrders.length > 0) {
        // Use real orders as base
        sellerOrders.slice(0, 3).forEach((order, index) => {
            if (['delivered', 'completed', 'shipped'].includes(order.status)) {
                sampleInvoices.push({
                    id: order.id,
                    ...order,
                    invoiceLocked: true,
                    taxPaymentStatus: 'required',
                    taxPaymentSubmitted: index === 0, // First one shows as submitted
                    createdAt: order.createdAt
                });
            }
        });
    }
    
    // If no real orders, create sample data
    if (sampleInvoices.length === 0) {
        for (let i = 1; i <= 3; i++) {
            const orderDate = new Date(Date.now() - i * 2 * 24 * 60 * 60 * 1000);
            const totalAmount = Math.floor(Math.random() * 5000) + 1000;
            
            sampleInvoices.push({
                id: `sample-invoice-${i}`,
                customerName: `Customer ${i}`,
                customerEmail: `customer${i}@example.com`,
                customerPhone: `03${Math.floor(Math.random() * 100)}-${Math.floor(Math.random() * 10000000).toString().padStart(7, '0')}`,
                status: 'delivered',
                totalAmount: totalAmount,
                subtotal: totalAmount * 0.95,
                shippingFee: 200,
                paymentMethod: 'cod',
                paymentStatus: 'paid',
                shippingAddress: `Street ${i}, City`,
                shippingCity: 'Lahore',
                items: [
                    {
                        productName: `Sample Product ${i}`,
                        quantity: i,
                        price: Math.floor(totalAmount / i),
                        image: 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'
                    }
                ],
                invoiceLocked: true,
                taxPaymentStatus: i === 1 ? 'pending' : 'required',
                taxPaymentSubmitted: i === 1,
                createdAt: orderDate
            });
        }
    }
    
    // Display sample invoices
    invoicesList.innerHTML = sampleInvoices.map(order => {
        const orderDate = order.createdAt;
        const formattedDate = orderDate.toLocaleDateString('en-PK', {
            day: '2-digit',
            month: 'short',
            year: 'numeric'
        });
        
        const taxAmount = Math.round(order.totalAmount * 0.05);
        const totalWithTax = order.totalAmount + taxAmount;
        
        return `
            <div class="order-card" style="position: relative;">
                ${order.taxPaymentStatus === 'pending' ? `
                    <div class="tax-invoice-lock" style="background: linear-gradient(135deg, #3498DB, #2980B9);">
                        <i class="fas fa-clock"></i>
                        <h4>Tax Payment Pending Review</h4>
                        <p>Your Rs. 50 payment is being verified (Sample)</p>
                    </div>
                ` : `
                    <div class="tax-invoice-lock">
                        <i class="fas fa-lock"></i>
                        <h4>Tax Invoice Locked (Sample Data)</h4>
                        <p>Pay Rs. 50 to unlock and generate tax invoice</p>
                    </div>
                `}
                
                <div class="order-header">
                    <div>
                        <h3 style="color: var(--primary);">Order #${order.id.slice(-8)}</h3>
                        <p style="color: var(--text-secondary);">
                            <i class="far fa-calendar"></i> ${formattedDate}
                        </p>
                        <p><strong>Customer:</strong> ${escapeHtml(order.customerName || 'Customer')}</p>
                    </div>
                    <div style="text-align: right;">
                        <div>
                            <p><strong>Order Total:</strong> Rs. ${(order.totalAmount || 0).toLocaleString()}</p>
                            <p><strong>Tax (5%):</strong> Rs. ${taxAmount.toLocaleString()}</p>
                            <p><strong>Total with Tax:</strong> Rs. ${totalWithTax.toLocaleString()}</p>
                        </div>
                    </div>
                </div>
                
                <div style="margin-top: 1rem; text-align: center;">
                    <button class="btn btn-warning" onclick="unlockTaxInvoice('${order.id}', ${order.totalAmount || 0})">
                        <i class="fas fa-unlock"></i> Generate & Unlock Tax Invoice (Rs. 50)
                    </button>
                    <button class="btn btn-secondary" onclick="viewSampleInvoiceDetails('${order.id}')" style="margin-left: 0.5rem;">
                        <i class="fas fa-eye"></i> View Details
                    </button>
                </div>
                
                ${order.taxPaymentSubmitted ? `
                    <div style="margin-top: 1rem; padding: 1rem; background: var(--info); color: white; border-radius: var(--radius); text-align: center;">
                        <i class="fas fa-check-circle"></i> Tax payment submitted. Waiting for admin verification.
                    </div>
                ` : ''}
            </div>
        `;
    }).join('');
    
    showToast('Sample tax invoices loaded for demonstration', 'info');
}

  async function unlockTaxInvoice(orderId, orderAmount = 0) {
    console.log('Unlocking tax invoice for order:', orderId);
    
    if (!currentSeller) {
        showToast('Please login as a seller first', 'error');
        return;
    }
    
    // Set invoice details in modal
    document.getElementById('invoiceNumberDisplay').textContent = orderId.slice(-8);
    document.getElementById('taxInvoiceNumber').value = orderId;
    document.getElementById('taxInvoiceAmount').value = orderAmount;
    
    // Reset form
    document.getElementById('taxTransactionId').value = '';
    document.getElementById('taxPaymentMethod').value = '';
    document.getElementById('taxPaymentProof').value = '';
    
    // Show payment amount in modal title
    document.querySelector('#taxInvoicePaymentModal .modal-content h3').innerHTML = `
        <i class="fas fa-file-invoice-dollar"></i> Unlock Tax Invoice - Rs. 50
    `;
    
    openModal('taxInvoicePaymentModal');
}

// Helper function for sample invoice details
function viewSampleInvoiceDetails(orderId) {
    alert(`Sample Invoice Details:\n\nOrder ID: ${orderId}\nThis is sample data for demonstration.\n\nTo test the tax invoice system:\n1. Click "Generate & Unlock Tax Invoice"\n2. Enter payment details\n3. Submit payment proof\n\nNote: This is a demonstration only.`);
}

    async function submitTaxPayment() {
    console.log('Submitting tax payment...');
    
    if (!currentSeller) {
        showToast('Please login as a seller first', 'error');
        return;
    }
    
    const method = document.getElementById('taxPaymentMethod').value;
    const transactionId = document.getElementById('taxTransactionId').value.trim();
    const invoiceNumber = document.getElementById('taxInvoiceNumber').value.trim();
    const paymentProof = document.getElementById('taxPaymentProof').files[0];
    
    console.log('Payment details:', { method, transactionId, invoiceNumber });
    
    if (!method) {
        showToast('Please select a payment method', 'error');
        return;
    }
    
    if (!transactionId) {
        showToast('Please enter transaction ID', 'error');
        return;
    }
    
    if (!invoiceNumber) {
        showToast('Invoice number is required', 'error');
        return;
    }
    
    // Validate transaction ID format
    if (transactionId.length < 8) {
        showToast('Transaction ID should be at least 8 characters', 'error');
        return;
    }
    
    try {
        let paymentProofUrl = '';
        
        // Upload payment proof if provided
        if (paymentProof) {
            console.log('Uploading payment proof...');
            
            // Validate file size (max 5MB)
            if (paymentProof.size > 5 * 1024 * 1024) {
                showToast('Payment proof image should be less than 5MB', 'error');
                return;
            }
            
            // Validate file type
            const validTypes = ['image/jpeg', 'image/png', 'image/jpg', 'image/webp'];
            if (!validTypes.includes(paymentProof.type)) {
                showToast('Please upload a valid image (JPG, PNG, WEBP)', 'error');
                return;
            }
            
            const storageRef = storage.ref(`tax_payments/${currentSeller.id}/${Date.now()}_${paymentProof.name}`);
            await storageRef.put(paymentProof);
            paymentProofUrl = await storageRef.getDownloadURL();
            console.log('Payment proof uploaded:', paymentProofUrl);
        }
        
        const paymentData = {
            orderId: invoiceNumber,
            sellerId: currentSeller.id,
            sellerName: currentSeller.shopName || currentSeller.name,
            amount: 50,
            method: method,
            transactionId: transactionId,
            paymentProof: paymentProofUrl,
            status: 'pending',
            submittedAt: new Date(),
            notes: 'Tax invoice generation fee',
            createdAt: new Date(),
            updatedAt: new Date()
        };
        
        console.log('Creating tax payment record:', paymentData);
        
        // Save payment record
        const paymentRef = await db.collection('taxPayments').add(paymentData);
        console.log('Tax payment record created:', paymentRef.id);
        
        // Update order with tax payment status
        try {
            await db.collection('orders').doc(invoiceNumber).update({
                taxPaymentStatus: 'pending',
                taxPaymentSubmitted: true,
                taxPaymentId: paymentRef.id,
                taxPaymentDate: new Date(),
                updatedAt: new Date()
            });
            console.log('Order updated with tax payment status');
        } catch (orderError) {
            console.warn('Could not update order, but payment was recorded:', orderError);
            // Continue anyway - the payment is recorded
        }
        
        // Close modal
        closeModal('taxInvoicePaymentModal');
        
        // Show success message
        showToast('Tax payment submitted successfully! Your invoice will be unlocked after admin verification. You will be notified once it is approved.', 'success');
        
        // Reload tax invoices
        setTimeout(() => {
            loadTaxInvoices();
        }, 1000);
        
        // Send notification to admin
        try {
            await db.collection('notifications').add({
                type: 'tax_payment_submitted',
                title: 'New Tax Payment Submitted',
                message: `Seller ${currentSeller.shopName || currentSeller.name} submitted tax payment for order ${invoiceNumber.slice(-8)}`,
                userId: 'admin', // This would be the admin user ID
                read: false,
                data: {
                    orderId: invoiceNumber,
                    sellerId: currentSeller.id,
                    paymentId: paymentRef.id
                },
                createdAt: new Date()
            });
            console.log('Admin notification sent');
        } catch (notificationError) {
            console.warn('Could not send admin notification:', notificationError);
        }
        
    } catch (error) {
        console.error('Error submitting tax payment:', error);
        
        if (error.code === 'failed-precondition') {
            showToast('Firestore index needs to be created. Please try again in a moment.', 'error');
            
            // Simulate success for demonstration
            simulateTaxPaymentSuccess(invoiceNumber);
        } else {
            showToast('Error submitting tax payment: ' + error.message, 'error');
        }
    }
}

// Helper function to simulate tax payment success
function simulateTaxPaymentSuccess(orderId) {
    closeModal('taxInvoicePaymentModal');
    
    showToast('Tax payment simulation successful! In a real system, this would be recorded in the database.', 'success');
    
    // Update UI to show payment submitted
    const invoicesList = document.getElementById('lockedInvoicesList');
    const invoiceElements = invoicesList.querySelectorAll('.order-card');
    
    invoiceElements.forEach(element => {
        const button = element.querySelector('button[onclick*="unlockTaxInvoice"]');
        if (button && button.getAttribute('onclick').includes(orderId)) {
            // Update the invoice card to show payment submitted
            const lockDiv = element.querySelector('.tax-invoice-lock');
            if (lockDiv) {
                lockDiv.innerHTML = `
                    <i class="fas fa-clock"></i>
                    <h4>Tax Payment Pending Review</h4>
                    <p>Your Rs. 50 payment is being verified (Demo)</p>
                `;
                lockDiv.style.background = 'linear-gradient(135deg, #3498DB, #2980B9)';
            }
            
            // Add submitted message
            const submittedDiv = document.createElement('div');
            submittedDiv.style.marginTop = '1rem';
            submittedDiv.style.padding = '1rem';
            submittedDiv.style.background = 'var(--info)';
            submittedDiv.style.color = 'white';
            submittedDiv.style.borderRadius = 'var(--radius)';
            submittedDiv.style.textAlign = 'center';
            submittedDiv.innerHTML = '<i class="fas fa-check-circle"></i> Tax payment submitted (Demo). Waiting for admin verification.';
            
            const actionsDiv = element.querySelector('div[style*="margin-top: 1rem; text-align: center;"]');
            if (actionsDiv) {
                actionsDiv.parentNode.insertBefore(submittedDiv, actionsDiv.nextSibling);
            }
        }
    });
    
    // Update seller dashboard
    setTimeout(() => {
        loadSellerDashboard();
    }, 500);
}

    async function loadSellerEarnings() {
        if (!currentSeller) return;
        
        try {
            const snapshot = await db.collection('orders')
                .where('sellerId', '==', currentSeller.id)
                .get();
            
            let totalEarnings = 0;
            let totalOrders = 0;
            let pendingEarnings = 0;
            let completedEarnings = 0;
            
            snapshot.docs.forEach(doc => {
                const order = doc.data();
                totalOrders++;
                
                if (order.status === 'delivered') {
                    completedEarnings += order.totalAmount || 0;
                } else {
                    pendingEarnings += order.totalAmount || 0;
                }
                
                totalEarnings += order.totalAmount || 0;
            });
            
            const earningsContent = document.getElementById('earningsContent');
            earningsContent.innerHTML = `
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-number">${totalOrders}</div>
                        <div class="stat-label">Total Orders</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">Rs. ${totalEarnings.toLocaleString()}</div>
                        <div class="stat-label">Total Earnings</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">Rs. ${completedEarnings.toLocaleString()}</div>
                        <div class="stat-label">Completed Earnings</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">Rs. ${pendingEarnings.toLocaleString()}</div>
                        <div class="stat-label">Pending Earnings</div>
                    </div>
                </div>
                
                <div style="margin-top: 2rem;">
                    <h4>Recent Transactions</h4>
                    <div style="background: var(--white); border-radius: var(--radius); padding: 1rem; margin-top: 1rem;">
                        ${snapshot.docs.slice(0, 10).map(doc => {
                            const order = doc.data();
                            const orderDate = order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt);
                            return `
                                <div style="display: flex; justify-content: space-between; padding: 0.75rem 0; border-bottom: 1px solid var(--border);">
                                    <div>
                                        <strong>Order #${doc.id.slice(-8)}</strong>
                                        <p style="color: var(--text-secondary); font-size: 0.9rem;">
                                            ${orderDate.toLocaleDateString()} • ${order.status}
                                        </p>
                                    </div>
                                    <div style="text-align: right;">
                                        <span style="font-weight: bold; color: var(--primary);">
                                            Rs. ${order.totalAmount?.toLocaleString() || '0'}
                                        </span>
                                    </div>
                                </div>
                            `;
                        }).join('')}
                    </div>
                </div>
            `;
            
        } catch (error) {
            console.error('Error loading seller earnings:', error);
            showToast('Error loading earnings data', 'error');
        }
    }

    async function loadOrderHistory() {
    console.log('Loading order history...');
    
    if (!currentSeller) {
        console.error('No seller logged in');
        showToast('Please login as a seller first', 'error');
        return;
    }
    
    const orderHistoryList = document.getElementById('orderHistoryList');
    
    // Show loading state
    orderHistoryList.innerHTML = `
        <div style="text-align: center; padding: 3rem;">
            <div class="loading" style="margin: 0 auto; width: 40px; height: 40px;"></div>
            <p style="margin-top: 1rem; color: var(--text-secondary);">Loading order history...</p>
        </div>
    `;
    
    try {
        let orders = [];
        const fromDate = document.getElementById('orderHistoryFrom')?.value;
        const toDate = document.getElementById('orderHistoryTo')?.value;
        const statusFilter = document.getElementById('orderHistoryStatus')?.value;
        
        // Build query
        let query = db.collection('orders').where('sellerId', '==', currentSeller.id);
        
        // Apply date filters
        if (fromDate) {
            const startDate = new Date(fromDate);
            startDate.setHours(0, 0, 0, 0);
            query = query.where('createdAt', '>=', startDate);
        }
        
        if (toDate) {
            const endDate = new Date(toDate);
            endDate.setHours(23, 59, 59, 999);
            query = query.where('createdAt', '<=', endDate);
        }
        
        // Apply status filter if selected
        if (statusFilter && statusFilter !== '') {
            query = query.where('status', '==', statusFilter);
        }
        
        // Try to order by date
        try {
            query = query.orderBy('createdAt', 'desc');
        } catch (error) {
            console.warn('Ordering not available:', error);
        }
        
        // Execute query
        const snapshot = await query.limit(100).get();
        
        orders = snapshot.docs.map(doc => {
            const data = doc.data();
            return {
                id: doc.id,
                ...data,
                createdAt: data.createdAt?.toDate ? data.createdAt.toDate() : new Date(data.createdAt || Date.now()),
                updatedAt: data.updatedAt?.toDate ? data.updatedAt.toDate() : new Date(data.updatedAt || Date.now())
            };
        });
        
        // If no orders found
        if (orders.length === 0) {
            orderHistoryList.innerHTML = `
                <div style="text-align: center; padding: 3rem;">
                    <i class="fas fa-history" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                    <h3>No Orders Found</h3>
                    <p>${fromDate || toDate || statusFilter ? 'No orders match your filter criteria.' : 'You have no orders yet.'}</p>
                    ${fromDate || toDate || statusFilter ? `
                        <button class="btn btn-primary" onclick="clearOrderHistoryFilters()" style="margin-top: 1rem;">
                            <i class="fas fa-filter"></i> Clear Filters
                        </button>
                    ` : ''}
                </div>
            `;
            return;
        }
        
        // Display orders
        displayOrderHistory(orders);
        
        // Initialize pagination
        initializeOrderHistoryPagination(orders);
        
        console.log('Order history loaded successfully:', orders.length);
        
    } catch (error) {
        console.error('Error loading order history:', error);
        
        // Show error message
        orderHistoryList.innerHTML = `
            <div style="text-align: center; padding: 3rem;">
                <i class="fas fa-exclamation-triangle" style="font-size: 3rem; color: var(--warning); margin-bottom: 1rem;"></i>
                <h3>Error Loading Order History</h3>
                <p style="color: var(--text-secondary); margin-bottom: 1.5rem;">${error.message || 'Could not load order history'}</p>
                <button class="btn btn-primary" onclick="loadOrderHistory()">
                    <i class="fas fa-redo"></i> Try Again
                </button>
            </div>
        `;
    }
}

// Display order history
function displayOrderHistory(orders) {
    const orderHistoryList = document.getElementById('orderHistoryList');
    
    orderHistoryList.innerHTML = orders.map(order => {
        const orderDate = order.createdAt;
        const formattedDate = orderDate.toLocaleDateString('en-PK', {
            day: '2-digit',
            month: 'short',
            year: 'numeric',
            hour: '2-digit',
            minute: '2-digit'
        });
        
        const totalItems = order.items ? order.items.reduce((sum, item) => sum + (item.quantity || 1), 0) : 0;
        
        return `
            <div class="order-card" id="history-order-${order.id}">
                <div class="order-header">
                    <div>
                        <h3 style="color: var(--primary);">
                            <i class="fas fa-receipt"></i> Order #${order.id.slice(-8)}
                        </h3>
                        <p style="color: var(--text-secondary); margin-top: 0.25rem;">
                            <i class="far fa-calendar"></i> ${formattedDate}
                        </p>
                        <div style="display: flex; gap: 1rem; margin-top: 0.5rem; flex-wrap: wrap;">
                            <div>
                                <strong>Customer:</strong> ${escapeHtml(order.customerName || 'N/A')}
                            </div>
                            <div>
                                <strong>Items:</strong> ${totalItems}
                            </div>
                            <div>
                                <strong>Payment:</strong> ${order.paymentMethod || 'COD'}
                            </div>
                        </div>
                    </div>
                    <div style="text-align: right;">
                        <div class="order-status-badge ${getStatusBadgeClass(order.status)}" style="font-size: 0.9rem;">
                            ${getStatusText(order.status)}
                        </div>
                        <div style="margin-top: 0.5rem;">
                            <p style="font-size: 1.5rem; font-weight: bold; color: var(--primary);">
                                Rs. ${(order.totalAmount || 0).toLocaleString()}
                            </p>
                        </div>
                    </div>
                </div>
                
                ${order.items && order.items.length > 0 ? `
                    <div class="order-items">
                        ${order.items.slice(0, 3).map(item => `
                            <div class="order-item">
                                <img src="${item.image || 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'}" 
                                     class="order-item-image" 
                                     alt="${escapeHtml(item.productName || 'Product')}"
                                     onerror="this.src='https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'">
                                <div style="flex: 1;">
                                    <h4>${escapeHtml(item.productName || 'Product')}</h4>
                                    <div style="display: flex; gap: 1rem; flex-wrap: wrap; margin-top: 0.25rem;">
                                        <span><strong>Qty:</strong> ${item.quantity || 1}</span>
                                        <span><strong>Price:</strong> Rs. ${(item.price || 0).toLocaleString()}</span>
                                        <span><strong>Total:</strong> Rs. ${((item.price || 0) * (item.quantity || 1)).toLocaleString()}</span>
                                    </div>
                                </div>
                            </div>
                        `).join('')}
                        
                        ${order.items.length > 3 ? `
                            <div style="text-align: center; padding: 1rem; color: var(--text-secondary); background: var(--accent); border-radius: var(--radius); margin-top: 0.5rem;">
                                <i class="fas fa-ellipsis-h"></i> 
                                ${order.items.length - 3} more item${order.items.length - 3 > 1 ? 's' : ''}
                            </div>
                        ` : ''}
                    </div>
                ` : '<p style="padding: 1rem; text-align: center; color: var(--text-secondary);">No items found</p>'}
                
                <div class="order-actions" style="margin-top: 1rem;">
                    <button class="btn btn-primary" onclick="viewOrderDetails('${order.id}')">
                        <i class="fas fa-eye"></i> View Details
                    </button>
                    <button class="btn btn-secondary" onclick="downloadOrderInvoice('${order.id}')">
                        <i class="fas fa-download"></i> Download Invoice
                    </button>
                    <button class="btn btn-info" onclick="messageBuyer('${order.customerId || ''}', '${order.id}')">
                        <i class="fas fa-comment"></i> Contact Buyer
                    </button>
                    ${order.status !== 'cancelled' && order.status !== 'delivered' ? `
                        <button class="btn btn-warning" onclick="updateOrderStatus('${order.id}')">
                            <i class="fas fa-edit"></i> Update Status
                        </button>
                    ` : ''}
                </div>
            </div>
        `;
    }).join('');
}

// Initialize pagination
function initializeOrderHistoryPagination(orders) {
    const paginationElement = document.getElementById('orderHistoryPagination');
    const itemsPerPage = 5;
    const totalPages = Math.ceil(orders.length / itemsPerPage);
    
    if (totalPages <= 1) {
        paginationElement.innerHTML = '';
        return;
    }
    
    let currentPage = 1;
    
    function displayPage(page) {
        currentPage = page;
        const startIndex = (page - 1) * itemsPerPage;
        const endIndex = startIndex + itemsPerPage;
        const pageOrders = orders.slice(startIndex, endIndex);
        
        displayOrderHistory(pageOrders);
        updatePaginationButtons();
    }
    
    function updatePaginationButtons() {
        let paginationHTML = '';
        
        // Previous button
        paginationHTML += `
            <button class="page-btn" onclick="displayPage(${currentPage - 1})" ${currentPage === 1 ? 'disabled' : ''}>
                <i class="fas fa-chevron-left"></i>
            </button>
        `;
        
        // Page numbers
        const maxVisiblePages = 5;
        let startPage = Math.max(1, currentPage - Math.floor(maxVisiblePages / 2));
        let endPage = Math.min(totalPages, startPage + maxVisiblePages - 1);
        
        if (endPage - startPage + 1 < maxVisiblePages) {
            startPage = Math.max(1, endPage - maxVisiblePages + 1);
        }
        
        for (let i = startPage; i <= endPage; i++) {
            paginationHTML += `
                <button class="page-btn ${i === currentPage ? 'active' : ''}" onclick="displayPage(${i})">
                    ${i}
                </button>
            `;
        }
        
        // Next button
        paginationHTML += `
            <button class="page-btn" onclick="displayPage(${currentPage + 1})" ${currentPage === totalPages ? 'disabled' : ''}>
                <i class="fas fa-chevron-right"></i>
            </button>
        `;
        
        paginationElement.innerHTML = paginationHTML;
    }
    
    // Initialize with first page
    displayPage(1);
}

// Filter order history
function filterOrderHistory() {
    loadOrderHistory();
}

// Clear order history filters
function clearOrderHistoryFilters() {
    document.getElementById('orderHistoryFrom').value = '';
    document.getElementById('orderHistoryTo').value = '';
    document.getElementById('orderHistoryStatus').value = '';
    
    showToast('Filters cleared', 'info');
    loadOrderHistory();
}

    async function loadSellerConversation(conversationId) {
        if (!currentSeller) return;
        
        try {
            const conversationDoc = await db.collection('conversations').doc(conversationId).get();
            if (!conversationDoc.exists) return;
            
            const conversation = conversationDoc.data();
            currentChatId = conversationId;
            
            // Load messages
            const messagesSnapshot = await db.collection('messages')
                .where('conversationId', '==', conversationId)
                .orderBy('timestamp', 'asc')
                .get();
            
            messages = messagesSnapshot.docs.map(doc => ({
                id: doc.id,
                ...doc.data()
            }));
            
               // Update chat header
            document.getElementById('adminChatHeader').innerHTML = `
                <h4><i class="fas fa-headset"></i> Admin Support</h4>
                <p style="color: var(--text-secondary); font-size: 0.9rem;">24/7 Support Available</p>
            `;
            
            // Display messages
            const chatMessages = document.getElementById('adminChatMessages');
            chatMessages.innerHTML = messages.map(msg => `
                <div class="message ${msg.senderId === currentSeller.id ? 'sent' : 'received'}">
                    <p>${escapeHtml(msg.content)}</p>
                    <small style="display: block; margin-top: 0.25rem; opacity: 0.7;">
                        ${msg.senderName || (msg.senderId === currentSeller.id ? 'You' : 'Admin')} • 
                        ${msg.timestamp?.toDate ? msg.timestamp.toDate().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'}) : ''}
                    </small>
                </div>
            `).join('');
            
            // Scroll to bottom
            chatMessages.scrollTop = chatMessages.scrollHeight;
            
        } catch (error) {
            console.error('Error loading admin conversation:', error);
            showToast('Error loading conversation', 'error');
        }
    }

    async function sendAdminMessage() {
        if (!currentSeller || !currentChatId) return;
        
        const messageInput = document.getElementById('adminMessageInput');
        const message = messageInput.value.trim();
        
        if (!message) return;
        
        try {
            const messageData = {
                conversationId: currentChatId,
                senderId: currentSeller.id,
                senderName: currentSeller.shopName || currentSeller.name,
                receiverId: 'admin',
                content: message,
                timestamp: new Date(),
                read: false
            };
            
            // Save message
            await db.collection('messages').add(messageData);
            
            // Update conversation last message
            await db.collection('conversations').doc(currentChatId).update({
                lastMessage: message,
                lastMessageAt: new Date()
            });
            
            // Clear input
            messageInput.value = '';
            
            // Reload conversation
            loadAdminConversation(currentChatId);
            
        } catch (error) {
            console.error('Error sending message:', error);
            showToast('Error sending message', 'error');
        }
    }

    function messageBuyer(buyerId, orderId) {
        if (!currentSeller) return;
        
        // Check if conversation exists
        db.collection('conversations')
            .where('sellerId', '==', currentSeller.id)
            .where('buyerId', '==', buyerId)
            .limit(1)
            .get()
            .then(snapshot => {
                if (snapshot.empty) {
                    // Create new conversation
                    return createConversationWithBuyer(buyerId, orderId);
                } else {
                    // Switch to messages tab
                    switchSellerTab('messages');
                    loadSellerConversation(snapshot.docs[0].id);
                }
            })
            .catch(error => {
                console.error('Error checking conversation:', error);
                showToast('Error starting conversation', 'error');
            });
    }

    async function createConversationWithBuyer(buyerId, orderId) {
        try {
            // Get buyer info
            const buyerDoc = await db.collection('users').doc(buyerId).get();
            const buyerData = buyerDoc.exists ? buyerDoc.data() : {};
            
            const conversationData = {
                sellerId: currentSeller.id,
                sellerName: currentSeller.shopName || currentSeller.name,
                buyerId: buyerId,
                buyerName: buyerData.displayName || buyerData.email || 'Buyer',
                buyerEmail: buyerData.email || '',
                orderId: orderId,
                lastMessage: 'Conversation started',
                lastMessageAt: new Date(),
                createdAt: new Date()
            };
            
            const conversationRef = await db.collection('conversations').add(conversationData);
            
            // Switch to messages tab
            switchSellerTab('messages');
            loadSellerConversation(conversationRef.id);
            
        } catch (error) {
            console.error('Error creating conversation:', error);
            showToast('Error starting conversation', 'error');
        }
    }

    // ==================== GREEN THEME STYLES ====================
const greenTheme = {
    colors: {
        primary: '#10b981', // Emerald Green
        primaryLight: '#34d399',
        primaryDark: '#059669',
        secondary: '#059669', // Darker Green
        secondaryLight: '#10b981',
        success: '#10b981',
        warning: '#f59e0b',
        danger: '#ef4444',
        info: '#3b82f6',
        dark: '#111827',
        light: '#f9fafb',
        white: '#ffffff',
        gray50: '#f9fafb',
        gray100: '#f3f4f6',
        gray200: '#e5e7eb',
        gray300: '#d1d5db',
        gray400: '#9ca3af',
        gray500: '#6b7280',
        gray600: '#4b5563',
        gray700: '#374151',
        gray800: '#1f2937',
        gray900: '#111827',
        gradientPrimary: 'linear-gradient(135deg, #10b981 0%, #059669 100%)',
        gradientSecondary: 'linear-gradient(135deg, #34d399 0%, #10b981 100%)',
        gradientSuccess: 'linear-gradient(135deg, #10b981 0%, #047857 100%)',
        gradientWarning: 'linear-gradient(135deg, #f59e0b 0%, #d97706 100%)',
        gradientLightGreen: 'linear-gradient(135deg, #d1fae5 0%, #a7f3d0 100%)'
    },
    shadows: {
        sm: '0 1px 2px 0 rgba(0, 0, 0, 0.05)',
        md: '0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06)',
        lg: '0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05)',
        xl: '0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04)',
        glow: '0 0 20px rgba(16, 185, 129, 0.2)'
    },
    animations: {
        fadeIn: 'fadeIn 0.5s ease-out',
        slideUp: 'slideUp 0.3s ease-out',
        pulse: 'pulse 2s infinite',
        bounceIn: 'bounceIn 0.6s ease-out',
        shimmer: 'shimmer 1.5s infinite'
    }
};

// Add CSS animations
const style = document.createElement('style');
style.textContent = `
    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }
    
    @keyframes slideUp {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }
    
    @keyframes pulse {
        0% { box-shadow: 0 0 0 0 rgba(16, 185, 129, 0.4); }
        70% { box-shadow: 0 0 0 10px rgba(16, 185, 129, 0); }
        100% { box-shadow: 0 0 0 0 rgba(16, 185, 129, 0); }
    }
    
    @keyframes bounceIn {
        0% { transform: scale(0.9); opacity: 0; }
        50% { transform: scale(1.05); }
        100% { transform: scale(1); opacity: 1; }
    }
    
    @keyframes shimmer {
        0% { background-position: -200px 0; }
        100% { background-position: 200px 0; }
    }
    
    /* Premium Green Theme Components */
    .premium-card {
        background: ${greenTheme.colors.white};
        border-radius: 16px;
        box-shadow: ${greenTheme.shadows.lg};
        border: 1px solid ${greenTheme.colors.gray200};
        transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        animation: ${greenTheme.animations.fadeIn};
    }
    
    .premium-card:hover {
        box-shadow: ${greenTheme.shadows.xl};
        transform: translateY(-4px);
        border-color: ${greenTheme.colors.primaryLight};
    }
    
    .premium-btn {
        background: ${greenTheme.colors.gradientPrimary};
        color: white;
        border: none;
        padding: 14px 28px;
        border-radius: 12px;
        font-weight: 600;
        font-size: 16px;
        transition: all 0.3s ease;
        position: relative;
        overflow: hidden;
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
    }
    
    .premium-btn:hover {
        transform: translateY(-2px);
        box-shadow: ${greenTheme.shadows.glow};
    }
    
    .premium-btn:active {
        transform: translateY(0);
    }
    
    .premium-btn-secondary {
        background: ${greenTheme.colors.white};
        color: ${greenTheme.colors.primary};
        border: 2px solid ${greenTheme.colors.primary};
    }
    
    .premium-btn-secondary:hover {
        background: ${greenTheme.colors.primary};
        color: white;
    }
    
    .price-tag {
        background: ${greenTheme.colors.gradientSuccess};
        color: white;
        padding: 6px 16px;
        border-radius: 20px;
        font-weight: bold;
        font-size: 14px;
        display: inline-flex;
        align-items: center;
        gap: 4px;
        animation: ${greenTheme.animations.bounceIn};
    }
    
    .flash-sale-badge {
        background: ${greenTheme.colors.gradientWarning};
        color: white;
        padding: 8px 16px;
        border-radius: 20px;
        font-weight: bold;
        font-size: 12px;
        position: absolute;
        top: 12px;
        left: 12px;
        z-index: 10;
        animation: ${greenTheme.animations.pulse};
        box-shadow: ${greenTheme.shadows.md};
        display: flex;
        align-items: center;
        gap: 4px;
    }
    
    .product-image-wrapper {
        position: relative;
        overflow: hidden;
        border-radius: 12px;
        cursor: pointer;
        transition: transform 0.3s ease;
        background: ${greenTheme.colors.gray100};
    }
    
    .product-image-wrapper:hover {
        transform: scale(1.05);
    }
    
    .product-image-wrapper:hover::after {
        content: '👁 View Details';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: rgba(16, 185, 129, 0.9);
        color: white;
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: 600;
        font-size: 16px;
        animation: fadeIn 0.3s ease;
        border-radius: 12px;
    }
    
    .quantity-control {
        display: flex;
        align-items: center;
        gap: 8px;
        background: ${greenTheme.colors.gray100};
        padding: 6px;
        border-radius: 12px;
        width: fit-content;
        border: 1px solid ${greenTheme.colors.gray200};
    }
    
    .quantity-btn {
        width: 36px;
        height: 36px;
        border-radius: 10px;
        border: none;
        background: ${greenTheme.colors.white};
        color: ${greenTheme.colors.primary};
        font-weight: bold;
        cursor: pointer;
        transition: all 0.2s ease;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 16px;
    }
    
    .quantity-btn:hover {
        background: ${greenTheme.colors.primary};
        color: white;
        transform: scale(1.1);
    }
    
    .quantity-btn:disabled {
        opacity: 0.5;
        cursor: not-allowed;
    }
    
    .discount-badge {
        background: ${greenTheme.colors.gradientSuccess};
        color: white;
        padding: 4px 12px;
        border-radius: 12px;
        font-size: 12px;
        font-weight: 600;
        display: inline-flex;
        align-items: center;
        gap: 4px;
    }
    
    .green-badge {
        background: ${greenTheme.colors.gradientLightGreen};
        color: ${greenTheme.colors.primaryDark};
        padding: 8px 16px;
        border-radius: 12px;
        font-size: 14px;
        font-weight: 600;
        border: 1px solid ${greenTheme.colors.primaryLight};
        display: inline-flex;
        align-items: center;
        gap: 6px;
    }
    
    .section-title {
        background: ${greenTheme.colors.gradientPrimary};
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
        font-size: 2.2rem;
        font-weight: 800;
        margin-bottom: 1.5rem;
        position: relative;
        display: inline-block;
        letter-spacing: -0.5px;
    }
    
    .section-title::after {
        content: '';
        position: absolute;
        bottom: -10px;
        left: 0;
        width: 80px;
        height: 5px;
        background: ${greenTheme.colors.gradientPrimary};
        border-radius: 3px;
    }
    
    .order-summary-card {
        background: ${greenTheme.colors.white};
        border-radius: 20px;
        padding: 2rem;
        box-shadow: ${greenTheme.shadows.lg};
        border: 2px solid ${greenTheme.colors.primaryLight};
        position: sticky;
        top: 20px;
        animation: ${greenTheme.animations.slideUp};
    }
    
    .progress-bar {
        height: 8px;
        background: ${greenTheme.colors.gray200};
        border-radius: 4px;
        overflow: hidden;
        margin: 1rem 0;
    }
    
    .progress-fill {
        height: 100%;
        background: ${greenTheme.colors.gradientPrimary};
        border-radius: 4px;
        transition: width 0.3s ease;
    }
    
    .empty-state {
        text-align: center;
        padding: 4rem 2rem;
        animation: ${greenTheme.animations.fadeIn};
    }
    
    .empty-state-icon {
        font-size: 5rem;
        color: ${greenTheme.colors.gray300};
        margin-bottom: 1.5rem;
        animation: ${greenTheme.animations.bounceIn};
    }
    
    .payment-method-card {
        padding: 1.5rem;
        border-radius: 16px;
        border: 2px solid ${greenTheme.colors.gray200};
        cursor: pointer;
        transition: all 0.3s ease;
        background: ${greenTheme.colors.white};
    }
    
    .payment-method-card:hover {
        border-color: ${greenTheme.colors.primary};
        transform: translateY(-2px);
    }
    
    .payment-method-card.selected {
        border-color: ${greenTheme.colors.primary};
        background: rgba(16, 185, 129, 0.05);
        box-shadow: ${greenTheme.shadows.glow};
    }
    
    .invoice-item {
        padding: 12px 0;
        border-bottom: 1px dashed ${greenTheme.colors.gray200};
    }
    
    .invoice-total {
        padding: 16px 0;
        border-top: 2px solid ${greenTheme.colors.primary};
        border-bottom: 2px solid ${greenTheme.colors.primary};
    }
    
    .green-text {
        color: ${greenTheme.colors.primary} !important;
    }
    
    .success-text {
        color: ${greenTheme.colors.success} !important;
    }
    
    .warning-text {
        color: ${greenTheme.colors.warning} !important;
    }
    
    body {
        color: ${greenTheme.colors.gray800};
    }
    
    h1, h2, h3, h4, h5, h6 {
        color: ${greenTheme.colors.gray900};
    }
    
    p {
        color: ${greenTheme.colors.gray700};
    }
    
    /* Flash Sale Animation */
    @keyframes flashPulse {
        0%, 100% { opacity: 1; }
        50% { opacity: 0.7; }
    }
    
    .flash-item {
        animation: flashPulse 2s infinite;
    }
`;

document.head.appendChild(style);

// ==================== GLOBAL VARIABLES ====================
let flashSales = []; // Make sure this is populated from your database

// ==================== UPDATED CART FUNCTIONS ====================
function showCart() {
    document.querySelectorAll('#mainContent > div').forEach(page => {
        page.style.display = 'none';
    });
    const cartPage = document.getElementById('cartPage');
    cartPage.style.display = 'block';
    
    const cartContent = document.getElementById('cartContent');
    
    cartContent.innerHTML = `
        <div class="section">
            <div class="section-header" style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 2rem;">
                <div>
                    <h2 class="section-title" style="color: var(--pakistan-green);">🛒 Shopping Cart</h2>
                    <p style="color: var(--text-secondary); margin-top: 0.5rem;">
                        Review your items and proceed to checkout
                    </p>
                </div>
                <div style="background: var(--pakistan-green); color: white; padding: 8px 16px; border-radius: 50px; font-weight: 600;">
                    <i class="fas fa-shopping-cart"></i>
                    ${cartItems.reduce((sum, item) => sum + item.quantity, 0)} items
                </div>
            </div>
            
            ${cartItems.length === 0 ? `
                <div style="text-align: center; padding: 4rem; background: var(--white); border-radius: var(--radius-lg); box-shadow: var(--shadow); border: 2px dashed var(--border);">
                    <div style="font-size: 4rem; color: var(--text-secondary); opacity: 0.5; margin-bottom: 1rem;">
                        <i class="fas fa-shopping-bag"></i>
                    </div>
                    <h3 style="color: var(--text-primary); margin-bottom: 1rem; font-size: 1.8rem;">Your Cart is Empty</h3>
                    <p style="color: var(--text-secondary); max-width: 400px; margin: 0 auto 2rem; line-height: 1.6;">
                        Discover amazing products and add them to your cart to get started!
                    </p>
                    <button class="btn btn-primary" onclick="showHomePage()" style="padding: 12px 30px; border-radius: 50px;">
                        <i class="fas fa-bolt"></i> Start Shopping Now
                    </button>
                </div>
            ` : `
                <div style="display: grid; grid-template-columns: 2fr 1fr; gap: 2rem;">
                    <!-- Cart Items -->
                    <div>
                        <div style="background: var(--white); border-radius: var(--radius-lg); box-shadow: var(--shadow); border: 1px solid var(--border);">
                            <div style="padding: 1.5rem; border-bottom: 1px solid var(--border); background: rgba(1, 65, 28, 0.05);">
                                <div style="display: flex; justify-content: space-between; align-items: center;">
                                    <h3 style="color: var(--pakistan-dark-green); margin-bottom: 0;">
                                        <i class="fas fa-shopping-cart"></i> Your Cart Items
                                    </h3>
                                    <div style="display: flex; align-items: center; gap: 12px;">
                                        <span style="color: var(--pakistan-dark-green); font-weight: 600;">
                                            Total ${cartItems.length} ${cartItems.length === 1 ? 'item' : 'items'}
                                        </span>
                                        <button class="btn btn-secondary" onclick="clearCart()" style="padding: 8px 16px; border-radius: 50px;">
                                            <i class="fas fa-trash-alt"></i> Clear All
                                        </button>
                                    </div>
                                </div>
                            </div>
                            
                            <div style="max-height: 500px; overflow-y: auto; padding: 0;">
                                ${cartItems.map((item, index) => {
                                    // Check for active flash sale
                                    const flashSale = flashSales?.find(s => 
                                        s.productId === item.id && 
                                        s.status === 'active' && 
                                        new Date(s.endDate) > new Date()
                                    );
                                    
                                    const isFlashSale = !!flashSale;
                                    const finalPrice = isFlashSale ? (flashSale.flashPrice || item.price) : item.price;
                                    const originalPrice = item.price;
                                    const discountAmount = originalPrice - finalPrice;
                                    const totalDiscount = discountAmount * item.quantity;
                                    
                                    return `
                                        <div style="display: flex; gap: 1.5rem; padding: 1.5rem; border-bottom: 1px solid var(--border); 
                                             background: ${isFlashSale ? 'rgba(243, 156, 18, 0.05)' : 'transparent'};
                                             position: relative;">
                                            
                                            ${isFlashSale ? `
                                                <div style="position: absolute; top: 10px; left: 10px; background: var(--warning); color: white; padding: 3px 10px; border-radius: 4px; font-size: 0.7rem; font-weight: 600; z-index: 2;">
                                                    <i class="fas fa-bolt"></i> FLASH SALE
                                                </div>
                                            ` : ''}
                                            
                                            <div onclick="viewProductDetails('${item.id}')" style="cursor: pointer; flex-shrink: 0;">
                                                <img src="${item.image || 'https://via.placeholder.com/150'}" 
                                                     style="width: 120px; height: 120px; object-fit: cover; border-radius: 12px; border: 1px solid var(--border);"
                                                     alt="${escapeHtml(item.name)}">
                                            </div>
                                            
                                            <div style="flex: 1; min-width: 0;">
                                                <div style="display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 0.5rem;">
                                                    <div style="flex: 1; min-width: 0;">
                                                        <h4 onclick="viewProductDetails('${item.id}')" 
                                                            style="color: var(--text-primary); margin-bottom: 0.25rem; cursor: pointer; line-height: 1.4;">
                                                            ${escapeHtml(item.name)}
                                                        </h4>
                                                        <div style="display: flex; align-items: center; gap: 12px; margin-bottom: 0.5rem; flex-wrap: wrap;">
                                                            <span style="color: var(--text-secondary); font-size: 0.9rem;">
                                                                <i class="fas fa-store" style="color: var(--pakistan-green);"></i> 
                                                                ${escapeHtml(item.sellerName || 'Unknown Seller')}
                                                            </span>
                                                            <span style="color: var(--text-secondary); font-size: 0.9rem;">
                                                                <i class="fas fa-tag" style="color: var(--pakistan-green);"></i> 
                                                                ${item.category || 'General'}
                                                            </span>
                                                        </div>
                                                    </div>
                                                    <button onclick="removeFromCart(${index})" 
                                                            style="background: none; border: none; color: var(--error); cursor: pointer; font-size: 1.2rem; padding: 5px;">
                                                        <i class="fas fa-trash"></i>
                                                    </button>
                                                </div>
                                                
                                                <!-- Price Information -->
                                                <div style="display: flex; flex-wrap: wrap; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                                                    <div style="display: flex; align-items: baseline; gap: 0.5rem;">
                                                        <span style="font-size: 1.4rem; font-weight: 700; color: var(--pakistan-green);">
                                                            Rs. ${(finalPrice * item.quantity).toLocaleString()}
                                                        </span>
                                                        ${discountAmount > 0 ? `
                                                            <span style="text-decoration: line-through; color: var(--text-secondary); font-size: 1rem;">
                                                                Rs. ${(originalPrice * item.quantity).toLocaleString()}
                                                            </span>
                                                            <span style="background: var(--success); color: white; padding: 2px 8px; border-radius: 4px; font-size: 0.8rem; font-weight: 600;">
                                                                <i class="fas fa-sack-dollar"></i> Save Rs. ${totalDiscount.toLocaleString()}
                                                            </span>
                                                        ` : ''}
                                                    </div>
                                                    <div style="margin-left: auto;">
                                                        <span style="font-size: 0.9rem; color: var(--text-secondary);">
                                                            Rs. ${finalPrice.toLocaleString()} each
                                                        </span>
                                                    </div>
                                                </div>
                                                
                                                <!-- Quantity Controls -->
                                                <div style="display: flex; justify-content: space-between; align-items: center;">
                                                    <div style="display: flex; align-items: center; gap: 0.5rem; background: var(--accent); padding: 5px 15px; border-radius: 50px;">
                                                        <button onclick="updateCartQuantity(${index}, ${item.quantity - 1})" 
                                                                ${item.quantity <= 1 ? 'disabled' : ''}
                                                                style="width: 30px; height: 30px; border-radius: 50%; border: 1px solid var(--border); 
                                                                       background: white; color: var(--pakistan-green); cursor: pointer; 
                                                                       display: flex; align-items: center; justify-content: center;">
                                                            <i class="fas fa-minus"></i>
                                                        </button>
                                                        <span style="font-weight: 700; min-width: 40px; text-align: center; color: var(--text-primary); font-size: 16px;">
                                                            ${item.quantity}
                                                        </span>
                                                        <button onclick="updateCartQuantity(${index}, ${item.quantity + 1})"
                                                                style="width: 30px; height: 30px; border-radius: 50%; border: 1px solid var(--border); 
                                                                       background: white; color: var(--pakistan-green); cursor: pointer; 
                                                                       display: flex; align-items: center; justify-content: center;">
                                                            <i class="fas fa-plus"></i>
                                                        </button>
                                                    </div>
                                                    
                                                    ${isFlashSale ? `
                                                        <div style="background: rgba(243, 156, 18, 0.1); padding: 8px 16px; border-radius: 20px; border: 1px solid var(--warning);">
                                                            <span style="color: var(--warning); font-weight: 700; font-size: 0.9rem; display: flex; align-items: center; gap: 6px;">
                                                                <i class="fas fa-bolt"></i>
                                                                Flash Sale Active!
                                                            </span>
                                                        </div>
                                                    ` : ''}
                                                </div>
                                            </div>
                                        </div>
                                    `;
                                }).join('')}
                            </div>
                        </div>
                    </div>
                    
                    <!-- Order Summary -->
                    <div>
                        ${generateCartOrderSummary()}
                    </div>
                </div>
            `}
        </div>
    `;
}

function generateCartOrderSummary() {
    // Group cart items by seller for shipping calculation
    const itemsBySeller = {};
    cartItems.forEach(item => {
        const sellerId = item.sellerId || 'default';
        if (!itemsBySeller[sellerId]) {
            itemsBySeller[sellerId] = {
                sellerId: sellerId,
                sellerName: item.sellerName || 'Unknown Seller',
                items: [],
                subtotal: 0
            };
        }
        itemsBySeller[sellerId].items.push(item);
        
        // Calculate item price with flash sale discount
        const flashSale = flashSales?.find(s => 
            s.productId === item.id && 
            s.status === 'active' && 
            new Date(s.endDate) > new Date()
        );
        
        let itemPrice = item.price;
        if (flashSale) {
            itemPrice = flashSale.flashPrice || item.price;
        }
        
        itemsBySeller[sellerId].subtotal += itemPrice * item.quantity;
    });
    
    // Calculate totals
    let subtotal = 0;
    let totalDiscount = 0;
    let shippingFee = 0;
    
    cartItems.forEach(item => {
        const flashSale = flashSales?.find(s => 
            s.productId === item.id && 
            s.status === 'active' && 
            new Date(s.endDate) > new Date()
        );
        
        if (flashSale) {
            const flashPrice = flashSale.flashPrice || item.price;
            const discount = (item.price - flashPrice) * item.quantity;
            totalDiscount += discount;
            subtotal += flashPrice * item.quantity;
        } else {
            subtotal += item.price * item.quantity;
        }
    });
    
    // Shipping fee: 230 per seller with items
    const sellerCount = Object.keys(itemsBySeller).length;
    shippingFee = sellerCount * 230;
    
    const tax = subtotal * 0.05;
    const total = subtotal + shippingFee + tax;
    const originalSubtotal = subtotal + totalDiscount;
    
    return `
        <div style="background: var(--white); border-radius: var(--radius-lg); padding: 1.5rem; box-shadow: var(--shadow); border: 2px solid var(--pakistan-green); position: sticky; top: 20px;">
            <h3 style="color: var(--pakistan-green); margin-bottom: 1.5rem; display: flex; align-items: center; gap: 10px; border-bottom: 2px solid var(--pakistan-green); padding-bottom: 1rem;">
                <i class="fas fa-receipt"></i>
                Order Summary
            </h3>
            
            <div style="margin-bottom: 1.5rem;">
                <!-- Seller Breakdown -->
                ${Object.entries(itemsBySeller).map(([sellerId, sellerData]) => `
                    <div style="margin-bottom: 1rem; padding: 1rem; background: rgba(1, 65, 28, 0.05); border-radius: 8px; border: 1px solid rgba(1, 65, 28, 0.1);">
                        <div style="font-weight: 600; color: var(--pakistan-green); margin-bottom: 0.5rem; display: flex; align-items: center; gap: 8px;">
                            <i class="fas fa-store"></i>
                            ${escapeHtml(sellerData.sellerName)}
                        </div>
                        <div style="display: flex; justify-content: space-between; font-size: 0.9rem; color: var(--text-secondary);">
                            <span>${sellerData.items.length} item(s)</span>
                            <span>Shipping: Rs. 230</span>
                        </div>
                    </div>
                `).join('')}
                
                <!-- Price Breakdown -->
                <div style="margin-top: 1.5rem;">
                    <div style="display: flex; justify-content: space-between; margin-bottom: 0.75rem; color: var(--text-primary);">
                        <span>Subtotal:</span>
                        <span>Rs. ${originalSubtotal.toLocaleString()}</span>
                    </div>
                    
                    ${totalDiscount > 0 ? `
                        <div style="display: flex; justify-content: space-between; margin-bottom: 0.75rem; color: var(--success);">
                            <span><i class="fas fa-bolt"></i> Discount:</span>
                            <span>- Rs. ${totalDiscount.toLocaleString()}</span>
                        </div>
                    ` : ''}
                    
                    <div style="display: flex; justify-content: space-between; margin-bottom: 0.75rem; color: var(--text-primary);">
                        <span>Shipping (${sellerCount} seller${sellerCount > 1 ? 's' : ''}):</span>
                        <span>Rs. ${shippingFee.toLocaleString()}</span>
                    </div>
                    
                    <div style="display: flex; justify-content: space-between; margin-bottom: 0.75rem; color: var(--text-primary);">
                        <span>Tax (5%):</span>
                        <span>Rs. ${tax.toFixed(2)}</span>
                    </div>
                    
                    <div style="height: 2px; background: linear-gradient(to right, var(--pakistan-green), var(--pakistan-light-green)); margin: 1.5rem 0; border-radius: 2px;"></div>
                    
                    <div style="display: flex; justify-content: space-between; font-size: 1.5rem; font-weight: 800; color: var(--pakistan-green);">
                        <span>Total Amount:</span>
                        <span>Rs. ${total.toFixed(2)}</span>
                    </div>
                    
                    ${totalDiscount > 0 ? `
                        <div style="text-align: right; margin-top: 0.5rem;">
                            <span style="color: var(--success); font-weight: 600; font-size: 0.9rem;">
                                <i class="fas fa-check-circle"></i> You saved Rs. ${totalDiscount.toLocaleString()}!
                            </span>
                        </div>
                    ` : ''}
                </div>
            </div>
            
            <button class="btn btn-primary" style="width: 100%; padding: 14px; border-radius: 50px; margin-bottom: 1rem;"
                    onclick="proceedToCheckout()" ${!currentUser ? 'disabled' : ''}>
                <i class="fas fa-lock"></i> Proceed to Secure Checkout
            </button>
            
            ${!currentUser ? `
                <div style="text-align: center;">
                    <button class="btn btn-secondary" style="width: 100%; padding: 12px; border-radius: 50px;"
                            onclick="openAuthModal('buyerLogin')">
                        <i class="fas fa-sign-in-alt"></i> Login to Checkout
                    </button>
                </div>
            ` : ''}
            
            <div style="display: flex; align-items: center; gap: 10px; margin-top: 1.5rem; padding-top: 1.5rem; border-top: 1px solid var(--border);">
                <i class="fas fa-shield-alt" style="color: var(--pakistan-green); font-size: 1.2rem;"></i>
                <span style="color: var(--text-secondary); font-size: 14px; line-height: 1.4;">
                    <strong>Secure Checkout:</strong> Your payment information is encrypted with 256-bit SSL security
                </span>
            </div>
        </div>
    `;
}

// ==================== FIXED CART FUNCTIONS ====================
function clearCart() {
    if (cartItems.length === 0) {
        showToast('Cart is already empty', 'info');
        return;
    }
    
    if (confirm('Are you sure you want to clear your entire cart? This action cannot be undone.')) {
        cartItems = [];
        localStorage.setItem('cartItems', JSON.stringify(cartItems));
        updateCartCount();
        showCart(); // Refresh cart view
        showToast('Cart cleared successfully', 'success');
    }
}

function removeFromCart(index) {
    if (index >= 0 && index < cartItems.length) {
        const removedItem = cartItems[index];
        cartItems.splice(index, 1);
        localStorage.setItem('cartItems', JSON.stringify(cartItems));
        updateCartCount();
        showCart(); // Refresh cart view
        showToast(`"${removedItem.name}" removed from cart`, 'info');
    }
}

function updateCartQuantity(index, newQuantity) {
    if (newQuantity < 1) {
        removeFromCart(index);
        return;
    }
    
    if (index >= 0 && index < cartItems.length) {
        cartItems[index].quantity = newQuantity;
        localStorage.setItem('cartItems', JSON.stringify(cartItems));
        updateCartCount();
        showCart(); // Refresh cart view
    }
}

function updateCartCount() {
    const count = cartItems.reduce((sum, item) => sum + item.quantity, 0);
    cartCount.textContent = count;
    cartCount.style.display = count > 0 ? 'flex' : 'none';
}

// ==================== CHECKOUT FUNCTIONS ====================
function proceedToCheckout() {
    if (!currentUser) {
        showToast('Please login to checkout', 'error');
        openAuthModal('buyerLogin');
        return;
    }
    
    if (cartItems.length === 0) {
        showToast('Your cart is empty', 'error');
        return;
    }
    
    document.querySelectorAll('#mainContent > div').forEach(page => page.style.display = 'none');
    document.getElementById('checkoutPage').style.display = 'block';
    
    const checkoutContent = document.getElementById('checkoutContent');
    checkoutContent.innerHTML = generateCheckoutHTML();
}

function generateCheckoutHTML() {
    // Calculate totals
    let subtotal = 0;
    let totalDiscount = 0;
    const itemsBySeller = {};
    
    cartItems.forEach(item => {
        const sellerId = item.sellerId || 'default';
        if (!itemsBySeller[sellerId]) {
            itemsBySeller[sellerId] = {
                sellerId: sellerId,
                sellerName: item.sellerName || 'Unknown Seller',
                items: [],
                subtotal: 0
            };
        }
        
        const flashSale = flashSales?.find(s => 
            s.productId === item.id && 
            s.status === 'active' && 
            new Date(s.endDate) > new Date()
        );
        
        let finalPrice = item.price;
        let discount = 0;
        
        if (flashSale) {
            finalPrice = flashSale.flashPrice || item.price;
            discount = (item.price - finalPrice) * item.quantity;
            totalDiscount += discount;
        }
        
        subtotal += finalPrice * item.quantity;
        itemsBySeller[sellerId].subtotal += finalPrice * item.quantity;
        itemsBySeller[sellerId].items.push({
            ...item,
            finalPrice: finalPrice,
            discount: discount
        });
    });
    
    const sellerCount = Object.keys(itemsBySeller).length;
    const shippingFee = sellerCount * 230;
    const tax = subtotal * 0.05;
    const total = subtotal + shippingFee + tax;
    const originalSubtotal = subtotal + totalDiscount;
    
    return `
        <div class="section">
            <!-- Checkout Header -->
            <div class="section-header" style="margin-bottom: 2rem;">
                <div>
                    <h2 class="section-title" style="color: var(--pakistan-green);">✅ Secure Checkout</h2>
                    <p style="color: var(--text-secondary); margin-top: 0.5rem;">
                        Complete your purchase in 3 simple steps
                    </p>
                </div>
                <button class="btn btn-secondary" onclick="showCart()">
                    <i class="fas fa-arrow-left"></i> Back to Cart
                </button>
            </div>
            
            <!-- Progress Steps -->
            <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; margin-bottom: 3rem; max-width: 600px; margin-left: auto; margin-right: auto;">
                <div style="text-align: center;">
                    <div style="width: 48px; height: 48px; border-radius: 50%; background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-light-green)); color: white; display: flex; align-items: center; justify-content: center; margin: 0 auto 0.5rem; font-weight: bold; font-size: 1.2rem; box-shadow: var(--shadow);">
                        1
                    </div>
                    <span style="color: var(--pakistan-green); font-weight: 700;">Shipping</span>
                </div>
                <div style="text-align: center;">
                    <div style="width: 48px; height: 48px; border-radius: 50%; background: var(--border); color: var(--text-secondary); display: flex; align-items: center; justify-content: center; margin: 0 auto 0.5rem; font-weight: bold; font-size: 1.2rem;">
                        2
                    </div>
                    <span style="color: var(--text-secondary);">Payment</span>
                </div>
                <div style="text-align: center;">
                    <div style="width: 48px; height: 48px; border-radius: 50%; background: var(--border); color: var(--text-secondary); display: flex; align-items: center; justify-content: center; margin: 0 auto 0.5rem; font-weight: bold; font-size: 1.2rem;">
                        3
                    </div>
                    <span style="color: var(--text-secondary);">Confirmation</span>
                </div>
            </div>
            
            <!-- Main Content -->
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem;">
                <!-- Left Column -->
                <div>
                    <!-- Shipping Address -->
                    <div class="glass-card" style="margin-bottom: 1.5rem;">
                        <div style="padding: 1.5rem; border-bottom: 1px solid var(--border); background: rgba(1, 65, 28, 0.05); border-radius: var(--radius) var(--radius) 0 0;">
                            <h3 style="color: var(--pakistan-dark-green); margin-bottom: 0.5rem; display: flex; align-items: center; gap: 10px;">
                                <i class="fas fa-map-marker-alt"></i>
                                Shipping Address
                            </h3>
                            <p style="color: var(--text-secondary); font-size: 14px;">
                                Where should we deliver your order?
                            </p>
                        </div>
                        <div style="padding: 1.5rem;">
                            <form id="checkoutAddressForm">
                                <div class="form-group">
                                    <label style="color: var(--text-primary); font-weight: 600; margin-bottom: 8px; display: block;">
                                        Full Name *
                                    </label>
                                    <input type="text" id="shippingName" class="form-control" 
                                           value="${escapeHtml(currentUserProfile?.displayName || '')}" 
                                           required>
                                </div>
                                <div class="form-group" style="margin-top: 1rem;">
                                    <label style="color: var(--text-primary); font-weight: 600; margin-bottom: 8px; display: block;">
                                        Phone Number *
                                    </label>
                                    <input type="tel" id="shippingPhone" class="form-control" 
                                           value="${escapeHtml(currentUserProfile?.phone || '')}" 
                                           required>
                                </div>
                                <div class="form-group" style="margin-top: 1rem;">
                                    <label style="color: var(--text-primary); font-weight: 600; margin-bottom: 8px; display: block;">
                                        Address *
                                    </label>
                                    <textarea id="shippingAddress" class="form-control" rows="3" required>${escapeHtml(currentUserProfile?.address || '')}</textarea>
                                </div>
                                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-top: 1rem;">
                                    <div class="form-group">
                                        <label style="color: var(--text-primary); font-weight: 600; margin-bottom: 8px; display: block;">
                                            City *
                                        </label>
                                        <input type="text" id="shippingCity" class="form-control" 
                                               value="${escapeHtml(currentUserProfile?.city || '')}" 
                                               required>
                                    </div>
                                    <div class="form-group">
                                        <label style="color: var(--text-primary); font-weight: 600; margin-bottom: 8px; display: block;">
                                            Postal Code *
                                        </label>
                                        <input type="text" id="shippingPostalCode" class="form-control" 
                                               required placeholder="Required for delivery">
                                    </div>
                                </div>
                            </form>
                        </div>
                    </div>
                    
                    <!-- Payment Method -->
                    <div class="glass-card">
                        <div style="padding: 1.5rem; border-bottom: 1px solid var(--border); background: rgba(1, 65, 28, 0.05); border-radius: var(--radius) var(--radius) 0 0;">
                            <h3 style="color: var(--pakistan-dark-green); margin-bottom: 0.5rem; display: flex; align-items: center; gap: 10px;">
                                <i class="fas fa-credit-card"></i>
                                Payment Method
                            </h3>
                            <p style="color: var(--text-secondary); font-size: 14px;">
                                Choose your preferred payment method
                            </p>
                        </div>
                        <div style="padding: 1.5rem;">
                            <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; margin-bottom: 1.5rem;">
                                <div class="payment-method-card ${selectedPaymentMethod === 'cod' ? 'selected' : ''}" 
                                     onclick="selectPaymentMethod('cod')">
                                    <div style="text-align: center;">
                                        <div style="width: 56px; height: 56px; background: var(--accent); border-radius: 12px; display: flex; align-items: center; justify-content: center; margin: 0 auto 10px;">
                                            <i class="fas fa-money-bill-wave" style="font-size: 1.8rem; color: var(--pakistan-green);"></i>
                                        </div>
                                        <span style="font-weight: 700; color: var(--text-primary); font-size: 15px;">Cash on Delivery</span>
                                    </div>
                                </div>
                                <div class="payment-method-card ${selectedPaymentMethod === 'easypaisa' ? 'selected' : ''}" 
                                     onclick="selectPaymentMethod('easypaisa')">
                                    <div style="text-align: center;">
                                        <div style="width: 56px; height: 56px; background: var(--accent); border-radius: 12px; display: flex; align-items: center; justify-content: center; margin: 0 auto 10px;">
                                            <i class="fas fa-mobile-alt" style="font-size: 1.8rem; color: var(--pakistan-green);"></i>
                                        </div>
                                        <span style="font-weight: 700; color: var(--text-primary); font-size: 15px;">EasyPaisa</span>
                                    </div>
                                </div>
                                <div class="payment-method-card ${selectedPaymentMethod === 'jazzcash' ? 'selected' : ''}" 
                                     onclick="selectPaymentMethod('jazzcash')">
                                    <div style="text-align: center;">
                                        <div style="width: 56px; height: 56px; background: var(--accent); border-radius: 12px; display: flex; align-items: center; justify-content: center; margin: 0 auto 10px;">
                                            <i class="fas fa-wallet" style="font-size: 1.8rem; color: var(--pakistan-green);"></i>
                                        </div>
                                        <span style="font-weight: 700; color: var(--text-primary); font-size: 15px;">JazzCash</span>
                                    </div>
                                </div>
                            </div>
                            
                            ${selectedPaymentMethod !== 'cod' ? `
                                <div id="paymentDetails" style="margin-top: 1.5rem; padding: 1.5rem; border-radius: var(--radius); background: rgba(1, 65, 28, 0.05); border: 2px dashed var(--pakistan-green);">
                                    <h4 style="color: var(--pakistan-dark-green); margin-bottom: 1rem; display: flex; align-items: center; gap: 10px; font-size: 1.2rem;">
                                        <i class="fas fa-info-circle"></i> Online Payment Instructions
                                    </h4>
                                    
                                    <div style="background: var(--white); padding: 1.2rem; border-radius: 10px; margin-bottom: 1rem; border: 1px solid var(--border); box-shadow: var(--shadow);">
                                        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px;">
                                            <span style="color: var(--text-secondary); font-weight: 600;">Account Number:</span>
                                            <span style="font-weight: 800; color: var(--pakistan-dark-green); font-size: 16px;">0332-2087563</span>
                                        </div>
                                        <div style="display: flex; justify-content: space-between; align-items: center;">
                                            <span style="color: var(--text-secondary); font-weight: 600;">Account Name:</span>
                                            <span style="font-weight: 800; color: var(--text-primary); font-size: 16px;">Muhammad Sadique</span>
                                        </div>
                                    </div>
                                    
                                    <div style="background: rgba(231, 76, 60, 0.1); padding: 1rem; border-radius: 10px; margin-bottom: 1.5rem; border: 1px solid rgba(231, 76, 60, 0.3);">
                                        <p style="color: var(--error); margin: 0; font-size: 14px; display: flex; align-items: flex-start; gap: 8px;">
                                            <i class="fas fa-exclamation-triangle" style="margin-top: 2px;"></i>
                                            <span><strong>Important:</strong> Transfer the exact total amount <strong>Rs. ${total.toFixed(2)}</strong> first, then enter the Transaction ID below.</span>
                                        </p>
                                    </div>
                                    
                                    <div class="form-group">
                                        <label style="color: var(--text-primary); font-weight: 600; margin-bottom: 8px; display: block;">
                                            Transaction ID *
                                        </label>
                                        <input type="text" id="onlineTransactionId" class="form-control" 
                                               placeholder="Enter 11-digit Transaction ID" required>
                                    </div>
                                    
                                    <div class="form-group" style="margin-top: 1rem;">
                                        <label style="color: var(--text-primary); font-weight: 600; margin-bottom: 8px; display: block;">
                                            Payment Proof (Screenshot)
                                        </label>
                                        <div style="border: 2px dashed var(--border); border-radius: var(--radius); padding: 2rem; text-align: center; cursor: pointer; background: var(--white);" 
                                             onclick="document.getElementById('paymentProofImage').click()">
                                            <i class="fas fa-cloud-upload-alt" style="font-size: 2.5rem; color: var(--text-secondary); margin-bottom: 10px;"></i>
                                            <p style="color: var(--text-primary); margin-bottom: 5px; font-weight: 600;">Click to upload payment screenshot</p>
                                            <p style="color: var(--text-secondary); font-size: 13px;">PNG, JPG, or JPEG (Max 5MB)</p>
                                        </div>
                                        <input type="file" id="paymentProofImage" accept="image/*" class="form-control" style="display: none;" onchange="handlePaymentProofUpload(event)">
                                        <div id="paymentProofPreview" style="margin-top: 1rem;"></div>
                                    </div>
                                </div>
                            ` : ''}
                        </div>
                    </div>
                </div>
                
                <!-- Right Column - Order Summary -->
                <div>
                    <div style="background: var(--white); border-radius: var(--radius-lg); padding: 1.5rem; box-shadow: var(--shadow); border: 2px solid var(--pakistan-green); position: sticky; top: 20px;">
                        <h3 style="color: var(--pakistan-green); margin-bottom: 1.5rem; display: flex; align-items: center; gap: 10px; border-bottom: 2px solid var(--pakistan-green); padding-bottom: 1rem;">
                            <i class="fas fa-file-invoice-dollar"></i>
                            Invoice Summary
                        </h3>
                        
                        <!-- Cart Items Preview -->
                        <div style="max-height: 250px; overflow-y: auto; margin-bottom: 1.5rem; padding-right: 8px;">
                            ${cartItems.map((item, index) => {
                                const flashSale = flashSales?.find(s => 
                                    s.productId === item.id && 
                                    s.status === 'active' && 
                                    new Date(s.endDate) > new Date()
                                );
                                const isFlashSale = !!flashSale;
                                const finalPrice = isFlashSale ? (flashSale.flashPrice || item.price) : item.price;
                                
                                return `
                                    <div style="display: flex; gap: 1rem; padding: 12px; border-bottom: 1px dashed var(--border); align-items: center; background: ${isFlashSale ? 'rgba(243, 156, 18, 0.05)' : 'transparent'}; border-radius: 8px; margin-bottom: 6px;">
                                        <img src="${item.image || 'https://via.placeholder.com/150'}" 
                                             style="width: 60px; height: 60px; object-fit: cover; border-radius: 8px; border: 1px solid var(--border);"
                                             alt="${escapeHtml(item.name)}">
                                        <div style="flex: 1; min-width: 0;">
                                            <p style="font-weight: 600; color: var(--text-primary); margin-bottom: 4px; font-size: 14px; line-height: 1.4;">
                                                ${escapeHtml(item.name).substring(0, 50)}${escapeHtml(item.name).length > 50 ? '...' : ''}
                                            </p>
                                            <div style="display: flex; justify-content: space-between; align-items: center;">
                                                <span style="color: var(--text-secondary); font-size: 13px;">
                                                    Qty: ${item.quantity} × Rs. ${finalPrice.toLocaleString()}
                                                </span>
                                                ${isFlashSale ? `
                                                    <span style="background: var(--warning); color: white; padding: 2px 8px; border-radius: 10px; font-size: 11px; font-weight: 600;">
                                                        ⚡ FLASH
                                                    </span>
                                                ` : ''}
                                            </div>
                                        </div>
                                    </div>
                                `;
                            }).join('')}
                        </div>
                        
                        <!-- Invoice Breakdown -->
                        <div style="margin-bottom: 1.5rem;">
                            <!-- Original Subtotal -->
                            <div style="display: flex; justify-content: space-between; margin-bottom: 0.75rem; color: var(--text-primary); padding: 0.75rem; background: var(--accent); border-radius: 8px;">
                                <span style="font-weight: 600;">Original Subtotal</span>
                                <span style="font-weight: 700;">Rs. ${originalSubtotal.toLocaleString()}</span>
                            </div>
                            
                            <!-- Flash Sale Discount -->
                            ${totalDiscount > 0 ? `
                                <div style="display: flex; justify-content: space-between; margin-bottom: 0.75rem; color: var(--success); padding: 0.75rem; background: rgba(39, 174, 96, 0.1); border-radius: 8px; border-left: 4px solid var(--success);">
                                    <span style="font-weight: 700; display: flex; align-items: center; gap: 8px;">
                                        <i class="fas fa-bolt"></i>
                                        Flash Sale Discount
                                    </span>
                                    <span style="font-weight: 800; font-size: 16px;">
                                        - Rs. ${totalDiscount.toLocaleString()}
                                    </span>
                                </div>
                            ` : ''}
                            
                            <!-- Discounted Subtotal -->
                            <div style="display: flex; justify-content: space-between; margin-bottom: 0.75rem; color: var(--text-primary); padding: 0.75rem; background: var(--accent); border-radius: 8px;">
                                <span style="font-weight: 600;">Discounted Subtotal</span>
                                <span style="font-weight: 800; color: var(--pakistan-green);">
                                    Rs. ${subtotal.toLocaleString()}
                                </span>
                            </div>
                            
                            <!-- Shipping -->
                            <div style="display: flex; justify-content: space-between; margin-bottom: 0.75rem; color: var(--text-primary); padding: 0.75rem; background: var(--accent); border-radius: 8px;">
                                <span style="font-weight: 600;">Shipping (${sellerCount} seller${sellerCount > 1 ? 's' : ''})</span>
                                <span style="font-weight: 700;">Rs. ${shippingFee.toLocaleString()}</span>
                            </div>
                            
                            <!-- Tax -->
                            <div style="display: flex; justify-content: space-between; margin-bottom: 0.75rem; color: var(--text-primary); padding: 0.75rem; background: var(--accent); border-radius: 8px;">
                                <span style="font-weight: 600;">Tax (5%)</span>
                                <span style="font-weight: 700;">Rs. ${tax.toFixed(2)}</span>
                            </div>
                            
                            <div style="height: 2px; background: linear-gradient(to right, var(--pakistan-green), var(--pakistan-light-green)); margin: 1.5rem 0; border-radius: 2px;"></div>
                            
                            <!-- Grand Total -->
                            <div style="background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-light-green)); color: white; padding: 1.5rem; border-radius: var(--radius); margin-top: 1rem;">
                                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px;">
                                    <span style="font-size: 1.4rem; font-weight: 900;">Total Amount</span>
                                    <span style="font-size: 2rem; font-weight: 900; text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);">
                                        Rs. ${total.toFixed(2)}
                                    </span>
                                </div>
                                ${totalDiscount > 0 ? `
                                    <div style="display: flex; justify-content: space-between; align-items: center;">
                                        <span style="font-weight: 700; font-size: 14px; display: flex; align-items: center; gap: 6px;">
                                            <i class="fas fa-sack-dollar"></i>
                                            Total Savings: Rs. ${totalDiscount.toLocaleString()}
                                        </span>
                                    </div>
                                ` : ''}
                            </div>
                        </div>
                        
                        <button class="btn btn-primary" style="width: 100%; padding: 16px; font-size: 1.1rem; border-radius: 50px; margin-top: 1rem; background: linear-gradient(135deg, var(--pakistan-green), var(--pakistan-light-green)); border: none;" 
                                onclick="placeOrder()">
                            <i class="fas fa-check-circle"></i> Confirm & Place Order
                        </button>
                        
                        <div style="text-align: center; margin-top: 1.5rem; padding-top: 1.5rem; border-top: 1px solid var(--border);">
                            <p style="color: var(--text-secondary); font-size: 13px; line-height: 1.5;">
                                <i class="fas fa-lock" style="color: var(--pakistan-green);"></i>
                                Your order is secured. By placing your order, you agree to our 
                                <a href="#" style="color: var(--pakistan-green); text-decoration: underline;">Terms & Conditions</a>
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    `;
}

// ==================== PAYMENT METHOD SELECTION ====================
function selectPaymentMethod(method) {
    selectedPaymentMethod = method;
    
    // Update UI
    document.querySelectorAll('.payment-method-card').forEach(card => {
        card.classList.remove('selected');
    });
    
    const selectedCard = event?.currentTarget || document.querySelector(`[onclick="selectPaymentMethod('${method}')"]`);
    if (selectedCard) {
        selectedCard.classList.add('selected');
    }
    
    // Show/hide online payment details
    const paymentDetails = document.getElementById('paymentDetails');
    if (paymentDetails) {
        paymentDetails.style.display = method !== 'cod' ? 'block' : 'none';
    }
}

// ==================== ORDER PLACEMENT FUNCTION ====================
async function placeOrder() {
    if (!currentUser) {
        showToast('Please login to place order', 'error');
        openAuthModal('buyerLogin');
        return;
    }
    
    if (cartItems.length === 0) {
        showToast('Your cart is empty', 'error');
        return;
    }
    
    // Validate shipping address
    const shippingName = document.getElementById('shippingName')?.value;
    const shippingPhone = document.getElementById('shippingPhone')?.value;
    const shippingAddress = document.getElementById('shippingAddress')?.value;
    const shippingCity = document.getElementById('shippingCity')?.value;
    const shippingPostalCode = document.getElementById('shippingPostalCode')?.value;
    
    if (!shippingName || !shippingPhone || !shippingAddress || !shippingCity || !shippingPostalCode) {
        showToast('Please fill all shipping details', 'error');
        return;
    }
    
    // For online payments, validate transaction details
    if (selectedPaymentMethod !== 'cod') {
        const transactionId = document.getElementById('onlineTransactionId')?.value;
        if (!transactionId || transactionId.length < 6) {
            showToast('Please enter a valid transaction ID', 'error');
            return;
        }
        
        const paymentProofFile = document.getElementById('paymentProofImage')?.files[0];
        if (!paymentProofFile) {
            showToast('Please upload payment proof screenshot', 'error');
            return;
        }
    }
    
    // Show loading
    showToast('Processing your order...', 'info');
    const placeOrderBtn = document.querySelector('[onclick="placeOrder()"]');
    if (placeOrderBtn) {
        placeOrderBtn.disabled = true;
        placeOrderBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Processing...';
    }
    
    try {
        // Group items by seller
        const itemsBySeller = {};
        cartItems.forEach(item => {
            const sellerId = item.sellerId || 'default';
            if (!itemsBySeller[sellerId]) {
                itemsBySeller[sellerId] = {
                    sellerId: sellerId,
                    sellerName: item.sellerName || 'Unknown Seller',
                    items: [],
                    subtotal: 0
                };
            }
            
            const flashSale = flashSales?.find(s => 
                s.productId === item.id && 
                s.status === 'active' && 
                new Date(s.endDate) > new Date()
            );
            
            let finalPrice = item.price;
            let discount = 0;
            
            if (flashSale) {
                finalPrice = flashSale.flashPrice || item.price;
                discount = (item.price - finalPrice) * item.quantity;
            }
            
            itemsBySeller[sellerId].subtotal += finalPrice * item.quantity;
            itemsBySeller[sellerId].items.push({
                id: item.id,
                name: item.name,
                image: item.image,
                price: finalPrice,
                originalPrice: item.price,
                quantity: item.quantity,
                discount: discount
            });
        });
        
        const sellerCount = Object.keys(itemsBySeller).length;
        const shippingFee = sellerCount * 230;
        
        // Create orders for each seller
        const orderPromises = Object.entries(itemsBySeller).map(async ([sellerId, sellerData]) => {
            const orderId = 'ORD' + Date.now() + Math.random().toString(36).substr(2, 6).toUpperCase();
            const tax = sellerData.subtotal * 0.05;
            const total = sellerData.subtotal + 230 + tax;
            
            const orderData = {
                orderId: orderId,
                buyerId: currentUser.uid,
                buyerEmail: currentUser.email,
                buyerName: shippingName,
                buyerPhone: shippingPhone,
                buyerAddress: shippingAddress,
                buyerCity: shippingCity,
                buyerPostalCode: shippingPostalCode,
                sellerId: sellerId,
                sellerName: sellerData.sellerName,
                items: sellerData.items,
                subtotal: sellerData.subtotal,
                shippingFee: 230,
                tax: tax,
                total: total,
                paymentMethod: selectedPaymentMethod,
                paymentStatus: selectedPaymentMethod === 'cod' ? 'pending' : 'pending_verification',
                orderStatus: selectedPaymentMethod === 'cod' ? 'pending' : 'payment_pending',
                transactionId: selectedPaymentMethod !== 'cod' ? document.getElementById('onlineTransactionId')?.value : null,
                createdAt: new Date(),
                updatedAt: new Date()
            };
            
            // Save to Firebase
            await db.collection('orders').doc(orderId).set(orderData);
            
            // Send notification to seller (but seller can't see details until payment verified)
            await db.collection('notifications').add({
                userId: sellerId,
                title: selectedPaymentMethod === 'cod' ? 'New Order Received!' : 'New Order - Payment Pending',
                message: selectedPaymentMethod === 'cod' ? 
                    `You have received a new COD order ${orderId} for Rs. ${orderData.total.toFixed(2)}` :
                    `You have received a new order ${orderId}. Payment verification pending.`,
                type: 'order',
                read: false,
                createdAt: new Date()
            });
            
            return orderId;
        });
        
        // Wait for all orders to be created
        const orderIds = await Promise.all(orderPromises);
        
        // Send notification to buyer
        await db.collection('notifications').add({
            userId: currentUser.uid,
            title: 'Order Placed Successfully!',
            message: `Your order ${orderIds[0]} has been placed ${selectedPaymentMethod === 'cod' ? '' : 'and is awaiting payment verification'}`,
            type: 'order_confirmation',
            read: false,
            createdAt: new Date()
        });
        
        // Clear cart
        cartItems = [];
        localStorage.setItem('cartItems', JSON.stringify(cartItems));
        updateCartCount();
        
        // Show success message
        showToast(`Order placed successfully! Order ID: ${orderIds[0]}`, 'success');
        
        // Show order success modal
        document.getElementById('successOrderId').textContent = orderIds[0];
        openModal('orderSuccessModal');
        
        // Reset button
        if (placeOrderBtn) {
            placeOrderBtn.disabled = false;
            placeOrderBtn.innerHTML = '<i class="fas fa-check-circle"></i> Confirm & Place Order';
        }
        
    } catch (error) {
        console.error('Error placing order:', error);
        showToast('Failed to place order. Please try again.', 'error');
        
        // Reset button
        if (placeOrderBtn) {
            placeOrderBtn.disabled = false;
            placeOrderBtn.innerHTML = '<i class="fas fa-check-circle"></i> Confirm & Place Order';
        }
    }
}

// ==================== PAYMENT PROOF UPLOAD ====================
function handlePaymentProofUpload(event) {
    const file = event.target.files[0];
    const previewContainer = document.getElementById('paymentProofPreview');
    
    if (!file) return;
    
    if (!file.type.startsWith('image/')) {
        showToast('Please upload an image file', 'error');
        return;
    }
    
    if (file.size > 5 * 1024 * 1024) {
        showToast('File size should be less than 5MB', 'error');
        return;
    }
    
    const reader = new FileReader();
    reader.onload = function(e) {
        previewContainer.innerHTML = `
            <div style="position: relative; width: 150px; height: 150px; border-radius: var(--radius); overflow: hidden; border: 2px solid var(--pakistan-green);">
                <img src="${e.target.result}" style="width: 100%; height: 100%; object-fit: cover;">
                <button type="button" onclick="removePaymentProof()" style="position: absolute; top: 5px; right: 5px; background: var(--error); color: white; border: none; border-radius: 50%; width: 24px; height: 24px; display: flex; align-items: center; justify-content: center; cursor: pointer;">
                    <i class="fas fa-times"></i>
                </button>
            </div>
        `;
    };
    reader.readAsDataURL(file);
}

function removePaymentProof() {
    document.getElementById('paymentProofImage').value = '';
    document.getElementById('paymentProofPreview').innerHTML = '';
}

// ==================== ADMIN PAYMENT VERIFICATION ====================
// This function should be called from admin panel
async function verifyPayment(orderId, status) {
    try {
        const orderRef = db.collection('orders').doc(orderId);
        const orderDoc = await orderRef.get();
        
        if (!orderDoc.exists) {
            showToast('Order not found', 'error');
            return;
        }
        
        const orderData = orderDoc.data();
        
        if (status === 'approved') {
            // Update order status
            await orderRef.update({
                paymentStatus: 'completed',
                orderStatus: 'confirmed',
                verifiedBy: 'admin',
                verifiedAt: new Date(),
                updatedAt: new Date()
            });
            
            // Send notification to seller (now seller can see order details)
            await db.collection('notifications').add({
                userId: orderData.sellerId,
                title: 'Payment Verified - Process Order!',
                message: `Payment for order ${orderId} has been verified. You can now process the order. Amount: Rs. ${orderData.total.toFixed(2)}`,
                type: 'payment_verified',
                read: false,
                createdAt: new Date()
            });
            
            // Send notification to buyer
            await db.collection('notifications').add({
                userId: orderData.buyerId,
                title: 'Payment Verified!',
                message: `Your payment for order ${orderId} has been verified. Seller will process your order soon.`,
                type: 'payment_verified',
                read: false,
                createdAt: new Date()
            });
            
            showToast('Payment verified and order confirmed', 'success');
            
        } else if (status === 'rejected') {
            // Update order status
            await orderRef.update({
                paymentStatus: 'failed',
                orderStatus: 'cancelled',
                verifiedBy: 'admin',
                verifiedAt: new Date(),
                updatedAt: new Date(),
                rejectionReason: 'Payment verification failed'
            });
            
            // Send notification to buyer
            await db.collection('notifications').add({
                userId: orderData.buyerId,
                title: 'Payment Rejected',
                message: `Your payment for order ${orderId} was rejected. Please contact support or try again.`,
                type: 'payment_rejected',
                read: false,
                createdAt: new Date()
            });
            
            showToast('Payment rejected and order cancelled', 'warning');
        }
        
        // Refresh orders view
        if (document.getElementById('ordersPage').style.display === 'block') {
            showOrders();
        }
        
    } catch (error) {
        console.error('Error verifying payment:', error);
        showToast('Failed to verify payment', 'error');
    }
}



// ==================== ORDER PLACEMENT ====================
async function placeOrder() {
    // Validate form
    const shippingName = document.getElementById('shippingName')?.value.trim();
    const shippingPhone = document.getElementById('shippingPhone')?.value.trim();
    const shippingAddress = document.getElementById('shippingAddress')?.value.trim();
    const shippingCity = document.getElementById('shippingCity')?.value.trim();
    const shippingPostalCode = document.getElementById('shippingPostalCode')?.value.trim();
    
    if (!shippingName || !shippingPhone || !shippingAddress || !shippingCity || !shippingPostalCode) {
        showToast('Please fill all shipping details, including Postal Code', 'error');
        return;
    }
    
    if (selectedPaymentMethod !== 'cod') {
        const transactionId = document.getElementById('onlineTransactionId')?.value.trim();
        if (!transactionId) {
            showToast('Please enter transaction ID', 'error');
            return;
        }
    }
    
    try {
        // Calculate totals for final order
        let subtotal = 0;
        let flashSaleDiscount = 0;
        let regularDiscount = 0;
        const shippingFee = 200;
        
        // Group items by seller
        const ordersBySeller = {};
        
        cartItems.forEach(item => {
            const flashSale = flashSales.find(s => 
                s.productId === item.id && 
                s.status === 'active' && 
                new Date(s.endDate) > new Date()
            );
            
            const isFlashSale = !!flashSale;
            const finalPrice = isFlashSale ? (flashSale.flashPrice || item.price * (1 - (flashSale.discount || 0) / 100)) : 
                           (item.discount > 0 ? item.price * (1 - item.discount / 100) : item.price);
            const discountAmount = item.price - finalPrice;
            
            if (isFlashSale) {
                flashSaleDiscount += discountAmount * item.quantity;
            } else if (item.discount > 0) {
                regularDiscount += discountAmount * item.quantity;
            }
            
            subtotal += finalPrice * item.quantity;
            
            // Group by seller
            if (!ordersBySeller[item.sellerId]) {
                ordersBySeller[item.sellerId] = {
                    sellerId: item.sellerId || 'unknown',
                    sellerName: item.sellerName || 'Unknown Seller',
                    items: [],
                    subtotal: 0,
                    discountTotal: 0,
                    flashSaleDiscount: 0
                };
            }
            
            ordersBySeller[item.sellerId].items.push({
                productId: item.id,
                productName: item.name,
                quantity: item.quantity,
                originalPrice: item.price,
                finalPrice: finalPrice,
                discountAmount: discountAmount,
                isFlashSale: isFlashSale,
                image: item.image || 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg',
                category: item.category || 'General'
            });
            
            ordersBySeller[item.sellerId].subtotal += finalPrice * item.quantity;
            ordersBySeller[item.sellerId].discountTotal += discountAmount * item.quantity;
            
            if (isFlashSale) {
                ordersBySeller[item.sellerId].flashSaleDiscount += discountAmount * item.quantity;
            }
        });
        
        const tax = subtotal * 0.05;
        const total = subtotal + shippingFee + tax;
        const totalDiscount = flashSaleDiscount + regularDiscount;
        
        // Show success message with invoice
        const orderId = 'ORD' + Date.now().toString().slice(-8);
        
        const successHTML = `
            <div style="text-align: center; padding: 2rem;">
                <div style="background: ${greenTheme.colors.gradientSuccess}; color: white; width: 100px; height: 100px; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto 1.5rem; font-size: 3rem;">
                    <i class="fas fa-check"></i>
                </div>
                
                <h3 style="color: ${greenTheme.colors.success}; margin-bottom: 1rem; font-size: 1.8rem;">
                    🎉 Order Placed Successfully!
                </h3>
                
                <div style="background: white; border-radius: 16px; padding: 1.5rem; margin: 1.5rem 0; box-shadow: ${greenTheme.shadows.md}; border: 1px solid ${greenTheme.colors.gray200};">
                    <p><strong>Order ID:</strong> <span style="color: ${greenTheme.colors.primary}; font-weight: 800;">${orderId}</span></p>
                    <p><strong>Payment Method:</strong> ${selectedPaymentMethod === 'cod' ? 'Cash on Delivery' : selectedPaymentMethod === 'easypaisa' ? 'EasyPaisa' : 'JazzCash'}</p>
                    <p><strong>Total Amount:</strong> <span style="color: ${greenTheme.colors.primary}; font-weight: 800;">Rs. ${total.toFixed(2)}</span></p>
                    ${totalDiscount > 0 ? `
                        <p><strong>Total Savings:</strong> <span style="color: ${greenTheme.colors.success}; font-weight: 800;">Rs. ${totalDiscount.toLocaleString()}</span></p>
                        ${flashSaleDiscount > 0 ? `
                            <p><strong>Flash Sale Savings:</strong> <span style="color: ${greenTheme.colors.warning}; font-weight: 800;">Rs. ${flashSaleDiscount.toLocaleString()}</span></p>
                        ` : ''}
                    ` : ''}
                </div>
                
                <div style="margin-top: 2rem; display: flex; flex-direction: column; gap: 1rem; align-items: center;">
                    <button class="premium-btn" onclick="showOrders()" style="width: 80%;">
                        <i class="fas fa-box"></i> View Orders
                    </button>
                    <button class="premium-btn-secondary" onclick="showHomePage()" style="width: 80%;">
                        <i class="fas fa-shopping-bag"></i> Continue Shopping
                    </button>
                </div>
            </div>
        `;
        
        // Create success modal
        const modal = document.createElement('div');
        modal.className = 'modal active';
        modal.style.display = 'flex';
        modal.innerHTML = `
            <div class="modal-content" style="max-width: 500px;">
                <div style="text-align: right;">
                    <button onclick="closeCustomOrderModal()" style="background: none; border: none; font-size: 1.8rem; color: ${greenTheme.colors.gray500}; cursor: pointer; padding: 0.5rem;">×</button>
                </div>
                ${successHTML}
            </div>
        `;
        
        document.body.appendChild(modal);
        
        // Clear cart
        cartItems = [];
        saveCart();
        updateCartCount();
        
    } catch (error) {
        console.error('❌ Error placing order:', error);
        showToast(`Error placing order: ${error.message}`, 'error');
    }
}

// Initialize flash sales (make sure to populate this from your database)
async function loadFlashSales() {
    try {
        const now = new Date();
        
        // Get all flash sales and filter client-side
        const snapshot = await db.collection('flashSales').get();
        
        flashSales = snapshot.docs
            .map(doc => {
                const data = doc.data();
                return {
                    id: doc.id,
                    ...data,
                    endDate: data.endDate?.toDate ? data.endDate.toDate() : new Date(data.endDate)
                };
            })
            .filter(sale => 
                sale.status === 'active' && 
                sale.endDate > now
            )
            .sort((a, b) => a.endDate - b.endDate) // Sort by soonest ending
            .slice(0, 20);
        
        console.log('✅ Flash Sales loaded:', flashSales.length);
        displayFlashSaleProducts();
        
    } catch (error) {
        console.error('❌ Error loading flash sales:', error);
        flashSales = [];
        displayFlashSaleProducts();
    }
}

// Call this when your app initializes
loadFlashSales();
            
       
// Function to view product details from anywhere (Cart, Home, Search)
async function viewProductDetail(productId) {
    try {
        const doc = await db.collection('products').doc(productId).get();
        if (!doc.exists) {
            showToast('Product not found', 'error');
            return;
        }
        const product = { id: doc.id, ...doc.data() };
        
        // Use your existing displayProductDetail function or modal
        displayProductDetailModal(product); // Assuming this is your detail view function
    } catch (error) {
        showToast('Error loading details', 'error');
    }
}

// Ensure cart items have an onclick
// Update the cart item HTML to include:
// <div onclick="viewProductDetail('${item.id}')" style="cursor:pointer">...</div>



// Helper function to clean object (remove undefined values)
function cleanObject(obj) {
    const cleaned = {};
    for (const key in obj) {
        if (obj[key] !== undefined && obj[key] !== null) {
            if (typeof obj[key] === 'object' && !(obj[key] instanceof Date) && !Array.isArray(obj[key])) {
                cleaned[key] = cleanObject(obj[key]);
            } else if (Array.isArray(obj[key])) {
                cleaned[key] = obj[key].map(item => 
                    typeof item === 'object' ? cleanObject(item) : item
                ).filter(item => item !== undefined && item !== null);
            } else {
                cleaned[key] = obj[key];
            }
        }
    }
    return cleaned;
}

// Also update the sendAdminPaymentVerificationNotification function:

async function sendAdminPaymentVerificationNotification(orderId) {
    try {
        const orderDoc = await db.collection('orders').doc(orderId).get();
        if (!orderDoc.exists) return;
        
        const order = orderDoc.data();
        
        // Create notification for admin (with cleaned data)
        const notificationData = cleanObject({
            type: 'payment_verification',
            orderId: orderId,
            customerName: order.customerName || 'Customer',
            customerEmail: order.customerEmail || '',
            amount: order.totalAmount || 0,
            paymentMethod: order.paymentMethod || 'unknown',
            transactionId: order.transactionId || '',
            status: 'pending',
            createdAt: firebase.firestore.FieldValue.serverTimestamp(),
            read: false
        });
        
        await db.collection('admin_notifications').add(notificationData);
        
        console.log('✅ Payment verification notification sent to admin');
        
    } catch (error) {
        console.error('❌ Error sending admin notification:', error);
    }
}
        
    

function closeCustomOrderModal() {
    const modal = document.querySelector('.modal.active:last-child');
    if (modal) {
        modal.remove();
    }
}

function showPaymentVerificationInfo() {
    closeCustomOrderModal();
    
    const infoModal = document.createElement('div');
    infoModal.className = 'modal active';
    infoModal.style.display = 'flex';
    infoModal.innerHTML = `
        <div class="modal-content" style="max-width: 600px;">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                <h2 style="color: var(--primary);"><i class="fas fa-shield-alt"></i> Payment Verification Process</h2>
                <button onclick="closeCustomOrderModal()" style="background: none; border: none; font-size: 1.5rem; color: var(--text-secondary); cursor: pointer;">×</button>
            </div>
            
            <div style="background: var(--accent); padding: 1.5rem; border-radius: var(--radius); margin-bottom: 1.5rem;">
                <h3><i class="fas fa-clock"></i> What happens next?</h3>
                <ol style="margin-left: 1.5rem; margin-top: 1rem;">
                    <li><strong>Payment Verification (0-48 hours):</strong> Admin verifies your payment</li>
                    <li><strong>Order Processing:</strong> Once verified, order is sent to seller</li>
                    <li><strong>Order Preparation:</strong> Seller prepares your order (1-2 days)</li>
                    <li><strong>Shipping:</strong> Order is shipped with tracking</li>
                    <li><strong>Delivery:</strong> Order delivered to your address</li>
                </ol>
            </div>
            
            <div style="background: rgba(52, 152, 219, 0.1); padding: 1.5rem; border-radius: var(--radius);">
                <h3><i class="fas fa-question-circle"></i> Frequently Asked Questions</h3>
                <div style="margin-top: 1rem;">
                    <p><strong>Q: Why is payment verification needed?</strong></p>
                    <p>A: To prevent fraud and ensure secure transactions.</p>
                    
                    <p><strong>Q: How long does verification take?</strong></p>
                    <p>A: Usually within 24 hours, maximum 48 hours.</p>
                    
                    <p><strong>Q: What if my payment isn't verified?</strong></p>
                    <p>A: You'll receive a notification and can contact support.</p>
                </div>
            </div>
            
            <div style="margin-top: 2rem; text-align: center;">
                <button class="btn btn-primary" onclick="closeCustomOrderModal(); showOrders();">
                    <i class="fas fa-box"></i> Check Order Status
                </button>
            </div>
        </div>
    `;
    
    document.body.appendChild(infoModal);
}

async function sendAdminPaymentVerificationNotification(orderId) {
    try {
        const orderDoc = await db.collection('orders').doc(orderId).get();
        if (!orderDoc.exists) return;
        
        const order = orderDoc.data();
        
        // Create notification for admin
        await db.collection('admin_notifications').add({
            type: 'payment_verification',
            orderId: orderId,
            customerName: order.customerName,
            customerEmail: order.customerEmail,
            amount: order.totalAmount,
            paymentMethod: order.paymentMethod,
            transactionId: order.transactionId,
            status: 'pending',
            createdAt: new Date(),
            read: false
        });
        
        console.log('Payment verification notification sent to admin');
        
    } catch (error) {
        console.error('Error sending admin notification:', error);
    }
}

    function showOrders() {
        if (!currentUser) {
            showToast('Please login to view orders', 'error');
            openAuthModal('buyerLogin');
            return;
        }
        
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        const ordersPage = document.getElementById('ordersPage');
        ordersPage.style.display = 'block';
        
        loadBuyerOrders();
    }

    async function loadBuyerOrders() {
    if (!currentUser) {
        console.log('❌ No user logged in');
        showToast('Please login to view orders', 'error');
        return;
    }
    
    try {
        console.log('🛍️ Loading buyer orders for:', currentUser.uid);
        
        // Target the correct container from your HTML
        const ordersContent = document.getElementById('ordersContent');
        if (ordersContent) {
            ordersContent.innerHTML = `
                <div style="text-align: center; padding: 3rem;">
                    <div class="loading" style="width: 40px; height: 40px; margin: 0 auto 1rem; border: 4px solid #f3f3f3; border-top: 4px solid var(--primary); border-radius: 50%; animation: spin 1s linear infinite;"></div>
                    <p>Loading your orders...</p>
                </div>
            `;
        }
        
        // FIX: Search for 'customerId' to match the field saved during checkout
        const snapshot = await db.collection('orders')
            .where('customerId', '==', currentUser.uid)
            .get();
        
        if (snapshot.empty) {
            console.log('📭 No orders found for customer:', currentUser.uid);
            buyerOrders = [];
            displayEmptyOrders(); // Call your existing empty state function
            return;
        }
        
        // Map the data and handle Firestore Timestamps
        buyerOrders = snapshot.docs.map(doc => {
            const data = doc.data();
            return {
                id: doc.id,
                ...data,
                createdAt: data.createdAt?.toDate ? data.createdAt.toDate() : new Date()
            };
        });
        
        // Sort newest first
        buyerOrders.sort((a, b) => b.createdAt - a.createdAt);
        
        console.log(`✅ Loaded ${buyerOrders.length} orders`);
        displayBuyerOrders(); // Call the display function below
        
    } catch (error) {
        console.error('❌ Error loading buyer orders:', error);
        showToast('Failed to load orders: ' + error.message, 'error');
    }
}
// Update the displayBuyerOrders() function:

function displayBuyerOrders() {
    const ordersContent = document.getElementById('ordersContent');
    if (!ordersContent) return;
    
    if (buyerOrders.length === 0) {
        ordersContent.innerHTML = `
            <div style="text-align: center; padding: 4rem 2rem;">
                <div style="font-size: 5rem; color: var(--text-secondary); opacity: 0.3; margin-bottom: 1.5rem;">
                    <i class="fas fa-box-open"></i>
                </div>
                <h3 style="color: var(--text-secondary); margin-bottom: 1rem; font-weight: 400;">
                    No Orders Yet
                </h3>
                <p style="color: var(--text-secondary); margin-bottom: 2rem; max-width: 400px; margin-left: auto; margin-right: auto;">
                    You haven't placed any orders yet. Start shopping to see your orders here.
                </p>
                <div style="display: flex; gap: 1rem; justify-content: center;">
                    <button class="btn btn-primary" onclick="showAllProducts()">
                        <i class="fas fa-shopping-bag"></i> Shop Now
                    </button>
                    <button class="btn btn-secondary" onclick="showHomePage()">
                        <i class="fas fa-home"></i> Go Home
                    </button>
                </div>
            </div>
        `;
        return;
    }
    
    ordersContent.innerHTML = buyerOrders.map(order => {
        // Format date
        const orderDate = order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt);
        const formattedDate = orderDate.toLocaleDateString('en-PK', {
            day: 'numeric',
            month: 'short',
            year: 'numeric'
        });
        
        // Calculate time difference for 24-hour cancellation
        const now = new Date();
        const diffInHours = (now - orderDate) / (1000 * 60 * 60);
        const canCancel = order.status === 'pending' && diffInHours < 24;
        
        // Payment verification status
        let paymentStatusBadge = '';
        let paymentStatusText = '';
        
        if (order.paymentMethod !== 'cod') {
            if (order.paymentVerification === 'approved') {
                paymentStatusBadge = 'status-approved-badge';
                paymentStatusText = 'Payment Verified';
            } else if (order.paymentVerification === 'rejected') {
                paymentStatusBadge = 'status-cancelled-badge';
                paymentStatusText = 'Payment Rejected';
            } else {
                paymentStatusBadge = 'status-pending-badge';
                paymentStatusText = 'Verification Pending';
            }
        }
        
        // Order status badge
        const orderStatusClass = getStatusBadgeClass(order.status);
        const orderStatusText = getStatusText(order.status);
        
        return `
            <div class="order-card" id="order-${order.id}">
                <div class="order-header">
                    <div>
                        <h3>Order #${order.id.slice(-8)}</h3>
                        <p>Placed on: ${formattedDate}</p>
                        <p>Seller: ${escapeHtml(order.sellerName || 'Unknown')}</p>
                        
                        <div style="display: flex; gap: 1rem; margin-top: 0.5rem; flex-wrap: wrap;">
                            <span class="order-status-badge ${orderStatusClass}">
                                ${orderStatusText}
                            </span>
                            
                            ${order.paymentMethod !== 'cod' ? `
                                <span class="order-status-badge ${paymentStatusBadge}">
                                    <i class="fas fa-credit-card"></i> ${paymentStatusText}
                                </span>
                            ` : ''}
                            
                            ${order.flashSaleDiscount > 0 ? `
                                <span class="order-status-badge" style="background: #ff6b35; color: white;">
                                    <i class="fas fa-bolt"></i> Flash Sale
                                </span>
                            ` : ''}
                        </div>
                    </div>
                    
                    <div style="text-align: right;">
                        <h3 class="current-price">Rs. ${order.totalAmount?.toLocaleString() || '0'}</h3>
                        <p style="color: var(--text-secondary); font-size: 0.9rem;">
                            ${order.items?.length || 0} item${order.items?.length !== 1 ? 's' : ''}
                        </p>
                    </div>
                </div>
                
                <div class="order-items" style="margin: 1rem 0;">
                    ${order.items && order.items.slice(0, 2).map((item, index) => `
                        <div class="order-item">
                            <img src="${item.image || 'https://via.placeholder.com/80'}" 
                                 alt="${escapeHtml(item.productName)}" 
                                 class="order-item-image"
                                 onerror="this.src='https://via.placeholder.com/80'">
                            <div style="flex: 1;">
                                <p style="font-weight: 500;">${escapeHtml(item.productName)}</p>
                                <div style="display: flex; gap: 1rem; margin-top: 0.5rem;">
                                    <span>Qty: ${item.quantity}</span>
                                    <span>
                                        Rs. ${item.finalPrice?.toLocaleString() || '0'}
                                        ${item.originalPrice > item.finalPrice ? `
                                            <span style="text-decoration: line-through; color: var(--text-secondary); margin-left: 0.5rem;">
                                                Rs. ${item.originalPrice?.toLocaleString()}
                                            </span>
                                        ` : ''}
                                    </span>
                                    ${item.isFlashSale ? `
                                        <span style="background: #ff6b35; color: white; padding: 2px 8px; border-radius: 4px; font-size: 0.8rem;">
                                            <i class="fas fa-bolt"></i> Flash Sale
                                        </span>
                                    ` : ''}
                                </div>
                            </div>
                        </div>
                    `).join('')}
                    
                    ${order.items && order.items.length > 2 ? `
                        <div style="text-align: center; padding: 0.5rem; color: var(--text-secondary);">
                            + ${order.items.length - 2} more item${order.items.length - 2 !== 1 ? 's' : ''}
                        </div>
                    ` : ''}
                </div>
                
                <div class="order-actions">
                    <button class="btn btn-primary btn-sm" onclick="viewOrderDetails('${order.id}')">
                        <i class="fas fa-eye"></i> View Details
                    </button>
                    
                    <button class="btn btn-secondary btn-sm" onclick="trackOrder('${order.id}')">
                        <i class="fas fa-truck"></i> Track Order
                    </button>
                    
                    ${canCancel ? `
                        <button class="btn btn-danger btn-sm" onclick="cancelOrder('${order.id}')">
                            <i class="fas fa-times"></i> Cancel Order
                        </button>
                    ` : ''}
                    
                    ${order.status === 'delivered' ? `
                        <button class="btn btn-success btn-sm" onclick="showReviewModal('${order.id}')">
                            <i class="fas fa-star"></i> Add Review
                        </button>
                    ` : ''}
                    
                    ${order.paymentMethod !== 'cod' && order.paymentVerification === 'pending' ? `
                        <button class="btn btn-warning btn-sm" onclick="viewPaymentVerificationStatus('${order.id}')">
                            <i class="fas fa-clock"></i> Payment Status
                        </button>
                    ` : ''}
                </div>
            </div>
        `;
    }).join('');
}

// Add new function for payment verification status
function viewPaymentVerificationStatus(orderId) {
    const order = buyerOrders.find(o => o.id === orderId);
    if (!order) return;
    
    const modal = document.createElement('div');
    modal.className = 'modal active';
    modal.style.display = 'flex';
    modal.innerHTML = `
        <div class="modal-content" style="max-width: 500px;">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                <h2 style="color: var(--primary);"><i class="fas fa-credit-card"></i> Payment Verification</h2>
                <button onclick="closeModalByElement(this)" style="background: none; border: none; font-size: 1.5rem; color: var(--text-secondary); cursor: pointer;">×</button>
            </div>
            
            <div style="background: var(--accent); padding: 1.5rem; border-radius: var(--radius); margin-bottom: 1.5rem;">
                <h3>Order #${order.id.slice(-8)}</h3>
                <p><strong>Amount:</strong> Rs. ${order.totalAmount?.toLocaleString()}</p>
                <p><strong>Payment Method:</strong> ${order.paymentMethod === 'easypaisa' ? 'EasyPaisa' : 'JazzCash'}</p>
                <p><strong>Transaction ID:</strong> ${order.transactionId || 'Not provided'}</p>
                <p><strong>Status:</strong> 
                    <span class="order-status-badge ${order.paymentVerification === 'approved' ? 'status-approved-badge' : 
                                                     order.paymentVerification === 'rejected' ? 'status-cancelled-badge' : 
                                                     'status-pending-badge'}">
                        ${order.paymentVerification === 'approved' ? 'Verified' : 
                          order.paymentVerification === 'rejected' ? 'Rejected' : 'Pending Verification'}
                    </span>
                </p>
            </div>
            
            <div style="background: rgba(52, 152, 219, 0.1); padding: 1.5rem; border-radius: var(--radius);">
                <h4><i class="fas fa-info-circle"></i> Verification Process</h4>
                <p>Your payment is being verified by our admin team. This usually takes:</p>
                <ul style="margin-left: 1.5rem; margin-top: 0.5rem;">
                    <li><strong>Within 24 hours:</strong> For transactions during business hours</li>
                    <li><strong>Up to 48 hours:</strong> For weekends and holidays</li>
                </ul>
                <p style="margin-top: 1rem; font-style: italic;">
                    Note: Your order will be sent to the seller only after payment verification.
                </p>
            </div>
            
            <div style="margin-top: 2rem; display: flex; gap: 1rem; justify-content: center;">
                <button class="btn btn-primary" onclick="closeModalByElement(this.parentElement.parentElement.parentElement)">
                    <i class="fas fa-check"></i> OK
                </button>
                <button class="btn btn-secondary" onclick="showSupportChat()">
                    <i class="fas fa-headset"></i> Contact Support
                </button>
            </div>
        </div>
    `;
    
    document.body.appendChild(modal);
}

function closeModalByElement(element) {
    if (element) {
        element.remove();
    }
}
async function cancelOrder(orderId) {
    if (!confirm('Are you sure you want to cancel this order? This cannot be undone.')) {
        return;
    }

    try {
        showToast('Processing cancellation...', 'info');
        
        await db.collection('orders').doc(orderId).update({
            status: 'cancelled',
            updatedAt: firebase.firestore.FieldValue.serverTimestamp(),
            cancelledBy: 'buyer',
            cancelReason: 'User requested cancellation within 24 hours'
        });

        showToast('Order cancelled successfully', 'success');
        
        // Refresh the orders list to update the UI
        loadBuyerOrders();
        
    } catch (error) {
        console.error("Error cancelling order:", error);
        showToast('Failed to cancel order: ' + error.message, 'error');
    }
}
// Update the displayEmptyOrders function to show index message
function displayEmptyOrdersWithIndexMessage() {
    const ordersContent = document.getElementById('ordersContent');
    if (!ordersContent) return;
    
    ordersContent.innerHTML = `
        <div style="text-align: center; padding: 4rem 2rem;">
            <div style="font-size: 5rem; color: var(--text-secondary); opacity: 0.3; margin-bottom: 1.5rem;">
                <i class="fas fa-cogs"></i>
            </div>
            <h3 style="color: var(--primary); margin-bottom: 1rem; font-weight: 500;">
                Database Index is Being Prepared
            </h3>
            <p style="color: var(--text-secondary); margin-bottom: 1.5rem; max-width: 500px; margin-left: auto; margin-right: auto; line-height: 1.6;">
                Your order history is being optimized for faster loading. 
                This usually takes 2-5 minutes. Please try again in a few moments.
            </p>
            <div style="background: var(--accent); padding: 1.5rem; border-radius: var(--radius); max-width: 400px; margin: 0 auto 2rem; text-align: left;">
                <h4 style="color: var(--primary); margin-bottom: 0.5rem; font-size: 1rem;">
                    <i class="fas fa-info-circle"></i> Quick Actions:
                </h4>
                <ul style="color: var(--text-secondary); margin: 0; padding-left: 1.5rem;">
                    <li>Refresh the page in 5 minutes</li>
                    <li>Continue shopping in the meantime</li>
                    <li>Check your email for order confirmations</li>
                </ul>
            </div>
            <div style="display: flex; gap: 1rem; justify-content: center;">
                <button class="btn btn-primary" onclick="showAllProducts()">
                    <i class="fas fa-shopping-bag"></i> Continue Shopping
                </button>
                <button class="btn btn-secondary" onclick="loadBuyerOrders()">
                    <i class="fas fa-redo"></i> Try Again
                </button>
            </div>
        </div>
    `;
}

// Keep the original displayEmptyOrders function
function displayEmptyOrders() {
    const ordersContent = document.getElementById('ordersContent');
    if (!ordersContent) return;
    
    ordersContent.innerHTML = `
        <div style="text-align: center; padding: 4rem 2rem;">
            <div style="font-size: 5rem; color: var(--text-secondary); opacity: 0.3; margin-bottom: 1.5rem;">
                <i class="fas fa-box-open"></i>
            </div>
            <h3 style="color: var(--text-secondary); margin-bottom: 1rem; font-weight: 400;">
                No Orders Yet
            </h3>
            <p style="color: var(--text-secondary); margin-bottom: 2rem; max-width: 400px; margin-left: auto; margin-right: auto;">
                You haven't placed any orders yet. Start shopping to see your orders here.
            </p>
            <div style="display: flex; gap: 1rem; justify-content: center;">
                <button class="btn btn-primary" onclick="showAllProducts()">
                    <i class="fas fa-shopping-bag"></i> Shop Now
                </button>
                <button class="btn btn-secondary" onclick="showHomePage()">
                    <i class="fas fa-home"></i> Go Home
                </button>
            </div>
        </div>
    `;
}
    async function viewOrderDetails(orderId) {
    console.log('=== viewOrderDetails START ===');
    console.log('Order ID:', orderId);
    console.log('Seller Orders:', sellerOrders.length);
    console.log('Buyer Orders:', buyerOrders.length);
    
    // Try to find the order in seller orders first
    let order = sellerOrders.find(o => o.id === orderId);
    console.log('Found in seller orders:', order ? 'YES' : 'NO');
    
    // If not found in seller orders, try buyer orders
    if (!order) {
        order = buyerOrders.find(o => o.id === orderId);
        console.log('Found in buyer orders:', order ? 'YES' : 'NO');
    }
    
    if (!order) {
        console.error('Order not found in any array');
        showToast('Order not found', 'error');
        return;
    }
    
    console.log('Order details:', order);
    
    // Format the date
    const orderDate = order.createdAt || new Date();
    const formattedDate = orderDate.toLocaleString('en-PK', {
        day: '2-digit',
        month: 'short',
        year: 'numeric',
        hour: '2-digit',
        minute: '2-digit'
    });
    
    // Create modal HTML
    const modalHTML = `
        <div class="modal" id="orderDetailsModal" style="display: flex;">
            <div class="modal-content" style="max-width: 800px; max-height: 90vh; overflow-y: auto;">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
                    <h2 style="color: var(--primary);">Order Details #${order.id.slice(-8)}</h2>
                    <button onclick="closeOrderDetailsModal()" style="background: none; border: none; font-size: 1.5rem; color: var(--text-secondary); cursor: pointer;">×</button>
                </div>
                
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; margin-bottom: 2rem;">
                    <div>
                        <h4>Order Information</h4>
                        <div style="background: var(--accent); padding: 1rem; border-radius: var(--radius); margin-top: 0.5rem;">
                            <p><strong>Order Date:</strong> ${formattedDate}</p>
                            <p><strong>Order Status:</strong> 
                                <span class="order-status-badge ${getStatusBadgeClass(order.status)}">
                                    ${getStatusText(order.status)}
                                </span>
                            </p>
                            <p><strong>Payment Method:</strong> ${order.paymentMethod === 'cod' ? 'Cash on Delivery' : 
                                order.paymentMethod === 'easypaisa' ? 'EasyPaisa' : 'JazzCash'}</p>
                            <p><strong>Payment Status:</strong> ${order.paymentStatus || 'pending'}</p>
                            <p><strong>Invoice Status:</strong> ${order.invoiceLocked ? '🔒 Locked' : '✅ Unlocked'}</p>
                        </div>
                    </div>
                    
                    <div>
                        <h4>Customer Information</h4>
                        <div style="background: var(--accent); padding: 1rem; border-radius: var(--radius); margin-top: 0.5rem;">
                            <p><strong>Name:</strong> ${escapeHtml(order.customerName || 'N/A')}</p>
                            <p><strong>Phone:</strong> ${escapeHtml(order.customerPhone || 'N/A')}</p>
                            <p><strong>Email:</strong> ${escapeHtml(order.customerEmail || 'N/A')}</p>
                            <p><strong>Address:</strong> ${escapeHtml(order.shippingAddress || 'N/A')}</p>
                            <p><strong>City:</strong> ${escapeHtml(order.shippingCity || 'N/A')}</p>
                        </div>
                    </div>
                </div>
                
                <div style="margin-bottom: 2rem;">
                    <h4>Order Items</h4>
                    <div style="background: var(--white); border-radius: var(--radius); padding: 1rem; margin-top: 0.5rem; border: 1px solid var(--border);">
                        ${order.items && order.items.length > 0 ? `
                            <table style="width: 100%; border-collapse: collapse;">
                                <thead>
                                    <tr>
                                        <th style="padding: 0.75rem; text-align: left; border-bottom: 2px solid var(--border);">Product</th>
                                        <th style="padding: 0.75rem; text-align: right; border-bottom: 2px solid var(--border);">Price</th>
                                        <th style="padding: 0.75rem; text-align: center; border-bottom: 2px solid var(--border);">Quantity</th>
                                        <th style="padding: 0.75rem; text-align: right; border-bottom: 2px solid var(--border);">Total</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${order.items.map((item, index) => `
                                        <tr>
                                            <td style="padding: 1rem; border-bottom: 1px solid var(--border);">
                                                <div style="display: flex; gap: 1rem; align-items: center;">
                                                    <img src="https://via.placeholder.com/60" 
                                                         style="width: 60px; height: 60px; object-fit: cover; border-radius: var(--radius);"
                                                         alt="${escapeHtml(item.productName || 'Product')}"
                                                         onerror="this.src='https://via.placeholder.com/60'">
                                                    <div>
                                                        <strong>${escapeHtml(item.productName || 'Product')}</strong>
                                                        <p style="color: var(--text-secondary); font-size: 0.9rem; margin-top: 0.25rem;">
                                                            Product ID: ${item.productId || 'N/A'}
                                                        </p>
                                                    </div>
                                                </div>
                                            </td>
                                            <td style="padding: 1rem; border-bottom: 1px solid var(--border); text-align: right;">
                                                Rs. ${item.finalPrice?.toLocaleString() || '0'}
                                            </td>
                                            <td style="padding: 1rem; border-bottom: 1px solid var(--border); text-align: center;">
                                                ${item.quantity || 1}
                                            </td>
                                            <td style="padding: 1rem; border-bottom: 1px solid var(--border); text-align: right;">
                                                Rs. ${((item.finalPrice || 0) * (item.quantity || 1)).toLocaleString()}
                                            </td>
                                        </tr>
                                    `).join('')}
                                </tbody>
                            </table>
                        ` : `
                            <p style="text-align: center; color: var(--text-secondary); padding: 2rem;">
                                No items found in this order
                            </p>
                        `}
                    </div>
                </div>
                
                <div style="text-align: right; padding-top: 1rem; border-top: 2px solid var(--primary);">
                    <div style="display: inline-block; text-align: left; min-width: 300px;">
                        <div style="display: flex; justify-content: space-between; margin-bottom: 0.5rem;">
                            <span>Subtotal:</span>
                            <span>Rs. ${order.subtotal?.toLocaleString() || '0'}</span>
                        </div>
                        <div style="display: flex; justify-content: space-between; margin-bottom: 0.5rem;">
                            <span>Shipping:</span>
                            <span>Rs. ${order.shippingFee?.toLocaleString() || '200'}</span>
                        </div>
                        <div style="display: flex; justify-content: space-between; margin-bottom: 0.5rem;">
                            <span>Tax:</span>
                            <span>Rs. ${order.tax?.toFixed(2) || '0.00'}</span>
                        </div>
                        <div style="height: 1px; background: var(--border); margin: 1rem 0;"></div>
                        <div style="display: flex; justify-content: space-between; font-size: 1.2rem; font-weight: bold;">
                            <span>Total Amount:</span>
                            <span class="current-price">Rs. ${order.totalAmount?.toLocaleString() || '0'}</span>
                        </div>
                    </div>
                </div>
                
                <div style="margin-top: 2rem; display: flex; gap: 1rem; justify-content: center;">
                    <button class="btn btn-primary" onclick="generateInvoice('${order.id}')">
                        <i class="fas fa-file-invoice"></i> Download Invoice
                    </button>
                    <button class="btn btn-secondary" onclick="closeOrderDetailsModal()">
                        <i class="fas fa-times"></i> Close
                    </button>
                    ${order.status === 'pending' || order.status === 'confirmed' ? `
                        <button class="btn btn-warning" onclick="updateOrderStatus('${order.id}')">
                            <i class="fas fa-edit"></i> Update Status
                        </button>
                    ` : ''}
                </div>
            </div>
        </div>
    `;
    
    // Create and show the modal
    const modalContainer = document.createElement('div');
    modalContainer.id = 'orderDetailsModalContainer';
    modalContainer.innerHTML = modalHTML;
    document.body.appendChild(modalContainer);
    
    console.log('=== viewOrderDetails END ===');
}

function closeOrderDetailsModal() {
    const modalContainer = document.getElementById('orderDetailsModalContainer');
    if (modalContainer) {
        modalContainer.remove();
    }
}

    function trackOrder(orderId) {
        const order = buyerOrders.find(o => o.id === orderId);
        if (!order) return;
        
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        const trackingPage = document.getElementById('orderTrackingPage');
        trackingPage.style.display = 'block';
        
        const trackingContent = document.getElementById('orderTrackingContent');
        const orderDate = order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt);
        
        trackingContent.innerHTML = `
            <div class="section">
                <div class="section-header">
                    <h2 class="section-title">Track Order #${order.id.slice(-8)}</h2>
                    <button class="btn btn-secondary" onclick="showOrders()">
                        <i class="fas fa-arrow-left"></i> Back to Orders
                    </button>
                </div>
                
                <div style="background: var(--white); border-radius: var(--radius); padding: 2rem; box-shadow: var(--shadow);">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 2rem;">
                        <div>
                            <h3>${escapeHtml(order.sellerName || 'Seller')}</h3>
                            <p style="color: var(--text-secondary);">
                                Order Date: ${orderDate.toLocaleDateString()}
                            </p>
                        </div>
                        <div class="order-status-badge ${getStatusBadgeClass(order.status)}" style="font-size: 1.1rem;">
                            ${getStatusText(order.status)}
                        </div>
                    </div>
                    
                    <div class="tracking-progress">
                        <div class="progress-steps">
                            <div class="step ${['pending', 'confirmed', 'packed', 'shipped', 'out_for_delivery', 'delivered'].indexOf(order.status) >= 0 ? 'active' : ''}">
                                <div class="step-circle">1</div>
                                <div class="step-label">Order Placed</div>
                            </div>
                            <div class="step ${['confirmed', 'packed', 'shipped', 'out_for_delivery', 'delivered'].indexOf(order.status) >= 0 ? 'active' : ''}">
                                <div class="step-circle">2</div>
                                <div class="step-label">Confirmed</div>
                            </div>
                            <div class="step ${['packed', 'shipped', 'out_for_delivery', 'delivered'].indexOf(order.status) >= 0 ? 'active' : ''}">
                                <div class="step-circle">3</div>
                                <div class="step-label">Packed</div>
                            </div>
                            <div class="step ${['shipped', 'out_for_delivery', 'delivered'].indexOf(order.status) >= 0 ? 'active' : ''}">
                                <div class="step-circle">4</div>
                                <div class="step-label">Shipped</div>
                            </div>
                            <div class="step ${['out_for_delivery', 'delivered'].indexOf(order.status) >= 0 ? 'active' : ''}">
                                <div class="step-circle">5</div>
                                <div class="step-label">Out for Delivery</div>
                            </div>
                            <div class="step ${['delivered'].indexOf(order.status) >= 0 ? 'active' : ''}">
                                <div class="step-circle">6</div>
                                <div class="step-label">Delivered</div>
                            </div>
                        </div>
                    </div>
                    
                    ${order.timeline ? `
                        <div class="tracking-timeline" style="margin-top: 3rem;">
                            <h4>Tracking History</h4>
                            ${order.timeline.map(event => {
                                const eventDate = event.timestamp?.toDate ? event.timestamp.toDate() : new Date(event.timestamp);
                                return `
                                    <div class="timeline-item">
                                        <div class="timeline-date">
                                            ${eventDate.toLocaleString()}
                                        </div>
                                        <div class="timeline-content">
                                            <strong>${getStatusText(event.status)}</strong>
                                            ${event.note ? `<p>${escapeHtml(event.note)}</p>` : ''}
                                            ${event.trackingNumber ? `<p><strong>Tracking Number:</strong> ${event.trackingNumber}</p>` : ''}
                                        </div>
                                    </div>
                                `;
                            }).join('')}
                        </div>
                    ` : `
                        <div style="text-align: center; padding: 2rem; color: var(--text-secondary);">
                            <i class="fas fa-clock" style="font-size: 3rem; margin-bottom: 1rem;"></i>
                            <h4>No Tracking Updates Yet</h4>
                            <p>Your order is being processed by the seller.</p>
                        </div>
                    `}
                    
                    ${order.trackingNumber ? `
                        <div style="margin-top: 2rem; background: rgba(1, 65, 28, 0.1); padding: 1.5rem; border-radius: var(--radius);">
                            <h4><i class="fas fa-truck"></i> Tracking Information</h4>
                            <p><strong>Tracking Number:</strong> ${order.trackingNumber}</p>
                            <p><strong>Carrier:</strong> TCS / Leopard Courier</p>
                            <p style="margin-top: 0.5rem;">
                                <a href="https://www.tcsexpress.com/track" target="_blank" class="btn btn-primary">
                                    <i class="fas fa-external-link-alt"></i> Track on Carrier Website
                                </a>
                            </p>
                        </div>
                    ` : ''}
                </div>
            </div>
        `;
    }

    async function cancelOrder(orderId) {
        if (!confirm('Are you sure you want to cancel this order?')) return;
        
        try {
            await db.collection('orders').doc(orderId).update({
                status: 'cancelled',
                updatedAt: new Date(),
                timeline: firebase.firestore.FieldValue.arrayUnion({
                    status: 'cancelled',
                    timestamp: new Date(),
                    note: 'Order cancelled by customer'
                })
            });
            
            showToast('Order cancelled successfully', 'success');
            loadBuyerOrders();
            
        } catch (error) {
            console.error('Error cancelling order:', error);
            showToast('Error cancelling order', 'error');
        }
    }

    function addReview(orderId) {
        const order = buyerOrders.find(o => o.id === orderId);
        if (!order) return;
        
        selectedReviewProductId = order.items[0]?.productId;
        starRating = 0;
        updateStarRating();
        document.getElementById('reviewForm').reset();
        openModal('reviewModal');
    }

    async function submitReview(e) {
        e.preventDefault();
        
        if (!selectedReviewProductId || starRating === 0) {
            showToast('Please provide a rating', 'error');
            return;
        }
        
        try {
            const reviewData = {
                productId: selectedReviewProductId,
                userId: currentUser.uid,
                userName: currentUserProfile?.displayName || currentUser.email,
                rating: starRating,
                title: document.getElementById('reviewTitle').value.trim(),
                text: document.getElementById('reviewText').value.trim(),
                images: [],
                video: null,
                verifiedPurchase: true,
                createdAt: new Date()
            };
            
            // Upload review images
            if (reviewImages.length > 0) {
                const imageUrls = await uploadReviewImages();
                reviewData.images = imageUrls;
            }
            
            // Upload review video
            if (reviewVideo && reviewVideo.length > 0) {
                const videoUrl = await uploadReviewVideo();
                reviewData.video = videoUrl;
            }
            
            // Save review
            await db.collection('reviews').add(reviewData);
            
            // Update product rating
            const productRef = db.collection('products').doc(selectedReviewProductId);
            const productDoc = await productRef.get();
            
            if (productDoc.exists) {
                const product = productDoc.data();
                const currentRating = product.rating || 0;
                const currentReviewsCount = product.reviewsCount || 0;
                
                const newRating = ((currentRating * currentReviewsCount) + starRating) / (currentReviewsCount + 1);
                
                await productRef.update({
                    rating: newRating,
                    reviewsCount: currentReviewsCount + 1,
                    updatedAt: new Date()
                });
            }
            
            closeModal('reviewModal');
            showToast('Review submitted successfully!', 'success');
            
            // Reset
            reviewImages = [];
            reviewVideo = null;
            selectedReviewProductId = null;
            starRating = 0;
            
        } catch (error) {
            console.error('Error submitting review:', error);
            showToast('Error submitting review: ' + error.message, 'error');
        }
    }

    async function uploadReviewImages() {
        const imageUrls = [];
        
        for (let i = 0; i < reviewImages.length; i++) {
            const file = reviewImages[i].file;
            const formData = new FormData();
            formData.append('file', file);
            formData.append('upload_preset', uploadPreset);
            formData.append('cloud_name', cloudName);
            
            try {
                const response = await fetch(`https://api.cloudinary.com/v1_1/${cloudName}/image/upload`, {
                    method: 'POST',
                    body: formData
                });
                
                const data = await response.json();
                if (data.secure_url) {
                    imageUrls.push(data.secure_url);
                }
            } catch (error) {
                console.error('Error uploading review image:', error);
            }
        }
        
        return imageUrls;
    }

    async function uploadReviewVideo() {
        if (!reviewVideo || reviewVideo.length === 0) return null;
        
        const file = reviewVideo[0].file;
        const formData = new FormData();
        formData.append('file', file);
        formData.append('upload_preset', uploadPreset);
        formData.append('cloud_name', cloudName);
        
        try {
            const response = await fetch(`https://api.cloudinary.com/v1_1/${cloudName}/video/upload`, {
                method: 'POST',
                body: formData
            });
            
            const data = await response.json();
            return data.secure_url;
        } catch (error) {
            console.error('Error uploading review video:', error);
            return null;
        }
    }

    function messageSellerFromOrder(sellerId, orderId) {
        if (!currentUser) {
            showToast('Please login to message seller', 'error');
            return;
        }
        
        // Check if conversation exists
        db.collection('conversations')
            .where('buyerId', '==', currentUser.uid)
            .where('sellerId', '==', sellerId)
            .limit(1)
            .get()
            .then(snapshot => {
                if (snapshot.empty) {
                    // Create new conversation
                    return createConversationFromOrder(sellerId, orderId);
                } else {
                    // Show messages page
                    showMessagesPage();
                }
            })
            .catch(error => {
                console.error('Error checking conversation:', error);
                showToast('Error starting conversation', 'error');
            });
    }

    async function createConversationFromOrder(sellerId, orderId) {
        try {
            // Get seller info
            const sellerDoc = await db.collection('sellers').doc(sellerId).get();
            const sellerData = sellerDoc.exists ? sellerDoc.data() : {};
            
            const conversationData = {
                buyerId: currentUser.uid,
                buyerName: currentUserProfile?.displayName || currentUser.email,
                buyerEmail: currentUser.email,
                sellerId: sellerId,
                sellerName: sellerData.shopName || sellerData.name,
                orderId: orderId,
                lastMessage: 'Conversation started',
                lastMessageAt: new Date(),
                createdAt: new Date()
            };
            
            await db.collection('conversations').add(conversationData);
            
            showMessagesPage();
            showToast('Conversation started with seller', 'success');
            
        } catch (error) {
            console.error('Error creating conversation:', error);
            showToast('Error starting conversation', 'error');
        }
    }

    function showWishlist() {
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        const wishlistPage = document.getElementById('wishlistPage');
        wishlistPage.style.display = 'block';
        
        const wishlistContent = document.getElementById('wishlistContent');
        
        if (wishlistItems.length === 0) {
            wishlistContent.innerHTML = `
                <div class="section">
                    <div class="section-header">
                        <h2 class="section-title">My Wishlist</h2>
                        <button class="btn btn-secondary" onclick="showHomePage()">
                            <i class="fas fa-arrow-left"></i> Continue Shopping
                        </button>
                    </div>
                    
                    <div style="text-align: center; padding: 4rem;">
                        <i class="fas fa-heart" style="font-size: 4rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                        <h3>Your Wishlist is Empty</h3>
                        <p>Save your favorite products here</p>
                        <button class="btn btn-primary" onclick="showHomePage()" style="margin-top: 1rem;">
                            <i class="fas fa-shopping-bag"></i> Start Shopping
                        </button>
                    </div>
                </div>
            `;
            return;
        }
        
        wishlistContent.innerHTML = `
            <div class="section">
                <div class="section-header">
                    <h2 class="section-title">My Wishlist</h2>
                    <button class="btn btn-secondary" onclick="showHomePage()">
                        <i class="fas fa-arrow-left"></i> Continue Shopping
                    </button>
                </div>
                
                <div class="products-grid">
                    ${wishlistItems.map(item => `
                        <div class="product-card">
                            ${item.discount ? `<div class="product-badge">${item.discount}% OFF</div>` : ''}
                            <img src="${item.image || 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'}" 
                                 class="product-image" 
                                 alt="${escapeHtml(item.name)}"
                                 onclick="viewProductDetails('${item.id}')">
                            <div class="product-info">
                                <div class="product-category">${escapeHtml(item.category || '')}</div>
                                <div class="product-name" onclick="viewProductDetails('${item.id}')">${escapeHtml(item.name)}</div>
                                <div class="product-rating">
                                    ${generateStarRating(item.rating || 0)}
                                    <span style="color: var(--text-secondary); font-size: 0.9rem;">(${item.reviewsCount || 0})</span>
                                </div>
                                <div class="product-price">
                                    <span class="current-price">Rs. ${item.price?.toLocaleString() || '0'}</span>
                                    ${item.originalPrice ? `
                                        <span class="original-price">Rs. ${item.originalPrice?.toLocaleString()}</span>
                                    ` : ''}
                                </div>
                                <div class="product-seller">
                                    <i class="fas fa-store"></i> ${escapeHtml(item.sellerName || 'Seller')}
                                </div>
                                <div class="product-actions">
                                    <button class="add-to-cart" onclick="addToCart('${item.id}')">
                                        <i class="fas fa-shopping-cart"></i> Add to Cart
                                    </button>
                                    <button class="btn btn-danger" onclick="removeFromWishlist('${item.id}')">
                                        <i class="fas fa-trash"></i>
                                    </button>
                                </div>
                            </div>
                        </div>
                    `).join('')}
                </div>
            </div>
        `;
    }

    function generateStarRating(rating) {
        let stars = '';
        for (let i = 1; i <= 5; i++) {
            if (i <= Math.floor(rating)) {
                stars += '<i class="fas fa-star"></i>';
            } else if (i === Math.ceil(rating) && rating % 1 !== 0) {
                stars += '<i class="fas fa-star-half-alt"></i>';
            } else {
                stars += '<i class="far fa-star"></i>';
            }
        }
        return stars;
    }

    function addToWishlist(product) {
        if (!wishlistItems.find(item => item.id === product.id)) {
            wishlistItems.push({
                id: product.id,
                name: product.name,
                price: product.price,
                originalPrice: product.originalPrice || null,
                discount: product.discount || 0,
                image: product.images?.[0] || null,
                category: product.category,
                sellerName: product.sellerName,
                rating: product.rating || 0,
                reviewsCount: product.reviewsCount || 0
            });
            
            localStorage.setItem('wishlistItems', JSON.stringify(wishlistItems));
            showToast('Added to wishlist', 'success');
        } else {
            removeFromWishlist(product.id);
        }
    }

    function removeFromWishlist(productId) {
        wishlistItems = wishlistItems.filter(item => item.id !== productId);
        localStorage.setItem('wishlistItems', JSON.stringify(wishlistItems));
        showToast('Removed from wishlist', 'info');
        showWishlist();
    }

    function viewBuyerProfile() {
        if (!currentUser) {
            showToast('Please login to view profile', 'error');
            openAuthModal('buyerLogin');
            return;
        }
        
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        const profilePage = document.getElementById('buyerProfilePage');
        profilePage.style.display = 'block';
        
        const profileContent = document.getElementById('buyerProfileContent');
        profileContent.innerHTML = `
            <div class="section">
                <div class="section-header">
                    <h2 class="section-title">My Profile</h2>
                    <button class="btn btn-secondary" onclick="showHomePage()">
                        <i class="fas fa-arrow-left"></i> Back to Home
                    </button>
                </div>
                
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem;">
                    <div>
                        <div style="background: var(--white); border-radius: var(--radius); padding: 1.5rem; box-shadow: var(--shadow);">
                            <h3 style="margin-bottom: 1.5rem;">Profile Information</h3>
                            <form id="buyerProfileForm">
                                <div class="profile-field">
                                    <label>Full Name</label>
                                    <div class="field-value">${escapeHtml(currentUserProfile?.displayName || 'Not set')}</div>
                                </div>
                                <div class="profile-field">
                                    <label>Email Address</label>
                                    <div class="field-value">${escapeHtml(currentUser?.email || '')}</div>
                                </div>
                                <div class="profile-field">
                                    <label>Phone Number</label>
                                    <div class="field-value">${escapeHtml(currentUserProfile?.phone || 'Not set')}</div>
                                </div>
                                <div class="profile-field">
                                    <label>Address</label>
                                    <div class="field-value">${escapeHtml(currentUserProfile?.address || 'Not set')}</div>
                                </div>
                                <div class="profile-field">
                                    <label>City</label>
                                    <div class="field-value">${escapeHtml(currentUserProfile?.city || 'Not set')}</div>
                                </div>
                                <div class="profile-field">
                                    <label>Affiliate Balance</label>
                                    <div class="field-value" style="color: var(--primary); font-weight: bold;">
                                        Rs. ${affiliateBalance?.toFixed(2) || '0.00'}
                                    </div>
                                </div>
                                <div class="profile-field">
                                    <label>Referral Code</label>
                                    <div class="field-value" style="display: flex; justify-content: space-between; align-items: center;">
                                        <span style="font-family: monospace; font-weight: bold;">${referrerCode || 'Not set'}</span>
                                        <button type="button" class="btn btn-sm btn-info" onclick="copyReferralCode()">
                                            <i class="fas fa-copy"></i> Copy
                                        </button>
                                    </div>
                                </div>
                                <button type="button" class="btn btn-primary" style="margin-top: 1rem;" onclick="editBuyerProfile()">
                                    <i class="fas fa-edit"></i> Edit Profile
                                </button>
                            </form>
                        </div>
                    </div>
                    
                    <div>
                        <div style="background: var(--white); border-radius: var(--radius); padding: 1.5rem; box-shadow: var(--shadow);">
                            <h3 style="margin-bottom: 1.5rem;">Recent Activity</h3>
                            
                            <div style="margin-bottom: 1.5rem;">
                                <h4>Orders Summary</h4>
                                <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 1rem; margin-top: 1rem;">
                                    <div style="background: var(--accent); padding: 1rem; border-radius: var(--radius); text-align: center;">
                                        <div style="font-size: 1.5rem; font-weight: bold; color: var(--primary);">
                                            ${buyerOrders.length}
                                        </div>
                                        <div style="color: var(--text-secondary); font-size: 0.9rem;">Total Orders</div>
                                    </div>
                                    <div style="background: var(--accent); padding: 1rem; border-radius: var(--radius); text-align: center;">
                                        <div style="font-size: 1.5rem; font-weight: bold; color: var(--primary);">
                                            ${buyerOrders.filter(o => o.status === 'delivered').length}
                                        </div>
                                        <div style="color: var(--text-secondary); font-size: 0.9rem;">Delivered</div>
                                    </div>
                                </div>
                            </div>
                            
                            <div>
                                <h4>Quick Actions</h4>
                                <div style="display: grid; grid-template-columns: 1fr; gap: 0.5rem; margin-top: 1rem;">
                                    <button class="btn btn-secondary" onclick="showOrders()">
                                        <i class="fas fa-box"></i> View All Orders
                                    </button>
                                    <button class="btn btn-secondary" onclick="showWishlist()">
                                        <i class="fas fa-heart"></i> View Wishlist
                                    </button>
                                    <button class="btn btn-secondary" onclick="viewAddresses()">
                                        <i class="fas fa-map-marker-alt"></i> Manage Addresses
                                    </button>
                                    <button class="btn btn-secondary" onclick="viewSettings()">
                                        <i class="fas fa-cog"></i> Account Settings
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        `;
    }

    function copyReferralCode() {
        if (!referrerCode) return;
        
        navigator.clipboard.writeText(referrerCode)
            .then(() => showToast('Referral code copied to clipboard', 'success'))
            .catch(() => showToast('Failed to copy referral code', 'error'));
    }

    function editBuyerProfile() {
        const profileContent = document.getElementById('buyerProfileContent');
        profileContent.innerHTML = `
            <div class="section">
                <div class="section-header">
                    <h2 class="section-title">Edit Profile</h2>
                    <button class="btn btn-secondary" onclick="viewBuyerProfile()">
                        <i class="fas fa-arrow-left"></i> Back to Profile
                    </button>
                </div>
                
                <div style="background: var(--white); border-radius: var(--radius); padding: 2rem; box-shadow: var(--shadow); max-width: 600px; margin: 0 auto;">
                    <form id="editBuyerProfileForm">
                        <div class="form-group">
                            <label>Full Name *</label>
                            <input type="text" id="editName" class="form-control" value="${escapeHtml(currentUserProfile?.displayName || '')}" required>
                        </div>
                        <div class="form-group">
                            <label>Phone Number *</label>
                            <input type="tel" id="editPhone" class="form-control" value="${escapeHtml(currentUserProfile?.phone || '')}" required>
                        </div>
                        <div class="form-group">
                            <label>Address *</label>
                            <textarea id="editAddress" class="form-control" rows="3" required>${escapeHtml(currentUserProfile?.address || '')}</textarea>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label>City *</label>
                                <input type="text" id="editCity" class="form-control" value="${escapeHtml(currentUserProfile?.city || '')}" required>
                            </div>
                            <div class="form-group">
                                <label>Postal Code</label>
                                <input type="text" id="editPostalCode" class="form-control" value="${escapeHtml(currentUserProfile?.postalCode || '')}">
                            </div>
                        </div>
                        <div class="form-actions" style="margin-top: 2rem;">
                            <button type="button" class="btn btn-secondary" onclick="viewBuyerProfile()">
                                Cancel
                            </button>
                            <button type="submit" class="btn btn-primary">
                                <i class="fas fa-save"></i> Save Changes
                            </button>
                        </div>
                    </form>
                </div>
            </div>
        `;
        
        document.getElementById('editBuyerProfileForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            try {
                const updatedData = {
                    displayName: document.getElementById('editName').value.trim(),
                    phone: document.getElementById('editPhone').value.trim(),
                    address: document.getElementById('editAddress').value.trim(),
                    city: document.getElementById('editCity').value.trim(),
                    postalCode: document.getElementById('editPostalCode').value.trim() || '',
                    updatedAt: new Date()
                };
                
                await db.collection('users').doc(currentUser.uid).update(updatedData);
                
                // Update current user profile
                currentUserProfile = { ...currentUserProfile, ...updatedData };
                
                showToast('Profile updated successfully', 'success');
                viewBuyerProfile();
                
            } catch (error) {
                console.error('Error updating profile:', error);
                showToast('Error updating profile', 'error');
            }
        });
    }

    function viewAddresses() {
        if (!currentUser) {
            showToast('Please login to view addresses', 'error');
            openAuthModal('buyerLogin');
            return;
        }
        
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        const addressesPage = document.getElementById('addressesPage');
        addressesPage.style.display = 'block';
        
        const addressesContent = document.getElementById('addressesContent');
        addressesContent.innerHTML = `
            <div class="section">
                <div class="section-header">
                    <h2 class="section-title">My Addresses</h2>
                    <button class="btn btn-secondary" onclick="viewBuyerProfile()">
                        <i class="fas fa-arrow-left"></i> Back to Profile
                    </button>
                </div>
                
                <div style="background: var(--white); border-radius: var(--radius); padding: 2rem; box-shadow: var(--shadow);">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 2rem;">
                        <h3>Saved Addresses</h3>
                        <button class="btn btn-primary" onclick="addNewAddress()">
                            <i class="fas fa-plus"></i> Add New Address
                        </button>
                    </div>
                    
                    ${currentUserProfile?.address ? `
                        <div style="background: var(--accent); border-radius: var(--radius); padding: 1.5rem; margin-bottom: 1rem; border: 2px solid var(--primary);">
                            <div style="display: flex; justify-content: space-between; align-items: flex-start;">
                                <div>
                                    <h4>Primary Address</h4>
                                    <p style="margin-top: 0.5rem;">
                                        <strong>${escapeHtml(currentUserProfile.displayName || '')}</strong><br>
                                        ${escapeHtml(currentUserProfile.address)}<br>
                                        ${escapeHtml(currentUserProfile.city)}<br>
                                        Phone: ${escapeHtml(currentUserProfile.phone || '')}
                                    </p>
                                </div>
                                <div>
                                    <button class="btn btn-sm btn-primary" onclick="editPrimaryAddress()">
                                        <i class="fas fa-edit"></i> Edit
                                    </button>
                                </div>
                            </div>
                        </div>
                    ` : `
                        <div style="text-align: center; padding: 2rem; color: var(--text-secondary);">
                            <i class="fas fa-map-marker-alt" style="font-size: 3rem; margin-bottom: 1rem;"></i>
                            <h4>No Addresses Saved</h4>
                            <p>Add your first address for faster checkout</p>
                        </div>
                    `}
                </div>
            </div>
        `;
    }

    function addNewAddress() {
        const addressesContent = document.getElementById('addressesContent');
        addressesContent.innerHTML = `
            <div class="section">
                <div class="section-header">
                    <h2 class="section-title">Add New Address</h2>
                    <button class="btn btn-secondary" onclick="viewAddresses()">
                        <i class="fas fa-arrow-left"></i> Back to Addresses
                    </button>
                </div>
                
                <div style="background: var(--white); border-radius: var(--radius); padding: 2rem; box-shadow: var(--shadow); max-width: 600px; margin: 0 auto;">
                    <form id="newAddressForm">
                        <div class="form-group">
                            <label>Address Label (e.g., Home, Office)</label>
                            <input type="text" id="addressLabel" class="form-control" placeholder="Home" required>
                        </div>
                        <div class="form-group">
                            <label>Full Name *</label>
                            <input type="text" id="addressName" class="form-control" value="${escapeHtml(currentUserProfile?.displayName || '')}" required>
                        </div>
                        <div class="form-group">
                            <label>Phone Number *</label>
                            <input type="tel" id="addressPhone" class="form-control" value="${escapeHtml(currentUserProfile?.phone || '')}" required>
                        </div>
                        <div class="form-group">
                            <label>Address *</label>
                            <textarea id="addressFull" class="form-control" rows="3" placeholder="House #, Street, Area" required></textarea>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label>City *</label>
                                <input type="text" id="addressCity" class="form-control" value="${escapeHtml(currentUserProfile?.city || '')}" required>
                            </div>
                            <div class="form-group">
                                <label>Postal Code</label>
                                <input type="text" id="addressPostalCode" class="form-control">
                            </div>
                        </div>
                        <div class="form-group">
                            <label>Additional Instructions (Optional)</label>
                            <textarea id="addressInstructions" class="form-control" rows="2" placeholder="Delivery instructions..."></textarea>
                        </div>
                        <div class="form-actions" style="margin-top: 2rem;">
                            <button type="button" class="btn btn-secondary" onclick="viewAddresses()">
                                Cancel
                            </button>
                            <button type="submit" class="btn btn-primary">
                                <i class="fas fa-save"></i> Save Address
                            </button>
                        </div>
                    </form>
                </div>
            </div>
        `;
        
        document.getElementById('newAddressForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            try {
                // Save as primary address for now (extend to multiple addresses later)
                const addressData = {
                    label: document.getElementById('addressLabel').value.trim(),
                    name: document.getElementById('addressName').value.trim(),
                    phone: document.getElementById('addressPhone').value.trim(),
                    address: document.getElementById('addressFull').value.trim(),
                    city: document.getElementById('addressCity').value.trim(),
                    postalCode: document.getElementById('addressPostalCode').value.trim() || '',
                    instructions: document.getElementById('addressInstructions').value.trim() || '',
                    isPrimary: true
                };
                
                await db.collection('users').doc(currentUser.uid).update({
                    displayName: addressData.name,
                    phone: addressData.phone,
                    address: addressData.address,
                    city: addressData.city,
                    postalCode: addressData.postalCode,
                    updatedAt: new Date()
                });
                
                currentUserProfile = { ...currentUserProfile, ...addressData };
                
                showToast('Address saved successfully', 'success');
                viewAddresses();
                
            } catch (error) {
                console.error('Error saving address:', error);
                showToast('Error saving address', 'error');
            }
        });
    }

    function editPrimaryAddress() {
        addNewAddress();
    }

    function viewSettings() {
        if (!currentUser) {
            showToast('Please login to view settings', 'error');
            openAuthModal('buyerLogin');
            return;
        }
        
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        const settingsPage = document.getElementById('settingsPage');
        settingsPage.style.display = 'block';
        
        const settingsContent = document.getElementById('settingsContent');
        settingsContent.innerHTML = `
            <div class="section">
                <div class="section-header">
                    <h2 class="section-title">Account Settings</h2>
                    <button class="btn btn-secondary" onclick="viewBuyerProfile()">
                        <i class="fas fa-arrow-left"></i> Back to Profile
                    </button>
                </div>
                
                <div style="background: var(--white); border-radius: var(--radius); padding: 2rem; box-shadow: var(--shadow);">
                    <div class="settings-tabs">
                        <div class="settings-tab active" onclick="switchSettingsTab('account')">Account</div>
                        <div class="settings-tab" onclick="switchSettingsTab('security')">Security</div>
                        <div class="settings-tab" onclick="switchSettingsTab('notifications')">Notifications</div>
                        <div class="settings-tab" onclick="switchSettingsTab('privacy')">Privacy</div>
                    </div>
                    
                    <div class="settings-content" id="settingsTabsContent">
                        <div id="accountTab" class="settings-tab-content active">
                            <h3>Account Settings</h3>
                            <form id="accountSettingsForm">
                                <div class="form-group">
                                    <label>Email Address</label>
                                    <input type="email" class="form-control" value="${escapeHtml(currentUser?.email || '')}" disabled>
                                </div>
                                <div class="form-group">
                                    <label>Account Type</label>
                                    <input type="text" class="form-control" value="${currentSeller ? 'Seller Account' : 'Buyer Account'}" disabled>
                                </div>
                                <div class="form-group">
                                    <label>Account Created</label>
                                    <input type="text" class="form-control" value="${currentUser?.metadata?.creationTime ? new Date(currentUser.metadata.creationTime).toLocaleDateString() : 'N/A'}" disabled>
                                </div>
                                <button type="button" class="btn btn-primary" onclick="requestAccountDeletion()">
                                    <i class="fas fa-trash"></i> Request Account Deletion
                                </button>
                            </form>
                        </div>
                        
                        <div id="securityTab" class="settings-tab-content">
                            <h3>Security Settings</h3>
                            <form id="securitySettingsForm">
                                <div class="form-group">
                                    <label>Change Password</label>
                                    <div class="password-input">
                                        <input type="password" id="currentPassword" class="form-control" placeholder="Current password">
                                    </div>
                                </div>
                                <div class="form-group">
                                    <div class="password-input">
                                        <input type="password" id="newPassword" class="form-control" placeholder="New password">
                                    </div>
                                </div>
                                <div class="form-group">
                                    <div class="password-input">
                                        <input type="password" id="confirmPassword" class="form-control" placeholder="Confirm new password">
                                    </div>
                                </div>
                                <button type="submit" class="btn btn-primary">
                                    <i class="fas fa-key"></i> Change Password
                                </button>
                            </form>
                            
                            <div style="margin-top: 2rem;">
                                <h4>Two-Factor Authentication</h4>
                                <p style="color: var(--text-secondary);">Add an extra layer of security to your account</p>
                                <button class="btn btn-secondary">
                                    <i class="fas fa-shield-alt"></i> Enable 2FA
                                </button>
                            </div>
                        </div>
                        
                        <div id="notificationsTab" class="settings-tab-content">
                            <h3>Notification Settings</h3>
                            <form id="notificationSettingsForm">
                                <div class="form-group">
                                    <label style="display: flex; justify-content: space-between; align-items: center;">
                                        <span>Email Notifications</span>
                                        <input type="checkbox" id="emailNotifications" checked>
                                    </label>
                                </div>
                                <div class="form-group">
                                    <label style="display: flex; justify-content: space-between; align-items: center;">
                                        <span>SMS Notifications</span>
                                        <input type="checkbox" id="smsNotifications">
                                    </label>
                                </div>
                                <div class="form-group">
                                    <label style="display: flex; justify-content: space-between; align-items: center;">
                                        <span>Order Updates</span>
                                        <input type="checkbox" id="orderNotifications" checked>
                                    </label>
                                </div>
                                <div class="form-group">
                                    <label style="display: flex; justify-content: space-between; align-items: center;">
                                        <span>Promotional Offers</span>
                                        <input type="checkbox" id="promoNotifications" checked>
                                    </label>
                                </div>
                                <button type="submit" class="btn btn-primary">
                                    <i class="fas fa-save"></i> Save Settings
                                </button>
                            </form>
                        </div>
                        
                        <div id="privacyTab" class="settings-tab-content">
                            <h3>Privacy Settings</h3>
                            <form id="privacySettingsForm">
                                <div class="form-group">
                                    <label style="display: flex; justify-content: space-between; align-items: center;">
                                        <span>Show my profile to other users</span>
                                        <input type="checkbox" id="showProfile" checked>
                                    </label>
                                </div>
                                <div class="form-group">
                                    <label style="display: flex; justify-content: space-between; align-items: center;">
                                        <span>Allow messaging from other users</span>
                                        <input type="checkbox" id="allowMessages" checked>
                                    </label>
                                </div>
                                <div class="form-group">
                                    <label style="display: flex; justify-content: space-between; align-items: center;">
                                        <span>Show my reviews publicly</span>
                                        <input type="checkbox" id="showReviews" checked>
                                    </label>
                                </div>
                                <div class="form-group">
                                    <label style="display: flex; justify-content: space-between; align-items: center;">
                                        <span>Share my data for analytics</span>
                                        <input type="checkbox" id="shareData">
                                    </label>
                                </div>
                                <button type="submit" class="btn btn-primary">
                                    <i class="fas fa-save"></i> Save Settings
                                </button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        `;
        
        // Add event listeners for settings forms
        setupSettingsForms();
    }

    function switchSettingsTab(tabName) {
        document.querySelectorAll('.settings-tab').forEach(tab => {
            tab.classList.remove('active');
        });
        
        document.querySelectorAll('.settings-tab-content').forEach(content => {
            content.classList.remove('active');
        });
        
        document.querySelector(`.settings-tab:nth-child(${['account', 'security', 'notifications', 'privacy'].indexOf(tabName) + 1})`).classList.add('active');
        document.getElementById(`${tabName}Tab`).classList.add('active');
    }

    function setupSettingsForms() {
        // Security form
        const securityForm = document.getElementById('securitySettingsForm');
        if (securityForm) {
            securityForm.addEventListener('submit', async function(e) {
                e.preventDefault();
                
                const currentPassword = document.getElementById('currentPassword').value;
                const newPassword = document.getElementById('newPassword').value;
                const confirmPassword = document.getElementById('confirmPassword').value;
                
                if (newPassword !== confirmPassword) {
                    showToast('New passwords do not match', 'error');
                    return;
                }
                
                try {
                    const user = auth.currentUser;
                    const credential = firebase.auth.EmailAuthProvider.credential(user.email, currentPassword);
                    
                    await user.reauthenticateWithCredential(credential);
                    await user.updatePassword(newPassword);
                    
                    showToast('Password updated successfully', 'success');
                    securityForm.reset();
                    
                } catch (error) {
                    console.error('Error updating password:', error);
                    showToast('Error updating password: ' + error.message, 'error');
                }
            });
        }
        
        // Notification settings
        const notificationForm = document.getElementById('notificationSettingsForm');
        if (notificationForm) {
            notificationForm.addEventListener('submit', async function(e) {
                e.preventDefault();
                
                const settings = {
                    email: document.getElementById('emailNotifications').checked,
                    sms: document.getElementById('smsNotifications').checked,
                    orders: document.getElementById('orderNotifications').checked,
                    promotions: document.getElementById('promoNotifications').checked,
                    updatedAt: new Date()
                };
                
                try {
                    await db.collection('user_settings').doc(currentUser.uid).set(settings, { merge: true });
                    showToast('Notification settings saved', 'success');
                } catch (error) {
                    console.error('Error saving notification settings:', error);
                    showToast('Error saving settings', 'error');
                }
            });
        }
        
        // Privacy settings
        const privacyForm = document.getElementById('privacySettingsForm');
        if (privacyForm) {
            privacyForm.addEventListener('submit', async function(e) {
                e.preventDefault();
                
                const settings = {
                    showProfile: document.getElementById('showProfile').checked,
                    allowMessages: document.getElementById('allowMessages').checked,
                    showReviews: document.getElementById('showReviews').checked,
                    shareData: document.getElementById('shareData').checked,
                    updatedAt: new Date()
                };
                
                try {
                    await db.collection('user_privacy').doc(currentUser.uid).set(settings, { merge: true });
                    showToast('Privacy settings saved', 'success');
                } catch (error) {
                    console.error('Error saving privacy settings:', error);
                    showToast('Error saving settings', 'error');
                }
            });
        }
    }

    function requestAccountDeletion() {
        if (confirm('Are you sure you want to request account deletion? This action cannot be undone.')) {
            showToast('Account deletion request submitted. Our team will contact you shortly.', 'info');
        }
    }

    function showMessagesPage() {
        if (!currentUser) {
            showToast('Please login to view messages', 'error');
            openAuthModal('buyerLogin');
            return;
        }
        
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        const messagesPage = document.getElementById('messagesPage');
        messagesPage.style.display = 'block';
        
        loadBuyerMessages();
    }

    async function loadBuyerMessages() {
        if (!currentUser) return;
        
        const messagesContent = document.getElementById('messagesContent');
        messagesContent.innerHTML = `
            <div class="section">
                <div class="section-header">
                    <h2 class="section-title">Messages</h2>
                    <button class="btn btn-secondary" onclick="showHomePage()">
                        <i class="fas fa-arrow-left"></i> Back to Home
                    </button>
                </div>
                
                <div class="message-system">
                    <div class="chat-container">
                        <div class="chat-sidebar">
                            <div class="chat-list" id="buyerChatList">
                                <!-- Conversations will be loaded here -->
                            </div>
                        </div>
                        <div class="chat-content">
                            <div class="chat-header" id="buyerChatHeader">
                                <p>Select a conversation to start messaging</p>
                            </div>
                            <div class="chat-messages" id="buyerChatMessages">
                                <!-- Messages will be loaded here -->
                            </div>
                            <div class="chat-input">
                                <input type="text" id="buyerMessageInput" placeholder="Type your message..." disabled>
                                <button class="btn btn-primary" id="buyerSendMessageBtn" disabled>
                                    <i class="fas fa-paper-plane"></i>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        `;
        
        try {
            // Load conversations
            const snapshot = await db.collection('conversations')
                .where('buyerId', '==', currentUser.uid)
                .orderBy('lastMessageAt', 'desc')
                .get();
            
            const chatList = document.getElementById('buyerChatList');
            
            if (snapshot.empty) {
                chatList.innerHTML = `
                    <div style="text-align: center; padding: 2rem; color: var(--text-secondary);">
                        <i class="fas fa-comments" style="font-size: 2rem; margin-bottom: 1rem;"></i>
                        <p>No conversations yet</p>
                    </div>
                `;
                return;
            }
            
            chatList.innerHTML = snapshot.docs.map(doc => {
                const conversation = doc.data();
                const lastMessageDate = conversation.lastMessageAt?.toDate ? 
                    conversation.lastMessageAt.toDate() : new Date(conversation.lastMessageAt);
                
                return `
                    <div class="chat-item" onclick="loadBuyerConversation('${doc.id}')">
                        <strong>${escapeHtml(conversation.sellerName || 'Seller')}</strong>
                        <p style="color: var(--text-secondary); font-size: 0.9rem; margin-top: 0.25rem;">
                            ${conversation.lastMessage?.substring(0, 50) || 'No messages yet'}...
                        </p>
                        <small style="color: var(--text-secondary);">${lastMessageDate.toLocaleDateString()}</small>
                    </div>
                `;
            }).join('');
            
            // Add event listeners for messaging
            document.getElementById('buyerSendMessageBtn').addEventListener('click', sendBuyerMessage);
            document.getElementById('buyerMessageInput').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    sendBuyerMessage();
                }
            });
            
        } catch (error) {
            console.error('Error loading buyer messages:', error);
            showToast('Error loading messages', 'error');
        }
    }

    async function loadBuyerConversation(conversationId) {
        if (!currentUser) return;
        
        try {
            const conversationDoc = await db.collection('conversations').doc(conversationId).get();
            if (!conversationDoc.exists) return;
            
            const conversation = conversationDoc.data();
            currentChatId = conversationId;
            
            // Load messages
            const messagesSnapshot = await db.collection('messages')
                .where('conversationId', '==', conversationId)
                .orderBy('timestamp', 'asc')
                .get();
            
            messages = messagesSnapshot.docs.map(doc => ({
                id: doc.id,
                ...doc.data()
            }));
            
            // Update chat header
            document.getElementById('buyerChatHeader').innerHTML = `
                <h4>${escapeHtml(conversation.sellerName || 'Seller')}</h4>
                <p style="color: var(--text-secondary); font-size: 0.9rem;">
                    ${conversation.orderId ? `Order #${conversation.orderId.slice(-8)}` : ''}
                </p>
            `;
            
            // Display messages
            const chatMessages = document.getElementById('buyerChatMessages');
            chatMessages.innerHTML = messages.map(msg => `
                <div class="message ${msg.senderId === currentUser.uid ? 'sent' : 'received'}">
                    <p>${escapeHtml(msg.content)}</p>
                    <small style="display: block; margin-top: 0.25rem; opacity: 0.7;">
                        ${msg.senderId === currentUser.uid ? 'You' : msg.senderName} • 
                        ${msg.timestamp?.toDate ? msg.timestamp.toDate().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'}) : ''}
                    </small>
                </div>
            `).join('');
            
            // Scroll to bottom
            chatMessages.scrollTop = chatMessages.scrollHeight;
            
            // Enable message input
            document.getElementById('buyerMessageInput').disabled = false;
            document.getElementById('buyerSendMessageBtn').disabled = false;
            
        } catch (error) {
            console.error('Error loading conversation:', error);
            showToast('Error loading conversation', 'error');
        }
    }

    async function sendBuyerMessage() {
        if (!currentUser || !currentChatId) return;
        
        const messageInput = document.getElementById('buyerMessageInput');
        const message = messageInput.value.trim();
        
        if (!message) return;
        
        try {
            const messageData = {
                conversationId: currentChatId,
                senderId: currentUser.uid,
                senderName: currentUserProfile?.displayName || currentUser.email,
                receiverId: '', // Will be populated from conversation
                content: message,
                timestamp: new Date(),
                read: false
            };
            
            // Save message
            await db.collection('messages').add(messageData);
            
            // Update conversation last message
            await db.collection('conversations').doc(currentChatId).update({
                lastMessage: message,
                lastMessageAt: new Date()
            });
            
            // Clear input
            messageInput.value = '';
            
            // Reload conversation
            loadBuyerConversation(currentChatId);
            
        } catch (error) {
            console.error('Error sending message:', error);
            showToast('Error sending message', 'error');
        }
    }

    function showSearchResultsPage() {
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        const searchPage = document.getElementById('searchResultsPage');
        searchPage.style.display = 'block';
    }
    
    
    

// ==================== PRODUCT FUNCTIONS ====================
let isProductPageActive = false;
let productMediaArray = [];
let activeVideos = new Set();

// Function to view product details - UPDATED TO FIX OPENING ISSUE
function viewProductDetails(productId) {
    // Cleanup any existing product page
    cleanupProductPage();
    isProductPageActive = true;
    
    // 1. Find product - improved search logic
    let product = null;
    
    // Search in main products array
    product = products.find(p => p.id === productId);
    
    // If not found, check if it's in seller products
    if (!product && window.sellerProducts) {
        product = window.sellerProducts.find(p => p.id === productId);
    }
    
    // Safety check
    if (!product) {
        console.error('Product not found:', productId);
        showToast('Product data is still loading...', 'info');
        isProductPageActive = false;
        return;
    }
    
    selectedProductId = productId;
    
    // 2. Hide other pages properly
    hideAllPages();
    
    const detailsPage = document.getElementById('productDetailsPage');
    const detailsContent = document.getElementById('productDetailsContent');
    
    // Ensure product details page exists and is visible
    if (!detailsPage) {
        console.error('Product details page element not found!');
        showToast('Page loading error', 'error');
        return;
    }
    
    // Clear previous content and show loading
    detailsContent.innerHTML = `
        <div style="text-align:center; padding:5rem; background: var(--white); border-radius: var(--radius);">
            <i class="fas fa-spinner fa-spin fa-2x" style="color: var(--primary);"></i>
            <p style="margin-top: 1rem;">Loading product details...</p>
        </div>
    `;
    
    detailsPage.style.display = 'block';
    window.scrollTo(0, 0);

    // Check for active flash sale
    const activeFlashSale = (typeof flashSales !== 'undefined') ? 
        flashSales.find(fs => fs.productId === productId) : null;
    
    let safePrice = product.price || 0;
    let isFlashSale = false;

    if (activeFlashSale) {
        safePrice = activeFlashSale.flashPrice || safePrice;
        isFlashSale = true;
    } else if (product.discount && product.discount > 0) {
        safePrice = product.price * (1 - product.discount / 100);
    }
    
    // Handle product images
    const safeImages = Array.isArray(product.images) ? product.images : 
        (product.image ? [product.image] : []);
    const safeDescription = product.description || 'No description available for this product.';
    
    // Build media array
    productMediaArray = [];
    
    // Add video first if available
    if (product.video) {
        productMediaArray.push({ 
            type: 'video', 
            src: product.video,
            id: `video-${Date.now()}-${Math.random().toString(36).substr(2, 9)}`
        });
    }
    
    // Add images after video
    if (safeImages.length > 0) {
        safeImages.forEach((img, index) => {
            productMediaArray.push({ 
                type: 'image', 
                src: img,
                id: `image-${index}`
            });
        });
    } else if (productMediaArray.length === 0) {
        // Add placeholder if no media
        productMediaArray.push({ 
            type: 'image', 
            src: 'https://via.placeholder.com/400?text=No+Image+Available',
            id: 'placeholder'
        });
    }
    
    currentMediaIndex = 0;
    
    // Create product details HTML
    setTimeout(() => {
        detailsContent.innerHTML = createProductDetailsHTML(product, safePrice, isFlashSale, safeDescription, safeImages);
        
        // Initialize video players
        setTimeout(() => {
            initializeVideoPlayers();
            updateQuantityButtons();
            setupPageCleanup();
            
            // Load related products from same category
            loadRelatedProducts(product.category || 'General');
        }, 100);
    }, 300);
}

// Function to create product details HTML
function createProductDetailsHTML(product, safePrice, isFlashSale, safeDescription, safeImages) {
    const originalPrice = product.originalPrice || product.price || 0;
    const discountPercentage = isFlashSale ? 
        Math.round(((originalPrice - safePrice) / originalPrice) * 100) :
        (product.discount || 0);
    
    return `
        <div class="section">
            <div style="display: flex; gap: 1rem; margin-bottom: 1.5rem; flex-wrap: wrap; align-items: center;">
                <button class="btn btn-secondary" onclick="goBackFromProductDetails()">
                    <i class="fas fa-arrow-left"></i> Back
                </button>
                <div style="flex: 1;">
                    <nav style="font-size: 0.9rem; color: var(--text-secondary);">
                        <a href="#" onclick="showHomePage()" style="color: var(--primary); text-decoration: none;">Home</a> 
                        <i class="fas fa-chevron-right" style="margin: 0 8px; font-size: 0.8rem;"></i>
                        <a href="#" onclick="filterProductsByCategory('${product.category || 'General'}')" style="color: var(--primary); text-decoration: none;">
                            ${product.category || 'General'}
                        </a>
                        <i class="fas fa-chevron-right" style="margin: 0 8px; font-size: 0.8rem;"></i>
                        <span>${product.name || 'Product'}</span>
                    </nav>
                </div>
            </div>
            
            <div class="product-details-grid">
                <!-- Left Column: Product Media -->
                <div class="product-media-section">
                    <div class="product-media-slider" id="productMediaSlider">
                        <div class="slider-media-container" id="sliderMediaContainer">
                            ${productMediaArray.map((media, index) => `
                                <div class="slider-media ${index === 0 ? 'active' : ''}" 
                                     data-media-type="${media.type}"
                                     data-index="${index}"
                                     data-media-id="${media.id}">
                                    ${media.type === 'image' ? `
                                        <img src="${media.src}" class="slider-media-item" 
                                             alt="Product Image ${index + 1}" onclick="zoomMedia('${media.src}')"
                                             loading="lazy" style="cursor: zoom-in;">
                                    ` : `
                                        <div class="video-wrapper">
                                            <video class="slider-media-item video-player" 
                                                   id="${media.id}"
                                                   playsinline
                                                   webkit-playsinline
                                                   preload="metadata"
                                                   disablePictureInPicture
                                                   controlsList="nodownload">
                                                <source src="${media.src}" type="video/mp4">
                                                Your browser does not support the video tag.
                                            </video>
                                            <div class="video-controls">
                                                <button class="video-control-btn play-pause-btn" onclick="toggleVideoPlayback('${media.id}')">
                                                    <i class="fas fa-play"></i>
                                                </button>
                                                <button class="video-control-btn fullscreen-btn" onclick="toggleFullscreen('${media.id}')">
                                                    <i class="fas fa-expand"></i>
                                                </button>
                                            </div>
                                            <div class="video-play-overlay" id="overlay-${media.id}" onclick="toggleVideoPlayback('${media.id}')">
                                                <i class="fas fa-play"></i>
                                            </div>
                                        </div>
                                    `}
                                </div>
                            `).join('')}
                        </div>
                        
                        ${productMediaArray.length > 1 ? `
                            <div class="slider-controls">
                                <button class="slider-btn prev" onclick="previousMedia()" aria-label="Previous media">
                                    <i class="fas fa-chevron-left"></i>
                                </button>
                                <button class="slider-btn next" onclick="nextMedia()" aria-label="Next media">
                                    <i class="fas fa-chevron-right"></i>
                                </button>
                            </div>
                            
                            <div class="slider-nav" id="sliderNav">
                                ${productMediaArray.map((media, index) => `
                                    <button class="slider-dot ${index === 0 ? 'active' : ''}" 
                                            onclick="goToMedia(${index})" 
                                            aria-label="Go to ${media.type} ${index + 1}"
                                            title="${media.type === 'video' ? 'Video' : 'Image'}">
                                        <i class="fas ${media.type === 'video' ? 'fa-video' : 'fa-image'}"></i>
                                    </button>
                                `).join('')}
                            </div>
                            
                            <div class="media-counter" id="mediaCounter" aria-live="polite">
                                1 / ${productMediaArray.length}
                            </div>
                        ` : ''}
                    </div>
                    
                    ${productMediaArray.length > 1 ? `
                        <div class="media-thumbnails" id="mediaThumbnails">
                            ${productMediaArray.map((media, index) => `
                                <button class="thumbnail-btn ${index === 0 ? 'active' : ''}" 
                                        onclick="goToMedia(${index})"
                                        aria-label="View ${media.type} ${index + 1}">
                                    ${media.type === 'image' ? `
                                        <img src="${media.src}" alt="Thumbnail ${index + 1}" loading="lazy">
                                    ` : `
                                        <div class="video-thumbnail">
                                            <i class="fas fa-play"></i>
                                            <span>Video</span>
                                        </div>
                                    `}
                                </button>
                            `).join('')}
                        </div>
                    ` : ''}
                </div>
                
                <!-- Right Column: Product Info -->
                <div class="product-info-section">
                    <div class="product-header">
                        <h1 class="product-title">${escapeHtml(product.name || 'Unnamed Product')}</h1>
                        <div class="product-category">
                            <i class="fas fa-tag"></i> ${escapeHtml(product.category || 'General')}
                            ${product.brand ? ` | <i class="fas fa-trademark"></i> ${escapeHtml(product.brand)}` : ''}
                        </div>
                        <div class="product-rating">
                            <div class="stars">
                                ${'<i class="fas fa-star"></i>'.repeat(5)}
                            </div>
                            <span class="rating-count">(${product.reviewCount || 0} reviews)</span>
                            <span style="margin-left: 10px; color: var(--text-secondary);">
                                <i class="fas fa-eye"></i> ${product.views || 0} views
                            </span>
                        </div>
                    </div>
                    
                    <div class="price-availability-card">
                        <div class="price-section">
                            <span class="current-price" style="${isFlashSale ? 'color: #e74c3c;' : ''}">
                                Rs. ${safePrice.toLocaleString()}
                            </span>
                            ${originalPrice > safePrice ? `
                                <span class="original-price">Rs. ${originalPrice.toLocaleString()}</span>
                                <span class="discount-badge" style="${isFlashSale ? 'background: #e74c3c;' : 'background: var(--primary);'}">
                                    ${isFlashSale ? 'FLASH SALE' : `-${discountPercentage}%`}
                                </span>
                            ` : ''}
                        </div>
                        
                        <div class="availability-section">
                            <span class="availability-label">Availability:</span>
                            <span class="availability-status ${product.quantity > 0 ? 'in-stock' : 'out-of-stock'}">
                                <i class="fas ${product.quantity > 0 ? 'fa-check-circle' : 'fa-times-circle'}"></i> 
                                ${product.quantity > 0 ? `In Stock (${product.quantity} available)` : 'Out of Stock'}
                            </span>
                        </div>
                        
                        ${product.deliveryInfo ? `
                            <div class="delivery-info">
                                <i class="fas fa-shipping-fast"></i>
                                <span>${product.deliveryInfo}</span>
                            </div>
                        ` : `
                            <div class="delivery-info">
                                <i class="fas fa-shipping-fast"></i>
                                <span>Free shipping on orders over Rs. 2000</span>
                            </div>
                        `}
                    </div>
                    
                    ${product.quantity > 0 ? `
                        <div class="add-to-cart-section">
                            <div class="quantity-controls">
                                <button id="decreaseQty" class="qty-btn" onclick="changeProductQuantity(-1)" 
                                        aria-label="Decrease quantity">
                                    <i class="fas fa-minus"></i>
                                </button>
                                <input type="number" id="productQuantity" value="1" min="1" max="${product.quantity}" 
                                       aria-label="Product quantity" class="qty-input">
                                <button id="increaseQty" class="qty-btn" onclick="changeProductQuantity(1)" 
                                        aria-label="Increase quantity">
                                    <i class="fas fa-plus"></i>
                                </button>
                            </div>
                            <button class="btn btn-primary add-to-cart-btn" onclick="addToCartFromDetails('${product.id}')">
                                <i class="fas fa-shopping-cart"></i> Add to Cart
                            </button>
                            <button class="btn btn-warning buy-now-btn" onclick="buyNow('${product.id}')">
                                <i class="fas fa-bolt"></i> Buy Now
                            </button>
                        </div>
                    ` : `
                        <div class="out-of-stock-notice">
                            <i class="fas fa-bell"></i>
                            <span>This product is currently out of stock</span>
                            <button class="btn btn-secondary btn-sm" onclick="notifyWhenAvailable('${product.id}')">
                                Notify Me
                            </button>
                        </div>
                    `}
                    
                    <div class="action-buttons">
                        <button class="action-btn" onclick="addToWishlist('${product.id}')" id="wishlistBtn${product.id}">
                            <i class="far fa-heart"></i> Add to Wishlist
                        </button>
                        <button class="action-btn" onclick="shareProduct('${product.id}')">
                            <i class="fas fa-share-alt"></i> Share
                        </button>
                        ${product.sellerId ? `
                            <button class="action-btn" onclick="messageSellerFromProduct('${product.sellerId}', '${product.id}')">
                                <i class="fas fa-comment"></i> Contact Seller
                            </button>
                        ` : ''}
                        <button class="action-btn" onclick="reportProduct('${product.id}')">
                            <i class="fas fa-flag"></i> Report
                        </button>
                    </div>
                    
                    <!-- Product Highlights -->
                    ${product.highlights ? `
                        <div class="product-highlights">
                            <h3><i class="fas fa-star"></i> Product Highlights</h3>
                            <ul>
                                ${Array.isArray(product.highlights) ? 
                                    product.highlights.map(h => `<li>${escapeHtml(h)}</li>`).join('') :
                                    `<li>${escapeHtml(product.highlights)}</li>`
                                }
                            </ul>
                        </div>
                    ` : ''}
                    
                    <div class="product-description-section">
                        <h3><i class="fas fa-align-left"></i> Product Description</h3>
                        <div class="description-content">
                            <p>${escapeHtml(safeDescription)}</p>
                        </div>
                    </div>
                    
                    ${product.specifications ? `
                        <div class="product-specs">
                            <h3><i class="fas fa-list-alt"></i> Specifications</h3>
                            <div class="specs-grid">
                                ${Object.entries(product.specifications).map(([key, value]) => `
                                    <div class="spec-item">
                                        <span class="spec-key">${escapeHtml(key)}</span>
                                        <span class="spec-value">${escapeHtml(value)}</span>
                                    </div>
                                `).join('')}
                            </div>
                        </div>
                    ` : ''}
                    
                    <!-- Seller Info -->
                    ${product.sellerId ? `
                        <div class="seller-info-card">
                            <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                                <div style="width: 50px; height: 50px; background: var(--primary); border-radius: 50%; 
                                      display: flex; align-items: center; justify-content: center; color: white;">
                                    <i class="fas fa-store"></i>
                                </div>
                                <div>
                                    <h4 style="margin: 0; color: var(--primary);">
                                        ${escapeHtml(product.sellerName || 'Official Store')}
                                    </h4>
                                    <p style="color: var(--text-secondary); font-size: 0.9rem; margin: 5px 0 0;">
                                        Seller Rating: 4.5/5 | 95% Positive Feedback
                                    </p>
                                </div>
                            </div>
                            <div style="display: flex; gap: 1rem;">
                                <button class="btn btn-primary btn-sm" onclick="viewSellerStore('${product.sellerId}', '${escapeHtml(product.sellerName || 'Store')}')">
                                    <i class="fas fa-store"></i> Visit Store
                                </button>
                                <button class="btn btn-secondary btn-sm" onclick="viewSellerProducts('${product.sellerId}')">
                                    <i class="fas fa-box"></i> View All Products
                                </button>
                            </div>
                        </div>
                    ` : ''}
                </div>
            </div>
            
            <!-- Related Products Section -->
            <div id="relatedProductsSection" style="margin-top: 3rem;">
                <div class="section-header">
                    <h3 class="section-title">
                        <i class="fas fa-th-large"></i> Related Products
                    </h3>
                    <a href="#" class="view-all" onclick="filterProductsByCategory('${product.category || 'General'}')">
                        View All <i class="fas fa-chevron-right"></i>
                    </a>
                </div>
                <div class="products-grid" id="relatedProductsGrid">
                    <div class="text-center" style="grid-column: 1/-1; padding: 2rem;">
                        <i class="fas fa-spinner fa-spin"></i>
                        <p>Loading related products...</p>
                    </div>
                </div>
            </div>
        </div>
    `;
}

// Function to load related products
async function loadRelatedProducts(category) {
    const relatedProductsGrid = document.getElementById('relatedProductsGrid');
    if (!relatedProductsGrid) return;
    
    try {
        // Get products from same category
        const snapshot = await db.collection('products')
            .where('category', '==', category)
            .where('status', '==', 'active')
            .limit(12)
            .get();
        
        let relatedProducts = [];
        snapshot.forEach(doc => {
            const product = { id: doc.id, ...doc.data() };
            // Exclude current product
            if (product.id !== selectedProductId) {
                relatedProducts.push(product);
            }
        });
        
        // If not enough products from same category, get random products
        if (relatedProducts.length < 4) {
            const randomSnapshot = await db.collection('products')
                .where('status', '==', 'active')
                .limit(12 - relatedProducts.length)
                .get();
            
            randomSnapshot.forEach(doc => {
                const product = { id: doc.id, ...doc.data() };
                if (product.id !== selectedProductId && !relatedProducts.find(p => p.id === product.id)) {
                    relatedProducts.push(product);
                }
            });
        }
        
        // Display related products
        if (relatedProducts.length === 0) {
            relatedProductsGrid.innerHTML = `
                <div class="text-center" style="grid-column: 1/-1; padding: 2rem;">
                    <i class="fas fa-box-open" style="font-size: 2rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                    <p>No related products found</p>
                </div>
            `;
            return;
        }
        
        let productsHTML = '';
        relatedProducts.forEach(product => {
            const discountedPrice = product.discount ? 
                product.price * (1 - product.discount/100) : product.price;
            
            productsHTML += `
                <div class="product-card" onclick="viewProductDetails('${product.id}')">
                    ${product.images && product.images.length > 0 ? `
                        <div class="product-image-container">
                            <img src="${product.images[0]}" alt="${product.name}" class="product-image">
                            ${product.discount ? `
                                <span class="product-badge">-${product.discount}%</span>
                            ` : ''}
                        </div>
                    ` : `
                        <div class="product-image-container" style="background: var(--accent);">
                            <i class="fas fa-image" style="font-size: 2rem; color: var(--text-secondary);"></i>
                        </div>
                    `}
                    
                    <div class="product-info">
                        <div class="product-category">${product.category || 'General'}</div>
                        <h3 class="product-name">${product.name}</h3>
                        <div class="product-price">
                            <span class="current-price">Rs. ${discountedPrice.toFixed(2)}</span>
                            ${product.discount ? `
                                <span class="original-price">Rs. ${product.price.toFixed(2)}</span>
                            ` : ''}
                        </div>
                        <div class="product-actions">
                            <button class="add-to-cart" onclick="event.stopPropagation(); addToCart('${product.id}')">
                                <i class="fas fa-shopping-cart"></i> Add to Cart
                            </button>
                        </div>
                    </div>
                </div>
            `;
        });
        
        relatedProductsGrid.innerHTML = productsHTML;
        
    } catch (error) {
        console.error('Error loading related products:', error);
        relatedProductsGrid.innerHTML = `
            <div class="text-center" style="grid-column: 1/-1; padding: 2rem; color: var(--error);">
                <i class="fas fa-exclamation-triangle"></i>
                <p>Error loading related products</p>
            </div>
        `;
    }
}

// Function to view all products from a seller
function viewSellerProducts(sellerId) {
    // Filter products by seller
    filterProductsBySeller(sellerId);
}

// Function to filter products by seller
async function filterProductsBySeller(sellerId) {
    hideAllPages();
    document.getElementById('homePage').style.display = 'block';
    
    // Show filter section
    const filterSection = document.getElementById('filterSection');
    if (filterSection) {
        filterSection.style.display = 'block';
    }
    
    // Clear existing products
    const productsGrid = document.getElementById('featuredProducts');
    if (productsGrid) {
        productsGrid.innerHTML = '<div class="text-center" style="grid-column: 1/-1; padding: 2rem;"><i class="fas fa-spinner fa-spin"></i> Loading products...</div>';
    }
    
    try {
        // Get seller name
        const sellerDoc = await db.collection('sellers').doc(sellerId).get();
        const sellerName = sellerDoc.exists ? (sellerDoc.data().shopName || sellerDoc.data().name) : 'Seller';
        
        // Get products from this seller
        const snapshot = await db.collection('products')
            .where('sellerId', '==', sellerId)
            .where('status', '==', 'active')
            .get();
        
        const sellerProducts = [];
        snapshot.forEach(doc => {
            sellerProducts.push({ id: doc.id, ...doc.data() });
        });
        
        // Update page title
        const pageTitle = document.querySelector('#homePage .section-title');
        if (pageTitle) {
            pageTitle.innerHTML = `Products from ${sellerName} <span style="font-size: 0.9rem; color: var(--text-secondary);">(${sellerProducts.length} products)</span>`;
        }
        
        // Display products
        displayProducts(sellerProducts);
        
        // Show back button
        const sectionHeader = document.querySelector('#homePage .section-header');
        if (sectionHeader) {
            const backButton = document.createElement('button');
            backButton.className = 'btn btn-secondary';
            backButton.innerHTML = '<i class="fas fa-arrow-left"></i> Back to All Products';
            backButton.onclick = () => {
                if (filterSection) filterSection.style.display = 'none';
                showAllProducts();
            };
            sectionHeader.querySelector('.view-all')?.remove();
            sectionHeader.appendChild(backButton);
        }
        
    } catch (error) {
        console.error('Error loading seller products:', error);
        showToast('Error loading seller products', 'error');
        showHomePage();
    }
}

// Cleanup function
function cleanupProductPage() {
    if (isProductPageActive) {
        pauseAllActiveVideos();
        activeVideos.clear();
        isProductPageActive = false;
    }
}

// Back function for product details
function goBackFromProductDetails() {
    cleanupProductPage();
    
    // Hide product details page
    document.getElementById('productDetailsPage').style.display = 'none';
    
    // Show home page
    showHomePage();
}

// Media slider functions
function previousMedia() {
    if (productMediaArray.length <= 1) return;
    
    const currentMedia = productMediaArray[currentMediaIndex];
    if (currentMedia.type === 'video') {
        pauseVideoById(currentMedia.id);
    }
    
    currentMediaIndex = (currentMediaIndex - 1 + productMediaArray.length) % productMediaArray.length;
    goToMedia(currentMediaIndex);
}

function nextMedia() {
    if (productMediaArray.length <= 1) return;
    
    const currentMedia = productMediaArray[currentMediaIndex];
    if (currentMedia.type === 'video') {
        pauseVideoById(currentMedia.id);
    }
    
    currentMediaIndex = (currentMediaIndex + 1) % productMediaArray.length;
    goToMedia(currentMediaIndex);
}

function goToMedia(index) {
    if (index < 0 || index >= productMediaArray.length) return;
    
    const currentMedia = productMediaArray[currentMediaIndex];
    if (currentMedia.type === 'video') {
        pauseVideoById(currentMedia.id);
    }
    
    currentMediaIndex = index;
    
    // Update media slides
    document.querySelectorAll('.slider-media').forEach((mediaSlide, i) => {
        mediaSlide.classList.toggle('active', i === index);
    });
    
    // Update dots
    document.querySelectorAll('.slider-dot').forEach((dot, i) => {
        dot.classList.toggle('active', i === index);
    });
    
    // Update thumbnails
    const thumbnails = document.querySelectorAll('.thumbnail-btn');
    if (thumbnails.length > 0) {
        thumbnails.forEach((thumb, i) => {
            thumb.classList.toggle('active', i === index);
        });
    }
    
    // Update counter
    const counter = document.getElementById('mediaCounter');
    if (counter) {
        counter.textContent = `${index + 1} / ${productMediaArray.length}`;
    }
    
    // Show play overlay for video
    const newMedia = productMediaArray[index];
    if (newMedia.type === 'video') {
        const overlay = document.getElementById(`overlay-${newMedia.id}`);
        if (overlay) {
            overlay.style.display = 'flex';
        }
        
        const video = document.getElementById(newMedia.id);
        if (video && video.paused) {
            const playBtn = video.parentElement.querySelector('.play-pause-btn i');
            if (playBtn) {
                playBtn.className = 'fas fa-play';
            }
        }
    }
}

// Video player functions
function pauseVideoById(videoId) {
    const video = document.getElementById(videoId);
    if (video) {
        video.pause();
        activeVideos.delete(videoId);
        
        const overlay = document.getElementById(`overlay-${videoId}`);
        if (overlay) {
            overlay.style.display = 'flex';
        }
        
        const playBtn = video.parentElement.querySelector('.play-pause-btn i');
        if (playBtn) {
            playBtn.className = 'fas fa-play';
        }
    }
}

function pauseAllActiveVideos() {
    productMediaArray.forEach((media) => {
        if (media.type === 'video') {
            const video = document.getElementById(media.id);
            if (video) {
                video.pause();
                video.currentTime = 0;
            }
        }
    });
    activeVideos.clear();
}

function initializeVideoPlayers() {
    productMediaArray.forEach((media) => {
        if (media.type === 'video') {
            const video = document.getElementById(media.id);
            if (video) {
                const newVideo = video.cloneNode(true);
                video.parentNode.replaceChild(newVideo, video);
                
                const currentVideo = document.getElementById(media.id);
                
                currentVideo.addEventListener('play', function() {
                    const overlay = document.getElementById(`overlay-${media.id}`);
                    if (overlay) overlay.style.display = 'none';
                    
                    const playBtn = this.parentElement.querySelector('.play-pause-btn i');
                    if (playBtn) playBtn.className = 'fas fa-pause';
                    
                    activeVideos.add(media.id);
                });
                
                currentVideo.addEventListener('pause', function() {
                    const overlay = document.getElementById(`overlay-${media.id}`);
                    if (overlay && !this.ended) overlay.style.display = 'flex';
                    
                    const playBtn = this.parentElement.querySelector('.play-pause-btn i');
                    if (playBtn) playBtn.className = 'fas fa-play';
                    
                    activeVideos.delete(media.id);
                });
                
                currentVideo.addEventListener('ended', function() {
                    const overlay = document.getElementById(`overlay-${media.id}`);
                    if (overlay) overlay.style.display = 'flex';
                    
                    const playBtn = this.parentElement.querySelector('.play-pause-btn i');
                    if (playBtn) playBtn.className = 'fas fa-play';
                    
                    activeVideos.delete(media.id);
                });
            }
        }
    });
}

function toggleVideoPlayback(videoId) {
    const video = document.getElementById(videoId);
    if (!video) return;
    
    if (video.paused) {
        video.play();
        activeVideos.add(videoId);
    } else {
        video.pause();
        activeVideos.delete(videoId);
    }
}

function toggleFullscreen(videoId) {
    const video = document.getElementById(videoId);
    if (!video) return;
    
    const videoWrapper = video.parentElement;
    
    if (!document.fullscreenElement) {
        if (videoWrapper.requestFullscreen) {
            videoWrapper.requestFullscreen();
        } else if (videoWrapper.webkitRequestFullscreen) {
            videoWrapper.webkitRequestFullscreen();
        } else if (videoWrapper.mozRequestFullScreen) {
            videoWrapper.mozRequestFullScreen();
        }
    } else {
        if (document.exitFullscreen) {
            document.exitFullscreen();
        } else if (document.webkitExitFullscreen) {
            document.webkitExitFullscreen();
        } else if (document.mozCancelFullScreen) {
            document.mozCancelFullScreen();
        }
    }
}

// Helper functions
function changeProductQuantity(change) {
    const quantityInput = document.getElementById('productQuantity');
    if (!quantityInput) return;
    
    let currentQty = parseInt(quantityInput.value) || 1;
    const maxQty = parseInt(quantityInput.max) || 1;
    
    currentQty += change;
    if (currentQty < 1) currentQty = 1;
    if (currentQty > maxQty) currentQty = maxQty;
    
    quantityInput.value = currentQty;
    updateQuantityButtons();
}

function updateQuantityButtons() {
    const quantityInput = document.getElementById('productQuantity');
    if (!quantityInput) return;
    
    const currentQty = parseInt(quantityInput.value) || 1;
    const maxQty = parseInt(quantityInput.max) || 1;
    
    const decreaseBtn = document.getElementById('decreaseQty');
    const increaseBtn = document.getElementById('increaseQty');
    
    if (decreaseBtn) decreaseBtn.disabled = currentQty <= 1;
    if (increaseBtn) increaseBtn.disabled = currentQty >= maxQty;
}

function addToCartFromDetails(productId) {
    const product = products.find(p => p.id === productId);
    if (!product) return;
    
    const quantityInput = document.getElementById('productQuantity');
    if (!quantityInput) return;
    
    const quantity = parseInt(quantityInput.value) || 1;
    
    addToCart(productId, quantity);
}

function setupPageCleanup() {
    document.addEventListener('visibilitychange', function() {
        if (document.hidden && isProductPageActive) {
            pauseAllActiveVideos();
        }
    });
    
    window.addEventListener('blur', function() {
        if (isProductPageActive) {
            pauseAllActiveVideos();
        }
    });
}

// Product view from store - updated to properly open product details
function showProductDetails(productId) {
    // This is a wrapper function to ensure product details open correctly
    viewProductDetails(productId);
}

// Add CSS for product details page
const productDetailsCSS = `
    /* Product Details Grid */
    .product-details-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2rem;
    }
    
    @media (max-width: 768px) {
        .product-details-grid {
            grid-template-columns: 1fr;
        }
    }
    
    /* Product Media Section */
    .product-media-section {
        background: var(--white);
        border-radius: var(--radius-lg);
        padding: 1rem;
        box-shadow: var(--shadow);
    }
    
    .product-media-slider {
        position: relative;
        width: 100%;
        height: 400px;
        overflow: hidden;
        border-radius: var(--radius);
        background: var(--accent);
    }
    
    @media (max-width: 768px) {
        .product-media-slider {
            height: 300px;
        }
    }
    
    /* Product Info Section */
    .product-info-section {
        background: var(--white);
        border-radius: var(--radius-lg);
        padding: 2rem;
        box-shadow: var(--shadow);
    }
    
    .price-availability-card {
        background: linear-gradient(135deg, rgba(1, 65, 28, 0.05), rgba(0, 105, 62, 0.03));
        padding: 1.5rem;
        border-radius: var(--radius);
        margin: 1.5rem 0;
        border: 1px solid var(--primary-light);
    }
    
    .add-to-cart-section {
        display: flex;
        gap: 1rem;
        margin: 1.5rem 0;
        align-items: center;
        flex-wrap: wrap;
    }
    
    .quantity-controls {
        display: flex;
        align-items: center;
        gap: 0.5rem;
    }
    
    .qty-btn {
        width: 36px;
        height: 36px;
        border-radius: 50%;
        border: 2px solid var(--primary);
        background: white;
        color: var(--primary);
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    
    .qty-btn:disabled {
        opacity: 0.5;
        cursor: not-allowed;
    }
    
    .qty-input {
        width: 60px;
        text-align: center;
        padding: 8px;
        border: 2px solid var(--primary);
        border-radius: var(--radius);
        font-weight: 600;
    }
    
    .action-buttons {
        display: flex;
        gap: 0.5rem;
        margin: 1rem 0;
        flex-wrap: wrap;
    }
    
    .action-btn {
        flex: 1;
        min-width: 120px;
        padding: 10px;
        border: 1px solid var(--border);
        background: white;
        border-radius: var(--radius);
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
        transition: all 0.3s;
    }
    
    .action-btn:hover {
        background: var(--accent);
        transform: translateY(-2px);
    }
    
    .product-description-section, 
    .product-specs,
    .product-highlights {
        margin: 2rem 0;
        padding: 1.5rem;
        background: var(--accent);
        border-radius: var(--radius);
    }
    
    .seller-info-card {
        background: var(--white);
        border: 2px solid var(--primary-light);
        border-radius: var(--radius);
        padding: 1.5rem;
        margin: 1.5rem 0;
    }
    
    /* Related Products */
    #relatedProductsGrid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        gap: 1.5rem;
        margin-top: 1rem;
    }
    
    /* Responsive */
    @media (max-width: 480px) {
        .product-details-grid {
            gap: 1rem;
        }
        
        .product-info-section {
            padding: 1rem;
        }
        
        .add-to-cart-section {
            flex-direction: column;
        }
        
        .action-buttons {
            flex-direction: column;
        }
        
        .action-btn {
            width: 100%;
        }
    }
`;

// Add the CSS to the document
const productStyleSheet = document.createElement("style");
productStyleSheet.textContent = productDetailsCSS;
document.head.appendChild(productStyleSheet);

// Update the existing hideAllPages function to include product details page
function hideAllPages() {
    const pages = [
        'homePage', 'productDetailsPage', 'cartPage', 'checkoutPage',
        'buyerProfilePage', 'ordersPage', 'orderTrackingPage', 'wishlistPage',
        'addressesPage', 'settingsPage', 'messagesPage', 'sellerStorePage', 
        'followingStoresPage', 'allStoresPage', 'notificationsPage',
        'searchResultsSection'
    ];
    
    pages.forEach(page => {
        const element = document.getElementById(page);
        if (element) {
            element.style.display = 'none';
        }
    });
}

// Update product display function to use the new view function
function displayProducts(productList = products) {
    const productsGrid = document.getElementById('featuredProducts');
    if (!productsGrid) return;
    
    if (!productList || productList.length === 0) {
        productsGrid.innerHTML = `
            <div class="text-center" style="grid-column: 1/-1; padding: 3rem;">
                <i class="fas fa-box-open" style="font-size: 3rem; color: var(--text-secondary); opacity: 0.5; margin-bottom: 1rem;"></i>
                <h3>No Products Found</h3>
                <p>Try adjusting your search or filters</p>
            </div>
        `;
        return;
    }
    
    let productsHTML = '';
    
    productList.forEach(product => {
        const discountedPrice = product.discount ? 
            product.price * (1 - product.discount/100) : product.price;
        
        productsHTML += `
            <div class="product-card" onclick="viewProductDetails('${product.id}')">
                <div class="product-badge">${product.category || 'General'}</div>
                <div class="product-image-container">
                    <img src="${product.images && product.images.length > 0 ? product.images[0] : 'https://via.placeholder.com/300?text=No+Image'}" 
                         alt="${product.name}" 
                         class="product-image">
                </div>
                <div class="product-info">
                    <div class="product-category">${product.category || 'General'}</div>
                    <h3 class="product-name">${product.name}</h3>
                    <div class="product-rating">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star-half-alt"></i>
                        <span>(0)</span>
                    </div>
                    <div class="product-price">
                        <span class="current-price">Rs. ${discountedPrice.toFixed(2)}</span>
                        ${product.discount ? `
                            <span class="original-price">Rs. ${product.price.toFixed(2)}</span>
                        ` : ''}
                    </div>
                    <div class="product-seller">
                        <i class="fas fa-store"></i> ${product.sellerName || 'Jeeto Pakistan'}
                    </div>
                    <div class="product-actions">
                        <button class="add-to-cart" onclick="event.stopPropagation(); addToCart('${product.id}')">
                            <i class="fas fa-shopping-cart"></i> Add to Cart
                        </button>
                    </div>
                </div>
            </div>
        `;
    });
    
    productsGrid.innerHTML = productsHTML;
}

// ==================== FOLLOWED STORES FUNCTIONS ====================

// Global variables
let allStores = [];

// Initialize followed stores
function initializeFollowedStores() {
    if (currentUser) {
        loadFollowedStoresIcons();
    }
}

// Load followed stores icons for dashboard
async function loadFollowedStoresIcons() {
    const iconsGrid = document.getElementById('followedStoresIconsGrid');
    if (!iconsGrid) {
        console.warn('Followed stores grid not found');
        return;
    }
    
    // Show loading state
    iconsGrid.innerHTML = `
        <div style="text-align: center; grid-column: 1/-1; padding: 2rem;">
            <i class="fas fa-spinner fa-spin fa-2x" style="color: var(--primary);"></i>
            <p style="margin-top: 1rem;">Loading your stores...</p>
        </div>
    `;
    
    if (!currentUser) {
        iconsGrid.innerHTML = `
            <div style="text-align: center; grid-column: 1/-1; padding: 2rem;">
                <i class="fas fa-user-lock" style="font-size: 3rem; color: var(--text-secondary); opacity: 0.5; margin-bottom: 1rem;"></i>
                <p>Login to see followed stores</p>
                <button class="btn btn-primary btn-sm" onclick="openAuthModal('buyerLogin')">
                    <i class="fas fa-sign-in-alt"></i> Login
                </button>
            </div>
        `;
        return;
    }
    
    const followedStoreIds = currentUserProfile?.followingSellers || [];
    
    if (followedStoreIds.length === 0) {
        iconsGrid.innerHTML = `
            <div style="text-align: center; grid-column: 1/-1; padding: 2rem;">
                <i class="fas fa-store-slash" style="font-size: 3rem; color: var(--text-secondary); opacity: 0.5; margin-bottom: 1rem;"></i>
                <p>Follow stores to see them here!</p>
                <button class="btn btn-primary btn-sm" onclick="showAllStores()">
                    <i class="fas fa-store"></i> Browse Stores
                </button>
            </div>
        `;
        return;
    }
    
    try {
        let iconsHTML = '';
        let loadedCount = 0;
        const maxStoresToShow = 8;
        
        // Fetch store details for each followed store
        for (const storeId of followedStoreIds.slice(0, maxStoresToShow)) {
            try {
                const storeDoc = await db.collection('sellers').doc(storeId).get();
                if (storeDoc.exists) {
                    const store = storeDoc.data();
                    const storeName = store.shopName || store.name || 'Unknown Store';
                    const safeStoreName = storeName.replace(/'/g, "\\'");
                    
                    iconsHTML += `
                        <div class="category-card" onclick="viewSellerStore('${storeId}', '${safeStoreName}')">
                            <div class="follow-badge" title="Following">
                                <i class="fas fa-check"></i>
                            </div>
                            <div style="font-size: 2rem; color: var(--primary); margin-bottom: 0.5rem;">
                                ${store.shopLogo ? 
                                    `<img src="${store.shopLogo}" alt="${storeName}" 
                                          style="width: 50px; height: 50px; border-radius: 50%; object-fit: cover; border: 2px solid var(--primary);">` :
                                    `<i class="fas fa-store"></i>`
                                }
                            </div>
                            <div class="category-name">
                                ${storeName.length > 15 ? storeName.substring(0, 15) + '...' : storeName}
                            </div>
                        </div>
                    `;
                    loadedCount++;
                }
            } catch (error) {
                console.error(`Error loading store ${storeId}:`, error);
            }
        }
        
        // Add "View All" button if we have more stores
        if (followedStoreIds.length > maxStoresToShow) {
            iconsHTML += `
                <div class="category-card view-all-stores-btn" onclick="showFollowingStores()">
                    <div style="font-size: 2rem; margin-bottom: 0.5rem;">
                        <i class="fas fa-ellipsis-h"></i>
                    </div>
                    <div class="category-name" style="color: white;">
                        View All
                    </div>
                    <small style="font-size: 0.7rem; margin-top: 5px; color: rgba(255,255,255,0.8);">
                        +${followedStoreIds.length - maxStoresToShow} more
                    </small>
                </div>
            `;
        }
        
        if (loadedCount === 0) {
            iconsGrid.innerHTML = `
                <div style="text-align: center; grid-column: 1/-1; padding: 2rem;">
                    <i class="fas fa-exclamation-triangle" style="font-size: 3rem; color: var(--warning); margin-bottom: 1rem;"></i>
                    <p>Unable to load your stores</p>
                    <button class="btn btn-secondary btn-sm" onclick="loadFollowedStoresIcons()">
                        <i class="fas fa-redo"></i> Retry
                    </button>
                </div>
            `;
        } else {
            iconsGrid.innerHTML = iconsHTML;
        }
        
    } catch (error) {
        console.error('Error loading store icons:', error);
        iconsGrid.innerHTML = `
            <div style="text-align: center; grid-column: 1/-1; padding: 2rem;">
                <i class="fas fa-exclamation-triangle" style="font-size: 3rem; color: var(--error); margin-bottom: 1rem;"></i>
                <p>Error loading stores</p>
                <button class="btn btn-secondary btn-sm" onclick="loadFollowedStoresIcons()">
                    <i class="fas fa-redo"></i> Retry
                </button>
            </div>
        `;
    }
}

// Show all followed stores page
async function showFollowingStores() {
    hideAllPages();
    
    let followingPage = document.getElementById('followingStoresPage');
    if (!followingPage) {
        followingPage = document.createElement('div');
        followingPage.id = 'followingStoresPage';
        followingPage.className = 'container';
        document.getElementById('mainContent').appendChild(followingPage);
    }
    followingPage.style.display = 'block';
    window.scrollTo(0, 0);
    
    if (!currentUser) {
        followingPage.innerHTML = `
            <div class="section-header mt-4">
                <h2 class="section-title">
                    <i class="fas fa-heart"></i> Followed Stores
                </h2>
                <button class="btn btn-secondary" onclick="showHomePage()">
                    <i class="fas fa-arrow-left"></i> Back to Home
                </button>
            </div>
            <div class="empty-state" style="margin-top: 2rem;">
                <i class="fas fa-user-lock empty-state-icon"></i>
                <h3>Please Login</h3>
                <p>Login to view your followed stores</p>
                <button class="btn btn-primary" onclick="openAuthModal('buyerLogin')">
                    <i class="fas fa-sign-in-alt"></i> Login Now
                </button>
            </div>
        `;
        return;
    }
    
    const storeIds = currentUserProfile?.followingSellers || [];
    
    if (storeIds.length === 0) {
        followingPage.innerHTML = `
            <div class="section-header mt-4">
                <h2 class="section-title">
                    <i class="fas fa-heart"></i> Followed Stores
                </h2>
                <div>
                    <button class="btn btn-secondary" onclick="showHomePage()">
                        <i class="fas fa-arrow-left"></i> Back to Home
                    </button>
                    <button class="btn btn-primary" onclick="showAllStores()" style="margin-left: 10px;">
                        <i class="fas fa-store"></i> Browse Stores
                    </button>
                </div>
            </div>
            <div class="empty-state" style="margin-top: 2rem;">
                <i class="fas fa-store-slash empty-state-icon"></i>
                <h3>No Stores Followed</h3>
                <p>You haven't followed any stores yet. Start following to see them here!</p>
                <button class="btn btn-primary" onclick="showAllStores()">
                    <i class="fas fa-store"></i> Explore Stores
                </button>
            </div>
        `;
        return;
    }
    
    followingPage.innerHTML = `
        <div class="section-header mt-4">
            <h2 class="section-title">
                <i class="fas fa-heart"></i> Your Followed Stores
                <span class="badge" style="background: var(--primary); color: white; font-size: 0.8rem; padding: 5px 10px; border-radius: 20px;">
                    ${storeIds.length} Stores
                </span>
            </h2>
            <div>
                <button class="btn btn-secondary" onclick="showHomePage()">
                    <i class="fas fa-arrow-left"></i> Back to Home
                </button>
                <button class="btn btn-primary" onclick="showAllStores()" style="margin-left: 10px;">
                    <i class="fas fa-plus"></i> Follow More Stores
                </button>
            </div>
        </div>
        
        <div id="allFollowedStores" style="margin-top: 2rem;">
            <div class="text-center p-5">
                <i class="fas fa-spinner fa-spin fa-2x"></i>
                <p>Loading your stores...</p>
            </div>
        </div>
    `;
    
    try {
        const container = document.getElementById('allFollowedStores');
        let storesHTML = '<div class="products-grid">';
        
        // Fetch each seller's details
        for (const storeId of storeIds) {
            const sellerDoc = await db.collection('sellers').doc(storeId).get();
            if (sellerDoc.exists) {
                const seller = sellerDoc.data();
                const storeName = seller.shopName || seller.name || 'Unknown Store';
                const safeStoreName = storeName.replace(/'/g, "\\'");
                
                // Get product count
                const productsSnapshot = await db.collection('products')
                    .where('sellerId', '==', storeId)
                    .where('status', '==', 'active')
                    .get();
                
                storesHTML += `
                    <div class="product-card" onclick="viewSellerStore('${storeId}', '${safeStoreName}')">
                        <div style="height: 150px; display: flex; align-items: center; justify-content: center; background: var(--accent); border-radius: var(--radius) var(--radius) 0 0;">
                            ${seller.shopLogo ? 
                                `<img src="${seller.shopLogo}" alt="${storeName}" 
                                      style="max-width: 100px; max-height: 100px; object-fit: contain;">` :
                                `<i class="fas fa-store" style="font-size: 3rem; color: var(--primary);"></i>`
                            }
                        </div>
                        
                        <div class="product-info">
                            <h3 class="product-name" style="text-align: center;">${storeName}</h3>
                            
                            ${seller.city || seller.description ? `
                                <p style="color: var(--text-secondary); font-size: 0.9rem; text-align: center; margin: 0.5rem 0;">
                                    ${seller.city || (seller.description ? seller.description.substring(0, 50) + '...' : '')}
                                </p>
                            ` : ''}
                            
                            <div style="display: flex; justify-content: space-between; align-items: center; margin-top: 1rem;">
                                <span style="font-size: 0.9rem; color: var(--text-secondary);">
                                    <i class="fas fa-box"></i> ${productsSnapshot.size} products
                                </span>
                                <button class="unfollow-btn btn-sm" 
                                        onclick="event.stopPropagation(); toggleFollowStore('${storeId}', '${safeStoreName}')">
                                    <i class="fas fa-times"></i> Unfollow
                                </button>
                            </div>
                        </div>
                    </div>
                `;
            }
        }
        
        storesHTML += '</div>';
        container.innerHTML = storesHTML || `
            <div class="empty-state">
                <i class="fas fa-exclamation-triangle empty-state-icon"></i>
                <h3>No Stores Found</h3>
                <p>Your followed stores couldn't be loaded</p>
            </div>
        `;
        
    } catch (error) {
        console.error("Error loading following stores:", error);
        const container = document.getElementById('allFollowedStores');
        if (container) {
            container.innerHTML = `
                <div class="empty-state">
                    <i class="fas fa-exclamation-triangle empty-state-icon"></i>
                    <h3>Error Loading Stores</h3>
                    <p>${error.message}</p>
                    <button class="btn btn-primary" onclick="showFollowingStores()">
                        <i class="fas fa-redo"></i> Try Again
                    </button>
                </div>
            `;
        }
    }
}

// View individual store
async function viewSellerStore(sellerId, shopName) {
    hideAllPages();
    
    let storePage = document.getElementById('sellerStorePage');
    if (!storePage) {
        storePage = document.createElement('div');
        storePage.id = 'sellerStorePage';
        storePage.className = 'container';
        document.getElementById('mainContent').appendChild(storePage);
    }
    storePage.style.display = 'block';
    window.scrollTo(0, 0);
    
    // Show loading state
    storePage.innerHTML = `
        <div class="text-center p-5">
            <i class="fas fa-spinner fa-spin fa-2x"></i>
            <p>Loading store...</p>
        </div>
    `;
    
    try {
        // Get store details
        const storeDoc = await db.collection('sellers').doc(sellerId).get();
        if (!storeDoc.exists) {
            storePage.innerHTML = `
                <div class="empty-state">
                    <i class="fas fa-exclamation-circle empty-state-icon"></i>
                    <h3>Store Not Found</h3>
                    <p>The store you're looking for doesn't exist.</p>
                    <button class="btn btn-primary" onclick="showHomePage()">
                        <i class="fas fa-arrow-left"></i> Back to Home
                    </button>
                </div>
            `;
            return;
        }
        
        const store = storeDoc.data();
        
        // Get store stats
        const productsSnapshot = await db.collection('products')
            .where('sellerId', '==', sellerId)
            .where('status', '==', 'active')
            .get();
        
        const followersSnapshot = await db.collection('users')
            .where('followingSellers', 'array-contains', sellerId)
            .get();
        
        // Check if user is following
        const isFollowing = currentUserProfile?.followingSellers?.includes(sellerId) || false;
        const safeShopName = shopName.replace(/'/g, "\\'");
        
        // Render store page
        storePage.innerHTML = `
            <!-- Store Header -->
            <div class="seller-store-header">
                <div class="container" style="position: relative; z-index: 2;">
                    <div style="display: flex; align-items: center; gap: 2rem; padding: 40px 0; flex-wrap: wrap;">
                        <!-- Store Logo -->
                        <div style="width: 120px; height: 120px; background: white; border-radius: 50%; 
                              display: flex; align-items: center; justify-content: center; 
                              border: 5px solid white; box-shadow: var(--shadow-lg);">
                            ${store.shopLogo ? 
                                `<img src="${store.shopLogo}" alt="${shopName}" 
                                      style="width: 100%; height: 100%; object-fit: cover; border-radius: 50%;">` :
                                `<i class="fas fa-store" style="font-size: 3rem; color: var(--primary);"></i>`
                            }
                        </div>
                        
                        <!-- Store Info -->
                        <div style="flex: 1; color: white;">
                            <h1 style="font-weight: 700; margin: 0; font-size: 2rem; text-shadow: 2px 2px 4px rgba(0,0,0,0.3);">
                                ${shopName}
                            </h1>
                            <p style="font-size: 1rem; opacity: 0.9; margin: 10px 0 20px; max-width: 600px;">
                                ${store.description ? store.description.substring(0, 100) + '...' : 'Premium Store on Jeeto Pakistan'}
                            </p>
                            
                            <!-- Store Stats -->
                            <div style="display: flex; gap: 2rem; flex-wrap: wrap;">
                                <div style="text-align: center;">
                                    <div style="font-size: 1.5rem; font-weight: bold;">${productsSnapshot.size}</div>
                                    <div style="font-size: 0.9rem; opacity: 0.8;">Products</div>
                                </div>
                                <div style="text-align: center;">
                                    <div style="font-size: 1.5rem; font-weight: bold;">${followersSnapshot.size}</div>
                                    <div style="font-size: 0.9rem; opacity: 0.8;">Followers</div>
                                </div>
                                <div style="text-align: center;">
                                    <div style="font-size: 1.5rem; font-weight: bold;">${store.rating || '4.5'}</div>
                                    <div style="font-size: 0.9rem; opacity: 0.8;">Rating</div>
                                </div>
                                <div style="text-align: center;">
                                    <div style="font-size: 1.5rem; font-weight: bold;">
                                        <i class="fas fa-check-circle"></i>
                                    </div>
                                    <div style="font-size: 0.9rem; opacity: 0.8;">Verified</div>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Action Buttons -->
                        <div style="display: flex; gap: 1rem; flex-wrap: wrap;">
                            <button class="follow-btn ${isFollowing ? 'following' : 'not-following'}" 
                                    id="storeFollowBtn"
                                    onclick="toggleFollowStore('${sellerId}', '${safeShopName}')"
                                    style="min-width: 140px;">
                                <i class="fas ${isFollowing ? 'fa-check' : 'fa-plus'}"></i>
                                <span>${isFollowing ? 'Following' : 'Follow Store'}</span>
                            </button>
                            
                            <button class="btn" style="background: rgba(255,255,255,0.2); color: white; border: 2px solid white;" 
                                    onclick="sendMessageToStore('${sellerId}', '${safeShopName}')">
                                <i class="fas fa-comment"></i> Message
                            </button>
                            
                            <button class="btn" style="background: transparent; color: white; border: 2px solid white;" 
                                    onclick="showHomePage()">
                                <i class="fas fa-arrow-left"></i> Home
                            </button>
                        </div>
                    </div>
                </div>
                
                <!-- Background Pattern -->
                <div style="position: absolute; top: 0; left: 0; right: 0; bottom: 0; 
                      background: linear-gradient(135deg, rgba(1,65,28,0.9), rgba(0,105,62,0.8)); 
                      z-index: 1;"></div>
            </div>
            
            <!-- Store Content -->
            <div style="margin-top: -40px; position: relative; z-index: 10;">
                <!-- Store Navigation -->
                <div class="store-nav">
                    <button class="store-nav-btn active" onclick="filterStoreProducts('all', '${sellerId}')">
                        <i class="fas fa-th-large"></i> All Products
                    </button>
                    <button class="store-nav-btn" onclick="filterStoreProducts('top-sale', '${sellerId}')">
                        <i class="fas fa-fire"></i> Top Deals
                    </button>
                    <button class="store-nav-btn" onclick="filterStoreProducts('price-low', '${sellerId}')">
                        <i class="fas fa-sort-amount-down"></i> Price: Low to High
                    </button>
                    <button class="store-nav-btn" onclick="filterStoreProducts('price-high', '${sellerId}')">
                        <i class="fas fa-sort-amount-up"></i> Price: High to Low
                    </button>
                </div>
                
                <!-- Store Description -->
                ${store.description ? `
                    <div class="store-description">
                        <h3 style="color: var(--primary); margin-bottom: 1rem;">
                            <i class="fas fa-info-circle"></i> About This Store
                        </h3>
                        <p style="line-height: 1.6;">${store.description}</p>
                        
                        ${store.address || store.city ? `
                            <div style="margin-top: 1rem; padding-top: 1rem; border-top: 1px solid var(--border);">
                                <h4 style="color: var(--primary); margin-bottom: 0.5rem;">
                                    <i class="fas fa-map-marker-alt"></i> Location
                                </h4>
                                <p>${store.address || ''} ${store.city ? ', ' + store.city : ''}</p>
                            </div>
                        ` : ''}
                    </div>
                ` : ''}
                
                <!-- Products Grid -->
                <div id="storeProductsContainer">
                    <div class="text-center p-5">
                        <i class="fas fa-spinner fa-spin fa-2x" style="color: var(--primary);"></i>
                        <p>Loading store products...</p>
                    </div>
                </div>
            </div>
        `;
        
        // Load initial products
        filterStoreProducts('all', sellerId);
        
    } catch (error) {
        console.error('Error loading store:', error);
        storePage.innerHTML = `
            <div class="empty-state">
                <i class="fas fa-exclamation-triangle empty-state-icon"></i>
                <h3>Error Loading Store</h3>
                <p>${error.message}</p>
                <button class="btn btn-primary" onclick="showHomePage()">
                    <i class="fas fa-arrow-left"></i> Back to Home
                </button>
            </div>
        `;
    }
}

// Filter store products
async function filterStoreProducts(criteria, sellerId) {
    const container = document.getElementById('storeProductsContainer');
    if (!container) return;
    
    container.innerHTML = `
        <div class="text-center p-5">
            <i class="fas fa-spinner fa-spin fa-2x" style="color: var(--primary);"></i>
            <p>Loading products...</p>
        </div>
    `;
    
    try {
        const snapshot = await db.collection('products')
            .where('sellerId', '==', sellerId)
            .where('status', '==', 'active')
            .get();
        
        let products = [];
        snapshot.forEach(doc => products.push({ id: doc.id, ...doc.data() }));
        
        // Apply sorting
        switch(criteria) {
            case 'price-low':
                products.sort((a, b) => a.price - b.price);
                break;
            case 'price-high':
                products.sort((a, b) => b.price - a.price);
                break;
            case 'top-sale':
                products.sort((a, b) => (b.discount || 0) - (a.discount || 0));
                break;
            case 'newest':
                products.sort((a, b) => {
                    const dateA = a.createdAt ? (a.createdAt.toDate ? a.createdAt.toDate() : new Date(a.createdAt)) : new Date(0);
                    const dateB = b.createdAt ? (b.createdAt.toDate ? b.createdAt.toDate() : new Date(b.createdAt)) : new Date(0);
                    return dateB - dateA;
                });
                break;
        }
        
        // Update active nav button
        document.querySelectorAll('.store-nav-btn').forEach(btn => {
            btn.classList.remove('active');
        });
        
        // Find and activate the correct button
        const activeBtn = Array.from(document.querySelectorAll('.store-nav-btn')).find(btn => 
            btn.textContent.includes(criteria === 'all' ? 'All Products' : 
            criteria === 'top-sale' ? 'Top Deals' : 
            criteria === 'price-low' ? 'Price: Low to High' : 
            criteria === 'price-high' ? 'Price: High to Low' : '')
        );
        
        if (activeBtn) {
            activeBtn.classList.add('active');
        }
        
        // Display products
        if (products.length === 0) {
            container.innerHTML = `
                <div class="empty-state">
                    <i class="fas fa-box-open empty-state-icon"></i>
                    <h3>No Products Found</h3>
                    <p>This store hasn't added any products yet.</p>
                </div>
            `;
            return;
        }
        
        let productsHTML = '<div class="products-grid">';
        
        products.forEach(product => {
            const discountedPrice = product.discount ? 
                product.price * (1 - product.discount/100) : 
                product.price;
            
            productsHTML += `
                <div class="product-card" onclick="showProductDetails('${product.id}')">
                    <div class="product-image-container" style="height: 200px; overflow: hidden;">
                        ${product.images && product.images.length > 0 ? 
                            `<img src="${product.images[0]}" alt="${product.name}" class="product-image" 
                                  style="width: 100%; height: 100%; object-fit: cover;">` : 
                            `<div style="width: 100%; height: 100%; background: var(--accent); 
                                  display: flex; align-items: center; justify-content: center;">
                                <i class="fas fa-image" style="font-size: 2rem; color: var(--text-secondary);"></i>
                            </div>`
                        }
                    </div>
                    
                    <div class="product-info">
                        <h3 class="product-name">${product.name}</h3>
                        <div class="product-price">
                            <span class="current-price">Rs. ${discountedPrice.toFixed(2)}</span>
                            ${product.discount ? 
                                `<span class="original-price">Rs. ${product.price.toFixed(2)}</span>` : 
                                ''
                            }
                        </div>
                        <button class="add-to-cart" onclick="event.stopPropagation(); addToCart('${product.id}')">
                            <i class="fas fa-shopping-cart"></i> Add to Cart
                        </button>
                    </div>
                </div>
            `;
        });
        
        productsHTML += '</div>';
        container.innerHTML = productsHTML;
        
    } catch (error) {
        console.error("Filter error:", error);
        container.innerHTML = `
            <div class="empty-state">
                <i class="fas fa-exclamation-triangle empty-state-icon"></i>
                <h3>Error Loading Products</h3>
                <p>${error.message}</p>
                <button class="btn btn-primary" onclick="filterStoreProducts('all', '${sellerId}')">
                    <i class="fas fa-redo"></i> Try Again
                </button>
            </div>
        `;
    }
}

// Toggle follow/unfollow store
async function toggleFollowStore(sellerId, shopName) {
    if (!currentUser) {
        showToast("Please login to follow stores", "error");
        openAuthModal('buyerLogin');
        return;
    }

    const userRef = db.collection('users').doc(currentUser.uid);
    let following = currentUserProfile.followingSellers || [];
    const isCurrentlyFollowing = following.includes(sellerId);

    try {
        if (isCurrentlyFollowing) {
            // Unfollow
            following = following.filter(id => id !== sellerId);
            await userRef.update({ followingSellers: following });
            currentUserProfile.followingSellers = following;
            
            showToast(`Unfollowed ${shopName}`, 'info');
            
            // Update UI
            const followBtn = document.getElementById('storeFollowBtn');
            if (followBtn) {
                followBtn.className = 'follow-btn not-following';
                followBtn.innerHTML = '<i class="fas fa-plus"></i> <span>Follow Store</span>';
            }
            
        } else {
            // Follow
            following.push(sellerId);
            await userRef.update({ followingSellers: following });
            currentUserProfile.followingSellers = following;
            
            showToast(`Now following ${shopName}`, 'success');
            
            // Update UI
            const followBtn = document.getElementById('storeFollowBtn');
            if (followBtn) {
                followBtn.className = 'follow-btn following';
                followBtn.innerHTML = '<i class="fas fa-check"></i> <span>Following</span>';
            }
        }
        
        // Refresh followed stores icons
        loadFollowedStoresIcons();
        
    } catch (error) {
        console.error("Error updating follow status:", error);
        showToast("Error updating follow status", "error");
    }
}

// Send message to store
function sendMessageToStore(sellerId, shopName) {
    if (!currentUser) {
        showToast('Please login to message stores', 'warning');
        openAuthModal('buyerLogin');
        return;
    }
    
    // Set values in the form
    document.getElementById('messageStoreId').value = sellerId;
    document.getElementById('messageStoreName').value = shopName;
    document.getElementById('storeMessageSubject').value = `Inquiry about ${shopName}`;
    document.getElementById('storeMessageText').value = '';
    
    // Open the modal
    openModal('messageStoreModal');
}

// Handle message store form submission
async function handleMessageStore() {
    const sellerId = document.getElementById('messageStoreId').value;
    const shopName = document.getElementById('messageStoreName').value;
    const subject = document.getElementById('storeMessageSubject').value;
    const message = document.getElementById('storeMessageText').value;
    
    if (!currentUser) {
        showToast('Please login to send messages', 'error');
        return;
    }
    
    if (!message.trim()) {
        showToast('Please enter a message', 'error');
        return;
    }
    
    try {
        const messageData = {
            senderId: currentUser.uid,
            senderName: currentUserProfile.displayName || currentUser.email,
            receiverId: sellerId,
            receiverName: shopName,
            subject: subject || `Message about ${shopName}`,
            message: message,
            read: false,
            createdAt: new Date(),
            type: 'store_inquiry'
        };
        
        await db.collection('messages').add(messageData);
        
        showToast('Message sent successfully!', 'success');
        closeModal('messageStoreModal');
        
        // Clear form
        document.getElementById('storeMessageText').value = '';
        
    } catch (error) {
        console.error('Error sending message:', error);
        showToast('Error sending message', 'error');
    }
}

// Show all stores directory
async function showAllStores() {
    hideAllPages();
    
    let allStoresPage = document.getElementById('allStoresPage');
    if (!allStoresPage) {
        allStoresPage = document.createElement('div');
        allStoresPage.id = 'allStoresPage';
        allStoresPage.className = 'container';
        document.getElementById('mainContent').appendChild(allStoresPage);
    }
    allStoresPage.style.display = 'block';
    window.scrollTo(0, 0);
    
    allStoresPage.innerHTML = `
        <div class="section-header mt-4">
            <h2 class="section-title">
                <i class="fas fa-store"></i> Browse All Stores
            </h2>
            <div>
                <button class="btn btn-secondary" onclick="showHomePage()">
                    <i class="fas fa-arrow-left"></i> Back to Home
                </button>
                ${currentUser ? `
                    <button class="btn btn-primary" onclick="showFollowingStores()" style="margin-left: 10px;">
                        <i class="fas fa-heart"></i> Your Followed Stores
                    </button>
                ` : ''}
            </div>
        </div>
        
        <div class="products-grid" id="allStoresList" style="margin-top: 2rem;">
            <div class="text-center p-5">
                <i class="fas fa-spinner fa-spin fa-2x"></i>
                <p>Loading stores...</p>
            </div>
        </div>
    `;
    
    try {
        const snapshot = await db.collection('sellers')
            .where('status', '==', 'active')
            .limit(50)
            .get();
        
        const stores = snapshot.docs.map(doc => ({
            id: doc.id,
            ...doc.data()
        }));
        
        allStores = stores; // Store globally
        
        if (stores.length === 0) {
            document.getElementById('allStoresList').innerHTML = `
                <div class="empty-state" style="grid-column: 1/-1;">
                    <i class="fas fa-store-slash empty-state-icon"></i>
                    <h3>No Stores Found</h3>
                    <p>Be the first to open a store!</p>
                </div>
            `;
            return;
        }
        
        let storesHTML = '';
        
        stores.forEach(store => {
            const storeName = store.shopName || store.name || 'Unknown Store';
            const safeStoreName = storeName.replace(/'/g, "\\'");
            const isFollowing = currentUserProfile?.followingSellers?.includes(store.id) || false;
            
            storesHTML += `
                <div class="product-card" onclick="viewSellerStore('${store.id}', '${safeStoreName}')">
                    <div style="height: 150px; display: flex; align-items: center; justify-content: center; background: var(--accent); border-radius: var(--radius) var(--radius) 0 0;">
                        ${store.shopLogo ? 
                            `<img src="${store.shopLogo}" alt="${storeName}" 
                                  style="max-width: 100px; max-height: 100px; object-fit: contain;">` :
                            `<i class="fas fa-store" style="font-size: 3rem; color: var(--primary);"></i>`
                        }
                    </div>
                    
                    <div class="product-info">
                        <h3 class="product-name" style="text-align: center;">${storeName}</h3>
                        
                        ${store.city || store.description ? `
                            <p style="color: var(--text-secondary); font-size: 0.9rem; text-align: center; margin: 0.5rem 0;">
                                ${store.city || (store.description ? store.description.substring(0, 50) + '...' : '')}
                            </p>
                        ` : ''}
                        
                        <div style="display: flex; justify-content: center; margin-top: 1rem;">
                            <button class="btn btn-sm ${isFollowing ? 'btn-warning' : 'btn-primary'}" 
                                    onclick="event.stopPropagation(); toggleFollowStore('${store.id}', '${safeStoreName}')">
                                <i class="fas ${isFollowing ? 'fa-check' : 'fa-plus'}"></i>
                                ${isFollowing ? 'Following' : 'Follow'}
                            </button>
                        </div>
                    </div>
                </div>
            `;
        });
        
        document.getElementById('allStoresList').innerHTML = storesHTML;
        
    } catch (error) {
        console.error('Error loading all stores:', error);
        document.getElementById('allStoresList').innerHTML = `
            <div class="empty-state" style="grid-column: 1/-1;">
                <i class="fas fa-exclamation-triangle empty-state-icon"></i>
                <h3>Error Loading Stores</h3>
                <p>${error.message}</p>
                <button class="btn btn-primary" onclick="showAllStores()">
                    <i class="fas fa-redo"></i> Try Again
                </button>
            </div>
        `;
    }
}

// Hide all pages helper
function hideAllPages() {
    const pages = [
        'homePage', 'productDetailsPage', 'cartPage', 'checkoutPage',
        'buyerProfilePage', 'ordersPage', 'orderTrackingPage', 'wishlistPage',
        'addressesPage', 'settingsPage', 'messagesPage', 'sellerStorePage', 
        'followingStoresPage', 'allStoresPage'
    ];
    
    pages.forEach(page => {
        const element = document.getElementById(page);
        if (element) element.style.display = 'none';
    });
}

// Update showHomePage function
function showHomePage() {
    hideAllPages();
    document.getElementById('homePage').style.display = 'block';
    
    // Load followed stores icons
    loadFollowedStoresIcons();
}

// ==================== INITIALIZATION ====================

// Add this to your DOMContentLoaded event listener
document.addEventListener('DOMContentLoaded', function() {
    // ... existing initialization code ...
    
    // Initialize followed stores
    setTimeout(() => {
        initializeFollowedStores();
    }, 1000);
    
    // Add event listener for message store form
    const messageStoreForm = document.getElementById('messageStoreForm');
    if (messageStoreForm) {
        messageStoreForm.addEventListener('submit', function(e) {
            e.preventDefault();
            handleMessageStore();
        });
    }
});

// Add to auth state change
auth.onAuthStateChanged(async function(user) {
    if (user) {
        // ... existing code ...
        
        // Initialize followed stores icons
        setTimeout(() => {
            loadFollowedStoresIcons();
        }, 500);
    } else {
        // Reset followed stores when user logs out
        if (document.getElementById('followedStoresIconsGrid')) {
            loadFollowedStoresIcons();
        }
    }
});

// Custom back function for product details
function goBackFromProductDetails() {
    cleanupProductPage();
    
    // Hide product details page
    document.getElementById('productDetailsPage').style.display = 'none';
    
    // Show home page
    document.getElementById('homePage').style.display = 'block';
    
    // Update navigation
    document.querySelectorAll('.nav-link').forEach(link => {
        link.classList.remove('active');
    });
    document.querySelector('.nav-link[data-page="home"]').classList.add('active');
}

// Media slider functions
function previousMedia() {
    if (productMediaArray.length <= 1) return;
    
    // Pause current video
    const currentMedia = productMediaArray[currentMediaIndex];
    if (currentMedia.type === 'video') {
        pauseVideoById(currentMedia.id);
    }
    
    currentMediaIndex = (currentMediaIndex - 1 + productMediaArray.length) % productMediaArray.length;
    goToMedia(currentMediaIndex);
}

function nextMedia() {
    if (productMediaArray.length <= 1) return;
    
    // Pause current video
    const currentMedia = productMediaArray[currentMediaIndex];
    if (currentMedia.type === 'video') {
        pauseVideoById(currentMedia.id);
    }
    
    currentMediaIndex = (currentMediaIndex + 1) % productMediaArray.length;
    goToMedia(currentMediaIndex);
}

function goToMedia(index) {
    if (index < 0 || index >= productMediaArray.length) return;
    
    // Pause current video
    const currentMedia = productMediaArray[currentMediaIndex];
    if (currentMedia.type === 'video') {
        pauseVideoById(currentMedia.id);
    }
    
    currentMediaIndex = index;
    
    // Update media slides
    document.querySelectorAll('.slider-media').forEach((mediaSlide, i) => {
        mediaSlide.classList.toggle('active', i === index);
    });
    
    // Update dots
    document.querySelectorAll('.slider-dot').forEach((dot, i) => {
        dot.classList.toggle('active', i === index);
    });
    
    // Update thumbnails
    const thumbnails = document.querySelectorAll('.thumbnail-btn');
    if (thumbnails.length > 0) {
        thumbnails.forEach((thumb, i) => {
            thumb.classList.toggle('active', i === index);
        });
    }
    
    // Update counter
    const counter = document.getElementById('mediaCounter');
    if (counter) {
        counter.textContent = `${index + 1} / ${productMediaArray.length}`;
    }
    
    // Show play overlay for video
    const newMedia = productMediaArray[index];
    if (newMedia.type === 'video') {
        const overlay = document.getElementById(`overlay-${newMedia.id}`);
        if (overlay) {
            overlay.style.display = 'flex';
        }
        
        // Update play button icon
        const video = document.getElementById(newMedia.id);
        if (video && video.paused) {
            const playBtn = video.parentElement.querySelector('.play-pause-btn i');
            if (playBtn) {
                playBtn.className = 'fas fa-play';
            }
        }
    }
}

function pauseVideoById(videoId) {
    const video = document.getElementById(videoId);
    if (video) {
        video.pause();
        activeVideos.delete(videoId);
        
        // Show overlay
        const overlay = document.getElementById(`overlay-${videoId}`);
        if (overlay) {
            overlay.style.display = 'flex';
        }
        
        // Update play button
        const playBtn = video.parentElement.querySelector('.play-pause-btn i');
        if (playBtn) {
            playBtn.className = 'fas fa-play';
        }
    }
}

function pauseAllActiveVideos() {
    productMediaArray.forEach((media) => {
        if (media.type === 'video') {
            const video = document.getElementById(media.id);
            if (video) {
                video.pause();
                video.currentTime = 0; // Reset to beginning
            }
        }
    });
    activeVideos.clear();
}

// Video player functions
function initializeVideoPlayers() {
    productMediaArray.forEach((media) => {
        if (media.type === 'video') {
            const video = document.getElementById(media.id);
            if (video) {
                // Remove all existing event listeners first by cloning
                const newVideo = video.cloneNode(true);
                video.parentNode.replaceChild(newVideo, video);
                
                const currentVideo = document.getElementById(media.id);
                
                // Hide overlay when video starts playing
                currentVideo.addEventListener('play', function() {
                    const overlay = document.getElementById(`overlay-${media.id}`);
                    if (overlay) overlay.style.display = 'none';
                    
                    const playBtn = this.parentElement.querySelector('.play-pause-btn i');
                    if (playBtn) playBtn.className = 'fas fa-pause';
                    
                    activeVideos.add(media.id);
                });
                
                // Show overlay when video pauses
                currentVideo.addEventListener('pause', function() {
                    const overlay = document.getElementById(`overlay-${media.id}`);
                    if (overlay && !this.ended) overlay.style.display = 'flex';
                    
                    const playBtn = this.parentElement.querySelector('.play-pause-btn i');
                    if (playBtn) playBtn.className = 'fas fa-play';
                    
                    activeVideos.delete(media.id);
                });
                
                // Show overlay when video ends
                currentVideo.addEventListener('ended', function() {
                    const overlay = document.getElementById(`overlay-${media.id}`);
                    if (overlay) overlay.style.display = 'flex';
                    
                    const playBtn = this.parentElement.querySelector('.play-pause-btn i');
                    if (playBtn) playBtn.className = 'fas fa-play';
                    
                    activeVideos.delete(media.id);
                });
                
                // Handle touch events for mobile
                currentVideo.addEventListener('touchend', function(e) {
                    e.preventDefault();
                    toggleVideoPlayback(media.id);
                });
                
                // Handle click on video itself
                currentVideo.addEventListener('click', function(e) {
                    e.stopPropagation();
                    toggleVideoPlayback(media.id);
                });
            }
        }
    });
}

function toggleVideoPlayback(videoId) {
    const video = document.getElementById(videoId);
    if (!video) return;
    
    if (video.paused) {
        video.play();
        activeVideos.add(videoId);
    } else {
        video.pause();
        activeVideos.delete(videoId);
    }
}

function toggleFullscreen(videoId) {
    const video = document.getElementById(videoId);
    if (!video) return;
    
    const videoWrapper = video.parentElement;
    
    if (!document.fullscreenElement) {
        if (videoWrapper.requestFullscreen) {
            videoWrapper.requestFullscreen();
        } else if (videoWrapper.webkitRequestFullscreen) {
            videoWrapper.webkitRequestFullscreen();
        } else if (videoWrapper.mozRequestFullScreen) {
            videoWrapper.mozRequestFullScreen();
        }
    } else {
        if (document.exitFullscreen) {
            document.exitFullscreen();
        } else if (document.webkitExitFullscreen) {
            document.webkitExitFullscreen();
        } else if (document.mozCancelFullScreen) {
            document.mozCancelFullScreen();
        }
    }
}

function changeProductQuantity(change) {
    const quantityInput = document.getElementById('productQuantity');
    if (!quantityInput) return;
    
    let currentQty = parseInt(quantityInput.value) || 1;
    const maxQty = parseInt(quantityInput.max) || 1;
    
    currentQty += change;
    if (currentQty < 1) currentQty = 1;
    if (currentQty > maxQty) currentQty = maxQty;
    
    quantityInput.value = currentQty;
    updateQuantityButtons();
}

function updateQuantityButtons() {
    const quantityInput = document.getElementById('productQuantity');
    if (!quantityInput) return;
    
    const currentQty = parseInt(quantityInput.value) || 1;
    const maxQty = parseInt(quantityInput.max) || 1;
    
    const decreaseBtn = document.getElementById('decreaseQty');
    const increaseBtn = document.getElementById('increaseQty');
    
    if (decreaseBtn) decreaseBtn.disabled = currentQty <= 1;
    if (increaseBtn) increaseBtn.disabled = currentQty >= maxQty;
}

function addToCartFromDetails(productId) {
    const product = products.find(p => p.id === productId);
    if (!product) return;
    
    const quantityInput = document.getElementById('productQuantity');
    if (!quantityInput) return;
    
    const quantity = parseInt(quantityInput.value) || 1;
    
    addToCart(productId, quantity);
}

// Helper functions for other actions
function addToWishlist(productId) {
    showToast('Added to wishlist!', 'success');
}

function shareProduct(productId) {
    if (navigator.share) {
        navigator.share({
            title: document.querySelector('.product-title')?.textContent || 'Product',
            text: 'Check out this product on Jeeto Pakistan!',
            url: window.location.href,
        });
    } else {
        navigator.clipboard.writeText(window.location.href);
        showToast('Link copied to clipboard!', 'success');
    }
}

function buyNow(productId) {
    const product = products.find(p => p.id === productId);
    if (!product) return;
    
    const quantityInput = document.getElementById('productQuantity');
    const quantity = quantityInput ? parseInt(quantityInput.value) || 1 : 1;
    
    addToCart(productId, quantity);
    setTimeout(() => {
        showCheckoutPage();
    }, 500);
}

// Override original showHomePage to include cleanup
const originalShowHomePage = showHomePage;
showHomePage = function() {
    cleanupProductPage();
    originalShowHomePage();
};

// Add this CSS for responsive design
const responsiveStyles = `
    /* Product Details Responsive */
    .product-details-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2rem;
    }
    
    @media (max-width: 768px) {
        .product-details-grid {
            grid-template-columns: 1fr;
            gap: 1.5rem;
        }
        
        .product-media-section {
            order: 1;
        }
        
        .product-info-section {
            order: 2;
        }
    }
    
    /* Media Slider Responsive */
    .product-media-slider {
        position: relative;
        width: 100%;
        height: 400px;
        overflow: hidden;
        border-radius: 12px;
        background: #f8f9fa;
    }
    
    @media (max-width: 768px) {
        .product-media-slider {
            height: 300px;
        }
    }
    
    @media (max-width: 480px) {
        .product-media-slider {
            height: 250px;
        }
    }
    
    .slider-media-container {
        position: relative;
        width: 100%;
        height: 100%;
    }
    
    .slider-media {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        opacity: 0;
        transition: opacity 0.3s ease;
        display: flex;
        align-items: center;
        justify-content: center;
        background: #f8f9fa;
    }
    
    .slider-media.active {
        opacity: 1;
        z-index: 1;
    }
    
    .slider-media-item {
        max-width: 100%;
        max-height: 100%;
        object-fit: contain;
    }
    
    /* Video Wrapper */
    .video-wrapper {
        position: relative;
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    
    .video-player {
        width: 100%;
        height: 100%;
        object-fit: contain;
        background: #000;
    }
    
    .video-controls {
        position: absolute;
        bottom: 10px;
        left: 0;
        right: 0;
        display: flex;
        justify-content: center;
        gap: 10px;
        padding: 8px;
        background: rgba(0, 0, 0, 0.5);
        z-index: 5;
        transition: opacity 0.3s;
    }
    
    .video-control-btn {
        background: rgba(255, 255, 255, 0.9);
        border: none;
        width: 36px;
        height: 36px;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: all 0.2s;
    }
    
    .video-control-btn:hover {
        background: white;
        transform: scale(1.1);
    }
    
    .video-play-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.3);
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        z-index: 4;
    }
    
    .video-play-overlay i {
        font-size: 4rem;
        color: white;
        opacity: 0.8;
    }
    
    /* Slider Controls */
    .slider-controls {
        position: absolute;
        top: 50%;
        left: 0;
        right: 0;
        transform: translateY(-50%);
        display: flex;
        justify-content: space-between;
        padding: 0 10px;
        z-index: 10;
    }
    
    .slider-btn {
        width: 40px;
        height: 40px;
        border-radius: 50%;
        background: rgba(0, 0, 0, 0.5);
        color: white;
        border: none;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: background 0.2s;
    }
    
    @media (max-width: 480px) {
        .slider-btn {
            width: 36px;
            height: 36px;
        }
    }
    
    .slider-btn:hover {
        background: rgba(0, 0, 0, 0.8);
    }
    
    /* Slider Navigation Dots */
    .slider-nav {
        position: absolute;
        bottom: 20px;
        left: 0;
        right: 0;
        display: flex;
        justify-content: center;
        gap: 8px;
        z-index: 10;
    }
    
    .slider-dot {
        width: 12px;
        height: 12px;
        border-radius: 50%;
        background: rgba(255, 255, 255, 0.5);
        border: none;
        cursor: pointer;
        transition: all 0.2s;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 8px;
        color: #fff;
        padding: 0;
    }
    
    .slider-dot.active {
        background: #007bff;
        transform: scale(1.2);
    }
    
    /* Media Counter */
    .media-counter {
        position: absolute;
        top: 15px;
        right: 15px;
        background: rgba(0, 0, 0, 0.7);
        color: white;
        padding: 4px 12px;
        border-radius: 20px;
        font-size: 14px;
        z-index: 10;
    }
    
    /* Thumbnails */
    .media-thumbnails {
        display: flex;
        gap: 8px;
        margin-top: 15px;
        overflow-x: auto;
        padding-bottom: 5px;
    }
    
    .thumbnail-btn {
        flex: 0 0 auto;
        width: 60px;
        height: 60px;
        border: 2px solid transparent;
        border-radius: 8px;
        overflow: hidden;
        cursor: pointer;
        padding: 0;
        background: #f8f9fa;
    }
    
    .thumbnail-btn.active {
        border-color: #007bff;
    }
    
    .thumbnail-btn img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
    
    .video-thumbnail {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background: #e9ecef;
        color: #6c757d;
        font-size: 10px;
    }
    
    .video-thumbnail i {
        font-size: 14px;
        margin-bottom: 2px;
    }
    
    /* Product Info Responsive */
    .product-header {
        margin-bottom: 1.5rem;
    }
    
    .product-title {
        color: #212529;
        font-size: 1.75rem;
        margin-bottom: 0.5rem;
    }
    
    @media (max-width: 768px) {
        .product-title {
            font-size: 1.5rem;
        }
    }
    
    .product-category {
        color: #6c757d;
        font-size: 0.9rem;
        margin-bottom: 0.75rem;
    }
    
    .product-rating {
        display: flex;
        align-items: center;
        gap: 8px;
    }
    
    .stars {
        color: #ffc107;
    }
    
    .rating-count {
        color: #6c757d;
        font-size: 0.9rem;
    }
    
    .price-availability-card {
        background: #f8f9fa;
        padding: 1.25rem;
        border-radius: 12px;
        margin-bottom: 1.5rem;
    }
    
    .price-section {
        display: flex;
        align-items: center;
        gap: 12px;
        margin-bottom: 1rem;
        flex-wrap: wrap;
    }
    
    .current-price {
        font-size: 2rem;
        font-weight: bold;
        color: #dc3545;
    }
    
    .original-price {
        font-size: 1.25rem;
        color: #6c757d;
        text-decoration: line-through;
    }
    
    .discount-badge {
        background: #dc3545;
        color: white;
        padding: 4px 8px;
        border-radius: 4px;
        font-size: 0.9rem;
        font-weight: bold;
    }
    
    .availability-section {
        display: flex;
        align-items: center;
        gap: 8px;
        margin-bottom: 0.75rem;
    }
    
    .availability-label {
        color: #6c757d;
    }
    
    .availability-status {
        font-weight: bold;
    }
    
    .availability-status.in-stock {
        color: #28a745;
    }
    
    .availability-status.out-of-stock {
        color: #dc3545;
    }
    
    .delivery-info {
        display: flex;
        align-items: center;
        gap: 8px;
        color: #007bff;
        font-size: 0.9rem;
    }
    
    /* Add to Cart Section */
    .add-to-cart-section {
        display: flex;
        gap: 12px;
        margin-bottom: 1.5rem;
        flex-wrap: wrap;
    }
    
    @media (max-width: 480px) {
        .add-to-cart-section {
            flex-direction: column;
        }
    }
    
    .quantity-controls {
        display: flex;
        align-items: center;
        gap: 4px;
    }
    
    .qty-btn {
        width: 40px;
        height: 40px;
        border: 1px solid #dee2e6;
        background: white;
        border-radius: 8px;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
    }
    
    .qty-btn:disabled {
        opacity: 0.5;
        cursor: not-allowed;
    }
    
    .qty-input {
        width: 60px;
        height: 40px;
        text-align: center;
        border: 1px solid #dee2e6;
        border-radius: 8px;
        font-size: 1rem;
    }
    
    .add-to-cart-btn, .buy-now-btn {
        flex: 1;
        min-width: 140px;
        height: 40px;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
    }
    
    @media (max-width: 480px) {
        .add-to-cart-btn, .buy-now-btn {
            width: 100%;
        }
    }
    
    .buy-now-btn {
        background: #ff6b35;
        color: white;
        border: none;
    }
    
    .buy-now-btn:hover {
        background: #e55a2b;
    }
    
    /* Action Buttons */
    .action-buttons {
        display: flex;
        gap: 12px;
        margin-bottom: 1.5rem;
        flex-wrap: wrap;
    }
    
    .action-btn {
        flex: 1;
        padding: 10px 16px;
        border: 1px solid #dee2e6;
        background: white;
        border-radius: 8px;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
        cursor: pointer;
        transition: all 0.2s;
        min-width: 120px;
    }
    
    @media (max-width: 480px) {
        .action-btn {
            min-width: 100px;
            font-size: 0.9rem;
        }
    }
    
    .action-btn:hover {
        background: #f8f9fa;
        border-color: #adb5bd;
    }
    
    /* Description & Specs */
    .product-description-section, .product-specs {
        margin-bottom: 1.5rem;
    }
    
    .product-description-section h3, .product-specs h3 {
        font-size: 1.25rem;
        margin-bottom: 1rem;
        color: #212529;
    }
    
    .description-content {
        line-height: 1.6;
        color: #495057;
    }
    
    .specs-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
        gap: 12px;
    }
    
    @media (max-width: 480px) {
        .specs-grid {
            grid-template-columns: 1fr;
        }
    }
    
    .spec-item {
        display: flex;
        justify-content: space-between;
        padding: 8px 0;
        border-bottom: 1px solid #e9ecef;
    }
    
    .spec-key {
        color: #6c757d;
        font-weight: 500;
    }
    
    .spec-value {
        color: #212529;
    }
    
    .no-specs {
        color: #6c757d;
        font-style: italic;
    }
    
    /* Out of Stock Notice */
    .out-of-stock-notice {
        display: flex;
        align-items: center;
        gap: 12px;
        padding: 1rem;
        background: #fff3cd;
        border: 1px solid #ffeaa7;
        border-radius: 8px;
        margin-bottom: 1.5rem;
        flex-wrap: wrap;
    }
    
    .out-of-stock-notice i {
        color: #f39c12;
    }
`;

// Add the CSS to the document
const styleSheet = document.createElement("style");
styleSheet.textContent = responsiveStyles;
document.head.appendChild(styleSheet);



// Helper functions for other actions
function addToWishlist(productId) {
    // Implement wishlist functionality
    showToast('Added to wishlist!', 'success');
}

function shareProduct(productId) {
    if (navigator.share) {
        navigator.share({
            title: document.querySelector('.product-title').textContent,
            text: 'Check out this product on Jeeto Pakistan!',
            url: window.location.href,
        });
    } else {
        // Fallback for desktop
        navigator.clipboard.writeText(window.location.href);
        showToast('Link copied to clipboard!', 'success');
    }
}

function buyNow(productId) {
    const product = products.find(p => p.id === productId);
    if (!product) return;
    
    const quantityInput = document.getElementById('productQuantity');
    const quantity = quantityInput ? parseInt(quantityInput.value) || 1 : 1;
    
    addToCart(productId, quantity);
    // Redirect to checkout
    setTimeout(() => {
        showCheckoutPage();
    }, 500);
}

function zoomMedia(mediaSrc) {
    // Implement zoom functionality for images
    console.log('Zoom media:', mediaSrc);
    // Could open a modal with larger image
}

// Message seller functions
function messageSellerFromProduct(sellerId, productId) {
    if (!currentUser) {
        showToast('Please login to message seller', 'error');
        openAuthModal('buyerLogin');
        return;
    }
    
    document.getElementById('messageSellerId').value = sellerId;
    document.getElementById('messageProductId').value = productId;
    openModal('messageSellerModal');
}

    async function handleMessageSeller(e) {
        e.preventDefault();
        
        const sellerId = document.getElementById('messageSellerId').value;
        const productId = document.getElementById('messageProductId').value;
        const subject = document.getElementById('messageSubject').value.trim();
        const message = document.getElementById('messageText').value.trim();
        
        if (!message) {
            showToast('Please enter a message', 'error');
            return;
        }
        
        try {
            // Get seller info
            const sellerDoc = await db.collection('sellers').doc(sellerId).get();
            const sellerData = sellerDoc.exists ? sellerDoc.data() : {};
            
            // Get product info
            const productDoc = await db.collection('products').doc(productId).get();
            const productData = productDoc.exists ? productDoc.data() : {};
            
            // Create or get conversation
            let conversationId;
            const convSnapshot = await db.collection('conversations')
                .where('buyerId', '==', currentUser.uid)
                .where('sellerId', '==', sellerId)
                .limit(1)
                .get();
            
            if (convSnapshot.empty) {
                const conversationData = {
                    buyerId: currentUser.uid,
                    buyerName: currentUserProfile?.displayName || currentUser.email,
                    buyerEmail: currentUser.email,
                    sellerId: sellerId,
                    sellerName: sellerData.shopName || sellerData.name,
                    productId: productId,
                    productName: productData.name,
                    lastMessage: message.substring(0, 100),
                    lastMessageAt: new Date(),
                    createdAt: new Date()
                };
                
                const convRef = await db.collection('conversations').add(conversationData);
                conversationId = convRef.id;
            } else {
                conversationId = convSnapshot.docs[0].id;
            }
            
            // Create message
            const messageData = {
                conversationId: conversationId,
                senderId: currentUser.uid,
                senderName: currentUserProfile?.displayName || currentUser.email,
                receiverId: sellerId,
                subject: subject || `Inquiry about ${productData.name}`,
                content: message,
                files: [],
                timestamp: new Date(),
                read: false
            };
            
            // Upload files if any
            if (messageFiles.length > 0) {
                const uploadedFiles = await uploadMessageFiles();
                messageData.files = uploadedFiles;
            }
            
            await db.collection('messages').add(messageData);
            
            // Update conversation
            await db.collection('conversations').doc(conversationId).update({
                lastMessage: message.substring(0, 100),
                lastMessageAt: new Date()
            });
            
            closeModal('messageSellerModal');
            showToast('Message sent successfully!', 'success');
            
            // Reset form
            document.getElementById('messageSellerForm').reset();
            messageFiles = [];
            document.getElementById('messageFilesPreview').innerHTML = '';
            
        } catch (error) {
            console.error('Error sending message:', error);
            showToast('Error sending message: ' + error.message, 'error');
        }
    }

    // ==================== SEARCH FUNCTIONS ====================
    function performSearch() {
        const searchTerm = document.getElementById('searchInput').value.trim().toLowerCase();
        
        if (!searchTerm) {
            showHomePage();
            return;
        }
        
        // Show search results section
        document.querySelectorAll('#mainContent > div').forEach(page => {
            page.style.display = 'none';
        });
        homePage.style.display = 'block';
        searchResultsSection.style.display = 'block';
        filterSection.style.display = 'block';
        
        // Filter products
        const filteredProducts = products.filter(product => 
            product.name.toLowerCase().includes(searchTerm) ||
            product.category.toLowerCase().includes(searchTerm) ||
            product.description.toLowerCase().includes(searchTerm) ||
            (product.brand && product.brand.toLowerCase().includes(searchTerm))
        );
        
        const resultsContainer = document.getElementById('searchResults');
        
        if (filteredProducts.length === 0) {
            resultsContainer.innerHTML = `
                <div style="grid-column: 1 / -1; text-align: center; padding: 3rem;">
                    <i class="fas fa-search" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                    <h3>No Results Found</h3>
                    <p>We couldn't find any products matching "${searchTerm}"</p>
                    <button class="btn btn-primary" onclick="showAllProducts()" style="margin-top: 1rem;">
                        <i class="fas fa-boxes"></i> Browse All Products
                    </button>
                </div>
            `;
        } else {
            resultsContainer.innerHTML = filteredProducts.map(product => createProductCard(product)).join('');
        }
        
        updateSortButtons();
    }

    function clearSearch() {
        document.getElementById('searchInput').value = '';
        showHomePage();
    }
// ==================== FULL SCREEN SEARCH FUNCTIONS ====================

let searchHistory = JSON.parse(localStorage.getItem('searchHistory')) || [];
let currentSearchResults = [];
let currentFilters = {
    category: [],
    minPrice: 0,
    maxPrice: 100000
};

let searchCurrentPage = 1;
const searchResultsPerPage = 12;

// Open search home page
function openSearchHome() {
    console.log('Opening search home');
    
    // Hide all other pages
    hideAllPages();
    
    // Show search home
    document.getElementById('fullScreenSearchHome').classList.add('active');
    
    // Focus on input
    setTimeout(() => {
        const input = document.getElementById('searchHomeInput');
        if (input) {
            input.focus();
            input.select();
        }
    }, 100);
    
    // Load recent searches
    loadRecentSearches();
}

// Close search home
function closeSearchHome() {
    document.getElementById('fullScreenSearchHome').classList.remove('active');
    showHomePage();
}

// Load recent searches
function loadRecentSearches() {
    const container = document.getElementById('recentSearchesList');
    if (!container) return;
    
    if (searchHistory.length === 0) {
        container.innerHTML = `
            <div style="text-align: center; padding: 2rem; color: var(--text-secondary);">
                <i class="fas fa-search" style="font-size: 2rem; opacity: 0.5; margin-bottom: 1rem;"></i>
                <p>No recent searches</p>
            </div>
        `;
        return;
    }
    
    container.innerHTML = searchHistory.map(item => `
        <div class="recent-search-item" onclick="searchKeyword('${escapeHtml(item)}')">
            <i class="fas fa-history"></i>
            <span class="recent-search-text">${escapeHtml(item)}</span>
            <button class="delete-search-item" onclick="event.stopPropagation(); clearSearchHistoryItem('${escapeHtml(item)}')">
                <i class="fas fa-times"></i>
            </button>
        </div>
    `).join('');
}

// Handle search input
function handleSearchInput(value) {
    const clearBtn = document.getElementById('clearSearchBtn');
    if (clearBtn) {
        clearBtn.style.display = value.trim() ? 'block' : 'none';
    }
}

// Clear search input
function clearSearchInput() {
    document.getElementById('searchHomeInput').value = '';
    document.getElementById('clearSearchBtn').style.display = 'none';
    document.getElementById('searchHomeInput').focus();
}

// Clear search history item
function clearSearchHistoryItem(item) {
    searchHistory = searchHistory.filter(search => search !== item);
    localStorage.setItem('searchHistory', JSON.stringify(searchHistory));
    loadRecentSearches();
}

// Clear all search history
function clearAllSearchHistory() {
    if (confirm('Clear all search history?')) {
        searchHistory = [];
        localStorage.removeItem('searchHistory');
        loadRecentSearches();
        showToast('Search history cleared', 'success');
    }
}

// Save to search history
function saveToSearchHistory(query) {
    if (!query.trim()) return;
    
    // Remove if already exists
    searchHistory = searchHistory.filter(item => item.toLowerCase() !== query.toLowerCase());
    
    // Add to beginning
    searchHistory.unshift(query);
    
    // Keep only last 10
    searchHistory = searchHistory.slice(0, 10);
    
    // Save to localStorage
    localStorage.setItem('searchHistory', JSON.stringify(searchHistory));
    
    // Update display
    loadRecentSearches();
}

// Perform search
function performSearch(query) {
    if (!query.trim()) {
        showToast('Please enter a search term', 'warning');
        return;
    }
    
    // Save to history
    saveToSearchHistory(query);
    
    // Close search home
    document.getElementById('fullScreenSearchHome').classList.remove('active');
    
    // Open search results
    openSearchResults(query);
}

// Search by keyword
function searchKeyword(keyword) {
    saveToSearchHistory(keyword);
    document.getElementById('fullScreenSearchHome').classList.remove('active');
    openSearchResults(keyword);
}

// Search by category
function searchByCategory(category) {
    saveToSearchHistory(category);
    document.getElementById('fullScreenSearchHome').classList.remove('active');
    openSearchResults(category);
}

// Open search results
function openSearchResults(query) {
    currentSearchQuery = query;
    searchCurrentPage = 1;
    
    // Hide all pages
    hideAllPages();
    
    // Show search results
    document.getElementById('fullScreenSearchResults').classList.add('active');
    
    // Set search query in UI
    document.getElementById('currentSearchQuery').textContent = query;
    document.getElementById('searchResultsInput').value = query;
    
    // Reset filters
    resetAllFilters();
    
    // Perform search
    searchProductsInResults(query);
}

// Back to search page
function backToSearchPage() {
    document.getElementById('fullScreenSearchResults').classList.remove('active');
    openSearchHome();
}

// Close search and go to home
function closeSearchAndGoHome() {
    document.getElementById('fullScreenSearchResults').classList.remove('active');
    document.getElementById('fullScreenSearchHome').classList.remove('active');
    showHomePage();
}

// Toggle filter dropdown
function toggleFilterDropdown(type) {
    const dropdowns = document.querySelectorAll('.filter-dropdown');
    dropdowns.forEach(dropdown => {
        if (dropdown.id !== type + 'FilterDropdown') {
            dropdown.classList.remove('active');
        }
    });
    
    const dropdown = document.getElementById(type + 'FilterDropdown');
    if (dropdown) {
        dropdown.classList.toggle('active');
    }
}

// Update category filter
function updateCategoryFilter() {
    const checkboxes = document.querySelectorAll('#categoryFilterDropdown input[type="checkbox"]:checked');
    currentFilters.category = Array.from(checkboxes).map(cb => cb.value);
    applyFilters();
}

// Update price filter
function updatePriceFilter() {
    const min = parseInt(document.getElementById('minPriceFilter').value) || 0;
    const max = parseInt(document.getElementById('maxPriceFilter').value) || 100000;
    
    currentFilters.minPrice = min;
    currentFilters.maxPrice = max;
    applyFilters();
}

// Update price range
function updatePriceRange() {
    const minSlider = document.getElementById('priceRangeMin');
    const maxSlider = document.getElementById('priceRangeMax');
    const minInput = document.getElementById('minPriceFilter');
    const maxInput = document.getElementById('maxPriceFilter');
    
    minInput.value = minSlider.value;
    maxInput.value = maxSlider.value;
    
    updatePriceFilter();
}

// Reset all filters
function resetAllFilters() {
    currentFilters = {
        category: [],
        minPrice: 0,
        maxPrice: 100000
    };
    
    document.querySelectorAll('.filter-dropdown input[type="checkbox"]').forEach(cb => {
        cb.checked = false;
    });
    
    document.getElementById('minPriceFilter').value = '';
    document.getElementById('maxPriceFilter').value = '';
    document.getElementById('priceRangeMin').value = 0;
    document.getElementById('priceRangeMax').value = 100000;
    
    currentSort = 'relevance';
    document.getElementById('resultsSort').value = 'relevance';
    
    applyFilters();
}

// Apply search filter
function applySearchFilter(filter) {
    // This is for the "All" button
    if (filter === 'all') {
        resetAllFilters();
    }
    applyFilters();
}

// Apply filters
function applyFilters() {
    if (!currentSearchQuery) return;
    
    showSearchLoading(true);
    
    setTimeout(() => {
        const filtered = filterProducts(currentSearchResults);
        displaySearchResults(filtered);
        showSearchLoading(false);
    }, 300);
}

// Filter products
function filterProducts(products) {
    return products.filter(product => {
        // Category filter
        if (currentFilters.category.length > 0) {
            if (!currentFilters.category.includes(product.category)) {
                return false;
            }
        }
        
        // Price filter
        if (product.price < currentFilters.minPrice || product.price > currentFilters.maxPrice) {
            return false;
        }
        
        return true;
    });
}

// Sort search results
function sortSearchResults(sortType) {
    currentSort = sortType;
    applyFilters();
}

// Search products in results
function searchProductsInResults(query) {
    if (query.trim()) {
        currentSearchQuery = query;
        document.getElementById('currentSearchQuery').textContent = query;
        saveToSearchHistory(query);
        
        // Show loading
        showSearchLoading(true);
        hideNoResults();
        
        // Simulate search
        setTimeout(() => {
            const allProducts = [...products]; // Use your existing products array
            const searchLower = query.toLowerCase();
            
            currentSearchResults = allProducts.filter(product => {
                return (
                    (product.name && product.name.toLowerCase().includes(searchLower)) ||
                    (product.description && product.description.toLowerCase().includes(searchLower)) ||
                    (product.category && product.category.toLowerCase().includes(searchLower))
                );
            });
            
            // Sort results
            sortResults(currentSearchResults, currentSort);
            
            // Display results
            displaySearchResults(currentSearchResults);
            showSearchLoading(false);
            
            if (currentSearchResults.length === 0) {
                showNoResults();
            }
        }, 500);
    }
}

// Sort results
function sortResults(results, sortType) {
    switch(sortType) {
        case 'price_low':
            return results.sort((a, b) => (a.price || 0) - (b.price || 0));
        case 'price_high':
            return results.sort((a, b) => (b.price || 0) - (a.price || 0));
        case 'rating':
            return results.sort((a, b) => (b.rating || 0) - (a.rating || 0));
        case 'newest':
            return results.sort((a, b) => new Date(b.createdAt || 0) - new Date(a.createdAt || 0));
        default:
            return results;
    }
}

// Display search results
function displaySearchResults(results) {
    const grid = document.getElementById('searchProductsGrid');
    const countElement = document.getElementById('resultsCount');
    
    if (!grid || !countElement) return;
    
    countElement.textContent = results.length;
    
    // Pagination
    const totalPages = Math.ceil(results.length / searchResultsPerPage);
    const startIndex = (searchCurrentPage - 1) * searchResultsPerPage;
    const endIndex = startIndex + searchResultsPerPage;
    const pageResults = results.slice(startIndex, endIndex);
    
    if (pageResults.length === 0) {
        grid.innerHTML = '';
        showNoResults();
        return;
    }
    
    // Display products (2 per row)
    grid.innerHTML = pageResults.map(product => `
        <div class="search-product-card" onclick="showProductDetails('${product.id}')">
            ${product.discount ? `<div class="search-product-badge">${product.discount}% OFF</div>` : ''}
            <div class="search-product-image-container">
                <img src="${product.images && product.images.length > 0 ? product.images[0] : 'https://via.placeholder.com/300x200?text=No+Image'}" 
                     alt="${product.name || 'Product'}" 
                     class="search-product-image"
                     loading="lazy">
            </div>
            <div class="search-product-info">
                <h3 class="search-product-name">${escapeHtml(product.name || 'Unnamed Product')}</h3>
                <div class="search-product-price">
                    <span class="search-current-price">Rs. ${(product.price || 0).toLocaleString()}</span>
                    ${product.originalPrice ? `<span class="search-original-price">Rs. ${product.originalPrice.toLocaleString()}</span>` : ''}
                    ${product.discount ? `<span class="search-product-discount">${product.discount}% off</span>` : ''}
                </div>
            </div>
        </div>
    `).join('');
    
    // Display pagination
    displaySearchPagination(totalPages);
}

// Display pagination
function displaySearchPagination(totalPages) {
    const container = document.getElementById('searchPagination');
    if (!container) return;
    
    if (totalPages <= 1) {
        container.innerHTML = '';
        return;
    }
    
    let html = '';
    
    // Previous button
    html += `<button class="search-page-btn" ${searchCurrentPage === 1 ? 'disabled' : ''} onclick="goToSearchPage(${searchCurrentPage - 1})">
        <i class="fas fa-chevron-left"></i>
    </button>`;
    
    // Page numbers
    for (let i = 1; i <= Math.min(5, totalPages); i++) {
        html += `<button class="search-page-btn ${i === searchCurrentPage ? 'active' : ''}" onclick="goToSearchPage(${i})">${i}</button>`;
    }
    
    // Next button
    html += `<button class="search-page-btn" ${searchCurrentPage === totalPages ? 'disabled' : ''} onclick="goToSearchPage(${searchCurrentPage + 1})">
        <i class="fas fa-chevron-right"></i>
    </button>`;
    
    container.innerHTML = html;
}

// Go to search page
function goToSearchPage(page) {
    if (page < 1 || page > Math.ceil(currentSearchResults.length / searchResultsPerPage)) return;
    
    searchCurrentPage = page;
    displaySearchResults(currentSearchResults);
}

// Show search loading
function showSearchLoading(show) {
    const loading = document.getElementById('searchLoading');
    if (loading) {
        loading.classList.toggle('active', show);
    }
}

// Show no results
function showNoResults() {
    const noResults = document.getElementById('noSearchResults');
    if (noResults) {
        noResults.classList.add('active');
    }
}

// Hide no results
function hideNoResults() {
    const noResults = document.getElementById('noSearchResults');
    if (noResults) {
        noResults.classList.remove('active');
    }
}

// Update hideAllPages function
function hideAllPages() {
    // Hide all main pages
    const pages = [
        'homePage', 'productDetailsPage', 'cartPage', 'checkoutPage',
        'buyerProfilePage', 'ordersPage', 'orderTrackingPage', 'wishlistPage',
        'addressesPage', 'settingsPage', 'messagesPage', 'notificationsPage'
    ];
    
    pages.forEach(page => {
        const element = document.getElementById(page);
        if (element) element.style.display = 'none';
    });
    
    // Hide seller panel
    document.getElementById('sellerPanel').style.display = 'none';
    
    // Hide search pages
    document.getElementById('fullScreenSearchHome').classList.remove('active');
    document.getElementById('fullScreenSearchResults').classList.remove('active');
    
    // Hide modals
    document.querySelectorAll('.modal, .payment-verification, .auth-modal, .forgot-password-modal, .invoice-modal').forEach(modal => {
        modal.classList.remove('active');
    });
}

    // ==================== DISPLAY FUNCTIONS ====================
    function displayCategories() {
        const categoriesGrid = document.getElementById('categoriesGrid');
        categoriesGrid.innerHTML = categories.map(category => `
            <div class="category-card" onclick="filterProductsByCategory('${category.name}')">
                <div class="category-icon">
                    <i class="fas fa-${category.icon}"></i>
                </div>
                <div class="category-name">${category.name}</div>
            </div>
        `).join('');
    }

    function displayProducts() {
        const featuredProducts = document.getElementById('featuredProducts');
        
        if (products.length === 0) {
            featuredProducts.innerHTML = `
                <div style="grid-column: 1 / -1; text-align: center; padding: 3rem;">
                    <i class="fas fa-box-open" style="font-size: 3rem; color: var(--text-secondary); margin-bottom: 1rem;"></i>
                    <h3>No Products Available</h3>
                    <p>Check back soon for new products</p>
                </div>
            `;
            return;
        }
        
        featuredProducts.innerHTML = products
            .slice(0, productsPerPage)
            .map(product => createProductCard(product))
            .join('');
        
        updatePagination();
    }

    function createProductCard(product) {
    const finalPrice = calculateFinalPrice(product.price, product.discount || 0);
    const hasVideo = product.video || product.hasVideo;
    const imageCount = product.images ? product.images.length : 0;
    const totalMedia = imageCount + (hasVideo ? 1 : 0);
    
    return `
        <div class="product-card" onclick="viewProductDetails('${product.id}')">
            <!-- Discount Badge -->
            ${product.discount > 0 ? `
                <div class="product-badge" style="background: var(--error);">
                    ${product.discount}% OFF
                </div>
            ` : ''}
            
            <!-- Media Count Badge -->
            ${totalMedia > 1 ? `
                <div class="image-count">
                    <i class="fas fa-camera"></i> ${totalMedia}
                </div>
            ` : ''}
            
            <!-- Video Badge -->
            ${hasVideo ? `
                <div class="video-badge">
                    <i class="fas fa-video"></i>
                </div>
            ` : ''}
            
            <!-- Product Image -->
            <img src="${product.images && product.images.length > 0 ? product.images[0] : 'https://via.placeholder.com/400x400?text=Product+Image'}" 
                 alt="${escapeHtml(product.name)}" 
                 class="product-image">
            
            <div class="product-info">
                <div class="product-category">${escapeHtml(product.category)}</div>
                <div class="product-name">${escapeHtml(product.name)}</div>
                
                <div class="product-rating">
                    ${generateStarRating(product.rating)}
                    <span style="color: var(--text-secondary); font-size: 0.9rem;">(${product.reviewsCount || 0})</span>
                </div>
                
                <div class="product-price">
                    <span class="current-price">Rs. ${finalPrice.toLocaleString()}</span>
                    ${product.discount > 0 ? `
                        <span class="original-price">Rs. ${product.price.toLocaleString()}</span>
                    ` : ''}
                </div>
                
                <div class="product-seller">
                    <i class="fas fa-store"></i> ${escapeHtml(product.sellerName)}
                </div>
                
                <div class="product-actions">
                    <button class="add-to-cart" onclick="event.stopPropagation(); addToCart('${product.id}')">
                        <i class="fas fa-shopping-cart"></i> Add to Cart
                    </button>
                    <button class="btn btn-sm btn-info" onclick="event.stopPropagation(); quickShare('${product.id}', '${escapeHtml(product.name)}')" title="Share">
                        <i class="fas fa-share-alt"></i>
                    </button>
                    <button class="btn btn-sm btn-secondary" onclick="event.stopPropagation(); addToWishlist('${product.id}')" title="Wishlist">
                        <i class="far fa-heart"></i>
                    </button>
                </div>
            </div>
        </div>
    `;
}

/// Quick share function for product cards
function quickShare(productId, productName) {
    event.stopPropagation();
    
    const shareUrl = generateShareLink(productId);
    const text = `Check out "${productName}" on Jeeto Pakistan!\n\n${shareUrl}`;
    
    if (navigator.share) {
        navigator.share({
            title: productName,
            text: text,
            url: shareUrl
        }).catch(err => {
            if (err.name !== 'AbortError') {
                copyProductLink(productId);
            }
        });
    } else {
        copyProductLink(productId);
    }
}

// Keyboard navigation for media slider
document.addEventListener('keydown', function(e) {
    if (e.key === 'ArrowLeft') {
        previousMedia();
    } else if (e.key === 'ArrowRight') {
        nextMedia();
    }
});

// Touch/swipe support for mobile
let touchStartX = 0;
let touchEndX = 0;

function handleTouchStart(e) {
    touchStartX = e.changedTouches[0].screenX;
}

function handleTouchEnd(e) {
    touchEndX = e.changedTouches[0].screenX;
    handleSwipe();
}

function handleSwipe() {
    const swipeThreshold = 50;
    const diff = touchStartX - touchEndX;
    
    if (Math.abs(diff) > swipeThreshold) {
        if (diff > 0) {
            // Swipe left - next media
            nextMedia();
        } else {
            // Swipe right - previous media
            previousMedia();
        }
    }
}

// Add event listeners for touch
document.addEventListener('DOMContentLoaded', function() {
    const slider = document.getElementById('enhancedSlider');
    if (slider) {
        slider.addEventListener('touchstart', handleTouchStart);
        slider.addEventListener('touchend', handleTouchEnd);
    }
});
    function displayFlashSaleProducts() {
    const flashSaleContainer = document.getElementById('flashSaleProducts');
    
    if (flashSales.length === 0) {
        flashSaleContainer.innerHTML = `
            <div style="grid-column: 1 / -1; text-align: center; padding: 2rem; color: var(--text-secondary);">
                <i class="fas fa-bolt" style="font-size: 2rem; margin-bottom: 1rem;"></i>
                <h4>No Flash Sales Active</h4>
                <p>Check back later for exciting deals!</p>
            </div>
        `;
        return;
    }
    
    // Get flash sale products from main products array
    const flashSaleProducts = flashSales.map(flashSale => {
        const product = products.find(p => p.id === flashSale.productId);
        return product ? { ...product, flashSale } : null;
    }).filter(p => p !== null);
    
    if (flashSaleProducts.length === 0) {
        flashSaleContainer.innerHTML = `
            <div style="grid-column: 1 / -1; text-align: center; padding: 2rem; color: var(--text-secondary);">
                <i class="fas fa-bolt" style="font-size: 2rem; margin-bottom: 1rem;"></i>
                <h4>No Flash Sale Products Available</h4>
                <p>Flash sale products are currently out of stock</p>
            </div>
        `;
        return;
    }
    
    flashSaleContainer.innerHTML = flashSaleProducts.map(item => {
        const product = item;
        const flashSale = item.flashSale;
        
        return `
            <div class="product-card">
                <div class="product-badge" style="background: var(--error);">FLASH SALE</div>
                <div style="position: absolute; top: 10px; right: 10px; background: rgba(0,0,0,0.7); color: white; padding: 5px 10px; border-radius: 4px; font-size: 0.8rem;">
                    Ends in: ${formatTimeRemaining(flashSale.endDate)}
                </div>
                <img src="${product.images?.[0] || 'https://res.cloudinary.com/df8t8uapf/image/upload/v1701700000/product-placeholder_eknfqf.jpg'}" 
                     class="product-image" 
                     alt="${escapeHtml(product.name)}"
                     onclick="viewProductDetails('${product.id}')">
                <div class="product-info">
                    <div class="product-category">${escapeHtml(product.category || '')}</div>
                    <div class="product-name" onclick="viewProductDetails('${product.id}')">${escapeHtml(product.name)}</div>
                    <div class="product-price">
                        <span class="current-price">Rs. ${flashSale?.flashPrice?.toLocaleString() || product.price.toLocaleString()}</span>
                        <span class="original-price">Rs. ${product.price.toLocaleString()}</span>
                    </div>
                    <div class="product-seller">
                        <i class="fas fa-store"></i> ${escapeHtml(product.sellerName || 'Seller')}
                    </div>
                    <div class="product-actions">
                        <button class="add-to-cart" onclick="addToCart('${product.id}')" ${product.quantity <= 0 ? 'disabled' : ''}>
                            <i class="fas fa-shopping-cart"></i> Buy Now
                        </button>
                    </div>
                </div>
            </div>
        `;
    }).join('');
}
    function displayTopSellers() {
        const topSellersGrid = document.getElementById('topSellersGrid');
        
        // Get top sellers by product count
        const sellerStats = {};
        products.forEach(product => {
            if (!sellerStats[product.sellerId]) {
                sellerStats[product.sellerId] = {
                    id: product.sellerId,
                    name: product.sellerName,
                    productCount: 0,
                    rating: 0
                };
            }
            sellerStats[product.sellerId].productCount++;
        });
        
        const topSellers = Object.values(sellerStats)
            .sort((a, b) => b.productCount - a.productCount)
            .slice(0, 6);
        
        topSellersGrid.innerHTML = topSellers.map(seller => `
            <div class="category-card" onclick="filterProductsBySeller('${seller.id}')">
                <div class="category-icon">
                    <i class="fas fa-store"></i>
                </div>
                <div class="category-name">${escapeHtml(seller.name)}</div>
                <div style="font-size: 0.8rem; color: var(--text-secondary); margin-top: 0.5rem;">
                    ${seller.productCount} products
                </div>
            </div>
        `).join('');
    }

    function displayNotifications() {
        const notificationList = document.getElementById('notificationList');
        
        if (notifications.length === 0) {
            notificationList.innerHTML = `
                <div class="notification-item">
                    <p style="text-align: center; color: var(--text-secondary); padding: 1rem;">No notifications</p>
                </div>
            `;
            return;
        }
        
        notificationList.innerHTML = notifications.map(notification => `
            <div class="notification-item ${notification.read ? '' : 'unread'}" onclick="markNotificationAsRead('${notification.id}')">
                <div style="font-weight: 500; margin-bottom: 0.25rem;">${escapeHtml(notification.title || 'Notification')}</div>
                <div style="font-size: 0.9rem; color: var(--text-secondary);">${escapeHtml(notification.message || '')}</div>
                <div style="font-size: 0.8rem; color: var(--text-secondary); margin-top: 0.25rem;">
                    ${notification.createdAt?.toDate ? notification.createdAt.toDate().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'}) : ''}
                </div>
            </div>
        `).join('');
    }

    function populateCategorySelect() {
        const categorySelect = document.getElementById('productCategory');
        if (categorySelect) {
            categorySelect.innerHTML = '<option value="">Select Category</option>' + 
                categories.map(cat => `<option value="${cat.name}">${cat.name}</option>`).join('');
        }
    }

    function filterProductsByCategory(category) {
        showAllProducts();
        currentFilterCategory = category;
        filterProducts();
    }

    function filterProductsBySeller(sellerId) {
        showAllProducts();
        const seller = sellers.find(s => s.id === sellerId);
        if (seller) {
            currentFilterCategory = null;
            filterProducts();
        }
    }

    function filterProducts() {
        let filteredProducts = [...products];
        
        // Filter by category
        if (currentFilterCategory) {
            filteredProducts = filteredProducts.filter(p => p.category === currentFilterCategory);
        }
        
        // Apply current sort
        sortProducts(currentSort, filteredProducts);
    }

    function sortProducts(sortType, productList = null) {
        currentSort = sortType;
        let productsToSort = productList || [...products];
        
        switch(sortType) {
            case 'price-low':
                productsToSort.sort((a, b) => (a.price || 0) - (b.price || 0));
                break;
            case 'price-high':
                productsToSort.sort((a, b) => (b.price || 0) - (a.price || 0));
                break;
            case 'newest':
                productsToSort.sort((a, b) => (b.createdAt || 0) - (a.createdAt || 0));
                break;
            case 'rating':
                productsToSort.sort((a, b) => (b.rating || 0) - (a.rating || 0));
                break;
            default:
                // Keep original order
                break;
        }
        
        updateSortButtons();
        
        const featuredContainer = document.getElementById('featuredProducts');
        featuredContainer.innerHTML = productsToSort
            .slice(0, productsPerPage)
            .map(product => createProductCard(product))
            .join('');
    }

    // Update sort buttons when active
function updateSortButtons() {
    const sortBtns = document.querySelectorAll('.sort-btn');
    sortBtns.forEach(btn => {
        btn.classList.remove('active');
    });
    
    // Find and activate the current sort button
    const currentSortBtn = document.querySelector(`.sort-btn[onclick*="${currentSort}"]`);
    if (currentSortBtn) {
        currentSortBtn.classList.add('active');
    }
}

// Toggle advanced filter
// ==================== FILTER FUNCTIONS ====================

// Toggle advanced filter
function toggleAdvancedFilter() {
    const advancedFilter = document.getElementById('advancedFilter');
    advancedFilter.classList.toggle('active');
    
    const toggleBtn = event.target.closest('button');
    if (toggleBtn) {
        if (advancedFilter.classList.contains('active')) {
            toggleBtn.innerHTML = '<i class="fas fa-times"></i> Close Filter';
        } else {
            toggleBtn.innerHTML = '<i class="fas fa-sliders-h"></i> Advanced Filter';
        }
    }
}

// Update sort buttons
function updateSortButtons() {
    const sortBtns = document.querySelectorAll('.sort-btn');
    sortBtns.forEach(btn => {
        btn.classList.remove('active');
    });
    
    // Find the active button based on onclick attribute
    const activeBtn = document.querySelector(`.sort-btn[onclick*="${currentSort}"]`);
    if (activeBtn) {
        activeBtn.classList.add('active');
    }
}

// Sort products
function sortProducts(sortType) {
    currentSort = sortType;
    let sortedProducts = [...products];
    
    switch(sortType) {
        case 'price-low':
            sortedProducts.sort((a, b) => {
                const priceA = a.price - (a.price * (a.discount || 0) / 100);
                const priceB = b.price - (b.price * (b.discount || 0) / 100);
                return priceA - priceB;
            });
            break;
        case 'price-high':
            sortedProducts.sort((a, b) => {
                const priceA = a.price - (a.price * (a.discount || 0) / 100);
                const priceB = b.price - (b.price * (b.discount || 0) / 100);
                return priceB - priceA;
            });
            break;
        case 'newest':
            sortedProducts.sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt));
            break;
        case 'rating':
            sortedProducts.sort((a, b) => (b.rating || 0) - (a.rating || 0));
            break;
        default:
            sortedProducts = products;
    }
    
    const featuredContainer = document.getElementById('featuredProducts');
    featuredContainer.innerHTML = sortedProducts.map(product => createProductCard(product)).join('');
    
    updateSortButtons();
    showToast(`Sorted by: ${getSortLabel(sortType)}`, 'info');
}

function getSortLabel(sortType) {
    switch(sortType) {
        case 'default': return 'Default';
        case 'price-low': return 'Price: Low to High';
        case 'price-high': return 'Price: High to Low';
        case 'newest': return 'Newest';
        case 'rating': return 'Top Rated';
        default: return sortType;
    }
}

// Apply price filter
function applyPriceFilter() {
    const minPrice = parseFloat(document.getElementById('minPrice').value) || 0;
    const maxPrice = parseFloat(document.getElementById('maxPrice').value) || Infinity;
    
    const filteredProducts = products.filter(product => {
        const finalPrice = product.price - (product.price * (product.discount || 0) / 100);
        return finalPrice >= minPrice && finalPrice <= maxPrice;
    });
    
    const featuredContainer = document.getElementById('featuredProducts');
    featuredContainer.innerHTML = filteredProducts.map(product => createProductCard(product)).join('');
    
    showToast(`Price filter applied: Rs. ${minPrice} - Rs. ${maxPrice === Infinity ? '∞' : maxPrice}`, 'success');
}

// Apply category filter
function applyCategoryFilter() {
    const category = document.getElementById('categoryFilter').value;
    
    if (!category) {
        displayProducts();
        return;
    }
    
    const filteredProducts = products.filter(product => product.category === category);
    const featuredContainer = document.getElementById('featuredProducts');
    featuredContainer.innerHTML = filteredProducts.map(product => createProductCard(product)).join('');
    
    showToast(`Showing ${category} products`, 'success');
}

// Apply rating filter
function applyRatingFilter() {
    const rating = parseFloat(document.getElementById('ratingFilter').value);
    
    if (!rating) {
        displayProducts();
        return;
    }
    
    const filteredProducts = products.filter(product => (product.rating || 0) >= rating);
    const featuredContainer = document.getElementById('featuredProducts');
    featuredContainer.innerHTML = filteredProducts.map(product => createProductCard(product)).join('');
    
    showToast(`Showing products with ${rating}+ stars rating`, 'success');
}

    function updatePagination() {
        const totalPages = Math.ceil(products.length / productsPerPage);
        const paginationContainer = document.getElementById('productPagination');
        
        if (totalPages <= 1) {
            paginationContainer.innerHTML = '';
            return;
        }
        
        let paginationHTML = '';
        
        // Previous button
        if (currentPage > 1) {
            paginationHTML += `<button class="page-btn" onclick="changePage(${currentPage - 1})"><i class="fas fa-chevron-left"></i></button>`;
        }
        
        // Page numbers
        for (let i = 1; i <= totalPages; i++) {
            if (i === currentPage) {
                paginationHTML += `<button class="page-btn active">${i}</button>`;
            } else if (i === 1 || i === totalPages || (i >= currentPage - 2 && i <= currentPage + 2)) {
                paginationHTML += `<button class="page-btn" onclick="changePage(${i})">${i}</button>`;
            } else if (i === currentPage - 3 || i === currentPage + 3) {
                paginationHTML += `<button class="page-btn" disabled>...</button>`;
            }
        }
        
        // Next button
        if (currentPage < totalPages) {
            paginationHTML += `<button class="page-btn" onclick="changePage(${currentPage + 1})"><i class="fas fa-chevron-right"></i></button>`;
        }
        
        paginationContainer.innerHTML = paginationHTML;
    }

    function changePage(page) {
        currentPage = page;
        const startIndex = (page - 1) * productsPerPage;
        const endIndex = startIndex + productsPerPage;
        
        const featuredProducts = document.getElementById('featuredProducts');
        featuredProducts.innerHTML = products
            .slice(startIndex, endIndex)
            .map(product => createProductCard(product))
            .join('');
        
        updatePagination();
    }

    // ==================== AUTH MODAL FUNCTIONS ====================
    function openAuthModal(defaultTab = 'buyerLogin') {
        authModal.classList.add('active');
        switchAuthTab(defaultTab);
    }

    function closeAuthModal() {
        authModal.classList.remove('active');
    }

    function switchAuthTab(tabName) {
        document.querySelectorAll('.auth-tab').forEach(tab => {
            tab.classList.remove('active');
        });
        
        document.querySelectorAll('.auth-form').forEach(form => {
            form.classList.remove('active');
        });
        
        document.querySelector(`.auth-tab[data-tab="${tabName}"]`).classList.add('active');
        document.getElementById(`${tabName}Form`).classList.add('active');
    }

    function showForgotPassword() {
        closeAuthModal();
        forgotPasswordModal.classList.add('active');
    }

    function closeForgotPassword() {
        forgotPasswordModal.classList.remove('active');
        openAuthModal('buyerLogin');
    }

    async function handleBuyerLogin(e) {
        e.preventDefault();
        
        const email = document.getElementById('buyerLoginEmail').value;
        const password = document.getElementById('buyerLoginPassword').value;
        
        try {
            const userCredential = await auth.signInWithEmailAndPassword(email, password);
            showToast('Login successful!', 'success');
            closeAuthModal();
            
        } catch (error) {
            console.error('Login error:', error);
            showToast('Login failed: ' + error.message, 'error');
        }
    }

    async function handleSellerLogin(e) {
        e.preventDefault();
        
        const email = document.getElementById('sellerLoginEmail').value;
        const password = document.getElementById('sellerLoginPassword').value;
        
        try {
            const userCredential = await auth.signInWithEmailAndPassword(email, password);
            
            // Check if user is a registered seller
            const sellerDoc = await db.collection('sellers').doc(userCredential.user.uid).get();
            
            if (sellerDoc.exists) {
                showToast('Seller login successful!', 'success');
                closeAuthModal();
            } else {
                await auth.signOut();
                showToast('You are not registered as a seller', 'error');
            }
            
        } catch (error) {
            console.error('Seller login error:', error);
            showToast('Login failed: ' + error.message, 'error');
        }
    }

    async function handleRegisterAsBuyer(e) {
        e.preventDefault();
        
        const name = document.getElementById('buyerName').value.trim();
        const email = document.getElementById('buyerEmail').value;
        const phone = document.getElementById('buyerPhone').value.trim();
        const address = document.getElementById('buyerAddress').value.trim();
        const password = document.getElementById('buyerPassword').value;
        const confirmPassword = document.getElementById('buyerConfirmPassword').value;
        
        if (password !== confirmPassword) {
            showToast('Passwords do not match', 'error');
            return;
        }
        
        try {
            const userCredential = await auth.createUserWithEmailAndPassword(email, password);
            const user = userCredential.user;
            
            // Create user profile
            const userProfile = {
                displayName: name,
                email: email,
                phone: phone,
                address: address,
                userType: 'buyer',
                affiliateBalance: 0,
                referrerCode: generateReferrerCode(),
                createdAt: new Date(),
                updatedAt: new Date()
            };
            
            await db.collection('users').doc(user.uid).set(userProfile);
            
            // Update user display name
            await user.updateProfile({
                displayName: name
            });
            
            showToast('Registration successful! Please check your email for verification.', 'success');
            closeAuthModal();
            
        } catch (error) {
            console.error('Registration error:', error);
            showToast('Registration failed: ' + error.message, 'error');
        }
    }

    async function handleRegisterAsSeller(e) {
        e.preventDefault();
        
        const name = document.getElementById('sellerRegName').value.trim();
        const fatherName = document.getElementById('sellerRegFatherName').value.trim();
        const email = document.getElementById('sellerRegEmail').value;
        const phone = document.getElementById('sellerRegPhone').value.trim();
        const password = document.getElementById('sellerRegPassword').value;
        const confirmPassword = document.getElementById('sellerConfirmPassword').value;
        
        if (password !== confirmPassword) {
            showToast('Passwords do not match', 'error');
            return;
        }
        
        try {
            const userCredential = await auth.createUserWithEmailAndPassword(email, password);
            const user = userCredential.user;
            
            // Create seller profile
            const sellerProfile = {
                name: name,
                fatherName: fatherName,
                email: email,
                phone: phone,
                userType: 'seller',
                verified: false,
                shopName: name + ' Store',
                availableBalance: 0,
                pendingWithdrawal: 0,
                createdAt: new Date(),
                updatedAt: new Date()
            };
            
            await db.collection('sellers').doc(user.uid).set(sellerProfile);
            
            // Create user profile
            const userProfile = {
                displayName: name,
                email: email,
                phone: phone,
                userType: 'seller',
                createdAt: new Date(),
                updatedAt: new Date()
            };
            
            await db.collection('users').doc(user.uid).set(userProfile);
            
            // Update user display name
            await user.updateProfile({
                displayName: name
            });
            
            showToast('Seller registration successful! Our team will verify your account.', 'success');
            closeAuthModal();
            
        } catch (error) {
            console.error('Seller registration error:', error);
            showToast('Registration failed: ' + error.message, 'error');
        }
    }

    async function handleForgotPassword(e) {
        e.preventDefault();
        
        const email = document.getElementById('forgotEmail').value;
        
        try {
            await auth.sendPasswordResetEmail(email);
            showToast('Password reset email sent! Check your inbox.', 'success');
            closeForgotPassword();
            
        } catch (error) {
            console.error('Forgot password error:', error);
            showToast('Error sending reset email: ' + error.message, 'error');
        }
    }

    function loginWithGoogle(userType) {
        const provider = new firebase.auth.GoogleAuthProvider();
        
        auth.signInWithPopup(provider)
            .then(async (result) => {
                const user = result.user;
                
                if (userType === 'seller') {
                    // Check if seller exists
                    const sellerDoc = await db.collection('sellers').doc(user.uid).get();
                    if (!sellerDoc.exists) {
                        showToast('Google login successful, but you need to register as a seller first', 'info');
                        await auth.signOut();
                        openAuthModal('sellerRegister');
                        return;
                    }
                }
                
                showToast('Google login successful!', 'success');
                closeAuthModal();
            })
            .catch((error) => {
                console.error('Google login error:', error);
                showToast('Google login failed: ' + error.message, 'error');
            });
    }

    // ==================== UTILITY FUNCTIONS ====================
    function togglePassword(inputId, button) {
        const input = document.getElementById(inputId);
        const icon = button.querySelector('i');
        
        if (input.type === 'password') {
            input.type = 'text';
            icon.className = 'far fa-eye-slash';
        } else {
            input.type = 'password';
            icon.className = 'far fa-eye';
        }
    }

    function formatPhoneNumber(input) {
        let value = input.value.replace(/\D/g, '');
        
        if (value.length > 0) {
            if (value.length <= 4) {
                value = value.replace(/(\d{1,4})/, '$1');
            } else if (value.length <= 7) {
                value = value.replace(/(\d{4})(\d{1,3})/, '$1-$2');
            } else {
                value = value.replace(/(\d{4})(\d{1,7})/, '$1-$2');
            }
        }
        
        input.value = value;
    }

    function toggleNotifications() {
        notificationPanel.classList.toggle('active');
        userMenu.classList.remove('active');
    }
function showNotificationsFullPage() {
    document.querySelectorAll('#mainContent > div').forEach(page => { page.style.display = 'none'; });
    
    const notifPage = document.getElementById('notificationsPage');
    const notifList = document.getElementById('notificationsListFull');
    notifPage.style.display = 'block';

    if (notifications.length === 0) {
        notifList.innerHTML = `<div style="text-align:center; padding:3rem;"><p>No notifications yet.</p></div>`;
        return;
    }

    notifList.innerHTML = notifications.map(n => `
        <div class="notif-item ${n.read ? '' : 'unread'}">
            <div class="notif-icon">
                <i class="fas ${n.type === 'order' ? 'fa-box' : 'fa-bell'}"></i>
            </div>
            <div style="flex: 1;">
                <h4 style="margin: 0; font-size: 1.1rem;">${n.title}</h4>
                <p style="margin: 5px 0; color: var(--text-secondary);">${n.message}</p>
                <small style="color: #999;">${n.createdAt?.toDate ? n.createdAt.toDate().toLocaleString() : 'Just now'}</small>
            </div>
            <button class="btn btn-sm" onclick="markNotificationRead('${n.id}')">
                <i class="fas fa-times"></i> Dismiss
            </button>
        </div>
    `).join('');
}
    function toggleUserMenu() {
        userMenu.classList.toggle('active');
        notificationPanel.classList.remove('active');
    }

    async function markNotificationRead(notifId) {
    try {
        await db.collection('notifications').doc(notifId).delete(); // Deletes it from DB
        notifications = notifications.filter(n => n.id !== notifId); // Removes it from screen
        updateNotificationCount();
        showNotificationsFullPage(); // Refresh list
        showToast('Notification cleared', 'success');
    } catch (error) {
        console.error("Error:", error);
    }
}



    function initializeHeroSlider() {
        const slides = document.querySelectorAll('.slide');
        if (slides.length === 0) return;
        
        let currentSlide = 0;
        
        function showSlide(index) {
            slides.forEach(slide => slide.classList.remove('active'));
            slides[index].classList.add('active');
            currentSlide = index;
        }
        
        function nextSlide() {
            const next = (currentSlide + 1) % slides.length;
            showSlide(next);
        }
        
        // Auto slide every 5 seconds
        heroSliderInterval = setInterval(nextSlide, 5000);
        
        // Add manual controls if needed
        // document.querySelector('.hero-slider').addEventListener('click', nextSlide);
    }

    function startCountdownTimer() {
        const countdown = document.getElementById('countdown');
        if (!countdown) return;
        
        // Set end time (2 hours from now)
        const endTime = new Date();
        endTime.setHours(endTime.getHours() + 2);
        
        function updateCountdown() {
            const now = new Date();
            const timeLeft = endTime - now;
            
            if (timeLeft <= 0) {
                countdown.innerHTML = '<span style="color: var(--error);">Sale Ended</span>';
                clearInterval(countdownInterval);
                return;
            }
            
            const hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);
            
            const hoursSpan = document.getElementById('countdown-hours');
            const minutesSpan = document.getElementById('countdown-minutes');
            const secondsSpan = document.getElementById('countdown-seconds');
            
            if (hoursSpan) hoursSpan.textContent = hours.toString().padStart(2, '0');
            if (minutesSpan) minutesSpan.textContent = minutes.toString().padStart(2, '0');
            if (secondsSpan) secondsSpan.textContent = seconds.toString().padStart(2, '0');
        }
        
        updateCountdown();
        const countdownInterval = setInterval(updateCountdown, 1000);
    }

    function toggleTheme() {
        const currentTheme = document.documentElement.getAttribute('data-theme');
        const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
        
        document.documentElement.setAttribute('data-theme', newTheme);
        localStorage.setItem('theme', newTheme);
        
        const themeIcon = document.querySelector('#themeToggle i');
        themeIcon.className = newTheme === 'dark' ? 'fas fa-sun' : 'fas fa-moon';
        
        showToast(`Switched to ${newTheme} mode`, 'info');
    }

    function openChatSupport() {
        if (!currentUser) {
            showToast('Please login to chat with support', 'error');
            openAuthModal('buyerLogin');
            return;
        }
        
        // For buyers, show support in messages page
        if (currentSeller) {
            switchSellerTab('support');
        } else {
            // Create admin support conversation for buyers
            createAdminSupportConversation();
        }
    }

    async function createAdminSupportConversation() {
        try {
            // Check if conversation exists
            const snapshot = await db.collection('conversations')
                .where('buyerId', '==', currentUser.uid)
                .where('adminId', '==', 'admin')
                .limit(1)
                .get();
            
            if (snapshot.empty) {
                const conversationData = {
                    buyerId: currentUser.uid,
                    buyerName: currentUserProfile?.displayName || currentUser.email,
                    buyerEmail: currentUser.email,
                    adminId: 'admin',
                    adminName: 'Admin Support',
                    lastMessage: 'Start of conversation',
                    lastMessageAt: new Date(),
                    createdAt: new Date()
                };
                
                await db.collection('conversations').add(conversationData);
            }
            
            showMessagesPage();
            
        } catch (error) {
            console.error('Error creating support conversation:', error);
            showToast('Error starting support chat', 'error');
        }
    }

    function handleImageUpload(event) {
        const files = event.target.files;
        const previewContainer = document.getElementById('imagePreviewContainer');
        
        // Clear previous previews
        previewContainer.innerHTML = '';
        productImages = [];
        
        // Limit to 8 images
        const fileArray = Array.from(files).slice(0, 8);
        
        fileArray.forEach(file => {
            if (!file.type.startsWith('image/')) {
                showToast('Only image files are allowed', 'error');
                return;
            }
            
            if (file.size > 5 * 1024 * 1024) {
                showToast('Image size should be less than 5MB', 'error');
                return;
            }
            
            const reader = new FileReader();
            reader.onload = function(e) {
                const imgContainer = document.createElement('div');
                imgContainer.className = 'image-preview';
                imgContainer.innerHTML = `
                    <img src="${e.target.result}" alt="Preview">
                    <button type="button" class="remove-image" onclick="removeProductImage(this)">
                        <i class="fas fa-times"></i>
                    </button>
                `;
                previewContainer.appendChild(imgContainer);
            };
            reader.readAsDataURL(file);
            
            productImages.push({
                file: file,
                url: URL.createObjectURL(file)
            });
        });
    }

    function handleVideoUpload(event) {
        const file = event.target.files[0];
        if (!file) return;
        
        if (!file.type.startsWith('video/')) {
            showToast('Only video files are allowed', 'error');
            return;
        }
        
        if (file.size > 50 * 1024 * 1024) {
            showToast('Video size should be less than 50MB', 'error');
            return;
        }
        
        const previewContainer = document.getElementById('videoPreviewContainer');
        previewContainer.innerHTML = '';
        
        const videoPreview = document.createElement('div');
        videoPreview.className = 'video-preview';
        videoPreview.innerHTML = `
            <video controls>
                <source src="${URL.createObjectURL(file)}" type="${file.type}">
            </video>
            <button type="button" class="remove-video" onclick="removeProductVideo()">
                <i class="fas fa-times"></i>
            </button>
        `;
        previewContainer.appendChild(videoPreview);
        
        productVideo = {
            file: file,
            url: URL.createObjectURL(file)
        };
    }

    function removeProductImage(button) {
        const imgContainer = button.closest('.image-preview');
        const index = Array.from(imgContainer.parentNode.children).indexOf(imgContainer);
        
        productImages.splice(index, 1);
        imgContainer.remove();
    }

    function removeProductVideo() {
        const previewContainer = document.getElementById('videoPreviewContainer');
        previewContainer.innerHTML = '';
        productVideo = null;
        document.getElementById('productVideo').value = '';
    }

    // ==================== ORDER LOCK FUNCTIONS ====================
    function cancelPayment() {
        orderLockPaymentModal.classList.remove('active');
        showToast('Payment cancelled', 'info');
    }

    async function submitPaymentProof() {
        const transactionId = document.getElementById('orderTransactionId').value.trim();
        const method = document.getElementById('paymentMethodSelect').value;
        const paymentProof = document.getElementById('paymentProof').files[0];
        
        if (!transactionId) {
            showToast('Please enter transaction ID', 'error');
            return;
        }
        
        if (!currentSeller) {
            showToast('Seller not found', 'error');
            return;
        }
        
        try {
            let paymentProofUrl = '';
            if (paymentProof) {
                const storageRef = storage.ref(`order_payments/${currentSeller.id}/${Date.now()}_${paymentProof.name}`);
                await storageRef.put(paymentProof);
                paymentProofUrl = await storageRef.getDownloadURL();
            }
            
            const paymentData = {
                sellerId: currentSeller.id,
                sellerName: currentSeller.shopName || currentSeller.name,
                amount: 50,
                method: method,
                transactionId: transactionId,
                paymentProof: paymentProofUrl,
                status: 'pending',
                submittedAt: new Date()
            };
            
            await db.collection('orderPayments').add(paymentData);
            
            // Mark order as payment submitted
            if (currentOrderId) {
                await db.collection('orders').doc(currentOrderId).update({
                    orderPaymentSubmitted: true,
                    orderPaymentStatus: 'pending',
                    updatedAt: new Date()
                });
            }
            
            orderLockPaymentModal.classList.remove('active');
            showToast('Payment proof submitted. Your order will be unlocked after verification.', 'success');
            
        } catch (error) {
            console.error('Error submitting payment proof:', error);
            showToast('Error submitting payment: ' + error.message, 'error');
        }
    }

    // ==================== INVOICE FUNCTIONS ====================
    async function generateInvoice(orderId) {
        const order = buyerOrders.find(o => o.id === orderId) || sellerOrders.find(o => o.id === orderId);
        if (!order) {
            showToast('Order not found', 'error');
            return;
        }
        
        // Check if invoice is locked
        if (order.invoiceLocked && !currentSeller) {
            showToast('Invoice is locked. Please contact seller.', 'error');
            return;
        }
        
        const orderDate = order.createdAt?.toDate ? order.createdAt.toDate() : new Date(order.createdAt);
        const invoiceNumber = 'INV-' + order.id.slice(-8).toUpperCase();
        
        const invoiceDetails = document.getElementById('invoiceDetails');
        invoiceDetails.innerHTML = `
            <div class="invoice-details">
                <div>
                    <h4>Invoice To:</h4>
                    <p><strong>${escapeHtml(order.customerName || '')}</strong></p>
                    <p>${escapeHtml(order.shippingAddress || '')}</p>
                    <p>${escapeHtml(order.shippingCity || '')}</p>
                    <p>Phone: ${escapeHtml(order.customerPhone || '')}</p>
                </div>
                <div style="text-align: right;">
                    <h4>Invoice Details</h4>
                    <p><strong>Invoice #:</strong> ${invoiceNumber}</p>
                    <p><strong>Order #:</strong> ${order.id.slice(-8)}</p>
                    <p><strong>Invoice Date:</strong> ${orderDate.toLocaleDateString()}</p>
                    <p><strong>Payment Method:</strong> ${order.paymentMethod === 'cod' ? 'Cash on Delivery' : 
                        order.paymentMethod === 'easypaisa' ? 'EasyPaisa' : 'JazzCash'}</p>
                </div>
            </div>
            
            <table class="invoice-table">
                <thead>
                    <tr>
                        <th>#</th>
                        <th>Description</th>
                        <th>Quantity</th>
                        <th>Unit Price</th>
                        <th>Total</th>
                    </tr>
                </thead>
                <tbody>
                    ${order.items?.map((item, index) => `
                        <tr>
                            <td>${index + 1}</td>
                            <td>
                                <strong>${escapeHtml(item.productName || 'Product')}</strong><br>
                                <small style="color: var(--text-secondary);">Seller: ${escapeHtml(order.sellerName || '')}</small>
                            </td>
                            <td>${item.quantity}</td>
                            <td>Rs. ${item.finalPrice?.toLocaleString() || '0'}</td>
                            <td>Rs. ${((item.finalPrice || 0) * (item.quantity || 1)).toLocaleString()}</td>
                        </tr>
                    `).join('')}
                </tbody>
            </table>
            
            <div class="invoice-total">
                <div style="display: inline-block; text-align: right;">
                    <div style="display: flex; justify-content: space-between; min-width: 300px; margin-bottom: 0.5rem;">
                        <span>Subtotal:</span>
                        <span>Rs. ${order.subtotal?.toLocaleString() || '0'}</span>
                    </div>
                    <div style="display: flex; justify-content: space-between; min-width: 300px; margin-bottom: 0.5rem;">
                        <span>Shipping:</span>
                        <span>Rs. ${order.shippingFee?.toLocaleString() || '200'}</span>
                    </div>
                    <div style="display: flex; justify-content: space-between; min-width: 300px; margin-bottom: 0.5rem;">
                        <span>Tax:</span>
                        <span>Rs. ${order.tax?.toFixed(2) || '0.00'}</span>
                    </div>
                    <div style="height: 2px; background: var(--primary); margin: 1rem 0;"></div>
                    <div style="display: flex; justify-content: space-between; min-width: 300px; font-size: 1.2rem; font-weight: bold;">
                        <span>Total Amount:</span>
                        <span>Rs. ${order.totalAmount?.toLocaleString() || '0'}</span>
                    </div>
                </div>
            </div>
            
            <div style="margin-top: 3rem; padding-top: 1rem; border-top: 1px solid var(--border);">
                <p><strong>Terms & Conditions:</strong></p>
                <p style="color: var(--text-secondary); font-size: 0.9rem;">
                    1. This is an official invoice from Jeeto Pakistan.<br>
                    2. Goods once sold will not be taken back.<br>
                    3. All disputes are subject to jurisdiction of Pakistan.<br>
                    4. Prices include all applicable taxes.
                </p>
            </div>
            
            <div style="text-align: center; margin-top: 2rem; color: var(--text-secondary); font-size: 0.9rem;">
                <p>Thank you for shopping with Jeeto Pakistan!</p>
                <p>This is a computer-generated invoice. No signature required.</p>
            </div>
        `;
        
        openModal('invoiceModal');
    }

    function printInvoice() {
        const printContent = document.getElementById('invoiceDetails').innerHTML;
        const originalContent = document.body.innerHTML;
        
        document.body.innerHTML = `
            <!DOCTYPE html>
            <html>
            <head>
                <title>Invoice - Jeeto Pakistan</title>
                <style>
                    body { font-family: Arial, sans-serif; margin: 0; padding: 20px; }
                    .invoice-header { text-align: center; margin-bottom: 30px; border-bottom: 3px solid #01411C; padding-bottom: 20px; }
                    .invoice-details { display: flex; justify-content: space-between; margin-bottom: 30px; }
                    table { width: 100%; border-collapse: collapse; margin: 20px 0; }
                    th { background: #f5f5f5; padding: 10px; text-align: left; }
                    td { padding: 10px; border-bottom: 1px solid #ddd; }
                    .invoice-total { text-align: right; padding: 20px; background: #f9f9f9; }
                </style>
            </head>
            <body>
                ${printContent}
            </body>
            </html>
        `;
        
        window.print();
        document.body.innerHTML = originalContent;
        location.reload(); // Reload to restore original state
    }

    function closeInvoice() {
        closeModal('invoiceModal');
    }

    // ==================== LOGOUT FUNCTION ====================
    async function handleLogout() {
        try {
            await auth.signOut();
            showToast('Logged out successfully', 'success');
            showHomePage();
        } catch (error) {
            console.error('Logout error:', error);
            showToast('Logout failed', 'error');
        }
    }

    // ==================== INITIALIZATION COMPLETE ====================
    console.log('✅ All functions loaded successfully!');
                console.log('✅ Platform ready!');
console.log('? All functions loaded successfully!');


</script>
</body>
</html>
