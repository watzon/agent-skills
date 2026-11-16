# Sources: design foundations

Evidence behind [design/foundations.md](../design/foundations.md). Labels and confidence as in [SOURCES.md](../SOURCES.md); reference numbers are listed in [design.md](design.md). Research pass: 2026-11-16.

## Claims

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Prose body at least 16 px; reading products 18 to 20 px | Body 19 px, small 16 px "sparingly" [36]; 15 to 25 px on the web [34] | verified / secondhand | 0.6 |
| Measure target 60 to 75; under about 80 | 45 to 90 [34]; 50 to 75 [35]; AAA cap 80 [41]; `ch` is the width of "0" | verified / secondhand | 0.85 |
| Prose line height at least 1.5 | [41]; 120 to 145% [34] | secondhand | 0.75 |
| Targets at least 24 CSS px | WCAG 2.5.8 [42] | secondhand (snippet) | 0.9 |
| Mobile platforms: 44 pt and 48 dp | Platform docs; the 44 pt guideline page did not load | secondhand, unverified | 0.7 to 0.8 |
| One declared scale per value; radius 2 to 4 steps; nested = outer minus padding | Seven-step radius scale in one system [45]; rest inference | secondhand + inference | 0.55 to 0.6 |
| Typeface pairing, spacing grid, radius per brand, image ratio | No authoritative source found | gap | n/a |
| People scan; long blocks get skipped | [37] context; e-commerce only for long blocks [35] | secondhand / verified | 0.4 to 0.8 |
| Informative images get attention; decoration is ignored | [40] snippet; no trust penalty for AI images with unknown provenance [39] | secondhand / verified | 0.6 to 0.7 |
| No autoplay with sound; moving content over 5 s pausable | WCAG 2.2.2 and 1.4.2, cited from memory, not re-fetched | secondhand, unverified | 0.85 |
| Motion 100 to 500 ms; feedback about 100 ms; exit shorter; ease-out on entry | [37] | verified | 0.85 |
| No parallax, scroll-jacking, auto-carousels; reduced motion honored | [38]; WCAG 2.3.3 [43]; [44] | verified / secondhand | 0.85 to 0.9 |
| Scroll entrances opt-in | No source endorses them; [38] cautions | inference | 0.7 |
| Product-type table | Starting points built from the above | inference | 0.6 |
| Token counts (roles, steps, durations) | No source sets a count | inference | 0.5 |
| Design tokens format is a Community Group report, not a W3C Standard | Final Community Group Report, 2025.10 [33] | verified | 0.9 |
| Defaults agents pick | Carried from the round 1 tells and [4] | verified + inference | 0.5 to 0.6 |

## Where people disagree

- **Measure.** 45 to 90 [34], 50 to 75 [35], 50 to 60 (via [35]), AAA cap 80 [41]. The skill uses under about 80, target 60 to 75.
- **Body size.** 16 px is the browser default; one government system chose 19 px for reading [36]. Context, not conflict.
- **Motion ceiling.** About 500 ms for UI [37]; one system has longer steps for large transitions [46]. The context decides.

## Gaps

- No authoritative source for typeface pairing, a spacing grid, radius by brand, or image ratio; these stay judgment with a reason in the brief.
- No controlled study of density, image ratio, video, or motion against user outcomes.
- Not re-fetched: WCAG 2.2.2 and 1.4.2 (cited from memory); the 44 pt mobile guideline page did not load; one system's motion-token page was empty [46].
- Not read in full: the type-scale calculators, spacing-scale books, animation principles, and the reading-behavior study behind "people scan".
