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

A metodologia adotada para a elaboração do Diagrama de Componentes do projeto Galáxia Conectada será estruturada em quatro etapas principais, com o objetivo de garantir consistência com os artefatos previamente desenvolvidos.

### Etapas da metodologia:

1. inicialmente será realizado o levantamento arquitetural, no qual serão identificados os módulos centrais do sistema a partir de:
    - [Rich Picture](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/ArtefatoGeneralista/RichPicture)  elaborado na etapa inicial do projeto;
    - [Requisitos elicitados e documentados na primeira etapa](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/IniciativaExtra/RequisitosElicitados);
    - [Modelo HW2H (How, What, Why, How much)](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/ArtefatoGeneralista/5W2H);
    - [Protótipo de alta fidelidade](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/DesignSprint/Prototipo);
    - [Diagrama de Classes](/DiagramaClasses.md) construído na modelagem estática;

2. O diagrama será desenvolvido utilizando a plataforma Draw.io.
3. Será aplicada uma [verificação por meio de um checklist](.../IniciativasExtras/Verificacao/VerificacaoDiagramaComponentes.md) de boas práticas de UML;, 


## Investigação dos Componentes Necessários

Antes da modelagem visual do Diagrama de Componentes na ferramenta Draw.io, foi realizada a identificação e a definição de todos os componentes chave e subsistemas que constituiriam a arquitetura da plataforma "Galáxia Conectada". Com isso, a Tabela 1 detalha os componentes identificados para a plataforma, especificando seus tipos, descrições, interfaces e dependências.

<details>
  <summary><strong>Tabela 1: Componentes e suas dependências.</strong></summary>

**Observação:** Varios componentes foram pensados de acordo com os requisitos elicitaos, então suas refeRências estão na coluna de observações.

