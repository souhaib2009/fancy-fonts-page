[index.html](https://github.com/user-attachments/files/23691782/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fancy English Fonts Generator</title>
<style>
body {
  margin: 0;
  padding: 20px;
  overflow: hidden;
  font-family: 'Courier Prime', monospace;
  color: #fff;
  text-align: center;
}

/* Canvas الخلفية */
#matrixCanvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1; /* تحت كل العناصر */
}
</style>

<canvas id="matrixCanvas"></canvas>

<script>
const canvas = document.getElementById('matrixCanvas');
const ctx = canvas.getContext('2d');

function resizeCanvas() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}
resizeCanvas();
window.addEventListener('resize', resizeCanvas);

const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789あいうえお漢字कखगשحظيабвгдеёжзθλμπσψ';
const fontSize = 16;
const columns = Math.floor(canvas.width / fontSize);
const drops = Array(columns).fill(1);

// تدرج لوني ديناميكي
function getGradientColor(y) {
  const hue = (Date.now() / 20 + y) % 360;
  return `hsl(${hue}, 100%, 70%)`;
}

function draw() {
  ctx.fillStyle = 'rgba(0,0,0,0.05)'; // لتأثير الذوبان
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  ctx.font = fontSize + 'px monospace';

  for (let i = 0; i < drops.length; i++) {
    const text = letters[Math.floor(Math.random() * letters.length)];
    ctx.fillStyle = getGradientColor(drops[i] * fontSize);
    ctx.fillText(text, i * fontSize, drops[i] * fontSize);

    if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
      drops[i] = 0;
    }
    drops[i]++;
  }
}

setInterval(draw, 50);
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Courier+Prime&family=Orbitron&family=Roboto+Mono&family=Press+Start+2P&family=Luckiest+Guy&family=Permanent+Marker&family=Shadows+Into+Light&family=Indie+Flower&family=Righteous&family=Amatic+SC&family=Patrick+Hand&family=Varela+Round&family=Quicksand&family=Bangers&display=swap');

body {
  font-family: 'Courier Prime', monospace;
  text-align: center;
  margin: 0;
  padding: 20px;
  background: #000;
  overflow-y: auto; /* تقدر تنزل بعجلة الفأرة */
  color: #fff;
}

h1 {
  color: #00ffff;
  text-shadow: 0 0 10px #00ffff;
  margin-bottom: 20px;
}

input[type="text"] {
  padding: 10px;
  font-size: 22px;
  width: 300px;
  border-radius: 8px;
  border: 1px solid #555;
  background: #111;
  color: #fff;
}

#results {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 15px;
  margin-top: 20px;
}

.styleBox {
  background: #111;
  padding: 12px 25px;
  border-radius: 12px;
  box-shadow: 0 0 8px #0ff, 0 0 12px #f0f, 0 0 16px #ff4;
  cursor: pointer;
  transition: 0.3s;
  min-width: 220px;
  font-weight: bold;
}

.styleBox:hover {
  transform: scale(1.05);
  box-shadow: 0 0 15px #0ff, 0 0 20px #f0f, 0 0 25px #ff4;
}

/* نجوم متلألئة */
.star {
  position: absolute;
  background: white;
  border-radius: 50%;
  opacity: 0.8;
  animation: twinkle 2s infinite alternate;
}

@keyframes twinkle {
  0% { opacity: 0.2; transform: scale(0.5); }
  50% { opacity: 1; transform: scale(1); }
  100% { opacity: 0.2; transform: scale(0.5); }
}
</style>
</head>
<body>

<h1>🎨 Fancy English Fonts Generator 🎨</h1>

<input type="text" id="textInput" placeholder="Type your text here..." oninput="generate()">

<div id="results"></div>

