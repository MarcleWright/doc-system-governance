# File Templates

Use these templates only when a project needs the file and no stronger local convention already exists.

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

## Deferred Areas
```

## `architecture/ARCHITECTURE_OVERVIEW.md`

```md
# Architecture Overview

## System Purpose

## Main Modules

## Responsibility Boundaries

## Data Flow
```

## `architecture/DATA_MODEL.md`

```md
# Data Model

## Overview

## Core Entities

## Relationships

## Important Constraints
```

## `design/UI_GUIDE.md`

```md
# UI Guide

## Main Screens Or Workspaces

## Layout Structure

## Key Visible Behaviors
```

## `design/INTERACTION_RULES.md`

```md
# Interaction Rules

## Create / Edit Flows

## Destructive Action Rules

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

## `ai/AI_WORKFLOW.md`

```md
# AI Workflow

## Roles

## Task Lifecycle

## Documentation Update Rules

## Review Rules
```

## `ai/DEV_LOG.md`

```md
# Dev Log

## Recent

- YYYY-MM-DD: short summary, related task path such as `ai/tasks/2026-06-04_01_example.md`

## Archive
```

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

## Reviewer Notes

## Context Delta

### Keep

### Changed

### Avoid

### Follow-up

## Final Result
```
