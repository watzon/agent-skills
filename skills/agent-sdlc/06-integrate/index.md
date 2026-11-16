# 06 Integrate

Read when merging a branch, combining work from parallel agents, or landing a reviewed change.

## Steps

1. **Check authority.** Follow the environment's rules on who may merge or push, and to which branch. If you may not merge, stop at a ready branch or pull request and say so.
2. **Rebase or merge onto current trunk.** Resolve conflicts by understanding both sides; never by dropping the other side's tests.
3. **Combine parallel work in dependency order.** Interfaces and shared types first, then their users. One writer per file; if two branches touched the same file, re-review the combined result.
4. **Run the full suite** (CI or local equivalent) on the combined result, not only on each branch alone.
5. **Check the diff once more** against trunk: nothing unexpected came in during the rebase.
6. **Land** only with green checks and zero open blocking findings.
7. **Clean up** branches and temporary workspaces you created, if the environment allows.

## When integration breaks

- A test that passed on the branch fails after rebase: treat it as a new bug. Find which change caused it ([fix-root-causes](../principles/fix-root-causes.md)); do not patch over it.
- Conflicting assumptions between parallel workers (names, data shape): stop, pick one with the coordinator, and fix both sides. See [failure-modes](../failure-modes/index.md) (integration regression).

## Done when

- [ ] You have authority to land, or you stopped at a ready branch and reported it.
- [ ] Branch is current with trunk.
- [ ] Full suite passes on the combined result, with output captured.
- [ ] No open blocking findings.
- [ ] Temporary branches and workspaces you created are cleaned up or listed.
