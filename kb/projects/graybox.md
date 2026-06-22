---
name: Graybox
description: "A local-first, literature-grounded meta-ontology for modeling organizations as typed, validated data."
year: 2026
tags: &a1
  - ontology
  - typescript
  - zod
  - local-first
  - cli
repos:
  - name: graybox
    role: author
    visibility: private
    description: A local-first, literature-grounded meta-ontology for modeling
      organizations as typed, validated data.
    year: 2026
    last_active: 2026-06
    language: TypeScript
    archived: false
    tags: *a1
---

Graybox is a local-first, literature-grounded meta-ontology for businesses and organizations: a typed vocabulary (agents, resources, activities, goals, relations, boundaries, plus five facets covering structure, value flow, coordination, capability and environment) that lets any organization be described as checked, machine-readable data. A local agent (e.g. Claude via the CLI) and humans (a React/D3 explorer) author, edit and validate org models entirely on the user's machine, with no hosted backend.

## What

The unit is the org model: a JSON document describing an organization through typed core entities (agents, resources, activities, goals, relations, boundaries) and five analytical facets (structure, value flow, coordination, capability, environment). Models are validated against a strict schema and explored as a graph, and are meant to be authored collaboratively by a human and a local AI agent. A canonical corpus of example orgs (bakery, hospital, manufacturer, SaaS startup) ships alongside the schema.

## Tech

A TypeScript/ESM monorepo. The source of truth is `@graybox/ontology`, a Zod schema with inferred types, a `validateOrg` checker, an `ingest` path and on-demand `toJsonSchema()` emission; every object is `.strict()`, so unknown fields fail validation. A `validate` CLI checks org JSON files, and a React/D3 explorer (`viz`) reads the corpus and renders each organization as an interactive graph. Tooling is vitest + tsx and requires Node >= 20. Local-first is a standing constraint: no hosted backend, and no remote APIs planned.

## Status

Phase 2 complete as of June 2026: the core is fully TypeScript/Zod and the earlier Python implementation has been retired. Private repository, in active development.
