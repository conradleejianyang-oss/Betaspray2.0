
# Betaspray 2.0

Single–file, offline‑playable climber game built with Kaboom.js and TypeScript.

This repo contains the full source (Vite + TS) and a self‑contained HTML build you can open directly in any modern browser.

## Quick start (no build required)

1. Open the file below in Chrome, Firefox, Edge, or Safari:
   - `dist/BetasprayGame2.0.html`
2. Play immediately — no server or installation needed.

If your OS blocks local file scripts, right‑click the file, choose “Open With → Browser”, or drag it into an open browser window.

## Controls

- Left: `A` or `←`
- Right: `D` or `→`
- Start/Replay: `Space` or `Enter`
- Mouse/Touch: click or tap left/right half of the screen while playing
- Mobile: on‑screen Left / Right buttons appear during gameplay
- Pause: top‑right circular pause button
- Settings: gear button (day/night theme, help, close)

## Gameplay

Climb the wall by hitting the correct side indicated by red markers. The time bar drains continuously; every correct move refills it. Some segments allow either side. Picking the wrong side ends the run.

## Features

- Two scenes: Menu and Game with clean enter/exit
- Time bar HUD with danger color shift
- Parallax mountains with vertical nudge as you climb
- Procedural rock wall texture and lane logic
- Procedural background (sky, clouds, trees, shrubs, ground)
- Animated entities on the ground (Maltese dog, small deer)
- Polished UI: large pause, centered score/time bar, settings panel
- Day/Night theme toggle (persisted)
- Mobile‑friendly controls and layout
- All assets vector‑drawn at runtime (no external images required)

## Persistence

The game stores a couple of tiny values in `localStorage`:

- `climbtap_best`: highest score achieved
- `climbtap_theme`: UI theme (`"day"` or `"night"`)

No personal data is collected or transmitted.

## Building from source

Requirements: Node 18+ (or Bun), PNPM/NPM/Yarn.

```bash
# Install deps
npm install

# Dev server with HMR
npm run dev

# Production build -> dist/
npm run build
```

The build step outputs a standard Vite bundle to `dist/`. A curated, single‑file build is also included as `dist/BetasprayGame2.0.html` for easy sharing and offline play.

## Project structure

```
src/
  config.ts            # Constants and tuning knobs
  core/                # Loop, input, state, theme
  render/              # Background, mountains, rock wall, spray can
  systems/             # Climber, HUD, obstacles
  scenes/              # Menu and Game scenes
  entities/            # Dog, Deer
  main.ts              # Scene registration and boot
dist/                  # Build output + single-file HTML
```

## Troubleshooting

- “Panel misaligned” in READY screen: refresh — fixed in 2.0 by centering the panel background box.
- Nothing happens on key press: click once in the canvas to focus, then use `A/D` or arrow keys.
- On iOS Safari, first interaction may be required before audio/haptics can trigger.

## Tech notes

- Engine: [Kaboom.js](https://kaboomjs.com) (ESM import from `unpkg` in the single‑file build)
- Rendering: Canvas 2D (no WebGL requirement)
- Build tool: Vite + TypeScript
- Design: deterministic procedural art for background/wall; no image assets necessary

## License

Copyright © 2025. All rights reserved by the project owner. If you need a specific license, add it here.

## Changelog

- 2.0
  - Added single‑file offline build `BetasprayGame2.0.html`
  - Centered start prompt panel
  - Polished pause/settings UI and theme toggle
  - Added parallax mountains, ground wildlife, and refined wall texture
