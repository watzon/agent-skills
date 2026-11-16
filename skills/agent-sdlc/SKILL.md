---
name: agent-sdlc
description: "Read before writing, changing, reviewing, testing, or handing off code, before delegating work to another agent, and before auditing a repo."
license: MIT
---

# Agent SDLC

This file is a router. Read only the files your current step needs. Project instructions and the user's intent override this skill.

## Always

- Pick a risk tier before starting (table below). Unsure: go one tier up.
- Never delete, weaken, or special-case a test to get green. If a test looks wrong, stop and report it.
- Evidence over claims: command output, a test that failed before and passes after, the diff.
- Stay inside the spec. Put unrelated findings in the report, not the diff.
- Follow the environment's rules on who may merge, push, deploy, or delete.

## Risk tiers

| Tier | Examples | Tests | Review | Human |
|---|---|---|---|---|
| T0 | Typos, comments, docs | None new; lint | CI only | No |
| T1 | Local bugfix, internal refactor | Repro + regression | 1 clean-context reviewer, max 2 rounds | No |
| T2 | Public interface, data shape, concurrency, parsers, multi-file | + integration, contract, or property tests | Against spec and design note, max 2 rounds; different model or human spot check | Optional |
| T3 | Auth, permissions, PII, money, migrations, deletes, infra | + adversarial and negative tests; staged rollout | Security-focused, max 3 rounds | Required |

Tiers are inference, confidence low to medium. See [SOURCES.md](SOURCES.md).

Minimum path: T0 implement, integrate. T1 adds spec (short), test, review, handoff. T2 adds design, and release if users see it. T3 runs every stage.

## Stages

| If you are... | Read |
|---|---|
| Turning a request into acceptance criteria | [01-spec/index.md](01-spec/index.md) |
| Choosing data shapes, interfaces, or a plan (T2+) | [02-design/index.md](02-design/index.md) |
| Writing or changing code | [03-implement/index.md](03-implement/index.md) |
| Writing tests or proving behavior | [04-test/index.md](04-test/index.md) |
| Reviewing a diff, yours or another agent's | [05-review/index.md](05-review/index.md) |
| Merging branches or combining parallel work | [06-integrate/index.md](06-integrate/index.md) |
| Shipping to users: changelog, rollout, rollback | [07-release/index.md](07-release/index.md) |
| Declaring done or writing a report | [08-handoff/index.md](08-handoff/index.md) |

## Roles, delegation, and the rest

| If you are... | Read |
|---|---|
| Acting as a role, or assigning roles when none are named | [roles/index.md](roles/index.md) |
| Splitting work or writing a brief for another agent | [delegation/index.md](delegation/index.md) |
| Choosing a principle for the situation (debugging, types, refactors...) | [principles/index.md](principles/index.md) |
| Seeing a warning sign: weakened test, scope creep, a loop that won't converge | [failure-modes/index.md](failure-modes/index.md) |
| Auditing a repo, adding CI safeguards, or writing AGENTS.md rules | [audit/index.md](audit/index.md) |
