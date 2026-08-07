# Flagship OSS quality patterns

Compressed from primary contribution/governance docs. Use as menus, not cargo cult.

## Recurring stack

| Layer | Pattern | Examples |
|---|---|---|
| Design gate | RFC / proposal / KEP before big work | Rust RFCs, Go proposals, K8s KEPs, React RFCs, Django DEPs |
| Ownership | Path or subsystem owners | Linux MAINTAINERS, K8s/Chromium OWNERS, Firefox modules |
| Human review | Mandatory non-trivial review | All serious projects |
| Two-phase review | Correctness then systemic approve | K8s `/lgtm` + `/approve` |
| Automation | Merge gates, formatters, trybots | Tide, CQ, bors/rollups, gofmt |
| Tests as contract | Fail without the fix | TypeScript baselines, LLVM FileCheck, Postgres regress |
| Release policy | Absorb risk before users | Merge window + rc, feature freeze, flags, deprecations |
| Written rejects | Explicit "no" list | Style-churn bans, freeze breakers, untested features |

## Project notes

### Linux kernel

- MAINTAINERS + get_maintainer routing
- One logical change; bisect-clean series
- checkpatch as guide, not sole law
- Coding style treats deep nesting as a design smell
- AI policy: human DCO `Signed-off-by`; agents must not DCO-sign; use `Assisted-by`
- Docs: https://docs.kernel.org/process/coding-assistants.html

### Kubernetes

- Directory OWNERS (reviewers, approvers, emeritus)
- Bots encode social state (labels, lgtm, approve)
- Tide merges only when policy + CI satisfied
- Inactive owners pruned / emeritus
- KEPs for significant features

### Google eng-practices

- Code health over time is the purpose of review
- Design, complexity, tests, naming, docs
- Reject over-engineering for speculative futures
- Look at every assigned line; context beyond the hunk
- https://google.github.io/eng-practices/

### Chromium

- OWNERS required for domain approval
- Commit Queue validates builds/tests after human approval
- Rubber Stamper never grants OWNERS
- Large Scale Changes process for mechanical repo-wide edits
- Security paths with stricter ownership (`set noparent`)

### SQLite

- Extreme verification: tests dwarf product code
- 100% branch / MC/DC in as-deployed configuration (TH3)
- Anomaly tests: OOM, I/O fail, crash, power loss
- Fuzz + mutation mindset
- Release checklists
- https://www.sqlite.org/testing.html

### TypeScript

- Baseline-driven compiler tests
- At least one test must fail without the fix
- Issue approval before non-trivial code
- Explicit AI policy: disclose assistance; ban bulk agent PR spam

### Rust

- RFC for language/std design
- Feature gates + stabilization reports
- crater for ecosystem breakage
- Team ownership + heavy CI

### Go

- gofmt ends style bikesheds
- Issue/proposal before significant change
- Code review comments as living law
- Trybots; small maintainer set; thorough review

### PostgreSQL

- Design on-list before large coding
- CommitFest + mutual review obligation
- Reject unrelated formatting in functional patches
- Regress + isolation tests

### Django / Rails

- Deprecation timelines and compatibility religion (Django)
- Tests that fail without the change; reject cosmetic-only (Rails)
- DEPs / design discussion for major features

## What scales

- Path OWNERS + suggested reviewers
- Mandatory formatters
- Golden/baseline tests for subtle surfaces
- Feature flags keeping trunk releasable
- Proposal layer so PR review is about code
- Stable/backport only from already-mainlined fixes

## What strains

- Hero owners without prune/emeritus
- Bulk low-context AI PRs
- Giant unrelated patches without LSC-like process
- Post-commit review without revert-to-green culture
- Coverage theater without semantic tests

## Portable rejects (global)

1. Untested user-visible features
2. Drive-by mass reformat / cosmetic-only PRs
3. Breaking stable APIs without process
4. Design-by-PR for substantial features
5. Ignoring review comments
6. Security bugs in the wrong channel
7. Undisclosed bulk autonomous agent spam
