<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine?</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #ff9a9e, #fecfef);
            color: #333;
            text-align: center;
            padding: 50px;
            margin: 0;
            overflow: hidden;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.9);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        h1 {
            font-size: 2.5em;
            color: #e91e63;
            margin-bottom: 20px;
        }
        p {
            font-size: 1.2em;
            line-height: 1.6;
            margin-bottom: 30px;
        }
        .buttons {
            position: relative;
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }
        button {
            padding: 15px 30px;
            font-size: 1.2em;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        #yes {
            background: #4caf50;
            color: white;
            transform: scale(1);
        }
        #no {
            background: #f44336;
            color: white;
            position: absolute;
        }
        .hearts {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
        }
        .heart {
            position: absolute;
            color: #ff4081;
            font-size: 2em;
            animation: float 3s infinite ease-in-out;
        }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>💕 Will You Be My Valentine? 💕</h1>
        <p>Hey my love, I've been thinking about you all day. You're the sweetest, funniest, and most amazing person I know. Will you make me the happiest by saying yes to being my Valentine? I promise lots of cuddles, kisses, and fun! 😘</p>
        
        <div class="buttons">
            <button id="yes">Yes! 💖</button>
            <button id="no">No 😢</button>
        </div>
        
        <div class="hearts" id="hearts"></div>
    </div>

    <script>
        const yesButton = document.getElementById('yes');
        const noButton = document.getElementById('no');
        const heartsContainer = document.getElementById('hearts');
        let yesScale = 1;

        // Function to create floating hearts
        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.textContent = '❤️';
            heart.style.left = Math.random() * 100 + '%';
            heart.style.animationDelay = Math.random() * 3 + 's';
            heartsContainer.appendChild(heart);
            setTimeout(() => heart.remove(), 3000);
        }

        // Make "No" button move away on hover/click
        noButton.addEventListener('mouseenter', () => {
            const container = document.querySelector('.container');
            const containerRect = container.getBoundingClientRect();
            const buttonRect = noButton.getBoundingClientRect();
            
            let newLeft = Math.random() * (containerRect.width - buttonRect.width);
            let newTop = Math.random() * (containerRect.height - buttonRect.height);
            
            noButton.style.left = newLeft + 'px';
            noButton.style.top = newTop + 'px';
            
            // Make "Yes" button bigger
            yesScale += 0.2;
            yesButton.style.transform = `scale(${yesScale})`;
            
            // Add a heart for fun
            createHeart();
        });

        // "Yes" button click: Show a cute response
        yesButton.addEventListener('click', () => {
            alert('Yay! I knew you\'d say yes! 💕 You\'re the best! Let\'s plan our perfect Valentine\'s Day. 😍');
            // You could redirect to a surprise page here if you want
        });
    </script>
</body>
</html>
