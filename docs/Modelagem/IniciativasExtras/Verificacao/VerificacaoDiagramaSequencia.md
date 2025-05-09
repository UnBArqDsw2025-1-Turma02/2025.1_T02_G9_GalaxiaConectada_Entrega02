# Verificação do Diagrama de Sequência

## Sumário
- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Tabela de Verificação para Lifelines, Atores e Objetos](#Tabela-de-Verificação-para-Lifelines-Atores-e-Objetos)
- [Tabela de Verificação para Mensagens e Fragmentos de Interação](#Tabela-de-Verificação-para-Mensagens-e-Fragmentos-de-Interação)
- [Observações](#Observações)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)

## Introdução

O Diagrama de Sequência é um tipo de diagrama de interação da UML que detalha como as operações são realizadas e como os objetos e componentes interagem entre si ao longo do tempo, como é definido em ([O que é um diagrama de sequência UML?](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml) [6](#ref6). Dessa maneira, ele enfatiza a ordem temporal das mensagens trocadas entre os objetos para realizar uma funcionalidade específica ou um caso de uso. Assim, no projeto Galáxia Conectada, os diagramas de sequência são utilizados para modelar cenários como o login de um usuário, a inscrição em um curso ou o acesso a um conteúdo interativo, mostrando a dinâmica das interações.

A verificação destes diagramas é crucial para assegurar que a lógica de interação entre os componentes do sistema esteja correta, completa, e que o comportamento dinâmico modelado corresponda aos requisitos funcionais e às regras de negócio estabelecidas.

## Objetivos

Este artefato tem como objetivo principal realizar a verificação dos Diagramas de Sequência desenvolvidos para o projeto Galáxia Conectada. Busca-se garantir que:
* As interações entre objetos e atores estejam representadas com precisão.
* A ordem cronológica das mensagens seja lógica e correta para cada cenário modelado.
* Os diagramas estejam em conformidade com a notação e as regras da UML com base em ([UML Diagrams - Sequence](https://www.uml-diagrams.org/sequence-diagrams.html) [10](#ref10)).
* Os diagramas sejam consistentes com outros artefatos do sistema, como diagramas de caso de uso e diagramas de classes.

## Metodologia

A metodologia adotada para a criação e verificação dos Diagramas de Sequência seguiu etapas progressivas. Inicialmente, foi realizado um estudo aprofundado sobre a UML, com foco nos elementos e nas regras específicas dos Diagramas de Sequência ([APOSTILA UML] [1](#ref1). Em seguida, com base nos casos de uso e nos requisitos funcionais do projeto Galáxia Conectada, foram elaborados os diagramas para os principais cenários de interação.

## Tabela de Verificação para Lifelines, Atores e Objetos

**Tabela 1:** Perguntas para a verificação de Lifelines, Atores e Objetos.

| ID   | Pergunta de Verificação                                                                 | Explicação                                                                                                                               | Rastreabilidade                                                                                                                                                                                                                            |
|------|-----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| LO01 | As lifelines estão corretamente representadas por uma caixa retangular e uma linha tracejada vertical? | Esta é a notação padrão para representar a linha de vida de um participante na interação.                                               | [Lucidchart - Diagrama de Sequência](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml), [UML Diagrams - Sequence](https://www.uml-diagrams.org/sequence-diagrams.html)                                               |
| LO02 | Cada lifeline possui um nome claro que identifica o participante (ator, objeto, classe)? | O nome dentro da caixa da lifeline deve ser `nomeInstancia : NomeClasse` ou `NomeClasse` se for uma classe, ou nome do ator.          | [IBM - Diagramas de Sequência](https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-sequence)                               |
| LO03 | Atores são representados com o símbolo de "boneco palito" (stickman) ou como uma lifeline com estereótipo `<<actor>>`? | Atores iniciam ou participam da interação e devem ser claramente identificados.                                                        | [Lucidchart - Diagrama de Sequência](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml)                                                                                                                             |
| LO04 | As barras de ativação (foco de controle) são usadas para indicar o período em que um objeto está ativo (processando)? | As barras de ativação (retângulos finos sobre a lifeline) mostram quando o objeto está executando uma ação.                             | [UML Diagrams - Sequence](https://www.uml-diagrams.org/sequence-diagrams.html), [Visual Paradigm - Sequence Diagram Tutorial](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-sequence-diagram-tutorial/)           |
| LO05 | A criação de objetos durante a sequência é representada com uma mensagem apontando para a caixa da lifeline do objeto criado? | A mensagem de criação (ex: `<<create>>`) deve originar-se na lifeline do criador e terminar na "cabeça" da lifeline do objeto criado. | [IBM - Diagramas de Sequência](https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-sequence)                                                                                                                             |
| LO06 | A destruição de objetos é representada por um "X" no final da lifeline e, opcionalmente, uma mensagem `<<destroy>>`? | Indica o fim da existência de um objeto durante a interação.                                                                            | [UML Diagrams - Sequence](https://www.uml-diagrams.org/sequence-diagrams.html)                                                                                                                                                           |
| LO07 | As lifelines estão dispostas de forma lógica (ex: ator à esquerda, ordem de interação)? | Uma disposição clara facilita a leitura e o entendimento do fluxo da interação.                                                          | [Lucidchart - Diagrama de Sequência](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml)                                                                                                                             |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Tabela de Verificação para Mensagens e Fragmentos de Interação

**Tabela 2:** Perguntas para a verificação de Mensagens e Fragmentos de Interação.

| ID   | Pergunta de Verificação                                                                                                | Explicação                                                                                                                                                                     | Rastreabilidade                                                                                                                                                                                                                            |
|------|------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| M01  | As mensagens síncronas são representadas por uma seta preenchida?                                                        | Indicam que o remetente espera pela conclusão da operação antes de continuar.                                                                                                  | [Lucidchart - Diagrama de Sequência](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml), [UML Diagrams - Sequence](https://www.uml-diagrams.org/sequence-diagrams.html)                                               |
| M02  | As mensagens assíncronas são representadas por uma seta com linha aberta?                                                | Indicam que o remetente não espera pela conclusão da operação e continua sua execução.                                                                                         | [IBM - Diagramas de Sequência](https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-sequence),                        |
| M03  | As mensagens de retorno (reply messages) são representadas por uma linha tracejada com seta aberta, voltando ao remetente original? | Mostram o retorno de uma chamada síncrona. Frequentemente omitidas se o retorno é óbvio.                                                                                  | [Lucidchart - Diagrama de Sequência](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml)                                                                                                                             |
| M04  | As mensagens têm nomes claros e correspondem a operações das classes receptoras (quando aplicável)?                      | O nome da mensagem geralmente reflete o método que está sendo invocado.                                                                                                        |            [Lucidchart - Diagrama de Sequência](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml)                                   |
| M05  | A ordem das mensagens (de cima para baixo) reflete a sequência temporal correta dos eventos?                             | Esta é a principal característica do diagrama de sequência.                                                                                                                    | [Visual Paradigm - Sequence Diagram Tutorial](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-sequence-diagram-tutorial/), [Sparx Systems - Sequence Diagram](https://sparxsystems.com/resources/tutorials/uml/sequence-diagram.html) [9](#ref9) |
| M06  | Auto-mensagens (self-messages), onde um objeto envia uma mensagem para si mesmo, estão corretamente representadas?        | A seta sai e retorna para a mesma lifeline, possivelmente com uma nova barra de ativação.                                                                                      | [UML Diagrams - Sequence](https://www.uml-diagrams.org/sequence-diagrams.html)                                                                                                                                                           |
| F01  | Fragmentos combinados (Combined Fragments) como `alt`, `opt`, `loop`, `par`, `ref` são usados corretamente quando necessário? | `alt` para escolhas alternativas, `opt` para opcionais, `loop` para repetições, `par` para paralelo, `ref` para referenciar outra interação.                               | [IBM - Diagramas de Sequência](https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-sequence), [Lucidchart - Diagrama de Sequência](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml)                |
| F02  | As condições de guarda (guards) nos fragmentos (ex: `[saldo > 0]`) estão claras e corretamente posicionadas?             | As condições determinam qual caminho da interação será seguido.                                                                                                                | [Visual Paradigm - Sequence Diagram Tutorial](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-sequence-diagram-tutorial/)                                                                                          |
| F03  | O escopo dos fragmentos combinados (a caixa retangular que os envolve) está claro e abrange as mensagens corretas?       | O fragmento deve englobar todas as mensagens que fazem parte daquela lógica condicional, opcional, de loop, etc.                                                              | [UML Diagrams - Sequence](https://www.uml-diagrams.org/sequence-diagrams.html)                                                                                                                                                           |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.



## Conclusão

A verificação dos Diagramas de Sequência do projeto Galáxia Conectada é uma etapa fundamental para garantir a robustez e a corretude do comportamento dinâmico do sistema. Ao aplicar os critérios definidos, foi possível assegurar que as interações entre os objetos e atores estão modeladas de forma clara.

## Bibliografia

<a name="ref1"></a>
[1] APOSTILA UML. Unified Modeling Language – Linguagem de Modelagem Unificada em Português. Seção sobre diagrama de atividades [e conceitos gerais de UML]. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref2"></a>
[2] UML DIAGRAMS. UML Activity Diagram Controls [Nota: Referência original sobre Diagrama de Atividades, conceitos de controle podem ter paralelos]. Disponível em: https://www.uml-diagrams.org/activity-diagrams-controls.html. Acesso em: 30 abr. 2025.

<a name="ref3"></a>
[3] BARCELAR, R. Engenharia de Software – Módulo 3: Modelagem de Sistemas Orientada a Objetos com UML. [Material Geral sobre UML]. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref4"></a>
[4] FOWLER, Martin. **UML Distilled**: A Brief Guide to the Standard Object Modeling Language. 3rd ed. Addison-Wesley Professional, 2003.

<a name="ref5"></a>
[5] IBM. Diagramas de Sequência. Rational Software Architect. Disponível em: https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-sequence. Acesso em: 06 mai. 2025. (Adaptado de "Diagramas de Atividades")

<a name="ref6"></a>
[6] LUCIDCHART. O que é Diagrama de Sequência UML?. Disponível em: https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml. Acesso em: 06 mai. 2025. (Adaptado de "O que é diagrama de atividades UML?")

<a name="ref7"></a>
[7] Object Management Group (OMG). Unified Modeling Language (UML) Specification. Version 2.5.1. 2017. Disponível em: https://www.omg.org/spec/UML/. Acesso em: 06 mai. 2025.

<a name="ref8"></a>
[8] TUTORIALSPOINT. UML - Sequence Diagrams. Disponível em: https://www.tutorialspoint.com/uml/uml_sequence_diagram.htm. Acesso em: 06 mai. 2025.

<a name="ref9"></a>
[9] SPARX SYSTEMS. UML Sequence Diagram. Enterprise Architect UML Tutorials. Disponível em: https://sparxsystems.com/resources/tutorials/uml/sequence-diagram.html. Acesso em: 06 mai. 2025.

<a name="ref10"></a>
[10] UML-DIAGRAMS. UML Sequence Diagrams Overview. UML Diagrams.org. Disponível em: https://www.uml-diagrams.org/sequence-diagrams.html. Acesso em: 06 mai. 2025.

<a name="ref11"></a>
[11] VISUAL PARADIGM. UML Sequence Diagram Tutorial (What is Sequence Diagram?). Visual Paradigm Guide. Disponível em: https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-sequence-diagram-tutorial/. Acesso em: 06 mai. 2025.


## Histórico de versão

| Versão | Alteração                                                     | Responsável     | Data       |
| :----- | :------------------------------------------------------------ | :-------------- | :--------- |
| 1.0    | Elaboração inicial do documento  | Larissa Stéfane          | 06/05/2025 |
| 1.0    | Complementação das tabelas | Larissa Stéfane          | 06/05/2025 |
