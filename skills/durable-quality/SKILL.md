---
name: durable-quality
description: "Quality baseline for code changes: state intent first, reuse existing patterns, and verify in proportion to risk before calling work done. Also covers repo quality audits, CI safeguards, agent-PR review, and writing AGENTS.md rules. Use when writing, changing, or reviewing code, or when asked to audit or harden a repository."
license: MIT
---

# Durable quality

Keep changes scoped, maintainable, and backed by evidence. Project instructions and the user's intent come first. This skill does not authorize deploys, unrelated cleanup, or new repository policy.

## Before editing

- State the expected behavior and any assumption you are relying on. Ask only if a missing answer blocks a sound decision.
- Reuse existing helpers and patterns. No speculative features, no unrelated refactors.
- Keep diffs small and bisectable: one intent per commit.

## Standing rules

- Preserve architecture boundaries, stable interfaces, and meaningful tests.
- Never weaken CI or hollow out a test to get green.
- Protect secrets and user data. Auth, payments, migrations, and deletion need stronger verification.
- Follow the project's own ownership and release process. Do not add a new approval step to an ordinary task.

## Verify in proportion to risk

Find the relevant checks in the project's instructions, scripts, or CI, and run the ones that exercise your change.

| Change | Proof |
|---|---|
| Docs, comments | Inspect, lint if applicable |
| Ordinary logic | Focused unit test or check |
| Bug fix | Regression test that fails without the fix, when a reliable repro is practical |
| API or service boundary | Contract or integration test |
| Parsers, state machines, money math, migrations | Property, fuzz, or boundary cases plus units |

Stop once the relevant checks pass, unless new evidence shows a gap. Report what changed, what you verified, and what remains unverified. Never claim success for incomplete work.

## Related skills

- `karpathy-guidelines`: surgical, non-speculative edits. Use together with this skill when implementing or refactoring.
- `principle-*` skills: situational playbooks (root-cause fixes, idempotent operations, type-system discipline, verifiable units, boundary discipline, and others). Read one only when the work matches its name.

## Deeper modes

Use these only for an explicit audit, safeguard, policy, or review request. Read just the listed files.

| Mode | Goal | Read |
|---|---|---|
| Audit repo quality | Score C1-C10, list top risks, propose a minimal fix order | `checklists/audit.md`, `references/constraint-packs.md`, `references/ai-failure-modes.md` |
| Bootstrap quality harness | Pick the minimum checks and ownership rules | `playbooks/bootstrap-harness.md`, `references/proof-ladder.md`, `references/constraint-packs.md` |
| Write agent laws | Lean `AGENTS.md` / `CLAUDE.md` rules with hard CI twins | `playbooks/laws-for-agents.md`, `examples/AGENTS-quality-section.md`, `examples/pr-template.md`, `checklists/agent-pr-gate.md` |
| Review a change (especially agent PRs) | Fast gate, then code-health review | `checklists/agent-pr-gate.md`, `checklists/code-health-review.md`, `references/oss-patterns.md` |
| Encode architecture as code | Turn boundaries into failing tests or CI rules | `playbooks/architecture-as-code.md`, `references/constraint-packs.md`, `references/principles.md` |

`references/principles.md` has the five-loop model, and `references/proof-ladder.md` has risk tiers and mutation-testing notes.
