<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>To Panha</title>

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, #ff9a9e, #fad0c4);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

/* Card animation */
.card {
  background: #fff;
  width: 90%;
  max-width: 400px;
  border-radius: 20px;
  box-shadow: 0 20px 40px rgba(0,0,0,0.2);
  text-align: center;
  padding: 20px;
  animation: slideFade 1.2s ease;
  position: relative;
  z-index: 10;
}

@keyframes slideFade {
  from { opacity: 0; transform: translateY(50px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Image heartbeat */
.card img {
  width: 100%;
  height: 300px;
  object-fit: cover;
  border-radius: 15px;
  animation: heartbeat 3s infinite;
}

@keyframes heartbeat {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.03); }
}

h1 {
  margin: 15px 0 5px;
  color: #e84393;
}

p {
  font-size: 15px;
  line-height: 1.6;
}

/* Button pulse */
button {
  margin-top: 15px;
  padding: 12px 20px;
  border: none;
  border-radius: 25px;
  background: #e84393;
  color: #fff;
  font-size: 16px;
  cursor: pointer;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% { box-shadow: 0 0 0 0 rgba(232,67,147,0.6); }
  70% { box-shadow: 0 0 0 15px rgba(232,67,147,0); }
  100% { box-shadow: 0 0 0 0 rgba(232,67,147,0); }
}

button:hover {
  background: #d63384;
}

/* Message pop */
.message {
  margin-top: 15px;
  font-weight: bold;
  color: #2d3436;
  min-height: 24px;
}

@keyframes pop {
  from { transform: scale(0.8); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}

/* Floating hearts */
.heart {
  position: absolute;
  bottom: -20px;
  font-size: 20px;
  animation: floatUp 5s linear infinite;
}

@keyframes floatUp {
  0% { transform: translateY(0) scale(1); opacity: 1; }
  100% { transform: translateY(-100vh) scale(1.5); opacity: 0; }
}

/* Card glow */
.card.glow {
  animation: glow 0.8s ease;
}

@keyframes glow {
  0% { box-shadow: 0 0 20px rgba(232,67,147,0.5); }
  50% { box-shadow: 0 0 60px rgba(232,67,147,1); }
  100% { box-shadow: 0 0 20px rgba(232,67,147,0.5); }
}

/* Screen shake */
.shake {
  animation: shake 0.4s;
}

@keyframes shake {
  0% { transform: translate(0); }
  25% { transform: translate(5px); }
  50% { transform: translate(-5px); }
  75% { transform: translate(5px); }
  100% { transform: translate(0); }
}

/* Heart explosion */
.burst {
  position: absolute;
  font-size: 24px;
  animation: burst 1.2s ease-out forwards;
}

@keyframes burst {
  from { transform: translate(0,0) scale(1); opacity: 1; }
  to {
    transform: translate(var(--x), var(--y)) scale(1.5);
    opacity: 0;
  }
}
</style>
</head>

<body>

<div class="card">
  <!-- Change image.jpg to your photo -->
  <img src="image.jpg" alt="My Love">

  <h1>My Love ❤️</h1>
  <p>
    You are the most beautiful part of my life.
    Every smile of yours makes my world brighter.
  </p>

  <button onclick="showLove()">Click for a surprise 💖</button>
  <div class="message" id="message"></div>
</div>

<script>
const messages = [
  "I love you more every day ❤️",
  "You are my sunshine ☀️",
  "My heart beats only for you 💓",
  "Forever and always 💍",
  "You are my everything 💖"
];

function showLove() {
  const card = document.querySelector(".card");
  const msg = document.getElementById("message");

  /* Show message */
  msg.textContent = messages[Math.floor(Math.random() * messages.length)];
  msg.style.animation = "none";
  msg.offsetHeight;
  msg.style.animation = "pop 0.4s ease";

  /* Glow effect */
  card.classList.remove("glow");
  void card.offsetWidth;
  card.classList.add("glow");

  /* Screen shake */
  document.body.classList.add("shake");
  setTimeout(() => document.body.classList.remove("shake"), 400);

  /* Heart explosion */
  for (let i = 0; i < 25; i++) {
    const heart = document.createElement("div");
    heart.className = "burst";
    heart.innerHTML = "❤️";
    heart.style.left = "50%";
    heart.style.top = "50%";
    heart.style.setProperty("--x", `${Math.random() * 400 - 200}px`);
    heart.style.setProperty("--y", `${Math.random() * 400 - 200}px`);
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 1200);
  }
}

/* Floating hearts background */
setInterval(() => {
  const heart = document.createElement("div");
  heart.className = "heart";
  heart.innerHTML = "❤️";
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.animationDuration = (3 + Math.random() * 3) + "s";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 6000);
}, 500);
</script>

</body>
</html>

