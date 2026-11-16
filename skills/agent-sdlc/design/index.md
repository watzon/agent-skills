# Design process

Read when building or changing UI, as designer or implementer. Generic design is the model's unchosen default: with no direction, output drifts to the most typical look, and a ban list only moves it to the next default. What helps is a process that derives each choice from the subject and records why.

## Size it first

- **Small visual fix:** skip to step 7. One contrast check, one state check, one screenshot.
- **New surface or product with no design system:** run every step and write a one-page brief.

## Steps

1. **Existing design system? Follow it and stop designing.** If tokens, a style guide, a component library, or a design file exist, use them. Do not invent new colors, fonts, or spacing. Go to step 7.
2. **Name the subject, audience, primary job, and the one action.** If the brief leaves them open, propose them in one line and continue. Ask only if the answer changes the build.
3. **Write the content hierarchy** with real copy, before any visual choice. Copy is design; follow [anti-slop/copy.md](../anti-slop/copy.md).
4. **Draft 3 to 5 directions.** Draw each from the subject's materials, trade, and vernacular, not from other websites. Each direction gives named color roles, a type pairing with a reason, a layout sketch, a density, and one sentence on fit. Any two directions differ on at least two of layout, type, color, and density. Describe a direction with specific words and references; style words such as "modern", "clean", or "premium" pull toward the default.
5. **Choose one and log the rejects.** Write the reason, tied to the audience and job. For each rejected direction, one line on why. Then compare the choice with the generic default you would produce for any similar page; revise where they match. Where the brief pins a choice, the brief wins; take risks only on what it leaves open.
6. **Build the identity and foundations,** in this order, each traced to the chosen direction:
   1. Brand: personality and voice from the product's purpose and name ([brand.md](brand.md)).
   2. Logo ([brand.md](brand.md)).
   3. Mascot, only if the brand calls for one ([brand.md](brand.md)).
   4. Color by role: ground, text, accent, status ([foundations.md](foundations.md)).
   5. Typography: one or two families with roles and a fallback stack, one type scale with its ratio ([foundations.md](foundations.md)).
   6. Spacing: one scale ([foundations.md](foundations.md)).
   7. Radii and shadows, only where they mean something ([foundations.md](foundations.md)).
   8. Line height and measure ([foundations.md](foundations.md)).
   9. Text density, set by the job ([foundations.md](foundations.md)).
   10. Imagery, then video ([foundations.md](foundations.md)).
   11. Motion: one orchestrated entrance at most; other motion answers a user action ([foundations.md](foundations.md)).

   Name tokens so the reason carries into code.
7. **Check the floor** ([floor-checks.md](floor-checks.md)). Any failure stops the work until fixed.
8. **Build, then screenshot** at desktop and phone width. Compare with the brief, not with taste.
9. **Report:** the direction, its reasons, the rejects and why, and what would change the call.

## Use lists as questions

A list of known default looks is useful as questions, not bans: "Does this numbering encode a sequence?" lasts longer than "no numbered markers". The lists go stale with each model release ([floor-checks.md](floor-checks.md)).

## Done when

- [ ] An existing system was followed, or steps 2 to 6 produced a written brief.
- [ ] At least three directions were drafted and the rejects logged with reasons (new surfaces only).
- [ ] Every color, typeface, and spacing value traces to the direction or the system.
- [ ] Floor checks pass, with screenshots at both widths.
- [ ] The report names the direction, reasons, rejects, and what would change it.
