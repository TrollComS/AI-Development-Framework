# Feature: Evoluir instalador para adaptadores de agentes

**Estado:** Rascunho

**Responsável:** A definir

**Papel recomendado:** IA Dev Principal

**Skill recomendada:** `docs/AI/Skills/SKILL_IMPLEMENTAR_MUDANCA.md`

## Contexto obrigatório

- `ADF/Features/FEATURE_DEFINIR_CONTRATO_INSTRUCOES_AGENTES.md`
- `ADF/Features/FEATURE_CRIAR_TEMPLATES_ADAPTADORES_AGENTES.md`
- `Installer/INSTALADOR_ADF.md`
- `Installer/FEATURE_INSTALAR_ADF.md`
- `docs/Projeto/CONFIGURACAO_IAS.md`
- `docs/Projeto/ADF_ADOCAO.md`

## Problema

O instalador atual coleta IAs e modelos, mas não pergunta quais agentes efetivamente serão usados nem cria seus arquivos de entrada. Além disso, parte da configuração ainda pressupõe OpenCode como obrigatório, algo que pertence à decisão do projeto consumidor.

## Resultado esperado

Durante a instalação, o usuário escolhe os agentes e adaptadores que deseja habilitar. O instalador coleta somente os dados necessários, cria os arquivos selecionados sem sobrescrita silenciosa e registra as escolhas no ADF do projeto consumidor.

## Escopo

### Incluído

- Adicionar perguntas sobre agentes e adaptadores habilitados.
- Perguntar por informações de projeto necessárias ao preflight: build, testes, diretórios relevantes, arquivos gerados e áreas sensíveis.
- Gerar apenas os adaptadores selecionados a partir dos templates aprovados.
- Atualizar `CONFIGURACAO_IAS.md` para representar ferramentas opcionais, incluindo OpenCode quando escolhido.
- Registrar a adoção e os adaptadores gerados em `ADF_ADOCAO.md`.
- Proteger arquivos existentes e conteúdo local conforme a estratégia de blocos gerenciados.
- Atualizar roteiros e validação final do instalador.

### Fora do escopo

- Atualizar instalações existentes; isso cabe ao atualizador.
- Detectar automaticamente contas, modelos pagos ou configurações pessoais de agentes.
- Instalar programas, extensões, CLIs ou modelos no computador do usuário.

## Requisitos

1. O instalador deve perguntar quais adaptadores o usuário deseja gerar, apresentando apenas formatos suportados pelos templates.
2. A escolha de OpenCode deve ser opcional; se selecionada, o instalador deve coletar seus modelos e rota alternativa.
3. O instalador deve perguntar pelos comandos oficiais de build e testes ou permitir registrá-los como pendência humana.
4. O instalador deve coletar diretórios de código, testes, scripts e áreas que não podem ser alteradas sem autorização, quando aplicável.
5. Antes de criar ou atualizar cada adaptador, o instalador deve verificar a existência do arquivo e pedir autorização para qualquer alteração.
6. Ao atualizar um arquivo existente, o instalador deve preservar conteúdo local fora do bloco gerenciado; se isso não for possível, deve parar e registrar uma pendência.
7. O instalador deve gerar `AGENTS.md` com essa capitalização exata quando esse adaptador for escolhido.
8. A mensagem final deve listar adaptadores criados, preservados, não selecionados e pendências.

## Critérios de aceite

- [ ] Dado um projeto novo, quando o usuário selecionar Codex e Copilot, então o instalador cria `AGENTS.md` e `.github/copilot-instructions.md` a partir dos templates.
- [ ] Dado um projeto que não usa OpenCode, quando a instalação terminar, então `CONFIGURACAO_IAS.md` não o declara obrigatório.
- [ ] Dado um arquivo de instrução existente, quando o instalador for executado, então não há sobrescrita sem autorização explícita.
- [ ] Dado uma configuração local de build pendente, quando a instalação terminar, então a pendência fica registrada de forma objetiva.
- [ ] Dado um adaptador não selecionado, quando a instalação terminar, então nenhum arquivo correspondente é criado.
- [ ] Dado o resumo final, quando o usuário o receber, então consegue identificar os documentos e adaptadores efetivamente criados ou alterados.

## Riscos, dependências e reversão

**Riscos:** mais perguntas podem tornar a instalação longa; a atualização de arquivos existentes pode falhar em preservar blocos locais.

**Mitigações:** agrupar perguntas por decisão, tornar adaptadores opcionais e interromper a alteração diante de marcadores ambíguos.

**Dependências:** as features de contrato e templates devem estar concluídas.

**Reversão:** restaurar o instalador e remover apenas arquivos de adaptador criados durante uma instalação de teste, preservando documentos do projeto consumidor conforme autorização humana.

## Evidências

- Simular instalação sem adaptadores.
- Simular instalação com `AGENTS.md` e Copilot.
- Simular instalação com arquivo preexistente e conteúdo local.
- Validar fluxo com e sem OpenCode e com comandos de build pendentes.

## Checklist de conclusão

- [ ] Perguntas, validações e registros de instalação atualizados.
- [ ] Adaptadores selecionados gerados com segurança.
- [ ] OpenCode tornado decisão de projeto consumidor.
- [ ] Casos de arquivos existentes validados.
- [ ] Resumo final e pendências verificáveis implementados.
