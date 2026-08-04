# Instalador do ADF para IA Leitora

Este arquivo e um roteiro operacional para uma IA instalar o ADF em qualquer projeto. A IA deve seguir este documento em ordem, fazer uma pergunta por vez, esperar a resposta do usuario, validar a resposta e somente entao executar comandos ou editar arquivos.

O usuario nao precisa abrir outros arquivos do ADF durante a instalacao. Este instalador deve conduzir a coleta de dados, copiar o esqueleto do ADF e preencher os arquivos principais.

## Regra principal

Voce, IA leitora, deve agir como instaladora do ADF.

Nao avance quando uma informacao obrigatoria estiver ausente, ambigua ou incompleta. Peca uma resposta mais clara, mostre um exemplo ideal e aguarde nova resposta.

Nunca invente:

- diretorio raiz do projeto;
- diretorio onde o ADF foi baixado;
- nome da IA Pensante;
- nome da IA Dev Principal;
- modelos disponiveis no OpenCode;
- responsaveis pelo ADF no projeto.

Nunca apague conteudo existente sem autorizacao explicita do usuario.

## Resultado esperado

Ao final, o projeto consumidor deve conter:

- `ADF_VERSION.md`
- `docs/INDICE_DOCUMENTACAO.md`
- `docs/AI/**`
- `docs/Projeto/**`
- `docs/Arquitetura/**`
- `docs/Padroes/**`
- `docs/RegrasNegocio/**`
- `docs/Features/**`
- `docs/Revisoes/**`
- `docs/Samples/**`

E os arquivos abaixo devem estar preenchidos com as respostas do usuario:

- `docs/Projeto/CONFIGURACAO_IAS.md`
- `docs/Projeto/ADF_ADOCAO.md`

Opcionalmente, quando o usuario autorizar, o instalador tambem pode criar:

- `docs/Projeto/LIMITACOES_EXECUCAO_FEATURES.md`
- `docs/Projeto/VISAO_PROJETO.md`
- `docs/Arquitetura/MAPA_PROJETOS.md`
- `docs/Arquitetura/COMPONENTES.md`
- `docs/Arquitetura/INTEGRACOES.md`
- `docs/Padroes/PADROES_TECNICOS.md`
- `docs/RegrasNegocio/README.md` atualizado com pendencias e regras confirmadas

## Como conduzir a conversa

Faca uma pergunta por vez.

Para cada resposta:

1. Verifique se a resposta e curta, objetiva e utilizavel.
2. Se estiver clara, registre internamente o valor e diga que vai continuar.
3. Se estiver vaga, pare e peca uma resposta melhor.
4. Se o usuario pedir exemplo ou sugestao, mostre exemplos e repita a mesma pergunta.
5. Se precisar executar comando, explique o comando antes, execute, leia o resultado e continue.

Para perguntas de decisao `sim`/`nao`, aceite somente respostas equivalentes a `sim` ou `nao`.

Respostas aceitas como `sim`:

- `sim`
- `s`
- `yes`
- `y`

Respostas aceitas como `nao`:

- `nao`
- `não`
- `n`
- `no`

Se a resposta nao for clara, diga:

```text
Preciso de uma resposta simples: sim ou nao.
```

Modelo para resposta invalida:

```text
Preciso de uma resposta mais clara para continuar.

Exemplo de resposta ideal:
D:\Projetos\MeuSistema

Por favor, envie apenas o diretorio completo da raiz do projeto.
```

## Dados obrigatorios

Colete e valide estes dados antes de copiar ou editar qualquer arquivo.

