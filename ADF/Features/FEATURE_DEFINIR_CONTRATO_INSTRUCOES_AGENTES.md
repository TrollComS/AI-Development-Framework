# Feature: Definir contrato de instruções de agentes

**Estado:** Concluída

**Responsável:** A definir

**Papel recomendado:** IA Arquiteta

**Skill recomendada:** `docs/AI/Skills/SKILL_REVISAR_ARQUITETURA.md`

## Contexto obrigatório

- `README.md`
- `CONTRIBUTING.md`
- `docs/INDICE_DOCUMENTACAO.md`
- `docs/AI/Core/ADF_FRAMEWORK.md`
- `docs/AI/Core/FLUXO_DESENVOLVIMENTO.md`
- `docs/AI/Core/ROTEAMENTO_IAS.md`
- `docs/Projeto/CONFIGURACAO_IAS.md`
- `Installer/INSTALADOR_ADF.md`

## Problema

O ADF define documentação, papéis e roteamento, mas não define um contrato para os arquivos de instrução que cada agente lê automaticamente. Por isso, projetos consumidores podem duplicar regras do ADF em `AGENTS.md`, arquivos de Copilot e outros formatos, criando divergência entre a documentação canônica e os pontos de entrada dos agentes.

## Resultado esperado

O ADF deve definir que `docs/` é a fonte canônica de contexto e estabelecer um fluxo único de entrada para agentes. Arquivos específicos de ferramenta devem ser adaptadores curtos que encaminham para essa fonte, com regras apenas quando forem exclusivas da ferramenta.

## Escopo

### Incluído

- Definir a hierarquia entre documentação canônica, `AGENTS.md` e adaptadores de ferramenta.
- Definir o preflight obrigatório para análise, planejamento, implementação, correção e revisão.
- Definir a política padrão de granularidade: uma feature representa o menor incremento funcional coerente.
- Definir a exceção para etapas tecnicamente inseparáveis por integridade, segurança, migração ou compatibilidade.
- Definir quais escolhas são universais do ADF e quais são decisões do projeto consumidor.
- Atualizar os documentos Core, índice e mapas afetados.

### Fora do escopo

- Criar templates ou arquivos de instrução para ferramentas específicas.
- Alterar o instalador ou o atualizador.
- Tornar OpenCode, Codex, Copilot ou qualquer fornecedor obrigatório.
- Inserir convenções de um projeto consumidor no Core do ADF.

## Requisitos

1. `docs/` deve ser declarado como fonte canônica para contexto, regras, arquitetura, features e decisões locais.
2. `AGENTS.md` deve ser definido como ponto de entrada universal recomendado quando o projeto o habilitar.
3. O preflight deve seguir esta ordem: instrução de entrada aplicável, `docs/INDICE_DOCUMENTACAO.md`, configuração e limitações locais, contexto específico da tarefa e código afetado.
4. O índice deve continuar direcionando a leitura mínima; o contrato não pode exigir leitura integral de toda a pasta `docs/`.
5. Adaptadores de ferramenta não podem duplicar integralmente documentos do ADF; devem apontar para os documentos canônicos.
6. A granularidade deve ser configurável no projeto consumidor, com o padrão recomendado de incremento funcional coerente.
7. Exceções de granularidade devem declarar motivo, impacto e aprovação ou pendência humana aplicável.
8. O contrato deve informar como resolver conflito entre instruções: usuário e segurança prevalecem; documentos locais complementam o Core; adaptadores não contradizem a fonte canônica.

## Critérios de aceite

- [x] Dado um projeto com ADF, quando um agente inicia uma tarefa, então encontra no contrato uma ordem objetiva de leitura.
- [x] Dado um adaptador de ferramenta, quando ele for gerado, então ele aponta para `docs/` sem copiar regras canônicas completas.
- [x] Dado uma iniciativa grande, quando ela for planejada, então o contrato orienta sua divisão em features independentes e verificáveis.
- [x] Dado que duas etapas são inseparáveis, quando forem mantidas na mesma feature, então a justificativa exigida pelo contrato pode ser registrada.
- [x] Dado um projeto que não usa OpenCode, quando adota o ADF, então o contrato não o bloqueia nem cria uma obrigação implícita.
- [x] Dado que documentos Core foram alterados, quando a entrega for concluída, então índice e mapas relacionados permanecem coerentes.

## Riscos, dependências e reversão

**Riscos:** um contrato longo demais pode repetir o índice; regras vagas podem gerar interpretações inconsistentes.

**Mitigações:** manter o contrato conciso, delegar o roteamento detalhado aos documentos já existentes e usar links para fontes canônicas.

**Dependências:** nenhuma. Esta é a fundação para as três features seguintes.

**Reversão:** restaurar os documentos Core e os índices afetados; nenhum artefato de projeto consumidor é alterado por esta feature.

## Evidências

- Revisar o fluxo de entrada contra os papéis Analista, Arquiteta, Executora e Revisora.
- Verificar links e ausência de referências obrigatórias a um fornecedor específico.
- Simular uma feature pequena, uma migração e uma revisão usando o novo preflight.

## Checklist de conclusão

- [x] Contrato canônico de instruções definido.
- [x] Política de granularidade e exceções definida.
- [x] Core, índice e mapas atualizados.
- [x] Compatibilidade com projetos sem um fornecedor específico verificada.
- [x] Evidências e pendências reportadas.
