# Writing agent rules (AGENTS.md)

Write rules agents can follow and machines can enforce. Instruction files are context, not enforcement.

## Every soft rule needs a hard twin

| Soft (text) | Hard (enforcement) |
|---|---|
| Agent instruction files | Required CI checks, hooks, branch protection, ownership files |
| Style guidance | Formatter, linter, typechecker |
| "Prefer reuse" | Duplication detector, review reject |
| "Be careful with auth" | Path owners plus extra CI on those paths |

If a rule matters, give it a hard twin or expect it to be broken under pressure. If you cannot enforce it and it is not essential, delete it.

## Drafting order

1. Commands that must work: install, build, test, focused test, lint, typecheck. Copy-pasteable.
2. Forbidden paths and actions (generated code, vendored code, secrets, pushing to trunk if policy says so).
3. Definition of done: proof required, no CI weakening, code health held.
4. Refusals (below).
5. Critical paths and their tier and owner.
6. Only then, short prose principles.

Keep the root file under about 200 lines. Put local detail in path-scoped files. Precision beats inspiration.

## Template

```
## Commands
<install> / <lint> / <typecheck> / <test> / <test one file> / <dependency check>

## Done means
1. Intent stated (problem, non-goals)
2. Commands run, output in the PR
3. Behavior changes include a test that fails without the change
4. Lint, types, tests, dependency checks pass
5. CI not weakened in this change
6. No new clone of an existing helper; no formatting mixed with logic
7. A named person owns the merge

## Refusals
- Do not edit CI or required checks to get green in a feature change
- Do not delete or hollow out tests
- Do not commit secrets or env files
- Do not add a helper without searching for an existing one
- Do not touch <critical paths> without tier-appropriate tests and owner review
- Do not claim done without running the relevant checks

## Critical paths
| Path | Tier | Owner | Extra |

## Architecture
<dependency direction, one paragraph>; run <check> after structural edits.
```

## Never include

Secrets or URLs with credentials; unenforceable absolutes ("always write perfect code"); rules that contradict CI; permission to skip hooks on mainline work.

## Runtime hard stops (where the agent runtime supports them)

Block production credentials, pushes to protected branches, edits to generated or vendored paths; require approval for recursive deletes, force pushes, and schema drops.

## Several agent tools in one repo

Keep one portable core file and import or link it from tool-specific files. One source of truth for commands.

## Done when

- [ ] Every command in the file runs as written.
- [ ] Every rule has a hard twin, or is essential judgment with an example.
- [ ] A deliberate break of a stated rule was caught by CI or a hook; uncaught rules were enforced or removed.
- [ ] No secrets; root file under about 200 lines.
