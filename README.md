<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>POWERMOD | Официальный доступ</title>
    <style>
        body { margin: 0; padding: 0; background: #000; color: #00ff41; font-family: 'Courier New', monospace; overflow: hidden; }
        canvas { position: absolute; top: 0; left: 0; z-index: 1; }
        .content { position: relative; z-index: 2; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; text-align: center; background: rgba(0,0,0,0.7); }
        h1 { font-size: 4rem; letter-spacing: 10px; margin: 0; text-shadow: 0 0 20px #00ff41; }
        p { font-size: 1.2rem; margin-bottom: 30px; opacity: 0.8; }
        .btn { border: 2px solid #00ff41; background: transparent; color: #00ff41; padding: 15px 40px; font-size: 1.1rem; cursor: pointer; text-transform: uppercase; transition: 0.3s; position: relative; overflow: hidden; }
        .btn:hover { background: #00ff41; color: #000; box-shadow: 0 0 30px #00ff41; }
        #key-box { margin-top: 25px; font-weight: bold; font-size: 1.5rem; letter-spacing: 2px; height: 30px; }
    </style>
</head>
<body>

<canvas id="matrix"></canvas>

<div class="content">
    <h1>POWERMOD</h1>
    <p>СИСТЕМА УПРАВЛЕНИЯ ДОСТУПОМ</p>
    <button class="btn" onclick="getKey()">Получить ключ бесплатно</button>
    <div id="key-box"></div>
</div>

<script>
    // Анимация заднего фона (Matrix)
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    const chars = "01ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    const fontSize = 16;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function draw() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "#0F0";
        ctx.font = fontSize + "px arial";
        for (let i = 0; i < drops.length; i++) {
            const text = chars.charAt(Math.floor(Math.random() * chars.length));
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
            drops[i]++;
        }
    }
    setInterval(draw, 33);

    // Логика кнопки
    function getKey() {
        const box = document.getElementById('key-box');
        box.style.color = "#fff";
        box.innerText = "ПОДКЛЮЧЕНИЕ...";
        
        setTimeout(() => {
            const key = "PWR-" + Math.random().toString(36).substr(2, 5).toUpperCase() + "-" + Math.random().toString(36).substr(2, 5).toUpperCase();
            box.innerText = key;
            box.style.color = "#00ff41";
        }, 1500);
    }
</script>

</body>
</html>
