<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Komal ❤️</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #ffafcc, #ffc8dd);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            overflow-x: hidden;
        }
        
        .container {
            background: white;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            max-width: 600px;
            width: 100%;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            position: relative;
            z-index: 10;
        }
        
        h1 {
            color: #ff4d7e;
            margin-bottom: 25px;
            font-size: 2rem;
            line-height: 1.4;
        }
        
        .name {
            color: #ff3366;
            font-weight: bold;
            display: block;
            margin-top: 5px;
        }
        
        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
            flex-wrap: wrap;
        }
        
        .btn {
            padding: 15px 40px;
            font-size: 1.2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            min-width: 120px;
        }
        
        .yes {
            background: #ff4d7e;
            color: white;
        }
        
        .no {
            background: #6c757d;
            color: white;
        }
        
        .yes:hover {
            background: #ff3366;
            transform: scale(1.05);
        }
        
        .message {
            margin-top: 30px;
            padding: 20px;
            background: #fff5f7;
            border-radius: 15px;
            display: none;
            border-left: 5px solid #ff4d7e;
        }
        
        .message h2 {
            color: #ff3366;
            margin-bottom: 10px;
        }
        
        .message p {
            font-size: 1.1rem;
            color: #555;
        }
        
        .icon {
            margin: 0 5px;
        }
        
        .heart {
            color: #ff4d7e;
        }
        
        .cat {
            color: #ff9966;
        }
        
        /* Floating elements */
        .floating {
            position: absolute;
            font-size: 30px;
            z-index: 1;
            animation: float 15s infinite linear;
            opacity: 0.8;
        }
        
        .heart-float {
            color: #ff4d7e;
        }
        
        .cat-float {
            color: #ff9966;
        }
        
        .rose-float {
            color: #ff3333;
        }
        
        @keyframes float {
            0% { transform: translate(0, 0) rotate(0deg); }
            25% { transform: translate(20px, -30px) rotate(5deg); }
            50% { transform: translate(-15px, -50px) rotate(-5deg); }
            75% { transform: translate(-20px, -30px) rotate(5deg); }
            100% { transform: translate(0, 0) rotate(0deg); }
        }
        
        /* Mobile styles */
        @media (max-width: 600px) {
            .container {
                padding: 20px;
                margin-top: 20px;
            }
            
            h1 {
                font-size: 1.6rem;
            }
            
            .btn {
                padding: 12px 30px;
                font-size: 1.1rem;
                min-width: 100px;
            }
            
            .buttons {
                gap: 15px;
            }
            
            .floating {
                font-size: 24px;
            }
        }
        
        @media (max-width: 400px) {
            h1 {
                font-size: 1.4rem;
            }
            
            .buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 80%;
            }
        }
    </style>
