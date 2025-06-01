# Tonoto-s-love
quiero amarte toda la f*cking life
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atrévete a Amar</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Courier+Prime:wght@400;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Dancing Script', cursive;
            background-color: #000;
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            transition: background-color 1s ease;
            position: relative;
        }

        /* Flores creciendo en el fondo inicial */
        .flowers-background {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExeXFwdnd2ZW5iOG9zMzFmZDg4b2N1M2wwaHE3OTc5MW1yNjlsazhrbSZlcD12MV9naWZzX3NlYXJjaCZjdD1n/PDnFFuE7mJ7by/giphy.gif');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            opacity: 0.3;
            z-index: -1;
        }

        .container {
            text-align: center;
            max-width: 800px;
            padding: 20px;
            position: relative;
            z-index: 1;
        }

        .main-text {
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 2rem;
            opacity: 0;
            animation: fadeIn 3s ease-in-out forwards;
            text-shadow: 2px 2px 4px rgba(255, 255, 255, 0.8);
        }

        .dedication {
            font-family: 'Courier Prime', monospace;
            font-size: 1.2rem;
            color: #ccc;
            font-weight: 700;
            opacity: 0;
            animation: fadeIn 2s ease-in-out 4s forwards;
            margin-bottom: 2rem;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
        }

        .buttons-container {
            opacity: 0;
            animation: fadeIn 2s ease-in-out 5s forwards;
        }

        .choice-btn {
            font-family: 'Dancing Script', cursive;
            font-size: 2rem;
            font-weight: 700;
            padding: 15px 40px;
            margin: 0 20px;
            border: 3px solid white;
            background: transparent;
            color: white;
            cursor: pointer;
            border-radius: 50px;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .choice-btn:hover {
            background: white;
            color: black;
            transform: scale(1.1);
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.5);
        }

        /* Respuesta del sí */
        .yes-response {
            display: none;
            text-align: center;
            opacity: 0;
            position: relative;
            z-index: 5;
        }

        .yes-response.active {
            display: block;
            animation: fadeIn 2s ease-in-out forwards;
        }

        .promise-text {
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 2rem;
            color: #333;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        }

        .love-text {
            font-size: 4rem;
            font-weight: 700;
            color: #FF69B4;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.2);
        }

        /* Corazones cayendo */
        .falling-hearts {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
            overflow: hidden;
            z-index: 10;
        }

        .falling-heart {
            position: absolute;
            font-size: 2.5rem;
            animation: fall linear infinite;
            opacity: 0.8;
        }

        .falling-heart:nth-child(1) { left: 5%; animation-duration: 4s; animation-delay: 0s; color: #FFB6C1; }
        .falling-heart:nth-child(2) { left: 15%; animation-duration: 5s; animation-delay: 0.5s; color: #FFC0CB; }
        .falling-heart:nth-child(3) { left: 25%; animation-duration: 4.5s; animation-delay: 1s; color: #FFCCCB; }
        .falling-heart:nth-child(4) { left: 35%; animation-duration: 5.5s; animation-delay: 1.5s; color: #FFB6C1; }
        .falling-heart:nth-child(5) { left: 45%; animation-duration: 4s; animation-delay: 2s; color: #F8BBD9; }
        .falling-heart:nth-child(6) { left: 55%; animation-duration: 5s; animation-delay: 2.5s; color: #FFC0CB; }
        .falling-heart:nth-child(7) { left: 65%; animation-duration: 4.5s; animation-delay: 3s; color: #FFCCCB; }
        .falling-heart:nth-child(8) { left: 75%; animation-duration: 5.5s; animation-delay: 3.5s; color: #FFB6C1; }
        .falling-heart:nth-child(9) { left: 85%; animation-duration: 4s; animation-delay: 4s; color: #F8BBD9; }
        .falling-heart:nth-child(10) { left: 95%; animation-duration: 5s; animation-delay: 4.5s; color: #FFC0CB; }

        .no-response {
            display: none;
            text-align: center;
            opacity: 0;
        }

        .no-response.active {
            display: block;
            animation: fadeInOut 6s ease-in-out forwards;
        }

        .goodbye-text {
            font-size: 2.5rem;
            font-weight: 700;
            text-shadow: 2px 2px 4px rgba(255, 255, 255, 0.3);
        }

        .pink-background {
            background: linear-gradient(135deg, #FFC5D3, #FFE4E8, #FFC5D3);
            color: #333;
        }

        .pink-background .flowers-background {
            display: none;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeInOut {
            0% { opacity: 0; transform: translateY(30px); }
            20% { opacity: 1; transform: translateY(0); }
            80% { opacity: 1; transform: translateY(0); }
            100% { opacity: 0; transform: translateY(-30px); }
        }

        @keyframes showLetter {
            from { 
                opacity: 0; 
                transform: translateY(30px) scale(0.9); 
            }
            to { 
                opacity: 1; 
                transform: translateY(0) scale(1); 
            }
        }

        @keyframes fall {
            0% {
                transform: translateY(-10vh) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(110vh) rotate(360deg);
                opacity: 0.3;
            }
        }

        .hidden {
            display: none !important;
        }

        @media (max-width: 768px) {
            .main-text {
                font-size: 2rem;
            }
            
            .choice-btn {
                font-size: 1.5rem;
                padding: 12px 30px;
                margin: 10px;
                display: block;
                width: 200px;
                margin-left: auto;
                margin-right: auto;
                margin-bottom: 20px;
            }
            
            .promise-text {
                font-size: 2rem;
            }
            
            .love-text {
                font-size: 2.5rem;
            }
            
            .goodbye-text {
                font-size: 1.8rem;
            }

            .signature {
                font-size: 0.8rem;
            }
        }
    </style>
</head>
<body>
    <div class="flowers-background"></div>
    
    <div class="container">
        <div id="initial-screen">
            <h1 class="main-text">Atrévete a amar una vez más</h1>
            <div class="dedication">- De Edwin Mendoza, para Leslie Tipan</div>
            <div class="buttons-container">
                <button class="choice-btn" onclick="chooseYes()">Sí</button>
                <button class="choice-btn" onclick="chooseNo()">No</button>
            </div>
        </div>

        <div id="yes-screen" class="yes-response">
            <div class="falling-hearts">
                <div class="falling-heart">♥</div>
                <div class="falling-heart">♥</div>
                <div class="falling-heart">♥</div>
                <div class="falling-heart">♥</div>
                <div class="falling-heart">♥</div>
                <div class="falling-heart">♥</div>
                <div class="falling-heart">♥</div>
                <div class="falling-heart">♥</div>
                <div class="falling-heart">♥</div>
                <div class="falling-heart">♥</div>
            </div>
            
            <div class="promise-text">Prometo construir un futuro juntos</div>
            <div class="love-text">Te amo</div>
        </div>

        <div id="no-screen" class="no-response">
            <h2 class="goodbye-text">Sé feliz, lamento no ser lo que esperabas</h2>
        </div>
    </div>

    <script>
        function chooseYes() {
            // Ocultar pantalla inicial
            document.getElementById('initial-screen').classList.add('hidden');
            
            // Cambiar fondo a rosa pastel
            document.body.classList.add('pink-background');
            
            // Mostrar respuesta del sí
            const yesScreen = document.getElementById('yes-screen');
            yesScreen.classList.add('active');
        }

        function chooseNo() {
            // Ocultar pantalla inicial
            document.getElementById('initial-screen').classList.add('hidden');
            
            // Mostrar respuesta del no
            const noScreen = document.getElementById('no-screen');
            noScreen.classList.add('active');
            
            // Después de 6 segundos, ocultar todo y dejar fondo negro
            setTimeout(() => {
                noScreen.classList.add('hidden');
            }, 6000);
        }

        // Prevenir clic derecho y selección de texto para una experiencia más inmersiva
        document.addEventListener('contextmenu', e => e.preventDefault());
        document.addEventListener('selectstart', e => e.preventDefault());
    </script>
</body>
</html>
