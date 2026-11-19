# Integrate and release

Read when merging a branch, combining work from parallel agents, or shipping a change to users.

## Integrate

1. **Check authority.** Follow the environment's rules on who may merge or push, and where. If you may not merge, stop at a ready branch or pull request and say so.
2. **One writer per branch or workspace.** Parallel agents read and review; they do not write the same branch.
3. **Update onto current trunk.** Resolve conflicts by understanding both sides; never by dropping the other side's tests.
4. **Combine in dependency order:** shared types and interfaces first, then their users, with focused checks on each intermediate combination. (Inference; no source sets a merge order.)
5. **Run the repository's configured integration gate on the final combined candidate,** not only on each branch alone. Anything that actually lands on trunk along the way runs its required gates first. If the gate fails or the candidate changes, rerun the required gates ([testing/index.md](../testing/index.md)). (Inference: no source tested full-suite-at-integration against alternatives.)
6. **Verify stacked work once it is stable.** Each author runs focused checks on its slice. Review and verify the stable combined candidate in full once its branches stop changing, not each slice while earlier ones still move; a change below invalidates the checks above it. (Owner observation plus inference.)
7. **Land only** with green checks and zero open blocking findings.
8. **Auto-merge only in the lowest-risk tier,** with proof and a rollback path. Otherwise a person approves. (Tier design is inference; practice differs, see [SOURCES.md](../SOURCES.md).)

## Parallel workspaces

One team's report from real runs (small sample):
- Give each worker its own database, ports, and other shared state.
- Workers do not pull trunk into themselves; the trunk takes from workers, and a stale worker is restarted fresh.
- Resolving a conflict changes a commit's identity: compare branches by content (for example `git range-diff`, `git cherry`) before deleting one.
- Remove a workspace only after it has no unapplied commits and no uncommitted changes.

## Long-running work

Each session does one unit, commits with a clear message, updates the progress file or feature list, and leaves the tree clean for the next session.

## Release (thin: no sources were read on this; all inference)

- **Changelog:** one line per user-visible change; call out breaking changes.
- **Rollback:** write the exact undo steps. No rollback: get a person's approval first.
- **Migrations:** expand, then contract. Every step safe to re-run ([principles/operations.md](../principles/operations.md)).
- **T3 or user-facing risk** (auth, money, data): ship behind a flag or to a small cohort first, with a stop signal defined before starting.
- **After release:** exercise the real path in the target environment, or say exactly what you could not check. Observability for agent-written code was not researched.
- Never deploy, tag, or publish without the authority the environment grants.

## Done when

- [ ] You had authority to land, or stopped at a ready branch and reported it.
- [ ] The integration gate passed on the final combined candidate, with output captured; anything landed earlier passed its required gates.
- [ ] No open blocking findings.
- [ ] Stacked work was verified in full as a combined candidate after its branches stopped changing.
- [ ] Workspaces you created are removed or listed, with no unapplied commits lost.
- [ ] User-facing changes have a changelog line and rollback steps.
