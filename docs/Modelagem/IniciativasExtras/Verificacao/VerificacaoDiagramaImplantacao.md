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

O Diagrama de Implantação, segundo a especificação UML [1], é um diagrama estrutural que modela a arquitetura física de um sistema. Ele mostra como os artefatos de software (executáveis, bibliotecas, arquivos de configuração, etc.) são distribuídos e implantados nos nós de hardware (servidores, dispositivos) e ambientes de execução (sistemas operacionais, containers). No contexto do projeto Galáxia Conectada, este diagrama é crucial para visualizar a topologia de implantação da plataforma, incluindo servidores web, bancos de dados e possíveis integrações com serviços externos.

A verificação deste diagrama assegura que a representação da infraestrutura física e da distribuição dos componentes de software esteja correta, completa e alinhada com os requisitos não funcionais do sistema, como desempenho, escalabilidade e segurança. Identificar problemas nesta fase ajuda a evitar custos e dificuldades na etapa de implantação real do sistema.

## Objetivos

Este artefato tem como objetivo realizar a verificação do Diagrama de Implantação criado para o projeto Galáxia Conectada. A finalidade é garantir que ele represente com precisão a arquitetura física planejada para o sistema, que todos os nós, artefatos e conexões relevantes estejam modelados corretamente conforme os padrões UML e que o diagrama seja consistente com os demais artefatos de arquitetura e os requisitos do projeto.

## Metodologia

Similarmente à verificação de outros diagramas UML no projeto, a metodologia para o Diagrama de Implantação envolveu, primeiramente, o estudo dos conceitos e da notação UML específica para este diagrama. Com base na arquitetura de software definida e nos requisitos de infraestrutura do Galáxia Conectada, foi elaborado um esboço do diagrama, identificando os nós de hardware e software e os artefatos a serem implantados.

Posteriormente, aplicou-se um processo de verificação sistemática utilizando tabelas de checklist. Cada item das tabelas foi cuidadosamente analisado em relação ao diagrama proposto. As inconsistências ou omissões identificadas foram corrigidas para garantir a conformidade com as boas práticas de modelagem de implantação e os objetivos do projeto.

## Tabela de Verificação para os Nós (Dispositivos e Ambientes de Execução)

**Tabela 1:** Perguntas para a verificação dos Nós no Diagrama de Implantação.

| ID   | Pergunta de Verificação                                                                 | Explicação                                                                                                | Rastreabilidade |
|------|-----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|-----------------|
| N01  | Os nós (nodes) estão representados corretamente como cubos tridimensionais?              | A notação padrão UML para nós (dispositivos ou ambientes de execução) é um cubo.                           | [UML Distilled] |
| N02  | Cada nó possui um nome claro e representativo da sua função (ex: Servidor Web, BD)?     | A nomenclatura deve facilitar a compreensão da arquitetura física.                                        | [UML Distilled] |
| N03  | Estereótipos (`<<device>>`, `<<executionEnvironment>>`) são usados para clarificar o tipo de nó? | Estereótipos ajudam a distinguir entre nós de hardware e ambientes de software.                           | [UML Spec]      |
| N04  | As especificações relevantes do nó (ex: SO, hardware) estão indicadas usando tags?     | Valores Marcados (Tagged Values) podem detalhar características importantes dos nós.                      | [UML Spec]      |
| N05  | Nós aninhados (nested nodes) são usados corretamente para representar ambientes contidos? | Útil para mostrar, por exemplo, um servidor de aplicação rodando dentro de um servidor físico.             | [UML Distilled] |
| N06  | Todos os componentes físicos relevantes da infraestrutura estão representados por nós?   | O diagrama deve incluir todos os servidores, dispositivos e ambientes de execução chave.                  | [Best Practices]|
| N07  | A relação entre os nós (ex: um dispositivo contido em outro) está clara?                | Se houver hierarquia ou contenção de nós, ela deve ser visualmente representada.                         | [UML Spec]      |
| N08  | Os nomes dos nós seguem um padrão consistente (ex: PascalCase)?                         | Padronização de nomes melhora a legibilidade e profissionalismo do diagrama.                             | [Best Practices]|

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Tabela de Verificação para Artefatos e Caminhos de Comunicação

**Tabela 2:** Perguntas para a verificação dos Artefatos e Caminhos de Comunicação.

