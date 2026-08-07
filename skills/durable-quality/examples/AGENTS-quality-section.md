# Quality bar (paste into AGENTS.md)

Copy and adapt. Keep the root file lean. Every rule below must match real CI or hooks.

## Commands

```bash
# adjust to the repo
pnpm install
pnpm lint
pnpm typecheck
pnpm test
pnpm test:unit -- path/to/file
pnpm check:deps   # architecture fitness, if present
```

Run the focused tests relevant to your change before claiming done.

## Definition of done

A change is done only when all of the following hold:

1. Intent is clear (what problem, what non-goals)
2. Proof exists: commands run + outcomes captured in the PR
3. Behavior changes include a regression that fails without the change
4. Lint, types, tests, and dependency checks pass locally
5. CI is not weakened (no skip, no `|| true`, no coverage floor drop) in this PR
6. Code health is improved or held: no new clone of an existing helper, no new illegal dependency, no drive-by reformat mixed with logic
7. A human is ready to own merge and production consequences

## Refusals

Do not:

- Edit CI workflows or required checks to obtain green in a feature PR
- Delete or hollow out tests to pass
- Commit secrets or `.env` files
- Add near-duplicate utilities without searching for an existing one
- Touch `auth/`, `billing/`, or `migrations/` without tier-appropriate tests and human review in mind
- Open bulk cosmetic PRs
- Claim done without running the relevant checks

## Critical paths (example map)

| Path | Tier | Extra expectation |
|---|---|---|
| `src/auth/**` | T4 | Owner review; tests for deny paths |
| `src/billing/**` | T4 | Owner review; money math tests |
| `migrations/**` | T4 | Expand/contract safe; rollback note |
| `src/domain/**` | T2–T3 | No framework imports if dependency rule enabled |
| `docs/**` | T0 | Lint only |

## Architecture

Dependency rule for this repo (example):

- `src/domain/**` must not import `src/api/**` or `src/infra/**`
- `src/api/**` may import domain and application services
- Run `pnpm check:deps` after structural edits

## PR notes for agents

Include in the PR body:

- Summary of intent
- Plan / approach
- Commands run (paste output tails)
- Risks and tier of paths touched
- Follow-ups intentionally deferred

Human reviewers apply an agent PR gate before deep review. Make their job easy.
