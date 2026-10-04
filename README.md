<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Кирилл ❤️ Диана</title>
<style>
* {
    box-sizing: border-box;
}
body {
    margin: 0;
    min-height: 100vh;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    background: linear-gradient(145deg, #fff0f5, #f0e7ff);
    color: #302027;
}
.container {
    max-width: 520px;
    margin: auto;
    padding: 25px 16px 40px;
}
.card {
    background: rgba(255,255,255,0.88);
    border-radius: 28px;
    padding: 22px;
    box-shadow: 0 18px 50px rgba(100,50,80,0.15);
}
h1 {
    text-align: center;
    font-size: 30px;
    margin: 5px 0;
}
.date {
    text-align: center;
    color: #9b6478;
    margin-bottom: 20px;
}
.counter {
    background: white;
    border-radius: 20px;
    padding: 16px;
    text-align: center;
    margin-bottom: 18px;
}
.counter b {
    display: block;
    font-size: 28px;
    margin-top: 5px;
}
.photos {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
}
.photo {
    aspect-ratio: 1;
    border-radius: 18px;
    background: linear-gradient(135deg, #f5d8e2, #ead9f5);
    display: flex;
    justify-content: center;
    align-items: center;
    color: #8f6c7b;
    overflow: hidden;
}
.photo img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.message {
    background: #fff8fb;
    border-radius: 20px;
    padding: 18px;
    margin-top: 18px;
    text-align: center;
    line-height: 1.55;
}
button {
    width: 100%;
    border: 0;
    border-radius: 18px;
    padding: 15px;
    margin-top: 16px;
    background: #e85d82;
    color: white;
    font-size: 16px;
    font-weight: bold;
}
#hearts {
    position: fixed;
    inset: 0;
    pointer-events: none;
    overflow: hidden;
}
.heart {
    position: absolute;
    bottom: -30px;
    font-size: 25px;
    animation: fly 2.5s ease-out forwards;
}
@keyframes fly {
    0% {
        transform: translateY(0);
        opacity: 0;
    }
    20% {
        opacity: 1;
    }
    100% {
        transform: translateY(-100vh);
        opacity: 0;
    }
}
</style>
</head>
<body>
<div id="hearts"></div>
<div class="container">
    <div class="card">
        <h1>Кирилл ❤️ Диана</h1>
        <div class="date">
            27.09.2026
        </div>
        <div class="counter">
            Вместе уже
            <b id="days">0 дней</b>
        </div>
        <div class="photos">
            <div class="photo">📸 Фото 1</div>
            <div class="photo">📸 Фото 2</div>
            <div class="photo">📸 Фото 3</div>
            <div class="photo">📸 Фото 4</div>
        </div>
        <div class="message">
            Я просто хотел сделать для тебя что-то,
            что останется на память.
            <br><br>
            Собрал сюда наши моменты,
            потому что каждый из них для меня особенный.
            <br><br>
            И это только начало нашей истории. ❤️
        </div>
        <button onclick="makeHearts()">
            Нажми ❤️
        </button>
    </div>
</div>
<script>
const startDate = new Date(2026, 8, 27);
function updateCounter() {
    const now = new Date();
    const difference = Math.max(
        0,
        Math.floor((now - startDate) / 86400000)
    );
    let word = "дней";
    const lastTwo = difference % 100;
    const lastOne = difference % 10;
    if (lastOne === 1 && lastTwo !== 11) {
        word = "день";
    }
    else if (
        [2, 3, 4].includes(lastOne) &&
        ![12, 13, 14].includes(lastTwo)
    ) {
        word = "дня";
    }
    document.getElementById("days").textContent =
        difference + " " + word;
}
function makeHearts() {
    const container =
        document.getElementById("hearts");
    for (let i = 0; i < 25; i++) {
        const heart =
            document.createElement("div");
        heart.className = "heart";
        heart.textContent =
            ["❤️", "💕", "💗", "💖"][
                Math.floor(Math.random() * 4)
            ];
        heart.style.left =
            Math.random() * 100 + "vw";
        heart.style.animationDelay =
            Math.random() * 0.7 + "s";
        container.appendChild(heart);
        setTimeout(() => {
            heart.remove();
        }, 3000);
    }
}
updateCounter();
setInterval(updateCounter, 60000);
</script>
</body>
</html>