**Tabela 1:** Componentes
| #  | Tipo de Elemento | Nome (Componente/Pacote/Subsistema)    | Descrição   | Interfaces Providas   | Interfaces Requeridas | Dependências  | Observações  |
| -- | ---------------- | -------------------------------------- | ----------- | --------------------- | --------------------- | ------------- | ------------ |
| 1  | Pacote           | `<<package>> Galáxia Conectada Site`       | Pacote raiz que contém todos os elementos da plataforma web.                                                                                                              | -                                                                                   | -                                                                                                                                                                                         | -                                                                                                                                                                                                           |                                                                                                                                                  |
| 2  | Pacote           | `<<package>> Backend Services`             | Agrupa os componentes e subsistemas do lado do servidor (localizado dentro de 'Galáxia Conectada Site').                                                                    | -                                                                                   | -                                                                                                                                                                                         | -                                                                                                                                                                                                           |                                                                                                                                                  |
| 3  | Componente       | `WebUI`                                      | (Frontend Website) Renderiza todas as páginas e interage com o usuário.                                                                                                   | -                                                                                   | `IAPIGeral` , `IMonitoramento`, `IAssetDelivery`, `ILocalizacao` | `APIGateway`, `ServicoMonitoramento`, `GestorAssetsEstaticos`, `ServicoLocalizacao`                                                                                                      | Adicionada dependência de `ServicoLocalizacao` (RNF07).                                                                                         |
| 4  | Componente       | `ServicoConfiguracao`                      | Carrega e fornece configurações (ex: chaves de API, URLs) para outros componentes. Reside no Pacote Principal.                                                               | `IConfiguracao`                                                                     | Acesso a Artefato `config.yaml`                                                                                                                                         | Artefato `config.yaml` / `env.properties`                                                                                                                                                                 | -                                                                                                     |
| 5  | Artefato         | `<<artifact>> config.yaml`                 | Arquivo físico (ou fonte externa) contendo as configurações da aplicação.                                                                                                 | -                                                                                   | -                                                                                                                                                                                         | -                                                                                                                                                                                                           |                                                                                                                                                  |
| 6  | Componente       | `ServicoMonitoramento`                     | Coleta dados de uso, erros, saúde da aplicação para análise.                                                                                  | `IMonitoramento`                                                                    | -   | -                                                                                                                                         | -                                                                                                |
| 7  | Componente       | `GestorAssetsEstaticos`                    | Armazena e entrega arquivos estáticos (CSS, JS, Imagens, sitemaps, robots.txt).                                                              | `IAssetDelivery`                                                       | Acesso a Artefato `static-files/`, Acesso a Artefato `generated-seo-files/`                                                                                                               | Artefato `static-files/`, Artefato `generated-seo-files/`                                                                                                                                                 | Adicionado suporte a arquivos de SEO (RNF10).                                                                                                  |
| 8  | Artefato         | `<<artifact>> static-files/`               | Representa o local físico onde os arquivos estáticos residem.                                                                                      | -                                                                                   | -                                                                                                                                                                                         | -                                                                                                                                                                                                           |                                                                                                                                                  |
| 9  | Artefato         | `<<artifact>> generated-seo-files/`      | Local para arquivos gerados relacionados a SEO (sitemap.xml, etc.).                                                                                                       | -                                                                                   | -                                                                                                                                                                                         | -                                                                                                                                                                                                           | Suporta RNF10.                                                                                                                                 |
| 10 | Componente       | `PublicAPIGateway`                         | API Gateway separada para acesso público ou por parceiros.                                                                                   | `IPublicAPI`                                                                        | `IMonitoramento`, `IAcessoConteudo`, `IAutenticacao`                                                                                                                        | `Sistema Parceiro` (Externo)                                                                                                                      |                                                                                                                                                  |
| 11 | Componente       | `APIGateway`                               | (Backend API) Ponto de entrada da API para a `WebUI`. Roteia requisições. Reside no Pacote `Backend Services`.                                                               | `IAPIGeral`                                                   | `IAutenticacao`, `IPerfilUsuario`, `IConfiguracao`, `IMonitoramento`, `IBusca`, `ICache`, `INotificacoes`                                                            | `GestaoUsuarios`, `Subsistema Conteudo Interativo`, `Subsistema Comunidade`, `Subsistema Integrações`, `ServicoNotificacoes`, `ServicoConfiguracao`, `ServicoMonitoramento`, `ServicoBusca`, `ServicoCache` | Adicionada dependência opcional de `ServicoCache` (RNF02).                                                                                     |
| 12 | Componente       | `GestaoUsuarios`                           | Gerencia usuários, perfis, autenticação, autorização. Suporta `Login`, `Perfil`.                                                         | `IAutenticacao`, `IPerfilUsuario`                                                   | `IPersistencia`, `IConfiguracao`, `IMonitoramento`                                                                                                                                        | `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                                                                                             | -                                                                                                           |
| 13 | Componente       | `ServicoNotificacoes`                      | Envia notificações (email, push, etc.). Serviço transversal.                                                                 | `INotificacoes`                                                                     |  `IConfiguracao`,  `ILocalizacao`, `IPerfilUsuario`, `IRecomendacoes`, `IAgendaEventos`, `IMonitorPromocoes`                                                                                                          | `GestaoUsuarios`, `ServicoConfiguracao`, `Serviços Externos (Email, Push)`, `ServicoLocalizacao`                                                                                                          |  Adicionada dependência de `ServicoLocalizacao` (RNF07).                                        |
| 14 | Componente       | `ServicoBusca`                             | Indexa conteúdo (Trilhas, Fórum, Divulgação) e fornece API de busca unificada.                                                          | `IBusca`                                                                            | `IAcessoConteudo`, `IGestaoArtigos`, `IGestaoForum`, `IPersistencia`, `IConfiguracao`, `IMonitoramento`                                                                                  | `ModuloEducacional`, `ModuloDivulgacao`, `ModuloForum`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                                     | Essencial para RF10.                                                                                                                             |
| 15 | Componente       | `ServicoRecomendacoes`                     | Gera recomendações personalizadas de conteúdo (Trilhas, Artigos, Jogos) baseado no perfil e histórico do usuário.                        | `IRecomendacoes`                                                                    | `IPerfilUsuario`, `IGestaoCurso`, `IGestaoArtigos`, `IAcessoJogos`, `IPersistencia`.  | `GestaoUsuarios`, `ModuloEducacional`, `ModuloDivulgacao`, `ModuloJogos`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                      | Essencial para RF16.                                                                                                   |
| 16 | Componente       | `ServicoCertificados`                      | Gera e disponibiliza certificados de conclusão para Trilhas Educacionais.                                                               | `IGestaoCertificados`                                                               | `IPerfilUsuario`, `IAcessoConteudo`, `IPersistencia`, `IAssetDelivery`                                      | `GestaoUsuarios`, `ModuloEducacional`, `BancoDeDados`, `ServicoConfiguracao`, `GestorAssetsEstaticos`                                                                                                     | Necessário para RF04.                                                                                                                          |
| 17 | Componente       | `ServicoCache`                             | (Opcional) Fornece um mecanismo de cache (in-memory ou distribuído) para otimizar o acesso a dados frequentes. Reside no Pacote `Backend Services`.                          | `ICache`                                                                            | `IPersistencia` , `IConfiguracao`                                                                                                                     | `BancoDeDados` (opcional), `ServicoConfiguracao`                                                                                                                             | Ajuda a atender RNF02 (Performance).                                                   |
| 18 | Componente       | `ServicoLocalizacao`                       | Fornece textos e strings traduzidos para diferentes idiomas suportados.                                                                 | `ILocalizacao`                                                                      | `IPersistencia` ou acesso a Artefato `localization_files/`, `IConfiguracao`                                                                                                             | `BancoDeDados` ou Artefato `localization_files/`, `ServicoConfiguracao`                                                                                                                                 | Suporta RNF07 (Multi-idioma).                                                                         |
| 19 | Artefato         | `<<artifact>> localization_files/`         | Arquivos (ex: JSON, properties) contendo as traduções da interface e conteúdo.                                                                                            | -                                                                                   | -                                                                                                                                                                                         | -                                                                                                                                                                                                           | Fonte de dados para `ServicoLocalizacao`.                                                                                                      |
| 20 | Subsistema       | `<<subsystem>> Conteudo Interativo`        | Agrega `ModuloEducacional`, `ModuloDivulgacao`, `ModuloJogos`, `ModuloRecursosPraticos`. Suporta `Trilhas`, `Jogos`, destaques, experimentos/apps. Reside no Pacote `Backend Services`. |                                                    | `IPersistencia`, `IGamificacao`, `IIntegracaoExterna`, `INotificacoes`, `IPerfilUsuario`, `IConfiguracao`, `IMonitoramento`, `IBusca`                                       | `BancoDeDados`, `ModuloGamificacao`, `BotImportadorNoticias`, `ServicoNotificacoes`, `GestaoUsuarios`, `ServicoConfiguracao`, `ServicoMonitoramento`, `ServicoBusca`                                           | Contém os módulos relacionados ao conteúdo principal da plataforma.                                                                              |
| 21 | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloEducacional`                        | Gerencia `Trilhas Educativas`, módulos, conteúdos (Artigo, Video, Quiz), progresso.                                                                        | `IGestaoCursos`, `IAcessoConteudo`,                               | `IGamificacao` , `IPerfilUsuario`, `IGestaoCertificados`                                                       | `ModuloGamificacao`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`, `ServicoCertificados`                                                                           | Interage com `ServicoCertificados` (RF04).                                                                                                     |
| 22 | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloDivulgacao`                         | Gerencia artigos/notícias (internos e externos), blog, glossário. Permite **submissão de usuário (RF15)**.                                                         | `IGestaoArtigos`                                                                    | `INotificacoes` , `IAcessoFonteExterna`, `IPerfilUsuario`, `IPersistencia`, `IConfiguracao` | `ServicoNotificacoes`, `BotImportadorNoticias`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                        |                                                                    |
| 23 | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloJogos`                              | Gerencia a `Seção de Jogos Educativos` e quizzes interativos.                                                                                             | `IAcessoJogos`                                                                      | `IGamificacao`,  `IPersistencia`, `IConfiguracao`                                                                            | `ModuloGamificacao`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                                                    |                                                                                                                                                  |
| 24 | Parte Interna (`Conteudo Interativo`) - Componente | `ModuloRecursosPraticos`                   | Gerencia roteiros de experimentos práticos e indicações de apps de astronomia.                                                                           | `IAcessoRecursosPraticos`                                                           | `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`                                                                                                                   | `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                                                                         | Implementa RF18.                                                                                                                               |
| 25 | Subsistema       | `<<subsystem>> Comunidade`                 | Agrega `ModuloForum`, `ModuloGamificacao`, `ModuloModeracao`. Suporta `Fórum`, `Perfil` (gamificação), Moderação. Reside no Pacote `Backend Services`.                      | (Interfaces das partes internas)                                                    | `IPersistencia`, `IPerfilUsuario`, `INotificacoes`, `IConfiguracao`, `IMonitoramento`, `IBusca` (para indexação)                                                                      | `BancoDeDados`, `GestaoUsuarios`, `ServicoNotificacoes`, `ServicoConfiguracao`, `ServicoMonitoramento`, `ServicoBusca`                                                                                | Contém os módulos relacionados à interação entre usuários.                                                                                       |
| 26 | Parte Interna (`Comunidade`) - Componente      | `ModuloForum`                              | Gerencia o `Fórum de Discussões` (tópicos, posts, comentários, votos).                                                                                    | `IGestaoForum`                                                                      |  `INotificacoes`, `IPerfilUsuario`, `IModeracao`                      | `ServicoNotificacoes`, `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`, `ModuloModeracao`                                                         | Interage com `ModuloModeracao` (RF07, RF09).                                                                                                   |
| 27 | Parte Interna (`Comunidade`) - Componente      | `ModuloGamificacao`                        | Calcula e fornece dados de XP, níveis, conquistas, reputação, rankings.                                                                                  | `IGamificacao`                                                                      | `IPerfilUsuario`, `IPersistencia`, `IAcessoJogos`                                                                   | `GestaoUsuarios`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                                                                         | -                                                                                                                      |
| 28 | Parte Interna (`Comunidade`) - Componente      | `ModuloModeracao`                          | Fornece funcionalidades para moderadores revisarem e gerenciarem conteúdo gerado pelo usuário (posts de fórum, artigos submetidos, comentários).             | `IModeracao`                                                                        | `IGestaoForum`, `IGestaoArtigos`.                                                     | `GestaoUsuarios`, `ModuloForum`, `ModuloDivulgacao`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                                     | Centraliza a lógica de moderação (RF07, RF09, RF15).                                                                                           |
| 29 | Subsistema       | `<<subsystem>> Integrações`                | Agrega `ModuloEventos`, `ModuloPromocoes`, `BotImportadorNoticias`, `BotImportadorPromocoes`. Suporta `Eventos`, `Promoções`. Reside no Pacote `Backend Services`.              | Interfaces das partes internas e dos Bots                                         | `IPersistencia`, `INotificacoes`, APIs Externas, `IConfiguracao`, `IMonitoramento`                                                                                                        | `BancoDeDados`, `ServicoNotificacoes`, `APIs/Sites Externos`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                                          | Contém módulos e bots que lidam com dados externos.                                                                                            |
| 30 | Parte Interna (`Integrações`) - Componente     | `ModuloEventos`                            | Gerencia o `Calendário de Eventos Astronômicos`.                                                                                 | `IAgendaEventos`                                                                    | `INotificacoes`, `IAcessoFonteExterna`.                                              | `ServicoNotificacoes`, `APIs/Sites Externos`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                                        |                                                                                                            |
| 31 | Parte Interna (`Integrações`) - Componente     | `ModuloPromocoes`                          | Gerencia as `Promoções Astronômicas` encontradas externamente.                                                                                            | `IMonitorPromocoes`                                                                 | `INotificacoes`, `IAcessoFonteExternaBots` (de Bots),                                                              | `ServicoNotificacoes`, `BotImportadorPromocoes`, `BancoDeDados`, `ServicoConfiguracao`, `ServicoMonitoramento`                                                                                     | Depende do `BotImportadorPromocoes`.                                                                                                           |
| 32 | Parte Interna (`Integrações`) - Componente     | `BotImportadorNoticias`                    | Componente/Processo que busca notícias em `FonteDeNoticias` configuradas e as importa via `IGestaoArtigos`.                                                     | `IAcessoFonteExternaBots`                            | `IAcessoFonteExterna`   |  `BancoDeDados`, `APIs/Sites Externos`, `ModuloDivulgacao`                                                                                                                  |                                                                                                       |
| 33 | Parte Interna (`Integrações`) - Componente     | `BotImportadorPromocoes`                   | Componente/Processo que busca promoções em `FontePromocaoExterna` configuradas e as registra via `IMonitorPromocoes`.                                                 | `INotificacoes`, `IIntegracaoExternaBots`                           | `IConfiguracao`, `IPersistencia` (para estado/log), APIs Externas (`FontePromocaoExterna`), `IMonitorPromocoes`                                                                       | `ServicoConfiguracao`, `BancoDeDados`, `APIs/Sites Externos`, `ModuloPromocoes`                                                                                                                   | Reflete a classe `BotImportadorPromocoes`.                                                                                                     |
| 34 | Componente       | `BancoDeDados`                             | (Infraestrutura) Armazena todos os dados persistentes.                                                                                                                    | `IPersistencia`                                                         | <<deploy>> `schema.sql`                                                                                                                                                                   | Artefato `schema.sql`                                                                                                                                                                             | Adicionada relação de deploy com o schema.                                                                                                       |
| 35 | Artefato         | `<<artifact>> schema.sql`                  | Arquivo físico contendo o esquema (estrutura) do banco de dados.                                                                                                          | -                                                                                   | -                                                                                                                                                                                         | -                                                                                                                                                                                                           |                                                                                                                                                  |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.


