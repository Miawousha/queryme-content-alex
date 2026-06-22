---
name: Graybox
description: "Une méta-ontologie local-first, ancrée dans la littérature, pour modéliser les organisations sous forme de données typées et validées."
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
    description: Une méta-ontologie local-first, ancrée dans la littérature, pour
      modéliser les organisations sous forme de données typées et validées.
    year: 2026
    last_active: 2026-06
    language: TypeScript
    archived: false
    tags: *a1
---

Graybox est une méta-ontologie local-first, ancrée dans la littérature, pour les entreprises et les organisations : un vocabulaire typé (agents, ressources, activités, objectifs, relations, frontières, plus cinq facettes couvrant la structure, le flux de valeur, la coordination, la capacité et l'environnement) qui permet de décrire n'importe quelle organisation sous forme de données vérifiées et exploitables par machine. Un agent local (par ex. Claude via la CLI) et des humains (un explorateur React/D3) créent, éditent et valident les modèles d'organisation entièrement sur la machine de l'utilisateur, sans backend hébergé.

## What

L'unité, c'est le modèle d'organisation : un document JSON décrivant une organisation à travers des entités cœur typées (agents, ressources, activités, objectifs, relations, frontières) et cinq facettes d'analyse (structure, flux de valeur, coordination, capacité, environnement). Les modèles sont validés contre un schéma strict et explorés sous forme de graphe, et sont pensés pour être rédigés conjointement par un humain et un agent IA local. Un corpus canonique d'exemples (boulangerie, hôpital, industriel, startup SaaS) accompagne le schéma.

## Tech

Un monorepo TypeScript/ESM. La source de vérité est `@graybox/ontology`, un schéma Zod avec types inférés, un validateur `validateOrg`, un chemin d'`ingest` et une émission `toJsonSchema()` à la demande ; chaque objet est `.strict()`, donc tout champ inconnu fait échouer la validation. Une CLI `validate` vérifie les fichiers JSON d'organisation, et un explorateur React/D3 (`viz`) lit le corpus et restitue chaque organisation sous forme de graphe interactif. L'outillage repose sur vitest + tsx et requiert Node >= 20. Le local-first est une contrainte permanente : aucun backend hébergé, et aucune API distante prévue.

## Status

Phase 2 terminée en juin 2026 : le cœur est entièrement TypeScript/Zod et l'implémentation Python antérieure a été retirée. Dépôt privé, en développement actif.
