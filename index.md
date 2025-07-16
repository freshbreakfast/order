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
    .retail {
      text-decoration: line-through;
      color: #999;
      margin: 0 6px;
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
      border: none;
      border-radius: 6px;
      font-weight: bold;
      font-size: 1.1em;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h2>鮮到味 點餐頁</h2>

  <!-- 商品清單 -->
  <div class="item">
    <div class="name">鮮到味漢堡肉20粒</div>
    <img src="https://i.postimg.cc/Kzdtxd97/image.jpg" />
    <div class="price">
      原價：<span class="retail">$199</span> 💰 團購價：$155
    </div>
    <button onclick="changeQty('鮮到味漢堡肉20粒', -1)">－</button>
    <span class="qty" id="qty-鮮到味漢堡肉20粒">0</span>
    <button onclick="changeQty('鮮到味漢堡肉20粒', 1)">＋</button>
  </div>

  <div class="item">
    <div class="name">正點牛肉堡10片</div>
    <img src="https://i.postimg.cc/s2sh6jth/image.jpg" />
    <div class="price">
      原價：<span class="retail">$249</span> 💰 團購價：$205
    </div>
    <button onclick="changeQty('正點牛肉堡10片', -1)">－</button>
    <span class="qty" id="qty-正點牛肉堡10片">0</span>
    <button onclick="changeQty('正點牛肉堡10片', 1)">＋</button>
  </div>

  <!-- 送出按鈕 -->
  <button id="lineBtn" onclick="sendToLine()">✅ 送出點餐</button>

  <!-- JavaScript 功能區 -->
  <script>
    const cart = {
      '鮮到味漢堡肉20粒': 0,
      '正點牛肉堡10片': 0,
    };

    function changeQty(name, delta) {
      cart[name] = Math.max(0, cart[name] + delta);
      document.getElementById('qty-' + name).textContent = cart[name];
    }

    function sendToLine() {
      let msg = '📦 鮮到味 訂單\n';
      const space = '\u3000\u3000'; // 兩個全形空格
      for (const [item, qty] of Object.entries(cart)) {
        if (qty > 0) {
          msg += `${item}${space}x${qty}\n`;  // 沒有價格、沒有圖案
        }
      }
      if (msg === '📦 鮮到味 訂單\n') {
        msg = '您尚未選擇任何品項喔～';
      }
      const encodedMsg = encodeURIComponent(msg);
      const lineUrl = `https://line.me/R/oaMessage/@567ncwhd/?text=${encodedMsg}`;
      scrollToTop();
      window.open(lineUrl, '_blank');
    }

    function scrollToTop() {
      setTimeout(() => window.scrollTo({ top: 0, behavior: 'smooth' }), 500);
    }
  </script>
</body>
</html>
 
 
  
