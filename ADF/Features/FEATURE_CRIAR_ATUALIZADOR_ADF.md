# Feature: Criar atualizador assistido do ADF

**Estado:** Concluida

**Responsavel:** IA Dev Principal

**Papel recomendado:** IA Arquiteta + IA Dev Principal

**Skill recomendada:** docs/AI/Skills/SKILL_ATUALIZAR_DOCUMENTACAO.md

## Problema

Projetos consumidores que ja instalaram o ADF precisam receber evolucoes do framework sem perder documentacao local, adaptacoes, features e regras preenchidas pelo usuario.

O instalador inicial nao e suficiente para esse caso, porque copiar o esqueleto do ADF por cima de um projeto existente pode sobrescrever contexto do cliente.

## Resultado esperado

O ADF deve oferecer um roteiro de atualizacao assistida que:

- identifique versao instalada e versao alvo;
- consulte um mapa de migracoes por versao;
- copie apenas arquivos novos ausentes;
- faca merge assistido em arquivos existentes;
- preserve documentos do projeto consumidor;
- registre pendencias e versao atualizada.

## Escopo

### Incluido

- Criar `Installer/UPDATE.md`.
- Criar `Installer/MIGRACOES_ADF.md`.
- Atualizar README, versao e changelog.
- Explicitar categorias de arquivos para atualizacao segura.

### Fora do escopo

- Criar script automatico de migracao.
- Fazer downgrade de versoes.
- Sobrescrever documentos do projeto consumidor.
- Copiar `ADF/**` para o projeto consumidor.

## Criterios de aceite

- [x] Existe roteiro de atualizacao separado do instalador inicial.
- [x] Existe mapa de migracoes por versao.
- [x] O fluxo preserva conteudo local do projeto consumidor.
- [x] O fluxo diferencia Core do ADF, documentos locais, versao e arquivos internos.
- [x] A versao e o changelog do ADF foram atualizados.

## Evidencias

- `Installer/UPDATE.md` criado.
- `Installer/MIGRACOES_ADF.md` criado.
- `ADF_VERSION.md` atualizado para `1.4.0`.
- `CHANGELOG_ADF.md` atualizado.
- README atualizado com instalacao inicial versus atualizacao.
