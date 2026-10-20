
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#090d2b">
<title>Gửi Nguyễn Cẩm Tiên 💗</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  font-family: "Segoe UI", sans-serif;
  color: white;
  background: radial-gradient(
    ellipse at top,
    #38225f 0%,
    #17163f 40%,
    #070b22 100%
  );
  overflow-x: hidden;
}

#sky {
  position: fixed;
  inset: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  pointer-events: none;
}

.container {
  position: relative;
  z-index: 1;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 25px 15px;
}

.card {
  width: 100%;
  max-width: 680px;
  padding: 35px 24px;
  text-align: center;
  border: 1px solid #ffffff40;
  border-radius: 28px;
  background: #ffffff12;
  backdrop-filter: blur(12px);
  box-shadow: 0 20px 70px #0005;
}

.moon {
  font-size: 48px;
  animation: glow 3s infinite;
}

.subtitle {
  color: #d9ccff;
  font-size: 13px;
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-top: 15px;
}

h1 {
  font-size: clamp(32px, 8vw, 55px);
  margin: 20px 0;
  background: linear-gradient(
    90deg,
    #fff,
    #ffb7df,
    #d1c2ff
  );
  color: transparent;
  background-clip: text;
  -webkit-background-clip: text;
}

.intro {
  font-size: 17px;
  line-height: 1.9;
  color: #f1eaff;
}

.stars {
  color: #ffd9f1;
  letter-spacing: 8px;
  margin: 25px 0;
}

button {
  border: none;
  border-radius: 30px;
  padding: 14px 22px;
  margin: 6px;
  font-size: 15px;
  font-weight: bold;
  color: white;
  background: linear-gradient(135deg, #a66cf0, #ed77bb);
  cursor: pointer;
  box-shadow: 0 5px 25px #b86bff44;
}

button:active {
  transform: scale(.96);
}

.secondary {
  background: #ffffff18;
  border: 1px solid #ffffff40;
}

#letter {
  display: none;
  margin-top: 25px;
  padding: 22px;
  border-radius: 20px;
  background: #080c2c99;
  border: 1px solid #ffffff30;
  text-align: left;
  white-space: pre-line;
  line-height: 2;
  font-size: 16px;
  color: #fff4fc;
}

#letter.show {
  display: block;
  animation: appear 1s ease;
}

.signature {
  text-align: right;
  color: #ffb7df;
  font-weight: bold;
  margin-top: 20px;
}

.status {
  color: #d9ccff;
  font-size: 12px;
  margin-top: 12px;
}

.heart {
  position: fixed;
  bottom: -40px;
  z-index: 2;
  pointer-events: none;
  animation: floatUp linear forwards;
}

@keyframes floatUp {
  to {
    transform: translateY(-110vh) rotate(40deg);
    opacity: 0;
  }
}

