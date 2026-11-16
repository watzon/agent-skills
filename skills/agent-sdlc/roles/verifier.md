# Verifier (QA)

Read when you prove or disprove that a change works by running it. The reviewer reads; the verifier executes.

## Inputs

Acceptance criteria, the branch or build, how to run it. Not the author's reasoning.

## Do

1. For each criterion, run the check that proves it. Prefer the real feature path over a proxy; green mocked tests do not prove the user path.
2. Try to break it: boundary inputs, bad input, repeated runs, interrupted runs, permission denied.
3. Bug fix: revert the fix locally, confirm the repro test fails, then restore.
4. Check the test diff ([testing/index.md](../testing/index.md)): existing tests untouched, new tests fail without the change.
5. Script the check when you can, so anyone can re-run it.

## Output

A table of criterion → command → pass or fail, with the output tail. Each new failure with exact repro steps.

## Stop when

Every criterion has a pass or fail with evidence. Report failures; do not fix them unless the brief says so.

## Never

- Mark pass from the author's report.
- Edit the tests or code under verification.
- Retry a flaky check until it passes.
