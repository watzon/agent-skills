# Sources: verification cost

Evidence behind the token- and time-saving rules in [testing/index.md](../testing/index.md), [review/index.md](../review/index.md), [roles/coordinator.md](../roles/coordinator.md), [roles/verifier.md](../roles/verifier.md), [delegation/brief.md](../delegation/brief.md), and [integrate-release/index.md](../integrate-release/index.md). Labels and confidence as in [SOURCES.md](../SOURCES.md). [1] here means reference [1] in SOURCES.md; [79] and up are listed here. Research pass: 2026-11-18, one short targeted search.

Most rows rest on one owner observation [79]. It is one fleet's usage data, not general research: treat its numbers as that fleet's, not as rates to expect elsewhere.

## Rules

| Rule | Basis | Label | Conf. |
|---|---|---|---|
| Verification cost is worth cutting | One fleet, 30 days: verification was about 70% of agent cost; 35 of the 40 costliest threads were verify or re-verify tasks, about $4 to $39 each; about 82% of input tokens were cache reads [79]. That those reads were mostly re-read context is the owner's interpretation, not measured | owner (observed) + owner interpretation | 0.6 for that fleet |
| Focused tests while working | Every verify reran the full gate, even for a small styling slice [79]; at one large company, a learned test selector beat dependency-based selection, halving testing infrastructure cost while still reporting over 99.9% of faulty changes [80] (a learned selector at monorepo scale, not file-based selection by an agent) | owner + verified abstract | 0.6 |
| Use the repo's affected-tests mode if it has one | [80] compares a learned selector with dependency-based selection; it does not show that any affected-tests mode is sufficient. That the repo's own mode is good enough for local work, with CI as the backstop, is inference | inference | 0.45 |
| Low test parallelism, 2 to 4 workers | Full-suite runs at 20 workers pushed a shared machine into memory pressure [79]; the 2-to-4 value is a house default | owner + house default | 0.5 |
| Re-verify from the delta, with the commit range and prior findings passed in | Each fix round started a cold re-verify that re-read the diff and reran everything [79]; one vendor capped review at three rounds and re-reviewed only the new diff after the first few passes, not right after round one [1]. Starting delta scope at round two is a house default | owner + vendor + house default | 0.55 |
| Widen to affected consumers; re-baseline after rebase or unclear impact | A worked counterexample from review of this skill: a shared rounding change fixed the failing display check while an unchanged export consumer broke, and a delta-only check passed. No study | inference | 0.6 |
| Row gates on the final candidate; rerun only when it changes; "once" means no redundant run | Follows from the rows above; no source tested it | inference | 0.5 |
| Gates by change type, chosen by the lead; required hooks and CI take precedence | Extends the router's tiers; the rows and their checks are a house default | house default | 0.45 |
| Verify stacks once stable; focused checks per slice and combination; required gates on anything that lands | Stacked slices were verified one by one while still moving [79]; that a lower change invalidates checks above it is inference | owner + inference | 0.5 |
| Known-issues list; a signature is a lead; confirm on the base before calling a failure pre-existing | Known-failing checks were re-investigated every round [79]; the list format and the base check are house defaults | owner + house default | 0.5 |
| Unlisted failures are findings; never retry to green; a list entry never waives CI | Carried from the flaky-test rule in SOURCES.md | inference | 0.5 |
| After two failed rounds the lead checks finding, brief, and design, inside the three-round cap | Some slices took five rounds [79]; the three-round cap is sourced [1]. In one self-refinement study, Fig. 4 shows most code-optimization gain in the first round (22.0, 27.0, 27.9, 28.8 over four outputs) [81]; that is self-refinement, not review, and does not support a two-round threshold. The threshold is a house default | owner + vendor + house default | 0.45 |
| Solo agent: unmet independent review goes to a person; it runs the two-round check itself | Follows from the fresh-context review rule in SOURCES.md; no source | inference | 0.5 |
| Short briefs that point to notes | Lead agents wrote long briefs from scratch each time [79]; "point, do not paraphrase" is already sourced in SOURCES.md | owner + inference | 0.5 |
| Single agent applies the same savings to its own re-checks | No source | inference | 0.45 |

## Not found or not read

- No source compared delta re-verification against full re-verification for agent work.
- No source set a test worker count for machines that host several agents.
- One flaky-test post from a large company was fetched, but only its comments loaded; it is not cited.
- Risk-based testing literature was not searched; the gate rows are inference.

## References

[79] Owner observation: usage data from the skill owner's own agent fleet, 30 days to 2026-11-18, not published. · [80] Machalica et al., Predictive Test Selection, ICSE-SEIP 2019, https://arxiv.org/abs/1810.05286 (abstract read) · [81] Madaan et al., Self-Refine: Iterative Refinement with Self-Feedback, NeurIPS 2023, https://arxiv.org/abs/2303.17651 (per-iteration numbers in Fig. 4 checked)
