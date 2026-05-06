# 👥 Tarefa 1: Explorar usuários e grupos (IAM)

Nesta tarefa, você irá explorar usuários e grupos no IAM.

## ⚙️ Passos iniciais

* 🔍 Acesse **IAM**
* 📂 Vá em **Usuários**

👤 Usuários disponíveis:

* user-1
* user-2
* user-3

---

## 🔎 Analisar user-1

* Clique em **user-1**

### 🔐 Permissões

* ❌ Nenhuma permissão

### 👥 Grupos

* ❌ Não pertence a nenhum grupo

### 🔑 Credenciais

* Possui senha de console

---

## 👥 Grupos de usuários

* Vá em **Grupos de usuários**

Grupos disponíveis:

* EC2-Admin
* EC2-Support
* S3-Support

---

## 📦 Grupo EC2-Support

* Clique no grupo
* Vá em **Permissões**

📜 Política:

* **AmazonEC2ReadOnlyAccess**

🔎 Permite:

* Listar recursos
* Descrever recursos

---

## 📦 Grupo S3-Support

* Política: **AmazonS3ReadOnlyAccess**

🔎 Permite:

* Listar buckets
* Ler dados

---

## 📦 Grupo EC2-Admin

* Possui **política em linha**

🔎 Permite:

* Visualizar instâncias
* Iniciar instâncias
* Parar instâncias

---

# 🧠 Cenário de negócio

| Usuário | Grupo       | Permissão           |
| ------- | ----------- | ------------------- |
| user-1  | S3-Support  | Somente leitura S3  |
| user-2  | EC2-Support | Somente leitura EC2 |
| user-3  | EC2-Admin   | Start/Stop EC2      |

---

# ➕ Tarefa 2: Adicionar usuários aos grupos

## 👤 user-1 → S3-Support

* Vá em **Grupos de usuários**
* Selecione **S3-Support**
* Aba **Usuários**
* ➕ Adicionar usuários
* Selecione **user-1**

---

## 👤 user-2 → EC2-Support

* Repita o processo
* Adicione **user-2** ao grupo

---

## 👤 user-3 → EC2-Admin

* Adicione **user-3** ao grupo

---

## ✅ Verificação

Cada grupo deve ter:

* 👤 1 usuário

---

# 🔐 Tarefa 3: Testar usuários

## 🌐 Obter URL de login

* Vá em **Painel**
* Copie a URL de login IAM

---

## 🕵️ Abrir navegador anônimo

* Chrome: Ctrl+Shift+N
* Edge: Ctrl+Shift+N
* Firefox: Ctrl+Shift+P

---

## 👤 Teste com user-1

````
Usuário: user-1
Senha: Lab-Password1
``` id="u1login"

### 🔎 Testes

- ✅ Acessa S3
- ❌ Não acessa EC2

---

## 👤 Teste com user-2

````

Usuário: user-2
Senha: Lab-Password2

```id="u2login"

### 🔎 Testes

- ✅ Visualiza EC2
- ❌ Não pode parar instância
- ❌ Não acessa S3

---

## 👤 Teste com user-3

```

Usuário: user-3
Senha: Lab-Password3

```id="u3login"

### 🔎 Testes

- ✅ Acessa EC2
- ✅ Pode parar instância

---

# 📤 Envio

- Clique em **Enviar**
- Confirme com **Sim**
- Aguarde resultado ⏳

---

# 🎯 Conclusão

Você:

- 👥 Explorou usuários IAM  
- 📜 Analisou políticas  
- ➕ Adicionou usuários a grupos  
- 🔐 Testou permissões  
- 🌐 Usou login IAM  

🎉 Laboratório concluído!
```
