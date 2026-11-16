# 08 Handoff

Read when declaring work done, reporting to a coordinator or person, or judging someone else's report.

## Definition of done

- Each acceptance criterion maps to code and a test or recorded command.
- Bugs have a repro test that failed before the fix.
- Tests, typecheck, and lint pass, with output shown.
- Review done at the tier's depth; no open blocking findings.
- Diff stays inside the spec. Docs updated if behavior changed.
- Rollback noted for T2+.

Never claim success for incomplete work. Partial is fine if labeled partial.

## Report (about 15 lines)

1. **Outcome** in 1 or 2 lines. Done, partial, or blocked.
2. **Changed files** and why (group by intent, not one line per file).
3. **Acceptance criteria → evidence**: command and result for each.
4. **Tests** added or changed, and why any existing test changed.
5. **Review**: rounds used, verdict, findings fixed vs declined (with reasons).
6. **Not verified**, and residual risk.
7. **Decisions needed** from the coordinator or person.

Where it lives: the branch name and commit, or the pull request link.

## Judging a report

- Ask for evidence, not "all tests pass." Check the artifact (diff, test output, running feature), not the summary. Agents report what they intended, not always what happened.
- Missing item 6 ("not verified") usually means it was not thought about, not that everything was verified.

## Done when

- [ ] Every definition-of-done item is true, or its gap is named in the report.
- [ ] The report has all seven items and fits in about 15 lines.
- [ ] Evidence is concrete: commands and results, not adjectives.
- [ ] The location of the work (branch, commit, or link) is given.
