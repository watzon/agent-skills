# Audit checklist

Score each pack: **M** missing · **W** weak · **S** solid. Cite paths/evidence.

## Repo facts (gather first)

- [ ] Languages/packages and build commands
- [ ] CI system and required checks on default branch
- [ ] Branch protection / merge rules
- [ ] Test layout and how to run locally
- [ ] Existing agent docs (`AGENTS.md`, `CLAUDE.md`, `.cursor/rules`, copilot-instructions)
- [ ] CODEOWNERS / OWNERS / MAINTAINERS
- [ ] Dependency/arch lint present?
- [ ] Secret scanning / SAST present?
- [ ] Recent AI-heavy PR patterns (size, test diffs, CI edits)

## Scorecard

| Pack | Score | Evidence | Next increment |
|---|---|---|---|
| C1 Instruction surfaces |  |  |  |
| C2 Deterministic wall |  |  |  |
| C3 Architecture as code |  |  |  |
| C4 Test honesty |  |  |  |
| C5 Evidence intake |  |  |  |
| C6 Blast-radius tiers |  |  |  |
| C7 Reuse / anti-clone |  |  |  |
| C8 Agent runtime safety |  |  |  |
| C9 Metrics / governance |  |  |  |
| C10 Human accountability |  |  |  |

## Targeted probes

- [ ] Can a feature PR weaken CI without a dedicated human-approved change?
- [ ] Is there a path map for auth/money/migrations?
- [ ] Do behavior tests fail when production logic is inverted?
- [ ] Are import boundaries enforceable in CI?
- [ ] Is there a named owner for each critical directory?
- [ ] Are agent instructions claiming rules that CI does not enforce? (lie detector)
- [ ] Average PR size / review latency trend (if data exists)
- [ ] Duplication hotspots in active modules

## Output template

```markdown
# Durable quality audit: <repo>

## Summary
<one paragraph: will this last under agent volume?>

## Scorecard
<table or list C1–C10>

## Top risks
1. ...
2. ...

## Minimal fix sequence
1. ... (small PR)
2. ...

## Non-goals this round
- ...

## Suggested mode next
bootstrap | laws | architecture | review training
```

## Severity guide

- **Blocker:** merge possible without tests on default branch; no human approval on critical paths; secrets in agent docs; CI freely weakenable
- **High:** no fail-without-change culture; no owners; no dependency rules on a layered app
- **Med:** soft agent docs without hard twins; no mutation on money path; weak PR template
- **Low:** missing dashboards; incomplete provenance labels
