# Changelog do ADF

## 1.4.0 — 2026-08-04

### Criados

- `Installer/UPDATE.md`: roteiro operacional para atualizar o ADF em projetos consumidores que ja possuem uma versao instalada.
- `Installer/MIGRACOES_ADF.md`: mapa de migracoes por versao, com arquivos novos, arquivos a revisar e regras de preservacao.
- `ADF/Features/FEATURE_CRIAR_ATUALIZADOR_ADF.md`: registro interno da feature de atualizacao assistida.

### Alterados

- README: adicionada diferenca entre instalacao inicial e atualizacao de projetos consumidores ja adotados.
- Versao do ADF: atualizada para `1.4.0` como capacidade compativel nova.

### Beneficios

- Projetos consumidores antigos podem receber evolucoes do ADF sem sobrescrever documentacao local.
- A IA atualizadora passa a ter um processo explicito para copiar arquivos ausentes, fazer merge assistido e registrar pendencias.
- O historico de migracoes reduz inferencias e torna atualizacoes futuras mais previsiveis.

## 1.3.0 — 2026-08-04

### Criados

- `ADF/Features`: área interna para features do próprio framework, separada do esqueleto documental do projeto consumidor.
- `docs/AI/Templates/TEMPLATE_LIMITACOES_EXECUCAO_FEATURES.md`: template para registrar limitações locais informadas pelo usuário.
- `docs/AI/Templates/TEMPLATE_DOCUMENTACAO_INICIAL_PROJETO.md`: contrato para documentação inicial curta, com informações informadas, inferidas e pendentes.

### Alterados

- Features internas do ADF movidas de `docs/Features` para `ADF/Features`.
- Instalador guiado: adicionadas perguntas opcionais para limitações de execução de features e documentação inicial do projeto consumidor.
- Índice, mapa documental, checklist, fluxo e guias: agora apontam para limitações locais quando existirem e para os documentos iniciais opcionais.
- Versão do ADF: atualizada para `1.3.0` como capacidade compatível nova.

### Benefícios

- A instalação básica continua funcionando com respostas `nao`.
- Projetos consumidores podem registrar áreas sensíveis e validações obrigatórias antes de executar features.
- A documentação inicial passa a diferenciar informação fornecida pelo usuário, inferida pela IA e pendente de confirmação humana.

## 1.2.0 — 2026-07-14

### Criados

- `docs/AI/Core/ROTEAMENTO_IAS.md`: contrato para decidir entre IA Pensante, IA Dev Principal e OpenCode.
- `docs/Projeto/CONFIGURACAO_IAS.md`: configuração local para definir ferramentas, modelos gratuitos do OpenCode, rotas alternativas e matriz de roteamento.
- `docs/Projeto/ADF_ADOCAO.md`: template para registrar responsáveis, cadência, adaptações aceitas e pendências locais.

### Alterados

- README: adicionada explicação das melhorias e dos arquivos que o usuário deve preencher antes de considerar o ADF pronto no projeto consumidor.
- Índice, mapa documental, papéis, fluxo, checklist, prompt de início, template de execução e adaptação do ADF: agora apontam para a configuração de IAs e exigem definição da rota de execução.
- Versão do ADF: atualizada para `1.2.0` como capacidade compatível nova.

### Benefícios

- A IA Pensante passa a ter uma fonte canônica para decidir quando executar, quando delegar para IA Dev Principal e quando usar OpenCode.
- Cada projeto consumidor pode declarar seus próprios modelos gratuitos do OpenCode sem alterar o Core.
- A instalação fica mais clara para novos usuários, com decisões obrigatórias antes da primeira feature.

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
