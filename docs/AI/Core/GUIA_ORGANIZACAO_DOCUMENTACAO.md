# Guia de organização da documentação

## Responsabilidade por diretório

| Diretório | Conteúdo canônico |
|---|---|
| `AI` | processo, papéis, skills, prompts e templates |
| `Projeto` | visão, glossário, status, roadmap e histórico |
| `Arquitetura` | estrutura, decisões, integrações e atributos de qualidade |
| `Padroes` | convenções recorrentes e verificáveis |
| `RegrasNegocio` | invariantes e políticas do domínio |
| `Features` | mudanças com escopo e aceite definidos |
| `Revisoes` | pareceres e evidências que precisam ser preservados |

## Regras de manutenção

1. Cada informação possui uma fonte canônica; outros documentos usam links.
2. Regra de negócio não fica em skill; decisão durável não fica somente em feature.
3. Crie arquivo quando o assunto tiver ciclo de vida ou referência próprios.
4. Atualize o arquivo existente quando a informação apenas evoluir sua responsabilidade.
5. Separe estado vigente de histórico; preserve o histórico em changelog, ADR, feature ou revisão.
6. Divida documentos extensos por responsabilidade, mantendo um resumo navegável.
7. Ao concluir uma mudança, avalie documentos afetados; não altere arquivos sem impacto real.
