<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Love Me Valentine 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
*{box-sizing:border-box;font-family:'Poppins',sans-serif}

body{
  margin:0;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background:linear-gradient(135deg,#ff9a9e,#fad0c4);
  overflow:hidden;
}

.container{
  background:white;
  padding:30px;
  border-radius:20px;
  text-align:center;
  width:90%;
  max-width:400px;
  box-shadow:0 20px 50px rgba(0,0,0,0.2);
}

h1{
  font-size:24px;
  color:#ff4d6d;
  margin-bottom:20px;
}

.buttons{
  position:relative;
  height:120px;
}

button{
  border:none;
  padding:14px 26px;
  font-size:18px;
  border-radius:50px;
  cursor:pointer;
  transition:0.3s ease;
}

#yes{
  background:#ff4d6d;
  color:white;
  position:absolute;
  left:50%;
  transform:translateX(-50%);
}

#no{
  background:#ddd;
  color:#333;
  position:absolute;
  top:60px;
  left:50%;
  transform:translateX(-50%);
}

.message{
  margin-top:20px;
  font-size:18px;
  color:#333;
  min-height:40px;
}

#finalText{
  font-size:22px;
  color:#ff2e63;
  font-weight:600;
  display:none;
}

.confetti{
  position:fixed;
  top:0;
  left:0;
  width:100%;
  height:100%;
  pointer-events:none;
}
</style>
</head>

<body>

<div class="container">
  <h1>My pyari Bannisa 💖<br>Will you be my wife?</h1>

  <div class="buttons">
    <button id="yes">Yes 💍</button>
    <button id="no">No 🙄</button>
  </div>

  <div class="message" id="msg"></div>
  <div id="finalText"></div>
</div>

<canvas class="confetti" id="confetti"></canvas>

<script>
const yes = document.getElementById("yes");
const no = document.getElementById("no");
const msg = document.getElementById("msg");
const finalText = document.getElementById("finalText");

let escape = true;

// YES bhagega pehle
yes.addEventListener("mouseover",()=>{
  if(escape){
    const x = Math.random()*200 - 100;
    const y = Math.random()*80;
    yes.style.transform = `translate(${x}px,${y}px)`;
  }
});

// NO pe click
no.addEventListener("click",()=>{
  msg.innerText = "Pagal ho rahe ho kya? 😒";
});

// YES final click
yes.addEventListener("click",()=>{
  escape = false;
  yes.style.transform = "translateX(-50%)";
  msg.innerText = "";
  startConfetti();
  showWords();
});

// Word by word text
function showWords(){
  const text = "Congratulations 💍 You are going to be my future wife";
  let i=0;
  finalText.style.display="block";
  finalText.innerText="";
  const interval = setInterval(()=>{
    finalText.innerText += text[i];
    i++;
    if(i===text.length){
      clearInterval(interval);
      setTimeout(()=>{
        finalText.innerText = "I love you ❤️ meri hone wali biwi";
      },5000);
    }
  },80);
}

// CONFETTI 🎉
function startConfetti(){
  const canvas = document.getElementById("confetti");
  const ctx = canvas.getContext("2d");
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  const pieces = [];
  for(let i=0;i<150;i++){
    pieces.push({
      x:Math.random()*canvas.width,
      y:Math.random()*canvas.height,
      r:Math.random()*6+4,
      d:Math.random()*canvas.height,
      color:`hsl(${Math.random()*360},100%,50%)`
    });
  }

  function draw(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    pieces.forEach(p=>{
      ctx.beginPath();
      ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fillStyle=p.color;
      ctx.fill();
    });
    update();
  }

  function update(){
    pieces.forEach(p=>{
      p.y+=2;
      if(p.y>canvas.height) p.y=0;
    });
  }

  setInterval(draw,20);
}
</script>

</body>
</html>
