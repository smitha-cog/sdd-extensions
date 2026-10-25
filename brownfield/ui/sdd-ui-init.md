---
description: Bootstrap SDD artifacts for an existing (brownfield) UI codebase.
argument-hint: "[ui root dir]"
---

## User input

```text
$ARGUMENTS
```

Consider the user input before proceeding (if not empty).

## Goal

Document an existing UI so later features can be specified and planned with SDD,
without changing application code.

## Steps

1. Detect the stack: framework, language, styling, state management, routing,
   build tooling, test tooling. <!-- TODO: list supported frameworks -->
2. Map the UI:
   - Routes / pages
   - Shared components and design-system primitives
   - Data sources (APIs, stores) each page depends on
3. Find the existing conventions (folder layout, naming, component patterns, tests).
4. Write the baseline artifacts:
   - `{{sdd-dir}}/ui/baseline.md` — stack, structure, conventions
   - `{{sdd-dir}}/ui/inventory.md` — table of routes and components
   - `{{sdd-dir}}/ui/constraints.md` — rules new specs must follow
5. List any gaps or risks you found (no tests, mixed patterns, dead code).
6. Suggest running `/sdd-ui-complexity` next.

## Inventory format

```markdown
| Route / Component | Path | Depends on | Tests | Notes |
|-------------------|------|------------|-------|-------|
```

## Rules

- Read-only on application code; write only under `{{sdd-dir}}`.
- Describe what exists, not what should exist.
