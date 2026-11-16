# Behavior baseline

Apply when writing, reviewing, or refactoring any code. Counters the most common agent coding mistakes: silent assumptions, overbuilding, collateral edits, and vague goals.

Ideas credited to Andrej Karpathy's observations on LLM coding pitfalls, as collected in the `karpathy-guidelines` skill (multica-ai/andrej-karpathy-skills). Rewritten here in our own words; see [README](../README.md).

## 1. Think before coding

- Say which assumptions you are relying on. If one is shaky and matters, ask.
- When a request has more than one reading, lay them out. Never choose one quietly.
- If something is confusing, stop and name the confusion instead of building around it.
- If a simpler approach meets the goal, propose it before building the complex one.

## 2. Simplicity

- Build only what was asked. No speculative features, options, or settings.
- No abstraction for code with one use. No handling for errors that cannot occur.
- If the result is far longer than the problem deserves, rewrite it shorter.
- Check: would an experienced engineer call this overbuilt? Then cut it. Depth: [laziness-protocol](laziness-protocol.md), [subtract-before-you-add](subtract-before-you-add.md).

## 3. Surgical changes

- Edit only what the task needs. Leave nearby code, comments, and formatting alone.
- Do not refactor what is not broken. Follow the file's existing style.
- Tidy only what you broke: delete imports and helpers your change orphaned. Report other dead code; do not remove it unasked.
- Check: every changed line traces back to the request.

## 4. Goal-driven execution

- Turn each instruction into a goal you can check: "fix the bug" becomes "this repro test fails, then passes."
- For multi-step work, write a short plan where each step names its check:

```
1. <step> → check: <command or observation>
2. <step> → check: <command or observation>
```

- Clear criteria let you loop on your own until done. "Make it work" forces someone to keep clarifying.

These bias toward care over speed. For a trivial T0 change, use judgment.
