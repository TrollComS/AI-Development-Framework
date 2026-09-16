# Feature: Instalar o ADF

## Objetivo

Adicionar a estrutura ADF sem apagar conteúdo existente.

## Procedimento

1. Criar branch e confirmar o estado da árvore.
2. Copiar `docs/AI`, diretórios documentais e `ADF_VERSION.md`.
3. Preservar arquivos existentes e integrar conflitos manualmente.
4. Perguntar se o usuario deseja registrar limitacoes locais de execucao de features.
5. Perguntar se o usuario deseja gerar documentacao inicial do projeto consumidor.
6. Perguntar quais adaptadores de agentes suportados devem ser gerados e coletar comandos, diretórios e áreas necessários ao preflight.
7. Validar links e UTF-8.
8. Registrar versão, responsável, ferramentas, adaptadores, respostas opcionais e pendencias em `docs/Projeto/ADF_ADOCAO.md`.

## Aceite

Estrutura presente, versão registrada, adaptadores selecionados criados ou preservados com segurança, links válidos e nenhuma perda de conteúdo. Para reverter, reverta o commit de instalação.
