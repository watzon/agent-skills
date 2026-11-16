# Sources: logo, mascot, deliverables

Evidence behind [design/logo.md](../design/logo.md), [design/logo-deliverables.md](../design/logo-deliverables.md), and [design/mascot.md](../design/mascot.md). Labels and confidence as in [SOURCES.md](../SOURCES.md). Research pass: 2026-11-16. References [1] to [47] are listed in [design.md](design.md); [48] onward are below. "Test feedback" means one agent run that followed an earlier version of this skill; it is one case, so rules resting on it are labeled inference.

## Process (design/logo.md)

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Logo and mascot order decided per brand | A museum mascot became the logo [20]; a mascot drawn from an existing logo [21] | verified / secondhand | 0.6 |
| Kinds of mark, including pictorial, emblem, geometric | Practice table; no study compares kinds on outcomes | inference | 0.5 |
| Minimal is a choice, not a default | Six studies: more descriptive logos improved evaluations, less so for familiar brands [55]; simple flat logos raised consumption for non-prestige food and reversed for prestige food [54]; the simplest version of a responsive set was least helpful for recognition [53] | secondhand / verified abstract / verified abstract | 0.55 |
| Complex marks allowed | Owner direction: newer models draw complex SVG well, and minimal-by-default produced bare marks in testing | owner | 0.55 |
| Build in stages (silhouette, construction, detail), render each | A benchmark finds every model degrades as complexity rises [29] (abstract read); it does not test staging, so the stages are reasoned from it | owner + inference | 0.5 |
| Study admired marks (idea, construction, omissions, 16 px) and anti-references | Built from practice; no source tests it | inference | 0.5 to 0.55 |
| Study real products or label "from memory" | Test feedback; no source | inference | 0.6 |
| Diverge: 20 to 30 rough concepts before finished work | Thirty small thumbnails, a second sheet, then circle six [48]; sketch, set aside, then refine [49] | secondhand | 0.7 |
| Each concept: idea, brief line, why ownable; drop shape-only ideas | "Simple ideas, as well as simple designs are, ironically, the products of circuitous mental purposes" [51] | verified + inference | 0.75 |
| No gates during exploration; gates on the ship set | Early gates filter out the unusual ideas a concept needs; no study | inference | 0.75 |
| Geometric construction (equal divisions, polygons, circle packing); optical corrections recorded in words | [48] [50] | secondhand | 0.75 |
| Construction stated per concept as its own vocabulary, not one geometric formula for every kind | One formula would over-regularize lettering, character, and emblem marks; no source | inference | 0.6 |
| Detail budget stated per variant | Follows from complex marks being allowed and quality falling with complexity [29]; no source tests a budget | inference | 0.5 |
| No golden-ratio method | A designer said it was not used for a famous mark [50]; reviews mixed [61] [62] | secondhand | 0.6 |
| 4 to 8 finished variants, all shown | Owner direction; see disagreements | owner | 0.55 |
| Concept and execution judged in separate lines | A minimal mark can be well made and have no idea; that pairing reads as low effort | inference | 0.6 |
| Show on light, dark, and small size, same size, one view | Consistent practitioner advice, no study [32] | vendor | 0.5 |
| Iterate within the chosen approach, citing the brief | [14] | secondhand | 0.6 |
| SVG in code; generated sets drift in stroke and radius; the model cannot see its own render | [28] | vendor | 0.7 |
| Hand off to tokens; colors from the brief's outside reference, not from a one-color mark | No source maps a logo to tokens; color variants as sub-brands [20]; the outside-reference rule is test feedback | inference | 0.45 to 0.6 |
| Rank with reasons; the owner decides | Model judges fail to reach majority agreement with designer panels [59]; aesthetic judgment gaps [60]; experts found AI logo-maker layouts lacked proportion, balance, unity [78] | verified abstract / secondhand | 0.65 |
| Render and look; do not trust a visual self-correction loop | Iterative visual refinement often lowered compilation rates [57]; naive loops suboptimal [58] | verified / verified abstract | 0.6 to 0.65 |
| Log every drop in a separate drop log the report points to; flag off-brief variants | Test feedback | inference | 0.5 to 0.6 |
| Font licence must allow logo use | Licences differ on logo and embedding rights; no licence text read in this pass | inference | 0.7 |
| Image models give raster; tracing gives messy nodes; text misspelled | [28]; [30] unread; misspelling not sourced | vendor + inference | 0.5 to 0.6 |
| Clearance needs a person | [31] | verified | 0.85 |
| Default-mark questions (shield, check mark, pulse line, hexagon, letter in a rounded square, generic mountain) | Seen in agent test runs; no prevalence study | inference | 0.4 |