| ID   | Pergunta de Verificação                                                                                                   | Explicação                                                                                                                             | Rastreabilidade |
|------|---------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| A01  | Os artefatos (artifacts) estão representados corretamente com o ícone de documento (retângulo com canto dobrado)?          | Esta é a notação padrão UML para artefatos como executáveis, bibliotecas, schemas de BD, etc.                                         | [UML Distilled] |
| A02  | Cada artefato possui um nome claro e representativo (ex: `webapp.war`, `user_db_schema.sql`)?                              | A nomenclatura deve identificar o componente de software específico.                                                                    | [UML Distilled] |
| A03  | Estereótipos (`<<executable>>`, `<<library>>`, `<<file>>`) são usados para clarificar o tipo de artefato?                   | Estereótipos ajudam a entender a natureza do componente de software.                                                                     | [UML Spec]      |
| A04  | A relação de implantação (deploy) entre um artefato e um nó está representada por uma linha tracejada com seta aberta?      | A seta aponta do artefato para o nó onde ele é implantado. Opcionalmente, pode usar a palavra-chave `<<deploy>>`.                       | [UML Spec]      |
| A05  | Todos os artefatos de software significativos do sistema estão representados e associados a um nó?                          | O diagrama deve mostrar onde cada componente chave do software reside na infraestrutura.                                               | [Best Practices]|
| A06  | As dependências entre artefatos (manifest) estão representadas corretamente (ex: `<<manifest>>`)?                           | Útil para mostrar que um artefato (ex: um JAR) contém outros (ex: arquivos .class).                                                    | [UML Spec]      |
| C01  | Os caminhos de comunicação (communication paths) entre nós estão representados por linhas sólidas?                          | Linhas sólidas conectam nós que se comunicam diretamente.                                                                              | [UML Distilled] |
| C02  | Os protocolos de comunicação (ex: HTTP, JDBC, RMI) estão indicados nos caminhos de comunicação, se relevante?              | Adicionar o protocolo como um estereótipo (`<<HTTP>>`) ou tag no caminho de comunicação aumenta a clareza.                             | [UML Spec]      |
| C03  | A direção da comunicação é indicada por setas, se for relevante ou não óbvia?                                               | Embora opcionais, setas podem clarificar o fluxo de comunicação entre os nós.                                                          | [Best Practices]|
| C04  | Todos os links de comunicação essenciais entre os componentes da infraestrutura estão modelados?                             | O diagrama deve refletir como os diferentes nós do sistema interagem.                                                                  | [Best Practices]|

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Observações



## Conclusão

A verificação do Diagrama de Implantação do projeto Galáxia Conectada foi essencial para validar a arquitetura física proposta para o sistema. Através da aplicação das tabelas de verificação, foi possível assegurar que a disposição dos artefatos de software nos nós de hardware e ambientes de execução está corretamente modelada, em conformidade com os padrões UML e alinhada aos requisitos do sistema. Este processo contribui para mitigar riscos relacionados à implantação e garante uma visão clara da infraestrutura necessária para a operação da plataforma.

## Bibliografia


1.  FOWLER, Martin. **UML Distilled**: A Brief Guide to the Standard Object Modeling Language. 3rd ed. Addison-Wesley Professional, 2003. (Referido como [UML Distilled])
2.  Object Management Group (OMG). **Unified Modeling Language (UML) Specification**. Version 2.5.1 (ou a versão utilizada). Disponível em: [https://www.omg.org/spec/UML/](https://www.omg.org/spec/UML/) (Referido como [UML Spec])
3.  *(Outras fontes, como artigos, guias de boas práticas ou ferramentas UML utilizadas, podem ser adicionadas aqui. Referido como [Best Practices] ou similar nas tabelas).*
4.  APOSTILA UML. Seção sobre Diagrama de Implantação. Disponibilizada pela professora. Acesso em: 05 mai. 2025.

## Histórico de versão

| Versão | Alteração                                     | Responsável     | Data       |
| :----- | :-------------------------------------------- | :-------------- | :--------- |
| 1.0    | Elaboração inicial do documento de verificação | Larissa Stéfane | 05/05/2025 |
| 1.1    | Adição das tabelas de verificação             | Larissa Stéfane | 05/05/2025 |

