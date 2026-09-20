# Big Easy Custom Cars &#8211; redesign mockup

Homepage mockup for [bigeasycustomcars.com](https://www.bigeasycustomcars.com/),
built on the design system carried over from the Big Easy Bathrooms and
TurnKey Pool redesigns.

**Live preview:** https://angel062388.github.io/bigeasycustomcars-redesign/

## What this is

A static, single-page mockup. No build step, no dependencies. Open
`index.html` or serve the folder.

| File | What it is |
|---|---|
| `index.html` | The homepage mockup |
| `hero-preview.html` | Earlier hero-only study, kept for reference |
| `assets/hero.mp4` | Hero video, 1280x720, 10s, 24fps, audio stripped, 3.4 MB |
| `assets/hero-poster.jpg` | Poster frame, 71 KB, used on mobile and reduced-motion |
| `assets/logo.png` | The client's own logo, unchanged |

## Design system

- **Type:** Fraunces (display serif) + Outfit (sans). Outfit is already
  self-hosted on the live site.
- **Palette:** automotive ink with the Big Easy orange, retuned so it does not
  glow. Orange switches value by ground (`--amber` on dark, `--amber-ink` on
  light) so it clears WCAG AA either way.
- **Buttons:** only `btn-p`, `btn-s`, `btn-l`, `btn-o` exist.
- **Motion:** `.rv` reveal gated on a `.js` class, fully disabled under
  `prefers-reduced-motion`.
- **Radius:** 20px on all cards and imagery.
- No em dashes. Non-ASCII as HTML entities.

## Service-areas coverage map

Layout is the Big Easy Bathrooms one (head / map card / numbered side list),
rebuilt for a car shop. BEB ran water through a navy pipe with a drop
travelling it. This is a night map: asphalt roads, animated amber lane dashes,
and a lifted pickup driving the main route via `animateMotion`.

All eight of the client's cities are placed with their real parishes. Lake
Pontchartrain and the Mississippi are real; pin positions are not to scale.
Under 700px the pin labels collapse to numbered dots, the same behaviour BEB
uses. Every animation stops under `prefers-reduced-motion`.

## Verified

- No console errors
- No horizontal overflow at 375px
- Hero video autoplays muted and loops on desktop
- On phones under 768px and under reduced-motion, the video source is detached
  so the 3.4 MB file never downloads; the poster shows instead
- Builds filter and FAQ accordion both work
- All 30 estimate buttons resolve to `#quote-form`

## Still placeholder, flagged for the client

- **Build gallery tiles** are empty panels marked "Photo needed". Real build
  photography is the highest-return item in the project.
- **Review quotes** are placeholders. The live site shows 4.8 from 80+ reviews
  but does not publish the text.
- **Stat numbers** conflict on the live site: "500+ Builds" in the hero against
  "64 Custom Cars Built" in the counter, plus "244K square feet of build space".
  These need confirming before launch.
- **Four dashed service cards** (lift kits, wheels and tires, off-road builds,
  blackout packages) are proposals. The live site sells these in its copy but
  has no page for any of them.
