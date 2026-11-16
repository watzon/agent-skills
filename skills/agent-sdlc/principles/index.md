# Principles

Read when choosing how to approach a piece of work. Open only the files whose trigger matches.

| File | Apply when |
|---|---|
| [behavior.md](behavior.md) | Writing, reviewing, or refactoring any code. The baseline: think first, keep it simple, change surgically, work to a goal. |
| [boundary-discipline.md](boundary-discipline.md) | Wiring validation, error handling, or framework adapters. |
| [encode-lessons-in-structure.md](encode-lessons-in-structure.md) | Writing the same instruction a second time, or seeing a recurring correction. |
| [fix-root-causes.md](fix-root-causes.md) | Debugging. |
| [foundational-thinking.md](foundational-thinking.md) | Before writing logic: choosing core types and data structures, ordering scaffold and feature work, sharing state between actors. |
| [laziness-protocol.md](laziness-protocol.md) | Refactoring, judging diff size, or tempted to add abstractions, layers, or threaded signals. |
| [make-operations-idempotent.md](make-operations-idempotent.md) | Designing commands, lifecycle steps, or loops that run amid crashes, restarts, and retries. |
| [minimize-reader-load.md](minimize-reader-load.md) | Reviewing or shaping code that is hard to trace. |
| [model-the-domain.md](model-the-domain.md) | Writing stateful logic, or code that branches a lot or repeats a shape assumption across files. |
| [prove-it-works.md](prove-it-works.md) | After finishing a task, before declaring done. |
| [sequence-verifiable-units.md](sequence-verifiable-units.md) | Multi-step work (sweeps, migrations, runs of similar edits) and stacking commits or pull requests. |
| [subtract-before-you-add.md](subtract-before-you-add.md) | Sequencing an addition, refactor, or rewrite. |
| [type-system-discipline.md](type-system-discipline.md) | Designing types, reviewing a signature, or writing code in a statically typed language. |

## Done when

- [ ] You read every principle whose trigger matches your current work, and no others.
- [ ] Each one's check passes for your change, or you noted why it does not apply.