## Ship gates

| Gate | Basis | Label | Conf. |
|---|---|---|---|
| 16, 32, 64 px; one color; inverse; no gradients | [25] read; [26] [27] read as snippets only | verified / secondhand | 0.7 to 0.8 |
| Judge a real 16 px file at 4x nearest-neighbour zoom; define recognizable; wordmark minimum size or square partner, here and in the deliverables | Test feedback: "recognizable" was undefined and 16 px means nothing for a wordmark | inference | 0.6 |
| A separate small version for any mark | Simplified small version, no thin lines [68]; draw a tiny version if 16 px blurs [63]; do not scale illustrated art down [71] | verified | 0.8 |
| Silhouette; fill the outer contour of stroke marks | Convention | inference | 0.5 |
| Clear space as a multiple of an internal unit | [76]; one brand uses half the logo height [75] | secondhand / vendor | 0.7 |
| Optical overshoot of 1 to 2% | [25] [50] | secondhand | 0.7 |
| Vector check: `<path>`, not `<image>` | Four of five tools returned a raster inside an svg tag [56] | secondhand, one source | 0.6 |
| Expand strokes or state they are live | Test feedback; common delivery practice, no source read | inference | 0.5 |
| Node count reported, not a gate | Rule of thumb [25], no study | verified, rule of thumb | 0.4 |

## Deliverables (design/logo-deliverables.md)

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Lockups: horizontal, stacked, icon, wordmark; a version per container | [75]; [76] [52] | vendor / secondhand | 0.75 |
| Favicon set: ICO, SVG, 180 touch icon, manifest 192 and 512, maskable 512 | [63] | verified | 0.8 |
| ICO with 16, 32, 48 px | Research checklist; [63] ships 32 px only | inference | 0.6 |
| Dark favicon through an SVG media query | [64] | verified | 0.85 |
| The largest search engine does not list SVG; square, 48 px or more | [65] | verified | 0.9 |
| Maskable: central circle, 40% radius | [66] | verified | 0.9 |
| Touch icon opaque; transparency turns black | [67] | secondhand | 0.75 |
| iOS and macOS: one 1024 px square; system masks; appearances generated if not supplied; no baked effects | [68] [69] | verified | 0.85 to 0.9 |
| Android: 108 dp layers, 66 dp safe zone, monochrome layer; store 512 px PNG under 1024 KB | [70] [71] | verified | 0.85 to 0.9 |
| Windows: unplated assets; ICO with 16, 24, 32, 48, 256 | [72]; the ICO list was not confirmed on the page read | verified / secondhand | 0.85 / 0.6 |
| Avatar: mark in a central circle of about 80% | A circle crop removes 1 minus pi/4 of a square, about 21%: computed | inference | 0.7 |
| Share image 1200 by 630, alt text, 600 by 315 minimum | [73] [74] | verified | 0.85 |
| Present in context: tab, dock, home screen, app list, avatar, share card | Presets [75]; mockups [14] | vendor / secondhand | 0.5 to 0.6 |
| Use the host's visual tool, not a saved image | Owner direction; no outside source | owner | 0.7 |
| Deliver source files, not screenshots | "Don't screenshot or export the logo from a PDF/presentation for reuse" [75] | vendor | 0.8 |

## Mascot (design/mascot.md)

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Living character, usually supplementary; fit test ("probably isn't going to fit" an introverted company); full body and expression range sheet | [19]; [20]. The listed emotions and extra views are examples, not sourced | verified + inference | 0.65 to 0.8 |
| Expression without a face | [21] [22] | secondhand | 0.65 |
| Targets at least 24 CSS px; non-text 3:1 | WCAG 2.2 SC 2.5.8 [42] and 1.4.11 | verified | 0.9 to 0.95 |

## Where people disagree

