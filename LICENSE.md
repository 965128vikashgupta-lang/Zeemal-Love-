<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Open Your Gift! 🎁</title>
    <style>
        body {
            background: #ffe5ec;
            font-family: 'Poppins', sans-serif;
            height: 100vh;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        /* Prank Button Styles */
        #prank-section { text-align: center; }
        .moving-btn {
            background-color: #ff4d6d;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            position: absolute; /* Dynamic position */
            transition: 0.1s;
            box-shadow: 0 5px 15px rgba(255, 77, 109, 0.4);
        }

        /* Surprise Section (Hidden) */
        #surprise-section {
            display: none;
            text-align: center;
            animation: zoomIn 1s ease-out;
        }

        .main-rose { font-size: 120px; animation: pulse 1.5s infinite; }
        h1 { color: #ff4d6d; font-size: 2.5rem; margin-bottom: 10px; }
        .love-letter {
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            max-width: 300px;
            margin: 0 auto;
            border-left: 5px solid #ff4d6d;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        @keyframes zoomIn {
            from { transform: scale(0); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        .falling-rose {
            position: absolute;
            top: -10%;
            pointer-events: none;
            animation: fall linear forwards;
        }
        @keyframes fall { to { transform: translateY(110vh) rotate(360deg); } }
    </style>
</head>
<body>

    <div id="prank-section">
        <h2 id="instruction-text">Aapke liye ek surprise hai!<br>Niche click karo 👇</h2>
        <button id="runaway-btn" class="moving-btn" onmouseover="moveButton()" onclick="handleClick()">Click Me! 🎁</button>
    </div>

    <div id="surprise-section">
        <div class="main-rose">🌹</div>
        <h1>Happy Rose Day, Jaan!</h1>
        <div class="love-letter">
            <p><strong>Uff! Kitni mehnat karwayi na?</strong></p>
            <p>Bilkul aise hi main hamesha tumhare peeche bhagunga. Tum door ho, par is gulab ki khushbu ki tarah mere har pal mein ho.</p>
            <p style="color: #ff4d6d;">❤️ I Love You So Much! ❤️</p>
        </div>
    </div>

    <script>
        let clickCount = 0;
        const btn = document.getElementById('runaway-btn');
        const instruction = document.getElementById('instruction-text');

        // Button bhagane wala logic
        function moveButton() {
            if (clickCount < 5) { // 5 baar bhagega button
                const x = Math.random() * (window.innerWidth - btn.offsetWidth);
                const y = Math.random() * (window.innerHeight - btn.offsetHeight);
                btn.style.left = x + 'px';
                btn.style.top = y + 'px';
                
                // Messages change hote rahenge
                const lines = ["Pakad ke dikhao! 😜", "Ofo! Miss ho gaya..", "Itni jaldi nahi milega! 😂", "Almost there..", "Ek baar aur!"];
                instruction.innerHTML = lines[clickCount];
                clickCount++;
            }
        }

        // Final click par kya hoga
        function handleClick() {
            if (clickCount >= 5) {
                document.getElementById('prank-section').style.display = 'none';
                document.getElementById('surprise-section').style.display = 'block';
                startRoseRain();
            }
        }

        function startRoseRain() {
            setInterval(() => {
                const rose = document.createElement('div');
                rose.classList.add('falling-rose');
                rose.innerHTML = '🌹';
                rose.style.left = Math.random() * 100 + 'vw';
                rose.style.fontSize = Math.random() * 20 + 20 + 'px';
                rose.style.animationDuration = Math.random() * 3 + 2 + 's';
                document.body.appendChild(rose);
                setTimeout(() => rose.remove(), 5000);
            }, 200);
        }
    </script>
</body>
</html>
