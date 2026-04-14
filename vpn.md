# 🔐 Servidor VPN no Orange Pi 4 Pro (Sem Port Forwarding)

Este guia mostra como configurar uma VPN moderna utilizando o Tailscale (baseado em WireGuard) para permitir acesso remoto seguro entre redes distintas **sem necessidade de abrir portas no roteador**.

---

## 🧠 Arquitetura

- Orange Pi 4 Pro → servidor principal
- Notebook / Celular → clientes
- Comunicação via rede privada (IP 100.x.x.x)

---

## ⚙️ Requisitos

- Debian 12 instalado no Orange Pi
- Acesso root ou sudo
- Conexão com internet

---

## 🔧 Instalação

### 1. Atualizar o sistema

```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Instalar Tailscale

```bash
curl -fsSL https://tailscale.com/install.sh | sh
```

### 3. Iniciar o serviço

```bash
sudo tailscale up
```

➡️ Será exibido um link para autenticação
Abra no navegador e faça login (Google, GitHub, etc.)

### 4. Verificar IP da VPN

```bash
tailscale ip -4
```

Exemplo:

```bash
100.64.0.5
```

## 🌐 Acesso remoto

Em outro dispositivo:

Instale o Tailscale
Faça login com a mesma conta
Acesse via SSH:

```bash
ssh usuario@100.x.x.x
```

## 🔁 Acessar rede interna (Subnet Router)

Permite acessar dispositivos da rede local (ex: 192.168.0.x)

### 1. Ativar IP Forwarding

```bash
echo 'net.ipv4.ip_forward = 1' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

### 2. Anunciar rota da rede

```bash
sudo tailscale up --advertise-routes=192.168.0.0/24
```

### 3. Aprovar rota

Acesse: <https://login.tailscale.com/admin/machines>
Habilite a rota anunciada

### 🔐 Recursos adicionais

#### ✔️ Habilitar SSH via Tailscale

```bash
sudo tailscale up --ssh
```

#### ✔️ Usar hostname

Exemplo

```bash
orange-pi.tailnet-name.ts.net
```
