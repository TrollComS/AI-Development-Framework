# Feature: Melhorar instalador do ADF com limitacoes de execucao e documentacao inicial do projeto

**Estado:** Concluida

**Responsavel:** A definir

**Papel recomendado:** IA Arquiteta + IA Dev Principal

**Skill recomendada:** docs/AI/Skills/SKILL_ATUALIZAR_DOCUMENTACAO.md

## Contexto obrigatorio

- docs/INDICE_DOCUMENTACAO.md
- Installer/INSTALADOR_ADF.md
- docs/AI/Core/FLUXO_DESENVOLVIMENTO.md
- docs/AI/Core/GUIA_ORGANIZACAO_DOCUMENTACAO.md
- docs/AI/Templates/TEMPLATE_VISAO_PROJETO.md
- docs/AI/Templates/TEMPLATE_PADRAO.md
- docs/AI/Templates/TEMPLATE_REGRA_NEGOCIO.md

## Problema

O instalador atual do ADF realiza a adocao inicial do framework, copia a estrutura documental e preenche arquivos obrigatorios como `CONFIGURACAO_IAS.md` e `ADF_ADOCAO.md`.

Porem, durante a instalacao em projetos reais, surgem duas necessidades adicionais:

1. Registrar limitacoes locais para execucao de features, evitando que IAs alterem areas sensiveis sem autorizacao.
2. Permitir que a IA gere uma documentacao inicial do projeto consumidor dentro da estrutura do ADF, usando a solucao/codigo existente como fonte.

Sem essas perguntas, o ADF fica instalado, mas ainda pouco alimentado com contexto real do projeto.

## Resultado esperado

O instalador do ADF deve passar a oferecer duas etapas opcionais:

1. Perguntar se o usuario deseja registrar limitacoes para execucao de features.
2. Perguntar se o usuario deseja gerar documentacao inicial do projeto atual nos arquivos do ADF.

Quando o usuario aceitar, o instalador deve conduzir a coleta/analise, preencher os documentos correspondentes e deixar claro o que foi informado pelo usuario e o que foi inferido pela IA.

## Escopo

### Incluido

- Atualizar `Installer/INSTALADOR_ADF.md`.
- Adicionar pergunta opcional sobre limitacoes de execucao de features.
- Adicionar pergunta opcional sobre documentacao inicial do projeto consumidor.
- Definir validacoes para respostas `sim`/`nao`.
- Definir onde registrar limitacoes locais.
- Definir quais documentos podem ser preenchidos na documentacao inicial.
- Criar ou atualizar templates necessarios.
- Atualizar indices e mapas do ADF para apontar para os novos documentos.
- Garantir que a funcionalidade continue generica, sem depender de um projeto especifico.

### Fora do escopo

- Documentar automaticamente todos os projetos existentes sem autorizacao do usuario.
- Inventar regras de negocio nao identificadas no codigo ou nao informadas pelo usuario.
- Fazer alteracoes em codigo-fonte do projeto consumidor.
- Exigir que todos os projetos adotem a documentacao inicial obrigatoriamente.
- Substituir revisao humana da arquitetura.

## Requisitos

1. O instalador deve perguntar:

   `Deseja registrar limitacoes para execucao de features neste projeto? Responda sim ou nao.`

2. Se a resposta for `sim`, o instalador deve coletar limitacoes em formato simples.

   Exemplo:

   `Nao alterar Scripts sem autorizacao; nao modificar fluxo de pagamento sem revisao; sempre executar build antes de finalizar.`

3. As limitacoes devem ser gravadas em um documento dedicado, preferencialmente:

   `docs/Projeto/LIMITACOES_EXECUCAO_FEATURES.md`

4. O indice principal deve referenciar o documento de limitacoes como leitura obrigatoria antes de executar features.

5. O instalador deve perguntar:

   `Deseja que eu analise o projeto atual e gere uma documentacao inicial nos arquivos do ADF? Responda sim ou nao.`

6. Se a resposta for `sim`, o instalador deve analisar a estrutura real do projeto consumidor.

7. A analise deve priorizar arquivos de solucao/projeto, diretorios principais, documentacao existente e nomes de modulos.

8. A documentacao inicial pode preencher ou criar:

   - `docs/Projeto/VISAO_PROJETO.md`
   - `docs/Arquitetura/MAPA_PROJETOS.md`
   - `docs/Arquitetura/COMPONENTES.md`
   - `docs/Arquitetura/INTEGRACOES.md`
   - `docs/Padroes/PADROES_TECNICOS.md`
   - `docs/RegrasNegocio/README.md`

