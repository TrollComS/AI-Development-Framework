# Feature: Criar templates de adaptadores para agentes

**Estado:** Rascunho

**Responsável:** A definir

**Papel recomendado:** IA Arquiteta + IA Executora

**Skill recomendada:** `docs/AI/Skills/SKILL_ATUALIZAR_DOCUMENTACAO.md`

## Contexto obrigatório

- `ADF/Features/FEATURE_DEFINIR_CONTRATO_INSTRUCOES_AGENTES.md`
- `docs/INDICE_DOCUMENTACAO.md`
- `docs/AI/Core/ROTEAMENTO_IAS.md`
- `docs/AI/Templates/`
- `Installer/INSTALADOR_ADF.md`

## Problema

Projetos consumidores precisam criar manualmente arquivos como `AGENTS.md` e `.github/copilot-instructions.md`. Sem modelos oficiais, cada projeto decide sozinho o que duplicar, quais links usar e como tratar particularidades de cada agente.

## Resultado esperado

O ADF deve oferecer modelos opt-in para os formatos de instrução mais comuns. Cada modelo deve conter um bloco gerenciado pelo ADF, referências ao contexto canônico e espaço claramente separado para instruções locais da ferramenta.

## Escopo

### Incluído

- Criar templates para `AGENTS.md` e `.github/copilot-instructions.md`.
- Avaliar e, se houver suporte definido, criar templates opcionais para `CLAUDE.md`, `GEMINI.md` e `.cursor/rules/*.mdc`.
- Definir metadados de origem, versão do ADF e marcadores de bloco gerenciado.
- Definir um bloco preservável para regras locais específicas de cada ferramenta.
- Documentar capacidades, limitações e precedência de cada adaptador.
- Atualizar mapas e documentação de instalação afetados.

### Fora do escopo

- Gerar os arquivos em projetos consumidores; isso cabe à feature do instalador.
- Manter cópias automáticas de regras locais fora dos marcadores definidos.
- Criar adaptadores para ferramentas sem formato de instrução versionável confirmado.

## Requisitos

1. Todo adaptador deve declarar que `docs/INDICE_DOCUMENTACAO.md` é o ponto documental de entrada.
2. O template de `AGENTS.md` deve orientar o preflight definido na feature de contrato.
3. O template de Copilot deve conter apenas orientações relevantes ao Copilot e links canônicos, respeitando seu local oficial `.github/copilot-instructions.md`.
4. Cada template deve separar visualmente conteúdo gerenciado pelo ADF de conteúdo local preservável.
5. O conteúdo gerenciado deve identificar a versão do ADF e o template de origem.
6. Templates opcionais só devem ser incluídos se o instalador puder detectar ou perguntar pela ferramenta correspondente.
7. Nenhum template pode impor uma IA, modelo, plano pago ou ferramenta operacional.
8. Regras por caminho devem ser tratadas como extensão opcional para módulos com convenções realmente diferentes, não como substituição do `AGENTS.md`.

## Critérios de aceite

- [ ] Dado um projeto que habilita Codex, quando o template universal for aplicado, então existe `AGENTS.md` com links válidos ao ADF.
- [ ] Dado um projeto que habilita Copilot, quando o template correspondente for aplicado, então existe `.github/copilot-instructions.md` sem duplicação integral de `AGENTS.md`.
- [ ] Dado conteúdo local fora do bloco gerenciado, quando um template for atualizado futuramente, então a estratégia documental prevê sua preservação.
- [ ] Dado um projeto que não usa Cursor, Claude ou Gemini, quando os templates forem disponibilizados, então nenhum desses arquivos é exigido.
- [ ] Dado um monorepo com convenções distintas, quando regras por caminho forem necessárias, então o template explica quando adotá-las.
- [ ] Dado cada template criado, quando seus links forem verificados, então todos apontam para caminhos existentes no esqueleto instalado.

## Riscos, dependências e reversão

**Riscos:** excesso de formatos amplia manutenção; blocos gerenciados mal definidos podem sobrescrever decisões locais.

**Mitigações:** começar por `AGENTS.md` e Copilot, tornar formatos adicionais opt-in e padronizar marcadores explícitos de conteúdo gerenciado.

**Dependências:** `FEATURE_DEFINIR_CONTRATO_INSTRUCOES_AGENTES.md` deve estar concluída.

**Reversão:** remover os templates e referências de mapa sem afetar a documentação canônica já instalada.

## Evidências

- Verificar os templates contra a documentação oficial das ferramentas habilitadas.
- Validar links com uma cópia limpa do esqueleto ADF.
- Simular uma atualização com conteúdo local antes e depois dos marcadores gerenciados.

## Checklist de conclusão

- [ ] Templates essenciais criados.
- [ ] Estratégia de bloco gerenciado e conteúdo local documentada.
- [ ] Formatos opcionais avaliados e justificados.
- [ ] Links e referências validados.
- [ ] Mapas e documentação afetados atualizados.
