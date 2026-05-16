# :notebook_with_decorative_cover: Códigos para implementação do Orange Pi

## Debian Bullseye

-----

## :computer: Setup inicial

Acessar o menu "Orange Pi Config"

* Alterar timezone para São Paulo;
* Alterar encoding para UTF-8;
* Atualizar Firmware;
* Restartar serviço SSH;
* Alterar nome do Host (Requer reinicialização)

## :pager: Terminal commands

:repeat: Atualização do Sistema Operacional

```bash
sudo apt update && upgrade -y 
sudo apt dist-upgrade -y 
sudo apt autoremove -y 
sudo reboot 
```

Navegador de internet deve ser instalado da loja - Chromium

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

## Softwares

Docker

``` bash
enable_docker.sh
docker run hello-world
sudo usermod -aG docker $diego
```