9. A IA deve diferenciar claramente:

   - informacao fornecida pelo usuario;
   - informacao inferida da estrutura do projeto;
   - pendencia que exige confirmacao humana.

10. O instalador nao deve sobrescrever documentos existentes sem autorizacao explicita.

11. Quando nao houver confianca suficiente para documentar uma regra, a IA deve registrar como pendencia, nao como verdade.

12. A documentacao inicial deve ser curta, objetiva e util para orientar futuras features.

13. O instalador deve atualizar `docs/INDICE_DOCUMENTACAO.md` e mapas relacionados quando novos documentos forem criados.

14. A instalacao deve continuar funcionando mesmo se o usuario responder `nao` para as duas novas perguntas.

15. Ao final da instalacao, o instalador deve informar claramente:

   - ADF instalado em modo basico ou completo;
   - limitacoes de execucao registradas ou nao registradas;
   - documentacao inicial do projeto realizada ou nao realizada.

## Criterios de aceite

- [ ] Dado um projeto sem limitacoes cadastradas, quando o usuario responder `sim` para limitacoes, entao o instalador cria `docs/Projeto/LIMITACOES_EXECUCAO_FEATURES.md`.
- [ ] Dado que o usuario informou limitacoes, quando o arquivo for criado, entao ele contem as limitacoes em formato claro e revisavel.
- [ ] Dado que o usuario respondeu `nao` para limitacoes, quando a instalacao terminar, entao nenhum documento de limitacoes e criado obrigatoriamente.
- [ ] Dado que o usuario respondeu `sim` para documentacao inicial, quando a instalacao terminar, entao os documentos de projeto/arquitetura/padroes aplicaveis sao criados ou atualizados.
- [ ] Dado que a IA inferiu informacoes do codigo, quando a documentacao for gerada, entao essas informacoes sao marcadas como inferidas.
- [ ] Dado que a IA nao conseguiu confirmar uma regra de negocio, quando a documentacao for gerada, entao a informacao aparece como pendencia.
- [ ] Dado que ja existe documentacao no projeto consumidor, quando a instalacao rodar, entao o instalador preserva conteudo existente e pede autorizacao antes de sobrescrever.
- [ ] Dado que o usuario respondeu `nao` para documentacao inicial, quando a instalacao terminar, entao apenas a instalacao basica do ADF e realizada.
- [ ] Dado que novos documentos foram criados, quando a instalacao terminar, entao `docs/INDICE_DOCUMENTACAO.md` aponta para eles.
- [ ] Dado que a instalacao terminou, quando a mensagem final for exibida, entao ela informa se a instalacao foi basica ou completa.

## Riscos, dependencias e reversao

Riscos:

- A IA pode inferir incorretamente responsabilidades de modulos apenas por nomes de arquivos.
- A documentacao inicial pode ficar grande demais e aumentar consumo de contexto.
- O instalador pode ficar longo e cansativo se fizer perguntas demais.

Mitigacoes:

- Toda informacao inferida deve ser marcada como inferida.
- O usuario deve poder responder `nao` para as etapas opcionais.
- A documentacao inicial deve priorizar mapas e resumos, nao documentacao exaustiva.
- Pendencias devem ser registradas quando houver incerteza.

Reversao:

- Como a mudanca afeta documentacao e templates do ADF, a reversao pode ser feita restaurando `Installer/INSTALADOR_ADF.md`, templates e indices alterados.
- Documentos novos devem ser removiveis sem quebrar a instalacao basica.

## Evidencias

- Executar uma instalacao simulada em um projeto vazio.
- Executar uma instalacao simulada em um projeto com `docs` existente.
- Validar fluxo com resposta `sim` para as duas perguntas.
- Validar fluxo com resposta `nao` para as duas perguntas.
- Verificar se os indices apontam para os novos documentos.
- Verificar se nao ha sobrescrita silenciosa.

## Checklist de conclusao

- [x] Escopo entregue e fora de escopo preservado.
- [x] Instalador atualizado.
- [x] Templates necessarios criados ou atualizados.
- [x] Indices e mapas atualizados.
- [x] Fluxo validado por inspecao documental para respostas `sim` e `nao`.
- [x] Documentacao gerada diferencia informacao informada, inferida e pendente.
- [x] Nenhuma regra especifica de projeto foi adicionada ao ADF base.
- [x] Arquivos, validacoes, documentos e pendencias reportados.
