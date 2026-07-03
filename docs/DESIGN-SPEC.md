# Handoff: PULPA — Landing Page

## Overview

This is a marketing landing page for **PULPA**, a cold-pressed juice brand. The design is a single, scroll-driven long page with a loud, chaotic, "loud life" personality — bold typography, hot magenta background, playful stickers, a rotating marquee, and product cards. It is meant to feel like a design-forward CPG brand (juice/soda) targeting a Gen Z / millennial audience — closer to a fashion drop than a supermarket product page.

The page contains the following sections, in order:

1. **Top nav** — brand mark, primary nav pills, "Shop the fridge" CTA
2. **Hero** — eyebrow tag, oversized 4-word headline with per-word color/rotation, subhead, dual CTAs, hero image with two rotating circular stickers
3. **Marquee band** — rotated-1.5° infinitely-scrolling wordmark strip (FRESH · LOUD · COLD-PRESSED · NO BS)
4. **Flavors grid** — 3 product cards ("Orange Riot", "Berry Brawl", "Green Scream") with number tag, image, name, price, description, add-to-cart button
5. **Manifesto** — large centered statement with a strikethrough word and a yellow-highlight word
6. **Press strip** — "As featured in" logos row on dark background
7. **Footer** — big brand mark + 3 link columns + copyright row

## About the Design Files

The files in this bundle — `index.html` and its two referenced JPEGs — are **design references created in HTML**. They are a prototype showing intended look and behavior, not production code to ship as-is.

The task is to **recreate this HTML design in the target codebase's existing environment** (React/Next.js, Vue/Nuxt, SvelteKit, Astro, Shopify Liquid, Webflow, etc.) using its established component patterns, styling system (CSS modules, Tailwind, styled-components, etc.), and image pipeline. If no environment exists yet, choose the most appropriate stack for a marketing site (Next.js + Tailwind and Astro + Tailwind are both good defaults for this kind of brand landing page) and implement the design there.

Do not ship the raw HTML file to production. Do reuse the exact design tokens, copy, and layout measurements listed below.

## Fidelity

**High-fidelity (hifi).** All colors, typography, spacing, radii, shadows, rotations, and copy are final and intentional. Recreate pixel-perfectly. The wonkiness (rotated cards, offset shadows, tilted marquee, per-word text colors) is the design — not sloppiness — and must be preserved.

## Screens / Views

This is a single long-scroll marketing page. All sections live on one route (`/`).

### 1. Top Nav

