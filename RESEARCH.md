# Endfield design — research digest (2026-08-30)

Ground-up study for a system meant to be indistinguishable from official.

## Sources examined
1. **Official site CSS** — `endfield.gryphline.com/en-us`, 9 `_next` bundles, 376 KB.
   Hypergryph's own code — most authoritative for the *web* expression.
2. **5 official key-art pieces** (operator-story banners, event key art) — the
   applied brand system.
3. **1 real in-game UI screenshot** — the "WHO ARE YOU?" identity-verify screen
   (character select). The clearest look at actual game HUD construction.
4. **`touying-endfield`** Typst theme (`leostudiooo/…`) — canonical presentation
   palette + the tri-stripe footer.
5. **`VBeatDead/ReEnd-Components`** — a mature community React/Tailwind Endfield
   design system (75+ components). Strong second opinion.
6. Community writeups on the in-game menus (Protos dashboard w/ tabs, AIC-mode
   facility hotbar, radial pause menu, minimap+quest HUD).

## Key correction vs. the earlier clockmost attempts
The **actual game HUD is restrained and sparse** — thin hairline outlines, heavy
negative space, white text, and typically **one yellow structural element per
screen**. Cyan/magenta are rare in-game. The promo website is louder (more
texture, more colour) because it is marketing. The earlier clockmost dashboard
put the tri-colour accent bar on *every card* — that is a print/brand motif,
over-applied. A faithful system leans minimal.

## Signature marks (priority order)
1. **Diamond ◇/◆** — the selection / focus / status marker. Hollow = available,
   filled = active; often nested inside a larger faint diamond frame. The
   loading spinner is a chamfered square that spins, not a circle.
2. **Corner brackets `⌐ ¬`** — 1.5–2px, framing any focus region, offset ~-1px
   outside the element. Usually the TL+BR diagonal pair.
3. **Hairline outlined containers** — buttons/panels are frequently just a 1px
   translucent outline + label, no fill. Fill = primary action only.
4. **Yellow as structure** — safety-yellow appears as a frame / rail / platform
   edge (an industrial structural element), rarely as button fill or body text.
5. **Chamfered corners** — `clip-path` cutting the **top-right + bottom-left**
   corners (~10–16px). THE panel/card/button shape. (`.clip-corner` in ReEnd.)
6. **Glitch-fragment echo** on large display headings — the heading duplicated
   above itself, offset, chopped into segments (seen on "WHO ARE YOU?").
7. **Chevron runs `‹‹‹‹  ››››`** — directional decoration on rails and nav.
8. **Tick marks + microtext** — tiny illegible technical text / tick sequences
   as edge texture.
9. **Tri-colour magenta→cyan→yellow** — a *brand signature*, used sparingly
   (footer mark, one loading bar, a section edge). Official gradient:
   `linear-gradient(180deg,#ff1aac 0,#ff1aac 1.5rem,#00ffa2 0,#00ffa2 3rem,#fffa00 0,rgba(255,250,0,0) 7rem)`.
10. **`//` prefix · `[ bracketed ]` subtitles · `+` tick accents · `▽` triangle
    emblem** — the key-art typographic vocabulary.
11. **Halftone / dot-matrix** fading off one edge — on category banners.
12. **Segmented data strips** — barcode-like dark blocks along an edge.

## Colour (final)
| token | value | notes |
|---|---|---|
| `--ef-yellow` | `#FFFA00` | official web CSS (56×). The one accent. |
| `--ef-yellow-hot` | `#FDFD1F` | hover / emission |
| `--ef-cyan` | `#00FFA2` | official web CSS. data / OK. |
| `--ef-magenta` | `#FF1AAC` | consensus across all 3 systems. alert. |
| `--ef-blue` | `#4A9FD4` | links only (muted) |
| `--ef-crimson` | `#D91E36` | editorial category banners only |
| `--ef-ground` | `#0F0F10` | near-black, faint cool cast |
| `--ef-surface` | `#17181A` | panels |
| `--ef-surface-2` | `#1E2024` | raised / nested (cool) |
| `--ef-well` | `#0A0A0B` | inset |
| `--ef-line` | `#33363C` | the blue-grey **steel** — borders, inactive. never pure grey. |
| `--ef-line-2` | `#4A4E56` | hover edge |
| `--ef-ink` | `#F0F0F2` | primary text (cool near-white) |
| `--ef-ink-2` | `#A8ABB2` | secondary |
| `--ef-ink-3` | `#6C6F76` | muted / captions |
| `--ef-ink-4` | `#44474D` | disabled / faint rules |

