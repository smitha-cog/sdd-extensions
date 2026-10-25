# Review vs. audit

*Written for: {{audience — e.g. engineers and leads new to SDD}}*

## The short version

{{One or two sentences: a review is part of building; an audit checks after the fact.}}

## Review

- **When:** during development, after each implementation pass
- **Against:** the feature's own spec and plan
- **Who acts on it:** the same agent/developer, right away (`/sdd-fix`)
- **Output:** findings to fix, then a re-review
- **Goal:** get this feature right

## Audit

- **When:** <!-- TODO: e.g. before release, periodically -->
- **Against:** <!-- TODO: org standards, compliance, security policy -->
- **Who acts on it:** <!-- TODO -->
- **Output:** <!-- TODO -->
- **Goal:** <!-- TODO -->

## Side by side

| | Review | Audit |
|---|---|---|
| Timing | During build | After build |
| Scope | One feature | System / process |
| Reference | Spec + plan | External standard |
| Loop | Review → fix → review | One-off report |

## Why the review loop matters in SDD

<!-- TODO: argument for why the spec makes reviews checkable -->

## When to use each

<!-- TODO -->
