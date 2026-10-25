---
description: Apply fixes for findings in a review report produced by /sdd-review.
argument-hint: "[review.md path] [finding IDs]"
---

## User input

```text
$ARGUMENTS
```

Consider the user input before proceeding (if not empty).

## Goal

Fix implementation misses: places where the spec, plan and tasks are correct but
the code doesn't deliver them (a requirement partly done, an edge case skipped, an
error path unhandled, a missing test). This command never decides whether the spec
is right. A person makes that call for each finding in `{{feature-dir}}/review.md`.

## Steps

1. Load the review report. Stop if it doesn't exist or its status is PASS.
2. Read the **Decision** column for each finding:
   - `fix`: in scope. Fix it.
   - `spec-change`: out of scope. Don't touch the code. List it in the fix log
     as `deferred to spec update`.
   - Blank: stop and ask the user to decide. Don't infer a decision.
   If the user named IDs, use only those, and they must still be marked `fix`.
3. For each `fix` finding:
   1. Re-read the cited requirement in the spec, the related plan decision, and the task.
   2. Make the smallest change that brings the code in line with them.
   3. Run the related tests: <!-- TODO: test command -->
   4. Mark the outcome: `fixed` or `skipped (reason)`.
4. Add a **Fix log** section to the review report:

```markdown
## Fix log — iteration {{n}}
| ID | Decision | Outcome | Change summary | Files |
|----|----------|---------|----------------|-------|
```

5. Tell the user to run `/sdd-review` again. For any `spec-change` items, tell them
   to update the spec, then the plan, then the tasks, and to change the code as
   part of that work, not through `/sdd-fix`.

## Rules

- Never edit spec.md, plan.md or tasks.md.
- Never reclassify a finding. If a `fix` item turns out to need a spec or plan
  change, mark it `skipped (needs decision: <reason>)` and leave it for the user.
- Don't refactor beyond what the finding needs.
- If a fix breaks tests you can't resolve, revert it and mark it `skipped`.
