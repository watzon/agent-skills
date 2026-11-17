# Design foundations

Read when a product has no design system and you are setting its values, after the [brand brief](brand.md) and the [logo](logo.md). Each topic has up to three layers. A **floor** comes from an accessibility standard or from [floor-checks.md](floor-checks.md) and is not negotiable. A **house default** is a starting value from research guidance or inference; the brief may change it with a reason. **Judgment** is what the brand chooses, with a reason in the brief.

## Name the product type first

The same brand sets different values for different kinds of product. These are starting points (inference); the brief overrides them with reasons.

| | Dense tool | Marketing | Editorial |
|---|---|---|---|
| Density | High; many items per view | Medium; a few claims per section | Low to medium; long reading |
| Measure | Short UI strings; less critical | Lead text 60 to 75 characters | 60 to 75 characters |
| Body size | Small UI labels allowed; no source sets their minimum | From the brand; 16 px default | 18 to 20 px |
| Radius | Small and consistent | From the brand | From the brand; often 0 |
| Images | Functional icons | Informative product or people images | Captioned, informative |
| Video | Only if it teaches a task | Only if a demo needs motion | Only where stills fail |
| Motion | Feedback under 150 ms; no entrances | One entrance at most | Page transitions only |

## Floor, default, and judgment by topic

| Topic | Floor (a standard; check it) | House default (change with a reason) | Judgment (the brand chooses) |
|---|---|---|---|
| Color | Normal text 4.5:1, large text 3:1; boundaries and meaningful icons 3:1 ([floor-checks.md](floor-checks.md)) | 4 to 6 roles (ground, surface, text, muted, border, status) plus one accent (inference) | Which colors: from the brief's outside reference, checked against the logo |
| Typography | None | Prose body 16 px on the web; reading-heavy products 18 to 20 px (secondhand, 0.6) | One or two families with roles and a fallback stack; a type scale with a named ratio. No rule exists for pairing; write why |
| Line height | Prose at least 1.5 (WCAG 1.4.8, AAA) | None | Heading leading |
| Measure | Prose under about 80 characters per line (WCAG 1.4.8, AAA) | Target 60 to 75; below about 45 reads choppy (practitioner sources). Measure the rendered text: a `ch` unit is the width of "0", not an average letter | Where the column sits on the page |
| Spacing | Targets at least 24 by 24 CSS px (WCAG 2.5.8, AA); mobile platform guidelines ask for more (see sources) | One declared scale of 5 to 7 steps, no off-scale values (inference) | Which steps; derive from line height and target size, not a habit grid |
| Radii | None | 2 to 4 declared steps (inference); a nested radius is the outer radius minus the padding (secondhand geometry) | Sharp or round, from the logo's shape language |
| Text density | None | None measured | A stated target per view with a reason: people scan, and long blocks get skipped |
| Imagery | Alt text (WCAG 1.1.1); no invented people, quotes, or numbers ([floor-checks.md](floor-checks.md)) | None | Each image carries information or is removed. How many, what kind, what treatment |
| Video | No autoplay with sound; auto-starting motion longer than about 5 s can be paused (WCAG 1.4.2 and 2.2.2, cited unverified) | Poster image unless motion teaches (inference) | Video only where motion teaches what a still cannot |
| Motion | Honor reduced motion; content visible at rest ([floor-checks.md](floor-checks.md)) | UI motion 100 to 500 ms; feedback about 100 ms; exit shorter than entry. No parallax, scroll-jacking, or auto-advancing carousels (research guidance). Scroll entrances opt-in (inference) | Which motion expresses the brand. Motion follows a user action or state change |

## Habits agents fall into

Each one is a finding unless the brief chose it with a reason.

| Topic | Habit | Fix |
|---|---|---|
| Type | The default neutral sans at 16 px | Choose from the brand; check size and measure |
| Spacing | An 8 px grid, used loosely | One declared scale from line height and target size |
| Radius | 8 or 16 px on everything; side-stripe cards | Radius from the logo; nested = outer minus padding |
| Measure | Full-width text | `max-width` on prose; check the rendered width |
| Density | Hero, three icon cards, six two-line sections | Count sections against the job |
| Images | Stock hero; decorative photos | Informative images only |
| Video | Autoplaying loop in the hero | Poster image unless motion teaches |
| Motion | Fade-up on every section; hover lift on every card | One purposeful motion or none |

## Tokens

- **Two layers.** Primitives hold raw values; semantic tokens name roles (`text-body`, `surface-muted`). Components use roles only.
- **Few.** 4 to 6 color roles plus one accent; one or two families; 5 to 7 type steps; 5 to 7 space steps; 2 to 4 radii; 2 durations; 1 or 2 easings. These counts are house defaults (inference, no source sets a count); change one with a reason.
- **Format.** If the project stores tokens as files, the design tokens JSON format (each token has `$value`, `$type`, optional `$description`; aliases as `{group.token}`) is a W3C Community Group report, not a W3C Standard. Use it if tools need interchange; it is not required.
- **Names carry the reason** into code, so a later change can see what the value is for.

## Design brief

Extend the [brand brief](brand.md) with one section:

1. Product type: dense tool, marketing, or editorial.
2. Per topic above: the value, the reason tied to the brand and product type, the floor it must pass, and any house default it changes and why.
3. Rejected options, one line each.
4. What would change the call.

## Done when

- [ ] The product type is named.
- [ ] Every topic has a value or is marked not used, each with a reason.
- [ ] Every floor in the table passes, with the check output kept.
- [ ] Each house default is kept, or changed with a reason in the brief.
- [ ] Every value in code comes from a declared token, or the brief says why not.
- [ ] Each habit in the habits table was either avoided or chosen with a reason.
