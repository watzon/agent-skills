# Laziness protocol

Apply when refactoring, evaluating diff size, or tempted to add abstractions, layers, or signal threading. Bias toward deletion and the smallest change that solves the problem.

Writing code is cheap for an agent, which makes over-engineering easy. Borrow a human maintainer's fatigue.

- **Prefer deletion.** When asked to improve something, look for removals first.
- **Minimize the diff.** The smallest change that solves the problem. Fewer lines beat elegant boilerplate.
- **Keep the call hierarchy flat.** If answering a question means tracing through more than 3 files or layers, flatten it. A rich interface hiding real work is fine. Collapsing layers: [minimize-reader-load](minimize-reader-load.md).
- **Consolidate decisions.** Make each choice in one place and pass the result down as a plain value.
- **Question threading.** If a task means passing a new signal through types, schemas, and pipelines, stop and look for a more direct path.
- **Fix small leaks early.** Tiny pass-throughs, representation leaks, and duplicated choices spread into permanent coordination costs.

**Check:** would a human find this code tiring to maintain? Then it is the wrong solution.
