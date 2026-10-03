# Bộ prompt dựng UI web — 8 dự án

Mỗi prompt tự đủ thông tin (brand, design system, section, motion, responsive) để dán thẳng vào AI builder / Claude / Cursor. Prompt viết bằng tiếng Anh vì copy gốc và tên font/thuật ngữ design là tiếng Anh; phần "Ghi chú dùng" bằng tiếng Việt.

## Khối ràng buộc chung (dán kèm đầu mọi prompt)

```
Build a single-page marketing website as ONE self-contained HTML file (inline CSS + vanilla JS; GSAP/ScrollTrigger from cdnjs is allowed for scroll effects).
- Semantic HTML (header/nav/main/section/footer), one <h1>, real <details> for FAQ, alt text on every image.
- Mobile-first, fully responsive, fluid type with clamp(). No horizontal scroll at 360px.
- Design tokens as CSS variables on :root. Respect prefers-reduced-motion (disable sticky/pin/parallax, keep content visible).
- Progressive enhancement: add a `motion` class on <html> only if reduced-motion is off; content must be fully readable without JS.
- Images: Unsplash URLs with width/height attributes, loading="lazy" below the fold, fetchpriority="high" on the hero image.
- Sticky header that hides on scroll-down and returns on scroll-up; mobile menu as an accessible button (aria-expanded, aria-controls).
- Keep the layout minimal, strong hierarchy, no decorative clutter beyond what is specified.
```

---

## 1. INFRA — festival of thermal images

```
Design a festival website for "Infra", a 3-night festival of posters, thermal portraits, films and live sound (11–13 June 2027, Tram Depot Hall 7, Rotterdam). Concept: "images that run hot" — everything feels like a thermal-camera heat map.

DESIGN SYSTEM
- Palette: ink #09050f, night #1c1046, cool #06a7e1, pink #e8098a, hot #ef3f29, sun #fbee0c, paper #e8e6e0.
- Fonts: Hubot Sans (variable, width 75–125, weight 200–900) for display/text; Kalnia (wide didone, weight 200) for the big serif headline only.
- Display type: condensed (font-stretch 75%), weight ~820, uppercase, line-height .84. Hero wordmark stretched vertically with transform: scaleY(). Radius 0, 1px–1.5px rules, no shadows.
- Signature device: soft radial "heat halos" (cool→pink→hot gradient circles) behind photos and as card glows, plus a film-grain SVG noise overlay at ~.13–.3 opacity. Photos with data-map="heat" are recoloured via SVG feColorMatrix + feComponentTransfer table filters (heat: ink→night→pink→hot→sun→paper; cold: ink→night→cool→paper).
- Buttons: flat rectangles; hover fills with a bottom-up clip-path gradient (hot→sun). Links: underline grows left→right with a hot→sun gradient.

SECTIONS (in order)
1. Fixed header: brand chip "INFRA" (sun on ink), nav pill (Programme, Artists, Schedule, Passes, Visit), yellow "Get a pass" CTA. <1100px: full-screen hot-red menu with grain, huge condensed links.
2. Hero (pinned, ~215vh scroll): hot-red field with cool halo, small tracked-out line "A festival of images that run hot", an SVG ellipse "ring" with a cool dot orbiting it, giant "INFRA" wordmark, a heat-mapped cover portrait with a thin frame + tag "Cover — Ida Marsh", tags "11—13 June 2027" / "Tram Depot, Hall 7, Rotterdam" + paper button.
3. About/manifesto (paper bg): Didone headline "See the / warmth" (cool blue, second line right-aligned), centre heat-mapped portrait over a pink halo, left column of 3 big figures (3 nights / 38 artists from 14 countries / 140 works on the walls), right column lead paragraph + "Read the full manifesto" link.
4. Programme: 6 strand cards (Walls, Screens, Live, Portraits, Print fair, Talks) in an auto-fill grid; each card cycles bg colour (hot, night, cool, pink, sun, paper) with a radial glow corner, huge fitted condensed title, one-line description and a tag (e.g. "Nightly from 19:00").
5. Artists (night bg): 6 people in 3 columns, middle column offset down; portraits revealed with a scanning sun-yellow line that flips the image from cold to heat filter; name in condensed caps, role/city, day tag.
6. Schedule: horizontal scroll pinned section — intro panel + 3 day panels (Fri/Sat/Sun) with coloured gradient bg, parallax photo, list of time / title / location rows separated by 1.5px rules.
7. Archive collage (paper): 6 overlapping photos in a 12-col grid with slight parallax, frame outlines and caption tags.
8. Voices: two rows of quote cards on night bg, serif light quotes, glow corner, name + role tag; marquee when motion is on.
9. Call for artists (sun bg): vertical rotated giant title, lead, 2-col facts list (deadline, fee…), photo with SVG frame.
10. Passes: 3 pricing tiers, the featured tier in hot red; huge stretched price numerals in sun yellow; dot-bullet lists.
11. "Join" pinned 200vh: giant outlined word with a stretched trailing "smear" that follows scroll, two buttons.
12. FAQ (paper): sticky left heading, right accordion with 1.5px rules and a square +/× icon that fills sun on hover.
13. Visit (night): big sun-yellow address, 2-col info list, buttons, and an isometric concentric-ellipse "map" graphic with a photo + pin.
14. Footer: hot-red with cool halo, lead line, 2 link columns, giant sun wordmark scaled vertically, legal row.

MOTION
Lenis-style smooth scroll, letter-by-letter hero wordmark entrance, clip-path reveals on cards, parallax on collage/day photos, pinned horizontal schedule. All off under reduced-motion.
```

