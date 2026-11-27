# RangeFoundry brand

Logos, wordmarks, colors and type of RangeFoundry and its projects, with the script that generates the logos.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="rangefoundry/rangefoundry-dark.svg">
  <img src="rangefoundry/rangefoundry-light.svg" width="400" alt="RangeFoundry">
</picture>

## Logos

| Folder | Mark |
|---|---|
| `rangefoundry/` | the family: cog with a case head |
| `autolever/` | cog with a lever |
| `workbench/` | cog with a pressure curve |
| `buildguide/` | cog with a page |

Each folder holds the icon (`-icon.svg`, `-icon-1024.png`) and the wordmark for light and dark backgrounds (`-light.svg`, `-dark.svg`, and 1280 x 640 PNGs; the dark one is the GitHub social preview). Project wordmarks carry "RangeFoundry" small above the project name.

To change a mark, edit `generate.py` and run `python3 generate.py` in the dev container (`.devcontainer/`), which pins the font and render tools so the PNGs come out byte-identical. Commit the generated files with the script change.

## Colors and type

`tokens.css` holds the colors and the font every RangeFoundry site uses: the base shared with the sister brands (surface, ink, muted, danger, focus) and the RangeFoundry blue as the one accent. `examples/index.html` renders every token; open it from a clone in a light and a dark system scheme.

| Role | Light | Dark | Use |
|---|---|---|---|
| surface | `oklch(0.97 0.003 95)` | `oklch(0.19 0.004 250)` | page background; theme-color `#f6f5f3` and `#121416` |
| surface-alt | `oklch(0.94 0.003 95)` | `oklch(0.23 0.004 250)` | cards, panels, code |
| ink | `oklch(0.21 0.004 250)` | `oklch(0.96 0.003 95)` | text, headings and links |
| muted | `oklch(0.45 0.006 250)` | `oklch(0.78 0.005 250)` | secondary text |
| danger | `oklch(0.5 0.17 32)` | `oklch(0.78 0.13 35)` | errors and destructive actions, always with a word or icon |
| focus | ink | accent | 2px focus outline |
| accent, accent-hover | `#1971c2`, `#1864ab` | `#4dabf7`, `#74c0fc` | primary buttons, active tab; accent text on surface-alt takes accent-hover |
| accent-tint, on-accent | `#e7f5ff`, `#ffffff` | `#172a40`, surface | active tab ground, text on an accent fill |
| line | `oklch(0.88 0.004 250)` | `oklch(0.31 0.005 250)` | separators only |
| control-line | `oklch(0.6 0.006 250)` | `oklch(0.55 0.006 250)` | edges of inputs and outlined buttons |
| select | `#fab005` | `#fab005` | selection highlight in drawings |
| warn | amber | amber | safety panels only |

Links take the text color and stay underlined, also on hover; there is no link color. The header of `tokens.css` lists the contrast of every pair (WCAG 2.2 AA in both schemes).

Type is Albert Sans (`--font-sans`): display 300, body 400, strong 600. Code keeps the site's monospace stack. `fonts/` holds its Latin subsets from [`@fontsource-variable/albert-sans`](https://www.npmjs.com/package/@fontsource-variable/albert-sans) 5.3.0 under the SIL Open Font License 1.1 (`fonts/OFL.txt`).

Accent: Mantine's built-in `blue` (shade 8 light, shade 4 dark), the same `primaryColor` the Ballistics app uses.

- Copy, do not link: copy `tokens.css` and `fonts/` into the site, with `fonts/` next to the stylesheet that holds the tokens, and note the version from the file's first comment. A site that loads either from another origin breaks when it changes.
- The scheme follows the system through `color-scheme: light dark` and `light-dark()`. A site toggle sets `color-scheme` on the root element; MkDocs Material's `data-md-color-scheme` does so through the rules at the end of `tokens.css`.
- MkDocs Material sites (AutoLever, Feeder): paste `tokens.css` as the first rules of `extra.css` and map Material's `--md-*` variables to it.
- Mantine apps (Ballistics): keep `primaryColor: 'blue'`; take the neutrals and the font from `tokens.css` as CSS variables.

### Version 2

What a site that copies version 1 changes:

- `--page` is gone: the page background is `--surface`. Cards and panels move from `--surface` to `--surface-alt`, which now holds one panel step.
- `--link` is gone: links use the text color (`--ink`), underlined.
- New: `--danger`, `--focus` and `--font-sans` with the `@font-face` rules for Albert Sans; copy `fonts/` with the file.
- New values for surface, surface-alt, ink, muted, line, control-line and the dark on-accent. The blue accent and amber keep their values.
- The dark scheme now also follows the system setting, not only MkDocs Material's `slate` scheme.

To change a color, edit `tokens.css`, raise its version, check every pair against the contrast ratios in its header, then update each site.
