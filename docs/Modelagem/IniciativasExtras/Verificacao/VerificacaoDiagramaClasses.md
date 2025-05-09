# Verificação do Diagrama de Classes

## Sumário
- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Tabela de Verificação para as Classes](#Tabela-de-Verificação-para-as-Classes)
- [Tabela de Verificação para os Relacionamentos das Classes](#Tabela-de-Verificação-para-os-Relacionamentos-das-Classes)
- [Observações](#Observações)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)

## Introdução

Ao considerar a Apostila UML [1], o Diagrama de Classes é um dos elementos centrais da modelagem estática em UML, usado para representar a estrutura de um sistema por meio de suas classes, atributos, métodos e relacionamentos. Com isso em mente, no projeto Galáxia Conectada, esse diagrama foi elaborado para modelar as entidades como usuários, cursos e conteúdos interativos. 

A verificação, por sua vez, é um processo o qual avalia se o diagrama foi construído corretamente, conforme os critérios da UML, o que permite a identificação de erros ainda nas fases iniciais do desenvolvimento e garante a consistência e qualidade do sistema final.

## Objetivos

Este artefato tem como objetivo realizar a verificação do diagrama de classes criado para o projeto Galáxia Conectada ao garantir que ele atenda aos critérios de qualidade, de clareza e de precisão definidos pela UML. COm isso, a verificação busca assegurar que todas as classes e seus relacionamentos estejam corretamente representados, que os elementos obrigatórios estejam presentes e que o diagrama seja coerente com os requisitos funcionais da plataforma.

## Metodologia

Como o desenvolvimento do projeto está sendo conduzido por uma única estudante de Engenharia de Software, a metodologia adotada para criação e verificação do diagrama de classes foi estruturada em etapas progressivas. Primeiramente, foi realizada uma pesquisa teórica sobre a linguagem UML, com foco no entendimento detalhado da estrutura e das regras do diagrama de classes. Em seguida, com base nos requisitos levantados para o projeto Galáxia Conectada, foi feito o esboço inicial do diagrama, representando as entidades e seus relacionamentos principais.

Após essa etapa, foi aplicada a verificação do diagrama, utilizando uma tabela de verificação previamente definida com critérios técnicos. Cada item da tabela será analisado e os pontos que apresentarem problemas serão corrigidos com base nas boas práticas da modelagem orientada a objetos.

## Tabela de Verificação para as Classes

**Tabela 1:** Perguntas para a verificação das classes.

| ID  | Pergunta de Verificação   | Explicação            | Rastreabilidade   |
|-----|---------------------------|-----------------------|-------------------|
| C01 | O nome da classe começa com letra maiúscula?                                             | Seguir convenções de nomenclatura.                                       | [Webel IT Australia](https://www.webel.com.au/node/669) |
| C02 | A classe está representada com três compartimentos (nome, atributos e operações)?        | A estrutura padrão de uma classe em UML inclui esses três compartimentos.                                      | Apostila UML, seção sobre representação de classes |
| C03 | O nome da classe representa um substantivo?                                              | Classes geralmente representam entidades ou objetos do mundo real.                                             | [GeeksforGeeks](https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/)  |
| C04 | Os atributos estão devidamente especificados com nome e tipo?                            | Detalhar atributos com seus tipos garante clareza na estrutura de dados.                                       | [GeeksforGeeks](https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/) |
| C05 | Os métodos (operações) estão claramente definidos com nome e parâmetros?                 | Especificar operações com seus parâmetros define o comportamento da classe.                                    | [GeeksforGeeks](https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/) |
| C06 | A classe representa uma entidade relevante do sistema?                                   | Classes devem corresponder a entidades significativas no domínio do sistema.                                   | [GeeksforGeeks](https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/) |
| C07 | Existem classes externas (sistemas, bibliotecas) que devem ser representadas?            | Identificar e representar classes externas permite modelar interações com outros sistemas.                     | Apostila UML, seção sobre bibliotecas e sistemas externos |
| C08 | A classe está associada a um ator do sistema, como usuário ou operador?                  | Ator pode ser representado como classe para modelar suas interações com o sistema.                             | Apostila UML, seção sobre papéis de atores |
| C09 | Os atributos estão nomeados utilizando camelCase?                                        | Seguir convenções de nomenclatura.                                       | [Ez Knowledge](https://www.ez-knowledge.com/comprehensive-guide-to-uml-class-diagrams/) |
| C10 | Os métodos estão nomeados utilizando camelCase?                                          | Seguir convenções de nomenclatura.                                       | [Ez Knowledge](https://www.ez-knowledge.com/comprehensive-guide-to-uml-class-diagrams/) |
| C11 | Os atributos e métodos estão alinhados à esquerda e em fonte normal?                     | Seguir convenções de formatação melhora a legibilidade e padronização.                                         | [UML Diagrams](https://www.uml-diagrams.org/class-reference.html) |
| C12 | Os métodos estão representados com parênteses, mesmo sem parâmetros?                     | Seguir convenções de representação melhora a clareza do diagrama.                                              | [University of Cape Town](https://www.cs.uct.ac.za/mit_notes/software/htmls/ch05s09.html) |
| C13 | Os atributos e métodos estão listados em ordem decrescente de visibilidade?              | Seguir convenções de ordenação melhora a organização e compreensão do diagrama.                                | [Creately Blog](https://creately.com/blog/diagrams/guidelines-for-uml-class-diagrams-part-1/) |
| C14 | Os métodos estão nomeados utilizando verbos no infinitivo?                               | Seguir convenções de nomenclatura melhora a clareza sobre o comportamento da classe.                           | [Visual Paradigm](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/) |
| C15 | Os métodos estão representados com seus parâmetros e tipos?                              | Detalhar métodos com seus parâmetros e tipos garante clareza na definição do comportamento da classe.          | [UML Diagrams](https://www.uml-diagrams.org/class-reference.html) |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Tabela de Verificação para os Relacionamentos das Classes

**Tabela 1:** Perguntas para a verificação do diagrama

| ID  | Pergunta de Verificação  | Explicação  | Rastreabilidade  |
|-----|--------------------------|-------------|------------------|
| DC01 | As associações entre classes estão corretamente representadas com linhas contínuas e, se necessário, com setas indicando a direção? | Associações representam relações estruturais entre classes e devem ser claramente indicadas com linhas contínuas; setas podem ser usadas para indicar a navegabilidade. | Apostila UML; [GeeksforGeeks](https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/)                                                                                                                                                                                                                                                                        |
| DC02 | As multiplicidades nas associações estão especificadas corretamente (por exemplo, 1..*, 0..1)?                   | Multiplicidades definem quantas instâncias de uma classe podem estar associadas a instâncias de outra classe, sendo essenciais para compreender as restrições do sistema. | Apostila UML; [Creately](https://creately.com/guides/class-diagram-relationships/)                                                                                                                                                                                                                                                                                                |
| DC03 | As dependências estão representadas com linhas tracejadas e setas apontando da classe dependente para a classe da qual depende? | Dependências indicam que uma classe utiliza ou depende de outra; devem ser representadas com linhas tracejadas e setas apropriadas.                                 | [IBM](https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-relationships-in-class)                                                                                                                                                                                                                                                                                               |
| DC04 | As generalizações (heranças) estão representadas com linhas contínuas e setas com triângulo vazio apontando para a superclasse? | Generalizações indicam relações de herança entre classes; devem ser claramente representadas para mostrar hierarquias de classes.                                   | Apostila UML; [Visual Paradigm](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-aggregation-vs-composition/)                                                                                                                                                                                                                                               |
| DC05 | As agregações estão representadas com linhas contínuas e losangos vazios na extremidade da classe agregadora?    | Agregações representam relações "todo/parte" onde a parte pode existir independentemente do todo; devem ser indicadas com losangos vazios.                         | [TutorialsPoint](https://www.tutorialspoint.com/uml/uml_association_vs_aggregation_vs_composition.htm)                                                                                                                                                                                                                                                                             |
| DC06 | As composições estão representadas com linhas contínuas e losangos preenchidos na extremidade da classe composta? | Composições representam relações "todo/parte" onde a parte não pode existir sem o todo; devem ser indicadas com losangos preenchidos.                              | [Visual Paradigm](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-aggregation-vs-composition/)                                                                                                                                                                                                                                                            |
| DC07 | As associações reflexivas (onde uma classe se associa a ela mesma) estão representadas corretamente?             | Associações reflexivas ocorrem quando uma classe tem uma relação com ela mesma; devem ser representadas com uma linha que retorna à própria classe.                 | [Guru99](https://www.guru99.com/uml-relationships-with-example.html)                                                                                                                                                                                                                                                                                                              |
| DC08 | As realizações (implementações de interfaces) estão representadas com linhas tracejadas e setas com triângulo vazio apontando para a interface? | Realizações indicam que uma classe implementa uma interface; devem ser representadas com linhas tracejadas e setas apropriadas.                                     | [IBM](https://www.ibm.com/docs/SS8PJ7_9.5.0/com.ibm.xtools.modeler.doc/topics/rreltyp.html)                                                                                                                                                                                                                                                                                       |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
 



## Observações

## Conclusão

A verificação do Diagrama de Classes desenvolvido para o projeto Galáxia Conectada demonstrou-se uma etapa fundamental para assegurar a qualidade e a coerência do modelo proposto. Por meio desse processo, foi possível identificar e corrigir inconsistências, alinhar a estrutura do sistema aos requisitos estabelecidos e garantir que a representação estivesse em conformidade com as normas da UML. 

## Bibliografia

1. APOSTILA UML. Seção sobre representação de classes. Disponíbilizada pela professora. Acesso em: 25 abr. 2025.
2. BÓSON TREINAMENTOS. Introdução à UML – Unified Modeling Language. Disponível em: https://www.youtube.com/watch?v=C3xYBT3o_5k. Acesso em: 25 abr. 2025.
3. BÓSON TREINAMENTOS. Curso de UML: O que é um diagrama de Classes. Disponível em: https://www.youtube.com/watch?v=JQSsqMCVi1k. Acesso em: 25 abr. 2025.
4. CREATELY. Class Diagram Relationships. Disponível em: https://creately.com/guides/class-diagram-relationships/. Acesso em: 25 abr. 2025.
5. EZ KNOWLEDGE. Comprehensive Guide to UML Class Diagrams. Disponível em: https://www.ez-knowledge.com/comprehensive-guide-to-uml-class-diagrams/. Acesso em: 25 abr. 2025.
6. GEEKSFORGEEKS. Unified Modeling Language (UML) Class Diagrams. Disponível em: https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/. Acesso em: 25 abr. 2025.
7. GURU99. UML Relationships with Example. Disponível em: https://www.guru99.com/uml-relationships-with-example.html. Acesso em: 25 abr. 2025.
8. IBM. Diagrams Relationships in Class. Disponível em: https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-relationships-in-class. Acesso em: 25 abr. 2025.
9. TUTORIALSPOINT. UML Association vs Aggregation vs Composition. Disponível em: https://www.tutorialspoint.com/uml/uml_association_vs_aggregation_vs_composition.htm. Acesso em: 25 abr. 2025.
10. UML DIAGRAMS. Class Reference. Disponível em: https://www.uml-diagrams.org/class-reference.html. Acesso em: 25 abr. 2025.
11. UML DIAGRAMS. Class Diagrams Overview. Disponível em: https://www.uml-diagrams.org/class-diagrams-overview.html. Acesso em: 25 abr. 2025.
12. UNIVERSITY OF CAPE TOWN. Software Engineering Notes. Disponível em: https://www.cs.uct.ac.za/mit_notes/software/htmls/ch05s09.html. Acesso em: 25 abr. 2025.
13. VISUAL PARADIGM. UML Aggregation vs Composition. Disponível em: https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-aggregation-vs-composition/. Acesso em: 25 abr. 2025.
14. WEBEL IT AUSTRALIA. UML Class Diagrams. Disponível em: https://www.webel.com.au/node/669. Acesso em: 25 abr. 2025.


## Histórico de versão

| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 25/04/2025 |
| 1.1 | Adição da tabela de verificação das classes| Larissa Stéfane | 25/04/2025 |
| 1.2 | Adição da tabela de verificação do diagrama das classes | Larissa Stéfane | 25/04/2025 |
