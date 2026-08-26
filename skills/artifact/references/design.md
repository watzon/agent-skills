# Design

Calibrate treatment, not whether to design. A memo gets the same care as a landing page. What changes is how loud the page is.

**Utilitarian.** Plan, memo, dashboard, table, most reports. Real hierarchy, considered spacing, a palette that belongs to the subject. No giant hero. Flourishes stay small.

**Editorial.** A landing page, game, or tool they will keep or share. Load `anti-slop-design` and give the page a point of view.

When unsure, a well-composed utilitarian page is the safe call. An over-designed identity sometimes is not.

## Before you write

1. Honor what is already there. If the repo has a design system, tokens, or theme file, use it. This file fills gaps. It does not override the project's own words.
2. Pin the subject: one concrete thing, its audience, and the page's single job. Distinctive choices come from that world, not from a house look.
3. Sketch tokens first: 4-6 named hex values, two or three type roles, one or two sentences of layout. Then build from that sketch.
4. Name the page. The `<title>` is a short noun phrase specific to this subject, two to four words. Not a category label. Not an explainer after a colon.

## Page rules

- One `index.html` with inline CSS and JS. No build step. Google Fonts is the only allowed external request, and every face needs a fallback stack.
- Real content only. No lorem. Placeholder numbers stay out of published output. Sample metrics belong only on a mockup, and they must read as sample.
- Every control that looks live must work.
- Copy speaks from the user's side of the screen. Errors say what went wrong and what to do next.
- Paint light and dark as a set. Tokens on `:root`. Overrides in `prefers-color-scheme` and `[data-theme]`. Change a token in every scope that declares it, or it snaps back. `body` gets an explicit background from those tokens.
- Pair type on purpose. Set a scale and stay on it. Running text stays under 65 characters wide.
- Ground the palette in the subject. Do not spend that freedom on the usual AI defaults: warm cream plus terracotta, purple-to-blue hero, Inter or Space Grotesk as the safe pair, `rounded-2xl` on every card.
- Structure encodes information. Numbered markers only when the content is a sequence.
- A dashboard or tool is scanned, not read. State should be visible at a glance. Semantic color (good / warning / critical) is separate from the accent.

The templates ship a quiet default. Retune it toward this subject, or restyle the `<style>` block. Keep the slot contract and any ids the script reads.
