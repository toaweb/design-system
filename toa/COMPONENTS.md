# toa:// Component Reference

> AI-oppslagsverk — alle CSS-klasser per komponent  
> Bergen, NO · 2026

Alle klasser refererer `--app-accent` — aldri hardkodede farger.  
Ingen `border-radius`. Ingen shadows. Ingen gradienter. Courier Prime overalt.

---

## Absolutte regler

```
border-radius: 0          — alltid, ingen unntak
ingen drop-shadows        — focus-ring er eneste glow
ingen gradienter          — 3-split topstripe er hard-edge stops
ingen emoji               — ☀/☾ theme-toggle er eneste unntak
Courier Prime overalt     — ingen andre fonter
lowercase løpende tekst   — UPPERCASE kun for labels/status/badges
--app-accent              — aldri raw shade-variabler i komponenter
ingen amber/gull/gul      — permanent bannlyst som accent
```

---

## Tokens — viktigste variabler

```css
/* Overflater */
--toa-bg         #04070E   /* sidebakgrunn */
--toa-surface    #080D18   /* cards, navbar, panels */
--toa-surface2   #0C1220   /* annenhver rad, inputs */
--toa-surface3   #0E1828   /* dype innsunket områder */
--toa-border     #243344   /* kortkanter */
--toa-border2    #2E4159   /* hover-kanter */

/* Tekst */
--toa-text       #F8FAFC   /* primærtekst */
--toa-muted      #B8C7D9   /* brødtekst */
--toa-dim        #9FB2C8   /* labels, meta */
--toa-hint       #6E8198   /* placeholders */

/* Semantisk */
--toa-danger     #F87171
--toa-warn       #F59E0B   /* kun advarsler, ALDRI som accent */

/* Typografi-skala */
--toa-fs-h1      64px
--toa-fs-h2      24px
--toa-fs-h3      16px
--toa-fs-body    12px
--toa-fs-small   10px
--toa-fs-label   8px       /* uppercase + 3px tracking */
--toa-fs-meta    7px

/* Layout */
--toa-max-width     1080px
--toa-side-padding  20px
--toa-touch-min     44px
```

---

## Layout

### Side-skjelett
```html
<div class="toa-page toa-graph">        <!-- min-height:100vh + grid-bakgrunn -->
  <!-- topstripe -->
  <!-- navbar -->
  <main class="toa-main">
    <div class="toa-wrap">             <!-- max-width 1080px, sentrert -->
      <!-- innhold -->
    </div>
  </main>
  <!-- footer -->
</div>
```

### Container-varianter
```html
<div class="toa-wrap">          <!-- max-width: 1080px -->
<div class="toa-wrap--wide">    <!-- max-width: 1280px -->
<div class="toa-container">     <!-- alias for toa-wrap -->
<div class="toa-section-gap">   <!-- padding: 28px 0 60px -->
```

### 12-kolonners grid
```html
<div class="toa-grid12">
  <div class="col-4">...</div>   <!-- 4 kolonner -->
  <div class="col-8">...</div>   <!-- 8 kolonner -->
</div>
<!-- Tilgjengelige: col-3 col-4 col-5 col-6 col-7 col-8 col-12 -->
<!-- Mobil (≤720px): alle kolonner → span 12 automatisk -->
```

### Boxed vs fullwidth
```html
<!-- Boxed (standard — innhold sentrert i toa-max-width) -->
<div class="toa-page">
  <div class="toa-wrap">...</div>
</div>

<!-- Fullwidth (ingen max-width på seksjonen) -->
<div class="toa-page">
  <div style="width:100%">...</div>
  <div class="toa-wrap">...</div>   <!-- bruk toa-wrap for innhold inne i fullwidth -->
</div>
```

---

## Topstripe

```html
<!-- Enkelt (alle apper unntatt portal) -->
<div class="toa-topstripe"></div>

<!-- Portal — 3-farge split (KUN toaweb.com) -->
<div class="toa-topstripe toa-topstripe--web">
  <div class="ts-blue"></div>
  <div class="ts-green"></div>
  <div class="ts-violet"></div>
</div>
```

---

## Navbar

```html
<nav class="toa-navbar">
  <div class="toa-navbar__inner">
    <span class="toa-navbar__prompt">toa://</span>

    <a href="/" class="toa-navbar__logo">
      appnavn<span class="toa-logo__sep">://</span>web
    </a>

    <div class="toa-navbar__links">
      <a href="/side" class="toa-navbar__link">side</a>
      <a href="/aktiv" class="toa-navbar__link active">aktiv</a>

      <!-- Lenke med dropdown -->
      <div class="toa-nav-item">
        <a href="#" class="toa-navbar__link">
          meny <span class="toa-nav-item__caret">▾</span>
        </a>
        <div class="toa-dropdown">
          <div class="toa-dropdown__head">kategori</div>
          <a href="/side" class="toa-dropdown__item">
            <span class="k">→</span> lenkenavn
            <span class="meta">ny</span>
          </a>
        </div>
      </div>
    </div>

    <div class="toa-navbar__right">
      <span class="toa-navbar__status">● LIVE</span>
      <button class="toa-navbar__btn">logg ut</button>
    </div>
  </div>
</nav>
```

