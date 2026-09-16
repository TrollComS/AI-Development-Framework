# Atualizador do ADF para IA Leitora

Este arquivo e um roteiro operacional para atualizar o ADF em um projeto consumidor que ja possui uma versao instalada.

A IA deve seguir este documento em ordem, fazer uma pergunta por vez, validar respostas e preservar qualquer conteudo local do projeto consumidor.

## Regra principal

Voce, IA leitora, deve agir como atualizadora do ADF.

Nunca atualize copiando o diretorio `docs` inteiro por cima do projeto consumidor.

Nunca apague, substitua ou reescreva documentos preenchidos pelo usuario sem autorizacao explicita.

Nunca copie o diretorio `ADF` do repositorio base para o projeto consumidor. Esse diretorio guarda historico interno do framework.

## Resultado esperado

Ao final, o projeto consumidor deve:

- manter suas adaptacoes locais;
- receber arquivos novos do ADF que ainda nao existiam;
- receber ajustes compativeis em arquivos do Core, Skills, Templates, Prompts e Installer;
- preservar documentos preenchidos em `docs/Projeto`, `docs/Arquitetura`, `docs/Padroes`, `docs/RegrasNegocio`, `docs/Features` e `docs/Revisoes`;
- registrar a versao atualizada e as pendencias em `docs/Projeto/ADF_ADOCAO.md`;
- atualizar `ADF_VERSION.md` para a versao do ADF de origem.
- classificar e tratar adaptadores de agentes sem sobrescrever instrucoes locais.

## Categorias de arquivos

Classifique cada arquivo antes de atualizar.

| Categoria | Caminhos comuns | Regra |
|---|---|---|
| Core do ADF | `docs/AI/Core/**`, `docs/AI/Skills/**`, `docs/AI/Templates/**`, `docs/AI/Prompts/**`, `Installer/**` | Pode receber atualizacao por copia quando ausente ou por merge assistido quando existir. |
| Configuracao local do cliente | `docs/Projeto/**`, `docs/Arquitetura/**`, `docs/Padroes/**`, `docs/RegrasNegocio/**`, `docs/Features/**`, `docs/Revisoes/**` | Nunca sobrescrever automaticamente. Acrescentar apenas conteudo ausente e autorizado. |
| Arquivos de versao | `ADF_VERSION.md`, `CHANGELOG_ADF.md` | Atualizar `ADF_VERSION.md`; copiar ou atualizar `CHANGELOG_ADF.md` se o projeto consumidor mantiver historico do framework. |
| Adaptadores de agentes | `AGENTS.md`, `.github/copilot-instructions.md` | Nunca sobrescrever como arquivo comum. Aplicar a classificacao e o fluxo de adaptadores desta atualizacao. |
| Arquivos internos do repositorio ADF | `ADF/**` | Nao copiar para o projeto consumidor. |

## Dados obrigatorios

| Campo | Pergunta ao usuario | Exemplo ideal |
|---|---|---|
| `ADF_SOURCE_DIR` | Qual e o diretorio completo da versao nova do repositorio ADF? | `D:\RepositorioGit\AI-Development-Framework` |
| `PROJECT_ROOT` | Qual e o diretorio completo da raiz do projeto consumidor que ja possui ADF instalado? | `D:\Projetos\MeuSistema` |
| `TARGET_ADF_VERSION` | Para qual versao do ADF voce deseja atualizar? Se quiser a versao da origem, responda `atual`. | `atual` |

## Validacoes obrigatorias

`ADF_SOURCE_DIR` deve:

- ser um caminho absoluto;
- existir;
- conter `ADF_VERSION.md`;
- conter `CHANGELOG_ADF.md`;
- conter `Installer/MIGRACOES_ADF.md`;
- conter a pasta `docs`;
- conter a pasta `Installer`.

`PROJECT_ROOT` deve:

- ser um caminho absoluto;
- existir;
- conter algum sinal de ADF instalado, como `ADF_VERSION.md`, `docs/INDICE_DOCUMENTACAO.md` ou `docs/AI/Core/ADF_FRAMEWORK.md`;
- nao ser igual a `ADF_SOURCE_DIR`.

## Fluxo de atualizacao

### 1. Apresentar o processo

Diga ao usuario:

```text
Vou atualizar o ADF deste projeto. Vou identificar a versao instalada, comparar com a versao nova, copiar arquivos ausentes e pedir autorizacao antes de alterar qualquer documento existente. Nao vou sobrescrever conteudo local do projeto consumidor.
```

