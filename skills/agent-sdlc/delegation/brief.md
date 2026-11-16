# Brief template

The worker has none of your context. A brief must stand alone.

```
Role: implementer | reviewer | verifier | researcher   (see roles/)
Goal: <1-2 sentences, and why it matters>
Acceptance criteria:
- [ ] <checkable by running something>
Where: <repo, branch or workspace, paths; files to read first>
Scope: <files you may change>  Do not touch: <...>
Tier: T?
Constraints: <decisions already made, shared names and data shapes, conventions, environment rules (who may merge or push)>
Output: <what to return and its shape: outcome, changed files, criteria → evidence, not verified, decisions needed>
Size: <expected effort>  Retry cap: <n>
Stop rule: stop and report instead of guessing when <...>
```

## Rules

- Acceptance criteria are commands or observations, not adjectives.
- Name every shared decision explicitly; an omitted one makes two workers diverge.
- Point to the file or commit for anything that must be exact. Do not paraphrase it.
- Reviewer briefs carry spec, diff, and test output. Never the author's transcript.
- Researcher briefs carry the question, why it matters, and a budget.
- State the stop rule even when it seems obvious. Weaker agents rarely escalate on their own.

## Common failures

- Vague goal → duplicated or misread work.
- Whole conversation pasted instead of the decisions drawn from it.
- No output shape → a report you cannot check.
- No stop rule → the worker guesses on something consequential.
