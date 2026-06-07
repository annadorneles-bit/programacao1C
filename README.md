<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Agrinho 2026 - ULTRA FINAL PREMIUM</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Montserrat:wght@300;500;700&display=swap" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3.12.5/dist/gsap.min.js"></script>

<style>
body{
    margin:0;
    font-family:'Montserrat', sans-serif;
    background:#0b1b2b;
    color:#f5f1e8;
    overflow-x:hidden;
}

/* HERO COM VÍDEO CINEMATOGRÁFICO */
.hero{
    height:100vh;
    position:relative;
    display:flex;
    justify-content:center;
    align-items:center;
    text-align:center;
    overflow:hidden;
}

.hero video{
    position:absolute;
    width:100%;
    height:100%;
    object-fit:cover;
    filter:brightness(0.4);
}

.hero-content{
    position:relative;
    z-index:2;
}

.hero h1{
    font-size:60px;
    font-family:'Playfair Display';
    text-shadow:0 0 25px rgba(127,179,255,0.5);
}

.hero p{
    font-size:20px;
    opacity:0.9;
}

/* MENU */
nav{
    position:fixed;
    top:0;
    width:100%;
    display:flex;
    justify-content:center;
    gap:25px;
    padding:14px;
    background:rgba(0,0,0,0.5);
    backdrop-filter:blur(10px);
    z-index:999;
}

nav a{
    color:white;
    text-decoration:none;
    font-weight:500;
}

nav a:hover{
    color:#7fb3ff;
}

/* SEÇÕES */
section{
    max-width:1000px;
    margin:auto;
    padding:70px 20px;
    opacity:0;
    transform:translateY(50px);
    transition:1s;
    position:relative;
}

section.show{
    opacity:1;
    transform:translateY(0);
}

/* CARDS */
.card{
    background:rgba(255,255,255,0.06);
    padding:25px;
    border-radius:16px;
    margin:20px 0;
    backdrop-filter:blur(10px);
    box-shadow:0 10px 30px rgba(0,0,0,0.3);
    transition:0.3s;
}

.card:hover{
    transform:scale(1.02);
}

/* STATS */
.stats{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
    gap:15px;
}

.stat{
    background:linear-gradient(135deg,#0b1b2b,#1f3b63);
    padding:20px;
    border-radius:14px;
    text-align:center;
}

/* GALERIA */
.gallery{
    display:flex;
    gap:15px;
    overflow-x:auto;
}

.gallery img{
    width:250px;
    border-radius:12px;
    transition:0.4s;
}

.gallery img:hover{
    transform:scale(1.05);
}

/* BOTÕES */
button{
    background:#1f3b63;
    color:white;
    border:none;
    padding:12px;
    width:100%;
    border-radius:10px;
    cursor:pointer;
}

/* PARTICLES */
canvas{
    position:fixed;
    top:0;
    left:0;
    z-index:-1;
}

/* TOOLTIP ROTEIRO ORAL */
.tooltip{
    position:absolute;
    top:-40px;
    left:50%;
    transform:translateX(-50%);
    background:rgba(31,63,179,0.9);
    color:white;
    padding:8px 12px;
    border-radius:8px;
    font-size:14px;
    opacity:0;
    pointer-events:none;
    transition:0.3s;
    white-space: nowrap;
}
.card:hover .tooltip{
    opacity:1;
}
</style>
</head>
<body>

<!-- HERO -->
<div class="hero">
<video autoplay muted loop>
<source src="https://cdn.pixabay.com/video/2023/03/30/156485-812796909_large.mp4" type="video/mp4">
</video>
<div class="hero-content">
<h1>AGRINHO 2026</h1>
<p>Do campo à cidade: conexão sustentável e tecnológica</p>
</div>
</div>

<!-- MENU -->
<nav>
<a href="#campo">Campo</a>
<a href="#cidade">Cidade</a>
<a href="#conexao">Conexão</a>
<a href="#dados">Dados</a>
<a href="#quiz">Quiz</a>
<a href="#galeria">Galeria</a>
</nav>

<!-- SEÇÕES -->
<section id="campo">
<div class="card">
<h2>🌾 O Campo</h2>
<p>O campo é responsável pela produção de alimentos, preservação ambiental e inovação tecnológica agrícola.</p>
<div class="tooltip">Apresente: destaque como a tecnologia aumenta a produtividade sem prejudicar a natureza.</div>
</div>
</section>

<section id="cidade">
<div class="card">
<h2>🏙️ A Cidade</h2>
<p>A cidade distribui recursos, promove consumo consciente e integra inovação para um futuro sustentável.</p>
<div class="tooltip">Apresente: explique a importância da cidade no equilíbrio com o campo.</div>
</div>
</section>

<section id="conexao">
<div class="card">
<h2>🔗 Conexão Campo-Cidade</h2>
<p>O equilíbrio entre campo e cidade garante desenvolvimento sustentável, social e ambiental.</p>
<div class="tooltip">Apresente: enfatize que ambos dependem um do outro para prosperar.</div>
</div>
</section>

<section id="dados">
<div class="card">
<h2>📊 Impacto Agrinho</h2>
<canvas id="chart"></canvas>
<div class="tooltip">Apresente: destaque os números positivos de sustentabilidade e tecnologia.</div>
</div>
</section>

<section id="quiz">
<div class="card">
<h2>🎮 Quiz Interativo</h2>
<p>O que ajuda mais o meio ambiente?</p>
<button onclick="q(true)">Energia limpa</button>
<button onclick="q(false)">Desmatamento</button>
<p id="res"></p>
<div class="tooltip">Apresente: mostre engajamento com perguntas interativas.</div>
</div>
</section>

<section id="galeria">
<div class="card">
<h2>🖼️ Galeria Campo e Natureza</h2>
<div class="gallery">
<img src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee">
<img src="https://images.unsplash.com/photo-1469474968028-56623f02e42e">
<img src="https://images.unsplash.com/photo-1501785888041-af3ef285b470">
</div>
<div class="tooltip">Apresente: descreva brevemente cada imagem e sua relação com sustentabilidade.</div>
</div>
</section>

<!-- PARTICLES -->
<canvas id="particles"></canvas>

<!-- MÚSICA DE FUNDO -->
<audio autoplay loop>
<source src="https://cdn.pixabay.com/download/audio/2022/10/16/audio_c8c8a8b8b7.mp3?filename=soft-piano-ambient-112191.mp3" type="audio/mpeg">
</audio>

<script>
// CHART
new Chart(document.getElementById("chart"),{
type:"bar",
data:{
labels:["Sustentável","Tecnologia","Produção","Consumo"],
datasets:[{
data:[95,90,85,80],
backgroundColor:["#0b1b2b","#1f3b63","#3b6fb3","#7fb3ff"]
}]
},
options:{plugins:{legend:{display:false}}}
});

// QUIZ
let p=0;
function q(c){
if(c)p++;
document.getElementById("res").innerText="Pontuação: "+p;
}

// SCROLL ANIMATION
const sections=document.querySelectorAll("section");
const obs=new IntersectionObserver(e=>{
e.forEach(i=>{
if(i.isIntersecting)i.target.classList.add("show")
});
},{threshold:0.2});
sections.forEach(s=>obs.observe(s));

// PARTICLES
const canvas=document.getElementById("particles");
const ctx=canvas.getContext("2d");
canvas.width=innerWidth;
canvas.height=innerHeight;
let particles=[];
for(let i=0;i<100;i++){
particles.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:1.5});
}
function
