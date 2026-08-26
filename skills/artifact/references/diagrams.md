# Diagrams

A diagram earns its place when a cold reader can see a mechanism they would otherwise have to assemble from prose. If a sentence is faster, write the sentence.

## What to draw

**Show the mechanism, not its name.** A box labelled "cache" repeats the prose. The path a request takes through it, the two stores it sits between, and the arrow that disappears when the cache is gone say what the words cannot.

**Comparing options?** Draw the difference. Two architectures side by side, a before and an after, the one edge each option adds or removes. A labelled box per option with nothing connecting them is a restated list.

**Match complexity to the stakes.** A one-hop question is a three-box diagram. A migration that reroutes writes needs the queue, the writer, the reader, and the ordering arrow.

**Label the arrows.** An unlabeled arrow is "related somehow". `writes`, `invalidates`, `polls every 30s` is information. A legend is only worth it when the same encoding repeats.

## Inline SVG

Hand-author `<svg>` with native shapes and `<text>`. No libraries, no runtime, no external images.

- Size by `viewBox="0 0 W H"` and let CSS scale it (`max-width: 100%; height: auto`).
- Theme through page tokens in `style` attributes. `var()` fails silently on bare SVG presentation attributes. Never hardcode near-black or white: those vanish on one of the two grounds.
- Arrowheads are a `<marker>` or a small `<polygon>`, never an image.
- Keep labels short, about 12-14px at the drawn scale. Explanatory sentences go in the caption.
- Align to a grid. Eyeballed offsets read as noise.
- One figure, one claim. Wrap in `<figure>` with a `<figcaption>`. Give the `<svg>` `role="img"` and an `aria-label` that states the same claim.
- Stay self-contained. No `<script>`, `<style>`, or `<foreignObject>` inside the SVG.
