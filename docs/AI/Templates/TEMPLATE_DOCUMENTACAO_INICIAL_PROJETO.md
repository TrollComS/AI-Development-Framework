# Template: documentacao inicial do projeto consumidor

Use este template quando o usuario autorizar a IA instaladora a analisar o projeto atual e gerar documentacao inicial do ADF.

## Regras de preenchimento

1. Preserve documentos existentes e peca autorizacao antes de acrescentar conteudo.
2. Registre apenas informacoes sustentadas por resposta do usuario, arquivos de projeto, estrutura de diretorios ou documentacao existente.
3. Marque toda informacao como `Informado pelo usuario`, `Inferido da estrutura do projeto` ou `Pendente de confirmacao humana`.
4. Nao registre regra de negocio como verdade quando ela for apenas suspeita.
5. Prefira textos curtos, revisaveis e uteis para orientar features futuras.

## Documentos permitidos

- `docs/Projeto/VISAO_PROJETO.md`
- `docs/Arquitetura/MAPA_PROJETOS.md`
- `docs/Arquitetura/COMPONENTES.md`
- `docs/Arquitetura/INTEGRACOES.md`
- `docs/Padroes/PADROES_TECNICOS.md`
- `docs/RegrasNegocio/README.md`

## Secao obrigatoria

Inclua esta secao em cada documento criado ou em cada bloco acrescentado a documento existente:

```markdown
## Classificacao das informacoes

- **Informado pelo usuario:** <itens ou Nao informado>
- **Inferido da estrutura do projeto:** <itens ou Nao identificado>
- **Pendente de confirmacao humana:** <itens ou Nenhuma pendencia inicial registrada>
```

## Estrutura sugerida: VISAO_PROJETO.md

```markdown
# Visao do projeto

## Proposito

<resumo curto>

## Escopo inicial

- <item>

## Estrutura observada

- <item>

## Classificacao das informacoes

- **Informado pelo usuario:** <itens ou Nao informado>
- **Inferido da estrutura do projeto:** <itens ou Nao identificado>
- **Pendente de confirmacao humana:** <itens ou Nenhuma pendencia inicial registrada>
```

## Estrutura sugerida: MAPA_PROJETOS.md

```markdown
# Mapa de projetos

| Projeto/pacote | Caminho | Tipo inferido | Observacao |
|---|---|---|---|
| <nome> | <caminho> | <tipo> | <origem ou pendencia> |

## Classificacao das informacoes

- **Informado pelo usuario:** <itens ou Nao informado>
- **Inferido da estrutura do projeto:** <itens ou Nao identificado>
- **Pendente de confirmacao humana:** <itens ou Nenhuma pendencia inicial registrada>
```

## Estrutura sugerida: COMPONENTES.md

```markdown
# Componentes

| Componente | Evidencia | Responsabilidade aparente | Confirmacao |
|---|---|---|---|
| <nome> | <arquivo/diretorio> | <responsabilidade> | Inferido da estrutura do projeto |

## Classificacao das informacoes

- **Informado pelo usuario:** <itens ou Nao informado>
- **Inferido da estrutura do projeto:** <itens ou Nao identificado>
- **Pendente de confirmacao humana:** <itens ou Nenhuma pendencia inicial registrada>
```

## Estrutura sugerida: INTEGRACOES.md

```markdown
# Integracoes

| Integracao | Evidencia | Uso aparente | Confirmacao |
|---|---|---|---|
| <nome> | <arquivo/pacote/configuracao> | <uso aparente> | Inferido da estrutura do projeto |

## Pendencias

- <integracao que precisa de confirmacao humana>

## Classificacao das informacoes

- **Informado pelo usuario:** <itens ou Nao informado>
- **Inferido da estrutura do projeto:** <itens ou Nao identificado>
- **Pendente de confirmacao humana:** <itens ou Nenhuma pendencia inicial registrada>
```

## Estrutura sugerida: PADROES_TECNICOS.md

```markdown
# Padroes tecnicos

| Padrao observado | Evidencia | Aplicacao | Confirmacao |
|---|---|---|---|
| <padrao> | <arquivo/diretorio/script> | <onde aplicar> | Inferido da estrutura do projeto |

## Classificacao das informacoes

- **Informado pelo usuario:** <itens ou Nao informado>
- **Inferido da estrutura do projeto:** <itens ou Nao identificado>
- **Pendente de confirmacao humana:** <itens ou Nenhuma pendencia inicial registrada>
```

## Estrutura sugerida: RegrasNegocio/README.md

```markdown
# Regras de negocio

## Regras confirmadas

- <regra confirmada por usuario ou documentacao existente>

## Pendencias de confirmacao humana

- <possivel regra ou decisao de dominio que nao deve ser tratada como verdade ainda>

## Classificacao das informacoes

- **Informado pelo usuario:** <itens ou Nao informado>
- **Inferido da estrutura do projeto:** <itens ou Nao identificado>
- **Pendente de confirmacao humana:** <itens ou Nenhuma pendencia inicial registrada>
```
