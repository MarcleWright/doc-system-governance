# Doc System Rules

Use this document as the sole instruction for an AI agent to create and maintain a project documentation system.

This is a generic specification.

It is intentionally not specialized for any single repository, stack, product type, or workflow.

## 1. Objective

Create and maintain a structured `doc/` system for the current project.

The documentation system must:

- support human readers and AI agents
- separate stable truth from temporary execution records
- avoid mixed catch-all documents
- remain maintainable over time
- support project continuity across sessions or contributors

## 2. Core Principle

`doc/` is not a passive file dump.

It is an active project knowledge system.

Every document must have a clear responsibility boundary.

## 3. Default Top-Level Structure

Unless the project already has a strong established convention, prefer this structure under `doc/`:

```text
doc/
  README.md

  product/
  architecture/
  design/
  engineering/
  ai/
```

These five areas are the default system backbone.

If the project already uses an established equivalent such as `docs/`, preserve that convention unless there is a strong reason to change it.

Sub-files and subfolders may be created as needed, but must respect the ownership rules in this document.

## 4. Top-Level Ownership Rules

### 4.1 `product`

Purpose:

- define what the product is
- define who it is for
- define what problems it solves
- define feature scope and business rules

Belongs here:

- product purpose
- target users
- feature definitions
- business constraints
- acceptance-oriented product rules
- roadmap priorities
- non-goals

Does not belong here:

- implementation details
- code structure
- technical module boundaries
- low-level UI rendering details
- setup, packaging, or release procedures
- task logs

### 4.2 `architecture`

Purpose:

- define how the system is structured technically
- define module and service boundaries
- define data flow and ownership
- define interface and integration boundaries

Belongs here:

- architecture overview
- module responsibilities
- data model
- system boundaries
- internal or external interface boundaries
- major structural decisions

Does not belong here:

- step-by-step contributor instructions
- temporary task execution notes
- product scope prose
- long-form release operation records

### 4.3 `design`

Purpose:

- define how the product behaves for users
- define interaction behavior and UI rules

Belongs here:

- UI structure
- user flows
- interaction rules
- component behavior
- visible states
- modal/menu/inline decisions

Does not belong here:

- business scope definitions already owned by product
- code/module explanations already owned by architecture
- release and setup instructions

### 4.4 `engineering`

Purpose:

- define how the project is developed, tested, packaged, released, and operated

Belongs here:

- setup instructions
- testing instructions
- contributor workflow instructions
- release instructions
- packaging instructions
- known issues
- troubleshooting guidance

Does not belong here:

- product definition
- architecture as primary system truth
- task history
- temporary planning records

### 4.5 `ai`

Purpose:

- define how AI agents collaborate on the project
- store AI-oriented execution records
- preserve current working context and durable work decisions

Belongs here:

- AI workflow rules
- AI current context
- task records
- decision records
- log indexes and archives

Does not belong here:

- stable product truth
- full architecture substitute
- general engineering instructions

## 5. Recommended Initial Files

The agent should create a minimal but usable initial set.

Recommended default files:

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

Additional files may be added only when the project actually needs them.

Do not create large empty trees without a concrete purpose.

## 6. File Responsibility Guidance

### 6.1 `README.md`

Role:

- entry point into the documentation system
- explain where different kinds of knowledge live

### 6.2 `PRODUCT_BRIEF.md`

Role:

- stable product identity

Typical contents:

- purpose
- target users
- core value
- core workflows
- non-goals

### 6.3 `PRODUCT_REQUIREMENTS.md`

Role:

- stable feature and business rule contract

Typical per-feature contents:

- goal
- user value
- scope
- rules
- acceptance criteria
- non-goals

### 6.4 `ROADMAP.md`

Role:

- priorities and future direction

### 6.5 `ARCHITECTURE_OVERVIEW.md`

Role:

- explain the project's technical skeleton

Typical contents:

- system purpose
- main modules
- responsibilities
- data flow
- key boundaries

### 6.6 `DATA_MODEL.md`

Role:

- explain core entities, relationships, and important constraints

### 6.7 `UI_GUIDE.md`

Role:

- explain visible UI structure and user-facing behavior

### 6.8 `INTERACTION_RULES.md`

Role:

- explain interaction-level decisions and behavior rules

