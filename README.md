# NEON HORIZON — INFINITE DRIFT 🏎

CLAUDE FABLE 5 test

A 3D open-world driving game in **a single HTML file**. The world is procedurally
generated and truly infinite — pick a direction and drive forever.

## Play

Just open `index.html` in a browser (double-click it, or):

```sh
open index.html
```

It needs an internet connection the first time (three.js loads from a CDN).
Press any key to start.

## The world

- **Infinite terrain**, streamed in chunks around you, with a floating-origin
  system so precision never degrades no matter how far you drive.
- **A winding highway network** — noise-bent roads with dashed center lines and
  edge markings, flattened into the landscape, crossing lakes on causeways and
  threading mountain passes.
- **Three biomes** that blend into each other: green meadows and deep forest,
  crimson dunes with saguaros, and snowfields with pines, falling snow, and
  glowing ice crystals.
- **Mountains, lakes, and beaches** carved by ridged noise — crest a hill fast
  enough and you'll catch air.
- **A full day/night cycle**: synthwave sunsets, stars and moonlight, automatic
  headlights, and neon underglow after dark.

## The driving

- Arcade physics with proper drifting — hold **SPACE** while turning to slide,
  leaving skid marks and tire smoke. Long drifts bank score.
- **Nitro orbs** float along the roads; collect them and hit **SHIFT** for
  flame-spitting boost.
- Air time, drift chains, and orbs all feed your score (best is saved locally).
- Procedural engine, wind, and skid audio synthesized live with WebAudio.

## Controls

| Key | Action |
|---|---|
| WASD / Arrows | accelerate · brake/reverse · steer |
| SPACE | handbrake — hold to drift |
| SHIFT | nitro boost |
| C | cycle camera (chase / hood / cinematic) |
| R | rescue — teleport to the nearest road |
| M / P / H | mute · pause · hide HUD hints |

## Mobile

Works on phones and tablets: touch devices get on-screen controls automatically
(steer arrows bottom-left; gas/brake/drift/nitro bottom-right; camera, rescue,
sound, and pause along the top) plus a lighter rendering preset. Landscape is
recommended, and "Add to Home Screen" gives you fullscreen.

To reach it from a phone, serve the folder on your network:

```sh
python3 -m http.server 8000
# then open http://<your-mac-ip>:8000 on the phone
```

Append `?touch=1` to any URL to force the touch UI on desktop for testing.

## Seeds

Every load generates a fresh world. The seed is shown on the title screen —
add `?seed=12345` to the URL to revisit or share a world.

## Tech

No build step, no dependencies beyond three.js. Terrain height, biomes, and
road curvature all derive from deterministic hash-based value noise, so any
coordinate in the infinite world is reproducible from the seed. Chunks are
built incrementally within a per-frame time budget; scenery is merged into
single draw calls per chunk.
