---
name: Personal tools
year: 2026
tags:
  - productivity
repos:
  - name: toudoux
    role: author
    visibility: private
    description: Next.js 15 todo app that doubles as an OAuth-protected MCP server,
      mainly driven from Claude.
    year: 2026
    last_active: 2026-04
    language: TypeScript
    archived: false
    tags:
      - productivity
      - mcp
      - nextjs
      - typescript
  - name: sirene
    url: https://github.com/Miawousha/sirene
    role: author
    visibility: public
    description: Tauri 2 desktop app for editing Mermaid diagrams with a live SVG preview.
    year: 2026
    last_active: 2026-02
    language: TypeScript
    stars: 0
    archived: false
    tags:
      - desktop
      - react
      - typescript
      - tooling
  - name: roadmap
    url: https://github.com/ION-Altergo/roadmap
    role: contributor
    visibility: private
    description: Internal roadmap workspace — markdown task DSL plus a Svelte
      Gantt/team viewer.
    year: 2026
    last_active: 2026-01
    language: Svelte
    archived: false
    tags:
      - svelte
      - productivity
      - docs
  - name: xblock
    url: https://github.com/matrice-technologies/xblock
    role: author
    visibility: public
    description: Chrome extension for fast blocking on X, with shareable block lists
      and a self-hostable server.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags:
      - browser-extension
      - typescript
      - express
      - prisma
      - open-source
  - name: book1doc
    url: https://github.com/Miawousha/book1doc
    role: author
    visibility: public
    description: Shows which Doctolib slots a new patient can actually book, as a
      browser extension, a web app and a CLI. Not affiliated with Doctolib.
    year: 2026
    last_active: 2026-08
    language: HTML
    archived: false
    tags:
      - browser-extension
      - python
      - healthcare
      - open-source
  - name: papylantir
    role: author
    visibility: private
    description: Night-time front-door agent for an elderly family member, with
      camera scene analysis, a voice conversation and silent alerts.
    year: 2026
    last_active: 2026-09
    language: Python
    archived: false
    tags:
      - python
      - ai-agents
      - computer-vision
      - voice
      - gemini
  - name: matrice-osint-fisc
    role: author
    visibility: private
    description: OSINT tooling on French public sources for investigative journalism
      on tax and financial matters.
    year: 2026
    last_active: 2026-10
    language: Python
    archived: false
    tags:
      - osint
      - python
      - cli
      - open-data
      - journalism
  - name: coolify-cli
    url: https://github.com/matrice-technologies/coolify-cli
    role: author
    visibility: public
    description: Thin CLI for driving a self-hosted Coolify v4 instance (deploy, env,
      inspect), built for chat-driven deployments.
    year: 2026
    last_active: 2026-07
    language: TypeScript
    archived: false
    tags:
      - cli
      - devops
      - typescript
      - open-source
  - name: nextjs-boilerplate
    role: author
    visibility: private
    description: Next.js SaaS starter with Supabase auth, workspaces, members and
      invitations, projects and settings.
    year: 2026
    last_active: 2026-08
    language: TypeScript
    archived: false
    tags:
      - nextjs
      - supabase
      - typescript
      - boilerplate
  - name: ionenergy-website
    role: author
    visibility: private
    description: Marketing website built for ION Energy with Next.js and shadcn/ui.
    year: 2026
    last_active: 2026-09
    language: TypeScript
    archived: false
    tags:
      - nextjs
      - website
      - typescript
---

A handful of small personal productivity tools.

## toudoux

toudoux is a Next.js 15 todo app that doubles as a Model Context Protocol server. `src/app/api/mcp/route.ts` wraps `mcp-handler` with a per-request OAuth bearer check and registers four tool families against the authenticated user: todos (list/add/update/complete/delete), people (a roster with mentions), recurrences (rrule-driven `add_recurring`, `list_recurring`, `stop_recurring`), and stats. The OAuth2 server is hand-rolled under `src/lib/mcp/oauth` with PKCE, dynamic client registration, and the `.well-known` discovery routes, alongside NextAuth v5 with the Drizzle adapter on pg. Daily-driver test bed for MCP — the browser app and the MCP server share the same Drizzle schema and the tools are the ones Alexandre actually uses from Claude.

### What

Two surfaces over one Postgres database. In the browser, you sign in with NextAuth and get a Trello-light dashboard for todos, contacts (mentionable with `@name`), and recurring rules expressed as rrule strings. In Claude (or any MCP client), you go through OAuth once via the `connect Claude` modal on the dashboard, then add/list/complete todos, look up or merge people, schedule recurrences, and pull stats by talking to the agent. Both surfaces see the same data because they hit the same Drizzle tables.

