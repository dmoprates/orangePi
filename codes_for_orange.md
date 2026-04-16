# :notebook_with_decorative_cover: Codes for implementation

-----

## :computer: Starter setup

Acessar o menu "Orange Pi Config"

* Alterar timezone para São Paulo;
* Alterar encoding para UTF-8;
* Atualizar Firmware;
* Restartar serviço SSH;
* Alterar nome do Host (Requer reinicialização)

Instalação de Aplicações

* Instalar Chromium através da loja do Debian

-----

## :pager: Terminal commands

:repeat: Atualização do Sistema Operacional

```bash
sudo apt update #Update Package Lists: Run the following command to fetch the latest package information
sudo apt upgrade -y #Upgrade Packages: Upgrade installed packages to their latest versions:
sudo apt dist-upgrade -y #Full Upgrade: If you need to handle changing dependencies
sudo apt autoremove -y #Remove unnecessary packages
sudo reboot #Reboot: Reboot the system to apply kernel updates
```

:bust_in_silhouette: Criação de novo usuário

```bash
sudo adduser dmop
sudo usermod -aG sudo dmop
```

:warning: Alterar senha padrão

``` bash
sudo passwd orangepi #Inserir nova senha solicitada no terminal
sudo passwd root #Inserir nova senha solicitada no terminal
```

:traffic_light: Alterar usuário de login automático

``` bash
sudo auto_login_cli.sh dmop #Login automático no terminal
sudo desktop_login.sh dmop #Login automático no sistema
```

-----

## Pacotes seguindo recomendações do GPT

* Pacotes básicos do sistema:

```bash
sudo apt install sudo locales tzdata bash-completion apt-transport-https ca-certificates software-properties-common
```

* Ferramentas de build e compilação

```bash
sudo apt install build-essential make cmake gcc g++ pkg-config
```

* Rede e diagnóstico

```bash
sudo apt install net-tools iproute2 iputils-ping dnsutils curl wget traceroute nmap
```

* Gerenciamento e utilitários de sistema

```bash
sudo apt install htop neofetch tree unzip zip rsync screen tmux nano vim less ncdu git
```

* Segurança básica

```bash
sudo apt install openssh-server ufw fail2ban
#Ativar as aplicações instaladas:
sudo systemctl enable ssh
sudo ufw enable
```

* Suporte a sistemas de arquivos

```bash
sudo apt install exfat-fuse exfatprogs ntfs-3g dosfstools parted lsblk
```

* Firmware e suporte ARM / SBC

```bash
sudo apt install firmware-linux firmware-linux-free device-tree-compiler u-boot-tools
```

* Monitoramento

```bash
sudo apt install lm-sensors sysstat iotop
#Configuração
sudo sensors-detect
```

* Ajustes recomendados

```bash
sudo apt install dphys-swapfile
```

-----

## Softwares

Gparted

``` bash
sudo apt install -y gparted
sudo gparted
df -h #verifica o tamanho do rootfs
```

Docker

``` bash
enable_docker.sh
docker run hello-world
sudo usermod -aG docker $diego
```

QT

``` bash
install_qt.sh
qtcreator
```

Servidor Básico

```bash
sudo apt install cron rsyslog logrotate
```

Sincronização de Tempo

```bash
sudo apt install systemd-timesyncd
```

WebServer

```bash
sudo apt install nginx
```

# Ip Público ation.dev.br -> 198.51.44.4
