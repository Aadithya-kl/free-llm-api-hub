# Owner decisions for brand H1 (2026-11-26)

- Direction: **H1 · Fingerprint + Receipts** (G + A).
- Tagline: **"We read the docs. You ship the code."** Use it as the home H1 and wherever the tagline constant is used (README, OG, GitHub description draft).
- Default theme: **light**, respecting `prefers-color-scheme` (dark when the system asks).
- Mascot: **no**. No Tick character anywhere.

## Open (2026-11-26)

- **Palette and aura/stamp shape are NOT final.** The owner asked for colour and shape variants of H1. Build everything parametrised: palette in tokens, aura shape and stamp shape as options/constants in `aura.mjs`. If PR 3 (palette) is ready before the variant is chosen, open it as a draft with the H1 palette marked provisional. Re-read this file before opening each PR; the chosen variant's tokens and parameters will be added here.
