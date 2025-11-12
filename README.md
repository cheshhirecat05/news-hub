<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NewsHub - Your Daily News Portal</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f5f5f5;
        }

        /* Header Styles */
        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .header-top {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            text-decoration: none;
            color: white;
        }

        .search-container {
            flex: 0 0 400px;
            position: relative;
        }

        .search-bar {
            width: 100%;
            padding: 10px 40px 10px 15px;
            border: none;
            border-radius: 25px;
            font-size: 14px;
            outline: none;
        }

        .search-btn {
            position: absolute;
            right: 5px;
            top: 50%;
            transform: translateY(-50%);
            background: #667eea;
            border: none;
            padding: 8px 15px;
            border-radius: 20px;
            color: white;
            cursor: pointer;
        }

        .login-btn {
            background: white;
            color: #667eea;
            padding: 10px 25px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            transition: transform 0.2s;
        }

        .login-btn:hover {
            transform: scale(1.05);
        }

        /* Navigation Menu */
        nav {
            background: rgba(255,255,255,0.1);
            margin-top: 1rem;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .menu {
            list-style: none;
            display: flex;
            justify-content: center;
            gap: 2rem;
        }

        .menu li a {
            color: white;
            text-decoration: none;
            padding: 15px 0;
            display: block;
            font-weight: 500;
            transition: opacity 0.3s;
        }

        .menu li a:hover {
            opacity: 0.8;
        }

        /* Main Content */
        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 20px;
        }

        .page-section {
            display: none;
        }

        .page-section.active {
            display: block;
        }

        /* Home Page Styles */
        .hero-news {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            margin-bottom: 2rem;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .hero-news img {
            width: 100%;
            height: 400px;
            object-fit: cover;
        }

        .hero-content {
            padding: 2rem;
        }

        .hero-content h1 {
            color: #667eea;
            margin-bottom: 1rem;
        }

        .news-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .news-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }

        .news-card:hover {
            transform: translateY(-5px);
        }

        .news-card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .news-card-content {
            padding: 1.5rem;
        }

        .category-tag {
            display: inline-block;
            background: #667eea;
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 12px;
            margin-bottom: 1rem;
        }

        .news-card h3 {
            color: #333;
            margin-bottom: 0.5rem;
        }

        .news-meta {
            color: #999;
            font-size: 14px;
            margin-bottom: 1rem;
        }

        .news-card p {
            color: #666;
            line-height: 1.6;
        }

        /* Comments Section */
        .comments-section {
            background: white;
            padding: 2rem;
            border-radius: 10px;
            margin-top: 2rem;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }

        .comment-form {
            margin-bottom: 2rem;
        }

        .comment-form input,
        .comment-form textarea {
            width: 100%;
            padding: 12px;
            margin-bottom: 1rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-family: inherit;
        }

        .submit-btn {
            background: #667eea;
            color: white;
            padding: 12px 30px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
        }

        .comment {
            border-bottom: 1px solid #eee;
            padding: 1rem 0;
        }

        .comment-author {
            font-weight: bold;
            color: #667eea;
            margin-bottom: 0.5rem;
        }

        /* Login Page */
        .login-container {
            max-width: 400px;
            margin: 4rem auto;
            background: white;
            padding: 3rem;
            border-radius: 10px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .login-container h2 {
            text-align: center;
            color: #667eea;
            margin-bottom: 2rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }

        .form-group input {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }

        .btn-primary {
            width: 100%;
            background: #667eea;
            color: white;
            padding: 12px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            font-size: 16px;
        }

        .signup-link {
            text-align: center;
            margin-top: 1rem;
            color: #666;
        }

        /* About Page */
        .about-section {
            background: white;
            padding: 3rem;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            margin-bottom: 2rem;
        }

        .about-section h2 {
            color: #667eea;
            margin-bottom: 1.5rem;
        }

        .contact-info {
            background: #f9f9f9;
            padding: 2rem;
            border-radius: 10px;
            margin-top: 2rem;
        }

        .contact-info h3 {
            color: #667eea;
            margin-bottom: 1rem;
        }

        .contact-item {
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
        }

        .contact-item strong {
            min-width: 100px;
            color: #667eea;
        }

        /* Footer */
        footer {
            background: #2c3e50;
            color: white;
            padding: 3rem 0 1rem;
            margin-top: 4rem;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }

        .footer-section h3 {
            margin-bottom: 1rem;
            color: #667eea;
        }

        .footer-section ul {
            list-style: none;
        }

        .footer-section ul li {
            margin-bottom: 0.5rem;
        }

        .footer-section a {
            color: #bbb;
            text-decoration: none;
        }

        .footer-bottom {
            text-align: center;
            margin-top: 2rem;
            padding-top: 1rem;
            border-top: 1px solid #444;
            color: #999;
        }

        @media (max-width: 768px) {
            .header-top {
                flex-direction: column;
                gap: 1rem;
            }

            .search-container {
                flex: 1;
                width: 100%;
            }

            .menu {
                flex-wrap: wrap;
                gap: 1rem;
            }

            .news-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="header-top">
            <a href="#" class="logo" onclick="showPage('home')">📰 NewsHub</a>
            <div class="search-container">
                <input type="text" class="search-bar" placeholder="Search news..." id="searchInput">
                <button class="search-btn" onclick="searchNews()">Search</button>
            </div>
            <button class="login-btn" onclick="showPage('login')">Login</button>
        </div>
        <nav>
            <div class="nav-container">
                <ul class="menu">
                    <li><a href="#" onclick="showPage('home')">Home</a></li>
                    <li><a href="#" onclick="showPage('news')">News</a></li>
                    <li><a href="#" onclick="showPage('technology')">Technology</a></li>
                    <li><a href="#" onclick="showPage('sports')">Sports</a></li>
                    <li><a href="#" onclick="showPage('business')">Business</a></li>
                    <li><a href="#" onclick="showPage('about')">About</a></li>
                </ul>
            </div>
        </nav>
    </header>

    <!-- Main Container -->
    <div class="container">
        <!-- Home Page -->
        <section id="home" class="page-section active">
            <div class="hero-news">
                <img src="https://images.unsplash.com/photo-1504711434969-e33886168f5c?w=800" alt="Breaking News">
                <div class="hero-content">
                    <h1>Breaking: Global Technology Summit Announces Major AI Breakthrough</h1>
                    <p class="news-meta">Published on November 12, 2025 | By Sarah Johnson</p>
                    <p>Scientists at the Global Technology Summit have unveiled a revolutionary artificial intelligence system that promises to transform healthcare diagnostics. The breakthrough comes after years of research and collaboration between international tech leaders...</p>
                </div>
            </div>

            <h2 style="margin-bottom: 1.5rem; color: #667eea;">Latest News</h2>
            <div class="news-grid">
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1488590528505-98d2b5aba04b?w=400" alt="Technology">
                    <div class="news-card-content">
                        <span class="category-tag">Technology</span>
                        <h3>New Quantum Computer Breaks Processing Records</h3>
                        <p class="news-meta">November 11, 2025 | Tech Desk</p>
                        <p>Scientists have developed a quantum computer that performs calculations 1000 times faster than previous models, opening new possibilities for complex problem-solving.</p>
                    </div>
                </div>

                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1461896836934-ffe607ba8211?w=400" alt="Sports">
                    <div class="news-card-content">
                        <span class="category-tag">Sports</span>
                        <h3>Championship Finals Draw Record Viewership</h3>
                        <p class="news-meta">November 10, 2025 | Sports Team</p>
                        <p>The championship finals attracted over 2 billion viewers worldwide, setting a new record for the most-watched sporting event in history.</p>
                    </div>
                </div>

                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1444653614773-995cb1ef9efa?w=400" alt="Business">
                    <div class="news-card-content">
                        <span class="category-tag">Business</span>
                        <h3>Markets Surge on Positive Economic Indicators</h3>
                        <p class="news-meta">November 12, 2025 | Business Desk</p>
                        <p>Global markets reached new heights today following the release of encouraging economic data, with technology and renewable energy sectors leading the gains.</p>
                    </div>
                </div>

                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1532619675605-1ede6c2ed2b0?w=400" alt="Environment">
                    <div class="news-card-content">
                        <span class="category-tag">Environment</span>
                        <h3>New Clean Energy Initiative Launched</h3>
                        <p class="news-meta">November 9, 2025 | Environment Team</p>
                        <p>World leaders announce ambitious new clean energy program aimed at reducing carbon emissions by 50% within the next decade.</p>
                    </div>
                </div>

                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1576091160399-112ba8d25d1d?w=400" alt="Health">
                    <div class="news-card-content">
                        <span class="category-tag">Health</span>
                        <h3>Medical Breakthrough in Cancer Treatment</h3>
                        <p class="news-meta">November 8, 2025 | Health Desk</p>
                        <p>Researchers announce successful trials of new cancer treatment showing unprecedented success rates with minimal side effects.</p>
                    </div>
                </div>

                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1503676260728-1c00da094a0b?w=400" alt="Education">
                    <div class="news-card-content">
                        <span class="category-tag">Education</span>
                        <h3>Digital Learning Revolution Transforms Schools</h3>
                        <p class="news-meta">November 7, 2025 | Education Team</p>
                        <p>Educational institutions worldwide embrace new digital learning platforms that personalize education for each student's learning style.</p>
                    </div>
                </div>
            </div>

            <!-- Comments Section -->
            <div class="comments-section">
                <h2>Comments</h2>
                <div class="comment-form">
                    <h3>Leave a Comment</h3>
                    <input type="text" id="commentName" placeholder="Your Name" required>
                    <textarea id="commentText" rows="4" placeholder="Your Comment" required></textarea>
                    <button class="submit-btn" onclick="addComment()">Post Comment</button>
                </div>
                <div id="commentsList">
                    <div class="comment">
                        <div class="comment-author">John Doe</div>
                        <p>Great article! Very informative and well-written.</p>
                    </div>
                    <div class="comment">
                        <div class="comment-author">Jane Smith</div>
                        <p>Thanks for sharing this news. Looking forward to more updates!</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- News Page -->
        <section id="news" class="page-section">
            <h1 style="color: #667eea; margin-bottom: 2rem;">All News</h1>
            <div class="news-grid">
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1504711434969-e33886168f5c?w=400" alt="News">
                    <div class="news-card-content">
                        <span class="category-tag">Breaking</span>
                        <h3>International Summit Addresses Climate Change</h3>
                        <p class="news-meta">November 12, 2025 | Global News</p>
                        <p>World leaders gather to discuss urgent climate action plans and carbon reduction strategies for the coming decade.</p>
                    </div>
                </div>
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1495020689067-958852a7765e?w=400" alt="News">
                    <div class="news-card-content">
                        <span class="category-tag">Politics</span>
                        <h3>New Policy Reforms Announced</h3>
                        <p class="news-meta">November 11, 2025 | Political Desk</p>
                        <p>Government unveils comprehensive policy reforms aimed at economic growth and social welfare improvements.</p>
                    </div>
                </div>
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1586339949916-3e9457bef6d3?w=400" alt="News">
                    <div class="news-card-content">
                        <span class="category-tag">Society</span>
                        <h3>Community Programs Show Positive Impact</h3>
                        <p class="news-meta">November 10, 2025 | Community Desk</p>
                        <p>Recent community development programs demonstrate significant improvements in education and employment rates.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Technology Category -->
        <section id="technology" class="page-section">
            <h1 style="color: #667eea; margin-bottom: 2rem;">Technology News</h1>
            <div class="news-grid">
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1518770660439-4636190af475?w=400" alt="Tech">
                    <div class="news-card-content">
                        <span class="category-tag">Technology</span>
                        <h3>5G Networks Expand to Rural Areas</h3>
                        <p class="news-meta">November 12, 2025 | Tech News</p>
                        <p>Telecommunications companies announce major expansion of 5G infrastructure to underserved rural communities.</p>
                    </div>
                </div>
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1535378917042-10a22c95931a?w=400" alt="Tech">
                    <div class="news-card-content">
                        <span class="category-tag">Technology</span>
                        <h3>Cybersecurity Threats and New Solutions</h3>
                        <p class="news-meta">November 11, 2025 | Security Team</p>
                        <p>Security experts unveil advanced protection systems against emerging cyber threats and data breaches.</p>
                    </div>
                </div>
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?w=400" alt="Tech">
                    <div class="news-card-content">
                        <span class="category-tag">Technology</span>
                        <h3>Space Exploration Reaches New Milestone</h3>
                        <p class="news-meta">November 10, 2025 | Space Desk</p>
                        <p>Private space companies successfully complete longest crewed mission, paving way for commercial space travel.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sports Category -->
        <section id="sports" class="page-section">
            <h1 style="color: #667eea; margin-bottom: 2rem;">Sports News</h1>
            <div class="news-grid">
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1579952363873-27f3bade9f55?w=400" alt="Sports">
                    <div class="news-card-content">
                        <span class="category-tag">Sports</span>
                        <h3>Olympic Preparations Enter Final Phase</h3>
                        <p class="news-meta">November 12, 2025 | Olympics Desk</p>
                        <p>Host city completes final preparations for upcoming Olympic Games with state-of-the-art facilities and infrastructure.</p>
                    </div>
                </div>
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1517466787929-bc90951d0974?w=400" alt="Sports">
                    <div class="news-card-content">
                        <span class="category-tag">Sports</span>
                        <h3>Rising Star Breaks Multiple Records</h3>
                        <p class="news-meta">November 11, 2025 | Sports Team</p>
                        <p>Young athlete amazes sports world by breaking three long-standing records in single competition.</p>
                    </div>
                </div>
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1605296867304-46d5465a13f1?w=400" alt="Sports">
                    <div class="news-card-content">
                        <span class="category-tag">Sports</span>
                        <h3>International Tournament Kicks Off</h3>
                        <p class="news-meta">November 10, 2025 | Tournament Desk</p>
                        <p>Major international tournament begins with exciting opening matches and record-breaking attendance figures.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Business Category -->
        <section id="business" class="page-section">
            <h1 style="color: #667eea; margin-bottom: 2rem;">Business News</h1>
            <div class="news-grid">
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=400" alt="Business">
                    <div class="news-card-content">
                        <span class="category-tag">Business</span>
                        <h3>Startup Ecosystem Flourishes</h3>
                        <p class="news-meta">November 12, 2025 | Business Team</p>
                        <p>Record number of startups secure funding as venture capital investment reaches all-time high.</p>
                    </div>
                </div>
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1454165804606-c3d57bc86b40?w=400" alt="Business">
                    <div class="news-card-content">
                        <span class="category-tag">Business</span>
                        <h3>E-commerce Sales Hit Record Highs</h3>
                        <p class="news-meta">November 11, 2025 | E-commerce Desk</p>
                        <p>Online retail continues explosive growth with mobile shopping driving majority of transactions.</p>
                    </div>
                </div>
                <div class="news-card">
                    <img src="https://images.unsplash.com/photo-1507679799987-c73779587ccf?w=400" alt="Business">
                    <div class="news-card-content">
                        <span class="category-tag">Business</span>
                        <h3>Corporate Sustainability Initiatives Expand</h3>
                        <p class="news-meta">November 10, 2025 | Corporate News</p>
                        <p>Major corporations commit to ambitious sustainability goals and carbon-neutral operations by 2030.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Login Page -->
        <section id="login" class="page-section">
            <div class="login-container">
                <h2>Login to NewsHub</h2>
                <form onsubmit="handleLogin(event)">
                    <div class="form-group">
                        <label for="email">Email Address</label>
                        <input type="email" id="email" required>
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" id="password" required>
                    </div>
                    <button type="submit" class="btn-primary">Login</button>
                </form>
                <p class="signup-link">Don't have an account? <a href="#" style="color: #667eea;">Sign up here</a></p>
            </div>
        </section>

        <!-- About Page -->
        <section id="about" class="page-section">
            <div class="about-section">
                <h2>About NewsHub</h2>
                <p>NewsHub is your premier destination for reliable, up-to-date news coverage from around the world. Established in 2020, we have been committed to delivering accurate, unbiased journalism that keeps you informed about the events that matter most.</p>
                
                <h3 style="margin-top: 2rem; color: #667eea;">Our Mission</h3>
                <p>Our mission is to empower our readers with comprehensive news coverage across multiple categories including technology, sports, business, health, and more. We believe in the power of informed citizens and strive to provide content that educates, enlightens, and inspires.</p>
                
                <h3 style="margin-top: 2rem; color: #667eea;">Our Vision</h3>
                <p>To become the most trusted and accessible news platform globally, delivering high-quality journalism that serves the public interest and promotes transparency, accountability, and truth.</p>
                
                <h3 style="margin-top: 2rem; color: #667eea;">Our Values</h3>
                <ul style="margin-left: 2rem; margin-top: 1rem;">
                    <li><strong>Integrity:</strong> We maintain the highest standards of journalistic ethics</li>
                    <li><strong>Accuracy:</strong> We verify facts and correct errors promptly</li>
                    <li><strong>Independence:</strong> We report without bias or external influence</li>
                    <li><strong>Transparency:</strong> We are open about our sources and methods</li>
                    <li><strong>Excellence:</strong> We strive for the highest quality in everything we do</li>
                </ul>

                <div class="contact-info">
                    <h3>Contact Information</h3>
                    <div class="contact-item">
                        <strong>Address:</strong>
                        <span>123 Media Street, Press District, New York, NY 10001, USA</span>
                    </div>
                    <div class="contact-item">
                        <strong>Phone:</strong>
                        <span>+1 (555) 123-4567</span>
                    </div>
                    <div class="contact-item">
                        <strong>Email:</strong>
                        <span>contact@newshub.com</span>
                    </div>
                    <div class="contact-item">
                        <strong>Business Hours:</strong>
                        <span>Monday - Friday: 9:00 AM - 6:00 PM EST</span>
                    </div>
                    <div class="contact-item">
                        <strong>Support:</strong>
                        <span>support@newshub.com (24/7 available)</span>
                    </div>
                </div>

                <h3 style="margin-top: 2rem; color: #667eea;">Our Team</h3>
                <p>NewsHub is powered by a dedicated team of over 200 journalists, editors, designers, and technology experts working around the clock to bring you the latest news. Our editorial team has decades of combined experience in major news organizations worldwide.</p>
            </div>
        </section>
    </div>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-section">
                <h3>About NewsHub</h3>
                <p>NewsHub is your trusted source for breaking news, in-depth analysis, and comprehensive coverage of global events. We are committed to delivering accurate, unbiased journalism.</p>
            </div>
            <div class="footer-section">
                <h3>Quick Links</h3>
                <ul>
                    <li><a href="#" onclick="showPage('home')">Home</a></li>
                    <li><a href="#" onclick="showPage('about')">About Us</a></li>
                    <li><a href="#">Privacy Policy</a></li>
                    <li><a href="#">Terms of Service</a></li>
                    <li><a href="#">Advertise With Us</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Categories</h3>
                <ul>
                    <li><a href="#" onclick="showPage('technology')">Technology</a></li>
