---
description: Assess the complexity of an existing UI to scope SDD adoption.
argument-hint: "[ui root dir or area]"
---

## User input

```text
$ARGUMENTS
```

Consider the user input before proceeding (if not empty).

## Goal

Score each UI area by complexity and risk so the team can decide where to start
using SDD and how much spec detail each area needs.

## Prerequisites

`{{sdd-dir}}/ui/inventory.md` from `/sdd-ui-init`. If it's missing, tell the user to run that first.

## Dimensions (score 1–5 each)

| Dimension | What to look at |
|-----------|-----------------|
| Size | LOC, number of components |
| Coupling | Shared state, cross-component imports |
| Data | Number of APIs/stores, async flows |
| Interaction | Forms, validation, multi-step flows |
| Test coverage | Present / partial / none (inverted: none = 5) |
| <!-- TODO --> | <!-- e.g. accessibility, i18n, legacy tech --> |

## Steps

1. Load the inventory.
2. Score each area on every dimension, with a one-line reason per score.
3. Compute a total and assign a tier:
   - **Low** (≤ {{low-threshold}}): lightweight spec
   - **Medium**: full spec + plan
   - **High** (≥ {{high-threshold}}): spec + plan + review loop, consider splitting first
4. Write `{{sdd-dir}}/ui/complexity.md`:

```markdown
| Area | Size | Coupling | Data | Interaction | Tests | Total | Tier | Notes |
|------|------|----------|------|-------------|-------|-------|------|-------|

## Recommended starting points
1. ...
```

## Rules

- Base scores on evidence in the code and cite paths.
- Read-only on application code.
