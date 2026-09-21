# Big Easy Custom Cars &#8211; redesign mockup

Redesign mockup for [bigeasycustomcars.com](https://www.bigeasycustomcars.com/),
built on the design system carried over from the Big Easy Bathrooms and
TurnKey Pool redesigns.

**Live preview:** https://angel062388.github.io/bigeasycustomcars-redesign/

## What this is

Seven static pages. No build step, no dependencies. Open `index.html` or serve
the folder.

| File | What it is |
|---|---|
| `index.html` | Homepage |
| `about.html` | About |
| `services.html` | Services |
| `services-areas.html` | Service Areas (slug matches the live site's) |
| `testimonials.html` | Testimonials |
| `contact.html` | Contact |
| `blog.html` | Blog (proposed posts, see below) |
| `hero-preview.html` | Earlier hero-only study, kept for reference |
| `assets/hero.mp4` | Hero video, 1280x720, 10s, 24fps, audio stripped, 3.4 MB |
| `assets/hero-poster.jpg` | Poster frame, 71 KB, used on mobile and reduced-motion |
| `assets/logo.png` | The client's own logo, unchanged |

### The six inner pages are generated, not hand-written

Each one is produced by a script in `scratch/` (not committed) that slices the
header, trust strip, quote band and footer straight out of `index.html`, so the
pages cannot drift apart. **Edit `index.html`, then re-run all six scripts:**

```
python scratch/build-about.py
python scratch/build-services.py
python scratch/build-areas.py
python scratch/build-testimonials.py
python scratch/build-contact.py
python scratch/build-blog.py
```

Every inner page carries a written `<title>`, a written meta description and
exactly one H1. The live site has an H1 on the homepage only and a meta
description on no page at all.

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

## Reviews: now the client's own, no longer invented

The reviews were placeholders while I believed the live site published none.
It does, on `/testimonials/`, a page the live homepage never links to. On
2026-09-21 all placeholder copy was replaced with the client's own text,
verbatim:

| Reviewer | Town | Build |
|---|---|---|
| Tyler B. | Metairie, LA | Camaro, custom paint and graphics |
| Monique R. | Covington | Full interior upholstery |
| Darren S. | Slidell, LA | Truck, engine tuning |
| Rachel D. | Covington | Interior upholstery |

The homepage shows the first three. `testimonials.html` shows all four.

> **Still to confirm with the client:** that these four are genuine customers.
> The same site carries five demo team pages all named "John Smithson", so
> placeholder copy is known to exist on it. The live site also claims 4.8 from
> 80+ reviews, so there should be far more than four to pull from Google.

## Blog: the six posts do not exist yet

The live `/blog/` page is **empty**. It renders its heading and an empty post
loop, and `post-sitemap.xml` lists only `/blog/` itself. It is also linked
from **nowhere** on the live site: not the menu, not the footer. The mockup
adds it to the footer only, because the header menu has to match live.

The six cards on `blog.html` are **proposed posts**, one per service, so the
layout can be reviewed. Each title targets a real keyword. Excerpts are
placeholders and deliberately state no prices and no legal limits, because
none are verified. Cards are not links, because there are no post pages.

Ahrefs Keywords Explorer, **United States**, pulled 2026-09-22. Volumes are
US-wide monthly searches, **not** New Orleans figures.

| Card | Target keyword | US vol/mo | KD |
|---|---|---|---|
| How Much Does It Cost to Lift a Truck? | how much does it cost to lift a truck | 800 | 0 |
| Car Wrap vs Paint | car wrap vs paint | 600 | 0 |
| Ceramic Coating vs Wax | ceramic coating vs wax | 500 | 0 |
| Louisiana Window Tint Law | louisiana window tint law | 400 | 1 |
| Reupholster Car Seats | how much to reupholster car seats | 350 | 1 |
| Classic Car Restoration Costs | how much does it cost to restore a classic car | 150 | 2 |

Next in line, same pull: leveling kit vs lift kit (600, KD 0), best window
tint percentage (150, KD 0), does tuning void warranty (90, KD 0), custom
paint job cost (80, KD 7), car audio installation cost (70, KD 0).

## Known robustness fixes worth keeping

- `html{scroll-padding-top:108px}` (88px on phones). The header is sticky and
  in flow, so without it every in-page jump, including every Free Estimate
  button, landed the section heading under the header. The value is the
  **unshrunk** header height on purpose: the header shrinks after the jump and
  pulls the content up 30px, so the shrunk height (78px) left the eyebrow 2px
  under the header when measured.

- The reviews grid uses `minmax(min(286px,100%),1fr)`. A bare `minmax(286px,1fr)`
  cannot shrink below its ideal width and pushed the page wider than the
  viewport on very narrow screens.
- The trust strip is flex, not grid. Five tiles never divide evenly, and grid
  leaves the odd tile on the last row with a hole beside it.
