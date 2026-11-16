# Design process

Read when building or changing UI, or setting a brand, as designer or implementer. Generic design is the model's unchosen default: with no direction, output drifts to the most typical look, and a ban list only moves it to the next default. What helps is a process that derives each choice from the subject and records why.

Copywriting beyond [anti-slop/copy.md](../anti-slop/copy.md) is out of scope here.

## Size it first

- **Small visual fix:** skip to step 5. One contrast check, one state check, one screenshot.
- **New product with no design system:** run every step. Brand comes first, then the logo and any mascot in the order the brief sets, then foundations.
- **New surface in a product that has a system:** step 1, then step 4 for layout.

## Steps

1. **Existing design system? Follow it and stop designing.** If tokens, a style guide, a component library, or a design file exist, use them. Do not invent new colors, fonts, or spacing. Go to step 4 if a new layout is needed, else step 5.
2. **Get the purpose and the name.** Purpose, audience, primary job, and the one action. If the purpose is open, propose it in one line and continue; ask one question only if the answer changes the work. Get a project name before visual work: the name shapes the brand and the logo. A working name is fine; note that a rename redoes the logo.
3. **Build the identity, in order.** Each step reads the one before it.
   1. Brand brief ([brand.md](brand.md)).
   2. Decide the logo and mascot relationship from the brief ([logo.md](logo.md)): logo first, character first, one asset, or no mascot.
   3. Make them in that order: the logo as 4 to 8 variations the owner picks from ([logo.md](logo.md)); the mascot, if any ([mascot.md](mascot.md)).
   4. Foundations: color, type, spacing, radii, measure, density, imagery, video, motion, tokens ([foundations.md](foundations.md)).
4. **Directions, where a surface still needs them.** For a new page or screen whose layout the system does not settle:
   1. Write the content hierarchy with real copy before any visual choice.
   2. Draft 3 to 5 layout directions (a house default count). Draw each from the subject's materials, trade, and vernacular, not from other websites. Any two differ on at least two of layout, type use, color use, and density. Describe each with specific words; style words such as "modern", "clean", or "premium" pull toward the default.
   3. Choose one and log the rejects, one line each, with the reason tied to the audience and job. Compare the choice with the generic default you would produce for any similar page; revise where they match. Where the brief pins a choice, the brief wins; take risks only on what it leaves open.

   Variety comes from the subject and this forced comparison, never from random seeds or dealt directions.
5. **Check the floor** ([floor-checks.md](floor-checks.md)). Any failure stops the work until fixed. For buttons, inputs, and icons, run [components.md](components.md) too.
6. **Build, then screenshot** at desktop and phone width. Compare with the brief, not with taste.
7. **Report:** the decisions, their reasons, the rejects and why, and what would change the call.

## Use lists as questions

A list of known default looks is useful as questions, not bans: "Does this numbering encode a sequence?" lasts longer than "no numbered markers". The lists go stale with each model release ([floor-checks.md](floor-checks.md)).

## Done when

- [ ] An existing system was followed, or steps 2 and 3 produced a brand brief, a written logo and mascot decision, a chosen logo, and foundations.
- [ ] Every new surface layout had 3 to 5 directions drafted and the rejects logged with reasons.
- [ ] Every color, typeface, and spacing value traces to the brief or the system.
- [ ] Floor checks pass, with screenshots at both widths.
- [ ] The report names the decisions, reasons, rejects, and what would change them.