### 2. Coletar e validar caminhos

Pergunte e valide `ADF_SOURCE_DIR` e `PROJECT_ROOT`.

Com PowerShell, a IA pode usar:

```powershell
Test-Path "ADF_SOURCE_DIR\ADF_VERSION.md"
Test-Path "ADF_SOURCE_DIR\CHANGELOG_ADF.md"
Test-Path "ADF_SOURCE_DIR\Installer\MIGRACOES_ADF.md"
Test-Path "ADF_SOURCE_DIR\docs"
Test-Path "PROJECT_ROOT"
Test-Path "PROJECT_ROOT\docs"
```

### 3. Identificar versoes

Leia:

- `ADF_SOURCE_DIR\ADF_VERSION.md`;
- `PROJECT_ROOT\ADF_VERSION.md`, quando existir;
- `PROJECT_ROOT\docs\Projeto\ADF_ADOCAO.md`, quando existir.

Se a versao instalada nao puder ser identificada, registre:

```text
Versao instalada: nao identificada.
```

Nesse caso, use `Installer/MIGRACOES_ADF.md` desde a primeira versao conhecida aplicavel e trate todos os arquivos existentes como conteudo que deve ser preservado.

### 4. Ler mapa de migracoes

Leia `ADF_SOURCE_DIR\Installer\MIGRACOES_ADF.md`.

Identifique todas as secoes entre a versao instalada e a versao alvo.

Se a versao instalada for maior que a versao de origem, pare e diga:

```text
O projeto consumidor parece estar em uma versao mais nova que a origem informada. Nao vou fazer downgrade automatico.
```

### 5. Criar inventario

Liste:

- arquivos novos indicados nas migracoes;
- arquivos existentes que precisam de revisao;
- arquivos locais do cliente que nao devem ser sobrescritos;
- templates de adaptador disponiveis e os arquivos de adaptador presentes;
- arquivos internos do repositorio ADF que nao devem ser copiados.

Com PowerShell, a IA pode usar:

```powershell
Get-ChildItem "ADF_SOURCE_DIR\docs" -Recurse -File
Get-ChildItem "PROJECT_ROOT\docs" -Recurse -File
```

Nao inclua segredos, binarios, arquivos temporarios ou diretorios de build no inventario.

### Classificacao de adaptadores

Para cada adaptador suportado, compare o arquivo do projeto consumidor com seu template de origem:

| Adaptador | Template de origem | Destino |
|---|---|---|
| Universal | `docs/AI/Templates/TEMPLATE_AGENTS.md` | `AGENTS.md` |
| Copilot | `docs/AI/Templates/TEMPLATE_COPILOT_INSTRUCTIONS.md` | `.github/copilot-instructions.md` |

Classifique cada destino antes de propor qualquer edicao:

- `Ausente`: o destino nao existe.
- `Compativel`: contem um unico bloco gerenciado e um unico bloco local, e o bloco gerenciado ja corresponde ao template de origem.
- `Gerenciado`: contem um unico bloco gerenciado e um unico bloco local, mas o bloco gerenciado difere do template de origem.
- `Local`: existe, mas nao contem marcadores ADF.
- `Ambiguo`: os marcadores estao ausentes parcialmente, duplicados, invertidos ou nao permitem identificar com seguranca um unico bloco gerenciado e local.

Nao classifique um arquivo local como gerenciado apenas por ter texto parecido com um template.

### 6. Mostrar plano antes de editar

Antes de qualquer edicao, mostre:

```text
Plano de atualizacao do ADF:
- Versao instalada: VERSAO_INSTALADA
- Versao alvo: VERSAO_ALVO
- Arquivos novos a copiar: LISTA
- Arquivos existentes a revisar por merge assistido: LISTA
- Arquivos locais preservados: LISTA
- Adaptadores encontrados e classificacao: LISTA
- Acoes de adaptador propostas: LISTA
- Arquivos internos do ADF que nao serao copiados: LISTA
- Pendencias previstas: LISTA

Posso aplicar este plano preservando conteudo existente? Responda sim ou nao.
```

Se o usuario responder `nao`, pergunte o que deve mudar no plano.

### 7. Copiar arquivos ausentes

Copie arquivos novos somente se nao existirem no projeto consumidor.

