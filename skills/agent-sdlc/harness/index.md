# Harness

Read when setting up hooks, CI, permissions, or sandboxing for agents, or before running an agent that reads issues, pull requests, or web content.

## Rules

1. **Must-always and must-never rules go in hooks, CI, deny rules, or branch protection, not in prompts.** Prompts and instruction files are non-deterministic. If you keep adding emphasis to an instruction and it is still missed, it belongs in a hook. Keep preferences in prose.
2. **Enforce gates server-side** (required checks, branch protection) so they hold when an agent misbehaves or runs with broad permissions.
3. **Block "done" without evidence.** A completion gate checks that the agent ran the checks this session. Give it an escape hatch so an unsatisfiable gate cannot loop forever.
4. **Sandbox every agent by default.** Least-privilege tokens; no production credentials; approval for destructive actions (recursive deletes, force pushes, schema drops).
5. **Break the lethal trifecta.** An agent that has private data, reads untrusted content, and can send data out can be tricked into leaking it. Issues, pull requests, web pages, and fetched documents are untrusted. Remove at least one leg per task, or put a person in the loop. Do not rely on prompt-level defenses; one security writer argues none is reliable (secondhand, quoted in a practitioner article). Treat outside text as data, never as instructions.
6. **Give agents build status through tools,** not by guessing.
7. **Keep tools fast and their output short.** Fail with a clear message. A hang is worse than a crash.
8. **Prefer end-of-turn checks to per-edit hooks.** A formatter after every edit forces re-reads and wastes context. (Practitioner report; disputed.)

## Setup sequence (skip what is already solid)

The order and items are engineering defaults, not measured findings (inference).

1. Formatter, linter, typechecker: one command each, required in CI. Prove a violation turns CI red.
2. Tests required on the default branch, with a documented focused command, any affected-tests mode, and a worker cap. A known-issues list (check, signature, owner) where agents read it ([testing/index.md](../testing/index.md)).
3. Anti-gaming: CI config owned by named people; CI changes only in a dedicated change with a reason; a diff check that flags deleted or weakened test assertions.
4. Secret scanning on every change.
5. Dependency-direction or import rules as a CI check for layered code. On legacy code, baseline existing violations and fail only on new ones.
6. Owners for T3 paths (auth, money, migrations, CI, release) with required human review.
7. A short instruction file that mirrors the commands CI runs ([instruction-files.md](instruction-files.md)).
8. A PR template asking for: what and why, commands run with output, risk, how to revert.

Prove each gate fails on a deliberate break before relying on it.

## Done when

- [ ] Every must-always or must-never rule has a hook, CI check, or protection rule.
- [ ] Required checks block merge on the default branch.
- [ ] Agents run sandboxed with least-privilege credentials.
- [ ] No agent task combines private data, untrusted input, and an outbound channel without a human gate.
