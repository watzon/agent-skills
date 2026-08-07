# Constraint packs (C1–C10)

Use these as the audit scorecard and bootstrap backlog. Each pack: must / must-not / hard twin.

## C1 — Instruction surfaces

**Must**

- Root `AGENTS.md` (and/or `CLAUDE.md`) with install, build, test, lint commands
- Forbidden paths (generated, vendor, secrets)
- Lean root doc (prefer under ~200 lines); path-scoped rules for local detail
- PR quality bar summarized for agents

**Must not**

- Secrets or prod credentials in rules
- Contradictory parent/child instruction stacks
- Treat markdown as a security boundary

**Hard twin:** CI jobs named in the doc actually exist and are required.

## C2 — Deterministic quality wall

**Must**

- Format, lint, types, unit/integration tests as required checks
- SAST + secret scan on default branch PRs
- License/dependency policy where relevant
- Branch protection: cannot merge greenless

**Must not**

- Agent "fixes" CI by deleting tests or skipping jobs in the feature PR
- Optional-only lint on critical languages

**Hard twin:** required status checks; CODEOWNERS or admins only to change workflow files (or separate PR + human label).

## C3 — Architecture as code

**Must**

- Dependency direction rules for real layers
- Cycle detection
- Public API / package boundary tests where libraries exist
- Freeze or baseline mode for messy legacy while preventing new violations

**Must not**

- Architecture only in wiki or chat
- Pathless "clean architecture" slogans without import rules

**Hard twin:** ArchUnit, NetArchTest, dependency-cruiser, import-linter, custom lint, bazel visibility, etc. in CI.

## C4 — Test honesty

**Must**

- Fail-without-change tests for behavior work
- Human-first review when tests and prod code both change a lot
- Mutation or property testing on T3–T5 packages (start sampled)

**Must not**

- Coverage % as sole gate
- Bulk snapshot updates without narrative

**Hard twin:** CI test jobs; optional mutation job on critical paths; diff policy bot if available.

## C5 — Evidence-required intake

**Must**

- Intent / decision log on non-trivial PRs
- Commands run + output (or recording) in PR body
- Scope limits; plan required above N files or N lines

**Must not**

- Review 3k-line agent dumps with no plan
- "Works on my machine" without commands

**Hard twin:** PR template; size-labeling bot; CI comment script that demands sections (soft) + human reject (hard).

## C6 — Blast-radius tiering

**Must**

- Map paths to tiers (auth, payments, migrations, workflows, infra)
- Heavier proof + human owner on high tiers
- AI review tools are sensors, not final verdict, on T4–T5

**Must not**

- Uniform rubber stamp because unit tests passed

**Hard twin:** CODEOWNERS on tiered paths; required reviewers; path-filtered CI jobs.

## C7 — Reuse and anti-clone

**Must**

- Search for existing utilities before adding helpers
- Prefer extend/reuse/delete over copy
- Track duplication/churn metrics over time

**Must not**

- Ship near-duplicate modules for speed optics

**Hard twin:** jscpd/pmd/cpd in CI (warn then gate); periodic consolidation issues.

## C8 — Agent runtime safety

**Must**

- Least-privilege tokens
- No unsanitized PR/issue text into shell-driving prompts
- Hooks/permissions for destructive commands
- Human gate for prod-touching actions

**Must not**

- Eval model output with write credentials
- Agents holding prod cloud keys by default

**Hard twin:** sandbox settings, hook configs, OIDC short-lived creds, environment protection rules.

## C9 — Metrics and governance

**Must**

- Report review time, incident/PR, churn, zero-review rate beside throughput
- Team norms for when agents are allowed and what "done" means
- Provenance labels for AI-assisted changes where feasible

**Must not**

- Manage by LOC or AI-adoption % alone
- Cut review capacity because generation rose

**Hard twin:** dashboards; release health gates; SLO on change-fail rate.

## C10 — Human accountability

**Must**

- Named human owns merge and on-call consequences
- Author self-reviews agent output before requesting review
- Assistance disclosed when policy requires (`Assisted-by`, label, trailer)

**Must not**

- "The model LGTM'd it" as sign-off
- Agent DCO / legal ownership marks

**Hard twin:** required human approvals; disable self-approve on critical repos; DCO bot if used.
