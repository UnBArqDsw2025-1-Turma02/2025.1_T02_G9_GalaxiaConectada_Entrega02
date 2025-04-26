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

#### 1. Dependência

- **O que é**: Representa uma ligação fraca e temporária entre classes, onde uma classe *depende* da outra para realizar alguma operação momentânea.
- **Exemplo no projeto**: O **BotImportador** depende da **IntegracaoExterna** para buscar dados, mas não mantém uma referência fixa a ela.
- **Símbolo**: Linha tracejada com seta.
  
- **Observação**: Como há muitas desses relacionamentos, a fim de deixar o diagrama mais legível, as relações de dependência não serão representadas no diagrama.

#### 2. Associação

- **O que é**: Representa um vínculo estruturado entre classes. Uma classe conhece a outra e pode enviar mensagens para ela a qualquer momento.
- **Exemplo no projeto**: A **WebUI** se associa ao **APICursos** para exibir cursos e módulos ao usuário.
- **Símbolo**: Linha contínua simples.
- **Cardinalidade**: Pode indicar quantos objetos de uma classe se relacionam com quantos objetos de outra (ex: "um para muitos", "muitos para muitos").

#### 3. Agregação

- **O que é**: É um tipo especial de associação que indica uma relação "parte-todo", mas com menor rigidez. As partes podem existir independentemente do todo.
- **Exemplo no projeto**: Um **Curso** agrega vários **Módulos**. Se o curso for excluído, os módulos ainda podem existir.
- **Símbolo**: Linha contínua com losango branco na extremidade do "todo".

#### 4. Composição

- **O que é**: É uma relação mais forte de "parte-todo", onde a parte não pode existir sem o todo. Se o todo for destruído, a parte também é destruída.
- **Exemplo no projeto**: Um **Quiz** é composto por várias **Questões**. Se o quiz for apagado, as questões também deixarão de existir.
- **Símbolo**: Linha contínua com losango preto na extremidade do "todo".

#### 5. Generalização

- **O que é**: Representa uma relação "é-um" entre classes. Uma classe mais específica herda atributos e comportamentos de uma classe mais genérica.
- **Exemplo no projeto**: **EventoAstronomico** poderia ser uma superclasse de eventos como **Eclipse** e **ChuvaDeMeteoros**.
- **Símbolo**: Linha contínua com seta aberta (vazia) apontando para a superclasse.

#### 6. Realização

- **O que é**: Representa a implementação de uma interface por uma classe concreta.
- **Exemplo no projeto**: A classe **ServicoNotificacoes** realiza (implementa) a interface **INotificacoes**.
- **Símbolo**: Linha tracejada com seta aberta (vazia) apontando para a interface.


# Conceitos Importantes

## Superclasse

- **Definição**: Uma superclasse é uma classe mais genérica que contém atributos e métodos comuns a várias outras classes.
- **Exemplo**: A classe **Usuario** pode ser a superclasse de **Aluno** e **Instrutor**, pois ambos compartilham características como `nome`, `e-mail` e `senha`.

## Subclasse

- **Definição**: Uma subclasse é uma classe mais específica que herda tudo da superclasse e pode adicionar seus próprios atributos e comportamentos.
- **Exemplo**: **Aluno** seria uma subclasse de **Usuario**, podendo acrescentar, por exemplo, um atributo `progressoNosCursos`.


## Investigação das Classes Necessárias

Antes de elaborar o diagrama diretamente no drawi.o, foi criada a tabela abaixo com base nas classes que seriam criadas ao se analisar os requisitos, os atores e as informações do 5W2H.

