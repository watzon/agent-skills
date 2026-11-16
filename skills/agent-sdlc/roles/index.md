# Roles

Read when you take on a role in a task, or must assign roles and no named agents exist.

Roles are capabilities, not names. Map them onto whatever agents exist.

| Role | Does | Give it to | File |
|---|---|---|---|
| Coordinator | Specs, splits, routes, tracks, decides, reports | The most capable agent, or you | [coordinator.md](coordinator.md) |
| Implementer | Writes code and tests to a spec | Strongest tier for hard or ambiguous work; cheaper tier for well-specified routine work | [implementer.md](implementer.md) |
| Reviewer | Reads the diff against the spec, finds defects | A clean-context agent that did not write the code | [reviewer.md](reviewer.md) |
| Verifier | Runs the change and tries to break it | A different agent from the author | [verifier.md](verifier.md) |
| Researcher | Reads, searches, summarizes with sources; edits nothing | Cheapest tier that reads well | [researcher.md](researcher.md) |

(The capability split is inference; see [SOURCES.md](../SOURCES.md).)

## Mapping

- **Named role agents exist:** route by role, then by difficulty. Easy work goes down a tier; ambiguous or design-heavy work goes up.
- **Generic or identical agents:** assign the role in each brief ([delegation/brief.md](../delegation/brief.md)). Give reviewer and verifier a fresh agent with the spec and diff, not the author's context.
- **One agent only:** play the roles in sequence. Spec, implement, then clear your head and re-read the diff as a reviewer against the criteria, then run it as a verifier.

## Fixed rules

- The author never reviews or verifies its own work as the only check at T1+.
- One writer per file or module at a time.
- A weaker agent often does not know when to escalate. Every brief states its stop rule.

## Done when

- [ ] Every role the tier needs has an owner (T0: implementer; T1+: plus a separate reviewer; T3: plus a human approver).
- [ ] Reviewer and verifier are not the author.
- [ ] Each assigned agent has read its role file.
