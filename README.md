# maze-survival
迷路で敵から逃げる2Dゲーム

<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>迷路サバイバル</title>
  <style>
    body {
      background: #202530;
      color: white;
      text-align: center;
      font-family: sans-serif;
    }

    canvas {
      background: #dce8c8;
      border: 3px solid white;
      max-width: 100%;
      touch-action: none;
    }

    button {
      font-size: 24px;
      min-width: 60px;
      min-height: 48px;
      margin: 3px;
    }
  </style>
</head>
<body>
  <h1>迷路サバイバル</h1>
  <p>矢印ボタンで移動しよう！</p>

  <canvas id="game" width="320" height="400"></canvas>

  <div>
    <button onclick="move(0,-10)">↑</button>
    <br>
    <button onclick="move(-10,0)">←</button>
    <button onclick="move(0,10)">↓</button>
    <button onclick="move(10,0)">→</button>
  </div>

  <script>
    // ゲーム画面を取得する
    const canvas = document.getElementById("game");
    const ctx = canvas.getContext("2d");

    // プレイヤーの位置と大きさ
    const player = {
      x: 40,
      y: 40,
      size: 16
    };

    // ゲーム画面を描く
    function draw() {
      ctx.clearRect(
        0, 0, canvas.width, canvas.height
      );

      // プレイヤーを緑色の四角で描く
      ctx.fillStyle = "green";
      ctx.fillRect(
        player.x,
        player.y,
        player.size,
        player.size
      );
    }

    // プレイヤーを移動させる
    function move(dx, dy) {
      player.x += dx;
      player.y += dy;

      // 画面の外に出ないようにする
      player.x = Math.max(
        0,
        Math.min(
          canvas.width - player.size,
          player.x
        )
      );

      player.y = Math.max(
        0,
        Math.min(
          canvas.height - player.size,
          player.y
        )
      );

      draw();
    }

    // 最初の画面を表示