| Campo | Pergunta ao usuario | Exemplo ideal | Onde gravar |
|---|---|---|---|
| `ADF_SOURCE_DIR` | Qual e o diretorio completo onde o repositorio ADF foi baixado? | `D:\RepositorioGit\AI-Development-Framework` | Usado para copiar o esqueleto |
| `PROJECT_ROOT` | Qual e o diretorio completo da raiz do projeto onde o ADF sera instalado? | `D:\Projetos\MeuSistema` | `docs/Projeto/ADF_ADOCAO.md` |
| `ADF_OWNER` | Quem sera o proprietario do ADF neste projeto? | `Marcos` | `docs/Projeto/ADF_ADOCAO.md` |
| `ADF_REVIEWERS` | Quem revisa o ADF neste projeto? Separe por virgula. | `Marcos, Ana` | `docs/Projeto/ADF_ADOCAO.md` |
| `REVIEW_CADENCE` | Qual sera a cadencia de revisao do ADF? | `Mensal` | `docs/Projeto/ADF_ADOCAO.md` |
| `THINKING_AI` | Qual e o nome da IA Pensante principal? | `ChatGPT Codex` | `docs/Projeto/CONFIGURACAO_IAS.md` |
| `DEV_AI` | Qual e o nome da IA Dev Principal? | `Claude Code` | `docs/Projeto/CONFIGURACAO_IAS.md` |
| `DEV_AI_FALLBACK` | Se a IA Dev Principal estiver indisponivel, qual rota alternativa deve ser usada? | `OpenCode com qwen2.5-coder` | `docs/Projeto/CONFIGURACAO_IAS.md` |
| `OPENCODE_MODELS` | Quais modelos gratuitos voce vai usar no OpenCode? Separe por virgula. | `qwen2.5-coder, deepseek-coder, llama3.1` | `docs/Projeto/CONFIGURACAO_IAS.md` |
| `FEATURE_STATES` | Quais estados de feature o projeto usara? | `Proposta, Planejada, Em execucao, Em revisao, Concluida` | `docs/Projeto/ADF_ADOCAO.md` |
| `FEATURE_ID_PATTERN` | Qual padrao de identificacao de features sera usado? | `FEATURE_NOME_DA_FEATURE.md` | `docs/Projeto/ADF_ADOCAO.md` |
| `PROJECT_DIR_MAP` | Quais diretorios reais do projeto devem ser mapeados no ADF? | `src=Codigo principal, tests=Testes, docs=Documentacao` | `docs/Projeto/ADF_ADOCAO.md` |

## Dados opcionais

Colete estes dados somente quando o usuario responder `sim` para a etapa correspondente.

| Campo | Pergunta ao usuario | Exemplo ideal | Onde gravar |
|---|---|---|---|
| `FEATURE_EXECUTION_LIMITATIONS_ENABLED` | Deseja registrar limitacoes para execucao de features neste projeto? Responda sim ou nao. | `sim` | Controle do fluxo |
| `FEATURE_EXECUTION_LIMITATIONS` | Informe as limitacoes em formato simples. | `Nao alterar Scripts sem autorizacao; nao modificar fluxo de pagamento sem revisao; sempre executar build antes de finalizar.` | `docs/Projeto/LIMITACOES_EXECUCAO_FEATURES.md` |
| `INITIAL_PROJECT_DOCS_ENABLED` | Deseja que eu analise o projeto atual e gere uma documentacao inicial nos arquivos do ADF? Responda sim ou nao. | `sim` | Controle do fluxo |

As etapas opcionais devem ser executadas depois da instalacao basica e antes da validacao final.

## Validacoes obrigatorias

### Diretorios

`ADF_SOURCE_DIR` deve:

- ser um caminho absoluto;
- existir;
- conter `ADF_VERSION.md`;
- conter a pasta `docs`;
- conter a pasta `Installer`.

`PROJECT_ROOT` deve:

- ser um caminho absoluto;
- existir;
- ser a raiz real do projeto consumidor;
- nao ser igual a `ADF_SOURCE_DIR`.

Se algum diretorio falhar:

```text
Nao consegui validar esse diretorio.

Exemplo de resposta ideal:
D:\Projetos\MeuSistema

Confirme o caminho completo da raiz do projeto.
```

### Nomes de IAs

`THINKING_AI` e `DEV_AI` devem:

- ter pelo menos 2 caracteres;
- ser nomes claros de ferramenta, modelo ou agente;
- nao ser respostas como `sim`, `nao`, `tanto faz`, `qualquer um`.

Se o usuario pedir sugestoes, ofereca:

