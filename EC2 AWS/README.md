# 🚀 Tarefa 1: Iniciar a instância do Amazon EC2

Nesta tarefa, você executará uma instância do Amazon EC2 com proteção contra encerramento 🔒 e proteção contra interrupção ⛔.

---

## ⚙️ Passos iniciais

- 🌐 Acesse: **Serviços > Computação > EC2**
- 📍 Região: **Norte da Virgínia (us-east-1)**
- ▶️ Clique em **Executar instância**

---

## 🏷️ Etapa 1: Nome e tags

- Nome: **Web Server**
- Tag:
  - **Chave:** Name  
  - **Valor:** Web Server  

📌 Tags ajudam a organizar recursos.

---

## 💿 Etapa 2: Imagem (AMI)

- ✅ Amazon Linux (Quick Start)
- ✅ Amazon Linux 2023

📦 Contém:
- Sistema operacional
- Permissões
- Configuração de disco

---

## 🖥️ Etapa 3: Tipo de instância

- Tipo: **t2.micro**

📊 Especificações:
- 1 vCPU
- 1 GiB RAM

---

## 🔑 Etapa 4: Par de chaves

- Selecionar: **vockey**

🔐 Usado para acesso seguro à instância.

---

## 🌐 Etapa 5: Rede

- Clique em **Editar**
- VPC: **Lab VPC**
- Sub-rede: **PublicSubnet1**

### 🔥 Grupo de segurança

- Nome: **Web Server security group**
- Remova regra existente ❌

📌 Funciona como firewall.

---

## 💾 Etapa 6: Armazenamento

- Manter padrão: **8 GiB**

---

## ⚡ Etapa 7: Detalhes avançados

- 🔒 Ativar proteção contra encerramento

📜 Script de inicialização (não incluído):
- Instala Apache
- Inicia servidor
- Cria página web

---

## ▶️ Etapa 8: Executar instância

- Clique em **Executar**
- Vá em **Visualizar instâncias**
- Selecione **Web Server**

⏳ Aguarde:
- Estado: **Em execução**
- Status: **2/2 checks ✅**

---

# 📊 Tarefa 2: Monitorar a instância

## ✅ Status
- Verifique:
  - Sistema ✔️
  - Instância ✔️

## 📈 Monitoramento
- Métricas via CloudWatch
- Atualização a cada 5 min

## 🧾 Logs
- Ações → Monitorar → **Log do sistema**

## 🖼️ Captura de tela
- Ações → Monitorar → **Screenshot**

---

# 🌍 Tarefa 3: Acessar servidor web

- 📋 Copie o IPv4 público
- 🌐 Abra no navegador

## ❌ Problema
Não abre a página

## 🤔 Motivo
Porta 80 bloqueada

## ✅ Solução

- Vá em **Grupos de segurança**
- Adicione regra:

  - Tipo: HTTP  
  - Origem: Anywhere IPv4 🌎  

- Salve 💾

🔄 Atualize a página

🎉 Resultado:
**Hello From Your Web Server!**

---

# 🔄 Tarefa 4: Redimensionar instância

## ⏹️ Parar instância
- Estado → Interromper

## 🔧 Alterar tipo
- Novo tipo: **t2.small**

## 🔒 Proteção contra interrupção
- Ativar

## 💽 Aumentar disco
- 8 → 10 GiB

## ▶️ Iniciar novamente

---

# 📏 Tarefa 5: Limites do EC2

- 🔍 Acesse **Service Quotas**
- Filtre por EC2

📌 Veja limites como:
- Instâncias em execução

---

# 🛑 Tarefa 6: Proteção contra interrupção

## 🚫 Teste
- Tente interromper → erro

## 🔓 Desativar
- Configurações → desmarcar proteção

## ⏹️ Interromper novamente

---

# 🎯 Conclusão

Você:

- 🚀 Criou uma instância EC2  
- 🔐 Configurou segurança  
- 🌐 Publicou um servidor web  
- 📊 Monitorou métricas  
- 🔄 Redimensionou recursos  
- 🛑 Testou proteções  

🎉 Parabéns!