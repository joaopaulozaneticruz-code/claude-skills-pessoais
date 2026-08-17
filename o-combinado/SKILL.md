---
name: o-combinado
description: Mantenha, em todo projeto onde decisões relevantes estejam sendo tomadas, um arquivo "O combinado.md" na raiz do projeto — um registro em linguagem humana (sem código, sem jargão técnico) do que foi decidido e, principalmente, do que o usuário já recusou que você faça. Atualize esse arquivo sempre que uma decisão relevante for tomada ou uma proposta sua for recusada, e sempre que o usuário pedir pra "salvar o projeto" (ou frases equivalentes: "salva tudo", "guarda isso", "registra isso"). Dispare esta skill de forma proativa nesses momentos, sem esperar o usuário pedir o arquivo explicitamente. Antes de propor algo relevante num projeto que já tem esse arquivo, leia a seção de recusas primeiro — não repita uma sugestão já recusada sem reconhecer que já foi recusada antes.
---

# O combinado

## Por que existe

Sem um registro, é fácil repropor algo que a pessoa já disse que não quer,
ou perder de vista por que uma decisão foi tomada daquele jeito. "O
combinado" existe pra isso: um lugar único, em linguagem simples, que
qualquer um — inclusive você numa sessão futura, sem memória da conversa
atual — consegue abrir e entender rápido o que já foi combinado e o que já
foi descartado. A parte das recusas importa tanto quanto (ou mais que) a
das decisões positivas: é o que evita repetir um erro de julgamento já
corrigido.

## Onde fica e como se chama

- Nome exato do arquivo: `O combinado.md`.
- Local: raiz do projeto (mesmo nível de README, CLAUDE.md, ou o arquivo de
  entrada principal do repositório, se existirem).
- Um arquivo por projeto. Não crie cópias em subpastas.
- Nasce na primeira decisão relevante do projeto — não precisa existir
  antes disso, e não precisa ser criado em conversas que não chegam a
  decidir nada de fato.

## Quando atualizar

- Sempre que uma decisão relevante for tomada (o usuário respondeu uma
  pergunta sua, aceitou uma proposta, ou escolheu entre alternativas).
- **Sempre que o usuário recusar algo que você propôs, perguntou ou
  sugeriu.** Esse é o gatilho mais importante dos três — uma recusa não
  registrada tende a virar a mesma sugestão de novo numa sessão futura.
- Quando o usuário pedir pra "salvar o projeto", ou usar uma frase
  equivalente ("salva tudo", "guarda isso", "registra isso", "não esquece
  disso") — nesse momento, revise o que mudou desde a última atualização e
  registre.
- Ao final de uma sessão de trabalho substancial no projeto, mesmo sem
  pedido explícito, se algo relevante mudou.

Não precisa registrar decisão trivial ou reversível sem consequência (nome
de variável, formatação) — o arquivo é sobre o que importa se for
esquecido, não uma ata literal de tudo que foi dito.

## Conteúdo: só linguagem humana

Sem blocos de código, sem nomes de função/classe/tabela citados como
referência técnica, sem trechos de configuração. Mesmo quando a decisão é
técnica, descreva o resultado e o porquê em prosa — o teste é: alguém sem
nenhum contexto técnico consegue ler o arquivo inteiro e entender o que
está combinado, mesmo sem saber programar.

Títulos e listas são bem-vindos (isso não é código, é organização) — o que
não pode é o conteúdo de um item virar sintaxe técnica.

Exemplo do teste: em vez de "RateioSocio.Valor recalcula quando a
Transacao é editada e Pago == false", escreva "quando uma despesa é
editada, a parte de quem ainda não pagou é recalculada — a de quem já
pagou fica como estava".

## Estrutura sugerida

Adapte ao projeto — isso é um ponto de partida, não um molde rígido:

```markdown
# O combinado — <nome do projeto>

## O que é
(1-3 frases — alguém que abre esse arquivo sem contexto nenhum entende do
que se trata.)

## Decisões
- <data> — <o que ficou decidido, e por quê, em uma ou duas frases>
- ...

## Já recusado (não repropor sem motivo novo)
- <data> — Propus/perguntei: <o quê>. Foi recusado porque: <motivo, se
  dito; senão, "sem motivo explicado"> .
- ...

## Pendente / em aberto
- <o que ainda não foi decidido, se fizer sentido registrar>
```

## Antes de propor algo novo

Se o projeto já tem `O combinado.md`, leia a seção de recusas antes de
sugerir algo. Se a ideia nova esbarrar numa recusa antiga, não finja que é
novidade — diga algo como "sei que isso já foi descartado antes por X, mas
acho que vale reconsiderar porque Y mudou" (ou não sugira, se não houver
razão nova). Isso vale tanto quando você está montando a proposta quanto
quando o usuário pedir sua opinião sobre algo.

## Relação com outros arquivos do projeto

Não substitui documentação técnica (CLAUDE.md, specs, schema) — essa
continua existindo e sendo técnica, é referência de como o código funciona.
"O combinado.md" é o espelho em linguagem humana das decisões e recusas, um
documento diferente com um público diferente (a pessoa, não uma sessão
futura tentando entender o código).

Se o projeto já tiver algum arquivo cumprindo parte desse papel (ex: um
resumo de progresso, uma ata, notas de decisão), consolide o conteúdo
relevante dele em `O combinado.md` — reescrevendo em linguagem humana onde
for técnico demais — e avise a pessoa que os conteúdos foram unidos, em vez
de manter dois documentos cobrindo o mesmo território.
