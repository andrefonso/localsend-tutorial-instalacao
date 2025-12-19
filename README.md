# Tutorial: Instalação e Configuração do LocalSend no Ubuntu

O **LocalSend** é uma ferramenta gratuita e open source que permite transferir arquivos entre dispositivos na **mesma rede local**, de forma rápida e segura, sem necessidade de internet ou serviços em nuvem. Ele funciona entre Linux, Windows, macOS, Android e iOS.

---

## 📌 Requisitos

- Ubuntu 20.04 ou superior (funciona também em derivados como Linux Mint e Zorin OS)
- Conexão de rede local (Wi‑Fi ou cabo)
- Permissões de administrador (sudo)

---

## 🔹 Método 1: Instalação via Flatpak (Recomendado)

Este é o método mais simples e confiável, pois o LocalSend é oficialmente distribuído via Flatpak.

### 1️⃣ Instalar o Flatpak (caso ainda não tenha)

Abra o terminal e execute:

```bash
sudo apt update
sudo apt install flatpak -y
```

Adicione o repositório Flathub:

```bash
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

Reinicie o sistema ou faça logout/login para garantir a integração com o sistema gráfico.

---

### 2️⃣ Instalar o LocalSend

No terminal:

```bash
flatpak install flathub org.localsend.localsend_app
```

Confirme a instalação quando solicitado.

---

### 3️⃣ Executar o LocalSend

- Pelo menu de aplicativos: procure por **LocalSend**
- Ou pelo terminal:

```bash
flatpak run org.localsend.localsend_app
```

---

## 🔹 Método 2: Instalação via AppImage

Útil se você não quiser usar Flatpak.

### 1️⃣ Baixar o AppImage

Baixe o arquivo `.AppImage` mais recente no site oficial do LocalSend.

### 2️⃣ Tornar o arquivo executável

No diretório onde o arquivo foi baixado:

```bash
chmod +x LocalSend-*.AppImage
```

### 3️⃣ Executar

```bash
./LocalSend-*.AppImage
```

> 💡 Dica: você pode mover o AppImage para `~/Applications` ou `/opt` e criar um atalho no menu.

---

## ⚙️ Configuração Inicial do LocalSend

Ao abrir o LocalSend pela primeira vez, faça as seguintes configurações:

### 🔸 1️⃣ Nome do dispositivo

- Vá em **Configurações**
- Defina um nome fácil de identificar (ex: `Ubuntu-Debian`, `Notebook-Sala`)

---

### 🔸 2️⃣ Pasta de recebimento

- Em **Configurações → Armazenamento**
- Escolha a pasta onde os arquivos recebidos serão salvos
- Exemplo:
  ```
  /home/seu_usuario/Downloads/LocalSend
  ```

---

### 🔸 3️⃣ Porta e rede

- Por padrão, o LocalSend detecta a rede automaticamente
- Se houver firewall ativo (UFW), libere a porta:

```bash
sudo ufw allow 53317/tcp
sudo ufw allow 53317/udp
```

Verifique o status do firewall:

```bash
sudo ufw status
```

---

### 🔸 4️⃣ Confirmação de recebimento

Você pode escolher:

- ✅ **Receber automaticamente** (menos seguro)
- 🔒 **Solicitar confirmação** (recomendado)

Essa opção fica em **Configurações → Segurança**.

---

## 🔄 Como Enviar Arquivos

1. Abra o LocalSend no Ubuntu
2. Clique em **Enviar**
3. Selecione arquivos ou pastas
4. Escolha o dispositivo de destino
5. Confirme o envio no outro dispositivo

---

## 🛠️ Solução de Problemas

### ❌ Dispositivo não aparece

- Verifique se ambos estão na **mesma rede**
- Confirme que o firewall não está bloqueando
- Teste desativar temporariamente o UFW:

```bash
sudo ufw disable
```

---

### ❌ Transferência lenta

- Prefira conexão via cabo Ethernet
- Evite redes Wi‑Fi públicas ou congestionadas

---

## ✅ Conclusão

O LocalSend é uma excelente alternativa ao AirDrop e similares, funcionando muito bem no Ubuntu e em outros sistemas Linux. A instalação via Flatpak é a mais recomendada por garantir atualizações fáceis e compatibilidade.


## ❗ LocalSend não aparece no menu do Ubuntu

Se o LocalSend foi instalado via Flatpak mas não aparece no menu ou lista dos aplicativos digite o comando abaixo e em seguida reinicie o sistema:

```bash
sudo apt install gnome-software-plugin-flatpak

