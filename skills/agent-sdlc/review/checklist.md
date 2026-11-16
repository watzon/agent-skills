# Review checklist

Read during a review, after the check output is in hand ([index.md](index.md)). Work top to bottom.

## Hard blockers: send back at once

- CI config, required checks, coverage floors, or lint rules weakened (removed tests, skip flags, `|| true`).
- Tests deleted, skipped, or assertions weakened to get green.
- Secrets, keys, or credentials added.
- Unrelated changes mixed in with no plan.
- T3 paths touched without the tier's tests or a human reviewer.

## In order

1. **Criteria.** Each acceptance criterion maps to code and a test.
2. **Scope.** Files outside the spec; drive-by refactors; formatting mixed with logic.
3. **Tests.** Would they still pass with the fix reverted? Is there a repro test for a bug? Are they mock-heavy or mirroring the implementation?
4. **APIs exist.** Every imported or called symbol is real (typecheck or search).
5. **Boundaries.** Input validation, auth, error paths, concurrency, idempotency.
6. **Duplicates.** A new helper that copies an existing one.
7. **One critical path,** traced end to end through the diff.
8. **Comments.** Any comment that narrates history or is now false is a finding ([writing-code/comments.md](../writing-code/comments.md)).
9. **Design and complexity** (T2 and up), below.
10. **Slop.** The anti-slop sweep output is present and its judgment checks hold ([anti-slop/index.md](../anti-slop/index.md)).

## Design and complexity (T2 and up)

- Does the code belong in this module? Does it extend an existing pattern or invent a parallel one?
- Speculative generality: options, layers, or hooks nobody asked for.
- Count the layers between a question and its answer, and the mutable state a reader must hold ([principles/design.md](../principles/design.md)).
- A new boolean that must stay in sync with another, or one more branch in a growing if/else chain, means the domain model is missing.
- Breaks a dependency direction, adds a cycle, or leaks transport or storage types through a public surface.

Health findings block only when they make the code measurably harder to change safely. Otherwise mark them "Nit:".

## Done when

- [ ] Hard blockers checked first.
- [ ] Every item above was checked or marked not applicable.
