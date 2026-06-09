# WEB_DESIGN_TRENDS_2026.md
# Web Design Trends & Typography — Referanseguide 2026

> For bruk av Claude Design og Claude Code ved nye prosjekter.  
> Gjelder alle prosjekter **utenfor** toa://-økosystemet.  
> For toa://-prosjekter: se `design/toa/HANDOFF.md` og `design/toa/COMPONENTS.md`.

---

## Velg riktig trend for prosjekttypen

Ikke alle trender passer alle prosjekter. Start her.

| Prosjekttype | Anbefalte trender | Unngå |
|---|---|---|
| SaaS / tech-produkt | Dark Mode First, Bento Grid, Glassmorphism 2.0 | Neo-Brutalism, Y2K |
| Gaming / community | Dark Mode First, Neo-Brutalism, Anti-Grid, Scanlines | Glassmorphism, Claymorphism |
| Blogg / editorial | Typography First, Scroll Storytelling, Sustainable | Bento Grid, Kinetic Typography |
| Landingsside / marketing | Bento Grid, Typography First, Kinetic Typography | Glassmorphism |
| Portfolio / kreativt byrå | Neo-Brutalism, Anti-Grid, Expressive Typography | Minimalism |
| Dokumentasjon | Sustainable Design, Typography First | Kinetic Typography, Glassmorphism |
| E-handel | Bento Grid, Human-Centered, Kinetic Typography | Neo-Brutalism |
| Premium / luksus | Typography First, Minimalism, Editorial | Neo-Brutalism, Y2K |

---

## Trender i 2026 — hva som faktisk vant

Basert på halvårs-analyse (H1 2026): **Bento Grid og Dark Mode er fortsatt dominerende.** Kinetic Typography er mer polering enn substans. 3D/WebGL ble for tung for de fleste. AI-drevet personalisering brøt mot GDPR.

**To uventede vinnere i 2026:**
1. **AI Readability Layers** — `llms.txt`, `agents.json`, schema markup. Sider uten dette er usynlige for AI-mediert søk.
2. **Anti-Grid Brutalism** — en motreaksjon mot Bento Grid. Brutt grid, rå HTML-estetikk, monospace overalt. Signaliserer autentisitet.

---

## 01 — Bento Grid

**Hva:** Modulær kortbasert layout inspirert av japansk matboks. Ulike kortstørrelser skaper visuell rytme.

**Passer til:** SaaS, dashboards, produktsider, landingssider.

**CSS-mønster:**
```css
.bento-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 1rem;
}

/* Store featured-kort */
.bento-card--featured { grid-column: span 8; grid-row: span 2; }
.bento-card--wide     { grid-column: span 6; }
.bento-card--small    { grid-column: span 4; }
.bento-card--tall     { grid-column: span 4; grid-row: span 2; }

/* Alle kort: ingen border-radius for neo-brutalist stil */
.bento-card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  padding: 1.5rem;
  overflow: hidden;
}
```

**Regler:**
- Bryt monotoni med varierte kortstørrelser — aldri like store
- Padding konsistent på tvers av alle kort
- Hover: subtil border-color-endring, ingen shadows
- Mobil: alle kort → full bredde (én kolonne)

---

## 02 — Typography First

**Hva:** Typografi er det primære designelementet. Store hero-overskrifter (80–140px), editorial uttrykk.

**Passer til:** Blogger, magasiner, premium landingssider, editorial design.

**CSS-eksempel:**
```css
/* Oversized hero — fyller viewport-bredde */
.hero-title {
  font-size: clamp(3rem, 10vw, 9rem);
  font-weight: 800;
  letter-spacing: -0.04em;
  line-height: 0.95;
}

/* Klippet tekst — bevisst overflow */
.hero-title--clipped {
  white-space: nowrap;
  overflow: hidden;
}

/* Bilde fyller gjennom teksten */
.hero-title--image-fill {
  background-image: url('hero-bg.webp');
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
}
```

**Regler:**
- En font-familie, maks to typefaces
- Heading og body skal kontrastere — ikke to like fonter
- Hvit space er et strukturelt element, ikke tomrom

---

## 03 — Neo-Brutalism / Tactile Brutalism

**Hva:** Rå layouts, synlige grenser og grids, funksjon over dekorasjon. Avviser "floating elements"-estetikken.

