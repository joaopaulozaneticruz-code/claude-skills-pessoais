---
name: fila-de-tarefas
description: Ao começar a construir uma solução (depois que o plano ou "O combinado.md" já tem decisões suficientes), transforme esse plano/decisões numa fila de tarefas dividida por funcionalidade da solução — nunca por camada técnica isolada. Cada tarefa precisa entregar algo testável de ponta a ponta (ex: ao construir um banco de dados, a tarefa inclui também a tela/comando que permite ver, editar e cadastrar registros nele — não fica só a estrutura invisível por trás). Mostre a fila completa em formato de checklist no início do projeto, salve numa "tarefas.md" na raiz do projeto, e toda vez que uma tarefa for concluída, mostre a fila inteira de novo com aquela tarefa marcada. Dispare esta skill de forma proativa sempre que a conversa sair do planejamento/decisão e entrar na fase de construir de fato — não espere o usuário pedir a fila explicitamente.
---

# Fila de tarefas

## Por que existe

Trabalho dividido por camada técnica (primeiro todo o banco, depois toda a
API, depois todo o front) só fica visível/testável no final — semanas de
trabalho invisível até dar pra ver alguma coisa funcionando. Dividido por
funcionalidade, cada tarefa entrega uma fatia completa e usável: dá pra ver
progresso de verdade a cada passo, pegar erro de rumo cedo, e nunca ficar
sem nada pra mostrar se o trabalho for interrompido no meio.

## Quando disparar

Dispare quando a conversa sai do modo "decidir o quê" e entra no modo
"construir de fato" — normalmente logo depois que um plano foi aprovado
(ex: saída do modo de planejamento) ou depois que `O combinado.md` já tem
decisões suficientes pra dar início à construção. Não espere o usuário
pedir a fila — monte e mostre proativamente antes do primeiro passo de
implementação.

Se já existir uma `tarefas.md` no projeto com uma fila em andamento, não
recomece do zero — retome de onde ela parou (ver seção "Retomando" abaixo).

## Como quebrar o plano em tarefas

O critério de divisão é **funcionalidade da solução, não camada técnica**.
Uma tarefa não é "criar o banco de dados", "criar a API" ou "criar o
front-end" como fases separadas cobrindo tudo — é uma fatia vertical de uma
funcionalidade específica, com todas as camadas que ela precisa pra ser
testável de ponta a ponta.

**Toda tarefa relevante precisa terminar em algo que dá pra ver e mexer**,
não só estrutura invisível por trás. Exemplo dado: ao construir um banco de
dados para uma funcionalidade, a tarefa não para na tabela criada — inclui
também a tela (ou comando, se o projeto não tiver interface visual) que
permite visualizar, editar e cadastrar novos registros ali. Sem isso, "está
pronto" não significa nada que dê pra conferir.

Isso não significa que TODA tarefa da fila é assim (setup inicial de
projeto, configuração de ambiente, autenticação de base às vezes precisam
vir antes de qualquer coisa ser testável) — mas a partir do momento em que
uma tarefa entrega uma funcionalidade real, ela carrega junto tudo que for
preciso pra essa funcionalidade poder ser vista e usada, não só a parte de
trás dela.

Nomeie cada tarefa pela funcionalidade entregue, não pela camada técnica
("Lançar despesa com rateio automático", não "Criar tabela de transações").

## A fila e o arquivo

- Use a ferramenta de tarefas (TaskCreate/TaskUpdate) pra rastrear o estado
  internamente, como já é seu hábito.
- Além disso, mantenha `tarefas.md` na raiz do projeto — mesmo nível de
  `O combinado.md`, se existir. É a versão persistente da fila: sobrevive
  entre sessões e a uma conversa compactada.
- Formato: checklist markdown simples, uma linha por tarefa, com uma frase
  curta do que fica testável ao concluir.

```markdown
# Tarefas — <nome do projeto>

- [ ] Login e autenticação (tela de entrada funcionando)
- [ ] Lançar despesa com rateio automático (formulário + lista + banco)
- [ ] Painel de sócios com pagamentos (tela + marcar como pago)
- [ ] Resumo por categoria (tela com os totais do período)
```

## Mostrando a fila

- **No início do projeto**: depois de montar a fila, mostre ela inteira
  como checklist na sua resposta — antes de começar a primeira tarefa.
- **A cada tarefa concluída**: não diga só "terminei a tarefa X" — mostre a
  fila inteira de novo, com aquela tarefa marcada (`[x]`). A pessoa
  precisa ver o progresso acumulado de uma vez, não só a última entrega
  isolada.
- Atualize `tarefas.md` no mesmo momento que atualiza a ferramenta de
  tarefas interna — os dois devem estar sempre sincronizados.

## Retomando

Se a `tarefas.md` já existir com tarefas concluídas e pendentes, ao
retomar: mostre a fila como está (o que já foi feito, o que falta) antes de
continuar — não assuma que a pessoa lembra onde parou.

## Relação com as outras skills

A fila nasce do que `me-entreviste` e `O combinado.md` já resolveram — não
é outra rodada de perguntas, é a tradução de decisões já tomadas em
trabalho executável. Se, ao montar a fila, aparecer uma decisão que ainda
não foi tomada, isso é sinal de que falta uma pergunta (`me-entreviste`)
antes de continuar — não invente a resposta só pra preencher a fila.
