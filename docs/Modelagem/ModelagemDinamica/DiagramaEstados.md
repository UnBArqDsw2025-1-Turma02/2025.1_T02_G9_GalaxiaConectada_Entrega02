# Diagrama de Estados

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Sobre o Diagrama de Estados](#Sobre-o-Diagrama-de-Estados)
- [Aba Promoção](#Aba-Promoção)
- [Aba Fórum](#Aba-Fórum)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)


## Aba Promoção

Tabela 1: Estados do Ciclo de Vida da Promoção Externa

| #  | Elemento                      | Descrição                                                                    | Relação com Requisitos (Exemplos) | Relação com Componentes (Gerenciador Principal) |
|----|-------------------------------|------------------------------------------------------------------------------|-----------------------------------|---------------------------------------------------|
| 1  | ⚫ (Estado Inicial)           | Ponto de entrada, representa a criação ou descoberta inicial da promoção.   | Implícito para RF19               | :BotImportadorPromocoes (#33)                     |
| 2  | `Recém Descoberta`            | A promoção foi identificada pelo bot, mas ainda não processada internamente.   | Implícito para RF19               | :BotImportadorPromocoes (#33), :ModuloPromocoes (#31) |
| 3  | `Pendente Validação Automática` | Aguardando a execução de verificações automáticas (ex: link válido, loja ok). | Suporte à qualidade para RF19     | :ModuloPromocoes (#31)                            |
| 4  | `Aguardando Validação Manual` | Falha/Inconclusão na validação automática, requer intervenção humana.         | Suporte à qualidade para RF19     | :ModuloPromocoes (#31), :ModuloModeracao (#28)    |
| 5  | `Rejeitada`                   | A promoção foi considerada inválida (manual ou automaticamente).               | Suporte à qualidade para RF19     | :ModuloPromocoes (#31), :ModuloModeracao (#28)    |
| 6  | `Aprovada (Aguardando Pub.)`  | Validada, mas ainda não está visível para os usuários (pode ter agendamento). | Suporte à qualidade para RF19     | :ModuloPromocoes (#31)                            |
| 7  | `Ativa (Visível)`             | **(Estado Composto)** Promoção visível e válida para os usuários. Contém subestados. | RF19                              | :ModuloPromocoes (#31)                            |
| 8  | `-> Listada Normalmente`       | Subestado de `Ativa`: Visível na listagem padrão.                            | RF19                              | :ModuloPromocoes (#31)                            |
| 9  | `-> Agendada para Destaque`    | Subestado de `Ativa`: Marcada para se tornar destaque em breve.              | RF19, (Relacionado a RF25 - Populares) | :ModuloPromocoes (#31), :ServicoRecomendacoes (#15)? |
| 10 | `-> Em Destaque`              | Subestado de `Ativa`: Visível com maior proeminência (ex: banner, topo lista). | RF19, (Relacionado a RF25 - Populares) | :ModuloPromocoes (#31), :ServicoRecomendacoes (#15)? |
| 11 | `Suspensa Temporariamente`    | Visibilidade interrompida por um administrador, mas pode ser reativada.      | Gerenciamento (Implícito)         | :ModuloPromocoes (#31)                            |
| 12 | `Expirada`                    | A data de validade da promoção foi atingida. Não deve mais ser mostrada.     | Suporte à validade para RF19    | :ModuloPromocoes (#31)                            |
| 13 | `Pendente de Remoção/Arq.`   | Estado intermediário após expirar ou ser rejeitada, antes do arquivamento.    | Gerenciamento (Implícito)         | :ModuloPromocoes (#31)                            |
| 14 | `Arquivada`                   | Dados movidos para histórico, não mais acessíveis diretamente pelos usuários.   | Gerenciamento (Implícito)         | :ModuloPromocoes (#31)                            |
| 15 | ⊚ (Estado Final)              | O ciclo de vida da promoção no sistema terminou (dados podem ser removidos). | Gerenciamento (Implícito)         | :ModuloPromocoes (#31)                            |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

Tabela 2: Transições do Ciclo de Vida da Promoção Externa


| Elementos entre a transição                    | Rótulo da transição                                                              | Relação com Requisitos (Exemplos)      | Relação com Componentes (Evento / Ação)                                       |
|------------------------------------------------|------------------------------------------------------------------------------------|----------------------------------------|-------------------------------------------------------------------------------|
| ⚫ -> `Recém Descoberta`                         | *(implícito)* | Implícito RF19                         | :BotImportadorPromocoes (#33)                                                 |
| `Recém Descoberta` -> `Pendente Val. Automática` | `botRegistraPromoção / salvarInfoInicialBD()`                                    | Implícito RF19                         | :BotImportadorPromocoes (#33) / :ModuloPromocoes (#31) via :BancoDeDados (#34) |
| `Pendente Val. Automática` -> `Aprovada (...)`   | `validacaoAutomaticaConcluida [resultado=OK] / registrarValidacaoOK()`             | Suporte RF19                           | :ModuloPromocoes (#31) / :ModuloPromocoes (#31) via :BancoDeDados (#34)       |
| `Pendente Val. Automática` -> `Aguardando Val. Manual` | `validacaoAutomaticaConcluida [resultado=Inconclusivo OU Falha] / marcarParaRevisaoManual()` | Suporte RF19                           | :ModuloPromocoes (#31) / :ModuloPromocoes (#31) via :BancoDeDados (#34)       |
| `Aguardando Val. Manual` -> `Aprovada (...)`   | `moderadorAprova [validacaoManual=OK] / registrarAprovacaoManual()`              | Suporte RF19                           | :ModuloModeracao (#28) / :ModuloPromocoes (#31) via :BancoDeDados (#34)       |
| `Aguardando Val. Manual` -> `Rejeitada`          | `moderadorRejeita [validacaoManual=Falha] / registrarRejeicaoManual()`           | Suporte RF19                           | :ModuloModeracao (#28) / :ModuloPromocoes (#31) via :BancoDeDados (#34)       |
| `Aprovada (...)` -> `Ativa (Visível)`            | `agendadorPublica / tornarVisivelNosListings(), notificarServicoBusca()`         | RF19                                   | Agendador ou :ModuloPromocoes (#31) / :ModuloPromocoes (#31), :ServicoBusca (#14)|
| `Listada Normalmente` -> `Agendada Destaque`     | `sistemaDetectaPopularidade [isPopular] / agendarDestaque()`                     | RF19, (RF25)                           | :ModuloPromocoes (#31) ou :ServicoRecomendacoes (#15) / :ModuloPromocoes (#31) |
| `Agendada Destaque` -> `Em Destaque`             | `agendadorAplicaDestaque / atualizarFlagDestaqueBD(true)`                          | RF19, (RF25)                           | Agendador ou :ModuloPromocoes (#31) / :ModuloPromocoes (#31) via :BD (#34)     |
| `Em Destaque` -> `Listada Normalmente`         | `popularidadeDiminui [isNaoMaisPopular] / atualizarFlagDestaqueBD(false)`         | RF19, (RF25)                           | :ModuloPromocoes (#31) / :ModuloPromocoes (#31) via :BD (#34)                 |
| `Agendada Destaque` -> `Listada Normalmente`     | `adminCancelaDestaque / cancelarAgendamentoDestaque()`                           | Gerenciamento                          | Admin via :ModuloPromocoes (#31) / :ModuloPromocoes (#31)                   |
| `Ativa (Visível)` -> `Suspensa Temporariamente`  | `adminSuspende / ocultarPromoção(), notificarUsuarioResponsavel()`               | Gerenciamento                          | Admin via :ModuloPromocoes (#31) / :ModuloPromocoes (#31), :ServicoNotificacoes (#13) |
| `Suspensa Temporariamente` -> `Ativa (Visível)`  | `adminReativa / tornarVisivelNovamente()`                                        | Gerenciamento                          | Admin via :ModuloPromocoes (#31) / :ModuloPromocoes (#31)                   |
| `Ativa (Visível)` -> `Expirada`                  | `when(dataAtual >= dataValidade) / marcarComoExpiradaBD(), notificarServicoBuscaRemover()` | Suporte RF19                           | :ModuloPromocoes (#31) / :ModuloPromocoes (#31) via :BD (#34), :ServicoBusca (#14) |
| `Expirada` -> `Pendente de Remoção/Arq.`        | `verificacaoPosExpiracaoConcluida / prepararParaArquivamento()`                  | Gerenciamento                          | :ModuloPromocoes (#31) / :ModuloPromocoes (#31)                               |
| `Rejeitada` -> `Pendente de Remoção/Arq.`       | `processoLimpezaRejeitadas / prepararParaArquivamento()`                         | Gerenciamento                          | :ModuloPromocoes (#31) / :ModuloPromocoes (#31)                               |
| `Pendente de Remoção/Arq.` -> `Arquivada`      | `jobArquivamentoExecutado / moverDadosParaHistorico(), removerDosListingsAtivos()` | Gerenciamento                          | Agendador ou :ModuloPromocoes (#31) / :ModuloPromocoes (#31) via :BD (#34)     |
| `Arquivada` -> ⊚ (Final)                        | `after(X meses) / removerDadosFinais()`                                          | Gerenciamento                          | Agendador ou :ModuloPromocoes (#31) / :ModuloPromocoes (#31) via :BD (#34)     |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

## Aba Fórum

Tabela 3: Estados do Ciclo de Vida do Tópico do Fórum

| #  | Elemento                      | Descrição                                                                                    | Relação com Requisitos (Exemplos)      | Relação com Componentes (Gerenciador/Influenciador)                                    |
|----|-------------------------------|----------------------------------------------------------------------------------------------|----------------------------------------|--------------------------------------------------------------------------------------|
| 1  | ⚫ (Estado Inicial)           | Ponto de entrada quando um usuário começa a criar um novo tópico.                              | Implícito para RF09                    | :WebUI, :ModuloForum (#26)                                                            |
| 2  | `Em Rascunho`                 | O tópico foi iniciado pelo usuário, mas ainda não foi submetido.                             | Implícito para RF09                    | :WebUI, :ModuloForum (#26), :BancoDeDados (#34)                                       |
| 3  | `Aguardando Moderação Inicial`| **(Composto)** Tópico submetido, aguardando análise inicial da moderação antes de ser visível. | Suporte à qualidade/regras para RF09   | :ModuloForum (#26), :ModuloModeracao (#28), :ServicoNotificacoes (#13)                 |
| 4  | `-> Análise Pendente`         | Subestado: Aguardando um moderador pegar o tópico para análise.                               | Suporte RF09                           | :ModuloModeracao (#28)                                                               |
| 5  | `-> Revisado (Aprovado)`      | Subestado: Moderador analisou e aprovou o tópico para publicação.                            | Suporte RF09                           | :ModuloModeracao (#28), :BancoDeDados (#34)                                           |
| 6  | `-> Revisado (Rejeitado)`     | Subestado: Moderador analisou e rejeitou o tópico.                                           | Suporte RF09                           | :ModuloModeracao (#28), :BancoDeDados (#34), :ServicoNotificacoes (#13)                 |
| 7  | `-> ⊚ (Aprovação Concluída)`   | Estado Final Interno: Fim do fluxo de moderação com aprovação.                               | Suporte RF09                           | :ModuloModeracao (#28)                                                               |
| 8  | `-> ⊚ (Rejeição Concluída)`   | Estado Final Interno: Fim do fluxo de moderação com rejeição.                                | Suporte RF09                           | :ModuloModeracao (#28)                                                               |
| 9  | `Visível`                     | **(Composto com Regiões)** Tópico publicado e visível para os usuários no fórum.             | RF09, RF25                             | :ModuloForum (#26), :ServicoBusca (#14), :ServicoNotificacoes (#13)                     |
| 10 | `--> (Região: Status Atividade)` | *Região Ortogonal dentro de Visível.* | RF09                                   | :ModuloForum (#26)                                                                   |
| 11 | `----> Ativo`                 | **(Composto)** Subestado de Visível: Tópico aberto para novas postagens e interações.        | RF09, RF24, RF25                       | :ModuloForum (#26)                                                                   |
| 12 | `------> Normal`              | Sub-subestado de Ativo: Atividade normal de postagens.                                       | RF09, RF24                             | :ModuloForum (#26)                                                                   |
| 13 | `------> Debate Intenso`      | Sub-subestado de Ativo: Alta frequência de postagens, pode indicar popularidade.             | RF09, RF24, (RF25)                     | :ModuloForum (#26)                                                                   |
| 14 | `------> Aguardando Resposta OP`| Sub-subestado de Ativo: Tópico aguardando esclarecimento do autor original.                 | RF09, RF24                             | :ModuloForum (#26), :ServicoNotificacoes (#13)                                         |
| 15 | `------> ⊚ (Resolvido)`       | Estado Final Interno de Ativo: Tópico marcado como resolvido pelo autor original.          | RF09                                   | :ModuloForum (#26), :ServicoNotificacoes (#13)                                         |
| 16 | `--> Fechado`                 | **(Composto)** Subestado de Visível: Tópico visível, mas trancado para novas postagens.      | RF09 (Implícito - gerenciamento)       | :ModuloForum (#26), :ModuloModeracao (#28)                                             |
| 17 | `----> Por Inatividade`       | Sub-subestado de Fechado: Trancado automaticamente por falta de atividade.                  | Gerenciamento                          | :ModuloForum (#26)                                                                   |
| 18 | `----> Por Moderador`         | Sub-subestado de Fechado: Trancado por um moderador.                                        | Gerenciamento                          | :ModuloModeracao (#28)                                                               |
| 19 | `----> Por OP`                | Sub-subestado de Fechado: Trancado pelo autor original (se permitido).                      | Gerenciamento                          | :ModuloForum (#26)                                                                   |
| 20 | `--> (Região: Status Destaque)`| *Região Ortogonal dentro de Visível.* | Gerenciamento                          | :ModuloModeracao (#28)                                                               |
| 21 | `----> Não Pinado`            | Subestado de Visível: Tópico com visibilidade padrão (não fixo no topo).                     | RF09                                   | :ModuloForum (#26)                                                                   |
| 22 | `----> Pinado`                | Subestado de Visível: Tópico fixado no topo do subfórum para maior visibilidade.           | Gerenciamento                          | :ModuloModeracao (#28), :ModuloForum (#26)                                             |
| 23 | `Arquivado`                   | Tópico removido da visualização principal, guardado em área de histórico.                  | Gerenciamento                          | :ModuloForum (#26), :BancoDeDados (#34)                                               |
| 24 | `Excluído Permanentemente`    | Tópico marcado para exclusão ou já removido completamente do sistema.                      | Gerenciamento                          | :ModuloForum (#26), :BancoDeDados (#34), :ServicoMonitoramento (#6)                   |
| 25 | ⊚ (Estado Final Principal)    | Fim definitivo do ciclo de vida do tópico no sistema.                                      | Gerenciamento                          | :ModuloForum (#26), :BancoDeDados (#34)                                               |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.







Tabela 4: Transições do Ciclo de Vida do Tópico do Fórum


| Elementos entre a transição                                    | Rótulo da transição                                                                          | Relação com Requisitos (Exemplos) | Relação com Componentes (Evento / Ação)                                                            |
|----------------------------------------------------------------|----------------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------------------------------------------------------------|
| ⚫ -> `Em Rascunho`                                              | `usuarioIniciaCriacao / criarRascunhoTopico()`                                               | Implícito RF09                    | :WebUI / :ModuloForum(#26) via :BD(#34)                                                            |
| `Em Rascunho` -> `Aguardando Moderação Inicial`                 | `usuarioSubmete / salvarConteudoFinal(), notificarModeracaoPendente()`                         | RF09                              | :WebUI / :ModuloForum(#26) via :BD(#34), :ServicoNotificacoes(#13)                                  |
| `Em Rascunho` -> `Excluído Permanentemente`                     | `usuarioCancelaCriacao / descartarRascunho()`                                                 | Gerenciamento                     | :WebUI / :ModuloForum(#26) via :BD(#34)                                                            |
| (Dentro Moderação) ⚫ -> `Análise Pendente`                       | *(implícito)* | Suporte RF09                    | :ModuloModeracao(#28)                                                              |
| (Dentro Moderação) `Análise Pendente` -> `Revisado (Aprovado)`  | `moderadorAprova / registrarAprovacao(), atualizarStatusTopicoBD('Aprovado')`                  | Suporte RF09                    | :ModuloModeracao(#28) / :ModuloModeracao(#28) via :BD(#34)                                         |
| (Dentro Moderação) `Análise Pendente` -> `Revisado (Rejeitado)` | `moderadorRejeita / registrarRejeicao(), notificarUsuarioRejeicao()`                         | Suporte RF09                    | :ModuloModeracao(#28) / :ModuloModeracao(#28) via :BD(#34), :ServicoNotificacoes(#13)               |
| (Dentro Moderação) `Revisado (Aprovado)` -> ⊚ (Aprovação)       | *(implícito)* | Suporte RF09                    | :ModuloModeracao(#28)                                                              |
| (Dentro Moderação) `Revisado (Rejeitado)` -> ⊚ (Rejeição)       | *(implícito)* | Suporte RF09                    | :ModuloModeracao(#28)                                                              |
| Borda(`Aguardando Moderação`) -> `Visível`                     | `[resultado=Aprovado] / publicarTopico(), indexarConteudoInicial()`                            | RF09                              | :ModuloModeracao(#28) / :ModuloForum(#26), :ServicoBusca(#14)                                      |
| Borda(`Aguardando Moderação`) -> `Excluído Permanentemente`    | `[resultado=Rejeitado] / marcarParaExclusaoBD()`                                             | Gerenciamento                     | :ModuloModeracao(#28) / :ModuloForum(#26) via :BD(#34)                                             |
| (Dentro Visível/Reg1) ⚫ -> `Ativo`                               | *(implícito)* | RF09                              | :ModuloForum(#26)                                                                  |
| (Dentro Ativo) ⚫ -> `Normal`                                     | *(implícito)* | RF09                              | :ModuloForum(#26)                                                                  |
| (Dentro Ativo) `Normal` -> `Debate Intenso`                       | `atividadeAumenta [posts>limite] / marcarComoIntenso()`                                      | RF09, RF25                        | :ModuloForum(#26) / :ModuloForum(#26)                                                            |
| (Dentro Ativo) `Debate Intenso` -> `Normal`                       | `atividadeDiminui / desmarcarComoIntenso()`                                                  | RF09, RF25                        | :ModuloForum(#26) / :ModuloForum(#26)                                                            |
| (Dentro Ativo) `Normal` -> `Aguardando Resposta OP`               | `after(3 dias sem resposta OP) / notificarOP()`                                              | RF09                              | Timer / :ServicoNotificacoes(#13)                                                                |
| (Dentro Ativo) `Aguardando Resposta OP` -> `Normal`               | `opResponde`                                                                                 | RF09                              | :ModuloForum(#26)                                                                  |
| (Dentro Ativo) `Normal` OR `Debate` OR `Aguardando` -> ⊚ (Resolvido) | `opMarcaResolvido / notificarParticipantesResolucao()`                                     | RF09                              | :ModuloForum(#26) / :ServicoNotificacoes(#13)                                                    |
| (Dentro Visível/Reg1) `Ativo` -> `Fechado`                       | `tempoInatividadeAtingido OR moderadorTranca OR opTranca / registrarMotivoFechamento()`        | Gerenciamento (RF09)            | Timer/:ModuloModeracao(#28)/:ModuloForum(#26) / :ModuloForum(#26) via :BD(#34)                   |
| (Dentro Visível/Reg2) ⚫ -> `Não Pinado`                          | *(implícito)* | Gerenciamento                     | :ModuloForum(#26)                                                                  |
| (Dentro Visível/Reg2) `Não Pinado` -> `Pinado`                    | `moderadorPina / atualizarFlagPinBD(true)`                                                   | Gerenciamento                     | :ModuloModeracao(#28) / :ModuloForum(#26) via :BD(#34)                                             |
| (Dentro Visível/Reg2) `Pinado` -> `Não Pinado`                    | `moderadorDespina / atualizarFlagPinBD(false)`                                                 | Gerenciamento                     | :ModuloModeracao(#28) / :ModuloForum(#26) via :BD(#34)                                             |
| Borda(`Visível`) -> `Arquivado`                                 | `adminArquiva OR after(1 ano inatividade) / moverParaArquivoHistorico()`                     | Gerenciamento                     | Admin ou Timer / :ModuloForum(#26) via :BD(#34)                                                |
| Borda(`Visível`) -> `Excluído Permanentemente`                  | `adminExcluiTopico / marcarParaExclusaoComLog()`                                             | Gerenciamento                     | Admin via :ModuloForum(#26) / :ModuloForum(#26) via :BD(#34), :ServicoMonitoramento(#6)         |
| `Arquivado` -> ⊚ (Final Principal)                              | `after(5 anos) / removerDadosArquivados()`                                                   | Gerenciamento                     | Timer / :ModuloForum(#26) via :BD(#34)                                                           |
| `Excluído Permanentemente` -> ⊚ (Final Principal)               | *(implícito ou via job)* | Gerenciamento                     | :ModuloForum(#26) via :BD(#34)                                                               |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
