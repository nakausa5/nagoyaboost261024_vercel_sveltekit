
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>忍者ジャンプ！</title>
<style>
  * { box-sizing: border-box; }
  body {
    margin: 0;
    background: #10182d;
    color: white;
    font-family: sans-serif;
    text-align: center;
    user-select: none;
  }
  h1 { color: #ffd34e; margin: 18px 0 5px; }
  p { margin: 8px; color: #d6e1ff; }
  #game {
    display: block;
    width: min(95vw, 800px);
    height: auto;
    margin: 15px auto;
    border: 3px solid #53658c;
    border-radius: 12px;
    background: #17284c;
  }
  #status { font-size: 20px; color: #ffd34e; }
  button {
    border: 0;
    border-radius: 12px;
    padding: 13px 20px;
    margin: 5px;
    background: #ffd34e;
    color: #18213b;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
    touch-action: manipulation;
  }
  .controls button { min-width: 65px; font-size: 25px; }
  #message { font-size: 20px; font-weight: bold; }
</style>
</head>
<body>

<h1>🥷 忍者ジャンプ！</h1>
<p>コインを集めて、トゲをよけろ！</p>

<div id="status">スコア：0　🏆 ベスト：0</div>

<canvas id="game" width="800" height="450"></canvas>

<div id="message">スタートボタンを押してね！</div>
<button onclick="startGame()">▶ スタート / もう一度</button>

<p>← → 移動　｜　↑ または スペース：ジャンプ</p>

<div class="controls">
  <button id="left">⬅️</button>
  <button id="jump">⬆️</button>
  <button id="right">➡️</button>
</div>

<script>
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");
const W = canvas.width;
const H = canvas.height;
const ground = 380;

let player, obstacles, coins, score, speed, frame;
let running = false;
let gameOver = false;
let best = 0;
let keys = {};
let jumpPressed = false;

function startGame() {
  player = {
    x: 100, y: ground - 44,
    w: 34, h: 44,
    vx: 0, vy: 0, onGround: true
  };
  obstacles = [];
  coins = [];
  score = 0;
  speed = 4;
  frame = 0;
  running = true;
  gameOver = false;
  jumpPressed = false;
  keys = {};
  document.getElementById("message").textContent =
    "いけ！忍者！コインを集めよう！";
  requestAnimationFrame(loop);
}

function jump() {
  if (running && player.onGround) {
    player.vy = -13;
    player.onGround = false;
  }
}

function hit(a, b) {
  return a.x < b.x + b.w &&
         a.x + a.w > b.x &&
         a.y < b.y + b.h &&
         a.y + a.h > b.y;
}

function spawnItems() {
  if (frame % 85 === 0) {
    obstacles.push({
      x: W + 20, y: ground - 35,
      w: 30, h: 35
    });
  }

  if (frame % 55 === 0) {
    let baseY = ground - 90 - Math.random() * 100;
    for (let i = 0; i < 3; i++) {
      coins.push({
        x: W + 20 + i * 35,
        y: baseY,
        r: 11,
        taken: false
      });
    }
  }
}

function drawBackground() {
  const sky = ctx.createLinearGradient(0, 0, 0, H);
  sky.addColorStop(0, "#17284c");
  sky.addColorStop(1, "#456b89");
  ctx.fillStyle = sky;
  ctx.fillRect(0, 0, W, H);

  // 星
  ctx.fillStyle = "#ffffff";
  for (let i = 0; i < 35; i++) {
    const x = (i * 137 + 30) % W;
    const y = (i * 67 + 20) % 240;
    ctx.fillRect(x, y, 3, 3);
  }

  // 月
  ctx.fillStyle = "#fff1ad";
  ctx.beginPath();
  ctx.arc(680, 75, 32, 0, Math.PI * 2);
  ctx.fill();

  // 山
  ctx.fillStyle = "#243d59";
  ctx.beginPath();
  ctx.moveTo(0, ground);
  ctx.lineTo(120, 190);
  ctx.lineTo(230, ground);
  ctx.lineTo(390, 230);
  ctx.lineTo(550, ground);
  ctx.lineTo(690, 200);
  ctx.lineTo(800, ground);
  ctx.fill();

  // 地面
  ctx.fillStyle = "#284d39";
  ctx.fillRect(0, ground, W, H - ground);
  ctx.fillStyle = "#6ac46c";
  ctx.fillRect(0, ground, W, 8);

  ctx.fillStyle = "#46744b";
  for (let i = 0; i < W; i += 45) {
    let x = (i - frame * speed * 0.5 % 45 + 45) % W;
    ctx.fillRect(x, ground + 25, 20, 5);
  }
}

function drawPlayer() {
  // 体
  ctx.fillStyle = "#ed3e52";
  ctx.fillRect(player.x, player.y + 12, player.w, 29);

  // 顔
  ctx.fillStyle = "#ffd4a3";
  ctx.fillRect(player.x + 5, player.y + 3, 25, 21);

  // 忍者の頭巾
  ctx.fillStyle = "#b51f38";
  ctx.fillRect(player.x + 2, player.y, 31, 12);

  // 目
  ctx.fillStyle = "#20233a";
  ctx.fillRect(player.x + 9, player.y + 12, 5, 4);
  ctx.fillRect(player.x + 23, player.y + 12, 5, 4);

  // 足
  ctx.fillStyle = "#20233a";
  ctx.fillRect(player.x + 3, player.y + 38, 12, 6);
  ctx.fillRect(player.x + 21, player.y + 38, 12, 6);

  // マフラー
  ctx.fillStyle = "#ffcf43";
  ctx.fillRect(player.x - 8, player.y + 13, 12, 6);
}

function drawObstacle(o) {
  ctx.fillStyle = "#cbd5e1";
  ctx.beginPath();
  ctx.moveTo(o.x, o.y + o.h);
  ctx.lineTo(o.x + o.w / 2, o.y);
  ctx.lineTo(o.x + o.w, o.y + o.h);
  ctx.closePath();
  ctx.fill();

  ctx.strokeStyle = "#7c8ba3";
  ctx.lineWidth = 3;
  ctx.stroke();
}

function drawCoin(c) {
  ctx.fillStyle = "#ffcf32";
  ctx.beginPath();
  ctx.arc(c.x, c.y, c.r, 0, Math.PI * 2);
  ctx.fill();

  ctx.strokeStyle = "#fff3a1";
  ctx.lineWidth = 3;
  ctx.stroke();

  ctx.fillStyle = "#9b6710";
  ctx.font = "bold 15px sans-serif";
  ctx.textAlign = "center";
  ctx.fillText("¥", c.x, c.y + 5);
}

function loop() {
  if (!running) return;

  frame++;
  drawBackground();

  // 移動
  player.vx = 0;
  if (keys.ArrowLeft) player.vx = -5;
  if (keys.ArrowRight) player.vx = 5;

  player.x += player.vx;
  player.x = Math.max(0, Math.min(W - player.w, player.x));

  // ジャンプと重力
  player.vy += 0.65;
  player.y += player.vy;

  if (player.y + player.h >= ground) {
    player.y = ground - player.h;
    player.vy = 0;
    player.onGround = true;
  }

  // アイテム生成
  spawnItems();

  // トゲ
  for (const o of obstacles) {
    o.x -= speed;
    drawObstacle(o);

    if (hit(player, o)) {
      running = false;
      gameOver = true;
    }
  }
  obstacles = obstacles.filter(o => o.x + o.w > 0);

  // コイン
  for (const c of coins) {
    c.x -= speed;
    if (!c.taken) {
      drawCoin(c);
      const box = {
        x: c.x - c.r, y: c.y - c.r,
        w: c.r * 2, h: c.r * 2
      };
      if (hit(player, box)) {
        c.taken = true;
        score += 10;
        speed = Math.min(8, 4 + score / 200);
      }
    }
  }
  coins = coins.filter(c => c.x + c.r > 0 && !c.taken);

  drawPlayer();

  // スコア表示
  ctx.fillStyle = "white";
  ctx.font = "bold 22px sans-serif";
  ctx.textAlign = "left";
  ctx.fillText("🪙 " + score, 20, 35);

  document.getElementById("status").textContent =
    "スコア：" + score + "　🏆 ベスト：" + best;

  if (gameOver) {
    best = Math.max(best, score);
    document.getElementById("status").textContent =
      "スコア：" + score + "　🏆 ベスト：" + best;
    document.getElementById("message").textContent =
      "💥 ゲームオーバー！ スコア：" + score;
    ctx.fillStyle = "rgba(0,0,0,0.65)";
    ctx.fillRect(0, 0, W, H);
    ctx.fillStyle = "#ffdf58";
    ctx.textAlign = "center";
    ctx.font = "bold 46px sans-serif";
    ctx.fillText("GAME OVER!", W / 2, H / 2 - 10);
    ctx.font = "24px sans-serif";
    ctx.fillText("スタートでもう一度！", W / 2, H / 2 + 35);
    return;
  }

  requestAnimationFrame(loop);
}

// キーボード操作
document.addEventListener("keydown", e => {
  if (["ArrowLeft", "ArrowRight", "ArrowUp", " "].includes(e.key)) {
    e.preventDefault();
  }

  keys[e.key] = true;

  if ((e.key === "ArrowUp" || e.key === " ") &&
      !jumpPressed) {
    jump();
    jumpPressed = true;
  }
});

document.addEventListener("keyup", e => {
  keys[e.key] = false;
  if (e.key === "ArrowUp" || e.key === " ") {
    jumpPressed = false;
  }
});

// スマホ用ボタン
function holdButton(id, key) {
  const btn = document.getElementById(id);

  btn.addEventListener("pointerdown", e => {
    e.preventDefault();
    keys[key] = true;
    if (key === "ArrowUp") jump();
  });

  for (const eventName of ["pointerup", "pointercancel", "pointerleave"]) {
    btn.addEventListener(eventName, () => {
      keys[key] = false;
    });
  }
}

holdButton("left", "ArrowLeft");
holdButton("right", "ArrowRight");
holdButton("jump", "ArrowUp");

// 最初の画面
drawBackground();
ctx.fillStyle = "white";
ctx.textAlign = "center";
ctx.font = "bold 32px sans-serif";
ctx.fillText("忍者の冒険へようこそ！", W / 2, 190);
ctx.font = "22px sans-serif";
ctx.fillText("スタートを押してね！", W / 2, 235);
</script>
</body>
</html>
