# File Templates

Use these templates only when creating missing documents.

Adapt them to the project instead of copying blindly.

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

## `ai/decisions/ADR-0001_<title>.md`

```md
# Decision

## Context

## Decision

## Reason

## Consequences
```