---

## Logo

```html
<!-- Portal-modus — 3 farger (KUN toaweb.com) -->
<a href="/" class="toa-logo toa-logo--md">
  toa<span class="pc1">:</span><span class="pc2">/</span><span class="pc3">/</span>web
</a>

<!-- App-modus — én kategori-farge -->
<a href="/" class="toa-logo toa-logo--md">
  appnavn<span class="sep">://</span>web
</a>

<!-- Størrelser -->
toa-logo--xl   64px
toa-logo--lg   32px
toa-logo--md   20px
toa-logo--sm   15px
```

---

## Hero

```html
<section class="toa-hero">
  <!-- Valgfri shell-linje over tittel -->
  <div class="toa-shell-line">$ init appnavn <span class="toa-blink"></span></div>

  <h1 class="toa-hero__title">
    første ord<br>
    <span class="out">outline ord</span>
    <span class="dot">.</span>
  </h1>

  <p class="toa-hero__sub">
    Beskrivende undertekst. Maks 640px bred.
  </p>

  <div class="toa-hero__actions">
    <a href="#" class="toa-btn toa-btn--primary">kom i gang</a>
    <a href="#" class="toa-btn toa-btn--ghost">les mer</a>
  </div>
</section>
```

`.out` = outline-tekst med `--app-accent` stroke  
`.dot` = terminal-punktum i `--app-accent`

---

## URL-bar (page chrome)

```html
<div class="toa-urlbar">
  <div class="toa-urlbar__lead">HTTPS</div>
  <div class="toa-urlbar__path">
    <span class="dim">toa</span><span class="sep">://</span>appnavn
    <span class="dim">/sti/her</span>
  </div>
  <div class="toa-urlbar__status">● LIVE</div>
</div>
```

---

## Seksjonsoverskrift

```html
<!-- toa-seclab (patterns) -->
<div class="toa-seclab">
  <span class="toa-seclab__pill">SEKSJON</span>
  <span class="toa-seclab__num">03</span>
  <div class="toa-seclab__line"></div>
  <span class="toa-seclab__meta">valgfri meta</span>
</div>

<!-- toa-sec-hd (components) -->
<div class="toa-sec-hd">
  <span class="toa-sec-hd__label">SEKSJON</span>
  <span class="toa-sec-hd__count">12 elementer</span>
  <div class="toa-sec-hd__line"></div>
  <span class="toa-sec-hd__status">● LIVE</span>
</div>
```

---

## Knapper

```html
<!-- Primær — fylt med --app-accent -->
<button class="toa-btn toa-btn--primary">handling</button>

<!-- Ghost — transparent med border -->
<button class="toa-btn toa-btn--ghost">sekundær</button>

<!-- Outline — transparent med accent-border -->
<button class="toa-btn toa-btn--outline">outline</button>

<!-- Deaktivert -->
<button class="toa-btn toa-btn--disabled" disabled>deaktivert</button>

<!-- Størrelser -->
<button class="toa-btn toa-btn--primary toa-btn--sm">liten</button>
<button class="toa-btn toa-btn--primary toa-btn--lg">stor</button>
```

---

## Cards

### Standard kort
```html
<div class="toa-card">
  <div class="toa-card__stripe"></div>   <!-- 2px accent-stripe øverst -->
  <div class="toa-card__body">
    <p>Innhold her</p>
  </div>
</div>
```

### App-kort (venstre accent-stripe)
```html
<div class="toa-app-card">
  <div class="toa-app-card__body">
    <div class="toa-app-card__header">
      <div class="toa-app-card__icon">toa</div>
      <span class="toa-badge toa-badge--live">LIVE</span>
    </div>
    <div class="toa-app-card__name">appnavn://web</div>
    <div class="toa-app-card__desc">Kort beskrivelse av appen.</div>
    <div class="toa-app-card__tags">
      <span class="toa-tag">nuxt</span>
      <span class="toa-tag">fastapi</span>
    </div>
    <div class="toa-app-card__footer">
      <a href="#" class="toa-app-card__open">åpne</a>
      <button class="toa-app-card__about">info</button>
    </div>
  </div>
</div>
```

