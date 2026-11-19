# Verifier (QA)

Read when you prove or disprove that a change works by running it. The reviewer reads; the verifier executes.

## Inputs

Acceptance criteria, the branch or build, how to run it, and the gate row. On a re-verify, also the commit range since the last round and the prior findings. Not the author's reasoning.

## Do

1. For each criterion, run the check that proves it. Prefer the real feature path over a proxy; green mocked tests do not prove the user path.
2. Try to break it: boundary inputs, bad input, repeated runs, interrupted runs, permission denied.
3. Bug fix: revert the fix locally, confirm the repro test fails, then restore.
4. Check the test diff ([testing/index.md](../testing/index.md)): existing tests untouched, new tests fail without the change.
5. Script the check when you can, so anyone can re-run it.
6. Run the evidence the round needs, with low parallelism, per [testing/index.md](../testing/index.md#which-gates-run-when): scoped on intermediate and fix rounds, the full row on the final candidate. On a re-verify, start from the delta and widen or re-baseline per [review/index.md](../review/index.md) rule 7.
7. A failure that matches a known-issues entry: confirm it fails the same way on the base commit, or find equivalent evidence, before calling it pre-existing. Keep it marked failed and move on. Anything else is a finding.

## Output

A table of criterion → command → pass or fail, with the output tail. Each new failure with exact repro steps.

## Stop when

Every criterion has a pass or fail with evidence. Report failures; do not fix them unless the brief says so.

## Never

- Mark pass from the author's report.
- Edit the tests or code under verification.
- Retry a flaky check until it passes.
- Rerun a failed gate without a fix, rerun gates on an unchanged candidate that already gave a result, or re-investigate a known issue already confirmed on the base.
- Call a failure pre-existing from its signature alone.

## Done when

- [ ] Each criterion has a command, pass or fail, and the output tail.
- [ ] Each bug fix was reverted locally and its repro test seen failing.
- [ ] The full row ran on the final candidate; a re-verify states its scope: delta, widened (to what), or re-baselined.
- [ ] Each failure is a finding with repro steps, or a known issue confirmed on the base and still shown as failed.
