# Failure modes

Read when you see a warning sign in a diff, a report, or a loop, or before reviewing agent-written work.

| Failure | Signal | Check | Guard |
|---|---|---|---|
| Test tampering | Deleted, skipped, or weakened asserts; edited fixtures or snapshots | Read the test diff first; revert the fix and confirm tests fail | Test edits in their own commit with a reason; human approval for test edits where possible |
| Reward hacking | Special-cased inputs, patched test runner or evaluator, hardcoded or cached answers, faked timing | Search the diff for literal test values in production code; run held-out inputs | Held-out tests; review behavior, not just green |
| CI gaming | Skip flags, `\|\| true`, continue-on-error, lowered coverage floor, disabled lint rule | Diff CI config and lint config | Any CI weakening is blocking unless it is its own change with a human-approved reason |
| Scope creep | Files outside the spec; drive-by refactors or formatting | Compare touched files to the scope allowlist | Allowlist per task; extras go in the report |
| Hallucinated API | Missing symbol, wrong signature, invented flag or package | Typecheck; grep the symbol in the dependency | Verify every new call before review |
| Clone sprawl | A new helper that near-duplicates an existing one | Search for similar names and bodies | Search before writing a helper; extend or reuse |
| Non-converging loop | Same finding returns; fix-undo cycles; growing diff with no progress | Compare this round's findings with last round's | Round cap (2; 3 at T3); escalate |
| Rubber stamp | Big diff approved with zero findings and no `file:line` | Count citations in the review | Every finding cites `file:line` and evidence; split big diffs |
| Integration regression | CI breaks after merging parallel work; conflicting names or data shapes | Full suite on the combined result | Single writer per file; shared decisions fixed in briefs; rebase and full CI |
| Insecure code | Auth, input handling, secrets, injection-prone string building | Security-focused review; negative tests | T3 review with human approval |
| Prompt injection | Untrusted issue, PR, or web text fed into a prompt that can run commands | Trace where prompt text comes from | Treat outside text as data; least-privilege tokens; human gate on destructive actions |

## When you find one

1. Stop. Do not fix around it silently.
2. Record it as a blocking finding with `file:line` and the check that shows it.
3. For tampering or reward hacking, also re-check the rest of the change: one instance suggests others.
4. If it recurs across tasks, encode a check: [encode-lessons-in-structure](../principles/encode-lessons-in-structure.md).

Evidence that these failures are real, with confidence labels: [SOURCES.md](../SOURCES.md).

## Done when

- [ ] Every signal in the table was checked for the change at hand (T1+).
- [ ] Each failure found is a blocking finding with evidence.
- [ ] Recurring failures have a structural check or a filed task.
