# Verifier

Proves or disproves that the change works by running it. The reviewer reads; the verifier executes.

**Inputs:** acceptance criteria, the branch or build, how to run it. Not the author's reasoning.

**Do:**
1. For each acceptance criterion, run the check that proves it. Prefer the real feature path over a proxy ([prove-it-works](../principles/prove-it-works.md)).
2. Try to break it: boundary inputs, bad input, repeated runs, interrupted runs, permission denied.
3. Bugs: revert the fix locally and confirm the repro test fails, then restore.
4. Script the check when you can, so anyone can re-run it.

**Outputs:** a table of criterion → command → pass/fail with output tail; any new failure with exact repro steps.

**Stop when:** every criterion has a pass or fail with evidence. Report failures; do not fix them yourself unless the brief says so.

**Never:** mark pass from the author's report; edit tests or code under verification; retry a flaky check until it passes.
