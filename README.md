# taichung-travel
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>台中旅遊導覽</title>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Serif+TC:wght@400;700;900&family=Noto+Sans+TC:wght@300;400;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --gold: #c9a84c;
      --dark: #1a1a2e;
      --mid: #16213e;
      --accent: #e94560;
      --light: #f5f0e8;
      --cream: #fdf6e3;
    }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: 'Noto Sans TC', sans-serif; background: var(--cream); color: var(--dark); overflow-x: hidden; }

    .hero {
      min-height: 100vh;
      background: linear-gradient(135deg, var(--dark) 0%, var(--mid) 50%, #0f3460 100%);
      display: flex; flex-direction: column; align-items: center; justify-content: center;
      text-align: center; position: relative; overflow: hidden;
    }
    .hero::before {
      content: ''; position: absolute; inset: 0;
      background: radial-gradient(ellipse at 20% 50%, rgba(201,168,76,0.15) 0%, transparent 60%),
                  radial-gradient(ellipse at 80% 20%, rgba(233,69,96,0.1) 0%, transparent 50%);
    }
    .hero-deco {
      position: absolute; font-size: 20rem; font-family: 'Noto Serif TC', serif; font-weight: 900;
      color: rgba(201,168,76,0.04); top: 50%; left: 50%; transform: translate(-50%,-50%);
      white-space: nowrap; pointer-events: none; user-select: none;
    }
    .hero-tag { font-size:.75rem; letter-spacing:.4em; color:var(--gold); text-transform:uppercase; margin-bottom:1.5rem; opacity:0; animation:fadeUp .8s ease .2s forwards; position:relative; }
    .hero h1 { font-family:'Noto Serif TC',serif; font-size:clamp(2rem,6vw,4.5rem); font-weight:900; color:var(--light); line-height:1.3; max-width:800px; padding:0 2rem; opacity:0; animation:fadeUp .8s ease .4s forwards; position:relative; }
    .hero h1 span { color:var(--gold); }
    .hero-sub { margin-top:1.5rem; font-size:1rem; color:rgba(245,240,232,0.6); letter-spacing:.1em; opacity:0; animation:fadeUp .8s ease .6s forwards; position:relative; }
    .hero-line { width:60px; height:2px; background:var(--gold); margin:2rem auto; opacity:0; animation:fadeUp .8s ease .8s forwards; position:relative; }
    nav { display:flex; gap:1rem; flex-wrap:wrap; justify-content:center; padding:0 2rem; opacity:0; animation:fadeUp .8s ease 1s forwards; position:relative; }
    nav button { background:transparent; border:1px solid rgba(201,168,76,0.5); color:var(--gold); padding:.65rem 1.6rem; font-family:'Noto Sans TC',sans-serif; font-size:.9rem; letter-spacing:.1em; cursor:pointer; transition:all .3s ease; position:relative; overflow:hidden; }
    nav button::before { content:''; position:absolute; inset:0; background:var(--gold); transform:translateX(-100%); transition:transform .3s ease; z-index:0; }
    nav button:hover::before { transform:translateX(0); }
    nav button:hover { color:var(--dark); }
    nav button span { position:relative; z-index:1; }

    section { padding:6rem 2rem; max-width:1100px; margin:0 auto; }
    .section-header { text-align:center; margin-bottom:3.5rem; }
    .section-label { font-size:.7rem; letter-spacing:.5em; color:var(--gold); text-transform:uppercase; display:block; margin-bottom:.75rem; }
    .section-title { font-family:'Noto Serif TC',serif; font-size:clamp(1.8rem,4vw,2.8rem); font-weight:700; color:var(--dark); line-height:1.3; }
    .divider { width:50px; height:2px; background:var(--accent); margin:1.2rem auto 0; }
.gallery { display:grid; grid-template-columns:repeat(auto-fill,minmax(300px,1fr)); gap:1.5rem; }
    .card { background:white; border-radius:2px; overflow:hidden; box-shadow:0 4px 20px rgba(0,0,0,0.08); transition:transform .3s ease,box-shadow .3s ease; }
    .card:hover { transform:translateY(-6px); box-shadow:0 12px 40px rgba(0,0,0,0.15); }
    .card-img { width:100%; height:220px; object-fit:cover; display:block; background:#e8e0d0; }
    .card-body { padding:1.25rem 1.5rem 1.5rem; }
    .card-tag { font-size:.65rem; letter-spacing:.3em; color:var(--gold); text-transform:uppercase; display:block; margin-bottom:.5rem; }
    .card-title { font-family:'Noto Serif TC',serif; font-size:1.15rem; font-weight:700; color:var(--dark); margin-bottom:.5rem; }
    .card-desc { font-size:.85rem; color:#666; line-height:1.7; }

    .photos-grid { display:grid; grid-template-columns:repeat(5,1fr); gap:.75rem; }
    .photo-item { aspect-ratio:3/4; border-radius:2px; overflow:hidden; position:relative; cursor:pointer; }
    .photo-item img { width:100%; height:100%; object-fit:cover; transition:transform .4s ease; display:block; }
    .photo-item:hover img { transform:scale(1.08); }
    .photo-label { position:absolute; bottom:0; left:0; right:0; padding:.75rem; background:linear-gradient(transparent,rgba(0,0,0,0.7)); color:white; font-size:.8rem; font-family:'Noto Serif TC',serif; text-align:center; }

    footer { background:var(--dark); color:rgba(245,240,232,0.5); text-align:center; padding:3rem 2rem; font-size:.85rem; letter-spacing:.1em; }
    footer .footer-title { font-family:'Noto Serif TC',serif; font-size:1.5rem; color:var(--gold); margin-bottom:.75rem; }
    .bg-alt { background:#f0ebe0; }

    @keyframes fadeUp { from{opacity:0;transform:translateY(24px)} to{opacity:1;transform:translateY(0)} }
    .reveal { opacity:0; transform:translateY(30px); transition:opacity .7s ease,transform .7s ease; }
    .reveal.visible { opacity:1; transform:none; }

    @media(max-width:600px) {
      .photos-grid { grid-template-columns:repeat(2,1fr); }
      nav { gap:.6rem; }
      nav button { padding:.55rem 1rem; font-size:.8rem; }
    }
  </style>
</head>
<body>

<div class="hero">
  <div class="hero-deco">台中</div>
  <p class="hero-tag">Taiwan · Taichung · 台灣中部</p>
  <h1>想去<span>台中</span>看山看水，<br>看一下台中城市美景，<br>去除壓力</h1>
  <div class="hero-line"></div>
  <p class="hero-sub">美食 · 建築 · 景點 · 民情風俗</p>
  <div style="height:2rem"></div>
  <nav>
    <button onclick="goTo('food')"><span>🍱 台中美食</span></button>
    <button onclick="goTo('arch')"><span>🏛 建築之美</span></button>
    <button onclick="goTo('spot')"><span>🌿 景點</span></button>
    <button onclick="goTo('culture')"><span>🎎 民情風俗</span></button>
  </nav>
</div>

<!-- 美食 -->
<div id="food" class="bg-alt">
  <section class="reveal">
    <div class="section-header">
      <span class="section-label">Taichung Cuisine</span>
      <h2 class="section-title">台中美食</h2>
      <div class="divider"></div>
    </div>
    <div class="gallery">
      <div class="card">
        <img class="card-img" src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/Taichung_Sun_Cake.jpg/640px-Taichung_Sun_Cake.jpg" alt="太陽餅" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1563245372-f21724e3856d?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">小吃</span>
          <div class="card-title">太陽餅</div>
          <div class="card-desc">台中最具代表性的名產，酥脆的餅皮搭配甜蜜麥芽糖內餡，是每位訪客必嚐的伴手禮。</div>
        </div>
      </div>
      <div class="card">
        <img class="card-img" src="https://images.unsplash.com/photo-1555396273-367ea4eb4db5?w=600&q=80" alt="夜市" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1504674900247-0877df9cc836?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">夜市</span>
          <div class="card-title">逢甲夜市</div>
          <div class="card-desc">全台知名的逢甲夜市，匯聚各式創意小吃，蚵仔煎、大雞排、珍珠奶茶，美食無極限。</div>
        </div>
      </div>
      <div class="card">
        <img class="card-img" src="https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=600&q=80" alt="珍珠奶茶" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1571091718767-18b5b1457add?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">飲品</span>
          <div class="card-title">珍珠奶茶發源地</div>
          <div class="card-desc">台中春水堂是珍珠奶茶的發源地，來台中一定要喝一杯正宗的珍珠奶茶，回味無窮。</div>
        </div>
      </div>
    </div>
  </section>
</div>

<!-- 建築 -->
<div id="arch">
  <section class="reveal">
    <div class="section-header">
      <span class="section-label">Architecture</span>
      <h2 class="section-title">建築之美</h2>
      <div class="divider"></div>
    </div>
    <div class="gallery">
      <div class="card">
        <img class="card-img" src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Taichung_City_Hall_1.jpg/640px-Taichung_City_Hall_1.jpg" alt="台中州廳" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1470082719408-b2843ab5c9ab?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">文化建築</span>
          <div class="card-title">台中州廳</div>
          <div class="card-desc">建於日治時期的台中州廳，是台灣重要的歷史建築，巴洛克式風格令人嘆為觀止。</div>
        </div>
      </div>
      <div class="card">
        <img class="card-img" src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/National_Taiwan_Museum_of_Fine_Arts_Entrance.jpg/640px-National_Taiwan_Museum_of_Fine_Arts_Entrance.jpg" alt="國立台灣美術館" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1554907984-15263bfd63bd?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">藝術空間</span>
          <div class="card-title">國立台灣美術館</div>
          <div class="card-desc">全台規模最大的美術館，典藏豐富的台灣藝術作品，是愛好藝術人士必訪之地。</div>
        </div>
      </div>
      <div class="card">
        <img class="card-img" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b3/National_Taichung_Theater_20160917.jpg/640px-National_Taichung_Theater_20160917.jpg" alt="台中歌劇院" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1493246507139-91e8fad9978e?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">現代建築</span>
          <div class="card-title">台中歌劇院</div>
          <div class="card-desc">由世界建築大師伊東豐雄設計，獨特的曲牆結構成為台中新地標，被譽為全球最美劇院之一。</div>
        </div>
      </div>
    </div>
  </section>
</div>

<!-- 景點 -->
<div id="spot" class="bg-alt">
  <section class="reveal">
    <div class="section-header">
      <span class="section-label">Attractions</span>
      <h2 class="section-title">景點</h2>
      <div class="divider"></div>
    </div>
    <div class="gallery">
      <div class="card">
        <img class="card-img" src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Wuling_Farm_2011.jpg/640px-Wuling_Farm_2011.jpg" alt="武陵農場" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1522383225653-ed111181a951?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">自然景觀</span>
          <div class="card-title">武陵農場</div>
          <div class="card-desc">春天滿開的櫻花將農場點綴成粉色夢境，是賞花與親近大自然的絕佳勝地。</div>
        </div>
      </div>
      <div class="card">
        <img class="card-img" src="https://images.unsplash.com/photo-1501854140801-50d01698950b?w=600&q=80" alt="大坑風景區" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">山岳</span>
          <div class="card-title">大坑風景區</div>
          <div class="card-desc">台中近郊的健行勝地，多條步道深入翠綠山林，俯瞰台中盆地的壯闊景色令人心曠神怡。</div>
        </div>
      </div>
      <div class="card">
        <img class="card-img" src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Gaomei_Wetlands.jpg/640px-Gaomei_Wetlands.jpg" alt="高美溼地" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1469474968028-56623f02e42e?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">濱海</span>
          <div class="card-title">高美溼地</div>
          <div class="card-desc">夕陽時分倒映在水面上的金色光芒與風力發電機，構成台中最美的日落景致之一。</div>
        </div>
      </div>
    </div>
  </section>
</div>

<!-- 民情風俗 -->
<div id="culture">
  <section class="reveal">
    <div class="section-header">
      <span class="section-label">Culture & Customs</span>
      <h2 class="section-title">民情風俗</h2>
      <div class="divider"></div>
    </div>
    <div class="gallery">
      <div class="card">
        <img class="card-img" src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Mazu_procession_2.jpg/640px-Mazu_procession_2.jpg" alt="大甲媽祖遶境" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1545569341-9eb8b30979d9?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">廟會文化</span>
          <div class="card-title">大甲媽祖遶境</div>
          <div class="card-desc">一年一度的大甲媽祖遶境進香是全球三大宗教活動之一，數十萬信眾虔誠徒步，感受震撼人心的信仰力量。</div>
        </div>
      </div>
      <div class="card">
        <img class="card-img" src="https://images.unsplash.com/photo-1604147706283-d7119b5b822c?w=600&q=80" alt="傳統工藝" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1565193566173-7a0ee3dbe261?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">傳統工藝</span>
          <div class="card-title">木雕與漆器</div>
          <div class="card-desc">台中豐原自古以木雕工藝聞名，精緻的傳統手藝代代相傳，展現台灣匠人的精神與智慧。</div>
        </div>
      </div>
      <div class="card">
        <img class="card-img" src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/Rainbow_Village%2C_Taichung%2C_Taiwan.jpg/640px-Rainbow_Village%2C_Taichung%2C_Taiwan.jpg" alt="彩虹眷村" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1492037766660-2a56f9eb3fcb?w=600&q=80'">
        <div class="card-body">
          <span class="card-tag">特色聚落</span>
          <div class="card-title">彩虹眷村</div>
          <div class="card-desc">老兵黃永阜以彩筆繪滿整個眷村，繽紛的色彩與童趣圖案讓這裡成為台中最受歡迎的打卡景點之一。</div>
        </div>
      </div>
    </div>
  </section>
</div>
