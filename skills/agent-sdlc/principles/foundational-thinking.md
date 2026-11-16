# Foundational thinking

Apply before writing logic: choosing core types and data structures, sequencing scaffold-vs-feature work, asking what concurrent actors share. Get the data structures right so downstream code becomes obvious.

Structural decisions protect option value; code-level decisions protect simplicity. Over-engineering is usually a premature decision that closes doors.

- **Data structures first.** Define core types early, trace every access pattern, and choose shapes that fit the dominant paths. Early, a shape change is a small diff; late, it is a rewrite.
- **Share structure, not every line.** Types and data models should converge. Three similar statements still beat a premature abstraction. Prefer explicit over clever.
- **Concurrency.** Before sharing state between actors, ask what happens if another actor changes it at the same time. If not "nothing", isolate it.
- **Scaffold first.** If something helps every later phase (CI, lint, test setup, shared types), do it first. Setup before features; tests before fixes.
- **Each increment lands or deepens one coherent abstraction.** Do not spread a new capability across callers as special-case coordination.
- Subtraction comes before scaffolding: [subtract-before-you-add](subtract-before-you-add.md).

**Check:** does every later step get simpler because of the shape you chose? If a later step needs a workaround, revisit the shape now.
