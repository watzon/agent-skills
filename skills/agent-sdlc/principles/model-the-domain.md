# Model the domain

Apply when writing stateful logic, or when code branches a lot or repeats a shape assumption across files. Encode the domain in a structure instead of scattered conditionals.

Scattered booleans, repeated shape assumptions, and branching across files are accidental complexity. A structure that matches the domain makes invalid states unrepresentable and deletes branches. Choosing it while writing is cheap; recovering it later looks like a refactor and gets deferred.

Reach for:
- A state machine instead of scattered booleans, phases, or lifecycle checks.
- A typed model instead of loose parameters or repeated shape assumptions.
- A lookup table, registry, or discriminated union instead of branching spread across files.
- A reducer or command/event model instead of ad hoc mutation.
- A module that owns one body of domain knowledge, not a phase (load, validate, transform, save). Execution order is not ownership.
- A queue, cache, index, tree, or normalized collection where the access pattern calls for it.
- None fits? Work out what the code must never allow and how the data is read, then pick the structure that encodes exactly that.

Do not force it. Keep boring code if the shape is clear, local, and unlikely to grow. Distrust an abstraction that adds indirection without removing branches, duplicated rules, invalid states, or lifecycle risk.

**Tells you skipped this:** a feature adds one more branch to an existing if/else chain; a second boolean must stay in sync with the first; phase-named modules repeat the same rules.