---

## 2. CRUMBO — small-batch bakery & baking school

```
Design a playful, tile-based website for "Crumbo", a small-batch bakery and baking school on Mill Lane (est. 1985; ovens on at 5 am; 36 bakes daily; 4.8★ from 1,200 neighbours).

DESIGN SYSTEM
- Palette: ground #e7e8de, paper #ffffff, sky #77c1e3, honey #ffb951, tangerine #fe8e49, leaf #02614a, ink #0a1317.
- Fonts: "Climate Crisis" (display, uppercase, line-height .9), "Google Sans" (text), "Playpen Sans" 700 (handwritten annotations, slightly rotated).
- Shape language: big rounded tiles (radius clamp 22–36px), 40% "blob" radius, circular product photos inside tinted blobs, round green "price stickers" rotated -8°, small 3-line spark icons, dashed hand-drawn arrows.
- Display words use a "fit" technique: font-size computed from container width / (character count × 1.1) via container queries so every word fills its tile.
- Buttons: pill; on hover a blob of honey rotates up from the bottom with overshoot easing (cubic-bezier(.3,1.45,.5,1)). Icon buttons do a jelly squash. Text links get an animated dashed underline.

SECTIONS
1. Floating header: pill brand (logo blob + CRUMBO), pill nav (Menu, School, Bread club, Visit, green "Order"), mobile sheet with coloured tone links.
2. Hero "bento board" (100svh, 4-col grid): large honey tile "BAKED TODAY!" with tilted croissant blob photo + "$3 from" sticker + two CTAs; tall white feature tile (Milk bun, $2.90); tangerine rating tile "(4.8) stars from 1,200 neighbours"; "Top picks" tile with 4 overlapping round thumbnails; sky "Classes" tile with cut-out portrait and handwritten "Join in!" arrow. Scroll: tiles stay pinned while a honey flood expands from centre to reveal the next section.
3. Story (honey bg): huge sentence with 3 inline pill photos (dough, loaves, coffee) rotated ±5°, handwritten signature "— Nell Hart, head baker", 3 fact tiles (1985 / 36 / 5 am).
4. Menu "On the counter": 6 items in an auto-fill grid, each a coloured tile (white/sky/tangerine/honey) with round photo on a spinning blob, sparkles and price sticker (Croissant $3.20, Cupcake $4, Berry tart $5.50, Cinnamon swirl $3.80, Country loaf $7, Macaron box $12).
5. Baking school: 2-col. Left sky card with big title, lead, arched photo at the bottom and handwritten "Join a class!"; right card listing 4 classes as rows (round honey date badge, title, "3 hours · 8 seats left", price, arrow button), a private-class strip and "Book a seat" + gift-card note.
6. Process "From dough to door": dashed green timeline with 4 coloured step tiles (5:00 Ovens on, 7:30 Counter's full, 9:00 Bikes out, 12:00 Sold out).
7. Gallery: pinned 100svh, 5 photos around a central text tile; scrolling shrinks/rearranges them.
8. Team: auto-fill cards with tilted blob behind each portrait, fitted names, role + quip.
9. Reviews: 4.8 rating tile + intro, marquee of quote cards with big green opening quote mark.
10. Bread club pricing: monthly/yearly switch (animated knob), 3 plan cards with round photo, check-icon features, a sticker badge on the featured plan.
11. FAQ: sticky sky card + rounded accordion (animated height via ::details-content, honey plus → sky ×).
12. Contact: big tangerine card (title, tilted photo, address/hours, pill buttons) + form card (name, email, message, submit → "sent" state).
13. Footer: green wordmark tile + 4 coloured info cells + legal row.

Keep copy warm, short and a little cheeky.
```

