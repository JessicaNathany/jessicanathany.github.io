---
layout: post

title: "Ideias de projetos backend para você praticar"

date: 2025-12-30

lang: pt

cover: "/assets/img/artigo-projeto1.jpg"

excerpt: "Idéias de projetos backend para estudar e praticar"

tags: [projetos, backend, estudos, portfolios]
---

## Introdução

Ja lhe faltou ideias para criar seus projetos e treinar suas habilidades de programação? Muitas vezes procuramos nos basear o mais próximo da realidade, é uma maneira de treinar nossas habilidades de escrever código e também, chegar o mais próximos dos problemas reais no mundo da programação.

Eu mesma enquanto estudava e treinava minhas habilidades em programação, tive dificuldade de encontrar ideias para criação de projetos backend, e olha que pesquisei bem. Pesquisei muito até juntar as ideias aqui para este artigo e compartilhar com outras pessoas. Uma ótima opção também é resolver os problemas do [Hackerrank](https://www.hackerrank.com/), mas mesmo assim é legal ter outras ideias outros desafios para poder pensar, elaborar e construir.

Pensando nisso, elaborei algumas ideias e alguns projetos cheguei a desenvolver, outros estou desenvolvendo e decidi compartilhar aqui. Algumas outras ideias, também busquei em uma enorme e consolidada busca na web, na qual deixo os links também.

## 1.  API de Investimentos (Fanfainvest)

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto2.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Criei esse projeto fictício em um processo de mentoria junto com outra desenvolvedora. Simulamos um serviço fake de investimento uma de API backend que tem como objetivo retornar a lista de investimento da carteira dos clientes. Ficou ridicularmente simples, mas a ideia foi boa praticar e pensar um pouco fora da caixa. Óbvio que um serviço de investimento é muito mais completo e complexo do que a FanfarInvest, mas o objetivo aqui foi puramente didático e criar algo mais simples possível e usando qualquer linguagem de programação.

Ao acessar o repositório, reparem que não tem tanta complexidade, nem muitas regras a ser seguida, por motivos didáticos e deixar o mais simples possível.

Objetivo: simular uma API de serviço de investimento, onde será possível obter todos os investimentos do cliente, como renda fixa, renda variável e etc. Nesta API tem a penas endpoints para consulta, mas você pode criar um banco local e criar outros endpoints como POST e PUT, ou quem sabe fazer pequenas integrações. [Neste link](https://dev.to/jessicanathany/how-to-create-a-simple-investiment-api-net-core-6-for-tranning-part1-5819), escrevi um artigo sobre esse projeto e a criação em passo a passo. 

[GitHub api-fanfareInvest](https://github.com/JessicaNathany/api-fanfareInvest)


<hr>

## 2. Conversor de Moedas (ConversorMoedas)

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto3.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Este projeto é super simples e é mais voltado para aquelas pessoas que estão iniciando na área. Criei esse conversor de moedas enquanto estudava Python, com a penas um arquivo onde é criado toda lógica do cálculo. Você pode melhorar ainda mais o projeto. Deixar mais dinâmico e quem sabe um pouco mais complexo. Por exemplo, obter a cotação do dia para fazer o cálculo de forma dinâmica, fazer uma consulta em outros serviços de câmbio fake e etc.

Objetivo: converter o valor da moeda pela cotação do dia, exemplo: converter real para dólar, passando o valor da moeda que deseja converter pela cotação do dia, o programa deverá calcular o valor que você deverá pagar pela cotação.

[GitHub conversor de moedas](https://github.com/JessicaNathany/conversor-moedas/blob/main/conversor-moedas.py)


<hr>

## 3. Gerador de senhas (PasswordGenerator)

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto4.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Este é um projeto simples e deve existir vários exemplos diferentes na web, acabei criando uma telinha simples para gerar senhas para o usuário.

Objetivo: gerar senhas para o usuário contendo como opções:

utilizar caracteres especiais;
ter pelo menos 8 caracteres no máximo e no mínimo 6 caracteres;
ter letra maiúscula no nome;
ter números como ! “ ? $ ? % ^ & * ( ) _ — + = { [ } ] : ; @ ‘ ~ # | \ < , > . ? /;

ter símbolos:

<hr>

## 4. Consultando API Ricky Morty (Consulting Information Rick and Morty.api)

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto5.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Este é um projeto de uma API Rest para consultar informações da [API Ricky Morty](https://rickandmortyapi.com/). Neste exemplo, a API tem como objetivo somente obter personagens e localização.

Objetivo: consumir a API do Ricky Morty acima, através do endpoints, trazer informações de personagens e episódios.

[GitHub RickyandMorty](https://github.com/Carlj28/RickAndMorty.Net.Api)


<hr>

## 5. Timer Pomodoro (Pomodoro Clock)

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto6.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Esse projeto achei a ideia dele aqui na Web e achei interessante também adicionar na lista, para tentar fazer. Basicamente consistem em criar um timer do pomodoro, algo semelhante ao pomodoro focus , criar um serviço semelhante ao pomodoro, contendo basicamente as funcionalidades do timer, um crônometro, colocar as pausas e zerar o cronômetro [pomofocus](https://pomofocus.io/).

[GitHub Pomodoro Clock](https://github.com/florinpop17/app-ideas/blob/master/Projects/1-Beginner/Pomodoro-Clock.md)

<hr>

## 6. Gerador SSH e HASH (Criptografia)

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto7.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Esse foi um projeto que fiz na pós -graduação em uma aula de Cybersecurity, uma ideia simples cujo objetivo criptografar a mensagem digitada pelo usuário.

GitHub:

[GitHub Projeto Criptografia](https://github.com/JessicaNathany/projetoCriptografia)

<hr>

## 7. Simulador Fast Food 

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto8.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Fast Food simula o funcionamento de um simples restaurante take-away e foi concebido para ajudar o criador a pôr os seus conhecimentos sobre Promessas e princípios de design SOLID a funcionar.

Objetivo: simular um Fast Food Fake utilizando os seguintes cenários:

- usuário — o usuário final que utiliza a aplicação;
- encomendar pedido — o simuladar a encomenda do pedido;
- cliente — simular o lado do cliente;
- cozinha — simular o pedido do lado da cozinha ;
- servidor — simular o lado do servidor

[Github FastFood](https://github.com/florinpop17/app-ideas/blob/master/Projects/3-Advanced/FastFood-App.md)

<hr>


## 8. Bot para consumir API Whatsapp (WhatsappPythonBot)

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto9.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Hoje em dia é muito comum empresas criarem bots para atender seus clientes no Whatsapp, seja par aenviar mensagens instântaneas, atendimento etc. E a ideia aqui é fazer o mesmo, criar um Bot para consumir a [API do Whatsapp](https://developers.facebook.com/docs/development). Abaixo inclui um o repositório do projeto que encontrei utilizando a linguagem Python.

Objetivo: criar um bot para consumir os endpoints da API Whatsapp

- enviar mensagens automatizadas;
- enviar áudios;
- enviar imagens;
- enviar arquivos;
- enviar contatos

[Github WhatsApp bot](https://github.com/ultramsg/python-whatsApp-bot)

<hr>


## 9. Dashboard TerraForm (Terraboard)

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto9.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Esse é um tipo de projeto mais avançado, mas é um bom desafio para se fazer. Esse projeto encontrei na web e é um painel para visualizar e consultar os estados da Terraform.

Objetivo: criar um dashboard para visualizar consultas e estados do Terraform.

- uma página de resumo com os arquivos de estado atualizados mais recentemente com sua atividade;
- uma página de estado com estados dos arquivos detalhados, incluindo versões e arquivos atribuídos;
- interface de busca para consultar recursos por tipo, nome ou atributos;
uma interface dif para comparar o estado entre as versões

[Github Terraboard](https://github.com/camptocamp/terraboard)

<hr>

## 10. Jogo de Xadrez

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto11.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Uma ideia bacana e também desafiadora é criar um jogo de xadrez utilizando sua linguagem favorita ou a linguagem que você se sentir mais confortável em desenvolver. Neste site o Macoratti crio um [jogo de xadrez](https://www.macoratti.net/10/06/c_xdz1.htm) usando a linguagem C#. Logo abaixo, tem um outro projeto feito em JavaScript, e tem outra ideia com linguagem [GO](https://acervolima.com/projete-um-jogo-de-xadrez/) e [Python](https://levelup.gitconnected.com/chess-python-ca4532c7f5a4).

Deixei algumas ideias de projetos para treino, mas vou deixar aqui um repositório de projetos backend com mais ideias pra vocês treinarem, pode acessar o [Backend Challanges Tech](https://github.com/CollabCodeTech/backend-challenges).


<hr>

## 10. Jogo de Xadrez

<br />
<div align="center">
  <img src="/assets/img/artigo-projeto10.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Deixei alguns repositórios de apis pública s que você pode consumir e estudar.

- [BrasilAPIs](https://github.com/BrasilAPI/BrasilAPI)
- [APIs públicas para desenvolvedores por Macoratti ](https://macoratti.net/19/07/net_apipub1.htm)
- [Google APIs](https://developers.google.com/)
- [Uber developres](https://developer.uber.com/)
- [The New York Time APIs](https://developer.nytimes.com/)
- [NASA APIs](https://api.nasa.gov/)
- [Exchangerate API](https://www.exchangerate-api.com/)
- [Linkedin Developers](https://developer.linkedin.com/)
- [Weather API](https://openweathermap.org/api)
- [INPE API](https://servicos.cptec.inpe.br/XML/)
- [INPE API](https://servicos.cptec.inpe.br/XML/)