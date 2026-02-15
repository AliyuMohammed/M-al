<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Maryam ❤️</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Quicksand:wght@400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-dark: #120507;
            --card-bg: #221014;
            --valentine-pink: #ff2d55;
            --white: #ffffff;
        }

        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            background-color: var(--bg-dark);
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Quicksand', sans-serif;
            overflow: hidden;
            touch-action: none; /* Disables double-tap zoom for better button escaping */
        }

        .card {
            background: var(--card-bg);
            padding: 50px 30px;
            border-radius: 40px;
            box-shadow: 0 0 40px rgba(0, 0, 0, 0.8);
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.05);
            width: 85%;
            max-width: 380px;
            position: relative;
        }

        h1 {
            font-family: 'Dancing Script', cursive;
            color: var(--white);
            font-size: 3.2rem;
            margin: 0 0 10px 0;
        }

        p.sub-text {
            color: #b3888e;
            font-size: 1rem;
            margin-bottom: 40px;
        }

        h2.question {
            color: var(--white);
            font-family: 'Quicksand', sans-serif;
            font-size: 1.3rem;
            font-weight: 400;
            margin-bottom: 50px;
        }

        .btn-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
            height: 150px; /* Buffer for button movement */
        }

        #yesBtn {
            background-color: var(--valentine-pink);
            color: white;
            width: 220px;
            padding: 18px;
            border-radius: 50px;
            font-size: 1.3rem;
            font-weight: 700;
            border: none;
            cursor: pointer;
            transition: transform 0.2s;
            z-index: 5;
        }

        /* The NO Button - Specifically designed to match your video */
        #noBtn {
            background-color: var(--white);
            color: var(--valentine-pink);
            width: 100px;
            height: 50px;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 700;
            border: none;
            position: absolute;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            /* Smooth transition for the position, plus a 'stretch' scale effect */
            transition: top 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), 
                        left 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), 
                        transform 0.2s ease-out, 
                        height 0.2s ease-out;
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
            /* Initial position below YES */
            bottom: 60px;
            left: 50%;
            transform: translateX(-50%);
        }

        /* This mimics the "stretching pill" effect from your video */
        #noBtn.active {
            height: 120px; 
            transform: translateX(-50%) scaleX(0.7);
        }

        #celebration {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: var(--bg-dark);
            z-index: 1000;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
        }

        .heart { font-size: 100px; color: var(--valentine-pink); animation: pulse 0.6s infinite alternate; }
        @keyframes pulse { to { transform: scale(1.2); } }
    </style>
</head>
<body>

    <div class="card" id="mainCard">
        <h1>I Love You</h1>
        <p class="sub-text">From the bottom of my heart</p>
        
        <h2 class="question">Will you be my Valentine, Maryam🤭?</h2>

        <div class="btn-container">
            <button id="yesBtn" onclick="celebrate()">YES</button>
            <button id="noBtn" onmouseover="teleportNo()" ontouchstart="teleportNo()">No</button>
        </div>
    </div>

    <div id="celebration">
        <div class="heart">❤️</div>
         <h1 style="font-size: 4rem;">I Knew It!</h1>
        <p style="font-size: 1.8rem; font-family: 'Dancing Script'; margin-top: 20px;">
            You've made me the happiest person alive, Maryam. <br>
            I love you today, tomorrow, and forever.
        </p>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');

        function teleportNo() {
            // 1. Add the stretching class (makes it look like a long pill)
            noBtn.classList.add('active');

            // 2. Calculate a safe random zone
            const padding = 60;
            const screenWidth = window.innerWidth - noBtn.offsetWidth - padding;
            const screenHeight = window.innerHeight - noBtn.offsetHeight - padding;

            const randomX = Math.max(padding, Math.floor(Math.random() * screenWidth));
            const randomY = Math.max(padding, Math.floor(Math.random() * screenHeight));

            // 3. Move the button
            noBtn.style.position = 'fixed';
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';
            
            // 4. Reset the stretch after a delay (makes it "snap" back into a normal shape)
            setTimeout(() => {
                noBtn.classList.remove('active');
            }, 300);
        }

        function celebrate() {
            document.getElementById('mainCard').style.display = 'none';
            document.getElementById('celebration').style.display = 'flex';
        }
    </script>
</body>
</html>
