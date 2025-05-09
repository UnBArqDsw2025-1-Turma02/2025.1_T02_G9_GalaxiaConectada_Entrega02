# Verificação do Diagrama de Componentes

## Sumário
- [Introdução](#introdução)
- [Objetivos](#objetivos)
- [Metodologia](#metodologia)
- [Tabela de Verificação dos Componentes](#tabela-de-verificação-dos-componentes)
- [Tabela de Verificação dos Relacionamentos entre Componentes](#tabela-de-verificação-dos-relacionamentos-entre-componentes)
- [Observações](#observações)
- [Conclusão](#conclusão)
- [Bibliografia](#bibliografia)
- [Histórico de Versão](#histórico-de-versão)

## Introdução

Com base na Apostila UML [1] e no artigo da [IBM - Component Diagrams](https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component), o Diagrama de Componentes é um dos principais instrumentos da modelagem estrutural, uma vez que é usado para representar a arquitetura física do sistema e suas dependências. Com isso, ele revela os módulos, suas interações e a separação entre funcionalidades, o que serve como base para decisões de implementação e integração.

Neste projeto, o diagrama foi desenvolvido para o sistema **Galáxia Conectada** ao refletir a disposição dos principais componentes do sistema, como autenticação, gestão de cursos, banco de dados, interfaces e serviços externos.

## Objetivos

Este artefato tem como finalidade verificar a correção e completude do Diagrama de Componentes do projeto **Galáxia Conectada**, com base em critérios objetivos e fontes confiáveis. Busca-se assegurar clareza na arquitetura do sistema, bem como identificar falhas ou omissões que possam comprometer a compreensão ou manutenção futura.

## Metodologia

Como o projeto está sendo conduzido por uma única estudante de Engenharia de Software, a verificação foi conduzida de maneira independente e estruturada, conforme os passos:

1. **Revisão teórica** da notação UML, com foco no diagrama de componentes;
2. **Criação e refinamento do diagrama**, baseado nos requisitos e módulos do sistema;
3. **Avaliação estruturada**, com critérios registrados nas tabelas abaixo;
4. **Correções e melhorias**, com base no resultado da verificação.

A verificação foi apoiada por literaturas, ferramentas online e guias de boas práticas da UML.

## Tabela de Verificação dos Componentes

| ID   | Critério de Verificação                                                                 | Explicação                                                                                         | Rastreabilidade |
|------|------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|-----------------|
| CP01 | Cada componente possui um nome claro, único e significativo?                            | Facilita a identificação e entendimento das responsabilidades.                                     | [UML Diagrams](https://www.uml-diagrams.org/component-diagrams.html) |
| CP02 | O componente está representado com a notação padrão UML?                                | Retângulo com dois retângulos menores à esquerda (símbolo de componente).                         | [Lucidchart](https://www.lucidchart.com/pages/uml-component-diagram) |
| CP03 | Os nomes dos componentes estão padronizados (ex: linguagem, convenções)?                 | Consistência entre elementos promove clareza.                                                      | Apostila UML |
| CP04 | Os componentes representam partes reais e executáveis do sistema?                        | Como bibliotecas, serviços, APIs, módulos etc.                                                     | [IBM Docs](https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component) |
| CP05 | Os componentes estão agrupados de forma lógica por responsabilidade?                     | Promove coesão e modularidade.                                                                    | [IBM Docs](https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component); Apostila UML|
| CP06 | Há clareza na distinção entre componentes internos e externos?                           | Auxilia a entender a fronteira do sistema.                                                        | [UML Diagrams](https://www.uml-diagrams.org/component-diagrams.html) |
| CP07 | O número de componentes está adequado à complexidade do sistema?                         | Nem excesso, nem omissão de módulos.                                                              | [StarUML Docs](http://staruml.io/docs/guide/uml/component-diagram) |
| CP08 | Cada componente está ligado a um ou mais artefatos (ex: .jar, .dll, .py, executáveis)?   | Mostra concretude dos módulos.                                                                    | [Sparx Systems](https://sparxsystems.com/enterprise_architect_user_guide/15.2/model_domains/componentdiagram.html) |
| CP09 | As interfaces internas de cada componente estão representadas ou documentadas?           | Relevante para integração e reutilização.                                                         | [Lucidchart](https://www.lucidchart.com/pages/uml-component-diagram) |
| CP10 | Os nomes refletem a função do componente no negócio (sem nomes genéricos como “Comp1”)?  | Melhora o entendimento para não desenvolvedores.                                                  | [Visual Paradigm](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-component-diagram/) |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Tabela de Verificação dos Relacionamentos entre Componentes

| ID   | Critério de Verificação                                                                  | Explicação                                                                                         | Rastreabilidade |
|------|-------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|-----------------|
| RC01 | As dependências estão representadas por setas tracejadas com direção correta?            | Representa corretamente o uso de um componente por outro.                                         | [IBM Docs](https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component) |
| RC02 | As interfaces fornecidas estão representadas com “lollipop”?                             | Símbolo de círculo indica o que o componente oferece.                                              | [Lucidchart](https://www.lucidchart.com/pages/uml-component-diagram) |
| RC03 | As interfaces exigidas estão representadas com “socket” (semicírculo)?                    | Indica o que o componente precisa de outro para funcionar.                                        | [IBM Docs](https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component); Apostila UML |
| RC04 | Existem nomes ou anotações nos relacionamentos quando o significado não é óbvio?          | Melhora a compreensão dos fluxos e das integrações.                                               | [Sparx Systems](https://sparxsystems.com/enterprise_architect_user_guide/15.2/model_domains/componentdiagram.html) |
| RC05 | Há relação excessiva entre os mesmos componentes (acoplamento forte)?                     | Avaliar para promover independência e manutenção.                                                  | [StarUML Docs](http://staruml.io/docs/guide/uml/component-diagram) |
| RC06 | As interfaces estão sendo reutilizadas por múltiplos componentes, se aplicável?           | Boa prática de arquitetura orientada a serviços e modularidade.                                   | [IBM Docs](https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component); Apostila UML |
| RC07 | Todos os relacionamentos refletem integrações reais do sistema?                           | Evita dependências fictícias ou não justificadas.                                                 | [UML Diagrams](https://www.uml-diagrams.org/component-diagrams.html) |
| RC08 | As dependências não são circulares (um depende de outro que depende do primeiro)?         | Ajuda a evitar loops de dependência e acoplamento excessivo.                                     | [IBM Docs](https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component) |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Observações



## Conclusão

A verificação do Diagrama de Componentes do sistema **Galáxia Conectada** demonstra que o modelo segue boas práticas da UML, está bem estruturado e facilita a compreensão da arquitetura. A análise criteriosa por meio de tabelas ajudou a identificar pontos fortes e aspectos que podem ser melhorados com o avanço do projeto.

## Bibliografia

1. APOSTILA UML. Seção sobre representação de classes. Disponíbilizada pela professora. Acesso em: 25 abr. 2025.
2. IBM CORPORATION. *Component diagrams*. IBM Documentation, 2023. Disponível em: https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component. Acesso em: 25 abr. 2025.
3. LUCID SOFTWARE INC. *UML Component Diagram*. Lucidchart, 2024. Disponível em: https://www.lucidchart.com/pages/uml-component-diagram. Acesso em: 25 abr. 2025.
4. SPARX SYSTEMS. *Component Diagram*. Enterprise Architect Documentation, 2024. Disponível em: https://sparxsystems.com/enterprise_architect_user_guide/15.2/model_domains/componentdiagram.html. Acesso em: 25 abr. 2025.
5. STARUML. *Component Diagrams*. StarUML Docs, 2024. Disponível em: http://staruml.io/docs/guide/uml/component-diagram. Acesso em: 25 abr. 2025.
6. UML DIAGRAMS. *Component Diagrams*. Disponível em: https://www.uml-diagrams.org/component-diagrams.html. Acesso em: 25 abr. 2025.  

## Histórico de Versão


| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 25/04/2025 |
| 1.1 | Adição de novas referências, links e critérios | Larissa Stéfane | 25/04/2025 |

