# Migracoes do ADF

Este arquivo lista mudancas entre versoes do ADF para orientar atualizacoes em projetos consumidores.

Use junto com `Installer/UPDATE.md`.

## Regras gerais

- Copie arquivos novos somente quando ausentes.
- Nunca sobrescreva documentos preenchidos pelo projeto consumidor.
- Em arquivos existentes, faca merge assistido e peca autorizacao antes de editar.
- Nao copie o diretorio `ADF/**` para projetos consumidores.
- Registre pendencias em `docs/Projeto/ADF_ADOCAO.md` quando uma atualizacao nao puder ser aplicada com seguranca.
- Quando `Installer/INSTALADOR_ADF.md` mudar, verifique se surgiram novas perguntas, etapas, validacoes ou documentos e execute apenas as etapas novas autorizadas pelo usuario.

## Sem versao identificada -> versao atual

Use quando o projeto consumidor tem sinais de ADF instalado, mas nao possui `ADF_VERSION.md` confiavel.

### Estrategia

- Tratar todo arquivo existente como customizacao local.
- Copiar apenas arquivos obrigatorios ausentes.
- Para arquivos existentes do Core, Skills, Templates, Prompts e Installer, propor merge assistido.
- Para documentos do projeto consumidor, apenas acrescentar secoes novas quando autorizado.

### Arquivos minimos a verificar

- `ADF_VERSION.md`
- `docs/INDICE_DOCUMENTACAO.md`
- `docs/AI/Core/ADF_FRAMEWORK.md`
- `docs/AI/Core/MAPA_DOCUMENTACAO.md`
- `docs/AI/Core/ROTEAMENTO_IAS.md`
- `docs/Projeto/CONFIGURACAO_IAS.md`
- `docs/Projeto/ADF_ADOCAO.md`
- `Installer/INSTALADOR_ADF.md`
- `Installer/UPDATE.md`
- `Installer/MIGRACOES_ADF.md`

## 1.0.0 -> 1.1.0

### Novos arquivos principais

- `docs/INDICE_DOCUMENTACAO.md`
- `docs/AI/Core/GUIA_ORGANIZACAO_DOCUMENTACAO.md`
- `docs/AI/Core/CHECKLIST_USO_ADF.md`
- `docs/Revisoes/README.md`
- skills adicionais em `docs/AI/Skills`
- templates adicionais em `docs/AI/Templates`

### Arquivos a revisar por merge assistido

- `README.md`
- `ADF_VERSION.md`
- `CHANGELOG_ADF.md`
- `docs/AI/Core/INDICE_DOCUMENTACAO.md`
- `docs/AI/Core/MAPA_DOCUMENTACAO.md`
- `docs/AI/Core/FLUXO_DESENVOLVIMENTO.md`
- `docs/AI/Core/PAPEIS_DAS_IAS.md`

### Regra de migracao

- Criar o indice canonico em `docs/INDICE_DOCUMENTACAO.md` quando ausente.
- Manter `docs/AI/Core/INDICE_DOCUMENTACAO.md` como compatibilidade, sem duplicar o indice completo.
- Acrescentar referencias aos novos mapas, skills e templates sem remover orientacoes locais.

## 1.1.0 -> 1.2.0

### Novos arquivos principais

- `docs/AI/Core/ROTEAMENTO_IAS.md`
- `docs/Projeto/CONFIGURACAO_IAS.md`
- `docs/Projeto/ADF_ADOCAO.md`

### Arquivos a revisar por merge assistido

- `README.md`
- `ADF_VERSION.md`
- `CHANGELOG_ADF.md`
- `docs/INDICE_DOCUMENTACAO.md`
- `docs/AI/Core/MAPA_DOCUMENTACAO.md`
- `docs/AI/Core/PAPEIS_DAS_IAS.md`
- `docs/AI/Core/FLUXO_DESENVOLVIMENTO.md`
- `docs/AI/Core/CHECKLIST_USO_ADF.md`
- `docs/AI/Prompts/PROMPT_INICIAR_FEATURE.md`
- `docs/AI/Templates/TEMPLATE_PROMPT_EXECUCAO.md`
- `Installer/FEATURE_ADAPTAR_ADF_AO_PROJETO.md`

### Regra de migracao

- Copiar `ROTEAMENTO_IAS.md` quando ausente.
- Criar `CONFIGURACAO_IAS.md` e `ADF_ADOCAO.md` quando ausentes.
- Se os arquivos de `docs/Projeto` ja existirem, preservar conteudo local e acrescentar apenas campos faltantes mediante autorizacao.
- Registrar pendencia se o usuario ainda nao souber quais IAs, modelos ou revisores usar.

## 1.2.0 -> 1.3.0

### Novos arquivos principais

- `docs/AI/Templates/TEMPLATE_LIMITACOES_EXECUCAO_FEATURES.md`
- `docs/AI/Templates/TEMPLATE_DOCUMENTACAO_INICIAL_PROJETO.md`

### Arquivos internos do repositorio ADF

- `ADF/README.md`
- `ADF/Features/README.md`
- `ADF/Features/FEATURE_ATUALIZACAO_ADF_BASEADO_INFOGESTOR.md`
- `ADF/Features/FEATURE_MELHORAR_INSTALADOR_ADF_LIMITACOES_E_DOCUMENTACAO_PROJETO.md`

Esses arquivos nao devem ser copiados para projetos consumidores.

### Arquivos a revisar por merge assistido

- `README.md`
- `ADF_VERSION.md`
- `CHANGELOG_ADF.md`
- `Installer/INSTALADOR_ADF.md`
- `Installer/FEATURE_INSTALAR_ADF.md`
- `Installer/FEATURE_ADAPTAR_ADF_AO_PROJETO.md`
- `docs/INDICE_DOCUMENTACAO.md`
- `docs/AI/Core/ADF_FRAMEWORK.md`
- `docs/AI/Core/CHECKLIST_USO_ADF.md`
- `docs/AI/Core/FLUXO_DESENVOLVIMENTO.md`
- `docs/AI/Core/GUIA_ORGANIZACAO_DOCUMENTACAO.md`
- `docs/AI/Core/MAPA_DOCUMENTACAO.md`
- `docs/Arquitetura/README.md`
- `docs/Features/README.md`
- `docs/Projeto/README.md`

### Regra de migracao

- Copiar os novos templates quando ausentes.
- Acrescentar ao instalador as perguntas opcionais sobre limitacoes de execucao e documentacao inicial.
- Depois de atualizar o instalador, oferecer ao usuario a execucao dessas novas etapas opcionais.
- Remover de `docs/Features/README.md` qualquer referencia a features internas do ADF.
- Garantir que `docs/Features` seja descrito como area do projeto consumidor.
- Registrar `docs/Projeto/LIMITACOES_EXECUCAO_FEATURES.md` apenas quando o usuario autorizar.

## 1.3.0 -> 1.4.0

### Novos arquivos principais

- `Installer/UPDATE.md`
- `Installer/MIGRACOES_ADF.md`

### Arquivos a revisar por merge assistido

- `README.md`
- `ADF_VERSION.md`
- `CHANGELOG_ADF.md`

### Regra de migracao

- Copiar `UPDATE.md` e `MIGRACOES_ADF.md` quando ausentes.
- Acrescentar ao README a diferenca entre instalacao inicial e atualizacao de projeto consumidor ja adotado.
- Acrescentar ao atualizador a regra para detectar e executar etapas novas introduzidas pelo instalador.
- Atualizar `ADF_VERSION.md` para `1.4.0`.
- Registrar no `CHANGELOG_ADF.md` a criacao do fluxo de atualizacao assistida.
