---
name: durable-quality
version: 0.2.0
description: >
  Load this before writing any code to prevent vibe rot and ensure high-quality,
  durable output. Standing baseline for every coding session under AI-assisted
  development: proof before done, small bisectable changes, reuse over clones,
  honest tests, architecture boundaries, and human accountability. Also use for
  "make this last", "stop vibe rot", "quality harness", "code health audit",
  "laws for agents", "fitness functions", "review agent PRs", and harness setup.
  Progressive docs live beside this file; load them when the task needs depth.
license: MIT
compatibility: claude-code opencode cursor codex
---

# Durable quality

**Load this skill before writing or modifying code.** It is the default quality baseline for the session, not an optional audit mode.

Code generation is cheap. Understanding, verification, ownership, and architectural integrity are not.

**One-line law:** Code is cheap. Proof, structure, and ownership are the product.

## Standing rules (every coding task)

Apply these on every implementation, fix, refactor, and agent-driven change. Do not wait for the user to ask.

### 1. Intent before edits

- Restate the goal and non-goals in one short block when the task is non-trivial.
- If requirements are ambiguous, surface assumptions explicitly before coding.
- Prefer the smallest change that satisfies the real ask. No speculative features, no drive-by refactors, no "while I'm here" rewrites.

### 2. Prove it works

- Run the relevant lint, typecheck, and tests for the touched surface before claiming done.
- Behavior changes need a regression that **fails without the change** and passes after.
- Capture evidence: commands run and outcomes. "Should work" is not done.
- Never delete, skip, or hollow out tests to obtain green.
- Never weaken CI (`|| true`, drop coverage floors, skip lint) in the same change as a feature.

### 3. Keep the system healthy

- Every change should **improve or hold** code health. Reject changes that degrade structure for speed.
- Search for an existing helper before adding a new one. Reuse and extend beat clone-and-tweak.
- Match local style and patterns. Do not invent a parallel abstraction next to an existing one.
- Prefer clear names and small, bisectable diffs. One intent per commit/PR when practical.
- Do not mix pure reformat with behavior changes.

### 4. Respect blast radius

- Auth, payments, migrations, data deletion, permissions, and security boundaries need stronger proof and more careful review.
- Touching generated code, vendor trees, or secrets is forbidden unless the task explicitly requires it and safeguards are in place.
- Dependency and layer rules in the repo are real. Do not "just this once" import the wrong direction.

### 5. Own the result

- The human (or named owner) is accountable for merge and production consequences. Agents draft; they do not absorb liability.
- Prefer disclosing substantial AI assistance when the project tracks it (`Assisted-by`, labels, trailers).
- If the change is unsafe to verify with available tools, say so and narrow scope rather than shipping hope.

### 6. Spend surplus on proof, not sprawl

When generation is fast:

- Prefer deeper tests, edge cases, and tighter structure over larger surface area.
- Prefer small lands over mega-diffs the reviewer cannot hold in their head.
- Clean structure still matters: messy code confuses agents and humans alike.

## Session start checklist

At the beginning of coding work in a repo (first implementation turn):

1. Note how to lint, typecheck, and test (README, package scripts, `AGENTS.md`, CI).
2. Note critical paths and ownership if present (`CODEOWNERS`, OWNERS, MAINTAINERS).
3. Note architecture or dependency checks if present.
4. Work inside those constraints. If they are missing and the task is to harden the repo, use the deeper modes below.

Do not block tiny tasks on a full audit. Do block "done" claims on missing proof for the touched surface.

## Explicit refusals

Do not do these unless the user explicitly overrides with eyes open:

1. Ship untested user-visible behavior
2. Pure cosmetic churn or mass reformat mixed into behavior work
3. Break stable APIs without deprecation, flag, or design note
4. Design-by-PR for substantial features (short design gate first)
5. CI gaming or test theater
6. Bulk low-context PR spam
7. Secrets in code, logs, or agent instruction files
8. Silent architecture violations
9. Managing success by LOC or PR count
10. Claiming done without running relevant checks

## Proof ladder (quick)

| Tier | Examples | Minimum proof |
|---|---|---|
| T0 | Docs, comments | Format/lint if applicable |
| T1 | Pure logic | Unit tests + types |
| T2 | APIs, service boundaries | Contract/integration tests |
| T3 | Parsers, state machines, money math | Property/fuzz + units |
| T4 | Auth, payments, migrations, data loss | T3 + careful human review path |
| T5 | Security / multi-tenant isolation | T4 + threat notes; dual review when possible |

