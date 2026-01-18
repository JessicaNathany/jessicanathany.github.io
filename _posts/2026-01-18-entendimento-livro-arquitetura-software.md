---
layout: post

title: "Resumo do livro Arquitetura de Software: As partes difíceis"

date: 2026-01-18

lang: pt

cover: "/assets/img/livro-arquitetura-software-partes-dficeis.jpg"

excerpt: "Resumo e entendimento do livro sobre principais pontos da arquitetura de software, casos complexos e trade-offs das soluções. Um ótimo livro para quem quer estudar melhor arquitetura de software"

tags: [arquitetura de software, microservices, monolitico, trade-offs]
---

## Introdução

Mergulhar no tema arquitetura de software pode ser algo bem abrangente, no meu ponto de vista. Não existe uma arquitetura certa para ser usada como modelo ou padrão que se encaixe perfeitamente ao seu esquema de negócio. A arquitetura de software é baseada no modelo de negócio, e não em um framework. Não há decisões fáceis na arquitetura de software, e sempre existirá contrapartida, ou mais conhecida como "trade-offs".<br />

Decidi mergulhar meus estudos e minhas leituras em assuntos relacionados à arquitetura de software. Comecei a me aprofundar nos conceitos, lições e estratégias, e a abstrair o melhor dos fundamentos. <br />

Pois bem, neste artigo, escrevo meu entendimento sobre a leitura do livro que concluí: *"Arquitetura de software: As partes difíceis"*, dos autores Neal Ford, Mark Richards, Pramod Sadalage e Zhamak Dehghani. Esta foi uma forma que encontrei de absorver melhor o conteúdo desse estudo, e poder compartilhar com vocês também um pouco sobre o livro, no qual recomendo a leitura. <br />

Se você gosta de mergulhar profundamente nos assuntos e busca algo mais denso e profundo, essa leitura é pra você. Se você prefere algo mais curto e com menos profundidade, essa leitura não é pra você.<br />

### Sobre o livro

<br />
<div align="center">
  <img src="/assets/img/livro-arquitetura-software-partes-dficeis.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 300px; border-radius: 6px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />


O livro, escrito pelos arquitetos de software e consultores Neal Ford, Mark Richards, Pramod Sadalage e Zhamak Dehghani, discute estratégias para a escolha de uma arquitetura adequada. Entrelaçando uma história fictícia de profissionais de tecnologia - o Sysops Squad -, eles examinam tudo: desde determinar a granularidade do serviço, contratos e gerenciar transações distribuídas, até como otimizar as características operacionais, como escalabilidade, elasticidade e desempenho.<br />

Durante a leitura, os autores usam a saga do Sysops Squad para exemplificar cada capítulo e ilustrar as técnicas de "trade-offs". Nesta saga, é discutida a migração de um sistema monolítico que possui cenários bem ruins. Como descrito no livro, o atual sistema da Sysops Squad é um grande monólito que foi desenvolvido há anos. <br />

Há muitas reclamações de clientes informando que o sistema nem sempre está disponível. Além disso, o sistema possui grandes problemas de confiabilidade, congela e trava, resultando em indisponibilidade em todas as funções. Se algo não for feito, isso poderá impactar todo o negócio da empresa, forçando-a a fechar as portas.<br />

Não vou entrar em muitos detalhes no negócio desse sistema, embora no livro eles destacam o negócio do sistema e desenham um diagrama das funcionalidades. O livro descreve a jornada desafiadora dessa migração de um sistema monolítico para microserviços, sendo o tempo obviamente um fator preocupante. 

Todas as decisões adotadas para resolver o problema da migração da Sysops Squad são muito bem justificadas. Isso faz com que você tenha essa visão da arquitetura e aprenda com os argumentos dessas discussões.<br />

### Meu entendimento

Nas primeiras partes do livro, é descrita a justificativa para a escolha de uma arquitetura de microserviços. Era preciso ter o sistema disponível, escalável e com tolerância a falhas, além de desacoplar módulos importantes do sistema. <br />

As primeiras partes do livro descrevem muito sobre acoplamento, como seria a abordagem do time em relação ao desacoplamento dos componentes e módulos do sistema legado, e como esses componentes se tornariam serviços e se comunicariam no futuro.<br />

Uma parte que me chamou a atenção em termos de conhecimento foi a parte dos dados. Desmembrar dados de um sistema monolítico não é uma tarefa fácil. Decidir como destrinchar um único banco em contextos diferentes, que no final se tornariam serviços, me trouxe vários questionamentos que foram sendo respondidos no decorrer do livro. <br />

Na minha opinião, uma das partes mais difíceis na migração para uma arquitetura de microserviços é encontrar os contextos do banco de dados e destrinchar esses contextos em serviços, indo além de cada serviço ter seu próprio banco de dados, pensando também em conexões, que tipo de banco escolher e por quê, transações, propriedade dos dados, etc. 

Além disso, o livro destaca os tipos de banco de dados e explica os tipos e a responsabilidade de cada um. <br />

Os autores explicam dois estilos principais de gestão de fluxos de trabalho distribuídos: arquitetura orquestrada e arquitetura orientada a eventos/coreografia.<br />

- **Orquestrada**: o orquestrador ou mediador é responsável por gerenciar o fluxo de trabalho, decidir qual serviço chamar e em que ordem. Possui maior acoplamento porque o orquestrador precisa conhecer todos os serviços necessários, tem um alto nível de controle do fluxo e facilita na gestão de tratamento de erros, rollbacks e transações.

- **Coreografia/Eventos**: a coreografia é descentralizada, os serviços se comunicam através de eventos, agindo de forma independente. Quando um novo evento acontece, o serviço interessado reage, sem haver necessidade de saber quem enviou o evento ou quem virá a seguir. Neste modelo, o acoplamento é baixo, pois os serviços funcionam de forma independente, mas pode ser mais complexo.<br />

Há outros capítulos do livro que não vou detalhar aqui, mas acho que valem a pena ser mencionados:

- **Primeira parte**: começa analisando e separando os contextos. Descreve a importância dos dados na arquitetura e a dificuldade de separar esses contextos, além da decomposição dos componentes.

- **Segunda parte**: traz sobre transações distribuídas, padrão de replicação, gerenciamento de fluxo de trabalho, separação de esquemas, sagas transacionais, etc.


### Conclusão

Para aqueles que estão focados em mergulhar cada vez mais no entendimento da arquitetura de software, é um ótimo livro que recomendo. O livro não descreve algo como "faça assim, faça assado...". Além de trazer abordagens relacionadas ao problema do negócio, traz muitas coisas que podem dar errado a cada decisão tomada, e isso precisa ser rediscutido para chegar a outros cenários e estratégias.<br />

O que mais gostei foi que os autores trouxeram um exemplo real, além de um simples exemplo acadêmico, que nos fez mergulhar no problema do negócio, na justificativa da migração, nos trade-offs e nas discussões técnicas entre membros do time, como, por exemplo, na parte de uma decisão estratégica sobre migração de contextos de dados entre arquitetos e o DBA. <br />

Os autores mostram a importância do diálogo, a justificativa da decisão e, principalmente, da comunicação das decisões com o time.<br />

Um bom caso de uso do qual dá para extrair muita coisa. Achei interessante o projeto de negócio da Sysops Squad e quantos problemas e desafios era preciso resolver para manter aquele negócio funcionando em uma nova arquitetura.

