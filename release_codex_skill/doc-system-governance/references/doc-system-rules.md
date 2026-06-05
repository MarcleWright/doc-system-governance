# Doc System Rules

Use this reference when the task materially affects a project's documentation system.

## Contents

1. Objective
2. Backbone
3. Ownership model
4. Core files
5. Maintenance rules
6. AI records
7. Naming
8. Quality check

## 1. Objective

Create and maintain a structured documentation system that:

- supports both humans and AI agents
- separates stable truth from temporary execution records
- avoids catch-all documents
- stays small enough to maintain

## 2. Backbone

Unless the repository already has a strong convention, prefer:

```text
doc/
  README.md
  product/
  architecture/
  design/
  engineering/
  ai/
```

If the repository already uses `docs/` or another clear equivalent, preserve that convention unless there is a strong reason to change it.

## 3. Ownership model

Route each fact to one primary home:

- `product/`: product purpose, target users, feature scope, business rules, acceptance-oriented requirements, non-goals
- `architecture/`: module boundaries, interfaces, data ownership, structural decisions, technical constraints
- `design/`: user flows, visible states, interaction rules, UI behavior
- `engineering/`: setup, testing, packaging, release, troubleshooting, contributor workflow
- `ai/`: AI workflow rules, current context, task records, decisions, logs

Do not make one document the source of truth for multiple ownership layers.

## 4. Core files

Create only the files the project actually needs. Common starting points:

```text
doc/
  README.md
  product/
    PRODUCT_BRIEF.md
    PRODUCT_REQUIREMENTS.md
    ROADMAP.md
  architecture/
    ARCHITECTURE_OVERVIEW.md
    DATA_MODEL.md
  design/
    UI_GUIDE.md
    INTERACTION_RULES.md
  engineering/
    DEV_SETUP.md
    TESTING.md
    KNOWN_ISSUES.md
  ai/
    AI_CONTEXT.md
    AI_WORKFLOW.md
    DEV_LOG.md
    tasks/
    decisions/
    logs/
```

## 5. Maintenance rules

Follow these rules when editing docs:

- Each important fact has one primary owner document.
- Cross-layer updates are allowed, but keep them minimal and intentional.
- Do not introduce new catch-all specs that mix product, architecture, design, engineering, and task history.
- For legacy mixed docs, extract content into owner files first, then shrink the old file into an index, stub, or deprecation note.
- Stable truth belongs in `product/`, `architecture/`, `design/`, and `engineering/`; execution history belongs in `ai/`.

Default routing for changes:

- product capability or business rule change -> `product/`
- interaction or UI behavior change -> `design/`
- technical structure or interface change -> `architecture/`
- setup, testing, packaging, release, or workflow change -> `engineering/`
- agent workflow or task-tracking change -> `ai/`

## 6. AI records

Use these boundaries:

- `AI_CONTEXT.md`: short current-phase context only
- `DEV_LOG.md`: concise recent-work index
- `tasks/`: one file per task with execution detail
- `decisions/`: durable decisions that should remain visible
- `logs/`: archived summaries

Task files should include `Context Delta` when the task changes durable project memory, responsibilities, rules, or follow-up obligations.

If `Context Delta` contains a follow-up that matters beyond the closed task, explicitly classify whether it should be promoted into `AI_CONTEXT.md`, `decisions/`, `KNOWN_ISSUES.md`, or `ROADMAP.md`.

## 7. Naming

Use clear, stable filenames.

Recommended patterns:

```text
ai/tasks/YYYY-MM-DD_nn_short-task-name.md
ai/decisions/ADR-0001_short-title.md
```

Use `nn` as the sequence number for that day only.

## 8. Quality check

Before finishing, verify:

1. Every active document has a clear owner layer.
2. No new catch-all spec was introduced.
3. Stable truth and execution history remain separated.
4. `AI_CONTEXT.md` is short and current.
5. `DEV_LOG.md` remains concise.
6. Durable conclusions are not buried only inside task files.