### Tech

`src/app/api/mcp/route.ts` parses the `Authorization: Bearer` header through `resolveUserFromAuthHeader`, returns a `401` with `WWW-Authenticate` pointing at `/.well-known/oauth-protected-resource` when missing, and otherwise constructs a fresh `mcp-handler` per request with each tool registered against that resolved `userId`. The OAuth2 issuer is hand-rolled — `src/lib/mcp/oauth/{issuer,clients,authz,tokens,pkce,crypto}.ts` cover discovery, dynamic client registration, the authorisation code + PKCE flow and token signing. Recurrences use the `rrule` package. Drizzle on `pg` (`src/lib/db/`), tests via Vitest, env validated in `src/lib/env.ts`.

### Status

Active throughout 2026 — last commit 2026-04 ("feat(dashboard): add 'connect Claude' button with MCP setup modal"). ~175 KB of TypeScript, private, single-user. Used daily from Claude; the dashboard mostly exists for setup and the occasional manual edit.

## sirene

Sirene is a Tauri 2 desktop app for editing Mermaid diagrams with a live preview. The Rust shell ships clipboard, fs, and dialog plugins around a React 19 renderer where CodeMirror 6 sits in an Allotment split-pane next to a Mermaid 11 SVG preview, with a file tree, multiple tabs, and eight starter templates (flowchart, sequence, class, state, ER, gantt, pie, gitGraph). Ctrl+S/O/N/W/C bind to save, open, new tab, close tab, and copy-as-PNG; PNG rendering goes through an off-screen canvas in `src/lib/clipboard.ts`. shadcn/ui + Tailwind 4 for the chrome, dark/light themes wired through a `useTheme` hook.

### What

Single-window editor: pick a template from the toolbar or open an `.mmd` file from the tree, type Mermaid source on the left, the SVG re-renders on the right as you go. Multiple tabs let you flip between diagrams; recent files persist across sessions; the preview pane is zoomable (scroll, Alt-drag, fit-to-view). Ctrl+C on the preview copies a 2x retina PNG straight to the clipboard so it pastes into Word or Google Docs without a save step.

### Tech

The Rust crate at `src-tauri/` is thin — `tauri-plugin-clipboard-manager`, `tauri-plugin-fs`, `tauri-plugin-dialog`, `tauri-plugin-log` and an `image-png` Tauri feature. All UX lives in React: `App.tsx` wires keyboard shortcuts, `hooks/useTabs.ts` owns multi-document state, `hooks/useFileTree.ts` the directory view, `lib/templates.ts` the eight seed diagrams, `lib/preprocessor.ts` auto-quotes labels with special characters, `lib/clipboard.ts` rasterises SVG to PNG via off-screen canvas plus `DOMParser` to inject `xmlns` and explicit width/height. CodeMirror 6 with a custom Mermaid language mode at `lib/mermaid-lang.ts`.

### Status

Started early 2026, last commit 2026-02 ("Auto-close tabs when files are deleted or renamed"). ~3 MB installer, Windows + macOS (Intel + Apple Silicon), version 0.2.0. Personal tool, used to make the diagrams in Alexandre's notes and decks.

## roadmap

roadmap is ION-Altergo's internal product-planning workspace, mostly markdown (`Adani/overview.md`, `Adani/tasks.md`, archived snapshots, reference SBOM/certification docs) driven by a small Svelte 4 + Vite viewer under `Adani/viewer/`. The viewer parses a custom task DSL (`++X` effort, `~X` lead time, `@W` week anchor, owner suffix) into a Gantt chart and a per-owner team-allocation view; it fetches `tasks.md` at runtime or accepts a file upload. Functional in-browser tool, no backend; not a SvelteKit app.

### What
The repo's payload is the markdown — the Adani BESS engagement overview, the live `tasks.md` list, weekly team-allocation reports, dated archive snapshots, and reference material (Altergo platform overview, SBOM, certification matrix) under `reference/`. Tasks follow a strict rule set: tasks within a section run sequential top-to-bottom, sibling sections run in parallel, same owner in same section cannot overlap, nested sections inherit parent start week unless overridden, `*m` marks certification-matrix milestones. The Svelte viewer turns this into a Gantt + capacity dashboard for weekly syncs.

