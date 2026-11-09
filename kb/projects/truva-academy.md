---
name: Truva Academy
description: "Agentic training platform for Truva's staff: spoken role-plays with Claude-played customers, graded debriefs, drills and a game layer, live at academy.truva.matricetechnologies.com."
year: 2026
url: https://academy.truva.matricetechnologies.com
tags: &a1
  - ai-agents
  - claude
  - edtech
  - voice
  - nextjs
  - supabase
  - typescript
repos:
  - name: truva-academy
    role: author
    visibility: private
    description: One Next.js application where headless Claude sessions play the
      customer, a separate session grades the transcript, and an append-only
      learner record drives the game.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags: *a1
---

Truva Academy is the training platform Matrice built for Truva, the Mumbai resale-homes platform, as part of the AI-transformation engagement described in the Truva AI transformation entry. A trainee opens it in the browser, signs in with their Truva Google account or a magic link, and follows their role's journey: lessons, quizzes, drills and spoken role-plays where Claude plays a seller or a buyer in character, followed by a debrief from a second Claude session that grades the transcript against the module's rubric. XP, streaks, levels, badges and leaderboards are computed from an append-only record of every attempt. It is the largest piece of the engagement: about 2,400 commits between August 8 and October 12, 2026, live at [academy.truva.matricetechnologies.com](https://academy.truva.matricetechnologies.com).

## What

The starting point was Truva's acquisitions trainer, a Claude skill used for role-play practice; the Academy turned it into an application, on the reasoning that what training needs (grading always runs, the persona's hidden brief stays hidden, the record survives a crash, progression follows from evidence) are guarantees code can make and prose cannot.

- **Role-plays.** A role-play is a live voice conversation: hands-free and interruptible, the persona answering aloud in a voice that fits the character. The actor session plays the counterpart throughout and never grades itself; the grader reads the transcript cold, with the rubric and a grading key of what was there to be found but without the actor's brief, and returns per-criterion scores in three classes (must-hit, instant fail, and flags that never decide the verdict). A run the trainee never spoke in is not graded or recorded. Results read as Perfect, Great, Good or Needs more work.
- **The trainer in the room.** A trainee chooses how much help to get, from a beat-by-beat rehearsal through a coach who steps in when the meeting goes wrong, down to solo. The coach is a second live voice that can voice the customer during rehearsal, open a back-and-forth mid-meeting and hand the trainee back with the customer's memory intact. Characters the trainer invents on the fly get a name, a stand-in face and a consistent voice.
- **Other activities.** Lessons, quizzes and structured drills, each with its own player; closed answers are graded in code and judgment answers by a grader session. Trainees can read Hindi passages in the script they choose.
- **The game.** XP, streaks, levels, badges, a progression ladder across modules and courses, shared records, leaderboards and challenges, and an avatar dressed from a wardrobe bought with what practice earns. All of it is derived from the record and never stored.
- **Authoring.** Courses, modules, personas, rubrics and the knowledge library are Markdown documents in the platform's own store, read at run time. Authors change them through an API, a CLI usable from Claude Code, or editors in the admin console, without a commit or a deploy; every change is validated, kept and revertible. An author can start a "drive", a synthetic trainee run by the platform, and have their own agent read the run and propose the fix. Each activity names its main author, and an Authors page lists them.

## Tech

One TypeScript repository holding one Next.js 16 application (App Router, route handlers for the API, React 19, Tailwind 4, shadcn on Base UI), with the orchestrator under `web/server/`. Every server file imports `server-only`, so a client component reaching the orchestrator fails `next build`; a test asserts the marker across the tree and an `npm run boundary` script proves the build goes red.

- **Sessions.** Each run composes a workspace (the role card as agent instructions, the module's files beside it) and opens a session through one substrate seam, on the Anthropic API or on Google's Gemini depending on the model chosen in the roster. Actor sessions run with no tools and the grader runs read-only; capability is set by spawn arguments, never by instructions. Every event is appended to a JSONL transcript as it arrives, so a killed process leaves a complete prefix.
- **Voice.** The Academy owns the voice loop: ElevenLabs transcribes one utterance and speaks one sentence at a time, while the conversation itself stays in the Academy's own Claude session. An earlier version on a hosted voice agent was retired in August 2026.
- **Activities.** An activity kind is code with one contract (compose, run, grade, record), each step triggered by the end of the previous one. Grader output is schema-validated; a malformed grade re-prompts once and then fails visibly.
- **State.** Three kinds: content, per-run workspaces (disposable) and the learner record (append-only, in Supabase Postgres, also used for auth). Live runs are held in an in-process registry pinned to `globalThis`, which makes the deployment single-replica by design.
- **Delivery.** Deployed on Coolify with Nixpacks. Vitest (329 test files) plus browser tests, `tsc` and `next build` gate every merge. Work follows an sdlc method vendored into the repo: a target-state document where every unbuilt clause points to a numbered work order in the backlog, checked by a script.

## Status

Hosted at academy.truva.matricetechnologies.com since August 2026. Releases R1 to R3 and R5 shipped between August 9 and 11 (typed role-play with a graded debrief, then quizzes, drills and a second trainer track, then spoken role-play, then a single component system in Truva's brand). R6 and R7 (the trainer in the room as a second voice, on a voice loop owned end to end) shipped on August 14 and 15, and R4 (the move to one hosted Next.js application with shared records, leaderboards and challenges) on September 5. Through September and early October the work moved to content authoring in the platform, synthetic trainee runs, character voices and grading presentation; the last commit is from October 12, 2026. Private repository.