```text
Sugestoes para IA Pensante:
- ChatGPT Codex
- ChatGPT
- Gemini

Sugestoes para IA Dev Principal:
- Claude Code
- Codex
- Cursor Agent
- OpenCode com modelo principal
```

Depois repita a pergunta original.

### Modelos do OpenCode

`OPENCODE_MODELS` deve:

- ter um ou mais nomes separados por virgula;
- nao conter segredo, token ou chave;
- representar apenas modelos que o usuario afirma ter configurado gratuitamente.

Se o usuario pedir exemplo:

```text
Exemplo:
qwen2.5-coder, deepseek-coder, llama3.1

Envie os nomes exatamente como voce reconhece no seu OpenCode, separados por virgula.
```

### Respostas longas ou confusas

Se a resposta misturar explicacao com valor, extraia somente se o valor estiver evidente. Se nao estiver evidente, peca confirmacao.

Exemplo:

```text
Entendi a explicacao, mas preciso do valor final em formato simples.

Responda assim:
IA Dev Principal: Claude Code
```

## Fluxo de instalacao

### 1. Apresentar o processo

Diga ao usuario:

```text
Vou instalar o ADF neste projeto. Vou fazer algumas perguntas obrigatorias, validar os caminhos, copiar o esqueleto do ADF e preencher os arquivos principais. Nao vou apagar conteudo existente sem sua autorizacao.
```

### 2. Coletar `ADF_SOURCE_DIR`

Pergunte:

```text
Qual e o diretorio completo onde o repositorio ADF foi baixado?
```

Valide o caminho.

Com PowerShell, a IA pode usar:

```powershell
Test-Path "CAMINHO_INFORMADO"
Test-Path "CAMINHO_INFORMADO\ADF_VERSION.md"
Test-Path "CAMINHO_INFORMADO\docs"
Test-Path "CAMINHO_INFORMADO\Installer"
```

### 3. Coletar `PROJECT_ROOT`

Pergunte:

```text
Qual e o diretorio completo da raiz do projeto onde o ADF sera instalado?
```

Valide o caminho e confirme que nao e o mesmo diretorio do ADF baixado.

Com PowerShell:

```powershell
Test-Path "CAMINHO_INFORMADO"
```

### 4. Verificar risco de sobrescrita

Antes de copiar, verifique se o projeto ja possui `docs`, `ADF_VERSION.md` ou arquivos ADF.

Com PowerShell:

```powershell
Test-Path "PROJECT_ROOT\docs"
Test-Path "PROJECT_ROOT\ADF_VERSION.md"
```

Se existir conteudo, diga:

```text
Encontrei arquivos ou pastas que podem receber arquivos do ADF. Vou preservar o que ja existe e copiar apenas o que estiver ausente. Se houver conflito de arquivo, vou parar e pedir autorizacao antes de sobrescrever.
```

### 5. Copiar o esqueleto do ADF

Copie os itens principais do ADF para o projeto consumidor.

Itens a copiar:

- `ADF_VERSION.md`
- `docs`

Nao copie o diretorio `ADF` do repositorio base durante a instalacao comum. Esse diretorio guarda features e historico interno do framework, nao documentos do projeto consumidor.

Opcionalmente, se o usuario quiser manter os documentos de instalacao no projeto consumidor, copie tambem:

- `Installer`

Pergunte:

```text
Voce quer copiar tambem a pasta Installer para o projeto consumidor? Responda sim ou nao.
```

Se a resposta nao for clara, peca:

```text
Preciso de uma resposta simples: sim ou nao.
```

#### Comando PowerShell recomendado

Use este comando somente depois de validar `ADF_SOURCE_DIR` e `PROJECT_ROOT`.

```powershell
robocopy "ADF_SOURCE_DIR\docs" "PROJECT_ROOT\docs" /E /XC /XN /XO
copy "ADF_SOURCE_DIR\ADF_VERSION.md" "PROJECT_ROOT\ADF_VERSION.md"
```

Se o usuario aprovou copiar `Installer`:

