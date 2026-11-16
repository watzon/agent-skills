# Design foundations

Read when a product has no design system and you are setting its values, after the [brand brief](brand.md) and the [logo](logo.md). Each topic has a floor (checkable, from a standard or research) and judgment above it that the brand chooses. Floors are not negotiable; judgment needs a reason in the brief.

## Name the product type first

The same brand sets different values for different kinds of product. These are starting points (inference); the brief overrides them with reasons.

| | Dense tool | Marketing | Editorial |
|---|---|---|---|
| Density | High; many items per view | Medium; a few claims per section | Low to medium; long reading |
| Measure | Short UI strings; less critical | Lead text 60 to 75 characters | 60 to 75 characters |
| Body size | Small UI labels allowed; no source sets their minimum | From the brand, at least 16 px | 18 to 20 px |
| Radius | Small and consistent | From the brand | From the brand; often 0 |
| Images | Functional icons | Informative product or people images | Captioned, informative |
| Video | Only if it teaches a task | Only if a demo needs motion | Only where stills fail |
| Motion | Feedback under 150 ms; no entrances | One entrance at most | Page transitions only |

## Floor and judgment by topic

| Topic | Floor (check it) | Judgment (the brand chooses, with a reason) |
|---|---|---|
| Color | Normal text 4.5:1, large text 3:1 ([floor-checks.md](floor-checks.md)) | 4 to 6 roles (ground, surface, text, muted, border, status) plus one accent, taken from the logo |
| Typography | Prose body never below 16 px on the web; reading-heavy products often use 18 to 20 px | One or two families with roles and a fallback stack; a type scale with a named ratio and 5 to 7 steps. No rule exists for pairing; write why |
| Line height | Prose at least 1.5 | Heading leading |
| Measure | Prose under about 80 characters per line, as in [floor-checks.md](floor-checks.md); target 60 to 75; below about 45 reads choppy. Measure the rendered text: a `ch` unit is the width of "0", not an average letter | Where the column sits on the page |
| Spacing | Every value comes from one declared scale; no off-scale values. Touch targets at least 24 by 24 CSS px; mobile platform guidelines ask for more (see sources) | Which steps (5 to 7); derive from line height and target size, not a habit grid |
| Radii | 2 to 4 declared steps; a nested radius is the outer radius minus the padding | Sharp or round, from the logo's shape language |
| Text density | None measured | A stated target per view with a reason: people scan, and long blocks get skipped |
| Imagery | Alt text; no invented people, quotes, or numbers | Each image carries information or is removed. How many, what kind, what treatment |
| Video | No autoplay with sound; auto-starting motion longer than about 5 s can be paused (from the accessibility standard; unverified, see sources) | Video only where motion teaches what a still cannot; poster image otherwise |
| Motion | UI motion 100 to 500 ms; feedback about 100 ms; exit shorter than entry; honor reduced motion; content visible at rest | Which motion expresses the brand. Motion follows a user action or state change. Scroll entrances are opt-in. No parallax, scroll-jacking, or auto-advancing carousels |

## Defaults agents pick without thinking

Each one is a finding unless the brief chose it with a reason.

| Topic | Default | Fix |
|---|---|---|
| Type | The default neutral sans at 16 px | Choose from the brand; check size floor and measure |
| Spacing | An 8 px grid, used loosely | One declared scale from line height and target size |
| Radius | 8 or 16 px on everything; side-stripe cards | Radius from the logo; nested = outer minus padding |
| Measure | Full-width text | `max-width` on prose; check the rendered width |
| Density | Hero, three icon cards, six two-line sections | Count sections against the job |
| Images | Stock hero; decorative photos | Informative images only |
| Video | Autoplaying loop in the hero | Poster image unless motion teaches |
| Motion | Fade-up on every section; hover lift on every card | One purposeful motion or none |

## Tokens

- **Two layers.** Primitives hold raw values; semantic tokens name roles (`text-body`, `surface-muted`). Components use roles only.
- **Few.** 4 to 6 color roles plus one accent; one or two families; 5 to 7 type steps; 5 to 7 space steps; 2 to 4 radii; 2 durations; 1 or 2 easings. Add a step only with a reason. These counts are a proposal, not a finding.
- **Format.** If the project stores tokens as files, the design tokens JSON format (each token has `$value`, `$type`, optional `$description`; aliases as `{group.token}`) is a W3C Community Group report, not a W3C Standard. Use it if tools need interchange; it is not required.
- **Names carry the reason** into code, so a later change can see what the value is for.

## Design brief

Extend the [brand brief](brand.md) with one section:

1. Product type: dense tool, marketing, or editorial.
2. Per topic above: the value, the reason tied to the brand and product type, and the floor it must pass.
3. Rejected options, one line each.
4. What would change the call.

## Done when

- [ ] The product type is named.
- [ ] Every topic has a value or is marked not used, each with a reason.
- [ ] Every floor in the table passes, with the check output kept.
- [ ] Every value in code comes from a declared token; none is off-scale.
- [ ] Each default in the defaults table was either avoided or chosen with a reason.
