
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>鮮到味 點餐頁</title>
  <style>
    body {
      font-family: sans-serif;
      padding: 20px;
      max-width: 500px;
      margin: auto;
    }
    .item {
      margin-bottom: 16px;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
    .name {
      font-weight: bold;
      margin-bottom: 8px;
    }
    button {
      padding: 4px 10px;
      margin: 0 6px;
    }
    .qty {
      display: inline-block;
      width: 20px;
      text-align: center;
    }
    #lineBtn {
      display: inline-block;
      margin-top: 20px;
      background: #06c755;
      color: white;
      padding: 10px 20px;
      text-decoration: none;
      border-radius: 6px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h2>鮮到味 點餐頁</h2>

  <div class="item">
    <div class="name">🐷 原肉豬排 – $255</div>
    <button onclick="changeQty('原肉豬排', -1)">－</button>
    <span id="qty-原肉豬排" class="qty">0</span>
    <button onclick="changeQty('原肉豬排', 1)">＋</button>
  </div>

  <div class="item">
    <div class="name">🧋 非基改豆漿 – $69</div>
    <button onclick="changeQty('非基改豆漿', -1)">－</button>
    <span id="qty-非基改豆漿" class="qty">0</span>
    <button onclick="changeQty('非基改豆漿', 1)">＋</button>
  </div>

  <a id="lineBtn" href="#" target="_blank">✅ 送出點餐</a>

  <script>
    const cart = {
      '原肉豬排': 0,
      '非基改豆漿': 0
    };

    function changeQty(name, delta) {
      cart[name] = Math.max(0, cart[name] + delta);
      document.getElementById('qty-' + name).textContent = cart[name];
      updateLineLink();
    }

    function updateLineLink() {
      let msg = '📦 鮮到味 訂單\n';
      for (const [item, qty] of Object.entries(cart)) {
        if (qty > 0) {
          msg += `🐾 ${item} x${qty}\n`;
        }
      }

      const encoded = encodeURIComponent(msg);
      const url = 'https://line.me/R/oaMessage/@567ncwhd/?' + encoded;
      document.getElementById('lineBtn').href = url;
    }

    updateLineLink(); // 初始化
  </script>
</body>
</html>