```powershell
robocopy "ADF_SOURCE_DIR\Installer" "PROJECT_ROOT\Installer" /E /XC /XN /XO
```

Importante:

- `/E` copia subpastas;
- `/XC /XN /XO` evita sobrescrever arquivos alterados, mais novos ou mais antigos;
- se houver conflito, pare e peca decisao ao usuario.

### 6. Coletar configuracao de responsaveis

Pergunte uma por vez:

```text
Quem sera o proprietario do ADF neste projeto?
```

```text
Quem revisa o ADF neste projeto? Separe por virgula.
```

```text
Qual sera a cadencia de revisao do ADF?
```

Exemplos:

- Proprietario: `Marcos`
- Revisores: `Marcos, Ana`
- Cadencia: `Mensal`

### 7. Coletar configuracao de IAs

Pergunte uma por vez:

```text
Qual e o nome da IA Pensante principal?
```

```text
Qual e o nome da IA Dev Principal?
```

```text
Se a IA Dev Principal estiver indisponivel, qual rota alternativa deve ser usada?
```

```text
Quais modelos gratuitos voce vai usar no OpenCode? Separe por virgula.
```

Se o usuario disser que nao usa OpenCode, informe:

```text
O ADF deste projeto esta configurado para exigir OpenCode com modelos gratuitos. Para instalar corretamente, preciso que voce informe os modelos gratuitos configurados ou autorize registrar uma pendencia de implantacao.
```

Se o usuario autorizar pendencia, registre `A definir` nos modelos e adicione pendencia em `ADF_ADOCAO.md`.

### 8. Coletar convencoes locais

Pergunte uma por vez:

```text
Quais estados de feature o projeto usara?
```

```text
Qual padrao de identificacao de features sera usado?
```

```text
Quais diretorios reais do projeto devem ser mapeados no ADF?
```

Se o usuario pedir sugestoes, ofereca:

```text
Sugestao de estados:
Proposta, Planejada, Em execucao, Em revisao, Concluida, Cancelada

Sugestao de padrao:
FEATURE_NOME_DA_FEATURE.md

Sugestao de mapeamento:
src=Codigo principal, tests=Testes automatizados, docs=Documentacao, scripts=Automacoes
```

Depois repita a pergunta original.

### 9. Perguntar sobre limitacoes de execucao de features

Pergunte:

```text
Deseja registrar limitacoes para execucao de features neste projeto? Responda sim ou nao.
```

Valide a resposta como `sim` ou `nao`.

Se a resposta for `nao`, registre internamente:

```text
Limitacoes de execucao: nao registradas por escolha do usuario.
```

Nao crie `docs/Projeto/LIMITACOES_EXECUCAO_FEATURES.md` obrigatoriamente.

Se a resposta for `sim`, pergunte:

```text
Informe as limitacoes em formato simples.
```

Exemplo:

```text
Nao alterar Scripts sem autorizacao; nao modificar fluxo de pagamento sem revisao; sempre executar build antes de finalizar.
```

Valide que a resposta:

- contem pelo menos uma limitacao objetiva;
- nao contem segredo, token ou chave;
- pode ser revisada por humanos;
- nao contradiz o fluxo obrigatorio do ADF.

Se a resposta estiver vaga, peca uma versao mais objetiva.

Antes de criar o arquivo, verifique:

```powershell
Test-Path "PROJECT_ROOT\docs\Projeto\LIMITACOES_EXECUCAO_FEATURES.md"
```

Se o arquivo ja existir, leia o conteudo e diga:

```text
Ja existe um documento de limitacoes de execucao. Vou preservar o conteudo existente. Posso acrescentar as novas limitacoes ao final do arquivo? Responda sim ou nao.
```

Se o usuario responder `nao`, nao altere o arquivo e registre a pendencia em `ADF_ADOCAO.md`.

Se o arquivo nao existir ou o usuario autorizar acrescentar, crie ou atualize o documento usando o template `docs/AI/Templates/TEMPLATE_LIMITACOES_EXECUCAO_FEATURES.md`.

O arquivo deve deixar claro que as limitacoes foram informadas pelo usuario durante a instalacao.

