---
name: Agentic design course for an engineering school
description: "Matrice's first-principles work on what people should learn in the age of agents, applied to the design of an agentic design course for a French engineering school, with the essays and articles written alongside."
year: 2026
tags: &a1
  - education
  - agents
  - curriculum
  - writing
  - claude-code
repos:
  - name: matrice-pedagogy
    role: author
    visibility: private
    description: Workspace for Matrice's pedagogy work. Frozen first-principles
      concept files, the course design for a French engineering school, an
      essay on planning with agents and two article drafts on working with
      agents.
    year: 2026
    last_active: 2026-11
    language: Markdown
    archived: false
    tags: *a1
---

Matrice works out, from first principles, what people should still learn now that agents can do most of the producing, and applies the answer to engineering education. The concrete case is an agentic design course for a French engineering school, whose curriculum did not yet cover generative AI or agents in October 2026. The work started as preparation for a talk Alexandre gives at the school in November 2026. It produced three things: a set of frozen concept files (what it means to learn, to train, and why learn at all once agents exist), a course design written in French for the school, and a group of essays and articles on working with agents. Everything lives in one private repository that Alexandre works in with Claude agents.

## What

**Concepts.** Four definitions, each frozen after review:

- **To learn:** to keep, from an experience, something that can change how you feel, think or act (version 10).
- **To train:** to take part in experiences designed for learning something specific, in order to learn it.
- **Learning and the good life:** learning is part of a good life, shapes who lives it, and is a means. Agents can take over only the means.
- **Why learn:** a grid that crosses whose good a reason serves (me, the people close to me, society) with what learning does for it (is part of it, enables it, protects it). Agents can supply the "enables" column. They cannot be part of your good, and they cannot protect you from depending on them. The grid gives a test for any course: remove the reasons agents now cover, and ask whether what is left is worth the students' time.

Two further concepts, "to judge" and "to answer for", are listed but not written.

**Course design.** Written in French for the school, as working hypotheses:

- **The role map.** Two axes: seeing (being able to judge the evidence behind a decision) and signing (answering for it). The target is the engineer who sees and signs. The danger is the one who signs without seeing, where blame lands on the nearest person who had no means to judge. Agents never sign. The school can only move students along the seeing axis, and it now has to, because agents take over the execution work where junior engineers used to learn to see.
- **The V-cycle and the sufficiency line.** The engineer keeps three acts: owning the need and the acceptance criteria, judging the evidence, and deciding to ship. Everywhere, they read the specification and the evidence one level below their decision. Where needed, they run targeted deep checks, chosen by severity, by whether a component is pushed outside the conditions its datasheet covers, and by how weak the evidence is. The document also proposes a ladder of independence for checking agents' work, from the same agent writing the code and its tests up to a different model family with a fresh context plus human checks, and an "inverted exercise": students start from an agent's design dossier with a planted defect and are graded on whether they would ship it, and why.
- **Two test cases with the same three gestures (specify, steer, validate).** Downstream, a mountain hut at 2,500 m that replaces its diesel generator with solar panels and a battery, where the rescue radio must never go down with the lights. Upstream, choosing a MOSFET for a converter: students build the evaluation set from public datasheets, then compare a frontier model given good context, an open model with retrieval, and a small fine-tuned open model, and argue whether a company should train its own.
- **A dry run of the hut case** with four fresh agents (Claude Opus 5.5, empty context, no tools), two briefs run twice each. All four rejected the client's consumption figure, gave the radio its own supply and refused to sign "compliant" without reserves. Only the runs that had the notes from the site visit tied the storm, the full hut and the radio together. Every run ended with a list of steps only people could close. This became a 30-minute demo script.
- **Five course ideas,** from quick to ambitious: review the curriculum course by course (keep, transform or shrink), workshops where teachers solve their own exam with an agent, a semester team project going from a real stakeholder's need to a built prototype with agents (graded on the specification, a log of what was delegated and why, an oral defence and a judgment of the result against the need, plus a small part done by hand), a lab on evaluation sets and whether to train one's own model, and a tutor that guides without doing the work.
- **The agreed scope** after the first working session with the school (October 16, 2026): a tiered student project to design a power converter, such as a charger or a solid-state circuit breaker, with generative AI tools. The most advanced students work at the top of the V-cycle, writing specifications and checking results as the person who signs without having done the work. Others build the agents the task needs, which add to the starting material from one year to the next.
- **The talk's first artifact,** a "Recursive Comprehension Matrix" (October 9, 2026): seven capabilities in three groups (understand, judge, act), each with why AI does not remove it, how to teach and assess it, and an example from the school's fields. The repository marks it as out of date, since it predates the concept files.

