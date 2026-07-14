# Roteamento de IAs

Este documento define como escolher a ferramenta de IA para cada etapa sem prender o ADF a um fornecedor, modelo ou plano pago.

## Fonte de configuração

Cada projeto consumidor deve preencher `docs/Projeto/CONFIGURACAO_IAS.md`.

Esse arquivo é a fonte canônica para:

- IA Pensante principal usada pelo usuário;
- IA de Dev principal para código pesado;
- obrigatoriedade e forma de uso do OpenCode;
- modelos gratuitos disponíveis no OpenCode;
- critérios para decidir quando delegar para cada opção.

O Core define o processo. A configuração do projeto define as escolhas concretas.

## Papéis operacionais

### IA Pensante

Responsável por conversar com o usuário, entender intenção, ler o ADF, separar fatos de lacunas, escolher papel e skill, decidir o roteamento e preparar prompts de delegação.

A IA Pensante não deve assumir que uma tarefa será implementada por ela quando a configuração indicar Dev principal ou OpenCode.

### IA Dev Principal

Responsável por implementações grandes, mudanças estruturais, refatorações amplas, features com múltiplos módulos, migrações, alterações de arquitetura e tarefas com alto risco de regressão.

### IA OpenCode

Responsável por tarefas que possam ser executadas no ambiente local via OpenCode usando modelos gratuitos configurados pelo usuário.

O OpenCode deve ser tratado como requisito operacional do projeto quando `docs/Projeto/CONFIGURACAO_IAS.md` marcar seu uso como obrigatório.

## Regra de decisão

Antes de iniciar uma feature, a IA Pensante deve:

1. Ler `docs/INDICE_DOCUMENTACAO.md`.
2. Ler `docs/Projeto/CONFIGURACAO_IAS.md`.
3. Identificar papel, skill e contexto mínimo.
4. Classificar a tarefa por risco, tamanho e tipo de mudança.
5. Escolher uma rota: IA Pensante, IA Dev Principal ou OpenCode.
6. Registrar no plano qual rota será usada e por quê.

## Quando usar a IA Dev Principal

Use a IA Dev Principal quando houver pelo menos um destes sinais:

- mudança em arquitetura, contratos públicos, segurança, autenticação, pagamentos, dados sensíveis ou migrações;
- feature grande com múltiplos módulos, muitos arquivos ou várias etapas dependentes;
- refatoração ampla;
- necessidade de raciocínio profundo sobre design, compatibilidade ou regressões;
- falha anterior de uma rota mais simples;
- incerteza alta sobre impacto.

## Quando usar OpenCode

Use OpenCode quando a configuração local indicar um modelo gratuito adequado e a tarefa for compatível com execução local, por exemplo:

- alteração pequena ou média com escopo bem definido;
- geração de código repetitivo;
- ajustes localizados de layout, testes, documentação ou CRUD simples;
- investigação mecânica em arquivos;
- revisão pontual de diff;
- tarefas que não exijam modelo pago, contexto muito longo ou decisão arquitetural complexa.

Se o OpenCode não estiver instalado, configurado ou disponível, registre o impedimento e use a rota alternativa definida em `docs/Projeto/CONFIGURACAO_IAS.md`.

## Quando a IA Pensante pode executar

A IA Pensante pode executar diretamente somente quando a tarefa for pequena, de baixo risco e compatível com as permissões disponíveis.

Mesmo nesses casos, deve seguir a skill aplicável, preservar mudanças não relacionadas, validar quando possível e relatar evidências.

## Prompt de delegação

Ao delegar para IA Dev Principal ou OpenCode, a IA Pensante deve enviar:

- objetivo da tarefa;
- arquivos e documentos ADF relevantes;
- papel e skill aplicáveis;
- escopo dentro e fora;
- critérios de aceite;
- restrições técnicas e de segurança;
- validações esperadas;
- formato da resposta esperada.

Não envie documentação inteira sem necessidade. O ADF privilegia contexto mínimo e direcionado.

## Limites

- Não escolher modelo pago quando a configuração exigir uso gratuito.
- Não inventar modelos disponíveis no OpenCode; usar apenas os declarados pelo usuário.
- Não expor segredos em prompts.
- Não delegar ação irreversível sem autorização humana.
- Não alterar a configuração de IAs sem registrar a decisão no projeto consumidor.
