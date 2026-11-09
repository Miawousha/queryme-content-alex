---
name: Massistant
description: "A WhatsApp bridge to Claude Code on a Mac: start and drive sessions by text, voice note or phone call, with a personal assistant that remembers, and a menu bar app around it."
year: 2026
tags: &a1
  - agents
  - claude-code
  - rust
  - whatsapp
  - voice
  - macos
  - swift
repos:
  - name: matrice-assistant
    role: author
    visibility: private
    description: matrice-bridge, one Rust binary that drives Claude Code sessions
      on a Mac from WhatsApp, with voice calls, wrapped in the Massistant menu
      bar app.
    year: 2026
    last_active: 2026-11
    language: Rust
    archived: false
    tags: *a1
---

Massistant lets Alexandre drive Claude Code on his Mac from his phone. A dedicated WhatsApp number, linked as a device, receives his messages, and `matrice-bridge`, a single Rust binary, turns them into real `claude` CLI sessions running under his claude.ai subscription rather than an API key. Permission prompts come back to WhatsApp and are answered there. The bridge ships inside Massistant, a native macOS menu bar app with its own window.

## What

From WhatsApp, `/new api api fix the failing auth tests` starts a session named `api` in a project folder; later messages go to the current session, to a named one (`api: …`), or to the session a quote-reply points at. `/ls`, `/peek`, `/stop`, `/fresh` and `/mv` list, inspect, interrupt, restart and rename sessions. Voice notes are transcribed and routed like text, photos are passed on with their caption, and approvals are answered with `y`, `n` plus a reason, or `a` (always allow), by text only.

Without a session, messages go to a standing assistant: one ongoing Claude Code conversation in its own folder, with a memory of preferences and promises, a knowledge base of people, companies and projects that the bridge updates between conversations, and a configurable name, picture, voice and persona. Its capabilities are listed and switched on or off in the app.

Calls are the other channel. Calling the bridge number, or asking Claude to call back when a task is done, starts a spoken conversation in French or English with live transcription and replies spoken a sentence at a time; tasks asked for during the call are carried out after hanging up, followed by one text summing up the call. Calls can also run through OpenAI's GPT-Live voice model. The assistant can phone or text a short list of approved contacts on Alexandre's behalf, through a locked-down session that can only talk. Later additions include meetings recorded at the Mac and written up from the transcript, a voice conversation opened with a keyboard shortcut, reminders, and read-only access to his own WhatsApp and mail.

## Tech

The bridge is Rust on tokio, using the `whatsapp-rust` client library for the linked device (with a patched `wacore` for call diagnostics), `rusqlite`, `reqwest` and WebSockets. Each Claude Code turn runs `claude -p` with stream-json in and out; the assistant and a call's session keep one long-lived `claude` process so a turn does not respawn it. An MCP server inside the bridge handles approvals over a Unix socket and gives Claude tools such as `call_me`, `call_contact` and settings changes. Speech goes through ElevenLabs or OpenAI for transcription and synthesis. The menu bar app is Swift. A ship script builds the app once into a shared cache; a running bridge notices a new binary, waits until no turn or approval is pending, restarts itself and says so on WhatsApp.

Safety rules are explicit: only allowlisted numbers are answered, sessions run only under configured workspace roots, Claude runs in a chosen permission mode with unanswered prompts denied after a timeout, and anything reaching other people that was started by a contact's words, not Alexandre's, waits for his approval. The README advises using a dedicated number, since the WhatsApp client is unofficial.

## Status

Private repository, created on 16 October 2026 and running on Alexandre's Mac. It was shipped five times on 3 November 2026 alone; the last recorded ship and merge (pull request #16) is from 3 November 2026.
