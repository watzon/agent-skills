# Comments

Read when you write, keep, or delete a comment, or when your change touches code that has comments.

Every line you leave is context a future agent must read. The goal is no unneeded content, not minimal content. Wrong text does the most harm: agents follow stale instructions even when the code disagrees, and rarely repair them.

## Rules

1. **Default to zero comments.** Keep one only for a "why" the code cannot carry: an invariant, an external constraint, a workaround for an upstream bug, a non-obvious edge case.
2. **Comments describe the code as it is now.** Never write history or narrate the change: "removed X", "previously", "now fixed", "changed per review", "new:", "renamed from". No resolved TODOs.
3. **When your change makes a comment false, fix or delete it in the same edit.** Delete history comments in code you touch.
4. **History goes in the commit message and PR description.** Version control already keeps it.
5. **Do not strip a real "why" to reach zero.** Removing comments is roughly neutral for strong models; a deleted reason is lost intent.
6. **Keep machine-read comments:** lint directives, type pragmas, license headers, and doc comments a build, a generator, or a public API needs.
7. **A TODO names something still open.** Never one for work that is done.
8. **Conventions do not go in comments.** Put commands and conventions in the project's short instruction file, which points to source files instead of copying them ([harness/instruction-files.md](../harness/instruction-files.md)).

## Examples

| Write | Do not write |
|---|---|
| `// Upstream returns 0 for "unknown"; treat it as absent.` | `// Changed to handle 0 (fix for review comment)` |
| (no comment; the name says it) `retryAfterRateLimit()` | `// retry the request` above `retry()` |
| `// Must run before migrations: they read this table.` | `// Previously this ran after migrations` |

## Done when

- [ ] Every comment in your diff states a current "why" or is machine-read.
- [ ] No comment narrates history, a diff, a review, or a previous version.
- [ ] No comment near your change is now false.
