# Logo deliverables

Read when presenting logo variants, and when the owner has chosen a mark and it passed the ship gates in [logo.md](logo.md). Each figure's source, label, and the open disagreements: [sources/logo.md](../sources/logo.md).

## The core set

1. **Lockups:** horizontal (primary) and stacked, each with its clear space and minimum size stated.
2. **Mark alone and wordmark alone,** where the brand has both.
3. **Small versions,** drawn for small sizes, not scaled down: fewer shapes, heavier strokes, no thin lines. Scaling the full mark down is the failure the sources name.
4. **One-color and inverse** versions of items 1 to 3.
5. **App icon,** favicon set, social avatar, and share image, each to its own figures below.

## Figures

Platform figures change; check the current platform docs before shipping. Labels are in the sources file.

| Item | Deliver |
|---|---|
| Favicon | `favicon.ico` with 16, 32, and 48 px images; `icon.svg` with a dark-scheme style; a 180 px touch icon PNG, opaque, mark inset on a solid ground; web manifest icons at 192 and 512 px, plus a 512 px maskable one |
| Search result icon | A square PNG or ICO, 48 px or larger. The largest search engine's favicon rules do not list SVG, so an SVG alone is not enough |
| Maskable web icon | The mark inside a central circle with a radius of 40% of the width |
| iOS and macOS app icon | One 1024 px square, unmasked; the system rounds the corners and makes the smaller sizes. No baked shadow, bevel, or blur. Dark and tinted versions if the brand needs control over them; otherwise the system generates them |
| Android app icon | Separate foreground and background layers at 108 dp, content inside the centred 66 dp; a monochrome layer for themed icons. Store listing: a 512 px square 32-bit PNG under 1024 KB, no rounded corners or shadow |
| Windows app icon | Unplated assets for light and dark themes; an ICO whose sizes you take from current platform documentation (16, 24, 32, 48, and 256 px is a secondhand list, not confirmed) |
| Social avatar | The mark inside a central circle about 80% of the width; a circle crop removes about 21% of a square |
| Share image | 1200 by 630 px, with alt text; 600 by 315 px at least |

Draw the 16 and 32 px versions of the square icon (or the small partner of a wordmark) by hand from the small version; do not rely on automatic downscaling. A wordmark is not drawn at 16 px: state its minimum size instead, as in the [small size gate](logo.md#ship-gates).

## Present

- **Use the host's visual tool.** Present in whatever canvas, preview, or design-board tool the host app provides, so the owner sees the work in place. Do not only save an image file to a library or folder. If the host has no such tool, render an HTML page and give its path.
- **Order:** the mark on a neutral ground; one-color and inverse; small sizes at 1x and at 4x zoom; then in context: a browser tab on light and dark, a dock or home screen, an app list, a circular avatar, and a share card.
- Variants (logo.md step 4) use the same tool: one view, same size, light and dark, a small-size row.

## Deliver

- Real source files: the SVG master, each lockup and version as SVG, the PNG and ICO sizes above, and the manifest entries. Never screenshots or exports from the presentation.
- A file list: each file, its size, and where it is used.
- Written down: clear space, minimum size per lockup, colors with their values, the font and its licence, whether strokes are live.

## Done when

- [ ] Every core-set item exists as a source file; lockups, marks, wordmarks, and small versions also in one-color and inverse.
- [ ] The square icon or small partner was drawn, not scaled, and checked as real 16 and 32 px files; each wordmark has a stated minimum size.
- [ ] The favicon set includes a PNG or ICO at 48 px or more, not only SVG.
- [ ] Favicon, app icon, avatar, and share image meet their own figures above, or the gap is named.
- [ ] The set was presented in context with the host's visual tool.
- [ ] The file list and the written specs are in the report.
