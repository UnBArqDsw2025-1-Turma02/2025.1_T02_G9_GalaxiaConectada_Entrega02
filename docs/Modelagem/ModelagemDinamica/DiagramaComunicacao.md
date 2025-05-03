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

O diagrama de colaboração (ou de comunicação), como é definido na Apostila UML - Unified Modeling Language - Linguagem de Modelagem Unificada em Português [1](#ref1), representa como os objetos de um sistema interagem entre si ao focar nos relacionamentos e nas trocas de mensagens, mais do que na ordem temporal dessas ações. Segundo a IBM [https://www.ibm.com/docs/pt-br/radfws/9.6.0?topic=SSRTLW_9.6.0/com.ibm.xtools.sequence.doc/topics/ccommndiag.htm], esse tipo de diagrama permite analisar o comportamento dinâmico do sistema ao identificar objetos participantes, dados trocados e caminhos de mensagens. 

Dessa forma, como o desenvolvimento de diagramas de comunicação é essencial para visualizar como os componentes e objetos do sistema interagem entre si, especialmente em áreas com maior troca de mensagens, esse artefato apresenta os diagramas de comunicação para a aba de fórum e a aba de jogos. 




## Aba Jogos

Tabela 1: Participantes do Diagrama de Comunicação (Jogos Educacionais)

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



Tabela 2: Mensagens e Vínculos do Diagrama de Comunicação (Jogos Educacionais)


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
