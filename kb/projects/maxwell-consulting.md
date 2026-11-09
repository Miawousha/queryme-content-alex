---
name: Maxwell Energy Systems (mxwl) consulting engagement
description: "Matrice's AI-enablement engagement for Maxwell Energy Systems (mxwl), the battery-management company Alexandre co-founded: an operating knowledge base and agent workflows for embedded engineering, validation and program delivery, scoped in a shared client room."
year: 2026
tags: &a1
  - consulting
  - ai-agents
  - battery
  - firmware
  - knowledge-base
  - docs
repos:
  - name: maxwell-consulting
    role: author
    visibility: private
    description: Shared engagement repo whose content is published live as Maxwell's
      client room on the Matrice website, holding the engagement proposal, its
      supporting documents and a presentation deck.
    year: 2026
    last_active: 2026-09
    language: HTML
    archived: false
    tags: *a1
---

In August 2026, Matrice Technologies, Alexandre's company, prepared an AI-enablement engagement for Maxwell Energy Systems (mxwl), the battery-management systems company he co-founded and where he was CTO until March 2025 (see his Maxwell experience entry). The engagement was scoped in a shared working repository that Maxwell reads directly and that is published as a client room on the Matrice website. The proposal rests on Alexandre's prior knowledge of Maxwell's platforms and code: there is no separate audit phase, and the first month is spent establishing what has changed since he left and choosing the platforms and programs the work applies to. The repository was active from August 10 to September 1, 2026 (67 commits) and covers the scoping and agreement of the engagement, not its delivery.

## What

The engagement's stated aim is to reduce the cost and cycle time of delivering a customer program, from request for quotation to start of production, by having agents take on the structured, traceable, document-heavy work of a regulated automotive supplier, with people reviewing everything they produce. Its second aim is that Maxwell's engineers learn to direct and review agents on their own work, so the method keeps running after the engagement ends.

The plan has one running thread and four workstreams:

- **An operating knowledge base**: a structured, machine-readable account of Maxwell's platforms and variant families, requirements, processes, ownership and quality bars, built with graybox (Alexandre's organization-modeling toolchain), seeded from what Alexandre already knows and corrected in working sessions with the engineering leads. It comes first because it is the context every agent workflow depends on.
- **Agent-native embedded engineering**: coding agents in the embedded team's real workflow, for comprehension and documentation of legacy firmware, variant porting, driver and platform migration, static analysis and MISRA remediation, and code review, starting on platforms that carry live programs.
- **Validation and safety artifacts**: generation and triage of test cases, hardware-in-the-loop test scripts, failure analysis and requirement-to-test traceability, to the evidence standards of ISO 26262, AIS-156 and Automotive SPICE (ASPICE), with every artifact on a safety or assessment path reviewed by a person and the review recorded.
- **Program delivery**: ingestion of customer specifications, gap analysis against the existing platform portfolio, documentation packs and ASPICE readiness gap analyses, run on a real customer opportunity.
- **Manager of agents**: training by function, where each participant ships reviewed work through an agent workflow on their own tasks.

Alongside these sit two decisions in Alexandre's former remit: a keep, rebuild, retire or buy recommendation on Maxwell's existing software products, and a target architecture for its connected battery software, designed for agents from the start. Progress is judged on artifacts that can be checked by looking at them (documents, workflows in use, reviewed work shipped by named engineers) rather than on KPI baselines Maxwell does not measure, with monthly reviews deciding whether each workstream continues, changes direction or stops.

What the repository contains: a page explaining how the room works, the engagement proposal through five revisions, its supporting documents, two figures (the two agent workflows and the six-month plan) and an eight-slide presentation deck.

## Tech

The repository is the engagement's single source for people and agents alike. The Matrice website reads its `content/` folder from `main` at request time and renders it as the client room, so merging to `main` publishes within seconds and a pull request serves as a draft. Every file, branch name and commit message is written for Maxwell to read; Matrice's internal working material is kept in a separate repository unconnected to the room. `CLAUDE.md` and `AGENTS.md` both point to the README, which holds the working rules for humans and agents, and a `writing-style.md` sets the plain-English rules that apply to documents, commits and pull requests alike.

A GitHub Actions workflow gates `main` with the room validator (a byte-identical copy of the canonical one in the Matrice website repository) and checks that the figures are current. Figures are kept as SVG sources and inlined into the Markdown as `data:` URIs by a script, since that is the only image form that renders in the room, in the room's PDF export and in the local PDF build. A dependency-free Node script prints the proposal to a branded PDF through the local Chrome, reading where each section landed from the PDF's named destinations to fill in an exact table of contents. The deck is built from one HTML fragment per slide, checked against a written script whose headings must match the slide titles, with fonts embedded and no third-party requests, and published in the room as a self-contained page.

## Status

The proposal was finalized with Maxwell at the end of August 2026. The repository was last updated on September 1, 2026, and holds no delivery documents after the scoping phase. Private.
