# Diagrama de Casos de Uso

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Sobre o Diagrama de Casos de Uso](#Sobre-o-Diagrama-de-Casos-de-Uso)
- [Diagrama de Casos de Uso](#Diagrama-de-Casos-de-Uso)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)


## Introdução

O Diagrama de Casos de Uso é um dos diagramas comportamentais da UML (Unified Modeling Language), fundamental para capturar os requisitos funcionais de um sistema sob a perspectiva do usuário. Conforme descrito por [Diagrama de caso de uso UML: O que é, como fazer e exemplos](https://www.lucidchart.com/pages/pt/diagrama-de-caso-de-uso-uml) [3](#ref3) e [O que é UML e Diagramas de Caso de Uso: Introdução Prática à UML](https://www.devmedia.com.br/o-que-e-uml-e-diagramas-de-caso-de-uso-introducao-pratica-a-uml/23408) [2](#ref2), ele identifica quem interage com o sistema (Atores) e o que esses atores podem fazer (Casos de Uso) ao definir o escopo e as funcionalidades principais da aplicação de forma visual e intuitiva. Portanto, segundo a [IBM](https://www.ibm.com/docs/pt-br/rsm/7.5.0?topic=diagrams-use-case) [4](#ref4), este diagrama é essencial para comunicar o propósito e o comportamento esperado do sistema para diferentes stakeholders.

Neste artefato, procura-se apresentar o Diagrama de Casos de Uso da plataforma Galáxia Conectada, que visa ilustrar as principais funcionalidades disponíveis para os diferentes tipos de usuários e sistemas externos que interagem com ela.

## Objetivos

Com o intuito de apresentar o Diagrama de Casos de Uso e destacar as funcionalidades da plataforma sob a ótica do usuário, busca-se:

- Representar as funcionalidades do sistema sob a perspectiva do usuário e de sistemas externos;
- Identificar os Atores (usuários e sistemas) e suas interações com as funcionalidades do sistema;
- Definir claramente o escopo funcional da plataforma "Galáxia Conectada";


## Metodologia

Para a construção do diagrama, Serão seguidas as etapas abaixo:

1.  Serão analisados os seguintes artefatos para identificação de atores, funcionalidades e escopo:
    - [Requisitos Funcionais e Não Funcionais elicitados - Elaborados na entrega 1](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/IniciativaExtra/RequisitosElicitados);
    - [Diagrama de Classe](/Modelagem/ModelagemEstatica/DiagramaClasses.md);
    - [Diagrama de Componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md);
    - [BrainStorming realizado na entrega 1](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/ArtefatoGeneralista/BrainStorm).

2.  Após a análise dos dados, serão feitas as seguintes etapas:
    1. Identificação dos Atores principais.
    2. Identificação dos Casos de Uso essenciais a partir dos requisitos funcionais.
    3.  Definição do Limite do Sistema, englobando os Casos de Uso pertencentes à "Galáxia Conectada".
    4.  Identificação dos Relacionamentos entre Atores e Casos de Uso (Associação) e entre Atores (Generalização).
    5.  Modelagem do diagrama utilizando a ferramenta Draw.io.

## Sobre o Diagrama de Casos de Uso

O Diagrama de Casos de Uso a seguir, na figura 2, elaborado com base nos princípios da UML de [Diagrama de caso de uso UML: O que é, como fazer e exemplos](https://www.ibm.com/docs/pt-br/rsm/7.5.0?topic=diagrams-use-case) [3](#ref3), [Tutorial do diagrama de caso de uso (guia com exemplos)](https://creately.com/blog/pt/diagrama/tutorial-de-diagrama-de-caso-de-uso/) [1](#ref1), [Criar um diagrama de caso de uso UML](https://support.microsoft.com/pt-br/topic/criar-um-diagrama-de-caso-de-uso-uml-92cc948d-fc74-466c-9457-e82d62ee1298) [7](#ref7), representa as principais interações funcionais da plataforma "Galáxia Conectada". Dessa maneira, ele destaca os `Atores` chave, como `Visitante`, `Entusiasta/Aluno` e sistemas como `BotImportadorConteudo`. Além disso, os `Casos de Uso` (elipses) representam as funcionalidades centrais agrupadas por temas.

Para melhor compreensão dos diagramas, a figura 1 mostra a legenda;

<div align="center">
    Figura 1: Legenda do Diagrama de Casos de Uso
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/725cd7a49c5a871bc729855e9f2b824492871fed/docs/Modelagem/Imagens/LegendaCasoUso.drawio.png" width="500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

## Diagrama de Casos de Uso


A Figura 2 mostra o diagrama de Casos de Uso da Galáxia Conectada

<div align="center">
    <b>Figura 2:</b> o Diagrama de Casos de Uso
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaCasoUsoGalaxia.drawio.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
</div>

<p><strong>Observação:</strong> Caso deseje visualizar ou baixar em PDF, clique aqui: 
<a href="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaCasoUsoGalaxia.drawio.pdf">PDF do Diagrama de Casos de Uso</a></p>


## Conclusão 

Portanto, o Diagrama de Casos de Uso elaborado consolida a visão funcional da plataforma e estabelece de forma clara quem são os Atores que interagem com o sistema e quais Casos de Uso (funcionalidades) estão disponíveis para eles, ao delimitar,assim, o escopo do projeto. COm isso, ele serve como um pilar fundamental para guiar as fases subsequentes de análise, design detalhado, desenvolvimento do sistema.

## Bibliografia

<a name="ref1"></a>**[1]** Creately. [*Tutorial do diagrama de caso de uso (guia com exemplos)*](https://creately.com/blog/pt/diagrama/tutorial-de-diagrama-de-caso-de-uso/). Acesso em: 05 mai. 2025.

<a name="ref2"></a>**[2]** DevMedia. [*O que é UML e Diagramas de Caso de Uso: Introdução Prática à UML*](https://www.devmedia.com.br/o-que-e-uml-e-diagramas-de-caso-de-uso-introducao-pratica-a-uml/23408). Acesso em: 05 mai. 2025.

<a name="ref3"></a>**[3]** IBM. [*Diagrama de caso de uso UML: O que é, como fazer e exemplos*](https://www.ibm.com/docs/pt-br/rsm/7.5.0?topic=diagrams-use-case). Acesso em: 04 mai. 2025.

<a name="ref4"></a>**[4]** IBM. [*Relacionamentos em Diagramas de Caso de Uso*](https://www.ibm.com/docs/pt-br/rsm/7.5.0?topic=diagrams-relationships-in-use-case). Acesso em: 04 mai. 2025.

<a name="ref5"></a>**[5]** Lucidchart. [*Diagrama de caso de uso UML: O que é, como fazer e exemplos*](https://www.lucidchart.com/pages/pt/diagrama-de-caso-de-uso-uml). Acesso em: 05 mai. 2025.

<a name="ref6"></a>**[6]** Lucid Software (YouTube). [*Tutorial de Caso de Uso UML - Lucid Software Português*](https://www.youtube.com/watch?v=ab6eDdwS3rA). Acesso em: 05 mai. 2025.

<a name="ref7"></a>**[7]** Microsoft. [*Criar um diagrama de caso de uso UML*](https://support.microsoft.com/pt-br/topic/criar-um-diagrama-de-caso-de-uso-uml-92cc948d-fc74-466c-9457-e82d62ee1298). Acesso em: 04 mai. 2025.

## Histórico de versão


| Versão | Alteração                                                                      | Responsável       | Data       |
| :----- | :----------------------------------------------------------------------------- | :---------------- | :--------- |
| 1.0    | Criação da estrutura inicial do documento                                      | Larissa Stéfane   | 04/05/2025 |
| 1.1    | Adição da seção de Metodologia                  | Larissa Stéfane   | 04/05/2025 |
| 1.2    | Adição da explicação         | Larissa Stéfane   | 04/05/2025 |
| 1.3    | Adição do Diagrama de Caso de Uso        | Larissa Stéfane   | 05/05/2025 |
| 1.4 | Ajustes no artefato| Larissa Stéfane | 06/05/2024 |