</details>

## Diagrama de Componentes

Para melhor compreensão do diagrama, a figura 1 mostra a legenda;

<div align="center">
    Figura 1: Legenda do Diagrama de Componentes
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/53cf0acfd5aa2490e948ad1c33379fc1ae75b03d/docs/Modelagem/Imagens/LegendaDiagramaComponentes.png" width="500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

Para tornar o diagrama de componentes mais legível, foram adicionadas cores aos elementos. O pacote do site está em amarelo, o pacote do backend em azul, e cada subsistema foi representado com uma cor distinta para facilitar a identificação visual.

Para facilitar a leitura e a compreensão da estrutura do sistema, o diagrama de componentes será apresentado em três partes: inicialmente, o pacote do site da Galáxia Conectada; em seguida, o pacote do backend; e, por fim, o diagrama completo que reúne ambos os pacotes em uma visão unificada.


<div align="center">
    Figura 2: o Diagrama de Componentes: Pacote do Site
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/53cf0acfd5aa2490e948ad1c33379fc1ae75b03d/docs/Modelagem/Imagens/DiagramaComponentesSite.drawio.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

**Observação:** Caso deseje visualizar ou baixar em PDF, clique [Diagrama de Componentes: Pacote do Site em PDF](https://github.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/blob/main/docs/Modelagem/Imagens/DiagramaComponentesSite.drawio.pdf)


<div align="center">
    Figura 3: o Diagrama de Componentes: Pacote do Backend
    <br>
    <img src="../Imagens/DiagramaComponentesPacoteBACKhend.drawio.png" alt="Diagrama Backend" width="1500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

**Observação:** Caso deseje visualizar ou baixar em PDF, clique [o Diagrama de Componentes: Pacote do Backend em PDF](/Imagens/DiagramaComponentesPacoteBACKhend.drawio.pdf)


<div align="center">
    Figura 4: o Diagrama de Componentes Completo
    <br>
    <img src="/Imagens/DiagramaComponentesCompleto.drawio.png" alt="Diagrama Completo" width="1500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

**Observação:** Caso deseje visualizar ou baixar em PDF, clique [ o Diagrama de Componentes Completo em PDF](/Imagens/DiagramaComponentesCompleto.drawio.pdf)



## Conclusão

O Diagrama de Componentes apresenta de forma estruturada os módulos físicos do sistema, suas interfaces e dependências. Essa visão facilita o planejamento de implantação, a definição de pipelines de build/deploy e a manutenção evolutiva da plataforma, ao evidenciar claramente quais artefatos e serviços cada componente exige ou oferece.

## Bibliografia

<a name="ref1"></a>  
[1]APOSTILA UML. *Linguagem de Modelagem Unificada*. Disponibilizado pela professora. Acesso em: 25 abr. 2025.  

<a name="ref2"></a>  
[2]UML DIAGRAMS. *Component Diagrams Overview*. Disponível em: https://www.uml-diagrams.org/component-diagrams.html. Acesso em: 25 abr. 2025. 

<a name="ref3"></a>  
[3] IBM CORPORATION. *Component diagrams*. IBM Documentation, 2023. Disponível em: https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component. Acesso em: 25 abr. 2025.  

<a name="ref4"></a>  
[4] LUCID SOFTWARE INC. *UML Component Diagram*. Lucidchart, 2024. Disponível em: https://www.lucidchart.com/pages/uml-component-diagram. Acesso em: 25 abr. 2025.

<a name="ref5"></a>  
[5] VISUAL PARADIGM INTERNATIONAL. *UML Component Diagram Guide*. Visual Paradigm, 2024. Disponível em: https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-component-diagram/. Acesso em: 25 abr. 2025.  

<a name="ref6"></a>
[6] IBM CORPORATION. Diagrama de componentes. IBM Documentation. Disponível em: https://www.ibm.com/docs/pt-br/rsas/7.5.0?topic=services-component-diagrams. Acesso em: 27 abr. 2025.

<a name="ref7"></a>
[7] LUCID SOFTWARE INC. Diagrama de componentes UML. Lucidchart. Disponível em: https://www.lucidchart.com/pages/pt/diagrama-de-componentes-uml. Acesso em: 27 abr. 2025.

<a name="ref8"></a>
[8] CREATELY. Tutorial de Diagrama de Componentes UML. Disponível em: https://creately.com/blog/pt/diagrama/tutorial-de-diagrama-de-componentes-2/. Acesso em: 27 abr. 2025.

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
| 2.0 | Reestruturação da tabela e adição da legenda | Larissa Stéfane | 28/04/2024 |
| 2.1 | Adição dos novos Diagramas | Larissa Stéfane | 29/04/2024 |
| 2.2 | Ajustes no artefato| Larissa Stéfane | 06/05/2024 |
