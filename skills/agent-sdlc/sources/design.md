# Sources: design

Evidence behind [design/](../design/index.md). Labels and confidence as in [SOURCES.md](../SOURCES.md). Research pass: 2026-11-16. No controlled study compares a design process or anti-slop skill with a plain baseline on user preference, accessibility, or task success; the evidence is originality benchmarks, vendor galleries, and practitioner skills.

## Why a process, not a ban list

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Unprompted output drifts to the typical design | Vendor names it "distributional convergence" [2]; models scored 0.592 originality vs 0.764 human-vs-model, and 0.581 creative range vs 0.902 for humans; appropriateness above 90% for all models; authors sell UI tools [3] | vendor + verified | 0.85 direction; 0.4 magnitude |
| AI sites sit at the center of the human range | 945 award sites vs three AI outputs on one brief [4] | verified, small | 0.5 |
| Ban lists move the default instead of removing it | A vendor guide bans common fonts and palettes, then notes the model converges on another font [5]; each year's list differs [1] [4] | verified | 0.85 that lists go stale within a release or two |

## Process (design/index.md)

| Step | Basis | Label | Conf. |
|---|---|---|---|
| 1 Existing system wins | The brief's own choices win [1]; a skill checks values against the project's design file [6] | verified / secondhand | 0.9 |
| 2 Subject, audience, job, one action | [1] | verified | 0.8 |
| 3 Content hierarchy first; copy is design | [1] | verified | 0.8 |
| 4 Draft 3 to 5 directions, differing on two axes | Built on [1]'s plan-then-review step | inference | 0.6 to 0.7 |
| 4 References from the subject's materials and trade | "the subject's industry, subject matter, materials, and vernacular are where distinctive visual choices come from" [1] | verified | 0.7 |
| 4 Avoid style words in briefs | Brief design in [4] | verified | 0.5 |
| 5 Choose, log rejects, compare with the generic default | Review the plan against "the generic default you would produce" [1]; rejects log is inference | verified + inference | 0.65 |
| 5 Brief wins on pinned axes; risk on the rest | Reconciles "take aesthetic risk if justified" [1] with "redirecting a clear brief is failure" [6] | inference | 0.7 |
| 6 Color by role, one or two families, one type scale, one spacing scale, tokens carry the reason | [1]; [6] | vendor | 0.55 to 0.7 |
| 6 Brand, logo, mascot, imagery, video order | Owner direction for this skill; round 2 research pending | inference | low |
| 8 Screenshot at desktop and phone width | [7]; [1] critique step | verified, vendor | 0.75 |
| 9 Report direction, reasons, rejects | Decision brief pattern [6] | secondhand | 0.6 |

## Floor checks (design/floor-checks.md)

| Check | Basis | Label | Conf. |
|---|---|---|---|
| 4.5:1 normal text, 3:1 large text | WCAG 2.2 SC 1.4.3 [8] | verified | 0.95 |
| Content visible by default | Detector rule on content hidden at rest [6] | secondhand | 0.7 |
| Render checks: overflow, overlap, blank | [7] | verified, vendor | 0.75 |
| Visible focus; reduced motion | [1]; [6] | vendor | 0.6 to 0.65 |
| Body lines under about 80 characters | [1]; another skill says 65 to 75 [6] | vendor | 0.6 |
| No invented numbers, testimonials, logos | A design skill's gate [9] | verified | 0.8 |
| Date-stamp banned lists; review each model release | Shifts between 2025 and 2026 lists [5] [1] [4] | verified | 0.85 |
| Default-look questions (eyebrows, numbering, side stripes, gradients, nested cards, entrance on every section) | 2026 tells named in [1] [6] [9]; written as questions so they test the reason, not the look | verified + inference | 0.5 to 0.6 |

## Where people disagree

- **Ban list vs process.** One skill's value is mostly refusals and a detector [6]; another's is the plan and review against the brief [1]. This skill keeps the process; a detector is optional.
- **Cream and beige.** Called a tell [1] [6], but [6] says keep it when it fits the product; another vendor bans it outright [7]. The questions test the reason, not the color.
- **Taste as thresholds.** Half of one skill's rules are taste written as numeric thresholds; only readability and defect rules have outside anchors [6]. Floor checks keep only the anchored ones.
- **Rule counts.** Published counts for the same skills disagree (57 to 67); do not quote one.
- **Random or dealt directions.** Some skills deal directions from a catalog by seed, or log draws so consecutive builds differ [6] [9]. Considered and rejected: no measured effect (confidence 0.3 to 0.35), and variety here comes from the subject and the forced comparison instead.

## Gaps

- No controlled study of design skills on user preference, accessibility, or task success.
- One vendor's gallery and catalog are private; vendor figures are qualitative.
- Not read: several brand and design-system skills, component-library guidance, full texts of [9], the original prevalence scan, homogeneity papers.
- Type-scale ratios, the 8-point spacing convention, and design-token formats are unverified here.
- Brand, logo, mascot, and foundations research arrives in round 2 ([design/brand.md](../design/brand.md), [design/foundations.md](../design/foundations.md)).

## References

[1] https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md · [2] https://claude.com/resources/articles/improving-frontend-design-through-skills · [3] https://arxiv.org/abs/2610.11539 · [4] https://ai-design-convergence.vercel.app/ · [5] https://platform.claude.com/cookbook/coding-prompting-for-frontend-aesthetics · [6] https://ai.satyajit.si/articles/impeccable-design-skill (secondhand view of https://github.com/pbakaus/impeccable) · [7] https://developers.openai.com/api/docs/guides/frontend-prompt · [8] https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum · [9] https://github.com/Nutlope/hallmark
