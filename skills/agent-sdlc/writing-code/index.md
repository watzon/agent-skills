# Writing code

Read when writing or changing code. Written for the implementer. Comments have their own file: [comments.md](comments.md).

## Rules

1. **Smallest complete change.** Every changed line traces to the task. No features, options, or settings nobody asked for. No handling for errors that cannot happen. If the result is far longer than the problem deserves, rewrite it shorter.
2. **No speculative abstraction.** No layer, interface, or helper for one caller or for a future nobody asked for. Add one when it removes real duplication or hides a real decision. Three similar lines beat a premature helper.
3. **Reuse before writing.** Search for an existing helper first and extend it. Agent changes tend to add near-duplicates.
4. **Fix the root cause.** A guard that only silences a symptom (a null check, a catch, a retry) is not a fix. See [principles/operations.md](../principles/operations.md).
5. **Surgical.** Match local style. Do not reformat, rename, or "improve" nearby code. Cleanup and refactors go in their own commit or change, not inside a feature diff.
6. **Dead code.** Delete what your change orphaned: imports, helpers, branches, flags. Report older dead code; remove it in a separate change.
7. **Greppable names.** Use the codebase's existing term for a concept. Prefer a specific name a search will find over a generic one (`data`, `handle`, `util`, `manager`). A name that carries the meaning beats a comment that explains it. (Weak direct evidence; mostly inference.)
8. **Readable, not clever.** No terse "golfed" code in the codebase, even if you write throwaway scripts that way.
9. **Every API you call exists.** Prove it with the typechecker or a search, not memory.
10. **One unit at a time.** Make one change, run its check, then continue. Never batch edits and check once at the end.
11. **Stop instead of thrashing.** After two failed attempts at the same approach, stop and report what you tried. (Inference.)

## Before the first edit

- Have acceptance criteria ([spec/index.md](../spec/index.md)). For a bug, have a failing repro ([testing/index.md](../testing/index.md)).
- Read the code you will change and its callers. Find the project's build, lint, typecheck, and test commands.

## Commits and PR text

- History and reasons live here, not in the code: what changed, why, how it was proven (commands and output), risk, and how to revert.
- One intent per commit. Each commit builds. Mechanical changes (renames, moves, formatting) apart from behavior changes.
- Order commits as an argument: failing test, then fix; removal, then addition.

## Done when

- [ ] Every acceptance criterion has code that implements it, and nothing else was added.
- [ ] No new helper duplicates an existing one; no orphaned code is left.
- [ ] No unrelated edits; cleanup, if any, is in its own commit.
- [ ] Build, lint, and typecheck pass, with output captured.
- [ ] You re-read the whole diff, including comments, before handing off.
