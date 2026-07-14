# Índice da documentação

Este é o ponto único de entrada do ADF. Comece aqui e carregue somente os documentos necessários à tarefa. Os mapas são catálogos, não roteiros de leitura.

Antes de planejar ou executar uma mudança, consulte `docs/Projeto/CONFIGURACAO_IAS.md` e aplique o [Roteamento de IAs](AI/Core/ROTEAMENTO_IAS.md).

## Leitura mínima por papel

### IA Arquiteta

1. Visão do projeto em `Projeto`.
2. Arquitetura e decisões relacionadas.
3. Regras e padrões da área afetada.
4. Skill e template aplicáveis.

### IA Executora

1. Feature ou descrição objetiva da tarefa.
2. Skill indicada para o tipo de mudança.
3. Arquitetura, regras e padrões diretamente afetados.
4. Testes semelhantes existentes.

### IA Revisora

1. Feature e critérios de aceite.
2. Skill usada na execução.
3. Diff e evidências de validação.
4. Regras, decisões e padrões afetados.

## Mapa por tipo de tarefa

| Tarefa | Skill principal | Contexto mínimo |
|---|---|---|
| Especificar ou executar feature | `AI/Skills/SKILL_ESPECIFICAR_FEATURE.md` | visão, feature, área afetada |
| Planejar implementação | `AI/Skills/SKILL_PLANEJAR_IMPLEMENTACAO.md` | feature, arquitetura, testes |
| Implementar mudança geral | `AI/Skills/SKILL_IMPLEMENTAR_MUDANCA.md` | plano, padrões e regras afetados |
| Corrigir bug | `AI/Skills/SKILL_CORRIGIR_BUG.md` | reprodução, comportamento esperado, testes |
| Implementar CRUD | `AI/Skills/SKILL_IMPLEMENTAR_CRUD.md` | entidade, arquitetura, validações |
| Criar integração externa | `AI/Skills/SKILL_CRIAR_INTEGRACAO_EXTERNA.md` | contrato, segurança, erros e testes |
| Ajustar layout | `AI/Skills/SKILL_AJUSTAR_LAYOUT.md` | interface atual e padrões visuais |
| Refatorar | `AI/Skills/SKILL_REFATORAR_CODIGO.md` | comportamento preservado e testes |
| Revisar arquitetura | `AI/Skills/SKILL_REVISAR_ARQUITETURA.md` | proposta, arquitetura e ADRs |
| Revisar entrega | `AI/Skills/SKILL_REVISAR_ENTREGA.md` | feature, diff e validações |
| Atualizar documentação | `AI/Skills/SKILL_ATUALIZAR_DOCUMENTACAO.md` | mudança validada e fontes canônicas |

## Catálogos e processo

- [Contrato do ADF](AI/Core/ADF_FRAMEWORK.md)
- [Fluxo de desenvolvimento](AI/Core/FLUXO_DESENVOLVIMENTO.md)
- [Papéis das IAs](AI/Core/PAPEIS_DAS_IAS.md)
- [Roteamento de IAs](AI/Core/ROTEAMENTO_IAS.md)
- [Guia de organização](AI/Core/GUIA_ORGANIZACAO_DOCUMENTACAO.md)
- [Checklist de uso](AI/Core/CHECKLIST_USO_ADF.md)
- [Catálogo documental](AI/Core/MAPA_DOCUMENTACAO.md)
- [Catálogo de skills](AI/Core/MAPA_SKILLS.md)

## Documentação do projeto consumidor

- `Projeto`: visão, glossário, status, roadmap, configuração de IAs e histórico.
- `Projeto/ADF_ADOCAO.md`: responsáveis, cadência, convenções locais, adaptações aceitas e pendências de implantação.
- `Projeto/CONFIGURACAO_IAS.md`: IA Pensante, IA Dev Principal, OpenCode, modelos gratuitos e matriz de roteamento.
- `Arquitetura`: contexto, componentes, integrações e ADRs.
- `Padroes`: convenções técnicas e de processo.
- `RegrasNegocio`: invariantes do domínio.
- `Features`: especificações e evidências das entregas.
- `Revisoes`: pareceres que precisem ser preservados.

Templates, prompts e exemplos ficam em `AI/Templates`, `AI/Prompts` e `Samples`.
