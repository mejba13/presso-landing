# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is a **design-handoff bundle**, not an application. It contains one self-contained HTML prototype of a marketing landing page for **Presso** (a cold-pressed juice brand), plus a comprehensive spec describing how to rebuild it.

- `index.html` — the full standalone prototype: all CSS lives in one `<style>` block in `<head>`, and the only JS is a single `<script>` at the bottom implementing an `IntersectionObserver` scroll-reveal. There is no framework, bundler, package.json, or test suite.
- `docs/DESIGN-SPEC.md` — **the authoritative design spec.** It documents every section, design token, animation, responsive breakpoint, and accessibility gap in exhaustive detail. Treat it as the source of truth for the design; read it before making design changes.
- `README.md` — project overview, quick-start, and how the site was built.
- `assets/img/03-presso-splash.jpg`, `03-presso-bottle.jpg` — the two product photos referenced by `index.html` (large, ~2 MB each; uncompressed).

There is nothing to build or test. To preview, open `index.html` directly in a browser (`open index.html`).

## The core task

Per `docs/DESIGN-SPEC.md`, the intended workflow is to **recreate this HTML design inside a target codebase's existing environment** (React/Next.js, Vue, Astro, Shopify Liquid, etc.) using that codebase's component patterns, styling system, and image pipeline — **not** to ship the raw HTML file. This repo currently contains no such target environment; if one is introduced, the raw prototype becomes reference-only.

This is a **high-fidelity** design. The intentional "wonkiness" — rotated cards, hard offset shadows (no blur), tilted marquee, per-word headline colors, spinning stickers — **is the design and must be preserved pixel-for-pixel.** Colors, copy, spacing, and rotations in `docs/DESIGN-SPEC.md` are final.

## Design system (canonical values)

Colors are defined as CSS custom properties on `:root` in `index.html` and tabulated in `README.md`:

```
--pink #ff2e88 (page bg)   --orange #ff7a1a (declared, unused)   --yellow #ffd60a (accent)
--blue #3d5cff             --green #0fdc7f                        --cream #fff4d6 (text on ink)
--ink #1a0d2e (text/borders/dark fills)
```

- **Fonts** (Google Fonts): `Bricolage Grotesque` (weights 400/700/800) for display/UI; `DM Mono` (400/500) for labels/mono.
- **Shadows are hard offsets, never blurred**: `8px 8px 0 var(--ink)` resting, `14px 14px 0 var(--ink)` on hover / hero frame.
- **Pills/buttons** all use `border-radius: 99px`. Borders step `3px → 4px → 6px solid var(--ink)` by element weight.
- **One breakpoint only: ≤780px.** Nav collapses (middle links hidden — a mobile menu is a known TODO), flavor grid goes single-column, footer goes 2×2.

## Known production gaps (documented in README, not yet addressed)

When rebuilding, `README.md` explicitly flags these as work to do, not oversights to copy:
- No `prefers-reduced-motion` handling — wrap wiggle/spin/marquee/float/blink/reveal animations and disable them.
- No mobile nav menu (nav links simply hide below 780px).
- No focus states; add visible focus rings.
- Images are uncompressed JPEGs — convert to WebP/AVIF, add `srcset`, lazy-load.
- "Add to fridge" / "Order a 6-pack" buttons are visual-only — wire to the target codebase's commerce layer.
- The "Green Scream" flavor card uses a `🥒` emoji + gradient placeholder instead of a real photo.
- Sticker spin animations rotate to `348deg` (not `360deg`) on purpose — preserve this to avoid a visible reset snap.
