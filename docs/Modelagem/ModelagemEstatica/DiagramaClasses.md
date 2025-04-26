# Diagrama de Classes

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Os Tipos de Relacionamentos](#Os-Tipos-de-Relacionamentos)
- [Investigação das Classes Necessárias](#Investigação-das-Classes-Necessárias)
- [Diagrama de Classes](#Diagrama-de-Classes)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)

## Introdução

Segundo o [artigo da plataforma UML Diagrams](https://www.uml-diagrams.org/class-diagrams-overview.html) [3](#ref3) e a Apostila UML – Linguagem de Modelagem Unificada [1](#ref1), uma classe pode ser definida como a descrição de um conjunto de objetos com os mesmos atributos, comportamentos e relacionamentos. Sendo assim, ela representa um conceito dentro do domínio do sistema. Já o Diagrama de Classes, um dos principais diagramas da modelagem estática da UML, é responsável por estruturar o sistema ao representar as suas classes, os atributos, os métodos (operações) e os relacionamentos entre elas, como herança, associação e agregação.

No projeto Galáxia Conectada, uma plataforma educacional voltada ao ensino de astronomia de forma acessível e interativa, o Diagrama de Classes será utilizado para modelar os principais elementos do sistema com o intuito de contribuir para a organização e para a compreensão da estrutura do software.

## Objetivos

O objetivo deste artefato é representar, de forma clara e estruturada, os componentes principais do sistema Galáxia Conectada por meio do Diagrama de Classes. Busca-se, com isso, garantir uma visualização precisa das entidades que compõem o sistema, suas responsabilidades e seus relacionamentos.

## Metodologia

O Diagrama de Classes será desenvolvido utilizando a ferramenta [Draw.io](https://app.diagrams.net/), a qual permite a criação de diagramas UML de forma prática e visual. 

Como base para a definição das classes, serão utilizadas as informações coletadas na [Entrega 01 do projeto](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/), a qual inclui:

- [Requisitos funcionais e não funcionais Elicitados](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/IniciativaExtra/RequisitosElicitados);

- [Atores do sistema identificados no Rich Picture](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/ArtefatoGeneralista/RichPicture);

- Informações organizadas por meio da metodologia [5W2H](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/ArtefatoGeneralista/5W2H)

A partir dessa base, será feita uma investigação detalhada das entidades envolvidas no sistema. Após a definição preliminar das classes, o diagrama será elaborado e, em seguida, verificado de acordo com uma [tabela de verificação](Modelagem/IniciativasExtras/Verificacao/VerificacaoDiagramaClasses.md) baseada nos critérios sintáticos e semânticos da UML. Com isso, ajustes e melhorias serão aplicados conforme necessário.

## Os Tipos de Relacionamentos

Com o objetivo de construir o diagrama da forma mais completa e mais correta possível, foi realizado um estudo por meio do artigo [Class Diagram | Unified Modeling Language (UML)](https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/) [2](#ref2) sobre os tipos de relacionamentos necessários para o sistema da **Galáxia Conectada**. Esses relacionamentos descrevem como as classes interagem e se conectam entre si, cada um com seu próprio significado e nível de acoplamento.

### Os relacionamentos:

A tabela 1 mostra os Tipos de Relacionamentos que serão utilizados no diagrama de classes.

**Tabela 1:** Tipos de Relacionamentos

| Tipo de Relacionamento | O que é | Exemplo no Projeto | Símbolo | Observação/Extra |
|:-----------------------|:--------|:-------------------|:--------|:-----------------|
| Dependência | Representa uma ligação fraca e temporária entre classes. | O `BotImportador` depende da `IntegracaoExterna` para buscar dados, mas não mantém referência fixa. | Linha tracejada com seta. | Não será representado no diagrama para manter a legibilidade. |
| Associação | Representa um vínculo estruturado entre classes; uma classe conhece a outra e pode enviar mensagens. | A `WebUI` se associa ao `APICursos` para exibir cursos e módulos. | Linha contínua simples. | Pode indicar cardinalidade (ex: "um para muitos", "muitos para muitos"). |
| Agregação | Um tipo especial de associação ("parte-todo") com baixa rigidez; partes podem existir sem o todo. | Um `Curso` agrega vários `Módulos`; módulos podem existir mesmo se o curso for excluído. | Linha contínua com losango branco no "todo". | — |
| Composição | Relação forte de "parte-todo"; a parte não existe sem o todo. | Um `Quiz` é composto por várias `Questões`; se o quiz for apagado, as questões também desaparecem. | Linha contínua com losango preto no "todo". | — |
| Generalização | Representa uma relação "é-um"; herança de atributos e comportamentos. | `EventoAstronomico` como superclasse de `Eclipse` e `ChuvaDeMeteoros`. | Linha contínua com seta aberta (vazia) para a superclasse. | — |
| Realização | Representa a implementação de uma interface por uma classe concreta. | `ServicoNotificacoes` realiza (implementa) a interface `INotificacoes`. | Linha tracejada com seta aberta (vazia) para a interface. | — |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

### Conceitos Importantes

### Superclasse

- **Definição**: Uma superclasse é uma classe mais genérica que contém atributos e métodos comuns a várias outras classes.
- **Exemplo**: A classe **Usuario** pode ser a superclasse de **Aluno** e **Instrutor**, pois ambos compartilham características como `nome`, `e-mail` e `senha`.

### Subclasse

- **Definição**: Uma subclasse é uma classe mais específica que herda tudo da superclasse e pode adicionar seus próprios atributos e comportamentos.
- **Exemplo**: **Aluno** seria uma subclasse de **Usuario**, podendo acrescentar, por exemplo, um atributo `progressoNosCursos`.


## Investigação das Classes Necessárias

Antes de elaborar o diagrama diretamente no drawi.o, foi criada a tabela abaixo com base nas classes que seriam criadas ao se analisar os requisitos, os atores e as informações do 5W2H.

**Tabela 2:** Classes do Sistema.

| Classe                 | O que é | Atributos            | Métodos   | Relacionamentos    |
|------------------------|---------|----------------------|-----------|--------------------|
| **Usuario**            | Representa o usuário do sistema, responsável por interações básicas como login, criação de tópicos e envio de mensagens. <br> <br>  **Observação:** Superclasse que representa um usuário do sistema. | - `id: Int` (private)<br>- `nome: String` (private)<br>- `email: String` (private)<br>- `senha: String` (private)<br>- `dataCadastro: DateTime` (private)    | + `login(): Boolean`<br>+ `logout(): Void`<br>+ `editarPerfil(novoNome: String): Void`                                       | - Perfil (1:1, agregação)<br> - MensagemPrivada (1:*, associação, “envia/recebe”)<br> - Topico (1:*, associação, “cria”)<br> - Comentario (1:*, associação, “escreve”) |
| **Aluno**         | Subclasse de Usuário; representa um aluno.   | `matricula`, `curso`  | `matricular()`, `consultarNotas()` | Generalização de `Usuário`, Associação com `Curso` |
| **Instrutor**     | Subclasse de Usuário; representa um instrutor. | `especialidade`, `disciplina` | `ministrarAula()`, `corrigirProvas()` | Generalização de `Usuário`, Associação com `Curso` |
| **Administrador**  | Subclasse de Usuário; representa um administrador do sistema. | `permissoes` | `gerenciarUsuarios()`, `modificarSistema()` | Generalização de `Usuário`, Associação com `Usuários` |
| **Perfil**             | Representa as informações adicionais e progressão do usuário, como XP e avatar. | - `nivel: Int` (private)<br>- `xp: Int` (private)<br>- `linguagem: String` (private)<br>- `avatarUrl: String` (public, necessário ser público para exibição em perfis) | + `atualizarNivel(): Void`<br>+ `adicionarXp(valor: Int): Void`                                                               | Usuario (1:1, agregação)                                                                                                                                       |
| **Notificacao**        | Representa mensagens enviadas ao usuário para alertas e atualizações. | - `id: Int` (private)<br>- `mensagem: String` (private)<br>- `data: DateTime` (private)<br>- `lida: Boolean` (private)                                        | + `enviarPara(u: Usuario): Void`<br>+ `marcarComoLida(): Void`                                                                 | Usuario ( *:1, associação, “recebe”)                                                                                                                           |
| **Reputacao**          | Representa o sistema de reputação baseado nos pontos acumulados pelo usuário. | - `pontos: Int` (private)<br>- `nivelReputacao: String` (public, necessário ser exibido publicamente no perfil)                                                                                           | + `atualizarPontos(valor: Int): Void`<br>+ `calcularNivel(): String`                                                           | Usuario (1:1, associação, “possui”)                                                                                                                            |
| **Conquista**          | Representa prêmios e medalhas que o usuário pode ganhar. | - `id: Int` (private)<br>- `titulo: String` (private)<br>- `descricao: String` (private)<br>- `dataConquista: DateTime` (private)                              | + `concederA(u: Usuario): Void`                                                                                                | Usuario ( *:*, associação, “ganha”)                                                                                                                            |
| **TrilhaEducacional**  | Representa um conjunto de módulos educativos agrupados em uma trilha temática. | - `id: Int` (private)<br>- `titulo: String` (private)<br>- `nivel: String` (private)<br>- `categoria: String` (private)                                        | + `iniciarPara(u: Usuario): Void`<br>+ `concluir(): Certificado`                                                                | Modulo (1:*, composição, “contém”)<br>Professor ( *:1, associação, “criada por”)                                                                                  |
| **Modulo**             | Representa um agrupamento de conteúdos dentro de uma trilha educacional. | - `id: Int` (private)<br>- `titulo: String` (private)                                                                                                        | + `adicionarConteudo(c: Conteudo): Void`<br>+ `removerConteudo(c: Conteudo): Void`                                              | TrilhaEducacional ( *:1, composição, “parte de”)<br>Conteudo (1:*, agregação, “agrupa”)                                                                            |
| **Conteudo** (abstrata)| Representa qualquer tipo de material de estudo (ex: artigos, vídeos, quizzes, jogos). | - `id: Int` (private)<br>- `titulo: String` (private)<br>- `descricao: String` (private)                                                                     | + `exibir(): Void`                                                                                                              | Modulo ( *:1, associação, “faz parte de”)<br>⥂ Artigo, Video, Quiz, Jogo (generalização)                                                                            |
| **Artigo**             | Conteúdo textual publicado como parte do material de estudo. | - `texto: String` (private)<br>- `dataPublicacao: DateTime` (private)                                                                                        | + `exibir(): Void`<br>+ `adicionarComentario(c: Comentario): Void`                                                              | Conteudo (1:1, generalização)<br>Comentario (1:*, associação, “recebe”)                                                                                            |
| **Video**              | Conteúdo audiovisual disponibilizado como material de estudo. | - `url: String` (private)<br>- `duracaoSegundos: Int` (private)                                                                                              | + `play(): Void`<br>+ `pause(): Void`                                                                                            | Conteudo (1:1, generalização)                                                                                                                                   |
| **Quiz**               | Conteúdo interativo para avaliação de conhecimento. | - `numPerguntas: Int` (private)<br>- `tempoLimite: Int` (private)                                                                                            | + `iniciar(): Void`<br>+ `avaliar(respostas: List<String>): Boolean`                                                             | Conteudo (1:1, generalização)                                                                                                                                   |
| **Jogo**               | Jogo educativo criado para complementar o aprendizado. | - `tipo: String` (private)<br>- `nivelDificuldade: Int` (private)                                                                                              | + `iniciar(): Void`<br>+ `finalizar(): ResultadoJogo`                                                                           | Conteudo (1:1, generalização)                                                                                                                                   |
| **Professor**          | Representa instrutores responsáveis pela criação e avaliação de trilhas e conteúdos. | - `id: Int` (private)<br>- `nome: String` (private)<br>- `areaEspecialidade: String` (private)                                                               | + `criarTrilha(t: TrilhaEducacional): Void`<br>+ `avaliarConteudo(c: Conteudo): Void`                                              | TrilhaEducacional (1:*, associação, “ministra”)                                                                                                                  |
| **Moderador**          | Usuário com poderes extras para gerenciar o fórum e suas postagens. | - `nivelModeracao: String` (private)                                                                                              | + `removerPostagem(p: Postagem): Void`<br>+ `fixarTopico(t: Topico): Void`                                                        | Usuario → Moderador (generalização)<br>Subforum ( *:*, associação, “modera”)                                                                                         |
| **Administrador**      | Usuário com privilégios de gerenciar o sistema e configurações globais. | (herda atributos privados de Usuario)                                                                                                                                      | + `gerenciarUsuario(u: Usuario): Void`<br>+ `configurarSistema(): Void`                                                          | Usuario → Administrador (generalização)                                                                                                                           |
| **FonteDeNoticias**    | Representa provedores externos de notícias para o sistema. | - `nomeFonte: String` (private)<br>- `endpoint: String` (private)<br>- `apiKey: String` (private)                                                           | + `buscarNoticias(): List<Noticia>`                                                                                                | BotImportador (1:*, dependência, “usa”)                                                                                                                           |
| **BotImportador**      | Bot responsável por buscar notícias periodicamente. | - `frequenciaMinutos: Int` (private)<br>- `ultimoRun: DateTime` (private)                                                                                  | + `importar(): Void`<br>+ `agendarImportacao(): Void`                                                                            | FonteDeNoticias ( *:1, dependência, “consulta”)<br>Noticia (1:*, criação, “gera”)                                                                                     |
| **BotModerador**       | Bot que analisa automaticamente postagens para encontrar violações. | - `frequenciaVerificacao: Int` (private)<br>- `ultimaVerificacao: DateTime` (private)                                                                      | + `executarModeracao(): Void`<br>+ `reportarInfracoes(): List<Postagem>`                                                            | Postagem ( *:*, dependência, “analisa”)<br>Moderador (1:*, associação, “auxilia”)                                                                                       |
| **BotNotificador**     | Bot que dispara notificações automáticas para os usuários. | - `tipoNotificacao: String` (private)<br>- `frequenciaEnvio: Int` (private)<br>- `ultimoEnvio: DateTime` (private)                                         | + `enviarLembretes(): Void`<br>+ `agendarEnvio(): Void`                                                                          | Notificacao ( *:*, criação, “dispara”)                                                                                                                              |
| **Subforum**           | Seções dentro do fórum onde tópicos são agrupados por tema. | - `id: Int` (private)<br>- `nome: String` (private)<br>- `descricao: String` (private)                                                                      | + `criarTopico(t: Topico): Void`<br>+ `removerTopico(t: Topico): Void`                                                             | Forum (1:*, agregação, “parte de”)<br>Topico (1:*, agregação, “contém”)                                                                                                  |
| **Topico**             | Discussões iniciadas dentro de um subfórum. | - `id: Int` (private)<br>- `titulo: String` (private)<br>- `dataCriacao: DateTime` (private)                                                                | + `adicionarPostagem(p: Postagem): Void`<br>+ `fechar(): Void`                                                                     | Subforum ( *:1, associação, “ pertence a”)<br>Postagem (1:*, agregação, “contém”)                                                                                       |
| **Postagem**           | Mensagens postadas pelos usuários dentro de um tópico. | - `id: Int` (private)<br>- `conteudo: String` (private)<br>- `dataPostagem: DateTime` (private)                                                             | + `editar(novoConteudo: String): Void`<br>+ `excluir(): Void`                                                                      | Topico ( *:1, associação, “parte de”)<br>Usuario (1:*, associação, “autor”)                                                                                               |
| **Comentario**         | Respostas ou observações feitas em postagens ou artigos. | - `id: Int` (private)<br>- `texto: String` (private)<br>- `dataComentario: DateTime` (private)                                                             | + `editar(texto: String): Void`<br>+ `excluir(): Void`                                                                           | Postagem ( *:1, associação, “parte de”)<br>Usuario (1:*, associação, “autor”)                                                                                             |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Diagrama de Classes 




## Conclusão

A elaboração do Diagrama de Classes para o projeto Galáxia Conectada possibilitou a representação estruturada das principais entidades do sistema e suas interações.

## Bibliografia

<a name="ref1"></a>  
[1] APOSTILA UML. Seção sobre representação de classes. Disponibilizada pela professora. Acesso em: 25 abr. 2025.

<a name="ref2"></a>  
[2]GEEKSFORGEEKS. Unified Modeling Language (UML) Class Diagrams. Disponível em: https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/. Acesso em: 25 abr. 2025.

<a name="ref3"></a>  
[3]Lucid Software Português. Tutorial de Diagramas de Classes UML. Disponível em: https://www.youtube.com/watch?v=rDidOn6KN9k. Acesso em: 26 abr. 2025.

<a name="ref4"></a>  
[4] UML DIAGRAMS. Class Diagrams Overview. Disponível em: https://www.uml-diagrams.org/class-diagrams-overview.html. Acesso em: 25 abr. 2025.

## Histórico de versão

| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 25/04/2024 |
| 1.1 | Adição da Metodologia  | Larissa Stéfane | 25/04/2024 |
| 1.2 | Criação da tabela de investigação das classes | Larissa Stéfane | 25/04/2024 |
| 1.3 | Adição de mais elementos na  tabela de investigação das classes | Larissa Stéfane | 26/04/2024 |
| 1.4 | Adição da análise dos tipos de relacionamentos | Larissa Stéfane | 26/04/2024 |
| 1.5 | Adição de mais elementos na  tabela de investigação das classes | Larissa Stéfane | 26/04/2024 |
