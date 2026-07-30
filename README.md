# PAC-MAPS

[![License: MIT](https://img.shields.io/github/license/ProfRino/pac-maps?label=License&color=yellow)](LICENSE)
[![Live demo](https://img.shields.io/badge/Live%20demo-profrino.github.io%2Fpac--maps-1f5b96?logo=github&logoColor=white)](https://profrino.github.io/pac-maps/)

PAC-MAPS is **Pac-Man on the real streets of the world**. Search any place on
Earth and its [OpenStreetMap](https://www.openstreetmap.org) road network
becomes the maze — dots along every street, power pellets in the corners, and
the four classic ghosts hunting you through real intersections. All in a
**single HTML file**: no build, no backend, no assets — just live map data
and browser-synthesized sound.

<img src="assets/demo.gif?v=2" alt="Demo — zooming from the real OpenStreetMap map into Manhattan, Paris, Barcelona and Rome, where the streets become a Pac-Man maze" width="100%">

---

## Features

Pure client-side — no installation, no backend, no account. One
self-contained HTML file you can host anywhere or open from disk.

* **Play anywhere on Earth.** A search box (Nominatim geocoding) flies you to
  any address or landmark; an *I'm Feeling Lucky* button teleports you to
  curated grid-friendly spots from Manhattan to Christchurch. Whatever roads
  are on screen become the maze.
* **Real street mazes.** The visible road network is fetched live from
  Overpass (with automatic mirror fallback to the OSM main API), cleaned of
  footpaths, motorways and driveways, clipped to the viewport, and compiled
  into a playable graph — dots spaced along every edge, power pellets in the
  corners, and screen-edge exits paired into wrap tunnels.
* **The four classic ghosts.** Blinky chases, Pinky ambushes ahead of you,
  Inky triangulates off Blinky, and Clyde loses his nerve up close — with
  authentic scatter/chase waves, frightened mode with flashing blue ghosts,
  eaten eyes that fly home to base, and staged releases from the ghost house.
* **Three difficulties.** Easy (2 slow ghosts, 5 lives, long power-ups) to
  Hard (4 fast ghosts, 3 lives, and a Blinky that pathfinds straight to you).
* **Arcade scoring.** Dots, pellets, ghost combos (200-400-800-1600), and the
  full fruit ladder — cherry to key — with a bonus item dropped on the
  streets each level. High score persists between sessions.
* **Synthesized audio.** Waka-waka, sirens that tighten as dots run out,
  frightened and eyes themes, death and level-up jingles — all generated with
  the Web Audio API. No audio files.
* **Plays everywhere.** Keyboard (arrows / WASD) on desktop; on phones and
  tablets a D-pad plus swipe steering, with a compact HUD. The map can be
  rotated to line the streets up with your thumb.
* **Level progression.** Clear the board and the same streets reload faster
  and meaner — speeds rise, power-ups shorten, and better fruit appears.

## How to play

You have **two equally simple ways** to run PAC-MAPS — both with no
installation, no account, and no server.

### Option 1 — Online

> **[Open it in your browser — profrino.github.io/pac-maps](https://profrino.github.io/pac-maps/)**

Just open the link in Chrome, Edge, Firefox, or Safari. That's it.

### Option 2 — Offline-ish, on your own computer

Download **[index.html](https://github.com/ProfRino/pac-maps/raw/main/index.html)**
— one single file — save it anywhere, then **double-click it**. The game opens
straight in your default browser. (It still needs an internet connection for
the map tiles and street data — the maze is the real world, after all.)

Then:

1. **Search** for a place you know — or hit **I'M FEELING LUCKY**.
2. Pick a **difficulty** and press **PLAY**.
3. Steer with the **arrow keys / WASD** (swipe or D-pad on touch screens).
   **P** pauses, **M** mutes, **B** toggles music.

Tip: dense, gridded downtowns make the best boards. If the PLAY button is
disabled, zoom in — the game wants a viewport under ~3.6 km at zoom 15+.

## For developers

The whole game is one file: [`index.html`](index.html) — styles, HUD, map
setup, street-graph compiler, game loop, ghost AI and synthesized audio, in
that order. Fork it, open it, edit it, refresh.

* **Street data:** Overpass QL query for `highway` ways in the current
  bounds, with mirror rotation and an OSM main-API fallback that recursively
  quarters the bbox when the server balks.
* **Graph compiler:** ways are clipped to the viewport, junctions detected by
  node reuse, edges built with per-edge dot placement, and clipped ends of
  the same street paired into Pac-Man wrap tunnels.
* **Movement:** entities travel along graph edges by arc length; steering
  picks the half-edge that best matches the desired direction, so controls
  feel like the arcade grid even on curved streets.

## Stack

[Leaflet](https://leafletjs.com) + [OpenStreetMap](https://www.openstreetmap.org)
(tiles, [Overpass API](https://overpass-api.de) and
[Nominatim](https://nominatim.org)). That's the whole stack. MIT-licensed.

## Citation

If you reference this work, please cite:

> Lovreglio, R. *PAC-MAPS*. Massey University.
> https://github.com/ProfRino/pac-maps

A machine-readable [`CITATION.cff`](CITATION.cff) is included in this
repository — GitHub renders it as a "Cite this repository" button in the
sidebar.

## License

[MIT](LICENSE) — © 2026 Rino Lovreglio. Map data ©
[OpenStreetMap](https://www.openstreetmap.org/copyright) contributors (ODbL);
map tiles by OpenStreetMap. PAC-MAPS is a fan tribute — Pac-Man is a
trademark of Bandai Namco Entertainment, which is not affiliated with this
project.

---