---

## 3. STRIA — contemporary dance house

```
Design a refined, editorial site for "Stria", a contemporary dance house: open classes, a touring company and two daylight studios for hire (Rotterdam harbour).

DESIGN SYSTEM
- Palette: bg #e1e2df, paper #eeeeeb, ink #191b1a, night #121615, teal #20b5a9 (text-safe teal-ink #0a6a63), red #c3402b.
- Fonts: Hubot Sans condensed (font-stretch 75%, weight 300) for all display; Instrument Sans for body. Display is light, tight, lowercase brand "stria".
- Signature device: FLUTED GLASS. Vertical ribbed panels (rib width ~22px desktop / 13px mobile) that refract the image behind them — built with repeated slices of the same image shifted/scaled per rib plus a highlight/shadow gradient and a bright top "rim". Used over the hero, the intro text panel, contact art, show/person photos, and as an assemble-on-scroll effect for the studio photo.
- Buttons: 2px radius, hover fills with vertical teal stripes (repeating gradient) wiping up; links get a hatched underline.

SECTIONS
1. Header: "stria" wordmark, nav (Classes, Season, Studios, Passes, Contact), "Book a class"; turns solid on scroll, switches to light text over dark sections.
2. Hero 100svh: pale radial bg, centre portrait of a dancer, huge red multiply-blended "stria" at the bottom, lower 42% covered by fluted glass with soft blur; H1 "Move until the edges blur" top-left, right column lead + "Book a first class" + "See the season". On scroll the glass edge moves up.
3. Intro: long statement in light display type; a fluted-glass pane sweeps across it and text fills from faint to ink as you scroll; 3 big teal figures (38 classes / 11 teachers / 2 studios).
4. Classes: table-like list of 6 (Contemporary Foundations, Floor & Release, Improvisation Lab, Partnering & Contact, Repertory, Young Movers) with name, level + duration, description, "Book" link; rules draw in, names "open" via ribbed mask, hover shows a teal rib pattern.
5. Season (night bg, pinned horizontal scroll): 5 tour shows (Salt Lines 14–16 Nov, The Weight of Air 5–6 Dec, Common Ground 22 Jan, Undertow 12–14 Feb, Open Night 20 Mar) as 4:5 photos with glass overlay, big teal dates, title, venue, "Tickets".
6. Studios for hire: headline + lead, full-width photo that assembles from ribs on scroll, two room specs (Studio One 160 m² €42/h, Studio Two 90 m² €28/h) as definition lists with giant rates, CTA row.
7. Team: 4 portraits, even columns offset down, glass reveal.
8. "Your first month": 4 steps (Week 1–4) on a horizontal line with hatch tick marks (vertical on mobile).
9. Passes: 3 plans, featured one teal with glass ribs.
10. Voices: sticky stacked cards (paper / teal / red) with large light quotes that dim as the next card covers them.
11. Gallery: 5 tall photos in staggered vertical offsets.
12. FAQ: sticky left title, accordion with clip-path reveal.
13. Contact: huge teal email link, definition list, and a blob-gradient art panel with a glass lower section.
14. Footer (night): statement line, nav + social, giant teal wordmark, base row.

Tone: calm, confident, a little wry.
```

---

## 4. LOUDCLOTH — small-batch clothing studio

