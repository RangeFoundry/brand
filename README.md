# OpenReloading brand

The colours every OpenReloading site uses, in one file you copy into your site.

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

## Use it

- MkDocs Material sites (AutoLever, Feeder): paste `tokens.css` as the first rules of `extra.css` and map Material's `--md-*` variables to it.
- Mantine apps (Ballistics): keep `primaryColor: 'blue'`; take the neutrals from `tokens.css` as CSS variables.
- Copy, do not link: a site that loads this file from another origin breaks when it changes. Note the version from the file's first comment in your copy.

## Change it

Change `tokens.css`, raise its version, check every pair against the contrast ratios in its header, then update each site.
