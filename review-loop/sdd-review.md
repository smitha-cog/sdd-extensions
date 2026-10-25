---
description: Review a feature's implementation against its spec and plan, and write a findings report.
argument-hint: "[feature-dir or spec path]"
---

## User input

```text
$ARGUMENTS
```

Consider the user input before proceeding (if not empty).

## Goal

Compare what was built against what the spec and plan say should be built.
Produce a findings report that `/sdd-fix` can act on. **Do not modify code.**

## Inputs

- Spec: `{{feature-dir}}/spec.md`
- Plan: `{{feature-dir}}/plan.md`
- Tasks: `{{feature-dir}}/tasks.md`
- Changed code: <!-- TODO: how to locate it (git diff vs base branch, task file refs, ...) -->

## Steps

1. Load the spec, plan and tasks. Stop with an error if the spec is missing.
2. Build a checklist of requirements and acceptance criteria from the spec.
3. For each item, find the code that satisfies it, or record that none does.
4. Check the implementation for:
   - Requirements missing or only partly done
   - Behaviour the spec doesn't ask for (scope creep)
   - Places where the code departs from the plan's design decisions
   - Correctness bugs and unhandled edge cases named in the spec
   - <!-- TODO: project-specific checks (constitution, style, security) -->
5. Write the report to `{{feature-dir}}/review.md` using the format below.

## Report format

```markdown
# Review: {{feature-name}}
Date: {{date}} · Iteration: {{n}}

## Summary
{{one-paragraph verdict}} — Status: PASS | CHANGES REQUESTED

## Findings
| ID | Severity | Requirement | File:line | Finding | Suggested fix | Decision |
|----|----------|-------------|-----------|---------|---------------|----------|
| R1 | high     | FR-003      | src/...   | ...     | ...           |          |

## Coverage
| Requirement | Status (met / partial / missing) | Evidence |
```

Severity: `critical` · `high` · `medium` · `low`.

Decision: always leave this column blank. A person fills it in for each finding:
`fix` (the spec is right and the code missed it) or `spec-change` (the spec or plan
needs to change and goes back through the normal SDD process).

## Rules

- Every finding cites a requirement ID and a file location.
- Report only issues you can point to in the code; no speculative findings.
- If nothing is found, say PASS and leave the findings table empty.
- Never fill in the Decision column.