### 10. Perguntar sobre documentacao inicial do projeto

Pergunte:

```text
Deseja que eu analise o projeto atual e gere uma documentacao inicial nos arquivos do ADF? Responda sim ou nao.
```

Valide a resposta como `sim` ou `nao`.

Se a resposta for `nao`, registre internamente:

```text
Documentacao inicial do projeto: nao realizada por escolha do usuario.
```

Execute apenas a instalacao basica do ADF.

Se a resposta for `sim`, analise a estrutura real do projeto consumidor antes de editar documentos.

Priorize:

- arquivos de solucao e projeto, como `.sln`, `.csproj`, `.fsproj`, `.vbproj`, `package.json`, `pom.xml`, `build.gradle`, `pyproject.toml`, `go.mod`, `Cargo.toml`;
- diretorios principais, como `src`, `tests`, `test`, `app`, `api`, `web`, `frontend`, `backend`, `scripts`, `infra`, `docs`;
- documentacao existente, como `README.md`, `CHANGELOG.md`, `docs/**`;
- nomes de modulos, projetos, pacotes e servicos;
- arquivos de configuracao que indiquem integracoes, sem expor segredos.

Nao leia nem copie valores de segredos, tokens, chaves ou arquivos sensiveis.

Com PowerShell, a IA pode usar consultas similares a:

```powershell
Get-ChildItem "PROJECT_ROOT" -Force -File
Get-ChildItem "PROJECT_ROOT" -Force -Directory
Get-ChildItem "PROJECT_ROOT" -Recurse -File -Include *.sln,*.csproj,*.fsproj,*.vbproj,package.json,pom.xml,build.gradle,pyproject.toml,go.mod,Cargo.toml,README.md,CHANGELOG.md
```

Mantenha a documentacao inicial curta, objetiva e util para orientar features futuras.

Os documentos que podem ser criados ou preenchidos sao:

- `docs/Projeto/VISAO_PROJETO.md`
- `docs/Arquitetura/MAPA_PROJETOS.md`
- `docs/Arquitetura/COMPONENTES.md`
- `docs/Arquitetura/INTEGRACOES.md`
- `docs/Padroes/PADROES_TECNICOS.md`
- `docs/RegrasNegocio/README.md`

Use `docs/AI/Templates/TEMPLATE_DOCUMENTACAO_INICIAL_PROJETO.md` como contrato de preenchimento.

Cada informacao registrada deve ser marcada em uma destas categorias:

- `Informado pelo usuario`: dado declarado explicitamente pelo usuario.
- `Inferido da estrutura do projeto`: dado deduzido a partir de arquivos, diretorios ou nomes.
- `Pendente de confirmacao humana`: dado incerto, incompleto ou nao comprovado.

Nao registre regras de negocio como verdade quando elas forem apenas suspeitas. Quando nao houver confianca suficiente, registre a regra como pendencia em `docs/RegrasNegocio/README.md`.

Antes de criar ou atualizar cada documento, verifique se ele ja existe.

Se existir, diga:

```text
O arquivo CAMINHO_DO_DOCUMENTO ja existe. Posso acrescentar uma secao de documentacao inicial preservando o conteudo atual? Responda sim ou nao.
```

Se o usuario responder `nao`, preserve o arquivo e registre a pendencia em `docs/Projeto/ADF_ADOCAO.md`.

Se o arquivo nao existir, crie-o com conteudo inicial curto.

Ao criar novos documentos, atualize `docs/INDICE_DOCUMENTACAO.md` e `docs/AI/Core/MAPA_DOCUMENTACAO.md` para apontar para eles. Se esses indices ja existirem no projeto consumidor, preserve o conteudo atual e acrescente apenas links ausentes.

## Como preencher `docs/Projeto/CONFIGURACAO_IAS.md`

Abra `PROJECT_ROOT\docs\Projeto\CONFIGURACAO_IAS.md` e atualize os campos abaixo.

### Estado

Substitua:

```text
- **Responsavel por manter esta configuracao:** A definir
- **Ultima revisao:** A definir
```

