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


| #   | Tipo de Elemento    | Nome (Componente/Pacote/Subsistema) | Descrição   | Interfaces Providas  | Interfaces Requeridas | Dependências  |                           
| -- | -------------------- | ----------------------------------- | ----------- | -------------------- | --------------------- | ------------- |
| 1   | Pacote                                      | `<<package>> Galáxia Conectada Site`  | Pacote raiz que contém todos os elementos da plataforma web.                                                                                        | -                                                 | -                                                           | -                                                           |                                      |
| 2   | Pacote                                      | `<<package>> Backend Services`        | Agrupa os componentes e subsistemas do lado do servidor (localizado dentro de 'Galáxia Conectada Site').                                             | -                                                 | -                                                           | -                                                           |                                      |
| 3   | Componente                                  | `WebUI`                             | (Frontend Website) Renderiza todas as páginas e interage com o usuário.                                                                                 | -                                                 | `IAPIGeral` (via porta `reqApiPort`), `IMonitoramento`, `IAssetDelivery` | `APIGateway`, `ServicoMonitoramento`, `GestorAssetsEstaticos` |                                      |
| 4   | Componente                                  | `ServicoConfiguracao`               | Carrega e fornece configurações (ex: chaves de API, URLs) para outros componentes. Reside no Pacote Principal.                                         | `IConfiguracao`                                   | Acesso a Artefato `config.yaml`/`env.properties`            | Artefato `config.yaml` / `env.properties`                   |                                      |
| 5   | Artefato                                    | `<<artifact>> config.yaml`          | Arquivo físico (ou fonte externa) contendo as configurações da aplicação.                                                                             | -                                                 | -                                                           | -                                                           |                                      |
| 6   | Componente                                  | `ServicoMonitoramento`              | Coleta dados de uso, erros, saúde da aplicação para análise. Reside no Pacote Principal.                                                              | `IMonitoramento`                                  | `IPersistencia` (Opcional), Conexão a Serviço Externo       | `BancoDeDados` (Opcional), `Plataforma Externa de Monitoramento` |                                      |
| 7   | Componente                                  | `GestorAssetsEstaticos`             | Armazena e entrega arquivos estáticos (CSS, JS, Imagens). Reside no Pacote Principal.                                                                  | `IAssetDelivery` (Conceitual)                     | Acesso a Artefato `static-files/`                         | Artefato `static-files/`                                  |                                      |
| 8   | Artefato                                    | `<<artifact>> static-files/`        | Representa o local físico (diretório, bucket S3) onde os arquivos estáticos residem.                                                                   | -                                                 | -                                                           | -                                                           |                                      |
| 9   | Componente                                  | `PublicAPIGateway`                  | API Gateway separada para acesso público ou por parceiros. Reside no Pacote Principal.                                                                | `IPublicAPI`                                      | Interfaces dos Módulos/Subsistemas Backend (Subconjunto)  | `GestaoUsuarios`, `Subsistema Conteudo Interativo`, etc., `Sistema Parceiro` (Externo) |                                      |
| 10  | Componente                                  | `APIGateway`                        | (Backend API) Ponto de entrada da API para a `WebUI`. Roteia requisições. Reside no Pacote `Backend Services`.                                       | `IAPIGeral` (via porta `apiPort`)                   | `IAutenticacao`, `IPerfilUsuario`, etc. (Módulos/Subsistemas), `IConfiguracao`, `IMonitoramento`, `IBusca` | `GestaoUsuarios`, `Subsistema Conteudo Interativo`, `Subsistema Comunidade`, `Subsistema Integrações`, `ServicoNotificacoes`, `ServicoConfiguracao`, `ServicoMonitoramento`, `ServicoBusca` |                                      |
| 11  | Componente                                  | `GestaoUsuarios`                    | Gerencia usuários, perfis, autenticação, autorização. Suporta `Login`, `Perfil`. Reside no Pacote `Backend Services`.                                    | `IAutenticacao`, `IPerfilUsuario`                 | `IPersistencia`, `IConfiguracao`                          | `BancoDeDados`, `ServicoConfiguracao`                       |                                      |
| 12  | Componente                                  | `ServicoNotificacoes`               | Envia notificações (email, push, etc.). Serviço transversal. Reside no Pacote `Backend Services`.                                                      | `INotificacoes`                                   | `IPerfilUsuario`, `IConfiguracao`, APIs Externas          | `GestaoUsuarios`, `ServicoConfiguracao`, `Serviços Externos (Email, Push)` |                                      |
| **13** | **Componente** | **`ServicoBusca`** | **Indexa conteúdo (Trilhas, Fórum, Divulgação) e fornece API de busca unificada. Reside no Pacote `Backend Services`.** | **`IBusca`** | **`IAcessoConteudo`, `IGestaoArtigos`, `IGestaoForum`, `IPersistencia`, `IConfiguracao`** | **`ModuloEducacional`, `ModuloDivulgacao`, `ModuloForum`, `BancoDeDados`, `ServicoConfiguracao`** |                                      |
| 14  | Subsistema                                  | `<<subsystem>> Conteudo Interativo` | Agrega `ModuloEducacional`, `ModuloDivulgacao`, `ModuloJogos`. Suporta `Trilhas`, `Jogos`, destaques. Reside no Pacote `Backend Services`.             | (Interfaces das partes internas)                    | `IPersistencia`, `IGamificacao`, `IIntegracaoExterna`, `INotificacoes`, `IPerfilUsuario`, `IConfiguracao`, `IMonitoramento` | `BancoDeDados`, `ModuloGamificacao`, `ServicoBotsExternos`, `ServicoNotificacoes`, `GestaoUsuarios`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 15  | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloEducacional`                 | Gerencia `Trilhas Educativas`.                                                                                                                        | `IGestaoCursos`, `IAcessoConteudo`                | `IGamificacao` (via `gamificationPort`), `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ModuloGamificacao`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 16  | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloDivulgacao`                  | Gerencia artigos/notícias.                                                                                                                           | `IGestaoArtigos`                                  | `INotificacoes` (via `notificationPort`), `IIntegracaoExterna` (via `externalDataPort`), `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ServicoNotificacoes`, `ServicoBotsExternos`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 17  | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloJogos`                       | Gerencia a `Seção de Jogos Educativos`.                                                                                                               | `IAcessoJogos`                                    | `IGamificacao` (via `gamificationPort`), `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ModuloGamificacao`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 18  | Subsistema                                  | `<<subsystem>> Comunidade`          | Agrega `ModuloForum`, `ModuloGamificacao`. Suporta `Fórum`, `Perfil` (gamificação). Reside no Pacote `Backend Services`.                               | (Interfaces das partes internas)                    | `IPersistencia`, `IPerfilUsuario`, `INotificacoes`, `IConfiguracao`, `IMonitoramento` | `BancoDeDados`, `GestaoUsuarios`, `ServicoNotificacoes`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 19  | Parte Interna (`Comunidade`) - Componente       | `ModuloForum`                       | Gerencia o `Fórum de Discussões`.                                                                                                                     | `IGestaoForum`                                    | `IGamificacao` (via `gamificationPort`), `INotificacoes` (via `notificationPort`), `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ModuloGamificacao`, `ServicoNotificacoes`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 20  | Parte Interna (`Comunidade`) - Componente       | `ModuloGamificacao`                 | Calcula e fornece dados de XP, níveis, conquistas.                                                                                                      | `IGamificacao`                                    | `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`        | `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`     |                                      |
| 21  | Subsistema                                  | `<<subsystem>> Integrações`       | Agrega `ModuloEventos`, `ModuloPromocoes`, `ServicoBotsExternos`. Suporta `Eventos`, `Promoções`. Reside no Pacote `Backend Services`.                  | (Interfaces das partes internas)                    | `IPersistencia`, `INotificacoes`, APIs Externas, `IConfiguracao`, `IMonitoramento` | `BancoDeDados`, `ServicoNotificacoes`, `APIs/Sites Externos`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 22  | Parte Interna (`Integrações`) - Componente     | `ModuloEventos`                     | Gerencia o `Calendário de Eventos Astronômicos`.                                                                                                      | `IAgendaEventos`                                  | `INotificacoes` (via `notificationPort`), `IIntegracaoExterna` (via `externalDataPort`), `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ServicoNotificacoes`, `ServicoBotsExternos`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 23  | Parte Interna (`Integrações`) - Componente     | `ModuloPromocoes`                   | Gerencia as `Promoções Astronômicas`.                                                                                                                 | `IMonitorPromocoes`                               | `INotificacoes` (via `notificationPort`), `IIntegracaoExterna` (via `externalDataPort`), `IPersistencia`, `IConfiguracao`, `IMonitoramento` | `ServicoNotificacoes`, `ServicoBotsExternos`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento` |                                      |
| 24  | Parte Interna (`Integrações`) - Componente     | `ServicoBotsExternos`               | Coleta dados externos para Eventos, Promoções, etc.                                                                                                     | `IIntegracaoExterna`                              | `IPersistencia`, APIs Externas, `IConfiguracao`           | `BancoDeDados`, `APIs/Sites Externos`, `ServicoConfiguracao` |                                      |
| 25  | Componente                                  | `BancoDeDados`                      | (Infraestrutura) Armazena todos os dados persistentes.                                                                                                | `IPersistencia` (implícita)                     | -                                                           | -                                                           |                                      |
| 26  | Artefato                                    | `<<artifact>> schema.sql`           | Arquivo físico contendo o esquema (estrutura) do banco de dados.                                                                                        | -                                                 | -                                                           | -                                                           |                                      |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.




## Diagrama de Componentes


<div align="center">
    Figura 1: o Diagrama de Componentes
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/ea040765f849aa6901c6f263b2e7656ce00f1def/docs/Modelagem/Imagens/DiagramaComponentes.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

**Observação:** Caso deseje visualizar ou baixar em PDF, clique na mensagem abaixo e o pdf será mostrado. Para baixá-lo, basta clicar nele.

<details>
  <summary size="20"><b> Ver em PDF e baixá-lo </b></summary> 

<a href="..Imagens/DiagramaComponentes.pdf" target="_blank">
  <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/ea040765f849aa6901c6f263b2e7656ce00f1def/docs/Modelagem/Imagens/DiagramaComponentes.png" alt="Abrir PDF" width="1000">
</a>

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>


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
| 1.8 | Reorganização da tabela de componentes e retirada da tabela de ligações | Larissa Stéfane | 27/04/2024 |
| 1.9 | Adição do Diagrama | Larissa Stéfane | 27/04/2024 |
