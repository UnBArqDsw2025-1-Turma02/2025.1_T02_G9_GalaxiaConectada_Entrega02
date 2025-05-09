# Diagrama de Implantação

## Sumário

- [Introdução](#introdução)  
- [Objetivos](#objetivos)  
- [Metodologia](#metodologia)  
- [Tabela de Análise](#Tabela-de-Análise)  
- [Diagrama de Implantação](#Diagrama-de-Implantação)  
- [Conclusão](#conclusão)  
- [Bibliografia](#bibliografia)  
- [Histórico de versão](#histórico-de-versão)  

## Introdução

O diagrama de implantação, segundo o artigo [O que é um diagrama de implementação?](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml) [2](#ref2), é um tipo de diagrama estrutural da UML que representa a implementação física de artefatos de software sobre os componentes de hardware. Neste diagrama, utilizam-se elementos gráficos como nódulos (caixas tridimensionais) para representar dispositivos ou ambientes de execução de software, e os artefatos são os produtos gerados pelo desenvolvimento, como arquivos executáveis, bibliotecas ou scripts. 

Com base nisso, o artigo [O Guia Fácil de Diagramas de Implantação UML](https://creately.com/blog/pt/diagrama/tutorial-do-diagrama-de-implantacao/#:~:text=Um%20diagrama%20de%20implanta%C3%A7%C3%A3o%20%C3%A9,software%20f%C3%ADsico%20de%20um%20sistema.) [1](#ref1) fala que esse tipo de diagrama é essencial para entender a arquitetura de execução do sistema ao evidenciar tanto o hardware necessário quanto o middleware que interliga os elementos da solução. Assim, no contexto do projeto Galáxia Conectada, o diagrama de implantação é importante pois permite visualizar de forma clara como a plataforma será distribuída fisicamente — por exemplo, o servidor onde será hospedado os serviços.

## Objetivos

Com isso, ao elaborar o diagrama de implantação, busca-se os seguintes objetivos:

- Representar a arquitetura física de execução do sistema Galáxia Conectada.

- Evidenciar os ambientes de hardware e software onde os componentes serão implantados.

- Demonstrar a distribuição dos artefatos e os canais de comunicação entre os nódulos.

## Metodologia:

A elaboração do diagrama de implantação será conduzida com o apoio da ferramenta Draw.io ao utilizar como base os materiais previamente desenvolvidos ao longo do projeto. Com isso, a construção seguirá uma abordagem sistemática, a partir da análise dos requisitos, diagramas e estrutura do sistema. Assim, as etapas da metodologia:

1. Inicialmente será realizada uma análise do material base a partir de:

  - [Requisitos elicitados e documentados na primeira etapa](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/IniciativaExtra/RequisitosElicitados);
  - [Diagrama de Classes](https://unbarqdsw2025-1-turma02.github.io/2025.1_T02_G9_GalaxiaConectada_Entrega02/#/Modelagem/ModelagemEstatica/DiagramaClasses);
  - [Diagrama de Componentes](https://unbarqdsw2025-1-turma02.github.io/2025.1_T02_G9_GalaxiaConectada_Entrega02/#/Modelagem/ModelagemEstatica/DiagramaComponentes);

2. Com base nessa análise, será criada uma tabela de apoio organizando os tipos de nós (hardware, software, containers etc.) necessários para a modelagem.
3. Ao utilizar a ferramenta **Draw.io**, será elaborada a versão inicial do diagrama de implantação, com identificação dos nós, artefatos e relações.
4. Após a construção, o diagrama passará por uma fase de [verificação](Modelagem/IniciativasExtras/Verificacao/VerificacaoDiagramaImplantacao.md), com o objetivo de garantir sua coerência.

## Tabela de Análise

A tabela 1 abaixo foi elaborada para auxiliar na análise dos tipos de nós necessários para a construção do Diagrama de Implantação do projeto Galáxia Conectada. 


<details>
  <summary><strong>Tabela 1: Base para Diagrama de Implantação</strong></summary>

**Tabela 1**: Base para Diagrama de Implantação

| # | Tipo de Nó  | Nome do Nó  | <<Estereótipo>> / Ícone Usado   | Descrição / Responsabilidade   | Artefatos / Componentes Implantados  | Ambiente de Execução / Software Chave  | Comunicação Principal (Para/De, Protocolo)  | Requisitos Atendidos  |
| - | :---------| :---------------------| :------------------- | :------------- | :--------- | :----- | :-------------------- | :---------- |
| 01 | Dispositivo Usuário | `Navegador Web`   | `<<device>>`    | Acessa a aplicação via browser. Executa o módulo de interface.   | `Module` (Representando UI/Frontend)    | Navegador Web  | [Para] Servidor Web (HTTPS)   | RNF01, RNF09 (Acesso via Browser)  |
| 02 | Servidor           | `Servidor Web`   | `<<server>>`  | Ponto de entrada para requisições dos clientes.   | `Module` (Representando Configuração/Lógica do Servidor Web)                                                                                                                                                         | Nginx / Apache (ou similar)                        | [De] Navegador Web (HTTPS)<br> [Para] Firewall (TCP/IP)   | -                                                                     |
| 03 | Rede / Segurança    | `Firewall` | `<<firewall>>` | Controla o tráfego de rede entre a camada web e os servidores internos.  | -      | Software de Firewall     | [De] Servidor Web (TCP/IP) <br> Para SGBD (TCP/IP)<br> [Para] Servidor de Aplicação 1 (TCP/IP)<br> [Para] Servidor de Aplicação 2 (TCP/IP)   | RNF04 ( Segurança)                                         |
| 04 | Servidor            | `Sistema Gerenciador de Banco de Dados` | `<<database>>`          | Armazena e gerencia os dados da aplicação.                                                                         | `Usuario` (Schema/Dados)<br>`Serviços` (Schema/Dados)<br>`Jogos` (Schema/Dados)<br>`Artigos` (Schema/Dados)                          | SGBD (Ex: PostgreSQL, MySQL)                       | [De] Firewall (TCP/IP)<br> [De] Servidor de Aplicação 1 (TCP/IP) <br> [De] Servidor de Aplicação 2 (TCP/IP) | RF04, RNF04 (Persistência e Segurança de Dados)                     |
| 05 | Servidor            | `Servidor de Aplicação 1 - Serviços`  | `<<server>>`  | Executa a aplicação principal de serviços da Galáxia Conectada.                                                    | `<<interface>> astronomia.war`<br>`web-tools-lib.jar`<br>`<<deployment spec>> web.xml`<br>`Componente Serviço Online`<br>`Componente Serviço de Usuário` - Referentes ao diagrama de Componentes.                                | Java App Server (Tomcat, etc.) + JRE / Docker     | [De] Firewall (TCP/IP) <br> [Para] SGBD (TCP/IP)                 |  RNF02, RNF05  |
| 06 | Servidor            | `Servidor de Aplicação 2 - Jogos`     | `<<server>>`          | execução da aplicação de jogos. | `<<interface>> astronomia.war`<br>`web-tools-lib.jar`<br>`<<deployment spec>> web.xml`<br>`Componente Conteudo Interativo` | Java App Server (Tomcat, etc.) + JRE / Docker     | [De] Firewall (TCP/IP)<br> [Para] SGBD (TCP/IP)                                                                                                                                                                                                                                              | RF08, RF21, RF22, RNF02, RNF05    |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>

## Diagrama de Implantação

Para melhor compreensão do diagrama, a figura 1 mostra a legenda;

<div align="center">
    Figura 1: Legenda do Diagrama de Implantação
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/75556a84c6b754819462bcc143af4787c4a62dde/docs/Modelagem/Imagens/LegendaDiagramaImplantacao.drawio.png" width="500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

<div align="center">
    Figura 2: o Diagrama de Implantação
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/75556a84c6b754819462bcc143af4787c4a62dde/docs/Modelagem/Imagens/DiagramaImplantacao.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

**Observação:** Caso deseje visualizar ou baixar em PDF, clique aqui [PDF](https://github.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/blob/main/docs/Modelagem/Imagens/DiagramaImplantacao.pdf)


## Conclusão

A construção do Diagrama de Implantação para o projeto Galáxia Conectada teve como base a Tabela 1, a qual sistematizou os principais nós da infraestrutura de execução da aplicação e incluiu dispositivos de usuário, servidores, rede e banco de dados. Portanto, esse mapeamento permitiu representar, de forma estruturada, como os componentes do sistema são distribuídos fisicamente em seus respectivos ambientes de execução. 

## Bibliografia

<a name="ref1"></a>
[1] CREATELY. O Guia Fácil de Diagramas de Implantação UML. Creately Blog, 2024. Disponível em: https://creately.com/blog/pt/diagrama/tutorial-do-diagrama-de-implantacao/. Acesso em: 6 mai. 2025.

<a name="ref2"></a>
[2] EDRAWSOFT. Exemplos de Diagrama de Implantação UML. Edraw, 2024. Disponível em: https://www.edrawsoft.com/pt/deployment-chart-example.html. Acesso em: 28 abr. 2025.

<a name="ref3"></a>
[3] IBM CORPORATION. Diagramas de implantação. IBM Documentation, 2024. Disponível em: https://www.ibm.com/docs/pt-br/rsas/7.5.0?topic=topologies-deployment-diagrams. Acesso em: 28 abr. 2025.

<a name="ref4"></a>
[4] LUCID SOFTWARE INC. O que é diagrama de implementação UML. Lucidchart, 2024. Disponível em: https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-implementacao-uml. Acesso em: 28 abr. 2025.

<a name="ref5"></a>
[5] MAURO DE BONI. Tutorial Draw.io: Como Fazer Diagrama de Implantação da UML. YouTube, 2023. Disponível em: https://www.youtube.com/watch?v=eFFq3SLMQJ4. Acesso em: 30 abr. 2025.

<a name="ref6"></a>
[6] PROFESSOR PAIVA. Curso de UML - Diagrama de Implantação. YouTube, 2022. Disponível em: https://www.youtube.com/watch?v=DgERD0HgggQ. Acesso em: 30 abr. 2025.

<a name="ref7"></a>
[7] UML-DIAGRAMS. Deployment Diagrams Overview. UML Diagrams.org, 2024. Disponível em: https://www.uml-diagrams.org/deployment-diagrams-overview.html. Acesso em: 28 abr. 2025.

<a name="ref8"></a>
[8] VISUAL PARADIGM. What is Deployment Diagram?. Visual Paradigm Guide, 2024. Disponível em: https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-deployment-diagram/. Acesso em: 28 abr. 2025.


## Histórico de versão

| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 28/04/2025 |
| 1.1 | Adição da Metodologia  | Larissa Stéfane | 28/04/2025 |
| 1.2 | Criação da tabela Base | Larissa Stéfane | 28/04/2025 |
| 1.3 | Reestruturação da Tabela base | Larissa Stéfane | 29/04/2025 |
| 1.4 | Adição do Diagrama de Implantação | Larissa Stéfane | 30/04/2025 |
| 1.5 | Ajustes no artefato| Larissa Stéfane | 06/05/2025 |
