---
name: doc-system-governance
description: Create, normalize, and maintain a layered project documentation system centered on `doc/` or an existing equivalent such as `docs/`. Use when Codex needs to bootstrap project docs, create or repair a `doc/` tree, reorganize mixed or catch-all documentation by ownership boundary, migrate product/architecture/design/engineering/AI content into separate layers, establish AI task-log-context records, or keep project documentation aligned after feature, architecture, UI, workflow, testing, release, or agent-process changes. Trigger on requests about documentation systems, doc governance, doc restructuring, doc taxonomy, project knowledge organization, or AI-maintainable project records. Do not use for ordinary single-file prose edits that do not materially affect the documentation system.
---

# Doc System Governance

Create a documentation system that separates stable project truth from execution history and keeps each fact in one primary home. Keep the system small, explicit, and maintainable by later agents.

Read [references/doc-system-rules.md](references/doc-system-rules.md) before substantial documentation work. Read [references/file-templates.md](references/file-templates.md) only when creating missing core files.

## Workflow

### 1. Inspect before editing

Check for:

- existing `doc/`, `docs/`, or another established documentation root
- mixed catch-all documents that combine product, architecture, design, engineering, or task history
- missing owner-layer files
- duplicated rules across files

Preserve an established project convention unless there is a strong reason to change it.

### 2. Route every fact to one owner

Use this default routing:

- product scope, feature intent, business rules -> `product/`
- technical boundaries, modules, interfaces, data ownership -> `architecture/`
- user-visible behavior, UI states, interaction rules -> `design/`
- setup, testing, release, troubleshooting, contributor workflow -> `engineering/`
- agent workflow, task records, decisions, current AI context -> `ai/`

If a change touches multiple layers, update the primary owner first and only the minimum downstream documents that truly changed.

### 3. Bootstrap minimally

If the project lacks a usable documentation system, create the minimum useful structure first:

```text
doc/
  README.md
  product/
  architecture/
  design/
  engineering/
  ai/
```

Do not create a large empty tree without evidence that the project needs it.

### 4. Repair legacy docs by extraction

When a mixed legacy document exists:

- treat it as source material
- extract content into owner documents
- reduce the old file into an index, stub, or deprecation note after replacements exist

Do not keep expanding the mixed document as the long-term source of truth.

### 5. Maintain the system during normal work

When project changes happen:

- update the owning layer first
- update only the minimum dependent docs
- avoid repeating the same explanation in multiple files

Prefer gradual cleanup over disruptive rewrites unless the user asked for a broad reorganization.

## AI Record Rules

Keep execution history separate from stable truth.

- `ai/AI_CONTEXT.md` stays short and current
- `ai/DEV_LOG.md` stays a concise recent-work index, not a transcript dump
- `ai/tasks/` keeps one file per task with full execution detail
- `ai/decisions/` stores durable decisions that should stay visible
- `Context Delta` belongs in task files only when the task changes durable project memory, workflow, ownership, or follow-up expectations

If a follow-up item matters beyond the finished task, explicitly decide whether it should be promoted into `AI_CONTEXT.md`, `decisions/`, `KNOWN_ISSUES.md`, or `ROADMAP.md`.

## Output Expectations

For bootstrap or repair requests, usually produce:

- a minimal documentation backbone if missing
- core owner-layer files where the project genuinely needs them
- migrated content in the correct layer
- reduced dependence on mixed catch-all documents
- AI-maintainable workflow, log, and task structure when the project has ongoing agent work

For ordinary maintenance after project changes:

- update only the affected owner-layer docs
- keep file boundaries clean
- avoid reintroducing mixed specification files
