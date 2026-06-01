# life1 — Browser Life Simulations

Two self-contained, zero-dependency life-simulation toys that run entirely in the
browser. No build step, no frameworks, no install — just open an HTML file (or the
hosted GitHub Pages link) and play.

## 🌍 Pixel World — God Sandbox (`worldbox.html`)

A WorldBox-style pixel god-game on an `<canvas>`. Paint terrain, seed life, and watch
kingdoms rise, war, and fall — then rain down disasters.

**Live demo:** https://djkdjkm.github.io/life1/worldbox.html

### Features
- **Procedural island worlds** generated with value-noise + radial falloff (water, sand, grass, forest, rock, snow).
- **A living ecosystem** — rabbits graze grass, wolves hunt rabbits (and stragglers), all breeding, starving, and aging on their own.
- **Kingdoms & roles** — each colored kingdom contains three human jobs:
  - **Farmer** — forages grass, builds and grows villages.
  - **Hunter** — hunts game, fights wolves, raids rival kingdoms.
  - **Nomad** — roams and defends.
- **Emergent warfare** — different-colored kingdoms raid each other's people and raze enemy dwellings; territory is claimed and contested.
- **Buildings you can grow** — houses level up **hut → house → keep**, claiming more land and resisting raids. **Archer towers** loose homing arrows at wolves, raiders, and monsters.
- **Monsters** — roaming brutes that smash villages and devour villagers until fighters (or tower volleys) bring them down.
- **Disasters** — drag-paint **lava** that flows across the land and cools into rock (and even hardens new land over the sea), or strike with **lightning** and **meteors**.
- **A world bigger than the screen** — zoom (scroll) and pan (right/middle-drag) across a large map; smooth slow-motion via position interpolation; day/night cycle, particles, and an event ticker.

### Controls
| Action | Input |
| --- | --- |
| Paint / use a tool | Left-drag |
| Pan the camera | Right-drag or middle-drag |
| Zoom | Scroll wheel |
| Reframe whole map | **Reset view** button |
| Pick what to paint | Terrain / Spawn / Disaster palettes in the sidebar |

Tools include terrain brushes, spawn brushes (rabbit, wolf, **Colony** = a fresh
kingdom with all three roles), **Upgrade** (level up the nearest house), **Tower**,
**Monster**, **Erase**, and the disaster brushes.

## 🧬 Evolving Ecosystem (`index.html`)

A separate, simpler creature-evolution sandbox (plants, herbivores, carnivores).

**Live demo:** https://djkdjkm.github.io/life1/

## Running locally

Everything is a single static HTML file, so just open it:

```bash
# clone, then open in your browser
git clone https://github.com/DJKDJKM/life1.git
cd life1
# Windows
start worldbox.html
# macOS
open worldbox.html
# Linux
xdg-open worldbox.html
```

Or serve the folder if your browser blocks `file://` features:

```bash
python -m http.server 8000
# then visit http://localhost:8000/worldbox.html
```

## Tech notes

- Pure HTML + CSS + vanilla JavaScript, one file each — no dependencies, no bundler.
- Simulation runs on typed arrays (`Uint8Array` terrain, `Float32Array` grass/lava,
  `Uint16Array` territory) and is rendered to an offscreen `ImageData` buffer that's
  scaled with nearest-neighbor for crisp pixels.
- Agents (rabbits, wolves, humans, monsters) use a spatial hash for fast neighbor lookups.

## Hosting on GitHub Pages

This repo is ready for Pages: **Settings → Pages → Build from branch → `main` / root**.
Both games are then live at `https://djkdjkm.github.io/life1/` (Ecosystem) and
`https://djkdjkm.github.io/life1/worldbox.html` (Pixel World).
