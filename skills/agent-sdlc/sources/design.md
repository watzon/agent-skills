# Sources: design

Evidence behind [design/](../design/index.md); foundations evidence is in [foundations.md](foundations.md), logo evidence in [logo.md](logo.md). Labels and confidence as in [SOURCES.md](../SOURCES.md). Research pass: 2026-11-16. No controlled study compares a design process or anti-slop skill with a plain baseline on user preference, accessibility, or task success; the evidence is originality benchmarks, vendor galleries, and practitioner skills.

## Why a process, not a ban list

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Unprompted output drifts to the typical design | Vendor names it "distributional convergence" [2]; models scored 0.592 originality vs 0.764 human-vs-model, and 0.581 creative range vs 0.902 for humans; appropriateness above 90% for all models; authors sell UI tools [3] | vendor + verified | 0.85 direction; 0.4 magnitude |
| AI sites sit at the center of the human range | 945 award sites vs three AI outputs on one brief [4] | verified, small | 0.5 |
| Ban lists move the default instead of removing it | A vendor guide bans common fonts and palettes, then notes the model converges on another font [5]; each year's list differs [1] [4] | verified | 0.85 that lists go stale within a release or two |

## Process (design/index.md)

| Step | Basis | Label | Conf. |
|---|---|---|---|
| Order: purpose and name, brand, then logo and mascot in the order the brief sets, then foundations and directions | Owner direction for this skill; brand before identity matches practice [10] [11]; logo-first and character-first both occur [20] [21] | owner + secondhand / verified | 0.8 |
| 1 Existing system wins | The brief's own choices win [1]; a skill checks values against the project's design file [6] | verified / secondhand | 0.9 |
| 2 Purpose, audience, job, one action; a name before visual work | [1]; naming in the strategy phase [10]; a name constrains the mark [11] | verified / secondhand | 0.8 |
| 4 Content hierarchy first; copy is design | [1] | verified | 0.8 |
| 4 Draft 3 to 5 directions, differing on two axes (house default counts) | Built on [1]'s plan-then-review step | inference | 0.6 to 0.7 |
| 4 References from the subject's materials and trade | "the subject's industry, subject matter, materials, and vernacular are where distinctive visual choices come from" [1] | verified | 0.7 |
| 4 Avoid style words in briefs | Brief design in [4] | verified | 0.5 |
| 4 Choose, log rejects, compare with the generic default | Review the plan against "the generic default you would produce" [1]; rejects log is inference | verified + inference | 0.65 |
| 4 Brief wins on pinned axes; risk on the rest | Reconciles "take aesthetic risk if justified" [1] with "redirecting a clear brief is failure" [6] | inference | 0.7 |
| 4 No random seeds or dealt directions | See disagreements | inference | 0.6 |
| 6 Screenshot at desktop and phone width | [7]; [1] critique step | verified, vendor | 0.75 |
| 7 Report direction, reasons, rejects | Decision brief pattern [6] | secondhand | 0.6 |
| Logo-only scope; a design report instead of the code report | Test feedback: a logo task loaded about ten files and a code report format | inference | 0.6 |

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

## Brand (design/brand.md)

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Strategy and naming before identity | Research, strategy (positioning, brief, naming), then identity [10]; "a logo reflects the company" [11] | secondhand / verified | 0.8 |
| An undrawable name moves the mark to the product's reference | "The word 'next' is not depictable"; the mark used the product's cube [11] | verified | 0.85 |
| The brief is the reference the mark is checked against | [10] [11] | secondhand / verified | 0.75 |
| Draft 3 to 5 brand directions, log rejects | Carried from the forced-divergence step; no brand-specific source | inference | 0.6 |
| List the neighbors before drafting directions; label them studied or from memory | No source; it feeds the position line | inference | 0.5 |
| Counts: three brand words, two anti-references | No source; house defaults | inference | 0.4 |
| Simplicity aids recall | Rand's analysis: easy to draw, drawable after a glance [12] | verified (practitioner, not a study) | 0.8 |
| Distinctive shapes carry recognition best | 2026 study, title and abstract only (403) [18] | secondhand | 0.5 |
| Archetypes are prompts, not evidence | A brand consultant calls them pseudoscience but useful [16] | secondhand (snippet) | 0.6 |
| Trend reports describe what is shown, not what works | [23] [47] read as trend lists | inference | 0.7 |
| Rejected folklore: "color increases brand recognition by 80%" | Earliest source a 2001 leaflet; the study it cites lacks the figure [17]. Not used in any rule | secondhand | 0.8 |

## Logo, mascot, deliverables

Moved to [logo.md](logo.md).

## Where people disagree

