---
name: Graybox
description: "A literature-grounded meta-ontology for modeling organizations as typed, validated data, with a local CLI, a graph explorer and a hosted viewer."
year: 2026
tags: &a1
  - ontology
  - typescript
  - zod
  - cli
  - nextjs
  - d3
repos:
  - name: graybox
    role: author
    visibility: private
    description: A literature-grounded meta-ontology for modeling organizations as
      typed, validated data, with a local CLI, a graph explorer and a hosted
      viewer.
    year: 2026
    last_active: 2026-08
    language: TypeScript
    archived: false
    tags: *a1
---

Graybox is a literature-grounded meta-ontology for businesses and organizations: a typed vocabulary (agents, resources, activities, goals, relations, boundaries, plus eight facets covering structure, value flow, operations, capability, environment, governance, delegation and knowledge) that lets any organization be described as checked, machine-readable data. Org models are JSON files kept in a git repository the user owns. They are written and queried with a local CLI, by a human or by a local agent such as Claude, explored in a React/D3 explorer, and can be browsed in a hosted Next.js viewer that reads them from GitHub without storing them.

## What

The unit is the org model: a set of JSON files describing an organization through typed core entities and eight analytical facets (the operations facet was called coordination until July 2026). Since June 2026 the schema gained the governance, delegation and knowledge facets, decision rights, and a goal "why-spine" (goal kind, owner, stakeholders served) that links the mission to strategic and operational goals and down to activities. Models are validated against a strict schema, checked by lint rules (for example an approval with no approver, a goal with no owner, a control loop with no operator) and queried with questions such as who is responsible for an activity, who decides, what applies to an activity, or what a resource change affects. A `report` command writes a Markdown diagnosis with sections on purpose, decision rights, oversight, delegation readiness and freshness. A fictional electronics manufacturer, Voltforge, is the reference demo org. Graybox was used to model a client organization during a Matrice consulting engagement.

## Tech

A TypeScript/ESM monorepo. `@graybox/ontology` is the source of truth: a Zod schema with inferred types, `validateOrg`, `ingest`, lint and query functions, and on-demand `toJsonSchema()`; every object is `.strict()`, so unknown fields fail validation. `@graybox/cli` provides the `graybox` command, which runs offline: create, list and show orgs, edit verbs (`add`, `set`, `rm`, `link`, `unlink`, `rename`) that re-validate after every write, query verbs, `lint`, `report`, and `init-repo`, which scaffolds a per-organization repo with agent skills for extracting (`extract-org`) or designing (`design-org`) a model. Both packages are published to npm. `viz` is a React/D3 explorer that renders a model as a graph, with a navigation mode that follows the goal hierarchy through the operating model. `web` is a Next.js App Router app for the hosted viewer: sign-in through a GitHub App, a repository picker, org assembly from the repository tarball (streamed, size-capped and cached on the repository's last push), a signed-out `/demo` route on Voltforge, per-IP rate limiting and security headers. It runs as a Docker container on Coolify, and its only database is an optional waitlist table. Tooling is vitest + tsx and requires Node >= 20.

## Status

The original "local-first, no hosted backend" constraint was revised at the end of June 2026: org data still lives only in the user's git repository and the CLI works without a network, but a hosted viewer now sits in front of those repositories. The latest work, in August 2026, made Voltforge a demo org that can be opened in the viewer without signing in. Private repository.
