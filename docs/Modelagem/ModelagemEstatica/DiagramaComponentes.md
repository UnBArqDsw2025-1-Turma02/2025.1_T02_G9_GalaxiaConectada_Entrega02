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

| # | Componente      | Descrição/Responsabilidade Principal        | Interfaces Providas  | Dependências / Interfaces Requeridas  |
|---|-----------------|---------------------------------------------|----------------------|---------------------------------------|
| 1 | **`WebUI`** | Interface gráfica com o usuário final via navegador web (desktop/mobile). Exibe dados e captura interações do usuário.                  | - (Interage diretamente com o usuário)             | `IAPIGeral` (do APIGateway)                                                                                                                                                                  |
| 2 | **`APIGateway`** | Ponto único de entrada e orquestração para a `WebUI`. Roteia requisições aos serviços de backend apropriados e agrega respostas.           | `IAPIGeral`                                        | `IAutenticacao`, `IPerfilUsuario`, `IGestaoCursos`, `IAcessoConteudo`, `IGestaoArtigos`, `IAcessoJogos`, `IGestaoForum`, `IGamificacao`, `IAgendaEventos`, `IMonitorPromocoes`, `INotificacoes` |
| 3 | **`GestaoUsuarios`** | Gerencia cadastro, login, perfis, papéis (Aluno, Instrutor, etc.) e controle de acesso (autenticação/autorização).                     | `IAutenticacao`, `IPerfilUsuario`                  | `IPersistencia` (do BancoDeDados)                                                                                                                                                            |
| 4 | **`ModuloEducacional`** | Gerencia trilhas de aprendizado, módulos, conteúdos (vídeos, artigos, quizzes internos), progresso do aluno e emissão de certificados.    | `IGestaoCursos`, `IAcessoConteudo`                 | `IPersistencia`, `IGamificacao`, `IPerfilUsuario`                                                                                                                                            |
| 5 | **`ModuloDivulgacao`** | Gerencia artigos de divulgação científica, notícias (internas/externas via bot), categorias, glossário e comentários/submissões.         | `IGestaoArtigos`                                   | `IPersistencia`, `IIntegracaoExterna` (para notícias), `IPerfilUsuario`, `INotificacoes` (para novas publicações/comentários)                                                                |
| 6 | **`ModuloJogos`** | Implementa e gerencia jogos interativos (quizzes, desafios), pontuações e rankings específicos dos jogos.                                 | `IAcessoJogos`                                     | `IPersistencia`, `IGamificacao`, `IPerfilUsuario`                                                                                                                                            |
| 7 | **`ModuloForum`** | Gerencia a estrutura de fóruns/subfóruns, tópicos, postagens, moderação e interage com Gamificação para reputação.                       | `IGestaoForum`                                     | `IPersistencia`, `IGamificacao`, `IPerfilUsuario`, `INotificacoes`                                                                                                                           |
| 8 | **`ModuloGamificacao`** | Centraliza a lógica de gamificação: cálculo e armazenamento de XP, níveis, conquistas e reputação, baseado em eventos de outros módulos. | `IGamificacao`                                     | `IPersistencia`, `IPerfilUsuario`                                                                                                                                                            |
| 9 | **`ModuloEventos`** | Mantém e exibe o calendário de eventos astronômicos (internos ou externos via bot), permitindo filtros e disparando notificações.         | `IAgendaEventos`                                   | `IPersistencia`, `IIntegracaoExterna` (para eventos), `INotificacoes`                                                                                                                        |
| 10| **`ModuloPromocoes`** | Exibe promoções de produtos astronômicos (telescópios, livros) coletadas pelos bots, com filtros e sistema de favoritos.                | `IMonitorPromocoes`                                | `IPersistencia`, `IIntegracaoExterna` (para promoções), `INotificacoes`                                                                                                                      |
| 11| **`ServicoNotificacoes`** | Responsável pelo envio de notificações aos usuários através de múltiplos canais (plataforma, e-mail, push).                            | `INotificacoes`                                    | `IPerfilUsuario` (para dados de contato/preferências), (Possivelmente serviços externos de email/push API)                                                                                |
| 12| **`ServicoBotsExternos`** | Agrupa processos automatizados (bots) que coletam dados de fontes externas: notícias, eventos, promoções de e-commerce.                 | `IIntegracaoExterna` (para fornecer dados coletados) | `IPersistencia` (para configuração/logs), (APIs/Sites Externos)                                                                                                                               |
| 13| **`BancoDeDados`** | Representa a camada de persistência de dados da aplicação (ex: Banco de dados relacional ou NoSQL).                                    | `IPersistencia` (implícita ou via ORM/Driver)      | - (É a base da infraestrutura de dados)                                                                                                                                                     |


