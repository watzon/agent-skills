# 01 Spec

Read when turning a request, issue, or bug report into work you can verify.

## Steps

1. **Restate the goal** in one or two sentences, with who it is for and why it matters.
2. **Resolve intent.** Use the request and project context first. List each assumption you rely on. Ask only when a missing answer changes the result and you cannot infer it. If two readings exist, name both; do not pick one silently. Keep doing independent work while you wait.
3. **Push back** when a simpler approach meets the goal. Say so before building.
4. **Write acceptance criteria** as checks someone can run:
   - "Add validation" → "These invalid inputs return error X; tests prove it."
   - "Fix the bug" → "This repro fails now and passes after."
   - "Refactor X" → "Existing tests pass before and after; public behavior unchanged."
5. **List non-goals**: what you will deliberately not do.
6. **Pick the risk tier** from the router table. List the files or modules you expect to touch (the scope allowlist).
7. **Note the proof plan**: which tests or commands will show each criterion holds.

## Artifact

Where the project keeps specs (issue, SPEC.md, task brief). Shape:

```
Goal: ...
Acceptance criteria:
- [ ] AC1 ... (proof: command or test)
Non-goals: ...
Tier: T?  Scope: paths...
Assumptions / open questions: ...
```

Size: one line for T0. Never skip for a behavior change.

## Done when

- [ ] Every acceptance criterion is checkable by running something.
- [ ] Tier and scope allowlist are written down.
- [ ] Assumptions are stated; blocking questions are asked or answered.
- [ ] Non-goals are listed for T1+.
