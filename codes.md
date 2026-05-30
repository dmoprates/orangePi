# Códigos para implementação da Orange Pi

---------

## Observações gerais

Para este projeto, está sendoo considerado o sistema operacional Debian Bookworm (Debian 12), disponível para download na página oficial do fabricante (Orange Pi)

No momento da criação deste documento (Maio 2026), o sistema está compilado no kernel 5.15.147

---------

### Configurações do Sistema Operacional

1. Atualização do sistema

    ``` bash
    sudo apt update
    ```

    ``` bash
    sudo apt upgrade
    ```

2. Alteração da senha padrão

    ``` bash
    sudo passwd orangepi
    ```

    ``` bash
    sudo passwd root
    ```

3. Adicionar novo usuário

    ```bash
    sudo adduser {nome_usuário}
    ```

    Elevar níveis de permissão

     ```bash
    sudo usermod -aG sudo {nome_usuário}
    ```

4. Alterar usuário padrão

    * Inicialização do sistema:

    ```bash
    sudo auto_login_cli.sh {nome_usuário}
    ```

    * Terminal

    ```bash
    sudo desktop_login.sh dmop
    ```

5. Alterar datetime

    * Configuração automática

    ```bash
    sudo timedatectl set-ntp true
    ```

    * Configuração Fuso-Horário

    ```bash
    sudo timedatectl set-timezone America/Sao_Paulo
    ```

6. Alterar encoding

    ```bash
    sudo dpkg-reconfigure locales
    ```

    * navegar com as setas do mouse até encontrar "pt-BR.UTF-8" e pressionar enter para confirmar

---------

### Instalação de aplicações

1. CasaOS - Serviço que transforma a orange pi em uma espécie de nuvem privada com diversos aplicativos

    ```bash
    curl -fsSL https://get.casaos.io | sudo bash
    ```

    obs. Para configurar o acesso externo, nesta versão do linux que não possui módulo TUN disponível, é necessário criar um tunel no cloudflare. A configuração é bem simples, porém é necessário ter um domínio cadastrado. A utilização desse serviço passa pela instalação do aplicativo "cloudflared" no casaOS e a configuração da rota na consolde de administração da CloudFlare.

2. Habilitar Docker

    * O docker vem por padrão instalado, mas é necessário realizar a habilitação do mesmo. Para isso basta executar o comando abaixo:

    Instalação:

    ``` bash
    enable_docker.sh
    ```

    Teste:

    ``` bash
    docker run hello-world
    ```

    Configuração para permissão de usuário

    ``` bash
    sudo usermod -aG docker ${nome_usuário}
    ```
