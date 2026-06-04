---
name: Dev tooling & experiments
year: 2026
tags:
  - tooling
repos:
  - name: blueprint-creator
    url: https://github.com/ION-Altergo/blueprint-creator
    role: contributor
    visibility: private
    description: Interactive Rich-based CLI for browsing, extending, and converting
      Altergo blueprints via the SDK.
    year: 2026
    last_active: 2026-01
    language: Python
    archived: false
    tags:
      - python
      - tooling
  - name: blueprints_importer
    url: https://github.com/ION-Altergo/blueprints_importer
    role: contributor
    visibility: private
    description: Altergo platform app that bulk-generates blueprints from an Excel
      workbook or dataset IDs.
    year: 2025
    last_active: 2025-10
    language: Python
    archived: false
    tags:
      - python
      - tooling
  - name: simple-app
    url: https://github.com/ION-Altergo/simple-app
    role: contributor
    visibility: private
    description: Empty starter scaffold for an Altergo platform app — entrypoint,
      settings, no logic.
    year: 2024
    last_active: 2024-10
    language: Python
    archived: false
    tags:
      - python
      - demo
  - name: openclaw-config
    role: author
    visibility: private
    description: Versioned config and state store for a personal long-running agent
      runtime (OpenClaw).
    year: 2026
    last_active: 2026-02
    language: Shell
    archived: false
    tags:
      - agent
      - shell
      - infra
  - name: opus-infra
    role: author
    visibility: private
    description: Backing infra for OPUS — manuscripts as typed, claim-level objects
      with AI + human peer review.
    year: 2026
    last_active: 2026-05
    language: TypeScript
    archived: false
    tags:
      - ai
      - nextjs
      - typescript
      - postgres
  - name: su2re
    role: author
    visibility: private
    description: "Electron desktop transcriber: faster-whisper + pyannote
      diarization, push-to-talk, GPT-4o-mini cleanup, Google Calendar."
    year: 2025
    last_active: 2025-10
    language: JavaScript
    archived: false
    tags:
      - ai
      - desktop
      - python
  - name: article-checker
    role: author
    visibility: private
    description: 2023 CRA prototype that grades news articles for objectivity and
      logical consistency via GPT-3.5.
    year: 2023
    last_active: 2023-03
    language: TypeScript
    archived: false
    tags:
      - react
      - typescript
      - ai
      - sandbox
      - shelved
  - name: bisque
    url: https://github.com/Miawousha/bisque
    role: author
    visibility: public
    description: Landing-page sandbox on Next.js 16 / React 19 / Tailwind 4 — a
      single button that does nothing.
    year: 2026
    last_active: 2026-02
    language: TypeScript
    stars: 0
    archived: false
    tags:
      - nextjs
      - react
      - typescript
      - ui-only
      - sandbox
  - name: saas
    role: author
    visibility: private
    description: "Real-time browser game: NestJS WebSocket server paired with a
      Phaser 3 / Vite client."
    year: 2025
    last_active: 2025-02
    language: TypeScript
    archived: false
    tags:
      - typescript
      - sandbox
---

Smaller developer tools, infrastructure benchmarks, and prototypes.

## blueprint-creator

blueprint-creator is an interactive Python CLI ("BP Extender") that drives the Altergo SDK to manage blueprints across multiple environments. The menu walks an operator through environment selection, blueprint search and tree-view, parameter and schema inspection, child-hierarchy creation from simspec JSON, conversion between blueprint formats, and bulk deletion — with Rich-rendered tables, banners, and diff reports written under `data/`. Internal developer tooling for blueprint authoring at scale.

### What
An operator runs `run.py`, picks an environment from `envs/`, and lands in a Rich-rendered numeric menu — not a flag-based CLI. From there they search blueprints by name or ID, walk the tree of children, inspect parameter and schema definitions, generate a child hierarchy from a simspec JSON, convert legacy blueprints to the current format, or bulk-delete a list. Diff and conversion reports drop into `data/` so changes are reviewable before they ship.

