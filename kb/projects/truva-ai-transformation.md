---
name: Truva AI transformation
description: "Matrice's AI-transformation engagement with Truva, a Mumbai resale-homes platform: agent workstations, a conversation-intelligence platform, an operating-model kernel and the tools around them."
year: 2026
tags: &a1
  - ai-agents
  - claude
  - consulting
  - real-estate
  - nextjs
  - typescript
repos:
  - name: truva-mapper-agent
    role: author
    visibility: private
    description: Mapper v1, a society-mapping and valuation workstation where Claude
      agents propose and deterministic code applies, with a Next.js console, a
      worker and an operator CLI.
    year: 2026
    last_active: 2026-09
    language: TypeScript
    archived: false
    tags: *a1
  - name: truva-mapping-assistant
    role: author
    visibility: private
    description: Mapper v2, one versioned JSON document per housing society, edited
      in a Next.js app by a person and by Claude Code through a CLI.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags: *a1
  - name: truva-intelligence
    role: author
    visibility: private
    description: Conversation-intelligence platform that turns captured buyer and
      seller conversations into an evidence-linked picture of buyers, homes and
      deals.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags:
      - ai-agents
      - llm-extraction
      - supabase
      - nextjs
      - typescript
  - name: truval
    role: author
    visibility: private
    description: Valuation workstation, one versioned valuation per flat, priced by a
      port of Truva's own valuation arithmetic and worked in the browser or by
      Claude Code.
    year: 2026
    last_active: 2026-09
    language: TypeScript
    archived: false
    tags: *a1
  - name: truva-os
    role: author
    visibility: private
    description: Operating-model kernel for replicating Truva's business in new
      clusters, with JSON schemas, governance files and a browser manual.
    year: 2026
    last_active: 2026-08
    language: TypeScript
    archived: false
    tags:
      - operating-model
      - knowledge-base
      - json-schema
      - react
  - name: inox
    role: contributor
    visibility: private
    description: Matrice's Truva-branded deployment of the open-source Onyx search
      and agent platform, the index behind Truva Intelligence.
    year: 2026
    last_active: 2026-08
    language: Python
    archived: false
    tags:
      - onyx
      - rag
      - deployment
      - docker
  - name: inox-ask
    role: author
    visibility: private
    description: Dependency-free Node CLI that asks the Inox agents a question from
      the terminal and prints the answer with its citations.
    year: 2026
    last_active: 2026-08
    language: JavaScript
    archived: false
    tags:
      - cli
      - onyx
      - nodejs
  - name: sales-playbook
    role: author
    visibility: private
    description: First-principles playbook for resale-home seller and buyer calls,
      structured so an AI live call coach can cite it.
    year: 2026
    last_active: 2026-09
    language: Markdown
    archived: false
    tags:
      - sales
      - docs
      - ai-agents
  - name: truva-consulting
    role: author
    visibility: private
    description: Shared engagement repo whose content is published live as Truva's
      client room on the Matrice website.
    year: 2026
    last_active: 2026-09
    language: HTML
    archived: false
    tags:
      - consulting
      - docs
      - knowledge-base
  - name: truva-consulting-archive
    role: author
    visibility: private
    description: Earlier client-room repo for the engagement (July to early August),
      superseded by truva-consulting.
    year: 2026
    last_active: 2026-08
    language: HTML
    archived: false
    tags:
      - consulting
      - docs
  - name: truva
    url: https://github.com/Miawousha/truva
    role: author
    visibility: public
    description: Truva's organization model in the graybox ontology, built from
      public research and validated in CI.
    year: 2026
    last_active: 2026-07
    language: JSON
    archived: false
    tags:
      - ontology
      - graybox
      - organization-modeling
---

