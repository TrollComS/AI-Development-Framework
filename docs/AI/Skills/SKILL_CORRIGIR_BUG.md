# Skill: Corrigir bug

**Entrada:** comportamento esperado, evidência da falha e contexto afetado. **Saída:** causa tratada e regressão validada.

1. Reproduzir a falha ou registrar por que isso não foi possível.
2. Localizar a causa, diferenciando-a dos sintomas.
3. Definir a correção mínima e os riscos de regressão.
4. Criar teste que falhe antes da correção, quando aplicável.
5. Implementar sem refatorar áreas não relacionadas.
6. Executar teste focal e suíte proporcional ao impacto.
7. Atualizar documentação somente se comportamento, regra ou decisão mudou.

Não masque erros, remova validações ou altere contratos sem avaliar o impacto.
