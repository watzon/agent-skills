# Testing

Read when writing or changing tests, or proving that a change works.

Tests are the feedback loop that stops "looks done" from being accepted. Keep them selective: each test earns its place. There is no evidenced case for skipping tests entirely.

## Rules

1. **One repro test per bug, seen failing first.** Write a test that reproduces the bug, run it, and see it fail for the stated reason. Then fix it and see it pass. Keep it as the regression test.
2. **Do not edit existing tests to make them pass.** Agents delete, weaken, or special-case failing tests, especially when spec and tests disagree. If a test looks wrong, stop and report it with evidence. A justified change to an existing test goes in its own commit with the reason.
3. **Evidence is the command and its output:** what you ran, the exit code, the relevant tail. Never "tests pass".
4. **A new test must fail when the code is broken.** Would it still pass with the fix reverted, or the core logic inverted? Then it proves nothing.
5. **Focused while working; the row's gates on the final candidate.** While working, run only the tests that cover the change: the changed files, their package, or related test files. If the repo has an affected-tests mode, use it. Before handoff, run the gates of the selected row (below) on the final candidate. Before landing, run the integration gate (usually the CI suite) on the final combined candidate. If a gate fails or the candidate changes, rerun the required gates on the new candidate. "Once" means no redundant run on an unchanged candidate, not one attempt.
6. **Green is not correct.** Check behavior against each acceptance criterion. Exercise the real feature path where you can; mocked tests do not prove the user path works.
7. **Low parallelism.** Cap test workers at a few (house default: 2 to 4). Never default to all cores or a high fixed count. Several agents often share one machine, and full-parallel runs can exhaust its memory and stall them all.

## Gates by change type

The lead picks the row and states it in the brief; a single agent picks its own. The selected row is the default for local work and for review. Required hooks and CI always run as configured and take precedence over the row. Unsure: take the stricter row. Rows are a house default (inference).

| Change | Gates that run |
|---|---|
| Docs, comments (T0) | Link or format check, if the repo has one. No local test, typecheck, lint, or build run. |
| Styling, tokens, UI copy (T0 to T1) | Lint, typecheck, and build for the touched package; focused tests for touched components; one look at each changed screen. |
| Small logic (T1) | Typecheck, lint, and build for the touched package; focused tests; the repro test. |
| Shared code, interfaces, security-sensitive (T2 to T3) | The above, plus the package or affected suite, an integration test on the changed path, negative tests at T3. |
| Release or merge to trunk | The integration gate on the final combined candidate; rerun if it fails or the candidate changes. |

## For whoever sets up the repo

- Enforce must-run checks (tests, typecheck, lint) in a hook or CI, not by instruction. See [harness/index.md](../harness/index.md).
- Block agent edits to existing tests with a deny rule or a CI diff check that flags deleted or weakened assertions.
- Name the focused test command, any affected-tests mode, the worker cap, and the integration gate command in the instruction file.
- Keep the known-issues list (below) where agents read it: a repo file or the project notes. Do not write "always run tests" there: generic instructions like that have been reported to backfire.

## Which tests earn their keep

| Test | Verdict |
|---|---|
| Repro test per bug | Always. Highest return. |
| Typecheck, lint, build | In every row except docs-only. Cheap and deterministic. |
| Integration or end-to-end on a critical path | Worth it where users or money depend on the path; costly to maintain. (Inference.) |
| Contract test at a module boundary agents change | Useful. (Inference; no source found.) |
| Property or fuzz test | For large input spaces: parsers, codecs, permission matrices. (Inference; no recent evidence.) |
| Mutation testing | A periodic sensor on changed packages, not a per-change gate. Slow. |
| Mock-heavy unit tests, one test per function, tests that mirror the implementation | Usually low value. Agents produce these easily, and some check the code against itself. (Weak evidence, partly inference.) |
| Snapshots updated in bulk without review | Usually low value. (Inference.) |

Bugs, contracts, and critical paths are the clearest cases for a new test; other tests should have a reason too. (Inference.) Do not add tests to raise a count or a coverage number; coverage is easy to inflate with shallow tests.

## Test-first

Do not require test-driven development inside the agent loop. One small experiment found no quality gain at about 3 to 8.5 times the tokens, and agents skipped or faked the red step. Use red/green when a person reviews the failing test, or when acceptance criteria are written as tests ([spec/index.md](../spec/index.md)). Either way, see each new test fail before the implementation exists.

## Flaky and known-failing checks

Quarantine and track a flaky test. Do not retry until green; that hides the signal. (Inference.)

The project keeps a short known-issues list. Each entry: the check, its signature (test name plus error text), how to confirm it, and an owner.
- A matching signature is a lead, not proof that the failure is pre-existing. Confirm it with a baseline: the same check failing the same way on the base commit, or equivalent evidence such as the base's own CI run. This is required when the diff touches the failing path or its inputs.
- Confirmed: note "known: <entry>, failing on base <commit>" and do not re-investigate it. Not confirmed: it is a finding.
- A failure that matches no entry is a finding, even if it looks flaky.
- Keep the check visibly failed in the report, and report anything new beside it. A list entry never waives a required CI check or excuses skipping one.

## Done when

- [ ] Each bug fix has a repro test you saw fail before the fix.
- [ ] No existing test was deleted, weakened, or skipped; any change has its own commit and reason.
- [ ] Each new test fails with the change reverted.
- [ ] Each acceptance criterion has a test or a recorded command, with output captured.
- [ ] Runs while working were focused and low-parallelism.
- [ ] The row's gates and required CI ran on the final candidate; none reran on an unchanged candidate.
- [ ] Each failure is a finding, or a known-issues entry confirmed failing the same way on the base.
