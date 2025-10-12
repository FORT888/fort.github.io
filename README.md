<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>聯信資財富導航</title>
<style>
body {
  font-family:"PingFang SC","Microsoft YaHei",sans-serif;
  background-color:#0d1117;
  margin:0;
  padding:0;
  color:#eaf5ff;
  transform:translateY(-10px); /* 整页上移一点 */
}

/* 顶部 */
.top-background {
  background: radial-gradient(circle at 50% 30%, rgba(56,189,248,0.12), transparent 70%), #0d1117;
  height: 230px; /* 稍微降低一点，让 LOGO 贴近标题 */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  padding-top: 5px;
  overflow: hidden;
  position: relative;
}

/* 滚动标题 */
.scroll-container { width:100%; height:40px; overflow:hidden; }
.scroll-title {
  font-size:28px;
  font-weight:700;
  background:linear-gradient(to right,#6ee7ff,#2ea3f0);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  white-space:nowrap;
  position:absolute;
  animation:scrollText 10s linear infinite;
}
@keyframes scrollText { 0%{transform:translateX(100%);} 100%{transform:translateX(-100%);} }

/* LOGO + 动态星星 */
.logo {
  position: relative;
  margin-top: 45px; /* LOGO上移贴近标题 */
  width: 160px;
  height: 160px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo img {
  width:150px;
  height:auto;
  mix-blend-mode:screen;
  z-index:2;
}

/* 星点柔光 */
.star {
  position:absolute;
  background:radial-gradient(circle, rgba(255,255,255,0.9), transparent 70%);
  border-radius:50%;
  opacity:0.8;
  animation:twinkle 4s ease-in-out infinite;
  z-index:1;
}
.star:nth-child(1){width:6px;height:6px;top:20%;left:60%;animation-delay:0s;}
.star:nth-child(2){width:4px;height:4px;top:60%;left:30%;animation-delay:1s;}
.star:nth-child(3){width:5px;height:5px;top:40%;left:75%;animation-delay:2s;}
.star:nth-child(4){width:3px;height:3px;top:70%;left:50%;animation-delay:3s;}
@keyframes twinkle {
  0%,100%{opacity:0.3;transform:scale(1);}
  50%{opacity:1;transform:scale(1.4);}
}

/* 导航栏 */
.tab {
  display:flex;
  justify-content:center;
  flex-wrap:wrap;
  gap:10px;
  margin:15px 10px; /* 整体稍上移 */
}
.tab button {
  padding:8px 15px;
  border:1px solid rgba(255,255,255,0.08);
  border-radius:25px;
  background:transparent;
  color:#eaf5ff;
  font-weight:500;
  font-size:14px;
  cursor:pointer;
  transition:all 0.3s ease;
}
.tab button:hover { color:#39bdf8; }
.tab button.active {
  background:linear-gradient(135deg,#2ea3f0,#0277bd);
  color:#fff;
  border:none;
  box-shadow:0 0 8px rgba(14,165,233,0.4);
}

/* 内容区 */
.tab-content { display:none; }
.tab-content.active { display:block; }
.nav-section {
  background-color:#161b22;
  border-radius:10px;
  margin:14px;
  padding:22px 14px 28px;
  box-shadow:0 4px 25px rgba(0,0,0,0.45);
}
.nav-section h2 {
  font-size:19px;
  font-weight:700;
  background:linear-gradient(to right,#9be5ff,#47a8ff);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  text-align:center;
  margin-bottom:18px;
}

/* 动态箭头按钮 */
.btn-group { display:flex; flex-direction:column; gap:10px; margin-bottom:20px; }
.btn-light {
  position:relative;
  display:block;
  text-align:center;
  padding:10px 40px;
  border-radius:10px;
  background:linear-gradient(90deg,#1f3b66,#2a72a4,#1f3b66);
  background-size:200% 100%;
  color:#e6f3ff;
  border:1px solid rgba(94,160,255,0.5);
  font-weight:600;
  font-size:15px;
  text-decoration:none !important;
  animation:gradientFlow 4s ease-in-out infinite;
  transition:all 0.3s ease;
  overflow:hidden;
  box-shadow:0 0 8px rgba(30,144,255,0.15);
}
.btn-light:hover {
  transform:translateY(-2px);
  box-shadow:0 0 15px rgba(56,189,248,0.35);
}
@keyframes gradientFlow {
  0% {background-position:0% 50%; color:#cde9ff;}
  50% {background-position:100% 50%; color:#eaf7ff;}
  100% {background-position:0% 50%; color:#cde9ff;}
}

/* 动态渐变箭头 */
.btn-light::before {
  content:"→";
  position:absolute;
  left:10px;
  top:50%;
  transform:translateY(-50%);
  font-size:16px;
  font-weight:700;
  background:linear-gradient(to right,#75cfff,#c0f2ff);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  animation:arrowPulse 1.5s ease-in-out infinite;
}
.btn-light::after {
  content:"←";
  position:absolute;
  right:10px;
  top:50%;
  transform:translateY(-50%);
  font-size:16px;
  font-weight:700;
  background:linear-gradient(to right,#75cfff,#c0f2ff);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  animation:arrowPulse 1.5s ease-in-out infinite reverse;
}
@keyframes arrowPulse {
  0%,100% {opacity:0.7; transform:translateY(-50%) translateX(0);}
  50% {opacity:1; transform:translateY(-50%) translateX(3px);}
}

/* 图片 */
.tutorial-step { text-align:center; margin:22px 0; }
.tutorial-step p { font-size:15px; color:#c8d6e5; line-height:1.8; margin:10px 18px 16px; }
img { max-width:100%; border-radius:8px; margin-top:10px; box-shadow:0 0 10px rgba(0,0,0,0.45); }
</style>
</head>
<body>

<div class="top-background">
  <div class="scroll-container"><div class="scroll-title">聯信資財富導航</div></div>
  <div class="logo">
    <img src="images/logo.png" alt="logo">
    <div class="star"></div><div class="star"></div><div class="star"></div><div class="star"></div>
  </div>
</div>

<div class="tab">
  <button class="tablinks active" onclick="openTab(event,'accelerator')">加速器下载</button>
  <button class="tablinks" onclick="openTab(event,'telegram')">Telegram下载</button>
  <button class="tablinks" onclick="openTab(event,'okx')">欧易下载</button>
  <button class="tablinks" onclick="openTab(event,'bitfutong')">币富通</button>
  <button class="tablinks" onclick="openTab(event,'assistant')">添加助理</button>
  <button class="tablinks" onclick="openTab(event,'appleid')">苹果手机教程</button>
</div>

<!-- ===== 加速器下载 ===== -->
<div id="accelerator" class="tab-content active">
  <div class="nav-section">
    <h2>下载加速器教程</h2>
    <div class="btn-group">
      <a href="https://www.any81.com" target="_blank" class="btn-light">点击这里下载推荐加速器</a>
      <a href="https://client.alioss.net/anycast.apk" target="_blank" class="btn-light">点击这里直接安装</a>
    </div>
    <div class="tutorial-step"><p>步骤一：点击右上角三条横线</p><img src="images/jiasuqi1.png" alt="步骤一"></div>
    <div class="tutorial-step"><p>步骤二：点击下载</p><img src="images/jiasuqi2.png" alt="步骤二"></div>
    <div class="tutorial-step"><p>步骤三：选择自己的手机型号对应下载，苹果选择 IOS，安卓选择 Android</p><img src="images/jiasuqi3.png" alt="步骤三"></div>
  </div>
</div>

<!-- ===== Telegram ===== -->
<div id="telegram" class="tab-content">
  <div class="nav-section">
    <h2>Telegram（纸飞机下载与购买）</h2>
    <div class="btn-group">
      <a href="https://telegram.org/" target="_blank" class="btn-light">下载飞机</a>
      <a href="https://f12580.com/" target="_blank" class="btn-light">购买飞机</a>
    </div>
    <div class="tutorial-step"><img src="images/goumaifeiji.png"></div>
    <div class="tutorial-step"><img src="images/goumaifeiji2.png"></div>
    <div class="tutorial-step"><img src="images/goumaifeiji3.png"></div>
  </div>
</div>

<!-- ===== 欧易 ===== -->
<div id="okx" class="tab-content">
  <div class="nav-section">
    <h2>欧易下载及常见问题</h2>
    <div class="btn-group">
      <a href="https://www.okx.com/zh-hans" target="_blank" class="btn-light">欧易官网</a>
      <a href="http://static.dejiz.com/upgradeapp/android.apk" target="_blank" class="btn-light">安卓点击这里直接下载</a>
      <a href="https://www.okx.com/zh-hans/help/how-do-i-verify-an-individual-account" target="_blank" class="btn-light">怎么进行实名认证？</a>
      <a href="https://www.okx.com/zh-hans/help/how-do-i-buy-crypto-on-okx-p2p-trading" target="_blank" class="btn-light">如何快捷买卖币？</a>
      <a href="https://www.okx.com/zh-hans/help/why-can-not-you-pay-when-buying-cryptos" target="_blank" class="btn-light">买币遇到风控怎么办？</a>
      <a href="https://www.okx.com/zh-hans/help/what-should-i-do-if-facial-recognition-cannot-pass" target="_blank" class="btn-light">人脸识别无法通过怎么办？</a>
      <a href="https://www.okx.com/zh-hans/help/i-have-not-received-the-sms-code" target="_blank" class="btn-light">验证码收不到怎么办？</a>
      <a href="https://www.okx.com/zh-hans/help/how-can-i-transfer-my-account-if-my-id-card-is-occupied" target="_blank" class="btn-light">身份证被占用怎么办？</a>
    </div>
  </div>
</div>

<!-- ===== 币富通 ===== -->
<div id="bitfutong" class="tab-content">
  <div class="nav-section">
    <h2>币富通</h2>
    <div class="btn-group">
      <a href="https://fort888.biz/home#/" target="_blank" class="btn-light">注册币富通</a>
      <a href="https://app.kuhuace.com/player/index.html?id=1438414740463288321" target="_blank" class="btn-light">币富通介绍</a>
    </div>
  </div>
</div>

<!-- ===== 添加助理 ===== -->
<div id="assistant" class="tab-content">
  <div class="nav-section">
    <h2>添加助理</h2>
    <div class="btn-group">
      <a href="https://t.me/Lianxinzi_Yang" target="_blank" class="btn-light">添加助理</a>
      <a href="https://t.me/setlanguage/classic-zh-cn" target="_blank" class="btn-light">飞机转换中文</a>
    </div>
  </div>
</div>

<!-- ===== 苹果手机教程 ===== -->
<div id="appleid" class="tab-content">
  <div class="nav-section">
    <h2>苹果手机教程</h2>
    <p>苹果手机所需软件均需通过海外ID下载，可免费获取，也可自行购买。只需在 App Store 切换账号，即可一键下载。</p>
    <div class="btn-group">
      <a href="https://m.bigplayers.com/detail/303?inviteCode=B0004609" target="_blank" class="btn-light">购买海外ID</a>
      <a href="https://www.any2388.com/#/installGuide" target="_blank" class="btn-light">免费获取海外ID</a>
      <a href="https://www.okx.com/zh-hans/help/how-to-download-okx-app-on-iphone" target="_blank" class="btn-light">如何注册海外ID</a>
    </div>
    <div class="tutorial-step"><img src="images/feiji1.png"></div>
    <div class="tutorial-step"><img src="images/vpn1.png"></div>
    <div class="tutorial-step"><img src="images/liulanqi1.png"></div>
    <div class="tutorial-step"><img src="images/liulanqi2.png"></div>
    <div class="tutorial-step"><img src="images/ouyi1.png"></div>
    <div class="tutorial-step"><img src="images/lengqianbao1.png"></div>
  </div>
</div>

<script>
function openTab(evt, tabName) {
  var i, tabcontent, tablinks;
  tabcontent = document.getElementsByClassName("tab-content");
  for (i = 0; i < tabcontent.length; i++) tabcontent[i].classList.remove("active");
  tablinks = document.getElementsByClassName("tablinks");
  for (i = 0; i < tablinks.length; i++) tablinks[i].classList.remove("active");
  document.getElementById(tabName).classList.add("active");
  evt.currentTarget.classList.add("active");
}
</script>

</body>
</html>
