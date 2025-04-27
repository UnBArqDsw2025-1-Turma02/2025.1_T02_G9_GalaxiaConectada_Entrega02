# Diagrama de Classes

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Investigação das Classes Necessárias](#Investigação-das-Classes-Necessárias)
- [Os Tipos de Relacionamentos](#Os-Tipos-de-Relacionamentos)
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

A partir dessa base, será feita uma investigação detalhada das entidades envolvidas no sistema. AEntão, serão definidas as classes do sistema, junto com seus atributos e métodos. Após compreender e definir bem as classes, serão analisados os relacionamentos de cada um delas. Por fim, o diagrama será elaborado e, em seguida, verificado de acordo com uma [tabela de verificação](Modelagem/IniciativasExtras/Verificacao/VerificacaoDiagramaClasses.md) baseada nos critérios sintáticos e semânticos da UML. Com isso, ajustes e melhorias serão aplicados conforme necessário.


## Investigação das Classes Necessárias

Antes de elaborar o diagrama diretamente no drawi.o, foi criada a tabela abaixo com base nas classes que seriam criadas ao se analisar os requisitos, os atores e as informações do 5W2H.

**Tabela 1:** Classes do Sistema.

| Classe   | O que é        | Atributos  | Métodos  |
|----------|----------------|------------|----------|
| **Usuario** | Conta de um indivíduo na plataforma, com dados básicos de login e perfil.                 | `- id: Int`<br>`- nome: String`<br>`- email: String`<br>`- senhaHash: String` <br>`- dataCadastro: DateTime`                                                                                                                                                           | `login(): Boolean`, `logout(): Void`, `editarPerfil(dados: Map): Void`, `enviarMensagemPrivada(dest: Usuario, texto: String): MensagemPrivada`, `criarTopicoForum(subforum: Subforum, titulo: String, postInicial: String): Topico`, `postarEmTopico(topico: Topico, texto: String): Postagem`, `comentar(item: Comentavel, texto: String): Comentario`                                                 |
| **Aluno** | Dados específicos de um usuário como aluno.                                                | `- progressoGeral: Float`<br>`- ultimoAcessoTrilha: DateTime`                                                                                                                                                                                                        | `listarCursosConcluidos(): List<Curso>`, `listarTrilhasEmAndamento(): List<TrilhaEducacional>`                                                                                                                                                                                                                                                                                                  |
| **Instrutor** | Dados específicos de um usuário como instrutor.                                            | `- biografiaCurta: String`<br>`- avaliacaoMedia: Float`<br>`- especialidades: List<String>`                                                                                                                                                                           | `listarTrilhasCriadas(): List<TrilhaEducacional>`, `listarConteudosCriados(): List<Conteudo>`                                                                                                                                                                                                                                                                                                      |
| **ProfessorVoluntario** | Dados de um usuário Professor Voluntário.                                                | `- areaEspecialidade: String`<br>`- artigosRevisados: Int`                                                                                                                                                                                                             | `listarArtigosSubmetidos(): List<Artigo>`                                                                                                                                                                                                                                                                                                                                                     |
| **Administrador** | Dados e permissões de um usuário administrador.                                          | `- permissoesGlobais: List<String>`<br>`- nivelAcesso: Int`                                                                                                                                                                                                            | `verLogSistema(filtro: String): List<LogEntry>`, `gerenciarUsuario(u: Usuario, acao: String): Boolean`, `gerenciarPromocao(p: Promocao, acao: String): Boolean`                                                                                                                                                                                                                              |
| **Moderador** | Dados e permissões de um usuário moderador do fórum.                                       | `- nivelModeracao: String`<br>`- dataInicioModeracao: DateTime`                                                                                                                                                                                                     | `listarSubforumsModerados(): List<Subforum>`, `moderarPostagem(p: Postagem, acao: String): Boolean`, `moderarTopico(t: Topico, acao: String): Boolean`                                                                                                                                                                                                                                            |
| **Perfil** | Informações adicionais e de progressão do usuário.                                         | `- nivel: Int`<br>`- xp: Int`<br>`- linguagemPref: String`<br>`+ avatarUrl: String`<br> **Observação**: Público para facilitar exibição direta da imagem em várias partes da UI. <br>`- bio: String`                                                                     | `atualizarNivel(): Void`, `adicionarXp(valor: Int): Void`, `atualizarAvatar(url: String): Void`                                                                                                                                                                                                                                                                                                 |
| **Reputacao** | Sistema de pontos e nível de reputação do usuário.                                         | `- pontos: Int`                                                                                                                                                                                                                                                      | `adicionarPontos(valor: Int, motivo: String): Void`, `calcularNivelReputacao(): String`                                                                                                                                                                                                                                                                                                        |
| **Notificacao** | Mensagens do sistema para o usuário.                                                     | `- id: Int`<br>`- mensagem: String`<br>`- tipo: String`<br>`- dataEnvio: DateTime`<br>`- lida: Boolean`<br>`+ link: String`<br>  **Observação:** Público para facilitar o uso do link de destino pela UI ao renderizar a notificação.                              | `marcarComoLida(): Void`                                                                                                                                                                                                                                                                                                                                                                           |
| **Conquista** | Prêmios, medalhas ou badges ganhos pelos usuários.                                         | `- id: Int`<br>`+ titulo: String`<br>  ``<br>`+ descricao: String`<br>  **Observação:** Público para exibição direta na UI. <br>`+ iconeUrl: String`<br> `<br>`- pontosXPConcedidos: Int`                                                                             | `desbloquearPara(u: Usuario): Boolean`                                                                                                                                                                                                                                                                                                                                                             |
| **TrilhaEducacional** | Conjunto de módulos educativos sobre um tema específico.                                   | `- id: Int`<br>`+ titulo: String`<br>  <br> **Observação**: Público para exibição em listas e títulos. <br> <br>`+ descricao: String`<br>  **Observação:** Público para exibição em catálogos/detalhes. <br>`+ nivel: String` <br>  `<br>`+ categoria: String`<br>  `<br>`- publicada: Boolean`<br>`+ imagemUrl: String` | `listarModulos(): List<Modulo>`, `calcularProgressoMedio(): Float`, `publicarTrilha(): Boolean`, `inscreverUsuario(u: Usuario): ProgressoUsuarioTrilha`                                                                                                                                                                                                                                  |
| **UsuarioConquista** | classe associativa que registra o evento e a data em que um Usuario específico ganhou uma determinada Conquista                                             | `- id: Int`<br>`- dataConquista: DateTime`<br> ` - progressoOrigem: ProgressoUsuarioTrilha `  | `getId(): Int`, `getDataConquista(): DateTime`,   ` getProgressoOrigem(): ProgressoUsuarioTrilha`    |
| **Modulo** | Agrupamento de conteúdos dentro de uma trilha.                                             | `- id: Int`<br>`+ titulo: String`<br>  **Observação**: Público para exibição na estrutura da trilha. <br>`+ ordem: Int`<br>  `<br>`+ descricaoBreve: String`<br>                                                                                                     | `listarConteudos(): List<Conteudo>`, `adicionarConteudo(c: Conteudo): Boolean`                                                                                                                                                                                                                                                                                                                   |
| **Conteudo** (Abstrata) | **Observação:** Superclasse (abstrata) que representa um material de estudo genérico na plataforma. | `- id: Int`<br>`+ titulo: String`<br>  **Observação:** Público para exibição em listas/sumários.`<br>`+ descricao: String`<br>  <br>`+ dataPublicacao: DateTime`<br>   <br>`- visibilidade: String`                                                                 | `exibir(): Void` (abstrato), `adicionarComentario(u: Usuario, texto: String): Comentario`                                                                                                                                                                                                                                                                                                           |
| **Artigo** | Subclasse de `Conteudo`; representa conteúdo textual.                                    | `- textoHtml: String`<br>`+ fonte: String`<br>  **Observação:** Público para exibição da fonte/referência.                                                                                                                                                         | `exibir(): Void`                                                                                                                                                                                                                                                                                                                                                                                   |
| **Video** | Subclasse de `Conteudo`; representa conteúdo audiovisual.                                  | `+ urlVideo: String`<br>  **Observação:** Público para acesso direto pelo player de vídeo.<br>`+ duracaoSegundos: Int`<br>`- transcricao: String`                                                                                                                 | `exibir(): Void`, `play(): Void`, `pause(): Void`                                                                                                                                                                                                                                                                                                                                                 |
| **Quiz** | Subclasse de `Conteudo`; representa avaliação interativa de conhecimento.                  | `+ tempoLimiteMin: Int`<br>  **Observação:** Público para exibir regras do quiz ao usuário. <br>`+ tentativasPermitidas: Int`<br>                                                                                                                              | `exibir(): Void`, `iniciar(u: Usuario): TentativaQuiz`, `submeter(t: TentativaQuiz): ResultadoQuiz`                                                                                                                                                                                                                                                                                            |
| **Jogo** | Subclasse de `Conteudo`; representa jogo educativo.                                        | `+ tipoJogo: String`<br>  <br>`+ nivelDificuldade: Int`<br>  `<br>`+ urlJogo: String`<br>                                                                                                                                                                   | `exibir(): Void`, `iniciar(u: Usuario): SessaoJogo`, `registrarPontuacao(s: SessaoJogo): PontuacaoJogo`                                                                                                                                                                                                                                                                                       |
| **Forum** | O Fórum principal da plataforma.                                                         | `- id: Int`<br>`+ nome: String`<br>  **Observação:** Público para exibição do nome do fórum. <br>`+ descricao: String`<br>                                                                                                                                             | `listarSubforums(): List<Subforum>`, `criarSubforum(nome: String, desc: String): Subforum`                                                                                                                                                                                                                                                                                                       |
| **Subforum** | Seção temática dentro do fórum.                                                          | `- id: Int`<br>`+ nome: String`<br>  <br>`+ descricao: String`<br>  <br>`+ ordemExibicao: Int`<br>  **Observação:** Público para ordenação na UI.                                                                                                                     | `listarTopicos(pagina: Int): List<Topico>`, `getModeradores(): List<Usuario>`                                                                                                                                                                                                                                                                                                                |
| **Topico** | Discussão iniciada em um subfórum.                                                       | `- id: Int`<br>`+ titulo: String`<br>  **Observação:** Público para exibição nas listas de tópicos. <br>`- dataCriacao: DateTime`<br>`+ dataUltPost: DateTime` <br>`- fixado: Boolean`<br>`- fechado: Boolean`                                                          | `listarPostagens(pagina: Int): List<Postagem>`, `fixar(): Void`, `fechar(): Void`                                                                                                                                                                                                                                                                                                              |
| **Postagem** | Contribuição de um usuário em um tópico.                                                   | `- id: Int`<br>`+ texto: String`<br>  **Observação:** Público, é o conteúdo principal da postagem para exibição. <br>`- dataPostagem: DateTime`<br>`+ editado: Boolean`<br>  <br>`+ dataEdicao: DateTime?`<br>  **Observação:** Público para exibir data da última edição na UI. | `editar(novoTexto: String): Void`                                                                                                                                                                                                                                                                                                                                                                  |
| **Comentario** | Comentário feito por um usuário (em Conteúdo, Postagem, etc.).                             | `- id: Int`<br>`+ texto: String`<br>  <br>`- dataComentario: DateTime`<br>`+ upvotes: Int`<br>  <br>`+ editado: Boolean`<br>                                                                                                                                  | `editar(novoTexto: String): Void`, `responderA(c: Comentario): Comentario`                                                                                                                                                                                                                                                                                                                |
| **MensagemPrivada** | Mensagem trocada entre dois usuários.                                                    | `- id: Int`<br>`- dataUltimaMensagem: DateTime`<br>`- participante1LidaAte: DateTime`<br>`- participante2LidaAte: DateTime`                                                                                                                                                                                 | `adicionarMensagem(remetente: Usuario, texto: String): MensagemPrivada`, `getMensagens(limite: Int, pagina: Int): Lista<MensagemPrivada>`, `getParticipantes(): Lista<Usuario>`, `getUltimaMensagem(): MensagemPrivada`                                                                                                                                                                                                                                                                                                                                                                           |
| **ConversaPrivada** | Mensagem trocada entre dois usuários.                                                    | `- id: Int`<br>`- texto: String`<br>`- dataEnvio: DateTime`<br>`- lida: Boolean`                                                                                                                                                                                 | `marcarComoLida(): Void`                                                                                                                                                                                                                                                                                                                                                                           |
| **Noticia** | Item de notícia (externo ou interno).                                                    | `- id: Int`<br>`+ titulo: String`<br>`+ resumo: String`<br>  <br>`+ urlOriginal: String`<br>  **Observação:** Público para link externo. <br>`+ dataPublicacao: DateTime`<br>  `**Observação:** Público para exibição.`<br>`+ imagemUrl: String`<br>  **Observação:** Público para exibição da imagem. | `exibirCompleta(): String`                                                                                                                                                                                                                                                                                                                                                             |
| **FonteDeNoticias** | Provedor de notícias.                                                                    | `- id: Int`<br>`+ nomeFonte: String`<br>  `**Observação:** Público para exibir a origem da notícia.`<br>`- urlBase: String`<br>`- tipo: String`<br>`- ativa: Boolean`                                                                                          | `buscarNovasNoticias(): List<Noticia>`                                                                                                                                                                                                                                                                                                                                                         |
| **PromocaoExterna** | Representa uma oferta especial encontrada em algum site, como Amazon ou Magazine Luiza.                                           | `- id: Int` <br>` - nomeProduto: String `<br>` - descricaoProduto: String `<br>` - precoOriginal: Float `<br>` - precoPromocional: Float `<br>` - lojaOrigem: String `<br>` + linkProduto: String `<br>` + urlImagemProduto: String `<br>` dataEncontrada: DateTime `<br>` - dataValidade: DateTime`                                                                   | `irParaLoja(): Void`, `verificarValidade(): Boolean`     |
| **FontePromocaoExterna** | Representa um site de e-commerce monitorado em busca de promoções (ex: Amazon, Magazine Luiza).               | `- id: Int `<br>` + nomeLoja: String `<br>` - urlBase: String `<br>` - seletorPreco: String `                                        | `+ getUrlBase(): String`           |
| **BotImportadorPromocoes** | Processo automatizado que busca promoções em sites externos e as registra na plataforma.                    | `- id: Int`<br>`- frequenciaMinutos: Int`<br>`- ultimaExecucao: DateTime`<br>`- ativo: Boolean`<br>` sitesMonitorados: List<FontePromocaoExterna>`                                                                                                 | `executarBusca(): Void`, `agendarProximaBusca(): Void`, `registrarPromocao(dadosPromocao: Map): PromocaoExterna`   |
| **ProgressoUsuarioTrilha** | Rastreia o progresso de um usuário em uma trilha específica.                              | `- status: String`<br>`- dataInicio: DateTime`<br>`- dataFim: DateTime?`<br>`- ultimoModuloAcessado: Int`<br>`- percentualConclusao: Float`                                                                                                                     | `atualizarProgresso(m: Modulo): Void`, `marcarConcluido(): Void`                                                                                                                                                                                                                                                                                                                               |
| **BotImportadorNoticias** | Processo automatizado para buscar e importar notícias de fontes externas.                | `- id: Int`<br>`- frequenciaMinutos: Int`<br>`- ultimaExecucao: DateTime`<br>`- ativo: Boolean`<br>`- fontesConfig: List<Map>`                                                                                                                                   | `executarImportacao(): Void`, `agendarProximaExecucao(): Void`, `configurarFonte(f: FonteDeNoticias): Void`                                                                                                                                                                                                                                                                           |


<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.


**Observação:** Inicialmente, tinha-se pensado em fazer o **usuário** como uma superclasse e **Aluno**, **Instrutor**, **Professor_Voluntário** e **Administrador** como suas subclasses. Contudo, percebeu-se que essa abordagem limita a representação de cenários reais onde uma única pessoa pode acumular múltiplas funções simultaneamente, como ser Instrutor e Professor_Voluntário ao mesmo tempo. **A herança estabelece uma relação "é um(a)", e assim força uma instância a pertencer a apenas uma das subclasses mais específicas, o que impede a combinação de papéis**. Por isso, optou-se por um modelo baseado em **composição: Usuario passa a ser uma classe comum**, representando a entidade central da pessoa ou conta no sistema, e ela se relaciona (agrega ou compõe) com outras classes que representam os diferentes Papéis (PapelAluno, PapelInstrutor, PapelProfessorVoluntario, PapelAdministrador). 
 


## Os Tipos de Relacionamentos

Com o objetivo de construir o diagrama da forma mais completa e mais correta possível, foi realizado um estudo por meio do artigo [Class Diagram | Unified Modeling Language (UML)](https://www.geeksforgeeks.org/unified-modeling-language-uml-class-diagrams/) [2](#ref2) sobre os tipos de relacionamentos necessários para o sistema da **Galáxia Conectada**. Esses relacionamentos descrevem como as classes interagem e se conectam entre si, cada um com seu próprio significado e nível de acoplamento.

### Os relacionamentos:

A tabela 1 mostra os Tipos de Relacionamentos que serão utilizados no diagrama de classes.

**Tabela 2:** Tipos de Relacionamentos

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
- **Exemplo**: A classe **Conteúdo** pode ser a superclasse de **Artigo** e **Vídeo**, pois ambos compartilham características como `título`, `descrição` e `Data de publicação`.

### Subclasse

- **Definição**: Uma subclasse é uma classe mais específica que herda tudo da superclasse e pode adicionar seus próprios atributos e comportamentos.
- **Exemplo**: **Artigo** seria uma subclasse de **Conteúdo**.

### Os Relacionamentos no Diagrama de Classes

Com base na análise da tabela das classes e no significado e relevância dos relacionamentos, a tabela 3 mostra os relacionamentos de cada uma das classes da tabela 1.



## Diagrama de Classes 

Abaixo, há o Diagrama de Classes criado:

**Observação:** Para analisaro Diagrama de Classes de forma ampliada e em seus detalhes, clique na imagem e ela será aberta em uma nova aba, a qual lhe permitirá explorá-lo com um zoom.

<div align="center">
    Figura 1: o Diagrama de Classes
    <br>
    <img src="Modelagem/Imagens/DiagramaClasses.png">
    <br>
     <b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>



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
| 1.6 | Reorganização das super e subclasses | Larissa Stéfane | 26/04/2024 |
| 1.7 | Adição da Tabela de Relacionamentos | Larissa Stéfane | 26/04/2024 |