Por:

```text
- **Responsavel por manter esta configuracao:** ADF_OWNER
- **Ultima revisao:** DATA_ATUAL
```

### IA Pensante principal

Substitua:

```text
- **Ferramenta/modelo:** A definir
```

Na primeira ocorrencia da secao `IA Pensante principal`, por:

```text
- **Ferramenta/modelo:** THINKING_AI
```

### IA Dev Principal

Substitua:

```text
- **Ferramenta/modelo:** A definir
- **Rota alternativa se indisponivel:** A definir
```

Na secao `IA Dev Principal`, por:

```text
- **Ferramenta/modelo:** DEV_AI
- **Rota alternativa se indisponivel:** DEV_AI_FALLBACK
```

### Modelos gratuitos do OpenCode

Na tabela `Modelos gratuitos disponiveis`, substitua as linhas `A definir` por uma linha para cada modelo informado em `OPENCODE_MODELS`.

Use este formato:

```markdown
| NOME_DO_MODELO | Uso geral conforme capacidade local | Tarefas criticas sem revisao humana | Informado pelo usuario na instalacao |
```

Exemplo com tres modelos:

```markdown
| qwen2.5-coder | Pequenos ajustes, testes e analise local | Arquitetura critica sem revisao | Informado pelo usuario na instalacao |
| deepseek-coder | Implementacao localizada e leitura de codigo | Mudancas amplas sem plano | Informado pelo usuario na instalacao |
| llama3.1 | Documentacao, resumo e apoio de contexto | Codigo pesado sem validacao | Informado pelo usuario na instalacao |
```

## Como preencher `docs/Projeto/ADF_ADOCAO.md`

Abra `PROJECT_ROOT\docs\Projeto\ADF_ADOCAO.md` e atualize os campos abaixo.

### Responsaveis

Substitua:

```text
- **Proprietario do ADF no projeto:** A definir
- **Revisores:** A definir
- **Cadencia de revisao:** A definir
```

Por:

```text
- **Proprietario do ADF no projeto:** ADF_OWNER
- **Revisores:** ADF_REVIEWERS
- **Cadencia de revisao:** REVIEW_CADENCE
```

### Decisoes locais

Substitua:

```text
- **Estados de feature usados:** A definir
- **Padrao de identificacao de features:** A definir
- **Diretorios do projeto mapeados para o ADF:** A definir
- **Ferramentas obrigatorias:** A definir
```

Por:

```text
- **Estados de feature usados:** FEATURE_STATES
- **Padrao de identificacao de features:** FEATURE_ID_PATTERN
- **Diretorios do projeto mapeados para o ADF:** PROJECT_DIR_MAP
- **Ferramentas obrigatorias:** OpenCode; THINKING_AI; DEV_AI
```

### Adaptacoes aceitas

Se nao houver adaptacao local alem da configuracao padrao, preencha:

```markdown
| Instalacao inicial do ADF | Adocao do framework no projeto | Cria estrutura documental e roteamento de IAs | ADF_OWNER | REVIEW_CADENCE |
```

### Pendencias de implantacao

Se nao houver pendencias, preencha:

```markdown
| Nenhuma pendencia inicial | ADF_OWNER | Nao aplicavel | Concluido |
```

Se OpenCode ou modelos ficarem pendentes, preencha:

```markdown
| Configurar modelos gratuitos no OpenCode | ADF_OWNER | A definir | Pendente |
```

Se limitacoes de execucao ou documentacao inicial ficarem pendentes por falta de autorizacao para atualizar arquivos existentes, registre tambem uma linha objetiva na tabela de pendencias.

Exemplos:

```markdown
| Revisar atualizacao de LIMITACOES_EXECUCAO_FEATURES.md | ADF_OWNER | A definir | Pendente |
| Revisar documentacao inicial preservada sem atualizacao automatica | ADF_OWNER | A definir | Pendente |
```

## Como criar `docs/Projeto/LIMITACOES_EXECUCAO_FEATURES.md`

Crie este arquivo somente quando o usuario responder `sim` para registrar limitacoes.