</head>
<body>
    <!-- Floating elements -->
    <div class="floating heart-float" id="heart1" style="left: 10%; top: 20%;"><i class="fas fa-heart"></i></div>
    <div class="floating heart-float" id="heart2" style="left: 80%; top: 30%;"><i class="fas fa-heart"></i></div>
    <div class="floating heart-float" id="heart3" style="left: 15%; top: 70%;"><i class="fas fa-heart"></i></div>
    <div class="floating cat-float" id="cat1" style="left: 70%; top: 10%;"><i class="fas fa-cat"></i></div>
    <div class="floating cat-float" id="cat2" style="left: 85%; top: 60%;"><i class="fas fa-cat"></i></div>
    <div class="floating rose-float" id="rose1" style="left: 20%; top: 10%;"><i class="fas fa-spa"></i></div>
    <div class="floating rose-float" id="rose2" style="left: 60%; top: 80%;"><i class="fas fa-spa"></i></div>
    
    <div class="container">
        <h1>
            Will you be my Valentine,<br>
            <span class="name">My cutiepatutie Komal??</span>
        </h1>
        
        <div class="buttons">
            <button class="btn yes" id="yesBtn">YES</button>
            <button class="btn no" id="noBtn">NO</button>
        </div>
        
        <div class="message" id="message">
            <h2>I Know u will say yes! <i class="fas fa-heart icon heart"></i></h2>
            <p>You're the best thing that ever happened to me! <i class="fas fa-cat icon cat"></i> <i class="fas fa-heart icon heart"></i></p>
            <p>Can't wait to celebrate with you! <i class="fas fa-heart icon heart"></i> <i class="fas fa-cat icon cat"></i></p>
        </div>
    </div>

    <script>
        // Get elements
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const message = document.getElementById('message');
        const floatingElements = document.querySelectorAll('.floating');
        
        // Make NO button move when clicked or hovered
        noBtn.addEventListener('mouseover', moveButton);
        noBtn.addEventListener('click', moveButton);
        
        // For mobile touch
        noBtn.addEventListener('touchstart', function(e) {
            e.preventDefault();
            moveButton();
        });
        
        function moveButton() {
            // Get random position within screen
            const maxX = window.innerWidth - noBtn.offsetWidth - 50;
            const maxY = window.innerHeight - noBtn.offsetHeight - 50;
            
            const randomX = Math.floor(Math.random() * maxX);
            const randomY = Math.floor(Math.random() * maxY);
            
            // Move button to random position
            noBtn.style.position = 'fixed';
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';
            noBtn.style.transition = 'left 0.3s, top 0.3s';
        }
        
        // Make floating elements move when clicked
        floatingElements.forEach(element => {
            element.addEventListener('click', function() {
                // Get random position
                const maxX = window.innerWidth - 50;
                const maxY = window.innerHeight - 50;
                
                const randomX = Math.floor(Math.random() * maxX);
                const randomY = Math.floor(Math.random() * maxY);
                
                // Move to new position
                this.style.left = randomX + 'px';
                this.style.top = randomY + 'px';
                this.style.transition = 'left 0.5s, top 0.5s';
                
                // Change color temporarily
                const originalColor = this.style.color;
                if (this.classList.contains('heart-float')) {
                    this.style.color = '#ff3366';
                } else if (this.classList.contains('cat-float')) {
                    this.style.color = '#ff7733';
                } else {
                    this.style.color = '#ff0000';
                }
                
                // Restore color after 0.5s
                setTimeout(() => {
                    this.style.color = originalColor;
                }, 500);
            });
            
            // For mobile touch
            element.addEventListener('touchstart', function(e) {
                e.preventDefault();
                this.click();
            });
        });
        
        // When YES is clicked
        yesBtn.addEventListener('click', function() {
            // Hide buttons
            yesBtn.style.display = 'none';
            noBtn.style.display = 'none';
            
            // Show message
            message.style.display = 'block';
            
            // Make floating elements move faster and change colors
            floatingElements.forEach(element => {
                element.style.animationDuration = '5s';
                element.style.opacity = '1';
                
                // Add celebration colors
                if (element.classList.contains('heart-float')) {
                    element.style.color = '#ff3366';
                } else if (element.classList.contains('cat-float')) {
                    element.style.color = '#ff7733';
                } else {
                    element.style.color = '#ff0000';
                }
            });
            
            // Create celebration effect
            createCelebration();
        });
        
        // Celebration effect
        function createCelebration() {
            const emojis = ['❤️', '🐱', '🎉', '🥰', '💖', '😻'];
            const container = document.querySelector('.container');
            
            for (let i = 0; i < 20; i++) {
                setTimeout(() => {
                    const emoji = document.createElement('div');
                    emoji.textContent = emojis[Math.floor(Math.random() * emojis.length)];
                    emoji.style.position = 'absolute';
                    emoji.style.fontSize = '25px';
                    emoji.style.left = Math.random() * window.innerWidth + 'px';
                    emoji.style.top = '-30px';
                    emoji.style.zIndex = '5';
                    document.body.appendChild(emoji);
                    
                    // Animate falling
                    emoji.animate([
                        { transform: 'translateY(0) rotate(0deg)', opacity: 1 },
                        { transform: `translateY(${window.innerHeight}px) rotate(360deg)`, opacity: 0 }
                    ], {
                        duration: 2000 + Math.random() * 1000,
                        easing: 'cubic-bezier(0.215, 0.610, 0.355, 1)'
                    });
                    
                    // Remove after animation
                    setTimeout(() => {
                        emoji.remove();
                    }, 3000);
                }, i * 100);
            }
        }
        
        // Initialize floating elements with random positions
        window.addEventListener('load', function() {
            floatingElements.forEach(element => {
                const maxX = window.innerWidth - 50;
                const maxY = window.innerHeight - 50;
                
                const randomX = Math.floor(Math.random() * maxX);
                const randomY = Math.floor(Math.random() * maxY);
                
                element.style.left = randomX + 'px';
                element.style.top = randomY + 'px';
                
                // Random animation delay
                const delay = Math.random() * 5;
                element.style.animationDelay = delay + 's';
            });
        });
        
        // Handle window resize
        window.addEventListener('resize', function() {
            // Reset button position
            noBtn.style.position = '';
            noBtn.style.left = '';
            noBtn.style.top = '';
        });
    </script>
</body>
</html>
