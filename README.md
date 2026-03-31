# taichung-travel
index.html

<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>台中夢幻之旅</title>

<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+TC:wght@400;700;900&family=Noto+Sans+TC:wght@300;400;700&display=swap" rel="stylesheet">

<style>
body{margin:0;font-family:'Noto Sans TC';background:#fdf6e3;}
.hero{
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  background:linear-gradient(135deg,#1a1a2e,#16213e);
  color:white;
  text-align:center;
}
nav button{
  margin:10px;
  padding:10px 20px;
  background:#c9a84c;
  border:none;
  cursor:pointer;
  color:white;
}
section{padding:60px;}
.gallery{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:20px;
}
.card img{width:100%;height:200px;object-fit:cover;}
</style>
</head>

<body>

<div class="hero">
<h1>台中夢幻之旅</h1>
<p>美食 · 建築 · 景點 · 民俗文化</p>

<nav>
<button onclick="goTo('food')">美食</button>
<button onclick="goTo('arch')">建築</button>
<button onclick="goTo('spot')">景點</button>
<button onclick="goTo('culture')">文化</button>
</nav>
</div>

<!-- 美食 -->
<section id="food">
<h2>台中美食</h2>
<div class="gallery">

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/8/87/Taichung_Sun_Cake.jpg">
<p>太陽餅（台中特產）</p>
</div>

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/5/52/Fengjia_Night_Market.jpg">
<p>逢甲夜市</p>
</div>

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/3/3a/Bubble_Tea_Taiwan.jpg">
<p>珍珠奶茶（台灣發源）</p>
</div>

</div>
</section>

<!-- 建築 -->
<section id="arch">
<h2>建築之美</h2>
<div class="gallery">

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/5/52/National_Taichung_Theater_20160917.jpg">
<p>台中歌劇院</p>
</div>

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/6/6e/National_Museum_of_Fine_Arts_Taichung.jpg">
<p>國美館</p>
</div>

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/0/0d/Taichung_City_Hall.jpg">
<p>台中市政府</p>
</div>

</div>
</section>

<!-- 景點 -->
<section id="spot">
<h2>景點</h2>
<div class="gallery">

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/d/d4/Wuling_Farm_2011.jpg">
<p>武陵農場</p>
</div>

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/1/19/Gaomei_Wetlands.jpg">
<p>高美濕地</p>
</div>

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/a/a7/Rainbow_Village%2C_Taichung%2C_Taiwan.jpg">
<p>彩虹眷村</p>
</div>

</div>
</section>

<!-- 文化 -->
<section id="culture">
<h2>民俗文化</h2>
<div class="gallery">

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/6/6e/Mazu_procession_2.jpg">
<p>大甲媽祖遶境</p>
</div>

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/2/2c/Wood_carving_Taiwan.jpg">
<p>豐原木雕工藝</p>
</div>

<div class="card">
<img src="https://upload.wikimedia.org/wikipedia/commons/a/a7/Rainbow_Village%2C_Taichung%2C_Taiwan.jpg">
<p>彩虹眷村文化</p>
</div>

</div>
</section>

<script>
function goTo(id){
  document.getElementById(id).scrollIntoView({behavior:"smooth"});
}
</script>

</body>
</html>
