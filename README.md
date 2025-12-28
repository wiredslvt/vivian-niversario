<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Feliz Aniversário Vivian!</title>

<style>
body{
 margin:0;
 height:100vh;
 background:#b300ff;
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

/* BOTÕES ESTILO DVD + GIRO */
.menu button{
 background:black;
 color:white;
 border:3px solid white;
 padding:12px 28px;
 margin:8px;
 cursor:pointer;
 font-size:20px;
 font-weight:bold;
 border-radius:50px;
 box-shadow:0 0 10px white;
 animation: dvdspin 6s linear infinite;
}

.menu button:hover{
 background:white;
 color:black;
 box-shadow:0 0 20px yellow;
}

@keyframes dvdspin{
 from{transform:rotate(0deg);}
 to{transform:rotate(360deg);}
}

#mensagem{
 margin-top:15px;
 font-size:22px;
 font-weight:bold;
}

/* IMAGEM CENTRAL */
.centro img{
 width:290px;
 max-width:80vw;
 border:4px solid white;
 border-radius:12px;
 box-shadow:0 0 20px black;
}

/* ESTRELAS CAINDO */
.star{
 position:fixed;
 top:-20px;
 color:white;
 animation: fall linear infinite, blink 1.3s infinite alternate;
 font-size:14px;
 opacity:.9;
 z-index:1;
}
@keyframes fall{
 to{transform:translateY(110vh);}
}
@keyframes blink{
 from{opacity:0.2;}
 to{opacity:1;}
}

/* IMAGENS PISCANDO NAS BORDAS */
.blink-img{
 position:fixed;
 width:150px;
 animation: piscar 1.5s infinite alternate;
 z-index:3;
 border:3px solid white;
 border-radius:10px;
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
 width:180px;
 animation:girar 7s linear infinite;
 z-index:4;
}
.gif.left{left:10px;}
.gif.right{right:10px;}

@keyframes girar{
 from{transform:translateY(-50%) rotate(0deg);}
 to{transform:translateY(-50%) rotate(360deg);}
}

/* LOCAL DO VÍDEO */
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

/* ÁREA DOS RECADOS */
.recados-box{
 position:fixed;
 bottom:8px;
 left:50%;
 transform:translateX(-50%);
 width:90%;
 max-width:500px;
 background:rgba(0,0,0,.4);
 border:2px solid white;
 border-radius:12px;
 padding:10px;
 z-index:10;
}

.recados-box input,
.recados-box textarea{
 width:100%;
 border:none;
 padding:6px;
 border-radius:6px;
 margin-top:4px;
}

.recados-box button{
 margin-top:6px;
 width:100%;
 padding:8px;
 font-weight:bold;
 cursor:pointer;
 border-radius:10px;
}

/* LISTA DE RECADOS */
#listaRecados{
 max-height:120px;
 overflow-y:auto;
 font-size:14px;
 margin-top:10px;
}
</style>
</head>

<body>

<!-- ESTRELAS -->
<script>
for(let i=0;i<60;i++){
 let s=document.createElement("div");
 s.className="star";
 s.innerHTML="✦";
 s.style.left=Math.random()*100+"vw";
 s.style.animationDuration=(4+Math.random()*6)+"s";
 s.style.fontSize=(10+Math.random()*20)+"px";
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

<!-- IMAGENS PISCANDO -->
<img src="herois.jpg" class="blink-img top-left">
<img src="herois.jpg" class="blink-img top-right">
<img src="herois.jpg" class="blink-img bottom-left">
<img src="herois.jpg" class="blink-img bottom-right">

<!-- GIFS GIRANDO -->
<div class="gif left">
 <img src="mar.gif" style="width:100%;">
</div>

<div class="gif right">
 <img src="estrela.gif" style="width:100%;">
</div>

<!-- VÍDEO -->
<div class="video-area">
 <!-- incluir vídeo -->
</div>


<!-- RECADOS (SALVA NO NAVEGADOR DO USUÁRIO) -->
<div class="recados-box">
 <strong>Deixe seu recado 💜</strong>

 <input id="nome" placeholder="Seu nome">
 <textarea id="recado" rows="2" placeholder="Escreva aqui..."></textarea>

 <button onclick="salvarRecado()">Enviar</button>

 <div id="listaRecados"></div>
</div>

<script>
function salvarRecado(){
 let nome=document.getElementById('nome').value.trim();
 let recado=document.getElementById('recado').value.trim();

 if(!nome || !recado) return alert('Preencha tudo 🙂');

 let lista=JSON.parse(localStorage.getItem('recadosVivian')||'[]');

 lista.push({nome,recado});

 localStorage.setItem('recadosVivian',JSON.stringify(lista));

 mostrarRecados();

 document.getElementById('recado').value="";
}

function mostrarRecados(){
 let lista=JSON.parse(localStorage.getItem('recadosVivian')||'[]');
 let div=document.getElementById('listaRecados');
 div.innerHTML="";

 lista.forEach(r=>{
  let p=document.createElement('p');
  p.innerHTML=`<b>${r.nome}</b>: ${r.recado}`;
  div.appendChild(p);
 });
}

mostrarRecados();
</script>

</body>
</html>