### Tech
`bp_extender/cli.py` owns the menu loop; `client.py` wraps the Altergo SDK with env-scoped auth (`envs/<env>.json`); `extender.py` builds child hierarchies from simspec; `converter.py` handles format migration; `schema.py` introspects blueprint schemas; `cli_reports.py` writes the diff artifacts. Rich drives every table, banner, and progress indicator. Multi-env support lets the same operator hop between dev, staging, and prod without re-auth ceremony.

### Status
Active developer tooling at Altergo, last touched 2026-01. Used by the modelling team to keep blueprint catalogs in sync across environments and to bootstrap new asset hierarchies without hand-editing JSON.

## blueprints_importer

blueprints_importer is a Python app packaged for the Altergo platform (declared in `altergo-settings.json` as a Simulation app) that ingests an Excel workbook of battery and non-battery components and materialises them as platform blueprints. The `main.py` pipeline downloads the workbook, extracts inputs to CSV and images, generates JSON blueprint templates, then deletes and regenerates the targeted blueprints and their datasets through the Altergo SDK; a "new_format" branch instead builds blueprints directly from referenced `datasetIds`. Filters by name or by category (Battery, Stack, Module, Cell) and supports import modes `all`, `only_new_blueprints`, `only_specified_blueprints`, `only_specified_categories`, `new_format`.

### What
Input is an Excel workbook held in shared storage with one sheet per component family (Battery, Stack, Module, Cell, plus non-battery parts). Output is a refreshed set of platform blueprints and their backing datasets visible to every downstream simulation app. Operators trigger it from the Altergo platform UI; the run filters by name or category and picks an import mode to bound the blast radius (regenerate everything, only-new, only-specified, only-categories, or the dataset-id-driven new_format path).

### Tech
`main.py` orchestrates the pipeline; `src/download_xlsx.py` pulls the workbook; `src/inputs_extractor_from_excel.py` writes per-component CSV and image artifacts; `src/generate_json_bp_battery_templates_from_csv.py` and its non-battery sibling produce blueprint JSON; `src/generate_bp_battery.py`, `src/generate_bp_non_battery.py`, and `src/create_bps_from_datasets.py` call the Altergo SDK to delete and recreate blueprints and datasets atomically; `src/delete_bps.py` handles the cleanup pass. `altergo-settings.json` registers it as a Simulation-category platform app with its parameter schema.

### Status
Internal Altergo bulk-import tool, last active 2025-10. Run when the upstream component spreadsheet changes and the platform catalog needs to be rebuilt. `requirements.txt` ships a hard-coded Bitbucket access token — already flagged to the owner; should be rotated and moved to env config.

## simple-app

simple-app is the empty starter scaffold for an Altergo platform "app" (as opposed to a model) — `entrypoint.py` initializes the Altergo SDK client, reads `configurationValues`, and ends on a `# Your logic here` comment. No README, no real code; `altergo-settings.json` declares a single placeholder parameter. Reference scaffold, not a project.

### What
Starting point an Altergo customer or internal developer forks to build a custom platform "app" — a unit of code the platform schedules and runs against assets, distinct from the "model" type. The repo gives them a working SDK client and parameter wiring; everything past that is theirs to fill in.

### Tech
Four files: `entrypoint.py` (`extract_altergo_parameters` → `Client(functionArguments=…)`), `altergo-settings.json` (declares `type: "app"`, one `parameter1` placeholder), `dev-parameters.json` (local-run shim), `requirements.txt` (pins `altergo-sdk` from the bitbucket `release/alpha` branch). No tests, no logic, no README.

### Status
Last touched 2024-10. Lives as a reference template alongside the function-template scaffold (`simple-soc-model`); the two together cover the "app" and "model" sides of the Altergo function ABI. Not a deliverable, used by other repos as a starting point.

## openclaw-config

openclaw-config is the on-disk config and state directory backing OpenClaw, a personal long-running agent runtime — provider/model registries, auth profiles, per-agent workspaces (main, inbox, robin), paired devices, cron jobs, shell completions, and a SQLite memory store, all kept as versioned files. Not a deployable codebase; it's the substrate the agent reads and writes against. Includes a WhatsApp channel config and a small canvas HTML test page. Private, edited continuously as the agent learns.

