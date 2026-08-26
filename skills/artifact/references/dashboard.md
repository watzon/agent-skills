# Dashboard

Glance page: a row of KPI tiles, one primary chart, one breakdown table.

Copy `templates/dashboard.html` to the publish path. Replace every `<!-- SLOT: ... -->`. Then fit the layout to the data: add a chart, drop a section, extend the grid. The slots are the start, not the cage.

## Slots

| Slot | Fill |
| --- | --- |
| `TITLE` | Page title. Same words in `<title>` and the `<h1>`. |
| `SCOPE` | Date range or filter, or omit the subtitle. |
| `KPI_TILES` | 2-5 `.kpi` cards. One headline number each. Optional `.delta`. |
| `CHART_TITLE` | Name the finding, not the axes. |
| `PRIMARY_CHART_SPEC` | JSON in `#primary-chart-spec`. See the comment in the template. |
| `BREAKDOWN_TITLE` | What the table is. |
| `BREAKDOWN_ROWS` | Header cells and one `<tr>` per row. `class="num"` on numeric columns. |
| `FOOTER_NOTE` | Source and timestamp from the conversation, or omit the footer. |

## Data

Replace every placeholder number, or remove that section. Do not invent a KPI, a trend, a date, or a source.

No time dimension? Do not invent one. Use `"type": "bar"` or `"type": "donut"`, hand-draw an SVG, or drop the chart and lead with tiles and the table.

Format for scanning: $1.2M, 98.7%, 412ms. Keep the breakdown to about ten rows. Roll the tail into Other.

Color deltas by meaning, not direction. `up` / `down` pick the arrow. Add `good` or `bad` when a decrease is the improvement (latency, cost, errors).

A narrow range far from zero flattens on a zero-floored axis. Set `y.min` / `y.max` and say so in the chart title.

The bundled script draws line, bar, and donut from the spec. Same spec, same pixels. Do not invent values to fill the chart.

**Done when** no `SLOT` markers remain, no placeholder zeros remain, and every number on the page came from the conversation or a file the user pointed at.
