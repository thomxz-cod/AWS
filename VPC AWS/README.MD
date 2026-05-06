# 🌐 Laboratório 2: Criar a VPC e executar um servidor web

---

## 🎯 Visão geral e objetivos do laboratório

Neste laboratório, você usará a **Amazon VPC** para criar sua própria rede virtual personalizada 🏗️.  
Você também irá:

- 🔐 Criar um grupo de segurança  
- 💻 Configurar uma instância EC2  
- 🌍 Executar um servidor web  

A Amazon VPC permite criar redes isoladas dentro da AWS, semelhantes a um data center tradicional, mas com escalabilidade ☁️.

---

### ✅ Ao final, você será capaz de:

- 🧱 Criar uma VPC  
- 🌐 Criar sub-redes  
- 🔒 Configurar grupo de segurança  
- 🚀 Executar uma instância EC2  

---

## ⏱️ Duração

Aproximadamente **30 minutos**

---

## ⚠️ Restrições

- Alguns serviços podem estar limitados 🚫  
- Use apenas o que for solicitado  

---

## 🧪 Cenário

Você irá construir uma infraestrutura completa de rede na AWS.

---

## 🔑 Acessar o Console AWS

1. ▶️ Clique em **Iniciar laboratório**
2. ⏳ Aguarde o cronômetro iniciar
3. 🟢 Espere o ícone da AWS ficar verde
4. 🌐 Abra o console AWS (nova aba)
5. 🪟 Organize as telas lado a lado

---

## 🏆 Como obter crédito

- 📤 Envie o laboratório ao final  
- 🧾 Use nomes EXATOS (case-sensitive)

---

# 🧱 Tarefa 1: Criar a VPC

### 🔎 Passos:

1. Vá em **Serviços → VPC**
2. Clique em **Criar VPC**

---

### ⚙️ Configuração:

- 🏷️ Nome: `lab`
- 🌍 CIDR: `10.0.0.0/16`
- 📍 AZs: `1`
- 🌐 Sub-redes públicas: `1`
- 🔒 Sub-redes privadas: `1`

---

### 🧩 CIDR personalizados:

- 🌐 Pública: `10.0.0.0/24`
- 🔒 Privada: `10.0.1.0/24`

---

### ⚡ Outras configs:

- 🔁 NAT Gateway: `1 AZ`
- 🚫 Endpoints: `Nenhum`
- 🧭 DNS: ativado

---

### ▶️ Criar

- Clique em **Criar VPC**
- ⏳ Aguarde finalizar

---

## 🧠 Conceitos importantes

- 🌍 **Internet Gateway** → acesso público  
- 🔁 **NAT Gateway** → internet para rede privada  
- 🌐 **Sub-rede pública** → acesso direto  
- 🔒 **Sub-rede privada** → acesso via NAT  

---

# 🌐 Tarefa 2: Criar sub-redes adicionais

## ➕ Sub-rede pública

- 🏷️ Nome: `lab-subnet-public2`
- 📍 AZ: `us-east-1b`
- 🌍 CIDR: `10.0.2.0/24`

---

## ➕ Sub-rede privada

- 🏷️ Nome: `lab-subnet-private2`
- 📍 AZ: `us-east-1b`
- 🔒 CIDR: `10.0.3.0/24`

---

## 🔁 Configurar rotas

### 🔒 Privadas

- Associar à: `lab-rtb-private1-us-east-1a`

### 🌐 Públicas

- Associar à: `lab-rtb-public`

---

# 🔒 Tarefa 3: Grupo de segurança

## ➕ Criar

- 🏷️ Nome: `Web Security Group`
- 📝 Descrição: `Enable HTTP access`
- 🌐 VPC: `lab-vpc`

---

### 🚪 Regra de entrada

- 📡 Tipo: HTTP  
- 🌍 Origem: Anywhere IPv4  
- 📝 Descrição: Permit web requests  

---

# 💻 Tarefa 4: EC2 (Servidor Web)

## 🚀 Criar instância

- 🏷️ Nome: `Web Server 1`
- 🖥️ AMI: Amazon Linux 2023
- ⚙️ Tipo: `t2.micro`
- 🔑 Key pair: `vockey`

---

## 🌐 Rede

- VPC: `lab-vpc`
- Sub-rede: `lab-subnet-public2`
- 🌍 IP público: ativado
- 🔒 Security Group: `Web Security Group`

---

## 🧪 Teste

1. ⏳ Aguarde **2/2 checks**
2. 📋 Copie o **Public IPv4 DNS**
3. 🌐 Cole no navegador
4. ✅ Verifique o funcionamento da aplicação web

---

# 📤 Envio

1. Clique em **Enviar**
2. ✔️ Confirme
3. 📊 Veja sua nota
4. 🔍 Consulte relatório

---

# 🎉 Finalização

Parabéns! 🚀

- ⛔ Clique em **Encerrar laboratório**
- ✔️ Confirme
- ❌ Feche o painel

---

© AWS