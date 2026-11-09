---
name: stigmatic
description: "Une application Mac locale de supervision pour mener de nombreuses sessions Claude Code sur de nombreux projets : ce qui attend une intervention, les sessions en cours, l'état git et le backlog sdlc, avec des commandes pour répondre, lancer et fusionner."
year: 2026
tags: &a1
  - agents
  - claude-code
  - rust
  - tauri
  - svelte
  - developer-tools
  - local-first
repos:
  - name: stigmatic
    role: author
    visibility: private
    description: Application Mac locale de supervision pour suivre et piloter les
      sessions Claude Code, les worktrees git et les backlogs sdlc d'une machine.
    year: 2026
    last_active: 2026-10
    language: Rust
    archived: false
    tags: *a1
---

stigmatic est une application Mac développée chez Matrice Technologies pour une personne qui mène de front de nombreuses sessions Claude Code sur dix projets ou plus. Elle suit chaque session de la machine, l'état git et les worktrees de chaque dépôt, ainsi que le backlog des projets qui appliquent la méthode sdlc (voir Frontier), et elle s'ouvre sur ce qui attend une intervention humaine : les sessions en attente de réponse, le travail laissé en plan, les vérifications en échec. Elle n'écoute que sur l'interface locale (`127.0.0.1:7844`) et ne sert qu'un seul utilisateur.

## What

L'accueil liste, pour tous les projets, ce qui attend une intervention. Choisir un projet ouvre un poste de pilotage dont chaque vue ne porte que sur ce projet : les sessions en cours, l'état git et les worktrees, et les tableaux sdlc (frontière, avancement, versions). La page de chaque session indique où le travail s'est arrêté : la dernière demande, la dernière réponse et les fichiers modifiés. Les chiffres rétrospectifs (activité, dépenses, avancement de la méthode) sont regroupés à part, dans une section Analytics.

L'application agit aussi, un clic à la fois : rejoindre une session, répondre à une session au repos (elle la reprend avec `claude -p --resume`), lancer un élément prêt du backlog dans son propre worktree git avec une session Claude Code sans interface, puis le fusionner et faire le ménage derrière lui, avec une boîte de dialogue native avant toute fusion dans main. Deux modes plus larges s'appuient sur ces commandes. Une exécution de répartition reçoit un budget, lance les éléments prêts sur plusieurs projets, fait vérifier chaque branche terminée par un sous-agent, fusionne ce qui passe et met de côté ce qui échoue. Le coordinateur est une session Claude unique avec laquelle on discute de l'ensemble de ses projets ; il n'agit que sur ce qui a été convenu dans la conversation. Les mêmes commandes de lancement, de fusion, de réponse et d'arrêt sont disponibles depuis un terminal via `bin/stig`.

## Tech

Un workspace Rust à deux crates. `core/` (tokio, axum, notify) constitue le plan de données : il suit les transcriptions JSONL de Claude Code, en déduit l'activité de chaque session, lit l'état git, ne lit l'état sdlc qu'à travers la sortie `--json` du vérificateur, et diffuse des événements typés par server-sent events. Le cœur est en lecture seule par construction : aucune route qui modifie quoi que ce soit, aucune écriture sur disque, ce que des tests garantissent. `app/` est une coque Tauri 2 qui embarque le cœur et contient le seul code qui lance des processus ou écrit, derrière un petit ensemble de commandes nommées que seule la fenêtre de l'application peut appeler. L'interface, dans `ui/`, est en Svelte 5 avec TypeScript, Vite et Tailwind v4, sur un design system unique de composants shadcn-svelte et de jetons. Les tests combinent `cargo test` et clippy, vitest et svelte-check, une suite Playwright de non-régression sur Chromium et WebKit à partir d'un corpus de données de test, et un corpus de référence figé qui a établi l'équivalence entre le cœur Rust et le serveur Node qu'il a remplacé.

## Status

Dépôt privé, développé avec sa propre méthode sdlc (BIGPICTURE et BACKLOG dans le dépôt). Le backlog consigne les versions depuis R1 (le mur des sessions en direct, 24 juillet 2026) jusqu'au remplacement du serveur Node par le cœur Rust et l'application Mac (R12 et R13, 2 octobre 2026), en passant par les commandes (R17), la répartition (R20) et le coordinateur (R22 et R23, 7 octobre 2026). Prochaine étape au backlog : suivre aussi les sessions Codex et OpenCode. La distribution, la signature et la notarisation sont explicitement hors du périmètre : l'application tourne depuis son propre dépôt cloné.
