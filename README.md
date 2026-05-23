# Fish-Rng
Rng Fish
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>

<title>Fish-Rng</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial, Helvetica, sans-serif;
}

body{
background:
linear-gradient(to bottom,#0f172a,#020617);
overflow:hidden;
color:white;
}

/* =========================
TOPBAR
========================= */

.topbar{
position:fixed;
top:0;
left:0;
width:100%;
height:75px;
background:rgba(0,0,0,.45);
backdrop-filter:blur(12px);
display:flex;
justify-content:space-between;
align-items:center;
padding:0 20px;
z-index:100;
border-bottom:2px solid #38bdf8;
}

.logo{
font-size:28px;
font-weight:bold;
color:#38bdf8;
text-shadow:0 0 15px #38bdf8;
}

.stats{
display:flex;
gap:18px;
align-items:center;
font-size:14px;
}

.statBox{
background:#0f172a;
padding:8px 12px;
border-radius:12px;
border:1px solid #334155;
min-width:90px;
text-align:center;
}

.expBar{
width:130px;
height:12px;
background:#1e293b;
border-radius:999px;
overflow:hidden;
margin-top:4px;
}

.expFill{
height:100%;
width:0%;
background:
linear-gradient(to right,#38bdf8,#22d3ee);
}

/* =========================
MENU
========================= */

.menuBtn{
position:fixed;
left:20px;
top:95px;
width:70px;
height:70px;
border:none;
border-radius:50%;
background:#0ea5e9;
color:white;
font-size:30px;
cursor:pointer;
box-shadow:0 0 25px #0ea5e9;
z-index:99;
}

.menu{
position:fixed;
left:-420px;
top:0;
width:400px;
height:100vh;
background:rgba(15,23,42,.98);
backdrop-filter:blur(12px);
padding:20px;
overflow:auto;
transition:.35s;
z-index:120;
border-right:2px solid #38bdf8;
}

.menu.active{
left:0;
}

.menuTitle{
font-size:28px;
margin-bottom:20px;
color:#38bdf8;
}

.section{
margin-bottom:30px;
}

.section h2{
margin-bottom:15px;
color:#38bdf8;
}

.card{
background:#111827;
padding:14px;
border-radius:16px;
margin-bottom:12px;
border:1px solid #334155;
animation:fade .25s;
}

@keyframes fade{
from{
opacity:0;
transform:translateY(10px);
}
to{
opacity:1;
transform:translateY(0);
}
}

.card button{
margin-top:10px;
margin-right:8px;
}

/* =========================
BUTTONS
========================= */

button{
border:none;
padding:10px 14px;
border-radius:12px;
font-weight:bold;
cursor:pointer;
transition:.2s;
}

button:hover{
transform:scale(1.04);
}

.buy{
background:#22c55e;
color:white;
}

.sell{
background:#ef4444;
color:white;
}

.lock{
background:#facc15;
color:black;
}

.equip{
background:#38bdf8;
color:white;
}

.upgrade{
background:#8b5cf6;
color:white;
}

/* =========================
CENTER GAME
========================= */

.game{
position:absolute;
top:50%;
left:50%;
transform:translate(-50%,-50%);
text-align:center;
width:100%;
}

.fishButton{
width:210px;
height:210px;
border-radius:50%;
border:none;
font-size:34px;
font-weight:bold;
background:
linear-gradient(to bottom,#38bdf8,#0284c7);
color:white;
cursor:pointer;
box-shadow:
0 0 30px #38bdf8,
0 0 60px rgba(56,189,248,.5);
transition:.2s;
}

.fishButton:hover{
transform:scale(1.05);
}

.fishButton:active{
transform:scale(.96);
}

.fishingText{
margin-top:20px;
font-size:18px;
color:#cbd5e1;
}

/* =========================
MINIGAME BAR
========================= */

.barContainer{
width:520px;
height:42px;
background:#111827;
border-radius:999px;
margin:30px auto 15px;
position:relative;
overflow:hidden;
display:none;
border:2px solid #334155;
}

.greenZone{
position:absolute;
left:180px;
width:150px;
height:100%;
background:
rgba(34,197,94,.45);
}

.movingBar{
position:absolute;
left:0;
top:0;
width:90px;
height:100%;
background:
linear-gradient(to right,#38bdf8,#0ea5e9);
}

.hpContainer{
width:520px;
height:22px;
background:#111827;
border-radius:999px;
overflow:hidden;
display:none;
margin:auto;
border:2px solid #334155;
}

.hpBar{
height:100%;
width:100%;
background:
linear-gradient(to right,#22c55e,#84cc16);
}

/* =========================
FISH CARD
========================= */

.fishArea{
margin-top:30px;
min-height:220px;
}

.fishCard{
width:340px;
margin:auto;
background:
rgba(15,23,42,.96);
padding:22px;
border-radius:22px;
border:2px solid #38bdf8;
box-shadow:
0 0 35px rgba(56,189,248,.4);
animation:pop .35s;
}

@keyframes pop{
from{
opacity:0;
transform:scale(.5);
}
to{
opacity:1;
transform:scale(1);
}
}

.fishEmoji{
font-size:95px;
animation:float 1s infinite alternate;
}

@keyframes float{
from{
transform:translateY(0);
}
to{
transform:translateY(-10px);
}
}

/* =========================
POPUP
========================= */

.popup{
position:fixed;
inset:0;
background:rgba(0,0,0,.6);
display:none;
justify-content:center;
align-items:center;
z-index:200;
}

.popupBox{
width:320px;
background:#0f172a;
padding:28px;
border-radius:20px;
border:2px solid #38bdf8;
text-align:center;
animation:pop .25s;
}

.popupBox h2{
margin-bottom:15px;
color:#38bdf8;
}

.popupBox button{
margin-top:20px;
background:#38bdf8;
color:white;
width:100%;
}

/* =========================
SCROLLBAR
========================= */

::-webkit-scrollbar{
width:8px;
}

::-webkit-scrollbar-thumb{
background:#38bdf8;
border-radius:20px;
}

@media(max-width:700px){

.barContainer,
.hpContainer{
width:90%;
}

.stats{
display:none;
}

.menu{
width:100%;
left:-100%;
}

}

</style>
</head>
<body>

<!-- TOPBAR -->

<div class="topbar">

<div class="logo">
🎣 FISCH RNG
</div>

<div class="stats">

<div class="statBox">
💰<br>
<span id="money">0</span>
</div>

<div class="statBox">
⭐ LEVEL<br>
<span id="level">1</span>
</div>

<div class="statBox">
🎯 LUCK<br>
<span id="luck">0</span>%
</div>

<div class="statBox">
⚔ DAMAGE<br>
<span id="damage">0</span>%
</div>

<div class="statBox">
🔮 POINTS<br>
<span id="points">0</span>
</div>

<div class="statBox">
EXP
<div class="expBar">
<div class="expFill" id="expFill"></div>
</div>
<div style="margin-top:5px">
<span id="exp">0</span>/<span id="needExp">100</span>
</div>
</div>

</div>

</div>

<!-- MENU BUTTON -->

<button class="menuBtn"
onclick="toggleMenu()">
☰
</button>

<!-- MENU -->

<div class="menu"
id="menu">

<div class="menuTitle">
🎣 MENU
</div>

<!-- UPGRADE -->

<div class="section">

<h2>Upgrade</h2>

<div class="card">
🎯 Luck Upgrade (+0.25%)
<br>

<button class="upgrade"
onclick="upgradeLuck()">
Upgrade
</button>

</div>

<div class="card">
⚔ Damage Upgrade (+0.50%)
<br>

<button class="upgrade"
onclick="upgradeDamage()">
Upgrade
</button>

</div>

</div>

<!-- SHOP -->

<div class="section">

<h2>Shop</h2>

<div id="shop"></div>

</div>

<!-- INVENTORY -->

<div class="section">

<h2>Inventory</h2>

<button class="sell"
onclick="sellAllFish()">
Sell All Fish
</button>

<br><br>

<div id="inventory"></div>

</div>

</div>

<!-- GAME -->

<div class="game">

<button
class="fishButton"
id="fishBtn"
onclick="startFishing()">
🎣 FISH
</button>

<div class="fishingText"
id="fishingText">
Press Fish To Start
</div>

<!-- BAR -->

<div class="barContainer"
id="barContainer">

<div class="greenZone"></div>

<div class="movingBar"
id="movingBar"></div>

</div>

<!-- HP -->

<div class="hpContainer"
id="hpContainer">

<div class="hpBar"
id="hpBar"></div>

</div>

<!-- FISH RESULT -->

<div class="fishArea"
id="fishArea"></div>

</div>

<!-- POPUP -->

<div class="popup"
id="popup">

<div class="popupBox">

<h2 id="popupTitle">
Message
</h2>

<div id="popupText"></div>

<button onclick="closePopup()">
OK
</button>

</div>

</div>

<script>

/* =========================
PLAYER DATA
========================= */

let money = 0;

let level = 1;

let exp = 0;

let needExp = 100;

let upgradePoints = 0;

let luck = 0;

let damage = 0;

let inventory = [];

let ownedItems = ["Basic Rod"];

let fishing = false;

/* =========================
SHOP SYSTEM
========================= */

const shopItems = [

{
name:"Lucky Rod",
price:250,
stock:1,
luck:2
},

{
name:"Steel Rod",
price:1200,
stock:1,
luck:6
},

{
name:"Mythic Rod",
price:5000,
stock:1,
luck:14
},

{
name:"Golden Bait",
price:850,
stock:1,
luck:4
},

{
name:"Shark Bait",
price:2500,
stock:1,
luck:10
}

];

/* =========================
FISH DATA
========================= */

const fishes = [

{
name:"Minnow",
emoji:"🐟",
rarity:2,
value:1,
exp:5,
hp:30
},

{
name:"Salmon",
emoji:"🐠",
rarity:8,
value:4,
exp:10,
hp:50
},

{
name:"Golden Fish",
emoji:"🐡",
rarity:35,
value:12,
exp:30,
hp:80
},

{
name:"Shark",
emoji:"🦈",
rarity:100,
value:35,
exp:90,
hp:140
},

{
name:"Megalodon",
emoji:"🐋",
rarity:450,
value:100,
exp:250,
hp:250
},

{
name:"Leviathan",
emoji:"🐉",
rarity:1200,
value:350,
exp:700,
hp:420
}

];

/* =========================
POPUP
========================= */

function popup(title,text){

document.getElementById("popupTitle").innerText =
title;

document.getElementById("popupText").innerText =
text;

document.getElementById("popup").style.display =
"flex";

}

function closePopup(){

document.getElementById("popup").style.display =
"none";

}

/* =========================
MENU
========================= */

function toggleMenu(){

document.getElementById("menu")
.classList.toggle("active");

}

/* =========================
UPDATE UI
========================= */

function updateUI(){

document.getElementById("money").innerText =
money;

document.getElementById("level").innerText =
level;

document.getElementById("luck").innerText =
luck.toFixed(2);

document.getElementById("damage").innerText =
damage.toFixed(2);

document.getElementById("points").innerText =
upgradePoints;

document.getElementById("exp").innerText =
Math.floor(exp);

document.getElementById("needExp").innerText =
needExp;

document.getElementById("expFill").style.width =
(exp/needExp*100)+"%";

renderInventory();

renderShop();

}

/* =========================
EXP SYSTEM
========================= */

function addExp(amount){

exp += amount;

while(exp >= needExp){

exp -= needExp;

level++;

needExp = Math.floor(needExp*1.4);

upgradePoints += 3;

popup(
"LEVEL UP!",
"+3 Upgrade Points"
);

}

updateUI();

}

/* =========================
UPGRADES
========================= */

function upgradeLuck(){

if(upgradePoints <= 0){

popup(
"ERROR",
"Upgrade point tidak cukup!"
);

return;
}

upgradePoints--;

luck += 0.25;

updateUI();

}

function upgradeDamage(){

if(upgradePoints <= 0){

popup(
"ERROR",
"Upgrade point tidak cukup!"
);

return;
}

upgradePoints--;

damage += 0.50;

updateUI();

}

/* =========================
SHOP
========================= */

function renderShop(){

const shop =
document.getElementById("shop");

shop.innerHTML = "";

shopItems.forEach((item,index)=>{

shop.innerHTML += `

<div class="card">

<b>${item.name}</b>

<br><br>

💰 Price: ${item.price}

<br>

🎯 Luck Bonus: +${item.luck}

<br>

📦 Stock: ${item.stock}

<br>

<button class="buy"
onclick="buyItem(${index})">
Buy
</button>

</div>

`;

});

}

function buyItem(index){

let item = shopItems[index];

if(ownedItems.includes(item.name)){

popup(
"ALREADY OWNED",
"Kamu sudah memiliki item ini!"
);

return;
}

if(item.stock <= 0){

popup(
"OUT OF STOCK",
"Stock item habis!"
);

return;
}

if(money < item.price){

popup(
"NOT ENOUGH MONEY",
"Uang kamu tidak cukup!"
);

return;
}

money -= item.price;

item.stock--;

luck += item.luck;

ownedItems.push(item.name);

popup(
"SUCCESS",
"Berhasil membeli "+item.name
);

updateUI();

}

/* =========================
INVENTORY
========================= */

function renderInventory(){

const inv =
document.getElementById("inventory");

inv.innerHTML = "";

if(inventory.length === 0){

inv.innerHTML =
`
<div class="card">
Belum ada ikan.
</div>
`;

return;
}

inventory.forEach((fish,index)=>{

inv.innerHTML += `

<div class="card">

<div style="
font-size:22px;
margin-bottom:8px;
">
${fish.emoji}
<b>${fish.name}</b>
</div>

🎲 1/${fish.rarity}

<br>

💰 ${fish.value}

<br>

⭐ ${fish.exp} EXP

<br><br>

<button class="sell"
onclick="sellFish(${index})">
Sell
</button>

<button class="lock"
onclick="toggleLock(${index})">

${fish.locked ? "Unlock":"Lock"}

</button>

</div>

`;

});

}

function sellFish(index){

let fish = inventory[index];

if(fish.locked){

popup(
"LOCKED",
"Ikan sedang dikunci!"
);

return;
}

money += fish.value;

inventory.splice(index,1);

updateUI();

}

function sellAllFish(){

let total = 0;

inventory = inventory.filter(fish=>{

if(!fish.locked){

total += fish.value;

return false;

}

return true;

});

money += total;

updateUI();

}

function toggleLock(index){

inventory[index].locked =
!inventory[index].locked;

updateUI();

}

/* =========================
GET RNG FISH
========================= */

function getFish(){

let selected = fishes[0];

for(let i=fishes.length-1;i>=0;i--){

let fish = fishes[i];

let rng = Math.floor(
Math.random() *
Math.max(
1,
fish.rarity - (luck*2)
)
)+1;

if(rng === 1){

selected = fish;

break;

}

}

return selected;

}

/* =========================
FISHING MINIGAME
========================= */

function startFishing(){

if(fishing) return;

fishing = true;

document.getElementById("fishBtn")
.innerText = "🎣 REEL";

document.getElementById("fishingText")
.innerText =
"Klik tombol saat bar berada di area hijau!";

document.getElementById("barContainer")
.style.display = "block";

document.getElementById("hpContainer")
.style.display = "block";

let movingBar =
document.getElementById("movingBar");

let hpBar =
document.getElementById("hpBar");

let fish = getFish();

let hp = fish.hp;

let maxHp = fish.hp;

let pos = 0;

let dir = 1;

/* MOVE BAR */

let barLoop = setInterval(()=>{

pos += dir * 8;

if(pos >= 430 || pos <= 0){

dir *= -1;

}

movingBar.style.left =
pos+"px";

},16);

/* REEL ACTION */

function reelAction(){

if(!fishing) return;

if(pos >= 180 && pos <= 300){

hp -= (
10 + (damage*2)
);

}else{

hp -= 2;

}

if(hp < 0){

hp = 0;

}

hpBar.style.width =
(hp/maxHp*100)+"%";

if(hp <= 0){

finishFishing(
fish,
barLoop
);

}

}

document.getElementById("fishBtn")
.onclick = reelAction;

}

/* =========================
FINISH FISHING
========================= */

function finishFishing(
fish,
barLoop
){

clearInterval(barLoop);

fishing = false;

document.getElementById("fishBtn")
.innerText = "🎣 FISH";

document.getElementById("fishBtn")
.onclick = startFishing;

document.getElementById("barContainer")
.style.display = "none";

document.getElementById("hpContainer")
.style.display = "none";

document.getElementById("fishingText")
.innerText =
"Fish Captured!";

inventory.push({

...fish,

locked:false

});

addExp(fish.exp);

document.getElementById("fishArea")
.innerHTML = `

<div class="fishCard">

<div class="fishEmoji">
${fish.emoji}
</div>

<h2 style="
margin-top:10px;
">
${fish.name}
</h2>

<br>

🎲 Chance: 1/${fish.rarity}

<br><br>

💰 Worth: ${fish.value}

<br>

⭐ EXP: +${fish.exp}

</div>

`;

updateUI();

}

/* =========================
START
========================= */

updateUI();

</script>

</body>
</html>