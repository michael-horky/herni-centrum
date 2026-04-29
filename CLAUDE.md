# Games — Car Infotainment for Daughter

## What this is

A static mini-arcade running on a laptop served over the car's WiFi hotspot.
Daughter connects on her phone browser — no install, no internet required.

**Serving:** `python3 -m http.server 8080` (or any static server) from this directory.
**Phone URL:** `http://<laptop-LAN-IP>:8080`

## Project structure

```
index.html          — Main game hub ("HERNÍ CENTRUM"), links to all games
cars/               — AUTA: lane-dodge car game
dino/               — DINO: endless runner, jump obstacles + pterodactyls
frog/               — ŽABKA: Frogger-style, get the frog to the pond
tictac/             — PIŠKVORKY: Tic-tac-toe vs AI (3 difficulties) or vs friend
oblekani/           — OBLÉKÁNÍ: Paper-doll dress-up game
  index.html        — Game UI
  PROMPTS.md        — AI image-generation prompts for all PNG layer assets
  layers/           — PNG assets organized by category
    hair-back/      — Grayscale hair behind head (CSS tint-able)
    hair-front/     — Grayscale hair in front of face (CSS tint-able)
    outfit/         — Full-color clothing layers
    shoes/          — Full-color footwear layers
```

## Language

All UI text is in **Czech**. Keep it that way.

## Design constraints

- **Mobile-first, touch-only** — no mouse, no keyboard. `viewport-fit=cover`, `user-select:none`, `touch-action:manipulation`.
- **Offline** — no CDN links, no external fetches. Everything self-contained.
- **Single-file games** — each game is one `index.html` with inline CSS+JS.
- Dark theme: background `#1a1a2e`, accent yellow `#ffd93d`.

## Oblékání — layered doll system

The dress-up game composites multiple PNG layers over an SVG base doll:

1. **SVG body** — base figure (skin, face, limbs) rendered via inline SVG
2. `hair-back` PNG — grayscale, rendered behind head; CSS `filter` applies color
3. `outfit` PNG — full-color clothing
4. `shoes` PNG — full-color footwear
5. SVG accessories (hats, crowns, clown nose) — drawn dynamically, not in PNGs
6. `hair-front` PNG — grayscale bangs/front strands, CSS `filter` applies color

All PNGs are **300×620 px**, transparent background. Hair layers are grayscale so a single CSS hue-rotate/sepia filter chain can recolor them for any hair color.

See `oblekani/PROMPTS.md` for the exact AI prompts used to generate each PNG asset.

## Adding a new game

1. Create `<gamename>/index.html` — self-contained, mobile-first, Czech UI.
2. Add a card to the main `index.html` grid following the existing pattern (icon, title, short description, arrow).
3. Pick a unique accent color for the card title.
