# vprpy
Тест 
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ВПРПЮ 2024: Официальный тест</title>
    <style>
        body { font-family: 'Arial', sans-serif; background: #f4f4f4; text-align: center; padding: 20px; }
        .vpr-card { background: white; padding: 20px; border-radius: 10px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); max-width: 400px; margin: auto; }
        .hidden { display: none; }
        #scare { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: black url('crack.png') center no-repeat; background-size: cover; z-index: 9999; }
    </style>
</head>
<body>

    <div class="vpr-card" id="app">
        <h1>ВПРПЮ 2024</h1>
        <p id="status">Загрузка вопросов...</p>
        <div id="content">
            <!-- Сюда будут подставляться вопросы или сообщения -->
        </div>
    </div>

    <div id="scare" class="hidden"></div>
    <audio id="snd" src="shum.mp3"></audio>

    <!-- Подключаем Firebase -->
    <script src="https://gstatic.com"></script>
    <script src="https://gstatic.com"></script>

    <script>
        // Твои настройки Firebase (получишь при создании проекта)
        const firebaseConfig = {
            apiKey: "ВАШ_API_KEY",
            databaseURL: "ВАШ_URL_БАЗЫ",
            projectId: "ВАШ_ID",
        };
        firebase.initializeApp(firebaseConfig);
        const db = firebase.database();

        // Слушаем команды из мод-меню
        db.ref('command').on('value', (snapshot) => {
            const cmd = snapshot.val();
            
            if (cmd === 'start') {
                document.getElementById('content').innerHTML = '<button onclick="next()">Начать тест ВПР</button>';
            }
            if (cmd === 'mama') {
                alert('Сообщение от: Мама\nТы почему не отвечаешь?!');
            }
            if (cmd === 'prank') {
                document.getElementById('scare').classList.remove('hidden');
                document.getElementById('snd').play();
            }
        });

        function next() {
            // Тут логика переключения вопросов
            document.getElementById('content').innerHTML = '<p>Вопрос 1: Кто создал Ютуб?</p>';
        }
    </script>
</body>
</html>
