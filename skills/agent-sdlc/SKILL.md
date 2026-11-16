---
name: agent-sdlc
description: "Use when planning, delegating, writing, testing, reviewing, or handing off code, or when setting up a repo for agents."
license: MIT
---

# Agent SDLC

This file is a router. Read the files listed for your role or task. When a file you read links to another for a step you are doing, read that one too. Project instructions and the person's intent override this skill.

## The flow

Spec → write code → test → review and verify → integrate → hand off. Size every step to the risk of the change. A typo needs only the checks; an auth change needs every step and a person.

| Tier | Examples | Spec | Tests | Review | Human |
|---|---|---|---|---|---|
| T0 | Typo, docs, comment | None | Existing checks | Checks only | No |
| T1 | Local bug fix, internal refactor | Intent + criteria | Repro test per bug | One fresh-context review | No |
| T2 | Public interface, data shape, concurrency, multi-file | + design note | + integration test on the changed path | Fresh-context review against the spec | One person, where available |
| T3 | Auth, permissions, money, personal data, migrations, deletes, CI, release | + design note | + negative tests | Fresh-context review, security focus | Required |

Unsure: go one tier up. The tiers are inference built on one vendor's practice ([SOURCES.md](SOURCES.md)).

## Always

- Run the checks and show the command and its output. "Done" or "tests pass" is not evidence.
- Never delete, weaken, or skip a test to get green. If a test looks wrong, stop and report it.
- Stay inside the task. Report unrelated findings; do not fix them in this diff.
- Follow the environment's rules on who may push, merge, deploy, or delete.

## Read by role

| You are acting as | Read, in order |
|---|---|
| Orchestrator / project manager: you plan and hand work to others | [roles/coordinator.md](roles/coordinator.md), [delegation/index.md](delegation/index.md), [delegation/brief.md](delegation/brief.md), [spec/index.md](spec/index.md), [handoff/index.md](handoff/index.md) |
| Senior developer: hard, ambiguous, or design-heavy work | [roles/implementer.md](roles/implementer.md), [spec/design-note.md](spec/design-note.md), [writing-code/index.md](writing-code/index.md), [writing-code/comments.md](writing-code/comments.md), [testing/index.md](testing/index.md), [review/index.md](review/index.md), [review/checklist.md](review/checklist.md), [anti-slop/index.md](anti-slop/index.md), [handoff/index.md](handoff/index.md); building UI: [design/index.md](design/index.md) |
| Junior developer: well-specified routine work | [roles/implementer.md](roles/implementer.md), [writing-code/index.md](writing-code/index.md), [writing-code/comments.md](writing-code/comments.md), [testing/index.md](testing/index.md), [review/checklist.md](review/checklist.md), [anti-slop/index.md](anti-slop/index.md), [handoff/index.md](handoff/index.md); building UI: [design/index.md](design/index.md) |
| Designer: UI, brand, or visual work | [design/index.md](design/index.md), [design/floor-checks.md](design/floor-checks.md); new brand: [design/brand.md](design/brand.md), [design/logo.md](design/logo.md), [design/mascot.md](design/mascot.md), [design/foundations.md](design/foundations.md); [anti-slop/copy.md](anti-slop/copy.md), [anti-slop/index.md](anti-slop/index.md), [handoff/index.md](handoff/index.md) |
| Reviewer | [roles/reviewer.md](roles/reviewer.md), [review/index.md](review/index.md), [review/checklist.md](review/checklist.md), [anti-slop/index.md](anti-slop/index.md), [failure-modes/index.md](failure-modes/index.md) |
| QA / verifier | [roles/verifier.md](roles/verifier.md), [review/index.md](review/index.md), [testing/index.md](testing/index.md) |
| Researcher | [roles/researcher.md](roles/researcher.md), [harness/index.md](harness/index.md) |
| A single agent with no roles | [spec/index.md](spec/index.md), [writing-code/index.md](writing-code/index.md), [testing/index.md](testing/index.md), [review/index.md](review/index.md), [anti-slop/index.md](anti-slop/index.md), [handoff/index.md](handoff/index.md) |

## Read by task

| If you are... | Read |
|---|---|
| Turning a request or bug into work you can check | [spec/index.md](spec/index.md) |
| Changing an interface, a data shape, or several modules | [spec/design-note.md](spec/design-note.md) |
| Writing or changing code | [writing-code/index.md](writing-code/index.md) |
| Writing, keeping, or deleting a comment | [writing-code/comments.md](writing-code/comments.md) |
| Choosing types, data structures, or boundaries | [principles/design.md](principles/design.md) |
| Debugging, or building steps that retry, resume, or run in sequence | [principles/operations.md](principles/operations.md) |
| Building or changing UI | [design/index.md](design/index.md), [design/floor-checks.md](design/floor-checks.md) |
| Setting a brand where no design system exists | [design/index.md](design/index.md), [design/brand.md](design/brand.md) |
| Making a logo or a mascot | [design/logo.md](design/logo.md), [design/mascot.md](design/mascot.md) |
| Setting type, spacing, motion, or design tokens | [design/foundations.md](design/foundations.md) |
| Building or reviewing buttons, inputs, icons, or other controls | [design/components.md](design/components.md) |
| Writing UI text, docs, or reports | [anti-slop/copy.md](anti-slop/copy.md) |
| Adding compatibility code, flags, settings, placeholders, or shown numbers | [anti-slop/product.md](anti-slop/product.md) |
| Writing tests or proving a change works | [testing/index.md](testing/index.md) |
| Reviewing a diff, or deciding review is done | [review/index.md](review/index.md), [review/checklist.md](review/checklist.md) |
| Splitting work or briefing another agent | [delegation/index.md](delegation/index.md), [delegation/brief.md](delegation/brief.md) |
| Merging, combining parallel work, or releasing | [integrate-release/index.md](integrate-release/index.md) |
| Declaring done, reporting, or judging a report | [anti-slop/index.md](anti-slop/index.md), [handoff/index.md](handoff/index.md) |
| Seeing a warning sign: weakened test, scope creep, a loop | [failure-modes/index.md](failure-modes/index.md) |
| Setting up hooks, CI, sandboxing, or agents that read untrusted text | [harness/index.md](harness/index.md) |
| Writing or fixing the project instruction file (always-loaded agent instructions) | [harness/instruction-files.md](harness/instruction-files.md) |
| Auditing a repo for agent work | [harness/audit.md](harness/audit.md) |

Every claim behind these files, with its label and confidence: [SOURCES.md](SOURCES.md), [sources/anti-slop.md](sources/anti-slop.md), [sources/design.md](sources/design.md), [sources/foundations.md](sources/foundations.md), [sources/components.md](sources/components.md).
