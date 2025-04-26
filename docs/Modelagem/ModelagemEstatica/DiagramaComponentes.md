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

Segundo a Apostila UML – Linguagem de Modelagem Unificada [1] e o guia da plataforma UML Diagrams [2], um **componente** é uma unidade física de software (código-fonte, biblioteca, executável) que encapsula um conjunto de funcionalidades. Com base nisso, o **Diagrama de Componentes** representa visualmente esses módulos e suas dependências, e assim mostra quais artefatos (ex.: arquivos .jar, .dll, .py) são necessários para executar cada parte do sistema. No projeto Galáxia Conectada, esse diagrama expõe módulos como Interface Web, API de Cursos, Serviço de Notificações, Banco de Dados e Integração com APIs externas (ex.: NASA).

## Objetivos

Tem em base o conceito de componentes e diagrama de componentes, busca-se os seguintes objetivos: 

- Apresentar de forma clara os componentes físicos do sistema Galáxia Conectada.  
- Evidenciar interfaces providas e requeridas por cada módulo.  
- Documentar dependências e artefatos para suportar implementação e deploy.  

## Metodologia

A metodologia adotada para a elaboração do Diagrama de Componentes do projeto Galáxia Conectada compreenderá quatro etapas principais: inicialmente será realizado o levantamento arquitetural, no qual serão identificados os módulos centrais do sistema a partir dos requisitos funcionais, do rich-picture e da análise 5W2H; em seguida, proceder-se-á à modelagem inicial no Draw.io, esboçando cada componente e as interfaces que proverá ou requererá; posteriormente, aplicar-se-á a verificação por meio de um checklist de boas práticas UML, avaliando notação, nomenclatura, coesão e clareza das dependências; por fim, conduzir-se-ão ajustes visuais e de nomenclatura para otimizar a legibilidade, a rastreabilidade e a conformidade do diagrama com os padrões estabelecidos.

## Investigação dos Componentes Necessários

## Investigação dos Componentes Necessários (versão detalhada)

