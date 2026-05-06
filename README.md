# ☁️ Fundamentos da AWS

## 🌐 O que é a AWS?

A **Amazon Web Services (AWS)** é uma plataforma de computação em nuvem que oferece serviços como:

* 🖥️ Servidores virtuais (EC2)
* 💾 Armazenamento (S3, EBS)
* 🗄️ Bancos de dados
* 🌍 Redes e entrega de conteúdo

💡 Em vez de comprar servidores físicos, você **aluga recursos sob demanda pela internet**.

---

## 🌎 Infraestrutura Global

A AWS possui uma infraestrutura distribuída globalmente para garantir alta disponibilidade e desempenho.

### 📍 Regiões

* São áreas geográficas (ex: EUA, Brasil, Europa)
* Cada região é **independente**
* Permite escolher onde seus dados ficam (importante para latência e compliance)

---

### 🏢 Zonas de Disponibilidade (AZs)

* Cada região possui várias AZs
* Uma AZ = um ou mais data centers isolados

💡 Características:

* ⚡ Baixa latência entre AZs
* 🔒 Isolamento (falha em uma não afeta as outras)
* 🔁 Alta disponibilidade

---

### 🧠 Resumo

```
Região (ex: us-east-1)
 ├── AZ-1 (Data Center)
 ├── AZ-2 (Data Center)
 └── AZ-3 (Data Center)
```

---

## 💰 Economia da Nuvem

### 💳 Modelo Pay-as-you-go

Você paga apenas pelo que usa:

* ⏱️ Tempo de uso de servidores
* 💾 Armazenamento consumido
* 🌐 Tráfego de dados

❌ Sem investimento inicial
❌ Sem contratos longos obrigatórios

---

### 📉 Economia de escala

A AWS reduz custos porque:

* Compra hardware em grande escala 📦
* Otimiza uso de data centers ⚙️
* Distribui custos entre milhões de clientes 👥

💡 Resultado:

* Preços mais baixos para clientes
* Lucro baseado em **volume e eficiência**

---

### 🧾 Exemplo simples

* Você usa um servidor por 2 horas
* Paga apenas por essas 2 horas

---

## 🎯 Conclusão

A AWS permite:

* ☁️ Escalar recursos rapidamente
* 💸 Reduzir custos com pagamento sob demanda
* 🌍 Operar globalmente com alta disponibilidade

🚀 É a base da maioria das aplicações modernas na nuvem.
