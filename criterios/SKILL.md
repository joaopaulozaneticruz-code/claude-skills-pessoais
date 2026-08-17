---
name: criterios
description: Sempre que for implementar uma tarefa concreta vinda de um spec, ticket, ou item de "tarefas.md" (ver skill fila-de-tarefas) — ou qualquer pedido direto de implementação — siga este critério de condução do trabalho, não só o que implementar. Implemente exatamente o que foi descrito, sem expandir escopo. Aplique TDD sempre (teste falhando antes de qualquer código de produção novo — feature, bugfix, refatoração) — ver skill test-driven-development pro processo completo; não pule por conta própria, pare e pergunte se achar que o caso não se encaixa. Rode typecheck e os arquivos de teste específicos regularmente durante o trabalho, e a suíte completa uma vez ao terminar (e de novo se o /code-review do passo 4 gerar correções); se o projeto não tiver testes/typecheck configurados, avise e pergunte antes de montar essa base, nunca instale ferramenta nova em silêncio. Ao terminar, use /code-review pra revisar o próprio trabalho antes de considerar concluído. Depois, faça commit no branch atual seguindo as regras normais de git. Dispare esta skill de forma proativa sempre que a conversa entrar em modo de implementação de algo já decidido — não espere o usuário pedir esse checklist explicitamente.
---

# Critérios

## Por que existe

Define não *o que* implementar (isso vem do spec, do ticket, ou da tarefa
da fila), mas *como* conduzir a implementação — pra pegar erro cedo (testes
e typecheck rodando ao longo do caminho, não só no fim), pra não crescer
escopo silenciosamente, e pra nunca considerar algo "pronto" sem passar por
uma revisão e sem estar de fato salvo no controle de versão.

## Quando disparar

Toda vez que for implementar uma tarefa concreta — vinda de um item de
`tarefas.md` (skill `fila-de-tarefas`), de um spec, de um ticket, ou de
qualquer pedido direto de implementação, mesmo fora do fluxo das outras
skills. Dispare proativamente, sem esperar a pessoa pedir esse checklist.

## Passo a passo

### 1. Implemente exatamente o que foi descrito

Não expanda o escopo além do que está no spec/ticket/tarefa. Se aparecer
uma necessidade nova no meio do caminho, isso é uma decisão nova — trate
como tal (dispare `me-entreviste` se for relevante o suficiente, ou pelo
menos confirme antes de seguir) em vez de decidir sozinho e continuar.

### 2. TDD sempre — sem exceção decidida por conta própria

- Escreva o teste que falha **antes** de qualquer código de produção novo
  — funcionalidade nova, correção de bug, refatoração, mudança de
  comportamento — e implemente só até esse teste passar (RED → GREEN →
  REFACTOR). Processo completo e a lista de racionalizações inválidas
  ("isso é diferente porque...") estão na skill `test-driven-development`.
- *(Decisão de 16/08/2026 — substitui a versão anterior desta seção, que
  limitava TDD a "seams" pré-combinados. Antes, a exceção era decidida por
  conta própria; agora, se um caso parecer não se encaixar em TDD — lógica
  de UI solta, glue code, script avulso —, pare e pergunte antes de pular,
  em vez de decidir sozinho.)*
- **Se o projeto não tiver nenhuma base de testes configurada ainda, pare
  antes de aplicar essa prática.** Avise que não há testes configurados e
  pergunte se a pessoa quer que você monte a base antes de seguir. Nunca
  instale ferramenta de teste nova, silenciosamente, num projeto que
  valoriza dependência mínima (confira o `CLAUDE.md` do projeto, se
  existir, antes de presumir que pode instalar algo).

### 3. Cadência de verificação

- Depois de cada mudança relevante: rode o typecheck (se o projeto tiver)
  e o(s) arquivo(s) de teste específico(s) do que você acabou de mexer —
  feedback rápido e focado, não a suíte inteira a cada mudança pequena.
- Ao terminar a tarefa inteira: rode a suíte de testes completa antes de
  considerar pronto — pra pegar qualquer regressão que os testes focados
  não teriam visto. Se o `/code-review` do passo 4 resultar em qualquer
  correção, rode a suíte de novo depois — "já rodei antes" não vale como
  prova depois que o código mudou.
- Se typecheck ou suíte completa não existirem no projeto, siga o
  combinado no passo 2 (avisar, perguntar) — nunca finja que rodou algo
  que não existe.

### 4. Revisão antes de fechar

Com a implementação feita e os testes passando, use `/code-review` pra
revisar o próprio trabalho antes de considerar a tarefa concluída. Trate os
achados como faria com qualquer revisão de código — corrija o que fizer
sentido corrigir, e explique claramente o que decidir não corrigir e por
quê, em vez de só ignorar silenciosamente.

### 5. Commit

Depois da revisão, registre o trabalho no branch atual — seguindo as
regras normais de controle de versão já em vigor (nunca commitar sem que
tenha sido pedido quando isso for ambíguo, nunca force push, nunca pular
hooks, sempre um commit novo em vez de reescrever um existente). Isso fecha
o ciclo da tarefa: ela está pronta pra ser marcada como concluída na fila.

## Relação com as outras skills

`fila-de-tarefas` decide qual tarefa fazer agora e em que ordem; `criterios`
decide como conduzir a implementação de cada uma. Ao terminar os 5 passos
acima pra uma tarefa, ela está pronta pra ser marcada `[x]` na fila — o que
inclui reapresentar a fila inteira atualizada, como já é o combinado na
skill `fila-de-tarefas`.

O passo 2 (TDD) delega o processo detalhado pra skill `test-driven-development`
(pacote superpowers) — `criterios` é o checklist geral de condução da
tarefa, aquela é a referência de como fazer RED-GREEN-REFACTOR direito.
