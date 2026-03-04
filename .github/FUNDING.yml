<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Arun Pro Gaming & Editor</title>

<style>
body{
  margin:0;
  font-family:Arial;
  background:#111;
  color:white;
  text-align:center;
}

nav{
  background:#ff5722;
  padding:15px;
}

nav button{
  padding:8px 12px;
  margin:5px;
  border:none;
  background:black;
  color:white;
  border-radius:5px;
}

section{ display:none; padding:20px; }

canvas{ background:black; margin-top:10px; }

input{ padding:5px; margin:5px; }

.darkmode{
  background:white;
  color:black;
}
</style>
</head>

<body>

<nav id="navbar" style="display:none;">
  <button onclick="show('home')">Home</button>
  <button onclick="show('photo')">Photo Edit</button>
  <button onclick="show('snake')">Snake</button>
  <button onclick="show('car')">Car</button>
  <button onclick="toggleMode()">Dark/Light</button>
  <button onclick="logout()">Logout</button>
</nav>

<!-- LOGIN -->
<section id="login" style="display:block;">
  <h2>Login</h2>
  <input id="username" placeholder="Username"><br>
  <input id="password" type="password" placeholder="Password"><br>
  <button onclick="login()">Login</button>
  <p id="msg"></p>
</section>

<!-- HOME -->
<section id="home">
  <h1>Welcome Arun Website 🎮</h1>
  <p>All-in-One Gaming & Editing Platform</p>
</section>

<!-- PHOTO -->
<section id="photo">
  <h2>Photo Editor</h2>
  <input type="file" id="upload"><br>
  <canvas id="photoCanvas" width="300" height="300"></canvas><br>
  <button onclick="grayscale()">Grayscale</button>
  <button onclick="invert()">Invert</button>
  <button onclick="resetImage()">Reset</button>
</section>

<!-- SNAKE -->
<section id="snake">
  <h2>Snake Game</h2>
  <p>Score: <span id="snakeScore">0</span></p>
  <canvas id="snakeCanvas" width="300" height="300"></canvas>
</section>

<!-- CAR -->
<section id="car">
  <h2>Car Game</h2>
  <p>Score: <span id="carScore">0</span></p>
  <canvas id="carCanvas" width="300" height="400"></canvas>
</section>

<script>

/* LOGIN SYSTEM */
function login(){
 let u=document.getElementById("username").value;
 let p=document.getElementById("password").value;

 if(u==="arun" && p==="1234"){
   document.getElementById("login").style.display="none";
   document.getElementById("navbar").style.display="block";
   show("home");
 }else{
   document.getElementById("msg").innerText="Wrong Login!";
 }
}

function logout(){
 location.reload();
}

/* SECTION SWITCH */
function show(id){
 document.querySelectorAll("section").forEach(s=>s.style.display="none");
 document.getElementById(id).style.display="block";
}

/* DARK MODE */
function toggleMode(){
 document.body.classList.toggle("darkmode");
}

/* PHOTO EDITOR */
let canvas=document.getElementById("photoCanvas");
let ctx=canvas.getContext("2d");
let img=new Image();

document.getElementById("upload").onchange=function(e){
 let reader=new FileReader();
 reader.onload=function(event){
  img.onload=function(){ ctx.drawImage(img,0,0,300,300); }
  img.src=event.target.result;
 }
 reader.readAsDataURL(e.target.files[0]);
}

function grayscale(){
 let data=ctx.getImageData(0,0,300,300);
 for(let i=0;i<data.data.length;i+=4){
  let avg=(data.data[i]+data.data[i+1]+data.data[i+2])/3;
  data.data[i]=data.data[i+1]=data.data[i+2]=avg;
 }
 ctx.putImageData(data,0,0);
}

function invert(){
 let data=ctx.getImageData(0,0,300,300);
 for(let i=0;i<data.data.length;i+=4){
  data.data[i]=255-data.data[i];
  data.data[i+1]=255-data.data[i+1];
  data.data[i+2]=255-data.data[i+2];
 }
 ctx.putImageData(data,0,0);
}

function resetImage(){
 ctx.drawImage(img,0,0,300,300);
}

/* SNAKE GAME */
let sc=document.getElementById("snakeCanvas");
let sctx=sc.getContext("2d");
let snake=[{x:150,y:150}];
let dx=0,dy=0;
let food={x:60,y:60};
let snakeScore=0;

document.addEventListener("keydown",function(e){
 if(e.key=="ArrowLeft"){dx=-10;dy=0;}
 if(e.key=="ArrowRight"){dx=10;dy=0;}
 if(e.key=="ArrowUp"){dx=0;dy=-10;}
 if(e.key=="ArrowDown"){dx=0;dy=10;}
});

function snakeGame(){
 sctx.fillRect(0,0,300,300);
 snake.unshift({x:snake[0].x+dx,y:snake[0].y+dy});

 if(snake[0].x==food.x && snake[0].y==food.y){
   snakeScore++;
   document.getElementById("snakeScore").innerText=snakeScore;
   food={x:Math.floor(Math.random()*30)*10,y:Math.floor(Math.random()*30)*10};
 }else{ snake.pop(); }

 sctx.fillStyle="green";
 snake.forEach(p=>sctx.fillRect(p.x,p.y,10,10));

 sctx.fillStyle="red";
 sctx.fillRect(food.x,food.y,10,10);
}
setInterval(snakeGame,120);

/* CAR GAME */
let cc=document.getElementById("carCanvas");
let cctx=cc.getContext("2d");
let carX=140;
let obstacleY=0;
let carScore=0;

function carGame(){
 cctx.fillRect(0,0,300,400);
 cctx.fillStyle="white";
 cctx.fillRect(carX,350,20,40);

 cctx.fillStyle="red";
 cctx.fillRect(140,obstacleY,20,40);

 obstacleY+=5;
 if(obstacleY>400){
   obstacleY=0;
   carScore++;
   document.getElementById("carScore").innerText=carScore;
 }
}
setInterval(carGame,50);

</script>
</body>
</html>
