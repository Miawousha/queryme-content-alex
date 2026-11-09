---
name: Aune
description: "An open method for reading French political programmes promise by promise, and Cpromis, the civic decision tool built on it for the 2027 presidential election."
year: 2026
tags: &a1
  - civic-tech
  - politics
  - ai-agents
  - nextjs
  - supabase
  - cli
url: https://cpromis.fr
repos:
  - name: aune
    role: author
    visibility: private
    description: Aune method and Cpromis site for reading, comparing and checking
      2027 presidential programmes, with external agents and human review.
    year: 2026
    last_active: 2026-10
    language: JavaScript
    archived: false
    tags: *a1
---

Aune is a method for reading French political programmes literally, promise by promise, built at Matrice Technologies for the 2027 presidential election. Cpromis is the public site that applies it: a civic decision tool that helps a person say what matters to them, examine the programmes and make their own choice. The method, the CLI and the published editions carry the Aune name; the site is Cpromis, online at cpromis.fr. The project is written in French and is tried in public as a method under construction.

## What

Every promise is put to the same four questions, with closed answers and written rules, so that every programme is read with the same grid. The site opens on three entry points: "Promis ?" (what a programme promises and how precisely), "Et vous ?" (a short profile of what the reader cares about) and "D'accord ?" (how a profile relates to the promises). Programmes are readable at six levels, from the whole programme down to the source behind a single verification, and one page per topic shows every programme's promises side by side, without totals or ranking.

The specification sets hard limits: no voting recommendation, no ranking of candidates, no overall score, no electoral prediction and no moral judgement of people. Every conclusion must cite an identified passage and criterion; uncertainty and abstention are valid results; a published edition never changes, and a correction creates a new one. A named person is responsible for each publication, and readers can contest a finding through a public form. "Mon profil" works without an account and compares in the page without sending anything; an account only stores a profile.

Analyses are drafted, reviewed and published by AI agents running in external sessions, through a CLI and a skill that the platform distributes. Aune hosts no agent. Contributors work in a separate space with screens for the corpus, review, editions and contestations. In October 2026 the roadmap moved the comparison from invented demonstration programmes to samples of real programmes, one per major political current, with twelve promises quoted verbatim across four topics (health, purchasing power, security and justice, energy and climate).

## Tech

A Next.js 16 and React 19 app in TypeScript, with shared and server modules in plain ES modules, shadcn on Base UI and Tailwind 4. It starts from Matrice's Next.js boilerplate, keeping its Supabase authentication, workspaces and row-level security. Editions follow a versioned format with a JSON Schema; scripts seal them by digest and verify them, and tests run with `node --test`. The agent CLI is built from an in-house tool package that bundles the CLI and its skill. Impact estimation started with a reference set of indicators and an OpenFisca proof of concept. A push to `main` rebuilds the public instance on Coolify, on a GCP host in Paris.

## Status

In active development from September 2026; last commit October 2026. The specification was at version 5.2.0 on 20 October 2026, and the documents state plainly that no rule of the method has yet been validated by measurement. Private repository; the site is public.