- **Options shown.** One [14]; three, each fully built, "never one you would not ship" [13] [48]; 4 to 8 (owner). The research behind this revision recommends generating many and showing about three. Not followed: the skill keeps the owner's 4 to 8, all finished and ranked, and makes them comparable (one view, same size, differ in approach). Choice overload averages near zero across 50 experiments and appears when options are hard to compare [15].
- **Simplicity.** Simple helps for non-prestige products [54]; the simplest version hurts recognition [53]; descriptive beats abstract [55]. Resolved: the kind comes from the brief.
- **Complex marks.** Owner: newer models draw complex SVG well. Benchmark: quality falls with complexity [29]. Resolved: allowed, built in stages, each stage rendered (the stages are inference).
- **Golden ratio.** Taught as method; reviews find no special attraction [61] [62]. Dropped.
- **ICO sizes attribute.** `32x32` to stop one browser preferring the ICO over the SVG [63], or `any` [64]. Test in the browsers you support.
- **Touch icon.** 180 px is still used but absent from current platform docs [67]; padding on a solid ground [63] or full bleed (practice). Reconciled: opaque ground, mark inset.
- **macOS grid.** Square layers that the system masks [68], or a transparent PNG with an 824 px body and 100 px margin [77], a marketplace rule.
- **Identify or charm** for mascots: see [design.md](design.md).

## Gaps and corrections

- **Correction:** the simplicity study is Bossel, Geyskens and Goukens (2019) [54]. Earlier research notes cited it under Geyskens, who is the corresponding author, not the first.
- No controlled study of agent-made vs human-made logos. Abstracts only for [53] [54] [55] [59]; no effect sizes read.
- No study of the divergence count, stroke expansion, font licences for logos, or the default-mark list.
- Not researched: `theme-color` and manifest colors, macOS `.icns` sizes. The clear-space and minimum-size numbers are one brand's.
- Considered, not adopted: a leaning or off-centre mark to suggest motion (asymmetry examples [23] [24]; nothing on off-centre characters; 0.3). Padding for most brands.

## References

[48] https://addaly.com/learn/vector-and-print/sketching-and-narrowing · [49] https://www.creativebloq.com/features/paula-scher-logo-sketches · [50] https://addaly.com/learn/vector-and-print/construction-and-the-golden-ratio · [51] https://www.paulrand.design/writing/articles/1991-logos-flags-and-escutcheons.html · [52] https://www.nameclub.com/blog/how-many-logos-should-a-brand-have · [53] https://theses.ubn.ru.nl/items/62400e88-0142-4d50-8d4e-51f3eee8999a · [54] https://cris.maastrichtuniversity.nl/en/publications/facing-a-trend-of-brand-logo-simplicity-the-impact-of-brand-logo- · [55] https://www.thewhyweproject.com/studies/luffarelli-let-the-logo-do-the-talking-the-influence-of-logo-descriptiveness-on- · [56] https://paul.argoud.net/en/real-svg-fake-svg-recraft-v4-and-the-end-of-the-vector-designer/ · [57] https://arxiv.org/html/2608.28678 · [58] https://arxiv.org/html/2604.20730v2 · [59] https://arxiv.org/html/2605.20731v2 · [60] https://arxiv.org/html/2603.01083 · [61] https://journals.sagepub.com/doi/10.1068/p240937 · [62] https://doi.org/10.2190/qb14-nk7b-aryt-w5qt · [63] https://evilmartians.com/chronicles/how-to-favicon-in-2021-six-files-that-fit-most-needs · [64] https://web.dev/articles/building/an-adaptive-favicon · [65] https://developers.google.com/search/docs/appearance/favicon-in-search · [66] https://web.dev/articles/maskable-icon · [67] https://realfavicongenerator.net/blog/apple-touch-icon-is-180x180-pixels-but-is-that-still-true · [68] https://developer.apple.com/design/human-interface-guidelines/app-icons · [69] https://developer.apple.com/documentation/xcode/configuring-your-app-icon · [70] https://developer.android.com/develop/ui/compose/system/icon_design_adaptive · [71] https://developer.android.com/distribute/google-play/resources/icon-design-specifications · [72] https://learn.microsoft.com/en-us/windows/apps/design/iconography/app-icon-construction · [73] https://ogp.me/ · [74] https://developers.facebook.com/documentation/sharing/webmasters/images · [75] https://brand.pulumi.com/identity/logo/ · [76] https://addaly.com/learn/vector-and-print/lockups-clear-space-minimum-size · [77] https://macosicons.com/resources/how-to-get-approved · [78] http://designmarketinglab.com/archives/5691
