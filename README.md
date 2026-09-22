# Big Easy Custom Cars &#8211; redesign mockup

Redesign mockup for [bigeasycustomcars.com](https://www.bigeasycustomcars.com/),
built on the design system carried over from the Big Easy Bathrooms and
TurnKey Pool redesigns.

**Live preview:** https://angel062388.github.io/bigeasycustomcars-redesign/

## What this is

Twenty-one static pages. No build step, no dependencies. Open `index.html` or
serve the folder.

| File | What it is |
|---|---|
| `index.html` | Homepage |
| `about.html` | About |
| `services.html` | Services |
| `services-areas.html` | Service Areas (slug matches the live site's) |
| `testimonials.html` | Testimonials |
| `contact.html` | Contact |
| `blog.html` | Blog (proposed posts, see below) |
| `post-how-much-does-it-cost-to-lift-a-truck.html` | The model blog post every future post follows |
| `audio-lighting.html` | Audio & Lighting: the model for all eight service pages |
| `engine-tuning-performance.html`, `body-kits-modifications.html`, `custom-paint-graphics.html`, `interior-upholstery.html`, `lighting-upgrades.html`, `restoration-rebuilds.html`, `window-tinting-detailing.html` | The other seven live services, same template |
| `lift-kits-suspension.html`, `wheels-tires.html`, `off-road-builds.html`, `blackout-packages.html` | **NEW services with no live page.** Copy written; client must approve |
| `abita-springs.html` | **City page: Abita Springs** (live: `/services-areas/abita-springs/`), the model for the other seven service-area pages |
| `hero-preview.html` | Earlier hero-only study, kept for reference |
| `assets/hero.mp4` | Hero video, 1280x720, 10s, 24fps, audio stripped, 3.4 MB |
| `assets/hero-poster.jpg` | Poster frame, 71 KB, used on mobile and reduced-motion |
| `assets/logo.png` | The client's own logo, unchanged |

### Every inner page is generated, not hand-written

Each one is produced by a script in `scratch/` (not committed) that slices the
header, trust strip, quote band and footer straight out of `index.html`, so the
pages cannot drift apart. **Edit `index.html`, then re-run all nine scripts:**

```
python scratch/build-about.py
python scratch/build-services.py
python scratch/build-areas.py
python scratch/build-testimonials.py
python scratch/build-contact.py
python scratch/build-blog.py
python scratch/build-post.py
python scratch/build-service.py
python scratch/build-area.py
```

Blog titles, dates, images and excerpts live in `scratch/blog_data.py`, shared
by the listing and the post, so the two cannot drift.

Every inner page carries a written `<title>`, a written meta description and
exactly one H1. On the live site, `/services/` and `/services-areas/` have
neither an H1 nor a meta description, and Audio & Lighting's meta description
is auto-generated and cut off. (Corrected 2026-09-22: this line used to say
only the homepage had an H1. All eight live service pages have one, and so
does the Abita Springs page, which also has a written meta description of
158 characters.)

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

### Card dates are placeholders

Added at the client's request so the listing reads as a live blog: weekly,
Tuesdays, newest first (Sep 15 back to Aug 11, 2026). Replace each with the
real publish date when the post goes live.

## The model blog post

`post-how-much-does-it-cost-to-lift-a-truck.html` is the template for every
future post, laid out on the pattern of the TurnKey sister project's posts
and built only from this site's homepage parts:

- **Hero:** the hero component with the post's photo in place of the video,
  a heavier centre-weighted scrim, category, date, read time and byline.
- **Sticky rail:** table of contents on the service board's numbered rows,
  lit for the section being read, then a Free Estimate / Call Us card.
- **Article:** the About page's prose styles, a "short answer" box, a cost
  table (stacks on phones), check lists, a photo, an FAQ.
- **Then:** trust strip, three related posts, the quote form.
- **Structured data:** BlogPosting and FAQPage JSON-LD. The URL is the
  intended live slug; add the featured image URL at launch.

The article was written with the blog-content-creator skill: 1,110 words,
no banned words, keyword in the title, first 100 words, an H2 and the close.
**Every price is a typical US parts range, not a Big Easy price**, taken from:

| Figure | Source |
|---|---|
| Leveling kits $99 to $1,000; premium kits over $10,000; labor about the kit price | [AmericanTrucks](https://www.americantrucks.com/cost-to-lift-a-truck.html), 2022-11-30 |
| Body lift kits $180 to $450 | [RealTruck](https://realtruck.com/blog/cost-to-lift-a-truck/), updated 2025-12-30 |
| Suspension lift kits $1,000 to $5,000+; install 7 to 15 shop hours | [NYE Chevrolet](https://www.nyechevrolet.com/complete-guide-to-truck-lift-kit-costs/), 2026-01-12 |
| Aftermarket parts do not void a warranty; the maker must prove the part caused the damage | [FTC](https://consumer.ftc.gov/articles/auto-warranties-and-auto-service-contracts) |

> **Before publishing:** the client approves the copy and confirms the date.

## The model service page: Audio & Lighting

`audio-lighting.html` (live: `/services/audio-lighting/`) is the template for
all eight service pages. `scratch/build-service.py` is **data-driven**: each
service is one dict, and the section renderers never change, so the other
seven pages are a matter of adding their content.

Every section is a homepage component: video hero, trust strip, the About
page's text-and-photo split (twice), the services bay board (10 rows), the
blog card shell, the process gauge, the Louisiana plates, the coverage map,
**Our Other Services** (the homepage services board itself, sliced at build
time minus this page's own row: 11 of 12) and the quote band (its form
preselects "Interior or audio").

**Copy is the client's own, word for word**, reorganised into those
components. The live H1 is kept. Two process-stage headings are authored
("Scope, Timeline and Cost", "Fitted and Tested") because the gauge has five
stages and the live page has three steps; marked in the markup.

Flags for the client:

- **A fourth "years" figure.** This page says "over 25 years of experience".
  Home says 15, About says 20+. The counter strip on this page shows reviews,
  rating and parishes instead, so no animated number contradicts the text.
- **The live site has 8 reviews, not 4.** This page's slider carries four
  that `/testimonials/` does not. Kevin T. (Kenner) is the one about audio and
  lighting, so he leads the plates here.
- **Photos:** four are the client's own, referenced from the live site
  (`/wp-content/uploads/`), the rest are the mockup's Unsplash stock. Three
  repeat, never next to each other. Row 08 uses a wide banner, slightly
  upscaled. More audio and lighting photos would fix both.
- **Live meta description** is auto-generated from the first paragraph, about
  300 characters and cut off mid-sentence. The mockup's is written, 137.
- **Live copy** leans on words like "seamlessly", "ensure" and "flawlessly".
  Kept as the client's; a copy pass would tighten it.
- **Structured data:** `Service` JSON-LD with nine service areas. Add the
  street address once the client supplies one.

## The service pages: how they are built

`scratch/build-service.py` builds all twelve: the eight live services and the
four new ones. **No client copy is typed** for the eight live services.
`scratch/live_parse.py` reads a snapshot of each live service page
(`scratch/live/<slug>.html`, gitignored, taken with curl) and hands over its
headings, paragraphs, list items (in page order), FAQ, testimonials and
photos. Each page then has a short plan saying which live section goes into
which homepage component. Text arrives verbatim, with curly quotes as entities
and em dashes as commas.

**Why parse instead of retype:** it found a service the hand-built Audio page
had missed (DSP Processors, now restored) and seven photo URLs that had been
typed from truncated listings and did not exist. Photos are now looked up by
a unique fragment of their file name, and the build stops if a fragment
matches none or several.

Every page is checked at build time for one H1, no em dashes, a title of 60
characters or less, a meta description of 155 or less, and a link to both the
live homepage and the live contact page. Structured data: `Service` and
`FAQPage` on all twelve.

**Every service page has an FAQ** (client rule, 2026-09-22). Three carry the
live page's own FAQ verbatim (Engine Tuning, Paint & Graphics, Restoration).
The other nine are **written**: six questions each, every answer restating
what that page's live copy (or, for the new pages, the client's site
elsewhere) already says. The only outside facts are the FTC rule on
aftermarket parts and warranties, the Louisiana 2025 tint change, and the lift
facts sourced for the blog post; each FAQ's HTML comment names its sources.
No prices, times or promises beyond the client's own. **Client must approve.**
The build refuses to write a service page without an FAQ, and checks all
written copy against the banned-word list.

**Other Services rows are links** (client request): the eight live services
link to their pages on the live site (new tab); the four new services link to
their new mockup pages. The page's own service is never listed.

**The four new service pages** (Lift Kits & Suspension, Wheels & Tires,
Off-Road Builds, Blackout Packages) have no live page to parse, so their copy
is written from what the client says elsewhere on their site: the brands
(FOX, BDS, Fuel Off-Road, Toyo Tires, Rough Country), the platforms (Ford,
Chevy, GMC, Jeep, RAM), "trail rigs with max clearance and armor", "blackout
packages and color-match builds", smoked lenses, steel bumpers, power steps.
Each runs 1,050 to 1,190 words, of which 606 to 831 are new. The build checks
the target phrase appears in the title, the opening, an H2 and the closing.
They are in the Services menu, which now lists twelve services against the
live site's eight (client request).

Shared changes made for them: the quote form gained four options its
dropdown was missing (engine tuning, body kits, lighting, restoration); the
FAQ cluster sizes itself to its question count and its counter now reads
"10 of 10" (it read "010 of 010"); service H1s over 50 characters get a
smaller size and wider measure (they took 5-6 lines on a phone); the menu
and footer service links point at the pages.

### Flags from the live service pages

| Page | Flag |
|---|---|
| Engine Tuning | An intro sentence is cut off mid-way on the live page ("...to finish your build,"). Left out. |
| Body Kits | The "Seamless Installation and Paint Matching" section appears twice live. Used once. |
| Paint & Graphics | "Commercial and Fleet Wraps" repeats a stray "Common accent areas include:" line. Left out. |
| Lighting | "Upload photos of your truck or SUV..." describes an upload the mockup form lacks. Left out. |
| Restoration | FAQ answers left out: "244,000 square feet" and "64 custom car builds" (About says 500+). The opening section repeats the About story nearly word for word. |
| Tint & Detailing | "What Is Automotive Window Tinting?" appears twice live. Used once. **Tint law, corrected 2026-09-22:** Act 143 of 2025 (HB 119) lowered the front side window limit from 40% to 25%, effective Aug 1, 2025 (FastDemocracy, BillTrack50). An earlier note here said the paragraph "holds for trucks and SUVs"; that check used the 2023 statute text, which predates the change. Whether trucks and SUVs still keep the exemption for windows behind the driver (the live copy's "any darkness") is **unconfirmed**: the enacted text could not be reached (legis.la.gov refused connections). The written FAQ states only the front-side rule. |
| Blackout Packages | Smoked lenses are a client-listed service; whether tinted head and tail lights are legal in Louisiana was not checked. |
| All | Seven client photos show people (a mechanic, a painter, a tint installer, a polisher, drivers, a gloved hand) and are not used, per the no-people rule. |

## The city page: Abita Springs (model for all eight)

`abita-springs.html` (live: `/services-areas/abita-springs/`), built by
`scratch/build-area.py`, which reuses the service-page components. Copy comes
from a snapshot of the live page (`scratch/live-areas/abita-springs.html`)
through `live_parse.py`, verbatim. Order follows the client's brief:

1. **Hero:** the live H1, the first live sentence as the lede (carries the
   live homepage link). Breadcrumb: Home, Services Areas, Abita Springs.
2. **Overview:** the rest of the live intro and "Your Local Custom Car Shop
   in Abita Springs", closing on "Contact us today..." (the live contact link).
3. **Where We Work:** the homepage map **without Abita Springs**: its pin,
   row, marker and the last leg of road are removed, the other seven are
   renumbered 01-07, and each row and pin opens that town's page on the live
   site (new tab), so the map's "Tap a city to open its page" is true here.
   Heading and lede are the live "Serving Abita Springs and Surrounding Areas".
4. **Services:** the homepage board, all twelve rows, each "<Service> in
   Abita Springs". Five descriptions are the live page's own (paint, body
   kits, tuning, upholstery, audio); the rest are the homepage board's.
   Rows link where the live Abita page links them today: each service's
   general page (the four NEW services: their mockup pages).
   **TO DO (client request):** when the location+service pages exist, link
   each row to its own page. `ROW_LINKS` in `build-area.py` takes the file
   names; nothing else changes.
5. **Reviews:** the live Abita page shows none (a heading and a "View All
   Reviews" button only), so the plates carry three of the client's own
   testimonials from Northshore towns: Denise M. (Abita Springs), Monique R.
   (Covington), Ashley M. (Mandeville). Button to `testimonials.html`.
6. **All About Abita Springs, LA:** the live block, verbatim, under the
   client's four headings. The About paragraphs and Interesting Facts sit
   beside the photo (the About page's split); Things To Do fills the left
   column below, Notable Residents and Public Transportation the right, so
   the two columns end within about 40px of each other.
7. **Quote band:** the live "Start Your Custom Car Project in Abita Springs
   Today". Then the footer.

Title 59 characters, meta 139 (the live meta is 158). Structured data:
`Service` with `areaServed` Abita Springs. The menu's Services Areas >
Abita Springs item now opens this page on every page.

### Flags from the Abita Springs page

| Item | Flag |
|---|---|
| Notable Residents | The live copy names one person (John Preble, in its paragraph, kept). The list adds Wikipedia's four "Notable people" (Dick Hart, David Lohr, Bunny Matthews, Michael G. Strain). **Client must approve**; one is a serving state official. |
| Things To Do | Sources disagree on the Trailhead Museum building: a replica of the 1856 Asher Dry Goods store (live copy, kept) or the relocated bachelor quarters of the Longbranch Hotel. |
| Nearby Suburbs | Left out: it says Madisonville is southeast of Abita Springs; it is southwest. The map covers the neighboring towns. |
| Photo | Abita Springs Pavilion by GreaterPonce665, Wikimedia Commons, **CC BY-SA 4.0**. Hotlinked for the mockup; self-host it at launch and keep the credit line (author, license, source, "cropped"). No people in it, checked at full size. |
| Left out | "Why Abita Springs Drivers Choose..." (generic list), the per-service bullet lists and closing paragraphs (they belong on the location+service pages), the "Our Services" and "Other Areas" link lists (the board and map replace them). |
| Other seven towns | Same template: a snapshot in `scratch/live-areas/`, the town's name, its sections. The map code only handles a town at the END of a road, as Abita Springs is. The rest need their own road edit: St. Rose starts the main route, Slidell and Madisonville end a branch, and Covington, Mandeville, Metairie and Kenner sit mid-route, where the road has to be re-joined around the gap. |

## Known robustness fixes worth keeping

- **Photo captions stay on their photo on phones.** `.story-figure` turned
  `position:static` under 900px, so an overlaid caption escaped to the page
  (the Abita credit line landed 7,400px up, over another section). It is now
  `relative`. The Abita credit also moved under the photo: overlaid, it ran
  three lines across the busiest part of the picture on a phone.


- **Service boards never leave a hole.** A 5-row board sat beside a panel
  twice its height: a 416px gap under the list (Window Tint, client report,
  2026-09-22), and every 4-5 row board had it. Boards with seven rows or fewer
  now use `.bay-compact` (the spec moves under the list, the photograph fills
  the other column); longer boards stretch both columns to finish together.
  Each board also reserves its tallest title and description on load, so
  switching jobs never changes the panel height (rows used to shift up to
  23px under the cursor). Measured after: 0px gap on every board at 1856px
  and 1280px, 0-1px row movement, phones keep list, photo, spec order.

- **The phone menu works.** The burger button had no handler, so on screens
  up to 980px the menu could not be opened on any page. It now opens a solid
  panel under the header (desktop dropdown style, sub-menus in two columns,
  scrolls when tall) and closes on a link, the X, Escape, or widening past
  980px. Tested at 390px: all 26 links reachable.

- The bay-board script runs **once per `.bay`**, looking everything up inside
  its own board. It used page-wide lookups, which would have made the service
  page's two boards share photos and titles. Every board on every page was
  click-swept after the change: homepage 12, About 6, Services 12, Audio &
  Lighting 10 + 11.
- **Every page carries a link to the live homepage and the live contact page
  in its body** (client rule). `build-service.py` refuses to write a page
  missing either. The homepage mockup had neither until 2026-09-22; they now
  sit in its hero and FAQ heading, which no inner page copies.

- The bay-board script is scoped to `#bayList .bay-row`. Unscoped, it bound
  to the blog post's table-of-contents rows and would throw on hover.
- Post heroes use a heavier scrim. Over the red truck photo, the amber
  headline keyword measured 2.63:1 average and 1.44:1 worst pixel with the
  standard scrim; 5.39:1 and 3.17:1 with the post scrim.

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
