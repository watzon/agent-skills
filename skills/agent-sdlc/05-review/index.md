# 05 Review

Read when reviewing a diff: your own self-review, another agent's work, or a pull request.

## Inputs

The spec (acceptance criteria and tier), the diff, and the test output. **Not** the author's transcript or reasoning: a fresh context finds more. Run deterministic checks before spending review effort.

Size: aim for 200 changed lines or fewer per review, 400 at most. Ask for a split above that; review quality drops on big diffs (confidence low to medium, [SOURCES.md](../SOURCES.md)).

## Step 1: hard blockers (send back at once)

- CI config, required checks, coverage floors, or skip directives weakened.
- Tests deleted, skipped, or asserts weakened to get green.
- Secrets, keys, or credentials added.
- Unrelated changes dumped together with no plan.
- T3 paths touched without the tier's proof.

## Step 2: checklist, in order

Read workflow and test diffs before production code.

1. Each acceptance criterion maps to code and a test.
2. Scope: files outside the spec, unrelated refactors, formatting mixed with logic.
3. Test diff: deleted or weakened assertions. Would the tests pass with the fix reverted?
4. Every imported or called API exists (grep or typecheck).
5. Boundaries: input validation, auth, error paths, concurrency, idempotency.
6. Duplicates: a new helper that copies an existing one.
7. Trace one critical path end to end through the diff.
8. Then complexity, naming, consistency with existing patterns. For T2+ also run [code-health.md](code-health.md).

Skip style and taste unless they hide a defect. A reviewer asked to find problems will invent some.

## Findings

- **Blocking:** wrong against the spec, security or data loss, failing or weakened tests, broken integration, CI weakened.
- **Nit:** style or taste. Prefix "Nit:". Never blocks.
- Every finding cites `file:line` and a command or test that shows it. Zero findings with no citations on a big diff is a rubber stamp; re-review.
- Verdict: approve, approve with nits, or request changes.

## Author response

Fix every blocking finding. For each nit, fix it or decline with a reason. Never skip a blocking finding silently.

## Rounds and escalation

- Round 1: full review. Round 2: verify the fixes and check only changed lines for new blockers. Targeted tests in round 2; full CI at integration.
- Cap: 2 rounds. A 3rd only at T3, or when round 2 found new blockers and a stronger reviewer takes it.
- Stop at zero blocking findings. Do not keep hunting for nits.
- **Escalate** to a stronger model or a person when: the same finding returns after a fix, the author disputes a blocking finding twice, or the cap is reached with blockers open.
- Reviewer at T2: a different model family or a human spot check. At T3: human approval required; review with a security focus.

## Done when

- [ ] Hard blockers checked first.
- [ ] Every acceptance criterion was traced to code and a test.
- [ ] Every finding has `file:line`, a severity, and evidence.
- [ ] Zero open blocking findings, or the item is escalated.
- [ ] Rounds used are within the tier's cap.