Use este formato:

```markdown
# Limitacoes de execucao de features

**Estado:** Ativo
**Origem:** Informado pelo usuario durante a instalacao do ADF
**Ultima revisao:** DATA_ATUAL
**Responsavel:** ADF_OWNER

## Leitura obrigatoria

Toda IA deve ler este documento antes de planejar ou executar features neste projeto.

## Limitacoes informadas pelo usuario

- LIMITACAO_1
- LIMITACAO_2

## Pendencias de confirmacao humana

- Nenhuma pendencia inicial registrada.
```

Se o usuario informar as limitacoes separadas por ponto e virgula, transforme cada item em uma linha.

Nao adicione limitacoes inferidas pela IA. Quando uma limitacao parecer necessaria mas nao tiver sido informada, registre em `Pendencias de confirmacao humana`.

## Como gerar documentacao inicial do projeto

Gere a documentacao inicial somente quando o usuario responder `sim`.

Antes de editar, apresente um resumo da analise:

```text
Resumo da analise para documentacao inicial:
- Arquivos de solucao/projeto encontrados: LISTA
- Diretorios principais encontrados: LISTA
- Documentacao existente encontrada: LISTA
- Integracoes ou tecnologias aparentes: LISTA
- Pendencias que exigem confirmacao humana: LISTA

Posso criar ou atualizar os documentos iniciais do ADF preservando conteudo existente? Responda sim ou nao.
```

Se o usuario responder `nao`, nao gere a documentacao inicial e registre pendencia em `ADF_ADOCAO.md`.

Se o usuario responder `sim`, preencha apenas o que for sustentado por fontes claras:

- `docs/Projeto/VISAO_PROJETO.md`: proposito, escopo, stakeholders e restricoes quando informados ou inferiveis com baixa incerteza.
- `docs/Arquitetura/MAPA_PROJETOS.md`: solucoes, projetos, pacotes e modulos identificados.
- `docs/Arquitetura/COMPONENTES.md`: componentes e responsabilidades aparentes.
- `docs/Arquitetura/INTEGRACOES.md`: integracoes identificadas por configuracoes, pacotes, nomes de clientes ou documentacao existente.
- `docs/Padroes/PADROES_TECNICOS.md`: padroes tecnicos observaveis em arquivos de projeto, scripts e estrutura.
- `docs/RegrasNegocio/README.md`: somente regras confirmadas; suspeitas devem ficar como pendencias.

Em todos os documentos gerados, inclua uma secao curta chamada `Classificacao das informacoes` com:

```markdown
## Classificacao das informacoes

- **Informado pelo usuario:** <itens ou Nao informado>
- **Inferido da estrutura do projeto:** <itens ou Nao identificado>
- **Pendente de confirmacao humana:** <itens ou Nenhuma pendencia inicial registrada>
```

Nao sobrescreva documentos existentes. Quando autorizado, acrescente uma secao chamada:

```markdown
## Documentacao inicial gerada pelo ADF em DATA_ATUAL
```

e mantenha o conteudo anterior intacto.

## Confirmacao antes de editar arquivos

Antes de alterar `CONFIGURACAO_IAS.md` e `ADF_ADOCAO.md`, mostre um resumo:

```text
Resumo da instalacao:
- Projeto: PROJECT_ROOT
- ADF origem: ADF_SOURCE_DIR
- Proprietario: ADF_OWNER
- Revisores: ADF_REVIEWERS
- IA Pensante: THINKING_AI
- IA Dev Principal: DEV_AI
- Rota alternativa: DEV_AI_FALLBACK
- Modelos OpenCode: OPENCODE_MODELS
- Estados de feature: FEATURE_STATES
- Padrao de features: FEATURE_ID_PATTERN
- Mapeamento de diretorios: PROJECT_DIR_MAP
- Limitacoes de execucao: registradas ou nao registradas
- Documentacao inicial do projeto: solicitada ou nao solicitada

Posso aplicar essas informacoes nos arquivos do ADF? Responda sim ou nao.
```

