<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>AstroNawak 3000</title>
    <style>
        :root {
            --cosmic-purple: #4b0082;
            --neon-pink: #ff00ff;
            --alien-green: #00ffcc;
        }
        
        body {
            background: radial-gradient(circle, #0f0022, #000);
            color: white;
            font-family: 'Comic Sans MS', cursive, sans-serif;
            margin: 0;
            min-height: 100vh;
        }
        
        header {
            background: rgba(0,0,0,0.7);
            padding: 1em;
            border-bottom: 3px dashed var(--neon-pink);
        }
        
        h1 {
            color: var(--alien-green);
            font-size: 4em;
            text-shadow: 0 0 15px var(--neon-pink);
            margin: 0;
            animation: glow 2s infinite alternate;
        }
        
        @keyframes glow {
            from { text-shadow: 0 0 10px var(--alien-green); }
            to { text-shadow: 0 0 20px var(--neon-pink), 0 0 30px var(--alien-green); }
        }
        
        nav {
            display: flex;
            justify-content: center;
            gap: 2em;
            margin: 1em 0;
        }
        
        nav a {
            color: white;
            text-decoration: none;
            font-size: 1.5em;
            padding: 0.5em;
            border-radius: 10px;
            transition: all 0.3s;
        }
        
        nav a:hover {
            background: var(--neon-pink);
            transform: scale(1.1);
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2em;
        }
        
        .section {
            background: rgba(0,0,0,0.5);
            border: 2px solid var(--alien-green);
            border-radius: 20px;
            padding: 2em;
            margin-bottom: 2em;
            box-shadow: 0 0 20px var(--neon-pink);
        }
        
        select, button {
            padding: 1em;
            margin: 1em;
            font-size: 1.2em;
            background: var(--cosmic-purple);
            color: white;
            border: 2px solid var(--alien-green);
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        button:hover {
            background: var(--neon-pink);
            transform: rotate(5deg);
        }
        
        #result {
            font-size: 1.8em;
            line-height: 1.5;
            margin: 1em 0;
            padding: 1em;
            background: rgba(0,0,0,0.7);
            border-radius: 15px;
            border-left: 5px solid var(--neon-pink);
        }
        
        .sign-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1em;
            margin: 2em 0;
        }
        
        .sign-card {
            background: rgba(75, 0, 130, 0.3);
            padding: 1em;
            border-radius: 10px;
            transition: all 0.3s;
            cursor: pointer;
        }
        
        .sign-card:hover {
            background: rgba(255, 0, 255, 0.3);
            transform: translateY(-10px);
        }
        
        .sign-card img {
            width: 80px;
            height: 80px;
            object-fit: contain;
        }
        
        /* Mini-jeu */
        #game-container {
            position: relative;
            height: 300px;
            background: #000;
            border: 3px solid var(--alien-green);
            border-radius: 15px;
            overflow: hidden;
        }
        
        #player {
            position: absolute;
            width: 50px;
            height: 50px;
            background: url('https://i.imgur.com/XYZ123.png') center/contain no-repeat;
            bottom: 10px;
            left: 50px;
        }
        
        .obstacle {
            position: absolute;
            width: 30px;
            height: 30px;
            background: var(--neon-pink);
            bottom: 10px;
        }
        
        /* Footer */
        footer {
            text-align: center;
            padding: 2em;
            background: rgba(0,0,0,0.7);
            margin-top: 2em;
            border-top: 3px dashed var(--alien-green);
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .sign-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            h1 {
                font-size: 2.5em;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1>ASTRO-NAWAK 3000</h1>
            <p style="text-align: center; font-size: 1.5em; color: var(--neon-pink);">
                L'horoscope intergalactique le plus peu fiable de l'univers
            </p>
            
            <nav>
                <a href="#horoscope">Horoscope</a>
                <a href="#game">Mini-Jeu</a>
                <a href="#about">À propos</a>
                <a href="#contact">Contact</a>
            </nav>
        </div>
    </header>

    <div class="container">
        <section id="horoscope" class="section">
            <h2 style="color: var(--alien-green); text-align: center;">Ton Horoscope Quotidien</h2>
            
            <div style="text-align: center;">
                <label for="lang" style="font-size: 1.3em;">Langue :</label>
                <select id="lang">
                    <option value="fr">Français</option>
                    <option value="en">English</option>
                    <option value="es">Español</option>
                    <option value="it">Italiano</option>
                </select>
            </div>
            
            <h3 style="text-align: center; color: var(--neon-pink);">Choisis ton signe :</h3>
            
            <div class="sign-grid">
                <!-- Bélier -->
                <div class="sign-card" onclick="selectSign('aries')">
                    <img src="https://i.imgur.com/ram.png" alt="Bélier">
                    <h3>Bélier</h3>
                    <p>21 mars - 19 avril</p>
                </div>
                
                <!-- Taureau -->
                <div class="sign-card" onclick="selectSign('taurus')">
                    <img src="https://i.imgur.com/bull.png" alt="Taureau">
                    <h3>Taureau</h3>
                    <p>20 avril - 20 mai</p>
                </div>
                
                <!-- Gémeaux -->
                <div class="sign-card" onclick="selectSign('gemini')">
                    <img src="https://i.imgur.com/gemini.png" alt="Gémeaux">
                    <h3>Gémeaux</h3>
                    <p>21 mai - 20 juin</p>
                </div>
                
                <!-- Cancer -->
                <div class="sign-card" onclick="selectSign('cancer')">
                    <img src="https://i.imgur.com/crab.png" alt="Cancer">
                    <h3>Cancer</h3>
                    <p>21 juin - 22 juillet</p>
                </div>
                
                <!-- Lion -->
                <div class="sign-card" onclick="selectSign('leo')">
                    <img src="https://i.imgur.com/lion.png" alt="Lion">
                    <h3>Lion</h3>
                    <p>23 juillet - 22 août</p>
                </div>
                
                <!-- Vierge -->
                <div class="sign-card" onclick="selectSign('virgo')">
                    <img src="https://i.imgur.com/virgo.png" alt="Vierge">
                    <h3>Vierge</h3>
                    <p>23 août - 22 septembre</p>
                </div>
                
                <!-- Balance -->
                <div class="sign-card" onclick="selectSign('libra')">
                    <img src="https://i.imgur.com/libra.png" alt="Balance">
                    <h3>Balance</h3>
                    <p>23 septembre - 22 octobre</p>
                </div>
                
                <!-- Scorpion -->
                <div class="sign-card" onclick="selectSign('scorpio')">
                    <img src="https://i.imgur.com/scorpio.png" alt="Scorpion">
                    <h3>Scorpion</h3>
                    <p>23 octobre - 21 novembre</p>
                </div>
                
                <!-- Sagittaire -->
                <div class="sign-card" onclick="selectSign('sagittarius')">
                    <img src="https://i.imgur.com/archer.png" alt="Sagittaire">
                    <h3>Sagittaire</h3>
                    <p>22 novembre - 21 décembre</p>
                </div>
                
                <!-- Capricorne -->
                <div class="sign-card" onclick="selectSign('capricorn')">
                    <img src="https://i.imgur.com/goat.png" alt="Capricorne">
                    <h3>Capricorne</h3>
                    <p>22 décembre - 19 janvier</p>
                </div>
                
                <!-- Verseau -->
                <div class="sign-card" onclick="selectSign('aquarius')">
                    <img src="https://i.imgur.com/water.png" alt="Verseau">
                    <h3>Verseau</h3>
                    <p>20 janvier - 18 février</p>
                </div>
                
                <!-- Poissons -->
                <div class="sign-card" onclick="selectSign('pisces')">
                    <img src="https://i.imgur.com/fish.png" alt="Poissons">
                    <h3>Poissons</h3>
                    <p>19 février - 20 mars</p>
                </div>
            </div>
            
            <div style="text-align: center; margin-top: 2em;">
                <button onclick="showMessage()" style="font-size: 1.5em; padding: 0.8em 2em;">
                    🚀 VOIR MA DESTINÉE (ou pas)
                </button>
            </div>
            
            <div id="result"></div>
        </section>
        
        <section id="game" class="section">
            <h2 style="color: var(--alien-green); text-align: center;">Mini-Jeu : Évite les Astéroïdes Nawak</h2>
            
            <div id="game-container">
                <div id="player"></div>
            </div>
            
            <div style="text-align: center; margin-top: 1em;">
                <button onclick="startGame()" style="background: var(--neon-pink);">
                    COMMENCER LE JEU
                </button>
                <p id="score" style="font-size: 1.5em; color: var(--alien-green);">Score: 0</p>
            </div>
        </section>
        
        <section id="about" class="section">
            <h2 style="color: var(--alien-green); text-align: center;">À propos d'AstroNawak</h2>
            <p style="font-size: 1.3em; line-height: 1.6;">
                AstroNawak est le premier site d'horoscope créé par des extraterrestres sous l'influence de café cosmique. 
                Nos prédictions sont 100% aléatoires, 0% fiables, et 200% divertissantes.
                <br><br>
                <span style="color: var(--neon-pink);">⚠️ Attention :</span> Ne prenez aucune décision importante basée sur nos conseils. 
                Sauf si c'est pour choisir la couleur de vos chaussettes.
            </p>
        </section>
        
        <section id="contact" class="section">
            <h2 style="color: var(--alien-green); text-align: center;">Contacte nos Astro-Clowns</h2>
            
            <div style="text-align: center; font-size: 1.3em;">
                <p>📧 Email : <a href="mailto:clowns@astronawak.com" style="color: var(--neon-pink);">clowns@astronawak.com</a></p>
                <p>📱 Twitter : <a href="https://twitter.com/astronawak" style="color: var(--neon-pink);">@AstroNawak</a></p>
                <p>👽 Discord : Rejoins notre serveur "Astro-Clowns Anonymes"</p>
            </div>
        </section>
    </div>
    
    <footer>
        <p style="font-size: 1.2em;">
            © 2023 AstroNawak 3000 - Tous droits inexistants
            <br>
            <span style="font-size: 0.8em; color: var(--neon-pink);">
                [Ce site ne contient aucune vérité astronomique. Ou peut-être que si. Qui sait ?]
            </span>
        </p>
    </footer>

    <script>
        // Messages d'horoscope pour tous les signes
        const messages = {
            fr: {
                aries: "🚀 ALERTE BÉLIER : Ton grille-pain va déclarer son indépendance aujourd'hui. Cache le beurre !",
                taurus: "🐮 TAUREAU COSMIQUE : Les vaches roses te regardent. Ne leur fais pas confiance.",
                gemini: "👥 GÉMEAUX ALERTE : Ton clone a volé tes chaussettes. Vérifie ton tiroir.",
                cancer: "🦀 CANCER SPECIAL : La Lune te conseille de manger plus de cookies. Écoute-la.",
                leo: "🦁 LION ROYAL : Tu vas rencontrer un chat aujourd'hui. Il te dominera.",
                virgo: "🌾 VIERGE PRÉCISE : Range ton bureau. Non, vraiment, c'est urgent.",
                libra: "⚖️ BALANCE DÉSÉQUILIBRÉE : Choisis entre pizza et tacos. Tu ne peux pas avoir les deux.",
                scorpio: "🦂 SCORPION MYSTÉRIEUX : Quelqu'un ment. Probablement toi.",
                sagittarius: "🏹 SAGITTAIRE AVENTURIER : Pars en voyage. Ton canapé te retient prisonnier.",
                capricorn: "🐐 CAPRICORNE AMBITIEUX : Fais une sieste. Ton CV peut attendre.",
                aquarius: "💧 VERSEAU ÉTRANGE : Invente une nouvelle danse. Le monde en a besoin.",
                pisces: "🐟 POISSONS RÊVEURS : Reste dans ton bocal aujourd'hui. Le monde est trop bizarre."
            },
            en: {
                aries: "🚀 ARIES ALERT: Your toaster will unionize today. Hide the bread!",
                taurus: "🐮 COSMIC COW: Pink cows are judging you. Don't make eye contact.",
                gemini: "👥 GEMINI WARNING: Your clone stole your Netflix password. Change it.",
                cancer: "🦀 CANCER MOOD: The Moon says eat ice cream for dinner. Obey.",
                leo: "🦁 LEO ENERGY: A cat will adopt you today. Resistance is futile.",
                virgo: "🌾 VIRGO VIBES: Alphabetize your spice rack. Now.",
                libra: "⚖️ LIBRA PROBLEMS: Can't decide? Flip a coin. Then ignore it.",
                scorpio: "🦂 SCORPIO SHADE: Someone is lying. (It's definitely you).",
                sagittarius: "🏹 SAGITTARIUS QUEST: Book a one-way ticket to anywhere.",
                capricorn: "🐐 CAPRICORN HUSTLE: Take a nap. Your emails can wait.",
                aquarius: "💧 AQUARIUS WEIRD: Start a cult about llamas. You know you want to.",
                pisces: "🐟 PISCES DREAM: Stay in bed. Reality is overrated."
            },
            es: {
                aries: "🚀 ARIES ALERTA: Tu tostadora se declarará en huelga. Esconde el pan.",
                taurus: "🐮 TAURO CÓSMICO: Las vacas rosas te están vigilando. Corre.",
                gemini: "👥 GÉMINIS AVISO: Tu clon robó tu contraseña de WiFi. Cámbiala.",
                cancer: "🦀 CÁNCER LUNA: La Luna dice que comas helado. Obedece.",
                leo: "🦁 LEO REY: Un gato te adoptará hoy. No puedes negarte.",
                virgo: "🌾 VIRGO ORDEN: Organiza tu armario por color. Ahora.",
                libra: "⚖️ LIBRA DILEMA: No puedes decidir? Usa una moneda. Luego ignórala.",
                scorpio: "🦂 ESCORPIO SECRETO: Alguien miente. (Probablemente tú).",
                sagittarius: "🏹 SAGITARIO AVENTURA: Compra un boleto a ningún lugar.",
                capricorn: "🐐 CAPRICORNIO TRABAJO: Duerme una siesta. Tus jefes pueden esperar.",
                aquarius: "💧 ACUARIO RARO: Inventa un baile nuevo. Hazlo viral.",
                pisces: "🐟 PISCIS SUEÑO: Quédate en casa. El mundo da miedo."
            },
            it: {
                aries: "🚀 ARIETE ALLERTA: Il tuo tostapane si ribellerà oggi. Nascondi il pane!",
                taurus: "🐮 TORO COSMICO: Le mucche rosa ti stanno giudicando. Scappa.",
                gemini: "👥 GEMELLI AVVISO: Il tuo clone ha rubato la tua password. Cambiala.",
                cancer: "🦀 CANCRO LUNA: La Luna dice di mangiare gelato. Ascoltala.",
                leo: "🦁 LEONE RE: Un gatto ti adotterà oggi. Non resistere.",
                virgo: "🌾 VERGINE ORDINE: Organizza i tuoi libri per colore. Subito.",
                libra: "⚖️ BILANCIA PROBLEMI: Non riesci a decidere? Lancia una moneta. Poi ignorala.",
                scorpio: "🦂 SCORPIONE MISTERO: Qualcuno mente. (Forse sei tu).",
                sagittarius: "🏹 SAGITTARIO AVVENTURA: Parti per un viaggio senza ritorno.",
                capricorn: "🐐 CAPRICORNO LAVORO: Fai un pisolino. Le email possono aspettare.",
                aquarius: "💧 ACQUARIO STRANO: Inventa una nuova religione. Fallo ora.",
                pisces: "🐟 PESCI SOGNO: Resta a letto. La realtà è sopravvalutata."
            }
        };

        // Mini-jeu
        let gameInterval;
        let score = 0;
        let gameStarted = false;
        
        function selectSign(sign) {
            document.getElementById("sign").value = sign;
            highlightSignCard(sign);
        }
        
        function highlightSignCard(sign) {
            // Retire la mise en évidence précédente
            document.querySelectorAll(".sign-card").forEach(card => {
                card.style.background = "rgba(75, 0, 130, 0.3)";
            });
            
            // Met en évidence la carte sélectionnée
            const selectedCard = document.querySelector(`.sign-card[onclick="selectSign('${sign}')"]`);
            if (selectedCard) {
                selectedCard.style.background = "rgba(255, 0, 255, 0.5)";
            }
        }
        
        function showMessage() {
            const lang = document.getElementById("lang").value;
            const sign = document.getElementById("sign").value;
            const message = messages[lang][sign] || "💥 LES ASTRES SONT EN PANNE. REESSAYE PLUS TARD.";
            
            document.getElementById("result").innerHTML = `
                <h3 style="color: var(--neon-pink);">Prédiction pour ${document.querySelector(`.sign-card[onclick="selectSign('${sign}')"] h3`).textContent} :</h3>
                <p>${message}</p>
                <div style="font-size: 3em; margin-top: 0.5em;">${getRandomEmoji()}</div>
                <p style="font-size: 0.8em; color: var(--alien-green);">Certifié 0% précis par l'Académie d'Astronawakologie</p>
            `;
            
            // Effet spécial
            document.body.style.animation = "none";
            setTimeout(() => {
                document.body.style.animation = "pulse 0.5s";
            }, 10);
        }
        
        function getRandomEmoji() {
            const emojis = ["👽", "🤡", "👾", "🐮", "🍕", "🚀", "🌈", "🍔", "🦄", "🍩", "🎪", "🪐"];
            return emojis[Math.floor(Math.random() * emojis.length)];
        }
        
        // Mini-jeu
        function startGame() {
            if (gameStarted) return;
            
            gameStarted = true;
            score = 0;
            document.getElementById("score").textContent = `Score: ${score}`;
            
            const gameContainer = document.getElementById("game-container");
            const player = document.getElementById("player");
            player.style.left = "50px";
            
            // Crée des obstacles
            gameInterval = setInterval(() => {
                const obstacle = document.createElement("div");
                obstacle.className = "obstacle";
                obstacle.style.left = `${gameContainer.offsetWidth}px`;
                gameContainer.appendChild(obstacle);
                
                let obstaclePosition = parseInt(obstacle.style.left);
                const moveObstacle = setInterval(() => {
                    obstaclePosition -= 5;
                    obstacle.style.left = `${obstaclePosition}px`;
                    
                    // Collision
                    if (
                        obstaclePosition < parseInt(player.style.left) + 50 &&
                        obstaclePosition + 30 > parseInt(player.style.left) &&
                        parseInt(obstacle.style.bottom) < parseInt(player.style.bottom) + 50
                    ) {
                        clearInterval(moveObstacle);
                        gameOver();
                    }
                    
                    // Sortie de l'écran
                    if (obstaclePosition < -30) {
                        clearInterval(moveObstacle);
                        obstacle.remove();
                        score++;
                        document.getElementById("score").textContent = `Score: ${score}`;
                    }
                }, 20);
            }, 1500);
            
            // Contrôles
            document.addEventListener("keydown", (e) => {
                if (e.code === "Space") {
                    jump();
                }
            });
        }
        
        function jump() {
            const player = document.getElementById("player");
            let position = 0;
            let jumpUp = setInterval(() => {
                position += 5;
                player.style.bottom = `${10 + position}px`;
                
                if (position >= 100) {
                    clearInterval(jumpUp);
                    let jumpDown = setInterval(() => {
                        position -= 5;
                        player.style.bottom = `${10 + position}px`;
                        
                        if (position <= 0) {
                            clearInterval(jumpDown);
                        }
                    }, 20);
                }
            }, 20);
        }
        
        function gameOver() {
            clearInterval(gameInterval);
            gameStarted = false;
            
            const gameContainer = document.getElementById("game-container");
            gameContainer.innerHTML = `
                <div style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); text-align: center;">
                    <h2 style="color: var(--neon-pink);">GAME OVER</h2>
                    <p style="font-size: 1.5em;">Score final: ${score}</p>
                    <p style="color: var(--alien-green);">Les astres ont décidé que tu avais perdu</p>
                    <button onclick="startGame()" style="margin-top: 1em;">Rejouer</button>
                </div>
            `;
        }
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>AstroNawak 3000 - Version Stabilisée</title>
    <style>
        /* Styles inchangés mais optimisés */
        :root {
            --cosmic-purple: #4b0082;
            --neon-pink: #ff00ff;
            --alien-green: #00ffcc;
        }
        
        body {
            background: radial-gradient(circle, #0f0022, #000);
            font-family: 'Comic Sans MS', cursive;
            color: white;
            margin: 0;
            min-height: 100vh;
        }
        
        /* ... (conserver le reste des styles existants) ... */
    </style>
</head>
<body>
    <!-- Structure HTML inchangée -->
    <header>...</header>

    <div class="container">
        <section id="horoscope" class="section">
            <!-- Interface de sélection -->
            <div style="text-align: center;">
                <label for="lang">Langue :</label>
                <select id="lang">
                    <option value="fr">Français</option>
                    <option value="en">English</option>
                    <option value="es">Español</option>
                    <option value="it">Italiano</option>
                </select>
            </div>

            <!-- Grille des signes revisitée -->
            <div class="sign-grid" id="signs-container">
                <!-- Les signes seront générés dynamiquement -->
            </div>

            <button id="predict-btn">🚀 VOIR MA DESTINÉE</button>
            <div id="result"></div>
        </section>

        <!-- ... autres sections ... -->
    </div>

    <script>
        // Nouvelle structure de données
        const astroData = {
            signs: [
                { id: "aries", name: "Bélier", dates: "21 mars - 19 avril", emoji: "🐏" },
                { id: "taurus", name: "Taureau", dates: "20 avril - 20 mai", emoji: "🐂" },
                // ... tous les autres signes ...
            ],
            
            messages: {
                fr: {
                    aries: "🚀 ALERTE : Ton grille-pain a des vues sur ton conjoint !",
                    taurus: "🐮 TODAY : Une vache va te parler. Ne bois pas son lait.",
                    // ... autres messages ...
                },
                en: {...},
                es: {...},
                it: {...}
            }
        };

        // Initialisation
        document.addEventListener('DOMContentLoaded', () => {
            // Génère les cartes de signes
            const signsContainer = document.getElementById('signs-container');
            astroData.signs.forEach(sign => {
                signsContainer.innerHTML += `
                    <div class="sign-card" data-sign="${sign.id}">
                        <span style="font-size: 2em">${sign.emoji}</span>
                        <h3>${sign.name}</h3>
                        <p>${sign.dates}</p>
                    </div>
                `;
            });

            // Gestion des événements
            document.querySelectorAll('.sign-card').forEach(card => {
                card.addEventListener('click', function() {
                    const signId = this.getAttribute('data-sign');
                    selectSign(signId);
                });
            });

            document.getElementById('predict-btn').addEventListener('click', showMessage);
        });

        // Fonctions principales
        function selectSign(signId) {
            // Désélectionne toutes les cartes
            document.querySelectorAll('.sign-card').forEach(card => {
                card.style.background = "rgba(75, 0, 130, 0.3)";
            });
            
            // Sélectionne la carte cliquée
            const selectedCard = document.querySelector(`.sign-card[data-sign="${signId}"]`);
            if (selectedCard) {
                selectedCard.style.background = "rgba(255, 0, 255, 0.5)";
                // Stocke la sélection
                document.getElementById('sign').value = signId;
            }
        }

        function showMessage() {
            const lang = document.getElementById('lang').value;
            const sign = document.getElementById('sign').value;
            
            if (!sign) {
                alert("Choisis un signe astro d'abord !");
                return;
            }

            const prediction = astroData.messages[lang]?.[sign] 
                            || "💥 ERREUR : Les astres sont en pause café";
            
            document.getElementById('result').innerHTML = `
                <h3>Prédiction pour ${document.querySelector(`.sign-card[data-sign="${sign}"] h3`).textContent} :</h3>
                <p>${prediction}</p>
                <div style="font-size: 3em">${getRandomEmoji()}</div>
            `;
        }

        function getRandomEmoji() {
            const emojis = ["👽", "🤡", "🪐", "🍕", "🚀"];
            return emojis[Math.floor(Math.random() * emojis.length)];
        }
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>AstroNawak Fix</title>
    <style>
        body {
            background: #1a0033;
            color: white;
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 2em;
        }
        button, select {
            padding: 10px;
            margin: 10px;
            font-size: 16px;
        }
        #result {
            margin-top: 20px;
            font-size: 24px;
            color: #00ffcc;
        }
    </style>
</head>
<body>
    <h1>AstroNawak</h1>
    
    <select id="lang">
        <option value="fr">Français</option>
        <option value="en">English</option>
    </select>
    
    <select id="sign">
        <option value="aries">Bélier</option>
        <option value="taurus">Taureau</option>
    </select>
    
    <button onclick="generateHoroscope()">Générer</button>
    
    <div id="result"></div>

    <script>
        const predictions = {
            fr: {
                aries: "🚀 Ton grille-pain va te parler aujourd'hui !",
                taurus: "🐮 Une vache rose apparaîtra dans ton salon."
            },
            en: {
                aries: "🚀 Your toaster will write you a poem!",
                taurus: "🐮 A pink cow will ask you to dance."
            }
        };

        function generateHoroscope() {
            const lang = document.getElementById("lang").value;
            const sign = document.getElementById("sign").value;
            document.getElementById("result").textContent = predictions[lang][sign];
        }
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Astronawak - Horoscope</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }

    header, footer {
      background-color: #333;
      color: white;
      text-align: center;
      padding: 1em 0;
    }

    nav ul {
      list-style: none;
      padding: 0;
    }

    nav li {
      display: inline;
      margin: 0 1em;
    }

    nav a {
      color: white;
      text-decoration: none;
    }

    main {
      padding: 2em;
    }

    @media (max-width: 600px) {
      nav li {
        display: block;
        margin: 0.5em 0;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>Astronawak</h1>
    <nav>
      <ul>
        <li><a href="#horoscope">Horoscope</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section id="horoscope">
      <h2>Horoscope du jour</h2>
      <div id="horoscope-content">
        <!-- Le contenu de l'horoscope sera inséré ici -->
      </div>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 Astronawak</p>
  </footer>

  <script>
    document.addEventListener('DOMContentLoaded', () => {
      const horoscopeContent = document.getElementById('horoscope-content');

      // Exemple de données d'horoscope (à personnaliser ou relier à une API)
      const horoscope = {
        signe: 'Bélier',
        message: 'Aujourd\'hui est une journée propice aux nouvelles rencontres.'
      };

      horoscopeContent.innerHTML = `
        <h3>${horoscope.signe}</h3>
        <p>${horoscope.message}</p>
      `;
    });
  </script>
</body>
</html>
