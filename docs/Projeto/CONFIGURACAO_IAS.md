# Configuração de IAs do projeto

Este arquivo deve ser preenchido ao adotar o ADF. Ele é lido pela IA Pensante antes de planejar ou executar features.

## Estado

- **OpenCode obrigatório:** Sim
- **Uso permitido:** apenas modelos gratuitos configurados localmente
- **Responsável por manter esta configuração:** A definir
- **Última revisão:** A definir

## IA Pensante principal

- **Ferramenta/modelo:** A definir
- **Uso:** conversa com o usuário, entendimento do pedido, leitura do ADF, planejamento, roteamento e revisão de contexto.
- **Pode implementar diretamente:** apenas tarefas pequenas, localizadas e de baixo risco.
- **Não deve fazer:** código pesado, feature grande, refatoração ampla ou mudança estrutural quando a rota indicada for IA Dev Principal ou OpenCode.

## IA Dev Principal

- **Ferramenta/modelo:** A definir
- **Uso:** código pesado, features grandes, mudanças amplas, refatorações complexas, arquitetura e tarefas com alto risco de regressão.
- **Critérios de envio:** múltiplos módulos, muitos arquivos, contrato público, segurança, migração, performance crítica ou incerteza técnica alta.
- **Rota alternativa se indisponível:** A definir

## OpenCode

- **Instalação exigida na máquina do usuário:** Sim
- **Comando de verificação:** `opencode --version`
- **Modo de uso:** gratuito
- **Rota alternativa se indisponível:** IA Dev Principal

### Modelos gratuitos disponíveis

Preencha somente modelos que o usuário realmente configurou e pode usar gratuitamente via OpenCode.

| Nome local no OpenCode | Melhor uso | Evitar quando | Observações |
|---|---|---|---|
| A definir | Documentação, pequenos ajustes ou análise local | Código pesado ou contexto longo | A definir |
| A definir | Testes, CRUD simples ou boilerplate | Arquitetura e decisões críticas | A definir |
| A definir | Revisão pontual de diff | Refatoração ampla | A definir |

## Matriz de roteamento

| Tipo de tarefa | Rota preferencial | Condição |
|---|---|---|
| Conversa inicial, descoberta de contexto e planejamento | IA Pensante | Sempre iniciar aqui |
| Feature pequena e localizada | OpenCode | Se houver modelo gratuito adequado |
| Correção simples de bug | OpenCode | Se reprodução e aceite estiverem claros |
| Testes ou documentação localizada | OpenCode | Se não envolver decisão de arquitetura |
| CRUD simples | OpenCode | Se padrões e entidade estiverem claros |
| Feature grande ou multi-módulo | IA Dev Principal | Quando envolver muitos arquivos ou etapas dependentes |
| Refatoração ampla | IA Dev Principal | Quando comportamento precisa ser preservado em várias áreas |
| Arquitetura, segurança, migração ou contrato público | IA Dev Principal | Sempre que houver alto impacto |
| Revisão final | IA Pensante ou IA Revisora definida | Deve comparar diff, aceite e validações |

## Regras para a IA Pensante

1. Começar em `docs/INDICE_DOCUMENTACAO.md`.
2. Ler este arquivo antes de decidir quem implementa.
3. Escolher a skill adequada para a tarefa.
4. Declarar a rota escolhida no plano.
5. Usar OpenCode somente com modelos gratuitos declarados neste arquivo.
6. Se OpenCode estiver indisponível, registrar o impedimento e usar a rota alternativa.
7. Não enviar segredos, tokens ou dados sensíveis para nenhuma IA.
8. Não alterar esta configuração sem aprovação humana.
