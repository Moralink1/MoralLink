<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Moralink</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #fff;
      color: #111;
    }

    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 20px;
      border-bottom: 1px solid #ccc;
      background-color: #fff;
      z-index: 10;
      position: relative;
    }

    header h1 {
      font-size: 1.5em;
      display: flex;
      align-items: center;
    }

    nav a {
      margin-left: 15px;
      text-decoration: none;
      color: #111;
      font-weight: bold;
    }

    .report-btn {
      background-color: #d33;
      color: white;
      padding: 8px 15px;
      border-radius: 8px;
    }

    main {
      padding: 40px;
      max-width: 800px;
      margin: auto;
    }

    .hidden {
      display: none;
    }

    h2 {
      font-size: 2em;
      color: #111;
    }

    input, textarea, select {
      width: 100%;
      padding: 10px;
      margin: 8px 0;
      box-sizing: border-box;
      color: #111;
    }

    button {
      background-color: #d33;
      color: white;
      padding: 12px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }

    .logo {
      width: 500px;
      height: 500px;
      object-fit: cover;
    }

    .logo2 {
      width: 50px;
      height: 50px;
      object-fit: cover;
    }

    .code {
      font-size: 1.4em;
      color: #003399;
      font-weight: bold;
    }

    .hero {
      height: 100vh;
      background-image: url('https://i.imgur.com/seuarquivo.png');
      background-size: cover;
      background-position: center;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      flex-direction: column;
      color: white;
      padding: 20px;
    }

    .hero img {
      margin-bottom: 20px;
    }

    .hero h2, .hero p {
      text-shadow: 1px 1px 3px black;
    }

    .hero h2 {
      font-size: 2.5em;
      margin-bottom: 0.5em;
    }

    .hero p {
      font-size: 1.2em;
      margin-bottom: 1.5em;
    }

    .hero button {
      font-size: 1.1em;
      padding: 12px 24px;
    }
  </style>
</head>
<body>
  <header>
    <img src="https://i.pinimg.com/736x/73/05/bb/7305bb23306c35537848d896df50cd5e.jpg" alt="Logo Moralink" class="logo2">
    <h1>Moralink</h1>
    <nav>
      <a href="#" onclick="showHome()">Home</a>
      <a href="#" onclick="showAbout()">About</a>
      <a href="#" class="report-btn" onclick="showForm()">Report</a>
    </nav>
  </header>

  <main id="home">
    <section class="hero">
      <img src="https://i.pinimg.com/736x/73/05/bb/7305bb23306c35537848d896df50cd5e.jpg" alt="Logo Moralink" class="logo">
      <h2>SUA VOZ DENTRO DA EMPRESA</h2>
      <p>Por uma IA mais inclusiva dentro da indústria</p>
      <button onclick="showForm()">Começar</button>
    </section>
    <p style="text-align: center; font-weight: bold; margin-top: 20px; color: #111;">
      Conectando Ética e Inclusão para um Ambiente de Trabalho Melhor
    </p>
  </main>

  <main id="form" class="hidden">
    <h2>Fazer uma denúncia</h2>
    <p style="color: #111;">Sua denúncia será tratada com confidencialidade e segurança.</p>
    <form onsubmit="sendReport(event)">
      <input type="text" id="nome" placeholder="Nome (opcional)">
      <input type="email" id="email" placeholder="E-mail">
      <select id="categoria" required>
        <option value="">Selecione a categoria</option>
        <option value="Assédio moral">Assédio moral</option>
        <option value="Discriminação">Discriminação</option>
        <option value="Assédio sexual">Assédio sexual</option>
      </select>
      <textarea id="descricao" placeholder="Inclua detalhes como data, local e pessoas envolvidas" required></textarea>
      <input type="text" id="local" placeholder="Local" required>
      <button type="submit">Enviar denúncia</button>
    </form>
  </main>

  <main id="confirmacao" class="hidden">
    <h2>Denúncia enviada</h2>
    <p>Obrigado por sua denúncia. Ela será analisada com cuidado e você será informado sobre o andamento.</p>
    <p><strong>Código de acompanhamento:</strong></p>
    <p class="code" id="codigo"></p>
    <p><strong>Categoria:</strong> <span id="cat"></span></p>
    <p><strong>Descrição:</strong> <span id="desc"></span></p>
    <p><strong>Local:</strong> <span id="loc"></span></p>
  </main>

  <script>
    function showHome() {
      document.getElementById("home").classList.remove("hidden");
      document.getElementById("form").classList.add("hidden");
      document.getElementById("confirmacao").classList.add("hidden");
    }

    function showForm() {
      document.getElementById("home").classList.add("hidden");
      document.getElementById("form").classList.remove("hidden");
      document.getElementById("confirmacao").classList.add("hidden");
    }

    function showAbout() {
      alert("Moralink é uma plataforma ética e segura para denúncias corporativas.");
    }

    function sendReport(event) {
      event.preventDefault();
      const codigo = "ABC" + Math.floor(100000 + Math.random() * 900000);
      document.getElementById("codigo").textContent = codigo;
      document.getElementById("cat").textContent = document.getElementById("categoria").value;
      document.getElementById("desc").textContent = document.getElementById("descricao").value;
      document.getElementById("loc").textContent = document.getElementById("local").value;

      document.querySelector("form").reset();

      document.getElementById("form").classList.add("hidden");
      document.getElementById("confirmacao").classList.remove("hidden");
    }
  </script>
</body>
</html>
