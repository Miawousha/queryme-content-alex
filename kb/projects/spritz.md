---
name: Spritz
year: 2025
tags:
  - productivity
repos:
  - name: spritz
    url: https://github.com/ION-Altergo/spritz
    role: contributor
    visibility: private
    description: Original Altergo task manager — markdown tasks, Firebase real-time
      collab, GSAP animations.
    year: 2025
    last_active: 2025-04
    language: JavaScript
    archived: false
    tags:
      - productivity
  - name: spritz-modern
    url: https://github.com/ION-Altergo/spritz-modern
    role: contributor
    visibility: private
    description: React + TS rewrite of spritz — Redux Toolkit, Styled Components,
      React Spring, Vite.
    year: 2025
    last_active: 2025-04
    language: TypeScript
    archived: false
    tags:
      - react
      - typescript
      - productivity
  - name: spritz-svelte
    role: author
    visibility: private
    description: SvelteKit task app with Yjs real-time collab, Firebase auth/data,
      and a Stripe Premium tier.
    year: 2025
    last_active: 2026-02
    language: Svelte
    archived: false
    tags:
      - svelte
      - typescript
      - productivity
---

Spritz is Alexandre's task manager, built across several stacks. The repositories below are its implementations.

## spritz

spritz is the original Altergo team task manager, a single-page app in plain HTML/CSS/JS with GSAP for motion and Firebase Realtime Database for shared state. A markdown editor on the left renders into an interactive task list on the right — left-click toggles, right-click on a completed task triggers a sound-effect-driven deletion, and idle tasks slowly "ooze" via an SVG goo filter after 24 hours. Real-time collab is genuinely wired: every board has a `?taskId=` URL, and `database.ref('taskLists/' + id).on('value', ...)` pushes edits to anyone holding the link. Hosted on Firebase App Hosting; superseded internally by `spritz-modern`.

### What
Users write tasks as markdown lines (`[ ] Fix bug @alice p**`) — the `@owner` suffix tags assignees and `p*` / `p**` / `p***` set priority levels rendered as color-coded badges. The editor pane stays the source of truth; the right pane is a model-rendered, click-interactive list with audio cues on toggle and a goo-filter destruction animation on right-click delete. A share link at the bottom carries the board's `?taskId=` so opening the URL in another tab or device joins the same Firebase node live.

### Tech
Vanilla JS broken into focused modules: `markdownParser.js` parses lines into a task model, `modelRenderer.js` paints the interactive list, `animations.js` drives GSAP timelines and the SVG goo filter, `skinManager.js` swaps CSS+JS skin bundles (default and dark-blue ship in `js/skins/`), and `share.js` owns the Firebase v8 SDK setup, URL `?taskId=` handling, `database.ref('taskLists/' + id).set(...)` saves, and `.on('value', ...)` subscriptions. Stale-task "ooze" compares `lastUpdated` server timestamps to now and ramps the goo filter past the 24h mark. Deployed via `apphosting.yaml` to Firebase App Hosting; `database.rules.json` keeps the realtime DB open to anyone holding a task ID.

### Status
Built and used by the Altergo team through 2025, last active April 2025. Internally superseded by `spritz-modern` (the React rewrite) and then by Alexandre's personal SvelteKit version. Codebase frozen in plain-JS form; the Firebase project (`spritz-31ad5`) and live URLs still resolve.

## spritz-modern

spritz-modern is the React + TypeScript rewrite of the Altergo spritz task manager, built on Vite with Redux Toolkit (theme and tasks slices), Styled Components, React Spring, react-dnd, and Firebase for persistence and presence. The original feature set carries over — markdown editor pane, interactive task list, share-by-URL collaboration via `useCollaboration` and `useTaskData` hooks, themed skinning through a styled-components `ThemeProvider`. Reaches feature parity with `spritz` and adds a typed component-based skin system that makes new themes trivial. Internal continuation; later superseded by the personal SvelteKit version.

### What
Same two-pane UX as the original — markdown editor on the left, interactive task list on the right with toggles, priority badges, owner mentions, and drag-and-drop reordering via react-dnd. Sharing still works through a `?taskId=` URL backed by Firebase Realtime Database; opening the link elsewhere joins the same board live, with a `CollaborationIndicator` showing other active users. Theme switching is exposed in the header and swaps the entire surface (colors, fonts, drop animations, icons) without reloading.

### Tech
File layout under `src/`: `components/{Layout,TaskInput,TaskDisplay,Shared}` for UI, `hooks/useTaskData.ts` and `hooks/useCollaboration.ts` wrap Firebase reads/writes and presence, `store/` holds Redux Toolkit slices (`themeSlice`, tasks), `skins/themes/` ships `default`, `darkBlue`, and `altergo` themes plus a `types.ts` `ThemeType` contract that any new skin implements (`colors`, `text`, `animations`, `icons`). Styled Components reads the active theme via `ThemeProvider`; React Spring drives physics-based drop and destruction animations declared per theme. Vite + ESLint + strict TS configs; Firebase v9 modular SDK; samples and migration notes kept alongside `samples/`.

### Status
Internal continuation of the original spritz, last active April 2025. Reached feature parity then stalled — the personal SvelteKit version (`spritz-svelte`) took over as Alexandre's preferred surface. Not deployed publicly; lives in the org GitHub as the canonical React reference for the skin system idea.

## spritz-svelte

spritz-svelte is a SvelteKit 2 + Svelte 5 task app organised around spaces and boards, with collaborative rich-text inside cards via Yjs (`y-fire` Firestore provider, `y-quill`, `quill-cursors`). Firebase handles auth and data through dedicated services under `src/lib/services/firebase`; Stripe gates a 3.99 EUR/month Premium plan (free tier is capped at 1 space) with webhook + checkout + portal routes under `src/routes/api/stripe`. SendGrid and Resend send invitation emails, and the app ships on the Vercel adapter. Personal product experiment — real-time collab and the upgrade flow are wired end-to-end, not stubbed.

### What

Each user has a roster of spaces; a space holds boards; a board holds cards arranged in lists, with drag-and-drop (`svelte-dnd-action`, `sortablejs`) and rich-text descriptions. Cards open into a full editor where multiple users can type at once, see each other's cursors, and not stomp on each other's edits. Invite teammates by email, accept via a tokenised link, upgrade to Premium from the dashboard when the 1-space free cap bites.

### Tech

Yjs documents are persisted directly to Firestore through `y-fire`, no separate websocket server. Quill 2 hosts the editor, `y-quill` binds it to a Yjs `Text`, `quill-cursors` renders awareness. Firebase Admin (`firebase-admin`) backs the server-side routes; the Stripe stack is split between client (`@stripe/stripe-js`) and server checkout/portal/webhook routes under `src/routes/api/stripe`. Email goes through `@sendgrid/mail` and `resend` with `nodemailer` as fallback. Deployed via `@sveltejs/adapter-vercel`. Vitest + `@testing-library/svelte` for unit tests.

### Status

Started 2025, last commit 2026-02 ("Remove SpotifyPlayer component from SpaceHeader"). ~920 KB of Svelte source, private. The Spotify embed was dropped late in the run; the product surface is the spaces/boards/cards loop with collaborative editing and the paid tier, all wired end-to-end and never launched.
