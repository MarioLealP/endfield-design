# Endfield game UI — observations

Distilled from a 77-screen tour of the live game interface. The patterns below
are backported into `endfield.css` v1.1 — see `RESEARCH.md` for the pattern → class
map.

## Registers (the game uses 3+ distinct treatments)
- **Loading/title** — monochrome or pale, grunge + grain + contour + dot-matrix,
  the yellow structural BAND, inverted-triangle "Endfield Industries" emblem.
- **Combat HUD** — near-invisible: thin white outlines, transparent panels,
  faceted (hex/octagon) circular frames for minimap/portraits/skills.
- **Menu / Protos / operator screens** — DARK ground with **frosted pale-grey
  tiles** (rgba(235,235,235,.9)+blur), radial/curved layout, big **yellow angled
  slabs** as the primary info zone, rich badge system.

## Signature elements
- **Yellow angled slab / band** — a large safety-yellow parallelogram carrying
  the ENDFIELD INDUSTRIES wordmark watermark; the primary info/action zone on
  operator screens. Hazard-stripe + microtext texture. Torn/glitch edges on the
  title band.
- **Diamond ◇/◆** — ranks (`◆◆◆◆` Elite), notification badges are small tilted
  ORANGE squares. Green diamond chain = ascension track.
- **`+` registration crosshairs** with tiny code labels — scattered survey marks.
- **Faceted circular frames** — minimap, operator portraits, skill buttons are
  hex/octagon-cut, never plain circles.
- **Chevrons `》》》》》`** — promotion rank on operators. `‹‹‹ ›››` runs = nav.
- **Contour/topographic rings** around circular map viewports; contour lines
  printed onto the yellow band.
- **Segmented rank tracks** — white cell bars with milestone dividers
  (MAX RANK 3/6/9 · MASTERY), trefoil node at the end.
- **Key hints** — every interactive element tagged with its key in a tiny box
  (`F10`, `V`, `TAB`, `ESC`…).
- **Coordinate/depth telemetry** as tiny mono — e.g. `Depth: 0.0583±0.0054`.
- **Right-side detail drawer** — dark panel, hex-icon + name header, UPPERCASE
  section labels, cyan keyword highlights in body, right-aligned stat values
  (`| 179` with a pipe), a state button at the bottom (`Maxed`).
- Stat rows: icon + label + number; the operator's KEY stat gets a yellow box.
- Currency chips: `icon + number + [＋]` where `[＋]` sits in a hex frame.
- "-ENDFIELD-" rainbow/CMYK glitch strip as a decorative border on reward popups.

## Colour in the game
- Yellow `#FFE800`-ish (safety), structural.
- Cyan/teal = element (Cryo), skill frames, player/account identity, keyword hl.
- Magenta/purple = news/promo headers.
- Orange = notification badges. Red = timers (`19h`), danger.
- Green = ascension/elite track, confirm.

## Update (after g09–g13)
- **Skewed parallelogram tiles** (`skewX(~-8°)`) ARE core to menu lists — event
  cards, progress cards, list items. Stacked with slight overlap along a curve.
  (Earlier I deprioritised skew; it belongs.)
- **Yellow-filled tile** = active / claimable / current state (black text on it).
- Time badges = **red pill + clock icon**. `NEW` = yellow tab. Category = yellow pill.
- **Operator ID card** — yellow header tab `// ENDFIELD INDUSTRIES` + big black
  name + portrait + barcode/data strip. The key-art banner made physical.
- **Redacted-document aesthetic** — black censor bars over "classified" text on
  pale paper cards, with the inverted-triangle emblem + barcodes.
- **Red full-width disabled button** for can't-afford (`⊘ Insufficient tokens`).
  Cost row: `item icon + count + Owned: N` (N red when short).
- Weapon refinement = **dash-arrow chevron glyphs** `>-)-)-)`. Skill levels =
  **diagonal-slash segmented pip bars** + `MAX` badge. Stat deltas in blue.
- Gear slots = cards on a **vertical spine rail** with node dots; yellow
  bottom-border = equipped; purple circular frame = rarity.
- Detail-drawer body text: cyan keyword highlights + underlined terms + blue
  numeric values.
