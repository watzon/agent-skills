# Project instruction files

Read when writing or fixing a project's always-loaded agent instructions.

Agents follow these files even when they are stale and the code disagrees, and they rarely fix them. Long or generated files cost tokens without helping. A short, correct, developer-written file helps.

## Rules

1. **Only what the agent cannot learn from the code and would need.** For each line ask: could it find this by reading the code, and would it look? If both are yes, cut it.
2. **Commands first:** build, scoped test, full-suite trigger, lint, typecheck. Exact and copy-pasteable. No "always run tests" boilerplate.
3. **Point to sources; do not copy them.** Copies go stale.
4. **No repository overview, inventories, dates, or issue numbers.** Do not auto-generate the file.
5. **Add a rule only after the same mistake repeats.**
6. **If a rule matters, enforce it** in a hook or CI ([index.md](index.md)) and keep at most a one-line pointer here. If you cannot enforce it and it is not essential, delete it.
7. **When the file and the code disagree, fix the file in the same change.** Check its paths and commands in CI if you can.
8. **Re-check after a model change** and delete rules the model no longer needs. Judge any rule change by paired runs, not one run; single runs vary widely.
9. **Keep personal or tool-specific settings in local files** so shared skills and files can be updated without overwriting them.

## Template

```
## Commands
<install> / <build> / <test one file> / <full suite, run when shared code changes> / <lint> / <typecheck>

## Conventions the code does not show
- <one line per fact, with a pointer to the source file>

## Do not
- Edit CI or required checks in a feature change
- Delete or weaken existing tests
- Commit secrets or env files
- Touch <critical paths> without owner review

## Lifecycle
Before you plan, delegate, write, test, review, or hand off code, read the agent-sdlc skill and the files it lists for your role.
```

Several agent tools in one repo: keep one core project instruction file and link it from each tool's own file.

## Done when

- [ ] Every command in the file runs as written.
- [ ] Every line passes the "could it find this, would it look" test.
- [ ] Every must-rule is enforced by a check, or is cut.
- [ ] No secrets, overviews, inventories, or dates.