**Tabela 1:** Classes do Sistema.
| Classe                 | Atributos            | Métodos   | Relacionamentos    |
|------------------------|----------------------|-----------|--------------------|
| **Usuario**            | - `id: Int` (private)<br>- `nome: String` (private)<br>- `email: String` (private)<br>- `senha: String` (private)<br>- `dataCadastro: DateTime` (public)    | + `login(): Boolean`<br>+ `logout(): Void`<br>+ `editarPerfil(novoNome: String): Void`                                       | - Perfil (1:1, agregação)<br> - MensagemPrivada (1:*, associação, “envia/recebe”)<br> - Topico (1:*, associação, “cria”)<br> - Comentario (1:*, associação, “escreve”) |
| **Perfil**             | - `nivel: Int` (private)<br>- `xp: Int` (private)<br>- `linguagem: String` (private)<br>- `avatarUrl: String` (public)                                       | + `atualizarNivel(): Void`<br>+ `adicionarXp(valor: Int): Void`                                                               | Usuario (1:1, agregação)                                                                                                                                       |
| **Notificacao**        | - `id: Int` (private)<br>- `mensagem: String` (public)<br>- `data: DateTime` (public)<br>- `lida: Boolean` (private)                                        | + `enviarPara(u: Usuario): Void`<br>+ `marcarComoLida(): Void`                                                                 | Usuario ( *:1, associação, “recebe”)                                                                                                                           |
| **Reputacao**          | - `pontos: Int` (private)<br>- `nivelReputacao: String` (public)                                                                                           | + `atualizarPontos(valor: Int): Void`<br>+ `calcularNivel(): String`                                                           | Usuario (1:1, associação, “possui”)                                                                                                                            |
| **Conquista**          | - `id: Int` (private)<br>- `titulo: String` (public)<br>- `descricao: String` (public)<br>- `dataConquista: DateTime` (public)                              | + `concederA(u: Usuario): Void`                                                                                                | Usuario ( *:*, associação, “ganha”)                                                                                                                            |
| **TrilhaEducacional**  | - `id: Int` (private)<br>- `titulo: String` (public)<br>- `nivel: String` (public)<br>- `categoria: String` (public)                                        | + `iniciarPara(u: Usuario): Void`<br>+ `concluir(): Certificado`                                                                | Modulo (1:*, composição, “contém”)<br>Professor ( *:1, associação, “criada por”)                                                                                  |
| **Modulo**             | - `id: Int` (private)<br>- `titulo: String` (public)                                                                                                        | + `adicionarConteudo(c: Conteudo): Void`<br>+ `removerConteudo(c: Conteudo): Void`                                              | TrilhaEducacional ( *:1, composição, “parte de”)<br>Conteudo (1:*, agregação, “agrupa”)                                                                            |
| **Conteudo** (abstrata)| - `id: Int` (private)<br>- `titulo: String` (public)<br>- `descricao: String` (public)                                                                     | + `exibir(): Void`                                                                                                              | Modulo ( *:1, associação, “faz parte de”)<br>⥂ Artigo, Video, Quiz, Jogo (generalização)                                                                            |
| **Artigo**             | - `texto: String` (private)<br>- `dataPublicacao: DateTime` (public)                                                                                        | + `exibir(): Void`<br>+ `adicionarComentario(c: Comentario): Void`                                                              | Conteudo (1:1, generalização)<br>Comentario (1:*, associação, “recebe”)                                                                                            |
| **Video**              | - `url: String` (public)<br>- `duracaoSegundos: Int` (public)                                                                                              | + `play(): Void`<br>+ `pause(): Void`                                                                                            | Conteudo (1:1, generalização)                                                                                                                                   |
| **Quiz**               | - `numPerguntas: Int` (private)<br>- `tempoLimite: Int` (public)                                                                                            | + `iniciar(): Void`<br>+ `avaliar(respostas: List<String>): Boolean`                                                             | Conteudo (1:1, generalização)                                                                                                                                   |
| **Jogo**               | - `tipo: String` (public)<br>- `nivelDificuldade: Int` (public)                                                                                              | + `iniciar(): Void`<br>+ `finalizar(): ResultadoJogo`                                                                           | Conteudo (1:1, generalização)                                                                                                                                   |
| **Professor**          | - `id: Int` (private)<br>- `nome: String` (public)<br>- `areaEspecialidade: String` (public)                                                               | + `criarTrilha(t: TrilhaEducacional): Void`<br>+ `avaliarConteudo(c: Conteudo): Void`                                              | TrilhaEducacional (1:*, associação, “ministra”)                                                                                                                  |
| **Moderador**          | (herda de `Usuario`)<br>- `nivelModeracao: String` (public)                                                                                              | + `removerPostagem(p: Postagem): Void`<br>+ `fixarTopico(t: Topico): Void`                                                        | Usuario → Moderador (generalização)<br>Subforum ( *:*, associação, “modera”)                                                                                         |
| **Administrador**      | (herda de `Usuario`)                                                                                                                                      | + `gerenciarUsuario(u: Usuario): Void`<br>+ `configurarSistema(): Void`                                                          | Usuario → Administrador (generalization)                                                                                                                           |
| **FonteDeNoticias**    | - `nomeFonte: String` (public)<br>- `endpoint: String` (private)<br>- `apiKey: String` (private)                                                           | + `buscarNoticias(): List<Noticia>`                                                                                                | BotImportador (1:*, dependência, “usa”)                                                                                                                           |
| **BotImportador**      | - `frequenciaMinutos: Int` (private)<br>- `ultimoRun: DateTime` (private)                                                                                  | + `importar(): Void`<br>+ `agendarImportacao(): Void`                                                                            | FonteDeNoticias ( *:1, dependência, “consulta”)<br>Noticia (1:*, criação, “gera”)                                                                                     |
| **BotModerador**       | - `frequenciaVerificacao: Int` (private)<br>- `ultimaVerificacao: DateTime` (private)                                                                      | + `executarModeracao(): Void`<br>+ `reportarInfracoes(): List<Postagem>`                                                            | Postagem ( *:*, dependência, “analisa”)<br>Moderador (1:*, associação, “auxilia”)                                                                                       |
| **BotNotificador**     | - `tipoNotificacao: String` (private)<br>- `frequenciaEnvio: Int` (private)<br>- `ultimoEnvio: DateTime` (private)                                         | + `enviarLembretes(): Void`<br>+ `agendarEnvio(): Void`                                                                          | Notificacao ( *:*, criação, “dispara”)                                                                                                                              |
| **Subforum**           | - `id: Int` (private)<br>- `nome: String` (public)<br>- `descricao: String` (public)                                                                      | + `criarTopico(t: Topico): Void`<br>+ `removerTopico(t: Topico): Void`                                                             | Forum (1:*, agregação, “parte de”)<br>Topico (1:*, agregação, “contém”)                                                                                                  |
| **Topico**             | - `id: Int` (private)<br>- `titulo: String` (public)<br>- `dataCriacao: DateTime` (public)                                                                | + `adicionarPostagem(p: Postagem): Void`<br>+ `fechar(): Void`                                                                     | Subforum ( *:1, associação, “ pertence a”)<br>Postagem (1:*, agregação, “contém”)                                                                                       |
| **Postagem**           | - `id: Int` (private)<br>- `conteudo: String` (public)<br>- `dataPostagem: DateTime` (public)                                                             | + `editar(novoConteudo: String): Void`<br>+ `excluir(): Void`                                                                      | Topico ( *:1, associação, “parte de”)<br>Usuario (1:*, associação, “autor”)                                                                                               |
| **Comentario**         | - `id: Int` (private)<br>- `texto: String` (public)<br>- `dataComentario: DateTime` (public)                                                             | + `editar(texto: String): Void`<br>+ `excluir(): Void`                                                                           | Postagem ( *:1, associação, “parte de”)<br>Usuario (1:*, associação, “autor”)                                                                                             |

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