Default: match proof to blast radius. Details in `references/proof-ladder.md`.

## Deeper modes (load files on demand)

When the user wants harness work, audits, or policy, pick a mode and **read the linked files** before acting.

### Audit repo quality

Score C1-C10, list top risks, propose minimal fix sequence.

Read:

- `checklists/audit.md`
- `references/constraint-packs.md`
- `references/ai-failure-modes.md`

### Bootstrap quality harness

Install the minimum durable wall (tooling → CI → anti-gaming → arch → owners → agent docs).

Read:

- `playbooks/bootstrap-harness.md`
- `references/proof-ladder.md`
- `references/constraint-packs.md`

### Write laws for agents

Author lean `AGENTS.md` / `CLAUDE.md` policy with hard CI twins.

Read:

- `playbooks/laws-for-agents.md`
- `examples/AGENTS-quality-section.md`
- `examples/pr-template.md`
- `checklists/agent-pr-gate.md`

### Review a change (especially agent PRs)

Fast gate first, then code-health review.

Read:

- `checklists/agent-pr-gate.md`
- `checklists/code-health-review.md`
- `references/oss-patterns.md`

### Encode architecture as code

Turn boundaries into failing tests/CI rules.

Read:

- `playbooks/architecture-as-code.md`
- `references/constraint-packs.md`
- `references/principles.md`

## Full file index

Load any of these when the standing rules are not enough. Paths are relative to this skill root.

### References

| File | Use when |
|---|---|
| `references/principles.md` | Need the five-loop model, code-health direction, craft vs tools |
| `references/oss-patterns.md` | Need flagship OSS patterns (Linux, K8s, Google, SQLite, Chromium, TS, Rust, Go) |
| `references/ai-failure-modes.md` | Need AI-era failure modes, empirical anchors, what works in practice |
| `references/proof-ladder.md` | Need risk tiers, mutation mindset, anomaly/property testing notes |
| `references/constraint-packs.md` | Need full C1-C10 packs (must / must-not / hard twin) |

### Checklists

| File | Use when |
|---|---|
| `checklists/audit.md` | Scoring a repo and writing an audit report |
| `checklists/code-health-review.md` | Reviewing design, complexity, tests, and health direction |
| `checklists/agent-pr-gate.md` | Fast-reject protocol before deep review of agent PRs |

### Playbooks

| File | Use when |
|---|---|
| `playbooks/bootstrap-harness.md` | Installing the quality wall in order |
| `playbooks/laws-for-agents.md` | Writing enforceable agent policy (soft vs hard) |
| `playbooks/architecture-as-code.md` | Adding dependency/layer fitness functions |

### Examples

| File | Use when |
|---|---|
| `examples/AGENTS-quality-section.md` | Pasting a quality bar into `AGENTS.md` |
| `examples/pr-template.md` | Adding an evidence-required PR template |

## Five loops (memory hook)

| Loop | Job |
|---|---|
| Intent | What must be true |
| Generation | Produce code |
| Proof | Deterministic evidence |
| Structure | Boundaries, deps, complexity |
| Ownership | Named human liability over time |

Missing proof, structure, or ownership is how AI-assisted codebases slump.

## Related skills

- `karpathy-guidelines` for surgical, non-speculative edits (complementary; use together)
- `init` when bootstrapping repo agent memory
- Stack-specific skills for concrete linters and test runners

## Non-goals

- Clean Code aesthetics as religion
- 100% MC/DC on low-risk apps
- Banning AI generation
- Replacing product judgment
- Treating markdown rules as a security boundary without CI/hooks

## Source anchors

Google eng-practices; Linux coding-assistants and submitting-patches; K8s OWNERS; SQLite testing; Chromium OWNERS/CQ; TypeScript baselines and anti bulk-agent spam; Martin (Oath, Tools are not the Answer, 2026 agent constraint notes); agents.md; Willison proof standard; Osmani agentic review; GitHub agent PR guide; empirical AI-debt and AI-slop studies.

URLs and detail live in `references/ai-failure-modes.md` and `references/oss-patterns.md`.
