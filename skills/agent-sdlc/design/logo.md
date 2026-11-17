# Logo

Read when making or changing a logo, after the [brand brief](brand.md) exists. The brief is the reference: every concept, variant, and change is checked against it. The ship set and how to present it: [logo-deliverables.md](logo-deliverables.md).

## Logo and mascot: decide the order

Whether a mascot fits is decided in [mascot.md](mascot.md). Write the decision down, then work in its order:

- **No mascot:** the logo only.
- **Logo first:** the logo, then a mascot that borrows its proportions and colors.
- **Character first:** the character already has equity or is the brand's main voice. Design it first, then draw the logo from it: a simplified head or silhouette.
- **One asset:** the character is the logo. Run the mascot steps and the ship gates on it.

## Kinds of mark

| Kind | Fits when | Watch for |
|---|---|---|
| Wordmark or lettering | The name is short and distinctive, or cannot be drawn | Set type alone is generic; draw or adjust the letters |
| Lettermark or monogram | A long name; a square icon is needed | Needs its own small version |
| Pictorial or descriptive | The product has a clear visual reference | Detail fills in when small; plan the small version |
| Emblem or badge | Heritage, craft, a place | High detail budget; needs a separate icon |
| Geometric constructed | Precision, systems | Looks generic without a stated construction |
| Character | A mascot fits ([mascot.md](mascot.md)) | Needs a simplified small version |
| Combination | A new name learned alongside a symbol | Each part must also work alone |

Choose the kind from the brief. Minimal is a choice the brief makes, not a default: descriptive marks beat abstract ones in one set of studies, and the simplest version of a mark hurt recognition in another (secondhand and abstract only). Detailed, complex marks are fine when the brief calls for them; draw them in stages (step 3). A variant may use a kind the brief does not favour if it is flagged off-brief.

## Process

1. **Study.** List marks you admire for this brief and a few anti-references (a generic glyph, no idea, clip art, needs a gradient), each with a reason. For each admired mark: the idea in one sentence, how it is built (stroke, radius, module), what it leaves out, and whether it holds at 16 px. Look at the real marks if you can browse; otherwise work from memory and label the list "from memory". Check the anti-references against the [default-mark questions](floor-checks.md#default-mark-questions).
2. **Diverge.** Write 20 to 30 rough concepts before drawing any finished SVG (a practitioner count, not a study). Each: the idea in one line, the brief line it serves, and why it is ownable, meaning this brand's and not any similar product's. Rough means a silhouette sketch or a line of text. No pass/fail gates here; they kill unusual ideas this early.
3. **Narrow and build 4 to 8 variants** that differ in approach (kind, idea, construction), not in color or small tweaks. Drop any concept whose only idea is its shape. Build each in stages: silhouette, then construction, then detail, rendering and looking after each. Quality falls as complexity rises (one benchmark, abstract read); building in stages is inferred from that. State for each variant:
   - **Construction vocabulary:** what this concept is built from, held consistent across the mark. A geometric mark names its stroke weights, radii, module, and angles; lettering names its tool, contrast, and stroke ends; a character or emblem names its line weight, shape language, and level of detail. Where geometry is used, prefer equal divisions, regular polygons, or circle packing. Do not claim a golden ratio.
   - **Optical corrections, in words:** for example "the circle overshoots the square by 1.5%, on purpose".
   - **Detail budget:** how much detail the brief allows, and where it goes (inference).

   A simple mark states its idea and construction like any other. A generic glyph with no stated idea is the low-effort result.
4. **Present and rank.** Show every variant at the same size in one view, on a light and a dark ground, plus a row at 32 and 16 px, using the host's visual tool ([logo-deliverables.md](logo-deliverables.md#present)). For each: the idea, its brief line, one line on concept (idea, ownability) and one on execution (construction, proportion, small size). Rank them with reasons; the owner decides. Do not treat your own aesthetic verdict as a gate: model judges did not reach majority agreement with designer panels (abstracts read).
5. **Iterate or accept.** Iterate within the chosen approach; each change cites the brief.
6. **Ship.** Run the gates below on the chosen mark and its responsive set, then build the [deliverables](logo-deliverables.md).

Log every drop, at every step including iteration, in the [drop log](index.md#drop-log) (inference).

## Making it as an agent

- **Draw SVG in code, then render and look.** You cannot see an SVG by reading its text. Render to PNG, view it, fix, render again. Nothing is shown unseen. Visual self-correction loops often fail, so look at each render yourself rather than trusting a loop.
- **Keep a set consistent.** Check every path against the declared construction vocabulary; generated sets drift.
- **Text:** use a real font whose licence allows logo use (inference, no licence text read); record the licence. Convert letters to outlines in the delivered SVG and check spelling letter by letter in the render.
- **Image models give pixels** and may misspell text (inference). Use their output only as a sketch and redraw it as paths; automatic tracing gives messy nodes.
- **Trademark clearance needs a person.** An agent's search is not clearance; flag the chosen mark for human or legal review before public use.

## Ship gates

For the chosen mark and its responsive set only, not for exploration. The 4x reading, silhouette, and stroke rules are inference; the others come from design guides ([sources/logo.md](../sources/logo.md)).

| Gate | Pass when |
|---|---|
| Small size | A square icon version, exported as a real 16 px PNG and viewed at 4x nearest-neighbour zoom: the main shape and its key detail are separate pixels, no stroke has gone grey or merged, and the silhouette matches the large mark. Check 32 and 64 px too. A wordmark is not judged at 16 px: state its minimum size or name the square partner used below it |
| Small version | Any mark with thin strokes or fine detail has a separately drawn heavier or simplified version for small sizes |
| One color | Solid black on white reads |
| Inverse | Solid white on black reads |
| No gradients | It works with no gradient, shadow, or transparency; a textured master has a one-color fallback |
| Silhouette | Filled solid, the outline still identifies it. For a stroke mark, fill the outer contour |
| Clear space | Stated now, as a multiple of a unit inside the mark, drawn on the sheet. Held later: nothing intrudes in mockups |
| Optical | Where round and flat parts must look the same size, the correction is made and recorded; judged at 100% and 16 px |
| Vector | Real `<path>` elements, no `<image>` inside the SVG, no `<text>`. Strokes expanded to fills where a tool can; if not, the report says strokes are live |
| Node count | Reported, not a gate |

## Hand off into tokens

For a full brand only; inference, no source maps a logo to tokens. Carry forward to [foundations.md](foundations.md):

- **Color:** take colors from the brief's outside reference (a material, trade, or place), checked against the mark on light and dark. A mark built to work in one color does not supply a palette.
- **Type:** families that match the mark's construction and the brief's words, with the reason.
- **Shape language:** the mark's corner radius, stroke weight, and curve set the UI's radii, icon stroke, and border weight.

## Done when

- [ ] The mascot decision and the work order are written down.
- [ ] The study lists admired marks and anti-references with reasons, labeled studied or from memory.
- [ ] 20 to 30 rough concepts exist, each with its idea, brief line, and why it is ownable.
- [ ] 4 to 8 variants differing in approach were rendered, viewed, and shown together on light, dark, and small size, each with its construction, concept and execution lines; off-brief ones are flagged.
- [ ] The variants are ranked with reasons and the owner chose.
- [ ] Every drop, including drops during iteration, is in the drop log with its reason.
- [ ] The chosen mark and its responsive set pass every ship gate, with the renders kept.
- [ ] Font licence recorded; human trademark review flagged before public use.
