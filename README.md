<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Partner Proposal</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500&family=Dancing+Script:wght@600&display=swap" rel="stylesheet">

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

body{
height:100vh;
overflow:hidden;
display:flex;
justify-content:center;
align-items:center;
text-align:center;
background:linear-gradient(135deg,#ffd6e8,#ff7aa8);
color:#fff;
}

.container{
max-width:500px;
padding:20px;
}

.bear{
font-size:70px;
animation:bounce 1.6s infinite;
}

@keyframes bounce{
0%,100%{transform:translateY(0)}
50%{transform:translateY(-20px)}
}

h1{
font-family:'Dancing Script',cursive;
font-size:48px;
margin:10px 0;
}

.subtitle{
font-style:italic;
opacity:.9;
margin-bottom:20px;
}

.closing{
margin-top:30px;
font-size:14px;
opacity:.9;
}

.buttons{
margin-top:30px;
display:flex;
justify-content:center;
gap:40px;
}

button{
cursor:pointer;
border:none;
padding:14px 30px;
font-size:18px;
border-radius:50px;
transition:.3s;
}

#yesBtn{
background:linear-gradient(45deg,#ff2d55,#ff5e7e);
color:#fff;
box-shadow:0 0 15px rgba(255,0,80,.6);
}

#yesBtn:hover{
transform:scale(1.1);
box-shadow:0 0 25px rgba(255,0,80,1);
}

#noBtn{
background:#fff;
color:#ff2d55;
border:2px solid #ff2d55;
}

.heart{
position:fixed;
bottom:-50px;
font-size:20px;
animation:floatUp linear infinite;
opacity:0;
}

@keyframes floatUp{
0%{transform:translateY(0);opacity:0}
20%{opacity:1}
80%{opacity:1}
100%{transform:translateY(-110vh);opacity:0}
}

.celebration{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
display:none;
justify-content:center;
align-items:center;
flex-direction:column;
background:linear-gradient(135deg,#ffd6e8,#ff7aa8);
z-index:10;
}

.celebration h2{
font-size:40px;
animation:pulse 1s infinite;
}

.spin{
font-size:60px;
margin:20px;
animation:spin 2s linear infinite;
}

@keyframes spin{
100%{transform:rotate(360deg)}
}

@keyframes pulse{
0%,100%{transform:scale(1)}
50%{transform:scale(1.2)}
}

.confetti{
position:fixed;
width:10px;
height:10px;
background:red;
top:-10px;
animation:fall linear forwards;
}

@keyframes fall{
to{
transform:translateY(110vh) rotate(720deg);
}
}

@media (max-width:600px){

h1{
font-size:34px;
}

.bear{
font-size:60px;
}

.buttons{
flex-direction:column;
gap:20px;
}

button{
padding:16px 36px;
font-size:20px;
}

}

</style>
</head>

<body>

<div class="container" id="mainBox">

<div class="bear">🐻</div>

<h1>Will You Be My Partner, Miss Bhardwaj?</h1>

<p class="subtitle">I've been gathering courage to ask you this...</p>

<div class="buttons">
<button id="yesBtn">Yes</button>
<button id="noBtn">No</button>
</div>

<p class="closing">Every love story is beautiful, but ours is my favourite</p>

</div>

<div class="celebration" id="celebration">
<h2>Mujhe pata tha tum maan jaogi 💖</h2>
<div class="spin">💞</div>
<p>Ab officially tum meri partner ho Miss Bhardwaj ❤️</p>
</div>

<script>

const messages=[
"Nope, not an option!",
"Try again!",
"You sure about that?",
"Not happening!",
"Think again!"
]

let msgIndex=0

const noBtn=document.getElementById("noBtn")
const yesBtn=document.getElementById("yesBtn")

function moveNoButton(){

const yesRect=yesBtn.getBoundingClientRect()

let x,y

do{
x=Math.random()*(window.innerWidth-120)
y=Math.random()*(window.innerHeight-60)
}
while(
x>yesRect.left-80 &&
x<yesRect.right+80 &&
y>yesRect.top-50 &&
y<yesRect.bottom+50
)

noBtn.style.position="fixed"
noBtn.style.left=x+"px"
noBtn.style.top=y+"px"

noBtn.innerText=messages[msgIndex]

msgIndex=(msgIndex+1)%messages.length
}

noBtn.addEventListener("click",moveNoButton)
noBtn.addEventListener("mouseover",moveNoButton)
noBtn.addEventListener("touchstart",moveNoButton)

function createHearts(){

for(let i=0;i<15;i++){

const heart=document.createElement("div")
heart.className="heart"
heart.innerText="❤️"

heart.style.left=Math.random()*100+"vw"
heart.style.fontSize=(Math.random()*20+10)+"px"
heart.style.animationDuration=(Math.random()*6+5)+"s"
heart.style.animationDelay=Math.random()*5+"s"

document.body.appendChild(heart)

}

}

createHearts()

yesBtn.onclick=function(){

document.getElementById("mainBox").style.display="none"

document.querySelectorAll(".heart").forEach(h=>h.remove())

document.getElementById("celebration").style.display="flex"

createConfetti()

}

function createConfetti(){

for(let i=0;i<120;i++){

const conf=document.createElement("div")
conf.className="confetti"

conf.style.left=Math.random()*100+"vw"

conf.style.background=`hsl(${Math.random()*360},70%,60%)`

conf.style.animationDuration=(Math.random()*3+2)+"s"

document.body.appendChild(conf)

}

}

</script>

</body>
</html>
