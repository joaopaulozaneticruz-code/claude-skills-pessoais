---
name: documentacao-viva
description: Antes de qualquer commit em um projeto de desenvolvimento de código (qualquer projeto, não só este) — dispare isso como parte do fluxo de commit, mesmo sem o usuário pedir, antes de finalizar o commit. Mantenha dois documentos técnicos vivos na raiz do projeto (ou onde já existir convenção de docs): (1) um diagrama UML de classes em mermaid, refletindo os models/entidades/relações atuais do código, e (2) uma documentação padrão do que o projeto é e como está construído hoje (arquitetura, stack, funcionalidades implementadas, endpoints/API, como rodar). Compare o estado atual do código com os dois documentos; se algo estrutural (classe/campo/relação nova) ou funcional (feature, endpoint, fluxo novo) mudou desde a última atualização, atualize o(s) documento(s) afetado(s) e inclua no mesmo commit. Se nenhum dos dois existir ainda, crie os dois refletindo o estado atual antes do primeiro commit em que isso for notado. Não dispare em toda edição de arquivo — só no momento do commit. Diferente de "o-combinado" (linguagem humana, decisões e recusas): aqui o público é técnico e o conteúdo é sobre como o sistema funciona hoje, não sobre por que uma decisão foi tomada.
---

# Documentação viva

## Por que existe

Documentação técnica que só é escrita uma vez, no começo do projeto, fica
desatualizada rápido — e documentação desatualizada é pior que nenhuma,
porque engana com confiança. Esta skill existe pra manter dois artefatos
técnicos sempre sincronizados com o código real, verificando-os no único
momento em que faz sentido parar pra isso: antes de cada commit, quando o
trabalho já está numa forma estável o suficiente pra descrever.

## Os dois documentos

### 1. UML — diagrama de classes

- Sintaxe mermaid (` ```mermaid classDiagram `), dentro de um arquivo `.md`
  versionado no git — texto puro, dá diff, não precisa de ferramenta extra
  pra visualizar (GitHub e a maioria dos editores renderizam mermaid nativo
  em markdown).
- Nome sugerido: `UML.md` na raiz do projeto — mas se o projeto já tem uma
  pasta `docs/` estabelecida, use `docs/UML.md` lá em vez de criar uma
  convenção nova.
- Escopo: as classes/entidades que formam o **domínio** do projeto — models,
  entidades de banco, DTOs centrais quando relevantes. Não diagrame
  componentes de UI, helpers, ou classes de infraestrutura genérica (isso
  vira ruído, não visão geral). Inclua atributos com tipo (`nome: tipo`) e
  relações com cardinalidade quando der pra saber (`"1" --> "*"`).
- Gatilho de atualização: mudança **estrutural** desde o último commit —
  classe/model novo ou removido, campo adicionado ou removido, relação nova
  ou alterada entre entidades, endpoint/interface que muda o contrato.

### 2. Documentação padrão

- Nome sugerido: `Documentacao.md` na raiz (mesmo critério de local do
  UML — siga a convenção de pasta `docs/` se já existir uma).
- Público técnico — ao contrário de `O combinado.md`, pode e deve citar
  nomes de classe, endpoint, tabela, tecnologia. Não é o mesmo documento.
- Estrutura sugerida (adapte ao projeto, não é molde rígido):

```markdown
# Documentação — <nome do projeto>

## O que é
(1-3 frases técnicas — o que o sistema faz e pra quem.)

## Arquitetura
Stack, camadas, como as partes se conectam (front, API, banco). Pode
referenciar o CLAUDE.md do projeto se as decisões de stack já estiverem
documentadas lá, em vez de duplicar.

## Funcionalidades implementadas
Lista do que já existe e funciona **hoje** — estado atual, não changelog
datado. Quando uma feature muda de comportamento, atualize a entrada em
vez de acrescentar uma nova.

## Modelo de dados / API
Visão geral textual; para o detalhe estrutural, aponte para `UML.md` em
vez de duplicar o diagrama aqui.

## Como rodar localmente
Passos práticos — comando de build, de start, variáveis de ambiente
necessárias.
```

- Gatilho de atualização: mudança **funcional** relevante desde o último
  commit — feature nova, endpoint novo ou removido, fluxo que mudou de
  comportamento, forma de rodar o projeto que mudou. Não precisa atualizar
  por causa de um ajuste visual ou de texto que não muda o que está descrito
  no documento.

## Quando disparar

Antes de finalizar qualquer commit num projeto de código — dispare
proativamente como parte do fluxo de commit, mesmo sem o usuário pedir.
Não é pra rodar a cada edição de arquivo; é um checkpoint único, no momento
do commit, olhando pra tudo que mudou desde o commit anterior.

## Passo a passo

1. Antes de montar o commit, olhe o diff acumulado desde o último commit
   (`git diff`/`git status` do que está sendo commitado).
2. Pergunte: alguma mudança aí é estrutural (afeta o UML) ou funcional
   (afeta a documentação padrão)? Se nenhuma das duas, siga pro commit sem
   mexer nos documentos.
3. Se os arquivos ainda não existem no projeto e a mudança que está sendo
   commitada já é significativa o suficiente pra valer a pena documentar,
   crie os dois do zero refletindo o estado atual do projeto (não só o
   diff — o projeto inteiro), avisando o usuário que criou.
4. Se já existem, edite só as seções afetadas — não reescreva o documento
   inteiro a cada commit.
5. Inclua os documentos atualizados no mesmo commit que motivou a mudança,
   não em um commit separado depois.

## Relação com outras skills

- `o-combinado` continua sendo o registro em linguagem humana de decisões e
  recusas — não sobrepõe esta skill, que é técnica. Um projeto pode (e
  frequentemente vai) ter os três documentos: `O combinado.md`, `UML.md` e
  `Documentacao.md`, cada um com um público e propósito diferente.
- `criterios` já manda fazer commit como passo final de qualquer tarefa
  implementada — esta skill se encaixa logo antes desse passo, como parte
  do mesmo fluxo de fechamento de tarefa.
