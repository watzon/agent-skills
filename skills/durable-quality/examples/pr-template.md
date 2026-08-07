# Pull request template (evidence-required)

```markdown
## Intent
<!-- What problem is this solving? Who is affected? -->

## Non-goals
<!-- What are you deliberately not doing? -->

## Approach
<!-- Brief plan. Link design notes if this is user-visible/API. -->

## Blast radius
<!-- Paths and tier: T0–T5. Call out auth/billing/migrations/CI. -->

- Paths:
- Tier:
- Owner(s):

## Proof
<!-- Commands you ran and outcomes. Paste tails. -->

```bash
# commands
```

```
# output (trimmed)
```

## Tests
<!-- What fails without this change? Where is the regression? -->

- [ ] Fail-without-change covered for behavior work
- [ ] No tests deleted/hollowed to go green
- [ ] Snapshots updated only with rationale: 

## CI and tooling
- [ ] No workflow/required-check weakening in this PR
- [ ] No secret material added
- [ ] Dependency/architecture checks still pass

## Code health
- [ ] No drive-by reformat mixed with logic
- [ ] Searched for existing utilities before adding helpers
- [ ] Docs updated if user-visible behavior changed

## Human accountability
- Author (human):
- Reviewer / owner:
- AI assistance: none | pair | agent-drafted (disclose)

## Rollback
<!-- How to undo if this breaks production -->
```
