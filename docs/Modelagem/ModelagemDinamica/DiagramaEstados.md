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

## Introdução

O **diagrama de estados**, também conhecido como **diagrama de máquina de estados**, segundo [fonte: O que é um diagrama de máquina de estados?](https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml) [1](#ref1), é um tipo de diagrama comportamental da UML (Unified Modeling Language) utilizado para representar o comportamento dinâmico de um objeto ao ilustrar os estados que ele pode assumir ao longo do tempo e as transições causadas por eventos específicos. Com isso, com base no artigo [State Machine Diagrams](https://www.uml-diagrams.org/state-machine-diagrams.html) [3](#ref3), esse tipo de modelagem é especialmente útil para descrever sistemas reativos e orientados a eventos em que as ações dependem das entradas recebidas e permiti visualizar como o objeto responde a diferentes estímulos durante sua existência.

No contexto do projeto Galáxia Conectada, serão elaborados dois diagramas de estados com base nas abas de **Fórum** e **Promoções**. Para isso, será descrito o comportamento de componentes interativos do sistema e as transições de estado que ocorrem nessas temáticas.

## Objetivos

O objetivo deste documento é representar, por meio de diagramas de estados, os comportamentos dinâmicos de elementos interativos dos módulos das promoções e do fórum da plataforma Galáxia Conectada. De forma mais específica, busca-se:

- Representar os diferentes estados que determinados objetos da plataforma podem assumir durante sua execução;

- Demonstrar as transições de estado com base em eventos, ações ou interações do usuário;

- Auxiliar na compreensão dos fluxos internos e das mudanças comportamentais dos componentes da plataforma;

- Apoiar a modelagem de sistemas reativos e orientados a eventos com uma representação visual clara e estruturada.


## Metodologia

A elaboração dos diagramas de estados será realizada com base na integração de artefatos previamente desenvolvidos no projeto da Galáxia Conectada, com o objetivo de representar visualmente os comportamentos dinâmicos de elementos interativos da plataforma. Assim, serão desenvolvidos **dois diagramas principais**, sendo um voltado para a **aba de promoções** e outro para a **aba de fórum**. 

- **Módulo de Promoções Astronômicas**: Este módulo funciona como um agregador de ofertas, ao buscar e exibir promoções e descontos relevantes para entusiastas da astronomia (como livros, telescópios, etc.). Essas promoções serão capturadas por bots de sites de e-commerce externos. 

- **Módulo de Fórum de Discussões:** É a área interativa da plataforma onde os usuários podem criar tópicos, fazer perguntas, compartilhar conhecimentos, responder a outros membros e discutir sobre astronomia e conteúdos relacionados. Com isso, o objetivo central é construir uma comunidade ativa, facilitar a troca de informações e o aprendizado entre pares, aumentar o engajamento e a retenção dos usuários na "Galáxia Conectada" através da interação social.


Para a construção dos diagramas, serão seguidas as etapas abaixo:

1. Inicialmente, serão analisados os seguintes artefatos como base para definição dos estados e transições:

  - [Requisitos Funcionais e Não Funcionais elicitados - Elaborados na entrega 1](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/IniciativaExtra/RequisitosElicitados);

  - [Diagrama de Classe](/Modelagem/ModelagemEstatica/DiagramaClasses.md);
    
  - [Diagrama de Componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md).


2. Os diagramas serão desenvolvidos utilizando a ferramenta [Draw.io](https://www.drawio.com/blog/uml-component-diagrams);

3. Será realizada uma verificação final com base em um [checklist](/Modelagem/IniciativasExtras/Verificacao/VerificacaoDiagramaEstados.md) de boas práticas da UML, assegurando clareza, coerência e padronização na modelagem.

## Sobre o Diagrama de Estados

Os Diagramas de Máquina de Estados a seguir ilustram o ciclo de vida e o comportamento dinâmico das entidades Promoção e Fórum dentro da plataforma "Galáxia Conectada". Sendo assim, com base em [State Machine Diagrams](https://www.uml-diagrams.org/state-machine-diagrams.html) [3](#ref3) e [UML 2 Tutorial - State Machine Diagram
](https://sparxsystems.com/resources/tutorials/uml2/state-diagram.html) [2](#ref2), eles mapeiam os diversos Estados possíveis para essas entidades (como Pendente Validação, Ativa, Fechado) e as Transições (setas) que ocorrem entre eles. Essas mudanças de estado são acionadas por Eventos específicos (ações do sistema, usuário ou tempo) e podem depender de Condições de Guarda ([]), frequentemente executando Ações (/) durante a transição. Para representar detalhadamente os fluxos, foram utilizados elementos como Estados Compostos (agrupando Subestados), Ações de Entrada/Saída/Do (entry/exit/do) e, no caso do Fórum, Regiões Ortogonais para modelar concorrência, o que permite uma visualização clara das regras que governam o comportamento dessas entidades ao longo do tempo.

Para melhor compreensão dos diagramas, a figura 1 mostra a legenda;

<div align="center">
    Figura 1: Legenda do Diagrama de Estados
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/refs/heads/main/docs/Modelagem/Imagens/LegendaDiagramaEstados.drawio.png" width="500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>


**Observação Importante:** Com o intuido de elaborar melhor os diagramas, foram elaboradas tabelas contendo os estados com suas descrições e relação com os requisitos elicitados e com os componentes do diagrama de componentes **(Tabelas 1 e 3)**. 
Da mesma forma, foram criadas tabelas que mostram as transições entre os estados. **(Tabelas 2 e 4)**

## Aba Promoção

O Diagrama de Máquina de Estados para o módulo de Promoções ilustra as diversas fases pelas quais uma PromocaoExterna pode passar ao longo de seu ciclo de vida na plataforma "Galáxia Conectada". Para detalhar e clarificar cada uma dessas fases, a Tabela 1 a seguir apresenta e descreve os diferentes estados definidos.


<details>
  <summary><strong>Tabela 1: Estados do Ciclo de Vida da Promoção</strong></summary>

**Tabela 1: Estados do Ciclo de Vida da Promoção** 

| #  | EEstados                     | Descrição                                                                    | Relação com Requisitos (Exemplos) | Relação com Componentes (Gerenciador Principal) |
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

</details>

Para complementar a compreensão dos estados de uma PromocaoExterna, a Tabela 2 se aprofunda nas transições que governam as mudanças entre esses diferentes estágios, conforme representado no Diagrama de Máquina de Estados do módulo de promoções. Esta tabela visa especificar os eventos gatilho (triggers), as condições de guarda (guards) que devem ser satisfeitas e as ações (actions) que são executadas durante cada mudança de estado. Ao fornecer esta visão estruturada, a tabela auxilia na leitura do diagrama.

<details>
  <summary><strong>Tabela 2: Transições do Ciclo de Vida da Promoção Externa</strong></summary>


**Tabela 2: Transições do Ciclo de Vida da Promoção Externa**


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

</details>

A Figura 2 mostra o diagrama de estados das promoções

<div align="center">
    <b>Figura 2:</b> o Diagrama de Estados – Promoções
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaEstadosPromocao.drawio.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
</div>

<p><strong>Observação:</strong> Caso deseje visualizar ou baixar em PDF, clique aqui: 
<a href="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaEstadosPromocao.drawio.pdf">PDF do Diagrama de Estados – Promoções</a></p>



## Aba Fórum

O comportamento dinâmico de um Topico dentro do Fórum da plataforma "Galáxia Conectada" é modelado através de um Diagrama de Máquina de Estados específico, e para um entendimento aprofundado dos estágios possíveis desta entidade, a Tabela 3 subsequente descreve cada um dos estados que um tópico pode assumir.

<details>
  <summary><strong>Tabela 3: Estados do Ciclo de Vida do Tópico do Fórum</strong></summary>


**Tabela 3: Estados do Ciclo de Vida do Tópico do Fórum**

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

</details>



A evolução de um Topico do Fórum entre seus diversos estados é regida por transições específicas, as quais são detalhadas na Tabela 4. Esta tabela serve como um complemento fundamental ao Diagrama de Máquina de Estados dos Tópicos, explicando as dinâmicas de mudança de estado. Seu propósito é elucidar os eventos disparadores (como uma ação de um Moderador ou um critério temporal), as condições de guarda que precisam ser atendidas para que a transição ocorra, e as ações que podem ser executadas como resultado dessa mudança (por exemplo, de 'Aberto' para 'Fechado'). Dessa maneira, ao apresentar essas informações de forma organizada, a tabela auxilia na compreensão das regras que ditam o comportamento e o fluxo de vida dos tópicos no Fórum.


<details>
  <summary><strong>Tabela 4: Transições do Ciclo de Vida do Tópico do Fóruns
</strong></summary>

**Tabela 4**: Transições do Ciclo de Vida do Tópico do Fóruns


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

</details>

A figura 3 apresenta o diagrama de estados do Fórum

<div align="center">
    <b>Figura 3:</b> o Diagrama de Estados – Fórum
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaEstadosForum.drawio.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
</div>

<p><strong>Observação:</strong> Caso deseje visualizar ou baixar em PDF, clique aqui: 
<a href="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaEstadosForum.drawio.pdf">PDF do Diagrama de Estados – Fórum</a></p>


## Conclusão

Em suma, os Diagramas de Máquina de Estados detalhados nesta seção forneceram uma modelagem visual dos ciclos de vida das entidades de Promoção e do fórum, essenciais para a plataforma "Galáxia Conectada". Através da aplicação de elementos fundamentais e avançados da UML, como estados compostos, regiões ortogonais, condições de guarda e ações específicas de estado (entry/exit/do), foi possível representar de forma clara e precisa as complexas sequências de estados, os eventos que disparam as transições e as regras que governam o comportamento dessas entidades.

## Bibliografia

<a name="ref1"></a>
[1] LUCIDCHART. O que é um diagrama de máquina de estados? Disponível em: https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml. Acesso em: 4 maio 2025.

<a name="ref2"></a>
[2] SPARX SYSTEMS. UML 2 Tutorial – State Machine Diagram. Disponível em: https://sparxsystems.com/resources/tutorials/uml2/state-diagram.html. Acesso em: 4 maio 2025.

<a name="ref3"></a>
[3] UML-DIAGRAMS. State Machine Diagrams. Disponível em: https://www.uml-diagrams.org/state-machine-diagrams.html. Acesso em: 4 maio 2025.

<a name="ref4"></a>
[4] IBM. Máquinas de Estado. Disponível em: https://www.ibm.com/docs/pt-br/dmrt/9.5.0?topic=diagrams-state-machines. Acesso em: 4 maio 2025.

<a name="ref5"></a>
[5] RAMOS, Ricardo Argenton. UML – Aula III: Diagramas de Estado, Atividades, Componentes e Instalação. Engenharia de Software II, 2013.1. Disponível em: http://www.univasf.edu.br/~ricardo.aramos/disciplinas/ES_II_2013_1/UML_Aula3.pdf. Acesso em: 4 maio 2025.

## Histórico de versão

| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 04/05/2025 |
| 1.1 | Adição do seção de explicação  | Larissa Stéfane | 04/05/2025 |
| 1.2 | Criação das tabelas da aba de promoção | Larissa Stéfane | 04/05/2025 |
| 1.3 | Criação das tabelas da aba de fórum | Larissa Stéfane | 04/05/2025 |
| 1.4 |Complementação das tabelas | Larissa Stéfane | 04/05/2025 |
| 1.5 | Adição dos Diagramas | Larissa Stéfane | 04/05/2025 |
| 1.6 | Adição da conclusão | Larissa Stéfane | 04/05/2025 |
| 1.7 | Ajustes no artefato| Larissa Stéfane | 06/05/2025 |
