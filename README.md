<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Feliz Aniversário Vivian!</title>

<style>
body{
 margin:0;
 height:100vh;
 background:#a200ff;
 color:white;
 font-family: Arial, Helvetica, sans-serif;
 overflow:hidden;
}

/* CONTEÚDO CENTRAL */
.container{
 position:relative;
 width:100%;
 height:100%;
 display:flex;
 flex-direction:column;
 align-items:center;
 justify-content:center;
 text-align:center;
 z-index:5;
}

.menu button{
 background:black;
 color:white;
 border:2px solid white;
 padding:12px 25px;
 margin:8px;
 cursor:pointer;
 font-size:18px;
}
.menu button:hover{
 background:white;
 color:black;
}

#mensagem{
 margin-top:15px;
 font-size:20px;
}

.centro img{
 width:270px;
 max-width:80vw;
}

/* ESTRELAS */
.star{
 position:fixed;
 top:-20px;
 color:white;
 animation: fall linear infinite, blink 1.5s infinite alternate;
 font-size:14px;
 opacity:.8;
 z-index:1;
}
@keyframes fall{
 to{transform:translateY(110vh);}
}
@keyframes blink{
 from{opacity:0.2;}
 to{opacity:1;}
}

/* IMAGENS QUE PISCAM */
.blink-img{
 position:fixed;
 width:140px;
 animation: piscar 1.5s infinite alternate;
 z-index:3;
}
.top-left{top:10px; left:10px;}
.top-right{top:10px; right:10px;}
.bottom-left{bottom:10px; left:10px;}
.bottom-right{bottom:10px; right:10px;}

@keyframes piscar{
 from{opacity:0;}
 to{opacity:1;}
}

/* GIFS GIRANDO */
.gif{
 position:fixed;
 top:50%;
 transform:translateY(-50%);
 width:170px;
 animation:girar 7s linear infinite;
 z-index:4;
}
.gif.left{left:5px;}
.gif.right{right:5px;}

@keyframes girar{
 from{transform:translateY(-50%) rotate(0deg);}
 to{transform:translateY(-50%) rotate(360deg);}
}

/* VÍDEO */
.video-area{
 position:fixed;
 top:50%;
 left:50%;
 transform:translate(-50%,-50%);
 z-index:2;
 color:white;
 font-weight:bold;
 text-shadow:0 0 5px black;
}
</style>
</head>

<body>

<script>
for(let i=0;i<55;i++){
 let s=document.createElement("div");
 s.className="star";
 s.innerHTML="✦";
 s.style.left=Math.random()*100+"vw";
 s.style.animationDuration=(4+Math.random()*6)+"s";
 s.style.fontSize=(10+Math.random()*18)+"px";
 document.body.appendChild(s);
}
</script>

<div class="container">
 <div class="centro">
  <img src="personagem.png" alt="Imagem central">
 </div>

 <div class="menu">
  <button onclick="document.getElementById('mensagem').innerHTML='feliz aniversário minha amiga amadaaaaaaa!!!!!!'">VIVIAN</button>
  <button onclick="document.getElementById('mensagem').innerHTML='achou que eu tinha esquecido né?'">vivian</button>
 </div>

 <div id="mensagem"></div>
</div>

<img src="herois.jpg" class="blink-img top-left">
<img src="herois.jpg" class="blink-img top-right">
<img src="herois.jpg" class="blink-img bottom-left">
<img src="herois.jpg" class="blink-img bottom-right">

<div class="gif left">
 <img src="mar.gif" style="width:100%;">
</div>

<div class="gif right">
 <img src="estrela.gif" style="width:100%;">
</div>

<div class="video-area">
 <!-- incluir vídeo -->
</div>

</body>
</html>
