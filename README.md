<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CodeCraft - Multi-Language Online Editor</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #6e8efb;
            --secondary: #a777e3;
            --dark: #2c3e50;
            --light: #f5f5f5;
            --success: #4CAF50;
            --danger: #f44336;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f9f9f9;
            color: #333;
            line-height: 1.6;
        }
        
        .navbar {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        .logo i {
            font-size: 1.8rem;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            margin-left: 1.5rem;
            font-weight: 500;
            transition: all 0.3s ease;
        }
        
        .nav-links a:hover {
            opacity: 0.8;
            transform: translateY(-2px);
        }
        
        .btn {
            padding: 0.6rem 1.2rem;
            border-radius: 30px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }
        
        .btn-primary {
            background-color: white;
            color: var(--primary);
        }
        
        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0,0,0,0.15);
        }
        
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            padding: 8rem 2rem 4rem;
            background: linear-gradient(135deg, rgba(110,142,251,0.1), rgba(167,119,227,0.1));
            position: relative;
            overflow: hidden;
        }
        
        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('https://images.unsplash.com/photo-1555066931-4365d14bab8c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80') center/cover;
            opacity: 0.1;
            z-index: -1;
        }
        
        .hero-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            align-items: center;
            gap: 3rem;
        }
        
        .hero-text {
            flex: 1;
        }
        
        .hero-image {
            flex: 1;
            position: relative;
        }
        
        .hero-image img {
            width: 100%;
            border-radius: 10px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
            transform: perspective(1000px) rotateY(-10deg);
            transition: all 0.5s ease;
        }
        
        .hero-image:hover img {
            transform: perspective(1000px) rotateY(0deg);
        }
        
        h1 {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            line-height: 1.2;
        }
        
        .tagline {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            color: #555;
        }
        
        .features {
            padding: 5rem 2rem;
            background-color: white;
        }
        
        .features-container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 3rem;
            font-size: 2.5rem;
            color: var(--dark);
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }
        
        .feature-card {
            background: white;
            border-radius: 10px;
            padding: 2rem;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            transition: all 0.3s ease;
            border: 1px solid #eee;
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.1);
        }
        
        .feature-icon {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .feature-title {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: var(--dark);
        }
        
        .cta {
            padding: 5rem 2rem;
            text-align: center;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
        }
        
        .cta h2 {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
        }
        
        .cta p {
            max-width: 700px;
            margin: 0 auto 2rem;
            font-size: 1.1rem;
        }
        
        .btn-cta {
            background-color: white;
            color: var(--primary);
            padding: 1rem 2rem;
            font-size: 1.1rem;
            border-radius: 50px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }
        
        .btn-cta:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.2);
        }
        
        footer {
            background-color: var(--dark);
            color: white;
            padding: 3rem 2rem;
            text-align: center;
        }
        
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 2rem;
        }
        
        .footer-links a {
            color: white;
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .footer-links a:hover {
            color: var(--primary);
        }
        
        .social-icons {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .social-icons a {
            color: white;
            font-size: 1.5rem;
            transition: all 0.3s ease;
        }
        
        .social-icons a:hover {
            color: var(--primary);
            transform: translateY(-5px);
        }
        
        @media (max-width: 768px) {
            .hero-content {
                flex-direction: column;
                text-align: center;
            }
            
            h1 {
                font-size: 2.5rem;
            }
            
            .nav-links {
                display: none;
            }
        }
    </style>
</head>
<body>
    <nav class="navbar">
        <div class="logo">
            <i class="fas fa-code"></i>
            <span>CodeCraft</span>
        </div>
        <div class="nav-links">
            <a href="#features">Features</a>
            <a href="#about">About</a>
            <a href="index.html" class="btn btn-primary">Launch Editor</a>
        </div>
    </nav>
    
    <section class="hero">
        <div class="hero-content">
            <div class="hero-text">
                <h1>Your Ultimate Multi-Language Code Editor</h1>
                <p class="tagline">Write, edit, and execute HTML, CSS, JavaScript, and Python code right in your browser with real-time preview.</p>
                <a href="index.html" class="btn btn-primary" style="padding: 1rem 2rem; font-size: 1.1rem;">
                    Start Coding Now <i class="fas fa-arrow-right"></i>
                </a>
            </div>
            <div class="hero-image">
                <img src="https://images.unsplash.com/photo-1619410283995-43d9134e7656?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80" alt="Code Editor">
            </div>
        </div>
    </section>
    
    <section class="features" id="features">
        <div class="features-container">
            <h2 class="section-title">Powerful Features</h2>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-laptop-code"></i>
                    </div>
                    <h3 class="feature-title">Multi-Language Support</h3>
                    <p>Write and execute HTML, CSS, JavaScript, and Python code all in one place with seamless switching between languages.</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-bolt"></i>
                    </div>
                    <h3 class="feature-title">Real-Time Preview</h3>
                    <p>See your web code results instantly as you type. Python output appears in a dedicated console.</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-file-export"></i>
                    </div>
                    <h3 class="feature-title">File Operations</h3>
                    <p>Open code files from your device or download your work with a single click.</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-mobile-alt"></i>
                    </div>
                    <h3 class="feature-title">Responsive Design</h3>
                    <p>Works perfectly on all devices from desktop computers to tablets and smartphones.</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-sun"></i>
                    </div>
                    <h3 class="feature-title">Beautiful UI</h3>
                    <p>Enjoy a clean, modern interface with syntax highlighting and intuitive controls.</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-server"></i>
                    </div>
                    <h3 class="feature-title">No Backend Needed</h3>
                    <p>Everything runs in your browser - no servers, no installations, no setup required.</p>
                </div>
            </div>
        </div>
    </section>
    
    <section class="cta">
        <h2>Ready to Boost Your Coding Productivity?</h2>
        <p>Join thousands of developers who use CodeCraft for quick prototyping, learning, and testing code snippets.</p>
        <a href="index.html" class="btn btn-cta">
            Launch Code Editor <i class="fas fa-arrow-right"></i>
        </a>
    </section>
    
    <footer>
        <div class="footer-links">
            <a href="index.html">Editor</a>
            <a href="#features">Features</a>
            <a href="#">Documentation</a>
            <a href="#">Privacy</a>
            <a href="#">Terms</a>
        </div>
        <div class="social-icons">
            <a href="#"><i class="fab fa-github"></i></a>
            <a href="#"><i class="fab fa-twitter"></i></a>
            <a href="#"><i class="fab fa-linkedin"></i></a>
            <a href="#"><i class="fab fa-youtube"></i></a>
        </div>
        <p>&copy; 2023 CodeCraft. All rights reserved.</p>
    </footer>
</body>
</html>