### What

The repo is the `~/.openclaw/` directory of a personal agent host, captured in git so config changes are inspectable and revertible. Top-level: `openclaw.json` is the central config; `agents/` holds one subdirectory per agent (`main`, `inbox`, `robin`), each with its own `auth.json`, `auth-profiles.json`, and `models.json`; `cron/jobs.json` schedules recurring agent tasks; `devices/paired.json` and `pending.json` track devices that have completed Ed25519 pairing with operator-scoped tokens; `identity/` holds the device's own keypair and auth state; `memory/main.sqlite` is the persistent memory store; `completions/` ships shell completions for bash/zsh/fish/PowerShell; `canvas/index.html` is a small JS test page that exercises `webkit.messageHandlers.openclawCanvasA2UIAction` (iOS) and the equivalent Android bridge to validate the agent's UI action channel from a webview.

### Tech

`openclaw.json` is a single JSON document the runtime merges with defaults. Sections: `meta` (last-touched version timestamps), `wizard` (onboarding state), `auth.profiles` (provider × mode tuples), `models` in `merge` mode listing custom OpenAI-compatible providers (e.g. nexos.ai, NVIDIA's hosted `moonshotai/kimi-k2.5`), `agents.defaults` (primary model, workspace path, `compaction.mode: safeguard`, `maxConcurrent: 4`, `subagents.maxConcurrent: 8`) plus an `agents.list` that overrides per agent, `hooks.internal` (boot-md, session-memory), `channels.whatsapp` (`dmPolicy: pairing`, `groupPolicy: allowlist`, `mediaMaxMb: 50`), and `gateway` (loopback HTTP on port 18789 with a token-mode auth and a Tailscale toggle, plus `nodes.denyCommands` that blocks `camera.snap`, `screen.record`, `calendar.add`, etc.). Backup copies `openclaw.json.bak.1..4` are kept on every meaningful write. Per-agent `auth-profiles.json` stores OpenRouter API keys with `usageStats` (lastUsed, errorCount) for fallback selection.

### Status

Private. Tracks an active personal install — `lastTouchedVersion: 2026.2.17`, `lastTouchedAt: 2026-02-19`. The `cron/jobs.json` is empty (jobs list `[]`); WhatsApp is the only plugin enabled. SQLite memory is small (~68KB). The repo exists so OpenClaw config edits — which happen frequently as the agent learns — have history.

## opus-infra

opus-infra is the Next.js 16 + Supabase application backing OPUS, a scientific journal that treats manuscripts as typed objects rather than PDFs — versioned content, claim extraction (contribution / result / method / limitation with evidence and citation refs), and a status workflow that moves a submission from draft through AI rubric review, reviewer matching, human review and consensus, to greenlit or declined. AI review and claim extraction both call Claude (`claude-opus-4-7`) via the Anthropic SDK with tool-use; the editor renders markdown + KaTeX and version diffs. Vitest integration tests cover the article, review, AI-review, claims, and admin oversight surfaces. Private, early but substantively wired beyond a stub.

### What

The submission is the unit, not the PDF. An author writes the manuscript as markdown + math, hits submit, and the article enters an explicit status machine: `draft → ai_review → ai_passed → matching → in_human_review → greenlit | declined`. During `ai_review` the system runs two Claude tool-use calls in parallel — a rubric scorer and a claim extractor — and shows both results on the manuscript. Claims are typed (`contribution`, `result`, `method`, `limitation`), carry `evidence_refs` (section / figure / table / equation locators) and `citation_refs` (raw text + optional DOI), and can be `suggested` (AI), `accepted`, or `dismissed` by the author. Editors then match human reviewers to topic tags, collect reviews, and the consensus logic decides the outcome. There's a public `/published` surface and an admin oversight surface for editors.

### Tech

The AI review (`src/lib/ai-review/reviewer.ts`) calls `claude-opus-4-7` via `@anthropic-ai/sdk` with a single `submit_rubric_review` tool whose schema enforces a `summary` plus one entry per rubric criterion (`structure`, `clarity`, `methodology`, `integrity`, each with a 70-point pass threshold). The claim extractor (`src/lib/claims/extract.ts`) uses the same pattern with a `submit_claims` tool whose JSON Schema enumerates the four claim types and the four evidence-ref kinds. Both system prompts are sent with `cache_control: { type: "ephemeral" }` for prompt-cache hits across retries. Versions are stored as separate rows in `article_versions` and rendered with a markdown + KaTeX + remark-math pipeline plus `diff` for version-to-version views. Reviewer matching (`src/lib/review/matching.ts`) is a simple lowercase tag-set intersection scored by count, sorted descending. Integration tests under `tests/integration/` (`articles`, `human-review`, `ai-review`, `profiles`, `public-access`, `admin-oversight`) run against a real Supabase via `db-helpers.ts`.

### Status

Private as of 2026-05; not yet open to authors. Schema, status workflow, AI pipeline, claims model, reviewer matching, consensus, and admin surfaces are all in place with integration coverage — substantively past a prototype, but no real submissions in flight. Two seed scripts (`seed:accounts`, `seed:articles`) bootstrap a dev environment.

## su2re

su2re is a cross-platform Electron transcriber paired with a Python backend. The Electron main process registers a global push-to-talk shortcut and spawns one of three Python entry points — `transcriber_backend.py` for plain transcription, `..._diarization.py` for `pyannote/speaker-diarization-community-1` on top of `faster-whisper`, or `streaming_transcriber.py` — communicating via stdout `STATUS:` lines. On the JS side, `ai-improver.js` calls OpenAI `gpt-4o-mini` to clean transcripts and extract calendar events as JSON; `calendar-scheduler.js` wraps `googleapis` to OAuth into Google Calendar and insert events. Windows NSIS/portable, macOS DMG, Linux AppImage targets via electron-builder.

### What

Press Ctrl+Shift+Space anywhere on the desktop, talk, release: the audio gets transcribed locally and lands as text in the active tab. Drop an audio file (MP3/WAV/M4A/FLAC/OGG/OPUS/MP4/AVI/MKV) onto the app for a longer transcription with model-size choice (tiny to large-v2). With diarization on, speakers come out colour-coded and label-editable. The AI tab offers cleanup presets (professional tone, concise, bullets, summary); the calendar tab parses the transcript for events, asks the user to confirm, then inserts them into the primary Google Calendar.

### Tech

Two-process design: Electron `main.js` owns lifecycle, `globalShortcut.register`, `spawn('python', ...)` and parses stdout for `STATUS:` lines + payloads; renderers (`renderer.js`, `renderer-tabs.js`, `renderer-diarization.js`, `renderer-improvement.js`, `renderer-calendar.js`) split UI per feature. Python side uses `faster-whisper` for the Whisper inference and `pyannote.audio` with `speaker-diarization-community-1` for diarization, both 100% local. `ai-improver.js` calls OpenAI `gpt-4o-mini` twice for calendar mode — once to clean, once to extract events as a strict JSON array. `calendar-scheduler.js` stores OAuth credentials and tokens in `electron-store` and calls `google.calendar('v3').events.insert`. Models can be bundled into the installer via `extraResources` so the user doesn't have to download multi-gigabyte weights on first run.

### Status

Built in October 2025 — last commit 2025-10-17 ("Implement calendar scheduling and speaker diarization features"). ~175 KB of JS + Python, electron-builder ships NSIS + portable Windows, DMG macOS, AppImage Linux. Personal utility, not distributed.

## article-checker

article-checker is a 2023 Create-React-App sketch that pastes an article into a textarea, sends it to GPT-3.5 with a "journalism professor" system prompt, and renders the structured JSON reply as Plotly radar and gauge charts (purpose breakdown, objectivity, logical-consistency scores). Built with React 18, react-bootstrap, and the openai client called straight from the browser — API key was committed in source, which is one reason it never went anywhere. Shelved.

### What
One page. User pastes article text into a `QuestionForm` textarea; `chatGPTService`
calls GPT-3.5-turbo with a single system prompt baked into the bundle plus the
schema JSON for the expected reply. The response is parsed and routed to a
`RadarChart` (purpose: Teach / Inform / Persuade / Entertain / Evaluate, summing
to 100%), two `GaugeChart` instances (objectivity %, logical-consistency %),
and an `AnswerCard` listing flagged rhetorical devices and logical fallacies.
A `cannedResponse.json` ships for offline UI work.

### Tech
CRA + React 18 + react-bootstrap, `openai@3.2.1` instantiated client-side.
A `news_extractor.ts` using cheerio is present but unwired. No backend, no auth.
The OpenAI key sits hard-coded in `src/services/chatGPTService.ts` — anyone with
the bundle has the credential.

### Status
~3 weeks of evening work in early 2023, shelved March 2023. Never deployed,
never shared. Killed by the committed key, the lack of any moat over "ask GPT
to grade an article", and lost interest. Kept around as a record of the idea.

## bisque

Bisque is a single-page teaser landing on Next.js 16 and React 19. The whole app is one page: a "this button does nothing" button that increments a click counter and reveals a sequence of lobster-themed whispers ("told you.", "🦞", "nothing, but with intention."), a next-themes light/dark toggle, and a warm orange glow. Built with shadcn/ui primitives on Tailwind 4 as a placeholder for `bisque.life`; "v0.0.1 — the primordial soup."

### What
One file (`src/app/page.tsx`). Title "bisque.life", a tagline ("something
useful and delicious is brewing. swarms of lobster agents are assembling."),
the button, the whisper line, a click counter that fades in at 3 clicks, and a
tease blurb that reveals at 5 clicks. Theme toggle top-right, lobster emoji,
ambient orange blur layers behind the content.

### Tech
Next.js 16, React 19.2, Tailwind 4, `next-themes`, one shadcn `Button`. No
backend, no analytics, no state beyond `useState`.

### Status
v0.0.1 placeholder for `bisque.life`. Built Feb 2026. Not deployed publicly.

## saas

saas is a two-package sandbox for a real-time browser game (the slug is a leftover from an older idea — it's not a SaaS). `game-server` is a NestJS 11 app whose `GameGateway` runs a socket.io WebSocket loop that tracks players, accepts `inputUpdate` messages, and broadcasts state; `game-client` is a Phaser 3 + Vite TypeScript client with a missile/radar/targeting setup (ships, lock symbols, starfield) authored in Phaser Editor. Personal experiment in real-time multiplayer architecture; not deployed.

### What

The player loads a Phaser scene (a `Level` scene preloaded by `Preload`) and finds a 2D space arena with their own ship, a few seeded drone ships, a missile system with lock-on targeting, and a HUD (`PlayerStatus`) on top of a starfield. Input goes over the WebSocket as `inputUpdate` messages; the server resolves movement, missile fire cooldowns, drone behaviour, and target locks, then broadcasts authoritative state back to all clients. Targeting is a `toggleTarget` event the client sends to pick or drop a missile lock on another ship.

### Tech

Two packages, no monorepo tool — just sibling directories sharing a `package-lock.json` at the root. `game-server` is NestJS 11 with `@nestjs/platform-socket.io` and `@nestjs/websockets`; the `GameGateway` (`src/game/game.gateway.ts`) hard-allows CORS from `http://localhost:3001` and delegates to `GameService` (`src/game/game.service.ts`), which holds the world (`ships`, `missiles`, `lastMissileFireTimes`) and ticks via `setInterval` at a `fixedDelta` of `1/30` s — a 30 Hz server loop. Ships split into `PlayerShip` and `DroneShip` subclasses of a shared `Ship`; missiles have a 5000 ms lifetime and 25-unit thrust. `game-client` is the Phaser 3.80 + Vite TypeScript template with `socket.io-client@4`, scenes authored as `.scene` files alongside their `.ts` counterparts in Phaser Editor.

### Status

Personal sandbox. Last activity 2025-02. Not deployed, no shipping target — built to explore the loop of an authoritative WebSocket server driving a Phaser client. The misleading `saas` slug is the only thing left from a prior framing.
