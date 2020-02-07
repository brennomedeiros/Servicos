# Instalando e configurando servidor Apache no Linux 18.04

Para completar esse tutorial, você vai precisar ter um servidor Ubuntu 18.04 com uma conta de usuário que não seja root, com privilégios sudo configurada e um firewall básico. Isso poe ser configurado utilizando nosso guia de Configuração Inicial de servidor com Ubuntu 18.04.

## Instalação do Apache e Atualização do Firewall

O servidor web Apache está entre os servidores web mais populares do mundo. É bem documentado, e tem sido amplamente utilizado em grande parte da história da web, o que faz dele uma ótima escolha padrão para hospedar um website.

Instale o Apache utilizando o gerenciador de pacotes do Ubuntu, apt:

    sudo apt update
    sudo apt install apache2

Como estamos utilizando um comando sudo, essas operações são executadas com privilégios de root. Ele irá pedir a senha do usuário comum para verificar suas intenções.

Uma vez que você tenha digitado sua senha, o apt irá lhe dizer quais pacotes ele planeja instalar e quanto de espaço extra em disco ele irá consumir. Pressione Y e aperte Enter para continuar, e a instalação prosseguirá.

## Ajustar o Firewall para Permitir Tráfego Web

Agora, assumindo que você seguiu as instruções de configuração inicial do servidor para habilitar o firewall UFW, certifique-se de que seu firewall permite tráfego HTTP e HTTPS. Você pode certificar-se de que o UFW tem um perfil de aplicativo para o Apache assim:

    sudo ufw app list

Output
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH

Se você olhar para o perfil Apache Full, ele deve mostrar que ele habilita tráfego para as portas 80 e 443:

    sudo ufw app info "Apache Full"

Output
Profile: Apache Full
Title: Web Server (HTTP,HTTPS)
Description: Apache v2 is the next generation of the omnipresent Apache web
server.

Ports:
  80,443/tcp

Permita o tráfego entrante HTTP e HTTPS para esse perfil:

    sudo ufw allow in "Apache Full"

Você pode fazer uma verificação imediata para verificar se tudo correu como planejado visitando o endereço IP público do seu servidor no seu navegador web (Veja a nota abaixo do próximo cabeçalho para descobrir qual é o seu endereço IP público se você ainda não tiver essa informação):

http://ip_do_seu_servidor

##
