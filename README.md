# RangeFoundry brand

Logos, wordmarks and colors of RangeFoundry and its projects, with the script that generates the logos.

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

## Colors

`tokens.css` is the palette every RangeFoundry site uses.

| Role | Light | Dark | Use |
|---|---|---|---|
| page | `#ffffff` | `#10121b` | page background |
| surface, surface-alt | `#f6f8fc`, `#eef0f6` | `#161923`, `#1e212c` | cards, panels, code |
| ink | `#1d2130` | `#e9ebf1` | text, headings |
| muted | `#555a6d` | `#acb0c0` | secondary text |
| accent | `#1971c2` | `#4dabf7` | primary buttons, active tab, links |
| line | `#dcdfe9` | `#2f323f` | separators only |
| control-line | `#7b7f91` | `#6f7485` | edges of inputs and outlined buttons |
| warn | amber | amber | safety panels only |

Neutrals: [Mantine colour generator, seed #63687C](https://mantine.dev/colors-generator/?color=63687C). Accent: Mantine's built-in `blue` (shade 8 light, shade 4 dark), the same `primaryColor` the Ballistics app uses.

- MkDocs Material sites (AutoLever, Feeder): paste `tokens.css` as the first rules of `extra.css` and map Material's `--md-*` variables to it.
- Mantine apps (Ballistics): keep `primaryColor: 'blue'`; take the neutrals from `tokens.css` as CSS variables.
- Copy, do not link: a site that loads this file from another origin breaks when it changes. Note the version from the file's first comment in your copy.

To change a color, edit `tokens.css`, raise its version, check every pair against the contrast ratios in its header, then update each site.
