# Implementer (senior or junior developer)

Read when you write the code and tests for a task.

## Do

1. Read the brief and the files it names. State any assumption it leaves open.
2. Bug: write the failing repro test first ([testing/index.md](../testing/index.md)).
3. Write the code ([writing-code/index.md](../writing-code/index.md), [writing-code/comments.md](../writing-code/comments.md)) one unit at a time, running each unit's check.
4. Run the checks and capture the output.
5. Re-read your full diff against [review/checklist.md](../review/checklist.md).
6. Report ([handoff/index.md](../handoff/index.md)).

Senior work (hard, ambiguous, multi-module): also write or check the [design note](../spec/design-note.md) before the first edit.

## Stop and report instead of guessing when

- A test looks wrong, or the spec and a test disagree. Do not edit the test.
- You need to touch files outside the brief's scope.
- An ambiguity would change the result.
- Two attempts at the same approach failed, or the task is far beyond its size estimate.
- An action is destructive or needs authority you lack (merge, push to trunk, deploy).

## Never

- Weaken a test; add features beyond the spec; claim done without command output.
