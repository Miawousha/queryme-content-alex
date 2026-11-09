---
name: Wimym
description: "Where is your mind: a local, open-source tool that reads Claude Code transcripts and git history to show how your weeks of agent work are going for your health and your work, with a weekly retro."
year: 2026
tags: &a1
  - agents
  - claude-code
  - wellbeing
  - open-source
  - python
  - react
  - local-first
url: https://github.com/matrice-technologies/wimym
repos:
  - name: wimym
    url: https://github.com/matrice-technologies/wimym
    role: author
    visibility: public
    description: Reads your Claude Code transcripts, prompt history and git
      history and shows, against your own usual, how your weeks of agent work
      are going.
    year: 2026
    last_active: 2026-11
    language: TypeScript
    archived: false
    tags: *a1
---

Wimym, short for "Where is your mind", is for people who work with agents on ambitious projects. Its stated purpose is to protect the mental health and the performance of people who spend long days directing coding agents, a way of working with fast, variable feedback and no natural end of day. It reads Claude Code transcripts, prompt history and git history on the person's own machine and shows how their weeks are going against their own usual: hours, late nights, consecutive days, how scattered or focused their attention was, and what actually landed.

## What

A local web page with several views. "This week" draws the days as a planet, then the vital signs, each over twelve weeks with the person's own range as a band and the ones outside it first. "The week" is the retro page: the days in a few sentences and the moments worth a question, each with its messages. "Days" and "Messages" list every session and every message sent, filterable by intent, tone, model, effort and project. "Practices" tracks what the person decided to try and the instructions they keep giving agents; another view shows what agents have saved about them in memory. A share switch hides message text, project names and people's names so the page can be shown safely, and a demo mode runs on an invented person.

Two Claude Code skills sit on top: `/wimym` answers open questions about one's own record ("Am I more scattered on days I start before 7?"), and `/retro` runs a weekly retro that brings up a few moments, then records the practices the person decides on. Optional hooks add a stopping hour, days off or a ceiling on simultaneous sessions to Claude's context, and a status line with today's hours.

## Tech

The engine is Python 3 using only the standard library: it scans transcripts, keeps an index that outlives the transcripts Claude Code deletes, reads git repositories behind working folders, builds messages, sessions, days and weeks, computes the vital signs, and serves the page and a JSON API on 127.0.0.1 only. A SQLite copy of the data backs the `wimym` CLI. The page is Vite, React, TypeScript and d3, with a three.js hero. A labeller adds model labels (what each message asks for, an account of each session and day, repeated instructions) through the person's logged-in `claude` CLI, with documented wording and measured accuracy; a label feeds a measure only once checked. A cross-platform installer (`install.sh`, `install.cmd`, `install.py`) builds and starts everything and handles updates; CI runs the tests and the installer on Windows and Linux. Nothing is sent anywhere by Wimym itself; text leaves the machine only when the person runs the labeller or asks Claude through the skills.

## Status

Open source under the AGPL-3.0 since 28 October 2026, with a public site at wimym.matricetechnologies.com and a guided setup that Claude Code can follow. First built in a local repository under the name Mirror, whose history quotes real messages and was not published; the public repository starts on 23 October 2026. Merging into `main` is the release. Last activity in November 2026.
