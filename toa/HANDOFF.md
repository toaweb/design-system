# toa:// Brand Identity — handoff

Reusable component library + reference for the whole **toa:// ecosystem**.
Built on the locked toa:// design system (Courier Prime, three colour families,
sharp corners, no shadows, no gradients, dark-first).

## The one rule that drives everything
Each app belongs to **one of three categories**, and the category sets the colour:

| Category | Colour | `data-theme` | Apps |
|---|---|---|---|
| **software** | green `#22C55E` | `software` | blog, cms, ratings, windrose, tools |
| **gaming** | blue `#2585DA` | `gaming` | wowchar, games, scmissions, sctraining |
| **auth** | violet `#A855F7` | `auth` | auth, backup, vault |
| portal (directory) | 3-colour | `portal` | toa://web only |

Set `data-theme` on `<html>` (or any element) and everything under it recolours.
Components reference `--app-accent` only — never raw shade vars. That is what makes
theme-switching work; keep it that way.

## Load order (always)
```html
<link rel="stylesheet" href="toa-tokens.css">      <!-- colour + type foundations -->
<link rel="stylesheet" href="toa-themes.css">      <!-- the 3-category mapping (NEW) -->
<link rel="stylesheet" href="toa-components.css">  <!-- base components -->
<link rel="stylesheet" href="toa-patterns.css">    <!-- page-level patterns (NEW) -->
```
`kit-chrome.css` styles the documentation pages only — **do not ship it.**

## Files
```
Brand Identity.html        full component library (20 sections, live)
toa-tokens.css             foundations — from the design system, ship as-is
toa-themes.css             NEW — category → colour mapping (software/gaming/auth/portal)
toa-components.css         base components — from the design system, ship as-is
toa-patterns.css           NEW — url-bar, hero, nav/dropdown, grid, cards, lists, feed, states…
kit-chrome.css             docs scaffolding ONLY — not part of the product
fonts/                     Courier Prime (4 weights)
icons/                     outline SVG, stroke="currentColor" (status / ui / actions)
favicon.svg                toa://web logo mark
sections/                  each of the 20 sections as its own standalone file + index.html
templates/                 single-page · single-post · archive (full pages)
```

## How to build from this
1. Ingest `toa-tokens.css` + `toa-themes.css` + `toa-components.css` + `toa-patterns.css`.
   Drive `data-theme` from the route / app slug.
2. Take `sections/*.html` one at a time and convert each to a Vue 3 SFC
   (`<script setup>`), reusing the CSS classes already defined — do not invent new ones.
3. `templates/*.html` show how the pieces compose into real pages.
4. Icons: inline the SVGs (they use `currentColor`); no icon font.

## Hard rules (do not violate)
- `border-radius: 0` everywhere · no drop-shadows (focus-ring is the only glow)
- no gradients (the 3-split portal topstripe is hard-edged stops)
- no emoji (☀/☾ theme-toggle excepted) · Courier Prime / Courier New only
- no amber/gold/yellow as accent
- components reference `--app-accent`, not raw shades
- logo has two modes: portal (3-colour) or app (single category colour) — never mix
- lower-case running copy; UPPERCASE only for labels/status/badges

`$ toa://brand-identity · v1.0 · Bergen, NO · 2026 · ─┘`
