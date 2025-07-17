<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>鮮到味 商品列表</title>
  <style>
    body { font-family: sans-serif; padding: 1rem; background: #f9f9f9; }
    h2 { border-bottom: 2px solid #ccc; padding-bottom: 0.25rem; }
    .product { display: flex; gap: 1rem; margin-bottom: 1rem; background: white; padding: 1rem; border-radius: 0.5rem; box-shadow: 0 0 5px #ddd; }
    .product img { width: 100px; height: 100px; object-fit: cover; }
    .product-info { flex: 1; }
    .price { color: #e91e63; font-weight: bold; }
    nav button { margin: 0.25rem; }
  </style>
</head>
<body>

  <h1>鮮到味 商品清單</h1>
  <nav id="category-nav"></nav>
  <section id="product-list"></section>

  <script>
    const items = [
      {
        name: "鮮到味漢堡肉20粒 / 盒 / 冷凍",
        image: "https://i.postimg.cc/PxdLJ4mc/image.jpg",
        retail: 170,
        group: 155,
        categories: ["豬肉類"]
      },
      {
        name: "正點牛肉堡10片 / 包 / 冷凍",
        image: "https://i.postimg.cc/Kjy0RC9b/image.jpg",
        retail: 225,
        group: 205,
        categories: ["海鮮類"]
      },
      {
        name: "鮮到味原味豬排1kg / 盒 / 冷凍",
        image: "https://i.postimg.cc/KjH49hdS/image.png",
        retail: 280,
        group: 255,
        categories: ["豬肉類", "熱門商品"]
      },
      {
        name: "東芳全肉火腿3kg / 條 / 冷凍",
        image: "https://i.postimg.cc/XY21QHvK/image.jpg",
        retail: 835,
        group: 765,
        categories: ["豬肉類"]
      },
      {
        name: "東芳熱狗9mm/100入 / 包 / 冷凍",
        image: "https://i.postimg.cc/W4GFsKJg/image.jpg",
        retail: 335,
        group: 305,
        categories: ["豬肉類"]
      },
      {
        name: "東芳培根0.6kg / 包 / 冷凍",
        image: "https://i.postimg.cc/pTvj8xts/image.jpg",
        retail: 235,
        group: 215,
        categories: ["豬肉類"]
      },
      {
        name: "鮮蝦排10片 / 包 / 冷凍",
        image: "https://i.postimg.cc/26H56fjb/鮮蝦.jpg",
        retail: 165,
        group: 150,
        categories: ["海鮮類"]
      },
      {
        name: "雞腿排1kg / 包 / 冷凍",
        image: "https://i.postimg.cc/SKdSTpMT/雞腿排1.jpg",
        retail: 325,
        group: 295,
        categories: ["雞肉類"]
      },
      {
        name: "紐奧良雞腿排10入 / 包 / 冷凍",
        image: "https://i.postimg.cc/VvLbGRvM/image.png",
        retail: 250,
        group: 235,
        categories: ["雞肉類", "熱門商品"]
      },
      {
        name: "蔥酥餅10片 / 包 / 冷凍",
        image: "https://i.postimg.cc/KjzRr8pD/image.jpg",
        retail: 115,
        group: 105,
        categories: ["餅.pizza.麵包", "熱門商品"]
      },
      {
        name: "蘿蔔糕18片 / 包 / 冷藏",
        image: "https://i.postimg.cc/SR2mx2t3/image.jpg",
        retail: 215,
        group: 205,
        categories: ["熱門商品"]
      },
      {
        name: "(口栓)鮮到味豆漿2500ml / 包 / 冷藏",
        image: "https://i.postimg.cc/hth1PSSx/image.jpg",
        retail: 80,
        group: 69,
        categories: ["飲品", "熱門商品"]
      },
      {
        name: "黑胡椒醬140G(含麵) / 包 / 冷藏",
        image: "https://i.postimg.cc/Dy0X1Bt3/黑胡椒.jpg",
        retail: 22,
        group: 25,
        categories: ["鐵板麵", "熱門商品"]
      }
    ];

    // 抓出所有分類
    const categories = Array.from(
      new Set(items.flatMap(item => item.categories))
    );

    const nav = document.getElementById("category-nav");
    const list = document.getElementById("product-list");

    function showCategory(cat) {
      list.innerHTML = "";
      const filtered = items.filter(i => i.categories.includes(cat));
      filtered.forEach(item => {
        const el = document.createElement("div");
        el.className = "product";
        el.innerHTML = `
          <img src="${item.image || 'https://via.placeholder.com/100'}" alt="${item.name}" />
          <div class="product-info">
            <div>${item.name}</div>
            <div class="price">團購價：${item.group} 元<br/>原價：${item.retail} 元</div>
          </div>
        `;
        list.appendChild(el);
      });
    }

    categories.forEach(cat => {
      const btn = document.createElement("button");
      btn.textContent = cat;
      btn.onclick = () => showCategory(cat);
      nav.appendChild(btn);
    });

    // 預設顯示第一分類
    showCategory(categories[0]);
  </script>
</body>
</html>
