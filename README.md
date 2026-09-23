# Big Easy Custom Cars &#8211; redesign mockup

Redesign mockup for [bigeasycustomcars.com](https://www.bigeasycustomcars.com/),
built on the design system carried over from the Big Easy Bathrooms and
TurnKey Pool redesigns.

**Live preview:** https://angel062388.github.io/bigeasycustomcars-redesign/

## What this is

Twenty-nine static pages. No build step, no dependencies. Open `index.html`
or serve the folder.

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
| `abita-springs.html`, `covington.html`, `madisonville.html`, `mandeville.html`, `slidell.html`, `metairie.html`, `kenner.html`, `st-rose.html` | **The eight city pages** (live: `/services-areas/<town>/`). Abita Springs is the model |
| `abita-springs-engine-tuning-performance.html` | **The model location+service page** (live: `/services-areas/<town>/<service>/`), on the turnkeypoolbuilders.com pattern |
| `hero-preview.html` | Earlier hero-only study, kept for reference |
| `assets/hero.mp4` | Hero video, 1280x720, 10s, 24fps, audio stripped, 3.4 MB |
| `assets/hero-poster.jpg` | Poster frame, 71 KB, used on mobile and reduced-motion |
| `assets/logo.png` | The client's own logo, unchanged |

### Every inner page is generated, not hand-written

Each one is produced by a script in `scratch/` (not committed) that slices the
header, trust strip, quote band and footer straight out of `index.html`, so the
pages cannot drift apart. **Edit `index.html`, then re-run all ten scripts:**

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
python scratch/build-loc-service.py
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

## The city pages: all eight service areas

`abita-springs.html`, `covington.html`, `madisonville.html`,
`mandeville.html`, `slidell.html`, `metairie.html`, `kenner.html`,
`st-rose.html` (the live site's own slugs, under `/services-areas/`), all
built by `scratch/build-area.py`, which reuses the service-page components.
Copy comes from snapshots of the live pages (`scratch/live-areas/<slug>.html`)
through `live_parse.py`, verbatim. The live city pages were written
separately and differ a lot (headings, order, one has no Notable Residents,
two have empty H1s), so each town has a short **plan** saying which live
section feeds which part. The menu's Services Areas items and the footer's
Service Areas list open these pages on every page.

Order follows the client's brief (map, services, reviews, All About,
footer), plus three parts that are not in the brief: the trust strip and
quote band every page carries, and an overview that keeps the live intro
copy and the live contact link. **Client to confirm the overview**; it can
move below the map or go.

1. **Hero:** the live H1 (Mandeville and Kenner have an empty H1 live: theirs
   is written from the page's own title), a live sentence naming Big Easy
   Custom Cars as the lede (the live homepage link). Breadcrumb: Home,
   Services Areas, town.
2. **Overview:** the rest of the live intro and the live "local shop" or
   "why choose us" section, closing on the live "Contact us today..."
   sentence (the live contact link; Saint Rose's page has none, so its
   "free consultation" line carries it).
3. **Where We Work:** the homepage map **without the page's own town**: its
   pin, row and marker go, the others are renumbered 01-07, and each row and
   pin opens that town's page on the live site. Roads: a town at the end of
   a road (Abita Springs, St. Rose, Slidell, Madisonville) takes that leg
   with it; where roads meet or run on (Covington, Mandeville, Metairie,
   Kenner) they stay. Heading and lede: the town's live "serving" section.
4. **Services:** the homepage board, all twelve rows, each "<Service> in
   <Town>". Descriptions: the town's live copy for the 5 to 8 services it
   covers (opening sentences, never retyped), the homepage board's for the
   rest. Rows link to each service's general page, as the live city pages
   do (the four NEW services: their mockup pages).
   **TO DO (client request):** when the location+service pages exist, link
   each row to its own page: `ROW_LINKS[<town>]` in `build-area.py`.
5. **Reviews:** the live city pages show none, so the plates carry three of
   the client's own testimonials from the nearest towns, the town's own
   first where there is one. Button to `testimonials.html`.
6. **All About <Town>, LA:** the live block under the client's four
   headings. About and Interesting Facts sit beside the photo (the About
   page's split); Things To Do, Notable Residents and Public Transportation
   flow through two balanced columns underneath (measured at 1280px and
   1856px: the columns end 2 to 118px apart; no heading or lead-in line is
   left at the foot of a column away from its list). A fact bullet that
   repeats the paragraph beside it is used once (Covington, Madisonville,
   Slidell).
7. **Quote band:** the town's live closing section. Then the footer, which
   on these pages carries the photo credit.

**Notable Residents are checked** against each person's own Wikipedia
article (2026-09-22), because this is where the first review found errors.
Rule used: live names are removed only when shown wrong; names added here
must be confirmed by the person's own article.

**On these pages the photo follows the text** (`.story-split.fit`): its
height matches the copy beside it, 320 to 640px, so short copy never leaves
a hole under the text (Covington's overview text ended 208px above a 4:5
photo). Phones: 16:10.

**Second review, fixed:** the sentence splitter cut "St. Tammany" and "St.
Charles" in two on the Madisonville hero, the Slidell map intro and the
Saint Rose map intro (now abbreviation-aware; the build fails if any
passage ends on "St."); Kenner's overview repeated "a complete system, not a
random mix of parts" a line before "a complete build, not a random
collection"; duplicate fact bullets removed; Saint Rose's one labelled fact
now plain like the rest.

### Errors on the LIVE city pages (tell the client; the live site shows them today)

| Page | Error | Here |
|---|---|---|
| Mandeville | Notable Residents calls **Moreese Bickham** "a professional football player". He was not: Wikipedia says he was a Mandeville resident sentenced to death in 1958 for killing two sheriff's deputies. | Dropped |
| Kenner | Notable Residents says **Donna Brazile** was "Born in Kenner in 1959". Wikipedia: born in New Orleans; her article never mentions Kenner. | Dropped |
| Abita Springs | "Nearby Suburbs" puts Madisonville southeast of Abita Springs; it is southwest. (Madisonville's own page puts Mandeville northwest of it; it is east.) | Nearby lists left out on every page |
| Mandeville, Kenner | The H1 is empty. | Written from each page's own title |
| Kenner | "Tinting, Detailing and Paint Protection" opens with a stray sentence about the build process. | Board uses its second paragraph |

### Other flags

| Page | Flag |
|---|---|
| Abita Springs | Notable Residents adds Mike Strain (serving state official) and Bunny Matthews (d. 2021); Dick Hart and David Lohr, on Wikipedia's town list, left out (no Abita residence in their articles). Trailhead Museum building: sources disagree (live copy kept). |
| Madisonville | No Notable Residents live: added Leah Chase, Cag Cagnolatti, Irv Stein, all born there per their own articles (Senator John Kennedy, on the town list, left out: his article never mentions Madisonville). "Pony Express Terminus" could not be confirmed; "largest marina in Louisiana" (Wikipedia: "in the region"). Live copy kept. Live title and cut-off meta description replaced. |
| Metairie | Live title reads "Custom Truck & SUV Builds Metairie": "in" added. Rhett Lewis's current NFL Network shows could not be confirmed. |
| Covington | Left out: an intro line that describes the page itself ("This Covington service-area page is crafted for..."). |
| Saint Rose | Live title 68 characters: written one used. The page says "Saint Rose" throughout, so the rows do; menu and map keep "St. Rose". Left out: a tagline and a button label the parser reads as text. |
| Covington | Heath B. Jones and Amanda Shaw are on Wikipedia's Covington list but their own articles never mention Covington (Shaw's says she is from Mandeville). Live copy, kept: client to confirm. A small bronze statue stands at the far right of the church photo; not visible at the sizes shown. |
| Slidell | John Besh: "Finalist on Iron Chef America" matches Wikipedia's Slidell list, not his own article (which mentions judging Iron Chef Showdown), and his article has a 2017 sexual-misconduct section. **Client's call whether to feature him.** |
| Kenner | Jon Batiste "attended schools in the Jefferson Parish area": his article names St. Augustine High and NOCCA, both in New Orleans. Live copy, kept. |
| Saint Rose | Margaret Taylor-Burroughs "(1917-2010)": her article gives 1915 (some sources 1917). "'Zweig' sounds like 'twig'": Zweig means twig. Live copy, kept. |
| Mandeville | Pat Brister, "Business professional with ties to the local community": she was St. Tammany Parish President (2012-2020). Live copy, kept. |
| Metairie | "Jefferson Parish Transit (JP Transit)": the system is Jefferson Transit (JeT), as Kenner's page says. Live copy, kept. |
| All | Live lines in the "not X, but Y" pattern are kept as the client's (e.g. "We build with you, not around you"); a copy pass could tighten them. |
| All | Written copy needs client approval: 3 titles, 2 meta descriptions, 2 H1s, the Madisonville and Abita Springs additions, labels. Overview, board and "All About" copy is live. |

### Photos (one per town, no people, credit in the footer, never under the photo)

Each shows a place the town's own copy names. Wikimedia Commons, license
and author checked, viewed at full size for people. Hotlinked for the
mockup; **self-host at launch and keep the credits**.

| Town | Photo | Author | License |
|---|---|---|---|
| Abita Springs | Pavilion and park arch | GreaterPonce665 | CC BY-SA 4.0 |
| Covington | Christ Episcopal Church | SouthernDiamond | CC BY-SA 4.0 |
| Madisonville | Town Hall Museum | Arelby3M | CC BY-SA 4.0 |
| Mandeville | Trailhead tower | Infrogmation of New Orleans | CC BY 3.0 |
| Slidell | Camp Salmen live oak | St. Tammany Parish Government | CC BY 2.0 |
| Metairie | Lafreniere Park lake | Jesse James | CC BY 2.0 |
| Kenner | Laketown lighthouse | Infrogmation of New Orleans | CC BY 3.0 |
| Saint Rose | Hale Boggs Memorial Bridge | Jonathan Sorrel | CC BY 2.0 |

## Location + service pages (the TurnKey pattern)

`<town>-<service>.html`, built by `scratch/build-loc-service.py`. At launch
these are `/services-areas/<town>/<service>/`, the pattern the client asked
us to copy from their other site, turnkeypoolbuilders.com.

**What that site does** (read 2026-09-23, structure only, no copy taken):

- `/service-areas/<city>/<service>/`: 104 such pages under 13 city pages.
- About 1,600 words each. Three sections are written for that service in
  that town and open on a local fact ("Metairie sits about three feet above
  sea level, and that single number shapes every custom pool built here").
- Everything after that is the same block the city page carries: All About
  <City>, the city's other services (each "<Service> in <City>", the current
  one left out), service areas, process, reviews, call to action.
- Every page links up to its city page and across to the city's other
  service pages. One H1, self canonical, no structured data.

**Ours**, in our own components. Model:
`abita-springs-engine-tuning-performance.html`

| Part | Where the words come from |
|---|---|
| Hero, crumb Home > Services Areas > Abita Springs > Engine Tuning | Written lede (carries the live homepage link) |
| Overview split | **Written**: three paragraphs on tuning for this town, from the town's own live facts (I-12 five miles south, the Causeway) and the service page's own claims (Ford, Chevy, GMC, Jeep, RAM; towing; trucks and SUVs only). Closes on the live "stop by Big Easy Custom Cars today" (live contact link) |
| What We Tune in Abita Springs | The live service page's own four tuning rows, verbatim |
| All About Abita Springs | The town page's block, unchanged |
| Our Other Services in Abita Springs | The homepage board minus Engine Tuning, 11 rows, each "<Service> in Abita Springs" |
| Where We Work | The coverage map, without Abita Springs |
| Reviews | Denise M. (Abita Springs), Darren S. (engine tuning), Monique R. (Covington) |
| FAQ | Four of the live service page's nine questions, verbatim |
| Quote band, footer | The service page's live closing copy; the town photo credit |

1,799 words, of which **169 are written**. Title 57, meta 126. `Service`
and `FAQPage` schema (TurnKey publishes none).

**Linking, both ways:** the town page's Engine Tuning row now opens this
page (`LOC_PAGES` in `build-area.py`, which fills `ROW_LINKS`), and this
page links up to the town page and across to the other eleven services.
Rows point at a service's general page until that town's page for it
exists, which is what the live town pages do today.

**To add a page:** write its plan in `build-loc-service.py` (lede, three
paragraphs, headings, meta, which FAQ questions), add the pair to
`LOC_PAGES` in `build-area.py`, run `build-loc-service.py` then
`build-area.py`.

### Flags

| Item | Flag |
|---|---|
| Written copy | Lede, three paragraphs, headings and meta are written for the mockup from the client's own claims and the town's live facts. **Client must approve.** |
| Repeated blocks | The All About block and the other-services board repeat the town page's, as TurnKey does on every service page of a city. About 1,000 of the 1,799 words are shared with other pages. |
| Scale | Eight towns x twelve services = 96 pages. Each one needs its own local angle in those three paragraphs, or the set reads as doorway pages: near-identical pages differing only by town name, which Google's spam policies name directly. The model's angle (highway and towing miles for a Northshore town) will not carry to all 96 by itself. |
| Services without a live FAQ | Nine of the twelve services have FAQs written for the mockup rather than live ones; a location+service page for those reuses that written FAQ, so it needs approving once per service, not once per page. |

## Known robustness fixes worth keeping

- **Navigation from inner pages.** Both logos and the footer "Home" link
  pointed at `#top`, the top of the SAME page, so from an inner page they
  never reached the homepage; the footer "Services" link pointed at a
  `#build` section the Services page does not have. All fixed in
  `index.html` (2026-09-22, second review). The footer's Service Areas list
  now carries all eight towns.

- **Photo captions stay on their photo on phones.** `.story-figure` turned
  `position:static` under 900px, so an overlaid caption escaped to the page
  (the Abita credit line landed 7,400px up, over another section). It is now
  `relative`. Photo credits have since left the photos altogether (client:
  no caption on the image): they sit in the footer's small print
  (`.foot-credit`) on the pages that need one.


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
