<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A Letter For You ❤️</title>

<link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@300;400&display=swap" rel="stylesheet">

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
}

body{
height:100vh;
overflow:hidden;
display:flex;
justify-content:center;
align-items:center;
font-family:'Poppins',sans-serif;
background:url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?q=80&w=2000') center/cover;
}

.overlay{
position:absolute;
inset:0;
background:rgba(0,0,0,.35);
backdrop-filter:blur(2px);
}

.envelope{
position:relative;
width:320px;
height:220px;
cursor:pointer;
z-index:10;
transition:.8s;
}

.envelope-body{
position:absolute;
bottom:0;
width:100%;
height:180px;
background:#f8e7d3;
border-radius:0 0 10px 10px;
}

.flap{
position:absolute;
top:0;
width:0;
height:0;
border-left:160px solid transparent;
border-right:160px solid transparent;
border-top:110px solid #e6d0b6;
transform-origin:top;
transition:1s;
}

.open .flap{
transform:rotateX(180deg);
}

.letter{
position:absolute;
left:50%;
top:50%;
transform:translate(-50%,-50%) scale(.2);
width:90%;
max-width:700px;
height:auto;
background:#fffaf0;
padding:35px;
border-radius:15px;
box-shadow:0 15px 40px rgba(0,0,0,.3);
opacity:0;
z-index:20;
transition:1.5s;
}

.show{
opacity:1;
transform:translate(-50%,-50%) scale(1);
}

.date{
text-align:right;
margin-bottom:20px;
color:#777;
}

.title{
font-family:'Dancing Script',cursive;
font-size:35px;
margin-bottom:15px;
}

.text{
line-height:1.8;
font-size:17px;
white-space:pre-wrap;
}

.signature{
margin-top:25px;
text-align:right;
font-family:'Dancing Script',cursive;
font-size:32px;
}

.music-btn{
position:fixed;
top:20px;
right:20px;
padding:12px 20px;
border:none;
border-radius:30px;
background:white;
cursor:pointer;
font-weight:bold;
z-index:100;
}

.heart{
position:absolute;
color:white;
font-size:20px;
animation:float 10s linear infinite;
}

@keyframes float{
0%{
transform:translateY(100vh);
opacity:0;
}
10%{
opacity:1;
}
100%{
transform:translateY(-120vh);
opacity:0;
}
}

@media(max-width:768px){
.letter{
width:95%;
padding:25px;
}
.title{
font-size:28px;
}
.text{
font-size:15px;
}
}
</style>
</head>

<body>

<div class="overlay"></div>

<button class="music-btn" onclick="playMusic()">
🎵 Play Music
</button>

<div class="envelope" id="envelope">
<div class="flap"></div>
<div class="envelope-body"></div>
</div>

<div class="letter" id="letter">

<div class="date" id="date"></div>

<div class="title">Hey, Resh.</div>

<div class="text" id="typing"></div>

<div class="signature">
With love,<br>
Gian ❤️
</div>

</div>

<audio id="music" loop>
<source src="https://files.catbox.moe/3l5v2f.mp3" type="audio/mpeg">
</audio>

<script>

document.getElementById("date").innerHTML =
new Date().toLocaleDateString();

const message = `It's been a while. I'm always thinking about you, ug okay ra ba ka. It's almost 2 months na since we talked the way we used to, and I miss you so much.

I'm just hoping nga dili ni moabot sa point nga mahimo tag strangers. Always remember nga naa ra ko diri if you ever need anything.

I hope everything is going well for you.

Amping pirmi ha, and take care of yourself. 🫶🏻🫶🏻`;

const envelope = document.getElementById("envelope");
const letter = document.getElementById("letter");

envelope.onclick = () => {

envelope.classList.add("open");

setTimeout(()=>{
letter.classList.add("show");
typeWriter();
},800);

}

let i = 0;

function typeWriter(){

if(i < message.length){
document.getElementById("typing").innerHTML += message.charAt(i);
i++;
setTimeout(typeWriter,40);
}

}

function playMusic(){
document.getElementById("music").play();
}

function createHeart(){

const heart = document.createElement("div");

heart.className="heart";
heart.innerHTML="❤️";

heart.style.left=Math.random()*100+"vw";
heart.style.fontSize=(Math.random()*25+15)+"px";

heart.style.animationDuration=
(Math.random()*5+6)+"s";

document.body.appendChild(heart);

setTimeout(()=>{
heart.remove();
},10000);

}

setInterval(createHeart,500);

</script>

</body>
</html>
