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
- [Diagrama de Componentes](docs/Modelagem/ModelagemEstatica/DiagramaComponentes.md).


2. Dois diagramas serão desenvolvidos, sendo um para o módulo Fórum (interação em tópicos) e outro para o módulo Jogos (início e encerramento de partidas);

3. Os diagramas serão criados utilizando a ferramenta [Draw.io](https://www.drawio.com/blog/uml-component-diagrams);

4. Será realizada uma revisão dos diagramas com base em checklist de boas práticas da UML para garantir a consistência e clareza da representação.

## Sobre o Diagrama de Comunicação

Conforme explicado em [Guia: Diagramas de colaboração UML](https://miro.com/pt/diagrama/o-que-e-diagrama-colaboracao-uml/) [5](#ref5), os Diagramas de Comunicação (também conhecidos como diagramas de Colaboração) apresentados a seguir ilustram as interações dinâmicas entre os diferentes objetos e componentes de sistema necessários para realizar cenários específicos nas abas de Fórum e Jogos Educacionais da plataforma "Galáxia Conectada". Diferente dos diagramas de sequência que enfatizam a ordem temporal, estes diagramas focam na estrutura da colaboração, mostrando os Vínculos (linhas de conexão) que existem entre os participantes (objetos/componentes como :WebUI, :ModuloForum, :ModuloJogos, entusiasta:Usuario, etc.) e como as Mensagens (representando chamadas de métodos ou comunicação) trafegam por esses vínculos para executar uma tarefa, como criar um novo tópico ou registrar a pontuação de um jogo. A sequência exata das interações é definida pela numeração anexada a cada mensagem, onde a notação decimal (ex: 1, 1.1, 1.2) indica o fluxo de controle e as chamadas aninhadas que ocorrem durante o processo, como é explicado em [Criar um diagrama de comunicação UML](https://support.microsoft.com/pt-br/topic/criar-um-diagrama-de-comunica%C3%A7%C3%A3o-uml-911956f4-5f19-4a58-97a3-bb14110a5ed1). [4](#ref4)

Com base no que foi explicado em [Criar um diagrama de comunicação UML](https://support.microsoft.com/pt-br/topic/criar-um-diagrama-de-comunica%C3%A7%C3%A3o-uml-911956f4-5f19-4a58-97a3-bb14110a5ed1) [4](#ref4), para construir estes diagramas e representar detalhadamente as interações, foram utilizados elementos chave da UML. Dessa forma, os participantes são mostrados como Objetos/Linhas de Vida (retângulos nomeados), conectados por Vínculos (linhas sólidas) que representam os caminhos de comunicação. As Mensagens, indicadas por setas ao longo dos vínculos, são rotuladas com números de sequência decimais para denotar a ordem e o aninhamento, nomes de operações e, ocasionalmente, parâmetros. Além desses fundamentos, para capturar a complexidade dos cenários, foram empregados elementos avançados: a notação <<create>> para indicar a criação de novas instâncias (como sessaoAtual : SessaoJogo ou topicoCriado : Topico), Condições de Guarda ([]) para mostrar mensagens que só são enviadas se uma condição for verdadeira (ex: [permissaoConcedida]), Iteração (*) para mensagens repetidas (como na atualização do jogo), Autochamadas (mensagens com setas em loop no mesmo objeto, ex: atualizações da :WebUI), e a notação <<destroy>> para indicar o fim do ciclo de vida de um objeto (como a sessaoAtual). 

Para melhor compreensão dos diagramas, a figura 1 mostra a legenda;

<div align="center">
    Figura 1: Legenda do Diagrama de Comunicação
    <br>
    <img src="" width="500">
    <br>
    <b>Autora:</b> <a href="">Larissa Stéfane</a>.
    <br>
</div>

## Aba Fórum

Tabela 1: Participantes do Diagrama de Comunicação (Fórum)

| #  | Elemento/Participante      | Descrição/Funcionalidade                                                                 |
|----|----------------------------|------------------------------------------------------------------------------------------|
| 1  | `entusiasta : Usuario`     | O usuário final que inicia a criação do tópico.                                          |
| 2  | `: WebUI`                  | A interface no navegador onde o usuário preenche e submete o formulário do tópico.       |
| 3  | `: APIGateway`             | Recebe a requisição da WebUI e a direciona para os serviços backend apropriados.       |
| 4  | `: GestaoUsuarios`         | Componente que verifica se o usuário tem permissão para postar no subfórum.              |
| 5  | `: ModuloForum`            | Orquestrador principal da lógica do fórum: cria tópico/post, chama outros serviços.       |
| 6  | `topicoCriado : Topico`    | A instância específica do Tópico que está sendo criada neste fluxo.                      |
| 7  | `postagemInicial : Postagem`| A instância da primeira Postagem associada ao tópico, criada neste fluxo.                |
| 8  | `: ModuloModeracao`        | Componente que avalia se o conteúdo requer moderação e atualiza seu status.              |
| 9  | `: ServicoBusca`           | Serviço responsável por indexar o novo conteúdo (tópico e postagem) para buscas futuras. |
| 10 | `perfilUsuario : Perfil`   | Instância do Perfil do usuário, consultada (indiretamente) para dados de reputação.        |
| 11 | `: Reputacao`              | Classe/Conceito representando a reputação. O Módulo Fórum interage para adicionar pontos.   |
| 12 | `: ServicoNotificacoes`    | Serviço para enviar notificações (ex: para inscritos no subfórum, para moderadores).    |
| 13 | `: ServicoMonitoramento`   | Serviço para registrar logs de eventos importantes (ex: submissão de tópico).            |
| 14 | `: ServicoConfiguracao`    | Serviço para buscar configurações do fórum (ex: regras de moderação).                    |
| 15 | `: BancoDeDados`           | Camada de persistência para salvar/buscar todos os dados (tópicos, posts, reputação, etc.). |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.


Tabela 2: Mensagens e Vínculos do Diagrama de Comunicação (Fórum)

| Etapa        | Vínculo (Mensagem)                                                              | Tipo                                         | Origem -> Destino                           |
|--------------|---------------------------------------------------------------------------------|----------------------------------------------|---------------------------------------------|
| 1            | `exibirFormularioNovoTopico()`                                                  | Operação Lógica (Autochamada)                | :WebUI -> :WebUI                            |
| 2            | `submeterNovoTopico(idSubforum, ..., titulo, textoPost, tags?)`               | Operação Lógica                              | :WebUI -> :APIGateway                       |
| 2.1          | `logEvento('submissao_novo_topico')`                                            | Operação Lógica                              | :APIGateway -> :ServicoMonitoramento        |
| 2.2          | `verificarPermissaoPostar(idUsuario, idSubforum)`                               | Operação Lógica                              | :APIGateway -> :GestaoUsuarios              |
| [permConcedida] 2.3 | `criarTopicoEPostagem(idSubforum, idUsuario, titulo, textoPost, tags?)` | Operação Lógica                              | :APIGateway -> :ModuloForum                 |
| 2.3.1        | `getConfigsForum(idSubforum)`                                                   | Operação Lógica                              | :ModuloForum -> :ServicoConfiguracao        |
| 2.3.2        | `<<create>> inserirTopicoBD(titulo, idUsuario, ...)`                          | Operação Lógica                              | :ModuloForum -> :BancoDeDados               |
| 2.3.3        | `<<create>> inserirPostagemBD(idTopicoCriado, textoPost, ...)`                | Operação Lógica                              | :ModuloForum -> :BancoDeDados               |
| 2.3.4        | `atualizarRefUltimoPost(postagemInicial)`                                       | Operação Lógica                              | :ModuloForum -> `topicoCriado : Topico`     |
| 2.3.5        | `inicializarEstado()`                                                           | Operação Lógica                              | :ModuloForum -> `postagemInicial : Postagem` |
| 2.3.6        | `getReputacaoUsuarioBD(idUsuario)`                                              | Operação Lógica                              | :ModuloForum -> :BancoDeDados               |
| 2.3.7        | `reputacaoDoUsuario.adicionarPontos(PONTOS_POST, 'Novo Post')`                  | Método da Classe (`Reputacao.adicionarPontos`) | :ModuloForum -> `: Reputacao`               |
| 2.3.8        | `salvarReputacaoBD(reputacaoDoUsuario)`                                         | Operação Lógica                              | :ModuloForum -> :BancoDeDados               |
| [reqMod] 2.3.9 | `marcarParaRevisao(postagemInicial)`                                            | Operação Lógica                              | :ModuloForum -> :ModuloModeracao            |
| 2.3.9.1      | `atualizarStatusPostagemBD(idPostagem, 'PENDENTE')`                             | Operação Lógica                              | :ModuloModeracao -> :BancoDeDados           |
| 2.3.9.2      | `notificarEquipeModeradores(idPostagem)`                                        | Operação Lógica                              | :ModuloModeracao -> :ServicoNotificacoes    |
| * 2.3.10     | `associarTagAoTopico(topicoCriado, tag)`                                        | Operação Lógica                              | :ModuloForum -> :BancoDeDados               |
| 2.3.11       | `indexarConteudo(topicoCriado)`                                                 | Operação Lógica                              | :ModuloForum -> :ServicoBusca               |
| 2.3.11.1     | `atualizarIndice(topicoCriado)`                                                 | Operação Lógica (Autochamada)                | :ServicoBusca -> :ServicoBusca              |
| 2.3.12       | `indexarConteudo(postagemInicial)`                                              | Operação Lógica                              | :ModuloForum -> :ServicoBusca               |
| 2.3.12.1     | `atualizarIndice(postagemInicial)`                                              | Operação Lógica (Autochamada)                | :ServicoBusca -> :ServicoBusca              |
| 2.3.13       | `notificarInscritos(idSubforum, topicoCriado)`                                  | Operação Lógica                              | :ModuloForum -> :ServicoNotificacoes        |
| 3            | `redirecionarParaTopico(idTopicoCriado)`                                        | Operação Lógica (Autochamada)                | :WebUI -> :WebUI                            |
| 4            | `exibirPaginaTopico(topicoCriado)`                                              | Operação Lógica                              | :WebUI -> entusiasta: Usuario               |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.


## Aba Jogos

Tabela 3: Participantes do Diagrama de Comunicação (Jogos Educacionais)

| #  | Elemento/Participante          | Descrição/Funcionalidade                                                                 |
|----|--------------------------------|------------------------------------------------------------------------------------------|
| 01  | `entusiasta : Usuario`         | O usuário final que interage com a plataforma para jogar.                                  |
| 02  | `: WebUI`                      | A interface com o usuário rodando no navegador, responsável por exibir e receber dados.      |
| 03  | `: APIGateway`                 | Ponto de entrada da API backend, recebe requisições da WebUI e direciona aos serviços.     |
| 04  | `: GestaoUsuarios`             | Componente responsável por gerenciar dados e permissões dos usuários.                      |
| 05  | `: ModuloJogos`                | Componente backend central para a lógica dos jogos (iniciar, registrar resultado, etc.).   |
| 06  | `jogoSel : Jogo`               | Instância específica da classe `Jogo`, contendo os dados/regras do jogo selecionado.        |
| 07  | `sessaoAtual : SessaoJogo`     | Instância que representa a partida atual do jogo (criada ao iniciar).                      |
| 08  | `: GestorAssetsEstaticos`      | Serviço responsável por fornecer URLs ou acesso aos arquivos de mídia do jogo (imagens, sons). |
| 09 | `: ServicoCache`               | Serviço (opcional) para armazenar temporariamente dados do jogo e acelerar o carregamento. |
| 10 | `: ModuloGamificacao`          | Componente backend responsável por aplicar regras de XP, conquistas e reputação.         |
| 11 | `perfilUsuario : Perfil`       | Instância da classe `Perfil`, contendo dados de progresso e XP do usuário.                |
| 12 | `: MotorRegrasGamificacao`     | Componente (ou conceito) que define como as recompensas (XP, conquistas) são calculadas.   |
| 13 | `: ServicoNotificacoes`        | Serviço responsável por enviar notificações ao usuário (ex: nova conquista).             |
| 14 | `: ServicoMonitoramento`       | Serviço para registrar logs de eventos importantes ou erros no sistema.                    |
| 15 | `: ServicoConfiguracao`        | Serviço para buscar configurações gerais da aplicação ou específicas de um jogo.           |
| 16 | `: BancoDeDados`               | Representa a camada de persistência onde todos os dados são armazenados/recuperados.      |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.



Tabela 4: Mensagens e Vínculos do Diagrama de Comunicação (Jogos Educacionais)


| Etapa   | Vínculo (Mensagem)                                                              | Tipo                                            | Origem -> Destino                        |
|---------|---------------------------------------------------------------------------------|-------------------------------------------------|------------------------------------------|
| 1       | `solicitarInicioJogo(idJogo, idUsuario?)`                                       | Operação Lógica                                 | :WebUI -> :APIGateway                    |
| 1.1     | `logEvento('req_inicio_jogo')`                                                  | Operação Lógica                                 | :APIGateway -> :ServicoMonitoramento     |
| 1.2     | `iniciarJogo(idJogo, idUsuario?)`                                               | Operação Lógica                                 | :APIGateway -> :ModuloJogos              |
| 1.2.1   | `getConfig(chave='jogo_config')`                                                | Operação Lógica                                 | :ModuloJogos -> :ServicoConfiguracao     |
| 1.2.2   | `getCacheJogo(idJogo)`                                                          | Operação Lógica                                 | :ModuloJogos -> :ServicoCache            |
| [cacheMiss] 1.2.3 | `buscarJogoDoBD(idJogo)`                                              | Operação Lógica                                 | :ModuloJogos -> :BancoDeDados            |
| 1.2.4   | `getUrlsAssets(jogoSel.assets)`                                                 | Operação Lógica                                 | :ModuloJogos -> :GestorAssetsEstaticos   |
| 1.2.5   | `sessaoAtual := <<create>> jogoSel.iniciar(entusiasta)`                         | Método da Classe (`Jogo.iniciar`)               | :ModuloJogos -> `jogoSel : Jogo`         |
| * 2     | `atualizarInterfaceJogo(estadoSessao)`                                          | Operação Lógica (Autochamada)                   | :WebUI -> :WebUI                         |
| * 2.1   | `getEstadoAtualizado()`                                                         | Operação Lógica/Método (`SessaoJogo` - implícito) | `sessaoAtual : SessaoJogo` -> :WebUI     |
| 3       | `submeterResultado(idSessao, pontuacao)`                                        | Operação Lógica                                 | :WebUI -> :APIGateway                    |
| 3.1     | `logEvento('submissao_resultado')`                                              | Operação Lógica                                 | :APIGateway -> :ServicoMonitoramento     |
| 3.2     | `registrarResultado(idSessao, pontuacao, idUsuario?)`                           | Operação Lógica                                 | :APIGateway -> :ModuloJogos              |
| 3.2.1   | `pontuacaoReg := jogoSel.registrarPontuacao(sessaoAtual)`                       | Método da Classe (`Jogo.registrarPontuacao`)    | :ModuloJogos -> `jogoSel : Jogo`         |
| 3.2.2   | `salvarPontuacaoBD(pontuacaoReg)`                                               | Operação Lógica                                 | :ModuloJogos -> :BancoDeDados            |
| [pontuacao > jogoSel.recorde] 3.2.3 | `atualizarRecordeBD(jogoSel, pontuacao)`            | Operação Lógica                                 | :ModuloJogos -> :BancoDeDados            |
| 3.3     | `idUsuarioLogado := getUsuarioDaSessao(idSessao)`                               | Operação Lógica                                 | :ModuloJogos -> :GestaoUsuarios          |
| [idUsuarioLogado != null] 3.4 | `registrarAcaoGamificacao('jogo_finalizado', idUsuarioLogado, pontuacaoReg)` | Operação Lógica                 | :ModuloJogos -> :ModuloGamificacao       |
| 3.4.1   | `getPerfilDoBD(idUsuarioLogado)`                                                | Operação Lógica                                 | :ModuloGamificacao -> :BancoDeDados      |
| 3.4.2   | `calcularRecompensas(acao, perfilUsuario, pontuacaoReg)`                        | Operação Lógica                                 | :ModuloGamificacao -> :MotorRegrasGamificacao |
| 3.4.3   | `perfilUsuario.adicionarXp(xpCalculado)`                                        | Método da Classe (`Perfil.adicionarXp`)         | :ModuloGamificacao -> `perfilUsuario : Perfil` |
| 3.4.4   | `salvarPerfilBD(perfilUsuario)`                                                 | Operação Lógica                                 | :ModuloGamificacao -> :BancoDeDados      |
| 3.4.5   | `verificarDesbloqueioConquista(...)`                                            | Operação Lógica                                 | :ModuloGamificacao -> :BancoDeDados      |
| [conquistaDesbloqueada] 3.4.6 | `enviarNotificacao(idUsuarioLogado, tipo='conquista', ...)` | Operação Lógica                 | :ModuloGamificacao -> :ServicoNotificacoes |
| 3.5     | `<<destroy>> finalizarSessaoJogo(sessaoAtual)`                                  | Operação Lógica                                 | :ModuloJogos -> `sessaoAtual : SessaoJogo` |
| 4       | `exibirFeedbackFinal(...)`                                                      | Operação Lógica                                 | :WebUI -> `entusiasta : Usuario`         |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

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
| 1.0 | Elaboração do documento| Larissa Stéfane | 01/05/2024 |
| 1.1 | Adição da metodologia e da seção de explicação  | Larissa Stéfane | 01/05/2024 |
| 1.2 | Criação das tabelas da aba fórum | Larissa Stéfane | 01/05/2024 |
| 1.3 | Criação das tabelas da aba de jogos | Larissa Stéfane | 02/05/2024 |
| 1.4 | Explicação dos diagramas de comunicação | Larissa Stéfane | 02/05/2024 |
