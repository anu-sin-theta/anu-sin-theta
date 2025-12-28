<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Optimus Prime | Anubhav Singh</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #0a0a0a;
            color: #fff;
            overflow-x: hidden;
        }

        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #0a0a0a 100%);
        }

        .hero::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 50%, rgba(0, 255, 255, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 50%, rgba(255, 0, 255, 0.1) 0%, transparent 50%);
            animation: pulse 8s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 0.6; }
        }

        .title-container {
            position: relative;
            z-index: 1;
            text-align: center;
            opacity: 0;
            transform: translateY(50px);
            animation: fadeInUp 1.5s ease forwards;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .main-title {
            font-size: clamp(3rem, 12vw, 10rem);
            font-weight: 900;
            background: linear-gradient(45deg, #00ffff, #ff00ff, #ffff00, #00ffff);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 5s ease infinite;
            text-transform: uppercase;
            letter-spacing: -0.05em;
            line-height: 0.9;
            margin-bottom: 0.2em;
            text-shadow: 0 0 80px rgba(0, 255, 255, 0.5);
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .subtitle {
            font-size: clamp(1.5rem, 4vw, 3rem);
            font-weight: 300;
            color: #00ffff;
            letter-spacing: 0.3em;
            text-transform: uppercase;
            margin-top: 1rem;
            opacity: 0;
            animation: fadeIn 2s ease 0.5s forwards;
        }

        @keyframes fadeIn {
            to { opacity: 1; }
        }

        .tagline {
            font-size: clamp(1rem, 2vw, 1.5rem);
            color: #888;
            margin-top: 2rem;
            opacity: 0;
            animation: fadeIn 2s ease 1s forwards;
        }

        .scroll-indicator {
            position: absolute;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%);
            opacity: 0;
            animation: fadeIn 2s ease 1.5s forwards, bounce 2s ease-in-out 2s infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(10px); }
        }

        .scroll-indicator::before {
            content: '↓';
            font-size: 2rem;
            color: #00ffff;
        }

        section {
            min-height: 100vh;
            padding: 5rem 2rem;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        .section-title {
            font-size: clamp(2.5rem, 6vw, 5rem);
            font-weight: 800;
            margin-bottom: 3rem;
            background: linear-gradient(90deg, #00ffff, #ff00ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-transform: uppercase;
            opacity: 0;
            transform: translateX(-100px);
            transition: all 1s ease;
        }

        .section-title.visible {
            opacity: 1;
            transform: translateX(0);
        }

        .content-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            width: 100%;
            opacity: 0;
            transform: translateY(50px);
            transition: all 1s ease 0.3s;
        }

        .content-grid.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(0, 255, 255, 0.2);
            border-radius: 20px;
            padding: 2rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 255, 0.1), transparent);
            transform: rotate(45deg);
            transition: all 0.5s ease;
        }

        .card:hover::before {
            left: 100%;
        }

        .card:hover {
            transform: translateY(-10px);
            border-color: rgba(0, 255, 255, 0.6);
            box-shadow: 0 10px 40px rgba(0, 255, 255, 0.3);
        }

        .card h3 {
            color: #00ffff;
            font-size: 1.5rem;
            margin-bottom: 1rem;
            font-weight: 700;
        }

        .card p {
            color: #ccc;
            line-height: 1.6;
            position: relative;
            z-index: 1;
        }

        .social-links {
            display: flex;
            gap: 2rem;
            margin-top: 2rem;
            flex-wrap: wrap;
            justify-content: center;
        }

        .social-link {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid #00ffff;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            color: #00ffff;
            font-size: 1.5rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .social-link::before {
            content: '';
            position: absolute;
            width: 0;
            height: 100%;
            background: #00ffff;
            transition: all 0.3s ease;
            z-index: -1;
        }

        .social-link:hover::before {
            width: 100%;
        }

        .social-link:hover {
            color: #0a0a0a;
            transform: scale(1.2) rotate(360deg);
        }

        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            justify-content: center;
            max-width: 800px;
        }

        .tech-item {
            padding: 0.8rem 1.5rem;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 0, 255, 0.3);
            border-radius: 50px;
            color: #ff00ff;
            font-weight: 600;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .tech-item:hover {
            background: rgba(255, 0, 255, 0.2);
            transform: scale(1.1);
            box-shadow: 0 5px 20px rgba(255, 0, 255, 0.4);
        }

        .cta-button {
            padding: 1.2rem 3rem;
            background: linear-gradient(45deg, #00ffff, #ff00ff);
            border: none;
            border-radius: 50px;
            color: #fff;
            font-size: 1.2rem;
            font-weight: 700;
            cursor: pointer;
            text-decoration: none;
            display: inline-block;
            margin-top: 2rem;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 0.1em;
        }

        .cta-button:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 40px rgba(0, 255, 255, 0.5);
        }

        .stats {
            display: flex;
            gap: 3rem;
            margin-top: 3rem;
            flex-wrap: wrap;
            justify-content: center;
        }

        .stat-item {
            text-align: center;
        }

        .stat-number {
            font-size: 3rem;
            font-weight: 900;
            color: #00ffff;
            display: block;
        }

        .stat-label {
            color: #888;
            text-transform: uppercase;
            font-size: 0.9rem;
            letter-spacing: 0.2em;
        }

        @media (max-width: 768px) {
            .main-title {
                font-size: 2.5rem;
            }
            .subtitle {
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <div class="hero">
        <div class="title-container">
            <h1 class="main-title">OPTIMUS<br>PRIME</h1>
            <p class="subtitle">Anubhav Singh</p>
            <p class="tagline">Cybersecurity × Cloud × IoT Architect</p>
        </div>
        <div class="scroll-indicator"></div>
    </div>

    <section id="about">
        <h2 class="section-title">Mission Statement</h2>
        <div class="content-grid">
            <div class="card">
                <h3>🚀 Current Mission</h3>
                <p>Leading innovation at Google Developer Groups Mathura 2024-2025. Leveraging AI, IoT, and Cloud technologies to revolutionize agricultural systems and empower farmers worldwide.</p>
            </div>
            <div class="card">
                <h3>⚡ Expertise</h3>
                <p>Specialized in the convergence of Cybersecurity, Cloud Computing (GCP), and Internet of Things. Building secure, scalable solutions for tomorrow's challenges.</p>
            </div>
            <div class="card">
                <h3>🎯 Philosophy</h3>
                <p>"Somebody is working harder than you for the same goal as yours" — Driven by continuous improvement and relentless innovation.</p>
            </div>
        </div>
    </section>

    <section id="tech">
        <h2 class="section-title">Arsenal</h2>
        <div class="tech-stack">
            <div class="tech-item">Python</div>
            <div class="tech-item">AWS</div>
            <div class="tech-item">Azure</div>
            <div class="tech-item">GCP</div>
            <div class="tech-item">Arduino</div>
            <div class="tech-item">Linux</div>
            <div class="tech-item">TensorFlow</div>
            <div class="tech-item">PostgreSQL</div>
            <div class="tech-item">Git</div>
            <div class="tech-item">Pandas</div>
            <div class="tech-item">Seaborn</div>
        </div>
        <div class="stats">
            <div class="stat-item">
                <span class="stat-number">24/7</span>
                <span class="stat-label">Innovation Mode</span>
            </div>
            <div class="stat-item">
                <span class="stat-number">∞</span>
                <span class="stat-label">Possibilities</span>
            </div>
            <div class="stat-item">
                <span class="stat-number">100%</span>
                <span class="stat-label">Dedication</span>
            </div>
        </div>
    </section>

    <section id="connect">
        <h2 class="section-title">Connect</h2>
        <p style="color: #888; max-width: 600px; text-align: center; margin-bottom: 2rem; font-size: 1.2rem;">
            Ready to collaborate on groundbreaking projects? Let's build the future together.
        </p>
        <div class="social-links">
            <a href="https://twitter.com/anubhav_singh20" class="social-link" target="_blank" title="Twitter">𝕏</a>
            <a href="https://www.linkedin.com/in/anubhav-singh-thedatum/" class="social-link" target="_blank" title="LinkedIn">in</a>
            <a href="https://instagram.com/the_unfocused_lens" class="social-link" target="_blank" title="Instagram">📷</a>
            <a href="https://github.com/anu-sin-theta" class="social-link" target="_blank" title="GitHub">⚡</a>
        </div>
        <a href="https://anufied.me" class="cta-button" target="_blank">Explore Projects</a>
    </section>

    <script>
        // Intersection Observer for scroll animations
        const observerOptions = {
            threshold: 0.2,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        // Observe all section titles and content grids
        document.querySelectorAll('.section-title, .content-grid, .tech-stack, .social-links').forEach(el => {
            observer.observe(el);
        });

        // Smooth scroll for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });

        // Parallax effect on hero
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const hero = document.querySelector('.hero');
            if (hero) {
                hero.style.transform = `translateY(${scrolled * 0.5}px)`;
                hero.style.opacity = 1 - (scrolled / window.innerHeight);
            }
        });
    </script>
</body>
</html>
