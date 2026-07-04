# Changelog do ADF

## 1.1.0 — 2026-07-04

### Criados

- `docs/INDICE_DOCUMENTACAO.md`: ponto único de entrada, com leituras mínimas por papel e roteamento por tarefa.
- `docs/AI/Core/GUIA_ORGANIZACAO_DOCUMENTACAO.md`: responsabilidades, fonte canônica e critérios para criar ou atualizar arquivos.
- `docs/AI/Core/CHECKLIST_USO_ADF.md`: gate compacto para uso e conclusão.
- Skills para correção de bug, CRUD, integração externa, layout, refatoração e revisão arquitetural: procedimentos recorrentes que antes dependiam da skill genérica.
- Templates de checklist, revisão e prompts de execução/revisão: padronização da passagem entre execução e revisão.
- `docs/Revisoes/README.md`: local opcional para pareceres com valor histórico.

### Alterados

- README e versão: adoção do índice único e documentação da compatibilidade.
- Índice legado: mantido como redirecionamento para evitar quebra de consumidores.
- Fluxo, papéis e mapas: separação entre roteiro e catálogo, responsabilidades mais explícitas e conclusão condicionada a revisão, validação e avaliação documental.
- Skills existentes: execução de feature por caminho, relato documental e revisão do gate final.
- Templates de feature e ADR: contexto mínimo, papel/skill, rastreabilidade e checklist de conclusão.

### Removidos

- Nenhum arquivo. A manutenção dos caminhos existentes evita migração incompatível.

### Benefícios

- Menos contexto carregado por tarefa e menos duplicação entre índice e mapas.
- Entregas rastreáveis entre feature, skill, validações e documentação.
- Procedimentos reutilizáveis para classes frequentes de mudança.
- Compatibilidade com instalações existentes e independência de domínio, tecnologia e fornecedor.