- Diegetic 3D dioramas (desk scenes, lowpoly paper-craft) for special/event art.

## Update: g52-g57 (Inventory, Intel, Medals, Etch Essence)
- **Inventory/Grid Views (g52, g57):** Standard layout is a dense square grid on the left, and a detail drawer/panel on the right. Selected item in the grid has a bright yellow border with the signature chamfered corners and a diamond indicator. 
- **Card Mosaics (g53, g54):** Intel archive uses a mix of large hero cards and smaller cards. Cards have thin borders, corner bracket accents, and cyan progress indicators. A "NEW" tag is a small yellow angled badge on the top right.
- **Hexagonal UI (g55):** Path of glory uses a honeycomb grid of hexagons. Not standard rectangles.
- **List with Side Nav (g56):** Medal album uses a DOC mode (light) style. Left side is a hierarchical navigation tree with active states in dark grey/yellow. Main content is a vertical list of wide cards with chamfered corners, subtle gradients, and right-aligned action/status badges (e.g., "Acquired").
- **Detail Drawer (g52, g57):** The right pane features right-aligned stats, horizontal bar graphs (slanted or segmented), and pill-shaped action buttons ("Etch").

## Update: g58-g64 (Tooltips, Missions, Maps, Web Overlays)
- **Tooltips (g58):** Context menus/tooltips use a mixed light/dark design. The header is often a solid yellow block with white text. The body is a light grey/white panel with dark text. The border is thin and sharp.
- **Mission List (g59):** Mission categories use colored tags (Yellow for "Recommended", Green for "Important"). List items have a thick colored left border indicating status. 
- **Map UI (g60, g61):** Map screens use dense cyan/blue accents on a dark topographical background. The 2D map uses thin white connection lines between nodes. The 3D map shows distinct elevation levels with a glowing yellow highlight for the selected sector.
- **Empty States (g63):** Survey center shows a very clean empty state using faint diagonal pinstripes (`#17181A` range) and a simple slashed circle icon `Ø` for "No surveys yet".
- **Web Overlays (g64):** In-game web tools (like Skport) use a distinct light theme (DOC mode). It heavily relies on rounded rectangles for tags, differing from the sharp chamfered in-game HUD, likely because it's a standard web container. The left navigation uses topographical map textures as a background for the buttons.

## Update: g65-g74 (Settings, Messages, Light Mode Data UI)
- **Settings (g66):** Uses long horizontal dropdowns and sliders. Segmented progress bars are used for hardware utilization (red for high load, green for moderate), adding a very tactical/diagnostic feel to the UI.
- **Mail & Messages (g67, g72):**
  - **Mail:** Two-pane dark UI. Read items dim. Critical information in the body text is highlighted in pure `--ef-yellow`.
  - **Chat:** Large, distinct pill-shaped white buttons for user reply choices at the bottom of the chat view.
- **Light Theme Data UI ("DOC Mode") (g70, g71):**
  - Production and power reports use a stark white background with a very subtle grey wireframe background pattern.
  - Data rows have a dark left-aligned block for the item name/icon, followed by dense area charts (using yellow/blue and orange/grey palettes) flowing rightwards.
  - Highlights a strong contrast between the dark combat/exploration UI and the light administrative/database UI.
- **Modals (g69, g73):**
  - System modals (like adjust level) often split horizontally: a dark top half containing the header and context, and a light bottom half containing the actionable choices.
  - In-world interactive panels (like Backup Power) use the light theme with high-visibility alert elements (yellow circles, red boxes with white text) and digital countdown timers.

## Update: g75-g77 (Database and Weapons)
- **Database Categories (g75):** Vertical scrolling list on a dark background on the left, with large icon representations of the categories (Threat Files, Weapon Files, etc.) in the center on a light background.
- **Database Tutorial (g76):** Video/image embed showing gameplay mechanics (e.g., Torrent Gun Tower) with descriptive text underneath. Uses the light "DOC Mode" aesthetic.
- **Inventory Weapons (g77):** Dense grid of weapon icons. Similar to the valuables stash, but with weapon-specific stats on the right-hand detail pane (Base ATK, Intellect Boost, etc.). Uses the standard dark theme.
