# Diagrama de Sequência

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Sobre o Diagrama de Sequência](#Sobre-o-Diagrama-de-Sequência)
- [Aba Conhecimento Trilhas de Aprendizado](#Aba-Conhecimento-Trilhas-de-Aprendizado)
- [Aba Promoções](#Aba-=Promoções)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)


## Introdução

Ao se desenvolver diagramas de sequência, é essencial compreender que eles representam uma das formas de modelar o comportamento dinâmico de um sistema. Sendo assim, de acordo com a Apostila UML - Unified Modeling Language - Linguagem de Modelagem Unificada em Português [1](#ref1), esse tipo de diagrama descreve, de maneira visual e cronológica, a troca de mensagens entre diferentes objetos envolvidos em uma interação, no cado deste documento, sobre **a aba de trilhas de aprendizado** e da **aba de promoções**. Assim, um ponto importanto sobre a estrutura básica do diagrama de sequência é composta por dois eixos: o eixo vertical, que representa o tempo (de cima para baixo), e o eixo horizontal, que representa os objetos envolvidos, cada um com sua respectiva linha de vida, como é descrito em [IBM - Diagramas de Sequência](https://www.ibm.com/docs/pt-br/rsm/7.5.0?topic=uml-sequence-diagrams) [3](#ref3).

Para o projeto Galáxia Conectada, a elaboração dos diagramas de sequência será baseada nas interações pensadas previamente nos diagramas de classes e de componentes,com o intuito de garantir uma coerência com a estrutura lógica e modular da aplicação. 


## Objetivos

O objetivo deste documento é apresentar dois diagramas de sequência que representam duas das interações fundamentais na plataforma Galáxia Conectada. Com isso, a partir desses diagramas, busca-se:

  - Modelar visualmente os fluxos de mensagens entre os objetos do sistema e os usuários;

  - Especificar a ordem das interações e responsabilidades envolvidas em dois dos módulos principais da plataforma;

  - Ilustrar o comportamento interno da aplicação durante a execução de casos de uso específicos;

  - Apoiar o entendimento do fluxo dinâmico e temporal das funcionalidades com base nas mensagens trocadas.

De forma mais específica, os diagramas desenvolvidos visam representar os seguintes cenários:

1. **Aba Conhecimento: Trilha de aprendizado**: A navegação e o progresso do usuário em uma trilha de aprendizado ;

2. **Aba Promoções:**: A navegação do usuário na aba de promoções.

## Metodologia 

A elaboração dos diagramas de sequência seguirá uma abordagem iterativa, com base em alguns dos artefatos previamente construídos no desenvolvimento da plataforma Galáxia Conectada. Com base nisso, o processo adotado visa observar o comportamento do sistema por meio da representação temporal das interações. Para isso, foram realizadas as seguintes etapas:

1. Análise dos seguintes artefatos de apoio ao entendimento comportamental:

  - Fluxo do [protótipo de alta fidelidade](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/DesignSprint/Prototipo);
  - [Diagrama de Classes](/Modelagem/ModelagemEstatica/DiagramaClasses.md);
  - [Diagrama de Componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md)

2. Após a análise. serão contriídos dois diagramas de sequência na ferramenta Draw.io. 
3. Por fim, será aplicada uma verificação por meio de checklist com critérios de consistência, completude e conformidade com a UML.


## Sobre o Diagrama de Sequência

Como foi mencionado na introdução, o diagrama de sequência é uma ferramenta da UML utilizada para representar a interação entre objetos ao longo do tempo durante a execução de um processo específico do sistema. Assim, os elementos e componentes da "linha da vida" serão feitos apartir dos componentes do [diagrama de componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md). 

Com base nisso, o diagrama de sequência é composto por diversos elementos fundamentais que permitem representar de forma clara a comunicação entre os objetos de um sistema. Assim, com base em [O que é um diagrama de sequência UML?](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml) [4](#ref4), os atores e objetos participantes são dispostos horizontalmente, cada um com uma linha de vida vertical que indica sua existência ao longo do tempo. As mensagens trocadas entre eles são representadas por setas horizontais, podendo ser síncronas, assíncronas ou de retorno, com ou sem rótulos descritivos.

Para melhor compreensão dos elementos, a figura 1 abaixo funciona como uma legenda para os diagramas elaborados.

<div align="center">
    Figura 1: Legenda do Diagrama de Sequência
    <br>
    <img src="" width="500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

## Aba Conhecimento Trilhas de Aprendizado



## Aba Promoções



## Conclusão

A elaboração dos diagramas de sequência permitiu representar com clareza os fluxos de interação entre os usuários e o sistema da plataforma Galáxia Conectada, o que permitiu uma compreensão maior sobre a dinâmica de funcionamento das funcionalidades das trilhas de aprendizado e da aba de promoções automatizadas. 
## Bibliografia

<a name="ref1"></a>
[1] APOSTILA UML. Unified Modeling Language – Linguagem de Modelagem Unificada em Português. Seção sobre diagrama de sequência. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref2"></a>
[2] CREATELY. Tutorial do Diagrama de Sequência: Guia completo com exemplos. Disponível em: https://creately.com/blog/pt/diagrama/tutorial-do-diagrama-de-sequencia/. Acesso em: 30 abr. 2025.

<a name="ref3"></a>
[3] IBM. Diagramas de Sequência. Atualizado pela última vez em: 5 mar. 2021. Disponível em: https://www.ibm.com/docs/pt-br/rsm/7.5.0?topic=uml-sequence-diagrams. Acesso em: 30 abr. 2025.

<a name="ref4"></a>
[4] LUCIDCHART. O que é um diagrama de sequência UML? Disponível em: https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml. Acesso em: 30 abr. 2025.

## Histórico de versão
