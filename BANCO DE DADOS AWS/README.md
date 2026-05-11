# 🚀 Laboratório AWS RDS + EC2

Este guia apresenta o passo a passo para configurar um ambiente com **Amazon RDS MySQL Multi-AZ**, integrando-o a uma aplicação web hospedada em uma instância EC2. ☁️

---

# 📌 Tarefa 1: Criar um Grupo de Segurança para o RDS

Nesta etapa, será criado um **Security Group** para permitir que o servidor web acesse a instância do banco de dados RDS.

## 🔹 Passo a passo

1. No **Console de Gerenciamento da AWS**, pesquise por **VPC**.

2. No menu lateral esquerdo, clique em **Grupos de segurança**.

3. Clique em **Criar grupo de segurança** e configure:

| Campo | Valor |
|---|---|
| 🏷️ Nome do grupo de segurança | `DB Security Group` |
| 📝 Descrição | `Permit access from Web Security Group` |
| 🌐 VPC | `Lab VPC` |

> 💡 Dica: remova a VPC selecionada automaticamente e escolha **Lab VPC**.

---

## 🔐 Configurar regra de entrada

1. Em **Regras de entrada**, clique em **Adicionar regra**.

2. Configure:

| Campo | Valor |
|---|---|
| Tipo | `MySQL/Aurora (3306)` |
| Origem | `Web Security Group` |

✅ Isso permitirá conexões na porta **3306** a partir das instâncias EC2 associadas ao grupo de segurança web.

3. Clique em **Criar grupo de segurança**.

---

# 📌 Tarefa 2: Criar um Grupo de Sub-redes do Banco de Dados

Nesta etapa, será criado um **DB Subnet Group**, utilizado pelo Amazon RDS para definir quais sub-redes poderão hospedar o banco de dados.

## 🔹 Passo a passo

1. No console da AWS, pesquise por **RDS**.

2. No menu lateral, clique em **Grupos de sub-redes**.

> ⚠️ Caso o menu não apareça, clique no ícone ☰ no canto superior esquerdo.

3. Clique em **Criar grupo de sub-redes de banco de dados**.

4. Configure:

| Campo | Valor |
|---|---|
| 🏷️ Nome | `DB-Subnet-Group` |
| 📝 Descrição | `DB Subnet Group` |
| 🌐 VPC | `Lab VPC` |

---

## 🌍 Adicionar Sub-redes

1. Em **Zonas de Disponibilidade**, selecione:

- `us-east-1a`
- `us-east-1b`

2. Em **Sub-redes**, selecione:

- `10.0.1.0/24`
- `10.0.3.0/24`

✅ As sub-redes aparecerão na tabela de sub-redes selecionadas.

3. Clique em **Criar**.

---

# 📌 Tarefa 3: Criar uma Instância Amazon RDS

Nesta etapa, será criada uma instância **MySQL Multi-AZ** utilizando o Amazon RDS.

## 🛠️ Benefícios do Multi-AZ

✨ Alta disponibilidade  
✨ Replicação automática  
✨ Maior durabilidade  
✨ Failover automático

---

## 🔹 Criando o banco de dados

1. No menu lateral do RDS, clique em **Bancos de dados**.

2. Clique em **Criar banco de dados**.

3. Caso apareça a opção:
   - **Switch to the new database creation flow**
   - Clique nela.

---

## ⚙️ Configurações do banco

### 🔸 Opções do mecanismo

| Campo | Valor |
|---|---|
| Banco de dados | `MySQL` |

---

### 🔸 Modelos

| Campo | Valor |
|---|---|
| Modelo | `Dev/teste` |

---

### 🔸 Disponibilidade e durabilidade

| Campo | Valor |
|---|---|
| Implantação | `Instância de banco de dados Multi-AZ` |

---

### 🔸 Configurações principais

| Campo | Valor |
|---|---|
| 🏷️ Identificador | `lab-db` |
| 👤 Usuário principal | `main` |
| 🔑 Senha | `lab-password` |

---

### 🔸 Classe da instância

| Campo | Valor |
|---|---|
| Classe | `db.t3.micro` |

✅ Escolha:
- **Classes com capacidade de intermitência (inclui classes t)**

---

### 🔸 Armazenamento

| Campo | Valor |
|---|---|
| Tipo | `Uso geral (SSD)` |
| Tamanho | `20 GB` |

---

### 🔸 Conectividade

| Campo | Valor |
|---|---|
| 🌐 VPC | `Lab VPC` |
| 🔐 Grupo de segurança | `Grupo de segurança do banco de dados` |

⚠️ Remova o grupo de segurança padrão.

---

### 🔸 Monitoramento

❌ Desmarque:
- `Habilitar monitoramento avançado`

---

### 🔸 Configuração adicional

| Campo | Valor |
|---|---|
| Nome inicial do banco | `lab` |

❌ Desmarque:
- `Habilitar backups automáticos`
- `Habilitar criptografia`

> ⚠️ Em ambientes reais, backups e criptografia são altamente recomendados.

---

## 🚀 Finalizando

1. Clique em **Criar banco de dados**.

2. Aguarde aproximadamente **4 minutos** ⏳.

3. Quando o status mudar para:
- `Modificando`
ou
- `Disponível`

o banco estará pronto ✅

---

## 🌐 Copiar Endpoint

1. Acesse a instância `lab-db`.

2. Vá até:
- **Conectividade e segurança**

3. Copie o campo Endpoint.

Exemplo:

lab-db.xxxx.us-east-1.rds.amazonaws.com

💾 Salve esse valor, ele será usado na próxima etapa.

---

# 📌 Tarefa 4: Interagir com o Banco de Dados

Agora será feita a conexão da aplicação web com o banco RDS. 🌐

---

## 🔹 Abrir aplicação web

1. Copie o IP do `WebServer` em:
- **Detalhes da AWS**

2. Abra uma nova aba do navegador.

3. Cole o IP e pressione **Enter**.

✅ A aplicação web será exibida.

---

## 🔹 Configurar conexão RDS

1. Clique no link **RDS** no topo da página.

2. Configure:

| Campo | Valor |
|---|---|
| Endpoint | `Endpoint copiado anteriormente` |
| Banco de dados | `lab` |
| Usuário | `main` |
| Senha | `lab-password` |

3. Clique em **Enviar**.

---

# 📒 Resultado Esperado

Após alguns segundos:

✅ O sistema criará as tabelas automaticamente  
✅ Será exibido um **Address Book**  
✅ Os dados serão armazenados no Amazon RDS  
✅ A replicação Multi-AZ acontecerá automaticamente

---

# 🧪 Testes

Você pode:

- ➕ Adicionar contatos
- ✏️ Editar contatos
- ❌ Remover contatos

Todos os dados serão persistidos no banco de dados RDS. 🎉

---

# ☁️ Tecnologias Utilizadas

- 🟧 Amazon EC2
- 🟦 Amazon RDS
- 🛡️ Security Groups
- 🌐 VPC
- 🗄️ MySQL
- 🔄 Multi-AZ Deployment

---

# ✅ Conclusão

Neste laboratório você aprendeu a:

✔️ Criar grupos de segurança  
✔️ Configurar sub-redes para RDS  
✔️ Implantar um banco MySQL Multi-AZ  
✔️ Conectar uma aplicação web ao banco  
✔️ Testar persistência e replicação de dados

🚀 Ambiente AWS configurado com sucesso!