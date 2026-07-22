---
name: doc-system-governance
description: Use when a project needs a structured documentation system, when existing docs need to be reorganized by ownership boundary, or when a task explicitly includes documentation-system maintenance across product, architecture, design, engineering, material, or ai records. Also use as a low-token end-of-task documentation impact gate to decide whether to skip docs, update ai/DEV_LOG.md with optional ai/AI_CONTEXT.md compression, run full documentation governance, or, only when explicitly requested, create/maintain a long-task self-loop execution document or reviewer conclusion record that preserves multi-round task context, review, validation, and local commit rhythm. Do not use for ordinary single-file prose edits or routine code changes unless they materially affect project documentation truth, current AI handoff context, task history, local reference material handling, an active long-task execution loop, or a task review record.
---

# Doc System Governance

This skill creates, repairs, and maintains a project documentation system centered on `doc/`.

Use it for both:

- first-time documentation-system bootstrap
- later documentation maintenance after project changes

Start with the fast gate below. Read [references/doc-system-rules.md](references/doc-system-rules.md) only before substantial documentation work or when the gate selects full governance.

Read [references/file-templates.md](references/file-templates.md) when creating missing core files.

Read [references/file-templates.md](references/file-templates.md) when the user explicitly asks to create or update a "long-task self-loop execution" document, "长任务自循环执行" document, execution loop, or equivalent multi-round task-control record.

Read [references/file-templates.md](references/file-templates.md) when the user explicitly asks to create or update a `task_review` reviewer conclusion record for a long-task execution loop.

## Fast Gate

Before loading reference files or inspecting the whole doc tree, classify the current task:

1. **Skip docs** when the change is a local code fix, small prose edit, formatting cleanup, dependency bump, or experiment that does not change stable project truth, current AI handoff context, task history, user-visible behavior, architecture, workflow, setup, testing, release, or follow-up work.
2. **Light AI maintenance** when there was a substantive project change but no broader documentation layer changed. Update `DEV_LOG.md` by default, update a task file when detail is worth preserving, and update `AI_CONTEXT.md` only when the compressed current context for the next AI agent changed.
3. **Full governance** when the change creates or repairs the doc system, reorganizes ownership boundaries, touches multiple documentation layers, changes product behavior, architecture, design, engineering workflow, durable decisions, or exposes stale/mixed documentation that must be split.
4. **Long-task self-loop execution** only when the user explicitly asks to create or maintain a document for multi-round autonomous task execution, especially wording such as "创建长任务自循环执行文档", "create self-loop execution document", "create execution loop md", or "落一个 execution-loop 文档". This is an AI workflow record under `doc/ai/tasks/` and normally combines task sequencing, review cadence, validation rules, documentation maintenance, and local commit requirements. When the user explicitly wants an independent reviewer conclusion record, use `doc/ai/task_review/`.

Default to the lightest class that preserves correctness. If unsure between skip and light maintenance, check only `doc/ai/DEV_LOG.md`, `doc/ai/AI_CONTEXT.md`, and the relevant task file before deciding. If unsure between light maintenance and full governance, read `references/doc-system-rules.md`.

Use these quick questions:

- Did this task make a substantive change that should appear in `DEV_LOG.md`?
- Would the next AI agent misunderstand the current active project state without changing the compressed `AI_CONTEXT.md`?
- Did the change alter stable product, architecture, design, engineering, or AI workflow truth?
- Did it create follow-up work, durable constraints, or a decision that should not live only in chat?

If all answers are no, skip documentation maintenance and say so briefly in the final response.

### Long-Task Self-Loop Execution

Use this path when a task is too large for one implementation pass and the user wants the agent to continue through ordered sub-tasks with review, documentation maintenance, and commits.

Do not create this document as an automatic side effect of ordinary task planning, task review, documentation governance, or sub-task decomposition. In those cases, the agent may mention that an execution-loop document could help, but must not create it unless the user asks for it.

Before creating the document, confirm that one of these is true:

- a parent task and ordered sub-task list already exist
- the user explicitly asked the agent to split the parent task into sub-tasks and create the execution-loop document in the same request

If neither is true, create or review the parent/sub-task plan first and wait for explicit direction before creating the execution-loop document.

Create or update one execution-control document under `doc/ai/tasks/`, usually named:

```text
YYYY-MM-DD_nn_execution-loop.md
```

If it controls a numbered parent task, include the parent identifier in the name, for example:

```text
YYYY-MM-DD_03_execution-loop.md
```

The execution document should make the loop explicit enough that a future agent can resume after context loss:

- read the execution document, parent task, and current sub-task before each round
- inspect current code and task status before editing
- implement only the current sub-task scope
- run the agreed automated checks unless the document explicitly defers a class of checks
- review the diff before closing the round
- update the current task file with execution notes, reviewer notes, final result, and `Context Delta` when durable context changed
- when an independent reviewer is assigned, have the agent acting as `Reviewer` write the reviewer conclusion under `doc/ai/task_review/` and link it from the execution document and reviewed task
- update `DEV_LOG.md` and `AI_CONTEXT.md` only when the normal governance rules require it
- reread the parent task before selecting the next sub-task
- make exactly one local commit per completed sub-task unless the user requests otherwise
- do not push unless explicitly asked

