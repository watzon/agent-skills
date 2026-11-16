# Brief template

Read when you write a task for another agent. The worker has none of your context: the brief must stand alone.

```
Role: implementer | reviewer | verifier | researcher
Objective: <1-2 sentences, and why it matters>
Done when:
- [ ] <checkable by running something>
Output: <what to return, its shape, and the file path to write it to>
Tools and sources: <what to use first; what to avoid>
Boundary: <files you may change>  Out of scope: <...>
Decisions already made: <names, data shapes, interfaces, style, edge cases>
Where: <repo, branch or workspace, files to read first>
Tier: T?   Size: <expected effort>   Retry cap: <n>
Stop rule: stop and report instead of guessing when <...>
```

## Rules

- **Objective, output format, tools and sources, boundary:** never omit these four. Vague briefs cause duplicated work and gaps.
- **Write down every implicit decision.** An unrecorded choice makes two workers build things that do not fit together.
- **Done-when items are commands or observations,** not adjectives.
- **Point, do not paraphrase,** for anything that must be exact: file, line, or commit.
- **Reviewer briefs** carry the spec, the diff, and the check output. Never the author's transcript.
- **Researcher briefs** carry the question, why it matters, and a budget.
- **State the stop rule** even when it seems obvious.

## Common failures

- Vague objective → duplicated or misread work.
- Whole conversation pasted instead of the decisions drawn from it.
- No output shape → a report you cannot check.
- No stop rule → the worker guesses on something consequential.