```
Design a bright, image-led e-commerce brand site for "Loudcloth", a small-batch clothing studio in Porto: everyday pieces, tailoring and knitwear dyed in forty studio colours.

DESIGN SYSTEM
- Palette: white bg, ink #121212, dark #1c1c1c; five plates: orange #f37325, mint #a4d0a0, amber #f4ad3c, sky #74c1d7, pine #2c705c; highlighter #f4e2a0.
- Fonts: Instrument Sans (all UI, bold tight tracking -0.035em for headings); Playwrite US Trad 300 for handwritten signatures (over a highlighter swatch).
- Signature shape: photos with a "tab" notch in the top edge (folder-tab silhouette via clip-path: shape()), colour plates behind/under images; buttons are pills that fill from the bottom with amber on hover; links highlight with a growing marker swatch.

SECTIONS
1. Header: logo "Loudcloth", nav (Home, New In, Lookbook, Contact, About Us), search + bag icons, outlined "Sign In".
2. Hero (pinned ~240vh): centred H1 "Bold Colour For Every Kind Of Day"; left circular rotating text badge "Step inside the spring lookbook ·" with play icon; right avatar stack "+" for stylists; below, a 5-column collage of colour-plated model photos with staggered tops, floating gently, a rotating dotted burst icon, and an "Explore Collections" pill in the middle. On scroll the centre photo floods to a full-bleed editorial image with headline "Cut in runs of forty. Dyed in colours you won't forget." and lead.
3. Intro: left quote with handwritten signature "Mara K."; right feature link "38 Lifestyle pieces → Set Up Your Week With The New Everyday Edit" with marker hover.
4. Collections: sticky stacked "folder" cards with coloured tabs (Everyday Edit from $32, Studio Tailoring from $120, Knit Club from $68, Rain Ready from $145): tab slides across, left lead + giant count + shop button, right photo; earlier cards dim and scale as next arrives.
5. Colour range: "Forty colours. Five you'll reach for first." — 5 tall arch-offset plates (Flare, Moss, Sun, Pool, Pine) with photo, colour wash reveal, name + piece count.
6. Lookbook: huge centred title, 3-column drifting gallery with captions ("Pattern set, Flare fan — $186"), click opens a lightbox.
7. Process: photo + copy, then a horizontal progress line with dots that fill as you scroll (vertical on mobile).
8. Facts: soft-grey band with huge figures and animated horizontal bars.
9. Team: 3:4 tabbed portraits, name + role.
10. Voices: one large quote + marquee of review cards.
11. Pricing/membership: toggle (monthly/annual), 3 plans, the main plan dark with a tab label.
12. FAQ: sticky heading + accordion with draw-in rules and circular +/× buttons.
13. Contact: big headline, highlighted email, info grid, tab-shaped photo.
14. Footer (dark): CTA, link columns, giant fitted wordmark, legal row.

Tone: friendly, confident, colour-first.
```

---

## 5. SATURDAY STAMPEDE — free hill & trail running club

