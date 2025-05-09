# Diagrama de Comunicação ou Colaboração

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Sobre o Diagrama de Comunicação](#Sobre-o-Diagrama-de-Atividades)
- [Aba Fórum](#Aba-Fórum)
- [Aba Jogos](#Aba-Jogos)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)


## Introdução

O diagrama de colaboração (ou de comunicação), como é definido na Apostila UML - Unified Modeling Language - Linguagem de Modelagem Unificada em Português [1](#ref1), representa como os objetos de um sistema interagem entre si ao focar nos relacionamentos e nas trocas de mensagens mais do que na ordem temporal dessas ações. Segundo a [IBM: Diagramas de comunicação](https://www.ibm.com/docs/pt-br/radfws/9.6.0?topic=SSRTLW_9.6.0/com.ibm.xtools.sequence.doc/topics/ccommndiag.htm) <a name="ref3"></a>, esse tipo de diagrama permite analisar o comportamento dinâmico do sistema ao identificar objetos participantes, dados trocados e caminhos de mensagens. 

Dessa forma, como o desenvolvimento de diagramas de comunicação é essencial para visualizar como os componentes e objetos do sistema interagem entre si, especialmente em áreas com maior troca de mensagens, esse artefato apresenta os diagramas de comunicação para a **aba de fórum** e a **aba de jogos**. 


## Objetivos

O objetivo deste documento é representar graficamente os principais fluxos de interação entre objetos dos módulos do fórum e dos jogos da plataforma Galáxia Conectada por meio de diagramas de comunicação (ou colaboração). De forma mais específica, busca-se:

- Ilustrar a troca de mensagens entre instâncias de classes nos módulos Fórum e Jogos;

- Demonstrar a organização estrutural das interações com foco nos relacionamentos entre os objetos;

- Evidenciar a ordem sequencial das mensagens numeradas para facilitar o rastreamento dos comportamentos do sistema;

- Apoiar a modelagem dinâmica da plataforma com base em dois cenários práticos: participação em tópicos do fórum e execução de jogos educativos.


## Metodologia

A elaboração dos diagramas de comunicação seguirá uma abordagem fundamentada na análise integrada dos artefatos previamente desenvolvidos no projeto Galáxia Conectada. 

Sobre os módulos de foco neste artefato:

- **Aba (Módulo) do Fórum**: O Fórum é o espaço comunitário central da "Galáxia Conectada", projetado para facilitar a interação e a troca de conhecimento entre os usuários. Nele, os membros podem criar novos tópicos de discussão sobre assuntos astronômicos ou dúvidas sobre a plataforma, postar respostas e comentários em tópicos existentes (RF09, RF24), além de potencialmente votar em posts úteis e usar tags para organização (RF09). 

- **Aba (Módulo) dos Jogos**: Esta seção da plataforma "Galáxia Conectada" é dedicada a oferecer uma coleção de jogos e quizzes interativos (RF08, RF21) focados em temas astronômicos, o qual serve como uma ferramenta lúdica e complementar de aprendizado. Assim, o objetivo principal é engajar os usuários (entusiastas) de forma divertida e permitir  que testem seus conhecimentos.
 
Para a construção dos diagramas, serão seguidas as etapas abaixo:

1. Serão analisados os seguintes artefatos para embasamento dos diagramas:

- [Requisitos Funcionais e Não Funcionais elicitados - Elaborados na entrega 1](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/IniciativaExtra/RequisitosElicitados);
- [5W2H - Elaborado na Entrega 1]((https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/ArtefatoGeneralista/5W2H));
- [Brainstorming](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/ArtefatoGeneralista/BrainStorm);
- [Diagrama de Classe](/Modelagem/ModelagemEstatica/DiagramaClasses.md);
- [Diagrama de Componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md).


2. Dois diagramas serão desenvolvidos, sendo um para o módulo Fórum (interação em tópicos) e outro para o módulo Jogos (início e encerramento de partidas);

3. Os diagramas serão criados utilizando a ferramenta [Draw.io](https://www.drawio.com/blog/uml-component-diagrams);


## Sobre o Diagrama de Comunicação

Conforme explicado em [Guia: Diagramas de colaboração UML](https://miro.com/pt/diagrama/o-que-e-diagrama-colaboracao-uml/) [5](#ref5), os Diagramas de Comunicação (também conhecidos como diagramas de Colaboração) apresentados a seguir ilustram as interações dinâmicas entre os diferentes objetos e componentes de sistema necessários para realizar cenários específicos nas abas de Fórum e Jogos Educacionais da plataforma "Galáxia Conectada". Diferente dos diagramas de sequência que enfatizam a ordem temporal, estes diagramas focam na estrutura da colaboração ao mostrar os Vínculos (linhas de conexão) que existem entre os participantes (objetos/componentes como :WebUI, :ModuloForum, :ModuloJogos, entusiasta:Usuario, etc.) e como as Mensagens (as quais representam chamadas de métodos ou comunicação) trafegam por esses vínculos para executar uma tarefa, como criar um novo tópico ou registrar a pontuação de um jogo. Além disso, a sequência exata das interações é definida pela numeração anexada a cada mensagem, onde a notação decimal (ex: 1, 1.1, 1.2) indica o fluxo de controle e as chamadas aninhadas que ocorrem durante o processo, como é explicado em [Criar um diagrama de comunicação UML](https://support.microsoft.com/pt-br/topic/criar-um-diagrama-de-comunica%C3%A7%C3%A3o-uml-911956f4-5f19-4a58-97a3-bb14110a5ed1). [4](#ref4)

Com base no que foi explicado em [Criar um diagrama de comunicação UML](https://support.microsoft.com/pt-br/topic/criar-um-diagrama-de-comunica%C3%A7%C3%A3o-uml-911956f4-5f19-4a58-97a3-bb14110a5ed1) [4](#ref4), para construir estes diagramas e representar detalhadamente as interações, foram utilizados elementos chave da UML. Dessa forma, os participantes são mostrados como Objetos/Linhas de Vida (retângulos nomeados), conectados por Vínculos (linhas sólidas) que representam os caminhos de comunicação. As Mensagens, indicadas por setas ao longo dos vínculos, são rotuladas com números de sequência decimais para denotar a ordem e o aninhamento, nomes de operações e, ocasionalmente, parâmetros. Além desses fundamentos, para capturar a complexidade dos cenários, foram empregados elementos avançados: a notação <<create>> para indicar a criação de novas instâncias (como sessaoAtual : SessaoJogo ou topicoCriado : Topico), Iteração (*) para mensagens repetidas (como na atualização do jogo), Autochamadas (mensagens com setas em loop no mesmo objeto, ex: atualizações da :WebUI), e a notação <<destroy>> para indicar o fim do ciclo de vida de um objeto (como a sessaoAtual). 

Para melhor compreensão dos diagramas, a figura 1 mostra a legenda;

<div align="center">
    Figura 1: Legenda do Diagrama de Comunicação
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/refs/heads/main/docs/Modelagem/Imagens/LegendaDiagramaComunica%C3%A7%C3%A3o.drawio.png" width="500">
    <br>
    <b>Autora:</b> <a href="">Larissa Stéfane</a>.
    <br>
</div>


**Observação Importante:** Com o intuido de elaborar melhor os diagramas, foram elaboradas tabelas contendo os elementos/Participantes com suas descrições e relação com os requisitos elicitados e com os componentes do diagrama de componentes **(Tabelas 1 e 3)**. 
Da mesma forma, foram criadas tabelas que mostram os vínculos entre os objetos **(Tabelas 2 e 4)**

## Aba Fórum

Para elucidar os elementos que interagem e colaboram no Diagrama de Comunicação referente às funcionalidades do Fórum da plataforma "Galáxia Conectada", a Tabela 1 a seguir identifica e descreve cada participante (objetos ou instâncias de classes) envolvido. Esta tabela tem como objetivo fornecer uma visão detalhada de cada elemento que troca mensagens ao detalhar a sua funcionalidade no contexto específico das interações do fórum. 

<details>
  <summary><strong>Tabela 1: Participantes do Diagrama de Comunicação (Fórum)</strong></summary>


**Tabela 1:** Participantes do Diagrama de Comunicação (Fórum)

| #  | Elemento/Participante      | Descrição/Funcionalidade                                          | Relação Requisitos (RFs)        | Relação Componentes (Nome e #)                                 | Relação Classes (# e Nome)                     |
|----|----------------------------|-------------------------------------------------------------------|---------------------------------|----------------------------------------------------------------|------------------------------------------------|
| 1  | `entusiasta : Usuario`     | O usuário final que inicia a criação do tópico.                   | RF09, RF07, RF23, RF24, RF25   | (Ator Externo, interage com WebUI #3)                          | #01 Usuario                                    |
| 2  | `: WebUI`                  | Interface no navegador para interação do usuário com o fórum.       | (Suporte visual para RFs do Fórum) | `WebUI` (#3)                                                   | (Usa dados de várias classes)                  |
| 3  | `: APIGateway`             | Ponto de entrada API para requisições do fórum vindas da WebUI.   | (Infraestrutura)                | `APIGateway` (#11)                                             | (Orquestra chamadas a componentes/serviços)    |
| 4  | `: GestaoUsuarios`         | Verifica permissões do usuário para postar.                       | (Suporte a regras RF09)         | `GestaoUsuarios` (#12)                                         | #01 Usuario, #07 Perfil                         |
| 5  | `: ModuloForum`            | Orquestrador principal da lógica do fórum (criação, moderação...). | RF09, RF07, RF25, RF10          | `ModuloForum` (#26) (Parte do Subsistema Comunidade #25)       | #19 Forum, #20 Subforum, #21 Topico, #22 Postagem |
| 6  | `topicoCriado : Topico`    | Instância do Tópico sendo criado.                                 | RF09                            | (Gerenciado por `ModuloForum` #26)                             | #21 Topico                                     |
| 7  | `postagemInicial : Postagem`| Instância da primeira Postagem do tópico.                         | RF09                            | (Gerenciado por `ModuloForum` #26)                             | #22 Postagem                                   |
| 8  | `: ModuloModeracao`        | Avalia conteúdo e aplica regras de moderação.                     | (Suporte a regras RF09, RF07)   | `ModuloModeracao` (#28) (Parte do Subsistema Comunidade #25) | (Usa #21 Topico, #22 Postagem)                 |
| 9  | `: ServicoBusca`           | Indexa novo conteúdo para permitir buscas futuras.                | RF10                            | `ServicoBusca` (#14)                                           | (Indexa dados de #21 Topico, #22 Postagem, etc) |
| 10 | `perfilUsuario : Perfil`   | Instância do Perfil do usuário (usado para Reputação).            | RF07, RF23                      | (Gerenciado por `GestaoUsuarios` #12, usado por ModForum #26) | #07 Perfil                                     |
| 11 | `: Reputacao`              | Classe/Conceito representando a reputação (pontos adicionados).   | RF07                            | (Gerenciado por `GestaoUsuarios` #12, usado por ModForum #26) | #08 Reputacao                                  |
| 12 | `: ServicoNotificacoes`    | Envia notificações (moderadores, inscritos, usuário rejeitado).   | RF12, (Suporte RF09)            | `ServicoNotificacoes` (#13)                                    | #09 Notificacao                                |
| 13 | `: ServicoMonitoramento`   | Registra logs de eventos importantes.                             | (Suporte RNF05, RNF12)          | `ServicoMonitoramento` (#6)                                    | (Pode usar LogEntry - não definida)            |
| 14 | `: ServicoConfiguracao`    | Fornece configurações específicas do fórum.                       | (Suporte a regras RF09)         | `ServicoConfiguracao` (#4)                                     | (Usa config.yaml #5)                           |
| 15 | `: BancoDeDados`           | Armazena/Recupera dados persistentes do fórum e usuários.         | (Suporte a todos RFs)           | `BancoDeDados` (#34)                                           | (Persiste instâncias de várias classes)      |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>

Para complementar a identificação dos participantes, a Tabela 2 se aprofunda na dinâmica das interações do Fórum ao detalhar a sequência, o conteúdo e as características das mensagens trocadas e dos vínculos estabelecidos no Diagrama de Comunicação correspondente. O propósito desta tabela é servir como um guia para a leitura do diagrama.

<details>
  <summary><strong>Tabela 2: Mensagens e Vínculos do Diagrama de Comunicação (Fórum)</strong></summary>


**Tabela 2:** Mensagens e Vínculos do Diagrama de Comunicação (Fórum)

| Etapa        | Vínculo (Mensagem)                                                              | Tipo                                         | Origem -> Destino                           | Relação Requisitos (RFs) | Relação Componentes (Origem -> Destino)              | Relação Classes (Método/Dados)               |
|--------------|---------------------------------------------------------------------------------|----------------------------------------------|---------------------------------------------|--------------------------|------------------------------------------------------|----------------------------------------------|
| 1            | `exibirFormularioNovoTopico()`                                                  | Operação Lógica (Autochamada)                | :WebUI -> :WebUI                            | RF09                     | #3 WebUI -> #3 WebUI                                 | (Lógica UI)                                  |
| 2            | `submeterNovoTopico(...)`                                                       | Operação Lógica                              | :WebUI -> :APIGateway                       | RF09                     | #3 WebUI -> #11 APIGateway                           | (Payload com dados p/ Topico/Postagem)       |
| 2.1          | `logEvento('submissao_novo_topico')`                                            | Operação Lógica                              | :APIGateway -> :ServicoMonitoramento        | RNF05, RNF12             | #11 APIGateway -> #6 ServicoMonitoramento            | (Log)                                        |
| 2.2          | `verificarPermissaoPostar(...)`                                                 | Operação Lógica                              | :APIGateway -> :GestaoUsuarios              | (Regra implícita RF09)   | #11 APIGateway -> #12 GestaoUsuarios                 | (Verifica dados de Usuario #01)              |
| [permConcedida] 2.3 | `criarTopicoEPostagem(...)`                                             | Operação Lógica                              | :APIGateway -> :ModuloForum                 | RF09                     | #11 APIGateway -> #26 ModuloForum                    | (Orquestra criação de Topico #21, Postagem #22)|
| 2.3.1        | `getConfigsForum(...)`                                                          | Operação Lógica                              | :ModuloForum -> :ServicoConfiguracao        | (Regra implícita RF09)   | #26 ModuloForum -> #4 ServicoConfiguracao            | (Configuração)                               |
| 2.3.2        | `<<create>> inserirTopicoBD(...)`                                               | Operação Lógica                              | :ModuloForum -> :BancoDeDados               | RF09                     | #26 ModuloForum -> #34 BancoDeDados                  | (Cria/Persiste Topico #21)                   |
| 2.3.3        | `<<create>> inserirPostagemBD(...)`                                             | Operação Lógica                              | :ModuloForum -> :BancoDeDados               | RF09                     | #26 ModuloForum -> #34 BancoDeDados                  | (Cria/Persiste Postagem #22)                 |
| 2.3.4        | `atualizarRefUltimoPost(postagemInicial)`                                       | Operação Lógica                              | :ModuloForum -> `topicoCriado : Topico`     | RF09                     | #26 ModuloForum -> (#21 Topico)                      | (Atualiza estado Topico #21)                 |
| 2.3.5        | `inicializarEstado()`                                                           | Operação Lógica                              | :ModuloForum -> `postagemInicial : Postagem` | RF09                     | #26 ModuloForum -> (#22 Postagem)                    | (Atualiza estado Postagem #22)               |
| 2.3.6        | `getReputacaoUsuarioBD(idUsuario)`                                              | Operação Lógica                              | :ModuloForum -> :BancoDeDados               | RF07                     | #26 ModuloForum -> #34 BancoDeDados                  | (Busca Reputacao #08)                        |
| 2.3.7        | `reputacaoDoUsuario.adicionarPontos(...)`                                       | Método da Classe (`Reputacao.adicionarPontos`) | RF07                     | #26 ModuloForum -> (#08 Reputacao)                   | #08 Reputacao.adicionarPontos                |
| 2.3.8        | `salvarReputacaoBD(reputacaoDoUsuario)`                                         | Operação Lógica                              | :ModuloForum -> :BancoDeDados               | RF07                     | #26 ModuloForum -> #34 BancoDeDados                  | (Persiste Reputacao #08)                     |
| [reqMod] 2.3.9 | `marcarParaRevisao(postagemInicial)`                                          | Operação Lógica                              | :ModuloForum -> :ModuloModeracao            | (Regra implícita RF09)   | #26 ModuloForum -> #28 ModuloModeracao               | (Usa Postagem #22)                           |
| 2.3.9.1      | `atualizarStatusPostagemBD(idPostagem, 'PENDENTE')`                             | Operação Lógica                              | :ModuloModeracao -> :BancoDeDados           | (Regra implícita RF09)   | #28 ModuloModeracao -> #34 BancoDeDados              | (Atualiza Postagem #22)                      |
| 2.3.9.2      | `notificarEquipeModeradores(idPostagem)`                                        | Operação Lógica                              | :ModuloModeracao -> :ServicoNotificacoes    | (Regra implícita RF09)   | #28 ModuloModeracao -> #13 ServicoNotificacoes       | (Cria Notificacao #09)                       |
| * 2.3.10     | `associarTagAoTopico(topicoCriado, tag)`                                        | Operação Lógica                              | :ModuloForum -> :BancoDeDados               | RF09                     | #26 ModuloForum -> #34 BancoDeDados                  | (Associa Tag a Topico #21)                   |
| 2.3.11       | `indexarConteudo(topicoCriado)`                                                 | Operação Lógica                              | :ModuloForum -> :ServicoBusca               | RF10                     | #26 ModuloForum -> #14 ServicoBusca                  | (Usa Topico #21)                             |
| 2.3.11.1     | `atualizarIndice(topicoCriado)`                                                 | Operação Lógica (Autochamada)                | :ServicoBusca -> :ServicoBusca              | RF10                     | #14 ServicoBusca -> #14 ServicoBusca                 | (Lógica interna de indexação)                |
| 2.3.12       | `indexarConteudo(postagemInicial)`                                              | Operação Lógica                              | :ModuloForum -> :ServicoBusca               | RF10                     | #26 ModuloForum -> #14 ServicoBusca                  | (Usa Postagem #22)                           |
| 2.3.12.1     | `atualizarIndice(postagemInicial)`                                              | Operação Lógica (Autochamada)                | :ServicoBusca -> :ServicoBusca              | RF10                     | #14 ServicoBusca -> #14 ServicoBusca                 | (Lógica interna de indexação)                |
| 2.3.13       | `notificarInscritos(idSubforum, topicoCriado)`                                  | Operação Lógica                              | :ModuloForum -> :ServicoNotificacoes        | RF12                     | #26 ModuloForum -> #13 ServicoNotificacoes       | (Cria Notificacao #09, usa Topico #21)      |
| 3            | `redirecionarParaTopico(idTopicoCriado)`                                        | Operação Lógica (Autochamada)                | :WebUI -> :WebUI                            | RF09                     | #3 WebUI -> #3 WebUI                                 | (Lógica UI)                                  |
| 4            | `exibirPaginaTopico(topicoCriado)`                                              | Operação Lógica                              | :WebUI -> entusiasta: Usuario               | RF09                     | #3 WebUI -> (Ator)                                   | (Exibe dados do Topico #21)                  |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>

A Figura 2 mostra o diagrama de comunicação da aba do fórum


<div align="center">
    <b>Figura 2:</b> Diagrama de Comunicação – Fórum
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaComunicacaoForumDiscurssoes.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
</div>

<p><strong>Observação:</strong> Caso deseje visualizar ou baixar em PDF, clique aqui: 
<a href="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaComunicacaoForumDiscurssoes.pdf">PDF do Diagrama de Comunicação – Fórum</a></p>




## Aba Jogos

A fim de detalhar os colaboradores envolvidos nos cenários de interação dos Jogos Educacionais, conforme ilustrado no respectivo Diagrama de Comunicação, a Tabela 3 apresenta uma listagem descritiva de cada participante e seu papel funcional. Esta tabulação visa clarificar as responsabilidades de cada objeto ou instância dentro do fluxo dos jogos, vinculando-os aos Requisitos Funcionais (RFs) específicos que implementam, aos Componentes arquiteturais relacionados e às Classes do modelo de domínio que lhes dão origem. 

<details>
  <summary><strong>Tabela 3: Participantes do Diagrama de Comunicação (Jogos Educacionais)</strong></summary>

**Tabela 3:** Participantes do Diagrama de Comunicação (Jogos Educacionais)

| #  | Elemento/Participante          | Descrição/Funcionalidade                                                      | Relação Requisitos (RFs)          | Relação Componentes (Nome e #)                                    | Relação Classes (# e Nome)                                   |
|----|--------------------------------|-------------------------------------------------------------------------------|-----------------------------------|-----------------------------------------------------------------|--------------------------------------------------------------|
| 01  | `entusiasta : Usuario`         | O usuário final que interage com a plataforma para jogar.                     | RF08, RF05, RF06, RF22, RF23      | (Ator Externo, interage com WebUI #3)                             | #01 Usuario                                                  |
| 02  | `: WebUI`                      | Interface no navegador para exibir jogos, receber input e mostrar feedback.     | (Suporte visual RFs de Jogos)     | `WebUI` (#3)                                                      | (Usa dados de Jogo #18, PontuacaoJogo [conceitual], etc.)    |
| 03  | `: APIGateway`                 | Ponto de entrada API para requisições relacionadas aos jogos.                   | (Infraestrutura)                  | `APIGateway` (#11)                                                | (Orquestra chamadas a componentes/serviços)                  |
| 04  | `: GestaoUsuarios`             | Gerencia dados do usuário (pode ser consultado para ID em ações logadas).       | (Suporte RF05, RF23)              | `GestaoUsuarios` (#12)                                            | #01 Usuario, #07 Perfil                                        |
| 05  | `: ModuloJogos`                | Lógica principal dos jogos (iniciar, registrar resultado, gerenciar sessão).  | RF08, RF06, RF21, RF22            | `ModuloJogos` (#23) (Parte do Subsistema Conteudo Interativo #20) | (Usa #18 Jogo, SessaoJogo [não listada], PontuacaoJogo [não listada]) |
| 06  | `jogoSel : Jogo`               | Instância específica da classe `Jogo`, com dados/regras do jogo selecionado.  | RF08                              | (Gerenciado por `ModuloJogos` #23)                                | #18 Jogo (Subclasse de #14 Conteudo)                         |
| 07  | `sessaoAtual : SessaoJogo`     | Instância que representa a partida atual do jogo (criada ao iniciar).         | RF08                              | (Gerenciado por `ModuloJogos` #23)                                | (Retornada por Jogo.iniciar - não listada explicitamente)     |
| 08  | `: GestorAssetsEstaticos`      | Fornece URLs/acesso aos arquivos de mídia do jogo.                             | RNF11 (Implícito)                 | `GestorAssetsEstaticos` (#7)                                      | (Gerencia Artefatos #8)                                      |
| 09 | `: ServicoCache`               | Armazena dados do jogo temporariamente para acelerar carregamento.              | RNF02 (Opcional)                  | `ServicoCache` (#17)                                              | (Infraestrutura de Cache)                                    |
| 10 | `: ModuloGamificacao`          | Aplica regras de XP, conquistas baseado na performance do jogo.               | RF05, RF07, RF22, RF23            | `ModuloGamificacao` (#27) (Parte do Subsistema Comunidade #25)    | (Usa #07 Perfil, #10 Conquista, #08 Reputacao)                 |
| 11 | `perfilUsuario : Perfil`       | Instância do Perfil do usuário, onde XP é adicionado.                         | RF05, RF23                        | (Gerenciado por `GestaoUsuarios` #12, usado por ModGamif #27)      | #07 Perfil                                                     |
| 12 | `: MotorRegrasGamificacao`     | Define como recompensas são calculadas (pode ser interno ao ModGamif).         | RF05                              | (Conceitual ou parte do `ModuloGamificacao` #27)                  | (Lógica de Negócio)                                          |
| 13 | `: ServicoNotificacoes`        | Envia notificações ao usuário (ex: nova conquista).                           | RF12                              | `ServicoNotificacoes` (#13)                                       | #09 Notificacao                                              |
| 14 | `: ServicoMonitoramento`       | Registra logs de eventos importantes do fluxo do jogo.                        | RNF05, RNF12 (Suporte)            | `ServicoMonitoramento` (#6)                                       | (Pode usar LogEntry)                                         |
| 15 | `: ServicoConfiguracao`        | Busca configurações gerais ou específicas do jogo (ex: pontuação base).      | (Suporte RF08, RF21)              | `ServicoConfiguracao` (#4)                                        | (Usa config.yaml #5)                                         |
| 16 | `: BancoDeDados`               | Persistência de dados do jogo, sessões, pontuações, perfil, etc.              | RF04, RF05, RF07, RF23 (Suporte) | `BancoDeDados` (#34)                                              | (Persiste instâncias de várias classes)                        |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>

Para uma análise minuciosa do fluxo de mensagens e das conexões representadas no Diagrama de Comunicação dos Jogos Educacionais, a Tabela 4 subsequente cataloga e explica cada interação fundamental entre os participantes. Através desta tabela, busca-se facilitar a compreensão do diagrama ao mapear a sequência da comunicação, ao identificar o conteúdo de cada mensagem (vínculo), seu tipo, o remetente e o destinatário. Para enriquecer o entendimento, a tabela também correlaciona essas trocas de mensagens com os Requisitos Funcionais (RFs) atendidos e as interações entre Componentes e os métodos/dados das Classes.

<details>
  <summary><strong>Tabela 4: Mensagens e Vínculos do Diagrama de Comunicação (Jogos Educacionais)
</strong></summary>

**Tabela 4:** Mensagens e Vínculos do Diagrama de Comunicação (Jogos Educacionais)


| Etapa        | Vínculo (Mensagem)                                                              | Tipo                                            | Origem -> Destino                        | Relação Requisitos (RFs) | Relação Componentes (Origem -> Destino)                     | Relação Classes (Método/Dados)                      |
|--------------|---------------------------------------------------------------------------------|-------------------------------------------------|------------------------------------------|--------------------------|-----------------------------------------------------------|-----------------------------------------------------|
| 1            | `solicitarInicioJogo(idJogo, idUsuario?)`                                       | Operação Lógica                                 | :WebUI -> :APIGateway                    | RF08                     | #3 WebUI -> #11 APIGateway                              | (Inicia fluxo do jogo)                              |
| 1.1          | `logEvento('req_inicio_jogo')`                                                  | Operação Lógica                                 | :APIGateway -> :ServicoMonitoramento     | (Monitoramento)          | #11 APIGateway -> #6 ServicoMonitoramento                 | (Log)                                               |
| 1.2          | `iniciarJogo(idJogo, idUsuario?)`                                               | Operação Lógica                                 | :APIGateway -> :ModuloJogos              | RF08                     | #11 APIGateway -> #23 ModuloJogos                         | (Orquestra início do jogo)                          |
| 1.2.1        | `getConfig(chave='jogo_config')`                                                | Operação Lógica                                 | :ModuloJogos -> :ServicoConfiguracao     | (Suporte RF08)           | #23 ModuloJogos -> #4 ServicoConfiguracao               | (Configuração)                                      |
| 1.2.2        | `getCacheJogo(idJogo)`                                                          | Operação Lógica                                 | :ModuloJogos -> :ServicoCache            | RNF02 (Opcional)         | #23 ModuloJogos -> #17 ServicoCache                     | (Cache)                                             |
| [cacheMiss] 1.2.3 | `buscarJogoDoBD(idJogo)`                                              | Operação Lógica                                 | :ModuloJogos -> :BancoDeDados            | RF08                     | #23 ModuloJogos -> #34 BancoDeDados                     | (Busca dados Jogo #18)                              |
| 1.2.4        | `getUrlsAssets(jogoSel.assets)`                                                 | Operação Lógica                                 | :ModuloJogos -> :GestorAssetsEstaticos   | RNF11 (Implícito)        | #23 ModuloJogos -> #7 GestorAssetsEstaticos             | (Assets)                                            |
| 1.2.5        | `sessaoAtual := <<create>> jogoSel.iniciar(entusiasta)`                         | Método da Classe (`Jogo.iniciar`)               | :ModuloJogos -> `jogoSel : Jogo`         | RF08                     | #23 ModuloJogos -> (#18 Jogo)                           | #18 Jogo.iniciar                                    |
| * 2          | `atualizarInterfaceJogo(estadoSessao)`                                          | Operação Lógica (Autochamada)                   | :WebUI -> :WebUI                         | RF08                     | #3 WebUI -> #3 WebUI                                      | (Lógica UI)                                         |
| * 2.1        | `getEstadoAtualizado()`                                                         | Operação Lógica/Método (`SessaoJogo`)         | `sessaoAtual : SessaoJogo` -> :WebUI     | RF08                     | (SessaoJogo) -> #3 WebUI                                  | (Estado SessaoJogo)                                 |
| 3            | `submeterResultado(idSessao, pontuacao)`                                        | Operação Lógica                                 | :WebUI -> :APIGateway                    | RF06                     | #3 WebUI -> #11 APIGateway                              | (Envia dados PontuacaoJogo)                         |
| 3.1          | `logEvento('submissao_resultado')`                                              | Operação Lógica                                 | :APIGateway -> :ServicoMonitoramento     | (Monitoramento)          | #11 APIGateway -> #6 ServicoMonitoramento                 | (Log)                                               |
| 3.2          | `registrarResultado(idSessao, pontuacao, idUsuario?)`                           | Operação Lógica                                 | :APIGateway -> :ModuloJogos              | RF06                     | #11 APIGateway -> #23 ModuloJogos                         | (Processa resultado)                                |
| 3.2.1        | `pontuacaoReg := jogoSel.registrarPontuacao(sessaoAtual)`                       | Método da Classe (`Jogo.registrarPontuacao`)    | :ModuloJogos -> `jogoSel : Jogo`         | RF06                     | #23 ModuloJogos -> (#18 Jogo)                           | #18 Jogo.registrarPontuacao                         |
| 3.2.2        | `salvarPontuacaoBD(pontuacaoReg)`                                               | Operação Lógica                                 | :ModuloJogos -> :BancoDeDados            | RF04, RF23               | #23 ModuloJogos -> #34 BancoDeDados                     | (Persiste PontuacaoJogo)                            |
| [pont > rec] 3.2.3 | `atualizarRecordeBD(jogoSel, pontuacao)`            | Operação Lógica                                 | :ModuloJogos -> :BancoDeDados            | RF07 (Implícito)         | #23 ModuloJogos -> #34 BancoDeDados                     | (Atualiza Jogo #18)                                 |
| 3.3          | `idUsuarioLogado := getUsuarioDaSessao(idSessao)`                               | Operação Lógica                                 | :ModuloJogos -> :GestaoUsuarios          | (Suporte RF05)           | #23 ModuloJogos -> #12 GestaoUsuarios                   | (Busca Usuario #01)                                 |
| [idUser] 3.4   | `registrarAcaoGamificacao('jogo_finalizado', ...)`                              | Operação Lógica                                 | :ModuloJogos -> :ModuloGamificacao       | RF05, RF07, RF23         | #23 ModuloJogos -> #27 ModuloGamificacao                | (Inicia processo Gamificação)                       |
| 3.4.1        | `getPerfilDoBD(idUsuarioLogado)`                                                | Operação Lógica                                 | :ModuloGamificacao -> :BancoDeDados      | RF05, RF23               | #27 ModuloGamificacao -> #34 BancoDeDados                 | (Busca Perfil #07)                                  |
| 3.4.2        | `calcularRecompensas(...)`                                                      | Operação Lógica                                 | :ModuloGamificacao -> :MotorRegrasGamificacao | RF05                   | #27 ModuloGamificacao -> (MotorRegras)                    | (Lógica de Negócio)                                 |
| 3.4.3        | `perfilUsuario.adicionarXp(xpCalculado)`                                        | Método da Classe (`Perfil.adicionarXp`)         | :ModuloGamificacao -> `perfilUsuario : Perfil` | RF05                   | #27 ModuloGamificacao -> (#07 Perfil)                     | #07 Perfil.adicionarXp                              |
| 3.4.4        | `salvarPerfilBD(perfilUsuario)`                                                 | Operação Lógica                                 | :ModuloGamificacao -> :BancoDeDados      | RF05, RF23               | #27 ModuloGamificacao -> #34 BancoDeDados                 | (Persiste Perfil #07)                               |
| 3.4.5        | `verificarDesbloqueioConquista(...)`                                            | Operação Lógica                                 | :ModuloGamificacao -> :BancoDeDados      | RF05                     | #27 ModuloGamificacao -> #34 BancoDeDados                 | (Verifica/Atualiza Conquista #10/UsuarioConquista #12) |
| [conqDesbl] 3.4.6 | `enviarNotificacao(idUsuarioLogado, tipo='conquista', ...)`                | Operação Lógica                                 | :ModuloGamificacao -> :ServicoNotificacoes | RF12                   | #27 ModuloGamificacao -> #13 ServicoNotificacoes          | (Cria Notificacao #09)                              |
| 3.5          | `<<destroy>> finalizarSessaoJogo(sessaoAtual)`                                  | Operação Lógica                                 | :ModuloJogos -> `sessaoAtual : SessaoJogo` | RF08                     | #23 ModuloJogos -> (SessaoJogo)                           | (Finaliza ciclo SessaoJogo)                         |
| 4            | `exibirFeedbackFinal(...)`                                                      | Operação Lógica                                 | :WebUI -> `entusiasta : Usuario`         | RF06                     | #3 WebUI -> (Ator)                                      | (Exibe resultado/XP)                                |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>

A figura 3 apresenta o diagrama de Comunicação da Aba de Jogos

<div align="center">
    <b>Figura 3:</b> Diagrama de Comunicação – Jogos
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaComunicacaoJogosEducacionais.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
</div>

<p><strong>Observação:</strong> Caso deseje visualizar ou baixar em PDF, clique aqui: 
<a href="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaComunicacaoJogosEducacionais.pdf">PDF do Diagrama de Comunicação – Jogos</a></p>




## Conclusão

Em conclusão, os Diagramas de Comunicação elaborados para os módulos de Fórum e Jogos Educacionais forneceram uma visão detalhada e estrutural das interações entre os diversos componentes e objetos da plataforma "Galáxia Conectada". Ao mapear os participantes, seus vínculos de comunicação e, crucialmente, a sequência numerada das mensagens trocadas – ao incorporar elementos avançados como criação de objetos, condições e iterações – estes diagramas elucidam como as diferentes partes do sistema colaboram para realizar funcionalidades chave, como a criação de um tópico ou a execução e pontuação de um jogo.

## Bibliografia

<a name="ref1"></a>
[1] APOSTILA UML. Seção sobre representação de Diagrama de Colaboração. Disponibilizada pela professora. Acesso em: 1 maio 2025.

<a name="ref2"></a>
[2] IBM. Criando Diagramas de Comunicação. Disponível em: https://www.ibm.com/docs/pt-br/dmrt/9.5.0?topic=diagrams-creating-communication. Acesso em: 2 maio 2025.

<a name="ref3"></a>
[3] IBM. Diagramas de comunicação. Disponível em: https://www.ibm.com/docs/pt-br/radfws/9.6.0?topic=SSRTLW_9.6.0/com.ibm.xtools.sequence.doc/topics/ccommndiag.htm. Acesso em: 1 maio 2025.

<a name="ref4"></a>
[4] MICROSOFT. Criar um diagrama de comunicação UML. Disponível em: https://support.microsoft.com/pt-br/topic/criar-um-diagrama-de-comunica%C3%A7%C3%A3o-uml-911956f4-5f19-4a58-97a3-bb14110a5ed1. Acesso em: 1 maio 2025.

<a name="ref5"></a>
[5] MIRO. Guia: Diagramas de colaboração UML. Disponível em: https://miro.com/pt/diagrama/o-que-e-diagrama-colaboracao-uml/. Acesso em: 2 maio 2025.

<a name="ref6"></a>
[6] OLIVEIRA, George. Diagrama de Comunicação. [Vídeo]. YouTube. Disponível em: https://www.youtube.com/watch?v=6feefuR-iqI. Acesso em: 1 maio 2025.

## Histórico de versão


| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 01/05/2025 |
| 1.1 | Adição da metodologia e da seção de explicação  | Larissa Stéfane | 01/05/2025 |
| 1.2 | Criação das tabelas da aba fórum | Larissa Stéfane | 01/05/2025 |
| 1.3 | Criação das tabelas da aba de jogos | Larissa Stéfane | 02/05/2025 |
| 1.4 | Explicação dos diagramas de comunicação | Larissa Stéfane | 02/05/2025 |
| 1.5 | Adição dos diagramas | Larissa Stéfane | 02/05/2025 |
| 1.6 | Ajustes no artefato| Larissa Stéfane | 06/05/2025 |
