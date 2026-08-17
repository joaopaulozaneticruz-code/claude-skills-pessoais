---
name: me-entreviste
description: Entreviste o usuário exaustivamente sobre cada aspecto de um plano ou projeto até chegar a um entendimento comum — percorrendo a árvore de decisões do projeto e resolvendo as dependências entre elas uma a uma, nunca em lote. Para cada decisão, apresente a resposta que você recomenda e peça confirmação; faça uma pergunta de cada vez, deixando a resposta anterior informar a próxima; se uma pergunta puder ser respondida explorando a base de código/arquivos existentes, explore em vez de perguntar. NÃO dispare proativamente para "elaborar uma ideia nova"/"planejar um projeto" — esse gatilho passou pra skill `brainstorming` (superpowers), ver decisão de 16/08/2026 abaixo. Invocável só diretamente, quando o usuário disser "me entrevista" ou "/me-entreviste" — nesse caso siga o processo normal (uma pergunta de cada vez, sempre com recomendação).
---

# Me entreviste

## Por que essa skill existe

Decisões tomadas cedo, com pouca informação, custam caro depois — a pessoa
que pediu isso já sentiu isso na pele o suficiente pra querer um hábito
deliberado de mapear o problema inteiro antes de avançar. O valor não está
em "fazer muitas perguntas" — está em não deixar nenhuma decisão real do
projeto sem dono até chegar a um entendimento em comum com a pessoa. Uma
pergunta genérica ("qual o público-alvo?") não faz isso; uma pergunta
específica, que já vem com uma recomendação e reconhece o que já foi dito
ou já é visível no código, faz.

## Quando disparar

*(Decisão de 16/08/2026: essa skill tinha um gatilho automático — "ideia
nova", "planejar projeto", "desenhar solução" — que colidia com a skill
`brainstorming` (superpowers), que reivindica exatamente o mesmo território
de forma obrigatória. O usuário escolheu ficar com `brainstorming` como
processo padrão pra esses casos. `me-entreviste` não dispara mais sozinha
— só por comando explícito.)*

Dispara **só** sob comando explícito: "me entrevista", "/me-entreviste".
Se o usuário pedir isso especificamente (em vez de deixar o `brainstorming`
tocar do jeito padrão dele), siga o processo normal desta skill abaixo.

## Como conduzir a entrevista

### 1. Monte a árvore de decisões antes de perguntar qualquer coisa

Antes de mapear do zero, veja se já existe um arquivo de acompanhamento
(seção abaixo) pra esse tema — as decisões já resolvidas nele saem da
árvore, você mapeia só o que falta.

Olhe pro plano/projeto e mapeie, pra você mesmo, quais são as decisões reais
que ainda precisam ser tomadas — não um checklist genérico, as decisões que
esse tema específico realmente levanta. Identifique as dependências entre
elas: quais decisões travam ou moldam outras (ex: escopo trava arquitetura,
arquitetura trava hospedagem). Ordene a entrevista por essa dependência —
resolva a raiz antes dos galhos, nunca pergunte algo cuja resposta pode
mudar de figura dependendo de uma decisão anterior ainda não tomada.

Esse mapa é seu, não precisa ser apresentado formalmente à pessoa — mas
nada impede de compartilhar se ajudar a situar onde a conversa está.

### 2. Para cada decisão, tente resolver sozinho antes de perguntar

Se existe uma base de código, arquivos de projeto, documentação (CLAUDE.md,
specs, configs) ou qualquer outra fonte já disponível, explore-a primeiro.
Muita coisa que pareceria uma pergunta de entrevista já está respondida no
que já existe: convenções em uso, decisões já registradas, schema atual,
dependências já instaladas. Só leve pra pessoa o que genuinamente depende
do julgamento, da preferência ou do conhecimento dela — não redescubra em
voz alta o que dá pra descobrir sozinho.

Se não há nada pra explorar (ideia nova, sem projeto/arquivos ainda), essa
etapa não se aplica — vá direto pra pergunta.

### 3. Pergunte uma decisão de cada vez, sempre com uma recomendação

