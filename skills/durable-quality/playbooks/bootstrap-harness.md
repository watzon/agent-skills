# Bootstrap harness playbook

Install the minimum wall that makes agent volume safe. Small PRs. Prove each gate fails closed.

## Prerequisites

- Know how to build, test, and lint locally
- Default branch protection available (or document the gap)
- Agree on critical paths (auth, money, data deletion, migrations, IAM)

## Sequence

### PR1: Floor tooling

- Formatter + linter + typechecker (as applicable)
- Single commands documented in README and agent docs
- CI runs them on PRs

Negative check: introduce a lint violation on a branch; CI red.

### PR2: Tests required

- Test job required on default branch
- Document how to run the relevant subset locally
- Fail PR template section for "tests"

Negative check: PR with failing test cannot merge.

### PR3: Anti-CI-gaming

- Workflow files owned by humans (CODEOWNERS)
- Policy: CI weakening only in dedicated PR with rationale label
- Optional bot comment on workflow diffs

Negative check: feature PR that sets `continue-on-error: true` on required job is rejected in review even if green.

### PR4: Secrets and SAST

- Secret scan on PRs
- Basic SAST or semgrep/bandit/eslint-security equivalent
- Stop committing `.env` via ignore + scan

### PR5: Architecture fitness (if layered codebase)

- Choose tool for stack (dependency-cruiser, import-linter, ArchUnit, custom)
- Encode 3–10 real rules max to start (not a fantasy hex diagram)
- Baseline existing violations if needed; forbid new ones

Negative check: illegal import fails CI.

### PR6: CODEOWNERS / critical paths

- Map T4–T5 paths to owners
- Required review from owners
- Document ownership expectations

### PR7: Agent instruction surfaces

- Add lean `AGENTS.md` quality section (see examples)
- Mirror commands that CI runs
- State refusals
- Add hooks only where the runtime supports hard blocks

### PR8: PR template + size norms

- Evidence sections: intent, commands, risks, tier
- Soft size guidance; hard reject culture for mudballs

### PR9: Metrics

- Define where change-fail, review time, and zero-review are visible
- Even a manual monthly snapshot beats nothing

### PR10: Mutation or property sampling (critical pkgs only)

- Pick one high-value package
- Run mutation or property tests in CI (nightly ok at first)
- Track survivors as test backlog

## Stack hints (examples, not mandates)

| Stack | Floor | Arch | Mutation/property |
|---|---|---|---|
| TS/JS | prettier/biome, eslint, tsc, vitest/jest | dependency-cruiser | stryker, fast-check |
| Python | ruff, pyright/mypy, pytest | import-linter | mutmut, hypothesis |
| JVM | spotless, checkstyle, junit | ArchUnit | PIT |
| Go | gofmt, govet, go test | internal package rules / custom | mostly property tests |
| Rust | rustfmt, clippy, cargo test | cargo modules / custom | cargo-mutants |

## Done criteria

Harness bootstrap is done when:

1. Required checks block merge on default branch
2. At least one architecture or ownership gate covers critical paths
3. Agent docs do not lie about enforcement
4. A deliberate break of each major gate was demonstrated
5. Named humans own T4–T5 directories

## Do not

- Boil the ocean with 50 arch rules on day one
- Block the whole org on mutation score before the suite is honest
- Write a 2,000-line AGENTS.md essay
- Fake green with skipped jobs
