<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <title>鮮到味 點餐頁</title>
  <style>
    body { font-family: sans-serif; padding: 20px; max-width: 500px; margin: auto; }
    .item { margin-bottom: 16px; padding: 10px; border: 1px solid #ccc; border-radius: 8px; }
    .name { font-weight: bold; margin-bottom: 8px; }
    button { padding: 4px 10px; margin: 0 6px; }
  </style>
</head>
<body>
  <h2>鮮到味 點餐頁</h2>

  <div class="item">
    <div class="name">🐷 原肉豬排 – $255</div>
    <button onclick="changeQty('原肉豬排', -1)">－</button>
    <span id="qty-原肉豬排">0</span>
    <button onclick="changeQty('原肉豬排', 1)">＋</button>
  </div>

  <div class="item">
    <div class="name">🧋 非基改豆漿 – $69</div>
    <button onclick="changeQty('非基改豆漿', -1)">－</button>
    <span id="qty-非基改豆漿">0</span>
    <button onclick="changeQty('非基改豆漿', 1)">＋</button>
  </div>

  <div style="margin-top: 30px; text-align: center;">
    <a id="lineBtn" href="#" target="_blank"
       style="padding: 10px 20px; background: #06C755; color: white; text-decoration: none; border-radius: 6px;">
       ✅ 送出點餐
    </a>
  </div>

  <script>
    const cart = { '原肉豬排': 0, '非基改豆漿': 0 };
    function changeQty(name, delta) {
      cart[name] = Math.max(0, cart[name] + delta);
      document.getElementById('qty-' + name).textContent = cart[name];
      updateLineLink();
    }

    function updateLineLink() {
      let msg = '📦 鮮到味 訂單%0A';
      for (const [item, qty] of Object.entries(cart)) {
        if (qty > 0) msg += `🐾 ${item} x${qty}%0A`;
      }
      const url = 'https://line.me/R/oaMessage/@567ncwhd/?' + msg;
      document.getElementById('lineBtn').href = url;
    }
  </script>
</body>
</html>