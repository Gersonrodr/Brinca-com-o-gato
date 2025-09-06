            color: #ffcc00;
        }
        
        .btn {
            display: block;
            width: 100%;
            padding: 12px;
            margin-top: 15px;
            background: #ffcc00;
            color: #333;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .btn:hover {
            background: #ffdd44;
            transform: scale(1.05);
        }
        
        /* Estilos para a área de bolhas */
        #bubble-container {
            height: 200px;
            position: relative;
            border: 2px dashed rgba(255, 255, 255, 0.3);
            border-radius: 10px;
            overflow: hidden;
        }
        
        .bubble {
            position: absolute;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.6);
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
            animation: float 8s infinite ease-in-out;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0) translateX(0); }
            25% { transform: translateY(-30px) translateX(20px); }
            50% { transform: translateY(20px) translateX(-30px); }
            75% { transform: translateY(-20px) translateX(30px); }
        }
        
        /* Estilos para o foguete */
        #rocket-container {
            height: 200px;
            position: relative;
            border: 2px dashed rgba(255, 255, 255, 0.3);
            border-radius: 10px;
            overflow: hidden;
        }
        
        .rocket {
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            font-size: 40px;
            transition: all 0.5s;
        }
        
        /* Estilos para os corações */
        #hearts-container {
            height: 200px;
            position: relative;
            border: 2px dashed rgba(255, 255, 255, 0.3);
            border-radius: 10px;
            overflow: hidden;
        }
        
        .heart {
            position: absolute;
            font-size: 24px;
            color: #ff3366;
            animation: fall 5s linear forwards;
        }
        
        @keyframes fall {
            to { transform: translateY(200px) rotate(360deg); opacity: 0; }
        }
        
        /* Estilos para o disco de dança */
        #dance-container {
            height: 200px;
            position: relative;
            border: 2px dashed rgba(255, 255, 255, 0.3);
            border-radius: 10px;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .dancer {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            position: absolute;
            animation: dance 2s infinite alternate;
        }
        
        @keyframes dance {
            0% { transform: translateY(0) rotate(0); }
            100% { transform: translateY(-50px) rotate(360deg); }
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            font-size: 0.9rem;
            opacity: 0.8;
        }
    </style>
</head>
<body>
    <header>
        <h1>Animações Divertidas</h1>
        <p>Clique nos botões para ativar diferentes animações!</p>
    </header>
    
    <div class="container">
        <div class="animation-card">
            <h2>Bolhas Flutuantes</h2>
            <div id="bubble-container"></div>
            <button class="btn" id="add-bubbles">Adicionar Bolhas</button>
        </div>
        
        <div class="animation-card">
            <h2>Foguete Espacial</h2>
            <div id="rocket-container">
                <div class="rocket">🚀</div>
            </div>
            <button class="btn" id="launch-rocket">Lançar Foguete</button>
        </div>
        
        <div class="animation-card">
            <h2>Chuva de Corações</h2>
            <div id="hearts-container"></div>
            <button class="btn" id="make-it-rain">Criar Chuva de Corações</button>
        </div>
        
        <div class="animation-card">
            <h2>Pista de Dança</h2>
            <div id="dance-container"></div>
            <button class="btn" id="add-dancers">Adicionar Dançarinos</button>
        </div>
    </div>
    
    <footer>
        <p>Criado com 💙, HTML, CSS e JavaScript</p>
    </footer>

    <script>
        // Bolhas flutuantes
        document.getElementById('add-bubbles').addEventListener('click', function() {
            const container = document.getElementById('bubble-container');
            const bubble = document.createElement('div');
            bubble.classList.add('bubble');
            
            // Tamanho aleatório
            const size = Math.random() * 50 + 20;
            bubble.style.width = `${size}px`;
            bubble.style.height = `${size}px`;
            
            // Posição aleatória
            const posX = Math.random() * (container.offsetWidth - size);
            const posY = Math.random() * (container.offsetHeight - size);
            bubble.style.left = `${posX}px`;
            bubble.style.top = `${posY}px`;
            
            // Cor aleatória
            const hue = Math.floor(Math.random() * 360);
            bubble.style.background = `hsla(${hue}, 80%, 70%, 0.7)`;
            bubble.style.boxShadow = `0 0 15px hsla(${hue}, 80%, 70%, 0.8)`;
            
            // Atraso aleatório na animação
            bubble.style.animationDelay = `${Math.random() * 2}s`;
            
            container.appendChild(bubble);
            
            // Remover a bolha após um tempo
            setTimeout(() => {
                bubble.remove();
            }, 10000);
        });
        
        // Foguete espacial
        document.getElementById('launch-rocket').addEventListener('click', function() {
            const rocket = document.querySelector('.rocket');
            rocket.style.bottom = '200px';
            rocket.style.transform = 'translateX(-50%) rotate(45deg)';
            
            // Resetar após a animação
            setTimeout(() => {
                rocket.style.bottom = '0';
                rocket.style.transform = 'translateX(-50%) rotate(0)';
            }, 2000);
        });
        
        // Chuva de corações
        document.getElementById('make-it-rain').addEventListener('click', function() {
            const container = document.getElementById('hearts-container');
            const heartCount = 20;
            
            for (let i = 0; i < heartCount; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.innerHTML = '❤️';
                
                // Posição aleatória
                const posX = Math.random() * container.offsetWidth;
                heart.style.left = `${posX}px`;
                
                // Atraso aleatório
                heart.style.animationDelay = `${i * 0.2}s`;
                
                container.appendChild(heart);
                
                // Remover o coração após a animação
                setTimeout(() => {
                    heart.remove();
                }, 5000);
            }
        });
        
        // Pista de dança
        document.getElementById('add-dancers').addEventListener('click', function() {
            const container = document.getElementById('dance-container');
            const dancer = document.createElement('div');
            dancer.classList.add('dancer');
            
            // Cor aleatória
            const hue = Math.floor(Math.random() * 360);
            dancer.style.background = `hsl(${hue}, 80%, 60%)`;
            
            // Posição aleatória
            const posX = Math.random() * container.offsetWidth;
            dancer.style.left = `${posX}px`;
            
            // Atraso aleatório na animação
            dancer.style.animationDelay = `${Math.random() * 2}s`;
            
            container.appendChild(dancer);
            
            // Remover o dançarino após um tempo
            setTimeout(() => {
                dancer.remove();
            }, 5000);
        });
    </script>
</body>
</html>
