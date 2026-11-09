---
name: Polish
description: "A tray app that rewrites selected text in any application with Claude or another model, one global shortcut per prompt."
year: 2026
tags: &a1
  - desktop
  - electron
  - typescript
  - llm
  - open-source
  - productivity
url: https://github.com/matrice-technologies/polish
repos:
  - name: polish
    url: https://github.com/matrice-technologies/polish
    role: author
    visibility: public
    description: Tray app that polishes the selected text in any app with Claude,
      then pastes the result over the selection.
    year: 2026
    last_active: 2026-11
    language: TypeScript
    archived: false
    tags: *a1
---

Polish is a desktop tray app from Matrice Technologies: select text in any application, press a shortcut, and the text comes back rewritten. Each prompt ("Polish", "Shorter", "Professional", and the person's own) has its own global shortcut; the others are reachable from a picker. It works without an account and without the Polish server: the text goes straight from the computer to the model provider the person chose.

## What

Pressing a shortcut copies the selection from whichever app has focus, sends it to the model with that prompt's instructions, pastes the result over the selection and restores the clipboard. Three kinds of provider are supported: the person's own Claude subscription through Claude Code installed on the same machine (no API key), an API key for Anthropic, OpenAI, Google Gemini or xAI Grok, or any OpenAI-compatible endpoint, including local models through Ollama or LM Studio. Signing in is optional and only adds sync of prompts, shortcuts and settings between machines, plus editing them on the web. Provider keys stay on each device.

## Tech

An npm workspaces monorepo in TypeScript. `apps/desktop` is the Electron app (tray, global shortcuts, picker, the copy, rewrite and paste cycle); `apps/web` is a Next.js app for sign-in, the prompt editor, settings, desktop sign-in and the website; `packages/shared` holds the prompt and settings schemas, shortcut parsing, the sync merge and the system prompt; Supabase stores accounts with row-level security. Reading a selection goes through the clipboard with a sentinel value, and keystrokes are posted with `uiohook-napi`. On macOS a small Swift helper registers Carbon hot keys by key position so shortcuts work on non-QWERTY layouts such as AZERTY. The subscription mode runs `claude -p` with no tools, no settings, no MCP servers and no saved session, in an empty directory. Sync is offline-first: the local file is the source of truth and prompts merge one by one, newest edit wins, with tombstones for deletions. The desktop app signs in through a device flow. Keys are encrypted with the OS keychain. Releases are built by GitHub Actions for Windows and macOS (Apple Silicon and Intel) and installed copies update themselves.

## Status

Public repository under the MIT licence, created on 30 October 2026, with a hosted instance at polish.matricetechnologies.com. Version 0.1.3 was the first signed and notarized macOS build; 0.1.5, released on 1 November 2026, is the latest. Not done yet: Wayland support on Linux and Windows code signing.
