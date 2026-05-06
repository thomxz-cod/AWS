# 💾 Tarefa 1: Criar um novo volume do EBS

Nesta tarefa, você criará e associará um volume do Amazon EBS a uma instância EC2.

## ⚙️ Passos

* 🔍 Acesse **EC2**
* 📂 Vá em **Instâncias**
* Observe a instância **Lab**
* 📍 Anote a **Zona de Disponibilidade**

---

## 📦 Criar volume

* Vá em **Volumes**
* Clique em **Criar volume**

Configuração:

* Tipo: **SSD gp2**
* Tamanho: **1 GiB**
* Zona: mesma da instância
* Tag:

  * Name: **My Volume**

✅ Criar volume
⏳ Aguarde: **Disponível**

---

# 🔗 Tarefa 2: Associar volume

* Selecione o volume
* Ações → **Anexar volume**
* Instância: **Lab**
* Dispositivo: `/dev/sdf`

✅ Estado: **Em uso**

---

# 💻 Tarefa 3: Conectar na instância

* Vá em **Instâncias**
* Selecione **Lab**
* Clique em **Conectar**
* Use **EC2 Instance Connect**

---

# 🧩 Tarefa 4: Configurar sistema de arquivos

## 📊 Ver armazenamento atual

```bash
df -h
```

## 🛠️ Criar sistema de arquivos

```bash
sudo mkfs -t ext3 /dev/sdf
```

## 📁 Criar diretório

```bash
sudo mkdir /mnt/data-store
```

## 🔗 Montar volume

```bash
sudo mount /dev/sdf /mnt/data-store
```

## 🔄 Montagem automática

```bash
echo "/dev/sdf   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```

## 🔍 Verificar configuração

```bash
cat /etc/fstab
```

## 📊 Ver armazenamento novamente

```bash
df -h
```

---

## 📝 Criar arquivo

```bash
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```

## 🔎 Verificar arquivo

```bash
cat /mnt/data-store/file.txt
```

---

# 📸 Tarefa 5: Criar snapshot

* Vá em **Volumes**
* Selecione volume
* Ações → **Criar snapshot**

Tag:

* Name: **My Snapshot**

⏳ Aguarde: **Concluído**

---

## 🗑️ Excluir arquivo

```bash
sudo rm /mnt/data-store/file.txt
```

## 🔎 Verificar exclusão

```bash
ls /mnt/data-store/
```

---

# ♻️ Tarefa 6: Restaurar snapshot

## 📦 Criar volume do snapshot

* Vá em **Snapshots**
* Selecione snapshot
* Ações → **Criar volume**

Tag:

* Name: **Restored Volume**

---

## 🔗 Anexar volume restaurado

* Vá em **Volumes**
* Selecione **Restored Volume**
* Ações → **Associar volume**
* Instância: **Lab**
* Dispositivo: `/dev/sdg`

---

## 📁 Montar volume restaurado

```bash
sudo mkdir /mnt/data-store2
sudo mount /dev/sdg /mnt/data-store2
```

## 🔎 Verificar arquivo restaurado

```bash
ls /mnt/data-store2/
```

✅ Deve conter o arquivo `.txt`

---

# 🎯 Conclusão

Você:

* 💾 Criou um volume EBS
* 🔗 Associou à EC2
* 🧩 Criou sistema de arquivos
* 📝 Adicionou arquivo
* 📸 Criou snapshot
* ♻️ Restaurou volume
* 🔍 Validou dados

🎉 Parabéns!
