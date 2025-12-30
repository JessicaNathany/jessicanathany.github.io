---
layout: post
title: "Como uso o Let's Encrypt para proteger meu site com SSL gratuito"
date: 2025-12-30
lang: pt
cover: "/assets/img/ssl-artigo.jpg"
excerpt: "Aprenda como implementei certificados SSL gratuitos com Let's Encrypt no site do Café Debug, incluindo automação com Certbot e crontab."
tags: [ssl, security, devops]
---

## Introdução


Quando publiquei o site do [Café Debug](www.cafedebug.com.br), percebi a necessidade de instalar um certificado SSL. Além de garantir a segurança dos dados, era essencial transmitir confiança aos usuários e melhorar indexação no Google. Desde de agosto de 2019, o Google começou a penalizar sites que não possuem um certificado digital de segurança SSL. Isso significa que, se um site não exibir a URL iniciando com "https" nem apresentar o ícone de cadeado na barra de endereço, ele será considerado não seguro.

Os certificados SSL são fundamentais para proteger os dados dos usuários, verificar a propriedade do domínio, impedir que invasores criem versões falsas de um site e reforçar a credibilidade.

## O que é um certificado de SSL

O SSL (Secure Sockets Layer) é um protocolo de internet que criptografa dados enviados entre navegadores e servidores. Ele é uma tecnologia padrão para garantir a privacidade das informações transmitidas. O SSL impede que hackers vejam ou roubem dados pessoais ou financeiros, sendo inclusive uma exigência legal para empresas que lidam com informações sensíveis de seus clientes. 

Embora o site do Café Debug não armazene informações sensíveis de usuários, sendo apenas site que organiza os episódios do podcast, a segurança do domínio é essencial. Afinal, se alguém for acessar e encontrar uma mensagem em vermelho "Esse site não é seguro", a credibilidade pode ser afetada, não é mesmo?

<br />
<div align="center">
  <img src="/assets/img/cloudflare-ssl.png" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

## Sobre o Let's Encrypt

Alguns provedores de cloud oferecem serviços de certificado SSL, entretanto eu procurava algo gratuito e open source, para não aumentar ainda mais os custos com o site. Após algumas pesquisas, descobri o Let's Encrypt — uma solução gratuita e open source — e decidi testá-la.

