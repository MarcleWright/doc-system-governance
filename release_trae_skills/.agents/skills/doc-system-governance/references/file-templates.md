# File Templates

Use these templates only when creating missing documents.

Adapt them to the project instead of copying blindly.

All documents created from these templates must be written in `UTF-8`, preferably `UTF-8 without BOM`.

## `doc/README.md`

```md
# Project Documentation

## Product
Defines what the product is, what it does, and what rules it must satisfy.

## Architecture
Defines the technical skeleton, module boundaries, and data model.

## Design
Defines user interaction rules and visible UI behavior.

## Engineering
Defines setup, testing, release, and operational guidance.

## Material
Stores local or temporary user-provided reference material. Material is not stable project truth until reviewed and promoted into the correct owner layer.

## AI
Defines AI workflow, task records, current context, and work history.
```

## `product/PRODUCT_BRIEF.md`

```md
# Product Brief

## Purpose

## Target Users

## Core Value

## Core Workflows

## Non-goals

## Key Domain Concepts
```

## `product/PRODUCT_REQUIREMENTS.md`

```md
# Product Requirements

## Feature: <name>

### Goal

### User Value

### Scope

### Rules

### Acceptance Criteria

### Non-goals
```

## `product/ROADMAP.md`

```md
# Roadmap

## Current Stage

## Near-Term Priorities

## Medium-Term Priorities

## Deferred Areas
```

## `architecture/ARCHITECTURE_OVERVIEW.md`

```md
# Architecture Overview

## System Purpose

## Main Modules

## Responsibility Boundaries

## Data Flow

## Key Technical Decisions
```

## `architecture/DATA_MODEL.md`

```md
# Data Model

## Overview

## Core Entities

## Relationships

## Important Constraints

## Source Of Truth
```

## `design/UI_GUIDE.md`

```md
# UI Guide

## Main Screens Or Workspaces

## Layout Structure

## Key Visible Behaviors

## Important UI States
```

## `design/INTERACTION_RULES.md`

```md
# Interaction Rules

## Selection Behavior

## Create / Edit Flows

## Delete / Destructive Action Rules

## Drag And Drop Rules

## Error / Confirmation Behavior
```

## `engineering/DEV_SETUP.md`

```md
# Development Setup

## Prerequisites

## Install

## Run

## Common Troubleshooting
```

## `engineering/TESTING.md`

```md
# Testing

## Test Types

## Automated Checks

## Manual Verification

## Release Validation
```

## `engineering/KNOWN_ISSUES.md`

```md
# Known Issues

| ID | Area | Severity | Status | Summary | Related Task |
|---|---|---|---|---|---|
```

## `material/README.md`

```md
# Material

This folder stores local or temporary reference material used during project work.

Material here may include user-provided documents, screenshots, sample files, exports, research snippets, or raw notes.

Material is not stable project truth until it has been reviewed and promoted into the correct owner layer:

- `product`
- `architecture`
- `design`
- `engineering`
- `ai`

By default, contents in this folder are local-first and should not be pushed to the remote unless explicitly requested.
```

## `material/.gitignore`

```gitignore
*
!.gitignore
!README.md
!.gitkeep
```

## `ai/AI_CONTEXT.md`

```md
# AI Context

## Current Priorities

## Current Constraints

## Current Important Decisions

## Suggested Read Order
```

Recommended for projects with ongoing handoffs, multiple agents, or longer-running phases.

## `ai/AI_WORKFLOW.md`

```md
# AI Workflow

## Roles

## Task Lifecycle

## Documentation Update Rules

## Review Rules
```

If the project uses planner/coder/reviewer separation, add rules such as:

- Planner defines scope and acceptance criteria in the task file.
- The implementation agent executes only the task scope and does not expand scope unilaterally.
- The implementation agent writes an execution report into the same task file after implementation.
- The implementation agent drafts the task's Context Delta after implementation.
- Deviations from the original plan are recorded explicitly.
- Planner or Reviewer may make a small in-scope correction during review, but must record it with explicit authorship in the same task file.
- Meaningfully out-of-scope follow-up work gets a new task.
- Planner or Reviewer refines the Context Delta and owns long-term context updates.
- Planner or Reviewer explicitly classifies any non-local Follow-up item before the task is finalized.

If role names differ, map responsibilities by behavior rather than by exact label.

## `ai/DEV_LOG.md`

```md
# Dev Log

## Recent

### YYYY-MM-DD Short Phase Title

Status: Done

Summary:

- short outcome or milestone
- short outcome or milestone

Primary task links:

- `ai/tasks/YYYY-MM-DD_nn_example.md`

## Archive
```

Keep `Recent` continuous when the same active work thread spans a month boundary.

This format should stay concise. Use it as a recent-work index with clear handoff value, not as a replacement for task files.

