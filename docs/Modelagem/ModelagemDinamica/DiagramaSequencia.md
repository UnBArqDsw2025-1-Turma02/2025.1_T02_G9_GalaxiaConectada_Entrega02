# Diagrama de Sequência

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Sobre o Diagrama de Sequência](#Sobre-o-Diagrama-de-Sequência)
- [Aba Conhecimento Trilhas de Aprendizado](#Aba-Conhecimento-Trilhas-de-Aprendizado)
- [Aba Promoções](#Aba-=Promoções)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)


## Introdução

Ao se desenvolver diagramas de sequência, é essencial compreender que eles representam uma das formas de modelar o comportamento dinâmico de um sistema. Sendo assim, de acordo com a Apostila UML - Unified Modeling Language - Linguagem de Modelagem Unificada em Português [1](#ref1), esse tipo de diagrama descreve, de maneira visual e cronológica, a troca de mensagens entre diferentes objetos envolvidos em uma interação, no caso deste documento, sobre **a aba de trilhas de aprendizado** e da **aba de promoções**. Assim, um ponto importanto sobre a estrutura básica do diagrama de sequência é composta por dois eixos: o eixo vertical, que representa o tempo (de cima para baixo), e o eixo horizontal, que representa os objetos envolvidos, cada um com sua respectiva linha de vida, como é descrito em [IBM - Diagramas de Sequência](https://www.ibm.com/docs/pt-br/rsm/7.5.0?topic=uml-sequence-diagrams) [3](#ref3).

Para o projeto Galáxia Conectada, a elaboração dos diagramas de sequência será baseada nas interações pensadas previamente nos diagramas de classes e de componentes,com o intuito de garantir uma coerência com a estrutura lógica e modular da aplicação. 


## Objetivos

O objetivo deste documento é apresentar dois diagramas de sequência que representam duas das interações fundamentais na plataforma Galáxia Conectada. Com isso, a partir desses diagramas, busca-se:

  - Modelar visualmente os fluxos de mensagens entre os objetos do sistema e os usuários;

  - Especificar a ordem das interações e responsabilidades envolvidas em dois dos módulos principais da plataforma;

  - Ilustrar o comportamento interno da aplicação durante a execução de casos de uso específicos;

  - Apoiar o entendimento do fluxo dinâmico e temporal das funcionalidades com base nas mensagens trocadas.

De forma mais específica, os diagramas desenvolvidos visam representar os seguintes cenários:

1. **Aba Conhecimento: Trilha de aprendizado**: A navegação e o progresso do usuário em uma trilha de aprendizado ;

2. **Aba Promoções:** A navegação do usuário na aba de promoções.

## Metodologia 

A elaboração dos diagramas de sequência seguirá uma abordagem iterativa, com base em alguns dos artefatos previamente construídos no desenvolvimento da plataforma Galáxia Conectada. Com base nisso, o processo adotado visa observar o comportamento do sistema por meio da representação temporal das interações. 

Os módulos trabalhados são:

- **Aba Conhecimento: Trilhas de Aprendizado**: A aba "Conhecimento: Trilhas de Aprendizado" é o coração educacional da plataforma "Galáxia Conectada", onde os usuários encontram jornadas de estudo sobre astronomia, organizadas de forma lógica por temas, níveis de dificuldade e categorias específicas.

- **Aba de Promoções**: A "Aba de Promoções" na "Galáxia Conectada" serve como um hub para a comunidade de entusiastas encontrarem ofertas e descontos em produtos e serviços relacionados à astronomia, como telescópios, livros, cursos externos ou acessórios.



Para isso, foram realizadas as seguintes etapas:

1. Análise dos seguintes artefatos de apoio ao entendimento comportamental:

  - Fluxo do [protótipo de alta fidelidade](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/DesignSprint/Prototipo);
  - [Diagrama de Classes](/Modelagem/ModelagemEstatica/DiagramaClasses.md);
  - [Diagrama de Componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md)

2. Após a análise. serão contriídos dois diagramas de sequência na ferramenta Draw.io. 
3. Por fim, será aplicada uma verificação por meio de [checklist](/Modelagem/IniciativasExtras/Verificacao/VerificacaoDiagramaSequencia.md) com critérios de consistência, completude e conformidade com a UML.


## Sobre o Diagrama de Sequência

Como foi mencionado na introdução, o diagrama de sequência é uma ferramenta da UML utilizada para representar a interação entre objetos ao longo do tempo durante a execução de um processo específico do sistema. Assim, os elementos e componentes da "linha da vida" serão feitos apartir dos componentes do [diagrama de componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md). 

Com base nisso, o diagrama de sequência é composto por diversos elementos fundamentais que permitem representar de forma clara a comunicação entre os objetos de um sistema. Assim, com base em [O que é um diagrama de sequência UML?](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml) [4](#ref4), os atores e objetos participantes são dispostos horizontalmente, cada um com uma linha de vida vertical que indica sua existência ao longo do tempo. As mensagens trocadas entre eles são representadas por setas horizontais, podendo ser síncronas, assíncronas ou de retorno, com ou sem rótulos descritivos.

Para melhor compreensão dos elementos, a figura 1 abaixo funciona como uma legenda para os diagramas elaborados.

<div align="center">
    Figura 1: Legenda do Diagrama de Sequência
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/refs/heads/main/docs/Modelagem/Imagens/LegendaDiagramaSequ%C3%AAncia.drawio.png" width="500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

## Aba Conhecimento Trilhas de Aprendizado

**Cenário:** Usuário logado acessa trilhas, navega até um módulo, interage com o conteúdo e marca o módulo como concluído, acionando a lógica de progresso e gamificação.

A tabela 1 mostra os elementos e as sequências no diagrama em relação às trilhas de aprendizado.

<details>
  <summary><strong>Tabela 1:  Sequência das trilhas de aprendizado</strong></summary>

**Tabela 1: Sequência das trilhas de aprendizado** 

| Elemento do Diagrama de Sequência          | Descrição na Sequência                                                                 | Relação com Diagrama de Classes                                                                                                                                                                                                                                                                                                                                   | Relação com Requisitos (RFs)                     | Relação com Diagrama de Componentes                                                                                                                                                                                                                                                                                                |
| :----------------------------------------- | :------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Lifelines / Participantes** |                                                                                        |                                                                                                                                                                                                                                                                                                                                                                           |                                                  |                                                                                                                                                                                                                                                                                                                                               |
| `Entusiasta` (Ator)                        | O usuário final interagindo com a plataforma.                                          | Representa uma instância de `Usuario` (provavelmente com papel `Aluno`).                                                                                                                                                                                                                                                                                           | (Geral) Todos os RFs que envolvem interação.   | (Externo) Interage com `WebUI`.                                                                                                                                                                                                                                                                                               |
| `:WebUI`                                   | A interface do usuário no navegador, renderiza informações e captura ações.            | (Implementação) Classes/frameworks de frontend. Interage via API.                                                                                                                                                                                                                                                                                                         | RF01, RF02, RF03, RF04, RF06, RF23. RNF01, RNF06. | Componente `WebUI`. Requer `IAPIGeral`, `IAssetDelivery`, `ILocalizacao`.                                                                                                                                                                                                                                                             |
| `:APIGateway`                              | Ponto de entrada para as requisições do backend, roteia para os serviços apropriados. | (Implementação) Framework de API Gateway. Orquestra chamadas.                                                                                                                                                                                                                                                                                                        | (Indireto) Suporta RFs do backend. RNF02, RNF05. | Componente `APIGateway`. Provê `IAPIGeral`. Requer interfaces dos módulos (`IAutenticacao`, `IAcessoConteudo`, etc.), `IConfiguracao`, `IMonitoramento`, `IBusca`, `ICache` (Opcional).                                                                                                                                            |
| `:ModuloEducacional`                       | Responsável pela lógica de trilhas, módulos, conteúdos e progresso.                    | Classes: `TrilhaEducacional`, `Modulo`, `Conteudo` (e subclasses), `ProgressoUsuarioTrilha`. Métodos: `listar...`, `registrarConclusaoModulo`. Relacionamentos: Composição `Trilha`-`Modulo`, Agregação `Modulo`-`Conteudo`, Associação `Usuario`-`Progresso`-`Trilha`.                                                                                        | RF01, RF02, RF03, RF04.                           | Componente `ModuloEducacional` (`Conteudo Interativo`). Provê `IGestaoCursos`, `IAcessoConteudo`, `IProgressoTrilha`. Requer `IGamificacao`, `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento`, `IGestaoCertificados`.                                                                                           |
| `:ModuloGamificacao`                       | Responsável por calcular e atualizar XP, níveis, conquistas e reputação.               | Classes: `Perfil` (XP, Nível), `Reputacao`, `Conquista`, `UsuarioConquista`. Métodos: `registrarAcao` (inf.), `processarAcao...` (inf.), `adicionarXP`, `verificarConquistas`. Relacionamentos: Composição `Usuario`-`Perfil`/`Reputacao`, Associação `Usuario`-`UsuarioConquista`-`Conquista`.                                                                   | RF05, RF07, RF23.                                | Componente `ModuloGamificacao` (`Comunidade`). Provê `IGamificacao`. Requer `IPerfilUsuario`, `IPersistencia`, `IConfiguracao`, `IMonitoramento`.                                                                                                                                                                               |
| `:BancoDeDados`                            | Armazena os dados persistentes da aplicação.                                           | Todas as classes persistentes (`Usuario`, `Trilha`, `Modulo`, `Conteudo`, `Progresso`, `Conquista`, etc.) e seus relacionamentos mapeados para o schema.                                                                                                                                                                                                         | RF04, RF05, RF07, RF09, etc. RNF04.              | Componente `BancoDeDados`. Provê `IPersistencia` (implícita). Depende do `<<artifact>> schema.sql`.                                                                                                                                                                                                                                  |
| *(Opcional)* `:ServicoNotificacoes`        | Envia notificações (ex: conquista desbloqueada).                                       | Classe: `Notificacao`. Métodos: `enviarNotificacao` (inf.).                                                                                                                                                                                                                                                                                                     | RF12.                                            | Componente `ServicoNotificacoes`. Provê `INotificacoes`. Requer `IPerfilUsuario`, `IConfiguracao`, APIs Externas, `ILocalizacao`.                                                                                                                                                                                                  |
| **Mensagens / Interações Chave** |                                                                                        |                                                                                                                                                                                                                                                                                                                                                                           |                                                  |                                                                                                                                                                                                                                                                                                                                               |
| `1: clicarAbaTrilhas()` ... `7: ...`        | Usuário acessa área de trilhas, UI busca e exibe categorias.                           | Métodos `listarCategoriasTrilhas` (`ModuloEducacional`), `buscarCategorias` (BD).                                                                                                                                                                                                                                                                                        | RF01.                                            | `WebUI`->`IAPIGeral`, `APIGateway`->Interface `ModuloEducacional`, `ModuloEducacional`->`IPersistencia`.                                                                                                                                                                                                                          |
| `8: selecionarCategoria(...)` ... `14: ...` | Usuário seleciona categoria, UI busca e exibe trilhas.                               | Métodos `listarTrilhasPorCategoria` (`ModuloEducacional`), `buscarTrilhas` (BD).                                                                                                                                                                                                                                                                                   | RF01.                                            | Similar ao anterior.                                                                                                                                                                                                                                                                                                          |
| `15: selecionarTrilha(...)` ... `23: ...`   | Usuário seleciona trilha, UI busca e exibe módulos e progresso.                      | Métodos `listarModulosTrilha`, `buscarModulos`, `buscarProgressoUsuarioTrilha` (`ModuloEducacional`, BD). Classe `ProgressoUsuarioTrilha`.                                                                                                                                                                                                                       | RF01, RF04.                                      | Similar, envolve consulta `ProgressoUsuarioTrilha`.                                                                                                                                                                                                                                                                 |
| `24: selecionarModulo(...)` ... `30: ...`   | Usuário seleciona módulo, UI busca e exibe conteúdos.                                | Métodos `listarConteudosModulo`, `buscarConteudos` (`ModuloEducacional`, BD). Classe `Conteudo` e subclasses.                                                                                                                                                                                                                                                      | RF02.                                            | Similar, focado em `Conteudo`.                                                                                                                                                                                                                                                                                |
| `32: clicarMarcarConcluido()` ... `39: ...` | Usuário marca módulo concluído, sistema atualiza progresso e dispara gamificação.    | Métodos `registrarConclusaoModulo` (`ModuloEducacional`), `atualizarProgressoTrilha` (BD), `registrarAcao` (`ModuloGamificacao` - async). Classe `ProgressoUsuarioTrilha`.                                                                                                                                                                                       | RF04, RF05.                                      | `ModuloEducacional` requer `IPersistencia` e `IGamificacao` (chamada async).                                                                                                                                                                                                                                                 |
| `40: processarAcao...(...)` ... `46: ...`   | Gamificação processa conclusão, atualiza XP e verifica conquistas.                   | Métodos `adicionarXp`, `verificarConquistas` (`ModuloGamificacao`, BD). Classes `Perfil`, `Conquista`, `UsuarioConquista`.                                                                                                                                                                                                                                           | RF05, RF07, RF23.                                | `ModuloGamificacao` requer `IPersistencia`.                                                                                                                                                                                                                                                                           |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>


Com base na tabela 1, abaixo, na figura 2, há o diagrama de Sequência - Trilhas de Aprendizado


<div align="center">
    Figura 2: o Diagrama de Sequência - Trilhas de Aprendizado
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/refs/heads/main/docs/Modelagem/Imagens/DiagramaSequenciaConhecimento.png">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>



## Aba Promoções

**Cenário:** Usuário logado visualiza a lista de promoções (capturadas externamente por bots) e marca uma delas como favorita.

A tabela 2 mostra os elementos e as sequências no diagrama em relação às promoções.

<details>
  <summary><strong>Tabela 2: Sequência das promoções</strong></summary>


**Tabela 2: Sequência das promoções** 


| Elemento do Diagrama de Sequência             | Descrição na Sequência                                                         | Relação com Diagrama de Classes                                                                                                                                                            | Relação com Requisitos (RFs)               | Relação com Diagrama de Componentes                                                                                                                                                              |
| :-------------------------------------------- | :----------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Lifelines / Participantes** |                                                                                |                                                                                                                                                                                            |                                            |                                                                                                                                                                                                  |
| `Entusiasta` (Ator)                           | O usuário final interagindo com a plataforma.                                  | Instância de `Usuario`.                                                                                                                                                                    | (Geral) Interação do usuário.            | (Externo) Interage com `WebUI`.                                                                                                                                                                |
| `:WebUI`                                      | Interface do usuário que exibe as promoções e permite favoritá-las.            | (Implementação) Classes/frameworks de frontend.                                                                                                                                            | RF19 (Exibir). RNF01, RNF06.               | Componente `WebUI`. Requer `IAPIGeral`.                                                                                                                                                        |
| `:APIGateway`                                 | Recebe as requisições da UI e as direciona para o Módulo de Promoções.         | (Implementação) Framework de API Gateway.                                                                                                                                                  | (Indireto) Suporta RF19. RNF02, RNF05.     | Componente `APIGateway`. Provê `IAPIGeral`. Requer interface do `ModuloPromocoes`, `IConfiguracao`, `IMonitoramento`.                                                                         |
| `:ModuloPromocoes`                            | Gerencia a lógica de listagem e favoritamento de promoções externas.           | Classe `PromocaoExterna`. Métodos: `listarPromocoesAtivas`, `salvarPromocaoFavorita` (inf.). Relação `PromocaoExterna`-`FontePromocaoExterna`. Possível classe associativa para favoritos. | RF19.                                      | Componente `ModuloPromocoes` (`Integrações`). Provê `IMonitorPromocoes` (ou similar). Requer `IPersistencia`, `IConfiguracao`, `IMonitoramento`, `INotificacoes` (para RF20, não neste fluxo). |
| `:BancoDeDados`                               | Armazena as promoções capturadas e os favoritos dos usuários.                  | Classes `PromocaoExterna`, `Usuario` e relação de favoritos.                                                                                                                               | RF19 (Armazenar). RNF04.                   | Componente `BancoDeDados`. Provê `IPersistencia`.                                                                                                                                                |
| **Mensagens / Interações Chave** |                                                                                |                                                                                                                                                                                            |                                            |                                                                                                                                                                                                  |
| `1: clicarAbaPromocoes()` ... `7: ...`         | Usuário acessa área de promoções, UI busca e exibe promoções ativas.           | Métodos `listarPromocoesAtivas` (`ModuloPromocoes`), `buscarPromocoes` (BD). Classe `PromocaoExterna`.                                                                                      | RF19.                                      | `WebUI`->`IAPIGeral`, `APIGateway`->Interface `ModuloPromocoes`, `ModuloPromocoes`->`IPersistencia`.                                                                                             |
| `8: clicarSalvarPromocaoFavorita(...)` ... `14: ...` | Usuário marca promoção como favorita, sistema registra a preferência. | Método `salvarPromocaoFavorita` (`ModuloPromocoes`, inf.), `inserirPromocaoFavorita` (BD, inf.). Relação Usuário-PromocaoExterna (favorito).                                                | RF19 (Permitir favoritar).                 | `ModuloPromocoes` consome `IPersistencia`.                                                                                                                                                       |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>

Com base na tabela 2, abaixo, na figura 3, há o diagrama de Sequência - Promoções

<div align="center">
    Figura 3: o Diagrama de Sequência - Promoções
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/refs/heads/main/docs/Modelagem/Imagens/DiagramaSequenciaPromocao.png">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>

## Conclusão

A elaboração dos diagramas de sequência permitiu representar com clareza os fluxos de interação entre os usuários e o sistema da plataforma Galáxia Conectada, o que permitiu uma compreensão maior sobre a dinâmica de funcionamento das funcionalidades das trilhas de aprendizado e da aba de promoções automatizadas. 

## Bibliografia

<a name="ref1"></a>
[1] APOSTILA UML. Unified Modeling Language – Linguagem de Modelagem Unificada em Português. Seção sobre diagrama de sequência. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref2"></a>
[2] CREATELY. Tutorial do Diagrama de Sequência: Guia completo com exemplos. Disponível em: https://creately.com/blog/pt/diagrama/tutorial-do-diagrama-de-sequencia/. Acesso em: 30 abr. 2025.

<a name="ref3"></a>
[3] IBM. Diagramas de Sequência. Atualizado pela última vez em: 5 mar. 2021. Disponível em: https://www.ibm.com/docs/pt-br/rsm/7.5.0?topic=uml-sequence-diagrams. Acesso em: 30 abr. 2025.

<a name="ref4"></a>
[4] LUCIDCHART. O que é um diagrama de sequência UML? Disponível em: https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-sequencia-uml. Acesso em: 30 abr. 2025.

## Histórico de versão

| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 30/04/2025 |
| 1.1 | Adição do seção de explicação  | Larissa Stéfane | 30/05/2025 |
| 1.2 | Adição dos diagramas | Larissa Stéfane | 01/05/2025 |
| 1.3 | Adição das tabelas | Larissa Stéfane | 04/05/2025 |
| 1.4 | Ajustes no artefato| Larissa Stéfane | 06/05/2025 |