<script>
// 100 خط مزخرف للإنجليزية (50 قديمة + 50 جديدة)
const englishFancy = [
  t=>t,
  t=>t.toUpperCase(),
  t=>t.toLowerCase(),
  t=>t.split('').reverse().join(''),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D3A)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D49)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D3C)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D20)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D400)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D434)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D468)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D49C)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D4D0)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D504)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D538)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D56C)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D5A0)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D5D4)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D608)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D63C)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D670)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D6A4)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D6D8)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D70C)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D740)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D774)),
  t=>t.replace(/[A-Za-z]/g,c=>String.fromCharCode(c.charCodeAt(0)+0x1D7A8)),
  t=>t.replace(/[A-Za-z]/g,c=>c+'*'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'~'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'`'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'^'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'!'),
  t=>t.replace(/[A-Za-z]/g,c=>'★'+c+'★'),
  t=>t.replace(/[A-Za-z]/g,c=>'♡'+c+'♡'),
  t=>t.replace(/[A-Za-z]/g,c=>'✦'+c+'✦'),
  t=>t.replace(/[A-Za-z]/g,c=>'❁'+c),
  t=>t.replace(/[A-Za-z]/g,c=>'◌'+c+'◌'),
  t=>t.replace(/[A-Za-z]/g,c=>'✧'+c+'✧'),
  t=>t.replace(/[A-Za-z]/g,c=>'🔥'+c+'🔥'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'̷'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'̴'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'̵'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'̶'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'̸'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'•'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'~'),
  t=>t.replace(/[A-Za-z]/g,c=>c+'*'),
  // 50 خطوط جديدة
  t=>t.replace(/[A-Za-z]/g,c=>'✪'+c+'✪'),
  t=>t.replace(/[A-Za-z]/g,c=>'✿'+c+'✿'),
  t=>t.replace(/[A-Za-z]/g,c=>'✰'+c+'✰'),
  t=>t.replace(/[A-Za-z]/g,c=>'❀'+c+'❀'),
  t=>t.replace(/[A-Za-z]/g,c=>'☯'+c+'☯'),
  t=>t.replace(/[A-Za-z]/g,c=>'☀'+c+'☀'),
  t=>t.replace(/[A-Za-z]/g,c=>'☁'+c+'☁'),
  t=>t.replace(/[A-Za-z]/g,c=>'❝'+c+'❞'),
  t=>t.replace(/[A-Za-z]/g,c=>'❞'+c+'❝'),
  t=>t.replace(/[A-Za-z]/g,c=>'✪'+c+'✪'),
  t=>t.replace(/[A-Za-z]/g,c=>'✧'+c+'✧'),
  t=>t.replace(/[A-Za-z]/g,c=>'✦'+c+'✦'),
  t=>t.replace(/[A-Za-z]/g,c=>'★'+c+'★'),
  t=>t.replace(/[A-Za-z]/g,c=>'☆'+c+'☆'),
  t=>t.replace(/[A-Za-z]/g,c=>'☯'+c+'☯'),
  t=>t.replace(/[A-Za-z]/g,c=>'☮'+c+'☮'),
  t=>t.replace(/[A-Za-z]/g,c=>'☾'+c+'☽'),
  t=>t.replace(/[A-Za-z]/g,c=>'☼'+c+'☼'),
  t=>t.replace(/[A-Za-z]/g,c=>'♛'+c+'♛'),
  t=>t.replace(/[A-Za-z]/g,c=>'♚'+c+'♚'),
  t=>t.replace(/[A-Za-z]/g,c=>'✌'+c+'✌'),
  t=>t.replace(/[A-Za-z]/g,c=>'☂'+c+'☂'),
  t=>t.replace(/[A-Za-z]/g,c=>'♠'+c+'♠'),
  t=>t.replace(/[A-Za-z]/g,c=>'♣'+c+'♣'),
  t=>t.replace(/[A-Za-z]/g,c=>'♥'+c+'♥'),
  t=>t.replace(/[A-Za-z]/g,c=>'♦'+c+'♦'),
  t=>t.replace(/[A-Za-z]/g,c=>'✎'+c+'✎'),
  t=>t.replace(/[A-Za-z]/g,c=>'☯'+c+'☯')
];

const fonts = [
  "'Courier Prime', monospace",
  "'Orbitron', sans-serif",
  "'Roboto Mono', monospace",
  "'Press Start 2P', cursive",
  "'Luckiest Guy', cursive",
  "'Permanent Marker', cursive",
  "'Shadows Into Light', cursive",
  "'Indie Flower', cursive",
  "'Righteous', cursive",
  "'Amatic SC', cursive",
  "'Patrick Hand', cursive",
  "'Varela Round', sans-serif",
  "'Quicksand', sans-serif",
  "'Bangers', cursive"
];

function generate() {
  const text = document.getElementById('textInput').value || 'Your text';
  const results = document.getElementById('results');
  results.innerHTML = '';
  englishFancy.forEach((fn,index)=>{
    const div = document.createElement('div');
    div.className='styleBox';
    div.textContent = fn(text);
    div.style.fontFamily = fonts[index % fonts.length];
    div.onclick = ()=>navigator.clipboard.writeText(div.textContent);
    results.appendChild(div);
  });
}

// توليد نجوم متلألئة
for(let i=0;i<100;i++){
  const star = document.createElement('div');
  star.className='star';
  const size = Math.random()*3+1;
  star.style.width = star.style.height=size+'px';
  star.style.top=Math.random()*100+'%';
  star.style.left=Math.random()*100+'%';
  star.style.animationDuration=(Math.random()*3+1)+'s';
  document.body.appendChild(star);
}

// توليد افتراضي
generate();
</script>

</body>
</html>

