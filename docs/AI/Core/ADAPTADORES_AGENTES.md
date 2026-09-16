# Adaptadores de instrução para agentes

Este guia define como um projeto consumidor pode expor o ADF a ferramentas que carregam arquivos de instrução automaticamente. Consulte primeiro o [contrato do ADF](ADF_FRAMEWORK.md#contrato-de-instruções-para-agentes).

## Princípio

`docs/` continua sendo a fonte canônica. Um adaptador apenas informa à ferramenta onde encontrar o contexto e qual preflight aplicar. Ele não deve reproduzir integralmente regras, arquitetura, features, decisões ou documentação operacional.

## Adaptadores disponíveis

| Adaptador | Template | Destino no projeto consumidor | Uso |
|---|---|---|---|
| Universal | [`TEMPLATE_AGENTS.md`](../Templates/TEMPLATE_AGENTS.md) | `AGENTS.md` | Entrada recomendada para agentes que reconhecem instruções universais. |
| GitHub Copilot | [`TEMPLATE_COPILOT_INSTRUCTIONS.md`](../Templates/TEMPLATE_COPILOT_INSTRUCTIONS.md) | `.github/copilot-instructions.md` | Contexto de repositório para recursos compatíveis do Copilot. |

Os adaptadores são opt-in. Um projeto pode usar somente `AGENTS.md`, somente o adaptador Copilot, ambos ou nenhum, conforme as ferramentas que adotou.

## Formatos avaliados e não incluídos nesta versão

`CLAUDE.md`, `GEMINI.md` e regras `.cursor/rules/*.mdc` têm formatos de instrução conhecidos, mas não recebem templates nesta versão. O instalador e o atualizador suportam somente `AGENTS.md` e Copilot; formatos adicionais só devem ser oferecidos quando tiverem template, seleção explícita e preservação local segura.

Essa decisão evita instalar arquivos que o projeto não usa e mantém a evolução desses formatos na feature de instalador correspondente.

## Blocos gerenciados e locais

Cada template contém dois blocos delimitados por comentários HTML:

- `ADF:BEGIN MANAGED` / `ADF:END MANAGED`: conteúdo mantido pelo ADF, identificando template e versão de origem.
- `ADF:BEGIN LOCAL` / `ADF:END LOCAL`: espaço destinado a regras exclusivas do projeto ou da ferramenta.

Em uma atualização futura, apenas o bloco gerenciado pode ser substituído, depois de confirmação humana. Conteúdo local, conteúdo fora dos marcadores ou marcadores ausentes devem ser preservados; se houver ambiguidade, registre uma pendência em vez de sobrescrever o arquivo.

## Ordem de leitura e precedência

O adaptador deve encaminhar para o [preflight obrigatório](ADF_FRAMEWORK.md#preflight-obrigatório). A precedência é:

1. Instruções explícitas do usuário e regras de segurança.
2. Documentação canônica do ADF e decisões locais em `docs/`.
3. Bloco local do adaptador, desde que não contradiga `docs/`.
4. Bloco gerenciado do adaptador.

Quando houver divergência, corrija a fonte apropriada. Não compense uma documentação desatualizada copiando regra nova para vários adaptadores.

## Regras por caminho

Regras específicas de caminho são extensões opcionais para módulos que realmente possuem convenções, validações ou riscos diferentes. No Copilot, elas podem ficar em `.github/instructions/**/*.instructions.md`.

Elas devem apontar para o contexto canônico, declarar o caminho a que se aplicam e conter apenas a diferença daquele módulo. Não substituem o `AGENTS.md`, o adaptador de repositório ou o índice documental.

## Aplicação manual

1. Escolha somente os adaptadores compatíveis com as ferramentas usadas pelo projeto.
2. Copie o template para o destino indicado, preservando a capitalização de `AGENTS.md`.
3. Preencha apenas o bloco local com instruções exclusivas e verificáveis.
4. Atualize `docs/Projeto/CONFIGURACAO_IAS.md` e `docs/Projeto/ADF_ADOCAO.md` para registrar a ferramenta e a decisão de adoção.
5. Verifique os links relativos depois de copiar, pois o template de Copilot é destinado ao diretório `.github`.

Não instale programas, extensões, modelos ou credenciais como parte dessa aplicação documental.
