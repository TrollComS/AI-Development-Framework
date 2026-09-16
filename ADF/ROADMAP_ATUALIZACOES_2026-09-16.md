# Roadmap de atualizações do ADF — 2026-09-16

**Estado:** Concluído

**Versão final do ADF:** 1.8.0

**Escopo:** evolução do fluxo de instruções para agentes, templates, instalação inicial e atualização assistida.

## Objetivo alcançado

Transformar a documentação do ADF em fonte canônica de contexto e permitir que projetos consumidores exponham esse contexto aos agentes por adaptadores opcionais, sem duplicar regras nem perder instruções locais durante instalação ou atualização.

## Linha do tempo

| Fase | Entrega | Versão | Commit | Resultado |
|---|---|---:|---|---|
| 1 | [Contrato de instruções](Features/FEATURE_DEFINIR_CONTRATO_INSTRUCOES_AGENTES.md) | 1.5.0 | `ae12e9e` | Define fonte canônica, preflight, precedência e granularidade. |
| 2 | [Templates de adaptadores](Features/FEATURE_CRIAR_TEMPLATES_ADAPTADORES_AGENTES.md) | 1.6.0 | `2cfa774` | Disponibiliza templates opt-in para `AGENTS.md` e Copilot. |
| 3 | [Instalador](Features/FEATURE_EVOLUIR_INSTALADOR_PARA_ADAPTADORES_AGENTES.md) | 1.7.0 | `68b4c27` | Permite configurar adaptadores, OpenCode opcional e contexto operacional. |
| 4 | [Atualizador](Features/FEATURE_EVOLUIR_ATUALIZADOR_PARA_ADAPTADORES_AGENTES.md) | 1.8.0 | `3ff0baf` | Migra instalações existentes com classificação e preservação segura. |

## Fase 1 — Contrato de instruções

O ADF passou a estabelecer que `docs/` é a fonte canônica de contexto. `AGENTS.md`, quando adotado, é uma entrada universal que encaminha ao índice e não uma cópia da documentação.

O preflight obrigatório agora orienta o agente a:

1. Ler a instrução de entrada aplicável.
2. Ler `docs/INDICE_DOCUMENTACAO.md`.
3. Consultar configuração de IAs e limitações locais.
4. Carregar somente o contexto pertinente.
5. Inspecionar código e estado atual antes de alterar.

Também foi formalizada a regra de que cada feature deve ser o menor incremento funcional coerente. Exceções por integridade, segurança, migração ou compatibilidade precisam de justificativa e registro.

## Fase 2 — Templates de adaptadores

Foram adicionados:

- [`TEMPLATE_AGENTS.md`](../docs/AI/Templates/TEMPLATE_AGENTS.md), destinado à raiz do projeto como `AGENTS.md`.
- [`TEMPLATE_COPILOT_INSTRUCTIONS.md`](../docs/AI/Templates/TEMPLATE_COPILOT_INSTRUCTIONS.md), destinado a `.github/copilot-instructions.md`.
- [`ADAPTADORES_AGENTES.md`](../docs/AI/Core/ADAPTADORES_AGENTES.md), com critérios de uso, precedência e regras por caminho.

Cada template separa:

- bloco `MANAGED`, que pode ser atualizado pelo ADF;
- bloco `LOCAL`, reservado a instruções exclusivas do projeto ou ferramenta.

`CLAUDE.md`, `GEMINI.md` e regras Cursor foram avaliados e permanecem fora do conjunto suportado até possuírem template, seleção explícita e atualização segura.

## Fase 3 — Instalação inicial

O instalador passou a perguntar, de modo explícito:

- ferramentas de IA habilitadas;
- adaptadores desejados: `AGENTS.md`, Copilot ou nenhum;
- uso de OpenCode, somente quando desejado;
- comandos oficiais de build e testes;
- diretórios relevantes, arquivos gerados e áreas que exigem autorização.

Na criação de um adaptador, o instalador usa o template correspondente. Se o arquivo já existir, ele só atualiza o bloco gerenciado quando os marcadores forem válidos e o usuário autorizar; caso contrário, preserva o arquivo e registra pendência.

## Fase 4 — Atualização de projetos existentes

O atualizador não reexecuta a instalação inicial. Ele classifica cada adaptador encontrado antes de agir:

| Classificação | Tratamento |
|---|---|
| Ausente | Pode criar somente após escolha do usuário. |
| Compatível | Mantém sem alteração. |
| Gerenciado | Pode atualizar somente o bloco gerenciado, com confirmação. |
| Local | Preserva; permite proposta manual ou adiamento. |
| Ambíguo | Preserva e registra pendência ou proposta manual. |

O roteiro registra a classificação, a ação aprovada, o bloco gerenciado anterior e o resultado final, possibilitando reversão sem apagar conteúdo local.

## Impacto para projetos consumidores

| Cenário | Caminho recomendado |
|---|---|
| Projeto novo | Usar `Installer/INSTALADOR_ADF.md` e escolher somente os adaptadores necessários. |
| Projeto com ADF anterior | Usar `Installer/UPDATE.md` e revisar as migrações até a versão 1.8.0. |
| Projeto sem adaptador | Manter como está ou criar um adaptador explicitamente durante instalação/atualização. |
| Projeto com arquivo local de instruções | Preservar o arquivo; não substituir sem marcadores ADF válidos e autorização. |

## Próximas ações recomendadas

1. Executar uma instalação piloto em projeto novo, com e sem adaptadores.
2. Executar uma atualização piloto de um projeto com `AGENTS.md` local e outro com bloco gerenciado.
3. Validar se os comandos de build e testes coletados no instalador são suficientes para o preflight de tarefas reais.
4. Decidir futuramente se Claude, Gemini ou Cursor devem receber templates próprios.

## Evidências

- Todos os commits da linha do tempo foram enviados para `origin/main`.
- Os quatro arquivos de feature estão marcados como concluídos.
- Verificações de links Markdown relativos e `git diff --check` foram executadas em cada fase.
