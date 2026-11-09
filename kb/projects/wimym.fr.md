---
name: Wimym
description: "Where is your mind : un outil local et open source qui lit les transcriptions Claude Code et l'historique git pour montrer comment se passent vos semaines de travail avec des agents, pour votre santé comme pour votre travail, avec une rétrospective hebdomadaire."
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
    description: Lit vos transcriptions Claude Code, votre historique de prompts et
      votre historique git, et montre, par rapport à vos habitudes, comment se
      passent vos semaines de travail avec des agents.
    year: 2026
    last_active: 2026-11
    language: TypeScript
    archived: false
    tags: *a1
---

Wimym, abréviation de « Where is your mind » (où est ta tête), s'adresse aux personnes qui travaillent avec des agents sur des projets ambitieux. Son objectif déclaré est de protéger la santé mentale et la performance de celles et ceux qui passent de longues journées à diriger des agents de code, une façon de travailler marquée par des retours rapides et imprévisibles, sans fin de journée naturelle. Il lit sur la machine de la personne ses transcriptions Claude Code, son historique de prompts et son historique git, et montre comment se passent ses semaines par rapport à ses propres habitudes : les heures, les nuits tardives, les jours d'affilée, le degré de dispersion ou de concentration de son attention, et ce qui a réellement abouti.

## What

Une page web locale avec plusieurs vues. « This week » représente les jours sous la forme d'une planète, puis les signes vitaux, chacun sur douze semaines avec la plage habituelle de la personne en bandeau, en commençant par ceux qui en sortent. « The week » est la page de rétrospective : les jours résumés en quelques phrases et les moments qui méritent une question, chacun avec ses messages. « Days » et « Messages » listent chaque session et chaque message envoyé, filtrables par intention, ton, modèle, niveau d'effort et projet. « Practices » suit ce que la personne a décidé d'essayer et les consignes qu'elle répète aux agents ; une autre vue montre ce que les agents ont retenu d'elle dans leur mémoire. Un interrupteur de partage masque le texte des messages, les noms de projets et les noms de personnes pour pouvoir montrer la page sans risque, et un mode démo fonctionne sur une personne fictive.

Deux skills Claude Code s'appuient dessus : `/wimym` répond aux questions ouvertes de la personne sur son propre historique (« Suis-je plus dispersé les jours où je commence avant 7 h ? »), et `/retro` mène une rétrospective hebdomadaire qui fait ressortir quelques moments, puis consigne les pratiques que la personne décide d'adopter. Des hooks facultatifs ajoutent au contexte de Claude une heure d'arrêt, des jours de repos ou un plafond de sessions simultanées, ainsi qu'une ligne d'état indiquant les heures du jour.

## Tech

Le moteur est en Python 3 et n'utilise que la bibliothèque standard : il analyse les transcriptions, tient un index qui survit aux transcriptions supprimées par Claude Code, lit les dépôts git derrière les dossiers de travail, reconstitue messages, sessions, jours et semaines, calcule les signes vitaux, et sert la page ainsi qu'une API JSON uniquement sur 127.0.0.1. Une copie SQLite des données alimente la CLI `wimym`. La page est faite avec Vite, React, TypeScript et d3, avec une illustration d'accueil en three.js. Un module d'étiquetage ajoute des étiquettes produites par un modèle (ce que demande chaque message, un récit de chaque session et de chaque journée, les consignes répétées) via la CLI `claude` de la personne, déjà connectée, avec une formulation et une précision mesurée documentées ; une étiquette n'alimente une mesure qu'une fois vérifiée. Un installateur multiplateforme (`install.sh`, `install.cmd`, `install.py`) compile et lance l'ensemble et gère les mises à jour ; l'intégration continue exécute les tests et l'installateur sous Windows et Linux. Wimym n'envoie rien de lui-même : le texte ne quitte la machine que lorsque la personne lance l'étiquetage ou interroge Claude via les skills.

## Status

Open source sous licence AGPL-3.0 depuis le 28 octobre 2026, avec un site public à l'adresse wimym.matricetechnologies.com et une installation guidée que Claude Code peut suivre. D'abord développé dans un dépôt local sous le nom de Mirror, dont l'historique cite de vrais messages et n'a pas été publié ; le dépôt public commence le 23 octobre 2026. Une fusion dans `main` vaut publication. Dernière activité en novembre 2026.

## Articles

- [Introducing Wimym: where is your mind?](https://matricetechnologies.com/blog/introducing-wimym) (26 octobre 2026), l'article de lancement sur le blog de Matrice (en anglais).