Se o usuario responder `nao`, pergunte qual campo deve corrigir. Nao edite os arquivos ate receber `sim`.

## Validacao final

Depois de copiar e preencher os arquivos, verifique:

```powershell
Test-Path "PROJECT_ROOT\ADF_VERSION.md"
Test-Path "PROJECT_ROOT\docs\INDICE_DOCUMENTACAO.md"
Test-Path "PROJECT_ROOT\docs\AI\Core\ADF_FRAMEWORK.md"
Test-Path "PROJECT_ROOT\docs\Projeto\CONFIGURACAO_IAS.md"
Test-Path "PROJECT_ROOT\docs\Projeto\ADF_ADOCAO.md"
```

Se o usuario respondeu `sim` para limitacoes, verifique tambem:

```powershell
Test-Path "PROJECT_ROOT\docs\Projeto\LIMITACOES_EXECUCAO_FEATURES.md"
```

Se o usuario respondeu `sim` para documentacao inicial, verifique os documentos criados ou atualizados e confirme que todos diferenciam informacao informada, inferida e pendente.

Leia os dois arquivos preenchidos e confirme que nao sobrou `A definir` em campos obrigatorios, exceto quando o usuario autorizou registrar pendencia.

Campos que nao podem ficar `A definir` sem pendencia registrada:

- proprietario do ADF;
- revisores;
- cadencia de revisao;
- IA Pensante;
- IA Dev Principal;
- rota alternativa;
- modelos OpenCode;
- estados de feature;
- padrao de identificacao de features;
- diretorios mapeados.

## Mensagem final ao usuario

Ao concluir, responda:

```text
Instalacao do ADF concluida.

Modo da instalacao:
- MODO_INSTALACAO
- Limitacoes de execucao: STATUS_LIMITACOES
- Documentacao inicial do projeto: STATUS_DOCUMENTACAO_INICIAL

Arquivos principais criados ou atualizados:
- ADF_VERSION.md
- docs/INDICE_DOCUMENTACAO.md
- docs/Projeto/CONFIGURACAO_IAS.md
- docs/Projeto/ADF_ADOCAO.md
- DOCUMENTOS_OPCIONAIS_QUANDO_EXISTIREM

Configuracao aplicada:
- IA Pensante: THINKING_AI
- IA Dev Principal: DEV_AI
- OpenCode: OPENCODE_MODELS

Proximo passo recomendado:
Abra docs/INDICE_DOCUMENTACAO.md e peca para a IA iniciar qualquer feature a partir desse indice.
```

Se algo falhar, responda com:

```text
A instalacao do ADF nao foi concluida.

Ponto de parada:
DESCREVA_O_PROBLEMA

O que preciso do usuario:
RESPOSTA_OU_AUTORIZACAO_NECESSARIA
```

## Checklist da IA instaladora

- [ ] Li este instalador ate o fim.
- [ ] Expliquei o processo ao usuario.
- [ ] Coletei e validei `ADF_SOURCE_DIR`.
- [ ] Coletei e validei `PROJECT_ROOT`.
- [ ] Verifiquei risco de sobrescrita.
- [ ] Copiei o esqueleto do ADF.
- [ ] Coletei responsaveis.
- [ ] Coletei configuracao de IAs.
- [ ] Coletei convencoes locais.
- [ ] Perguntei sobre limitacoes de execucao de features.
- [ ] Criei ou preservei `LIMITACOES_EXECUCAO_FEATURES.md` conforme resposta do usuario.
- [ ] Perguntei sobre documentacao inicial do projeto.
- [ ] Analisei a estrutura real do projeto somente se autorizado.
- [ ] Criei ou atualizei documentacao inicial somente se autorizado.
- [ ] Diferenciei informacoes informadas, inferidas e pendentes.
- [ ] Mostrei resumo antes de editar arquivos.
- [ ] Preenchi `docs/Projeto/CONFIGURACAO_IAS.md`.
- [ ] Preenchi `docs/Projeto/ADF_ADOCAO.md`.
- [ ] Validei os arquivos finais.
- [ ] Informei a conclusao ou o ponto de parada.
