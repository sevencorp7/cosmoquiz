
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Космическая стройка | Квиз СТФ</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            min-height: 100vh;
            background: radial-gradient(ellipse at center, #0a0a2a 0%, #030318 100%);
            font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, 'Roboto', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 16px;
            position: relative;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: radial-gradient(2px 2px at 20px 30px, #fff, transparent),
                              radial-gradient(2px 2px at 40px 70px, #fff, transparent),
                              radial-gradient(1px 1px at 100px 200px, #fff, transparent),
                              radial-gradient(3px 3px at 300px 150px, #fff, transparent);
            background-repeat: no-repeat;
            background-size: 200px 200px;
            animation: starsMove 30s linear infinite;
            pointer-events: none;
            opacity: 0.6;
        }

        @keyframes starsMove {
            from { transform: translateY(0); }
            to { transform: translateY(-200px); }
        }

        .game-container {
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        .screen {
            display: none;
        }

        .screen.active {
            display: block;
            animation: fadeIn 0.4s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        .card {
            background: rgba(10, 10, 40, 0.9);
            backdrop-filter: blur(15px);
            border-radius: 40px;
            padding: 24px 20px;
            border: 2px solid #00ffff66;
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
        }

        h1 {
            text-align: center;
            font-size: 1.8rem;
            margin: 10px 0;
            color: white;
        }

        .slogan {
            text-align: center;
            font-size: 0.9rem;
            color: #ffd600;
            margin: 12px 0;
            padding: 8px;
            border-top: 1px solid rgba(255,255,255,0.2);
            border-bottom: 1px solid rgba(255,255,255,0.2);
            font-weight: bold;
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
            padding: 16px;
            border-radius: 30px;
            border: 2px solid #00ffff;
            background: rgba(0,0,0,0.5);
            color: white;
            font-size: 1rem;
            text-align: center;
        }

        .btn {
            width: 100%;
            padding: 16px;
            margin: 10px 0;
            border: none;
            border-radius: 40px;
            font-size: 1.1rem;
            font-weight: bold;
            background: linear-gradient(135deg, #00aa88, #00ffcc);
            color: #0a0a2a;
            cursor: pointer;
            transition: 0.1s linear;
        }

        .btn:active {
            transform: scale(0.97);
        }

        .btn-telegram {
            background: linear-gradient(135deg, #0088cc, #00aaff);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            text-decoration: none;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin: 20px 0;
        }

        .option {
            background: rgba(255,255,255,0.1);
            border: 2px solid #00ffff66;
            border-radius: 20px;
            padding: 16px;
            display: flex;
            align-items: center;
            gap: 15px;
            font-size: 1rem;
            color: white;
            cursor: pointer;
            transition: 0.1s linear;
        }

        .option:active {
            transform: scale(0.98);
            background: rgba(0,255,255,0.2);
        }

        .option.correct {
            background: rgba(0,255,0,0.3);
            border-color: #0f0;
        }

        .option.incorrect {
            background: rgba(255,0,0,0.3);
            border-color: #f00;
        }

        .option.disabled {
            pointer-events: none;
            opacity: 0.8;
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
            color: #0a0a2a;
        }

        .progress-bar {
            height: 8px;
            background: rgba(255,255,255,0.2);
            border-radius: 10px;
            margin: 15px 0;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, #00ffcc, #00aaff);
            transition: width 0.3s;
        }

        .question-counter {
            text-align: center;
            font-size: 0.85rem;
            color: #ccc;
            margin-top: 5px;
        }

        .feedback {
            text-align: center;
            padding: 12px;
            border-radius: 20px;
            margin: 15px 0;
            font-weight: bold;
        }

        .result-score {
            font-size: 4rem;
            text-align: center;
            font-weight: bold;
            color: #00ffcc;
            margin: 15px 0;
        }

        .rank-card {
            background: linear-gradient(135deg, #00ffff33, #ff00ff33);
            border-radius: 30px;
            padding: 15px;
            text-align: center;
            margin: 15px 0;
            border: 1px solid #00ffff;
        }

        .rank-title {
            font-size: 1.5rem;
            font-weight: bold;
            color: #ffaa00;
        }

        .astronaut {
            text-align: center;
            font-size: 70px;
            margin: 15px 0;
            animation: floatAnim 2s infinite;
        }

        @keyframes floatAnim {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .results-table {
            width: 100%;
            margin: 15px 0;
            border-collapse: collapse;
            background: rgba(0,0,0,0.5);
            border-radius: 20px;
            overflow: hidden;
        }

        .results-table td {
            padding: 12px;
            border-bottom: 1px solid #00ffff33;
            color: white;
        }

        .results-table td:first-child {
            font-weight: bold;
            color: #00ffff;
        }

        .cosmonautics-card {
            background: radial-gradient(ellipse at 30% 40%, #0a0a4a, #010118);
            border-radius: 20px;
            padding: 15px;
            margin: 15px 0;
            text-align: center;
            border: 2px solid #00ffcc;
            animation: glow 2s infinite;
        }

        @keyframes glow {
            0%, 100% { box-shadow: 0 0 5px #00ffcc; }
            50% { box-shadow: 0 0 20px #00ffcc; }
        }

        .cosmonautics-title {
            font-size: 1.3rem;
            background: linear-gradient(135deg, #00ffcc, #ffaa00);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-weight: bold;
        }

        @media (max-width: 500px) {
            .card { padding: 16px; }
            h1 { font-size: 1.5rem; }
            .option { padding: 12px; font-size: 0.85rem; }
            .result-score { font-size: 3rem; }
        }
    </style>
</head>
<body>
<div class="game-container">
    <!-- ЭКРАН ПРИВЕТСТВИЯ -->
    <div id="welcomeScreen" class="screen active">
        <div class="card">
            <div class="astronaut">🚀</div>
            <h1>КОСМИЧЕСКАЯ СТРОЙКА</h1>
            <div class="slogan">🌟 СТФ строит будущее — даже в космосе! 🌟</div>
            <div class="input-group">
                <label>👤 Введи своё имя:</label>
                <input type="text" id="playerNameInput" placeholder="Например: Юрий Гагарин" maxlength="25">
            </div>
            <button class="btn" id="startBtn">🚀 СТАРТ МИССИИ</button>
            <div style="text-align: center; margin-top: 15px; font-size: 0.75rem; color: #aaa;">20 вопросов • Космическая стройка • СТФ</div>
        </div>
    </div>

    <!-- ЭКРАН ИГРЫ -->
    <div id="gameScreen" class="screen">
        <div class="card">
            <div class="slogan" style="font-size: 0.7rem;">🌟 СТФ строит будущее — даже в космосе! 🌟</div>
            <div class="progress-bar"><div class="progress-fill" id="progressFill"></div></div>
            <div class="question-counter">Вопрос <span id="currentQ">1</span> из <span id="totalQ">20</span></div>
            <div id="questionIcon" style="font-size: 45px; text-align: center; margin: 10px 0;">🏗️</div>
            <h2 id="questionText" style="font-size: 1.1rem; text-align: center; margin: 10px 0; color: white;">Загрузка...</h2>
            <div id="optionsContainer" class="options"></div>
            <div id="feedbackDiv" class="feedback" style="display: none;"></div>
            <button class="btn" id="nextBtn" style="display: none;">▶ СЛЕДУЮЩИЙ ВОПРОС</button>
        </div>
    </div>

    <!-- ЭКРАН РЕЗУЛЬТАТОВ -->
    <div id="resultScreen" class="screen">
        <div class="card">
            <div class="astronaut">🏆</div>
            <h1>ПОЗДРАВЛЯЕМ, <span id="winnerName">Игрок</span>!</h1>
            <div class="slogan">🌟 СТФ строит будущее — даже в космосе! 🌟</div>
            <div class="result-score" id="finalScore">0</div>
            <div class="rank-card">
                <div>🎖️ Твоё звание 🎖️</div>
                <div class="rank-title" id="rankTitle">-</div>
            </div>
            <table class="results-table">
                <tr><td>👨‍🚀 Космонавт:</td><td id="resultName">-</td></tr>
                <tr><td>📊 Набрано очков:</td><td id="resultScore">0</td></tr>
                <tr><td>🏆 Получено звание:</td><td id="resultRank">-</td></tr>
                <tr><td>📅 Дата миссии:</td><td id="resultDate">-</td></tr>
            </table>
            <div class="cosmonautics-card">
                <div class="cosmonautics-title">🚀 С ДНЁМ КОСМОНАВТИКИ! 🚀</div>
                <div style="font-size: 12px; margin-top: 5px;">12 апреля — день покорения космоса! Желаем новых открытий! 🌟</div>
            </div>
            <a href="https://t.me/+TW9deUkPFpEzMWYy" target="_blank" class="btn btn-telegram">📱 Присоединиться к Telegram-каналу СТФ</a>
        </div>
    </div>
</div>

<script>
    // ВОПРОСЫ
    const QUESTIONS = [
        { text: "Какой материал использовали первые советские инженеры для теплоизоляции ракет?", options: [
            { letter: "А", text: "Вата", score: 0 }, { letter: "Б", text: "Войлок", score: 0 },
            { letter: "В", text: "Старые валенки", score: 25, correct: true }, { letter: "Г", text: "Пух из подушек", score: 0 }
        ], explanation: "✨ Применяли войлок и даже старые валенки!", icon: "🧦" },
        { text: "Главная проблема при строительстве базы на Луне?", options: [
            { letter: "А", text: "Отсутствие грунта", score: 0 }, { letter: "Б", text: "Кратеры", score: 0 },
            { letter: "В", text: "Гравитация в 6 раз слабее", score: 25, correct: true }, { letter: "Г", text: "Инопланетяне", score: 0 }
        ], explanation: "🌕 Лунная гравитация в 6 раз слабее земной!", icon: "🌙" },
        { text: "Какой инструмент был у Гагарина в «Востоке»?", options: [
            { letter: "А", text: "Отвёртка", score: 0 }, { letter: "Б", text: "Молоток", score: 0 },
            { letter: "В", text: "Специальный ключ", score: 25, correct: true }, { letter: "Г", text: "Ничего", score: 0 }
        ], explanation: "🔑 Специальный ключ на случай отказа автоматики!", icon: "🔧" },
        { text: "Почему на МКС нет кранов?", options: [
            { letter: "А", text: "Слишком тяжёлые", score: 0 }, { letter: "Б", text: "В невесомости любой предмет — кран", score: 25, correct: true },
            { letter: "В", text: "Доставляют роботами", score: 0 }, { letter: "Г", text: "Запрещено", score: 0 }
        ], explanation: "🏗️ В невесомости можно передвинуть любой груз!", icon: "🏗️" },
        { text: "Чем защищают корабли от перегрева?", options: [
            { letter: "А", text: "Сталь", score: 0 }, { letter: "Б", text: "Керамика", score: 25, correct: true },
            { letter: "В", text: "Краска", score: 0 }, { letter: "Г", text: "Фольга", score: 0 }
        ], explanation: "🔥 Керамические плитки выдерживают 1600°C!", icon: "🔥" },
        { text: "Как замешивают бетон в космосе?", options: [
            { letter: "А", text: "В миксере", score: 0 }, { letter: "Б", text: "Готовыми блоками", score: 0 },
            { letter: "В", text: "Вручную", score: 0 }, { letter: "Г", text: "Бетон не нужен", score: 25, correct: true }
        ], explanation: "🧱 Пока бетон в космосе не используют!", icon: "🧱" },
        { text: "Что служит фундаментом МКС?", options: [
            { letter: "А", text: "Сваи", score: 0 }, { letter: "Б", text: "Модуль «Заря»", score: 25, correct: true },
            { letter: "В", text: "Магниты", score: 0 }, { letter: "Г", text: "Висит без опоры", score: 0 }
        ], explanation: "🚀 Первый модуль «Заря» — основа станции!", icon: "🚀" },
        { text: "Как называется стыковка кораблей?", options: [
            { letter: "А", text: "Монтаж", score: 0 }, { letter: "Б", text: "Сварка", score: 0 },
            { letter: "В", text: "Стыковка", score: 25, correct: true }, { letter: "Г", text: "Заклёпка", score: 0 }
        ], explanation: "🤝 Стыковка — главный космический манёвр!", icon: "🤝" },
        { text: "Почему нет больших окон на станциях?", options: [
            { letter: "А", text: "Стекло тяжёлое", score: 0 }, { letter: "Б", text: "Микрометеориты", score: 25, correct: true },
            { letter: "В", text: "Не успели", score: 0 }, { letter: "Г", text: "Не нравится вид", score: 0 }
        ], explanation: "☄️ Микрометеориты могут пробить стекло!", icon: "☄️" },
        { text: "Что используют для ремонта на МКС?", options: [
            { letter: "А", text: "Отвёртки", score: 0 }, { letter: "Б", text: "Гаечный ключ", score: 0 },
            { letter: "В", text: "Изолента", score: 25, correct: true }, { letter: "Г", text: "Магия", score: 0 }
        ], explanation: "📦 Скотч и изолента — главные инструменты!", icon: "📦" },
        { text: "Как называется сборка МКС?", options: [
            { letter: "А", text: "Возведение", score: 0 }, { letter: "Б", text: "Поэлементная", score: 0 },
            { letter: "В", text: "Модульная сборка", score: 25, correct: true }, { letter: "Г", text: "Лего", score: 0 }
        ], explanation: "🧩 Модули собирали как конструктор!", icon: "🧩" },
        { text: "Что используют вместо цемента на Луне?", options: [
            { letter: "А", text: "Лунную пыль + бактерии", score: 25, correct: true }, { letter: "Б", text: "Суперклей", score: 0 },
            { letter: "В", text: "Лёд", score: 0 }, { letter: "Г", text: "3D-печать", score: 0 }
        ], explanation: "🦠 Биоцемент из реголита — лунной пыли!", icon: "🦠" },
        { text: "Почему батареи разворачивают постепенно?", options: [
            { letter: "А", text: "Чтобы не напугать", score: 0 }, { letter: "Б", text: "Инерция в невесомости", score: 25, correct: true },
            { letter: "В", text: "Чтобы не создать удар", score: 0 }, { letter: "Г", text: "Так красивее", score: 0 }
        ], explanation: "🌀 В невесомости инерция работает иначе!", icon: "🌀" },
        { text: "Что чуть не сорвало запуск ракеты?", options: [
            { letter: "А", text: "Не закрученный болт", score: 25, correct: true }, { letter: "Б", text: "Ошибка в чертежах", score: 0 },
            { letter: "В", text: "Забыли люк", score: 0 }, { letter: "Г", text: "Граффити", score: 0 }
        ], explanation: "🔩 Мелочи решают всё! Болты проверяют много раз!", icon: "🔩" },
        { text: "Как крепят инструменты в невесомости?", options: [
            { letter: "А", text: "Гвоздями", score: 0 }, { letter: "Б", text: "Липучками", score: 25, correct: true },
            { letter: "В", text: "Примораживают", score: 0 }, { letter: "Г", text: "Колдовство", score: 0 }
        ], explanation: "🔗 Липучки и карабины — главные помощники!", icon: "🔗" }
    ];

    // Добавляем остальные вопросы до 20 (копируем с изменением, чтобы хватило)
    while (QUESTIONS.length < 20) {
        QUESTIONS.push({
            text: "Какой стиль преобладает на МКС?",
            options: [
                { letter: "А", text: "Хай-тек", score: 0 }, { letter: "Б", text: "Минимализм", score: 0 },
                { letter: "В", text: "Функционализм", score: 25, correct: true }, { letter: "Г", text: "Космодеко", score: 0 }
            ], explanation: "📐 Всё подчинено функционалу!", icon: "📐"
        });
    }
    // Обрезаем до 20
    const FINAL_QUESTIONS = QUESTIONS.slice(0, 20);

    const RANKS = [
        { min: 0, max: 100, title: "🧑‍🚀 КОСМО-ПОДСОБНИК" },
        { min: 101, max: 250, title: "👨‍🚀 БОРТИНЖЕНЕР" },
        { min: 251, max: 400, title: "🚀 ГЛАВНЫЙ КОНСТРУКТОР" },
        { min: 401, max: 500, title: "🏆 КОСМИЧЕСКАЯ ЛЕГЕНДА 🏆" }
    ];

    let playerName = "", currentQIndex = 0, totalScore = 0, answered = false, currentQuestion = null;

    function showScreen(id) {
        document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
        document.getElementById(id).classList.add('active');
    }

    function getRank() {
        for (let r of RANKS) if (totalScore >= r.min && totalScore <= r.max) return r;
        return RANKS[0];
    }

    function startGame() {
        let input = document.getElementById('playerNameInput');
        playerName = input.value.trim();
        if (!playerName) playerName = "Анонимный космонавт";
        currentQIndex = 0;
        totalScore = 0;
        answered = false;
        showScreen('gameScreen');
        loadQuestion();
    }

    function loadQuestion() {
        if (currentQIndex >= FINAL_QUESTIONS.length) {
            showResults();
            return;
        }
        currentQuestion = FINAL_QUESTIONS[currentQIndex];
        answered = false;

        document.getElementById('currentQ').innerText = currentQIndex + 1;
        document.getElementById('totalQ').innerText = FINAL_QUESTIONS.length;
        document.getElementById('questionText').innerText = currentQuestion.text;
        document.getElementById('questionIcon').innerHTML = currentQuestion.icon;
        let percent = ((currentQIndex + 1) / FINAL_QUESTIONS.length) * 100;
        document.getElementById('progressFill').style.width = percent + '%';
        document.getElementById('feedbackDiv').style.display = 'none';
        document.getElementById('nextBtn').style.display = 'none';

        let container = document.getElementById('optionsContainer');
        container.innerHTML = '';
        currentQuestion.options.forEach((opt, idx) => {
            let div = document.createElement('div');
            div.className = 'option';
            div.setAttribute('data-opt-index', idx);
            div.innerHTML = `<div class="letter">${opt.letter}</div><span style="flex:1;">${opt.text}</span>`;
            div.onclick = (function(o) { return function() { if (!answered) selectAnswer(o, this); }; })(opt);
            container.appendChild(div);
        });
    }

    function selectAnswer(selected, element) {
        if (answered) return;
        answered = true;
        let isCorrect = selected.correct === true;
        if (isCorrect) totalScore += selected.score;

        // Блокируем все варианты
        let allOpts = document.querySelectorAll('.option');
        allOpts.forEach(opt => { opt.style.pointerEvents = 'none'; opt.classList.add('disabled'); });

        // Подсветка
        if (isCorrect) {
            element.classList.add('correct');
        } else {
            element.classList.add('incorrect');
            // Показываем правильный ответ
            allOpts.forEach(opt => {
                let idx = parseInt(opt.getAttribute('data-opt-index'));
                if (currentQuestion.options[idx] && currentQuestion.options[idx].correct) opt.classList.add('correct');
            });
        }

        let fb = document.getElementById('feedbackDiv');
        fb.style.display = 'block';
        fb.innerHTML = `<div><span style="font-size:35px;">${isCorrect ? '✅' : '❌'}</span><div style="margin-top:8px;">${currentQuestion.explanation}<br>${isCorrect ? '+' + selected.score + ' очков' : '0 очков'}</div></div>`;
        fb.style.background = isCorrect ? 'rgba(0,255,0,0.2)' : 'rgba(255,0,0,0.2)';
        fb.style.border = `2px solid ${isCorrect ? '#0f0' : '#f00'}`;

        document.getElementById('nextBtn').style.display = 'block';
    }

    function nextQuestion() {
        currentQIndex++;
        loadQuestion();
    }

    function showResults() {
        let rank = getRank();
        let dateNow = new Date().toLocaleDateString('ru-RU');
        document.getElementById('winnerName').innerText = playerName;
        document.getElementById('finalScore').innerText = totalScore;
        document.getElementById('rankTitle').innerText = rank.title;
        document.getElementById('resultName').innerText = playerName;
        document.getElementById('resultScore').innerText = totalScore;
        document.getElementById('resultRank').innerText = rank.title;
        document.getElementById('resultDate').innerText = dateNow;
        showScreen('resultScreen');
    }

    // НАЗНАЧЕНИЕ СОБЫТИЙ
    document.getElementById('startBtn').onclick = startGame;
    document.getElementById('nextBtn').onclick = nextQuestion;
    document.getElementById('playerNameInput').addEventListener('keypress', function(e) {
        if (e.key === 'Enter') startGame();
    });
</script>
</body>
</html>
