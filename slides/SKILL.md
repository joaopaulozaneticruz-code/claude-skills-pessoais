---
name: slides
description: Create strategic HTML presentations with Chart.js, design tokens, responsive layouts, copywriting formulas, and contextual slide strategies.
argument-hint: "[topic] [slide-count]"
metadata:
  author: claudekit
  version: "1.0.0"
---

# Slides

Strategic HTML presentation design with data visualization.

*(Nota de roteamento — 16/08/2026: existem duas outras implementações de
slides no ambiente. A skill `design` tem um bloco "Slides" embutido que usa
os mesmos `references/slides-*.md` — dispara quando você já está dentro do
fluxo unificado dela (ex: pedindo logo + CIP + apresentação juntos). A skill
`design-system` tem um "Slide System" mais robusto (busca BM25, CSVs de
estratégia/emoção, validação de conformidade com brand tokens, comando
`/slides:create`) — prefira aquela quando a apresentação precisa seguir
`brand-guidelines.md`/`design-tokens.css` à risca. Esta skill (`slides`) é o
atalho mais direto: peça uma apresentação sem contexto de marca ou de outro
fluxo já em andamento, ela serve bem.)*

## When to Use

- Marketing presentations and pitch decks
- Data-driven slides with Chart.js
- Strategic slide design with layout patterns
- Copywriting-optimized presentation content

## Subcommands

| Subcommand | Description | Reference |
|------------|-------------|-----------|
| `create` | Create strategic presentation slides | `references/create.md` |

## References (Knowledge Base)

| Topic | File |
|-------|------|
| Layout Patterns | `references/layout-patterns.md` |
| HTML Template | `references/html-template.md` |
| Copywriting Formulas | `references/copywriting-formulas.md` |
| Slide Strategies | `references/slide-strategies.md` |

## Routing

1. Parse subcommand from `$ARGUMENTS` (first word)
2. Load corresponding `references/{subcommand}.md`
3. Execute with remaining arguments
