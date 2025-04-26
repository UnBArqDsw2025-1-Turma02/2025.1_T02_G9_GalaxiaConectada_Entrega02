# Diagrama de Componentes

## Sumário

- [Introdução](#introdução)  
- [Objetivos](#objetivos)  
- [Metodologia](#metodologia)  
- [Investigação dos Componentes Necessários](#investigação-dos-componentes-necessários)  
- [Diagrama de Componentes](#diagrama-de-componentes)  
- [Conclusão](#conclusão)  
- [Bibliografia](#bibliografia)  
- [Histórico de versão](#histórico-de-versão)  

## Introdução

Segundo a Apostila UML – Linguagem de Modelagem Unificada [1] e o guia da plataforma UML Diagrams [2], um **componente** é uma unidade física de software (código-fonte, biblioteca, executável) que encapsula um conjunto de funcionalidades. O **Diagrama de Componentes** representa visualmente esses módulos e suas dependências, mostrando quais artefatos (ex.: arquivos .jar, .dll, .py) são necessários para executar cada parte do sistema. No projeto Galáxia Conectada — uma plataforma educacional de astronomia — esse diagrama expõe módulos como Interface Web, API de Cursos, Serviço de Notificações, Banco de Dados e Integração com APIs externas (ex.: NASA).

## Objetivos

- Apresentar de forma clara os componentes físicos do sistema Galáxia Conectada.  
- Evidenciar interfaces providas e requeridas por cada módulo.  
- Documentar dependências e artefatos para suportar implementação e deploy.  

## Metodologia

1. **Levantamento arquitetural** — identificação de módulos principais a partir dos requisitos funcionais, do rich-picture e do 5W2H.  
2. **Modelagem inicial** — esboço no Draw.io das caixas de componentes e suas interfaces.  
3. **Verificação** — aplicação de checklist de boas práticas UML (notação, nomenclatura, coesão).  
4. **Refino** — ajustes visuais e de nomenclatura para maximizar legibilidade e rastreabilidade.  

## Investigação dos Componentes Necessários

| Componente               | Responsabilidade                                                | Artefatos                  | Interfaces providas              | Interfaces requeridas             |
|--------------------------|-----------------------------------------------------------------|----------------------------|----------------------------------|-----------------------------------|
| **WebUI**                | Apresentar páginas, capturar interação do usuário               | webui.jar, CSS, HTML       | IAutenticacao, ICursos           | IAPICursos, INotificacoes         |
| **APICursos**            | Gerenciar lógica de cursos, trilhas e quizzes                   | apicursos.jar              | ICursos, ITrilhas                | IDatabase                         |
| **ServicoNotificacoes**  | Enviar e agendar notificações push e e-mail                     | notif-service.jar          | INotificacoes                    | IUsuario, IEventoAstronomico      |
| **Database**             | Persistir dados de usuários, progresso, conteúdo                | postgres.db                | IDatabase                        | —                                 |
| **IntegracaoExterna**    | Coletar notícias astronômicas de APIs públicas (NASA, ESA)      | integracao-api.py          | —                                | IFonteNoticias                    |
| **BotImportador**        | Agendar e executar importação de notícias externas              | bot_import.py              | IFonteNoticias                   | IntegracaoExterna                 |
| **ServicoRecomendacao**  | Calcular e fornecer recomendações de conteúdo                    | recommender.jar            | IRecomendacao                    | IDatabase, IUsuario               |

## Diagrama de Componentes


## Conclusão

O Diagrama de Componentes apresenta de forma estruturada os módulos físicos do sistema, suas interfaces e dependências. Essa visão facilita o planejamento de implantação, a definição de pipelines de build/deploy e a manutenção evolutiva da plataforma, ao evidenciar claramente quais artefatos e serviços cada componente exige ou oferece.

## Bibliografia

<a name="ref1"></a>  
[1]APOSTILA UML. *Linguagem de Modelagem Unificada*. Universidade XYZ, 2023. (Documento interno). Acesso em: 25 abr. 2025.  

<a name="ref2"></a>  
[2]UML DIAGRAMS. *Component Diagrams Overview*. Disponível em: https://www.uml-diagrams.org/component-diagrams.html. Acesso em: 25 abr. 2025. 

<a name="ref3"></a>  
[3] IBM CORPORATION. *Component diagrams*. IBM Documentation, 2023. Disponível em: https://www.ibm.com/docs/en/dmrt/9.5.0?topic=diagrams-component. Acesso em: 25 abr. 2025.  

<a name="ref4"></a>  
[4] LUCID SOFTWARE INC. *UML Component Diagram*. Lucidchart, 2024. Disponível em: https://www.lucidchart.com/pages/uml-component-diagram. Acesso em: 25 abr. 2025.

<a name="ref5"></a>  
[5] VISUAL PARADIGM INTERNATIONAL. *UML Component Diagram Guide*. Visual Paradigm, 2024. Disponível em: https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-component-diagram/. Acesso em: 25 abr. 2025.  

## Histórico de versão

| Versão | Alteração | Responsável | Data |
| - | - | - | - |
| 1.0 | Elaboração do documento| Larissa Stéfane | 25/04/2024 |
| 1.1 | Adição da Metodologia  | Larissa Stéfane | 25/04/2024 |
| 1.2 | Criação da tabela de investigação das classes | Larissa Stéfane | 25/04/2024 |
