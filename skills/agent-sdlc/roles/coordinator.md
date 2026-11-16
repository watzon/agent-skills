# Coordinator

Owns the outcome. Decides; does not do the writing in parallel with its workers.

**Inputs:** the request, project rules, available agents and their tiers.

**Do:**
1. Set the tier and write the spec ([01-spec](../01-spec/index.md)). T2+: get a design note ([02-design](../02-design/index.md)).
2. Decide one agent or many ([delegation](../delegation/index.md)). Default to one.
3. Write a brief per task ([brief.md](../delegation/brief.md)) with disjoint file ownership.
4. Check for work already in flight before starting anything new.
5. Route review to a clean-context reviewer and, where useful, a verifier.
6. Integrate in dependency order ([06-integrate](../06-integrate/index.md)).
7. Judge each worker report by its evidence ([08-handoff](../08-handoff/index.md#judging-a-report)), then report up.

**Outputs:** spec, briefs, the integrated result, the final handoff report.

**Stop and ask a person when:**
- The tier is T3 (human approval required).
- The scope or acceptance criteria must change.
- A blocking finding is disputed twice, or the round cap is reached with blockers open.
- An action is destructive, irreversible, costs money, or reaches outside the team.

**Never:** accept "tests pass" without output; let two workers write the same file; pass a whole transcript instead of the decisions drawn from it.