**Passer til:** Gaming, kreative byråer, artist-portfolios, indie-produkter.

**CSS-prinsipper:**
```css
/* Ingen border-radius — null, ikke en eneste px */
* { border-radius: 0 !important; }

/* Synlige, tunge borders */
.card {
  border: 2px solid currentColor;
  box-shadow: 4px 4px 0 currentColor;  /* offset shadow, ikke blur */
}

/* Sterk hover — offset-shift */
.card:hover {
  transform: translate(-2px, -2px);
  box-shadow: 6px 6px 0 currentColor;
}

/* Monospace overalt */
body { font-family: 'Courier New', monospace; }
```

**Regler:**
- Offset shadows (X Y 0 color) — aldri blur-based
- Høy kontrast — sort/hvit eller én sterk accent
- Monospace font forsterker terminal/rå-estetikk
- Gjelder spesielt for toa://-stil

---

## 04 — Dark Mode First

**Hva:** Design mørkt først. Lyse tekster på mørk bakgrunn, sterke accent-farger.

**Passer til:** Alle tech-produkter, gaming, developer-tools.

**CSS-tokens (mørkt):**
```css
:root {
  --color-bg:      #0a0a0a;
  --color-surface: #111111;
  --color-border:  #222222;
  --color-text:    #f0f0f0;
  --color-muted:   #888888;
  --color-accent:  #your-brand-color;
}

/* Light mode som override, ikke standard */
@media (prefers-color-scheme: light) {
  :root {
    --color-bg:      #fafafa;
    --color-surface: #ffffff;
    --color-border:  #e0e0e0;
    --color-text:    #0a0a0a;
    --color-muted:   #666666;
  }
}
```

**Regler:**
- Mørkt er default — light er override
- Accent-farger skal fungere på mørk bakgrunn
- Tekst-kontrast minimum 7:1 for WCAG AAA

---

## 05 — Glassmorphism 2.0

**Hva:** Subtil blur, transparente paneler, frosted glass-effekt. Moderne AI/fintech-estetikk.

**Passer til:** SaaS, fintech, AI-produkter. **Ikke** gaming eller neo-brutalism-prosjekter.

```css
.glass-panel {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

/* Subtil — ikke overdriv blur */
.glass-subtle {
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(8px);
  border: 1px solid rgba(255, 255, 255, 0.06);
}
```

**Regler:**
- Kun subtilt — 5–10% opacity max
- Virker best på mørk bakgrunn med fargerikt bakgrunnsbilde
- `backdrop-filter` krever at bakgrunnen er synlig — funker ikke på solid bakgrunn
- **Ikke bruk i toa://-prosjekter** — glassmorphism er eksplisitt forbudt

---

## 06 — Scroll Storytelling

**Hva:** Historiedrevet scrolling, sticky seksjoner, progressive animasjoner.

**CSS scroll-animations (native — ingen JS):**
```css
/* Native scroll-driven animation */
@keyframes fade-in {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}

.scroll-reveal {
  animation: fade-in linear both;
  animation-timeline: view();
  animation-range: entry 0% entry 30%;
}

/* Sticky seksjon */
.sticky-section {
  position: sticky;
  top: 0;
  height: 100vh;
}
```

**Regler:**
- Bruk native CSS `animation-timeline: view()` — ikke biblioteker
- Respekter `prefers-reduced-motion`
- Aldri blokkér scrolling — animasjoner skal være additive

---

## 07 — Sustainable Design

**Hva:** Minimal JavaScript, Core Web Vitals-fokus, bedre ytelse.

**Passer til:** Alle prosjekter — dette er ikke en trend, det er baseline 2026.

**Stack-valg:**
- Statisk innhold → Astro 6 eller Hugo (null JS by default)
- Dynamiske apper → Nuxt 4 med SSR
- Aldri tunge biblioteker for simple animasjoner

**Core Web Vitals mål:**
```
LCP (Largest Contentful Paint) < 2.5s
INP (Interaction to Next Paint) < 200ms   ← erstattet FID i 2024
CLS (Cumulative Layout Shift)   < 0.1
```

---

## 08 — Anti-Grid Brutalism

**Hva:** Motreaksjon mot Bento Grid. Brutt layout, rå HTML, monospace overalt, overlappende elementer.

