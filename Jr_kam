<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>AstroNawak 3000 - Version Fun</title>
    <style>
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
            padding: 0;
        }

        header {
            text-align: center;
            padding: 1em;
            background-color: var(--cosmic-purple);
            font-size: 2em;
            font-weight: bold;
            text-shadow: 2px 2px 5px black;
        }

        .container {
            padding: 2em;
            max-width: 900px;
            margin: auto;
        }

        .sign-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 1em;
            margin: 2em 0;
        }

        .sign-card {
            background: rgba(255, 255, 255, 0.1);
            padding: 1em;
            text-align: center;
            border-radius: 10px;
            cursor: pointer;
            transition: 0.3s;
        }

        .sign-card:hover {
            background: rgba(255, 0, 255, 0.3);
        }

        #predict-btn {
            display: block;
            margin: 2em auto;
            padding: 1em 2em;
            background-color: var(--alien-green);
            color: black;
            border: none;
            font-size: 1.2em;
            cursor: pointer;
            border-radius: 10px;
        }

        #result {
            margin-top: 2em;
            text-align: center;
            font-size: 1.3em;
        }

        #minijeu {
            margin-top: 4em;
            text-align: center;
        }

        #game-zone {
            position: relative;
            height: 300px;
            background: #111;
            border: 2px solid #00ffcc;
            border-radius: 10px;
            margin-top: 1em;
        }

        #ovni {
            position: absolute;
            width: 60px;
            display: none;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <header>AstroNawak 3000</header>

    <div class="container">
        <section id="horoscope">
            <div style="text-align: center;">
                <label for="lang">Langue :</label>
                <select id="lang">
                    <option value="fr">Français</option>
                    <option value="en">English</option>
                    <option value="es">Español</option>
                    <option value="it">Italiano</option>
                </select>
            </div>

            <div class="sign-grid" id="signs-container">
                <!-- Signes générés dynamiquement -->
            </div>

            <input type="hidden" id="sign">
            <button id="predict-btn">🚀 VOIR MA DESTINÉE</button>
            <div id="result"></div>
        </section>

        <hr style="margin: 3em 0; border: 1px dashed #ff00ff;">

        <section id="minijeu">
            <h2>Mini-Jeu : Chasse à l’OVNI</h2>
            <p>Clique sur l’OVNI avant qu’il ne disparaisse !</p>
            <div id="game-zone">
                <img id="ovni" src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f0/UFO_icon.svg/200px-UFO_icon.svg.png"
                     alt="ovni">
            </div>
            <p id="score">Score : 0</p>
        </section>
    </div>

    <script>
        const astroData = {
            signs: [
                { id: "aries", name: "Bélier", dates: "21 mars - 19 avril", emoji: "🐏" },
                { id: "taurus", name: "Taureau", dates: "20 avril - 20 mai", emoji: "🐂" },
                { id: "gemini", name: "Gémeaux", dates: "21 mai - 20 juin", emoji: "👯‍♂️" },
                { id: "cancer", name: "Cancer", dates: "21 juin - 22 juillet", emoji: "🦀" },
                { id: "leo", name: "Lion", dates: "23 juillet - 22 août", emoji: "🦁" },
                { id: "virgo", name: "Vierge", dates: "23 août - 22 septembre", emoji: "🌾" },
                { id: "libra", name: "Balance", dates: "23 septembre - 22 octobre", emoji: "⚖️" },
                { id: "scorpio", name: "Scorpion", dates: "23 octobre - 21 novembre", emoji: "🦂" },
                { id: "sagittarius", name: "Sagittaire", dates: "22 novembre - 21 décembre", emoji: "🏹" },
                { id: "capricorn", name: "Capricorne", dates: "22 décembre - 19 janvier", emoji: "🐐" },
                { id: "aquarius", name: "Verseau", dates: "20 janvier - 18 février", emoji: "🏺" },
                { id: "pisces", name: "Poissons", dates: "19 février - 20 mars", emoji: "🐟" }
            ],
            messages: {
                fr: {
                    aries: "🚀 ALERTE : Ton grille-pain a des vues sur ton conjoint !",
                    taurus: "🐮 TODAY : Une vache va te parler. Ne bois pas son lait.",
                    gemini: "🌀 MULTIPLICITÉ : Attention aux clones aujourd’hui.",
                    cancer: "🦀 Crabes dans le dos ? C’est normal. Ou pas.",
                    leo: "🔥 ROOOAR : Ta journée sera rugissante… ou rugueuse.",
                    virgo: "📚 RANGE TOUT : Même tes idées bizarres.",
                    libra: "⚖️ Tu vas hésiter entre deux pizzas. Choisis la troisième.",
                    scorpio: "🦂 Piquant ! Mais c’est ton charme.",
                    sagittarius: "🏹 Tire au hasard, tu toucheras peut-être Jupiter.",
                    capricorn: "🐐 Tu grimperas haut, sauf si tu dors.",
                    aquarius: "💧 Verses-tu de l’eau ou des vérités ?",
                    pisces: "🐟 Gaffe aux hameçons émotionnels."
                }
            }
        };

        document.addEventListener('DOMContentLoaded', () => {
            const signsContainer = document.getElementById('signs-container');
            astroData.signs.forEach(sign => {
                signsContainer.innerHTML += `
                    <div class="sign-card" data-sign="${sign.id}">
                        <div style="font-size: 2em">${sign.emoji}</div>
                        <h3>${sign.name}</h3>
                        <p>${sign.dates}</p>
                    </div>
                `;
            });

            document.querySelectorAll('.sign-card').forEach(card => {
                card.addEventListener('click', function() {
                    document.querySelectorAll('.sign-card').forEach(c => c.style.background = "rgba(255,255,255,0.1)");
                    this.style.background = "rgba(255, 0, 255, 0.5)";
                    document.getElementById('sign').value = this.getAttribute('data-sign');
                });
            });

            document.getElementById('predict-btn').addEventListener('click', showMessage);
        });

        function showMessage() {
            const lang = document.getElementById('lang').value || "fr";
            const sign = document.getElementById('sign').value;

            if (!sign) {
                alert("Choisis un signe astro d'abord !");
                return;
            }

            const prediction = astroData.messages[lang]?.[sign] || "💥 Les astres sont en grève cosmique.";
            const emoji = getRandomEmoji();

            document.getElementById('result').innerHTML = `
                <h3>Prédiction pour ${document.querySelector(`.sign-card[data-sign="${sign}"] h3`).textContent} :</h3>
                <p>${prediction}</p>
                <div style="font-size: 3em">${emoji}</div>
            `;
        }

        function getRandomEmoji() {
            const emojis = ["👽", "🤡", "🪐", "🍕", "🚀", "🛸"];
            return emojis[Math.floor(Math.random() * emojis.length)];
        }

        // MINI-JEU OVNI
        let score = 0;
        const ovni = document.getElementById("ovni");
        const gameZone = document.getElementById("game-zone");
        const scoreDisplay = document.getElementById("score");

        function moveOvni() {
            const x = Math.random() * (gameZone.clientWidth - 60);
            const y = Math.random() * (gameZone.clientHeight - 60);
            ovni.style.left = x + "px";
            ovni.style.top = y + "px";
            ovni.style.display = "block";

            setTimeout(() => {
                ovni.style.display = "none";
                setTimeout(moveOvni, 1000 + Math.random() * 2000);
            }, 1000);
        }

        ovni.addEventListener("click", () => {
            score++;
            scoreDisplay.textContent = "Score : " + score;
            ovni.style.display = "none";
        });

        setTimeout(moveOvni, 2000);
    </script>
</body>
</html>