- **Layout:** 3-column CSS grid — `auto 1fr auto`. Padding `22px 32px`. Gap `24px`. Vertically centered.
- **Brand mark (left):**
  - Text "PULPA" + a decorative dot
  - Font: Bricolage Grotesque 800, `36px`, letter-spacing `-0.04em`, line-height 1
  - Color: `--ink` (#1a0d2e)
  - Rotated `-2deg` by default; on hover rotates to `+2deg` and scales to `1.05` (transition `0.3s`)
  - Dot: `10px × 10px` yellow (`--yellow` #ffd60a) circle with a 3px ink ring (`box-shadow: 0 0 0 3px var(--ink)`), positioned inline after "PULPA" with `margin-left: 4px` and `margin-top: 8px`
- **Nav links (center, `justify-self: center`):**
  - Flex row, `gap: 8px`, unstyled `<ul>`
  - Items: "Flavors", "Story", "Stockists", "Wholesale"
  - Pill style: `padding: 10px 18px`, background `--ink`, color `--cream` (#fff4d6), `border-radius: 99px`, weight 700, `14px`, letter-spacing `-0.01em`
  - Hover: background → `--yellow`, color → `--ink`, `translateY(-2px) rotate(-2deg)`, transition `0.3s`
  - Hidden below 780px
- **Buy CTA (right):** "Shop the fridge 🧃"
  - Pill: `padding: 14px 22px`, background `--ink`, color `--cream`, `border-radius: 99px`, weight 800, `15px`
  - Hover: background → `--yellow`, color → `--ink`, `rotate(-3deg) scale(1.05)`

### 2. Hero

- **Container:** `padding: 40px 32px 80px`, `text-align: center`, `position: relative`
- **Eyebrow tag:**
  - Copy: "Fresh batch — June 2026 drop"
  - Inline-flex pill, `padding: 8px 16px`, background `--ink`, color `--cream`, `border-radius: 99px`
  - Font: DM Mono 500, `12px`, letter-spacing `0.08em`, `text-transform: uppercase`
  - Preceded by an `8px × 8px` green (`--green` #0fdc7f) dot that blinks (`opacity: 1 → 0.3 → 1` on a 1.4s loop)
  - `margin-bottom: 32px`
- **Headline (`h1.hero-h`):**
  - Copy: "LOUD JUICE, / LOUD LIFE." (line break between "JUICE," and "LOUD")
  - Font: Bricolage Grotesque 800, `clamp(72px, 15vw, 220px)`, line-height `0.82`, letter-spacing `-0.05em`
  - `text-wrap: balance`, `margin-bottom: 40px`
  - Each word is wrapped in `<span class="wrd">` and animates on a 5s "wiggle" loop (`translateY(-12px) rotate(-1.5deg)` at 50%), with staggered `animation-delay` `0s / 0.4s / 0.8s / 1.2s`
  - **Per-word color:**
    - Word 1 ("LOUD") → `--ink`
    - Word 2 ("JUICE,") → fill `--yellow`, `-webkit-text-stroke: 3px var(--ink)` (outlined)
    - Word 3 ("LOUD") → `--ink`
    - Word 4 ("LIFE.") → `--blue` (#3d5cff)
- **Subhead paragraph:**
  - Copy: "Cold-pressed in small batches. Zero added sugar. 100% chaos in a bottle. Now in six flavors that taste like the volume knob broke at 11."
  - `font-size: 22px`, `line-height: 1.4`, `max-width: 580px`, centered, `margin-bottom: 36px`, weight 500
- **CTAs (inline-flex row, gap 14px, centered, wrap):**
  - Primary "Order a 6-pack →": `padding: 20px 32px`, background `--ink`, color `--cream`, `border-radius: 99px`, Bricolage 800 `18px`. Hover: bg → `--yellow`, color → `--ink`, `rotate(-2deg) scale(1.05)`.
  - Secondary "Read the story": `padding: 20px 28px`, transparent bg, `border: 3px solid var(--ink)`, color `--ink`, `border-radius: 99px`, weight 800 `18px`. Hover: fill ink, cream text, `rotate(2deg) scale(1.05)`.
- **Hero image block:**
  - Wrapper: `max-width: 1100px`, `margin: 60px auto 0`, `padding: 0 32px`, positioned relative
  - Image frame: `border-radius: 36px`, `border: 6px solid var(--ink)`, `box-shadow: 14px 14px 0 var(--ink)` (hard offset shadow, not blur), `aspect-ratio: 16/10`, background `assets/img/03-pulpa-splash.jpg` centered and covered
  - **Two circular stickers absolute-positioned over the frame:**
    - `.sticker.s-tl` — top-left, offset `top: -30px; left: -30px`, `140 × 140px`, yellow bg, ink text "COLD / PRESSED / ★ ★ ★", `font-size: 15px`, spins slowly (`14s linear infinite`, starts at `-12deg`)
    - `.sticker.s-br` — bottom-right, offset `bottom: -40px; right: -30px`, `160 × 160px`, green bg, "NEW / FLAVOR / ↓", `font-size: 20px`, spins reverse (`18s`)
    - Both: Bricolage 800, `border: 4px solid var(--ink)`, `border-radius: 50%`, grid-centered text
- **Reveal animation:** the hero image wrap fades in from `translateY(40px) rotate(-2deg)` with a springy easing `cubic-bezier(0.34, 1.56, 0.64, 1)` when it enters the viewport (IntersectionObserver, threshold 0.12)

### 3. Marquee Band

- **Wrapper:** `padding: 30px 0`, background `--ink`, color `--yellow`, top+bottom 6px ink borders, **rotated `-1.5°`**, `margin: 80px -40px` (bleeds past page edges)
- **Track:** flex row, `gap: 60px`, `white-space: nowrap`, translates from `0` to `-50%` over 30s linearly, infinite
- **Content:** the words "FRESH", "LOUD", "COLD-PRESSED", "NO BS" (repeated twice for seamless loop) separated by `32×32px` pink (`--pink`) circles
- **Type:** Bricolage 800, `78px`, letter-spacing `-0.03em`, line-height 1

### 4. Flavors Grid

- **Container:** `max-width: 1240px`, centered, `padding: 80px 32px`, id `flavors`
- **Section heading:** "Pick your *chaos.*"
  - Bricolage 800, `clamp(48px, 8vw, 110px)`, line-height 0.92, letter-spacing `-0.04em`, centered, `text-wrap: balance`, `margin-bottom: 60px`
  - The word "chaos." is inside `<em>` styled as `font-style: italic; color: var(--blue)`
- **Grid:** `grid-template-columns: repeat(3, 1fr)`, `gap: 28px`. On ≤780px collapses to single column with `gap: 18px`.
- **Card structure (each `.flavor`):**
  - Padding `32px`, `border: 4px solid var(--ink)`, `border-radius: 32px`, `box-shadow: 8px 8px 0 var(--ink)`
  - Hover: `translate(-4px, -4px)` and shadow grows to `14px 14px 0 var(--ink)`, transition `0.4s`
  - **Number label** (`.num`): absolute top-right (`top: 18px; right: 24px`), DM Mono 500, `13px`
  - **Visual** (image): square (`aspect-ratio: 1`), `border-radius: 22px`, `border: 3px solid var(--ink)`, `overflow: hidden`, `margin-bottom: 20px`. Inner `<img>` covers; on card hover image scales to `1.08` and rotates `2deg` over 0.6s.
  - **Product name** `<h3>`: Bricolage 800, `36px`, letter-spacing `-0.03em`, line-height 0.95 — displayed on two lines (e.g., "Orange<br>Riot")
  - **Price row**: flex justify-between baseline. Left: DM Mono `13px` size text ("500ml · 6-pack"). Right: `<b>` Bricolage 800, `28px`, letter-spacing `-0.02em` ("$24").
  - **Description** `<p>`: `15px`, line-height 1.45, color `#4a3760`, `margin-bottom: 20px`
  - **CTA button**: full-width, `padding: 14px`, ink bg, cream text, `border-radius: 99px`, Bricolage 800 `16px`. Hover: bg → `--pink`, `rotate(-2deg)`.
- **Per-card variations:**
  - `.f1` — background `#ffe9d4` (peach). Number "No. 01 / WAKE-UP CALL". Name "Orange Riot". Price "$24". Body: "Florida valencias, ginger, a dirty splash of lemon. Tastes like sunrise yelling." Image: `assets/img/03-pulpa-splash.jpg`.
  - `.f2` — background `#d8e7ff` (soft blue). **Rotated `1deg`** by default. Number "No. 02 / NEW DROP". Name "Berry Brawl". Price "$26". Body: "Wild blackberry, hibiscus, and that pomegranate that bites back. Magenta forever." Image: `assets/img/03-pulpa-bottle.jpg`.
  - `.f3` — background `#d4f7e2` (mint). Number "No. 03 / FAN FAVORITE". Name "Green Scream". Price "$24". Body: "Cucumber, mint, kale, lime. The 'I'm being healthy' one — but make it loud." **Visual is a placeholder** rather than a photo: a diagonal green→light-green gradient (`linear-gradient(135deg, var(--green), #7fffba)`) with a large `🥒` emoji (Bricolage 800, `80px`, ink color) centered. Its transform is reset (`transform: none`) so the visual doesn't inherit rotation. Replace with a real product photo when available.
- All three cards fade/slide-in via the `.reveal` observer.

### 5. Manifesto

- **Container:** `padding: 120px 32px`, `max-width: 900px`, centered, `text-align: center`, id `story`
- **Heading:**
  - Bricolage 800, `clamp(40px, 6vw, 80px)`, line-height 1, letter-spacing `-0.035em`, `text-wrap: balance`, `margin-bottom: 36px`
  - Copy (with inline formatting):
    - Plain: "We make juice for people who think "
    - `<span class="stk">` — "wellness" — rendered with `text-decoration: line-through`, color `#6a5278`, weight 500 (not 800), `font-style: italic`
    - Plain: " "
    - `<span class="hl">` — "vibes." — yellow (`--yellow`) rounded-rectangle highlight badge: `padding: 0 0.1em`, `border-radius: 18px`, `border: 3px solid var(--ink)`, rotated `-1deg`, inline-block
- **Body paragraph** (inline style used in source): `font-size: 20px`, line-height 1.5, `max-width: 680px`, centered, weight 500. Copy: "No detox cult. No 12-step routine. No nine-dollar bottle of celery water dressed up like a religion. Just real fruit, pressed hard, bottled fast, drunk loudly. That's it. That's the brand."

### 6. Press Strip

- **Container:** `padding: 60px 32px`, background `--ink`, color `--cream`, `border-radius: 48px 48px 0 0` (top corners only rounded), `margin-top: 60px`, centered text
- **Label:** "AS FEATURED IN" — DM Mono `12px`, letter-spacing `0.18em`, uppercase, color `--yellow`, `margin-bottom: 24px`
- **Logos row:** flex-wrap, `justify-content: center`, `gap: 48px`. Rendered as **type-only** (no actual logos): Bricolage 800, `24px`, opacity 0.7. Names: "Vogue", "Eater", "Hypebeast", "It's Nice That", "BoF", "Dazed". On hover each: opacity → 1, color → `--yellow`, `rotate(-2deg)`.

### 7. Footer

- **Container:** background `--ink`, color `--cream`, `padding: 60px 32px 30px`
- **Grid:** `grid-template-columns: 2fr 1fr 1fr 1fr`, `gap: 32px`, `max-width: 1240px`, centered. Collapses to `1fr 1fr` (with `padding: 0`) below 780px.
- **Column 1 (brand):**
  - Big wordmark: "PULPA" + dot. Bricolage 800, `80px` (mobile `54px`), line-height 0.85, letter-spacing `-0.04em`, color `--cream`. Dot is a `20 × 20px` yellow circle with `margin-left: 6px`.
  - Paragraph below: `14px`, opacity 0.7, line-height 1.5, `max-width: 300px`. Copy: "Cold-pressed in Brooklyn since 2024. Distributed in 240 fridges across NYC, LA & Mexico City."
- **Column 2 — "Shop":** links "All flavors", "6-packs", "Subscriptions", "Gift cards"
- **Column 3 — "Pulpa World":** links "About", "Stockists", "Wholesale", "Press"
- **Column 4 — "Talk to us":** "hello@drinkpulpa.com" (mailto), "@drinkpulpa", "TikTok", "FAQ"
- **Column headings** `<h4>`: color `--yellow`, DM Mono `12px`, letter-spacing `0.18em`, uppercase, `margin-bottom: 14px`
- **Link style:** block, `padding: 3px 0`, `font-size: 15px`, opacity 0.8. Hover: opacity 1, color `--yellow`.
- **Bottom row (`.copy-foot`):** max-width 1240, `margin: 40px auto 0`, `padding-top: 24px`, `border-top: 1px solid rgba(255,244,214,0.2)`, flex justify-between, DM Mono `12px`, opacity 0.6. Left: "© 2026 PULPA Inc. — Drink loud." Right: "Privacy · Terms · Recycle the glass please".

### Background decoration (fixed, all sections)

Three large fixed-position blurred circles float behind everything at `z-index: 0` (main content sits at `z-index: 1`). `pointer-events: none`, opacity 0.5, `filter: blur(40px)`, `border-radius: 50%`.

- `.s1` — `400 × 400px`, yellow, `top: -100px; right: -80px`, 18s float loop (`translate(-50px, 30px) scale(1.15)` at 50%)
- `.s2` — `300 × 300px`, blue, `bottom: 200px; left: -50px`, 14s (`translate(60px, -40px) scale(0.9)`)
- `.s3` — `250 × 250px`, green, `top: 50%; left: 50%`, 22s (`translate(-30%, 40%) scale(1.2)`)

## Interactions & Behavior

- **Scroll reveal**: elements with `.reveal` start at `opacity: 0; transform: translateY(40px) rotate(-2deg)` and animate to `opacity: 1; transform: none` when they cross the viewport (`IntersectionObserver`, `threshold: 0.12`). Transition `0.7s cubic-bezier(0.34, 1.56, 0.64, 1)` (springy). Currently applied to the hero image wrap, the section heading, and each flavor card.
- **Marquee**: infinite left scroll, 30s linear loop. Duplicate content ensures a seamless wrap at `-50%`.
- **Sticker spin**: `.sticker.s-tl` spins CW `0 → 348deg` in 14s; `.s-br` spins reverse in 18s. Do not spin a full 360° in a single keyframe or the rotate resets visibly — the design intentionally uses 348deg for a soft "correction". Preserve this.
- **Word wiggle**: staggered per-word vertical bounce + micro-rotate on the hero headline. Delays: 0s, 0.4s, 0.8s, 1.2s.
- **Blinking dot** on the eyebrow: 1.4s opacity blink.
- **Hover states**: every button, nav item, brand mark, and press logo has a rotate + scale/translate hover with a 0.3s transition. See individual sections above for values.
- **Card hover**: `translate(-4px, -4px)` shifts the card up-left while its shadow deepens from `8px` to `14px` offset — the "peel off the page" effect. Inner image scales 1.08 and rotates 2° over 0.6s.
- **Anchor navigation**: nav "Flavors" → `#flavors`, "Story" → `#story`. The "Order a 6-pack →" hero CTA also links to `#flavors`. Add smooth-scroll behavior in the target framework (`scroll-behavior: smooth` on `html` is fine; or use the router's scroll helpers). The source HTML does not enable it — please add it in production.
- **No JS beyond IntersectionObserver.** No modals, no cart drawer, no form submission logic implemented. "Add to fridge" and "Order a 6-pack" are visual only — wire them to the target codebase's commerce layer (Shopify, Stripe, Snipcart, etc.).

## State Management

The static prototype has no state. When implementing in a real app:

- **Cart**: "Add to fridge" and "Order a 6-pack" should push line items into a cart store (Zustand / Pinia / Redux / Shopify AJAX cart, whichever the codebase uses). Cart badge/drawer is out of scope for this design — coordinate with the checkout flow separately.
- **Flavors list**: hard-coded in the design (3 items). If the codebase already has a product CMS/Shopify catalog, drive the grid from that data instead of hard-coding. Map fields: `title`, `image`, `price`, `size`, `description`, `numberTag`, `numberLabel`, `cardBgColor`, `cardRotation`.
- **Newsletter / email capture**: not included in this design. If the brand wants one, ask before adding.

## Design Tokens

### Colors

| Token       | Hex        | Usage                                            |
| ----------- | ---------- | ------------------------------------------------ |
| `--pink`    | `#ff2e88`  | Page background; marquee dots                    |
| `--orange`  | `#ff7a1a`  | Declared but not used in current sections; reserved |
| `--yellow`  | `#ffd60a`  | Accent (stickers, highlight badge, footer accents, hover state) |
| `--blue`    | `#3d5cff`  | "LIFE." word; "chaos." em; bg shape              |
| `--green`   | `#0fdc7f`  | Green Scream card visual gradient start; eyebrow status dot; bg shape; bottom-right sticker |
| `--cream`   | `#fff4d6`  | Text on ink (buttons, footer, nav pills)         |
| `--ink`     | `#1a0d2e`  | Primary text; borders; dark section fills        |

Additional one-off colors:
- Flavor card backgrounds: `#ffe9d4` (peach), `#d8e7ff` (soft blue), `#d4f7e2` (mint)
- Green-Scream gradient stop 2: `#7fffba`
- Flavor description body copy: `#4a3760`
- Manifesto strikethrough text: `#6a5278`
- Footer copy row divider: `rgba(255, 244, 214, 0.2)`

### Typography

- **Display / UI heading**: Bricolage Grotesque (Google Fonts). Weights loaded: 400, 700, 800. Optical-size axis: 12–96.
- **Mono / label**: DM Mono (Google Fonts). Weights: 400, 500.
- **Fallback stack**: `'Bricolage Grotesque', sans-serif` for display; `'DM Mono', ui-monospace, monospace` for mono. Consider adding `system-ui, -apple-system, Segoe UI, Roboto` as an intermediate fallback in production.
- **Rendering tweaks**: `-webkit-font-smoothing: antialiased`, `text-rendering: optimizeLegibility` on `body`.

Type scale (as used):

| Role                 | Font              | Weight | Size                            | Line-height | Letter-spacing |
| -------------------- | ----------------- | ------ | ------------------------------- | ----------- | -------------- |
| Hero headline        | Bricolage Grotesque | 800  | `clamp(72px, 15vw, 220px)`      | 0.82        | -0.05em        |
| Section heading      | Bricolage Grotesque | 800  | `clamp(48px, 8vw, 110px)`       | 0.92        | -0.04em        |
| Manifesto heading    | Bricolage Grotesque | 800  | `clamp(40px, 6vw, 80px)`        | 1           | -0.035em       |
| Marquee text         | Bricolage Grotesque | 800  | 78px                            | 1           | -0.03em        |
| Footer brand         | Bricolage Grotesque | 800  | 80px (desktop) / 54px (mobile)  | 0.85        | -0.04em        |
| Product name (h3)    | Bricolage Grotesque | 800  | 36px                            | 0.95        | -0.03em        |
| Nav brand mark       | Bricolage Grotesque | 800  | 36px                            | 1           | -0.04em        |
| Price value          | Bricolage Grotesque | 800  | 28px                            | –           | -0.02em        |
| Primary button label | Bricolage Grotesque | 800  | 18px                            | –           | –              |
| Card button label    | Bricolage Grotesque | 800  | 16px                            | –           | –              |
| Nav pill link        | Bricolage Grotesque | 700  | 14px                            | –           | -0.01em        |
| Buy CTA              | Bricolage Grotesque | 800  | 15px                            | –           | –              |
| Hero subhead         | Bricolage Grotesque | 500  | 22px                            | 1.4         | –              |
| Manifesto body       | Bricolage Grotesque | 500  | 20px                            | 1.5         | –              |
| Flavor description   | Bricolage Grotesque | 500  | 15px                            | 1.45        | –              |
| Footer link          | Bricolage Grotesque | 500  | 15px                            | –           | –              |
| Footer body copy     | Bricolage Grotesque | 500  | 14px                            | 1.5         | –              |
| Press label / footer h4 | DM Mono          | 500  | 12px                            | –           | 0.18em (uppercase) |
| Eyebrow tag          | DM Mono           | 500   | 12px                            | –           | 0.08em (uppercase) |
| Card number label    | DM Mono           | 500   | 13px                            | –           | –              |
| Card size line       | DM Mono           | 500   | 13px                            | –           | –              |
| Copy-foot row        | DM Mono           | 400   | 12px                            | –           | –              |

### Spacing

The design does not use a strict token scale; the source uses ad-hoc values. Reasonable production scale to normalize to:

`4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 28, 32, 36, 40, 48, 60, 80, 120` (px)

Common paddings used:
- Section vertical: 60px, 80px, 120px
- Section horizontal: 18px (mobile) / 32px (desktop)
- Content max-widths: 580 (hero subhead), 680 (manifesto body), 900 (manifesto), 1100 (hero image), 1240 (flavors, footer)

### Border radius

- `18px` — highlight badge
- `22px` — flavor card visual
- `32px` — flavor card
- `36px` — hero image frame
- `48px 48px 0 0` — press section top
- `50%` — dots, stickers, background blobs
- `99px` — all pills / buttons / nav links

### Shadows

Hard/offset only — no blur:

- `8px 8px 0 var(--ink)` — flavor card resting
- `14px 14px 0 var(--ink)` — flavor card hover; hero image frame
- `0 0 0 3px var(--ink)` — small dot ring on brand marks

### Borders

- `3px solid var(--ink)` — outline button; card visual; highlight badge
- `4px solid var(--ink)` — flavor card; stickers
- `6px solid var(--ink)` — hero image frame; marquee top & bottom

### Motion tokens

- Hover transitions: `0.3s` default; card hover `0.4s`; inner card image `0.6s`; reveal `0.7s`
- Reveal easing: `cubic-bezier(0.34, 1.56, 0.64, 1)` (spring / back-out)
- Everything else: default `ease` unless noted
- Marquee: `30s linear infinite`
- Word wiggle: `5s ease-in-out infinite` per word, staggered 0.4s
- Sticker spin: 14s / 18s linear infinite (one reversed); rotates to `348deg`, not `360deg`
- Background blob floats: 14s / 18s / 22s `ease-in-out infinite`
- Eyebrow status dot blink: `1.4s infinite`

### Selection color

`::selection { background: currentColor; color: #fff; }` — highlight adopts the text color; selected text renders white.

## Responsive Behavior

One breakpoint in the source: **≤ 780px**.

- Nav collapses to 2 columns (brand + buy button); the middle nav list is hidden. **Add a mobile menu** in the target implementation (drawer, sheet, or a simple stacked list on tap) — the current design omits it.
- Hero padding tightens (`20px 18px 60px`); headline caps at `clamp(56px, 18vw, 120px)`.
- Marquee margin `-20px`; text drops to 48px.
- Flavors + manifesto + press sections drop to `padding: 60px 18px`.
- Flavor grid becomes a single column, gap 18px; card `.f2` rotation resets to 0.
- Footer grid becomes 2 × 2; brand wordmark shrinks to 54px.
- Stickers shrink: `.s-tl` to `90 × 90px, 11px`, offset `-15px`; `.s-br` to `100 × 100px, 13px`, offset `-15/-20px`.

Tablet range (781–1023px) is not explicitly styled; the design flexes reasonably. Verify at 768, 834, 1024, 1280, 1440, 1920.

## Accessibility Notes

The prototype does not include some things production should have:

- **Reduced motion**: wrap the wiggle, spin, marquee, blob-float, blink, and reveal animations in `@media (prefers-reduced-motion: reduce)` and disable them. The design remains legible without motion.
- **Contrast**: the primary combos (`--ink` on `--pink`, `--ink` on `--cream`, `--cream` on `--ink`, `--yellow` on `--ink`) all clear WCAG AA. The `#6a5278` strikethrough word on `--pink` background is decorative — keep it purely visual and ensure the meaningful word ("vibes.") has strong contrast.
- **Marquee**: add `aria-hidden="true"` on the marquee track since its content is decorative (same words twice). Or use `<div role="marquee">` sparingly — the safest bet is `aria-hidden` + a visually-hidden static equivalent if the words carry meaning.
- **Stickers**: absolute overlay text ("COLD PRESSED", "NEW FLAVOR"). Add `aria-hidden="true"` if the same info appears elsewhere, otherwise expose it in the DOM order.
- **Buttons vs links**: "Add to fridge" is a `<button>` today. Keep it a button (it triggers an action, not navigation). "Order a 6-pack →" is currently an `<a href="#flavors">` — that's correct if it scrolls; make sure the destination has `tabindex="-1"` focus handling or use `<button>` if it opens a cart.
- **Focus states**: none defined in the source. Add visible focus rings — a solid `3px solid var(--yellow)` outline offset by 3px works with the brand.
- **Alt text**: the flavor `<img>`s currently have empty `alt=""`. That's fine if they're decorative (product name is already in text); otherwise write descriptive alts like "Pulpa Orange Riot bottle, mid-splash".

## Assets

Bundled in `assets/img/`:

- `03-pulpa-splash.jpg` — hero image and Orange Riot card image. High-res juice-splash photo. ~2 MB — **compress + convert to WebP/AVIF** in production; also generate a `srcset` (768w, 1200w, 1800w) and lazy-load below-the-fold copies.
- `03-pulpa-bottle.jpg` — Berry Brawl card image. Bottle product shot on solid ground. ~1.9 MB — same treatment.

Missing / to-source:

- **Green Scream real photo** — currently a placeholder (mint gradient + 🥒 emoji). Get a real product shot before launch.
- **Real press logos** — the "As featured in" strip renders publication names as plain type. If Pulpa has actual placement, use real SVG logos; if they don't, either kill this section or keep it as-typed with copy the legal team is comfortable with.
- **Favicon / app icons** — not included.
- **Open Graph / Twitter card image** — not included. Recommend a 1200×630 image using the hero splash + big "PULPA" wordmark.
- **Fonts** — currently loaded from Google Fonts (`Bricolage Grotesque` + `DM Mono`). If the target site self-hosts fonts, download the woff2 subsets and update the `@font-face` declarations.

## Files

Copies of the prototype are included in this handoff folder for reference:

- `index.html` — the full standalone prototype (all CSS in `<style>`, one `<script>` for reveal observer)
- `assets/img/03-pulpa-splash.jpg` — hero + Orange Riot photo
- `assets/img/03-pulpa-bottle.jpg` — Berry Brawl photo

Open `index.html` in a browser to interact with the design (hover states, marquee, sticker spin, scroll reveals) before implementation.
