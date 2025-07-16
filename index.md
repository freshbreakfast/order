<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <title>鮮到味 點餐頁</title>
  <style>
    body {
      font-family: sans-serif;
      padding: 20px;
      max-width: 700px;
      margin: auto;
    }
    .item {
      margin-bottom: 24px;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 10px;
    }
    .item img {
      max-width: 100%;
      border-radius: 6px;
      margin: 10px 0;
    }
    .name {
      font-weight: bold;
      font-size: 1.1em;
    }
    .price {
      color: #444;
      margin-bottom: 8px;
    }
    button {
      padding: 4px 10px;
      margin: 0 6px;
    }
    .qty {
      display: inline-block;
      width: 30px;
      text-align: center;
    }
    #lineBtn {
      display: inline-block;
      margin-top: 20px;
      background: #06c755;
      color: white;
      padding: 12px 24px;
      text-decoration: none;
      border-radius: 6px;
      font-weight: bold;
      font-size: 1.1em;
    }
  </style>
</head>
<body>
  <h2>鮮到味 點餐頁</h2>

  <!-- 商品清單 -->
  <div class="item">
    <div class="name">鮮到味漢堡肉20粒</div>
    <img src="https://drive.google.com/uc?export=view&id=1vo2WVLHm1wv4pUuqu2FabZ2HUiZvX_Qz" />
    <div class="price">💰 團購價：$155</div>
    <button onclick="changeQty('鮮到味漢堡肉20粒', -1)">－</button>
    <span class="qty" id="qty-鮮到味漢堡肉20粒">0</span>
    <button onclick="changeQty('鮮到味漢堡肉20粒', 1)">＋</button>
  </div>

<div class="item">
    <div class="name">正點牛肉堡10片</div>
    <img src="https://drive.google.com/file/d/1xvT4WZvi9szVVOBHZIM_tlGk1ZTo7CKr" />
    <div class="price">💰 團購價：$205</div>
    <button onclick="changeQty('正點牛肉堡10片', -1)">－</button>
    <span class="qty" id="qty-正點牛肉堡10片">0</span>
    <button onclick="changeQty('正點牛肉堡10片', 1)">＋</button>
  </div>
 
  <!-- 送出按鈕 -->
  <a id="lineBtn" target="_blank" onclick="scrollToTop()">✅ 送出點餐</a>

  <!-- JavaScript 功能區 -->
  <script>
    const cart = {
      '鮮到味漢堡肉20粒': 0,
      '正點牛肉堡10片': 0,
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
      if (msg === '📦 鮮到味 訂單\n') {
        msg = '您尚未選擇任何品項喔～';
      }
      const encodedMsg = encodeURIComponent(msg);
      const lineUrl = `https://line.me/R/oaMessage/@567ncwhd/?text=${encodedMsg}`;
      document.getElementById('lineBtn').href = lineUrl;
    }

    function scrollToTop() {
      setTimeout(() => window.scrollTo({ top: 0, behavior: 'smooth' }), 500);
    }

    updateLineLink();
  </script>
</body>
</html>