@keyframes glow {
  50% {
    filter: drop-shadow(0 0 25px #ffe9ad);
    transform: scale(1.08);
  }
}

@keyframes appear {
  from {
    opacity: 0;
    transform: translateY(15px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: .01ms !important;
  }
}
</style>
</head>

<body>

<canvas id="sky"></canvas>

<div class="container">
  <main class="card">

    <div class="moon">☾ ✦</div>

    <div class="subtitle">
      Một lời nhắn dành riêng cho
    </div>

    <h1>Nguyễn Cẩm Tiên</h1>

    <p class="intro">
      Giữa hàng triệu vì sao trên bầu trời,
      có một ngôi sao đặc biệt mà anh luôn muốn
      dành những điều dịu dàng nhất. 🌙💗
      <br><br>
      Chúc em ngày 20/10 thật vui vẻ,
      xinh đẹp và luôn ngập tràn hạnh phúc!
    </p>

    <div class="stars">
      ✧ · ˚ · ✦ · ˚ · ✧
    </div>

    <button id="openBtn">
      💌 Mở lời nhắn bí mật
    </button>

    <button id="musicBtn" class="secondary">
      ♫ Bật nhạc nền
    </button>

    <div class="status" id="status">
      Có một điều bí mật anh muốn nói với em...
    </div>

    <section id="letter"></section>

    <p style="color:#c8c8e9;font-size:12px;margin-top:25px">
      Made with ♥ just for you
    </p>

  </main>
</div>

<script>
// ===== BẦU TRỜI SAO LẤP LÁNH =====
const canvas = document.getElementById("sky");
const ctx = canvas.getContext("2d");

let stars = [];

function resizeSky() {
  const dpr = Math.min(window.devicePixelRatio || 1, 2);

  canvas.width = innerWidth * dpr;
  canvas.height = innerHeight * dpr;
  canvas.style.width = innerWidth + "px";
  canvas.style.height = innerHeight + "px";

  ctx.setTransform(dpr, 0, 0, dpr, 0, 0);

  stars = Array.from(
    { length: Math.min(180, Math.floor(innerWidth / 5)) },
    () => ({
      x: Math.random() * innerWidth,
      y: Math.random() * innerHeight,
      r: Math.random() * 1.5 + .3,
      alpha: Math.random() * .7 + .2,
      speed: Math.random() * .015 + .003
    })
  );
}

function drawStars() {
  ctx.clearRect(0, 0, innerWidth, innerHeight);

  stars.forEach(s => {
    s.alpha += s.speed;

    if (s.alpha > 1 || s.alpha < .15) {
      s.speed *= -1;
    }

    ctx.beginPath();
    ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(255,240,255,${s.alpha})`;
    ctx.fill();
  });

  requestAnimationFrame(drawStars);
}

window.addEventListener("resize", resizeSky);
resizeSky();
drawStars();


// ===== LỜI TỎ TÌNH =====
const message = `Nhóc à ... 🌙💗

Chúc mừng 20/10 Nhóc nhỏ ❤️🌷

Chúc em luôn vui vẻ, xinh đẹp và gặp nhiều điều tốt đẹp trong cuộc sống. Cảm ơn em đã đến bên anh, cho anh những niềm vui và cảm giác hạnh phúc từ những điều nhỏ bé nhất.

Anh biết đôi khi mình chưa đủ tinh tế, chưa hiểu hết những điều em nghĩ, nhưng anh sẽ cố gắng để yêu thương em tốt hơn mỗi ngày. Anh mong chúng mình sẽ luôn thấu hiểu, quan tâm và cùng nhau đi qua thật nhiều ngày tháng phía trước.

Ngày hôm nay, anh chỉ muốn em biết rằng anh rất thương em, trân trọng em và thật lòng muốn có em bên cạnh thật lâu. Mong em luôn hạnh phúc, và anh cũng mong mình sẽ là một phần trong hạnh phúc ấy.

Thương em nhiều. ❤️`;

const openBtn = document.getElementById("openBtn");
const letter = document.getElementById("letter");

let opened = false;

openBtn.addEventListener("click", () => {
  if (opened) return;

  opened = true;
  openBtn.textContent = "💖 Gửi em thật nhiều yêu thương";
  letter.classList.add("show");

  let i = 0;

  const timer = setInterval(() => {
    letter.textContent = message.slice(0, i);
    i++;

    if (i > message.length) {
      clearInterval(timer);

      const sign = document.createElement("div");
      sign.className = "signature";
      sign.textContent =
        "— Người Già của em 💗";

      letter.appendChild(sign);
    }
  }, 35);

  for (let n = 0; n < 30; n++) {
    setTimeout(makeHeart, n * 100);
  }
});


// ===== TRÁI TIM BAY =====
function makeHeart() {
  const heart = document.createElement("div");

  heart.className = "heart";

  const emojis = ["💗", "💕", "💖", "✨", "🌸", "♡"];

  heart.textContent =
    emojis[Math.floor(Math.random() * emojis.length)];

  heart.style.left = Math.random() * 100 + "vw";
  heart.style.fontSize = (15 + Math.random() * 25) + "px";
  heart.style.animationDuration = (4 + Math.random() * 5) + "s";

  document.body.appendChild(heart);

  setTimeout(() => heart.remove(), 10000);
}

setInterval(() => {
  if (Math.random() > .35) makeHeart();
}, 1200);

  
// Trình duyệt chỉ phát sau khi người xem bấm nút.

<audio id="bgMusic" loop>
  <source src="Say Yes (Vietnamese Version).mp3" type="audio/mpeg">
</audio>

<button onclick="playMusic()">
  🎵 Nghe nhạc cùng Tiên
</button>

<script>
  function playMusic() {
    const music = document.getElementById("bgMusic");

    if (music.paused) {
      music.play().catch(error => {
        alert("Không phát được nhạc. Hãy kiểm tra file MP3 nhé!");
      });
    } else {
      music.pause();
    }
  }
</script>

</body>
</html>
