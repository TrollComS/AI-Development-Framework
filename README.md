# AI Development Framework (ADF)

[Português](#português) | [English](#english)

O ADF é um framework documental para organizar desenvolvimento de software assistido por IA. Ele transforma contexto, requisitos, decisões e procedimentos em artefatos versionados e verificáveis.

ADF is a documentation framework for organizing AI-assisted software development. It turns context, requirements, decisions, and procedures into versioned, verifiable artifacts.

---

## Português

### O que é o ADF

O AI Development Framework define como pessoas e IAs compartilham contexto e colaboram durante uma mudança de software. Ele não substitui código, testes, controle de versão ou responsabilidade humana. Sua função é garantir que cada participante saiba:

- qual problema deve ser resolvido;
- quais regras, decisões e padrões devem ser respeitados;
- qual papel está sendo exercido;
- qual procedimento deve ser seguido;
- como a entrega será validada e documentada.

O framework é independente de linguagem, arquitetura, ferramenta de IA e domínio de negócio. Cada projeto consumidor preenche a estrutura com seu próprio contexto.

### Por que usar

Sem contexto persistente, cada conversa com uma IA tende a reconstruir o projeto do zero. Isso aumenta consumo de tokens, decisões contraditórias e mudanças fora do escopo. O ADF reduz esse problema ao manter uma fonte de verdade navegável no próprio repositório.

Os principais benefícios são:

- contexto mínimo e direcionado para cada tarefa;
- rastreabilidade entre regra, decisão, feature, código e teste;
- separação clara entre arquitetura, negócio, padrões e execução;
- critérios objetivos para concluir uma entrega;
- procedimentos reutilizáveis para tarefas recorrentes;
- entrada mais rápida de pessoas ou IAs em um projeto existente.

### Conceitos fundamentais

| Conceito | Função |
|---|---|
| Papel | Define responsabilidades e limites de quem atua, como IA Arquiteta, Executora ou Revisora. |
| Skill | Procedimento reutilizável para realizar um tipo de tarefa. Não contém regras específicas do projeto. |
| Feature | Especificação de uma mudança: problema, escopo, requisitos, aceite e validações. |
| Padrão | Convenção recorrente e verificável que deve ser aplicada em várias mudanças. |
| Regra de negócio | Invariante do domínio que o sistema precisa preservar. |
| ADR | Registro de uma decisão arquitetural durável, incluindo alternativas e consequências. |
| Prompt | Instrução curta para iniciar uma execução ou revisão usando o contexto do ADF. |
| Template | Estrutura vazia e padronizada para criar um novo artefato. |
| Roteamento de IAs | Regra que define se uma tarefa fica com a IA Pensante, com a IA Dev Principal ou com o OpenCode. |

### Fluxo de trabalho

1. **Orientar:** começar no [índice principal](docs/INDICE_DOCUMENTACAO.md), consultar a configuração de IAs, escolher papel, rota e skill e carregar apenas o contexto relacionado.
2. **Especificar:** registrar problema, escopo, requisitos, riscos e critérios de aceite.
3. **Planejar:** dividir a mudança em incrementos e definir testes, compatibilidade e reversão.
4. **Implementar:** alterar o menor conjunto coerente de arquivos.
5. **Revisar:** comparar a implementação com feature, skill, regras, decisões e padrões.
6. **Validar:** executar build, testes e verificações proporcionais ao risco.
7. **Documentar:** atualizar somente as fontes canônicas realmente afetadas.
8. **Concluir:** informar arquivos alterados, validações, documentos avaliados e pendências.

Uma feature não está concluída somente porque o código compila. Revisão, validações aplicáveis e avaliação documental fazem parte da entrega.

### Como começar

Para adotar o ADF em outro projeto, siga esta ordem:

1. **Preparar decisões locais:** antes de considerar o ADF pronto para uso, defina quais IAs serão usadas, quais modelos gratuitos existem no OpenCode, quem mantém a documentação e quais arquivos precisam ser preenchidos no projeto consumidor.
2. [Instalar o ADF](Installer/FEATURE_INSTALAR_ADF.md): copiar a estrutura base e registrar a versão instalada.
3. [Adaptar ao projeto](Installer/FEATURE_ADAPTAR_ADF_AO_PROJETO.md): definir responsáveis, convenções, roteamento de IAs e extensões necessárias sem alterar silenciosamente o Core.
4. [Popular a documentação](Installer/FEATURE_POPULAR_DOCUMENTACAO_ADF.md): registrar visão, glossário, arquitetura, padrões e regras existentes.
5. [Implantar o fluxo](Installer/FEATURE_IMPLANTAR_ADF.md): validar links, testar uma feature piloto e incorporar o processo ao trabalho da equipe.

Depois da instalação, toda tarefa deve começar em [`docs/INDICE_DOCUMENTACAO.md`](docs/INDICE_DOCUMENTACAO.md). Não é necessário ler toda a documentação: o índice indica a leitura mínima por papel e tipo de tarefa.

### O que configurar antes da primeira feature

O ADF instala o esqueleto, mas cada projeto consumidor precisa preencher decisões locais antes de usar o fluxo com segurança.

| Arquivo | O que preencher | Por que importa |
|---|---|---|
| [`docs/Projeto/CONFIGURACAO_IAS.md`](docs/Projeto/CONFIGURACAO_IAS.md) | IA Pensante principal, IA Dev Principal, exigência do OpenCode, modelos gratuitos disponíveis, melhor uso de cada modelo e rota alternativa. | Permite que a IA Pensante saiba quando executar, quando delegar para código pesado e quando usar OpenCode sem depender de suposição. |
| [`docs/Projeto/ADF_ADOCAO.md`](docs/Projeto/ADF_ADOCAO.md) | Responsável pelo ADF, cadência de revisão, desvios aceitos, ferramentas usadas e decisões locais de adoção. | Registra como o framework foi adaptado ao projeto sem modificar o Core. |
| [`docs/Projeto/README.md`](docs/Projeto/README.md) | Visão, escopo, glossário, stakeholders e estado do projeto consumidor. | Dá contexto de produto para a IA entender intenção e limites. |
| [`docs/Arquitetura/README.md`](docs/Arquitetura/README.md) | Componentes, integrações, decisões, riscos técnicos e atributos de qualidade. | Ajuda a decidir se uma mudança é simples, estrutural ou deve ir para a IA Dev Principal. |
| [`docs/Padroes/README.md`](docs/Padroes/README.md) | Convenções de código, testes, layout, commits, revisão e organização. | Mantém as entregas consistentes entre pessoas, IA Dev Principal e OpenCode. |
| [`docs/RegrasNegocio/README.md`](docs/RegrasNegocio/README.md) | Regras e invariantes do domínio. | Evita que a IA altere comportamento de negócio por falta de contexto. |

### Melhoria de roteamento de IAs

A versão atual adiciona uma camada explícita para separar papel, ferramenta e rota de execução:

- [`docs/AI/Core/ROTEAMENTO_IAS.md`](docs/AI/Core/ROTEAMENTO_IAS.md) define a regra geral para escolher entre IA Pensante, IA Dev Principal e OpenCode.
- [`docs/Projeto/CONFIGURACAO_IAS.md`](docs/Projeto/CONFIGURACAO_IAS.md) é preenchido pelo usuário em cada projeto com as ferramentas reais e os modelos gratuitos do OpenCode.
- A IA Pensante deve ler essa configuração antes de planejar uma feature e declarar a rota escolhida.
- O OpenCode deve ser usado apenas com modelos gratuitos declarados pelo usuário.
- Mudanças grandes, estruturais, sensíveis ou de alto risco devem ir para a IA Dev Principal.

### Estrutura do repositório

#### Arquivos da raiz

| Arquivo | Para que serve |
|---|---|
| [`README.md`](README.md) | Apresentação bilíngue do framework, seus conceitos, estrutura e forma de adoção. |
| [`ADF_VERSION.md`](ADF_VERSION.md) | Versão atual do contrato ADF, política de versionamento e observações de compatibilidade. |
| [`CHANGELOG_ADF.md`](CHANGELOG_ADF.md) | Histórico das mudanças do framework, com arquivos afetados, justificativas e benefícios. |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | Regras para propor alterações ao ADF sem introduzir dependência de domínio ou tecnologia. |
| [`LICENSE`](LICENSE) | Termos da licença MIT aplicáveis ao uso e à distribuição. |

#### `docs`: documentação operacional e do projeto consumidor

| Caminho | Para que serve |
|---|---|
| [`docs/INDICE_DOCUMENTACAO.md`](docs/INDICE_DOCUMENTACAO.md) | Ponto único de entrada. Direciona a leitura mínima por papel e por tipo de tarefa. |
| [`docs/AI/Core`](docs/AI/Core/ADF_FRAMEWORK.md) | Contrato, fluxo, papéis, organização, checklist e mapas centrais do ADF. |
| [`docs/AI/Skills`](docs/AI/Core/MAPA_SKILLS.md) | Procedimentos reutilizáveis para analisar, especificar, implementar, revisar e documentar mudanças. |
| [`docs/AI/Templates`](docs/AI/Core/MAPA_DOCUMENTACAO.md) | Modelos para criar features, ADRs, planos, regras, revisões, prompts e checklists consistentes. |
| [`docs/AI/Prompts`](docs/AI/Prompts/PROMPT_INICIAR_FEATURE.md) | Instruções curtas para iniciar uma feature ou uma revisão usando o processo ADF. |
| [`docs/Projeto`](docs/Projeto/README.md) | Propósito, escopo, glossário, stakeholders, configuração de IAs, estado e histórico do projeto consumidor. |
| [`docs/Arquitetura`](docs/Arquitetura/README.md) | Contexto técnico, componentes, integrações, atributos de qualidade e decisões arquiteturais. |
| [`docs/Padroes`](docs/Padroes/README.md) | Convenções técnicas, visuais e de processo que devem ser repetidas e verificadas. |
| [`docs/RegrasNegocio`](docs/RegrasNegocio/README.md) | Regras e invariantes do domínio, separados de detalhes de implementação. |
| [`docs/Features`](docs/Features/README.md) | Especificações das mudanças planejadas ou executadas, com escopo e critérios de aceite. |
| [`docs/Revisoes`](docs/Revisoes/README.md) | Pareceres de revisão que precisam ser preservados como evidência ou histórico. |
| [`docs/Samples`](docs/Samples/FEATURE_EXEMPLO.md) | Exemplos preenchidos que demonstram como usar os templates sem definir regras reais. |

#### Conteúdo de `docs/AI/Core`

| Arquivo | Para que serve |
|---|---|
| [`ADF_FRAMEWORK.md`](docs/AI/Core/ADF_FRAMEWORK.md) | Contrato essencial: propósito, regras, limites e adoção mínima do framework. |
| [`FLUXO_DESENVOLVIMENTO.md`](docs/AI/Core/FLUXO_DESENVOLVIMENTO.md) | Sequência oficial desde a orientação inicial até a conclusão documentada. |
| [`PAPEIS_DAS_IAS.md`](docs/AI/Core/PAPEIS_DAS_IAS.md) | Responsabilidades e limites das IAs Analista, Arquiteta, Executora, Revisora e Curadora. |
| [`ROTEAMENTO_IAS.md`](docs/AI/Core/ROTEAMENTO_IAS.md) | Critérios para escolher IA Pensante, IA Dev Principal ou OpenCode conforme risco e tipo de tarefa. |
| [`GUIA_ORGANIZACAO_DOCUMENTACAO.md`](docs/AI/Core/GUIA_ORGANIZACAO_DOCUMENTACAO.md) | Define onde cada informação deve ficar e como evitar duplicidade e documentos gigantes. |
| [`CHECKLIST_USO_ADF.md`](docs/AI/Core/CHECKLIST_USO_ADF.md) | Verificação compacta para confirmar que contexto, escopo, testes e documentação foram tratados. |
| [`MAPA_DOCUMENTACAO.md`](docs/AI/Core/MAPA_DOCUMENTACAO.md) | Catálogo dos documentos e explicação das relações entre visão, regras, arquitetura, features e código. |
| [`MAPA_SKILLS.md`](docs/AI/Core/MAPA_SKILLS.md) | Catálogo das skills disponíveis e da saída esperada de cada uma. |
| [`INDICE_DOCUMENTACAO.md`](docs/AI/Core/INDICE_DOCUMENTACAO.md) | Caminho legado mantido para compatibilidade; redireciona para o índice principal em `docs`. |

#### Skills disponíveis

| Skill | Quando usar |
|---|---|
| [`SKILL_ANALISAR_CONTEXTO`](docs/AI/Skills/SKILL_ANALISAR_CONTEXTO.md) | Para localizar fontes relevantes, restrições e lacunas antes de propor uma solução. |
| [`SKILL_ESPECIFICAR_FEATURE`](docs/AI/Skills/SKILL_ESPECIFICAR_FEATURE.md) | Para transformar uma necessidade em feature verificável ou executar uma feature já existente. |
| [`SKILL_PLANEJAR_IMPLEMENTACAO`](docs/AI/Skills/SKILL_PLANEJAR_IMPLEMENTACAO.md) | Para decompor uma feature em passos, testes, migração e reversão. |
| [`SKILL_IMPLEMENTAR_MUDANCA`](docs/AI/Skills/SKILL_IMPLEMENTAR_MUDANCA.md) | Para mudanças gerais que já possuem feature e plano suficientes. |
| [`SKILL_CORRIGIR_BUG`](docs/AI/Skills/SKILL_CORRIGIR_BUG.md) | Para reproduzir uma falha, tratar a causa e validar regressões. |
| [`SKILL_IMPLEMENTAR_CRUD`](docs/AI/Skills/SKILL_IMPLEMENTAR_CRUD.md) | Para operações de cadastro e manutenção de recursos respeitando camadas e validações. |
| [`SKILL_CRIAR_INTEGRACAO_EXTERNA`](docs/AI/Skills/SKILL_CRIAR_INTEGRACAO_EXTERNA.md) | Para comunicação com APIs ou serviços externos com isolamento, segurança e resiliência. |
| [`SKILL_AJUSTAR_LAYOUT`](docs/AI/Skills/SKILL_AJUSTAR_LAYOUT.md) | Para mudanças visuais e de interação, incluindo responsividade e acessibilidade. |
| [`SKILL_REFATORAR_CODIGO`](docs/AI/Skills/SKILL_REFATORAR_CODIGO.md) | Para melhorar a estrutura preservando comportamento e contratos existentes. |
| [`SKILL_REVISAR_ARQUITETURA`](docs/AI/Skills/SKILL_REVISAR_ARQUITETURA.md) | Para avaliar mudanças estruturais, dependências, riscos e necessidade de ADR. |
| [`SKILL_REVISAR_ENTREGA`](docs/AI/Skills/SKILL_REVISAR_ENTREGA.md) | Para comparar diff e evidências com o aceite, buscando defeitos e riscos. |
| [`SKILL_ATUALIZAR_DOCUMENTACAO`](docs/AI/Skills/SKILL_ATUALIZAR_DOCUMENTACAO.md) | Para manter fontes canônicas, links, índices e histórico coerentes após uma mudança. |

#### Templates disponíveis

| Template | Artefato gerado |
|---|---|
| [`TEMPLATE_FEATURE`](docs/AI/Templates/TEMPLATE_FEATURE.md) | Feature com contexto, escopo, requisitos, aceite, riscos e gate de conclusão. |
| [`TEMPLATE_PLANO_IMPLEMENTACAO`](docs/AI/Templates/TEMPLATE_PLANO_IMPLEMENTACAO.md) | Plano incremental ligado aos critérios e às validações. |
| [`TEMPLATE_CHECKLIST_IMPLEMENTACAO`](docs/AI/Templates/TEMPLATE_CHECKLIST_IMPLEMENTACAO.md) | Checklist operacional para execução e entrega. |
| [`TEMPLATE_REVISAO`](docs/AI/Templates/TEMPLATE_REVISAO.md) | Parecer de revisão com severidade, evidência, impacto e recomendação. |
| [`TEMPLATE_ADR`](docs/AI/Templates/TEMPLATE_ADR.md) | Registro de decisão arquitetural com alternativas e consequências. |
| [`TEMPLATE_PADRAO`](docs/AI/Templates/TEMPLATE_PADRAO.md) | Convenção reutilizável com aplicação, regras, exemplos e verificação. |
| [`TEMPLATE_REGRA_NEGOCIO`](docs/AI/Templates/TEMPLATE_REGRA_NEGOCIO.md) | Regra de domínio com motivação, exceções, exemplos e rastreabilidade. |
| [`TEMPLATE_VISAO_PROJETO`](docs/AI/Templates/TEMPLATE_VISAO_PROJETO.md) | Visão do produto com propósito, escopo, stakeholders e indicadores. |
| [`TEMPLATE_PROMPT_EXECUCAO`](docs/AI/Templates/TEMPLATE_PROMPT_EXECUCAO.md) | Prompt parametrizável para orientar uma IA Executora. |
| [`TEMPLATE_PROMPT_REVISAO`](docs/AI/Templates/TEMPLATE_PROMPT_REVISAO.md) | Prompt parametrizável para orientar uma IA Revisora. |

### Exemplo de uso em uma tarefa

Para corrigir um erro:

1. Abra o [índice](docs/INDICE_DOCUMENTACAO.md).
2. Leia a feature ou descrição do erro e a [`SKILL_CORRIGIR_BUG`](docs/AI/Skills/SKILL_CORRIGIR_BUG.md).
3. Consulte somente arquitetura, regra, padrão e testes da área afetada.
4. Reproduza o erro e identifique a causa.
5. Implemente a menor correção suficiente e valide a regressão.
6. Use a [`SKILL_REVISAR_ENTREGA`](docs/AI/Skills/SKILL_REVISAR_ENTREGA.md) para revisar o resultado.
7. Avalie a documentação e reporte arquivos, testes e pendências.

### Evolução e contribuição

Consulte [`CONTRIBUTING.md`](CONTRIBUTING.md) antes de alterar o framework. Mudanças devem continuar genéricas, possuir ganho verificável e preservar compatibilidade sempre que possível. Alterações no contrato público exigem atualização de [`ADF_VERSION.md`](ADF_VERSION.md), dos mapas afetados e de [`CHANGELOG_ADF.md`](CHANGELOG_ADF.md).

Distribuído sob a [licença MIT](LICENSE).

---

## English

### What ADF is

The AI Development Framework defines how people and AI systems share context and collaborate during software changes. It does not replace code, tests, version control, or human accountability. Its purpose is to ensure that every participant understands:

- which problem must be solved;
- which rules, decisions, and standards must be respected;
- which role is currently active;
- which procedure must be followed;
- how the delivery will be validated and documented.

The framework is independent of programming language, architecture, AI provider, and business domain. Each adopting project fills the structure with its own context.

### Why use it

Without persistent context, each AI conversation tends to reconstruct the project from scratch. This increases token usage, conflicting decisions, and out-of-scope changes. ADF reduces this problem by keeping a navigable source of truth inside the repository.

Key benefits include:

- minimal, task-focused context;
- traceability across rules, decisions, features, code, and tests;
- clear separation between architecture, business rules, standards, and execution;
- objective delivery completion criteria;
- reusable procedures for recurring tasks;
- faster onboarding for people and AI systems.

### Core concepts

| Concept | Purpose |
|---|---|
| Role | Defines responsibilities and boundaries for an Architect, Executor, or Reviewer AI. |
| Skill | Reusable procedure for a type of task. It must not contain project-specific rules. |
| Feature | Change specification containing the problem, scope, requirements, acceptance criteria, and validation. |
| Standard | Recurring, verifiable convention applied across multiple changes. |
| Business rule | Domain invariant that the system must preserve. |
| ADR | Durable architectural decision record, including alternatives and consequences. |
| Prompt | Short instruction used to start execution or review with ADF context. |
| Template | Standard empty structure used to create a new artifact. |
| AI routing | Rule that defines whether a task stays with the Thinking AI, goes to the Main Dev AI, or uses OpenCode. |

### Workflow

1. **Orient:** start from the [main index](docs/INDICE_DOCUMENTACAO.md), read the AI configuration, select the role, route, and skill, and load only related context.
2. **Specify:** document the problem, scope, requirements, risks, and acceptance criteria.
3. **Plan:** split the change into increments and define tests, compatibility, and rollback.
4. **Implement:** change the smallest coherent set of files.
5. **Review:** compare implementation against the feature, skill, rules, decisions, and standards.
6. **Validate:** run builds, tests, and checks proportional to risk.
7. **Document:** update only the canonical sources actually affected.
8. **Complete:** report changed files, validation, reviewed documentation, and remaining issues.

A feature is not complete merely because the code compiles. Review, applicable validation, and documentation assessment are part of delivery.

### Getting started

Adopt ADF in this order:

1. **Prepare local decisions:** before treating ADF as ready for use, define which AIs will be used, which free OpenCode models are available, who maintains the documentation, and which files must be filled in the adopting project.
2. [Install ADF](Installer/FEATURE_INSTALAR_ADF.md): copy the base structure and record the installed version.
3. [Adapt it to the project](Installer/FEATURE_ADAPTAR_ADF_AO_PROJETO.md): define ownership, conventions, AI routing, and required extensions without silently modifying Core.
4. [Populate documentation](Installer/FEATURE_POPULAR_DOCUMENTACAO_ADF.md): record the existing vision, glossary, architecture, standards, and rules.
5. [Deploy the workflow](Installer/FEATURE_IMPLANTAR_ADF.md): validate links, run a pilot feature, and incorporate the process into team practices.

After installation, every task starts at [`docs/INDICE_DOCUMENTACAO.md`](docs/INDICE_DOCUMENTACAO.md). Reading the entire documentation set is unnecessary; the index identifies the minimum context for each role and task.

### What to configure before the first feature

ADF installs the skeleton, but each adopting project must fill local decisions before using the workflow safely.

| File | What to fill in | Why it matters |
|---|---|---|
| [`docs/Projeto/CONFIGURACAO_IAS.md`](docs/Projeto/CONFIGURACAO_IAS.md) | Main Thinking AI, Main Dev AI, OpenCode requirement, available free models, best use for each model, and fallback route. | Allows the Thinking AI to know when to execute, when to delegate heavy code, and when to use OpenCode without guessing. |
| [`docs/Projeto/ADF_ADOCAO.md`](docs/Projeto/ADF_ADOCAO.md) | ADF owner, review cadence, accepted deviations, tools used, and local adoption decisions. | Records how the framework was adapted to the project without modifying Core. |
| [`docs/Projeto/README.md`](docs/Projeto/README.md) | Vision, scope, glossary, stakeholders, and adopting project status. | Gives product context so the AI understands intent and boundaries. |
| [`docs/Arquitetura/README.md`](docs/Arquitetura/README.md) | Components, integrations, decisions, technical risks, and quality attributes. | Helps decide whether a change is simple, structural, or should go to the Main Dev AI. |
| [`docs/Padroes/README.md`](docs/Padroes/README.md) | Code, test, layout, commit, review, and organization conventions. | Keeps deliveries consistent across people, Main Dev AI, and OpenCode. |
| [`docs/RegrasNegocio/README.md`](docs/RegrasNegocio/README.md) | Domain rules and invariants. | Prevents the AI from changing business behavior due to missing context. |

### AI routing improvement

The current version adds an explicit layer for separating role, tool, and execution route:

- [`docs/AI/Core/ROTEAMENTO_IAS.md`](docs/AI/Core/ROTEAMENTO_IAS.md) defines the general rule for choosing between Thinking AI, Main Dev AI, and OpenCode.
- [`docs/Projeto/CONFIGURACAO_IAS.md`](docs/Projeto/CONFIGURACAO_IAS.md) is filled by the user in each project with real tools and free OpenCode models.
- The Thinking AI must read this configuration before planning a feature and declare the chosen route.
- OpenCode must be used only with free models declared by the user.
- Large, structural, sensitive, or high-risk changes should go to the Main Dev AI.

### Repository structure

#### Root files

| File | Purpose |
|---|---|
| [`README.md`](README.md) | Bilingual introduction to the framework, its concepts, structure, and adoption process. |
| [`ADF_VERSION.md`](ADF_VERSION.md) | Current ADF contract version, versioning policy, and compatibility notes. |
| [`CHANGELOG_ADF.md`](CHANGELOG_ADF.md) | Framework change history, including affected files, rationale, and benefits. |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | Rules for changing ADF without introducing domain or technology dependencies. |
| [`LICENSE`](LICENSE) | MIT License terms for use and distribution. |

#### Documentation directories

| Path | Purpose |
|---|---|
| [`docs/INDICE_DOCUMENTACAO.md`](docs/INDICE_DOCUMENTACAO.md) | Single entry point that routes minimum reading by role and task type. |
| [`docs/AI/Core`](docs/AI/Core/ADF_FRAMEWORK.md) | ADF contract, workflow, roles, organization guide, checklist, and central maps. |
| [`docs/AI/Skills`](docs/AI/Core/MAPA_SKILLS.md) | Reusable procedures for analyzing, specifying, implementing, reviewing, and documenting changes. |
| [`docs/AI/Templates`](docs/AI/Core/MAPA_DOCUMENTACAO.md) | Models for consistent features, ADRs, plans, rules, reviews, prompts, and checklists. |
| [`docs/AI/Prompts`](docs/AI/Prompts/PROMPT_INICIAR_FEATURE.md) | Short instructions for starting a feature or review with the ADF process. |
| [`docs/Projeto`](docs/Projeto/README.md) | Adopting project's purpose, scope, glossary, stakeholders, AI configuration, status, and history. |
| [`docs/Arquitetura`](docs/Arquitetura/README.md) | Technical context, components, integrations, quality attributes, and architectural decisions. |
| [`docs/Padroes`](docs/Padroes/README.md) | Recurring and verifiable technical, visual, and process conventions. |
| [`docs/RegrasNegocio`](docs/RegrasNegocio/README.md) | Domain rules and invariants kept separate from implementation details. |
| [`docs/Features`](docs/Features/README.md) | Planned or completed change specifications with scope and acceptance criteria. |
| [`docs/Revisoes`](docs/Revisoes/README.md) | Review reports preserved as evidence or historical records. |
| [`docs/Samples`](docs/Samples/FEATURE_EXEMPLO.md) | Filled examples showing template usage without defining real project rules. |

#### Core files

| File | Purpose |
|---|---|
| [`ADF_FRAMEWORK.md`](docs/AI/Core/ADF_FRAMEWORK.md) | Essential contract covering purpose, rules, boundaries, and minimum adoption. |
| [`FLUXO_DESENVOLVIMENTO.md`](docs/AI/Core/FLUXO_DESENVOLVIMENTO.md) | Official sequence from initial orientation through documented completion. |
| [`PAPEIS_DAS_IAS.md`](docs/AI/Core/PAPEIS_DAS_IAS.md) | Responsibilities and boundaries for Analyst, Architect, Executor, Reviewer, and Curator roles. |
| [`ROTEAMENTO_IAS.md`](docs/AI/Core/ROTEAMENTO_IAS.md) | Criteria for choosing Thinking AI, Main Dev AI, or OpenCode based on risk and task type. |
| [`GUIA_ORGANIZACAO_DOCUMENTACAO.md`](docs/AI/Core/GUIA_ORGANIZACAO_DOCUMENTACAO.md) | Defines information ownership and prevents duplication and oversized documents. |
| [`CHECKLIST_USO_ADF.md`](docs/AI/Core/CHECKLIST_USO_ADF.md) | Compact check ensuring context, scope, tests, and documentation were addressed. |
| [`MAPA_DOCUMENTACAO.md`](docs/AI/Core/MAPA_DOCUMENTACAO.md) | Document catalog and relationship map across vision, rules, architecture, features, and code. |
| [`MAPA_SKILLS.md`](docs/AI/Core/MAPA_SKILLS.md) | Catalog of available skills and their expected outputs. |
| [`INDICE_DOCUMENTACAO.md`](docs/AI/Core/INDICE_DOCUMENTACAO.md) | Legacy compatibility path redirecting readers to the main index under `docs`. |

#### Available skills

| Skill | Use it when |
|---|---|
| [`SKILL_ANALISAR_CONTEXTO`](docs/AI/Skills/SKILL_ANALISAR_CONTEXTO.md) | Finding relevant sources, constraints, and gaps before proposing a solution. |
| [`SKILL_ESPECIFICAR_FEATURE`](docs/AI/Skills/SKILL_ESPECIFICAR_FEATURE.md) | Turning a need into a verifiable feature or executing an existing feature. |
| [`SKILL_PLANEJAR_IMPLEMENTACAO`](docs/AI/Skills/SKILL_PLANEJAR_IMPLEMENTACAO.md) | Breaking a feature into steps, tests, migration, and rollback. |
| [`SKILL_IMPLEMENTAR_MUDANCA`](docs/AI/Skills/SKILL_IMPLEMENTAR_MUDANCA.md) | Implementing a general change with sufficient feature and plan context. |
| [`SKILL_CORRIGIR_BUG`](docs/AI/Skills/SKILL_CORRIGIR_BUG.md) | Reproducing a failure, treating its cause, and validating regressions. |
| [`SKILL_IMPLEMENTAR_CRUD`](docs/AI/Skills/SKILL_IMPLEMENTAR_CRUD.md) | Implementing resource maintenance operations while respecting layers and validation. |
| [`SKILL_CRIAR_INTEGRACAO_EXTERNA`](docs/AI/Skills/SKILL_CRIAR_INTEGRACAO_EXTERNA.md) | Communicating with external APIs or services with isolation, security, and resilience. |
| [`SKILL_AJUSTAR_LAYOUT`](docs/AI/Skills/SKILL_AJUSTAR_LAYOUT.md) | Changing visuals and interactions, including responsiveness and accessibility. |
| [`SKILL_REFATORAR_CODIGO`](docs/AI/Skills/SKILL_REFATORAR_CODIGO.md) | Improving structure while preserving behavior and existing contracts. |
| [`SKILL_REVISAR_ARQUITETURA`](docs/AI/Skills/SKILL_REVISAR_ARQUITETURA.md) | Assessing structural changes, dependencies, risks, and the need for an ADR. |
| [`SKILL_REVISAR_ENTREGA`](docs/AI/Skills/SKILL_REVISAR_ENTREGA.md) | Comparing a diff and validation evidence against acceptance criteria. |
| [`SKILL_ATUALIZAR_DOCUMENTACAO`](docs/AI/Skills/SKILL_ATUALIZAR_DOCUMENTACAO.md) | Keeping canonical sources, links, indexes, and history consistent after a change. |

#### Available templates

| Template | Generated artifact |
|---|---|
| [`TEMPLATE_FEATURE`](docs/AI/Templates/TEMPLATE_FEATURE.md) | Feature containing context, scope, requirements, acceptance criteria, risks, and completion gate. |
| [`TEMPLATE_PLANO_IMPLEMENTACAO`](docs/AI/Templates/TEMPLATE_PLANO_IMPLEMENTACAO.md) | Incremental plan mapped to acceptance criteria and validation. |
| [`TEMPLATE_CHECKLIST_IMPLEMENTACAO`](docs/AI/Templates/TEMPLATE_CHECKLIST_IMPLEMENTACAO.md) | Operational checklist for implementation and delivery. |
| [`TEMPLATE_REVISAO`](docs/AI/Templates/TEMPLATE_REVISAO.md) | Review report containing severity, evidence, impact, and recommendation. |
| [`TEMPLATE_ADR`](docs/AI/Templates/TEMPLATE_ADR.md) | Architectural decision record with alternatives and consequences. |
| [`TEMPLATE_PADRAO`](docs/AI/Templates/TEMPLATE_PADRAO.md) | Reusable convention with applicability, rules, examples, and verification. |
| [`TEMPLATE_REGRA_NEGOCIO`](docs/AI/Templates/TEMPLATE_REGRA_NEGOCIO.md) | Domain rule with rationale, exceptions, examples, and traceability. |
| [`TEMPLATE_VISAO_PROJETO`](docs/AI/Templates/TEMPLATE_VISAO_PROJETO.md) | Product vision with purpose, scope, stakeholders, and indicators. |
| [`TEMPLATE_PROMPT_EXECUCAO`](docs/AI/Templates/TEMPLATE_PROMPT_EXECUCAO.md) | Parameterized prompt for an Executor AI. |
| [`TEMPLATE_PROMPT_REVISAO`](docs/AI/Templates/TEMPLATE_PROMPT_REVISAO.md) | Parameterized prompt for a Reviewer AI. |

### Task example

To fix a defect:

1. Open the [documentation index](docs/INDICE_DOCUMENTACAO.md).
2. Read the feature or defect report and [`SKILL_CORRIGIR_BUG`](docs/AI/Skills/SKILL_CORRIGIR_BUG.md).
3. Load only the architecture, rules, standards, and tests related to the affected area.
4. Reproduce the defect and identify its cause.
5. Implement the smallest sufficient correction and validate regressions.
6. Review the outcome with [`SKILL_REVISAR_ENTREGA`](docs/AI/Skills/SKILL_REVISAR_ENTREGA.md).
7. Assess documentation and report files, tests, and remaining issues.

### Evolution and contribution

Read [`CONTRIBUTING.md`](CONTRIBUTING.md) before changing the framework. Changes must remain generic, provide a verifiable benefit, and preserve compatibility whenever possible. Public contract changes require updates to [`ADF_VERSION.md`](ADF_VERSION.md), affected maps, and [`CHANGELOG_ADF.md`](CHANGELOG_ADF.md).

Distributed under the [MIT License](LICENSE).