### Command-kort (toa-appc — stor versjon)
```html
<div class="toa-appc">
  <div class="toa-appc__hd">
    <div class="toa-appc__icon">toa</div>
    <span class="toa-cbadge toa-cbadge--live">LIVE</span>
  </div>
  <div class="toa-appc__bigname">
    appnavn<span class="sep">://</span>web
  </div>
  <div class="toa-appc__desc">Beskrivelse av appen.</div>
  <a href="#" class="toa-appc__cmd">start appnavn</a>
</div>
```

### Bloggpost-kort
```html
<div class="toa-postc">
  <div class="toa-postc__art">
    <img src="/images/posts/cover.webp" alt="tittel">
  </div>
  <div class="toa-postc__body">
    <div class="toa-postc__meta">
      <span>2026-06-04</span>
      <span>kategori</span>
    </div>
    <div class="toa-postc__title">Innleggstittel her</div>
    <div class="toa-postc__excerpt">Kort utdrag fra innlegget...</div>
    <a href="/blogg/slug" class="toa-postc__more">les mer</a>
  </div>
</div>
```

### Stat-kort
```html
<div class="toa-stat">
  <div class="toa-stat__label">TOTAL</div>
  <div class="toa-stat__value">1 337</div>
  <div class="toa-stat__desc">siden forrige uke</div>
</div>
```

---

## Badges og tags

```html
<!-- Badges — status -->
<span class="toa-badge toa-badge--live">LIVE</span>
<span class="toa-badge toa-badge--wip">WIP</span>
<span class="toa-badge toa-badge--planned">PLANNED</span>
<span class="toa-badge toa-badge--error">ERROR</span>
<span class="toa-badge toa-badge--ai">AI</span>

<!-- Category badges -->
<span class="toa-cbadge toa-cbadge--live">LIVE</span>
<span class="toa-cbadge toa-cbadge--wip">WIP</span>
<span class="toa-cbadge toa-cbadge--planned">PLANNED</span>

<!-- Tag / chip -->
<span class="toa-tag">nuxt</span>
<span class="toa-tag">fastapi</span>
```

---

## Skjemaelementer

```html
<!-- Input -->
<div>
  <label class="toa-label">BRUKERNAVN</label>
  <input type="text" class="toa-input" placeholder="skriv her...">
</div>

<!-- Textarea -->
<div>
  <label class="toa-label">MELDING</label>
  <textarea class="toa-textarea" rows="4"></textarea>
</div>

<!-- Select -->
<div>
  <label class="toa-label">VELG</label>
  <select class="toa-select">
    <option>alternativ 1</option>
    <option>alternativ 2</option>
  </select>
</div>

<!-- Checkbox -->
<div class="toa-check toa-check--checked"></div>
<div class="toa-check"></div>

<!-- Toggle -->
<div class="toa-toggle toa-toggle--on"></div>
<div class="toa-toggle"></div>
```

---

## Sidebar

```html
<nav>
  <a href="/dashboard" class="toa-sidebar-item">
    <!-- inline SVG ikon -->
    dashboard
  </a>
  <a href="/innlegg" class="toa-sidebar-item toa-sidebar-item--active">
    innlegg
  </a>
  <a href="/innstillinger" class="toa-sidebar-item">
    innstillinger
  </a>
</nav>
```

---

## Lister

```html
<!-- Directory list (key → value) -->
<div class="toa-dl">
  <div class="toa-dl__row">
    <span class="toa-dl__k">SERVER</span>
    <span class="toa-dl__v">AX41-NVMe · Helsinki</span>
  </div>
  <div class="toa-dl__row">
    <span class="toa-dl__k">STATUS</span>
    <span class="toa-dl__v toa-status">● online</span>
  </div>
</div>

<!-- Arrow list -->
<ul class="toa-ul">
  <li>første punkt</li>
  <li>andre punkt</li>
</ul>

<!-- Timeline -->
<div class="toa-timeline">
  <div class="toa-timeline__item">
    <div class="toa-timeline__date">2026-06-04</div>
    <div class="toa-timeline__title">Hendelse</div>
    <div class="toa-timeline__body">Beskrivelse av hendelsen.</div>
  </div>
</div>
```

---

## Tabell

```html
<table class="toa-table">
  <thead>
    <tr>
      <th>NAVN <span class="toa-sort">↑</span></th>
      <th>STATUS</th>
      <th>DATO</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>radnavn</td>
      <td><span class="toa-badge toa-badge--live">LIVE</span></td>
      <td class="num">2026-06-04</td>
    </tr>
  </tbody>
</table>
```

---

## System-tilstander

