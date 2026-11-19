# Delegation

Read when work could be split across agents, or before handing any task to another agent. Brief template: [brief.md](brief.md).

## Rules

1. **One agent by default.** Add workers only when the work is independent, parallel, and too big for one context. Multi-agent setups help on parallel work and hurt on sequential work, and they cost far more tokens. Most coding has fewer parallel parts than research.
2. **Delegate to protect context.** The main reason to hand off is to keep exploration out of your own context and get back a short result.
3. **One writer.** One agent writes a given file or module at a time. Parallelize reading, searching, reviewing, and verifying freely. Parallel writers make conflicting hidden choices even when the text merges cleanly. Split writing only along disjoint files, each claimed by one worker.
4. **Every brief is complete.** The worker sees none of your context. It gets the objective, the output format, the tools and sources to use or avoid, and the task boundary, plus the done-when check, the gate row, and the decisions already made ([brief.md](brief.md)). Complete is not long: point to project notes instead of restating them.
5. **Right amount of context.** Writers get the full decision record. Read-only workers get the question and its constraints. (The split is inference.) Point to files and commits for anything that must be exact; summaries lose detail.
6. **Results come back as files.** Workers write output to a file and return the path and a short summary. Failed attempts: one line each.
7. **Accept evidence, not claims.** Check the diff, the test output, the repro that now passes.

## When there are no named roles

- **Generic or identical agents:** put the role in each brief. Give reviewer and verifier a fresh agent with the spec and diff, not the author's context.
- **One agent only:** play the roles in sequence. Spec, implement, then re-read the diff as a reviewer against the criteria, then run it as a verifier. At T1+, your own review does not count as the independent one: start a fresh-context reviewer (a new session given only spec, diff, and output) if the environment allows. If it does not, record "independent review: not met" and hand the change to a person ([review/index.md](../review/index.md)).
- A single agent also runs the two-round check on itself ([roles/coordinator.md](../roles/coordinator.md)) and pauses for a person when it needs a decision it cannot make. Same savings on its own checks: focused tests while working, re-check from the delta and widen per [review/index.md](../review/index.md), the row's gates on the final candidate ([testing/index.md](../testing/index.md)).
- A weaker agent often does not know when to escalate. Every brief states its stop rule.

## Splitting

1. List the units and what each depends on.
2. Fix shared decisions first (names, data shapes, interfaces, style) and copy them into each brief that needs them.
3. Give each unit one owner, one isolated workspace, and one branch.
4. Size each unit for one review, and give it a size expectation and a retry cap.
5. Combine results in dependency order and test the combined result ([integrate-release/index.md](../integrate-release/index.md)). No source sets a merge order; this one is inference.

## Anti-patterns

- Many agents for a task one agent could finish in about the same time.
- Parallel writers on shared code.
- Assuming the worker shares your state, or that it will report discoveries without being asked.
- Retry loops with no cap.
- A cold, full re-verify after every fix round, or verifying each stacked slice while earlier ones still change.
- A delta-only re-verify after a fix to shared code, which never runs the unchanged consumers.
- A verifier that only reads the author's report.

## Done when

- [ ] Each extra agent buys parallel breadth, clean context, or a cheaper tier for routine work.
- [ ] No two tasks write the same file at the same time.
- [ ] Shared decisions are fixed and copied into every brief that needs them.
- [ ] Every brief is complete per [brief.md](brief.md), including a stop rule.
