# Spec

Read when turning a request, issue, or bug report into work you can check.

## Rules

1. **Size the spec to the cost of a wrong guess.** Fixed heavy workflows for every change size are where spec-driven tools fail.

   | Change | Spec |
   |---|---|
   | T0: typo, docs | None. The request is the spec. |
   | Small, one module | One line of intent plus acceptance criteria. |
   | Multi-file, interface, or data-shape change | Criteria plus a [design note](design-note.md). |
   | Multi-session work | A feature list: each item a check that starts failing, where only its pass/fail state may change. Keep it in a structured format (JSON) rather than prose. |

2. **Write acceptance criteria as checks that run.** Where you can, write each one as a test first and run it to see it fail. "Add validation" becomes "these inputs return error X; this test proves it."
3. **One verifiable unit per session.** Do not try to build the whole thing in one pass. Each unit ends in a check that passes.
4. **Gather, then build fresh.** For larger work, settle the requirements first (ask the person until the answers add up to a spec), then build in a fresh session that starts from the written spec.
5. **Ask only when a wrong guess is costly to reverse.** Otherwise state the assumption and continue. If a request has two readings, name both. (Inference; no source counts questions.)
6. **Push back** when a simpler approach meets the goal. Say so before building.
7. **Do not keep prose specs in the repo by default.** They go stale and agents follow stale text. Code and tests are the source of truth; the spec ends up in the commit message or PR description. Keep a living plan with a decision log only for multi-session work, and update it when discovery changes the plan.
8. **If reviewing the spec would take longer than reviewing the code, the spec is too big.**

## Template

```
Goal: <one or two sentences: what and why>
Acceptance criteria:
- [ ] <check: command or test>
Non-goals: <what you will not do>
Tier: T?   Scope: <paths you expect to touch>
Assumptions: <each one you rely on>
```

## Done when

- [ ] Every acceptance criterion is checkable by running something.
- [ ] The spec is no bigger than the change deserves.
- [ ] Tier, scope, and assumptions are written down; costly-to-reverse questions are asked.
- [ ] Multi-session work has a feature list and one unit is chosen for this session.
