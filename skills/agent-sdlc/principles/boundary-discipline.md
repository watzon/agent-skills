# Boundary discipline

Apply when wiring validation, error handling, or framework adapters. Concentrate guards at system boundaries (CLI, config, network, external APIs); trust internal types and keep business logic in pure functions.

Scattered validation is noisy, redundant, and gives false safety. Validate once where data enters; trust it after.

- **At boundaries** (CLI args, config, env vars, network, external APIs, database rows, IPC): parse raw input into domain types, return errors, handle defensively.
- **Inside:** typed data, propagate errors, no re-validation, no nil checks deep in call chains the boundary already covered.
- **Across a boundary:** expose domain concepts, not the transport, storage, framework, or wire types. General mechanism inside; special-case policy at the edge.
- **Logic in pure functions** with no framework dependency: parsing (bytes in, typed state out), prompt building (state in, string out), scoring (state in, result out). The shell just calls them.

Type-level detail: [type-system-discipline](type-system-discipline.md).

**Check:**
- Is this data crossing a system boundary right now? If not, the validation is redundant.
- Could this be a pure function the shell calls? If yes, extract it.
