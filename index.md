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
    select {
      margin-bottom: 20px;
      padding: 6px 12px;
      font-size: 1em;
    }
  </style>
</head>
<body>
  <h2>鮮到味 點餐頁</h2>

  <!-- 分類下拉選單 -->
  <label for="filter">📂 篩選分類：</label>
  <select id="filter" onchange="filterItems()">
    <option value="all">全部</option>
    <option value="豬肉">🐷 豬肉</option>
    <option value="海鮮">🦐 海鮮</option>
  </select>

  <!-- 商品清單（加上 data-category 屬性） -->
  <div class="item" data-category="豬肉">
    <div class="name">鮮到味漢堡肉20粒</div>
    <img src="https://drive.google.com/uc?export=view&id=1vo2WVLHm1wv4pUuqu2FabZ2HUiZvX_Qz" />
    <div class="price">💰 團購價：$155</div>
    <button onclick="changeQty('鮮到味漢堡肉20粒', -1)">－</button>
    <span class="qty" id="qty-鮮到味漢堡肉20粒">0</span>
    <button onclick="changeQty('鮮到味漢堡肉20粒', 1)">＋</button>
  </div>

  <div class="item" data-category="豬肉">
    <div class="name">正點牛肉堡10片</div>
    <img src="https://drive.google.com/uc?export=view&id=1xvT4WZvi9szVVOBHZIM_tlGk1ZTo7CKr" />
    <div class="price">💰 團購價：$205</div>
    <button onclick="changeQty('正點牛肉堡10片', -1)">－</button>
    <span class="qty" id="qty-正點牛肉堡10片">0</span>
    <button onclick="changeQty('正點牛肉堡10片', 1)">＋</button>
  </div>

  <div class="item" data-category="海鮮">
    <div class="name">鮮蝦排10片</div>
    <img src="https://drive.google.com/uc?export=view&id=1s068nkEHIfJ3LT7KiaLQTqVLVDGUYHJe" />
    <div class="price">💰 團購價：$150</div>
    <button onclick="changeQty('鮮蝦排10片', -1)">－</button>
    <span class="qty" id="qty-鮮蝦排10片">0</span>
    <button onclick="changeQty('鮮蝦排10片', 1)">＋</button>
  </div>

  <!-- 更多商品照這樣複製，分類只要改 data-category 即可 -->

  <a id="lineBtn" target="_blank" onclick="scrollToTop()">✅ 送出點餐</a>

  <script>
    const cart = {
      '鮮到味漢堡肉20粒': 0,
      '正點牛肉堡10片': 0,
      '鮮蝦排10片': 0
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

    function filterItems() {
      const selected = document.getElementById('filter').value;
      const items = document.querySelectorAll('.item');
      items.forEach(item => {
        const category = item.getAttribute('data-category');
        item.style.display = (selected === 'all' || category === selected) ? 'block' : 'none';
      });
    }

    function scrollToTop() {
      setTimeout(() => window.scrollTo({ top: 0, behavior: 'smooth' }), 500);
    }

    updateLineLink();
  </script>
</body>
</html>
