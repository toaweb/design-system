# toa:// Design System

> Design guidelines, component references and web design standards  
> Bergen, NO · 2026

This repository is the single source of truth for all design standards
used across the toa:// ecosystem and beyond.

---

## For AI assistants (Claude Design, Claude Code)

Reference these raw URLs directly in your sessions:

### toa:// ecosystem

| File | Purpose |
|---|---|
| [HANDOFF.md](https://raw.githubusercontent.com/toaweb/design-system/main/toa/HANDOFF.md) | Rules, load order, core principles |
| [COMPONENTS.md](https://raw.githubusercontent.com/toaweb/design-system/main/toa/COMPONENTS.md) | All CSS classes per component |
| [toa-tokens.css](https://raw.githubusercontent.com/toaweb/design-system/main/toa/css/toa-tokens.css) | Colors, typography, spacing tokens |
| [toa-themes.css](https://raw.githubusercontent.com/toaweb/design-system/main/toa/css/toa-themes.css) | portal / software / gaming / auth theme mapping |
| [toa-components.css](https://raw.githubusercontent.com/toaweb/design-system/main/toa/css/toa-components.css) | All component classes |
| [toa-patterns.css](https://raw.githubusercontent.com/toaweb/design-system/main/toa/css/toa-patterns.css) | Page-level patterns |

### General web design

| File | Purpose |
|---|---|
| [WEB_DESIGN_TRENDS_2026.md](https://raw.githubusercontent.com/toaweb/design-system/main/general/WEB_DESIGN_TRENDS_2026.md) | Design trends, typography system, project-type guide |

---

## When to use which

### Use `toa/` when:
- Building any app within the toa:// ecosystem (toaportal, toablog, toabackup, toascribe, toagames, toawowchar)
- The project will integrate with Authentik SSO
- The project lives at `*.toaweb.com` or a toa:// branded domain

### Use `general/` when:
- Building for a client outside toa://
- Building a standalone project with its own visual identity (e.g. gamingforge.net)
- Starting a greenfield project without an existing brand

---

## toa:// Design Rules (non-negotiable)

```
border-radius: 0          — always, no exceptions
no shadows                — focus-ring is the only glow
no gradients              — hard-edge color stops only
Courier Prime everywhere  — no other fonts
lowercase body text       — UPPERCASE for labels/status/badges only
--app-accent              — never raw hex colors in components
no amber/gold/yellow      — permanently banned as accent
```

## Theme per app category

Set `data-theme` on the `<html>` element:

| App | data-theme | Accent |
|---|---|---|
| toaweb.com portal | `portal` | 3-color stripe (blue/green/violet) |
| toablog, toacms, toascribe | `software` | green #22C55E |
| toagames, toawowchar | `gaming` | blue #2585DA |
| toabackup, auth pages | `auth` | violet #A855F7 |

## CSS Load Order

Always load in this order:

```html
<link rel="stylesheet" href="toa-tokens.css">
<link rel="stylesheet" href="toa-themes.css">
<link rel="stylesheet" href="toa-components.css">
<link rel="stylesheet" href="toa-patterns.css">
```

---

## Repository structure

```
design-system/
│
├── toa/                    ← toa:// ecosystem (use for toa:// projects)
│   ├── HANDOFF.md          ← rules and principles
│   ├── COMPONENTS.md       ← component reference
│   ├── css/
│   │   ├── toa-tokens.css
│   │   ├── toa-themes.css
│   │   ├── toa-components.css
│   │   └── toa-patterns.css
│   ├── fonts/              ← Courier Prime (4 variants)
│   └── icons/              ← SVG icons (actions/ status/ ui/)
│       ├── actions/
│       ├── status/
│       └── ui/
│
└── general/                ← General web design (use for non-toa projects)
    └── WEB_DESIGN_TRENDS_2026.md
```

---

*Maintained by Tor · toaweb · Bergen, NO*
