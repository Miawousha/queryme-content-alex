---
name: stigmatic
description: "A local mission-control Mac app for running many Claude Code sessions across many projects: what needs you, live sessions, git state and the sdlc backlog, with controls to answer, dispatch and merge."
year: 2026
tags: &a1
  - agents
  - claude-code
  - rust
  - tauri
  - svelte
  - developer-tools
  - local-first
repos:
  - name: stigmatic
    role: author
    visibility: private
    description: Local mission-control Mac app for watching and acting on Claude
      Code sessions, git worktrees and sdlc backlogs on one machine.
    year: 2026
    last_active: 2026-10
    language: Rust
    archived: false
    tags: *a1
---

stigmatic is a Mac app built at Matrice Technologies for one person running many Claude Code sessions across ten or more projects at once. It watches every session on the machine, the git and worktree state of each repository, and the backlog of projects that use the sdlc method (see Frontier), and it opens on what needs the human: sessions waiting on an answer, work left unfinished, broken checks. It listens on loopback only (`127.0.0.1:7844`) and serves a single user.

## What

The home lists what needs you across every project. Picking a project switches to a cockpit where every view answers for that project alone: live sessions, git and worktree state, and the sdlc boards (frontier, progress, releases). Each session page says where the work was left: the last request, the last reply and the files changed. Retrospective figures (activity, spend, progress of the method) live apart in an Analytics area.

The app also acts, one click at a time: go to a session, answer a resting session (it resumes it with `claude -p --resume`), dispatch a ready backlog item into its own git worktree with a headless Claude Code session, then merge and clean up after it, with a native dialog before anything is merged into main. Two larger modes build on this. A dispatcher run takes a budget, dispatches ready items across projects, has a verifier subagent check each finished branch, merges what passes and parks what fails. The coordinator is one Claude session you talk with about all your projects; it acts only on what was agreed in the conversation. The same dispatch, merge, answer and stop commands are available from a terminal through `bin/stig`.

## Tech

A Rust workspace with two crates. `core/` (tokio, axum, notify) is the data plane: it tails Claude Code JSONL transcripts, derives each session's liveness, reads git state, reads sdlc state only through the checker's `--json` output, and pushes typed events over server-sent events. The core is read-only by construction: no mutating routes and no disk writes, enforced by tests. `app/` is a Tauri 2 shell that embeds the core and holds the only code that spawns processes or writes, behind a small set of named commands only the app's own window can call. The interface in `ui/` is Svelte 5 with TypeScript, Vite and Tailwind v4, built on one design system of shadcn-svelte components and tokens. Tests combine `cargo test` and clippy, vitest and svelte-check, a Playwright smoke suite on Chromium and WebKit over a fixture corpus, and a frozen golden corpus that recorded the parity between the Rust core and the earlier Node server it replaced.

## Status

Private repository, built with its own sdlc method (BIGPICTURE and BACKLOG in the repo). The backlog records releases from R1 (live session wall, 24 July 2026) through the Rust core and the Mac app replacing the Node server (R12 and R13, 2 October 2026), the controls (R17), the dispatcher (R20) and the coordinator (R22 and R23, 7 October 2026). Next on the backlog is watching Codex and OpenCode sessions. Distribution, signing and notarization are explicit non-goals: the app runs from its own checkout.
