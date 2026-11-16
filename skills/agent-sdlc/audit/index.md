# Audit

Read when asked to audit a repository's quality, harden it for agent-written changes, add CI safeguards, or write agent rules. Not for ordinary feature work.

| Goal | Read |
|---|---|
| Score a repo and propose a fix order | This file |
| Add the minimum CI and ownership safeguards | [harness.md](harness.md) |
| Write or fix AGENTS.md (or the repo's agent instructions file) | [agents-md.md](agents-md.md) |
| Review an agent-written pull request | [05-review](../05-review/index.md) and [failure-modes](../failure-modes/index.md) |

## Gather facts first

Languages and build commands; CI system and required checks on the default branch; branch protection; test layout and how to run a subset; agent instruction files; ownership files; dependency or architecture lint; secret scanning; recent agent-heavy pull requests (size, test diffs, CI edits).

## Scorecard

Score each pack **M** missing, **W** weak, **S** solid. Cite a path or evidence for every score.

| Pack | Solid means |
|---|---|
| C1 Instructions | A lean agent file lists exact commands, forbidden paths, and the done bar; every check it names exists in CI |
| C2 Deterministic wall | Format, lint, types, tests, and secret scan are required checks; merge is blocked when red |
| C3 Architecture as code | Dependency direction and cycles enforced in CI; legacy violations baselined, new ones fail |
| C4 Test honesty | Behavior changes come with tests that fail without the change; coverage is not the only gate |
| C5 Evidence intake | Pull requests state intent, commands run with output, risks, and tier |
| C6 Risk tiers | Auth, money, migrations, and infra paths are mapped to owners and heavier checks |
| C7 Reuse | Duplication is searched for or detected; helpers are extended, not cloned |
| C8 Agent runtime safety | Least-privilege tokens; untrusted text never drives commands; destructive actions need approval |
| C9 Metrics | Review time, change-fail rate, and churn are visible beside throughput |
| C10 Human accountability | A named person owns each merge on critical paths; model approval is not sign-off |

## Probes

- Can a feature change weaken CI without a separate, approved change?
- Do behavior tests fail when the production logic is inverted?
- Does the agent file claim rules that CI does not enforce? (Lie detector.)
- Is there a named owner for each critical directory?

## Severity

- **Blocker:** merge possible without tests; no human approval on critical paths; secrets in agent files; CI freely weakened.
- **High:** no fail-without-change practice; no owners; no dependency rules in a layered app.
- **Medium:** soft rules with no enforcing check; no mutation or property tests on money paths; weak PR template.
- **Low:** missing dashboards; incomplete provenance labels.

## Output

```
# Quality audit: <repo>
Summary: <one paragraph: will this hold up under agent volume?>
Scorecard: C1-C10 with evidence
Top risks: 1..3
Fix sequence: small, ordered changes (see harness.md)
Non-goals this round
```

## Done when

- [ ] All ten packs scored, each with cited evidence.
- [ ] Top risks ranked by severity.
- [ ] Fix sequence is a list of small, independently landable changes.
- [ ] No fixes were made unless the request included them.
