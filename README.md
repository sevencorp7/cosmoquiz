
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Космическая стройка | Квиз СТФ</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            min-height: 100vh;
            background: radial-gradient(ellipse at center, #0a0a2a 0%, #030318 100%);
            font-family: 'Segoe UI', 'Poppins', 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            position: relative;
            overflow-x: hidden;
            color: white;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                radial-gradient(2px 2px at 20px 30px, #fff, rgba(0,0,0,0)),
                radial-gradient(2px 2px at 40px 70px, #fff, rgba(0,0,0,0)),
                radial-gradient(1px 1px at 100px 200px, #fff, rgba(0,0,0,0)),
                radial-gradient(3px 3px at 300px 150px, #fff, rgba(0,0,0,0)),
                radial-gradient(2px 2px at 500px 400px, #fff, rgba(0,0,0,0)),
                radial-gradient(1px 1px at 700px 100px, #fff, rgba(0,0,0,0)),
                radial-gradient(2px 2px at 900px 500px, #fff, rgba(0,0,0,0)),
                radial-gradient(2px 2px at 150px 800px, #fff, rgba(0,0,0,0)),
                radial-gradient(3px 3px at 600px 900px, #fff, rgba(0,0,0,0));
            background-repeat: no-repeat;
            background-size: 200px 200px;
            animation: starsMove 30s linear infinite;
            pointer-events: none;
            opacity: 0.8;
        }

        @keyframes starsMove {
            from { transform: translateY(0); }
            to { transform: translateY(-300px); }
        }

        .game-container {
            width: 100%;
            max-width: 700px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        .screen {
            display: none;
            animation: fadeIn 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        .active-screen {
            display: block;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: scale(0.9) translateY(20px);
            }
            to {
                opacity: 1;
                transform: scale(1) translateY(0);
            }
        }

        .card {
            background: rgba(10, 10, 40, 0.85);
            backdrop-filter: blur(15px);
            border-radius: 40px;
            padding: 30px 25px;
            border: 2px solid rgba(0, 255, 255, 0.3);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5), 0 0 20px rgba(0, 255, 255, 0.2);
            transition: all 0.3s ease;
        }

        .rocket-icon {
            font-size: 60px;
            text-align: center;
            animation: rocketFloat 3s ease-in-out infinite;
            filter: drop-shadow(0 0 10px rgba(0, 255, 255, 0.5));
        }

        @keyframes rocketFloat {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-10px) rotate(5deg); }
        }

        h1 {
            text-align: center;
            font-size: 2rem;
            margin: 15px 0 10px;
            color: white;
            text-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
        }

        .subtitle {
            text-align: center;
            color: #ccc;
            margin-bottom: 30px;
            font-size: 1rem;
        }

        .slogan {
            text-align: center;
            font-size: 1rem;
            color: #ffd600;
            margin: 15px 0;
            padding: 10px;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            font-weight: bold;
            letter-spacing: 1px;
        }

        .input-group {
            margin: 20px 0;
        }

        label {
            display: block;
            color: #00ffff;
            margin-bottom: 8px;
            font-weight: bold;
        }

        input {
            width: 100%;
            padding: 15px;
            border-radius: 25px;
            border: 2px solid #00ffff;
            background: rgba(0, 0, 0, 0.5);
            color: white;
            font-size: 1.1rem;
            transition: all 0.3s;
        }

        input:focus {
            outline: none;
            box-shadow: 0 0 15px #00ffff;
            transform: scale(1.02);
        }

        .btn {
            width: 100%;
            padding: 16px;
            margin: 12px 0;
            border: none;
            border-radius: 30px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            background: linear-gradient(135deg, #00aa88, #00ffcc);
            color: #0a0a2a;
            box-shadow: 0 5px 15px rgba(0, 255, 255, 0.3);
        }

        .btn:hover, .btn:active {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0, 255, 255, 0.5);
        }

        .btn-telegram {
            background: linear-gradient(135deg, #0088cc, #00aaff);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .btn-screenshot {
            background: linear-gradient(135deg, #ff6600, #ffaa00);
            color: #0a0a2a;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin: 25px 0;
        }

        .option {
            background: rgba(255, 255, 255, 0.08);
            border: 2px solid rgba(0, 255, 255, 0.3);
            border-radius: 20px;
            padding: 18px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 15px;
            font-size: 1rem;
            position: relative;
            overflow: hidden;
            color: white;
        }

        .option::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }

        .option:hover::before {
            left: 100%;
        }

        .option:hover {
            transform: translateX(8px);
            border-color: #00ffff;
            background: rgba(0, 255, 255, 0.15);
        }

        .option.selected {
            background: rgba(0, 255, 255, 0.3);
            border-color: #00ffcc;
            transform: scale(1.02);
        }

        .option.correct {
            background: rgba(0, 255, 0, 0.3);
            border-color: #00ff00;
            animation: correctPulse 0.5s;
        }

        .option.incorrect {
            background: rgba(255, 0, 0, 0.3);
            border-color: #ff0000;
            animation: shake 0.5s;
        }

        @keyframes correctPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); box-shadow: 0 0 20px #00ff00; }
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }

        .letter {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #ffaa00, #ff6600);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.2rem;
            color: #0a0a2a;
        }

        .progress-container {
            margin: 20px 0;
        }

        .progress-bar {
            height: 10px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #00ffcc, #00aaff);
            border-radius: 10px;
            width: 0%;
            transition: width 0.5s ease;
            box-shadow: 0 0 10px #00ffcc;
        }

        .question-counter {
            text-align: center;
            margin-top: 10px;
            font-size: 0.9rem;
            color: #ccc;
        }

        .feedback {
            text-align: center;
            padding: 15px;
            border-radius: 20px;
            margin: 20px 0;
            animation: slideIn 0.4s;
            font-weight: bold;
            color: white;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .result-score {
            font-size: 5rem;
            text-align: center;
            font-weight: bold;
            color: #00ffcc;
            margin: 20px 0;
            text-shadow: 0 0 20px #00ffcc;
        }

        .rank-card {
            background: linear-gradient(135deg, rgba(0, 255, 255, 0.2), rgba(255, 0, 255, 0.2));
            border-radius: 30px;
            padding: 20px;
            text-align: center;
            margin: 20px 0;
            border: 1px solid #00ffff;
        }

        .rank-title {
            font-size: 1.8rem;
            font-weight: bold;
            color: #ffaa00;
        }

        .astronaut {
            text-align: center;
            font-size: 80px;
            animation: astronautFloat 2s ease-in-out infinite;
            margin: 20px 0;
        }

        @keyframes astronautFloat {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-15px) rotate(5deg); }
        }

        .results-table {
            width: 100%;
            margin: 20px 0;
            border-collapse: collapse;
            color: white;
        }

        .results-table td {
            padding: 12px;
            border-bottom: 1px solid rgba(0, 255, 255, 0.2);
        }

        .results-table td:first-child {
            font-weight: bold;
            color: #00ffff;
        }

        .cosmonautics-card {
            background: radial-gradient(ellipse at 30% 40%, #0a0a4a, #010118);
            border-radius: 20px;
            padding: 18px;
            margin: 20px 0;
            text-align: center;
            border: 2px solid #00ffcc;
            box-shadow: 0 0 20px rgba(0, 255, 204, 0.3);
            animation: glowPulse 3s infinite;
        }

        @keyframes glowPulse {
            0%, 100% { box-shadow: 0 0 10px rgba(0, 255, 204, 0.3); border-color: #00ffcc; }
            50% { box-shadow: 0 0 30px rgba(0, 255, 204, 0.6); border-color: #00ffff; }
        }

        .cosmonautics-title {
            font-size: 24px;
            margin-bottom: 8px;
            background: linear-gradient(135deg, #00ffcc, #ffaa00);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-weight: bold;
        }

        .screenshot-container {
            position: fixed;
            left: -9999px;
            top: -9999px;
            width: 800px;
            background: radial-gradient(ellipse at center, #0a0a2a 0%, #030318 100%);
            border-radius: 30px;
            padding: 30px;
            font-family: 'Segoe UI', 'Arial', sans-serif;
            color: white;
            border: 2px solid #00ffcc;
        }

        @media (max-width: 500px) {
            .card {
                padding: 20px;
            }
            h1 {
                font-size: 1.6rem;
            }
            .option {
                padding: 14px;
                font-size: 0.9rem;
            }
            .result-score {
                font-size: 3.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="game-container">
        <div id="welcome-screen" class="screen active-screen">
            <div class="card">
                <div class="rocket-icon">🚀</div>
                <h1>КОСМИЧЕСКАЯ СТРОЙКА</h1>
                <div class="slogan">🌟 СТФ строит будущее — даже в космосе! 🌟</div>
                <p class="subtitle">20 вопросов о космическом строительстве с юмором!</p>
                
                <div class="astronaut">👨‍🚀</div>
                
                <div class="input-group">
                    <label>👤 Введи своё имя:</label>
                    <input type="text" id="player-name" placeholder="Например: Юрий Гагарин" maxlength="25">
                </div>
                
                <button class="btn" id="start-btn">🚀 СТАРТ МИССИИ</button>
                
                <p class="subtitle" style="margin-top: 20px; font-size: 0.85rem;">
                    🌌 20 вопросов • 🏗️ Космическая стройка • 🎓 СТФ
                </p>
            </div>
        </div>

        <div id="game-screen" class="screen">
            <div class="card">
                <div class="slogan" style="font-size: 0.8rem; padding: 5px;">🌟 СТФ строит будущее — даже в космосе! 🌟</div>
                
                <div class="progress-container">
                    <div class="progress-bar">
                        <div class="progress-fill" id="progress-fill"></div>
                    </div>
                    <div class="question-counter">
                        Вопрос <span id="current-q">1</span> из <span id="total-q">20</span>
                    </div>
                </div>

                <div id="question-icon" style="font-size: 50px; text-align: center; margin: 15px 0;">🏗️</div>
                <h2 id="question-text" style="font-size: 1.2rem; text-align: center; margin-bottom: 20px; color: white;">
                    Загрузка вопроса...
                </h2>

                <div class="options" id="options-container"></div>

                <div id="feedback" class="feedback" style="display: none;"></div>

                <button class="btn" id="next-btn" style="display: none;">▶ СЛЕДУЮЩИЙ ВОПРОС</button>
            </div>
        </div>

        <div id="result-screen" class="screen">
            <div class="card">
                <div class="astronaut">🏆</div>
                <h1>ПОЗДРАВЛЯЕМ, <span id="winner-name">Игрок</span>!</h1>
                <div class="slogan">🌟 СТФ строит будущее — даже в космосе! 🌟</div>
                
                <div class="result-score" id="final-score">0</div>
                
                <div class="rank-card">
                    <div>🎖️ Твоё звание 🎖️</div>
                    <div class="rank-title" id="rank-title">КОСМО-ПОДСОБНИК</div>
                </div>

                <table class="results-table">
                    <tr><td>👨‍🚀 Космонавт:</td><td id="result-name">-</td></tr>
                    <tr><td>📊 Набрано очков:</td><td id="result-score">0</td></tr>
                    <tr><td>🏆 Получено звание:</td><td id="result-rank">-</td></tr>
                    <tr><td>📅 Дата миссии:</td><td id="result-date">-</td></tr>
                </table>

                <div class="cosmonautics-card">
                    <div class="cosmonautics-title">🚀 С ДНЁМ КОСМОНАВТИКИ! 🚀</div>
                    <div style="font-size: 14px; opacity: 0.95; margin-top: 8px;">
                        12 апреля — день, когда человек покорил космос!<br>
                        Желаем новых открытий и космических высот! 🌟
                    </div>
                </div>

                <button class="btn btn-screenshot" id="screenshot-btn">
                    📸 Сделать скриншот с результатом
                </button>

                <a href="https://t.me/+TW9deUkPFpEzMWYy" target="_blank" class="btn btn-telegram" style="text-decoration: none;">
                    <span>📱</span> Присоединиться к Telegram-каналу СТФ
                </a>
            </div>
        </div>
    </div>

    <div id="screenshot-template" class="screenshot-container">
        <div style="text-align: center;">
            <div style="font-size: 50px; margin-bottom: 15px;">🚀</div>
            <h1 style="font-size: 36px; color: #00ffcc; margin-bottom: 10px;">КОСМИЧЕСКАЯ СТРОЙКА</h1>
            <div style="font-size: 16px; color: #ffd600; margin-bottom: 20px;">🌟 СТФ строит будущее — даже в космосе! 🌟</div>
            
            <div style="font-size: 28px; margin: 20px 0;">Поздравляем, <span id="screenshot-name">Игрок</span>!</div>
            
            <div style="font-size: 64px; font-weight: bold; color: #00ffcc; margin: 20px 0;">
                <span id="screenshot-score">0</span>
            </div>
            
            <div style="background: linear-gradient(135deg, rgba(0,255,204,0.2), rgba(255,0,255,0.2)); border-radius: 20px; padding: 15px; margin: 20px 0;">
                <div style="font-size: 24px; font-weight: bold; color: #ffaa00;" id="screenshot-rank">КОСМО-ПОДСОБНИК</div>
            </div>
            
            <div style="background: rgba(0,255,204,0.1); border-radius: 15px; padding: 15px; margin: 20px 0; text-align: left;">
                <div><strong>👨‍🚀 Космонавт:</strong> <span id="screenshot-player-name"></span></div>
                <div style="margin-top: 8px;"><strong>📊 Набрано очков:</strong> <span id="screenshot-points"></span></div>
                <div style="margin-top: 8px;"><strong>🏆 Получено звание:</strong> <span id="screenshot-player-rank"></span></div>
                <div style="margin-top: 8px;"><strong>📅 Дата миссии:</strong> <span id="screenshot-date"></span></div>
            </div>
            
            <div style="margin-top: 20px; font-size: 14px; opacity: 0.8;">
                🚀 С Днём космонавтики! 🚀
            </div>
        </div>
    </div>

    <script>
        const questions = [
            { text: "Какой «строительный материал» использовали первые советские инженеры для теплоизоляции ракет, чтобы сэкономить на дорогих покрытиях?", options: [
                { letter: "А", text: "Вата", score: 0 }, { letter: "Б", text: "Войлок", score: 0 },
                { letter: "В", text: "Старые валенки", score: 25, correct: true }, { letter: "Г", text: "Пух из подушек", score: 0 }
            ], explanation: "✨ Действительно применяли войлочные материалы, в т.ч. переработанные валенки! ✨", icon: "🧦" },
            { text: "Представьте, что вы проектируете фундамент для базы на Луне. Что будет главной проблемой?", options: [
                { letter: "А", text: "Отсутствие грунта", score: 0 }, { letter: "Б", text: "Слишком много кратеров", score: 0 },
                { letter: "В", text: "Гравитация в 6 раз меньше земной", score: 25, correct: true }, { letter: "Г", text: "Соседи-инопланетяне против стройки", score: 0 }
            ], explanation: "🌕 Гравитация на Луне в 6 раз слабее, это меняет всё строительство!", icon: "🌙" },
            { text: "Какой «космический инструмент» был у Гагарина в кабине «Востока» на случай нештатной ситуации?", options: [
                { letter: "А", text: "Отвёртка", score: 0 }, { letter: "Б", text: "Молоток", score: 0 },
                { letter: "В", text: "Специальный ключ для вскрытия панели", score: 25, correct: true }, { letter: "Г", text: "Ничего — всё было запаяно намертво", score: 0 }
            ], explanation: "🔑 Специальный ключ был на случай, если бы автоматика отказала!", icon: "🔧" },
            { text: "Почему на МКС нет привычных для стройки кранов?", options: [
                { letter: "А", text: "Они слишком тяжёлые", score: 0 }, { letter: "Б", text: "В невесомости любой предмет становится «краном»", score: 25, correct: true },
                { letter: "В", text: "Всё доставляют роботами", score: 0 }, { letter: "Г", text: "Запретил комитет по охране невесомости", score: 0 }
            ], explanation: "🏗️ В невесомости даже космонавт может передвинуть тяжёлый груз!", icon: "🏗️" },
            { text: "Какой материал используют для обшивки космических кораблей, чтобы защитить их от перегрева при входе в атмосферу?", options: [
                { letter: "А", text: "Оцинкованная сталь", score: 0 }, { letter: "Б", text: "Термостойкие керамические плитки", score: 25, correct: true },
                { letter: "В", text: "Краска «космо-термо»", score: 0 }, { letter: "Г", text: "Фольгированный утеплитель", score: 0 }
            ], explanation: "🔥 Керамические плитки выдерживают температуру до 1600°C!", icon: "🔥" },
            { text: "Как космонавты «замешивают» бетон в невесомости?", options: [
                { letter: "А", text: "В специальном миксере с магнитным приводом", score: 0 }, { letter: "Б", text: "Они его не замешивают — используют готовые блоки", score: 0 },
                { letter: "В", text: "Вручную, как на Земле", score: 0 }, { letter: "Г", text: "Бетон в космосе не нужен", score: 25, correct: true }
            ], explanation: "🧱 Пока технологии не позволяют работать с бетоном в космосе!", icon: "🧱" },
            { text: "Что служит «фундаментом» для МКС?", options: [
                { letter: "А", text: "Сваи, вбитые в орбиту", score: 0 }, { letter: "Б", text: "Первый модуль «Заря»", score: 25, correct: true },
                { letter: "В", text: "Магнитные якоря", score: 0 }, { letter: "Г", text: "Она висит в воздухе без опоры", score: 0 }
            ], explanation: "🚀 Модуль «Заря» был первым и стал основой для всей станции!", icon: "🚀" },
            { text: "Какой «строительный» термин используют космонавты для стыковки кораблей?", options: [
                { letter: "А", text: "Монтаж", score: 0 }, { letter: "Б", text: "Сварка", score: 0 },
                { letter: "В", text: "Стыковка", score: 25, correct: true }, { letter: "Г", text: "Заклёпка века", score: 0 }
            ], explanation: "🤝 Стыковка — ключевой манёвр в космическом строительстве!", icon: "🤝" },
            { text: "Почему на космических станциях нет окон во всю стену, как в современных небоскрёбах?", options: [
                { letter: "А", text: "Стекло слишком тяжёлое", score: 0 }, { letter: "Б", text: "Опасность микрометеоритов", score: 25, correct: true },
                { letter: "В", text: "Архитекторы не успели придумать дизайн", score: 0 }, { letter: "Г", text: "Космонавтам не нравится вид на Землю", score: 0 }
            ], explanation: "☄️ Микрометеориты могут пробить стекло — это слишком опасно!", icon: "☄️" },
            { text: "Какой «инструмент» есть у каждого космонавта на МКС для мелкого ремонта?", options: [
                { letter: "А", text: "Набор отвёрток", score: 0 }, { letter: "Б", text: "Универсальный гаечный ключ", score: 0 },
                { letter: "В", text: "Изолента космического образца", score: 25, correct: true }, { letter: "Г", text: "Волшебная палочка", score: 0 }
            ], explanation: "📦 Скотч и изолента — must-have в космосе!", icon: "📦" },
            { text: "Как называется процесс «сборки» МКС на орбите?", options: [
                { letter: "А", text: "Возведение", score: 0 }, { letter: "Б", text: "Поэлементное строительство", score: 0 },
                { letter: "В", text: "Модульная сборка", score: 25, correct: true }, { letter: "Г", text: "Конструктор «Лего-космос»", score: 0 }
            ], explanation: "🧩 Модули доставляли по одному и собирали как конструктор!", icon: "🧩" },
            { text: "Что используют вместо цемента при строительстве на Луне (в экспериментальных проектах)?", options: [
                { letter: "А", text: "Лунную пыль + бактерии", score: 25, correct: true }, { letter: "Б", text: "Суперклей", score: 0 },
                { letter: "В", text: "Замороженную воду", score: 0 }, { letter: "Г", text: "Ничего — печатают на 3D-принтере из металла", score: 0 }
            ], explanation: "🦠 Есть проекты биоцемента из реголита — лунной пыли!", icon: "🦠" },
            { text: "Почему солнечные батареи на МКС разворачивают постепенно, а не сразу?", options: [
                { letter: "А", text: "Чтобы не напугать космонавтов", score: 0 }, { letter: "Б", text: "Из-за инерции в невесомости", score: 25, correct: true },
                { letter: "В", text: "Чтобы не создать ударную волну", score: 0 }, { letter: "Г", text: "Так красивее", score: 0 }
            ], explanation: "🌀 Инерция в невесомости работает иначе — нужно быть осторожным!", icon: "🌀" },
            { text: "Какой «строительный дефект» однажды чуть не сорвал запуск ракеты?", options: [
                { letter: "А", text: "Не закрученный болт", score: 25, correct: true }, { letter: "Б", text: "Ошибка в чертежах", score: 0 },
                { letter: "В", text: "Забыли люк закрыть", score: 0 }, { letter: "Г", text: "На корпусе нашли граффити", score: 0 }
            ], explanation: "🔩 Мелочи иногда решают всё! Болты проверяют несколько раз!", icon: "🔩" },
            { text: "Как космонавты крепят инструменты к стене в невесомости?", options: [
                { letter: "А", text: "Гвоздями", score: 0 }, { letter: "Б", text: "Липучками и карабинами", score: 25, correct: true },
                { letter: "В", text: "Примораживают", score: 0 }, { letter: "Г", text: "Заколдовывают", score: 0 }
            ], explanation: "🔗 Липучки и карабины — главные помощники космонавтов!", icon: "🔗" },
            { text: "Какой «архитектурный стиль» преобладает на МКС?", options: [
                { letter: "А", text: "Хай-тек", score: 0 }, { letter: "Б", text: "Минимализм", score: 0 },
                { letter: "В", text: "Функционализм", score: 25, correct: true }, { letter: "Г", text: "Космодеко", score: 0 }
            ], explanation: "📐 Всё подчинено функционалу — каждый сантиметр на счету!", icon: "📐" },
            { text: "Какой неожиданный предмет стал символом космического строительства?", options: [
                { letter: "А", text: "Зубная щётка", score: 0 }, { letter: "Б", text: "Клейкая лента (скотч)", score: 25, correct: true },
                { letter: "В", text: "Карандаш", score: 0 }, { letter: "Г", text: "Резинка", score: 0 }
            ], explanation: "📜 Скотч чинил всё — от скафандров до оборудования!", icon: "📜" },
            { text: "Что космонавты используют как «отвес» в невесомости?", options: [
                { letter: "А", text: "Верёвку с грузиком", score: 0 }, { letter: "Б", text: "Лазерный уровень", score: 0 },
                { letter: "В", text: "Самого себя — выравниваются по линиям модуля", score: 25, correct: true }, { letter: "Г", text: "Маятник Фуко", score: 0 }
            ], explanation: "🧭 В невесомости ориентируются по визуальным меткам!", icon: "🧭" },
            { text: "Какая проблема со строительной техникой возникла бы на Марсе?", options: [
                { letter: "А", text: "Пыль всё сломает", score: 0 }, { letter: "Б", text: "Гравитация слишком слабая для тяжёлой техники", score: 25, correct: true },
                { letter: "В", text: "Нет электричества", score: 0 }, { letter: "Г", text: "Техника будет тонуть в песке", score: 0 }
            ], explanation: "🪨 Марсианская гравитация слабее земной в 2.5 раза!", icon: "🪨" },
            { text: "Что общего между строительством небоскрёбов и МКС?", options: [
                { letter: "А", text: "Используют краны", score: 0 }, { letter: "Б", text: "Модульный принцип сборки", score: 25, correct: true },
                { letter: "В", text: "Нужен фундамент", score: 0 }, { letter: "Г", text: "Работают на высоте", score: 0 }
            ], explanation: "🏢 И небоскрёбы, и МКС строят из готовых модулей!", icon: "🏢" }
        ];

        const ranks = [
            { min: 0, max: 100, title: "🧑‍🚀 КОСМО-ПОДСОБНИК", desc: "Ты только начинаешь космический путь!" },
            { min: 101, max: 250, title: "👨‍🚀 БОРТИНЖЕНЕР", desc: "Уже кое-что понимаешь в космосе!" },
            { min: 251, max: 400, title: "🚀 ГЛАВНЫЙ КОНСТРУКТОР", desc: "Отличные знания! Роскосмос зовёт тебя!" },
            { min: 401, max: 500, title: "🏆 КОСМИЧЕСКАЯ ЛЕГЕНДА 🏆", desc: "Ты покорил космос! Поздравляем!" }
        ];

        let playerName = "", currentIndex = 0, totalScore = 0, isAnswered = false, currentQuestion = null;

        function showScreen(id) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active-screen'));
            document.getElementById(id).classList.add('active-screen');
        }

        function getRank() { for (let r of ranks) if (totalScore >= r.min && totalScore <= r.max) return r; return ranks[0]; }

        function startGame() {
            playerName = document.getElementById('player-name').value.trim() || "Анонимный космонавт";
            currentIndex = 0; totalScore = 0; isAnswered = false;
            showScreen('game-screen');
            loadQuestion();
        }

        function loadQuestion() {
            if (currentIndex >= questions.length) { showResults(); return; }
            currentQuestion = questions[currentIndex];
            isAnswered = false;
            document.getElementById('current-q').textContent = currentIndex + 1;
            document.getElementById('total-q').textContent = questions.length;
            document.getElementById('question-text').textContent = currentQuestion.text;
            document.getElementById('question-icon').textContent = currentQuestion.icon;
            document.getElementById('progress-fill').style.width = `${((currentIndex + 1) / questions.length) * 100}%`;
            document.getElementById('feedback').style.display = 'none';
            document.getElementById('next-btn').style.display = 'none';
            
            const container = document.getElementById('options-container');
            container.innerHTML = '';
            currentQuestion.options.forEach((opt, idx) => {
                const div = document.createElement('div');
                div.className = 'option';
                div.innerHTML = `<div class="letter">${opt.letter}</div><span style="flex:1;">${opt.text}</span>`;
                div.onclick = () => { if (!isAnswered) selectAnswer(opt); };
                container.appendChild(div);
            });
        }

        function selectAnswer(selected) {
            isAnswered = true;
            const isCorrect = selected.correct === true;
            if (isCorrect) totalScore += selected.score;
            
            document.querySelectorAll('.option').forEach((opt, idx) => {
                opt.style.pointerEvents = 'none';
                if (currentQuestion.options[idx].correct) opt.classList.add('correct');
                else if (currentQuestion.options[idx] === selected && !currentQuestion.options[idx].correct) opt.classList.add('incorrect');
            });
            
            const fb = document.getElementById('feedback');
            fb.style.display = 'block';
            fb.innerHTML = `<div><span style="font-size:40px;">${isCorrect ? '✅' : '❌'}</span><div style="margin-top:10px;">${currentQuestion.explanation}<br>${isCorrect ? `+${selected.score} очков` : `+0 очков (правильный ответ: ${currentQuestion.options.find(o => o.correct).letter})`}</div></div>`;
            fb.style.background = isCorrect ? 'rgba(0,255,0,0.2)' : 'rgba(255,0,0,0.2)';
            fb.style.border = `2px solid ${isCorrect ? '#00ff00' : '#ff0000'}`;
            document.getElementById('next-btn').style.display = 'block';
        }

        function nextQuestion() { currentIndex++; loadQuestion(); }
        
        function showResults() {
            const rank = getRank();
            document.getElementById('winner-name').textContent = playerName;
            document.getElementById('final-score').textContent = totalScore;
            document.getElementById('rank-title').textContent = rank.title;
            document.getElementById('result-name').textContent = playerName;
            document.getElementById('result-score').textContent = totalScore;
            document.getElementById('result-rank').textContent = rank.title;
            document.getElementById('result-date').textContent = new Date().toLocaleDateString('ru-RU');
            showScreen('result-screen');
        }

        function createScreenshot() {
            const rank = getRank();
            const currentDate = new Date().toLocaleDateString('ru-RU');
            
            document.getElementById('screenshot-name').textContent = playerName;
            document.getElementById('screenshot-player-name').textContent = playerName;
            document.getElementById('screenshot-score').textContent = totalScore;
            document.getElementById('screenshot-points').textContent = totalScore;
            document.getElementById('screenshot-rank').textContent = rank.title;
            document.getElementById('screenshot-player-rank').textContent = rank.title;
            document.getElementById('screenshot-date').textContent = currentDate;
            
            const screenshotElement = document.getElementById('screenshot-template');
            
            html2canvas(screenshotElement, {
                scale: 2,
                backgroundColor: null,
                useCORS: true,
                logging: false
            }).then(canvas => {
                const imageData = canvas.toDataURL('image/png');
                const link = document.createElement('a');
                const fileName = `стройка_космос_${playerName}_${totalScore}.png`;
                link.download = fileName;
                link.href = imageData;
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
                showMessage('✅ Скриншот сохранён! Поделитесь результатом в Telegram!');
            }).catch(error => {
                console.error('Ошибка:', error);
                showMessage('⚠️ Не удалось создать скриншот. Попробуйте ещё раз.');
            });
        }

        function showMessage(text) {
            const message = document.createElement('div');
            message.textContent = text;
            message.style.cssText = `
                position: fixed;
                top: 20px;
                left: 50%;
                transform: translateX(-50%);
                background: rgba(0,0,0,0.9);
                color: white;
                padding: 15px 25px;
                border-radius: 10px;
                font-size: 16px;
                z-index: 10000;
                box-shadow: 0 4px 20px rgba(0,0,0,0.5);
                animation: fadeIn 0.3s ease;
            `;
            document.body.appendChild(message);
            setTimeout(() => {
                message.style.opacity = '0';
                message.style.transform = 'translateX(-50%) translateY(-20px)';
                message.style.transition = 'all 0.3s ease';
                setTimeout(() => document.body.removeChild(message), 300);
            }, 3000);
        }

        document.addEventListener('DOMContentLoaded', () => {
            document.getElementById('start-btn').onclick = startGame;
            document.getElementById('next-btn').onclick = nextQuestion;
            document.getElementById('screenshot-btn').onclick = createScreenshot;
            document.getElementById('player-name').focus();
        });
    </script>
    <script src="https://html2canvas.hertzen.com/dist/html2canvas.min.js"></script>
</body>
</html>
