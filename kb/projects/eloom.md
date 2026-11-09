---
name: Eloom
description: "An agentic workspace for the electronics product lifecycle, where AI agents design boards and parts and the product's model holds the requirements, evidence and releases."
year: 2026
url: https://eloom.matricetechnologies.com
tags: &a1
  - electronics
  - kicad
  - agents
  - claude-code
  - nextjs
  - typescript
  - supabase
repos:
  - name: eloom
    role: author
    visibility: private
    description: Agentic electronics product lifecycle workspace; web app, served
      CLI and skill for agents, hosted KiCad worker.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags: *a1
  - name: aloud
    role: author
    visibility: private
    description: "Eloom's worked example: a clip-on voice pin whose microphone has
      no power unless its recording light is on."
    year: 2026
    last_active: 2026-10
    language: YAML
    archived: false
    tags:
      - electronics
      - product-design
      - safety
  - name: intercom
    role: author
    visibility: private
    description: USB-C desk box with one button and a light ring that tells you when
      your agents need you and lets you answer by voice.
    year: 2026
    last_active: 2026-10
    language: C
    archived: false
    tags:
      - electronics
      - kicad
      - firmware
      - rp2040
      - agents
  - name: hestia
    role: author
    visibility: private
    description: Battery-powered e-ink wall clock that shows where each family member
      is instead of the time, with its firmware and service.
    year: 2026
    last_active: 2026-10
    language: C
    archived: false
    tags:
      - electronics
      - kicad
      - firmware
      - esp32
      - privacy
  - name: home-battery
    role: author
    visibility: private
    description: Example product model of a 10 kWh LFP home battery with a 5 kW
      hybrid inverter, split into modules per subsystem.
    year: 2026
    last_active: 2026-10
    language: C
    archived: false
    tags:
      - electronics
      - product-model
      - energy
  - name: trail-light
    role: author
    visibility: private
    description: Example product model of a bicycle rear light that brightens when
      the bike slows down.
    year: 2026
    last_active: 2026-10
    language: YAML
    archived: false
    tags:
      - electronics
      - product-model
  - name: pocket-blinker
    role: author
    visibility: private
    description: Coin-cell LED blinker board designed and released by a fresh agent
      using only the Eloom CLI and its skill.
    year: 2026
    last_active: 2026-09
    language: KiCad
    archived: true
    tags:
      - electronics
      - kicad
      - agents
  - name: usb-power-indicator
    role: author
    visibility: private
    description: USB power indicator board designed by an agent through the Eloom
      CLI, checked with KiCad and released through Eloom.
    year: 2026
    last_active: 2026-09
    language: KiCad
    archived: true
    tags:
      - electronics
      - kicad
      - agents
---

Eloom is Matrice's workspace for the electronics product lifecycle, built on the bet that AI agents will do most of the work between a stated need and a product ready for production. Its central idea is that the product's model, not any one agent's memory, is the shared state: needs, requirements, design, rationale and evidence live as structured text in the product's git repository, are checked on every change like code, and are what every agent reads to start and changes to finish. People (the principal the product is made for, engineers, customers, regulators) work at the edges and approve what the method requires. Alexandre wrote about 1,400 commits between late September and mid-October 2026; a public instance runs at eloom.matricetechnologies.com.

## What

A signed-in user creates a product with a brief (a description and requirements), and their own agent (Claude Code or Codex) does the engineering through the `eloom` CLI and its skill: checking the product out into a local directory, searching real KiCad library parts, reading and writing schematics and boards against observed SHA-256 hashes, running ERC and DRC, exporting the BOM, attaching the check runs as evidence and asking for a release. Eloom keeps the record and the gate. Evidence is bound to the hash of the file it examined; any edit makes it stale, and a release is refused, with one reason per file, while a schematic or board is unverified, stale or failing.

