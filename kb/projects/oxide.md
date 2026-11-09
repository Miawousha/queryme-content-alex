---
name: Oxide
description: "A native macOS workbench for git repositories of markdown: reader, live-preview editor, git surface and an AI layer over the Claude Code CLI."
year: 2026
url: https://github.com/Miawousha/oxide-releases
tags: &a1
  - desktop
  - tauri
  - rust
  - svelte
  - markdown
  - git
  - claude-code
repos:
  - name: oxide
    role: author
    visibility: private
    description: Native macOS markdown workbench on Tauri 2; reader, editor, git,
      repo map and AI, with signed public releases.
    year: 2026
    last_active: 2026-10
    language: Rust
    archived: false
    tags: *a1
---

Oxide is a local, native macOS application for repositories that are mostly markdown: docs, specs, notes, knowledge bases, agent instructions. It opens a folder, ideally a git repository, and combines a reader with careful typography, an editor where formatting appears as you type while the file on disk stays plain markdown, a git surface for status, diff, commit and sync, and a map of the repository as a graph. An AI layer runs on the user's installed Claude Code CLI, so there are no API keys or separate billing, and every suggestion arrives as a reviewable diff. Alexandre started it in July 2026 and has written about 1,100 commits; signed builds are published at github.com/Miawousha/oxide-releases.

## What

Reading covers CommonMark and GFM with wikilinks, relative links, highlighted code, a card for YAML frontmatter, local images and a floating table of contents. The editor is a hybrid live preview on CodeMirror 6: raw markdown reveals on the line being edited, autosave writes atomically, and a property test enforces that opening and saving a file without editing it is byte-identical. Navigation has fuzzy quick-open, a command palette, repository-wide search and backlinks.

The git surface stages by file or by hunk (by paragraph in prose), shows paragraph-anchored word diffs for markdown, syncs in one button (fetch, then push or rebase with autostash), switches and creates branches, resolves conflicts in the app, and shows history with blame. Discarding an untracked file sends it to the Trash rather than running `git clean`.

The AI layer has two tiers. Inline actions (improve, tighten, fix grammar, continue writing) stream editable proposals pinned to their range, from a subprocess that cannot read or write files. A per-repository agent chat can read and edit the working tree and cites its sources; its edits land as ordinary working-tree changes reviewed through the git surface, with shell commands and writes to `.git` denied. Commit messages can be drafted from the staged diff, and a per-repository kill switch is enforced in the adapter.

The map builds a knowledge graph live from folders, links and frontmatter, with an optional committed schema for types and relations, drill-down views and health signals (orphans, broken links, untyped documents). A bundled `oxide` CLI gives agents the same core: structure queries, a `check` lint with exit codes for CI, and safe writes such as a move that rewrites every inbound link.

## Tech

Tauri 2 with a Rust core and a Svelte 5 + TypeScript + Vite UI in WKWebView. The Rust workspace has a Tauri-free library crate (`oxide-core`: repository model, atomic file writes, link index, search, markdown rendering and sanitizing, git subprocess, diff engine, conflict parsing, AI adapters), the app crate and the CLI crate. The WebView never touches the disk, git or the network: it calls typed IPC commands whose TypeScript bindings are generated from Rust and checked for drift in CI. CI runs formatting, clippy, Rust tests, svelte-check and Vitest on Linux and macOS, and a release job on version tags. Releases are signed, and the app checks for updates at launch and every four hours.

## Status

All v1 milestones are closed, including the "Ship" milestone (typography, performance budgets, onboarding, release hardening) in August 2026; open work is tracked in a backlog. Latest public release 0.8.2 (October 2026). Targets macOS 14+ on Apple Silicon. The source is private; the release repository is public.
