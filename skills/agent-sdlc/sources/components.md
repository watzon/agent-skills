# Sources: components

Evidence behind [design/components.md](../design/components.md). Labels and confidence as in [SOURCES.md](../SOURCES.md); numbers [42] and below are in [design.md](design.md), [49] and up are listed here. Research pass: 2026-11-16, one pass of 20 rules.

## Worked example

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Icon side gets less padding than label side | One design system tightened icon spacing in a toolbar button, PR text read, outcome not checked [57]; equal-padding-looks-wider explanation is inference | verified (text) + inference | 0.55 |
| Icon size follows the text style, one size per text size | One platform's symbols come in sizes relative to adjacent text [58]; that platform's guideline page did not load | secondhand | 0.6 |
| Icon-label gap is a token; no ratio exists | A third-party library's docs, describing its Material 3 button, give a 20 px icon, 8 px gap, 16 dp side padding [59]; not the official spec; no authority gives a ratio | secondhand, unofficial | 0.4 |
| Optical nudge for asymmetric glyphs | Center a triangle on its centroid [50]; a small rightward shift for play icons is common (demo only) | verified / secondhand | 0.8 |
| Icon-only buttons are square, equal padding | From design-system practice; one system's text-button padding read from a snippet [60] | inference | 0.6 |
| One declared scale, not an 8 px grid | No standard requires 8 px; one skill asks for "one declared scale" (secondhand) | secondhand + inference | 0.8 that 8 px is folklore |

## Computed checks

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Targets at least 24 by 24 CSS px, with spacing, inline, and essential exceptions | WCAG 2.5.8 AA [42] | verified | 0.95 |
| Grow the hit area with padding or a pseudo-element; no dead areas | [42]; [52] | verified | 0.85 |
| Nested radius = outer minus padding, floored at 0 | [53]; a course module on the topic was not readable | secondhand | 0.8 |
| Focus ring follows the radius; box-shadow ring; outline fallback for forced colors | [52]; one browser's outline followed the radius only from version 16.4; fallback is inference | verified + inference | 0.6 to 0.85 |
| Ring area 2 CSS px perimeter, 3:1 change | WCAG 2.4.13, AAA [55] | verified | 0.85 |
| Boundaries and meaningful icons 3:1; inactive exempt | WCAG 1.4.11 AA [56] | verified | 0.9 |
| Hover only under `(hover: hover)` | [52] | verified | 0.85 |
| No weight change across states | Causes layout shift [52] | verified | 0.8 |
| Loading keeps size; disable after submit | [52]; measure movement with layout-shift scoring [61] | verified / secondhand | 0.75 |
| `tabular-nums` for tables and timers | [52]; [62] | verified / secondhand | 0.9 |
| Inputs at least 16 px | One mobile browser zooms on focus below that [52] | verified | 0.85 |
| One icon set; one stroke width; the set's native grid | One icon set's design principles, rules 1 to 3 [49] | verified, vendor | 0.75 to 0.85 |

## Render checks

| Claim | Basis | Label | Conf. |
|---|---|---|---|
| Circle beside square: match area, snap to pixels | Area and convex-hull formulas [50] | verified | 0.6 |
| `text-box: trim-both cap alphabetic` centers button labels; not for prose | [51]; Baseline status from a docs snippet [63] | verified / secondhand | 0.75 |
| Stroke weight matches text weight | Mixed strokes called wrong [49]; one platform's symbols have weights matched to text [58] | verified / secondhand | 0.75 |
| Loop: 2x render, crop, adjust one value, re-render, confirm at 1x | Check order from the research pass; loop steps are inference | inference | 0.6 |

## Where people disagree

- **Touch target size.** 24 CSS px (WCAG AA) [42]; 44 pt (Apple) and 48 dp (Android), both secondhand: the Apple guideline page returned empty and the Android figure is from a snippet. The skill uses 24 px as the floor and points touch products at the platform guideline. Conf. 0.8.
- **Focus ring method.** Box-shadow [52] vs outline (older guidance; outlines now follow radius in current browsers). The skill states the outcome (ring follows the radius, survives forced colors) and names box-shadow as the portable way. Conf. 0.6.
- **Optical method.** Compute area, centroid, or convex hull [50] vs balance by eye [49]. Both reject the bounding-box center. The skill computes first, then checks by eye. Conf. 0.7.
- **Gap direction.** The owner's example says tighter; the one sourced example (8 px at a 20 px icon [59]) is tight but sets no ratio. Both fit "gap is a token, chosen by render". Conf. 0.5.

## Gaps

- Apple guideline pages for symbols, layout, and accessibility returned empty: Apple icon sizes and the 44 pt target are secondhand and unverified.
- Material's current button and icon-button specs returned empty: its icon sizes and the 48 dp target come from a third-party mirror or a snippet. Re-check at the official site before citing a number. Material's radius steps are a system, not a rule (secondhand).
- Not read in full: a nested-radius course module, a practitioner's button guidance (fetch failed; summary also failed), one design system's icon-button page, a layout book.
- No source gives an icon-to-cap-height ratio, an icon-label gap, a better-tested shadow recipe, or a rule for borders versus shadows. These stay taste with a reason.
- No controlled study compares any of these rules with user outcomes.
- Left out of the rule file as low confidence or taste: press scale and duration, layered shadows [54], label position, empty-state wording, truncation, disabled-button tooltips.

## References

[49] https://lucide.dev/contribute/icons/design-principles · [50] https://bjango.com/articles/opticaladjustments/ · [51] https://developer.chrome.com/docs/modern-web-guidance/guides/visual-design/precise-text-alignment · [52] https://interfaces.rauno.me/ · [53] https://www.30secondsofcode.org/css/s/nested-border-radius/ · [54] https://tobiasahlin.com/blog/layered-smooth-box-shadows/ · [55] https://www.w3.org/WAI/WCAG22/Understanding/focus-appearance.html · [56] https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast · [57] https://github.com/Shopify/polaris-react-archive/pull/11985 · [58] https://mckinleysymbols.com/docs/concepts/multiple-weights.html · [59] https://github.com/gersilva96/react-material-expressive/blob/main/docs/components/Button.md (third-party library docs found on re-check; the research pass did not keep its URL, so this may not be the page it read) · [60] https://www.primer.style/product/components/button/ (returned no content; snippet only) · [61] https://web.dev/articles/optimize-cls · [62] https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/font-variant-numeric · [63] https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/text-box-trim