DOC (light) mode is real — used on official operator art on light grounds.
Ground `#F7F7F5`, surface `#FFFFFF`, steel `#C9CBD0`, ink `#17181A`. Yellow
becomes a fill/rail only (illegible as text on white).

Radius: **0** — fully sharp. The chamfer does the "sharp" character.

## Type
- **Display: Chakra Petch** (500/600/700) — chamfered letterforms echo the
  clip-corner motif; uppercase; wordmark = 700 + `letter-spacing:.3em`.
  Authentic upgrade if licensed: **Novecentosanswide**.
- **Body: Jost** (400/500) — geometric, Gilroy-adjacent. Authentic: **Gilroy**.
- **Data/mono: JetBrains Mono** (400/500/700) — every number, label, timestamp,
  `[SEC]` tag, code. Tabular.

## Motion
- Snap easing: `cubic-bezier(1, 0, .7, 1)` (official).
- Settle: `cubic-bezier(.16, 1, .3, 1)`.
- Durations .12 / .28 / .6 s.
- Named: `diamondSpin` (chamfered box, .8s linear), `glitch` (±1px, on trigger),
  `wipeIn` (clip-path L→R, .6s), `breathe` (opacity+scale, 2s), chevron-run.
- Everything no-ops under `prefers-reduced-motion`.

## Deliverables
- `styleguide.html` — the styleguide (source of truth).
- `endfield.css` — standalone token + component sheet.

## v1.1 — game backport (2026-08-30)

After v1.0 shipped, a 77-screen tour of the live game UI was analysed
screen-by-screen and the recurring patterns distilled into `GAME-UI-NOTES.md`.
v1.1 folds those patterns into the sheet — nothing in v1.0 changed, only
additions. The `gNN` codes below are the reference frames each pattern was
catalogued from:

| pattern | seen in | class |
|---|---|---|
| skewed parallelogram nav list | g13, g20, g22, g26, g46, g59, g74 | `.ef-skewnav` |
| un-sheared rail sidebar | g29, g56, g66, g76 | `.ef-railnav` |
| right-side detail drawer + pipe-aligned stat rows | g06, g09, g10, g12, g19, g52, g77 | `.ef-drawer` · `.ef-statrow` · `.ef-kw` · `.ef-delta` |
| state-driven task / quest row | g14, g20, g34, g42, g47 | `.ef-task[data-state]` |
| diagonal-slash pip bar ("//////// MAX") | g05, g09, g57, g77 | `.ef-pips` |
| blocked / deficit button ("⊘ Insufficient…") | g12, g14, g15, g57 | `.ef-btn--blocked` |
| radial 360° gauge | g23, g24, g25, g73 | `.ef-gauge` |
| vertical spine rail w/ diamond nodes | g10 | `.ef-spine` |
| operator ID card (yellow name tab) | g11, g49 | `.ef-idcard` |
| big yellow structural slab | g04, g05, g74 | `.ef-slab` |
| currency chip (icon · N · [＋] hex) | most menus | `.ef-currency` |
| item-rarity bottom-border spine | g52, g77 | `.ef-rarity` + `--ef-rarity-*` |
| split-tone modal (dark head / light body) | g69, g73 | `.ef-modal--split` |
| hybrid tooltip (yellow head · dark meta · DOC body) | g58 | `.ef-tipcard` |
| DOC-mode yield/usage report row | g70, g71 | `.ef-report` + `--ef-data-*` |
| tilted orange notification square | every menu | `.ef-notif` + `--ef-orange` |
| registration crosshair / four-corner frame | throughout | `.ef-reg` · `.ef-frame` |
| faceted (octagon) frame — never a plain circle | g03, g04, g11 | `.ef-facet` |
| CMYK glitch strip (louder than the triband) | g20, g26, g30 | `.ef-glitchstrip` + `--ef-glitchstrip` |
| key hint `[E]` `[F10]` | every interactive element | `.ef-key` |

Corrections carried in: the game also uses **orange** (notifications, power
consumption) and **lime-green** (`Important`, `Online`, confirm, ascension) as
real semantic colours — added as `--ef-orange` / `--ef-green` (both darkened for
DOC). Cyan stays "OK / data", magenta stays "attention", the triband stays
once-per-view.

**Deliberately not built:** the classified/redacted-document card (pure lore art,
no dashboard use), the honeycomb medal grid (g55), the 3D dioramas.