```
Design a loud, energetic site for "Saturday Stampede", a free hill and trail running club on Kestrel Common (every Saturday 07:00, north gate, every pace welcome).

DESIGN SYSTEM
- Palette: acid yellow #fdfe02, ink #1a0e07, paper #efece3, sky #3f5c7a, tan #e98a4f. Radius 0.
- Fonts: Hubot Sans 900 condensed (font-stretch 75%) for display; TikTok Sans (wide, variable) for text and tickers.
- Signature device: "FILL TYPE" — headlines stretched to fill the full container width AND a fixed row height using container-query font-size + scaleY, so every word becomes a solid block of letters. Also diamond bullets (rotated squares) and marquee tickers in wide uppercase.
- Buttons: hover fills with a rotated 45° square expanding from the centre. Links get a highlighter block rising behind the text.

SECTIONS
1. Acid-yellow header: brand, nav (Runs, The week, Crew, Membership, FAQ), "Join a run"; full-screen yellow mobile menu with huge condensed links.
2. Hero 100svh: full-bleed leaping runner photo (sky-tinted), ticker rows ("Free hill & trail running club · Every Saturday 07:00 · Kestrel Common, north gate · Every pace welcome"), stacked fill-type "SATURDAY / STAMPEDE", second ticker running the opposite direction; a diamond-shaped clip-path window of the photo grows on scroll; grain overlay.
3. About (acid yellow): ticker, large lead paragraph (line-by-line reveal), parallax photo, 3 facts (07:00 / Free / 5–21 km) with thick top rules, "See the runs".
4. Runs (ink bg, pinned horizontal scroll): intro panel "Pick your hill" + 5 poster cards (Hill run Sat 07:00, Repeats Tue 18:30, Night loop Thu 19:30, Long Sunday Sun 08:00, First 5K Sat 07:15) each with full-bleed photo, fill-type title, meta strip with diamond separators, blurb.
5. Values "How we run" (sky bg): 4 rubber-band fill words (Uphill, Nobody last, Any weather, Loud summits) each with a short rule sentence.
6. The week (paper): schedule rows — giant day, title + description, time, location, km; yellow sweep on hover/scroll-in.
7. Crew (ink): 4 portraits that open from a diamond clip-path, overlapping yellow condensed names, role + one-line joke.
8. Voices (acid): large feature quote (word-by-word reveal) + auto-scrolling marquee of ink quote cards.
9. "Your first Saturday": 4 steps climbing diagonally ("Turn up", "Say hi", "Pick a group", "Climb and cheer") joined by a drawn SVG line with diamond markers.
10. Gallery: bordered acid frame grid of 6 photos with 3D tilt entrance.
11. Season (sky bg): 3 big stats + an animated monthly bar chart (yellow bars).
12. Membership (paper): 3 plans with thick ink borders, main plan yellow, diamond bullets.
13. FAQ (acid): sticky title, condensed accordion with diamond icon that rotates.
14. Contact: full-bleed photo with gradient, H2, ink contact card (dl + buttons), giant fill-type word at the bottom.
15. Footer: ink, ticker, brand, blurb, nav, small print.

Copy voice: cheeky, inclusive, hills-on-purpose.
```

---

## 6. FARLAND EXPEDITIONS — slow overland journeys

```
Design an atmospheric, cinematic site for "Farland Expeditions", small-convoy overland trips in hand-rebuilt 4x4s across lava fields, salt pans and dune seas (yard at the plateau edge; convoys March–November).

DESIGN SYSTEM
- Palette: sand #e1c49c, sky-teal #89b3aa, sea #3b6a5f, moss #26352c, ink #181412, coral #e06244, paper = sand mixed 62% with white. All photos get a teal "grade" overlay; a full-page film grain overlay at ~.16 opacity (animated grain on the hero).
- Fonts: "Special Gothic" (condensed, weight 700, lowercase, line-height .8) for headings; Hubot Sans for text, with wide (font-stretch 125%, weight 300) used for captions, specs and body quotes.
- Signature device: a 4-point star icon used as logo, menu button, list bullets, route markers and FAQ icon (rotates 45° on hover). Spec lists as "Label - value" definition lists.
- Shape: radius 0; buttons coral with ink fill wiping up on hover.

SECTIONS
1. Header: star + "Farland Expeditions", nav (Expeditions, Fleet, Route, Guides, Prices, Contact), "Reserve a seat"; fixed star menu button opening a circular-reveal (clip-path) moss full-screen menu with big lowercase links + contact line.
2. Hero 100svh: 4 spec columns (Pace: Unhurried, Terrain: Sand & stone, Next convoy: 14 May, Seats left: Six of twelve); giant lowercase "farland" in sky-teal whose letters are knocked out to show the photo (background-clip:text with the dune image, parallax on scroll); a tall dune photo frame rises from the bottom (clip-path inset animates); centred caption paragraph.
3. Manifesto: spinning coral star, big wide-light centred statement ("never drive faster than the conversation" in bold), rule + signature "Ines & Tomas Varga, founders" and 3 spec facts.
4. Expeditions: sticky stacked poster cards (Lava fields 1,240 km/9 days €2,900; Salt pan 860 km/7 days €2,300; Dune sea 1,020 km/8 days €2,650; High pass 1,480 km/10 days €3,400) each with 4 specs, huge lowercase title, blurb, price, link and a full-width photo; cards tinted paper / moss / sky / coral and darken as the next one covers them.
5. Fleet (moss bg): 4 rigs (Shorty 1979, The wagon 1984, Mule 1991, Kettle 1982) as rows: name + type, 16:10 photo, specs (seats, range, sleeps, rebuilt year); top rule draws in.
6. Route "Nine days on the lava fields loop": pinned horizontal scroll with an SVG line drawing itself through 6 staggered stops (Day 1 The yard, Days 2–3 Stone towers, Day 4 Crater rim, Days 5–6 The long straight, Day 7 Fire night, Days 8–9 Down to the lake); stop photos unmask left-to-right and the star marker turns coral.
7. Seasons (sky bg): copy + 3 seasonal notes, and a monthly "good driving days" bar chart (moss bars, best month coral; becomes horizontal bars on mobile).
8. Guides: 4 portrait cards where giant lowercase names overlap the photo bottom.
9. Stories: big sky-coloured quote, marquee of quotes separated by top rules.
10. Gallery: 12-col collage with title block.
11. Prices: Shared / Private toggle that slides prices up/down (.swap), 3 plan cards with specs, coral main plan.
12. FAQ: sticky side + accordion with star icons.
13. Contact: spec list (email, phone, yard hours), a photo panel revealed via clip-path with a huge knocked-out word, lead + buttons.
14. Footer: sand, giant sea-coloured lowercase wordmark, nav row.

Tone: unhurried, literary, dry humour.
```

