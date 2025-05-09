# Diagrama de Pacotes

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Sobre o Diagrama de Pacotes](#Sobre-o-Diagrama-de-Pacotes)
- [Elaboração do Diagrama](Elaboração-do-Diagrama)
- [Diagrama de Pacotes](#Diagrama-de-Pacotes)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)

## Introdução

O Diagrama de Pacotes é um dos diagramas estruturais da UML (Unified Modeling Language) utilizado para representar, de forma hierárquica e organizada, os agrupamentos lógicos dos elementos de um sistema, como classes, casos de uso, componentes, entre outros. Conforme definido na APOSTILA UML [1](#ref1), o pacote é um mecanismo de propósito geral que permite reunir elementos semanticamente relacionados, o que facilita a visualização e o gerenciamento modular de grandes sistemas.

Segundo o [Diagrama de Pacotes: Definição, Componentes](https://gitmind.com/pt/diagrama-de-pacotes.html#:~:text=Um%20diagrama%20de%20pacotes%20pode,outros%20campos%20em%20pacotes%20simplificados.) [2](#ref2) , o diagrama de pacotes simplifica a leitura de sistemas complexos e torna visíveis suas dependências e relacionamentos de alto nível. Cada pacote pode conter elementos empacotáveis, como diagramas, documentos e outros pacotes, e relaciona-se a outros por meio de dependências, importações e extensões. 

Neste artefato, procura-se apresentar o Diagrama de Pacotes da plataforma Galáxia Conectada, que visa ilustrar os principais agrupamentos funcionais e estruturais do sistema.

## Objetivos

Com o intuito de apresentar o Diagrama de Pacotes e destacar a estrutura modular do sistema, busca-se:

- Representar a organização lógica dos elementos do sistema em pacotes distintos;

- Evidenciar relações de dependência entre pacotes;

- Facilitar a compreensão da arquitetura em camadas da plataforma;

- Contribuir para a manutenibilidade, escalabilidade e reutilização dos componentes do software;


## Metodologia

Para a construção do diagrama, serão seguidas as etapas abaixo:

1. Serão analisados os seguintes artefatos para agrupamento e análise de informações:

- [Requisitos Funcionais e Não Funcionais elicitados - Elaborados na entrega 1](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/IniciativaExtra/RequisitosElicitados);
- [Diagrama de Classe](/Modelagem/ModelagemEstatica/DiagramaClasses.md);
- [Diagrama de Componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md);
- [Diagrama de Casos de Uso](/Modelagem/ModelagemOrganizacional/DiagramaCasosUso.md).


Após a análise dos dados, serão feitas as seguintes etapas:

1. Organização dos elementos identificados em pacotes temáticos.
2. Organização e compreensão das tependências entre os pacotes.
3. Modelagem do diagrama no Draw.io.


## Sobre o Diagrama de Pacotes

O Diagrama de Pacotes a seguir, elaborado com base nos princípios de [Diagrama de Pacotes: Definição, Componentes](https://gitmind.com/pt/diagrama-de-pacotes.html#:~:text=Um%20diagrama%20de%20pacotes%20pode,outros%20campos%20em%20pacotes%20simplificados.) [2](#ref2) e [Diagrama de Pacotes](https://docentes.ifrn.edu.br/diegooliveira/disciplinas/pds/aula-14-diagrama-de-pacotes) [5](#ref5), apresenta a organização arquitetural do sistema em módulos lógicos (Pacotes) e as suas interconexões. Com isso, a estrutura adota uma abordagem em camadas, separando Apresentacao (frontend) do Servidor (backend), o qual é subdividido em pacotes como Aplicacao, Dominio (regras de negócio/entidades), Infraestrutura (detalhes técnicos) e ServicosCompartilhados. Além disso, as Dependências são clarificadas por Estereótipos (<<verbo>>), como <<usar>> ou <<chamar>>, o qual declara a natureza das interações. 

Para melhor compreensão dos diagramas, a figura 1 mostra a legenda;

<div align="center">
    Figura 1: Legenda do Diagrama de Estados
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/refs/heads/main/docs/Modelagem/Imagens/LegendaDiagramaPacote.drawio.png" width="500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

## Elaboração do Diagrama

A estruturação da plataforma "Galáxia Conectada" em uma arquitetura modular e organizada é fundamental para sua compreensão e manutenibilidade, sendo o Diagrama de Pacotes a representação visual dessa organização lógica. Para fornecer um inventário claro e uma descrição detalhada de cada agrupamento funcional e técnico apresentado no referido diagrama, a Tabela 1 subsequente lista cada Pacote, sua Descrição concisa e sua Rastreabilidade com outros artefatos importantes do projeto, como Componentes, Requisitos Funcionais (RFs) ou Classes Chave. Assim, esta tabela serve como um dicionário dos blocos construtivos da visão macro da arquitetura, facilitando o entendimento do papel de cada pacote antes de se analisar suas interdependências.


<details>
  <summary><strong>Tabela 1:  Pacotes do Diagrama</strong></summary>

**Tabela 1:** Pacotes do Diagrama

| Pacote                               | Descrição                                                                                                | Rastreabilidade (Componentes / RFs / Classes Chave)                                                                 |
| :----------------------------------- | :------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------ |
| **`GalaxiaConectada`** | **Pacote raiz que engloba toda a aplicação.** | **Aplicação Completa** |
| `  Apresentacao`                   | Camada responsável pela interface com o usuário (frontend web).                                          | Componente: `WebUI`. Atende RNF01, RNF06.                                                                           |
| `  Servidor`                       | Pacote que agrupa todos os componentes e lógica do backend.                                              | Pacote: `Backend Services`.                                                                                         |
| `    GatewayAPI`                   | Ponto de entrada para requisições da `Apresentacao`, roteia para serviços internos.                      | Componente: `APIGateway`. Suporta indiretamente todos RFs via API.                                                  |
| `    GerenciamentoUsuarios`        | Lógica de autenticação, autorização, gerenciamento de perfis e papéis de usuários.                     | Componente: `GestaoUsuarios`. RFs relacionados a login, perfil, permissões. Classes: `Usuario`, `Perfil`, Papéis. |
| `    Dominio`                      | Contém as entidades, VOs, regras de negócio e interfaces de repositório (lógica central).                | (Conceitual) Corresponde às entidades de negócio das classes.                                                       |
| `      Dominio.Compartilhado`      | Tipos base, interfaces e VOs usados em múltiplos contextos de domínio.                               | -                                                                                                                 |
| `      Dominio.Usuario`            | Entidades e regras de negócio relacionadas ao Usuário, Perfil, Reputação.                               | Classes: `Usuario`, `Perfil`, `Reputacao`.                                                                          |
| `      Dominio.Aprendizagem`      | Entidades e regras de negócio de Trilhas, Módulos, Conteúdos Educacionais, Jogos, Progresso.           | Classes: `TrilhaEducacional`, `Modulo`, `Conteudo`, `Jogo`, `ProgressoUsuarioTrilha`.                               |
| `      Dominio.Comunidade`         | Entidades e regras de negócio do Fórum, Postagens, Comentários, Conquistas.                             | Classes: `Forum`, `Subforum`, `Topico`, `Postagem`, `Comentario`, `Conquista`.                                      |
| `      Dominio.ConteudoInfo`       | Entidades e regras de negócio de Notícias, Artigos (Blog), Eventos, Promoções.                          | Classes: `Noticia`, `Artigo`, `Evento`, `PromocaoExterna`.                                                          |
| `    Aplicacao`                    | Orquestra os casos de uso, coordena interações entre Domínio, Infraestrutura e Serviços.                | (Conceitual) Implementa a lógica dos RFs.                                                                           |
| `      Aplicacao.Usuario`          | Handlers/Serviços para casos de uso de Autenticação, Conta e Perfil.                                   | RFs: Login, Registro, Edição Perfil.                                                                          |
| `      Aplicacao.Aprendizagem`     | Handlers/Serviços para casos de uso de Trilhas, Módulos, Conteúdo, Jogos.                              | RFs: RF01, RF02, RF04, RF05, RF06, RF08, RF16, RF21, RF22.                                                          |
| `      Aplicacao.Comunidade`       | Handlers/Serviços para casos de uso de Fórum, Gamificação, Moderação.                                  | RFs: RF05, RF07, RF09, RF23, RF24, RF25.                                                                            |
| `      Aplicacao.Conteudo`         | Handlers/Serviços para casos de uso de Notícias, Blog, Eventos, Promoções, Submissões.                 | RFs: RF10, RF11, RF13, RF14, RF15, RF18, RF19.                                                                     |
| `      Aplicacao.Integracao`       | Serviços que coordenam a execução dos bots de importação.                                              | RFs: RF14, RF19.                                                                                                    |
| `    ServicosCompartilhados`       | Serviços transversais reutilizáveis por diferentes partes da aplicação.                                  | Componentes: `ServicoNotificacoes`, `ServicoBusca`.                                                          |
| `      Notificacoes`               | Serviço para envio de emails, push notifications.                                                 | Componente: `ServicoNotificacoes`. RF11, RF12, RF20.                                                              |
| `      Busca`                      | Serviço para indexação e consulta de conteúdo na plataforma.                                           | Componente: `ServicoBusca`. RF10.                                                                                 |
| `      Recomendacoes`              | Serviço para gerar recomendações personalizadas.                                                       | Componente: `ServicoRecomendacoes`. RF16.                                                                         |
| `      Certificados`               | Serviço para geração de certificados de conclusão.                                                      | Componente: `ServicoCertificados`. RF04.                                                                          |
| `      Localizacao`                | Serviço para internacionalização e tradução (i18n).                                                    | Componente: `ServicoLocalizacao`. RNF07.                                                                          |
| `      Configuracao`               | Serviço para acesso a configurações da aplicação.                                                      | Componente: `ServicoConfiguracao`.                                                                                  |
| `      Monitoramento`              | Serviço para logging, métricas e tracing.                                                              | Componente: `ServicoMonitoramento`. RNF05.                                                                        |
| `      Cache`                      | Serviço (Interface e/ou Implementação base) para abstração de cache.                                      | Componente: `ServicoCache`. RNF02.                                                                                |
| `    Infraestrutura`               | Camada mais baixa, lida com detalhes técnicos (BD, APIs externas).                               | Componente: `BancoDeDados`, Clientes HTTP.                                                                     |
| `      Persistencia`               | Implementação do acesso a dados (Repositórios, ORM).                                                   | Componente: `BancoDeDados` (conceitual). RNF04.                                                                     |
| `      ClientesExternos`           | Implementação de clientes para consumir APIs/fontes externas (Notícias, Promoções, Email).        | Componentes: `FonteExternaNoticias`, `FonteExternaPromocoes`.                                                       |
| `      Cache (Impl)`               | Implementação concreta do serviço de cache (Ex: Adaptador Redis).                                      | RNF02.                                                                                                            |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>

Enquanto a Tabela 1 define os pacotes individualmente, a Tabela 2, a seguir, foca em elucidar as interconexões e os relacionamentos de dependência entre eles, conforme representados pelas setas no Diagrama de Pacotes. Reconhecendo que um diagrama com múltiplos pacotes e suas respectivas interações pode, por vezes, apresentar uma complexidade visual onde linhas de dependência se cruzam, esta tabela é crucial para a correta interpretação: ela detalha cada Pacote Dependente que qualifica a natureza da relação (como <<usar>> ou <<chamar>>), o Pacote Fornecedor (Destino) e uma Justificativa / Explicação para tal vínculo. Desta forma, a Tabela 2 funciona como um guia textual preciso e complementar à visualização gráfica.

<details>
  <summary><strong>Tabela 2: Dependências dos Pacotes</strong></summary>

**Tabela 2:** Dependências dos Pacotes

| Pacote Dependente (Cliente)                  | Estereótipo (Verbo)    | Pacote Fornecedor (Destino)                | Justificativa / Explicação                                                                                                                                |
| :------------------------------------------- | :--------------------- | :----------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `GalaxiaConectada.Apresentacao`              | `<<chamar>>`           | `Servidor.GatewayAPI`                      | Interface do usuário envia requisições para a API Gateway.                                                                                                |
| `GalaxiaConectada.Apresentacao`              | `<<obterTextoDe>>`     | `Servidor.ServicosCompartilhados.Localizacao` | (Conceitual via API) Interface busca textos traduzidos para exibir.                                                                                       |
| `Servidor.GatewayAPI`                        | `<<rotearPara>>`       | `Servidor.Aplicacao.Usuario`               | Roteia requisições de login, perfil.                                                                                                                 |
| `Servidor.GatewayAPI`                        | `<<rotearPara>>`       | `Servidor.Aplicacao.Aprendizagem`          | Roteia requisições de trilhas, jogos.                                                                                                                |
| `Servidor.GatewayAPI`                        | `<<rotearPara>>`       | `Servidor.Aplicacao.Comunidade`            | Roteia requisições de fórum, gamificação.                                                                                                            |
| `Servidor.GatewayAPI`                        | `<<rotearPara>>`       | `Servidor.Aplicacao.Conteudo`              | Roteia requisições de notícias, eventos.                                                                                                             |
| `Servidor.GatewayAPI`                        | `<<usar>>`             | `Servidor.GerenciamentoUsuarios`           | Pode necessitar verificar autenticação/autorização básica na borda.                                                                                         |
| `Servidor.GatewayAPI`                        | `<<usar>>`             | `Servidor.ServicosCompartilhados.Busca`      | Pode oferecer um endpoint de busca unificado que usa o serviço de busca.                                                                                  |
| `Servidor.GatewayAPI`                        | `<<usar>>`             | `Servidor.ServicosCompartilhados.Monitoramento` | Registra logs e métricas das requisições na entrada.                                                                                                      |
| `Servidor.GatewayAPI`                        | `<<usar>>`             | `Servidor.ServicosCompartilhados.Cache`      | Pode implementar cache de respostas da API.                                                                                                             |
| `Servidor.GerenciamentoUsuarios`             | `<<manipular>>`        | `Servidor.Dominio.Usuario`                 | Contém lógica para criar/atualizar/validar entidades de Usuário/Perfil.                                                                                   |
| `Servidor.GerenciamentoUsuarios`             | `<<usar>>`             | `Servidor.Infraestrutura.Persistencia`     | Salva e carrega dados de usuário/perfil/papéis do banco de dados.                                                                                         |
| `Servidor.GerenciamentoUsuarios`             | `<<ler>>`              | `Servidor.ServicosCompartilhados.Configuracao` | Lê configurações relacionadas a usuários (ex: regras de senha).                                                                                           |
| `Servidor.GerenciamentoUsuarios`             | `<<reportarPara>>`     | `Servidor.ServicosCompartilhados.Monitoramento` | Registra eventos de login, falhas, criação de usuário.                                                                                               |
| `Servidor.Dominio.Usuario`                 | `<<usar>>`             | `Servidor.Dominio.Compartilhado`           | Utiliza tipos base, IDs, VOs, interfaces comuns definidos no pacote compartilhado.                                                                        |
| `Servidor.Dominio.Aprendizagem`            | `<<usar>>`             | `Servidor.Dominio.Compartilhado`           | Utiliza tipos base, IDs, VOs, interfaces comuns definidos no pacote compartilhado.                                                                        |
| `Servidor.Dominio.Aprendizagem`            | `<<referenciar>>`      | `Servidor.Dominio.Usuario`                 | Pode referenciar o Usuário (Aluno) associado a um Progresso.                                                                                              |
| `Servidor.Dominio.Comunidade`              | `<<usar>>`             | `Servidor.Dominio.Compartilhado`           | Utiliza tipos base, IDs, VOs, interfaces comuns definidos no pacote compartilhado.                                                                        |
| `Servidor.Dominio.Comunidade`              | `<<referenciar>>`      | `Servidor.Dominio.Usuario`                 | Referencia o Usuário autor de Postagens, Comentários, ou quem ganhou Conquistas.                                                                          |
| `Servidor.Dominio.ConteudoInfo`            | `<<usar>>`             | `Servidor.Dominio.Compartilhado`           | Utiliza tipos base, IDs, VOs, interfaces comuns definidos no pacote compartilhado.                                                                        |
| `Servidor.Dominio.ConteudoInfo`            | `<<referenciar>>`      | `Servidor.Dominio.Usuario`                 | Pode referenciar o Usuário autor de um Artigo.                                                                                                            |
| `Servidor.Aplicacao.Usuario`               | `<<usar>>`             | `Servidor.Dominio.Usuario`                 | Manipula entidades de Usuário/Perfil para executar casos de uso.                                                                                          |
| `Servidor.Aplicacao.Usuario`               | `<<orquestrarCom>>`    | `Servidor.GerenciamentoUsuarios`           | Coordena a lógica específica de autenticação/gerenciamento de conta.                                                                                     |
| `Servidor.Aplicacao.Usuario`               | `<<usar>>`             | `Servidor.Infraestrutura.Persistencia`     | Utiliza repositórios para carregar/salvar dados necessários aos casos de uso.                                                                             |
| `Servidor.Aplicacao.Usuario`               | `<<usar>>`             | `Servidor.ServicosCompartilhados.Notificacoes` | Envia notificações (ex: email de confirmação, senha recuperada).                                                                                         |
| `Servidor.Aplicacao.Usuario`               | `<<reportarPara>>`     | `Servidor.ServicosCompartilhados.Monitoramento` | Loga eventos de aplicação relacionados a usuários.                                                                                                        |
| `Servidor.Aplicacao.Aprendizagem`          | `<<usar>>`             | `Servidor.Dominio.Aprendizagem`           | Manipula entidades de Trilha, Módulo, Jogo, Progresso.                                                                                                    |
| `Servidor.Aplicacao.Aprendizagem`          | `<<usar>>`             | `Servidor.Dominio.Usuario`                 | Associa progresso ao usuário correto.                                                                                                                     |
| `Servidor.Aplicacao.Aprendizagem`          | `<<notificar>>`/`<<chamar>>` | `Servidor.Aplicacao.Comunidade`          | Informa a Gamificação sobre eventos relevantes (módulo concluído, jogo finalizado).                                                                       |
| `Servidor.Aplicacao.Aprendizagem`          | `<<consultar>>`        | `Servidor.GerenciamentoUsuarios`           | Pode verificar permissões ou obter dados básicos do usuário.                                                                                              |
| `Servidor.Aplicacao.Aprendizagem`          | `<<usar>>`             | `Servidor.ServicosCompartilhados.Notificacoes` | Notifica sobre conclusão de trilha, certificados.                                                                                                         |
| `Servidor.Aplicacao.Aprendizagem`          | `<<usar>>`             | `Servidor.ServicosCompartilhados.Certificados` | Solicita a geração de certificados.                                                                                                                       |
| `Servidor.Aplicacao.Aprendizagem`          | `<<usar>>`             | `Servidor.Infraestrutura.Persistencia`     | Salva progresso, carrega trilhas.                                                                                                                    |
| `Servidor.Aplicacao.Aprendizagem`          | `<<reportarPara>>`     | `Servidor.ServicosCompartilhados.Monitoramento` | Loga eventos de aplicação relacionados à aprendizagem.                                                                                                    |
| `Servidor.Aplicacao.Comunidade`            | `<<usar>>`             | `Servidor.Dominio.Comunidade`              | Manipula entidades de Fórum, Gamificação, Moderação.                                                                                                      |
| `Servidor.Aplicacao.Comunidade`            | `<<usar>>`             | `Servidor.Dominio.Usuario`                 | Associa posts/comentários/conquistas a usuários.                                                                                                          |
| `Servidor.Aplicacao.Comunidade`            | `<<consultar>>`        | `Servidor.GerenciamentoUsuarios`           | Verifica permissões para postar, moderar.                                                                                                                 |
| `Servidor.Aplicacao.Comunidade`            | `<<usar>>`             | `Servidor.ServicosCompartilhados.Notificacoes` | Notifica sobre novas respostas, denúncias.                                                                                                           |
| `Servidor.Aplicacao.Comunidade`            | `<<usar>>`             | `Servidor.Infraestrutura.Persistencia`     | Salva/carrega tópicos, posts, comentários, pontos, conquistas.                                                                                            |
| `Servidor.Aplicacao.Comunidade`            | `<<reportarPara>>`     | `Servidor.ServicosCompartilhados.Monitoramento` | Loga eventos de aplicação relacionados à comunidade.                                                                                                      |
| `Servidor.Aplicacao.Conteudo`              | `<<usar>>`             | `Servidor.Dominio.ConteudoInfo`            | Manipula entidades de Notícia, Artigo, Evento, Promoção.                                                                                                  |
| `Servidor.Aplicacao.Conteudo`              | `<<usar>>`             | `Servidor.Dominio.Usuario`                 | Associa artigos a autores, favoritos a usuários.                                                                                                          |
| `Servidor.Aplicacao.Conteudo`              | `<<usar>>`             | `Servidor.Infraestrutura.Persistencia`     | Salva/carrega notícias, artigos, eventos, promoções, favoritos.                                                                                           |
| `Servidor.Aplicacao.Conteudo`              | `<<usar>>`             | `Servidor.ServicosCompartilhados.Busca`      | Solicita indexação de novo conteúdo informativo.                                                                                                          |
| `Servidor.Aplicacao.Conteudo`              | `<<reportarPara>>`     | `Servidor.ServicosCompartilhados.Monitoramento` | Loga eventos de aplicação relacionados a conteúdo.                                                                                                        |
| `Servidor.Aplicacao.Integracao`            | `<<registrar>>`        | `Servidor.Aplicacao.Conteudo`              | Chama os serviços de aplicação de conteúdo para salvar itens importados.                                                                                  |
| `Servidor.Aplicacao.Integracao`            | `<<usar>>`             | `Servidor.Infraestrutura.ClientesExternos` | Usa os clientes HTTP/Scrapers para buscar dados externos.                                                                                                 |
| `Servidor.Aplicacao.Integracao`            | `<<ler>>`              | `Servidor.ServicosCompartilhados.Configuracao` | Lê configurações dos bots (URLs de fontes, frequência).                                                                                                   |
| `Servidor.Aplicacao.Integracao`            | `<<usar>>`             | `Servidor.Infraestrutura.Persistencia`     | Pode logar o status da importação ou gerenciar o estado dos bots.                                                                                         |
| `Servidor.Aplicacao.Integracao`            | `<<reportarPara>>`     | `Servidor.ServicosCompartilhados.Monitoramento` | Loga eventos de execução dos bots.                                                                                                                        |
| `Servidor.ServicosCompartilhados.Notificacoes` | `<<obterTextoDe>>`   | `Servidor.ServicosCompartilhados.Localizacao`| Obtém textos traduzidos para as notificações.                                                                                                             |
| `Servidor.ServicosCompartilhados.Notificacoes` | `<<ler>>`            | `Servidor.ServicosCompartilhados.Configuracao` | Lê configurações de envio (chaves de API de email/push).                                                                                                |
| `Servidor.ServicosCompartilhados.Notificacoes` | `<<enviarVia>>`      | `Servidor.Infraestrutura.ClientesExternos`   | Usa os clientes implementados para enviar emails ou pushes.                                                                                             |
| `Servidor.ServicosCompartilhados.Notificacoes` | `<<reportarPara>>`   | `Servidor.ServicosCompartilhados.Monitoramento` | Loga envios de notificação.                                                                                                                               |
| `Servidor.ServicosCompartilhados.Busca`      | `<<acessarDadosDe>>` | `Servidor.Infraestrutura.Persistencia`     | Acessa o banco de dados ou um índice de busca mantido pela persistência.                                                                                  |
| `Servidor.ServicosCompartilhados.Busca`      | `<<ler>>`            | `Servidor.ServicosCompartilhados.Configuracao` | Lê configurações do serviço de busca.                                                                                                                     |
| `Servidor.ServicosCompartilhados.Busca`      | `<<reportarPara>>`   | `Servidor.ServicosCompartilhados.Monitoramento` | Loga consultas e indexações.                                                                                                                              |
| `Servidor.ServicosCompartilhados.Recomendacoes` | `<<lerDadosPara>>` | `Servidor.Infraestrutura.Persistencia`     | Lê dados de perfil, progresso, conteúdo para gerar recomendações.                                                                                         |
| `Servidor.ServicosCompartilhados.Recomendacoes` | `<<ler>>`          | `Servidor.ServicosCompartilhados.Configuracao` | Lê parâmetros dos algoritmos de recomendação.                                                                                                             |
| `Servidor.ServicosCompartilhados.Recomendacoes` | `<<usar>>`         | `Servidor.Dominio.*`                         | Entende as entidades de domínio para poder recomendá-las.                                                                                                 |
| `Servidor.ServicosCompartilhados.Recomendacoes` | `<<reportarPara>>` | `Servidor.ServicosCompartilhados.Monitoramento` | Loga geração de recomendações.                                                                                                                            |
| `Servidor.ServicosCompartilhados.Certificados` | `<<lerDadosPara>>` | `Servidor.Infraestrutura.Persistencia`     | Busca dados do usuário e da trilha concluída para gerar o certificado.                                                                                  |
| `Servidor.ServicosCompartilhados.Certificados` | `<<usar>>`         | `Servidor.Dominio.Usuario`                 | Usa dados da entidade Usuário.                                                                                                                            |
| `Servidor.ServicosCompartilhados.Certificados` | `<<usar>>`         | `Servidor.Dominio.Aprendizagem`            | Usa dados da entidade TrilhaEducacional.                                                                                                                |
| `Servidor.ServicosCompartilhados.Certificados` | `<<reportarPara>>` | `Servidor.ServicosCompartilhados.Monitoramento` | Loga geração de certificados.                                                                                                                            |
| `Servidor.ServicosCompartilhados.Localizacao` | `<<lerRecursoDe>>` | `Servidor.Infraestrutura.Persistencia`     | Lê textos/traduções do banco de dados (ou sistema de arquivos).                                                                                           |
| `Servidor.ServicosCompartilhados.Localizacao` | `<<ler>>`          | `Servidor.ServicosCompartilhados.Configuracao` | Lê configurações de idioma (padrão, suportados).                                                                                                        |
| `Servidor.ServicosCompartilhados.Configuracao`| `<<lerDe>>`        | `Servidor.Infraestrutura.Persistencia`     | Pode ler configurações armazenadas no banco de dados.                                                                                                     |
| `Servidor.ServicosCompartilhados.Monitoramento`| `<<ler>>`          | `Servidor.ServicosCompartilhados.Configuracao` | Lê configurações de monitoramento (nível de log, endpoint externo).                                                                                       |
| `Servidor.ServicosCompartilhados.Monitoramento`| `<<enviarPara>>`   | `Servidor.Infraestrutura.ClientesExternos`   | Envia dados para ferramentas externas de monitoramento.                                                                                                   |
| `Servidor.Infraestrutura.Persistencia`      | `<<implementar>>`    | `Servidor.Dominio.*`                         | Implementa interfaces de repositório definidas no domínio; manipula/mapeia entidades do domínio.                                                        |
| `Servidor.Infraestrutura.Persistencia`      | `<<ler>>`            | `Servidor.ServicosCompartilhados.Configuracao` | Lê strings de conexão e outras configurações de persistência.                                                                                             |
| `Servidor.Infraestrutura.Persistencia`      | `<<reportarPara>>`   | `Servidor.ServicosCompartilhados.Monitoramento` | Loga queries de banco de dados, erros de persistência.                                                                                                    |
| `Servidor.Infraestrutura.ClientesExternos`  | `<<ler>>`            | `Servidor.ServicosCompartilhados.Configuracao` | Lê URLs, chaves de API para serviços externos.                                                                                                            |
| `Servidor.Infraestrutura.ClientesExternos`  | `<<reportarPara>>`   | `Servidor.ServicosCompartilhados.Monitoramento` | Loga chamadas a APIs externas, erros de comunicação.                                                                                                      |
| `Servidor.Infraestrutura.Cache`             | `<<implementar>>`    | `Servidor.ServicosCompartilhados.Cache`      | Implementa a interface de cache definida nos serviços compartilhados.                                                                                   |
| `Servidor.Infraestrutura.Cache`             | `<<ler>>`            | `Servidor.ServicosCompartilhados.Configuracao` | Lê configurações do servidor de cache (endereço, porta).                                                                                                  |
| `Servidor.Infraestrutura.Cache`             | `<<reportarPara>>`   | `Servidor.ServicosCompartilhados.Monitoramento` | Loga operações de cache (hit, miss, erros).                                                                                                             |
| `Servidor.Infraestrutura.Mensageria`        | `<<implementar>>`    | `Servidor.Aplicacao.*` ou `Dominio.*`      | Implementa interfaces para publicação/consumo de eventos/mensagens.                                                                                       |
| `Servidor.Infraestrutura.Mensageria`        | `<<ler>>`            | `Servidor.ServicosCompartilhados.Configuracao` | Lê configurações do broker de mensagens.                                                                                                                  |
| `Servidor.Infraestrutura.Mensageria`        | `<<reportarPara>>`   | `Servidor.ServicosCompartilhados.Monitoramento` | Loga publicação e consumo de mensagens.                                                                                                                 |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>

## Diagrama de Pacotes

**Observação:** Para visualizar a imagem em mamior definição, clique nela.

A Figura 2 mostra o diagrama de pacotes da Galáxia Conectada

<div align="center">
    <b>Figura 2:</b> o Diagrama de Pacotes
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaPacotes001.drawio.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
</div>

<p><strong>Observação:</strong> Caso deseje visualizar ou baixar em PDF, clique aqui: 
<a href="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaPacotes.drawio.pdf">PDF do Diagrama de Pacotes</a></p>

### Diagrama Simplificado

Para complementar a visão detalhada e oferecer uma compreensão mais rápida da estrutura de alto nível, apresenta-se também um Diagrama de Pacotes simplificado. Esta versão foca nos principais agrupamentos lógicos (como as camadas Apresentacao, Servidor, e os subsistemas principais dentro do backend) e nas dependências mais críticas.

**Observação:** Para visualizar a imagem em mamior definição, clique nela.

<div align="center">
    <b>Figura 3:</b> o Diagrama de Pacotes - Simplificado
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaPacotesSimplificado.drawio.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
</div>

<p><strong>Observação:</strong> Caso deseje visualizar ou baixar em PDF, clique aqui: 
<a href="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaPacotesSimplificado.drawio.pdf">PDF do Diagrama de Pacotes - Simplificado</a></p>


## Conclusão

Em suma, o Diagrama de Pacotes detalhado oferece um mapa estruturado da arquitetura lógica da plataforma "Galáxia Conectada". Desse modo, a organização modular em pacotes com responsabilidades bem definidas, como Apresentacao, Aplicacao, Dominio e Infraestrutura, juntamente com a visualização explícita das dependências entre eles é fundamental para gerenciar a complexidade do sistema. Essa abordagem facilita a compreensão da estrutura geral e a localização de funcionalidades como também promove um guia essencial para o desenvolvimento e a evolução coesa do código-fonte.

## Bibliografia

<a name="ref1"></a>
[1] APOSTILA UML. Seção sobre representação de Pacotes. Disponibilizada pela professora. Acesso em: 5 maio 2025.

<a name="ref2"></a>
[2] Diagrama de Pacotes: Definição, Componentes e Exemplos. Disponível em: https://gitmind.com/pt/diagrama-de-pacotes.html. Acesso em: 5 maio 2025.

<a name="ref3"></a>
[3] LUCIDCHART. Tudo sobre diagramas de pacotes UML. Disponível em: https://www.lucidchart.com/pages/pt/diagrama-de-pacotes-uml. Acesso em: 5 maio 2025.

<a name="ref4"></a>
[4] VISUAL PARADIGM. What is Package Diagram? Disponível em: https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-package-diagram/. Acesso em: 5 maio 2025.

<a name="ref5"></a>
[5] OLIVEIRA, Diego. Projeto de Desenvolvimento de Software – Aula 14: Diagrama de Pacotes. Disponível em: https://docentes.ifrn.edu.br/diegooliveira/disciplinas/pds/aula-14-diagrama-de-pacotes. Acesso em: 5 maio 2025.



## Histórico de versão


| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 05/05/2024 |
| 1.1 | Adição da metodologia | Larissa Stéfane | 05/05/2024 |
| 1.2 | Criação da Tabela de Pacotes | Larissa Stéfane | 05/05/2024 |
| 1.3 | Reorganização da Tabela de Pacotes | Larissa Stéfane | 05/05/2024 |
| 1.4 | Adição de elementos na  Tabela de Pacotes | Larissa Stéfane | 05/05/2024 |
| 1.5 | Adição de elementos na  Tabela de Pacotes | Larissa Stéfane | 06/05/2024 |
| 1.5 | Adição de elementos na  Tabela de Pacotes | Larissa Stéfane | 06/05/2024 |
| 1.6 | Reorganização da Tabela de Pacotes | Larissa Stéfane | 06/05/2024 |
| 1.7 | Criação da Tabela de dependências | Larissa Stéfane | 06/05/2024 |
| 1.8 | Reorganização da taela de dependências | Larissa Stéfane | 06/05/2024 |
| 1.9 | Adição das figuras| Larissa Stéfane | 06/05/2024 |
| 2.0 | Ajustes no artefato| Larissa Stéfane | 06/05/2024 |
