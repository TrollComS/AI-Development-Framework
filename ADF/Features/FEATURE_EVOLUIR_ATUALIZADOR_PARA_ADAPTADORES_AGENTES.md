# Feature: Evoluir atualizador para adaptadores de agentes

**Estado:** Concluída

**Responsável:** A definir

**Papel recomendado:** IA Dev Principal + IA Revisora

**Skill recomendada:** `docs/AI/Skills/SKILL_ATUALIZAR_DOCUMENTACAO.md`

## Contexto obrigatório

- `ADF/Features/FEATURE_DEFINIR_CONTRATO_INSTRUCOES_AGENTES.md`
- `ADF/Features/FEATURE_CRIAR_TEMPLATES_ADAPTADORES_AGENTES.md`
- `ADF/Features/FEATURE_EVOLUIR_INSTALADOR_PARA_ADAPTADORES_AGENTES.md`
- `Installer/UPDATE.md`
- `Installer/MIGRACOES_ADF.md`
- `Installer/FEATURE_ADAPTAR_ADF_AO_PROJETO.md`
- `ADF_VERSION.md`

## Problema

Projetos que já usam o ADF não devem executar a instalação inicial novamente. Sem uma migração específica, eles não recebem o contrato de instruções nem os novos adaptadores de forma segura, ou acabam recriando arquivos manualmente e perdendo contexto local.

## Resultado esperado

O atualizador deve identificar a nova capacidade, explicar as escolhas disponíveis, comparar arquivos existentes e conduzir uma migração assistida dos adaptadores, sem sobrescrever conteúdo local ou presumir quais agentes o projeto utiliza.

## Escopo

### Incluído

- Registrar a migração em `Installer/MIGRACOES_ADF.md`.
- Atualizar `Installer/UPDATE.md` com a descoberta e execução opcional da nova etapa.
- Comparar versão instalada, templates disponíveis e arquivos de adaptador presentes.
- Perguntar quais adaptadores devem ser criados, mantidos, convertidos ou adiados.
- Inserir ou atualizar apenas blocos gerenciados quando os marcadores forem reconhecidos.
- Registrar pendências quando não for seguro atualizar um arquivo existente.
- Atualizar versão, changelog e mapas exigidos pela mudança de contrato público.

### Fora do escopo

- Alterar automaticamente instruções locais fora dos blocos gerenciados.
- Remover adaptadores que o usuário não selecionou sem autorização explícita.
- Forçar todos os projetos existentes a adotar novos arquivos de agente.

## Requisitos

1. O atualizador deve detectar que o contrato de instruções e os adaptadores são uma novidade da versão do ADF.
2. Antes de editar, deve exibir os arquivos encontrados e classificar cada um como ausente, compatível, gerenciado, local ou ambíguo.
3. Arquivos ausentes podem ser criados somente após escolha explícita do usuário.
4. Arquivos com blocos gerenciados reconhecidos podem receber atualização limitada a esses blocos, após confirmação.
5. Arquivos locais ou ambíguos não podem ser sobrescritos; o atualizador deve oferecer preservar, criar proposta manual ou registrar pendência.
6. A migração deve atualizar `CONFIGURACAO_IAS.md` e `ADF_ADOCAO.md` somente com autorização e preservando decisões existentes.
7. O relatório final deve identificar versão anterior, versão final, arquivos alterados, arquivos preservados e pendências.
8. A documentação de migração deve indicar como reverter as alterações geradas.

## Critérios de aceite

- [x] Dado um projeto com versão anterior, quando o atualizador identificar a migração, então explica os adaptadores disponíveis antes de alterar arquivos.
- [x] Dado um `AGENTS.md` com bloco gerenciado reconhecido, quando o usuário aprovar a atualização, então apenas o bloco gerenciado é alterado.
- [x] Dado um arquivo de instrução local sem marcadores, quando o atualizador for executado, então ele não é sobrescrito automaticamente.
- [x] Dado que o usuário adia a criação de adaptadores, quando a atualização terminar, então a pendência fica registrada de forma rastreável.
- [x] Dado uma atualização concluída, quando o relatório final for entregue, então ele discrimina alterações, preservações, versão e reversão.
- [x] Dado que a versão pública do ADF foi alterada, quando a feature terminar, então versão, changelog e migrações estão coerentes.

## Riscos, dependências e reversão

**Riscos:** projetos antigos podem conter instruções parecidas, mas sem marcadores; uma classificação incorreta pode destruir conteúdo local.

**Mitigações:** tratar ausência de marcadores como ambiguidade, exigir confirmação e preferir proposta ou pendência a alteração automática.

**Dependências:** as três features anteriores devem estar concluídas e versionadas.

**Reversão:** restaurar o bloco gerenciado anterior ou remover somente arquivos criados pela migração, conforme o registro produzido e autorização humana.

## Evidências

- Simular atualização de projeto sem adaptadores.
- Simular atualização de projeto com adaptador gerenciado.
- Simular atualização de projeto com arquivo local sem marcadores.
- Verificar versão, changelog, migrações, links e relatório final.

## Checklist de conclusão

- [x] Migração registrada e atualizador atualizado.
- [x] Estratégia segura para arquivos gerenciados, locais e ambíguos validada.
- [x] Registros de adoção e configuração preservados.
- [x] Versão, changelog e mapas atualizados.
- [x] Cenários de reversão e pendências documentados.