The execution document must also preserve:

- the ordered sub-task list and current status
- parent/sub-task naming, where a numbered parent task such as `16` uses lettered child tasks such as `16A`, `16B`, `16C`, and so on
- non-goals and scope boundaries
- validation command list
- manual test deferrals and who owns them
- known follow-ups that must not be mixed into the current loop
- a ledger of completed rounds with commit hashes when available
- reviewer conclusion links when separate review records are used

When creating a long-task self-loop document, add lightweight references from the parent task and relevant sub-task files so future agents can find the control document quickly. Do not duplicate the full loop policy into every sub-task.

### Light AI Maintenance

Use this path for normal task completion when documentation impact is real but narrow.

- Update `DEV_LOG.md` for substantive changes; keep it as a concise milestone index, not a transcript.
- Treat `AI_CONTEXT.md` as a compressed recent/current context cache. Update it only when priorities, constraints, active decisions, suggested read order, or near-term follow-up context changed.
- Put detailed execution notes in one task file when detail is worth preserving.
- Add `Context Delta` only when the task changes durable memory, follow-up work, rules, structure, or responsibilities.
- Do not read or rewrite product, architecture, design, or engineering docs unless the fast gate says their stable truth changed.

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
  material/
  ai/
```

These layers mean:

- `product` = what the product is, what features exist, what business rules hold
- `architecture` = how the system is structured technically
- `design` = how users interact with the system
- `engineering` = how the project is developed, tested, packaged, released, and operated
- `material` = local or temporary user-provided reference material used during work; default to not pushing its contents to the remote unless explicitly promoted
- `ai` = how AI agents collaborate and how task history/current context are recorded

## Workflow

### 1. Run The Fast Gate

Classify the task as skip docs, light AI maintenance, or full governance before doing broad inspection.

For skip docs, do not touch documentation.

For light AI maintenance, inspect `doc/ai/DEV_LOG.md`, then inspect `doc/ai/AI_CONTEXT.md` only if current compressed context may need to change, plus the relevant task record if needed.

For full governance, continue with the full workflow.

### 2. Inspect Before Editing

First inspect the current documentation state:

- existing `doc/` or equivalent folders
- mixed catch-all docs
- missing owner-layer docs
- duplicated rules across layers

### 3. Route By Ownership

Before editing any content, decide its primary owner:

- product capability or business rule -> `product`
- technical structure or interface boundary -> `architecture`
- interaction or visible behavior -> `design`
- setup, testing, packaging, release, troubleshooting -> `engineering`
- local user-provided references, source documents, screenshots, research snippets, or temporary inputs -> `material`
- agent workflow, task history, durable work decisions, current agent context -> `ai`

Each fact should have one primary home.

### 4. Bootstrap Minimally

If the project has no proper doc system, create the minimum useful structure first.

Do not create a large empty tree unless the project actually needs it.

Start with the backbone and the smallest set of core files.

### 5. Maintain The System During Normal Work

When a project change happens, update the owning layer first, then only the minimum downstream documents that truly changed.

Do not duplicate the same full explanation across multiple files.

### 6. Reduce Mixed Legacy Docs

If a mixed legacy doc exists:

- treat it as source material
- extract content into owner documents
- shrink the legacy doc into an index, stub, or deprecation note after replacements exist

Do not keep expanding the mixed doc.

## Required Maintenance Behaviors

When this skill is active, the agent should preserve these rules:

- `AI_CONTEXT.md` stays short and current
- `DEV_LOG.md` stays a concise index, not a transcript dump
- `DEV_LOG.md` may use structured phase entries with `Status`, short `Summary`, and task links when that improves handoff clarity, but it should still remain a concise index
- `DEV_LOG.md` may retain a continuous recent work thread across month boundaries when the same work phase is still active
- task-level detail goes into one file per task
- task files should include a `Context Delta` section when the task changes durable project memory, introduces follow-up work, or changes rules, structure, or responsibilities
- durable conclusions go into decisions, not only logs
- stable truth and temporary execution history stay separated
- all generated or edited documentation files must be written as `UTF-8`, preferably `UTF-8 without BOM`
- `.md`, `.txt`, `.json`, `.yml`, `.yaml`, and all task, execution, review, dev log, and AI context documents must be saved as `UTF-8`
- never rely on system default encoding, ANSI, GBK, GB2312, or editor default save encoding
- on Windows, any script or command that writes files must explicitly choose `UTF-8`
- use conservative document characters by default: allow Chinese text when needed, prefer ASCII punctuation, prefer plain `"` and `'`, and avoid smart quotes or unnecessary special Unicode punctuation
- inspect new or modified documents for mojibake or encoding corruption before delivery; if corruption is found, fix it before handoff
- if existing documents contain encoding damage, apply the smallest semantic repair that removes the corruption without rewriting unrelated content

## Change Routing

Use this default routing:

- product rule or feature-scope change -> update `product`
- interaction change -> update `design`
- technical boundary change -> update `architecture`
- contributor workflow / testing / packaging / release change -> update `engineering`
- local or temporary reference input -> store under `material`; promote only stable conclusions to the owning product, architecture, design, engineering, or ai layer
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
