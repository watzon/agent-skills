# Encode lessons in structure

Apply when you catch yourself writing the same instruction a second time, or notice a recurring correction. Encode the rule as a lint, metadata flag, runtime check, or script instead of more text.

Text instructions need the reader to notice, remember, and comply. Mechanisms enforce without cooperation.

**When a correction repeats:**
1. Can it be a type, lint, CI check, metadata flag, runtime check, or script? If yes, build it and delete the instruction.
2. If it truly needs judgment, make the instruction prominent and add an example of the failure.

**Pick the strongest rung that fits:** a state that cannot compile > a lint or banned API that fails CI > one canonical helper > a runtime check > a written rule. Agents copy what nearby code does, so a weak guard becomes the next template.

If a structural fix exists, use only that. The instruction is the symptom.

**Close the loop on every correction or failed check:**
- One-off: note it where the team keeps notes.
- Recurring: a lint, check, or skill rule.
- Systemic: a principle.
- Apply it now or file a concrete task. "I'll keep that in mind" does not persist.

**Anti-patterns:** acknowledging without recording; recording without building the check; fixing one instance and leaving the pattern.

Repo-level version: [audit/agents-md.md](../audit/agents-md.md) (every soft rule needs a hard twin).
