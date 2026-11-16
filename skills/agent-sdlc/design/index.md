# Design process

Read when building or changing UI, or setting a brand, as designer or implementer. Generic design is the model's unchosen default: with no direction, output drifts to the most typical look, and a ban list only moves it to the next default. What helps is a process that derives each choice from the subject and records why.

Copywriting beyond [anti-slop/copy.md](../anti-slop/copy.md) is out of scope here.

## Size it first

- **Small visual fix:** skip to step 5. One contrast check, one state check, one screenshot.
- **New product with no design system:** run every step. Brand comes first, then the logo and any mascot in the order the brief sets, then foundations.
- **New surface in a product that has a system:** step 1, then step 4 for layout.
- **Brand only:** steps 2 and 3.1, then the report. Stop there: no logo, mascot, foundations, or layouts unless asked.
- **Logo:** steps 2 and 3.1 to 3.3 (keep an existing brief; write one if none exists), then the [logo deliverables](logo-deliverables.md) and the report. No foundations, layouts, or page screenshots unless asked.

## Steps

1. **Existing design system? Follow it and stop designing.** If tokens, a style guide, a component library, or a design file exist, use them. Do not invent new colors, fonts, or spacing. Go to step 4 if a new layout is needed, else step 5.
2. **Get the purpose.** Purpose, audience, primary job, and the one action. If the purpose is open, propose it in one line and continue; ask one question only if the answer changes the work. A new brand also needs a name first ([brand.md](brand.md)).
3. **Build the identity, in order.** Each step reads the one before it.
   1. Brand brief ([brand.md](brand.md)).
   2. Logo and full scopes only: decide the logo and mascot relationship from the brief ([logo.md](logo.md)): logo first, character first, one asset, or no mascot.
   3. Logo and full scopes only: make them in that order: the logo, from a wide set of rough concepts down to 4 to 8 finished variants the owner picks from ([logo.md](logo.md)); the mascot, if any ([mascot.md](mascot.md)).
   4. Foundations: color, type, spacing, radii, measure, density, imagery, video, motion, tokens ([foundations.md](foundations.md)).
4. **Directions, where a surface still needs them.** For a new page or screen whose layout the system does not settle:
   1. Write the content hierarchy with real copy before any visual choice.
   2. Draft 3 to 5 layout directions (a house default count). Draw each from the subject's materials, trade, and vernacular, not from other websites. Any two differ on at least two of layout, type use, color use, and density. Describe each with specific words; style words such as "modern", "clean", or "premium" pull toward the default.
   3. Choose one and log the rejects in the drop log, one line each, with the reason tied to the audience and job. Compare the choice with the generic default you would produce for any similar page; revise where they match. Where the brief pins a choice, the brief wins; take risks only on what it leaves open.

   Variety comes from the subject and this forced comparison, never from random seeds or dealt directions.
5. **Check the floor** ([floor-checks.md](floor-checks.md)). Any failure stops the work until fixed. For buttons, inputs, and icons, run [components.md](components.md) too.
6. **Build, then screenshot** at desktop and phone width. Compare with the brief, not with taste.
7. **Report** in the format below.

## Use lists as questions

A list of known default looks is useful as questions, not bans: "Does this numbering encode a sequence?" lasts longer than "no numbered markers". The lists go stale with each model release ([floor-checks.md](floor-checks.md)).

## Drop log

Keep every rejected option in one file in the work folder, `drops.md` unless the project names another: one line each with what was dropped, at which step, and why it lost. The report points to it instead of repeating it.

## Design report

The code report in [handoff/index.md](../handoff/index.md) does not fit design work. Report instead, in about 12 lines:

1. **Outcome:** done, partial, or blocked, and which scope (fix, surface, brand only, logo, full).
2. **Where:** the view in the host's visual tool, and the paths of the source files.
3. **Decisions** with their reasons, each tied to a brief line.
4. **Options shown,** ranked with reasons; the owner's choice, or that it is pending.
5. **Drops:** the path to the drop log and its count; name only a drop the owner may want back.
6. **Checks:** the gates or floor checks run, with their evidence (renders, contrast output).
7. **Not verified:** trademark, font licence, platform previews, anything else.
8. **Decisions needed** from the owner, and what would change the call.

## Done when

Check the items that apply to the scope.

- [ ] An existing system was followed, or the brand brief exists.
- [ ] Brand only: no logo, mascot, foundations, or layout work was added.
- [ ] Logo: the written logo and mascot decision, the chosen logo, and the deliverables set exist; no layout or foundations work was added.
- [ ] Full: the logo items above, plus foundations, with every color, typeface, and spacing value traced to the brief or the system.
- [ ] Every new surface layout had 3 to 5 directions drafted and the rejects in the drop log.
- [ ] UI work: floor checks pass, with screenshots at both widths.
- [ ] The report follows the design report format.