```html
<!-- Tom tilstand -->
<div class="toa-state toa-state--empty">
  <div class="toa-state__prompt">$ ls -la</div>
  <div class="toa-state__msg">ingen resultater funnet</div>
  <div class="toa-state__hint">prøv et annet søk</div>
</div>

<!-- Feil -->
<div class="toa-state toa-state--error">
  <div class="toa-state__prompt">ERROR</div>
  <div class="toa-state__msg">noe gikk galt</div>
</div>

<!-- Suksess -->
<div class="toa-state toa-state--success">
  <div class="toa-state__prompt">OK</div>
  <div class="toa-state__msg">operasjonen var vellykket</div>
</div>

<!-- Laster -->
<div class="toa-state toa-state--loading">
  <div class="toa-state__prompt">LOADING</div>
  <div class="toa-state__msg">henter data</div>
</div>
```

---

## Toast-meldinger

```html
<div class="toa-toast toa-toast--success">● lagret</div>
<div class="toa-toast toa-toast--error">● feil ved lagring</div>
<div class="toa-toast toa-toast--info">● oppdatert</div>
```

---

## Deploy-feed

```html
<div class="toa-feed">
  <div class="toa-feed__hd">
    <div class="toa-feed__dot"></div>
    LIVE FEED
  </div>
  <div class="toa-feed__row">
    <span class="toa-feed__ts">2026-06-04 17:40</span>
    <span class="toa-feed__app toa-feed__app--tools">toablog</span>
    <span class="toa-feed__ev">DEPLOY</span>
    <span class="toa-feed__msg">v2.1.4 → production</span>
  </div>
</div>
<!-- toa-feed__app--tools / --games / --secure for kategori-farge -->
```

---

## Footer

```html
<footer class="toa-foot">
  <div class="toa-wrap">
    toa<span class="sep">://</span>web · Bergen, NO · 2026 · ─┘
  </div>
</footer>

<!-- Eller med border: -->
<footer class="toa-footer">
  <div class="toa-footer__inner">
    toa:// · Bergen, NO · 2026
  </div>
</footer>
```

---

## Ikoner

Alle ikoner er outline SVG med `stroke="currentColor"`. Bruk inline — ikke img-tag.

```html
<!-- Størrelser: width/height settes manuelt (standard: 16×16 eller 20×20) -->
<!-- Farge arves fra foreldreelementet via currentColor -->

<!-- actions/ -->
icons/actions/add.svg
icons/actions/delete.svg
icons/actions/edit.svg
icons/actions/logout.svg
icons/actions/publish.svg
icons/actions/refresh.svg
icons/actions/unpublish.svg

<!-- status/ -->
icons/status/alert.svg
icons/status/error.svg
icons/status/info.svg
icons/status/live.svg
icons/status/planned.svg
icons/status/wip.svg

<!-- ui/ -->
icons/ui/database.svg
icons/ui/deploy.svg
icons/ui/docker.svg
icons/ui/external.svg
icons/ui/filter.svg
icons/ui/home.svg
icons/ui/lock.svg
icons/ui/post.svg
icons/ui/search.svg
icons/ui/server.svg
icons/ui/settings.svg
icons/ui/star.svg
icons/ui/tag.svg
icons/ui/terminal.svg
```

### Icon tile (ikon med bakgrunn)
```html
<div class="toa-icon-tile">
  <!-- inline SVG -->
</div>
<div class="toa-icon-tile toa-icon-tile--accent">
  <!-- inline SVG -->
</div>
<div class="toa-icon-tile toa-icon-tile--lg">
  <!-- inline SVG -->
</div>
```

---

## Typografi-klasser

```html
<h1 class="toa-h1">stor overskrift</h1>
<h1 class="toa-h1"><span class="toa-h1--outline">outline</span></h1>
<h2 class="toa-h2">seksjonstittel</h2>
<h3 class="toa-h3">undertittel</h3>
<p class="toa-body">brødtekst i --toa-muted</p>
<p class="toa-small">liten tekst i --toa-dim</p>
<span class="toa-label-text">LABEL TEKST</span>
<span class="toa-meta">META INFO</span>
<code class="toa-code">kode-snippet</code>

<!-- Terminal-prefix -->
<span class="toa-prompt">kommando her</span>   <!-- → prefiks -->
<span class="toa-shell">bash kommando</span>    <!-- $ prefiks -->
```

---

## Prosatekst (blogg/artikkel)

```html
<article class="toa-prose" data-density="reading">
  <h2>Overskrift</h2>
  <p>Brødtekst med <a href="#">lenke</a> og <strong>uthevet tekst</strong>.</p>
  <code>inline kode</code>
</article>
<!-- data-density="reading" bumper font-size: body→15px, small→13px -->
```

---

## Dividers

```html
<div class="toa-divider"></div>          <!-- solid 1px -->
<hr class="toa-div-dashed">             <!-- dashed -->
<hr class="toa-div-dotted">             <!-- dotted -->
```

---

*COMPONENTS.md · toa:// ecosystem · Bergen, NO · 2026*
