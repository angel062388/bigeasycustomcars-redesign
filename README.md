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

## Builds collection carousel

Pattern taken from the Gunther Werks collection: light ground, the active
vehicle centred and full colour, its neighbours scaled back, desaturated and
half off-frame, then the model name, spec pills, circular arrows and one
outlined CTA underneath. Wraps around, dots track the active slide, arrow keys
work inside the stage, and the slide transition is disabled under
`prefers-reduced-motion`.

### Photography: stock, and labelled as such

The five carousel images are **Unsplash stock**, used under the
[Unsplash Licence](https://unsplash.com/license) (free for commercial use, no
attribution required). Unsplash was chosen over Freepik, Vecteezy and Pngtree
specifically because those require attribution or a paid licence for much of
their catalogue.

**These are not Big Easy Custom Cars builds.** The visible "Stock photo" tags
were removed at the client's request, so nothing on the rendered page says so
any more. This README and the source comments are now the only record.

> **Before this page goes public:** replace every image below with real job
> photography, or the site implies work the shop did not do.

The carousel deliberately **alternates cars and trucks**, because this is a
full custom shop and not a truck shop (see the positioning note below).

| # | File | Unsplash photo ID | Subject | Type |
|---|---|---|---|---|
| 1 | `build-blackout.jpg` | `1601252300554-4ad551483bd2` | Blacked-out lifted Silverado | Truck |
| 2 | `build-muscle.jpg` | `1609386464913-4cbfa39de540` | Challenger, amber halo headlights | Car |
| 3 | `build-trail.jpg` | `1559416523-140ddc3d238c` | Tan Tacoma, black wheels, light bar | Truck |
| 4 | `build-graphics.jpg` | `1625231334168-35067f8853ed` | Shelby with red racing stripes | Car |
| 5 | `build-offroad.jpg` | `1598110579456-122e6342daee` | Red RAM, grille guard, bronze wheels | Truck |
| 6 | `build-luxury.jpg` | `1628519592419-bf288f08cef5` | Matte black exotic on a wet street | Car |
| 7 | `build-suspension.jpg` | `1659653198574-3218ea02ed36` | Wheel and coilover detail | Both |

Rejected after review: a Silverado in deep snow (reads wrong for New Orleans),
a white RAM shot from the rear (weakest of the set), semi-trucks (wrong
business), and any frame containing a person (house rule: no people, no faces).

All seven were re-encoded at 1280px wide, quality 72, progressive:
**2,380 KB to 1,307 KB**, a saving of 1,072 KB.

## Positioning: NOT a truck-only shop

An earlier draft of this mockup was written truck-led. **That was wrong** and
the client corrected it. The evidence was on their own site the whole time:

- The portfolio filters on the live homepage are All / Trucks / SUVs /
  **Luxury** / Off-Road, and the section is headed "Our Custom **Car** Projects".
- All eight live service pages are vehicle-agnostic: paint and graphics,
  upholstery, audio, window tint, tuning, body kits, lighting, restoration.
- The brand name is Custom **Cars**, and the logo is a classic pickup.

What misled the draft was the homepage body copy, which talks almost entirely
about lifted trucks and SUVs. That copy is unrepresentative of the business.
The mockup now reads **cars, trucks and SUVs** throughout: hero lede, services
lede, builds lede, meta description, FAQ answers, footer and the quote form
dropdown.

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

## Service card photography

All twelve service cards lead with a real photograph. Five are new Unsplash
downloads; seven reuse images from the builds carousel where the subject
genuinely matches the service, which avoids extra downloads.

| Service | Image | Source |
|---|---|---|
| Engine Tuning &amp; Performance | `svc/svc-engine.jpg` | Unsplash `1752774580658-730f2fafbe0b` |
| Lighting Upgrades | `builds/build-muscle.jpg` | reused, the halo headlights |
| Custom Paint &amp; Graphics | `builds/build-graphics.jpg` | reused, the racing stripes |
| Interior Upholstery | `svc/svc-interior.jpg` | Unsplash `1563986642669-49162177a0bc` |
| Window Tinting &amp; Detailing | `builds/build-luxury.jpg` | reused, matte black on a wet street |
| Body Kits &amp; Modifications | `svc/svc-bodykit.jpg` | Unsplash `1577801342097-045874893030` |
| Audio &amp; Lighting | `svc/svc-audio.jpg` | Unsplash `1758411898478-4f7e70d533d9` |
| Restoration &amp; Rebuilds | `svc/svc-restoration.jpg` | Unsplash `1591278169757-deac26e49555` |
| Lift Kits &amp; Suspension | `builds/build-suspension.jpg` | reused, the coilover detail |
| Wheels &amp; Tires | `builds/build-offroad.jpg` | reused, the bronze wheels |
| Off-Road Builds | `builds/build-trail.jpg` | reused, the trail rig |
| Blackout Packages | `builds/build-blackout.jpg` | reused, the blacked-out truck |

The five new files were reviewed by eye before use and optimised from 698 KB
down to 348 KB. All are Unsplash Licence, same as the carousel.

## Safety net on scroll animations

Reveals, the trust counters and the tacho sweep are all driven by
IntersectionObserver. In some embedded and background rendering contexts IO
exists but never fires, and the page would then sit with invisible content and
counters reading a literal zero.

**That is exactly the bug the client's live site has today**, where a dead
scroll library leaves eight service cards invisible. So a 3 second timer
forces anything unfinished to its final state. The page can degrade to "no
animation", never to "no content".

## Reviews are INVENTED

The four testimonials in the reviews section were **written for the mockup at
the client's request**. They are not real customers and not real quotes.

The live site shows a 4.8 rating from 80+ reviews but does not publish the
review text, so the genuine ones have to be pulled from Google.

> **Before this page goes public:** swap in real reviews. Publishing invented
> testimonials as genuine is a problem for the client, not just a content gap.

## Known robustness fixes worth keeping

- The reviews grid uses `minmax(min(286px,100%),1fr)`. A bare `minmax(286px,1fr)`
  cannot shrink below its ideal width and pushed the page wider than the
  viewport on very narrow screens.
- The trust strip is flex, not grid. Five tiles never divide evenly, and grid
  leaves the odd tile on the last row with a hole beside it.
