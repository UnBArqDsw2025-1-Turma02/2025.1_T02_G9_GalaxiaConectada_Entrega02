# Diagrama de Atividades

## Sumário

- [Introdução](#Introdução)
- [Objetivos](#Objetivos)
- [Metodologia](#Metodologia)
- [Sobre o Diagrama de Atividades](#Sobre-o-Diagrama-de-Atividades)
- [Aba Conhecimento Trilhas de Aprendizado](#Aba-Conhecimento-Trilhas-de-Aprendizado)
- [Aba Científico Notícias e Artigos](#Aba-Científico-Notícias-e-Artigos)
- [Conclusão](#Conclusão)
- [Bibliografia](#Bibliografia)
- [Histórico de versão](#Histórico-de-versão)


## Introdução

A plataforma Galáxia Conectada está sendo desenvolvida na disciplina como uma solução digital abrangente para o ensino e divulgação da Astronomia. Com isso, para organizar e representar um pouco o comportamento e os fluxos de processos do sistema, foram elaborados dois diagramas de atividade conforme a notação UML (Unified Modeling Language).

Segundo a Apostila UML - Unified Modeling Language - Linguagem de Modelagem Unificada em Português [1](#ref1), os diagramas de atividade são uma forma de representar o fluxo sequencial das ações realizadas por uma operação do sistema ao evidenciar as mudanças de estado dos objetos envolvidos, a ordem de execução e a responsabilidade pelas tarefas por meio de raias (swimlanes). Sendo assim, eles são especialmente úteis para modelar fluxos de trabalho, decisões, execuções paralelas e resultados esperados. Além disso, conforme destaca a [IBM](https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-activity), esses diagramas são semelhantes a fluxogramas, mas com maior capacidade de representar fluxos paralelos e alternativos.

## Objetivos

O objetivo deste documento é algumas das atividades desenvolvidas para a plataforma Galáxia Conectada ao evidenciar os principais fluxos funcionais e comportamentais do sistema. De forma mais específica, busca-se:

- Ilustrar os principais processos internos da plataforma;

- Demonstrar a responsabilidade dos atores e componentes por meio das raias;

- Evidenciar os pontos de decisão, bifurcação e encerramento dos fluxos;

- Apoiar a modelagem comportamental dos casos de uso com uma representação visual precisa.

## Metodologia

A elaboração dos diagramas de atividade seguirá uma abordagem baseada na integração entre diferentes artefatos desenvolvidos anteriormente no projeto Galáxia Conectada. Isso com o  objetivo será representar visualmente o fluxo das ações executadas pelos usuários e pelo sistema em dois módulos principais da plataforma: **a aba Conhecimento (trilhas de aprendizado)** e a **aba Científico (notícias e artigos científicos)**.

- **Módulo de Trilhas de Aprendizado**: Esta é a espinha dorsal educacional da plataforma "Galáxia Conectada", oferecendo aos usuários entusiastas roteiros de estudo estruturados, conhecidos como "trilhas". Essas trilhas são cuidadosamente organizadas por tema (ex: Sistema Solar, Cosmologia), nível de dificuldade (iniciante a avançado) e categoria (RF01), e são apresentadas de forma lúdica, como "missões espaciais" (RF03), para aumentar o engajamento. 

- **Módulo Científico: Notícias e Artigos**: uncionando como o centro de divulgação científica da plataforma, esta aba agrega e apresenta conteúdo atualizado sobre astronomia. Ela inclui um blog com artigos explicativos, possivelmente um glossário de termos técnicos (RF13), e notícias recentes do mundo científico, muitas das quais podem ser importadas e até traduzidas (RNF07) de fontes externas confiáveis (como portais da NASA) através de bots (RF14). 

 Para isso, serão feitas as seguintes etapas:

1. inicialmente serão realizadas análises dos seguintes artefatos:
     - [5W2H](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/ArtefatoGeneralista/5W2H)
     - Fluxo do [protótipo de alta fidelidade](https://unbarqdsw2025-1-turma02.github.io/2025.1-T02-_G9_GalaxiaConectada_Entrega01/#/Base/DesignSprint/Prototipo)
     - [Diagrama de classes](/Modelagem/ModelagemEstatica/DiagramaClasses.md)
     - [Diagrama de Componentes](/Modelagem/ModelagemEstatica/DiagramaComponentes.md)
3.  Os diagramas serão desenvolvidos na ferramenta Draw.io.
4.  Será aplicada uma [verificação por meio de um checklist](/IniciativasExtras/Verificacao/VerificacaoDiagramaAtividades.md) de boas práticas de UML;, 


## Sobre o Diagrama de Atividades

Ao se desenvolver os diagramas de atividade, é necessário levar em consideração que esse tipo de representação tem como objetivo principal demonstrar o fluxo de ações dentro de um processo ao ilustrar como as atividades ocorrem e se conectam. Com base nisso, no projeto da **Galáxia Conectada**, foram elaborados dois diagramas de atividades: um para a **aba Conhecimento**, que compreende as trilhas de aprendizado, e outro para a **aba Científico**, que apresenta notícias e artigos da área de astronomia. Ambos foram estruturados para refletir a sequência das operações esperadas no sistema, conforme as funcionalidades previamente definidas nos diagramas de classes e de componentes.

A estrutura do diagrama de atividades utiliza elementos visuais específicos para representar os passos e decisões envolvidos em um fluxo. Entre eles, destaca-se o nó inicial, que marca o ponto de partida da atividade, e o nó final, que encerra o fluxo, segundo [UML Activity Diagram Controls](https://www.uml-diagrams.org/activity-diagrams-controls.html) [5](#ref5). As ações são representadas por retângulos arredondados e indicam as tarefas a serem executadas. Para melhor compreensão dos elementos, a figura 1 abaixo funciona como uma legenda para os diagramas elaborados.

<div align="center">
    Figura 1: Legenda do Diagrama de Atividades
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/refs/heads/main/docs/Modelagem/Imagens/LegendaDiagramaAtividade.drawio.png" width="500">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
    <br>
</div>


## Aba Conhecimento Trilhas de Aprendizado


Para complementar a representação visual do fluxo de interação do usuário com as Trilhas de Aprendizado, a Tabela 1 a seguir detalha cada uma das principais ações, decisões e estados presentes no diagrama correspondente. Esta tabulação foi elaborada com o intuito de facilitar a leitura e a compreensão sequencial do processo. Ao listar as atividades de forma ordenada e concisa, a tabela serve também como um guia de referência rápida,pois auxilia na análise dos diferentes caminhos e condições que compõem a jornada do usuário ao engajar-se com o conteúdo educativo da plataforma.


<details>
  <summary><strong>Tabela 1: Atividades das Trilhas de Aprendizado</strong></summary>

**Tabela 1: Atividades das Trilhas de Aprendizado** 

| Atividade                                     | Descrição Sucinta                                                           | Relação Requisitos (RFs) | Relação Classes (Nome)                                     | Relação Componentes (# Nome)              |
|-----------------------------------------------|-----------------------------------------------------------------------------|--------------------------|------------------------------------------------------------|-------------------------------------------|
| Acessar Plataforma                            | Usuário inicia a interação.                                                 | (Geral)                  | Usuario                                                    | Entusiasta                              |
| Clicar na Aba "Trilhas"                       | Usuário navega para a seção de trilhas.                                     | RF01                     | Usuario                                                    | Entusiasta                              |
| Solicitar Categorias de Trilhas               | UI pede dados das categorias ao backend.                                    | RF01                     | -                                                          | 3 WebUI                                 |
| Buscar e Enviar Categorias                    | Backend busca categorias (BD) e envia para UI.                              | RF01                     | TrilhaEducacional (Categoria)                              | 21 ModuloEducacional, 34 BancoDeDados   |
| Exibir Categorias na Tela                     | UI mostra as categorias.                                                    | RF01                     | TrilhaEducacional (Categoria)                              | 3 WebUI                                 |
| Selecionar Categoria                          | Usuário escolhe uma categoria de interesse.                                 | RF01                     | Usuario                                                    | Entusiasta                              |
| Solicitar Trilhas da Categoria                | UI pede trilhas da categoria ao backend.                                    | RF01                     | TrilhaEducacional                                          | 3 WebUI                                 |
| Buscar e Enviar Trilhas                       | Backend busca trilhas (BD) e envia para UI.                                 | RF01                     | TrilhaEducacional                                          | 21 ModuloEducacional, 34 BancoDeDados   |
| Exibir Trilhas da Categoria                   | UI mostra as trilhas.                                                       | RF01                     | TrilhaEducacional                                          | 3 WebUI                                 |
| Selecionar Trilha                             | Usuário escolhe uma trilha específica para estudar.                         | RF01                     | Usuario                                                    | Entusiasta                              |
| Solicitar Módulos e Progresso da Trilha       | UI pede módulos e progresso ao backend.                                     | RF01, RF02, RF04         | Modulo, ProgressoUsuarioTrilha                             | 3 WebUI                                 |
| Processar Requisição de Módulos               | Backend inicia busca paralela de dados dos módulos e progresso.               | RF01, RF02, RF04         | -                                                          | 21 ModuloEducacional                    |
| Buscar Metadados dos Módulos no BD            | (Paralelo) Backend busca info dos módulos.                                  | RF01, RF02               | Modulo                                                     | 21 ModuloEducacional, 34 BancoDeDados   |
| Retornar Metadados Módulos                    | (Paralelo) BD retorna info dos módulos.                                     | RF01, RF02               | Modulo                                                     | 34 BancoDeDados                         |
| Buscar Progresso do Usuário nos Módulos no BD | (Paralelo) Backend busca progresso.                                         | RF04                     | ProgressoUsuarioTrilha                                     | 21 ModuloEducacional, 34 BancoDeDados   |
| Retornar Progresso do Usuário                 | (Paralelo) BD retorna progresso.                                            | RF04                     | ProgressoUsuarioTrilha                                     | 34 BancoDeDados                         |
| Combinar Módulos e Progresso                  | Backend junta as informações recebidas em paralelo.                         | RF01, RF02, RF04         | Modulo, ProgressoUsuarioTrilha                             | 21 ModuloEducacional                    |
| Enviar Lista de Módulos com Status para WebUI | Backend envia a lista combinada para UI.                                    | RF01, RF02, RF04         | Modulo, ProgressoUsuarioTrilha                             | 21 ModuloEducacional                    |
| Exibir Módulos da Trilha                      | UI mostra os módulos e status.                                              | RF01, RF02, RF04         | Modulo, ProgressoUsuarioTrilha                             | 3 WebUI                                 |
| Selecionar Módulo                             | Usuário escolhe um módulo para acessar o conteúdo.                          | RF02                     | Usuario                                                    | Entusiasta                              |
| Solicitar Conteúdo do Módulo                  | UI pede o conteúdo do módulo ao backend.                                    | RF02                     | Conteudo, Artigo, Video, Quiz, Jogo                        | 3 WebUI                                 |
| Buscar e Enviar Conteúdo                      | Backend busca conteúdo (BD) e envia para UI.                                | RF02                     | Conteudo, Artigo, Video, Quiz, Jogo                        | 21 ModuloEducacional, 34 BancoDeDados   |
| Exibir Conteúdo do Módulo                     | UI mostra o conteúdo (aula, artigo, etc.).                                  | RF02                     | Conteudo, Artigo, Video, Quiz, Jogo                        | 3 WebUI                                 |
| Visualizar/Interagir com Conteúdo             | Usuário consome o conteúdo.                                                 | RF02                     | Usuario, Conteudo                                          | Entusiasta                              |
| Clicar em "Marcar como Concluído"             | Usuário indica finalização do módulo.                                       | RF04                     | Usuario                                                    | Entusiasta                              |
| Enviar Requisição de Conclusão                | UI envia comando de conclusão ao backend.                                   | RF04                     | -                                                          | 3 WebUI                                 |
| Receber Requisição e Verificar Status Atual   | Backend verifica se o módulo já estava concluído (BD).                      | RF04                     | ProgressoUsuarioTrilha                                     | 21 ModuloEducacional, 34 BancoDeDados   |
| Informar Usuário "Módulo Já Concluído"        | (Se já concluído) UI exibe mensagem informativa.                            | RF04                     | -                                                          | 3 WebUI                                 |
| Processar Conclusão do Módulo                 | (Se não concluído) Backend inicia o processo de registro.                   | RF04                     | ProgressoUsuarioTrilha                                     | 21 ModuloEducacional                    |
| Atualizar Progresso da Trilha no BD           | Backend pede para atualizar o status no BD.                                 | RF04                     | ProgressoUsuarioTrilha                                     | 21 ModuloEducacional                    |
| Registrar Progresso Atualizado                | BD salva o novo status.                                                     | RF04                     | ProgressoUsuarioTrilha                                     | 34 BancoDeDados                         |
| Calcular e Registrar XP/Recompensas           | Backend calcula e salva XP/recompensas (BD).                                | RF05                     | Perfil, Conquista?                                         | 21 ModuloEducacional?, 12 GestaoUsuarios?, 34 BancoDeDados |
| Exibir Feedback de Conclusão e XP             | UI mostra mensagem de sucesso e XP ganho.                                   | RF04, RF05, RF06         | Perfil                                                     | 3 WebUI                                 |

<b> Autora: </b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.

</details>

A figura 2 apresenta o diagrama de atividades da aba de conhecimento.


<div align="center">
    <b>Figura 2:</b> Diagrama de Atividade – Aba Conhecimento
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaAtividadeTrilhaEducacional.drawio.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
</div>

<p><strong>Observação:</strong> Caso deseje visualizar ou baixar em PDF, clique aqui: 
<a href="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaAtividadeTrilhaEducacional.drawio.pdf">PDF da Aba Conhecimento</a></p>


## Aba Científico Notícias e Artigos

Visando proporcionar maior clareza e um roteiro textual para o Diagrama de Atividades referente à Aba Científico (Notícias e Artigos), a Tabela 2 subsequente enumera e descreve as etapas e pontos de decisão que constituem este fluxo de navegação e consumo de conteúdo. A apresentação tabular das atividades foi concebida para auxiliar na interpretação da representação gráfica.

<details>
  <summary><strong>Tabela 2: Atividades de  Científico Notícias e Artigos</strong></summary>

**Tabela 2: Atividades de  Científico Notícias e Artigos** 

| Atividade                                           | Descrição Sucinta                                                              | Relação Requisitos (RFs) | Relação Classes (Nome)                 | Relação Componentes (# Nome)                     |
|-----------------------------------------------------|--------------------------------------------------------------------------------|--------------------------|----------------------------------------|--------------------------------------------------|
| Acessar Plataforma                                  | Usuário inicia a interação.                                                    | (Geral)                  | Usuario                                | Entusiasta                               |
| Clicar na Aba "Notícias/Artigos"                   | Usuário navega para a seção de notícias.                                       | RF13, RF14               | Usuario                                | Entusiasta                               |
| Inserir Termos de Busca / Selecionar Filtros        | (Opcional) Usuário define critérios para refinar a lista.                      | RF10, RF13               | Usuario                                | Entusiasta                               |
| Enviar Requisição de Busca/Filtro para Backend    | (Se Filtrou) UI envia critérios ao backend.                                    | RF10, RF13               | -                                      | 3 WebUI                                |
| Solicitar Lista de Artigos (com/sem filtro)       | UI pede a lista (padrão ou filtrada) ao backend.                               | RF10, RF13, RF14         | Artigo, Noticia                        | 3 WebUI                                |
| Processar Requisição da Lista                       | Backend prepara a consulta ao BD.                                              | RF10, RF13, RF14         | -                                      | 22 ModuloDivulgacao                      |
| Construir e Executar Query no BD                    | Backend busca artigos no BD, aplicando filtros se houver.                      | RF10, RF13, RF14         | Artigo, Noticia                        | 22 ModuloDivulgacao, 34 BancoDeDados |
| Retornar Lista de Artigos Encontrados               | BD retorna a lista de artigos correspondente.                                  | RF10, RF13, RF14         | Artigo, Noticia, FonteDeNoticias       | 34 BancoDeDados                        |
| Formatar Lista e Enviar para WebUI                  | Backend prepara os dados para exibição.                                        | RF10, RF13, RF14         | Artigo, Noticia, FonteDeNoticias       | 22 ModuloDivulgacao                      |
| Exibir Lista de Artigos (mostrando Origem)          | UI mostra a lista, incluindo a fonte.                                        | RF10, RF13, RF14         | Artigo, Noticia, FonteDeNoticias       | 3 WebUI                                |
| Selecionar Artigo da Lista                          | Usuário clica em um artigo.                                                    | RF13, RF14               | Usuario                                | Entusiasta                               |
| Solicitar Conteúdo Completo do Artigo               | UI pede o conteúdo detalhado ao backend.                                       | RF13, RF14               | Artigo, Noticia                        | 3 WebUI                                |
| Processar Requisição de Conteúdo                    | Backend inicia a busca do conteúdo completo.                                   | RF13, RF14               | -                                      | 22 ModuloDivulgacao                      |
| Buscar Dados Detalhados no BD                       | Backend busca texto, link original, fonte, etc., no BD.                        | RF13, RF14               | Artigo, Noticia, FonteDeNoticias       | 22 ModuloDivulgacao, 34 BancoDeDados |
| Retornar Dados Completos do Artigo                  | BD retorna os detalhes.                                                        | RF13, RF14               | Artigo, Noticia, FonteDeNoticias       | 34 BancoDeDados                        |
| Receber Dados e Verificar Região/Idioma Usuário   | Backend verifica localidade para possível tradução.                            | RNF07                    | Usuario, Perfil?                       | 22 ModuloDivulgacao, 18 ServicoLocalizacao? |
| Traduzir Conteúdo do Artigo                 | (Se necessário) Backend realiza a tradução.                                    | RNF07                    | Artigo, Noticia                        | 22 ModuloDivulgacao, 18 ServicoLocalizacao? |
| Formatar Conteúdo e Enviar para WebUI             | Backend prepara o conteúdo (original ou traduzido).                            | RF13, RF14, RNF07         | Artigo, Noticia                        | 22 ModuloDivulgacao                      |
| Exibir Conteúdo Completo (...) com Botões           | UI mostra o artigo com origem, status tradução e botões.                       | RF13, RF14, RNF07         | Artigo, Noticia, FonteDeNoticias       | 3 WebUI                                |
| Ler o Artigo (...)                                | Usuário lê o conteúdo.                                                         | RF13, RF14               | Usuario                                | Entusiasta                               |
| Obter URL da Fonte Original                       | (Se clicou link) UI pega a URL.                                              | (Navegação)              | Artigo, Noticia                        | 3 WebUI                                |
| Indicar Intenção de Acesso à Fonte Externa        | (Se clicou link) UI sinaliza direcionamento para fonte externa.                | (Navegação)              | -                                      | 3 WebUI -> Fontes Externas               |
| Receber Requisição / Servir Página                | (Se clicou link) Fonte externa responde ao navegador.                          | (Navegação)              | -                                      | Fontes Externas                          |
| Redirecionar Navegador / Exibir Página Externa    | (Se clicou link) Navegador exibe a página da fonte original.                   | (Navegação)              | -                                      | 3 WebUI / Navegador                      |
| Exibir Mensagem/Pedido de Login                 | (Se tentou favoritar sem login) UI informa o usuário.                          | (Interação UI)           | -                                      | 3 WebUI                                |
| Enviar Requisição para Favoritar                | (Se logado e clicou favoritar) UI envia pedido ao backend.                   | RF15 (Implícito)         | -                                      | 3 WebUI                                |
| Processar Requisição Favorito                   | Backend inicia processo de salvar favorito e log (paralelo).                 | RF15 (Implícito)         | -                                      | 22 ModuloDivulgacao                      |
| Salvar Artigo como Favorito no BD               | (Paralelo) Backend pede para salvar relação User-Artigo no BD.                | RF15 (Implícito)         | Usuario, Artigo/Noticia                | 22 ModuloDivulgacao, 34 BancoDeDados |
| Registrar Favorito                              | (Paralelo) BD persiste a relação.                                             | RF15 (Implícito)         | (Relação Usuario-Artigo)               | 34 BancoDeDados                        |
| Registrar Log (Favoritar Artigo)                | (Paralelo) Backend registra o evento.                                        | (Monitoramento)          | (Log)                                  | 22 ModuloDivulgacao, 6 ServicoMonitoramento? |
| Salvar Entrada de Log                           | (Paralelo) BD ou Serviço de Log persiste o evento.                            | (Monitoramento)          | (Log)                                  | 34 BancoDeDados ou 6 ServicoMonitoramento |
| Enviar Confirmação para WebUI                   | Backend envia sucesso para UI após salvar/logar.                               | RF15 (Implícito)         | -                                      | 22 ModuloDivulgacao                      |
| Atualizar Interface (ícone favorito)            | UI mostra que o artigo foi favoritado.                                       | RF15 (Implícito)         | -                                      | 3 WebUI                                |

</details>

A figura 3 apresenta o diagrama de atividades da aba de Científico

<div align="center">
    <b>Figura 3:</b> Diagrama de Atividade – Aba Científico
    <br>
    <img src="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaAtividadeCientifico.drawio.png" width="1000">
    <br>
    <b>Autora:</b> <a href="https://github.com/SkywalkerSupreme">Larissa Stéfane</a>.
</div>

<p><strong>Observação:</strong> Caso deseje visualizar ou baixar em PDF, clique aqui: 
<a href="https://raw.githubusercontent.com/UnBArqDsw2025-1-Turma02/2025.1_T02_G9_GalaxiaConectada_Entrega02/main/docs/Modelagem/Imagens/DiagramaAtividadeCientifico.drawio.pdf">PDF da Aba Científico</a></p>



## Conclusão

A conclusão do desenvolvimento desses diagramas de atividade para a plataforma da Galáxia Conectada oferece uma representação clara e estruturada dos fluxos de trabalho nas abas Conhecimento e Científico, o que possibilita uma compreensão aprofundada das interações entre usuários e o sistema. 

## Bibliografia

<a name="ref1"></a>
[1] APOSTILA UML. Unified Modeling Language – Linguagem de Modelagem Unificada em Português. Seção sobre diagrama de atividades. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref2"></a>
[2] IBM. Diagramas de Atividades. Atualizado pela última vez: 02 mar. 2021. Disponível em: https://www.ibm.com/docs/pt-br/rational-soft-arch/9.7.0?topic=diagrams-activity. Acesso em: 30 abr. 2025.

<a name="ref3"></a>
[3] LUCIDCHART. O que é diagrama de atividades UML? Disponível em: https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-atividades-uml. Acesso em: 30 abr. 2025.

<a name="ref4"></a>
[4] RICARDO BARCELAR, R. Engenharia de Software – Módulo 3: Modelagem de Sistemas Orientada a Objetos com UML. Disponibilizada pela professora. Acesso em: 30 abr. 2025.

<a name="ref5"></a>
[5] UML DIAGRAMS. UML Activity Diagram Controls. Disponível em: https://www.uml-diagrams.org/activity-diagrams-controls.html. Acesso em: 30 abr. 2025.



## Histórico de versão

| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 30/04/2025 |
| 1.1 | Adição do tópico "Sobre o diagrama"  | Larissa Stéfane | 30/04/2025 |
| 1.2 | Adição dos diagramas | Larissa Stéfane | 30/04/2025 |
| 1.3 | Adição da legenda | Larissa Stéfane | 30/04/2025 |
| 1.4 | Adição das tabelas 1 e 2 | Larissa Stéfane | 04/05/2025 |
| 1.5 | Ajustes no artefato| Larissa Stéfane | 06/05/2025 |
