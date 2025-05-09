# Verificação do Diagrama de Implantação

## Sumário
- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Tabela de Verificação para os Nós (Dispositivos e Ambientes de Execução)](#Tabela-de-Verificação-para-os-Nós-Dispositivos-e-Ambientes-de-Execução)
- [Tabela de Verificação para Artefatos e Caminhos de Comunicação](#Tabela-de-Verificação-para-Artefatos-e-Caminhos-de-Comunicação)
- [Observações](#Observações)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)

## Introdução

O Diagrama de Implantação, segundo a [especificação UML](https://www.omg.org/spec/UML/) [7](#ref7), é um diagrama estrutural que modela a arquitetura física de um sistema. Ele mostra como os artefatos de software (executáveis, bibliotecas, arquivos de configuração, etc.) são distribuídos e implantados nos nós de hardware (servidores, dispositivos) e ambientes de execução (sistemas operacionais, containers), de acordo com [O que é um diagrama de implementação?](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml) [5](#ref5). No contexto do projeto Galáxia Conectada, este diagrama é crucial para visualizar a topologia de implantação da plataforma, ao incluir servidores web, bancos de dados e possíveis integrações com serviços externos.

A verificação deste diagrama assegura que a representação da infraestrutura física e da distribuição dos componentes de software esteja correta, completa e alinhada com os requisitos não funcionais do sistema, como desempenho, escalabilidade e segurança. 

## Objetivos

Este artefato tem como objetivo realizar a verificação do Diagrama de Implantação criado para o projeto Galáxia Conectada. A finalidade é garantir que ele represente com precisão a arquitetura física planejada para o sistema, que todos os nós, artefatos e conexões relevantes estejam modelados corretamente conforme os padrões UML, [UML Diagrams](https://www.uml-diagrams.org/deployment-diagrams-overview.html) [11](#ref11)) e que o diagrama seja consistente com os demais artefatos de arquitetura e os requisitos do projeto.

## Metodologia

Similarmente à verificação de outros diagramas UML no projeto, a metodologia para o Diagrama de Implantação envolveu, primeiramente, o estudo dos conceitos e da notação UML específica para este diagrama .Com base na arquitetura de software definida e nos requisitos de infraestrutura do Galáxia Conectada, foi elaborado um esboço do diagrama. Posteriormente, aplicou-se um processo de verificação sistemática utilizando tabelas de checklist abaixo. Cada item das tabelas foi analisado em relação ao diagrama proposto. As inconsistências ou omissões identificadas foram corrigidas para garantir a conformidade com as boas práticas de modelagem de implantação.

## Tabela de Verificação para os Nós

**Tabela 1:** Perguntas para a verificação dos Nós no Diagrama de Implantação.

| ID   | Pergunta de Verificação                                                                 | Explicação                                                                                                | Rastreabilidade                                                                                                                                                                                             |
|------|-----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| N01  | Os nós (nodes) estão representados corretamente como cubos tridimensionais?              | A notação padrão UML para nós (dispositivos ou ambientes de execução) é um cubo.                           |  [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml), [Visual Paradigm](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-deployment-diagram/) |
| N02  | Cada nó possui um nome claro e representativo da sua função (ex: Servidor Web, BD)?     | A nomenclatura deve facilitar a compreensão da arquitetura física.                                        |  [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml)                     |
| N03  | Estereótipos (`<<device>>`, `<<executionEnvironment>>`) são usados para clarificar o tipo de nó? | Estereótipos ajudam a distinguir entre nós de hardware e ambientes de software.                           | [UML Spec (OMG)](https://www.omg.org/spec/UML/), [IBM](https://www.ibm.com/docs/pt-br/rsas/7.5.0?topic=topologies-deployment-diagrams), [UML Diagrams](https://www.uml-diagrams.org/deployment-diagrams-overview.html)       |
| N04  | As especificações relevantes do nó (ex: SO, hardware) estão indicadas usando tags?     | Valores Marcados (Tagged Values) podem detalhar características importantes dos nós.                      | [UML Spec (OMG)](https://www.omg.org/spec/UML/), [IBM](https://www.ibm.com/docs/pt-br/rsas/7.5.0?topic=topologies-deployment-diagrams)                                                                                                                       |
| N05  | Nós aninhados (nested nodes) são usados corretamente para representar ambientes contidos? | Útil para mostrar, por exemplo, um servidor de aplicação rodando dentro de um servidor físico.             |  [Visual Paradigm](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-deployment-diagram/)                                                                                                             |
| N06  | Todos os componentes físicos relevantes da infraestrutura estão representados por nós?   | O diagrama deve incluir todos os servidores, dispositivos e ambientes de execução chave.                  | [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml), [Edraw](https://www.edrawsoft.com/pt/deployment-chart-example.html)                                                                                                                   |
| N07  | A relação entre os nós (ex: um dispositivo contido em outro) está clara?                | Se houver hierarquia ou contenção de nós, ela deve ser visualmente representada.                         | [UML Spec (OMG)](https://www.omg.org/spec/UML/)                                                                                                                                 |
| N08  | Os nomes dos nós seguem um padrão consistente (ex: PascalCase)?                         | Padronização de nomes melhora a legibilidade e profissionalismo do diagrama.                             | [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml)                                                                                                                               |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Tabela de Verificação Caminhos de Comunicação

**Tabela 2:** Perguntas para a verificação dos Artefatos e Caminhos de Comunicação.

| ID   | Pergunta de Verificação                                                                                                   | Explicação                                                                                                                             | Rastreabilidade                                                                                                                                                                                             |
|------|---------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| A01  | Os artefatos (artifacts) estão representados corretamente com o ícone de documento (retângulo com canto dobrado)?          | Esta é a notação padrão UML para artefatos como executáveis, bibliotecas, schemas de BD, etc.                                         |  [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml), [Visual Paradigm](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-deployment-diagram/) |
| A02  | Cada artefato possui um nome claro e representativo (ex: `webapp.war`, `user_db_schema.sql`)?                              | A nomenclatura deve identificar o componente de software específico.                                                                    |           [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml), [Visual Paradigm](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-deployment-diagram/)                                                                                                                         |
| A03  | Estereótipos (`<<executable>>`, `<<library>>`, `<<file>>`) são usados para clarificar o tipo de artefato?                   | Estereótipos ajudam a entender a natureza do componente de software.                                                                     | [UML Spec (OMG)](https://www.omg.org/spec/UML/), [UML Diagrams](https://www.uml-diagrams.org/deployment-diagrams-overview.html)                                                                                                              |
| A04  | A relação de implantação (deploy) entre um artefato e um nó está representada por uma linha tracejada com seta aberta?      | A seta aponta do artefato para o nó onde ele é implantado. Opcionalmente, pode usar a palavra-chave `<<deploy>>`.                       | [UML Spec (OMG)](https://www.omg.org/spec/UML/), [IBM](https://www.ibm.com/docs/pt-br/rsas/7.5.0?topic=topologies-deployment-diagrams)                                                                                                                       |
| A05  | Todos os artefatos de software significativos do sistema estão representados e associados a um nó?                          | O diagrama deve mostrar onde cada componente chave do software reside na infraestrutura.                                               | [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml), [Edraw](https://www.edrawsoft.com/pt/deployment-chart-example.html)                                                                                                                   |
| A06  | As dependências entre artefatos (manifest) estão representadas corretamente (ex: `<<manifest>>`)?                           | Útil para mostrar que um artefato (ex: um JAR) contém outros (ex: arquivos .class).                                                    | [UML Spec (OMG)](https://www.omg.org/spec/UML/), [UML Diagrams](https://www.uml-diagrams.org/deployment-diagrams-overview.html)                                                                                                              |
| C01  | Os caminhos de comunicação (communication paths) entre nós estão representados por linhas sólidas?                          | Linhas sólidas conectam nós que se comunicam diretamente.                                                                              |  [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml)                     |
| C02  | Os protocolos de comunicação (ex: HTTP, JDBC, RMI) estão indicados nos caminhos de comunicação, se relevante?              | Adicionar o protocolo como um estereótipo (`<<HTTP>>`) ou tag no caminho de comunicação aumenta a clareza.                             | [UML Spec (OMG)](https://www.omg.org/spec/UML/), [IBM](https://www.ibm.com/docs/pt-br/rsas/7.5.0?topic=topologies-deployment-diagrams)                                                                                                                       |
| C03  | A direção da comunicação é indicada por setas, se for relevante ou não óbvia?                                               | Embora opcionais, setas podem clarificar o fluxo de comunicação entre os nós.                                                          | [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml)                                                                                                                               |
| C04  | Todos os links de comunicação essenciais entre os componentes da infraestrutura estão modelados?                             | O diagrama deve refletir como os diferentes nós do sistema interagem.                                                                  | [Lucidchart](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml), [Edraw](https://www.edrawsoft.com/pt/deployment-chart-example.html)                                                                                                                   |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.


## Conclusão

A verificação do Diagrama de Implantação do projeto Galáxia Conectada foi essencial para validar a arquitetura física proposta para o sistema. Através da aplicação das tabelas de verificação, foi possível assegurar que a disposição dos artefatos de software. Este processo contribui para mitigar riscos relacionados à implantação e garante uma visão clara da infraestrutura necessária para a operação da plataforma.

## Bibliografia

<a name="ref1"></a>
[1] APOSTILA UML. Seção sobre Diagrama de Implantação. Disponibilizada pela professora. Acesso em: 05 mai. 2025.

<a name="ref2"></a>
[2] EDRAWSOFT. Exemplos de Diagrama de Implantação UML. Edraw, 2024. Disponível em: https://www.edrawsoft.com/pt/deployment-chart-example.html. Acesso em: 28 abr. 2025.

<a name="ref3"></a>
[3] FOWLER, Martin. **UML Distilled**: A Brief Guide to the Standard Object Modeling Language. 3rd ed. Addison-Wesley Professional, 2003.

<a name="ref4"></a>
[4] IBM CORPORATION. Diagramas de implantação. IBM Documentation, 2024. Disponível em: https://www.ibm.com/docs/pt-br/rsas/7.5.0?topic=topologies-deployment-diagrams. Acesso em: 28 abr. 2025.

<a name="ref5"></a>
[5] LUCID SOFTWARE INC. O que é diagrama de implementação UML. Lucidchart, 2024. Disponível em: https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml. Acesso em: 28 abr. 2025.

<a name="ref6"></a>
[6] MAURO DE BONI. Tutorial Draw.io: Como Fazer Diagrama de Implantação da UML. YouTube, 2023. Disponível em: https://www.youtube.com/watch?v=eFFq3SLMQJ4. Acesso em: 30 abr. 2025.

<a name="ref7"></a>
[7] Object Management Group (OMG). Unified Modeling Language (UML) Specification. Version 2.5.1. 2017. Disponível em: https://www.omg.org/spec/UML/. Acesso em: 05 mai. 2025.

<a name="ref8"></a>
[8] PROFESSOR PAIVA. Curso de UML - Diagrama de Implantação. YouTube, 2022. Disponível em: https://www.youtube.com/watch?v=DgERD0HgggQ. Acesso em: 30 abr. 2025.

<a name="ref9"></a>
[9] SPARX SYSTEMS. Deployment Diagram. Enterprise Architect UML Tutorials, 2024. Disponível em: https://sparxsystems.com/resources/tutorials/uml/deployment-diagram.html. Acesso em: 05 mai. 2025.

<a name="ref10"></a>
[10] TUTORIALSPOINT. UML - Deployment Diagrams. TutorialsPoint, 2024. Disponível em: https://www.tutorialspoint.com/uml/uml_deployment_diagram.htm. Acesso em: 05 mai. 2025.

<a name="ref11"></a>
[11] UML-DIAGRAMS. Deployment Diagrams Overview. UML Diagrams.org, 2024. Disponível em: https://www.uml-diagrams.org/deployment-diagrams-overview.html. Acesso em: 28 abr. 2025.

<a name="ref12"></a>
[12] VISUAL PARADIGM. What is Deployment Diagram?. Visual Paradigm Guide, 2024. Disponível em: https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-deployment-diagram/. Acesso em: 28 abr. 2025.

## Histórico de versão

| Versão | Alteração                                                              | Responsável     | Data       |
| :----- | :--------------------------------------------------------------------- | :-------------- | :--------- |
| 1.0    | Elaboração inicial do documento de verificação                          | Larissa Stéfane | 05/05/2025 |
| 1.1    | Adição das tabelas de verificação                                      | Larissa Stéfane | 05/05/2025 |
| 2.0    | Adição de referências bibliográficas e links na rastreabilidade         | Larissa Stéfane   | 05/05/2025 |
| 3.0    | Ajuste da formatação da bibliografia (ABNT) e rastreabilidade          | Larissa Stéfane    | 05/05/2025 |
| 4.0    | Ajuste da formatação da bibliografia (âncoras) e citações no texto | Larissa Stéfane   | 05/05/2025 |

