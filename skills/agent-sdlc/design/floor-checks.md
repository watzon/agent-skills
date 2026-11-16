# Floor checks

Read before handing off any UI change, and when reviewing one. These checks have an outside anchor (a standard or a render), so they apply to every design, whatever its style.

## Checks

1. **Contrast.** Normal text at least 4.5:1 against its background; large text at least 3:1 (WCAG 2.2 AA, 1.4.3). Control boundaries and meaningful icons at least 3:1 against adjacent colors (1.4.11). Check with an automated tool, not by eye, in every theme.
2. **Visible by default.** Content shows with no script or animation running. An entrance animation may start from visible, never from hidden, so a failed animation leaves content readable.
3. **Desktop and phone renders.** Screenshot every changed view at a desktop width and a phone width. Fail on horizontal overflow, overlapping elements, clipped text, or a blank area where content belongs.
4. **Focus.** Every interactive element shows a visible focus state.
5. **Reduced motion.** When the user asks for reduced motion, non-essential motion stops.
6. **Readable body text.** Body lines stay under about 80 characters. No all-caps body text.
7. **No invented content.** No made-up numbers, testimonials, customer logos, ratings, or case-study counts. Placeholder copy is marked as such and gone before handoff ([anti-slop/product.md](../anti-slop/product.md)).
8. **Target size.** Every clickable target at least 24 by 24 CSS px, or spaced so a 24 px circle centered on it touches no other target (WCAG 2.2 AA, 2.5.8). Component checks: [components.md](components.md).
9. **Banned lists are dated.** Any list of default looks to avoid carries the date it was last reviewed and is reviewed at each model release. Use it as questions (below), never as a hex or font ban.

## Default-look questions

Last reviewed 2026-11-16. Review at each model release; the defaults move with each model and year. Each "no" is a finding unless the design system or brief asks for it.

- Does the eyebrow or tracked all-caps label above this heading carry information?
- Does the numbering (01, 02, 03) encode a real sequence?
- Does the colored side stripe on this card encode a status?
- Does the gradient text, glow, or blurred shape behind content serve the subject?
- Do the palette and typefaces trace to the subject, or are they what any similar page would get?
- Does every section need its own entrance animation, and every card a hover effect?
- Are cards nested inside cards?

## Done when

- [ ] Automated contrast output is in the handoff, for every theme.
- [ ] Desktop and phone screenshots exist for every changed view, with no overflow or overlap.
- [ ] Focus, reduced-motion, and target-size checks were done.
- [ ] No invented content ships.
- [ ] Each default-look question was answered for each changed view.
