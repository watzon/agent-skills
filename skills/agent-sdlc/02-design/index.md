# 02 Design

Read before implementing a T2+ change: a new interface, data shape, concurrency, or anything spanning several modules. Skip for single-file, reversible changes.

## Steps

1. **Data first.** Define the core types and trace every access pattern before writing logic. A late data-shape change is a rewrite. See [foundational-thinking](../principles/foundational-thinking.md), [model-the-domain](../principles/model-the-domain.md), [type-system-discipline](../principles/type-system-discipline.md).
2. **Interfaces.** Name each public surface you add or change: signature, inputs, outputs, errors. Expose domain concepts, not transport or storage types. See [boundary-discipline](../principles/boundary-discipline.md).
3. **Fit.** Search for an existing pattern or helper that does this. Extend it before inventing a parallel one.
4. **Shared state.** For each piece of state two actors can touch, answer "what if another actor changes this at the same time?" If the answer is not "nothing", isolate it.
5. **Failure modes.** Retries, crashes mid-operation, partial input. See [make-operations-idempotent](../principles/make-operations-idempotent.md).
6. **Subtract first.** Plan removals before additions. See [subtract-before-you-add](../principles/subtract-before-you-add.md).
7. **Sequence.** Break the work into units that each end in a check: scaffold, then feature; failing test, then fix. See [sequence-verifiable-units](../principles/sequence-verifiable-units.md).
8. **Rollout** (T3, or anything users see): compatibility, migration order, flag, rollback.

## Artifact

A design note of one page or less, next to the spec:

```
Problem / non-goals
Data shapes and interfaces
Alternatives rejected (one line each)
Risks and failure modes
Proof plan (tests per acceptance criterion)
Units in order
Rollout and rollback (T3 or user-facing)
```

## Done when

- [ ] Core types and interfaces are named, with no boundary types leaking.
- [ ] Concurrency and failure questions have answers.
- [ ] At least one alternative was considered and rejected with a reason.
- [ ] Work is split into ordered units, each with a check.
- [ ] The note fits on one page.
