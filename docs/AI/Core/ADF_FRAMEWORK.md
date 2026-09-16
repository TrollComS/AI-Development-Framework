# Contrato do ADF

## Propósito

O ADF é uma camada documental versionada para dar contexto confiável a pessoas e IAs. Não substitui controle de versão, testes ou responsabilidade humana.

## Regras

1. O repositório é a fonte de verdade dos artefatos; dentro do ADF, `docs/` é a fonte canônica de contexto, regras, arquitetura, features e decisões locais.
2. Fatos, hipóteses e decisões devem ser distinguíveis.
3. Toda feature possui critérios de aceite verificáveis.
4. Mudanças atualizam regras, decisões e mapas afetados.
5. A IA declara lacunas e não inventa contexto.
6. Publicação, exclusão e ações irreversíveis exigem autorização.
7. Segredos e dados sensíveis não entram em documentos ou prompts.

## Contrato de instruções para agentes

O ADF separa documentação canônica de arquivos de instrução que uma ferramenta pode carregar automaticamente.

- `docs/` contém a fonte canônica e versionada do projeto consumidor.
- `docs/INDICE_DOCUMENTACAO.md` é o roteiro de leitura mínima por papel e tipo de tarefa.
- `AGENTS.md`, quando o projeto consumidor decidir adotá-lo, é o ponto de entrada universal recomendado para agentes. Ele deve encaminhar para este contrato e para o índice, sem copiar toda a documentação.
- Arquivos específicos de ferramenta são adaptadores opcionais. Eles devem conter somente instruções próprias daquela ferramenta e links para as fontes canônicas; não devem duplicar integralmente regras, arquitetura, features ou decisões do ADF.

### Preflight obrigatório

Antes de analisar, planejar, implementar, corrigir ou revisar, o agente deve seguir esta ordem:

1. Ler a instrução de entrada aplicável ao agente, quando existir.
2. Ler `docs/INDICE_DOCUMENTACAO.md`.
3. Ler `docs/Projeto/CONFIGURACAO_IAS.md` e `docs/Projeto/LIMITACOES_EXECUCAO_FEATURES.md`, quando existir.
4. Carregar somente a feature, skill, regras, arquitetura, padrões, decisões e testes relacionados à tarefa.
5. Inspecionar o código e o estado atual antes de propor ou realizar alteração.

O preflight não exige ler toda a pasta `docs/`. O índice define o contexto mínimo suficiente.

### Precedência e decisões locais

Instruções explícitas do usuário e regras de segurança prevalecem sobre orientações genéricas. O Core define o processo; documentos do projeto consumidor definem ferramentas, convenções, comandos, riscos e demais decisões locais. Adaptadores de ferramenta não podem contradizer a documentação canônica; divergências devem ser corrigidas na fonte apropriada.

### Granularidade das entregas

O padrão recomendado é que cada feature represente o menor incremento funcional coerente, com escopo, critérios de aceite, riscos e validações próprios. Iniciativas maiores devem ser divididas em features independentes e verificáveis.

Etapas inseparáveis para preservar integridade, segurança, migração ou compatibilidade podem permanecer na mesma feature. A exceção deve registrar motivo, impacto e a aprovação humana aplicável ou a pendência que impede a aprovação.

Cada projeto consumidor pode ajustar essa política em `docs/Projeto/CONFIGURACAO_IAS.md` ou `docs/Projeto/ADF_ADOCAO.md`, sem modificar o Core.

## Adoção mínima

Visão, glossário, arquitetura, padrões essenciais, uma feature do projeto consumidor, índice navegável e responsável pela manutenção.

O ADF pode ser estendido; adaptações do Core devem ser registradas.
