# Testing

Read when writing or changing tests, or proving that a change works.

Tests are the feedback loop that stops "looks done" from being accepted. Keep them selective: each test earns its place. There is no evidenced case for skipping tests entirely.

## Rules

1. **One repro test per bug, seen failing first.** Write a test that reproduces the bug, run it, and see it fail for the stated reason. Then fix it and see it pass. Keep it as the regression test.
2. **Do not edit existing tests to make them pass.** Agents delete, weaken, or special-case failing tests, especially when spec and tests disagree. If a test looks wrong, stop and report it with evidence. A justified change to an existing test goes in its own commit with the reason.
3. **Evidence is the command and its output:** what you ran, the exit code, the relevant tail. Never "tests pass".
4. **A new test must fail when the code is broken.** Would it still pass with the fix reverted, or the core logic inverted? Then it proves nothing.
5. **Scoped while working, full at the boundary.** Run the tests for what you changed as you go; run the full suite when shared code changes and before integration.
6. **Green is not correct.** Check behavior against each acceptance criterion. Exercise the real feature path where you can; mocked tests do not prove the user path works.

## For whoever sets up the repo

- Enforce must-run checks (tests, typecheck, lint) in a hook or CI, not by instruction. See [harness/index.md](../harness/index.md).
- Block agent edits to existing tests with a deny rule or a CI diff check that flags deleted or weakened assertions.
- Name the scoped test command and the full-suite trigger in the instruction file. Do not write "always run tests" there: generic instructions like that have been reported to backfire.

## Which tests earn their keep

| Test | Verdict |
|---|---|
| Repro test per bug | Always. Highest return. |
| Typecheck, lint, build | Always on. Cheap and deterministic. |
| Integration or end-to-end on a critical path | Worth it where users or money depend on the path; costly to maintain. (Inference.) |
| Contract test at a module boundary agents change | Useful. (Inference; no source found.) |
| Property or fuzz test | For large input spaces: parsers, codecs, permission matrices. (Inference; no recent evidence.) |
| Mutation testing | A periodic sensor on changed packages, not a per-change gate. Slow. |
| Mock-heavy unit tests, one test per function, tests that mirror the implementation | Waste. Agents produce these easily, and some check the code against itself. |
| Snapshots updated in bulk without review | Waste. (Inference.) |

Add a test for a bug, a contract, or a critical path. Do not add tests to raise a count or a coverage number; coverage is easy to inflate with shallow tests.

## Test-first

Do not require test-driven development inside the agent loop. One small experiment found no quality gain at about 3 to 8.5 times the tokens, and agents skipped or faked the red step. Use red/green when a person reviews the failing test, or when acceptance criteria are written as tests ([spec/index.md](../spec/index.md)). Either way, see each new test fail before the implementation exists.

## Flaky tests

Quarantine and track a flaky test. Do not retry until green; that hides the signal. (Inference.)

## Done when

- [ ] Each bug fix has a repro test you saw fail before the fix.
- [ ] No existing test was deleted, weakened, or skipped; any change has its own commit and reason.
- [ ] Each new test fails with the change reverted.
- [ ] Each acceptance criterion has a test or a recorded command, with output captured.
