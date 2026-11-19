# Brief template

Read when you write a task for another agent. The worker has none of your context: the brief must stand alone. Standing alone means self-sufficient, not long.

```
Role: implementer | reviewer | verifier | researcher
Objective: <1-2 sentences, and why it matters>
Done when:
- [ ] <checkable by running something>
Output: <what to return, its shape, and the file path to write it to>
Tools and sources: <what to use first; what to avoid>
Boundary: <files you may change>  Out of scope: <...>
Decisions already made: <names, data shapes, interfaces, style, edge cases>
Where: <repo, branch or commit range, files and project notes to read first>
Tier: T?   Gates: <row from testing/index.md>   Size: <expected effort>   Retry cap: <n>
Re-verify only: <commit range since last round; prior findings, or a path to them>
Stop rule: stop and report instead of guessing when <...>
```

## Rules

- **Objective, output format, tools and sources, boundary:** never omit these four. Vague briefs cause duplicated work and gaps.
- **Short, not thin.** Give the goal, branch or commit range, gate row, checklist, and done-when. Point to project notes and files instead of re-explaining the project. For a repeat task, reuse the last brief and change only what changed.
- **Write down every implicit decision.** An unrecorded choice makes two workers build things that do not fit together.
- **Done-when items are commands or observations,** not adjectives.
- **Point, do not paraphrase,** for anything that must be exact: file, line, or commit.
- **Reviewer briefs** carry the spec, the diff, and the check output. Never the author's transcript. A re-review brief adds the commit range and prior findings ([review/index.md](../review/index.md)).
- **Researcher briefs** carry the question, why it matters, and a budget.
- **State the stop rule** even when it seems obvious.

## Common failures

- Vague objective → duplicated or misread work.
- Whole conversation pasted instead of the decisions drawn from it.
- The project re-explained from scratch each time → cost, and drift from the notes.
- No gate row → the worker runs every check on a small change.
- No output shape → a report you cannot check.
- No stop rule → the worker guesses on something consequential.

## Done when

- [ ] Objective, output, tools and sources, boundary, and stop rule are all present.
- [ ] The gate row is stated; a re-verify brief carries the commit range and prior findings.
- [ ] Project background is a pointer to notes or files, not a restatement.
