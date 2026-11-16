# Review

Read when reviewing a diff (your own, another agent's, or a pull request), or when deciding whether review is done.

## Rules

1. **Checks before review.** The author runs tests, typecheck, lint, and build, and attaches the commands and output. No output: send it back before reading the diff.
2. **Fresh context.** The reviewer gets the spec (criteria and tier), the diff, and the test output. Not the author's transcript or reasoning. At T1 and up, self-review alone does not count.
3. **Blocking or nit.** Blocking: wrong against the spec, security or data loss, failing or weakened tests, weakened CI, broken integration. Nit: style, taste, naming preference. Nits never block. Pre-existing problems are reported, not blocked on.
4. **Every finding cites `file:line` and evidence:** a command, a test, or a reproduction. A finding without evidence is a hypothesis and does not block.
5. **Stop when no blocking findings remain.** Do not keep hunting for nits; a reviewer told to find problems will report some.
6. **Hard cap: three rounds.** After the first round, re-review only the new diff. Do not repeat findings already given; name the bug class, not one line.
7. **Escalate** to a stronger reviewer or a person when the same finding returns after a fix, the author disputes a blocking finding twice, or the cap is reached with blockers open. At the cap, step back and reconsider the approach or scope rather than patching again.

## How to read the diff

Hard blockers first, then the ordered checklist: [checklist.md](checklist.md). Read test and CI diffs before production code.

## Size

One self-contained change per review. A widely used guide: about 100 changed lines is usually fine and 1,000 usually too large; spread matters too (200 lines in one file can be fine, 200 lines across 50 files is too large). Ask for a split before reviewing a change too big to review well.

## Who reviews

- T1 and up: a fresh-context agent that did not write the change. A different model is optional; one study found the benefit runs in one direction only.
- Humans by tier (router table). Auth, billing, CI, and release paths always need a person. An agent's approval never counts as human approval, and an approval covers only the commit it reviewed.

## Author response

Fix every blocking finding. For each nit, fix it or decline it with a reason. Never skip a blocking finding silently.

## Verdict

Approve, approve with nits, or request changes, plus the findings list. Each finding: severity, `file:line`, evidence.

## Done when

- [ ] Check output was present before review began.
- [ ] Every acceptance criterion was traced to code and a test.
- [ ] Every finding has a severity, `file:line`, and evidence.
- [ ] Zero open blocking findings, or the change is escalated.
- [ ] No more than three rounds were used.
