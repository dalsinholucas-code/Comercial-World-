# Comercial-World-
Aqui todos são vencedores 
<!DOCTYPE html>
<html>
<head>
<title>Desconto BUE - Benguela</title>
<style>
body{font-family:Arial; background:#f5f5f5; padding:20px}
.card{background:white; padding:15px; border-radius:10px; margin:10px 0; box-shadow:0 2px 5px #ccc}
button{background:#6A5AFF; color:white; border:none; padding:10px; border-radius:8px; cursor:pointer}
input{padding:8px; width:100%; margin:5px 0; border:1px solid #ccc; border-radius:5px}
</style>
</head>
<body>
<h2>Desconto BUE 🔥</h2>

<h3>Cadastrar meu negócio</h3>
<div class="card">
<input id="nome" placeholder="Nome do Negócio">
<input id="whats" placeholder="WhatsApp">
<input id="desc" placeholder="O que você vende?">
<input id="desconto" type="number" placeholder="% de Desconto">
<button onclick="cadastrar()">Cadastrar</button>
</div>

<h3>Negócios de Hoje</h3>
<div id="lista"></div>

<script>
let negocios = JSON.parse(localStorage.getItem('negocios')) || [];

function cadastrar(){
  let n = {
    nome: document.getElementById('nome').value,
    whats: document.getElementById('whats').value,
    desc: document.getElementById('desc').value,
    desconto: document.getElementById('desconto').value,
    id: Date.now()
  }
  negocios.push(n);
  localStorage.setItem('negocios', JSON.stringify(negocios));
  mostrar();
  alert('Negócio cadastrado com sucesso!');
}

function gerarCupom(id){
  let cupom = 'DESC' + id.toString().slice(-4);
  alert('Teu cupom é: ' + cupom + '\nUse no WhatsApp e ganhe o desconto automático!');
}

function mostrar(){
  let html = '';
  negocios.forEach(n=>{
    html += `<div class="card">
      <h4>${n.nome} - ${n.desconto}% OFF</h4>
      <p>${n.desc}</p>
      <button onclick="gerarCupom(${n.id})">Pegar Desconto</button>
    </div>`
  })
  document.getElementById('lista').innerHTML = html;
}
mostrar();
</script>
</body>
</html>
