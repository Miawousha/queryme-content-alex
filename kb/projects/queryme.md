---
name: Queritae
description: "A multi-tenant queryable-CV platform: each account's knowledge base lives in its own GitHub repo and answers recruiter and AI-agent questions with citations, over web chat and MCP."
year: 2026
stack:
  - TypeScript
  - Next.js
  - Vercel AI SDK
tags:
  - ai
  - open-source
  - personal
url: https://github.com/Miawousha/queryme
repos:
  - name: queryme
    url: https://github.com/Miawousha/queryme
    role: author
    visibility: public
    description: Multi-tenant queryable-CV app that syncs each account's content
      repo and answers questions from it, with citations, over web chat and MCP.
    year: 2026
    last_active: 2026-11
    language: TypeScript
    archived: false
    tags:
      - ai
      - agent
      - mcp
      - typescript
      - nextjs
---

## Summary
A queryable CV. A person's knowledge base (structured YAML facts and Markdown stories) and the agent's system prompt live in a public GitHub content repository; the app syncs that repository and answers questions from recruiters and AI agents over a web chat and an MCP server, with citations that point to the source files. The knowledge base, the system prompt and the code are all open source. Since June 2026 the app is multi-tenant: it holds no content of its own and serves any number of accounts, each backed by its own content repository.

## Why it exists
Two reasons. First, recruiting workflows are increasingly delegated to AI agents; a static CV is a poor fit for that interface. Second, transparency about what an agent "knows" about you is a trust problem worth solving up front.

## What
Each account is served at `/{username}`, with a house account at the root domain. People sign up with GitHub OAuth: the first sign-in creates an account named after the GitHub login. Self-serve signups first went through a waitlist approved by a super-admin; since June 22, 2026 new accounts are active immediately, and the waitlist and disabled statuses remain as admin controls in the cross-account `/admin` console. Owners manage their own account at `/{username}/admin`, and accept the terms of service at first login.

A GitHub App connects a content repository in one install, after which every push re-syncs it automatically; the earlier per-account manual webhook was removed. An account without content is guided through setup: the admin generates a prompt for the owner's coding agent that carries a scoped setup token (HMAC-signed, valid for one hour), so the agent can register the content repository it built without a browser session. A content repository can also declare its own collections (notes, glossary, writing and so on) in a `content.config.yaml` file; without one, a resume preset applies and the assembled prompt is unchanged.

Other additions over the same period: the platform injects its own citation instruction into the system prompt, so cited answers no longer depend on each owner's prompt; the knowledge-base panel shows an outline with cited sections marked and hover previews; each account gets a printable CV with an optional photo and a QR code; usage is metered per account with daily and monthly quotas and spend alerts by email; Stripe billing defines a free plan and a pro plan (which adds custom domains). In November 2026 the interface was restyled to follow the design language of the Matrice website v2.

## Tech
Next.js with the Vercel AI SDK and Anthropic prompt caching, Postgres (Neon) and Upstash Redis for persistence, Resend for email, Stripe for billing, and a golden-question eval suite run against the live model. The MCP endpoint currently serves the house account only.

## Status
Most of the work happened in May and June 2026, followed by the design refresh in November 2026. The roadmap still lists impersonation guardrails for usernames and custom domains before a public launch, then onboarding work such as a template content repository and a CV importer.