**Passer til:** Indie-produkter, developer-tools, alt som vil signalisere "ikke en mal".

**Gjenkjennende trekk:**
- Elementer som bevisst overlapper
- Rotert tekst (`transform: rotate(-3deg)`)
- Eksponert grid (`outline: 1px solid red` som estetikk)
- Monospace som displayfont, ikke bare kode

---

## 09 — AI Readability (ny standard 2026)

**Hva:** `llms.txt`, schema.org markup, `agents.json`. Sider uten dette er usynlige for AI-mediert søk.

**Ikke en visuell trend — men kritisk for SEO i 2026.**

Se `SEO_STANDARD_2026.md` for full implementasjon. Kort:
```
public/llms.txt         ← hvem AI-er kan sitere og hva
public/robots.txt       ← hva søkemotorer og AI kan indeksere
<script type="application/ld+json">  ← BlogPosting, WebSite schema
```

---

## Typography System 2026

### Anbefalte fonter

| Font | Karakter | Bruk |
|---|---|---|
| **Inter Variable** | Nøytral, høy lesbarhet | UI, navigasjon, dashboards, dokumentasjon |
| **Geist** | Teknisk, moderne | SaaS hero-seksjoner, developer-tools |
| **Newsreader** | Redaksjonelt, menneskelig | Blogger, langlesing, artikler |
| **Playfair Display** | Premium, magasin | Premium hero-overskrifter, editorial |
| **Fraunces** | Karakter, kreativ | Merkevarer, landingssider med personlighet |
| **Manrope** | Mer personlighet enn Inter | Alternativ UI-font |
| **Satoshi** | Moderne, populær | Landingssider, branding |
| **Courier Prime** | Terminal, rå | toa://-prosjekter, neo-brutalism |

### Font Stack per prosjekttype

```css
/* SaaS / dashboard */
--font-ui:      'Inter Variable', system-ui, sans-serif;
--font-display: 'Geist', 'Inter Variable', sans-serif;

/* Blogg / editorial */
--font-ui:      'Inter Variable', system-ui, sans-serif;
--font-body:    'Newsreader', Georgia, serif;
--font-display: 'Playfair Display', Georgia, serif;

/* Gaming / neo-brutalist */
--font-ui:      'Courier Prime', 'Courier New', monospace;
--font-display: 'Courier Prime', monospace;

/* Premium landingsside */
--font-ui:      'Manrope', system-ui, sans-serif;
--font-display: 'Fraunces', Georgia, serif;
```

### Type-skala (fluid, clamp-basert)

```css
--text-xs:   clamp(0.75rem,  1vw,   0.875rem);
--text-sm:   clamp(0.875rem, 1.2vw, 1rem);
--text-base: clamp(1rem,     1.5vw, 1.125rem);
--text-lg:   clamp(1.125rem, 2vw,   1.5rem);
--text-xl:   clamp(1.5rem,   3vw,   2.25rem);
--text-2xl:  clamp(2rem,     5vw,   4rem);
--text-hero: clamp(3rem,     10vw,  9rem);
```

---

## Hva som er ute i 2026

```
❌ Tunge drop-shadows (box-shadow med blur)
❌ Ekstreme border-radius på alt (mer enn 8px)
❌ Floating elements / card-hover-lift
❌ Muted pastell-fargepaletter
❌ Identiske bento-grid-maler (ser alle like ut)
❌ 3D og WebGL på marketing-sider (performance-kostnad for liten gevinst)
❌ AI-drevet personalisering uten GDPR-hensyn
❌ FID som performance-metrikk (erstattet av INP)
```

---

## Hurtigguide: Start nytt prosjekt

```
1. Hva er prosjekttypen?         → Se tabell øverst
2. Mørkt eller lyst tema?        → Dark Mode First som default
3. Hvilken font-kombinasjon?     → Se Font Stack per prosjekttype
4. Hvilken layout-stil?          → Bento Grid (standard) eller Anti-Grid (posisjonering)
5. AI Readability satt opp?      → llms.txt + schema.org (alltid)
6. Core Web Vitals i fokus?      → Minimal JS, riktige bilder, ingen layout shift
```

---

*WEB_DESIGN_TRENDS_2026.md · Bergen, NO · Juni 2026*
