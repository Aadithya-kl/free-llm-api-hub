# Owner decisions for brand H1 (2026-11-26)

- Direction: **H1 · Fingerprint + Receipts** (G + A).
- Tagline: **"We read the docs. You ship the code."** Use it as the home H1 and wherever the tagline constant is used (README, OG, GitHub description draft).
- Default theme: **light**, respecting `prefers-color-scheme` (dark when the system asks).
- Mascot: **no**. No Tick character anywhere.

## Final variant (2026-11-26): H1-e · Cálida, with H1-b's pill stamp in tables

- **Palette, aura and main stamp: H1-e · Cálida.** Take the exact light and dark tokens, contrast values, modality hues and aura parameters from section "H1-e · Cálida" of `brand-drafts/08-variantes-h1.md`; visual reference `brand-drafts/prototipos/h1-e-calida.html`.
  - Aura = **radial bars**: 40 bars in a fan, one colour sector per modality, bar length derived from the slug. Ongoing tier: bars grow from the centre (sun). Trial: only an outer crown. Flags not stated: dashed outer circle.
  - Main stamp = **perforated ticket**: side notches, a cut line between the ✓ and the text, apricot fill. Use it on provider pages, OG images and badges.
- **Compact stamp in tables and lists: H1-b · Neon Night's minimalist pill** (flat, not rotated: status dot + "Verified · 24 Nov 2026 · N sources"), recoloured with the Cálida tokens. Shape spec from section "H1-b · Neon Night" of `brand-drafts/08-variantes-h1.md` and `brand-drafts/prototipos/h1-b-neon.html`. Cálida palette only; none of Neon's colours.
- Typography stays as in H1 (Roboto Flex + DM Mono) unless the H1-e section says otherwise.
- Keep everything parametrised (palette in tokens; aura and stamp shapes as options in `scripts/lib/aura.mjs`).

## Also include (2026-11-26)

- Fix in the hero restyle (PR 5): on phones the generated pages' hero breadcrumb, title and lede touch the screen edge. Cause: `site/styles.css` `.page-hero .wrap { padding: 34px 0 26px; }` overrides the side padding of `.wrap` (`padding: 0 24px`). Keep a side gutter of at least 16px. Issue #831 was closed in favour of this.
