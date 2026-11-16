# Minimize reader load

Apply when reviewing or shaping code that's hard to trace. Count layers between question and answer, and hidden state in the reader's head; collapse one-caller wrappers and shrink mutable scope.

Maintainability is the work a reader must do to understand code. Line counts and complexity scores are proxies. Track two independent axes:
1. **Layers to trace** between a question and its answer.
2. **State to hold**: hidden or mutable context the reader must keep in mind.

A flat file with 50 globals can be as hard to follow as a 6-layer adapter stack. Guard both.

- **Collapse layers that don't earn their keep:** wrappers with one caller, adapters with one implementation, indirection for a future that never came.
- **Each layer must change the abstraction.** A layer that repeats the same methods and arguments adds load without compression.
- **Prefer deep interfaces:** a small surface hiding a real decision. A wide surface hiding little makes readers learn both.
- **Shrink state scope:** return values over mutation, locals over fields, fields over module state, module state over globals. Derive values instead of syncing copies.
- **Name an invariant once, at the boundary,** not in every consumer.
- Before adding a layer or a piece of state: does it reduce reader load elsewhere by at least as much?

**Check:** can a new reader answer "where does X come from?" and "what can change X?" in under 30 seconds? If not, cut layers or state.