### Tech
Svelte 4 + TypeScript + Vite, no SvelteKit, no backend — `index.html` + `src/main.ts` mount `App.svelte`. The DSL parser lives in `src/lib/`, produces tasks with computed start/end weeks honoring inheritance and ordering rules, and feeds two views: a Gantt timeline and a per-owner allocation chart. Loads `tasks.md` over `fetch` at dev/preview time or via file-upload fallback. Pure client-side; deploys as static files when needed.

### Status
Active 2026-01 for the ADANI 24-month BESS engagement — drives weekly syncs and certification tracking. Contributor role — Alexandre built the viewer and DSL parser, authors the task list, owns most of the planning markdown. Single-user tool today; team-shareable in browser without infra.

## xblock

XBlock is a Chrome extension for fast blocking on X (formerly Twitter), with block lists that can be shared and subscribed to. Matrice Technologies released it as open source under the MIT licence in October 2026, together with its self-hostable API server and a public website.

### What

From the X website, a user blocks an account in one click and adds it to their own block list. A list can be shared through a code; subscribers then block every account on it automatically, which suits community moderation. The extension and website are available in seven languages (English, French, Spanish, German, Japanese, Brazilian Portuguese, Indonesian), and the extension is listed on the Chrome Web Store. Blocking comes with its own animations, including a "Samurai" mode in which the post is sliced apart; the website hero is a playable demo of it on a fake timeline.

### Tech

A repository in three parts. `chrome_extension/` is a Manifest V3 extension built with webpack, with Chrome's i18n message files for translations. `server/` is an Express 5 API with Prisma on SQLite and rate limiting; a server secret turns each user's token into a user ID by HMAC, allowed extension origins are set for CORS, and optional admin endpoints expose usage statistics and curated lists. It ships as a Docker image that runs migrations on start. `website/` is a Next.js site with Tailwind and shadcn/ui, with one dictionary per language checked by a script, and Chrome Web Store images rendered from the site. `DEPLOY.md` documents hosting one's own server.

### Status

Open-sourced on 30 October 2026 at version 1.6.4; version 1.7.1, with the seven languages, the same day. Public repository.

## book1doc

book1doc shows which Doctolib appointment slots a new patient can actually book. Doctolib's search page advertises each practitioner's next availability for whichever visit motive its engine matched, and for specialists that is often a follow-up or a technical exam that a first-time patient is not allowed to book, which only becomes clear several clicks later. Not affiliated with Doctolib; personal project, published on Alexandre's own GitHub account.

### What

Three front ends share the same logic. DoctoBook, a browser extension for Chrome, Edge and Firefox, adds a line to each card of the Doctolib results page saying what a new patient can book and when. A small web app takes a pasted search URL and sorts practitioners into really bookable, advertised but not for a new patient, and nothing online. A Python CLI runs the same scan with HTML and JSON export, filters for insurance sector and age, and a wider search around the coordinates. The README gives one measured example: for one specialty in one city on 28 August 2026, 10 practitioners were listed, 8 shown with availability, and 1 actually bookable for a first consultation.

### Tech

The tool calls Doctolib's public, unauthenticated endpoints (search, booking-funnel info, availabilities) and reimplements the client-side rule that decides whether a visit motive is open to new patients, along with insurance and age restrictions; visit-motive names are only used to label and order results. The extension sends requests from the user's own browser session, so there is no central server. The web app needs a backend only because Doctolib sends no CORS header: a stateless Node server with four validated routes, deployable on Cloudflare Workers with Wrangler. The CLI uses the Python standard library plus `certifi`.

### Status

Published on 31 August 2026 under the MIT licence. Public repository.

## papylantir

Papylantir is a night-time watch agent for the front door of an elderly family member's home, built in September 2026. When someone moves in front of the door at night, the agent speaks to them through a speaker, listens, assesses whether they seem awake and oriented, gently suggests going back to bed, and alerts the family when needed.

### What

The design starts from the assumption that a night-time visit is ordinary, and aims to stay calm and brief. A vision agent describes the scene about once a second in a fixed JSON form (who is present, what they are doing, a risk level), and a code rule opens a conversation only on concrete signs of leaving, such as a hand on the handle, keys, shoes or a coat. A supervisor agent reads the night's log every few seconds to catch patterns that single frames miss, such as standing still for a long time or pacing, and is the only path to an alert; an open front door triggers an urgent alert by hard-coded rule. The voice agent introduces itself as the house assistant, never as a relative, and never says aloud that it is alerting anyone. Monitoring only runs during configured night hours and starts paused.

### Tech

