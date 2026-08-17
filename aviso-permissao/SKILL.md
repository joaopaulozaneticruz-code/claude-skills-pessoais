---
name: aviso-permissao
description: Sempre que você estiver prestes a rodar um comando (Bash ou PowerShell) que não está na lista de permissões liberadas do projeto — ou seja, que provavelmente vai parar esperando aprovação do usuário — dispare uma notificação (ferramenta PushNotification) descrevendo o comando pendente, na mesma resposta em que você chama esse comando. Isso é pra o usuário ouvir/ver mesmo estando longe do computador. NÃO dispare para perguntas de múltipla escolha (AskUserQuestion) — só para comandos de terminal que ficam esperando permissão. Isso já foi pedido explicitamente pelo usuário, então não precisa de julgamento extra sobre "vale a pena notificar" — dispare sempre que esse gatilho específico acontecer.
---

# Aviso de permissão pendente

## Por que existe

O usuário se afasta do computador enquanto o trabalho roda, e quer saber na
hora em que algo trava esperando a aprovação dele — não só descobrir isso
minutos (ou horas) depois, quando volta e vê a sessão parada. `PushNotification`
manda um aviso de desktop (com som) e, se o Remote Control estiver
conectado, também no celular — exatamente o alcance que "mesmo estando
longe do computador" pede.

## Quando disparar

Só um gatilho: **um comando de terminal (Bash ou PowerShell) que vai
provavelmente pedir permissão** — ou seja, que não está coberto por uma
regra de `permissions.allow` já liberada no `.claude/settings.json` do
projeto atual. Antes de chamar um comando assim, verifique mentalmente se
ele bate com algum padrão já liberado; se não bater, é candidato a
notificação.

**Não dispara para**: perguntas de múltipla escolha (`AskUserQuestion`),
nem para comandos que já estão cobertos pela lista de permissões (esses
rodam direto, sem parar esperando nada).

## Como disparar

Chame `PushNotification` (`status: "proactive"`) na mesma resposta em que
você vai chamar o comando pendente — não espere o resultado do comando pra
só então notificar, porque nesse ponto o usuário já pode estar esperando a
aprovação sem saber.

A mensagem deve dizer o que está pendente, curta e direta (a ferramenta já
limita a 200 caracteres): o que é o comando, não só "preciso de permissão".

**Exemplo:**
Comando pendente: `git push origin master`
Mensagem: `"Esperando permissão pra dar git push no Boar D Games."`

**Exemplo:**
Comando pendente: `dotnet ef database update`
Mensagem: `"Esperando permissão pra aplicar migration no banco do Boar D Games."`

## Uma observação sobre julgamento

A ferramenta `PushNotification` normalmente pede pra usar com moderação
("erre pro lado de não notificar"), porque notificação desnecessária cansa.
Mas esse gatilho específico já foi pedido explicitamente pelo usuário — ele
sabe o custo e quer exatamente esse aviso toda vez que rolar. Não precisa
reavaliar "será que vale a pena" a cada vez; a decisão já foi tomada.
