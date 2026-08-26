# Table

A filter box, a dense sortable table, a row count. Data lives in two JSON script blocks. The bundled renderer draws the rows.

Copy `templates/table.html` to the publish path. Replace every `<!-- SLOT: ... -->` and the sample JSON.

## Slots

| Slot | Fill |
| --- | --- |
| `TITLE` | Same words in `<title>` and the `<h1>`. |
| `SCOPE` | Optional header meta. |
| `COLUMNS` | JSON array of `{key, label, type}`. `type` is `"text"` or `"num"`. |
| `ROWS` | JSON array of objects keyed by those column keys. |
| `FOOTER_NOTE` | Source and timestamp, or omit the footer. |

## Data

- `"num"` values are JSON numbers: `1234.5`, never `"$1,234.50"`. Put the unit in the column label.
- Missing is `null` or an omitted key. Never `0`, `"N/A"`, or `"-"`.
- Dates go in `"text"` columns as ISO-8601 (`2026-08-26`) so alpha sort is chrono sort.
- Both blocks are strict JSON: double quotes, no trailing commas, no comments.
- Inside JSON strings, write `<\/` and `<\u0021--` so the script tag does not end early.
- Pre-round numbers to the precision worth showing.
- Embed the full set up to a few thousand rows. Beyond that, subset and say what was cut in `FOOTER_NOTE`.

Keep the ids and classes the script reads: `dt`, `dt-filter`, `dt-count`, `dt-columns`, `dt-rows`, `arrow`, `sorted`, `num`, `empty`.

**Done when** no `SLOT` markers remain, both JSON blocks parse, every `"num"` cell is a number or null, and the filter plus header sort work.
