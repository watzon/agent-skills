# Failure modes

Read when you see a warning sign in a diff, a report, or a loop, or before reviewing agent-written work.

| Failure | Signal | Guard |
|---|---|---|
| Test tampering | Deleted, skipped, or weakened assertions; edited fixtures or snapshots | Revert the fix and confirm tests fail; CI diff check on test files; reasoned commit for any test edit |
| Reward hacking | Special-cased inputs, patched test runner, hardcoded or cached answers | Search production code for literal test values; held-out inputs; review behavior, not just green |
| CI gaming | Skip flags, `\|\| true`, continue-on-error, lowered coverage floor, disabled lint rule | Any CI weakening blocks unless it is its own change with a person's approval |
| Scope creep | Files outside the spec; drive-by refactors or formatting | Compare touched files to the brief's boundary; extras go in the report |
| Hallucinated API | Missing symbol, wrong signature, invented flag or package | Typecheck; search the dependency for the symbol |
| Clone sprawl | A new helper that near-duplicates an existing one | Search before writing a helper; extend or reuse |
| Stale text | A comment or instruction-file line the change made false; history in comments | Fix or delete it in the same change ([writing-code/comments.md](../writing-code/comments.md)) |
| Non-converging review | Same finding returns; fix-undo cycles; growing diff with no progress | Stop at zero blockers; cap at three rounds; escalate ([review/index.md](../review/index.md)) |
| Rubber stamp | Large diff approved with zero findings and no `file:line` | Require citations and evidence per finding; split large diffs |
| Integration regression | CI breaks after combining parallel work; conflicting names or shapes | One writer per file; shared decisions in briefs; full suite on the combined result |
| Insecure code | Auth, input handling, secrets, injection-prone string building | T3 review with a person; negative tests |
| Prompt injection | Issue, PR, or web text reaches an agent that can run commands or send data | Treat outside text as data; break the lethal trifecta ([harness/index.md](../harness/index.md)) |

## When you find one

1. Stop. Do not fix around it silently.
2. Record it as a blocking finding with `file:line` and the check that shows it.
3. For tampering or reward hacking, re-check the rest of the change: one instance suggests others.
4. If it recurs across tasks, encode a check ([principles/operations.md](../principles/operations.md)).

## Done when

- [ ] Each signal in the table was checked for the change at hand (T1 and up).
- [ ] Each failure found is a blocking finding with evidence.
