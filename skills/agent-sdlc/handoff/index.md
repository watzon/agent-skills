# Handoff

Read when declaring work done, reporting to a coordinator or person, or judging someone else's report.

## Definition of done

- Each acceptance criterion maps to code and a test or recorded command.
- Bugs have a repro test that failed before the fix.
- Tests, typecheck, and lint ran, with the commands and output shown.
- Review done at the tier's depth; no open blocking findings.
- The diff stays inside the spec. Docs and comments touched by the change are still true.
- Rollback noted for T2 and up.

Never claim success for incomplete work. Partial is fine when labeled partial.

## Report (about 15 lines)

1. **Outcome** in one or two lines: done, partial, or blocked.
2. **Where:** branch and commit, or the pull request link.
3. **Changed** files and why, grouped by intent.
4. **Criteria → evidence:** command and result for each.
5. **Tests** added or changed, and why any existing test changed.
6. **Review:** rounds used, verdict, findings fixed or declined (with reasons).
7. **Not verified,** and residual risk.
8. **Decisions needed** from the coordinator or person.

## Judging a report

- Check the artifact (diff, test output, running feature), not the summary. Agents report what they meant to do, not always what happened.
- No "not verified" item usually means nobody thought about it, not that everything was verified.
- "Tests pass" without output is not evidence; ask for the command and its output.

## Done when

- [ ] Every definition-of-done item is true, or its gap is named in the report.
- [ ] The report has all eight items and fits in about 15 lines.
- [ ] Evidence is commands and results, not adjectives.
