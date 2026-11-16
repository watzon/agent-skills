# Quality harness

Install the minimum safeguards that make agent-written changes safe to land. One small change per step. Prove each gate fails closed.

## Sequence (skip steps already solid)

1. **Floor:** formatter, linter, typechecker, each one command, run in CI on every change. Negative proof: a lint violation turns CI red.
2. **Tests required** on the default branch. Document how to run a subset. Negative proof: a failing test blocks merge.
3. **Anti-gaming:** CI config owned by named humans; CI weakening only in a dedicated change with a stated reason. Negative proof: a feature change that makes a required job non-blocking is rejected.
4. **Secrets and static analysis** on every change; secret files ignored and scanned.
5. **Architecture as code** (layered codebases): see below.
6. **Ownership:** map T3 paths (auth, money, migrations, infra) to owners with required review.
7. **Agent instructions:** a lean file mirroring the commands CI runs ([agents-md.md](agents-md.md)).
8. **Pull request template** with intent, commands run with output, risks, tier, rollback.
9. **Metrics:** make review time, change-fail rate, and zero-review merges visible. A monthly manual snapshot beats nothing.
10. **Mutation or property tests** on one critical package, nightly at first. Track surviving mutants as missing tests.

## Architecture as code

Diagrams do not constrain agents; failing checks do.

1. Name 3 to 10 real boundaries: dependency direction (app → domain ← infra), public vs internal package API, no UI importing data access, no cycles.
2. Pick the stack's import or dependency rule checker (or module visibility, or a small custom script).
3. Legacy mess: baseline existing violations and fail only on new ones (a ratchet). Never block all work on day one.
4. Run it in CI, fast enough to be required, with error messages an agent can act on.
5. Document the direction and the local command in the agent file, plus "do not disable this rule in feature changes."
6. Negative proof: add an illegal import on a throwaway branch; CI must fail.

Match ceremony to size: no full layered architecture for a script-sized repo. Keep large mechanical changes separate from behavior changes.

## Done when

- [ ] Required checks block merge on the default branch.
- [ ] At least one architecture or ownership gate covers critical paths.
- [ ] Each gate was shown to fail on a deliberate break.
- [ ] The agent file claims no rule that CI does not enforce.
- [ ] Named people own the T3 paths.

## Don't

Add 50 rules on day one; gate on mutation score before the suite is honest; write a 2,000-line agent file; fake green with skipped jobs.
