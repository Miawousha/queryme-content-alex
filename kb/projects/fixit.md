---
name: Fixit
description: "Feedback capture for web apps: a widget sends annotated bug reports with console, network, screenshot and DOM replay to an inbox that people triage and coding agents work through."
year: 2026
tags: &a1
  - agents
  - claude-code
  - feedback
  - nextjs
  - typescript
  - supabase
  - mcp
url: https://fixit.matricetechnologies.com
repos:
  - name: fixit
    role: author
    visibility: private
    description: Feedback capture platform with an embeddable widget, a triage
      dashboard, an agent API, an MCP server, a CLI and a Claude Code skill.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags: *a1
  - name: skills
    url: https://github.com/matrice-technologies/skills
    role: author
    visibility: public
    description: Public agent skills for Fixit, installable with the `skills`
      installer; now retired in favour of the skill served by the app.
    year: 2026
    last_active: 2026-08
    language: Markdown
    archived: true
    tags:
      - agents
      - skills
      - claude-code
---

Fixit is Matrice Technologies' feedback capture platform for web apps, hosted at fixit.matricetechnologies.com. A widget in the corner of a site lets whoever found a problem point at it, draw on it and send it. The report that reaches the project's inbox carries the note, the element pointed at, the console output, the failed requests, a screenshot and a DOM replay. People triage reports in a dashboard, and coding agents work through them with a CLI and its Claude Code skill.

## What

Connecting a repository takes a CLI installed from the app, a browser login and `/fixit setup` in Claude Code, which places the widget where the project's stack loads third-party scripts; each project's Setup page also gives a ready prompt for a coding agent. From then on an agent can answer questions from the inbox ("the last 3 reports"), or take a report by its id, claim it, fix the cause, verify and release it. CI uses the same CLI from npm with a token created in the dashboard.

## Tech

An npm workspaces monorepo in TypeScript. `apps/web` is a Next.js 16 and React 19 app holding the dashboard, the ingest API, the agent API and the CLI installer. `packages/widget` is the embeddable script, written without a framework and recording DOM replays with rrweb. `packages/shared` holds Zod schemas and generated database types, `packages/client` is the REST client shared by the CLI and `packages/mcp`, an MCP server for agents. The CLI is built on served-tool into one committed script that the app serves at `/api/cli/*` and that is also published to npm as `@matrice-technologies/fixit-cli`, so both copies run the same bytes. Data lives in a self-hosted Supabase (Postgres), and the web app is deployed as a Docker image.

## Status

Private repository, created on 10 August 2026. In early October 2026 the CLI was rebuilt on served-tool 0.2 and is now served by the app itself, which retired the public skills mirror. Last activity in October 2026.

## skills

### What

A public repository that published the Fixit agent skill for installation with `npx skills add matrice-technologies/skills`, which works with Claude Code, Cursor, Codex, OpenCode and other agents supported by that installer. The skill drives the Fixit CLI for setup, inbox questions and fixing reports.

### Tech

A single `skills/fixit/SKILL.md`, synced automatically from the Fixit repository rather than edited in place.

### Status

Active from 10 to 12 August 2026, then retired and archived once the skill shipped inside the CLI served by the Fixit app (`fixit skill --install`).