Between July and October 2026, Matrice Technologies, Alexandre's company, ran an AI-transformation engagement for Truva, a Mumbai platform for resale homes. It opened with discovery: an organization model of Truva written in Alexandre's graybox ontology from public research, and a shared client room where every document of the engagement was published for Truva to read. From August the work became a set of builds, each released weekly: Truva Intelligence, which records buyer and seller conversations and turns them into an evidence-linked picture of buyers, sellers, homes and deals, with Inox (a deployment of the open-source Onyx) indexing Truva's data underneath; Truva Academy, a training platform for Truva's staff (its own entry); Truva OS, the operating model written down as a versioned kernel; and agent workstations for mapping housing societies and valuing flats, which went through three repositories (mapper v1, mapper v2 and truval). Smaller pieces around them are a terminal client for the Inox agents and a sales-call playbook for an AI call coach. A few conventions hold across the builds: an agent's output is a proposal that deterministic code applies and a person approves, Truva's production data is read through a read-only, guarded connection and never written without a person signing, deployments run on Coolify behind Google sign-in, and every repository carries its working rules for Claude Code sessions in a `CLAUDE.md`.

## truva-mapper-agent and truva-mapping-assistant

The society mapper, in two versions. Truva's inventory is organised by housing society (towers, stacks, floor plans, units), and building that record by hand from brochures, floor plans and RERA filings is slow. Both repositories are workstations for that job; v1 (`truva-mapper-agent`, August 24 to September 16, about 1,380 commits) ran the agents on a server, and v2 (`truva-mapping-assistant`, September 16 to October 12, about 540 commits) moved the agent work into a Claude Code session on the mapper's own machine.

### What

**v1** is a workstation with two agents inside it. The society mapper takes a society name to a mapped inventory: a gather pass searches the web and the RERA register for the society's sources, a render step extracts each PDF's text, tables and figures, a vision pass reads the floor-plan plates, a judge forms the picture one tower at a time, and a verifier checks it against the same frozen sources. A person then authors over that picture on the society's page and publishes it one milestone at a time (tower list first, then each tower). The valuation agent takes a mapped unit through assemble, judge and verify to a proposal that a person approves. Every judgment a person has to make becomes a row in a review inbox, and every output stays a proposal until a person signs it.

**v2** keeps the domain and drops the server-side agents. Each society is one JSON document, versioned on the platform: every push is a new version with a message and an author, a push of named entities is refused only when someone else changed those same entities since its base, and nothing is deleted. A Claude Code session works the society through the `truva-mapper` CLI and a bundled `society-mapper` skill, one entity at a time with a source on every row; a person reads and edits the same document in the app, whose tables edit like a spreadsheet and whose drawings show each tower floor by floor. The app seeds a new society from Truva's existing records and compares the mapped version with them at any time, and a review step gates publication. In October the app was renamed Tru Storey and given its own logo.

### Tech

**v1** is a pnpm monorepo of a dozen packages with dependencies in one direction: `@mapper/core` (changeset schemas, the floors grammar, the milestone ladder, no I/O), `@mapper/corpus` (a content-addressed snapshot store and document rendering), `@mapper/db` (Prisma over its own MySQL database of 34 models, plus a SELECT-only reader for Truva's product database), `@mapper/valuation` (a deterministic port of Truva's pricing and comparables scoring, checked for parity against the original), `@mapper/harness`, `@mapper/sessions` (every node that calls a model), `@mapper/applier`, `@mapper/evals`, `@mapper/market` and `@mapper/desk`. The console is Next.js 15 with NextAuth, shadcn on Base UI and Cesium for maps; `aidesk` is a dependency-free HTTP client to the console's desk API with 54 commands. The deployed stack is six containers on Coolify: the agent database, the worker, the console, an SSH tunnel to the product database, docling-serve for PDFs and Crawl4AI for page captures.

