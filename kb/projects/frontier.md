---
name: Frontier (sdlc)
description: "A repository-local method and read-only checker for coordinating agentic development, plus a shared package for apps that serve their own CLI and skill to Claude Code."
year: 2026
tags: &a1
  - agents
  - claude-code
  - methodology
  - python
  - cli
  - developer-tools
repos:
  - name: frontier
    role: author
    visibility: private
    description: Repository-local "sdlc" method for coordinating agentic work
      (BIGPICTURE, BACKLOG) with a dependency-free Python checker.
    year: 2026
    last_active: 2026-10
    language: Python
    archived: false
    tags: *a1
  - name: served-tool
    role: author
    visibility: private
    description: Shared package for apps that serve their own CLI and skill to a
      Claude Code session and mint its key through a device flow.
    year: 2026
    last_active: 2026-10
    language: JavaScript
    archived: false
    tags:
      - claude-code
      - cli
      - device-flow
      - nodejs
      - npm
---

Two pieces of Matrice Technologies' tooling for agentic work. Frontier is a small method for coordinating several agents (and people) on the same repository, through documents kept in the repository itself. served-tool is the package that lets a web app hand its own CLI and Claude Code skill to an agent session.

## What

The method keeps product intent in `BIGPICTURE.md`, work items in `BACKLOG.md`, and decisions that later sessions need beside the code. Agents claim items, declare dependencies, file footprints and handoffs, so any session can pick up a piece of work without the conversation that started it. Work is sized by outcome rather than by session: past half the context window, a session hands off and a fresh one continues the same item.

A checker reads those documents and reports ready work (the "frontier"), blockers, declared file overlaps and structural errors, with `--find`, `--trace`, `--progress`, `--graph` and `--json` queries. It does not claim to prove that a feature works or that parallel changes are safe. Projects adopt the method by copying a released `sdlc/` folder into their root (`git archive vN.N.N sdlc`); a manifest of hashes detects local modifications. Frontier runs the method on itself, and stigmatic is one of the projects that vendor it.

## Tech

The checker is a single Python script (Python 3.8+ and Git, no dependencies) with its own test runner over fixtures and mutated instances. The method itself is three documents: BOOT (entry steps), PROCESS (coordination, completion, artifact upkeep) and SYNTAX (the fields), plus templates. The tool has no daemon, network access, write surface or dashboard. MIT licence.

## Status

Private repository, created in July 2026. The first release shipped on 23 July 2026 and the folder became its own versioned unit with v1.0.0 on 30 July. v6.0.0 (29 September and 2 October 2026) cut the method back to a lean core: plans, specs, audits and verification vouchers became optional, and agents choose their own reading and planning. Last activity in October 2026.

## served-tool

### What

served-tool gathers what every Matrice app needs when it serves its own CLI and skill to a Claude Code session: the CLI core (`login`, `whoami`, `version`, `upgrade`, `skill --install`, `help`, plus the project's own commands), the server-side decisions of a device-flow login and its key store, and a build step that bundles the CLI and stamps the skill and two version counts into one served file. Because the app serves the tool, a deployment and the tool that talks to it never disagree, and `upgrade` fetches whichever newer CLI and skill the deployment serves. Version 0.2 added options so that an existing tool (Fixit) could move onto it: publication to npm as well, a login in two commands (`--begin`, `--finish`) because an agent sees a command's output only when it ends, a skill installed per repository, and the environment variable names and config file a tool's users already had.

### Tech

An ES module package with no runtime dependency, Node 20 or later, with four entry points: `/cli`, `/server` (login and key operations over a store interface, with an in-memory store), `/build` (esbuild bundling and embedding, plus a `served-tool` binary) and `/guides` (renders a skill's Markdown files as pages an app can draw). The contract between app and tool, including the device-flow routes and their statuses, is written down in `contract.md`. Tests use `node --test` with a fake clock, a fake platform and a fake disk. Published to npm as `@matrice-technologies/served-tool` under the MIT licence.

### Status

Private repository, created on 22 September 2026. Version 0.2.1, released on 3 October 2026, fixed long output being cut at 64 KiB when piped on macOS. Fixit builds its CLI on it.
