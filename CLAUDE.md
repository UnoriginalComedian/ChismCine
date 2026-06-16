# Chism Cinematics — project context

Personal site for **Chism Cinematics**, a solo wedding / commercial / music-video film studio in Boyds, MD (Joel Chism). Started 2024, ~6 films delivered, no client ratings yet — lean into "new, hungry, direct access to the filmmaker" as a strength. Never invent stats or star ratings.

## Files
- `chism-immersive-site.html` — **the current site** (single self-contained file: HTML + CSS + JS, Three.js loaded from CDN for the 3D experiments). This is what to work on.
- `homepage-clean-gallery.html` — earlier scrolling "Clean Gallery" direction. Superseded; keep for reference only.
- `Chism Cine — Brand Guide.pdf` — the official brand guide (source of truth).

## Brand (from the brand guide — source of truth)
- **Wordmark**: full name spelled lowercase = `chism cinematics` ("chism" forest green, "cinematics" teal), with the ring-**C** as the "c". Outfit Medium 500. (Guide originally shortened it to "chism cine"; Joel wants the full word.)
- **The mark**: capital C of "chism" as a monoline ring (open C). The **center dot is orange = the record light**. On hover (header only, ~0.55s, reverse on release): aperture closes to a full lens ring, the orange dot **morphs along a path into a curved reflection glint** in the top-right of the glass, and "chism cinematics" tucks behind the C. Implemented as a JS path-tween whose duration/easing match the ring's CSS transition so they resolve as one motion.
- **Colors**: Forest `#163A29` (primary/headlines/mark), Teal `#1C8C7D` (secondary/links/"cinematics"), Orange `#E8772E` (**aperture/record + tiny highlights ONLY — never large areas, never recolor the dot**), Off-white `#F7F7F4` (surface), Ink `#11140F` (dark surfaces).
- **Type**: Outfit (display/UI), Newsreader (serif body/captions, has italic), IBM Plex Mono (micro-labels/data/timecodes/ƒ-stops).
- Medium film **grain** over everything; subtle vignette.

## Structure & interactions
- **Home** = airy gateway. A **focus-pull menu** of the four work categories: Weddings / Commercial / Music Videos / Short Films. All readable at rest; hovering one racks the *others* out of focus (blur + chromatic-aberration color fringe), fills the **whole screen with that category's video**, and shows a mono `ƒ1.4 · 35mm ● FOCUS — …` readout. Smooth glide, no shake.
- Clicking a category = **SHUTTER transition** (letterbox black bars close together to black, then part to reveal). Going **back to focus** and navigating to info pages = slow (~1.3s) warm **double light-leak** that fully whites out to hide the page swap.
- **Top nav**: About · Work with me · Collab · Contact. Back button ("← Focus") lives in the top bar beside the logo.
- **Sections**: category screens (full-bleed still bg + film list; hovering a film swaps the bg) · **About** (split layout, Joel's real portrait `https://chismcine.com/assets/images/image01.jpg`) · **Work with me** = warm CLIENT page (personality + 3-step Say hello / The day / Your film) · **Collab** = nerdy **Sony-style camera spec menu** for fellow creators · **Contact**.
- **Collab menu**: a contained, centered "device screen" card with a title above it. Left icon rail (thin square Sony-colored tabs, selected = brighter) → numbered middle list whose **number boxes** take the category's color (CSS vars `--cat` / `--catink`; light cats use dark ink) but whose **selected/highlighted item bar is ALWAYS Sony red `#CC3A2C`** (white text + inverted white number box), like the real FX30 screen → right column is a **black Sony-style sub-options list** (each middle row carries a `sub:[...]` array of short spec lines, rendered with `▸` markers, filling the column). (The 360 spinner is currently parked — not shown in the detail; the `spin`/`setupSpinner` code remains for re-homing it later, e.g. open-on-click.) The whole menu is composited inside an actual FX30 photo (`photos/fx30/fx30-cropped.png`): `.fx30-cam` holds the image, `.fx30-lcd` is the transparent-screen mask (position/size in % — the dial to fit the screen), and JS scales `.menu-os` (base width 760) to fill the LCD. Click + arrow-key navigation (▲▼ items, ◀▶ tabs). Rail icons and list rows share one row-height grid so they line up.
- **360 viewer** lives in the Collab detail panel. Architecture is angle-driven: each row can carry a `frames:[urls]` array → it becomes an **image-sequence 360** (idx = angle→frame). Currently a placeholder spinning CSS-3D cube. A from-scratch Three.js FX30 model was tried but looked too rough — **plan is reference photos** (turntable image sequences), not generated geometry.

## Contact button
Floating **C-lens contact button** bottom-right on every page (`.contact` / `#contactFab`): the green C-lens circle morphs open into an off-white card with an async message form + a "Text me" button (`sms:2403974170`). The form posts to **Web3Forms** via `fetch` — replace `WEB3FORMS_KEY='YOUR_WEB3FORMS_ACCESS_KEY'` in the inline script with Joel's free key from web3forms.com (the key must be generated with **joel@chismcine.com** — Web3Forms routes to the key-owner's email, not a field in the code). Contact email throughout the site = joel@chismcine.com. Until the key is added it runs in "demo mode" (shows the success state without actually sending). No live chat by design (solo studio).

## Open TODOs
- Home-hover **video**: Weddings now uses Joel's real clip `videos/hero-preview.mp4` (+ poster `videos/hero-preview.jpg`, 1280×720 H.264, ~15s, muted via the element). Commercial / Music Videos / Short Films have `video:''` (show their gradient) until Joel exports their own short muted loops into `videos/` — then just set each `video:`/`poster:` path in the home `meta` array. Video files live in `videos/` next to the HTML; open the page from the project folder so the relative paths resolve.
- **Instagram** link is a placeholder (`https://www.instagram.com/`) — needs the real handle.
- **360 photo sequences** per kit item: shoot ~24–36 turntable frames (locked tripod, constant light/exposure/WB, clean bg), then set `frames:[...]` on the matching Collab row.
- Confirm the **Collab spec values** (FX30 Super 35, 4K 10-bit, lenses, etc. are reasonable placeholders).
- Real **Commercial** and **Music Video** films (only the two wedding films are real, via YouTube thumbnails).
- Consider splitting the single HTML into separate `index.html` + `css/` + `js/` files.
- **Mobile**: focus-pull is hover-driven (desktop-first) — add a tap/scroll fallback for touch.

## Working style
Joel is a videographer, strong with Apple/tech, not a coder — he's visual and iterates fast on look and feel. Show, don't just describe. Keep responses concise.