### 6.9 `DEV_SETUP.md`

Role:

- explain how to run and develop the project

### 6.10 `TESTING.md`

Role:

- explain how to validate changes

### 6.11 `KNOWN_ISSUES.md`

Role:

- track known problems in a structured way

### 6.12 `AI_CONTEXT.md`

Role:

- short current working context for incoming AI agents

### 6.13 `AI_WORKFLOW.md`

Role:

- explain how AI agents should work on this project

### 6.14 `DEV_LOG.md`

Role:

- concise recent work index

### 6.15 `tasks/`

Role:

- one file per task with full execution detail

### 6.16 `decisions/`

Role:

- durable work decisions that should remain visible over time

### 6.17 `logs/`

Role:

- archived time-based summaries

## 7. Maintenance Rules

### 7.1 One Primary Home Per Fact

Each important fact should have one primary owner document.

Other documents may reference it, but should not fully duplicate it.

### 7.2 No Catch-All Spec Documents

Do not create or keep expanding a single mixed document that combines:

- product definition
- architecture explanation
- design rules
- engineering operations
- task history

If such a document exists, gradually split it by ownership.

### 7.3 Stable Truth vs Execution History

Stable truth belongs in:

- `product`
- `architecture`
- `design`
- `engineering`

Execution history belongs in:

- `ai/tasks`
- `ai/logs`
- `ai/DEV_LOG.md`

### 7.4 Smallest Necessary Cross-Layer Updates

When one change affects multiple layers:

- update the primary owner layer first
- update only necessary downstream implications elsewhere

Do not duplicate the same full explanation across multiple documents.

### 7.5 Legacy Mixed Documents

If the project already contains mixed legacy docs:

- treat them as source material
- extract content into proper owner documents
- reduce the old file into an index, stub, or deprecation note after replacement exists

Do not keep using the mixed file as the long-term main source.

## 8. Change Routing Rules

When deciding which docs to update, use this logic.

### 8.1 Product Capability Or Business Rule Change

Update:

- `product`

Update `design` only if user behavior changes.

Update `architecture` only if technical boundaries change.

### 8.2 Interaction Or UI Behavior Change

Update:

- `design`

Update `product` only if user-visible behavior changes the product rule or acceptance criteria.

### 8.3 Technical Structure Or Boundary Change

Update:

- `architecture`

Update `engineering` only if contributor workflow or operational steps also change.

### 8.4 Development / Testing / Packaging / Release Change

Update:

- `engineering`

Update `architecture` only if the underlying structural design also changed.

### 8.5 AI Collaboration Or Task-Tracking Change

Update:

- `ai`

## 9. `AI_CONTEXT.md` Rules

`AI_CONTEXT.md` is strongly recommended for projects with ongoing multi-step work, multiple agents, or recurring handoffs.

For very small or short-lived projects, it may be omitted if there is no real need for current-phase memory compression.

It is not a replacement for architecture docs.

It is not a long history file.

Its job is to provide current, compressed working context.

It should contain only:

- current priorities
- current constraints
- currently important decisions still affecting work
- suggested read order if useful

It should be updated by:

- removing no-longer-relevant context
- adding newly relevant current-phase context

It is expected to change significantly over time.

## 10. `DEV_LOG.md` And Task History Rules

Relationship:

- `DEV_LOG.md` = short recent work index
- `tasks/` = one full record per task
- `logs/` = archived summaries

Rule:

- long detail goes into task files
- concise summary goes into logs

Do not copy full task reports into the main dev log.

Recommended `DEV_LOG.md` entry style:

- prefer one entry per meaningful work thread, milestone, or completed phase
- use a short heading such as `### YYYY-MM-DD Short Phase Title`
- include `Status:`
- include a short `Summary:` section with only the most important bullets
- include task links such as `Primary task links:` or `Links:`

This richer block format is allowed when it improves handoff clarity, but it must still behave like an index rather than a second full task report.

Practical limits:

- prefer roughly 2 to 6 summary bullets
- link to task files for execution detail instead of repeating the whole implementation story
- keep only current or high-value recent entries in `DEV_LOG.md`; move older detail into `logs/`

Reference-path rule for `DEV_LOG.md`:

