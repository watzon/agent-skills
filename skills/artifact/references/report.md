# Report

Long-form page: masthead, takeaways, contents, sections, optional appendix. The reader goes top to bottom.

Copy `templates/report.html` to the publish path. Replace every `<!-- SLOT: ... -->` and the placeholder text after it. Removing the comments alone leaves sample copy on the live page.

## Slots

| Slot | Fill |
| --- | --- |
| `TITLE` | Headline claim or subject. Put the same words in `<title>` and the `<h1>`. |
| `SUBTITLE` | One sentence: the finding or the scope. |
| `EYEBROW` | Doc type and date, or omit the `<p class="eyebrow">`. |
| `KEY_TAKEAWAYS` | Optional. 3-5 one-line bullets. A number or a specific, not a second sentence. Omit the whole `<aside>` on a short memo. |
| `TOC_ITEMS` | One `<li><a href="#id">...</a></li>` per `<h2>` in `SECTIONS`. Fill this after the sections exist. The page script rebuilds the list in the browser; the static list is what no-JS sees. |
| `SECTIONS` | One `<section id="...">` per topic, each with an `<h2>`. Lead with the conclusion. Use `<h3>`, `<table>`, `<pre>`, `<blockquote>`, and `<figure>` as needed. |
| `APPENDIX` | Optional. Cut the whole `<section class="appendix">` if you do not need it. |

## Content

Lead with what matters. The subtitle carries the finding. The takeaways carry the specifics. Each section opens with its conclusion. Method and raw data come later, or go in the appendix.

Plain language. Short sentences. Define a term of art on first use. State what was measured, what is inferred, and what is a guess.

A diagram or chart belongs here when it carries the point better than prose. Read `references/diagrams.md` before you draw.

Keep a contents list when there are three or more sections.

**Done when** no `SLOT` markers remain, no placeholder sentences remain, every TOC href matches a section id, and the `<title>` is specific to this document.
