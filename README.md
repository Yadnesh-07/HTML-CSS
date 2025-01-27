# HTML-CSS
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tech Services</title>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #1a1a2e;
            color: #eaeaea;
            display: flex;
        }

        .sidebar {
            background: #0f3460;
            width: 250px;
            height: 100vh;
            position: fixed;
            top: 0;
            left: 0;
            display: flex;
            flex-direction: column;
            padding-top: 2rem;
            transition: transform 0.3s;
            transform: translateX(0);
        }
        
        .sidebar.minimized {
            transform: translateX(-250px);
        }

        .sidebar a {
            color: #eaeaea;
            padding: 1rem;
            text-decoration: none;
            font-weight: bold;
            text-align: center;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            transition: color 0.3s;
        }

        .sidebar a:hover {
            background: #533483;
        }

        .toggle-btn {
            position: absolute;
            top: 10px;
            left: 250px;
            background: #533483;
            color: #eaeaea;
            border: none;
            border-radius: 50%;
            cursor: pointer;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background 0.3s;
            z-index: 1001;
            margin-right: 10px;
        }

        .toggle-btn:hover {
            background: #6c63ff;
        }

        .content {
            margin-left: 250px;
            width: calc(100% );
            transition: margin-left 0.3s;
            text-align: center;
        }

        .content.minimized {
            margin-left: 0;
            width: 100%;
        }

        .hero {
            text-align: center;
            padding: 6rem 1rem;
            background: linear-gradient(to right, #0f3460, #533483);
            color: #eaeaea;
        }

        .hero h1 {
            margin: 0;
            font-size: 3.5rem;
            text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.4);
        }

        .hero p {
            font-size: 1.5rem;
            margin: 1.5rem 0;
        }

        .hero button {
            padding: 1rem 2rem;
            font-size: 1rem;
            color: #eaeaea;
            background-color: #533483;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .hero button:hover {
            background-color: #6c63ff;
        }

        .services {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            padding: 4rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .service-card {
            background: #16213e;
            border-radius: 12px;
            box-shadow: 0 6px 10px rgba(0, 0, 0, 0.3);
            padding: 2rem;
            text-align: center;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.4);
        }

        .service-card h3 {
            margin-top: 0;
            color: #6c63ff;
        }

        .service-card p {
            color: #ccc;
        }

        .service-card button {
            padding: 0.5rem 1.5rem;
            font-size: 0.9rem;
            color: #eaeaea;
            background-color: #533483;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .service-card button:hover {
            background-color: #6c63ff;
        }

        footer {
            text-align: center;
            background: #0f3460;
            color: #eaeaea;
            padding: 2rem 1rem;
            margin-top: 2rem;
        }

        footer p {
            margin: 0;
        }

        footer a {
            color: #6c63ff;
            text-decoration: none;
            transition: color 0.3s;
        }

        footer a:hover {
            color: #9b8de6;
        }

        @media (max-width: 600px) {
            .hero h1 {
                font-size: 2.5rem;
            }

            .hero p {
                font-size: 1.2rem;
            }
        }
    </style>
</head>
<body>
    <div class="sidebar" id="sidebar">
        <a href="#hero">Home</a>
        <a href="#services">Services</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
    </div>

    <button class="toggle-btn" id="toggleBtn" onclick="toggleSidebar()">&#9776;</button>

    <div class="content" id="content">
        <header>
            <h1>Dev-ly</h1>
            <p>Delivering Cutting-Edge Technology Solutions</p>
        </header>

        <section id="hero" class="hero">
            <h1>Your Tech Solution Starts Here</h1>
            <p>We provide top-notch services in content creation, programming, web development, and more.</p>
            <button>Explore Now</button>
        </section>

        <section id="services" class="services">
            <div class="service-card">
                <h3>Content Creation</h3>
                <p>Engaging and high-quality content tailored for your audience.</p>
                <button>Learn More</button>
            </div>
            <div class="service-card">
                <h3>Programming</h3>
                <p>Custom software solutions to meet your unique requirements.</p>
                <button>Learn More</button>
            </div>
            <div class="service-card">
                <h3>Web Development</h3>
                <p>Modern and responsive websites that bring your vision to life.</p>
                <button>Learn More</button>
            </div>
            <div class="service-card">
                <h3>IT Consultation</h3>
                <p>Expert advice to optimize your technological infrastructure.</p>
                <button>Learn More</button>
            </div>
        </section>

        <footer>
            <p>&copy; 2025 Tech Services. All rights reserved. | <a href="#">Privacy Policy</a> | <a href="#">Terms of Service</a></p>
        </footer>
    </div>

    <script>
        function toggleSidebar() {
            const sidebar = document.getElementById('sidebar');
            const content = document.getElementById('content');
            const toggleBtn = document.getElementById('toggleBtn');

            sidebar.classList.toggle('minimized');
            content.classList.toggle('minimized');

            if (sidebar.classList.contains('minimized')) {
                toggleBtn.style.left = '10px';
            } else {
                toggleBtn.style.left = '250px';
            }
        }
    </script>
</body>
</html>
