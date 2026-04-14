
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Tamil New Year</title>

<style>
body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    text-align: center;
    background: linear-gradient(135deg, #ffcc70, #ff8177);
    color: white;
    overflow: hidden;
}

h1 {
    margin-top: 80px;
    font-size: 40px;
    animation: glow 2s infinite alternate;
}

p {
    font-size: 20px;
}

@keyframes glow {
    from { text-shadow: 0 0 10px #fff; }
    to { text-shadow: 0 0 30px #ffd700, 0 0 40px #ff0000; }
}

/* Floating particles */
.circle {
    position: absolute;
    border-radius: 50%;
    background: rgba(255,255,255,0.3);
    animation: float 10s infinite;
}

@keyframes float {
    from { transform: translateY(100vh); }
    to { transform: translateY(-10vh); }
}

button {
    margin-top: 20px;
    padding: 12px 25px;
    border: none;
    border-radius: 25px;
    background: gold;
    color: black;
    font-size: 18px;
    cursor: pointer;
    transition: 0.3s;
}

button:hover {
    background: white;
}

/* Confetti */
canvas {
    position: fixed;
    top: 0;
    left: 0;
}
</style>
</head>

<body>

<h1>🎉 இனிய தமிழ் புத்தாண்டு நல்வாழ்த்துக்கள் 🎉</h1>
<p>Wishing you happiness, success, and prosperity 🌸</p>

<button onclick="playMusic()">🎶 Play Music</button>

<audio id="music" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"></audio>

<canvas id="confetti"></canvas>

<script>
// Floating circles
for (let i = 0; i < 25; i++) {
    let c = document.createElement("div");
    c.classList.add("circle");
    c.style.width = c.style.height = Math.random()*20+10+"px";
    c.style.left = Math.random()*100+"vw";
    c.style.animationDuration = Math.random()*5+5+"s";
    document.body.appendChild(c);
}

// Music
function playMusic(){
    document.getElementById("music").play();
}

// Confetti
const canvas = document.getElementById("confetti");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let pieces = [];
for(let i=0;i<100;i++){
    pieces.push({
        x: Math.random()*canvas.width,
        y: Math.random()*canvas.height,
        size: Math.random()*5+2,
        speed: Math.random()*3+1
    });
}

function update(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    ctx.fillStyle="white";
    pieces.forEach(p=>{
        ctx.fillRect(p.x,p.y,p.size,p.size);
        p.y+=p.speed;
        if(p.y>canvas.height) p.y=0;
    });
    requestAnimationFrame(update);
}
update();
</script>

</body>
</html>