- **Uma pergunta por vez.** Não empacote várias decisões independentes numa
  lista grande de uma vez só. Resolva uma, deixe a resposta dela informar
  (ou até eliminar) a próxima pergunta, e só então avance pro próximo galho
  da árvore. É uma conversa sequencial e adaptativa, não um formulário.
- **Sempre chegue com uma resposta recomendada.** Nunca pergunte em aberto
  sem ponto de vista — isso empurra trabalho de volta pra pessoa sem
  necessidade. Diga o que você recomendaria e por quê, e peça confirmação
  ou correção. Quando a decisão se resume a poucas opções discretas, use a
  ferramenta de pergunta com opções, marcando a recomendada como tal.
  Quando é uma decisão mais aberta (não cabe em 2-4 opções), proponha a
  resposta em texto corrido e pergunte se a pessoa concorda ou quer ajustar.
- **Critério de parada é entendimento comum, não quantidade.** Continue
  até esgotar as ramificações que realmente importam pra esse plano — pode
  ser 3 perguntas, pode ser muitas mais, dependendo de quanto da árvore já
  estava resolvido por contexto ou pela base de código.

### 4. Depois de cada resposta

- Se a resposta abrir uma ramificação nova que não estava mapeada, adicione
  ela à árvore antes de seguir — não ignore.
- Se algo ficou ambíguo ou contradiz uma decisão anterior, resolva isso
  antes de avançar — não empilhe incerteza.
- Ao esgotar a árvore, sintetize as decisões tomadas (pode ser um parágrafo
  curto) antes de seguir pro próximo passo do trabalho.
- Atualize o arquivo de acompanhamento (seção abaixo) com as decisões
  resolvidas nessa rodada.

### 5. Nas etapas seguintes do mesmo projeto

Quando perceber uma transição real de etapa (ex: o planejamento terminou e
a construção vai começar; um rascunho ficou pronto e entra em revisão; o
escopo mudou de forma relevante), **avise e pergunte antes** de percorrer a
árvore de decisões daquela etapa nova — algo como "chegamos numa etapa
nova aqui, quer que eu percorra as decisões dela antes de eu seguir?". Se a
pessoa disser que não, siga em frente sem insistir *nessa* transição — a
skill continua valendo pra próxima.

A árvore da etapa nova normalmente é menor: já existe contexto acumulado,
então ela mira só nas decisões que a etapa nova de fato levanta —
consultando o arquivo de acompanhamento e a base de código pra não
reperguntar terreno já coberto.

## Arquivo de acompanhamento

Pra não repetir decisão já resolvida entre rodadas, mantenha um arquivo
markdown por tema/projeto:

- Local: `entrevistas/<slug-do-tema>.md` dentro do diretório de trabalho
  atual (crie a pasta `entrevistas/` se não existir). Se a conversa não
  tiver um diretório de projeto claro (é só um brainstorm de chat, sem
  arquivos), não crie arquivo — mantenha o controle apenas na conversa.
- `<slug-do-tema>`: um nome curto derivado do assunto (ex: `boardgames-financeiro`,
  `campanha-lancamento-x`), estável entre rodadas do mesmo projeto.
- Formato: uma seção por rodada, com data, contexto da etapa, e as decisões
  resolvidas (pergunta, sua recomendação, e o que a pessoa decidiu — quando
  ela seguir a recomendação, basta anotar isso, não precisa repetir tudo).

```markdown
# Entrevistas — <nome do tema>

## Rodada 1 — 2026-08-14 (kickoff)
Contexto: início do projeto, ainda sem nada definido.

- Decisão: ...  →  Recomendei: ...  →  Ficou: ...
- Decisão: ...  →  Recomendei: ...  →  Ficou: ...

## Rodada 2 — 2026-08-20 (fim do planejamento → início da construção)
Contexto: escopo fechado, entrando em implementação.
...
```

## O que essa skill não é

Não é uma forma de adiar trabalho ou empurrar decisão pro usuário quando
você já tem informação suficiente (seja por contexto da conversa, seja pela
base de código) pra propor um caminho — nesses casos, proponha e peça só a
confirmação, não transforme isso numa pergunta aberta. E não é despejar uma
lista de perguntas de uma vez — é uma conversa sequencial, uma decisão por
vez, cada resposta moldando a próxima.
