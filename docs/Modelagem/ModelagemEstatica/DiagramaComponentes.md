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

**Tabela Resumo dos Elementos do Diagrama - Galáxia Conectada (com Novos Componentes)**

| #   | Tipo de Elemento                            | Nome (Componente/Pacote/Subsistema) | Descrição                                                                                                                                             | Interfaces Providas (Exemplos)                 | Interfaces Requeridas (Exemplos / Portas)                 | Dependências (Este elemento depende de...)                |               
| :-- | :------------------------------------------ | :---------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------ | :---------------------------------------------------------- | :---------------------------------------------------------- |
| 1   | Pacote                                      | `<<package>> Galáxia Conectada Site`  | Pacote raiz que contém todos os elementos da plataforma web.                                                                                        | -                                                 | -                                                           | -                                                           |                                      |
| 2   | Pacote                                      | `<<package>> Backend Services`        | Agrupa os componentes e subsistemas do lado do servidor (localizado dentro de 'Galáxia Conectada Site').                                             | -                                                 | -                                                           | -                                                           |                                      |
| 3   | Componente                                  | `WebUI`                             | (Frontend Website) Renderiza todas as páginas e interage com o usuário.                                                                                 | -                                                 | `IAPIGeral` (via porta `reqApiPort`), `IMonitoramento`, `IAssetDelivery` | `APIGateway`, `ServicoMonitoramento`, `GestorAssetsEstaticos` |                                      |
| 4   | Componente                                  | `ServicoConfiguracao`               | Carrega e fornece configurações (ex: chaves de API, URLs) para outros componentes. Reside no Pacote Principal.                                         | `IConfiguracao`                                   | Acesso a Artefato `config.yaml`/`env.properties`            | Artefato `config.yaml` / `env.properties`                   |                                      |
| 5   | Artefato                                    | `<<artifact>> config.yaml`          | Arquivo físico (ou fonte externa) contendo as configurações da aplicação.                                                                             | -                                                 | -                                                           | -                                                           |                                      |
| 6   | Componente                                  | `ServicoMonitoramento`              | Coleta dados de uso, erros, saúde da aplicação para análise. Reside no Pacote Principal.                                                              | `IMonitoramento`                                  | `IPersistencia` (Opcional), Conexão a Serviço Externo       | `BancoDeDados` (Opcional), `Plataforma Externa de Monitoramento` |                                      |
| 7   | Componente                                  | `GestorAssetsEstaticos`             | Armazena e entrega arquivos estáticos (CSS, JS, Imagens). Reside no Pacote Principal.                                                                  | `IAssetDelivery` (Conceitual)                     | Acesso a Artefato `static-files/`                         | Artefato `static-files/`                                  |                                      |
| 8   | Artefato                                    | `<<artifact>> static-files/`        | Representa o local físico (diretório, bucket S3) onde os arquivos estáticos residem.                                                                   | -                                                 | -                                                           | -                                                           |                                      |
| 9   | Componente                                  | `PublicAPIGateway`                  | API Gateway separada para acesso público ou por parceiros. Reside no Pacote Principal.                                                                | `IPublicAPI`                                      | Interfaces dos Módulos/Subsistemas Backend (Subconjunto)  | `GestaoUsuarios`, `Subsistema Conteudo Interativo`, etc., `Sistema Parceiro` (Externo) |                                      |
| 10  | Componente                                  | `APIGateway`                        | (Backend API) Ponto de entrada da API para a `WebUI`. Roteia requisições. Reside no Pacote `Backend Services`.                                       | `IAPIGeral` (via porta `apiPort`)                   | `IAutenticacao`, `IPerfilUsuario`, etc. (Módulos/Subsistemas), `IConfiguracao`, `IMonitoramento` | `GestaoUsuarios`, `Subsistema Conteudo Interativo`, `Subsistema Comunidade`, `Subsistema Integrações`, `ServicoNotificacoes`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 11  | Componente                                  | `GestaoUsuarios`                    | Gerencia usuários, perfis, autenticação, autorização. Suporta `Login`, `Perfil`. Reside no Pacote `Backend Services`.                                    | `IAutenticacao`, `IPerfilUsuario`                 | `IPersistencia`, `IConfiguracao`                          | `BancoDeDados`, `ServicoConfiguracao`                       |                                      |
| 12  | Componente                                  | `ServicoNotificacoes`               | Envia notificações (email, push, etc.). Serviço transversal. Reside no Pacote `Backend Services`.                                                      | `INotificacoes`                                   | `IPerfilUsuario`, `IConfiguracao`, APIs Externas          | `GestaoUsuarios`, `ServicoConfiguracao`, `Serviços Externos (Email, Push)` |                                      |
| 13  | Subsistema                                  | `<<subsystem>> Conteudo Interativo` | Agrega `ModuloEducacional`, `ModuloDivulgacao`, `ModuloJogos`. Suporta `Trilhas`, `Jogos`, destaques. Reside no Pacote `Backend Services`.             | (Interfaces das partes internas)                    | `IPersistencia`, `IGamificacao`, `IIntegracaoExterna`, `INotificacoes`, `IPerfilUsuario`, `IConfiguracao`, `IMonitoramento` | `BancoDeDados`, `ModuloGamificacao`, `ServicoBotsExternos`, `ServicoNotificacoes`, `GestaoUsuarios`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 14  | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloEducacional`                 | Gerencia `Trilhas Educativas`.                                                                                                                        | `IGestaoCursos`, `IAcessoConteudo`                | `IGamificacao` (via `gamificationPort`), `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ModuloGamificacao`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 15  | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloDivulgacao`                  | Gerencia artigos/notícias.                                                                                                                           | `IGestaoArtigos`                                  | `INotificacoes` (via `notificationPort`), `IIntegracaoExterna` (via `externalDataPort`), `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ServicoNotificacoes`, `ServicoBotsExternos`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 16  | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloJogos`                       | Gerencia a `Seção de Jogos Educativos`.                                                                                                               | `IAcessoJogos`                                    | `IGamificacao` (via `gamificationPort`), `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ModuloGamificacao`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 17  | Subsistema                                  | `<<subsystem>> Comunidade`          | Agrega `ModuloForum`, `ModuloGamificacao`. Suporta `Fórum`, `Perfil` (gamificação). Reside no Pacote `Backend Services`.                               | (Interfaces das partes internas)                    | `IPersistencia`, `IPerfilUsuario`, `INotificacoes`, `IConfiguracao`, `IMonitoramento` | `BancoDeDados`, `GestaoUsuarios`, `ServicoNotificacoes`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 18  | Parte Interna (`Comunidade`) - Componente       | `ModuloForum`                       | Gerencia o `Fórum de Discussões`.                                                                                                                     | `IGestaoForum`                                    | `IGamificacao` (via `gamificationPort`), `INotificacoes` (via `notificationPort`), `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ModuloGamificacao`, `ServicoNotificacoes`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 19  | Parte Interna (`Comunidade`) - Componente       | `ModuloGamificacao`                 | Calcula e fornece dados de XP, níveis, conquistas.                                                                                                      | `IGamificacao`                                    | `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`        | `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`     |                                      |
| 20  | Subsistema                                  | `<<subsystem>> Integrações`       | Agrega `ModuloEventos`, `ModuloPromocoes`, `ServicoBotsExternos`. Suporta `Eventos`, `Promoções`. Reside no Pacote `Backend Services`.                  | (Interfaces das partes internas)                    | `IPersistencia`, `INotificacoes`, APIs Externas, `IConfiguracao`, `IMonitoramento` | `BancoDeDados`, `ServicoNotificacoes`, `APIs/Sites Externos`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 21  | Parte Interna (`Integrações`) - Componente     | `ModuloEventos`                     | Gerencia o `Calendário de Eventos Astronômicos`.                                                                                                      | `IAgendaEventos`                                  | `INotificacoes` (via `notificationPort`), `IIntegracaoExterna` (via `externalDataPort`), `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ServicoNotificacoes`, `ServicoBotsExternos`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 22  | Parte Interna (`Integrações`) - Componente     | `ModuloPromocoes`                   | Gerencia as `Promoções Astronômicas`.                                                                                                                 | `IMonitorPromocoes`                               | `INotificacoes` (via `notificationPort`), `IIntegracaoExterna` (via `externalDataPort`), `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ServicoNotificacoes`, `ServicoBotsExternos`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 23  | Parte Interna (`Integrações`) - Componente     | `ServicoBotsExternos`               | Coleta dados externos para Eventos, Promoções, etc.                                                                                                     | `IIntegracaoExterna`                              | `IPersistencia`, APIs Externas, `IConfiguracao`           | `BancoDeDados`, `APIs/Sites Externos`, `ServicoConfiguracao` |                                      |
| 24  | Componente                                  | `BancoDeDados`                      | (Infraestrutura) Armazena todos os dados persistentes.                                                                                                | `IPersistencia` (implícita)                     | -                                                           | -                                                           |                                      |
| 25  | Artefato                                    | `<<artifact>> schema.sql`           | Arquivo físico contendo o esquema (estrutura) do banco de dados.                                                                                        | -                                                 | -                                                           | -                                                           |                                      |


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
