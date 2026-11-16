# 04 Test

Read when writing tests or proving that a change works.

## Rules

1. **Repro first for bugs.** Write a test that fails on current behavior, run it and see it fail, fix, then see it pass. Keep it as the regression test.
2. **Tests must fail when the code is broken.** For each new test ask: would it pass with the fix reverted? Would it pass if the core logic were inverted? If yes, it proves nothing.
3. **Never delete, weaken, skip, or special-case a test to get green.** Models do this when spec and tests conflict ([SOURCES.md](../SOURCES.md)). If a test seems wrong, stop and report it with evidence. Any test change goes in its own commit with a reason.
4. **Green is not correct.** Check behavior against each acceptance criterion, not only the suite. Run the real feature path end to end where you can. See [prove-it-works](../principles/prove-it-works.md).
5. **Deterministic checks first**: typecheck, lint, tests. They are cheaper than review tokens.

## Proof by tier

| Tier | Minimum proof |
|---|---|
| T0 | Inspect; lint if applicable |
| T1 | Focused unit test; repro + regression for bugs |
| T2 | + contract or integration test at the boundary; property or fuzz tests for parsers, codecs, state machines |
| T3 | + negative tests (denied access, bad input, rollback path), adversarial cases, mutation sampling where tests are the only check |

## Test honesty

Healthy: asserts lock observable behavior; edge and error paths covered; fixtures small and readable.

Red flags (send back): asserts weakened right after a failure; broad catch blocks that swallow errors; mocks so heavy the test proves nothing about the system; snapshots bulk-updated without a reason; coverage floor lowered in the same change.

## Mutation, property, anomaly tests (T2+)

- **Mutation:** flip a comparison, remove a call; a good suite fails. Surviving mutants are missing tests. Use on modules where tests are the only safeguard. (Inference: results of the mutation-testing papers were not read.)
- **Property or fuzz:** use when the input space is large: parsers, serializers, permission matrices, retry logic.
- **Anomaly:** timeouts, disk full, duplicate delivery, clock skew, process killed mid-write. Pick only the ones that apply.

## Flaky tests

Quarantine and track a flaky test. Do not retry until green; that hides the signal. (Inference, no verified source.)

## Evidence to keep

For the handoff: the commands run, exit codes, the relevant tail of output, and what was **not** run and why. A script that re-runs the comparison beats a one-time look.

## Done when

- [ ] Each acceptance criterion has a test or a recorded command that proves it.
- [ ] Bug fixes have a repro test you saw fail before the fix.
- [ ] No existing test was deleted, weakened, or skipped; any change has its own commit and reason.
- [ ] Proof meets the tier's minimum.
- [ ] Command output is captured for the handoff.
