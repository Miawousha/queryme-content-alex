---
name: Gister
description: "Local meeting memory for in-person meetings: records the room, transcribes and diarizes it with Gemini, and is designed to keep a living plan and a decision log."
year: 2026
tags: &a1
  - rust
  - audio
  - tauri
  - gemini
  - local-first
  - sqlite
repos:
  - name: gister
    role: author
    visibility: private
    description: Local meeting recorder for physical meetings, with a Rust audio
      core and Gemini transcription.
    year: 2026
    last_active: 2026-08
    language: Rust
    archived: false
    tags: *a1
---

Gister is a meeting memory for physical, in-person meetings, started at Matrice Technologies in August 2026. It records the room from a laptop microphone, transcribes and separates speakers with Gemini, and is designed to keep a living plan and a decision log with the reasoning attached, so that weeks later one can ask what the plan is, why a decision was taken and what it replaced. It is local-first: the user's machine, the user's own Gemini API key, no accounts and no server.

## What

The design rests on one open question: whether Gemini can tell speakers apart well enough from a single laptop microphone, without a local voice-embedding model. The evaluation harness that answers it was therefore built before the interface. It replays hand-labelled recordings through the production chunker and scores speaker error rate and word error rate, and its thresholds decide the architecture: below 15% the design stands, between 15% and 30% speaker naming becomes mandatory, above 30% local voice embeddings move into the first version.

What runs today is a small always-on-top recording capsule. Audio is captured, resampled to 16 kHz mono, cut on silences rather than on a clock, and written incrementally to Ogg/Opus. Each chunk is queued on disk, sent to Gemini in the background and committed to a local SQLite store with full-text search. A recording survives a crash or a closed app: the queue resumes on the next launch. Decision extraction, speaker naming, questions over past meetings and an in-app transcript reader are not built yet.

## Tech

A Rust workspace of five crates: `audio` (cpal capture, resampling, Silero voice activity detection, a silence-aware chunker with a 20 s target and 35 s ceiling, Opus writer fsynced about once a second, no network code), `transcribe` (the Gemini client, with failures classified as retryable, malformed or permanent and one repair attempt on malformed output), `store` (SQLite schema and migrations, an FTS5 index, a durable chunk queue, overlap deduplication and startup recovery), `app` (the Tauri v2 shell, recording session and background uploader) and `eval` (the diarization scorer and its CLI gate). The capsule UI is a Next.js and React page inside the Tauri webview; the clock and level meter come from Rust so that reloading the window does not lose a recording. The API key is read from the system keychain, then from the environment. The README reports 171 Rust tests passing with 11 ignored (device or network), clean clippy and rustfmt, and a separate frontend test suite.

## Status

Built over 17 to 19 August 2026, private, early stage. The capsule records and transcribes in the background, but the evaluation gate has not been run on real meetings yet, and transcripts can only be read with `sqlite3` against the store.
