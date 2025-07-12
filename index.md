<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <title>鮮到味｜三星蔥 點餐頁</title>
  <style>
    body { font-family: sans-serif; padding: 20px; max-width: 480px; margin: auto; background: #f8f8f8; }
    h2 { text-align: center; color: #333; margin-bottom: 30px; }
    .item { background: white; border-radius: 10px; padding: 20px; box-shadow: 0 2px 6px rgba(0,0,0,0.1); text-align: center; }
    .name { font-size: 20px; font-weight: bold; margin-bottom: 20px; }
    .qty-controls { display: flex; justify-content: center; align-items: center; margin-bottom: 20px; }
    button { padding: 8px 14px; font-size: 18px; border: none; border-radius: 6px; margin: 0 10px; background: #ccc; cursor: pointer; }
    .qty { font-size: 18px; min-width: 40px; text-align: center; display: inline-block; }
    #lineBtn { display: block; background: #06C755; color: white; text-decoration: none; padding: 14px; border-radius: 8px; text-align: center; font-size: 18px; margin-top: 30px; }
  </style>
</head>
<body>

<h2>鮮到味｜三星蔥 點餐頁</h2>

<div class="item">
  <div class="name">🧄 三星蔥</div>
  <div class="qty-controls">
    <button onclick="changeQty(-1)">－</button>
    <span class="qty" id="qty">0</span>
    <button onclick="changeQty(1)">＋</button>
  </div>
  <a id="lineBtn" href="https://line.me/R/oaMessage/@567ncwhd/?三星蔥+1" target="_blank">✅ 送出點餐</a>
</div>

<script>
  let qty = 0;
  function changeQty(delta) {
    qty = Math.max(0, qty + delta);
    document.getElementById("qty").textContent = qty;
    updateLineLink();
  }

  function updateLineLink() {
    const base = "https://line.me/R/oaMessage/@567ncwhd/?";
    const message = qty > 0 ? `三星蔥 x${qty}` : "三星蔥+1";
    document.getElementById("lineBtn").href = base + encodeURIComponent(message);
  }
</script>

</body>
</html>