<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.


## As Ligações entre os Componentes


As relações padrão mostrada na tabela são **Dependências**.
**Tabela2 : Conexões entre Componentes 

| Componente Origem       | Componente Destino      | Interface Fornecida (Destino) | Interface Requerida / Porta (Origem) | Notas / Racional                                                                                                                                                               |
| :---------------------- | :---------------------- | :---------------------------- | :----------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `WebUI`                 | `APIGateway`            | `IAPIGeral`                   | Porta `apiPort` (Requer `IAPIGeral`) | A interface web (`WebUI`) precisa consumir a API principal (`IAPIGeral`) exposta pelo `APIGateway` através de um ponto de entrada definido (`apiPort`). Representa o uso da API. |
| `APIGateway`            | `GestaoUsuarios`        | `IAutenticacao`, `IPerfilUsuario` | -                                    | O Gateway delega chamadas de autenticação e gerenciamento de perfil para este componente.                                                                                      |
| `APIGateway`            | `ModuloEducacional`     | `IGestaoCursos`, `IAcessoConteudo` | -                                    | Delega chamadas relacionadas a cursos, conteúdos e progresso.                                                                                                                |
| `APIGateway`            | `ModuloDivulgacao`      | `IGestaoArtigos`            | -                                    | Delega chamadas para buscar ou gerenciar artigos/notícias.                                                                                                                   |
| `APIGateway`            | `ModuloJogos`           | `IAcessoJogos`              | -                                    | Delega chamadas relacionadas a jogos e pontuações.                                                                                                                           |
| `APIGateway`            | `ModuloForum`           | `IGestaoForum`              | -                                    | Delega chamadas para interagir com o fórum.                                                                                                                                 |
| `APIGateway`            | `ModuloGamificacao`     | `IGamificacao`              | -                                    | Delega chamadas para buscar informações de gamificação (XP, nível, etc.).                                                                                                      |
| `APIGateway`            | `ModuloEventos`         | `IAgendaEventos`            | -                                    | Delega chamadas para buscar dados do calendário de eventos.                                                                                                                  |
| `APIGateway`            | `ModuloPromocoes`       | `IMonitorPromocoes`         | -                                    | Delega chamadas para buscar promoções.                                                                                                                                      |
| `APIGateway`            | `ServicoNotificacoes`   | `INotificacoes`             | -                                    | Dispara o envio de notificações com base em ações ocorridas no backend.                                                                                                      |
| `ModuloEducacional`     | `ModuloGamificacao`     | `IGamificacao`              | Porta `gamificationPort`             | Notifica o módulo de gamificação sobre progressos (ex: módulo concluído) através de uma porta específica para registrar XP/conquistas.                                            |
| `ModuloEducacional`     | `BancoDeDados`          | `IPersistencia`             | -                                    | Necessita acessar o banco para ler/escrever dados de cursos, módulos, progresso.                                                                                              |
| `ModuloJogos`           | `ModuloGamificacao`     | `IGamificacao`              | Porta `gamificationPort`             | Notifica o módulo de gamificação sobre resultados de jogos (pontuações) via porta específica.                                                                                 |
| `ModuloJogos`           | `BancoDeDados`          | `IPersistencia`             | -                                    | Necessita acessar o banco para ler/escrever dados de jogos, recordes.                                                                                                        |
| `ModuloForum`           | `ModuloGamificacao`     | `IGamificacao`              | Porta `gamificationPort`             | Notifica o módulo de gamificação sobre atividades (posts, votos) via porta específica para atualizar reputação/XP.                                                              |
| `ModuloForum`           | `ServicoNotificacoes`   | `INotificacoes`             | Porta `notificationPort`             | Solicita o envio de notificações (ex: novo post em tópico seguido) através de uma porta dedicada.                                                                            |
| `ModuloForum`           | `BancoDeDados`          | `IPersistencia`             | -                                    | Necessita acessar o banco para ler/escrever dados de fóruns, tópicos, posts.                                                                                                  |
| `ModuloDivulgacao`      | `ServicoBotsExternos`   | `IIntegracaoExterna`        | Porta `externalDataPort`             | Consome dados de notícias coletados pelos bots através de uma porta específica.                                                                                                |
| `ModuloDivulgacao`      | `ServicoNotificacoes`   | `INotificacoes`             | Porta `notificationPort`             | Solicita notificações (ex: novo artigo publicado) via porta dedicada.                                                                                                       |
| `ModuloDivulgacao`      | `BancoDeDados`          | `IPersistencia`             | -                                    | Necessita acessar o banco para ler/escrever artigos, notícias.                                                                                                              |
| `ModuloEventos`         | `ServicoBotsExternos`   | `IIntegracaoExterna`        | Porta `externalDataPort`             | Consome dados de eventos coletados pelos bots via porta específica.                                                                                                          |
| `ModuloEventos`         | `ServicoNotificacoes`   | `INotificacoes`             | Porta `notificationPort`             | Solicita notificações/lembretes de eventos via porta dedicada.                                                                                                              |
| `ModuloEventos`         | `BancoDeDados`          | `IPersistencia`             | -                                    | Necessita acessar o banco para ler/escrever detalhes de eventos.                                                                                                             |
| `ModuloPromocoes`       | `ServicoBotsExternos`   | `IIntegracaoExterna`        | Porta `externalDataPort`             | Consome dados de promoções coletados pelos bots via porta específica.                                                                                                       |
| `ModuloPromocoes`       | `ServicoNotificacoes`   | `INotificacoes`             | Porta `notificationPort`             | Solicita notificações sobre novas promoções relevantes via porta dedicada.                                                                                                   |
| `ModuloPromocoes`       | `BancoDeDados`          | `IPersistencia`             | -                                    | Necessita acessar o banco para ler/escrever dados de promoções, preferências do usuário.                                                                                       |
| `GestaoUsuarios`        | `BancoDeDados`          | `IPersistencia`             | -                                    | Necessita acessar o banco para ler/escrever dados de usuários, perfis, credenciais.                                                                                           |
| `ModuloGamificacao`     | `BancoDeDados`          | `IPersistencia`             | -                                    | Necessita acessar o banco para ler/escrever dados de XP, níveis, conquistas, reputação.                                                                                      |
| `ServicoNotificacoes`   | `GestaoUsuarios`        | `IPerfilUsuario`            | -                                    | Precisa buscar dados do usuário (email, preferências) para poder enviar a notificação corretamente.                                                                          |
| `ServicoNotificacoes`   | `(Serviços Externos)` | `(API Email, API Push, etc.)` | -                                    | Depende de serviços externos (representados fora do diagrama ou como ator/componente externo) para o envio efetivo da notificação.                                                 |
| `ServicoBotsExternos`   | `BancoDeDados`          | `IPersistencia`             | -                                    | Necessita acessar o banco para ler configurações (sites a monitorar) e gravar logs.                                                                                            |
| `ServicoBotsExternos`   | `(APIs/Sites Externos)` | -                           | -                                    | Depende de acessar sites e APIs externas (representados fora do diagrama ou como ator/componente externo) para coletar os dados.                                                 |


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
| 1.5 | Criação da tabela de ligações ente os componentes | Larissa Stéfane | 26/04/2024 |