- for files and documents inside the project, prefer relative path text such as `ai/tasks/2026-06-04_01_example.md`
- use absolute paths only when the referenced document is outside the project boundary
- keep log references lightweight and readable rather than using environment-specific project-internal absolute paths by default

Monthly archives are recommended, but they must not break active continuity unnecessarily.

If work at the end of one month and the start of the next month is clearly part of the same active thread, `DEV_LOG.md` should keep a concise continuous summary for that thread even if some detailed entries have already moved into `logs/YYYY-MM.md`.

Treat monthly archives as historical organization, not as a hard boundary for ongoing context.

## 10.1 Encoding and character rules

All documentation files must be written in `UTF-8`, preferably `UTF-8 without BOM`.

This applies to:

- `.md`
- `.txt`
- `.json`
- `.yml`
- `.yaml`
- all generated task documents
- all execution documents
- all review documents
- all `DEV_LOG.md` documents
- all `AI_CONTEXT.md` documents

Do not rely on:

- system default encoding
- ANSI
- GBK
- GB2312
- editor default save encoding

On Windows, any script or command that writes files must explicitly specify `UTF-8`.

Recommended write patterns:

- PowerShell file writes should pass an explicit UTF-8 encoding
- Python file writes should use `encoding="utf-8"`
- JSON/YAML emitters should be configured to write UTF-8 rather than inheriting the host locale

Character policy:

- allow Chinese content normally when the project needs it
- prefer ASCII punctuation by default
- prefer plain `" "` and `' '` for quotes
- avoid smart quotes such as `“ ”` and `‘ ’`
- avoid unnecessary special Unicode punctuation unless it has a clear purpose

If you see mojibake or encoding corruption such as `鈥`, `锟`, or `�`, treat it as a document quality defect and fix it.

When repairing existing documents with encoding damage, make the smallest semantic change that removes the corruption. Do not rewrite the whole document just to refresh encoding unless that is actually necessary.

## 11. Context Delta Rule

Task files should include a `Context Delta` section when the task produces durable lessons, future follow-up items, or changes to project rules, structure, ownership, or workflow.

Purpose:

- capture what the task changed in the project's long-term working memory
- compress durable lessons without copying the whole execution log

`Context Delta` is not:

- a full task summary
- a command transcript
- a replacement for the execution report

It should capture only information that may matter to future tasks.

If a task is very small and produces no durable memory change, the section may be omitted.

Useful categories include:

- `Keep` = durable facts worth remembering
- `Changed` = structure, responsibility, or rule changes
- `Avoid` = incorrect paths or rejected directions to avoid repeating
- `Follow-up` = future work that remains open

Authorship guidance:

- if the project uses separate planner/coder/reviewer roles, the agent that actually performed the implementation work should draft the `Context Delta` inside the task file because that agent knows the concrete execution findings best
- `Planner` or `Reviewer` should then refine it and decide what, if anything, should be promoted into longer-lived documents
- do not require `Planner` alone to write all `Context Delta` content when `Planner` did not directly perform the implementation work
- do not let the implementation agent alone decide all long-term memory promotion when broader project context is needed

Promotion guidance:

- if it affects current active work repeatedly, it may be promoted into `AI_CONTEXT.md`
- if it is a durable principle or important decision, it may be promoted into `decisions/`
- if it is a bug or persistent risk, it may be promoted into `KNOWN_ISSUES.md`
- if it is only relevant to this one task, keep it inside the task file only

Follow-up handling rule:

- if `Context Delta -> Follow-up` contains an item that is expected to matter beyond this single finished task, `Planner` or `Reviewer` must explicitly decide whether it should be promoted into `AI_CONTEXT.md`, `decisions/`, `KNOWN_ISSUES.md`, or `ROADMAP.md`
- such items must not be left silently buried only inside the closed task file
- if an item is intentionally kept task-local, the reviewer should record that decision briefly

## 12. Decision Record Rules

Use `decisions/` for durable decisions that should remain visible over time.

Typical examples:

- important workflow rules
- scope boundary decisions
- architecture decisions
- important rejected approaches

Recommended format:

- context
- decision
- reason
- consequences

## 13. AI Workflow Rules

If the project uses multiple agent roles, document them in `AI_WORKFLOW.md`.

Examples may include:

- planner
- coder
- reviewer

But these roles are optional.

Do not assume every project uses the same AI collaboration model.