Use preferencialmente copia arquivo a arquivo, guiada pelo mapa de migracoes.

Nao use comando que sobrescreva tudo.

### 8. Tratar arquivos existentes

Para cada arquivo existente que precisa de atualizacao:

1. Compare origem e destino.
2. Identifique apenas secoes, links ou regras novas.
3. Preserve o texto local.
4. Mostre um resumo do que sera acrescentado.
5. Peca autorizacao antes de editar.

Mensagem sugerida:

```text
O arquivo CAMINHO ja existe no projeto consumidor. Encontrei diferencas do ADF novo que parecem aplicaveis.

Vou preservar o conteudo atual e acrescentar apenas:
- ITEM_1
- ITEM_2

Posso aplicar esse merge? Responda sim ou nao.
```

Se o usuario responder `nao`, registre pendencia em `docs/Projeto/ADF_ADOCAO.md`.

### 9. Tratar adaptadores de agentes

Execute esta etapa depois de copiar os templates ausentes e antes de executar etapas novas do instalador.

Mostre os adaptadores disponiveis, sua classificacao e as opcoes permitidas:

| Classificacao | Opcoes permitidas |
|---|---|
| Ausente | criar a partir do template ou adiar. |
| Compativel | manter sem alteracao. |
| Gerenciado | atualizar somente o bloco gerenciado, manter sem alteracao ou adiar. |
| Local | preservar, criar proposta manual ou adiar. |
| Ambiguo | preservar e registrar pendencia, ou criar proposta manual. |

Pergunte uma opcao por adaptador. Nao presuma que o projeto usa Codex, Copilot ou qualquer outra ferramenta.

Para um adaptador `Ausente`, crie o arquivo somente se o usuario escolher `criar`. Para `Copilot`, crie a pasta `.github` somente quando necessario para criar o arquivo selecionado.

Para um adaptador `Gerenciado`, leia o arquivo e pergunte:

```text
Encontrei CAMINHO com um bloco gerenciado pelo ADF. Posso substituir somente esse bloco pelo conteudo do template atual, preservando o bloco local e todo texto fora dos marcadores? Responda sim ou nao.
```

Se houver autorizacao, substitua somente o conteudo entre `ADF:BEGIN MANAGED` e `ADF:END MANAGED`. Nunca altere o bloco local nem conteudo fora dos marcadores.

Para adaptadores `Local` ou `Ambiguo`, nunca sobrescreva o arquivo. Se o usuario escolher proposta manual, mostre o bloco gerenciado que poderia ser inserido e aguarde uma autorizacao posterior para qualquer alteracao. Se escolher adiar ou preservar, registre a pendencia ou preservacao.

Antes de alterar qualquer adaptador, registre em um relatorio de atualizacao o caminho, classificacao, acao aprovada e o bloco gerenciado anterior, quando existir. O relatorio pode ficar em `docs/Revisoes/` ou no mecanismo de historico aprovado pelo projeto. Isso permite reversao sem perder instrucao local.

### 10. Executar etapas novas introduzidas pelo instalador

Depois de atualizar ou revisar `Installer/INSTALADOR_ADF.md`, compare a versao antiga e a nova do instalador.

Procure novas perguntas, etapas opcionais, etapas obrigatorias, validacoes, arquivos obrigatorios ou documentos recomendados que nao existiam na versao instalada.

Classifique cada item novo:

- `Obrigatorio`: necessario para o ADF atualizado funcionar corretamente.
- `Opcional`: melhora contexto ou seguranca, mas pode ser recusado pelo usuario.
- `Pendente`: exige decisao humana, acesso externo ou informacao ainda indisponivel.

Mostre ao usuario:

```text
Encontrei novas etapas no instalador atualizado:

- Obrigatorias: LISTA
- Opcionais: LISTA
- Pendentes: LISTA

Deseja executar agora as etapas novas aplicaveis? Responda sim ou nao.
```

Se o usuario responder `sim`, conduza somente as etapas novas. Nao repita perguntas antigas ja respondidas, nao reinstale o ADF e nao sobrescreva documentos existentes.

Se uma etapa nova criar ou atualizar documento local do projeto consumidor, siga as mesmas regras de preservacao deste atualizador: verificar existencia, mostrar resumo, pedir autorizacao e registrar pendencia quando nao houver autorizacao.

Se o usuario responder `nao`, registre as etapas novas como pendencias em `docs/Projeto/ADF_ADOCAO.md`.

