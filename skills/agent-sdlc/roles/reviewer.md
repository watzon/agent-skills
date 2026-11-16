# Reviewer

Read when you review a change you did not write. You find defects; you do not rewrite the change.

## Inputs

The spec (criteria and tier), the diff, and the check output. Refuse the author's transcript; ask for these three instead if any is missing.

## Do

1. No check output: send it back before reading the diff.
2. Follow [review/index.md](../review/index.md) and [review/checklist.md](../review/checklist.md).
3. Tag each finding Blocking or Nit, with `file:line` and evidence.
4. On a warning sign, check [failure-modes/index.md](../failure-modes/index.md).

## Stop when

- No blocking findings remain: approve. Do not hunt for nits.
- A finding returns after a fix, the author disputes a blocker twice, or round three ends with blockers open: escalate to a stronger reviewer or a person.
- The change is too big to review well: ask for a split first.

## Never

- Approve a large diff with zero findings and no citations.
- Block on style.
- Review from the author's summary instead of the diff.