The agent should only define role-specific rules when they actually apply to the project.

Role recognition should be based primarily on behavior, not only on labels.

Examples:

- an agent acting mainly through implementation, debugging, validation, and direct code changes is functionally acting as the coding/implementation role
- an agent acting mainly through task planning, decomposition, orchestration, review coordination, and long-horizon documentation maintenance is functionally acting as the planning role
- an agent acting mainly through review, scope control, result validation, and follow-up classification is functionally acting as the review role

Role labels and aliases may help, but behavior should take precedence when deciding which responsibilities apply.

If the project explicitly uses a `planner / coder / reviewer` workflow, add and maintain role-specific rules such as:

- `Planner` defines the task file, scope boundary, and acceptance criteria
- the implementation agent executes only the task scope defined in the task file and does not expand scope without approval
- after implementation, the implementation agent updates the same task file with an execution report
- after implementation, the implementation agent drafts the task's `Context Delta`
- any deviation from the original task plan is recorded explicitly
- `Planner` or `Reviewer` may apply a small in-scope correction during review when it is faster or clearer to do so directly
- such planner/reviewer corrections must be recorded explicitly in the same task file with clear authorship
- if the follow-up change is meaningfully out of scope, create a new task instead of silently extending the old one
- `Planner` or `Reviewer` refines the `Context Delta` if needed
- `Planner` or `Reviewer` decides whether any `Context Delta` should be promoted into `AI_CONTEXT.md`, `decisions/`, or other long-term documents
- before closing the task, `Planner` or `Reviewer` explicitly classifies any non-local `Follow-up` item so it does not remain only in the task file by accident
- `Reviewer` or `Planner` decides whether durable conclusions should update `AI_CONTEXT.md` or `decisions/`

General rule regardless of role naming:

- any agent that materially contributes implementation, correction, or validation work to a task should record the relevant result back into the same task file with clear authorship

## 14. Naming Guidance

Use clear, stable, descriptive file names.

Avoid names such as:

- `temp`
- `misc`
- `notes2`
- `final_final`
- `project_spec` as a catch-all

For task files, recommended pattern:

```text
YYYY-MM-DD_nn_short-task-name.md
```

Where:

- `YYYY-MM-DD` is the task date
- `nn` is the sequence number for that day only

Use day-local numbering such as:

```text
2026-06-04_01_fix-import-flow.md
2026-06-04_02_update-task-log-rules.md
```

Do not use one global continuous task counter across the whole project.

If parallel branches independently create the same day-local number, resolve the collision pragmatically when histories meet. Prefer renaming the less-established task record or adding a short suffix rather than introducing a global counter system.

For decision files, recommended pattern:

```text
ADR-0001_short-title.md
```

## 15. Optional Metadata

If useful, the agent may add lightweight front matter such as:

```md
---
title: Product Brief
status: active
owner: product
last_updated: YYYY-MM-DD
---
```

Use metadata only if it will actually be maintained.

Do not add noisy metadata by default.

## 16. Bootstrap Procedure

When initializing or standardizing docs for a project, the agent should:

1. inspect current docs
2. identify mixed, duplicated, or missing documentation areas
3. create the top-level `doc/` structure if missing
4. create the recommended initial files if missing
5. route existing content into the correct owner layers
6. reduce mixed legacy documents after replacements exist
7. establish AI workflow and task-record structure
8. keep the system small and useful rather than over-expanding it

## 17. Quality Checklist

Before finishing documentation work, verify:

1. Every active document has a clear owner layer.
2. No new catch-all spec was introduced.
3. Stable truth and execution history remain separated.
4. `AI_CONTEXT.md` is short and current.
5. `DEV_LOG.md` remains concise.
6. New or modified documents were checked for mojibake or encoding corruption.
7. Document writes used explicit UTF-8 where files were created or rewritten.
8. `Context Delta` is used only for durable memory changes, not general summaries.
9. Durable decisions are not buried only in task files.
10. The structure is not more detailed than the project currently needs.

## 18. Execution Instruction

If asked to initialize, normalize, or maintain a project documentation system, the agent should:

- use this specification directly
- create the minimum useful structure
- maintain ownership boundaries
- keep docs readable for later AI agents
- prefer gradual cleanup over disruptive rewrites unless instructed otherwise
