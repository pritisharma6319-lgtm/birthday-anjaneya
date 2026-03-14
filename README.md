<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Ultimate Birthday Surprise – ANJANEYA 🎉</title>

<style>
body{
  margin:0;
  font-family:Arial, Helvetica, sans-serif;
  background:linear-gradient(135deg,#ff9a9e,#fad0c4,#ffdde1);
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
  overflow:hidden;
}

.container{
  background:white;
  padding:35px;
  border-radius:20px;
  box-shadow:0 15px 40px rgba(0,0,0,0.25);
  max-width:700px;
  position:relative;
  z-index:2;
}

button{
  padding:12px 25px;
  border:none;
  border-radius:10px;
  background:#ff4d6d;
  color:white;
  font-size:16px;
  cursor:pointer;
  margin:8px;
}

button:hover{background:#e63956}

.hidden{display:none}

#cake{font-size:90px;margin-top:10px}

.candle{font-size:36px;cursor:pointer}

.message{margin-top:20px;font-size:18px;color:#444;line-height:1.6}

#photo{
  width:220px;
  border-radius:20px;
  box-shadow:0 10px 25px rgba(0,0,0,0.3);
  margin-top:15px;
}

#countdown{
  font-size:26px;
  font-weight:bold;
  margin-top:10px;
}

.balloon{
  position:absolute;
  font-size:40px;
  cursor:pointer;
  animation:float 6s linear infinite;
}

@keyframes float{
  from{transform:translateY(110vh)}
  to{transform:translateY(-120vh)}
}

.confetti{
  position:fixed;
  width:10px;
  height:10px;
  top:-10px;
  animation:fall 3s linear forwards;
}

@keyframes fall{
  to{transform:translateY(110vh) rotate(360deg)}
}

.firework{position:fixed;font-size:28px;animation:boom 1s ease-out forwards}

@keyframes boom{
  from{transform:scale(0);opacity:1}
  to{transform:scale(2.5);opacity:0}
}

</style>
</head>

<body>

<div class="container">

<h1>🎉 Birthday Countdown for ANJANEYA 🎂</h1>

<div id="countdown">Loading countdown...</div>

<button onclick="startCelebration()">Start Celebration</button>

<div id="celebration" class="hidden">

<h2>✨ Special Birthday Photo ✨</h2>

<!-- Put the photo file named anjaneya.jpg in the same folder -->
<img id="photo" src="anjaneya.jpg" alt="Birthday Photo">

<br>

<button onclick="startGame()">🎮 Start Balloon Game</button>

<div id="gameArea"></div>

<div id="cakeArea" class="hidden">

<div id="cake">🎂</div>
<p>Make a wish and blow the candle!</p>

<div id="candle" class="candle" onclick="blowCandle()">🕯️</div>

<button onclick="playMusic()">🎵 Play Birthday Music</button>

<p id="wishText" class="message hidden">
✨ Happy Birthday ANJANEYA! ✨

May your day be filled with happiness, laughter, wonderful surprises, and unforgettable moments. You deserve all the joy and success in the world.

May this new year of life bring exciting adventures, amazing achievements, and countless reasons to smile. Keep shining, keep dreaming big, and keep being the wonderful person you are.

Today the world celebrates YOU. Enjoy every moment of your special day! 🎊🎁
</p>

</div>

</div>

<iframe id="music" class="hidden" width="0" height="0"
src="https://www.youtube.com/embed/Eo-KmOd3i7s?enablejsapi=1"
allow="autoplay"></iframe>

</div>

<script>

// COUNTDOWN (example date – change if needed)
const birthday=new Date("2026-12-01T00:00:00")

setInterval(()=>{
  const now=new Date()
  const diff=birthday-now

  const d=Math.floor(diff/(1000*60*60*24))
  const h=Math.floor(diff/(1000*60*60)%24)
  const m=Math.floor(diff/(1000*60)%60)
  const s=Math.floor(diff/1000%60)

  document.getElementById("countdown").innerText=
  d+"d "+h+"h "+m+"m "+s+"s"
},1000)

function startCelebration(){
  document.getElementById("celebration").classList.remove("hidden")
}

// BALLOON POP GAME
function startGame(){
  const area=document.getElementById("gameArea")
  area.innerHTML="<h3>Pop 10 balloons! 🎈</h3>"

  let score=0

  for(let i=0;i<10;i++){
    const b=document.createElement("div")
    b.className="balloon"
    b.textContent="🎈"
    b.style.left=Math.random()*90+"vw"

    b.onclick=()=>{
      b.remove()
      score++

      if(score==10){
        area.innerHTML="🎉 You popped all balloons!"
        document.getElementById("cakeArea").classList.remove("hidden")
      }
    }

    document.body.appendChild(b)
  }
}

function blowCandle(){
  document.getElementById("candle").textContent="💨"
  document.getElementById("wishText").classList.remove("hidden")
  confettiBurst()
  fireworks()
}

function playMusic(){
  const iframe=document.getElementById("music")
  iframe.src += "&autoplay=1"
}

function confettiBurst(){
  for(let i=0;i<80;i++){
    const c=document.createElement('div')
    c.className='confetti'
    c.style.left=Math.random()*100+'vw'
    c.style.background=`hsl(${Math.random()*360},100%,50%)`
    document.body.appendChild(c)
    setTimeout(()=>c.remove(),3000)
  }
}

function fireworks(){
  for(let i=0;i<12;i++){
    const f=document.createElement('div')
    f.className='firework'
    f.textContent='🎆'
    f.style.left=Math.random()*100+'vw'
    f.style.top=Math.random()*60+'vh'
    document.body.appendChild(f)
    setTimeout(()=>f.remove(),1000)
  }
}

</script>

</body>
</html>
