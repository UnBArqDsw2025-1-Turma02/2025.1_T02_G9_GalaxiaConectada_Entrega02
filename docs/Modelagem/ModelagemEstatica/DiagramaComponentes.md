# Diagrama de Componentes

## Sumário

- [Introdução](#introdução)  
- [Objetivos](#objetivos)  
- [Metodologia](#metodologia)  
- [Investigação dos Componentes Necessários](#investigação-dos-componentes-necessários)  
- [Diagrama de Componentes](#diagrama-de-componentes)  
- [Conclusão](#conclusão)  
- [Bibliografia](#bibliografia)  
- [Histórico de versão](#histórico-de-versão)  

## Introdução

Segundo a Apostila UML – Linguagem de Modelagem Unificada [1](#ref1) e o guia da plataforma UML Diagrams [2](#ref2), um **componente** é uma unidade física de software (código-fonte, biblioteca, executável) que encapsula um conjunto de funcionalidades. Com base nisso, o **Diagrama de Componentes** representa visualmente esses módulos e suas dependências, e assim mostra quais artefatos (ex.: arquivos .jar, .dll, .py) são necessários para executar cada parte do sistema. No projeto Galáxia Conectada, esse diagrama expõe módulos como Interface Web, API de Cursos, Serviço de Notificações, Banco de Dados e Integração com APIs externas (ex.: NASA).

## Objetivos

Tem em base o conceito de componentes e diagrama de componentes, busca-se os seguintes objetivos: 

- Apresentar de forma clara os componentes físicos do sistema Galáxia Conectada.  
- Evidenciar interfaces providas e requeridas por cada módulo.  
- Documentar dependências e artefatos para suportar implementação e deploy.  

## Metodologia

A metodologia adotada para a elaboração do Diagrama de Componentes do projeto Galáxia Conectada compreenderá quatro etapas principais: inicialmente será realizado o levantamento arquitetural, no qual serão identificados os módulos centrais do sistema a partir dos requisitos funcionais, do rich-picture e da análise 5W2H; em seguida, proceder-se-á à modelagem inicial no Draw.io, esboçando cada componente e as interfaces que proverá ou requererá; posteriormente, aplicar-se-á a verificação por meio de um checklist de boas práticas UML, avaliando notação, nomenclatura, coesão e clareza das dependências; por fim, conduzir-se-ão ajustes visuais e de nomenclatura para otimizar a legibilidade, a rastreabilidade e a conformidade do diagrama com os padrões estabelecidos.

## Investigação dos Componentes Necessários


A tabela 1 mostra os possíveis componentes necessários para o desenvolvimento da Galáxia Conectada.

**Tabela 1:** Componentes

| #   | Tipo de Elemento                            | Nome (Componente/Pacote/Subsistema) | Descrição / Estrutura Interna Potencial                                                                                                                               | Interfaces Providas (Exemplos)                 | Dependências / Interfaces Requeridas (Exemplos)          | Artefatos Potenciais (`<<manifest>>`)                                          |
| :-- | :------------------------------------------ | :---------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------ | :------------------------------------------------------- | :---------------------------------------------------------------------------- |
| 1   | **Pacote** | `<<package>> Galáxia Conectada Site`  | Pacote raiz que contém todos os elementos da plataforma web.                                                                                                          | -                                                 | -                                                        | -                                                                             |
| 2   | Componente                                  | `WebUI`                             | Interface gráfica com o usuário (Frontend). Responsável pela apresentação e interação. (Poderia conter partes internas como: `ViewComponents`, `AuthClient`, `APIClient`) | - (Interage com usuário)                        | `IAPIGeral` (do APIGateway)                              | `webapp.war`, `frontend-build/` (JS/CSS/HTML)                                 |
| 3   | Componente                                  | `APIGateway`                        | Ponto único de entrada (Facade/Proxy) para o backend. Roteia requisições, pode fazer agregação leve.                                                                    | `IAPIGeral`                                       | Interfaces dos Módulos/Subsistemas de Backend            | `gateway-service.jar`, `nginx.conf`, `kong-plugin.lua`                          |
| 4   | **Pacote** | `<<package>> Backend Services`        | Agrupa os componentes e subsistemas do lado do servidor.                                                                                                              | -                                                 | -                                                        | -                                                                             |
| 5   | Componente                                  | `GestaoUsuarios`                    | Gerencia usuários, perfis, autenticação, autorização. (Estrutura interna: `AuthService`, `UserProfileRepo`, `RoleManager`)                                              | `IAutenticacao`, `IPerfilUsuario`                 | `IPersistencia` (do BancoDeDados)                        | `user-service.jar`                                                            |
| 6   | **Subsistema** | `<<subsystem>> Conteudo Interativo` | **Agrega funcionalidades de conteúdo.** (Estrutura Interna: `ModuloEducacional`, `ModuloDivulgacao`, `ModuloJogos` como partes internas).                                | `IGestaoCursos`, `IAcessoConteudo`, `IGestaoArtigos`, `IAcessoJogos` | `IPersistencia`, `IGamificacao`, `IIntegracaoExterna`, `INotificacoes`, `IPerfilUsuario` | `content-subsystem.ear` (agregado)                                            |
| 7   | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloEducacional`                 | Gerencia trilhas, módulos, vídeos, quizzes, progresso, certificados. Suporta a página `Trilhas Educativas`.                                                          | `IGestaoCursos`, `IAcessoConteudo`                | `IPersistencia`, `IGamificacao`, `IPerfilUsuario`        | `educational-module.jar`                                                      |
| 8   | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloDivulgacao`                  | Gerencia artigos, notícias, categorias, glossário, comentários. Suporta destaques na `Tela Inicial` ou seção própria.                                                  | `IGestaoArtigos`                                  | `IPersistencia`, `IIntegracaoExterna`, `IPerfilUsuario`, `INotificacoes` | `news-module.jar`                                                             |
| 9   | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloJogos`                       | Gerencia jogos, desafios, pontuações, rankings. Suporta a `Seção de Jogos Educativos`.                                                                              | `IAcessoJogos`                                    | `IPersistencia`, `IGamificacao`, `IPerfilUsuario`        | `games-module.jar`                                                            |
| 10  | **Subsistema** | `<<subsystem>> Comunidade`          | **Agrega funcionalidades de interação social.** (Estrutura Interna: `ModuloForum`, `ModuloGamificacao` como partes internas).                                           | `IGestaoForum`, `IGamificacao`                    | `IPersistencia`, `IPerfilUsuario`, `INotificacoes`       | `community-subsystem.ear` (agregado)                                          |
| 11  | Parte Interna (`Comunidade`) - Componente       | `ModuloForum`                       | Gerencia fóruns, tópicos, posts, moderação, reputação (via Gamificação). Suporta a página `Fórum de Discussões`.                                                     | `IGestaoForum`                                    | `IPersistencia`, `IGamificacao`, `IPerfilUsuario`, `INotificacoes` | `forum-module.jar`                                                            |
| 12  | Parte Interna (`Comunidade`) - Componente       | `ModuloGamificacao`                 | Centraliza XP, níveis, conquistas, reputação. Usado por `Perfil`, `Trilhas`, `Fórum`, `Jogos`.                                                                      | `IGamificacao`                                    | `IPersistencia`, `IPerfilUsuario`                        | `gamification-module.jar`                                                     |
| 13  | **Subsistema** | `<<subsystem>> Integrações`       | **Agrega funcionalidades que dependem de dados/serviços externos.** (Estrutura Interna: `ModuloEventos`, `ModuloPromocoes`, `ServicoBotsExternos` como partes).       | `IAgendaEventos`, `IMonitorPromocoes`, `IIntegracaoExterna` | `IPersistencia`, `INotificacoes`, (APIs/Sites Externos) | `integrations-subsystem.ear` (agregado)                                       |
| 14  | Parte Interna (`Integrações`) - Componente     | `ModuloEventos`                     | Gerencia calendário de eventos astronômicos (internos/externos). Suporta a página `Calendário de Eventos`.                                                            | `IAgendaEventos`                                  | `IPersistencia`, `IIntegracaoExterna`, `INotificacoes`   | `events-module.jar`                                                           |
| 15  | Parte Interna (`Integrações`) - Componente     | `ModuloPromocoes`                   | Exibe promoções de produtos (via bots). Suporta a página `Promoções Astronômicas`.                                                                                 | `IMonitorPromocoes`                               | `IPersistencia`, `IIntegracaoExterna`, `INotificacoes`   | `promotions-module.jar`                                                       |
| 16  | Parte Interna (`Integrações`) - Componente     | `ServicoBotsExternos`               | Agrupa bots que coletam dados externos (notícias, eventos, promoções).                                                                                             | `IIntegracaoExterna`                              | `IPersistencia`, (APIs/Sites Externos)                   | `bots-service.jar`, `web-scrapers.py`, `api-clients/`                         |
| 17  | Componente                                  | `ServicoNotificacoes`               | Envia notificações (email, push, etc.). (Estrutura interna: `EmailGateway`, `PushGateway`, `NotificationQueue`)                                                         | `INotificacoes`                                   | `IPerfilUsuario`, (Serviços Externos de Email/Push)      | `notification-service.jar`                                                    |
| 18  | **Artefato** | `<<artifact>> schema.sql`           | Arquivo físico contendo o esquema (estrutura) do banco de dados.                                                                                                  | -                                                 | -                                                        | `schema.sql` (o próprio arquivo)                                              |
| 19  | Componente                                  | `BancoDeDados`                      | Representa o sistema de gerenciamento de banco de dados (SGBD) e os dados armazenados.                                                                              | `IPersistencia` (implícita via driver/ORM)        | -                                                        | Arquivos de dados do SGBD, (`schema.sql` manifesta a estrutura)               |
| 20  | **Interface** | `IAPIGeral`                         | Contrato da API principal exposta pelo APIGateway para o WebUI.                                                                                                       | -                                                 | -                                                        | - (É uma definição/contrato)                                                  |
| 21  | **Interface** | `IAutenticacao`                     | Contrato para serviços de autenticação.                                                                                                                               | -                                                 | -                                                        | -                                                                             |
| 22  | **Interface** | `IPerfilUsuario`                    | Contrato para operações relacionadas ao perfil do usuário.                                                                                                          | -                                                 | -                                                        | -                                                                             |
| 23  | **Interface** | `IGestaoCursos`                     | Contrato para gerenciar cursos e trilhas.                                                                                                                             | -                                                 | -                                                        | -                                                                             |
| 24  | **Interface** | `IAcessoConteudo`                   | Contrato para acessar conteúdos educacionais.                                                                                                                       | -                                                 | -                                                        | -                                                                             |
| 25  | **Interface** | `IGestaoArtigos`                    | Contrato para gerenciar artigos e notícias.                                                                                                                         | -                                                 | -                                                        | -                                                                             |
| 26  | **Interface** | `IAcessoJogos`                      | Contrato para acessar e interagir com jogos.                                                                                                                        | -                                                 | -                                                        | -                                                                             |
| 27  | **Interface** | `IGestaoForum`                      | Contrato para gerenciar fóruns, tópicos e posts.                                                                                                                    | -                                                 | -                                                        | -                                                                             |
| 28  | **Interface** | `IGamificacao`                      | Contrato para interagir com o sistema de gamificação (XP, níveis, etc.).                                                                                             | -                                                 | -                                                        | -                                                                             |
| 29  | **Interface** | `IAgendaEventos`                    | Contrato para acessar o calendário de eventos.                                                                                                                        | -                                                 | -                                                        | -                                                                             |
| 30  | **Interface** | `IMonitorPromocoes`                 | Contrato para acessar informações de promoções.                                                                                                                     | -                                                 | -                                                        | -                                                                             |
| 31  | **Interface** | `INotificacoes`                     | Contrato para solicitar o envio de notificações.                                                                                                                    | -                                                 | -                                                        | -                                                                             |
| 32  | **Interface** | `IIntegracaoExterna`                | Contrato para acessar dados coletados de fontes externas pelos bots.                                                                                                | -                                                 | -                                                        | -                                                                             |
| 33  | **Interface** | `IPersistencia`                     | Contrato (muitas vezes implícito) para interagir com o mecanismo de persistência (Banco de Dados).                                                                   | -                                                 | -                                                        | -                                                                             |


<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.


## As Ligações entre os Componentes


As relações padrão mostrada na tabela são **Dependências**.

**Tabela 2** : Conexões entre Componentes 

Lembre-se que a relação principal aqui é a **Dependência** (geralmente desenhada como uma seta tracejada `------>` da origem para o destino no diagrama). A **Realização** de uma interface é mostrada visualmente no diagrama pelo símbolo de interface (pirulito `–o`) ligado ao componente que a implementa, muitas vezes através de uma Porta.

**Tabela: As Ligações entre os Componentes - Galáxia Conectada**

| Componente Origem                                  | Componente Destino                  | Interface Fornecida (Destino) | Interface Requerida / Porta (Origem) | Notas / Racional                                                                                                                                   |
| :------------------------------------------------- | :---------------------------------- | :---------------------------- | :----------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------- |
| `WebUI`                                            | `APIGateway`                        | `IAPIGeral`                   | Porta `apiPort` (Requer `IAPIGeral`) | Interface (`WebUI`) consome a API principal (`IAPIGeral`) exposta pelo `APIGateway` via porta.                                                       |
| `APIGateway`                                       | `GestaoUsuarios`                    | `IAutenticacao`, `IPerfilUsuario` | -                                    | Gateway direciona requisições de login, perfil, etc. para o componente de usuários.                                                               |
| `APIGateway`                                       | `<<subsystem>> Conteudo Interativo` | `IGestaoCursos`, `IAcessoConteudo`, `IGestaoArtigos`, `IAcessoJogos` | -                                    | Gateway direciona requisições de conteúdo (trilhas, artigos, jogos) para o subsistema responsável.                                                 |
| `APIGateway`                                       | `<<subsystem>> Comunidade`          | `IGestaoForum`, `IGamificacao` | -                                    | Gateway direciona requisições sociais (fórum, gamificação) para o subsistema responsável.                                                        |
| `APIGateway`                                       | `<<subsystem>> Integrações`       | `IAgendaEventos`, `IMonitorPromocoes`, `IIntegracaoExterna` | -                                    | Gateway direciona requisições de dados externos (eventos, promoções) para o subsistema responsável.                                                |
| `APIGateway`                                       | `ServicoNotificacoes`               | `INotificacoes`             | -                                    | Gateway pode disparar notificações com base em ações de outros componentes/subsistemas.                                                            |
| ---                                                | ---                                 | ---                           | ---                                  | ---                                                                                                                                                |
| **Dentro de `Conteudo Interativo`:** |                                     |                               |                                      | **_(Dependências das Partes Internas)_** |
| `ModuloEducacional`                                | `ModuloGamificacao`                 | `IGamificacao`              | Porta `gamificationPort`             | Módulo Educacional reporta progresso para o Módulo de Gamificação (que está no Subsistema Comunidade).                                             |
| `ModuloEducacional`                                | `GestaoUsuarios`                    | `IPerfilUsuario`            | -                                    | Precisa saber qual usuário está acessando/progredindo.                                                                                             |
| `ModuloEducacional`                                | `BancoDeDados`                      | `IPersistencia`             | -                                    | Persiste dados de cursos, progresso, etc.                                                                                                        |
| `ModuloDivulgacao`                                 | `ServicoBotsExternos`               | `IIntegracaoExterna`        | Porta `externalDataPort`             | Consome notícias/dados externos coletados pelos Bots (que estão no Subsistema Integrações).                                                          |
| `ModuloDivulgacao`                                 | `ServicoNotificacoes`               | `INotificacoes`             | Porta `notificationPort`             | Solicita envio de notificações (ex: novo artigo).                                                                                                |
| `ModuloDivulgacao`                                 | `GestaoUsuarios`                    | `IPerfilUsuario`            | -                                    | Precisa saber quem comentou/submeteu conteúdo.                                                                                                   |
| `ModuloDivulgacao`                                 | `BancoDeDados`                      | `IPersistencia`             | -                                    | Persiste artigos, notícias, comentários.                                                                                                         |
| `ModuloJogos`                                      | `ModuloGamificacao`                 | `IGamificacao`              | Porta `gamificationPort`             | Módulo de Jogos reporta pontuações para o Módulo de Gamificação (no Subsistema Comunidade).                                                        |
| `ModuloJogos`                                      | `GestaoUsuarios`                    | `IPerfilUsuario`            | -                                    | Precisa saber qual usuário está jogando.                                                                                                         |
| `ModuloJogos`                                      | `BancoDeDados`                      | `IPersistencia`             | -                                    | Persiste dados de jogos, rankings.                                                                                                               |
| ---                                                | ---                                 | ---                           | ---                                  | ---                                                                                                                                                |
| **Dentro de `Comunidade`:** |                                     |                               |                                      | **_(Dependências das Partes Internas)_** |
| `ModuloForum`                                      | `ModuloGamificacao`                 | `IGamificacao`              | Porta `gamificationPort`             | Reporta atividades do fórum (posts, votos) para o Módulo de Gamificação (no mesmo subsistema).                                                      |
| `ModuloForum`                                      | `ServicoNotificacoes`               | `INotificacoes`             | Porta `notificationPort`             | Solicita envio de notificações (ex: novo post).                                                                                                  |
| `ModuloForum`                                      | `GestaoUsuarios`                    | `IPerfilUsuario`            | -                                    | Precisa saber quem postou/comentou.                                                                                                              |
| `ModuloForum`                                      | `BancoDeDados`                      | `IPersistencia`             | -                                    | Persiste dados de fóruns, tópicos, posts.                                                                                                        |
| `ModuloGamificacao`                                | `GestaoUsuarios`                    | `IPerfilUsuario`            | -                                    | Precisa associar XP/níveis/conquistas a um usuário específico.                                                                                    |
| `ModuloGamificacao`                                | `BancoDeDados`                      | `IPersistencia`             | -                                    | Persiste dados de XP, níveis, conquistas.                                                                                                        |
| ---                                                | ---                                 | ---                           | ---                                  | ---                                                                                                                                                |
| **Dentro de `Integrações`:** |                                     |                               |                                      | **_(Dependências das Partes Internas)_** |
| `ModuloEventos`                                    | `ServicoBotsExternos`               | `IIntegracaoExterna`        | Porta `externalDataPort`             | Consome dados de eventos coletados pelos Bots (no mesmo subsistema).                                                                               |
| `ModuloEventos`                                    | `ServicoNotificacoes`               | `INotificacoes`             | Porta `notificationPort`             | Solicita envio de notificações (ex: lembrete de evento).                                                                                          |
| `ModuloEventos`                                    | `BancoDeDados`                      | `IPersistencia`             | -                                    | Persiste dados de eventos.                                                                                                                       |
| `ModuloPromocoes`                                  | `ServicoBotsExternos`               | `IIntegracaoExterna`        | Porta `externalDataPort`             | Consome dados de promoções coletados pelos Bots (no mesmo subsistema).                                                                             |
| `ModuloPromocoes`                                  | `ServicoNotificacoes`               | `INotificacoes`             | Porta `notificationPort`             | Solicita envio de notificações (ex: nova promoção).                                                                                               |
| `ModuloPromocoes`                                  | `BancoDeDados`                      | `IPersistencia`             | -                                    | Persiste dados de promoções.                                                                                                                     |
| `ServicoBotsExternos`                              | `BancoDeDados`                      | `IPersistencia`             | -                                    | Persiste configurações dos bots e logs.                                                                                                          |
| `ServicoBotsExternos`                              | `(APIs/Sites Externos)`             | -                           | -                                    | Acessa fontes externas para coletar dados (representado como dependência a elemento externo).                                                      |
| ---                                                | ---                                 | ---                           | ---                                  | ---                                                                                                                                                |
| **Outras Dependências:** |                                     |                               |                                      |                                                                                                                                                    |
| `ServicoNotificacoes`                              | `GestaoUsuarios`                    | `IPerfilUsuario`            | -                                    | Busca preferências e dados de contato do usuário para envio.                                                                                     |
| `ServicoNotificacoes`                              | `(Serviços Externos de Email/Push)` | -                           | -                                    | Usa APIs externas para realizar o envio efetivo (representado como dependência a elemento externo).                                                |
| `GestaoUsuarios`                                   | `BancoDeDados`                      | `IPersistencia`             | -                                    | Persiste dados de usuários, perfis, etc.                                                                                                         |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.


## Diagrama de Componentes


## Conclusão

O Diagrama de Componentes apresenta de forma estruturada os módulos físicos do sistema, suas interfaces e dependências. Essa visão facilita o planejamento de implantação, a definição de pipelines de build/deploy e a manutenção evolutiva da plataforma, ao evidenciar claramente quais artefatos e serviços cada componente exige ou oferece.

## Bibliografia

<a name="ref1"></a>  
[1]APOSTILA UML. *Linguagem de Modelagem Unificada*. Universidade XYZ, 2023. (Documento interno). Acesso em: 25 abr. 2025.  

<a name="ref2"></a>  
[2]UML DIAGRAMS. *Component Diagrams Overview*. Disponível em: https://www.uml-diagrams.org/component-diagrams.html. Acesso em: 25 abr. 2025. 

<a name="ref3"></a>  
[3] IBM CORPORATION. *Component diagrams*. IBM Documentation, 2023. Disponível em: https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component. Acesso em: 25 abr. 2025.  

<a name="ref4"></a>  
[4] LUCID SOFTWARE INC. *UML Component Diagram*. Lucidchart, 2024. Disponível em: https://www.lucidchart.com/pages/uml-component-diagram. Acesso em: 25 abr. 2025.

<a name="ref5"></a>  
[5] VISUAL PARADIGM INTERNATIONAL. *UML Component Diagram Guide*. Visual Paradigm, 2024. Disponível em: https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-component-diagram/. Acesso em: 25 abr. 2025.  

## Histórico de versão

| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 25/04/2024 |
| 1.1 | Adição da Metodologia  | Larissa Stéfane | 25/04/2024 |
| 1.2 | Criação da tabela de investigação dos componentes | Larissa Stéfane | 26/04/2024 |
| 1.3 | Atualização das tabela dos componentes | Larissa Stéfane | 27/04/2024 |
| 1.4 | Correção da tabela dos componentes | Larissa Stéfane | 27/04/2024 |
| 1.5 | Criação da tabela de ligações ente os componentes | Larissa Stéfane | 27/04/2024 |
| 1.6 | Atualização da tabela de componentes | Larissa Stéfane | 27/04/2024 |
| 1.7 | Atualização da tabela de ligações | Larissa Stéfane | 27/04/2024 |