| Componente       | Responsabilidade      | Artefatos      | Interfaces Providas     | Interfaces Requeridas        |
|------------------|-----------------------|----------------|-------------------------|------------------------------|
| **WebUI**                | - Renderizar telas responsivas (desktop/mobile)  <br>- Capturar eventos de usuário (cliques, formulários)  <br>- Validar entradas no client-side                         | `webui.jar`<br>`styles.css`<br>`index.html`           | `IAutenticacao`<br>`ICursos`<br>`IForum`                                                                    | `IAPICursos`<br>`INotificacoes`<br>`ISearch`                       |
| **AuthService**          | - Gerenciar login/logout  <br>- Emitir JWT/OAuth tokens  <br>- Renovar e revogar tokens                                                                              | `auth-service.jar`<br>`auth-config.yaml`              | `IAutenticacao`<br>`IUsuario`                                                                                | `IDatabase`<br>`ILogger`                                            |
| **APICursos**            | - CRUD de cursos, módulos e quizzes  <br>- Validação de regras de negócio (pré-requisitos de trilhas)  <br>- Paginação e filtro de listagens                           | `apicursos.jar`<br>`courses-schema.sql`               | `ICursos`<br>`ITrilhas`                                                                                     | `IDatabase`<br>`ILogging`                                           |
| **ServicoNotificacoes**   | - Agendar envio de push, e-mail e bot messages  <br>- Gerenciar templates de notificação  <br>- Rastrear entregas e leituras                                         | `notif-service.jar`<br>`templates/`                   | `INotificacoes`<br>`IEmail`<br>`IPush`                                                                        | `IUsuario`<br>`IEventoAstronomico`                                  |
| **Database**             | - Persistir entidades do domínio (Usuário, Curso, Progresso)  <br>- Garantir ACID e backups  <br>- Fornecer conexões JDBC/ORM                                          | `postgres.db`<br>`db-migrations/`                     | `IDatabase`                                                                                                 | —                                                                   |
| **IntegracaoExterna**    | - Chamar APIs externas (NASA, ESA)  <br>- Traduzir e normalizar payloads  <br>- Gerenciar rate-limit e cache                                                          | `integracao-api.py`<br>`schemas/external/`            | —                                                                                                          | `IFonteNoticias`<br>`ILogger`                                      |
| **BotImportador**        | - Agendar tarefas de importação (cron)  <br>- Extrair e mapear notícias astronômicas  <br>- Registrar logs de importação                                             | `bot_import.py`<br>`cron.yaml`                        | `IFonteNoticias`                                                                                           | `IntegracaoExterna`<br>`IDatabase`                                  |
| **ServicoRecomendacao**   | - Gerar recomendações personalizadas (CF, conteúdo similar)  <br>- Treinar e servir modelos ML  <br>- Exportar relatórios de acurácia                                   | `recommender.jar`<br>`models/`                        | `IRecomendacao`                                                                                             | `IDatabase`<br>`ILogger`<br>`IUsuario`                              |
| **ForumService**         | - CRUD de tópicos, postagens e comentários  <br>- Gerenciar sistema de reputação e votos  <br>- Moderar conteúdo via regras e bots                                      | `forum-service.jar`<br>`forum-schema.sql`             | `IForum`<br>`ITopico`<br>`IComentario`                                                                        | `IDatabase`<br>`IAuthService`                                       |
| **SearchService**        | - Indexar conteúdos (trilhas, artigos, quizzes)  <br>- Executar buscas por texto e facetas  <br>- Sugerir termos relacionados                                            | `search-service.jar`<br>`elasticsearch-config.yml`    | `ISearch`                                                                                                   | `IDatabase`<br>`IContentService`                                   |
| **ContentService**       | - Gerenciar publicação de artigos, vídeos e experimentos  <br>- Versionamento de conteúdo  <br>- Workflow de aprovação editorial                                          | `content-service.jar`<br>`cms-config.yaml`            | `IContentManagement`                                                                                         | `IDatabase`<br>`IAuthService`                                      |
| **EventoScheduler**      | - Agendar eventos astronômicos  <br>- Sincronizar com calendário externo  <br>- Enviar lembretes pré-evento                                                           | `event-scheduler.jar`<br>`scheduler-config.yaml`      | `IEventoAstronomico`<br>`INotificacoes`                                                                       | `IDatabase`                                                       |
| **PromocaoService**      | - Gerenciar campanhas e descontos  <br>- Filtrar promoções por categoria  <br>- Notificar usuários sobre ofertas                                                       | `promocao-service.jar`<br>`promotions-schema.sql`     | `IPromocao`<br>`INotificacoes`                                                                                | `IDatabase`                                                       |
| **LoggingService**       | - Centralizar logs de aplicação (error, audit)  <br>- Rotações e retenção  <br>- Expor API de consulta de logs                                                       | `logging-service.jar`<br>`log4j2.xml`                 | `ILogger`                                                                                                    | —                                                                   |
| **AnalyticsService**     | - Coletar métricas de uso (page views, eventos)  <br>- Gerar dashboards e relatórios  <br>- Exportar dados para BI                                                    | `analytics-service.jar`<br>`grafana-dashboards/`      | `IAnalytics`                                                                                                 | `IDatabase`<br>`ILogger`                                           |
| **CacheService**         | - Fornecer cache distribuído de objetos de domínio  <br>- Configurar TTL e invalidação  <br>- Monitorar hit/miss rate                                                 | `cache-service.jar`<br>`redis-config.yaml`            | `ICache`                                                                                                     | `IDatabase`<br>`ILogger`                                           |
| **NotificationBot**      | - Escutar eventos do sistema  <br>- Enviar mensagens em tempo real via chat-bot  <br>- Responder comandos de usuários                                                   | `notification-bot.js`<br>`bot-config.json`            | `INotificacoesBot`                                                                                         | `IUsuario`<br>`IForum`                                             |
| **HealthCheckService**   | - Verificar saúde dos componentes (ping, tempo de resposta)  <br>- Expor endpoints de status  <br>- Alertar sobre falhas                                                | `health-service.jar`<br>`health-config.yaml`          | `IHealthCheck`                                                                                              | `ILogger`<br>`INotificacoes`                                        |
| **PaymentService**       | - Processar transações financeiras (pagamentos, reembolsos)  <br>- Integrar com gateways (Stripe, PayPal)  <br>- Gerenciar faturas e recibos                           | `payment-service.jar`<br>`payment-config.yaml`        | `IPayment`                                                                                                   | `IDatabase`<br>`ILogger`                                           |
| **UserProfileService**   | - Gerenciar preferências do usuário  <br>- Atualizar avatar, configurações de notificação  <br>- Sincronizar dados com AuthService                                      | `profile-service.jar`<br>`profile-schema.sql`         | `IUserProfile`                                                                                               | `IAuthService`<br>`IDatabase`                                      |
| **EmailService**         | - Enviar e-mail transacional e marketing  <br>- Gerenciar templates e filas  <br>- Rastrear entregabilidade e bounces                                              | `email-service.jar`<br>`smtp-config.yaml`             | `IEmail`                                                                                                     | `ILogger`<br>`IDatabase`                                           |




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
| 1.2 | Criação da tabela de investigação das classes | Larissa Stéfane | 26/04/2024 |
