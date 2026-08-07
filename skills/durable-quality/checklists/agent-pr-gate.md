# Agent PR gate

Run this **before** deep design review. Fast rejects save the depleted resource: human attention.

## Hard blockers

Stop review and send back if any are true:

1. CI config, required checks, coverage floors, or skip directives weakened without a dedicated human-approved rationale
2. Tests removed or asserts hollowed to obtain green
3. Secrets, prod keys, or credentials introduced
4. No named human author/owner accountable for merge
5. Scope is a multi-unrelated dump with no plan
6. High blast-radius paths touched with no tier-appropriate proof
7. Bulk autonomous spam pattern (tiny drive-by noise, undisclosed agent farms)

## Ten-minute protocol

Adapted from GitHub agent PR guidance and Osmani-style review:

1. Check workflows and CI diffs first
2. Read test diffs before production diffs
3. Search for duplicate utilities / clone sprawl introduced
4. Trace one critical path end-to-end in the diff
5. Demand a regression test that fails on pre-change behavior for bugfixes
6. Confirm commands-run evidence in the PR body
7. Confirm dependency/architecture gates still meaningful
8. If stuck or huge, request split + plan rather than rubber-stamping

## Intent restoration

If the PR lacks intent, require:

- problem statement
- approach chosen and alternatives rejected
- risk notes
- proof performed
- follow-ups deferred

Agent decision logs are useful sensors; they are not accountability.

## Size and shape

Prefer:

- one intent per PR
- bisectable history
- separate mechanical refactors from behavior changes

Send back when:

- thousands of lines across unrelated modules
- reformat mixed with logic
- generated code committed without need

## Sensors vs verdicts

AI review bots may add comments. Treat them as sensors.

Final merge verdict remains human on T2+ paths, and mandatory human on T4–T5.

## After pass

Only then apply `checklists/code-health-review.md` for design, complexity, and system health direction.
