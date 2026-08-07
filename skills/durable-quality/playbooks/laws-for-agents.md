# Laws for agents playbook

Write policy agents can follow and machines can enforce.

## Split soft vs hard

| Soft (context) | Hard (enforcement) |
|---|---|
| AGENTS.md, CLAUDE.md, cursor rules | CI required checks, hooks, branch protection, CODEOWNERS |
| Style essays, rationale | Formatters, linters, typecheckers |
| "Prefer reuse" | Clone detectors, review reject |
| "Don't touch auth lightly" | Path owners + extra CI |

If a rule matters, give it a hard twin or accept it will be violated under pressure.

## Drafting order

1. List commands that must work: install, build, test, lint, typecheck
2. List forbidden paths and actions
3. List quality bar for "done" (proof evidence)
4. List explicit refusals
5. Map critical paths and tiers
6. Only then write prose principles (short)

## Lean root doc

Prefer under ~200 lines at repo root. Put deep conventions in path-scoped rules or contributing docs.

Agents drown in contradictory novels. Precision beats inspiration.

## Must include

- Exact commands (copy-pasteable)
- Where tests live and how to run a focused subset
- Definition of done: proof + no CI weaken + health direction
- Refusals list (from SKILL.md)
- Pointer to CODEOWNERS / who to ping
- "Human owns merge" statement

## Must never include

- Secrets, tokens, private URLs with embedded creds
- Unenforceable absolute claims ("always write perfect clean code")
- Instructions that conflict with CI
- Permission to skip hooks on mainline work

## Runtime hard stops

When the agent runtime supports hooks/permissions:

- block raw prod deploy credentials
- block `git push` to main if policy says so
- block edits under `vendor/` or generated paths
- require approval for `rm -rf`, force push, schema drop

Claude Code note: memory files are context; PreToolUse hooks enforce.

## Dual-tool repos

If both Codex and Claude (etc.) are used:

- keep AGENTS.md as the portable core
- import or symlink into tool-specific files
- avoid drift: one source of command truth

## Verification

After writing laws:

1. Break a stated rule on a branch
2. Confirm CI or hook catches it
3. If not caught, either add a hard twin or remove the lying soft rule

## Templates

- `examples/AGENTS-quality-section.md`
- `examples/pr-template.md`
