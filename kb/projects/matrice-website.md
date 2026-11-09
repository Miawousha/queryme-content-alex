---
name: Matrice Website
year: 2026
tags: &a1
  - nextjs
  - react
  - typescript
  - supabase
repos:
  - name: matrice-website-v2
    role: author
    visibility: private
    description: Matrice Technologies' current site, rebuilt in October 2026, with
      service pages, a blog, an invite-only team area and client rooms (Next.js
      16 + Supabase, self-hosted on Coolify).
    year: 2026
    last_active: 2026-11
    language: TypeScript
    archived: false
    tags: *a1
  - name: matrice-website
    role: author
    visibility: private
    description: First version of Matrice's site, with a marketing landing, an
      invite-only team area and client rooms that render engagement repos live
      (Next.js 16 + Supabase, Playwright and Vitest covered).
    year: 2026
    last_active: 2026-08
    language: TypeScript
    archived: false
    tags: *a1
---

Matrice Website covers Matrice Technologies' public site and the private spaces behind it, across two private repositories. `matrice-website` (May to August 2026) is the first version: a marketing landing, an invite-only team area at `/app` and, from July 2026, client rooms. `matrice-website-v2` (started October 22, 2026) is a rebuild and is now the live site at matricetechnologies.com: new service pages and a blog, with the private area and the client rooms carried over from the first version. Both are Next.js 16 / React 19 apps on Supabase, tested with Vitest and Playwright.

## What

The public side of v2 has a home page, service pages (Ask Your Company, Build Your Academy, Build Your Digital Twin, Engineering), about, partners and careers pages, and a blog of articles on working with agents, several with interactive figures or playable demos (for example "Planning with Agents", "Work 2.0", "Introducing Wimym"). The interactive articles written for the first version's insights section were ported to it.

A client room, at `matricetechnologies.com/clients/<slug>`, is a gated space for one consulting engagement. Its content lives in the client's own engagement repository (`content/` and `README.md`) and is read live from that repository's `main` branch, so merging to `main` publishes a change within seconds, with no website deploy. A room shows the engagement's overview, plan, initiatives and KPIs, commercials as priced phases, meetings, documents (downloadable as branded PDFs), the client's org model, and a Map page that draws the links between documents, meetings, phases and initiatives as a force-directed graph. Client contacts get access through the invite system. The authoring contract for agents that write engagement repositories is published at `/clients/contribute/agents`, next to a pitch-deck guide and starter kit.

The invite-only `/app` area serves the Matrice team (knowledge base, graph, admin): admins issue and revoke invitations from `/app/admin`, and in v2 manage the client-room registry from `/app/admin/repos`.

## Tech

Access control comes from the first version: Supabase auth with `profiles` and `invites` tables under strict RLS, a `consume_invite` SECURITY DEFINER function that marks an invite consumed atomically only if it is unrevoked, unconsumed, unexpired and (when pinned) matches the user's email, and an internal endpoint that purges accounts that never consumed an invite. For client rooms, the site looks up the room's repository and branch in a registry, downloads the repository tarball over the GitHub API with a GitHub App token, builds the room from that snapshot and caches it under a per-room tag; a push webhook from the GitHub App invalidates the tag. A local mode (`CLIENTS_LOCAL_<SLUG>`) serves a room from a checkout on disk for previews. Every engagement repository runs a `validate-room` CI check against the authoring contract; the canonical validator lives in the website repository and a unit test pins it against the real room builders. The first version kept the registry in a JSON file and deployed on Vercel. v2 moves the registry into a Supabase `client_repos` table edited from the admin, offers Google and email sign-in, runs on a VPS deployed by Coolify alongside a self-hosted Supabase, and prints document PDFs through Gotenberg. The UI uses Tailwind 4, Base UI and shadcn/ui, with d3 for the graphs.

## Status

v2 is the live site, with active work through November 2026, mostly on blog articles. The first version has had no commits since August 2026. Both repositories are private and internal to Matrice.