### 11. Registrar atualizacao

Atualize `PROJECT_ROOT\docs\Projeto\ADF_ADOCAO.md` sem apagar historico.

Acrescente uma linha em adaptacoes aceitas ou pendencias, conforme o caso.

Exemplo:

```markdown
| Atualizacao do ADF para VERSAO_ALVO | Migracao assistida preservando conteudo local | Arquivos novos copiados e merges autorizados | RESPONSAVEL | DATA_ATUAL |
```

Se houver pendencias:

```markdown
| Revisar merge pendente do arquivo CAMINHO | RESPONSAVEL | A definir | Pendente |
```

Registre tambem adaptadores criados, atualizados, preservados ou adiados. Nao substitua as escolhas existentes em `CONFIGURACAO_IAS.md` ou `ADF_ADOCAO.md`; acrescente somente campos ausentes ou uma entrada historica depois de mostrar o resumo e receber autorizacao.

### 12. Atualizar versao

Atualize `PROJECT_ROOT\ADF_VERSION.md` para a versao alvo.

Se o projeto consumidor tiver adaptacoes locais nesse arquivo, preserve-as e acrescente a versao nova sem apagar observacoes existentes.

### 13. Validacao final

Verifique:

```powershell
Test-Path "PROJECT_ROOT\ADF_VERSION.md"
Test-Path "PROJECT_ROOT\docs\INDICE_DOCUMENTACAO.md"
Test-Path "PROJECT_ROOT\docs\AI\Core\ADF_FRAMEWORK.md"
Test-Path "PROJECT_ROOT\docs\Projeto\ADF_ADOCAO.md"
```

Verifique tambem os arquivos novos listados em `MIGRACOES_ADF.md`.

Confirme que:

- nenhum arquivo local do cliente foi sobrescrito sem autorizacao;
- o diretorio `ADF` nao foi copiado para o projeto consumidor;
- `docs/Features` contem apenas features do projeto consumidor;
- novas etapas do instalador foram executadas ou registradas como pendencia;
- adaptadores locais ou ambiguos foram preservados sem sobrescrita;
- adaptadores gerenciados alterados tiveram somente o bloco gerenciado modificado;
- pendencias foram registradas quando um merge foi recusado ou incerto;
- links adicionados apontam para arquivos existentes.

## Mensagem final ao usuario

Ao concluir, responda:

```text
Atualizacao do ADF concluida.

Versao anterior: VERSAO_INSTALADA
Versao atual: VERSAO_ALVO

Arquivos copiados:
- LISTA

Arquivos atualizados por merge assistido:
- LISTA

Arquivos preservados sem alteracao:
- LISTA

Adaptadores criados ou atualizados:
- LISTA

Adaptadores preservados:
- LISTA

Pendencias:
- LISTA
```

Se algo falhar, responda:

```text
A atualizacao do ADF nao foi concluida.

Ponto de parada:
DESCREVA_O_PROBLEMA

O que preciso do usuario:
RESPOSTA_OU_AUTORIZACAO_NECESSARIA
```

## Checklist da IA atualizadora

- [ ] Li este atualizador ate o fim.
- [ ] Validei `ADF_SOURCE_DIR`.
- [ ] Validei `PROJECT_ROOT`.
- [ ] Identifiquei versao instalada e versao alvo.
- [ ] Li `Installer/MIGRACOES_ADF.md`.
- [ ] Classifiquei arquivos por categoria.
- [ ] Mostrei plano antes de editar.
- [ ] Copiei somente arquivos ausentes.
- [ ] Pedi autorizacao antes de alterar arquivos existentes.
- [ ] Classifiquei adaptadores como ausente, compativel, gerenciado, local ou ambiguo.
- [ ] Criei ou atualizei adaptadores somente com autorizacao e sem alterar conteudo local.
- [ ] Registrei adaptadores preservados, adiados e pendencias.
- [ ] Identifiquei novas etapas introduzidas pelo instalador atualizado.
- [ ] Executei etapas novas autorizadas ou registrei pendencias.
- [ ] Preservei documentos locais do projeto consumidor.
- [ ] Nao copiei o diretorio `ADF`.
- [ ] Atualizei ou registrei pendencia em `ADF_ADOCAO.md`.
- [ ] Atualizei `ADF_VERSION.md`.
- [ ] Validei arquivos finais e links aplicaveis.
