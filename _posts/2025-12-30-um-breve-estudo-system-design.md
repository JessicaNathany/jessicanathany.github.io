---
layout: post

title: "Um breve estudo sobre System Design"

date: 2025-12-30

lang: pt

cover: "/assets/img/cdn.jpg"

excerpt: "Um pequeno artigo que descreve alguns conceitos sobre o que é o system design"

tags: [system design, arquitetura de software, aplicações]
---

## Introdução

Quando decidi escrever esse artigo o objetivo foi poder absorver melhor esse conhecimento, que venho mergulhando a alguns meses em livros, artigos e vídeos e cada dia que passa, parece que vou escalando mais sobre esse assunto e tenho ainda mais que aprender.

Porém, pecebe-se que é um conteúdo difícil de se achar na web em uma versão português, e também é facilmente de ser confundindo com assuntos relacionados a UX. Se você fizer uma busca por Design System muito provavelmnet encontrará assuntos relacionados a UX.

Em um artigo do Renato Lopes [Design System](https://brasil.uxdesign.cc/afinal-o-que-%C3%A9-design-system-448c257b0021) é - “Design System é um ecossistema de bibliotecas instaláveis, com componentes programados e padrões semânticos de design, que reúne padrões de comportamentos.” (Renato Lopes Lidio). Mas aqui, irei abordar o tema do System Design.

### O que System Design?

System Design nada mais é um processo inicial do desenho da arquitetura da aplicação, que envolve componentes, interfaces, comunicação entre aplicações, banco de dados etc. É nesse ponto que definimos soluções pensando nos requisitos da aplicação e suas necessidades durante a definição de arquitetura do projeto.

Pensando em cases como Linkedin, Twitter ou Instagram que são aplicações que usamos em nosso cotidiano, todas são aplicações escaláveis, ou seja, bilhões de pessoas no mundo inteiro acessam de forma simultânea essas aplicações fazendo diversas requisições e trafegam dados a cada minuto. Mas então, como que essas aplicações conseguem lhe dar com esse tanto de acesso e dados tempo inteiro sem deixar o sistema com instabilidade?

Ai que entra o System Design. Desenvolvedores precisam entender a necessidade e a complexidade do negócio antes de poder aplicar os conceitos do System Design, e encontrar soluções para eventuais problemas, pensando em Escalabilidade, Disponibilidade e Confiabilidade. Esse é ponto inicial do desenho da arquitetura e é onde pode ser encontrado falhas ou até mesmo prever problemas futuros.

É bem comum na carreira de um Software Engineer de nível superior, se deparar em alguns processos seletivos sobre os conceitos de System Design, claro que depende muito para qual cargo você esteja aplicando para vaga e para qual empresa. É normal as big techs como Google, Amazon, Airbnb, Instagram etc, incluirem esse tema no processo seletivo.

Existem hoje artigos, bootcamps e até mentorias sobre o tema, para te preparar sobre os conceitos de System Design para os processos seletivos em big techs. Separei alguns sites abaixo onde você pode conferir.

- [Preparing for the System Design a Coding Interview](https://blog.pragmaticengineer.com/preparing-for-the-systems-design-and-coding-interviews/)
- [31 system design interview questions (and sample answers)](https://igotanoffer.com/blogs/tech/system-design-interviews)
- [Cracking the Big Tech Interview](https://medium.com/@rahul.9269/cracking-the-big-tech-interview-7b6c13205d05)
- [Top 10 System Design Interview Questions and Answers](https://www.geeksforgeeks.org/system-design/top-10-system-design-interview-questions-and-answers/)


### Abordagem do problema

É aconselhável antes de você começar a desenhar os diagramas, é preciso fazer uma abordagem geral do problema. Para uma melhor forma, é sugerido que descreva as funcionalidades da aplicação e quais os requisitos principais e os requisitos não funcionais que essa aplicação terá.

Tive uma mentoria com um Software Engineer o [Sergei Gusachenko](https://www.linkedin.com/in/sergeigusachenko/) que trabalha no Airbnb, conversamos sobre System Design, e conforme a imagem da Figura 1, ele descreveu uma possível aplicação para exercitarmos, no caso uma rede social bem simples e descreveu as funcionalidades dessa aplicação. Foi bem legal e enriquecedor o papo. Discutimos ideias sobre a solução, levantamos os requisitos, e pensamos em eventuais problemas que poderia ocorrer.

Esse processo eu fiz no site [Pramp](pramp.com/dashboard#/) que é uma forma de você se preparar para entrevistas nas grandes big techs e treinar também o seu inglês, e claro além de trocar ideias e conhecimento.

*A Social Graph*

Uma popular rede social que contém milhões e bilhões de conexões entre individuos. Desenhar a arquitetura do sistema que permitará usuários fazer pesquisas por outras pessoas, e ver o caminho mais curto.

**Requisitos Funcionais**

- pesquisar outras pessoas
- quantos nós teremos entre das pessoas
- mostrar notificação quando um usuário adicionar outro
- 1 milhão de usuários
- 1 bilhão de conexões

**Requisitos Não Funcionais**

- alta disponibilidade
- consistência
- alta performance com baixa latência

Descrevi esse exemplo para que você possa enxergar que, antes de sair desenhando diagramas, é necessário ter a abordagem geral do problema, e o que faremos para atender os usuários daquele sistema. Sendo assim respondendo as eventuais perguntas com o time. Qual o negócio que minha aplicação irá atender? Como devo construir? O que preciso escalar para atender as requisições e o tempo de resposta para os usuários?

Tendo os requisitos funcionais e os não funcionais, o segundo passo é criar o esboço. Vale lembrar que isso não é uma regra, mas é um passo que eu seguiria antes de usar um software específico para desenhar os componentes, APIs, banco de dados etc. Você não necessariamente precisa seguir o modelo abaixo, você pode fazer a forma que achar melhor. Você pode partir desta forma e depois usar fazer o diagrama da arquitetura no geral, usando um software como [app.diagrams](https://app.diagrams.net/).

### Entendendo os conceitos do System Design

Antes de analisar a solução do problema, é importante entender alguns conceitos do System Dsign consideramos importantes. Para sua aplicação ter sucesso, é preciso assegurar que o software seja confiável, esteja disponível e seja escalável e claro, de fácil manutenção.

<br />
<div align="center">
  <img src="/assets/img/escalabilidade.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

**Confiabilidade**

O sistema tem que ser confiável e que satisfaça os requisitos e funcionalidades do usuário, sistema tolerante a falhas, ou seja, mesmo que ocorra uma falha o sistema continua operante para o usuário e não havendo interrupções. Imagina usuários querendo acessar um streamming de filmes e algumas funcionalidades não funciona de forma esperada, isso faz com o que o usuário perca a confiança naquele sistema.

**Disponibilidade**

É uma característica do sistema, que deve estar disponível e operando de forma correta, e claro é essencial que o sistema contenha disponibilidade em até alto nível, para servir a outros sistemas que o depende.

Na análise do problema, é discutido que tipo de disponibilidade o sistema deverá ter, isso pode variar de sistema para sistema. Aplicações como rede social por exemplo, pode ter uma demanda alta de disponiblidade mas não tolera lentidão, atrasos de minutos em requisição pode ser algo intolerável para o negócio. Ou outro exemplo são sistemas de alta criticidade como Bancos e Hospitais, que precisam de alta dispoinibilidade pois possuem criteriosidade em seus serviços.

**Escalabilidade**

É a capacidade que o sistema tem de lidar com carga crescente, acho que podemos imaginar a situação de um ecommerce, por exemplo. O sistema foi pensado para ser ecalável em um período de black friday, onde há um número muito maior de requisições, acessos, pedidos sendo criado, pedidos sendo despachado, requisições de milhares de produtos na base, integrações e etc. Com isso, esse sistema deve ser eficiente o suficiente para lidar com a carga crescente e com eficiência. E é isso que o torna Escalável.

*Escalabilidade Vertical*

Escalabilidade Vertical significa melhorar os recursos computacionais do servidor, ou seja, aumentar de memória, CPU ou melhorar o desempenho de armazenamento.

*Escalabilidade Horizontal*

Escalabilidade Horizontal significa aumentar o número de servidores, só que diferente da escalabilidade vertical, há alguns pontos que deve ser considerado, por exemplo, arquitetura da aplicação, se aplicação não é distribuída fica difícil escalar horizontalmente pelo fato de haver acoplamento entre as APIs.


<br />
<div align="center">
  <img src="/assets/img/scaling.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />


*Banco de dados*

Esse é o ponto que questionamos no inicio do desenho, qual banco de dados utilizar? Isso vai depender muito da aplicação. Você pode escolher um tradicional banco de dados relacional, como SQL Server, MySQL ou PostgreSQL, etc e um banco de dados não relacional como MongoDB, DynamoDB, Cassandra etc. Vale lembrar que a escolha do banco de dados vai depender muito da ideia ou o negócio da aplicação e o objetivo pretendido.

Mas é importante ressaltar que a escolha do banco de dados deve levar alguns fatores importantes como: velocidade, confiabilidade e precisão. A escolha de um banco de dados SQL garante a veracidade dos dados e para o banco NoSQL garante uma eventual consistência.

Não vou entrar em detalhes aqui, até porque o artigo ficaria extenso, mas para saber mais afundo o entedimento e as estruturas a serem consideradas na escolha do banco de dados durante o desenho da arquitetura, recomendo a forte leitura desse artigo [Complete Guide System Design database](https://www.educative.io/courses/grokking-the-system-design-interview#databases). 


*CDN (Coontent Delivery Network)*

O CDN(Content Delivery Network) ou Rede de Distribuição de Conteúdo, refere-se a um grupo de servidores distribuídos de forma geográfica que trabalham em conjunto para entregar o conteúdo de forma rápida a internet. O autor Alex Xu colocou em seu livro System Design Interview — An insider’s Guide alguns pontos a se considerar usando o CDN, vejamos:

Preço: o CDN é gerido por fornecedores terceiros, e é cobrado por transferência de dados dentro e fora do CDN. O cache de ativos utilizados com pouca frequência não proporciona benefícios significativos, pelo que deve considerar a sua retirada do CDN.

CDN fallback: deve ser considerado como sua aplicação lida com o CDN, se houver uma parada temporária do CDN, os clientes devem ser capazes de detectar o probleam e solicitar os recursos á origem.

Invalidação de arquivos: pode remover um arquivos do CDN antes deste expirar.

Press enter or click to view image in full size


<br />
<div align="center">
  <img src="/assets/img/cdn.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />


*Load Balancer*

O Load Balancer é a distribuição de tráfego, ou seja, uma técnica utilizada para manter a estabilidade e distribuir a carga entre servidores, quando o tráfego ou o volume de dados é muito grande, evitando a sobrecarga e melhorando o desempenho do sistema.


<br />
<div align="center">
  <img src="/assets/img/loadbalance.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />


*Cache*

É uma camada de armazenamento físico de dados de alta velocidade que guarda um conjunto de dados temporários, para que futuras solicitações possam obter esses dados. Cada vez que uma nova página web é carregada, é feito uma consulta na base de dados. O desempenho da aplicação é grandemente afetado pela consulta dos dados repetidamente e o cache pode mitigar este problema.

Não coloquei todos os tópicos dos conceitos que fazem parte do System Design a ser considerado quando pensarmos na arquitetura do software, até porque o objetivo desse artigo é dar um breve estudo sobre os conceitos do System Design uma introdução na verdade. Abaixo há tópicos que eu não descrevi aqui neste artigo, mas que você pode escontrar no livro do Alex Xu. Vejamos:

- Data Base Replication
- Cache Tier
- Stateless Web Tier
- Stateful Architeture
- Message Queue
- Loggin Metrics
- Frameworks para System Design
- Design Patterns no System Design
- Map Reduce
- Proxy Server

### System Design de algumas aplicações do mercado

Conforme visto na imagem abaixo, temos o modelo do Netflix que trabalha com cloud AWS e Open Connect. “O programa Netflix Open Connect oferece aos provedores de Internet parceiros a oportunidade de aprimorar a experiência de usuário de seus clientes na Netflix com instâncias locais do tráfego da Netflix e reduzindo a entrega de tráfego com um provedor intermediário.” [Netflix Open Connect](https://openconnect.netflix.com/pt_br/). Isso explica porque o serviço do Netflix funciona tão bem e performático.


<br />
<div align="center">
  <img src="/assets/img/netflix.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Como podemos ver acima o System Design é representa os componentes que a plataforma utiliza como: cloud, banco de dados, serviços e comunicação entre as APIs. Neste artigo [System Design Netflix — A Complete Architecture](https://www.geeksforgeeks.org/system-design/system-design-netflix-a-complete-architecture/) você poderá ver com muito mais detalhes sobre a arquitetura.

Abaixo temos o System Design do Twitter, se compararmos com o desenho do Netflix, vimos uma quantidade de serviços menor, mas isso não significa ser menos complexo. Se formos escrever o desenho do Twitter, podemos ver que os requerimentos funcionais é a timeline, onde o usuário irá criar e ver twiits de outras pessoas, pesquisar twitts por palavra chave ou tags que estão relacionadas ao assunto etc.

Para ver os melhores detalhes dessa arquitetura, clique neste no link [twitter system design](https://www.youtube.com/watch?v=wYk0xPP_P_8).



<br />
<div align="center">
  <img src="/assets/img/sdtwitter.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

### Conclusão

Conforme vamos avançando em nossa carreira tecnológica como desenvolvedores, chegamos a um ponto que além de criar novas funcionalidades, corrigir bugs ou criar melhorias para o sistema, queremos entender como tudo isso funciona por baixo dos panos. Isso faz parte do nível de senioridade, você ter uma participação maior em soluções e tomada de de decisões que envolve a arquitetura do software.

Como havia escrito no inicio do artigo, hoje em dia esta sendo muito comum em processos seletivos em big techs que o canditato tenha conhecimento em System Design, e se tiver um domínio maior, melhor ainda.

Eu comecei a lendo e assistindo muitos vídeos sobre isso até entender como tudo isso funciona. Depois disso exercitar, discutir com outras pessoas, passar por processos de mentoria, vem ajudando muito a adquirir um conhecimento ainda maior e me aprofundar a cada vez mais.

Se você gostou desse artigo e quer aprofundar mais o conhecimento nisso, aproveite para ler e consultar todas as refrências que escrevi aqui. Espero que este artigo tenha lhe ajudado.


### Referência

- [Github cdn-up-and-running](https://github.com/leandromoreira/cdn-up-and-running)
- [Plataforma cursos System Design](https://www.educative.io/courses/grokking-the-system-design-interview)
- [Blog Neflix System Design](https://medium.com/@narengowda/netflix-system-design-dbec30fede8d?source=post_page-----33f8c2c8bb92---------------------------------------)
- [Open Connet](https://openconnect.netflix.com/pt_br/?source=post_page-----33f8c2c8bb92---------------------------------------)
- [Github System Design estudos](https://github.com/donnemartin/system-design-primer?source=post_page-----33f8c2c8bb92---------------------------------------#study-guide)
- [Github System Design estudos](https://github.com/donnemartin/system-design-primer?source=post_page-----33f8c2c8bb92---------------------------------------#study-guide)
