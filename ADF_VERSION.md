# Versão do ADF

**Versão:** 1.5.0

**Esquema:** Semantic Versioning 2.0.0

- **MAJOR:** mudança incompatível no contrato.
- **MINOR:** capacidade nova e compatível.
- **PATCH:** correção compatível.

O projeto consumidor deve registrar a versão instalada e suas adaptações.

## Compatibilidade da versão 1.5

A versão 1.5 formaliza o contrato de instruções para agentes: `docs/` passa a ser a fonte canônica declarada, `AGENTS.md` passa a ser o ponto de entrada universal recomendado quando adotado, e o preflight passa a orientar a leitura mínima. A política de granularidade de features também é explícita e configurável por projeto. Não há movimentação de diretórios; projetos existentes podem adotar as novas seções e manter suas ferramentas atuais.

## Compatibilidade da versão 1.4

A versão 1.4 adiciona o fluxo de atualização assistida em `Installer/UPDATE.md` e o mapa de migrações em `Installer/MIGRACOES_ADF.md`. Projetos existentes podem atualizar o ADF sem reinstalar o esqueleto por cima da documentação local; não há movimentação de diretórios nem quebra dos caminhos da versão 1.3.

## Compatibilidade da versão 1.3

A versão 1.3 amplia o instalador guiado com duas etapas opcionais: registro de limitações locais para execução de features e geração de documentação inicial do projeto consumidor. Projetos existentes podem continuar usando a instalação básica; não há movimentação de diretórios nem quebra dos caminhos da versão 1.2.

## Compatibilidade da versão 1.2

A versão 1.2 adiciona roteamento de IAs e configuração local em `docs/Projeto/CONFIGURACAO_IAS.md`. Projetos existentes podem adotar essa capacidade preenchendo o novo arquivo e consultando `docs/AI/Core/ROTEAMENTO_IAS.md`; não há movimentação de diretórios nem quebra dos caminhos da versão 1.1.

## Compatibilidade da versão 1.1

O índice canônico agora fica em `docs/INDICE_DOCUMENTACAO.md`. O caminho anterior em `docs/AI/Core` permanece como redirecionamento documental. Nenhum diretório existente foi movido.
