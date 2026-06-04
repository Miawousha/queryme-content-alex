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
