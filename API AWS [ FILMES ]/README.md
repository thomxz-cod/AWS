# 📚 Projeto Final: API de Catálogo de Filmes (AWS Academy)

---

## 🏗️ Parte 1: Infraestrutura de Rede (Passo a Passo)

### 1. Criar a VPC e Gateway

- Aceda ao console da VPC.
- Clique em **Criar VPC** e selecione **VPC e muito mais**.

**Configurações:**
- Nome: Lab-VPC  
- Bloco CIDR: 10.0.0.0/16  
- Zonas de Disponibilidade (AZs): 1  
- Sub-redes Públicas: 1  
- Sub-redes Privadas: 0  
  (Para garantir que sua instância tenha acesso direto à internet)

- Clique em **Criar VPC**.

---

### 2. Configurar o Firewall (Security Group)

- Vá em **Security Groups > Criar grupo de segurança**.

**Configurações:**
- Nome: SG-API-Livros  
- VPC: Lab-VPC  

**Regras de Entrada:**
- SSH | Porta 22 | 0.0.0.0/0  
- TCP Personalizado | Porta 3000 | 0.0.0.0/0  

- Clique em **Criar grupo de segurança**.

---

## 💻 Parte 2: Lançamento e Configuração da Instância

### 1. EC2

- AMI: Amazon Linux 2023  
- Tipo: t2.micro  
- VPC: Lab-VPC  
- Sub-rede: Pública  
- IP público: Habilitado  
- SG: SG-API-Livros  

---

### 2. Instalação

```bash
curl -sL https://rpm.nodesource.com/setup_18.x | sudo bash -
sudo yum install -y nodejs

mkdir lab-filmes && cd lab-filmes
npm init -y
npm install express
```

### 📝 Parte 3: Backend

```js
const express = require('express');
const app = express();

const filmes = [
  { id: 1, titulo: "Interestelar", diretor: "Christopher Nolan", ano: 2014, genero: "Ficção Científica" },
  { id: 2, titulo: "Vingadores: Ultimato", diretor: "Anthony e Joe Russo", ano: 2019, genero: "Ação" },
  { id: 3, titulo: "Parasita", diretor: "Bong Joon-ho", ano: 2019, genero: "Drama" },
  { id: 4, titulo: "O Lobo de Wall Street", diretor: "Martin Scorsese", ano: 2013, genero: "Biografia" },
  { id: 5, titulo: "Cidade de Deus", diretor: "Fernando Meirelles", ano: 2002, genero: "Crime" }
];

app.get('/api/filmes', (req, res) => {
  res.json({
    status: "sucesso",
    mensagem: "🎬 Lista de filmes carregada com sucesso!",
    total: filmes.length,
    filmes
  });
});

app.get('/api/filmes/:id', (req, res) => {
  const filme = filmes.find(f => f.id === parseInt(req.params.id));

  if (!filme) {
    return res.status(404).json({
      status: "erro",
      mensagem: "Filme não encontrado ❌"
    });
  }

  res.json({
    status: "sucesso",
    filme
  });
});

app.listen(3000, () => {
  console.log('🎬 API rodando na porta 3000');
});
```

### 🎨 Frontend

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Lista de Filmes 🎬</title>
<style>
body {
  margin: 0;
  font-family: Arial;
  color: white;
  background: linear-gradient(90deg, #050505, #591818, #ff0000);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  text-align: center;
  width: 80%;
}

.filme {
  background: rgba(0,0,0,0.6);
  padding: 15px;
  margin: 10px;
  border-radius: 10px;
}
</style>
</head>

<body>
<div class="container">
<h1>🎬 Lista de Filmes</h1>
<div id="lista-filmes"></div>
</div>

<script>
fetch('http://localhost:3000/api/filmes')
.then(res => res.json())
.then(data => {
  const container = document.getElementById('lista-filmes');

  data.filmes.forEach(filme => {
    const div = document.createElement('div');
    div.className = 'filme';

    div.innerHTML = `
      <h2>${filme.titulo}</h2>
      <p>Diretor: ${filme.diretor}</p>
      <p>Ano: ${filme.ano}</p>
      <p>Gênero: ${filme.genero}</p>
    `;

    container.appendChild(div);
  });
});
</script>
</body>
</html>
```

## 🚀 Execução
```bash
node server.js
```
