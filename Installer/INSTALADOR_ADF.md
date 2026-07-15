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

## Como conduzir a conversa

Faca uma pergunta por vez.

Para cada resposta:

1. Verifique se a resposta e curta, objetiva e utilizavel.
2. Se estiver clara, registre internamente o valor e diga que vai continuar.
3. Se estiver vaga, pare e peca uma resposta melhor.
4. Se o usuario pedir exemplo ou sugestao, mostre exemplos e repita a mesma pergunta.
5. Se precisar executar comando, explique o comando antes, execute, leia o resultado e continue.

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

Arquivos principais criados ou atualizados:
- ADF_VERSION.md
- docs/INDICE_DOCUMENTACAO.md
- docs/Projeto/CONFIGURACAO_IAS.md
- docs/Projeto/ADF_ADOCAO.md

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
- [ ] Mostrei resumo antes de editar arquivos.
- [ ] Preenchi `docs/Projeto/CONFIGURACAO_IAS.md`.
- [ ] Preenchi `docs/Projeto/ADF_ADOCAO.md`.
- [ ] Validei os arquivos finais.
- [ ] Informei a conclusao ou o ponto de parada.
