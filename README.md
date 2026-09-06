# Endfield Design System

A dark, industrial UI design language — near-black grounds, hairline outlines
with two corners chamfered away, a diamond as the status marker, one safety-yellow
doing the structural work, and a magenta / cyan / yellow triband held back for a
single signature moment per screen. Restraint is the point.

It was rebuilt from the ground up as a study of the *Arknights: Endfield*
interface — the game's own HUD, not the louder promo site. Not affiliated with
or endorsed by Hypergryph.

## Contents

| file | what |
| --- | --- |
| `endfield.css` | the portable sheet — tokens, base, motif, components, utilities, in cascade layers |
| `styleguide.html` | the living reference — every token and component rendered, with the CSS inline. Open it in a browser |
| `RESEARCH.md` | how the system was derived: sources studied, the colour/type/motion decisions, and the v1.1 pattern → class map |
| `GAME-UI-NOTES.md` | the distilled UI observations the components are built from |

## Quick start

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Chakra+Petch:wght@400;500;600;700&family=Jost:ital,wght@0,400;0,500;1,400&family=JetBrains+Mono:wght@400;500;700&display=swap">
<style>@layer tokens, base, motif, components, utilities;</style>
<link rel="stylesheet" href="endfield.css">
<html data-theme="dark">   <!-- "light" = the DOC document surface · omit = follow the OS -->
```

- Build with tokens (`var(--ef-*)`), never literals.
- Panels, cards and buttons take `clip-path: var(--ef-chamfer)` — the top-right +
  bottom-left corner cut.
- Radius is `0` everywhere; the chamfer carries the "sharp" character.
- Everything no-ops under `prefers-reduced-motion`.

## Two surfaces

**HUD** (dark, default) is the screen interface. **DOC** (`data-theme="light"`)
is the document surface — light ground, the same marks, yellow demoted to a fill
or rail because it is illegible as text on white.

## License

Code and documentation are MIT (`LICENSE`). "Arknights: Endfield" and all related
marks belong to Hypergryph; this project only studies the interface and shares no
game assets.
