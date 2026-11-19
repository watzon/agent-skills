# Sources: verification cost

Evidence behind the token- and time-saving rules in [testing/index.md](../testing/index.md), [review/index.md](../review/index.md), [roles/coordinator.md](../roles/coordinator.md), [roles/verifier.md](../roles/verifier.md), [delegation/brief.md](../delegation/brief.md), and [integrate-release/index.md](../integrate-release/index.md). Labels and confidence as in [SOURCES.md](../SOURCES.md). [1] here means reference [1] in SOURCES.md; [79] and up are listed here. Research pass: 2026-11-18, one short targeted search.

Most rows rest on one owner observation [79]. It is one fleet's usage data, not general research: treat its numbers as that fleet's, not as rates to expect elsewhere.

## Rules

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Verification cost is worth cutting | One fleet, 30 days: verification was about 70% of agent cost; 35 of the 40 costliest threads were verify or re-verify tasks, about $4 to $39 each; about 82% of input tokens were cache reads, mostly re-read context [79] | owner | 0.6 for that fleet |
| Focused tests while working; full gate once at the end | Every verify reran the full gate, even for a small styling slice [79]; at one large company, learned test selection halved the infrastructure cost of testing changes while still reporting over 99.9% of faulty changes [80] (an ML selector at monorepo scale, not file-based selection by an agent) | owner + verified abstract | 0.6 |
| Use the repo's affected-tests mode if it has one | Same as above [80]; that the repo's own mode is good enough is inference | verified abstract + inference | 0.5 |
| Low test parallelism, 2 to 4 workers | Full-suite runs at 20 workers pushed a shared machine into memory pressure [79]; the 2-to-4 value is a house default | owner + house default | 0.5 |
| Delta re-verify with the commit range and prior findings passed in | Each fix round started a cold re-verify that re-read the diff and reran everything [79]; re-review only the new diff [1] | owner + vendor | 0.6 |
| Full gate only in the final round | Follows from the two rows above; no source tested it | inference | 0.5 |
| Gates by change type, chosen by the lead | Extends the router's tiers; the rows and their checks are a house default | inference | 0.45 |
| Verify stacks once stable, not per slice | Stacked slices were verified one by one while still moving [79]; that a lower change invalidates checks above it is inference | owner + inference | 0.5 |
| Known-issues list; confirm by signature, then move on | Known-failing checks were re-investigated every round [79]; the list format is a house default | owner + inference | 0.5 |
| Unlisted failures are findings; never retry to green | Carried from the flaky-test rule in SOURCES.md | inference | 0.5 |
| After two failed rounds the lead checks finding, brief, and design | Some slices took five rounds [79]; in one study of self-feedback refinement, most of the gain came in the first round (code optimization: 22.0, 27.0, 27.9, 28.8 over four outputs) [81], which is self-refinement, not review; the existing three-round cap [1] | owner + verified (indirect) | 0.5 |
| Short briefs that point to notes | Lead agents wrote long briefs from scratch each time [79]; "point, do not paraphrase" is already sourced in SOURCES.md | owner + inference | 0.5 |
| Single agent applies the same savings to its own re-checks | No source | inference | 0.45 |

## Not found or not read

- No source compared delta re-verification against full re-verification for agent work.
- No source set a test worker count for machines that host several agents.
- One flaky-test post from a large company was fetched, but only its comments loaded; it is not cited.
- Risk-based testing literature was not searched; the gate rows are inference.

## References

[79] Owner observation: usage data from the skill owner's own agent fleet, 30 days to 2026-11-18, not published. · [80] Machalica et al., Predictive Test Selection, ICSE-SEIP 2019, https://arxiv.org/abs/1810.05286 (abstract read) · [81] Madaan et al., Self-Refine: Iterative Refinement with Self-Feedback, NeurIPS 2023, https://arxiv.org/abs/2303.17651 (read through the per-iteration table)