A [Let’s Encrypt](https://letsencrypt.org/pt-br/about/) é uma autoridade certificadora (AC) gratuita, automatizada e aberta que opera em prol do benefício público. É um serviço provido pela [Internet Security Research Group (ISRG)](https://www.abetterinternet.org/). Fornecendo gratuitamente os certificados digitais necessários para habilitar (SSL/TLS) em websites de maneira mais amigável possível. 

É preciso renovar o certificado a cada três meses. Normalmente, a Let's Encrypt envia um email notificando sobre a renovação, basta seguir simples comandos (que explicarei mais adiante) para renova-lo. Entretanto, recentemente, a Let's Encrypt comunicou aos usuários que deixará de enviar esses emails de aviso. Ou seja, aquele lembrete que eu recebia cerca de um mês antes da expiração do certificado não será mais enviado.

Os motivos declarados no site do Let's Encrypt são: traduzido diretamente do site: "Desde o seu início, a Let's Encrypt tem enviado e-mails de notificação de expiração para assinantes que nos forneceram um endereço de e-mail. Encerraremos este serviço em 4 de junho de 2025. A decisão de encerrar este serviço é o resultado dos seguintes fatores:

1. Nos últimos 10 anos, cada vez mais assinantes conseguiram implementar automação confiável para renovação de certificados.

2. Fornecer e-mails de notificação de expiração significa que temos que reter milhões de endereços de e-mail conectados a registros de emissão. Como uma organização que valoriza a privacidade, remover esse requisito é importante para nós.

3. Fornecer notificações de expiração custa à Let's Encrypt dezenas de milhares de dólares por ano, dinheiro que acreditamos que poderia ser melhor gasto em outros aspectos da nossa infraestrutura.

4. Fornecer notificações de expiração adiciona complexidade à nossa infraestrutura, o que leva tempo e atenção para gerenciar e aumenta a probabilidade de erros serem cometidos. A longo prazo, particularmente à medida que adicionamos suporte para novos componentes de serviço, precisamos gerenciar a complexidade geral eliminando gradualmente os componentes do sistema que não podem mais ser justificados."

Ou seja, essa foi aúnica mudança. O Let's Encrypt continua funcionando normalmente como CA (Autoridade Certificadora). No próprio comunicado, eles indicam um serviço de terceiros, como Red Sift Certificate Lite. A mudança foi porque a maioria dos usuários automatizou a renovação, assim como eu que explicarei logo mais abaixo, redução de custos e complexidade para Let's Encrypt.

## Começando a usar Let's Encrypt

Para ativar o HTTPS em seu site, você precisa obter um certificado (um tipo de arquivo) emitido por uma Autoridade Certificadora (CA), neste caso mostrarei o exemplo com a Let's Encrypt. No exemplo que darei a seguir, estou utilizando uma máquina EC2 Linux Unbuntu na AWS. Minha aplicação ASPNET Core MVC está rodando em um container Docker, utilizando um Nginx como proxy reverso.

Primeiramente, execute o comando abaixo para verificar se o Certbot está instalado. O Certbot é uma ferramenta gratuita e de código aberto que automatiza processo de obtenção e renovação de certificados SSL/TLS do Let's Encrypt. O exemplo que exibirei abaixo é uma máquina Linux Ubuntu.

1. Vamos verificar se o Certbot está instalado e caso não esteja, digite o segundo comando para instalar.

```bash
certbot --version
```

```bash
sudo apt update
sudo apt install certbot python3-certbot-nginx
```

Caso esteja usando Apache ao invés de Nginx, utilize o comando abaixo

```bash
sudo apt install certbot python3-certbot-apache
```

2. Gerar certificado SSL
O próximo passo é executar o comando abaixo para criar um novo certificado SSL. No meu caso, acabei gerando dois: um com o "www" e outro sem.

```bash
sudo certbot --nginx -d cafedebug.com.br -d www.cafedebug.com.br
```

Esses comandos faz com que o Certbot verifique se o domínio está apontando corretamente, gere os certificados SSL e configre automaticamente o seu servidor Nginx ou Apache. Caso precise de uma configuração manual, pode digitar o comando abaixo

```bash
sudo certbot certonly --manual -d cafedebug.com.br -d www.cafedebug.com.br
```

## Automatizando o processo

Como descrevi anteriormente, o Let's Encrypt não envia mais e-mails lembrando sobre a renovação do certificado. Depois de me deparar com um e-mail antigo e de tantas vezes digitar o mesmo comando manualmente, decidi colocar esses comandos em um script e executá-lo diretamente no meu servidor. Inicialmente, o script era executado manualmente, mas com a ajudinha do copilot, consegui deixá-lo mais automatizado. Para isso, configurei a execução periódica via crontab. Crontab é um programa Unix que permite agendar tarefas serem executadas no Linux e em outros programas semelhantes.


```bash
# valida certificado SSL de forma automática

#!/bin/bash

# Função para renovar um certificado específico
renew_certificate() {
    local cert_name=$1
    echo "Renovando certificado: $cert_name..."

    sudo docker stop proxy
    sudo systemctl start nginx
    sudo certbot renew --cert-name "$cert_name"
    sudo systemctl stop nginx
    sudo docker start proxy

    echo "Renovação concluída para $cert_name!"
}

# Lista de certificados para renovar
certificates=("cafedebug.com.br" "www.cafedebug.com.br")

# Renova cada certificado
for cert_name in "${certificates[@]}"; do
    renew_certificate "$cert_name"
done
```

Para rodar de forma automatica, adiciono no crontab. Primeiro digite o comando abaixo para visualizar o crontab como root.


```bash
sudo crontab -u root -l
```

Para adicionar seu script crontab, digite o comando abaixo. Esse comando abrirá o arquivo de tarefas agendadas para seu usuário no editor de texto, pode ser vim ou nano. 


```bash
sudo crontab -u root -e
```

```bash
0 0 */89 * * /home/scripts/renew-certificate.sh
```

Há um porém, eu não tenho certeza se o crontab entenderia no linux o "/89", então pode ser que não funcione essa execução. Essa parte, confesso que ainda não teste. Uma outra sugestão seria adicionar desta forma para executar diariamente, conforme visto no comando abaixo. 


```bash
0 0 1 * * /home/cafedebug/scripts/renew-certificate.sh
```

Mas não é uma solução adequada que me agrada. Não acho uma boa ideia no caso do meu site, ficar parando o container e subindo novamente pra executar o script. Como tive alguns problemas recorrente durante a renovação do certificado, não por conta do Let's Encrypt mas porque estava fazendo errado, fico um pouco com receio de parar o container diariamente.

Enfim, como eu não sei como fazer para executar a partir de determinados dias, acabei colocando pra executar 1x ao mês. Se você tiver alguma dica de como fazer, comente aqui.

### Referência
[letsencrypt](https://letsencrypt.org/pt-br/getting-started/)

[Certbot.org](https://certbot.eff.org/pages/about)

[Amazon SSL Certificate](https://aws.amazon.com/pt/what-is/ssl-certificate/)

[Cloudflare learning SSL](https://www.cloudflare.com/pt-br/learning/ssl/what-is-ssl/)


[Letsencrypt tutorial](https://letsencrypt.org/pt-br/getting-started/)




