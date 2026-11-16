# Logo

Read when making or changing a logo, after the [brand brief](brand.md) exists. The brief is the reference: every variant and every change is checked against it.

## Logo and mascot: decide per brand

Neither comes first by rule. Some brands grew the logo out of an existing character; others drew the character from the logo's shapes. Decide from the brief:

- **Character first** when a character already has equity, or the personality is outgoing and the character is the brand's main way to speak. Then the logo is the character, or a simplified head or silhouette of it.
- **Logo first** in most new brands. A mascot, if any, comes later and borrows the logo's proportions and colors ([mascot.md](mascot.md)).

## Choose the kind of mark

| Kind | Fits when | Watch for |
|---|---|---|
| Wordmark | The name is short and distinctive, or cannot be drawn; reserved or technical personality | Generic type makes a generic brand; set it deliberately |
| Symbol or monogram | The product has a clear reference point, or needs an app icon | Must survive 16 px and one color |
| Combination | A new name that needs to be learned alongside a symbol | Each part must also work alone |
| Personality-led or character | Outgoing, playful, consumer brands; the brief says so | Detail dies at small size; plan a simplified version |

No study compares minimal marks with character marks on outcomes; this table is judgment. One possible option among the variants is a character or mark that leans or sits off-centre to suggest motion. Treat it as one idea to try, not a rule: the evidence for it is unverified.

## Make 4 to 8 variations

1. Make 4 to 8 variants. They differ in **approach** (kind of mark, concept, construction), not in color or small tweaks.
2. Write one line of reasoning for each, tied to a line of the brief.
3. Run the quality tests below on each before showing it. Drop or fix any that fail.
4. Present all of them at the same size in one grid, on a light and a dark ground, plus a row at small size (32 and 16 px).
5. The owner picks one, or asks for another round.
6. Iterate within the chosen approach. Each change cites the brief. Or accept it as is.
7. Log the rejected variants, one line each.

## How to make a logo as an agent

- **Draw it as SVG in code.** Real vector paths, simple geometry. Models handle simple icons and break on complex layered marks.
- **Render it and look.** You cannot see an SVG by reading its text. Render each variant to PNG at the test sizes, view the image, fix, render again. No variant is shown unseen.
- **Keep a set consistent.** Declare one stroke width and one corner radius for the set and check every path against them; generated sets drift.
- **Text:** use a real font and convert the letters to outlines in the final SVG. Check spelling letter by letter in the render.
- **Image models give pixels.** Their output is raster and often misspells text. Use it only as a sketch, then redraw it as clean paths; automatic tracing gives hundreds of messy nodes.
- **Trademark clearance needs a person.** Generators can reproduce marks they were trained on. A search or similarity check by the agent is not clearance; flag the chosen mark for human or legal review before public use.

## Quality tests

Run on every variant before showing it, and again on the final.

| Test | Pass when |
|---|---|
| Small size | Exported at 64, 32, and 16 px, it is still recognizable |
| One color | Solid black on white reads |
| Inverse | Solid white on black reads |
| No gradients | It works with no gradient, shadow, or transparency |
| Silhouette | Filled solid, the outline still identifies it |
| Clear space | A stated minimum clear space around it; nothing intrudes in mockups |
| Simplicity | Roughly under 50 nodes; well over 150 is an illustration, not a mark (rule of thumb) |
| Optical | Round shapes overshoot slightly so they look the same size as flat ones; judge at 100% and 16 px |

## Deliver

SVG master with outlined text; PNG at 1024, 512, 256, 64, 32, 16 px; one-color and inverse versions; minimum size and clear space written down.

## Hand off into tokens

No source maps a logo to design tokens; this is inference. Carry forward to [foundations.md](foundations.md):

- **Color:** the mark already works in one color, so color is a choice. Take 2 to 4 colors from it and give each a role.
- **Type:** pick families that match the mark's construction and the brief's words; record why.
- **Shape language:** corner radius, stroke weight, and curve from the mark set the UI's radii, icon stroke, and border weight.

## Done when

- [ ] The logo and mascot relationship was decided from the brief and written down.
- [ ] 4 to 8 variants differing in approach were rendered, viewed, and shown in one grid on light, dark, and at small size, each with one line of reasoning.
- [ ] The chosen mark passes every quality test, with the renders kept.
- [ ] Rejected variants are logged.
- [ ] Human trademark review is flagged before public use.
- [ ] Color, type, and shape decisions were handed to the foundations.
