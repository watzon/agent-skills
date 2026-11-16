# Design principles

Read when choosing core types, data structures, module boundaries, or validation. These are engineering judgment, not measured findings about agents (see [SOURCES.md](../SOURCES.md)).

## Rules

1. **Data structures first.** Define core types early and trace every access pattern. Early, a shape change is a small diff; late, it is a rewrite. If a later step needs a workaround, revisit the shape now.
2. **Make illegal states unrepresentable.** Model variants as sum types, not a bag of optional fields: `{ kind: 'open' } | { kind: 'done'; at: Date }`, not `{ done: boolean; doneAt?: Date }`. Adding a variant must break compilation wherever it is unhandled.
3. **Model the domain instead of branching.** A state machine instead of scattered booleans; a lookup table or union instead of if/else chains across files; a module that owns one body of domain knowledge, not one phase. Do not force it where the code is local and unlikely to grow.
4. **Validate at the boundary, trust inside.** Parse raw input (CLI args, config, env, network, database rows, IPC) into domain types once, where it enters. No re-validation or deep null checks inside. Expose domain concepts across boundaries, not transport or storage types.
5. **Brand primitives that mean different things.** `UserId` and `OrderId` must not be interchangeable even if both are strings.
6. **Do not lie to the compiler.** A cast or non-null assertion is a deferred crash; prove the fact at the boundary instead.
7. **Derive types from the authoritative schema** (API spec, migrations, protobuf). Hand-written parallel types drift.
8. **Keep logic in pure functions;** the shell (CLI, handler, UI) only calls them.
9. **Minimize reader load.** Count the layers between a question and its answer, and the mutable state a reader must hold. Collapse wrappers with one caller and adapters with one implementation. Prefer return values to mutation and locals to shared state.
10. **Share structure, not every line.** Types and data models converge; three similar statements still beat a premature abstraction.

## Checks

- Can you write a sentence saying when a field combination is valid? Make it a sum type.
- If a variant is added next month, will the compiler find every place that needs it?
- Is this data crossing a boundary right now? If not, the validation is redundant.
- Can a new reader answer "where does X come from?" and "what can change X?" quickly?
