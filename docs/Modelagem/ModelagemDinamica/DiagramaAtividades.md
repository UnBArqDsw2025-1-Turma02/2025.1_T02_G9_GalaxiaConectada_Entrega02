# Diagrama de Atividades

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Sobre o Diagrama de Atividades](#Sobre-o-Diagrama-de-Atividades)
- [Aba Conhecimento Trilhas de Aprendizado](#Aba-Conhecimento-Trilhas-de-Aprendizado)
- [Aba Científico Notícias e Artigos](#Aba-Científico-Notícias-e-Artigos)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)


## Introdução

A plataforma Galáxia Conectada está sendo desenvolvida na disciplina como uma solução digital abrangente para o ensino e divulgação da Astronomia. Com isso, para organizar e representar um pouco o comportamento e os fluxos de processos do sistema, foram elaborados dois diagramas de atividade conforme a notação UML (Unified Modeling Language).

Segundo a Apostila UML - Unified Modeling Language - Linguagem de Modelagem Unificada em Português [1](#ref1), os diagramas de atividade são uma forma de representar o fluxo sequencial das ações realizadas por uma operação do sistema ao evidenciar as mudanças de estado dos objetos envolvidos, a ordem de execução e a responsabilidade pelas tarefas por meio de raias (swimlanes). Sendo assim, eles são especialmente úteis para modelar fluxos de trabalho, decisões, execuções paralelas e resultados esperados. Além disso, conforme destaca a [IBM](https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-activity), esses diagramas são semelhantes a fluxogramas, mas com maior capacidade de representar fluxos paralelos e alternativos.

## Objetivos

O objetivo deste documento é algumas das atividades desenvolvidas para a plataforma Galáxia Conectada ao evidenciar os principais fluxos funcionais e comportamentais do sistema. De forma mais específica, busca-se:

- Ilustrar os principais processos internos da plataforma;

- Demonstrar a responsabilidade dos atores e componentes por meio das raias;

- Evidenciar os pontos de decisão, bifurcação e encerramento dos fluxos;

- Apoiar a modelagem comportamental dos casos de uso com uma representação visual precisa.

## Metodologia

A elaboração dos diagramas de atividade seguirá uma abordagem baseada na integração entre diferentes artefatos desenvolvidos anteriormente no projeto Galáxia Conectada. Isso com o  objetivo será representar visualmente o fluxo das ações executadas pelos usuários e pelo sistema em dois módulos principais da plataforma: **a aba Conhecimento (trilhas de aprendizado)** e a **aba Científico (notícias e artigos científicos)**. Para isso, serão feitas as seguintes etapas:

1. inicialmente serão realizadas análises dos seguintes artefatos:
     - [5W2H](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/ArtefatoGeneralista/5W2H)
     - Fluxo do [protótipo de alta fidelidade](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/DesignSprint/Prototipo)
     - [Diagrama de classes](/Modelagem/ModelagemEstatica/DiagramaClasses.md)
     - [Diagrama de Componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md)
3.  Os diagramas serão desenvolvidos na ferramenta Draw.io.
4.  Será aplicada uma [verificação por meio de um checklist](.../IniciativasExtras/Verificacao/VerificacaoDiagramaAtividades.md) de boas práticas de UML;, 


## Sobre o Diagrama de Atividades

Ao se desenvolver os diagramas de atividade, é necessário levar em consideração que esse tipo de representação tem como objetivo principal demonstrar o fluxo de ações dentro de um processo ao ilustrar como as atividades ocorrem e se conectam. Com base nisso, no projeto da **Galáxia Conectada**, foram elaborados dois diagramas de atividades: um para a **aba Conhecimento**, que compreende as trilhas de aprendizado, e outro para a **aba Científico**, que apresenta notícias e artigos da área de astronomia. Ambos foram estruturados para refletir a sequência das operações esperadas no sistema, conforme as funcionalidades previamente definidas nos diagramas de classes e de componentes.

A estrutura do diagrama de atividades utiliza elementos visuais específicos para representar os passos e decisões envolvidos em um fluxo. Entre eles, destaca-se o nó inicial, que marca o ponto de partida da atividade, e o nó final, que encerra o fluxo [UML Activity Diagram Controls](https://www.uml-diagrams.org/activity-diagrams-controls.html) [5](#ref5). As ações são representadas por retângulos arredondados e indicam as tarefas a serem executadas. Setas conectam essas ações, indicando o fluxo de controle. Há ainda nós de decisão, que permitem desviar o fluxo com base em condições, e nós de mesclagem, que reúnem caminhos alternativos. Para representar tarefas simultâneas, utilizam-se nós de bifurcação (fork) e junção (join). Além disso, os diagramas foram organizados em swimlanes (raias), que atribuem responsabilidades específicas a diferentes partes do sistema, evidenciando “quem faz o quê”, como foi mensionado no conteúdo de Modelagem de Sistemas Orientada a Objetos com UML.

Para melhor compreensão dos elementos, a figura 1 abaixo funciona como uma legenda para os diagramas elaborados.

<div align="center">
    Figura 1: Legenda do Diagrama de Atividades
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/5850e355e01ff1a380ebb122ca19172098febbf1/docs/Modelagem/Imagens/LegendaDiagramaAtividade.drawio.png" width="500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>


## Aba Conhecimento Trilhas de Aprendizado

A figura 2 apresenta o diagrama de atividades da aba de conhecimento.


<div align="center">
    Figura 2: o Diagrama de Atividade - Aba Conhecimento
    <br>
    <img src="../Imagens/DiagramaAtividadeTrilhaEducacional.drawio.png">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

**Observação:** Caso deseje visualizar ou baixar em PDF, clique na mensagem abaixo e o pdf será mostrado. Para baixá-lo, basta clicar nele.

<details>
  <summary size="20"><b> Ver em PDF e baixá-lo </b></summary> 

<a href="../Imagens/DiagramaAtividadeTrilhaEducacional.drawio.pdf" target="_blank">
  <img src="../Imagens/DiagramaAtividadeTrilhaEducacional.drawio.png" alt="Abrir PDF" width="1000">
</a>

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>



## Aba Científico Notícias e Artigos

A figura 3 apresenta o diagrama de atividades da aba de Científico

<div align="center">
    Figura 3: o Diagrama de Atividade - Aba Científico
    <br>
    <img src="../Imagens/DiagramaAtividadeCientifico.drawio.png">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

**Observação:** Caso deseje visualizar ou baixar em PDF, clique na mensagem abaixo e o pdf será mostrado. Para baixá-lo, basta clicar nele.

<details>
  <summary size="20"><b> Ver em PDF e baixá-lo </b></summary> 

<a href="../Imagens/DiagramaAtividadeCientifico.drawio.pdf" target="_blank">
  <img src="../Imagens/DiagramaAtividadeCientifico.drawio.png" alt="Abrir PDF" width="1000">
</a>

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>



## Conclusão

A conclusão do desenvolvimento desses diagramas de atividade para a plataforma da Galáxia Conectada oferece uma representação clara e estruturada dos fluxos de trabalho nas abas Conhecimento e Científico, o que possibilita uma compreensão aprofundada das interações entre usuários e o sistema. 

## Bibliografia

<a name="ref1"></a>
[1] APOSTILA UML. Unified Modeling Language – Linguagem de Modelagem Unificada em Português. Seção sobre diagrama de atividades. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref2"></a>
[2] IBM. Diagramas de Atividades. Atualizado pela última vez: 02 mar. 2021. Disponível em: https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-activity. Acesso em: 30 abr. 2025.

<a name="ref3"></a>
[3] LUCIDCHART. O que é diagrama de atividades UML? Disponível em: https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-atividades-uml. Acesso em: 30 abr. 2025.

<a name="ref4"></a>
[4] RICARDO BARCELAR, R. Engenharia de Software – Módulo 3: Modelagem de Sistemas Orientada a Objetos com UML. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref5"></a>
[5] UML DIAGRAMS. UML Activity Diagram Controls. Disponível em: https://www.uml-diagrams.org/activity-diagrams-controls.html. Acesso em: 30 abr. 2025.



## Histórico de versão

| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 30/04/2024 |
| 1.1 | Adição do tópico "Sobre o diagrama"  | Larissa Stéfane | 30/04/2024 |
| 1.2 | Adição dos diagramas | Larissa Stéfane | 30/04/2024 |
| 1.3 | Adição da legenda | Larissa Stéfane | 30/04/2024 |
