# My Emulator

A self-hosted browser emulator built on [EmulatorJS](https://emulatorjs.org/) (MIT licensed).

## Structure

```
.
├── index.html      # Page that boots the emulator
├── data/           # EmulatorJS engine (loader, player, cores config)
└── roms/           # Put your game file(s) here
```

## Setup

1. Drop your ROM file into `roms/`.
2. In `index.html`, update:
   - `EJS_core` — must match the system your ROM is for (`nes`, `snes9x`, `gba`, `gambatte` for GB/GBC, `melonds` for DS, `genesis_plus_gx`, etc. — full list in [EmulatorJS docs](https://emulatorjs.org/docs/options)).
   - `EJS_gameUrl` — path to your ROM, e.g. `roms/mygame.nds`.
   - `EJS_gameName` — display name.
3. Open `index.html` via a local server (not `file://` — browsers block module/worker loading over `file://`). Easiest options:
   - VS Code "Live Server" extension
   - `python3 -m http.server` from the repo root, then visit `http://localhost:8000`

## Cores

Only the `melonds` (DS) core config is currently bundled under `data/cores/reports/`. If you switch to a different system, EmulatorJS's loader will pull the matching core automatically from its CDN the first time it's needed — you don't need to vendor every core yourself unless you want a fully offline/self-contained build.

## Notes

- Only load ROMs you actually own/have the right to use.
- If GitHub Pages is your target host, this repo is already structured for it — just enable Pages on the `main` branch, root folder, once it's pushed.
