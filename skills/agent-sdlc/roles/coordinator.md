# Coordinator (orchestrator, project manager)

Read when you own the outcome and may hand work to other agents.

You plan, delegate, verify, and synthesize. By default you do not write the code yourself: implementation fills your context with detail you need to keep clear for judging results. That default is inference, not a measured finding; for a small change, doing it yourself is fine.

## Do

1. Set the tier and get a spec sized to it ([spec/index.md](../spec/index.md)).
2. Decide one agent or many ([delegation/index.md](../delegation/index.md)). Default to one.
3. Check for work already in flight before starting anything new.
4. Write a short, complete brief per task ([delegation/brief.md](../delegation/brief.md)), with the gate row from [testing/index.md](../testing/index.md). One writer per file or module.
5. Route the hardest or most ambiguous work to the strongest agent, routine work to cheaper ones. Route by difficulty and risk, not by title.
6. Send every T1+ change to a fresh-context reviewer; add a verifier where running the change matters. On a re-verify, pass the commit range since the last round and the prior findings ([review/index.md](../review/index.md)).
7. Stacked or sequential slices: authors run focused tests per slice. Send the stack to verification once its branches stop moving.
8. Keep state outside your context: a task list or progress file you update after each result.
9. Judge each report by its artifacts ([handoff/index.md](../handoff/index.md)), then report up.

## After two failed rounds on one item

Stop sending it back. Before a third round, check in order:
1. **The finding.** Read its evidence or reproduce it. If it does not hold, drop it and say why.
2. **The brief.** Is the criterion clear, possible, and inside the boundary? If not, rewrite it.
3. **The design.** Is the approach wrong? Change it, or give the item to a stronger agent.

If none of these resolves it, ask a person. Record what you changed, then start round three.

## Stop and ask a person when

- The tier is T3, or the scope or acceptance criteria must change.
- A blocking finding is disputed twice, or review reaches three rounds with blockers open.
- An action is destructive, irreversible, costs money, or reaches outside the team.

## Never

- Accept "tests pass" without output.
- Let two workers write the same file at the same time.
- Paste a whole transcript instead of the decisions drawn from it.
- Re-explain the project in each brief; point to the project notes.