---

## 7. MODULO — School of Graphic Design

```
Design a bold, geometric site for "Modulo", an evening/weekend graphic design school (poster design, typography, layout, brand identity, screen & riso printing; 12 per group; print studio downstairs).

DESIGN SYSTEM
- Palette: paper #e7ecf0, ink #212445, amber #ffa802, sky #00a9ff, pink #ff73a5, light #fdfefd. "Four inks, no more."
- Fonts: Gabarito 600–900 (display, uppercase, line-height .9) and Instrument Sans (text).
- Signature device: GEOMETRIC TILES — square tiles containing a quarter-circle, half-circle, ring, dot or pill, each rotatable in 90° steps (--r). Used in the logo mark, the hero figure, list icons, gallery filler cells, card corners and footer ink strip. Images get one rounded corner (border-radius 0 big 0 0). Pill-shaped buttons/rows, buttons fill with a circle expanding from the bottom-left.
- "Echo" text effect: headlines repeated 2–4 times underneath in offset colours (pink, amber, light) to look like overprinted inks.

SECTIONS
1. Header: logo mark + "modulo", nav (Courses, Work, Tutors, Fees, FAQ), "Apply now", hamburger with 3 pill bars → dark full-screen menu.
2. Hero (sticky, dims as next section covers it): a 7×4 grid block in ink: left 4×3 figure of 9 quarter-circle tiles with a big sky tile carrying an amber "eye"; top-right amber block with 3 ink pills; sky H1 "Graphic design" (with echo) and giant "SCHOOL" along the bottom; lead paragraph + "Apply for autumn" + "See the courses"; tiles rotate on load/scroll.
3. About: big statement "We teach design the way a good poster works…", photo with a rounded top-right corner, 3 principles with tile icons (Shape first / A grid you can defend / Four inks, no more) separated by 3px rules.
4. Courses (amber bg): 5 pill-shaped accordion rows (Poster design €480, Typography €480, Layout & editorial €520, Brand identity €560, Screen & riso printing €290) — closed row: name + "12 weeks · Tue & Thu evenings" + circular +; open row: rounded-rect body with description, facts (Level, You leave with), price and "Book a place".
5. Manifesto (sky bg, pinned): giant "SIMPLE" whose echo copies fan out in pink/amber/light/ink as you scroll, plus a statement "Simple is not easy…".
6. Work "Posters from last term": asymmetric 6-column grid mixing photos with captions and solid-colour geometric tiles; cells slide in from l/r/up/down.
7. Process (pink bg): "From brief to print" sticky heading; right vertical rail with a four-quadrant disc that rolls down as you scroll; 4 steps (Weeks 1–2 Brief, 3–5 Sketch, 6–9 Grid & type, 10–12 Print) that light up when active.
8. Tutors (ink bg): 4 grayscale multiply-blended portraits on amber/sky/pink tiles with one curved corner, name + role.
9. Numbers: 3 big colour cards (12 / 900+ / 94%) + "Where graduates go next" animated pill bars (46%, 31%, 17%, 6%).
10. Voices (sky bg): sticky stacked quote cards (amber / pink / ink) each with a corner shape, big bold quotes.
11. Fees: 3 cards with a coloured geometric header band, big price, pink pill bullets, main card ink with amber button.
12. FAQ (amber bg): 3px ruled accordion with round ink +/× icon.
13. Contact (ink): giant "echo" word, info dl, Apply button, three-tile geometric figure.
14. Footer: paper, logo, address, nav, social, and a 4-colour ink strip.

Tone: precise, playful, teacherly.
```

