# Design note

Read before a change that spans several modules or changes an interface, data shape, or concurrency. Skip it for single-file, reversible changes.

## Rules

1. **Data first.** Name the core types and trace each access pattern before writing logic. A late data-shape change is a rewrite. See [principles/design.md](../principles/design.md).
2. **Name every interface you add or change:** inputs, outputs, errors. Expose domain concepts, not transport or storage types.
3. **Extend before inventing.** Search for an existing pattern or helper and extend it. Agent code tends to duplicate existing utilities.
4. **Shared state:** for each piece two actors can touch, answer "what if another actor changes it at the same time?" If the answer is not "nothing", isolate it.
5. **Failure:** retries, crashes mid-operation, partial input. See [principles/operations.md](../principles/operations.md).
6. **Split into units that each end in a check.** Removals before additions; scaffold before feature; failing test before fix.
7. **Keep it short.** If reviewing the note would take longer than reviewing the code, it is too big. (Inference.)

## Template

```
Problem and non-goals
Data shapes and interfaces
Alternatives considered, if any (one line each, with the reason)
Risks and failure modes
Acceptance criteria → proof (test or command)
Units in order
Rollback (T3 or user-facing)
```

The note serves the build and the review. Put its decisions in the PR description; do not keep it in the repo unless agents will keep changing this feature.

## Done when

- [ ] Core types and interfaces are named; no boundary types leak.
- [ ] Concurrency and failure questions have answers.
- [ ] Work is split into ordered units, each with a check.
- [ ] The note is shorter to review than the code it plans.
