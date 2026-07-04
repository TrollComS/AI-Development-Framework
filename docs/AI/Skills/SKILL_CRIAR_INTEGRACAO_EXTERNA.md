# Skill: Criar integração externa

**Entrada:** contrato externo, autenticação, requisitos de erro e segurança. **Saída:** integração isolada, resiliente e testável.

1. Confirmar contrato, limites, idempotência e dados sensíveis.
2. Isolar transporte e modelos externos atrás de uma abstração do projeto.
3. Configurar autenticação sem registrar ou versionar segredos.
4. Definir timeout, cancelamento, retentativa e tratamento de indisponibilidade conforme o risco.
5. Validar entradas e respostas; registrar logs sem conteúdo sensível.
6. Testar com transporte simulado, incluindo erros e respostas inválidas.
7. Documentar contrato, operação e decisão arquitetural quando durável.

Não use serviço real em teste unitário nem espalhe chamadas externas pelas camadas.
