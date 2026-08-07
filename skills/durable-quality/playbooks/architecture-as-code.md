# Architecture as code playbook

Wiki diagrams do not constrain agents. Failing tests do.

## Goal

Encode a few load-bearing boundaries so local green cannot silently dissolve the system.

## Steps

### 1. Name real boundaries

From the codebase as it is (or as the next increment needs):

- app → domain ← infra direction
- package public API vs internal
- no UI importing data access directly
- no billing importing debug tooling
- extension points that must stay stable

Prefer 3–10 rules. More rules that nobody understands will be disabled.

### 2. Pick an enforcement mechanism

Examples:

- TypeScript/JS: dependency-cruiser, eslint import plugins
- Python: import-linter
- Java/Kotlin: ArchUnit
- .NET: NetArchTest
- Monorepo: package visibility (Bazel, pants, nx module boundaries)
- Go: internal packages + custom checks
- Rust: module visibility + CI script checks

### 3. Baseline legacy

If the repo is already muddy:

- generate a baseline of existing violations
- fail only on new violations (ratchet)
- optional dedicated cleanup epics

Never block all delivery on historical sin on day one.

### 4. Wire CI

- Run on PRs
- Fast enough to be required (seconds to low minutes)
- Clear error messages agents can fix

### 5. Document for agents

In AGENTS.md:

- one paragraph on the intended direction
- command to run the check locally
- "do not disable this rule in feature PRs"

### 6. Negative proof

Add an illegal import on a throwaway branch; CI must fail.

## Dependency rule (Clean Architecture, operational)

When the domain warrants it:

- policy/domain modules do not import frameworks, DB drivers, or UI
- adapters depend inward
- cycles are defects

Do not force full clean architecture ceremony on a script-sized repo. Match complexity to system size.

## Complexity budgets (optional)

Where useful, gate:

- max cyclomatic complexity on new code
- max file length for new files
- max dependency fan-out

Start as warnings; promote to gates when calibrated.

## Large-scale mechanical change

If a refactor touches dozens of packages:

- use an explicit LSC-style process (Chromium lesson)
- pure mechanical PR separate from behavior
- owners still approve domains touched

## Done

Architecture-as-code is working when:

- illegal dependencies fail CI
- agents fix violations rather than deleting the rule
- humans rarely debate import direction in PR nits
