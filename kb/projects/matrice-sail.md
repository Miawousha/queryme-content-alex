---
name: Apparent (Matrice Sail)
description: "A VR-capable sailing game in the browser: a deterministic Rust physics simulation compiled to wasm, with a Three.js and WebXR view and multi-crew racing."
year: 2026
url: https://apparent.matricetechnologies.com
tags: &a1
  - rust
  - wasm
  - threejs
  - webxr
  - simulation
  - game
repos:
  - name: matrice-sail
    role: author
    visibility: private
    description: "Apparent: VR-capable sailing game; Rust simulation, wasm, Three.js
      and WebXR, with a WebSocket crew server."
    year: 2026
    last_active: 2026-11
    language: Rust
    archived: false
    tags: *a1
---

Apparent is a sailing game that runs in the browser and in VR headsets such as the Quest. The physics is an engine-agnostic Rust simulation and the browser app is a thin Three.js and WebXR view on top of it. The boats are an ILCA dinghy, the AP75 (an AC75 foiling monohull built to the AC75 Class Rule V3.01) sailed station by station by a crew, and the J-Class Ranger; a windsurfer exists in the simulation only. The default scenery is San Francisco Bay, with its land, wind and tide modelled. Several people can sail one boat together through a crew server, on a local network or at play.apparent.matricetechnologies.com. Alexandre wrote about 250 commits in its first week, in November 2026.

## What

The simulation is meant to be recognised as right by experienced sailors and foilers, not only to look plausible: behaviour comes from physics checked against reference data and scenarios with tolerances, not from per-boat tuning. On the AP75 each crew station (two helms, flying trimmer, sail trimmer, P5) can be taken by a person in VR or in a browser, or left to an emulated crew member. Racing lays a course to the wind with a start sequence, gates, boundaries and penalties under the America's Cup racing rules, against an AI opponent or another crew, with a tactician's display, race clock and results. Sound is procedural, including the wind at the sailor's ears.

## Tech

A Rust workspace with four crates: `sail-sim`, the pure simulation with no dependencies (wind, Gerstner waves, hull, foils, sails, crews, races), running at a fixed 120 Hz in `f64` so it is deterministic; `sail-wasm`, a wasm-bindgen wrapper that shares state through buffers in wasm memory; `sail-lab`, headless tools for polars, stability, feel scenarios, AC75 designs, races and log replay; and `sail-server`, the crew server, which runs one boat in real time and fills its stations over WebSocket. The web app uses Vite, TypeScript and Three.js with WebXR; the bay's built-in scenery (terrain, city, seabed) is stored in Git LFS, and Google's 3D tiles are an option. AC75 designs are TOML files. The crew server is deployed with Docker Compose and Caddy on a VPS, and the landing page is a static page published from the same repository.

## Status

Started in early November 2026 and in active development. A simulation roadmap tracks the work phase by phase (multibody core, lifting surfaces, wind and sea fields, the sailor as a physical body, new craft, world, design prediction, test bench, crew training). The match racing plan reached its fifth milestone in November 2026: a friend in your boat over the internet through the deployed crew server, then a friend in the rival boat. Private repository.
