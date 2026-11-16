# Components

Read when building, changing, or reviewing a button, input, icon, or other control. Most component mistakes are measurable: check computed values first, then render the component and look for the rest. Values come from the project's tokens ([foundations.md](foundations.md)); this file says how to check them.

## Worked example: an icon in a button

An icon beside a label needs less space around it than the text does. The icon's box holds empty space around the ink, so equal padding reads wider on the icon side (inference). Four fixes, tried in this order:

1. **Less padding on the icon side** than on the label side.
2. **A smaller icon**, sized from the label's text style, not by guess.
3. **A tighter gap** between icon and label, from a gap token.
4. **An optical nudge** when the glyph is asymmetric: a play triangle, a chevron, an arrow.

No authority gives a number for fixes 1 to 3: no icon-to-text ratio, no gap value, no padding ratio. Make each a token, choose its value with the render loop below, and record the reason. The nudge has the best support of the four: compute it, then check it by eye. An icon-only button is square, with equal padding on every side (inference).

The same holds for spacing in general: one declared scale, not a fixed 8 px grid. The 8 px grid is a habit, not a standard.

## 1. Check computed values

Read each value from the CSS or the DOM, in every state the component has (default, hover, focus, active, selected, disabled, loading).

| Rule | Check | Fails when |
|---|---|---|
| Hit area | Bounding box of the clickable element, or a 24 px circle centered on it | Under 24 by 24 CSS px and the circle touches another target. Touch products: mobile platform guidelines ask for more (see sources). Grow the hit area with padding or a pseudo-element, not a bigger icon |
| Nested radius | Inner radius = outer radius minus the padding between them, floored at 0 | The inner radius equals or exceeds the outer one on a padded child |
| Focus ring | Ring shape against the control's radius; forced-colors mode on | The ring is square on a rounded control, or vanishes in forced-colors mode. A box-shadow ring follows the radius everywhere; keep an outline fallback for forced colors |
| Focus ring strength | Ring area and its contrast against the unfocused state | Below a 2 CSS px perimeter or under 3:1 (the stricter AAA level; apply when the project targets it) |
| Non-text contrast | Control boundary and meaningful icon against adjacent colors | Under 3:1. Inactive controls are exempt. Text contrast is in [floor-checks.md](floor-checks.md) |
| Hover | Every `:hover` rule | A hover style outside `@media (hover: hover)`; touch screens show it on press |
| Weight across states | Computed `font-weight` and width per state | Weight or width changes on hover or selected |
| Layout shift | Bounding box per state, before and after submit | Size changes when loading. Swap the icon for a spinner or reserve the label width; disable after submit |
| Numbers | `font-variant-numeric` on tables, timers, counters, prices in columns | Not `tabular-nums`, so digits jitter or misalign |
| Input text | Computed `font-size` of text inputs | Under 16 px; some mobile browsers zoom the page on focus |
| Icon set | Icon imports; `stroke-width` across icons in a view | More than one icon set, or mixed stroke widths at the same size |

## 2. Render and look

These have no computed answer. Use the loop for each.

- **Optical offset for asymmetric glyphs.** A play triangle, chevron, or arrow at its box center looks off-center. Center the triangle on its centroid, not its box; for others, compute what you can, then adjust by eye. Store the offset as a named value with the reason.
- **Round beside square.** A circle as wide as a square looks smaller. Scale it to match the square's area, snap to whole pixels, then look.
- **Button text centering.** Font metrics add space above and below the letters, so a label centered by box sits low. On the label, `text-box: trim-both cap alphabetic`, with the button as `inline-flex` and `align-items: center`. Check the browsers you support; where unsupported the property is ignored, so look at that render too. Never on prose.
- **Icon and label proportions.** One icon size per text size, set as a token. The icon should read as the same visual weight as the label's letters; no source gives a ratio.
- **Stroke weight matches text weight.** A bold label needs a heavier stroke than a regular one. Keep one stroke width per icon size within a view.

### The loop

The loop's steps are inference; the checks it runs are sourced.

1. Render the component at 2x device scale, in every state and every theme.
2. Crop to the component with a small margin, icon and label in one crop.
3. Look for: unequal visual padding, an off-center glyph or label, an icon heavier or lighter than the text, a gap that reads wider than the padding.
4. Change one token or offset at a time.
5. Re-render and compare with the previous crop side by side. Repeat until a fresh look finds nothing, then confirm at 1x.

Keep the final crops for the handoff.

## Done when

- [ ] Every row in section 1 was read from computed values in every state, with the output kept.
- [ ] Every target is at least 24 by 24 CSS px or passes the spacing test.
- [ ] Icon size, icon-label gap, and icon-side padding are tokens with a recorded reason.
- [ ] Each section 2 item that applies went through the loop; the final 2x crops are in the handoff.
- [ ] Each optical offset is a named value with its reason.