- **Ban list vs process.** One skill's value is mostly refusals and a detector [6]; another's is the plan and review against the brief [1]. This skill keeps the process; a detector is optional.
- **Cream and beige.** Called a tell [1] [6], but [6] says keep it when it fits the product; another vendor bans it outright [7]. The questions test the reason, not the color.
- **Taste as thresholds.** Half of one skill's rules are taste written as numeric thresholds; only readability and defect rules have outside anchors [6]. Floor checks keep only the anchored ones.
- **Rule counts.** Published counts for the same skills disagree (57 to 67); do not quote one.
- **Brand or logo first.** Strategy first [10] [11]; some designers fix type and color first and draw the mark inside them. Resolved: the brief first, the mark checked against it.
- **Identify or charm.** "Designed to identify" [11] vs mascot practice, where charm is the point [19]. Resolved: a mascot must still identify.
- **Option count:** see [logo.md](logo.md).
- **Random or dealt directions.** Some skills deal directions from a catalog by seed, or log draws so consecutive builds differ [6] [9]. Considered and rejected: no measured effect (confidence 0.3 to 0.35), and variety here comes from the subject and the forced comparison instead.

## Gaps

- No controlled study of design skills on user preference, accessibility, or task success.
- One vendor's gallery and catalog are private; vendor figures are qualitative.
- Not read: several brand and design-system skills, component-library guidance, full texts of [9], the original prevalence scan, homogeneity papers.
- Type-scale ratios and the 8-point spacing convention are unverified here; the token format is checked in [foundations.md](foundations.md).
- Unread: a logo complexity study (title only), archetype studies, the image-to-SVG paper [30], full texts of [11] [18] [23], the strategy book behind [10]. Logo gaps are in [logo.md](logo.md).

## References

[1] https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md · [2] https://claude.com/resources/articles/improving-frontend-design-through-skills · [3] https://arxiv.org/abs/2610.11539 · [4] https://ai-design-convergence.vercel.app/ · [5] https://platform.claude.com/cookbook/coding-prompting-for-frontend-aesthetics · [6] https://ai.satyajit.si/articles/impeccable-design-skill (secondhand view of https://github.com/pbakaus/impeccable) · [7] https://developers.openai.com/api/docs/guides/frontend-prompt · [8] https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum · [9] https://github.com/Nutlope/hallmark · [10] https://www.logodesignlove.com/brand-identity-process · [11] https://www.paulrand.design/life/interviews/1988-id-magazine.html · [12] https://www.printmag.com/branding-identity-design/6-logo-tips-master-paul-rand/ · [13] https://www.logodesignlove.com/how-many-options · [14] https://logogeek.uk/logo-design/presenting-one-logo/ · [15] https://academic.oup.com/jcr/article-abstract/37/3/409/1827647 (summary: https://www.thewhyweproject.com/reports/evidence-reviews/choice-overload) · [16] https://www.thedrum.com/opinion/yes-brand-archetypes-are-pseudoscience-does-make-them-completely-useless · [17] https://www.insights4print.ceo/2019/02/color-increases-brand-recognition-by-80-the-real-contents-of-the-loyola-study-revealed/ · [18] https://www.tandfonline.com/doi/full/10.1080/02650487.2026.2637295 · [19] https://www.adobe.com/creativecloud/design/discover/mascot-logo-design.html · [20] https://www.pentagram.com/work/brooklyn-children-s-museum · [21] https://brandlic.studio/brand-mascots/ · [22] https://www.creativeboom.com/news/studio-kiln-builds-a-shape-shifting-character-for-weight-loss-app-reset/ · [23] https://www.logolounge.com/trend/2026-logo-trend-report · [24] https://www.logohistories.com/p/asymmetrical-logos · [25] https://addaly.com/learn/vector-and-print/logo-at-sixteen-pixels · [26] https://node36.app/guides/logo-scale-proofing · [27] https://www.zolveno.com/small-size-logo-testing · [28] https://www.recraft.ai/blog/can-chatgpt-make-svg-files · [29] https://arxiv.org/abs/2506.03139 · [30] https://openaccess.thecvf.com/content/CVPR2025/papers/Rodriguez_StarVector_Generating_Scalable_Vector_Graphics_Code_from_Images_and_Text_CVPR_2025_paper.pdf · [31] https://www.varnumlaw.com/insights/using-generative-ai-in-branding-and-trademarks/ · [32] https://www.atomm.com/blog/2887-how-to-present-a-logo · [33] https://www.designtokens.org/TR/2025.10/format/ · [34] https://practicaltypography.com/line-length.html · [35] https://baymard.com/research-articles/line-length-readability · [36] https://design-system.service.gov.uk/styles/paragraphs/ · [37] https://www.nngroup.com/articles/animation-duration/ · [38] https://www.nngroup.com/articles/animation-usability/ · [39] https://www.nngroup.com/articles/ai-generated-images/ · [40] https://www.nngroup.com/articles/photos-as-web-content/ · [41] https://www.w3.org/WAI/WCAG22/Understanding/visual-presentation · [42] https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html · [43] https://wcag.a11y.ing/en/wcag/operable/seizures-and-physical-reactions/animation-from-interactions/ · [44] https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion · [45] https://m3.material.io/styles/shape/corner-radius-scale · [46] https://m3.material.io/styles/motion/overview/specs · [47] https://www.creativebloq.com/design/logos-icons/these-logo-design-trends-will-define-2026
