# sdd-extensions

Extensions for Spec-Driven Development (SDD) workflows: extra slash commands for
review loops and brownfield (existing codebase) adoption.

> **Status:** template. Replace every `<!-- TODO -->` and `{{placeholder}}`.

## What's inside

| Path | Purpose |
|------|---------|
| `review-loop/sdd-review.md` | Review a spec/plan/implementation against its spec and report findings |
| `review-loop/sdd-fix.md` | Apply fixes for findings produced by `sdd-review` |
| `brownfield/ui/sdd-ui-init.md` | Bootstrap SDD artifacts for an existing UI codebase |
| `brownfield/ui/sdd-ui-complexity.md` | Assess UI complexity to scope SDD adoption |
| `docs/review-vs-audit.md` | Background: why a review loop differs from an audit |
| `examples/` | Worked examples of each command |

## Install

Copy the command files into your agent's commands directory, e.g.:

```bash
# Claude Code
cp review-loop/*.md brownfield/ui/*.md .claude/commands/
```

<!-- TODO: add instructions for other agents (Copilot, Cursor, Gemini CLI, ...) -->

## Usage

```text
/sdd-review {{feature-or-spec-path}}
/sdd-fix {{review-report-path}}
/sdd-ui-init {{ui-root-dir}}
/sdd-ui-complexity {{ui-root-dir}}
```

## The review loop

```
spec ──▶ implement ──▶ /sdd-review ──▶ findings ──▶ /sdd-fix ──┐
                            ▲                                  │
                            └──────────── repeat until clean ◀─┘
```

See [docs/review-vs-audit.md](docs/review-vs-audit.md).

## Contributing

<!-- TODO -->

## License

See [LICENSE](LICENSE).