Prefer relative path text for project-internal references. Use absolute paths only for documents outside the project.

## Encoding and review checklist

Before handing off any document created from these templates, verify:

- file encoding is `UTF-8`
- no system-default or locale-derived encoding was used during writes
- no mojibake appears in the rendered file
- no unnecessary smart quotes or special punctuation were introduced
- any existing corruption was repaired with the smallest semantic change possible

## `ai/tasks/<task>.md`

```md
# Task

## ID

## Title

## Status

## Goal

## Scope

## Non-goals

## Plan

## Acceptance Criteria

## Execution Report

### Implementation Contributor(s)

### Planner/Reviewer Follow-up Fixes

## Reviewer Notes

## Context Delta

### Keep

### Changed

### Avoid

### Follow-up

## Final Result

## Links
```

Recommended task filename pattern:

```text
YYYY-MM-DD_nn_short-task-name.md
```

Use `nn` as the sequence number for that day only.

If parallel branches create the same date and daily sequence number, resolve the collision later with a pragmatic rename or suffix rather than switching to a global counter.

For decomposed long tasks, use the parent task's day-local number plus uppercase letters for ordered sub-tasks:

```text
YYYY-MM-DD_16_parent-task.md
YYYY-MM-DD_16A_first-sub-task.md
YYYY-MM-DD_16B_second-sub-task.md
YYYY-MM-DD_16C_third-sub-task.md
YYYY-MM-DD_16_execution-loop.md
```

## `ai/tasks/<execution-loop>.md`

Use this template only when the user explicitly asks for a "long-task self-loop execution" document, "长任务自循环执行" document, execution loop md, or equivalent multi-round task-control record.

Do not create this file as an automatic side effect of task planning, sub-task review, or ordinary documentation governance. Create it only after the parent task and ordered sub-task list exist, unless the user explicitly asked to split the task and create this execution-loop document in the same request.

Recommended filename patterns:

```text
YYYY-MM-DD_nn_execution-loop.md
YYYY-MM-DD_03_execution-loop.md
```

```md
# Long-Task Self-Loop Execution

## Status

Active

## Objective

## Parent Task

- `ai/tasks/YYYY-MM-DD_nn_parent-task.md`

## Scope Boundaries

## Non-goals

## Ordered Sub-Tasks

| Order | Task | Status | Commit | Notes |
|---:|---|---|---|---|
| 1 | `ai/tasks/YYYY-MM-DD_16A_first-sub-task.md` | Ready |  |  |
| 2 | `ai/tasks/YYYY-MM-DD_16B_second-sub-task.md` | Blocked |  | Starts after 16A |

Naming rule:

- parent task keeps the numeric id, such as `16`
- child tasks append uppercase letters without an extra separator, such as `16A`, `16B`, `16C`
- execution-loop document uses the parent id, such as `YYYY-MM-DD_16_execution-loop.md`

## Per-Round Loop

1. Read this execution document, the parent task, and the current sub-task.
2. Inspect current code, current task status, recent log entries, and git status.
3. Implement only the current sub-task scope.
4. Run the agreed automated checks unless this document explicitly defers them.
5. Review the full diff and fix in-scope findings.
6. Update the current task file with execution notes, reviewer notes, final result, and Context Delta when durable context changed.
7. Update `DEV_LOG.md`, and update `AI_CONTEXT.md` only when current handoff context changed.
8. Update this execution ledger.
9. Make one local commit for the completed sub-task unless the user requested a different commit policy.
10. Reread the parent task before selecting the next sub-task.

## Validation

Automated checks:

- `<command>`

Manual checks:

- `<manual check or explicitly deferred>`

Deferred checks:

- `<reason and owner>`

## Documentation Maintenance

- Use the normal doc-system governance gate after each round.
- Keep detailed execution notes in the active sub-task.
- Keep this file as the control ledger, not a full transcript.
- Promote durable context to `AI_CONTEXT.md` only when future agents need it.

## Commit Policy

- One local commit per completed sub-task.
- Do not push unless explicitly requested.
- Record commit hashes in the ledger after each successful commit.

## Resume Instructions

1. Check `git status`.
2. Read this document, then the parent task, then the first Ready or In Progress sub-task.
3. Continue from the next incomplete ordered sub-task.
4. Preserve the scope boundaries and non-goals above.

## Execution Ledger

| Round | Date | Task | Result | Commit | Notes |
|---:|---|---|---|---|---|
| 1 | YYYY-MM-DD | `ai/tasks/...md` |  |  |  |

## Open Follow-ups Outside This Loop

- `<follow-up task or intentionally empty>`
```

## `ai/decisions/ADR-0001_<title>.md`

```md
# Decision

## Context

## Decision

## Reason

## Consequences
```
