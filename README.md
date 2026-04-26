<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mansi Nishad — Data Analyst</title>
    <link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=DM+Sans:wght@400;500&family=JetBrains+Mono&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --pink: #f472b6; --purple: #a78bfa; --cyan: #22d3ee;
            --bg: #07050f; --bg2: #0d0b1a; --border: rgba(167,139,250,0.15);
            --text: #e2e8f0;
        }

        body {
            background: var(--bg);
            color: var(--text);
            font-family: 'DM Sans', sans-serif;
            margin: 0; padding: 20px;
        }

        .container { max-width: 800px; margin: 0 auto; }

        /* HERO SECTION */
        .hero {
            position: relative;
            background: var(--bg2);
            border: 1px solid var(--border);
            border-radius: 24px;
            padding: 40px;
            display: flex;
            align-items: center;
            gap: 30px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        #matrixCanvas {
            position: absolute; top: 0; left: 0;
            width: 100%; height: 100%;
            opacity: 0.15; pointer-events: none;
        }

        .avatar-wrap { position: relative; z-index: 2; }
        
        .avatar-img {
            width: 150px; height: 150px;
            border-radius: 50%;
            border: 3px solid var(--pink);
            object-fit: cover;
            animation: float 4s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .hero-text { z-index: 2; }
        .hero-name { font-family: 'Syne', sans-serif; font-size: 2.5rem; margin: 0; }
        .accent { color: var(--pink); }

        /* SKILLS */
        .sk-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-top: 30px; }
        .sk-card { background: var(--bg2); padding: 15px; border-radius: 12px; border: 1px solid var(--border); }
        .sk-fill { height: 6px; border-radius: 10px; background: var(--purple); width: 0; transition: 2s; }

        /* PROJECTS */
        .proj-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 30px; }
        .proj-card { 
            background: var(--bg2); border: 1px solid var(--border); 
            padding: 20px; border-radius: 15px; text-decoration: none; color: inherit;
            transition: 0.3s;
        }
        .proj-card:hover { transform: translateY(-5px); border-color: var(--cyan); }
    </style>
</head>
<body>

<div class="container">
    <div class="hero" id="hero">
        <canvas id="matrixCanvas"></canvas>
        <div class="avatar-wrap">
            <img class="avatar-img" src="https://via.placeholder.com/150" alt="Mansi">
        </div>
        <div class="hero-text">
            <p style="color: var(--cyan); font-family: 'JetBrains Mono';">DATA ANALYST</p>
            <h1 class="hero-name">Mansi <span class="accent">Nishad</span></h1>
            <p>Turning raw data into meaningful stories.</p>
        </div>
    </div>

    <div class="sk-grid">
        <div class="sk-card">Excel <div class="sk-fill" style="width: 90%; background: var(--pink);"></div></div>
        <div class="sk-card">SQL <div class="sk-fill" style="width: 85%; background: var(--purple);"></div></div>
        <div class="sk-card">Python <div class="sk-fill" style="width: 80%; background: var(--cyan);"></div></div>
        <div class="sk-card">Power BI <div class="sk-fill" style="width: 75%; background: #4ade80;"></div></div>
    </div>

    <div class="proj-grid">
        <a href="#" class="proj-card">
            <h3>📊 Sales Dashboard</h3>
            <p>Advanced data visualization using Excel and Power BI.</p>
        </a>
        <a href="#" class="proj-card">
            <h3>🐍 Python Automation</h3>
            <p>Web scraping and data cleaning scripts.</p>
        </a>
    </div>
</div>

<script>
    // Matrix Effect
    const canvas = document.getElementById('matrixCanvas');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = 400;
    const letters = "010101PYTHONSQLDATA";
    const fontSize = 10;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function draw() {
        ctx.fillStyle = "rgba(7, 5, 15, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "#a78bfa";
        ctx.font = fontSize + "px monospace";
        for (let i = 0; i < drops.length; i++) {
            const text = letters[Math.floor(Math.random() * letters.length)];
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
            drops[i]++;
        }
    }
    setInterval(draw, 33);
</script>

</body>
</html>
show output of thsi code
