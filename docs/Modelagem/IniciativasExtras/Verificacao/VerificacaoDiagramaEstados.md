# Verificação do Diagrama de Estados

## Sumário
- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Tabela de Verificação para Estados e Elementos Fundamentais](#Tabela-de-Verificação-para-Estados-e-Elementos-Fundamentais)
- [Tabela de Verificação para Transições, Eventos e Ações](#Tabela-de-Verificação-para-Transições-Eventos-e-Ações)
- [Observações](#Observações)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)

## Introdução

O Diagrama de Estados, também conhecido como Diagrama de Máquina de Estados, é um diagrama comportamental da UML que especifica as sequências de estados pelos quais um objeto ou uma interação passa durante seu ciclo de vida em resposta a eventos, com base em [Diagrama de Máquina de Estados](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml) [6](#ref6). Com isso, ele é fundamental para modelar o comportamento dinâmico de entidades que possuem estados significativos e cujo comportamento muda com base nesses estados. No projeto Galáxia Conectada, Diagramas de Estados podem ser usados para modelar o ciclo de vida de um `Usuário` (ex: Não Verificado, Ativo, Suspenso), o progresso de uma `Inscrição` em um curso (ex: Iniciada, Paga, Concluída, Cancelada), ou o estado de um `ConteúdoInterativo`.

A verificação destes diagramas é essencial para garantir que todos os possíveis estados de um objeto, as transições entre eles, os eventos que as disparam e as ações resultantes estejam corretamente e completamente modelados.

## Objetivos

Este artefato tem como objetivo principal realizar a verificação dos Diagramas de Estados desenvolvidos para o projeto Galáxia Conectada. Busca-se assegurar que:
* Todos os estados relevantes de um objeto ou sistema sejam identificados e representados.
* As transições entre estados sejam válidas e acionadas pelos eventos corretos.
* As ações e atividades associadas aos estados e transições estejam claramente definidas.
* Os diagramas estejam em conformidade com a notação e as regras da UML ([UML Diagrams - State Machine](https://www.uml-diagrams.org/state-machine-diagrams.html) [10](#ref10)).
* Os diagramas sejam compreensíveis, consistentes e completos para os objetos modelados.

## Metodologia

A metodologia para a criação e verificação dos Diagramas de Estados envolveu, primeiramente, um estudo detalhado da UML, com ênfase nos componentes e na semântica dos Diagramas de Máquina de Estados em APOSTILA UML [1](#ref1). Com base nos requisitos do projeto Galáxia Conectada e na identificação de objetos com comportamento dinâmico complexo, foram elaborados os Diagramas de Estados.

Cada diagrama foi então submetido a uma verificação ao utilizar as tabelas de checklist apresentadas neste documento. Estas tabelas cobrem aspectos desde a representação correta dos elementos (estados, transições, pseudoestados) até a lógica do comportamento modelado. 

## Tabela de Verificação para Estados e Elementos Fundamentais

**Tabela 1:** Perguntas para a verificação de Estados e Elementos Fundamentais.

| ID   | Pergunta de Verificação                                                                                                | Explicação                                                                                                                                  | Rastreabilidade                                                                                                                                                                                                                            |
|------|------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| E01  | Os estados são representados por retângulos com cantos arredondados?                                                     | Esta é a notação padrão para estados em um Diagrama de Máquina de Estados.                                                                  | [Lucidchart - Diagrama de Máquina de Estados](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml), [UML Diagrams - State Machine](https://www.uml-diagrams.org/state-machine-diagrams.html)                             |
| E02  | Cada estado possui um nome claro e significativo que descreve a condição do objeto?                                      | O nome do estado deve ser conciso e representar uma situação identificável do objeto.                                                       |  [Lucidchart - Diagrama de Máquina de Estados](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml), [UML Diagrams - State Machine](https://www.uml-diagrams.org/state-machine-diagrams.html)  |
| E03  | Existe um estado inicial claramente definido, representado por um círculo preenchido?                                     | Todo Diagrama de Estados deve ter um único ponto de partida.                                                                                | [Lucidchart - Diagrama de Máquina de Estados](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml), [TutorialsPoint - Statechart Diagrams](https://www.tutorialspoint.com/uml/uml_statechart_diagram.htm) [8](#ref8) |
| E04  | Existem um ou mais estados finais claramente definidos, representados por um círculo preenchido dentro de outro círculo (olho de boi)? | Indica o término do ciclo de vida ou de um processo modelado pela máquina de estados.                                                     | [UML Diagrams - State Machine](https://www.uml-diagrams.org/state-machine-diagrams.html), [Visual Paradigm - State Machine Diagram Guide](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-state-machine-diagram/)    |
| E05  | As atividades internas de um estado (entry, do, exit) estão corretamente especificadas, se houver?                       | `entry`: ação ao entrar no estado; `do`: atividade contínua enquanto no estado; `exit`: ação ao sair do estado.                             | [Visual Paradigm - State Machine Diagram Guide](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-state-machine-diagram/)  |
| E06  | Estados compostos (submáquinas ou estados com regiões ortogonais) são usados adequadamente para gerenciar complexidade?    | Estados compostos ajudam a organizar diagramas complexos aninhando máquinas de estados ou mostrando paralelismo.                             | [UML Diagrams - State Machine](https://www.uml-diagrams.org/state-machine-diagrams.html#composite-states)                                                                                                                                        |
| E07  | Pseudoestados como 'choice' (escolha), 'junction' (junção), 'history' (histórico - superficial ou profundo) são usados corretamente? | `choice`: ramificação dinâmica baseada em condição; `junction`: une/divide transições; `history`: lembra o último subestado ativo. |  [Visual Paradigm - State Machine Diagram Guide](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-state-machine-diagram/)    |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Tabela de Verificação para Transições, Eventos e Ações

**Tabela 2:** Perguntas para a verificação de Transições, Eventos e Ações.

| ID   | Pergunta de Verificação                                                                                                | Explicação                                                                                                                                                           | Rastreabilidade                                                                                                                                                                                                                            |
|------|------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| T01  | As transições entre estados são representadas por setas direcionadas do estado de origem para o estado de destino?       | A seta indica a mudança de um estado para outro.                                                                                                                     | [Lucidchart - Diagrama de Máquina de Estados](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml), [UML Diagrams - State Machine](https://www.uml-diagrams.org/state-machine-diagrams.html)                             |
| T02  | Cada transição é rotulada com o evento que a dispara (trigger), opcionalmente seguido por uma condição de guarda e uma ação/efeito? | Formato: `evento [condição_guarda] / ação_efeito`.                                                                                                      | [UML Diagrams - State Machine](https://www.uml-diagrams.org/state-machine-diagrams.html)     |
| T03  | Os eventos (triggers) são nomeados de forma clara e representam ocorrências significativas?                             | Eventos podem ser sinais, chamadas de operação, passagem de tempo ou mudança de condição.                                                                            | [Visual Paradigm - State Machine Diagram Guide](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-state-machine-diagram/), [TutorialsPoint - Statechart Diagrams](https://www.tutorialspoint.com/uml/uml_statechart_diagram.htm) |
| T04  | As condições de guarda (`[condição]`) são expressões booleanas que devem ser verdadeiras para a transição ocorrer?     | Guardas permitem ou bloqueiam uma transição mesmo que o evento ocorra.                                                                                              | [UML Diagrams - State Machine](https://www.uml-diagrams.org/state-machine-diagrams.html#guards-actions), [Sparx Systems - State Machine Diagram](https://sparxsystems.com/resources/tutorials/uml/state-machine-diagram.html)                  |
| T05  | As ações/efeitos (`/ ação`) associadas às transições são breves e representam um comportamento atômico?                  | Ações são executadas quando a transição é disparada e a guarda (se houver) é satisfeita.                                                                             | [UML Diagrams - State Machine](https://www.uml-diagrams.org/state-machine-diagrams.html)                                                                         |
| T06  | Transições internas (self-transitions), onde o estado de origem e destino são os mesmos, estão corretamente representadas? | Uma seta que sai e retorna ao mesmo estado. Útil para executar ações em resposta a um evento sem mudar de estado.                                                    | [Lucidchart - Diagrama de Máquina de Estados](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml)                                                                                                                |
| T07  | O diagrama é determinístico (para um dado estado e evento, há no máximo uma transição válida)? Ou o não-determinismo é intencional e bem compreendido? | Geralmente, máquinas de estado são determinísticas. Se não forem, as condições de guarda devem resolver ambiguidades.                                   |                                                                                                                                     | [Lucidchart - Diagrama de Máquina de Estados](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml)  
| T08  | Todas as transições possíveis a partir de cada estado foram consideradas?                                                | O diagrama deve cobrir todos os caminhos relevantes do ciclo de vida do objeto.                                                                                      | [Visual Paradigm - State Machine Diagram Guide](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-state-machine-diagram/)                                                                                          |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Conclusão

A verificação dos Diagramas de Estados para o projeto Galáxia Conectada é um passo crucial para assegurar que o comportamento de objetos complexos seja modelado com precisão e completude. 

## Bibliografia

<a name="ref1"></a>
[1] APOSTILA UML. Unified Modeling Language – Linguagem de Modelagem Unificada em Português. Seção sobre diagrama de atividades [e conceitos gerais de UML]. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref2"></a>
[2] BARCELAR, R. Engenharia de Software – Módulo 3: Modelagem de Sistemas Orientada a Objetos com UML. [Material Geral sobre UML]. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref3"></a>
[3] FOWLER, Martin. **UML Distilled**: A Brief Guide to the Standard Object Modeling Language. 3rd ed. Addison-Wesley Professional, 2003.

<a name="ref4"></a>
[4] IBM. Diagramas de Máquina de Estados. IBM Documentation - Engineering Lifecycle Management. Disponível em: https://www.ibm.com/docs/pt-br/engineering-lifecycle-management-suite/systems-design-rhapsody/6.0.6?topic=diagrams-statechart. Acesso em: 06 mai. 2025.

<a name="ref5"></a>
[5] Object Management Group (OMG). Unified Modeling Language (UML) Specification. Version 2.5.1. 2017. Disponível em: https://www.omg.org/spec/UML/. Acesso em: 06 mai. 2025.

<a name="ref6"></a>
[6] LUCIDCHART. O que é Diagrama de Máquina de Estados UML?. Disponível em: https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml. Acesso em: 06 mai. 2025.

<a name="ref7"></a>
[7] MDN Web Docs. State machine diagrams. Disponível em: https://developer.mozilla.org/en-US/docs/Games/Techniques/State_machine_diagrams. Acesso em: 06 mai. 2025. (Referência conceitual sobre máquinas de estado)

<a name="ref8"></a>
[8] TUTORIALSPOINT. UML - Statechart Diagrams. Disponível em: https://www.tutorialspoint.com/uml/uml_statechart_diagram.htm. Acesso em: 06 mai. 2025.

<a name="ref9"></a>
[9] SPARX SYSTEMS. UML State Machine Diagram. Enterprise Architect UML Tutorials. Disponível em: https://sparxsystems.com/resources/tutorials/uml/state-machine-diagram.html. Acesso em: 06 mai. 2025.

<a name="ref10"></a>
[10] UML-DIAGRAMS. UML State Machine Diagrams Overview. UML Diagrams.org. Disponível em: https://www.uml-diagrams.org/state-machine-diagrams.html. Acesso em: 06 mai. 2025.

<a name="ref11"></a>
[11] VISUAL PARADIGM. What is State Machine Diagram? (State Diagram). Visual Paradigm Guide. Disponível em: https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-state-machine-diagram/. Acesso em: 06 mai. 2025.

## Histórico de versão

| Versão | Alteração                                                     | Responsável     | Data       |
| :----- | :------------------------------------------------------------ | :-------------- | :--------- |
| 1.0    | Criação do documento | Larissa Stéfane          | 06/05/2025 |

