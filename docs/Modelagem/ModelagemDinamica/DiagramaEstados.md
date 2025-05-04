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