---

## 8. VARGA — photographer portfolio (Louver preview)

```
Design a dark, editorial portfolio for photographer/director "Ines Varga" (Lisbon & New York, est. 2014, 212 commissions, available Oct 2026). This is a LAYOUT TRIAL: use CSS gradients as image placeholders (.p1–.p6) so real photos can be dropped in later.

DESIGN SYSTEM
- Palette: bg #0d0d0b, fg #efece4, red #ff3d17, muted rgba(239,236,228,.55).
- Fonts: Big Shoulders Display 800/900 (huge uppercase, line-height .88), Instrument Serif italic (accents, captions, inline keyword), Geist Mono 11px uppercase tracked (labels), Inter (body).
- Floating pills: logo pill "VARGA ines" (light bg, serif italic "ines"), centred blurred nav pill (Work, About, Contact), right availability pill with red dot "Available — Oct 2026". Section labels like "(01) — Intro" in mono.

SECTIONS
1. Hero carousel 100vh: 5 cross-fading slides (scale 1.06→1), auto-advance every 5s, drag/swipe to change, bottom bar: counter "01 / 05", serif italic title (e.g. "Solstice"), mono meta "Vogue Italia — Fashion — 2026", clickable thin progress bars.
2. Intro: giant uppercase headline "I make [pill image] pictures that *refuse* [pill image] to stand still. [pill]" — inline rounded gradient chips between words, "refuse" in red serif italic underlined; right column short paragraph + "About Ines ↗".
3. Work "WORK ⁰⁶" (mega type with red serif superscript) + "View all work ↗" button; 2-column grid of 6 cards (4:3, hover zoom 1.05, caption with serif italic title and mono client/year).
4. Reel: rounded section with gradient, huge "REEL ’26", white circular "Play ▶" button toggling to "Pause ❚❚", timecode "01:24 — Sound on".
5. Frames "in-betweens & outtakes": 5 slightly rotated images in a row (alternating portrait/landscape) that straighten on hover; below a clients strip (Maison Oré, KŌRA, nuit, OSTRA, Hale & Co, AUTODROME) in mixed typefaces at 55% opacity.
6. CTA (red bg with faint vertical grid lines): "Let's turn *the next frame.*", dark pill "Start a project ↗", email link, "Reply within 48h".
7. Footer: 4 columns (Index, Social, Contact, Based in), mega "VARGA" wordmark across the page width, legal row.

MOTION: IntersectionObserver fade-up reveals (opacity + translateY 28px), smooth anchor scroll, carousel as above. Fully responsive (grid → 1 col under 700px, hide availability pill).
```

---

## Ghi chú dùng
- Muốn kết quả sát bản gốc: dán **Khối ràng buộc chung** + 1 prompt dự án. Muốn tự do hơn: bỏ bớt phần MOTION.
- Những effect nặng (fluted glass của Stria, SVG heat filter của Infra, `clip-path: shape()` của Loudcloth, `::details-content` của Crumbo) chỉ chạy đẹp trên trình duyệt mới; nên yêu cầu fallback đơn giản.
- Mỗi prompt đều ép "fit text" bằng container query hoặc `scaleY` — nếu dùng Tailwind/React thì nên tách thành component `<FitText len="n">`.
- Nội dung (tên, giá, địa chỉ) là dữ liệu mẫu trong file gốc; thay bằng dữ liệu thật của bạn trước khi dùng.
