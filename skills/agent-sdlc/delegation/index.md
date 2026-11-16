# Delegation

Read when work could be split across agents, or before handing any task to another agent.

## One agent or many

Default to one agent. Add agents only when they buy something:
- **Breadth:** independent searches, reading many files, comparing options.
- **Clean-context review or verification.**
- **A cheaper tier** for routine, well-specified work.

Before spawning, ask: could one agent do this in about the same time? If yes, don't. Multi-agent runs cost far more tokens than one agent (about 15x chat in one vendor measurement, [SOURCES.md](../SOURCES.md)). Most coding work has fewer parallel parts than research.

## Writes stay single-threaded

- One writer per file, module, or interface at a time. Parallel writers make conflicting hidden decisions even when the text merges cleanly.
- Parallelize reading, searching, and reviewing freely.
- Split writing only along disjoint files, or along an interface fixed in advance. If two tasks must touch one file, run them in sequence.

## Splitting

1. List the units of work and what each depends on.
2. Fix shared decisions first (names, data shapes, interfaces, style) and put them in every brief that needs them.
3. Give each unit one owner, one isolated workspace, and one branch.
4. Size each unit for one review (about 200 changed lines, 400 at most).
5. Give each task a size expectation and a retry cap.

## Context and cost

- The worker sees nothing of your conversation. Write a full brief: [brief.md](brief.md).
- Pass decisions and pointers, not transcripts. For anything that must be exact, point to the file, line, or commit; summaries lose detail.
- Don't delegate what a single search answers.
- Cheap tiers for reading and routine edits; the strongest tier for planning, review, and hard bugs.

## Collecting results

- Accept evidence, not claims: diff, test output, a repro that now passes.
- At most two fix-and-recheck rounds per task, then escalate to a stronger agent or a person.
- Integrate in dependency order and test the combined result ([06-integrate](../06-integrate/index.md)).

## Anti-patterns

- Parallel writers on shared code.
- More hand-offs than work; each one loses detail.
- Telephone-game summaries that drop constraints.
- Retry loops with no cap.
- Many agents for a simple task.
- A verifier that only reads the author's report.

## Done when

- [ ] Each delegated task is worth an extra agent (breadth, clean context, or cheaper tier).
- [ ] No two tasks write the same file at the same time.
- [ ] Shared decisions are fixed and copied into every brief that needs them.
- [ ] Every brief has all six parts from [brief.md](brief.md).
- [ ] Each task has a size expectation, a retry cap, and a stop rule.
