# Code health pass (T2+)

Run after the main checklist passes. Bar: approve when the change leaves the codebase easier to change, or at least no worse. Perfect is not the bar; a net decline in health is a blocker except in an emergency.

## Design

- Does this belong in this module or package?
- Does it extend an existing pattern, or invent a parallel one?
- Is there speculative generality: options, layers, or hooks for a future nobody asked for?

## Complexity

- Could it be simpler at line, function, or module level?
- Count the layers between a question and its answer, and the mutable state a reader must hold. See [minimize-reader-load](../principles/minimize-reader-load.md).
- Deep nesting means redesign, not more comments.
- Does the change grow an if/else chain or add a boolean that must stay in sync with another? See [model-the-domain](../principles/model-the-domain.md).

## Structure

- Breaks a dependency direction or adds a cycle?
- Exposes transport, storage, or framework types through a public surface?
- Changes a public API without docs or changelog?

## Functionality

- Edge cases, concurrency, idempotency, permissions?
- For UI or operator-visible behavior: evidence beyond unit tests (a run, a screenshot, a log)?

## Tests

- Right level (unit, integration, end to end) for the change?
- Test code held to the same bar as production code?

## Names and docs

- Names reveal intent. Comments explain why, not what.
- User-facing docs updated when behavior changed.

Report health findings as blocking only when they make the code measurably harder to change safely; otherwise "Nit:".
