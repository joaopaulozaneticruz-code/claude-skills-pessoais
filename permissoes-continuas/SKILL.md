---
name: permissoes-continuas
description: Ao final de cada resposta em que você rodou comandos de terminal (Bash/PowerShell), avalie se surgiu um padrão novo de comando seguro/reversível que ainda não está na lista de permissões do projeto (.claude/settings.json) e, se sim, adicione — e também preveja, olhando o que falta na fila de tarefas e no roadmap do projeto, quais permissões provavelmente vão ser necessárias no caminho que a solução está tomando, adicionando-as antes de precisar pedir. Só escreva no arquivo quando houver algo genuinamente novo para adicionar — não reescreva o arquivo toda resposta sem necessidade. Segue o mesmo critério já estabelecido (comandos somente-leitura, reversíveis e de baixo risco liberados; apagar arquivo, mudança de schema/banco, instalar dependência nova, git push/force-push e execução de código arbitrário continuam pedindo confirmação, nunca entram na lista automaticamente).
---

# Permissões contínuas

## Por que existe

O usuário já pediu, antes, pra eu propor uma lista de permissões baseada no
histórico — mas isso exigia ele pedir de novo cada vez que a fricção
voltava a aparecer. Essa skill torna esse hábito contínuo: em vez de
esperar acumular frustração e um pedido explícito, eu mesmo mantenho a
lista andando junto com o trabalho, então a lista de permissões nunca fica
muito atrás do que o projeto realmente precisa.

## Quando avaliar

Ao final de uma resposta em que comandos de terminal foram executados —
não durante, não antes. Isso é uma checagem leve de rotina, não uma tarefa
que merece anúncio grande toda vez.

**Não é preciso avaliar em toda resposta indiscriminadamente** — só faz
sentido quando a resposta envolveu rodar comando de terminal. Uma resposta
que só respondeu uma pergunta ou editou um arquivo sem rodar nada não tem o
que avaliar aqui.

## O que fazer na avaliação

1. **Padrão observado**: olhe os comandos rodados nessa resposta (e, se
   fizer sentido, na sessão até aqui). Algum deles é seguro/reversível
   (leitura, build, rodar servidor local, etc. — mesmo critério de
   [[feedback-permissions-scope]] se essa memória existir, ou o bom senso
   já estabelecido no projeto) e ainda não está coberto por uma regra em
   `permissions.allow`? Se sim, é candidato.
2. **Previsão pelo caminho da solução**: olhe pra onde o trabalho está
   indo — a fila de tarefas (`tarefas.md`, se existir), as pendências
   registradas em `O combinado.md`, o roadmap do `CLAUDE.md`. Tem algum
   tipo de comando que vai ser claramente necessário em breve (ex: o
   roadmap menciona uma tecnologia nova que ainda não apareceu nos
   comandos rodados) e que já dá pra liberar hoje, sem esperar bater de
   frente com o pedido de permissão? Só adicione o que é razoavelmente
   previsível — não invente permissão pra algo hipotético demais.
3. **Filtro de risco, sempre**: nunca adicione automaticamente comando que
   apague arquivo, mude schema/banco, instale dependência nova, dê
   git push/force-push, ou rode código arbitrário (interpretador direto,
   JS solto em página). Esses continuam pedindo confirmação de propósito —
   essa skill não muda esse limite, só acelera o que já era considerado
   seguro liberar.
4. **Só escreva se houver novidade real.** Se nada mudou desde a última
   vez que a lista foi revisada, não toque no arquivo — não fica
   reescrevendo `settings.json` com o mesmo conteúdo toda resposta.

## Como aplicar

- Edite `permissions.allow` no `.claude/settings.json` do projeto atual
  (nunca `permissions.deny`/`ask`, nunca outro campo do arquivo).
- Prefira o padrão mais estreito que cobre o uso observado (ex:
  `Bash(dotnet build*)` em vez de `Bash(dotnet*)`), do jeito que já vem
  sendo feito nesse projeto.
- Quando adicionar algo, mencione em uma linha curta no fim da resposta
  (não precisa de tabela nem explicação longa toda vez — isso já foi feito
  quando a lista foi revisada a fundo da primeira vez). Quando não houver
  nada novo pra adicionar, não precisa dizer "nada mudou" — só segue quieto.
