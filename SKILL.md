---
name: doc-system-governance
description: Use when a project needs a structured documentation system, when existing docs need to be reorganized by ownership boundary, or when a task explicitly includes documentation-system maintenance across product, architecture, design, engineering, or ai records. This skill covers both initial doc-system creation and ongoing governance, but should not be used for ordinary single-file prose edits or routine code changes that do not materially affect the documentation system.
---

# Doc System Governance

This skill creates, repairs, and maintains a project documentation system centered on `doc/`.

Use it for both:

- first-time documentation-system bootstrap
- later documentation maintenance after project changes

Read [references/doc-system-rules.md](references/doc-system-rules.md) before substantial documentation work.

Read [references/file-templates.md](references/file-templates.md) when creating missing core files.

## When To Use

Use this skill when the user asks to:

- create a project documentation system
- standardize or reorganize existing docs
- split mixed documents into clearer layers
- update project docs after feature, architecture, UI, workflow, or release changes when the task materially affects documentation-system truth
- establish AI-friendly task, log, context, or decision records

Do not use this skill for ordinary single-file prose edits that do not affect the doc system.

## Core Model

The default documentation backbone is:

```text
doc/
  README.md
  product/
  architecture/
  design/
  engineering/
  ai/
```

These layers mean:

- `product` = what the product is, what features exist, what business rules hold
- `architecture` = how the system is structured technically
- `design` = how users interact with the system
- `engineering` = how the project is developed, tested, packaged, released, and operated
- `ai` = how AI agents collaborate and how task history/current context are recorded

## Workflow

### 1. Inspect Before Editing

First inspect the current documentation state:

- existing `doc/` or equivalent folders
- mixed catch-all docs
- missing owner-layer docs
- duplicated rules across layers

### 2. Route By Ownership

Before editing any content, decide its primary owner:

- product capability or business rule -> `product`
- technical structure or interface boundary -> `architecture`
- interaction or visible behavior -> `design`
- setup, testing, packaging, release, troubleshooting -> `engineering`
- agent workflow, task history, durable work decisions, current agent context -> `ai`

Each fact should have one primary home.

### 3. Bootstrap Minimally

If the project has no proper doc system, create the minimum useful structure first.

Do not create a large empty tree unless the project actually needs it.

Start with the backbone and the smallest set of core files.

### 4. Maintain The System During Normal Work

When a project change happens, update the owning layer first, then only the minimum downstream documents that truly changed.

Do not duplicate the same full explanation across multiple files.

### 5. Reduce Mixed Legacy Docs

If a mixed legacy doc exists:

- treat it as source material
- extract content into owner documents
- shrink the legacy doc into an index, stub, or deprecation note after replacements exist

Do not keep expanding the mixed doc.

## Required Maintenance Behaviors

When this skill is active, the agent should preserve these rules:

- `AI_CONTEXT.md` stays short and current
- `DEV_LOG.md` stays a concise index, not a transcript dump
- `DEV_LOG.md` may retain a continuous recent work thread across month boundaries when the same work phase is still active
- task-level detail goes into one file per task
- task files should include a `Context Delta` section when the task changes durable project memory, introduces follow-up work, or changes rules, structure, or responsibilities
- durable conclusions go into decisions, not only logs
- stable truth and temporary execution history stay separated

## Change Routing

Use this default routing:

- product rule or feature-scope change -> update `product`
- interaction change -> update `design`
- technical boundary change -> update `architecture`
- contributor workflow / testing / packaging / release change -> update `engineering`
- agent workflow or task-tracking change -> update `ai`

Cross-layer updates are allowed, but they should be minimal and intentional.

## Output Expectations

When asked to establish or repair the doc system, the agent should usually produce:

- the required `doc/` backbone if missing
- core owner-layer files if missing
- migrated or reorganized content in the correct layer
- reduced reliance on mixed catch-all documents
- AI-maintainable task/log/context structure where relevant

When asked to maintain docs after ordinary project changes, the agent should:

- update only the affected owner-layer docs
- keep file boundaries clean
- avoid reintroducing mixed specification files
