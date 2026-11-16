# 03 Implement

Read when writing or changing code against a spec.

## Before the first edit

- Have acceptance criteria ([01-spec](../01-spec/index.md)). For a bug, have a failing repro first ([04-test](../04-test/index.md)).
- Read the code you will change and its callers. Find the project's build, lint, typecheck, and test commands.
- Search for an existing helper before writing one. Reuse beats a near-duplicate.

## While editing

- **Smallest complete change.** No features, options, or configurability nobody asked for. No error handling for cases that cannot happen. If 200 lines could be 50, rewrite.
- **Surgical.** Every changed line traces to the spec. Match local style even if you would do it differently. Do not reformat, rename, or "improve" nearby code.
- **Clean only your own mess.** Remove imports, variables, and helpers your change made unused. Mention pre-existing dead code; do not delete it unless asked.
- **No new abstraction for one caller.** Add one when it hides a real decision or removes real duplication. See [laziness-protocol](../principles/laziness-protocol.md).
- **Verify every API you call exists**: grep it or let the typechecker prove it.
- **Unit by unit.** Make one change, run its check, then move on. Never batch edits and check once at the end. See [sequence-verifiable-units](../principles/sequence-verifiable-units.md).
- **Debugging?** Reproduce, then ask "why" until the root cause. No guard that only silences the symptom. See [fix-root-causes](../principles/fix-root-causes.md).
- **Stuck?** After two failed attempts on the same approach, stop and report what you tried. Do not thrash.

## Commits

- One intent per commit. Each commit builds and passes. Mechanical changes (renames, moves, formatting) go in separate commits from behavior changes.
- Test changes go in their own commit with the reason in the message.
- Order commits so they read as an argument: failing test, then fix; removal, then addition.

## Self-review before handing off

Read your own full diff as a reviewer would ([05-review](../05-review/index.md) checklist). Look for: files outside scope, debug leftovers, weakened tests, missing tests for a criterion.

## Done when

- [ ] Every acceptance criterion has code that implements it.
- [ ] Diff stays inside the scope allowlist, or the extra is justified in the report.
- [ ] Build, lint, and typecheck pass, with output captured.
- [ ] No unused code left by your change; no unrelated edits.
- [ ] Commits are single-purpose and each one passes.
- [ ] You re-read the whole diff.