**Writing.**

- **"My take on Planning with Agents"** (October 25, 2026), a reply to a published essay on planning with agents. It argues that human time should go to the edges of the work: a shared picture of the goal, built from rich prototypes people can react to and from choosing between pairs of agent-made variants; a convergence view that shows at a glance whether agent teams are getting closer to done; and acceptance criteria written before any work starts, with part of them kept out of the agents' reach. It draws on historical examples (the clay model in car design, a 19th-century map of a failed military campaign, the 18th-century longitude prize, mission command).
- **"Stages of delegation,"** a planned series of four articles. Article 1, "Work 2.0", describes six stages of working with AI (alone, with a chat, with one agent, with several, through an orchestrator agent, through a tree of agents) and what stays with the person at every stage: deciding what is wanted, judging whether it was achieved, and answering for it. It is published on the Matrice website. Articles 2 to 4 (moving up a stage, working at scale, teams and institutions including schools) are outlined, on top of working notes that model the evolution with three drivers: how long an agent can work alone, how much it costs to check its work, and the reusable environment the person builds.
- **"Tools before agents"** (working title "From Excel to Agents orchestration"), an article for consultants and engineers on the pattern behind five Matrice tools (truva-mapper, Eloom, Truva Academy, truva-intel and Fixit): build the experts a domain app and a CLI as one, get them to adopt it, teach agents the domain and measure them with evals, then delegate and feed what people and agents trip on back into the tool. The draft groups it into four phases.
- A short text in French on AI and intellectual work, which argues that agents remove the market value of intellectual production but not its intrinsic value, and that recognition and collective decisions become the open questions.

## Tech

The repository is a writing workspace rather than software. Alexandre works in it with Claude agents under a few written house rules:

- **Concept files are frozen.** Each carries a status line with a version and a date. Changes are proposed in the conversation and applied only once Alexandre agrees.
- **Concepts stay general.** The course folder applies them to the school and links back to them, but never redefines them.
- **One language per audience.** English by default, French for documents meant for the school.
- **Every folder with several files has an index README,** updated when a file is added.

Each concept file follows the same shape: a one-line definition, a numbered derivation from what is true of every case, a table of boundary cases, what follows, and sources from philosophy, psychology and automation research. The course documents carry their own status lines and are illustrated with SVG figures. The essay's and the articles' figures (a schematic of where human time goes, choosing between two cards, three drafts of the convergence view, a task map) are drawn by Python scripts that render SVG, PNG and HTML in the Matrice website's visual language. The master copies of the essays are Claude Docs, with local Markdown copies in the repository. The decks for the first working session were built as HTML slides. The claims in "Tools before agents" come from working notes read from each project's repository on November 3, 2026, with the gaps listed.

## Status

The work ran from October 9 to November 5, 2026, and was gathered into the repository in one commit on November 5. The four concept files were frozen between October 11 and 15; "to judge" and "to answer for" are not written. The course design is a set of working hypotheses: the scope was agreed in principle at the first working session on October 16, and no course has been taught yet. The talk is set for November 2026; the repository gives no exact date and does not record it as given. On the writing side, the planning essay is complete, "Work 2.0" is published, articles 2 to 4 of the series are outlines, and "Tools before agents" is a first draft dated November 3. Private repository.