Python 3.12. Motion detection with OpenCV (or optional person detection), scene understanding with Gemini Flash-Lite, and a Claude supervisor with schema-constrained JSON output. Two interchangeable voice chains: Silero VAD, faster-whisper and streaming Claude replies spoken by ElevenLabs; or a single Gemini Live session driven by an explicit state machine in which code, not the model, decides every transition. Alerts go to ntfy or a webhook. A FastAPI dashboard on the local network shows live video, agent states, analysed frames and the event log, and replays recorded episodes from a state journal; each episode is recorded with pre-roll video, both audio tracks and the full AI logs. Camera, microphone and speaker are swappable through configuration, from a webcam to an RTSP camera.

### Status

Built from 8 to 10 September 2026; a first version that runs on a local PC. Private repository.

## matrice-osint-fisc

matrice-osint-fisc is a set of OSINT tools on French public sources, built at Matrice Technologies in October 2026 to support investigative journalism on tax and financial matters. It is designed to be used with Claude: the journalist asks a question, Claude calls the `fisc` tool, cross-checks the results and keeps the case file according to written method rules.

### What

The `fisc` CLI looks up company directorships, legal announcements and public-official interest declarations for a person; profiles a company and its officers; builds the network of companies and holding structures around a person, optionally with the real estate those companies own; compares interest declarations with the company register; searches leaked offshore databases and sanctions lists; and screens all national declarants for directorships missing from their declarations, graded by confidence. A benchmark command replays cases already decided by courts. Case files can be presented as a summary page with an anonymised version, and exported as a single file that can be encrypted with a passphrase. The tool qualifies nothing: it reports what public registers contain, where and when, and how closely a record matches the person searched.

### Tech

Python, managed with uv, using httpx, DuckDB (reading public tax-administration Parquet files remotely) and PyYAML. Sources include the French company directory API (RNE and SIRENE), BODACC, HATVP, DGFiP data on properties held by legal entities, ICIJ Offshore Leaks and OpenSanctions. Raw responses can be archived in the case folder with URL, date and SHA-256 hash, and every command has a JSON output for Claude. Network graphs export to JSON, Mermaid, GraphML and an offline HTML view built on Cytoscape.js. A Claude Code skill describes the investigation workflow.

### Status

Built on 22 and 23 October 2026. Private repository.

## coolify-cli

coolify-cli is a thin command-line tool for driving a self-hosted Coolify v4 instance, written at Matrice Technologies in July 2026 so that deployments can be run from a chat session with an agent.

### What

Commands cover profiles (`config set`, `config use`, `config ls` with masked tokens), listing applications, services, databases, projects and servers, inspecting a resource by name or UUID, deploying with a status watcher, and listing, setting or removing environment variables with an optional redeploy. Read commands take `--json` for machine output, and `COOLIFY_URL` and `COOLIFY_TOKEN` override stored profiles.

### Tech

TypeScript with commander, built with tsup, tested with Vitest, with a name-to-UUID resolver, table and JSON output helpers, and a GitHub Actions workflow that tests and builds on push and pull request.

### Status

Version 0.1.1 released on 13 July 2026. Public repository.

## nextjs-boilerplate

nextjs-boilerplate is Matrice Technologies' starting point for Next.js products, created in August 2026: the parts every product needs, taken from a working product with the product removed.

### What

Authentication by magic link and Google OAuth through Supabase; workspaces with logos, created, switched, renamed and deleted; members with owner, admin and member roles, expiring email invitations and a guard against a workspace losing its last owner; projects with a near-empty page where the product goes; and a settings section for profile, appearance, workspace and members. Aune is built on it and records that provenance.

### Tech

Next.js 16, React 19, TypeScript, shadcn on Base UI and Tailwind 4, with light and dark themes. The Supabase schema is self-contained in three migrations (tables and triggers, row-level security policies and grants, storage buckets), and the README documents the pitfalls of combining grants with RLS. Deployment is a Coolify server running both Supabase and the app, carried out by a Claude agent following a written routine.

### Status

Created on 12 and 13 August 2026. Private repository.

## ionenergy-website

ionenergy-website is the marketing site Alexandre built for ION Energy, which makes battery intelligence software for EV fleets and grid-scale storage.

### What

A single-page site with one component per section, case study PDFs to download, and a social preview image generated at build time. All copy, figures and links live in one content file so they can be edited in one place.

### Tech

Next.js App Router, React 19, Tailwind CSS 4, shadcn/ui and lucide icons, with brand colours defined as CSS tokens.

### Status

First built in July 2026 as a Next.js rebuild of the earlier Altergo site made with Framer, then rebranded to ION Energy in September 2026. Private repository.
