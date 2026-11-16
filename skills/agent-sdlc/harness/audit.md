# Repo audit

Read when asked to audit a repository's readiness for agent-written changes. Not for ordinary feature work. Make no fixes unless the request includes them.

## Gather facts first

Build commands; CI system and required checks; branch protection; how to run a scoped test; agent instruction files; ownership files; dependency rules; secret scanning; recent agent-heavy pull requests (size, test diffs, CI edits).

## Scorecard

Score each area **M** missing, **W** weak, **S** solid. Cite a path or evidence for every score. The areas and severities are engineering defaults (inference).

| Area | Solid means |
|---|---|
| C1 Instructions | Short file with exact commands; every check it names exists in CI; no stale paths ([instruction-files.md](instruction-files.md)) |
| C2 Deterministic wall | Format, lint, types, tests, secret scan are required checks; red blocks merge |
| C3 Architecture as code | Dependency direction and cycles enforced in CI; legacy violations baselined |
| C4 Test honesty | Bug fixes come with repro tests; existing-test edits are flagged; coverage is not the only gate |
| C5 Evidence intake | PRs state intent, commands with output, risk, and how to revert |
| C6 Risk tiers | Auth, money, migrations, CI, and release paths have owners and human review |
| C7 Reuse | Duplication is searched for or detected |
| C8 Agent safety | Sandboxed; least-privilege tokens; untrusted text never drives commands ([index.md](index.md)) |
| C9 Accountability | A named person owns each merge on critical paths; agent approval is not sign-off |

## Probes

- Can a feature change weaken CI without a separate, approved change?
- Do tests fail when the production logic is inverted?
- Does the instruction file claim rules that CI does not enforce?
- Can an agent that reads issues or web pages also reach secrets and send data out?

## Severity

- **Blocker:** merge possible without tests; no human on critical paths; secrets in agent files; CI freely weakened; lethal trifecta open.
- **High:** no repro-test practice; no owners; stale commands in the instruction file.
- **Medium:** soft rules with no enforcing check; weak PR template.
- **Low:** missing dashboards.

## Output

```
# Agent-readiness audit: <repo>
Summary: <one paragraph>
Scorecard: C1-C9 with evidence
Top risks: 1..3
Fix sequence: small, independently landable changes (see index.md setup sequence)
```

## Done when

- [ ] Every area scored with cited evidence.
- [ ] Top risks ranked by severity.
- [ ] The fix sequence is a list of small, ordered changes.
