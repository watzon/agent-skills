# Explainer

A page that teaches. A lede says what the reader will understand. Then either numbered steps or looser sections. A recap at the end.

Copy `templates/explainer.html` to the publish path. Keep one body flavor and delete the other wrapper. Replace every `<!-- SLOT: ... -->` and the sample copy after it.

## Flavor

**Steps** (default). A progression start to finish. How something works. 3-6 steps. Fewer is a report. More should split.

**Sections.** A tour of a system, a change, or an architecture. 2-7 topics, cut at the material's joints. Code usually carries the weight. Open with one wide flow diagram only when the subject has a structural story.

## Slots

| Slot | Fill |
| --- | --- |
| `TITLE` | The reader's question. Same words in `<title>` and the `<h1>`. |
| `LEDE` | Two or three sentences: what they will understand, and why it matters. |
| `STEPS` | One `<li class="step">` per idea: heading, 1-3 short paragraphs, a `.visual`. Optional `<p class="callout">` for a gotcha. |
| `SECTIONS` | One `<section class="topic">` per joint: `<h2>`, short prose, `.visual` blocks. |
| `RECAP` | 3-5 bullets in the reader's new vocabulary. |

## Visuals

In the steps flavor, most steps carry a diagram. Reach for `<pre>` alone only when the concept is symbolic (syntax, exact values). Code belongs in `<pre>`, not inside an SVG.

Give every SVG a `viewBox` and no width or height. Color through tokens in `style` attributes. Read `references/diagrams.md`.

**Done when** one flavor remains, no `SLOT` markers remain, no sample headings remain, and each kept step or topic teaches one idea.