Beyond the board, a product is made of parts (housing, bought parts, packaging, the user manual), each made by an agent in its own change and drawn by Eloom from its files: an assembly check tests placed parts for interference and clearance, and packaging and housing are built from a spec. The web workbench shows each product's model, files, evidence, BOM, manufacturing package, releases and sharing, with a Model explorer (canvas, outline, inspector, history). A written method, the compendium, describes the loop applied at every level (need, design, risk, evidence, baseline) and is served to both people and agents. Stations let a person run Claude Code sessions on their own machine and follow or steer them from the app. A `/demo` route runs a fictional sample workflow with no sign-in.

## Tech

Next.js 16 (App Router), React 19 and TypeScript, Tailwind 4 with shadcn and Base UI, Supabase for sign-in and workspaces, and PostgreSQL for products, evidence, reviews and jobs. The product model is a YAML format (`product.yaml`) with a JSON Schema, a checker, content fingerprints and generated views, written as plain ES modules that run unchanged in Node and in the browser. The agent CLI is built with Matrice's `served-tool` package and distributed by the app with its skill, device login and revocable API keys. A hosted worker with KiCad, ngspice, Chromium and OpenCascade runs on every push: rule checks, 3D bodies, BOM, fabrication package, simulations, printed documents and STEP conversion. The 3D views use three.js, graphs use React Flow and ELK, and record PDFs use PDFKit. An evals suite measures how well a fresh agent completes real design tasks with the tools, scoring each run with a deterministic checker. Deployed with Docker Compose on Coolify.

## Status

Version 0.2.0, last commit October 2026. The verified-release path uses real KiCad checks; the `/demo` workflow remains fictional and separate from real products. Private repository.

## aloud

Aloud is Eloom's worked example: a clip-on pin that records spoken notes when its button is pressed and syncs them to a companion web page (Web Bluetooth) for transcription. Its promise is that the microphone cannot get power unless the recording light is on. The repository holds the brief, the interview with the product owner, the model and a failure analysis started at the requirements step. Designed end to end with Eloom's method, September to October 2026.

## intercom

Intercom is a USB-C desk box with one button and a ring of light, plus a desktop app and `intercom` command line that agents call to ask, report or close a thread. The box lights up when an agent waits; holding the button records the spoken answer, and the microphone is powered only through the button's circuit. The repository holds the KiCad board with simulations, an RP2040 firmware (pico-sdk and TinyUSB, a USB audio device plus a HID button and LED ring, with a host-tested gate that only lets audio out during a hold), an enclosure checked by Eloom's assembly check, and the order for a first run of five assembled prototype boards. Active October 2026.

## hestia

Hestia is a battery-powered e-ink wall clock that shows where each family member is (Home, Work, School, On the way) instead of the time, specified by an outside product owner. The phone computes the zone locally and sends only its name; the service keeps no history, only each member's current state. The repository holds the KiCad design, the ESP32 firmware for the clock, the battery, display, enclosure, packaging and user manual parts, and a Node 24 service on PostgreSQL hosted in the EU. Designed in Eloom in October 2026.

## home-battery

A worked example model of a wall-mounted 10 kWh LFP home battery with a 5 kW single-phase hybrid inverter, split into modules per subsystem (pack, BMS, inverter, controller, enclosure) with safety goals and BMS firmware bound to its source tree. Values are illustrative. It started as a test fixture of Eloom's model checker.

## trail-light

A one-file example model of a bicycle rear light that brightens when the bike slows down, at its first prototype stage. Also a fixture of the model checker.

## pocket-blinker

A coin-cell LMC555 LED blinker board, designed from a brief by a fresh agent that had only the served `eloom` CLI and its skill, with no repository or example to copy. It passed ERC and DRC with KiCad 10 defaults and was released through Eloom. Archived.

## usb-power-indicator

The first board designed this way: a USB Micro-B connector, a 680 ohm resistor and a green LED on a 24 x 16 mm two-layer board, iterated by the agent to zero ERC and DRC violations and released. A script replays the whole loop against a running instance. Archived.