**v2** is one Next.js 15 app (`web/`), a pure `@v2/society` package (schema, floors grammar, validation, normalisation, diff and the seed from Truva's records) and a single-file CLI with its installer and embedded skill. The store is SQLite (better-sqlite3) on the app's volume; Truva's database is reached through a guarded reader that allows one `SELECT` or `SHOW` at a time. An eval harness scores a mapped society against Truva's own rows. Vitest and strict TypeScript (`noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`) in both versions.

### Status

v1 ran on its deployed stack through the second of five milestones on a reference society, and its valuation pipeline was built as far as the verifier; neither wrote to Truva's system, since the applier was never issued a write credential. v2 succeeded it in mid-September, is deployed as a Coolify application behind Google sign-in, and was last committed to on October 12, 2026. Both private.

## truva-intelligence

### What

The platform that keeps a current, evidence-backed picture of Truva's buyers, sellers, homes and deals, and derives from it the insights and recommended actions that help sell a home. Its stated principles: raw conversations are kept verbatim and every derived fact links to its source; extraction is versioned and replayable; nothing writes to the CRM until extraction accuracy has been measured; capture is passive, so people do not change how they work to feed it; and the platform recommends while people decide. Shipped work by early October includes the app shell and invited accounts with roles, WhatsApp capture so each relationship manager sees their own threads, an insight catalogue, buyer preferences read as "must" or "wish" with the text they came from, a buyer-to-home matcher, places near each society, and an area editor where neighbourhood shapes are drawn, checked and ruled on by a person.

### Tech

A Next.js 15 app on Supabase (Postgres with PostGIS, 89 migrations), MapLibre and Cesium for maps, and a set of Node services: a worker, an insight engine where each model-backed insight is a typed, versioned definition and every execution is recorded verbatim, preference extraction with its own scoring harness, transcription tests, a Slack service and a LangChain agent proof of concept. Model calls go through the Anthropic SDK and Gemini. A `truva-intel` CLI with a Claude skill gives terminal access to buyer readings. The design runs in four layers: raw capture, normalised and linked threads, versioned extraction, and a live entity model whose current state is a fold over a transition log. Work is planned in a backlog of numbered work orders against a target-state document, following an sdlc method vendored into the repo.

### Status

Active August 7 to October 2, 2026, about 330 commits. Deployed and in first release; calls and transcription were the next capture sources. Private.

## truval

### What

A valuation workstation: one JSON valuation per flat, versioned in the app, worked by a person in the browser or by a Claude Code session through the `truval` CLI, each able to do the whole job alone. Both set inputs (facts, which comparable sales count and why, the adjustments left to the valuer, the confidence, the rules) and the engine works out the price. Only inputs are written; the platform recomputes the working into every stored version, so the history shows how each edit moved the price, and a write to a computed figure is refused with the input to set instead.

### Tech

It is mapper v2 rebuilt for valuations: a Next.js 15 app on SQLite, a pure `@truval/valuation` package (schema, validation, diff, the seed from Truva's records and `price.ts`, Truva's valuation arithmetic reproduced to the rupee and checked against its finalised valuations by a parity eval), and a CLI bundled by Matrice's `served-tool` package and served by the app itself. Scripts run under `TZ=Asia/Kolkata` because the engine's month arithmetic depends on local time. Deployed on the same host as the mapping assistant, behind Google sign-in, with poppler to render floor plans kept as PDFs.

### Status

Built between September 28 and 30, 2026 (about 150 commits). Private.

## truva-os

### What

The knowledge base Truva would use to replicate its business in new clusters: each new office, run end to end by a Cluster CEO, follows the same versioned kernel and builds its own local knowledge on top. The kernel describes an eight-stage deal loop, the roles and teams that own each stage, seven JSON schemas, governance files (limits and a metric register binding each metric to a reader) and a frozen vocabulary that every document and agent must use. Every file records whether it rests on Truva's own documents or on Matrice's design, and a runbook states which areas are grounded and which are scaffolding.

### Tech

Markdown and JSON under `kernel/`, a Python validator for the whole tree, and a React 19 / Vite 8 viewer opened by a `truvaos` command that renders the kernel as a manual in the browser, with tests for colour contrast and minimum font size. An office-simulation harness, where agents run synthetic offices as the kernel's integration test, is specified but not built.

### Status

Written August 13 to 18, 2026 (90 commits), and read as a repository with no deployed application. Further work was waiting on documents from Truva. Private.

## inox and inox-ask

### What

Inox is Matrice's deployment of [Onyx](https://github.com/onyx-dot-app/onyx), an open-source search and AI-agent platform, branded for Truva and used as the index behind Truva Intelligence: it indexes Truva's GitHub, Notion, Slack and WhatsApp sources and serves agents that answer with citations. Onyx itself is upstream work; the fork keeps its changes small and additive so upstream merges stay cheap. Those changes are the Truva branding as a token override, a read-only WhatsApp inbox connector that indexes conversations in fixed time buckets so document ids never shift, a raw archive that keeps the source payloads Onyx normally discards, a conversation explorer over that archive, and fixes to three upstream bugs. Alexandre's part is the deployment and configuration of the instance, not the fork's code or Onyx.

`inox-ask` is Alexandre's terminal client for that instance: `inox-ask "question"` sends a question to an Onyx agent and prints the synthesised answer with its citations as markdown links, so a person or a Claude Code session can ask how Truva does something without leaving the terminal. It reaches the agent instead of the raw index because the agent returns about a kilobyte of answer where the index search returns every matching document in full.

### Tech

Inox runs from Onyx's Docker Compose deployment with a local-dev overlay; the fork's additions are a Python connector and an Alembic migration on the backend and a few TypeScript files in the Next.js web app. `inox-ask` is a single dependency-free Node 20 script: it lists the agents an API key can see (with whether each can reach the web), continues a session by chaining on the last assistant message, and parses Onyx's streamed response by tracking brace depth across chunk boundaries, with a self-test that replays a stream split at every possible point.

### Status

Inox was forked and configured in mid-August 2026 and runs as the index for Truva Intelligence. `inox-ask` was written on August 17, 2026. Both private.

## sales-playbook

### What

A short playbook, meant to be read in about twenty minutes, for two kinds of call: owners thinking of selling and buyers who enquired about a listing. Seven principles apply to every call; each call type then has a call flow, a qualification list (what to learn and a good question for it) and an objection table. It is written so an AI coach listening to a live call can suggest the next move and cite the section it comes from.

### Tech

Markdown, one idea per heading so each heading is a citable section, plus a `coach.yaml` declaring the stages, qualification fields and objections the coach tracks for each call type.

### Status

Written on September 30, 2026. Private.

## truva-consulting

### What

The engagement's shared working repository, written for Truva to read. Its `content/` folder is rendered live as Truva's client room on the Matrice website, so merging to `main` publishes; a pull request is a draft. It holds the discovery, approach and build documents, a script-first pitch deck whose slides are checked against a reviewed storyboard before they are stitched, interactive HTML explainers, a script that drafts each week's release notes from the source changes in every build repository, and the specification of an acquisitions role-play trainer that preceded Truva Academy. The graybox organization model is included as a submodule and rendered as an interactive graph. `truva-consulting-archive` is the first version of the same client room, from July to early August, kept as an archive.

### Tech

Markdown with frontmatter following the client-room authoring contract, Node and Python build scripts for the deck and the embeds (fonts inlined, no third-party requests in the output), and a room validation script.

### Status

Active July 11 to September 10, 2026 (about 130 commits); the archive covers July 6 to August 7. Both private.

## truva (graybox model)

### What

Truva's organization model in graybox, Alexandre's ontology for describing organizations as typed, validated data. The model was built from public research and contains no client-confidential data. It covers 45 activities, 30 resources, 10 agents and 9 goals, plus structure, value-flow, governance and capability facets, including decision rights for the activities that need an approval.

### Tech

The graybox split-file layout: `org/org.json` plus one JSON file per entity. `graybox validate` checks referential integrity and the schema, `graybox lint` reports authoring debt, and `graybox report` writes a diagnosis. A GitHub Actions workflow runs the validator on every push and pull request once the graybox CLI is published.

### Status

Created June 26, 2026 and retrofitted to ontology 0.2.0 on July 13, 2026. Public, and used as a submodule of the client room.
