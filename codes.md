# Comandos Shell - ORANGE PI 4 PRO

## Primeira inicialização

* Atualização do sistema operacional ⚠️:

``` bash
sudo apt update
sudo apt upgrade -y
```

* Alterar senha padrão ⚠️

``` bash
sudo passwd orangepi
sudo passwd root
```

* Criação de usuário 🙋🏻‍♂️

``` bash
sudo adduser diego
sudo usermod -aG sudo diego
```

* Login automático usuário "diego"

``` bash
sudo auto_login_cli.sh diego #Login automático no terminal
sudo desktop_login.sh diego #Login automático no sistema
```

## Segunda Inicialização

*Instalando Firefox 

Rever, pois o comando não funcionou!! 😪

``` bash
sudo snap install firefox-esr

# OU

sudo snap remove firefox
sudo add-apt-repository ppa:mozillateam/ppa
echo '
Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
' | sudo tee /etc/apt/preferences.d/mozilla-firefox
sudo apt update
sudo apt install firefox
```

*Instalando Chromium

Rever, pois o comando não funcionou!! 😪

``` bash
sudo apt install chromium chromium-l10n -y

# OU

sudo apt install snapd
sudo snap install chromium
```

* Instalando o Gparted para verificar espaço de disco

``` bash
sudo apt install -y gparted
sudo gparted
df -h #verifica o tamanho do rootfs
```

* Habilitando acesso SSH

``` bash
ip addr show wlan0
ping #para sair acionar Ctrl+C
sudo nmtui #Setar IP estático
# Clicar em editar conexão, mudar para "manual" e inserir o IP desejado
# No meu caso será utilizado: IP: 192.168.3.144/24 Gateway: 192.168.3.1 DNS 8.8.8.8
#Desconectar e conectar na rede novamente e ver se o IP foi alterado.
ssh diego@192.168.3.144
#em caso de falha usar o comando abaixo:
sudo reset_ssh.sh
```

* Instalando o Python

``` bash
sudo apt-get update
sudo apt-get install -y build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libsqlite3-dev libreadline-dev libffi-dev curl libbz2-dev
wget \ https://www.python.org/ftp/python/3.9.10/Python-3.9.10.tgz
tar xvf Python-3.9.10.tgz
cd Python-3.9.10
./configure --enable-optimizations
make -j4
sudo make altinstall
/usr/local/bin/python3.9 -m pip install --upgrade pip
```

* Instalando o Docker

``` bash
enable_docker.sh
docker run hello-world
sudo usermod -aG docker $diego
```

* Instalando OpenCV

``` bash
sudo apt-get update
sudo apt-get install -y libopencv-dev python3-opencv
python3 -c "import cv2; print(cv2.__version__)"

```

* Instalando QT

``` bash
install_qt.sh
qtcreator
```

* Instalando CasaOS

``` bash
curl -fsSL https://get.casaos.io | sudo bash
```

### Modelo base
``` bash

```