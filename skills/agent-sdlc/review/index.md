# Review

Read when reviewing a diff (your own, another agent's, or a pull request), or when deciding whether review is done.

## Rules

1. **Checks before review.** The author attaches the commands and output of the evidence this round needs, per [Which gates run when](../testing/index.md#which-gates-run-when): scoped evidence on intermediate and fix rounds, the full selected row on the final handoff candidate. Required hooks and CI run as configured. No output: send it back before reading the diff.
2. **Fresh context.** The reviewer gets the spec (criteria and tier), the diff, and the test output. Not the author's transcript or reasoning. At T1 and up, self-review alone does not count as the independent review. A single agent that cannot start a fresh-context reviewer still does its own review pass, records "independent review: not met", and hands the change to a person for review instead of landing it.
3. **Blocking or nit.** Blocking: wrong against the spec, security or data loss, failing or weakened tests, weakened CI, broken integration. Nit: style, taste, naming preference. Nits never block. Pre-existing problems are reported, not blocked on.
4. **Every finding cites `file:line` and evidence:** a command, a test, or a reproduction. A finding without evidence is a hypothesis and does not block.
5. **Stop when no blocking findings remain.** Do not keep hunting for nits; a reviewer told to find problems will report some.
6. **Hard cap: three rounds.** Do not repeat findings already given; name the bug class, not one line.
7. **Re-verify from the delta; widen when needed.** A re-review gets the commit range since the last round and the prior findings, so it does not re-derive them. The delta is the default scope, not the limit: the new commits, each prior finding, and scoped evidence for the changed files ([testing/index.md](../testing/index.md#which-gates-run-when)).
   - **Widen** to the affected consumers (callers, importers, outputs built from the changed behavior) when the delta changes shared behavior, a contract or interface, config, dependencies, fixtures, or CI. A fix can repair the check that failed while breaking an unchanged consumer that a delta-only check never runs.
   - **Re-establish the baseline** (review the whole change against its base again) after a rebase, a history rewrite, or a change in the upstream stack, or when you cannot tell what the delta affects.
   - The full row runs once, at final handoff; reruns follow [testing/index.md](../testing/index.md#which-gates-run-when). A single agent re-checking its own work does the same.
8. **Escalate at once** to a stronger reviewer or a person when the same blocking finding returns after a fix or the author disputes a blocking finding twice. Do not wait for round three or the two-round check. (Both triggers are inference.)
9. **Two failed rounds on one item: the lead checks before a third,** per [roles/coordinator.md](../roles/coordinator.md). The check sits inside the cap; it adds no round. When it needs a person's decision, round three waits for it. (Owner observation plus inference.)
10. **At the cap with blockers open,** escalate; step back and reconsider the approach or scope rather than patching again.
11. **Stacks:** focused checks per slice, the required gates on anything that lands, full review and verification on the stable combined candidate ([integrate-release/index.md](../integrate-release/index.md)).

## How to read the diff

Hard blockers first, then the ordered checklist: [checklist.md](checklist.md). Read test and CI diffs before production code.

## Size

One self-contained change per review. A widely used guide: about 100 changed lines is usually fine and 1,000 usually too large; spread matters too (200 lines in one file can be fine, 200 lines across 50 files is too large). Ask for a split before reviewing a change too big to review well.

## Who reviews

- T1 and up: a fresh-context agent that did not write the change. None available: a person, per rule 2. A different model is optional; one study found the benefit runs in one direction only.
- Humans by tier (router table). Auth, billing, CI, and release paths always need a person. An agent's approval never counts as human approval, and an approval covers only the commit it reviewed.

## Author response

Fix every blocking finding. For each nit, fix it or decline it with a reason. Never skip a blocking finding silently.

## Verdict

Approve, approve with nits, or request changes, plus the findings list. Each finding: severity, `file:line`, evidence.

## Done when

- [ ] Output of the evidence the round needs (scoped, or the full row at final handoff) was present before review began.
- [ ] Every acceptance criterion was traced to code and a test.
- [ ] Every finding has a severity, `file:line`, and evidence.
- [ ] Zero open blocking findings, or the change is escalated.
- [ ] At T1 and up, an agent other than the author or a person reviewed it, or the gap is recorded and escalated.
- [ ] No more than three rounds were used.
- [ ] Each re-review covered the delta and prior findings, widened to affected consumers or re-baselined where rule 7 says.
- [ ] Gates ran and reran per [testing/index.md](../testing/index.md#which-gates-run-when).
