---
name: Fixit
description: "Collecte de retours pour applications web : un widget envoie des rapports de bug annotés, avec console, réseau, capture d'écran et rejeu du DOM, vers une boîte de réception que les équipes trient et que les agents de code traitent."
year: 2026
tags: &a1
  - agents
  - claude-code
  - feedback
  - nextjs
  - typescript
  - supabase
  - mcp
url: https://fixit.matricetechnologies.com
repos:
  - name: fixit
    role: author
    visibility: private
    description: Plateforme de collecte de retours avec un widget intégrable, un
      tableau de bord de tri, une API pour agents, un serveur MCP, une CLI et une
      skill Claude Code.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags: *a1
  - name: skills
    url: https://github.com/matrice-technologies/skills
    role: author
    visibility: public
    description: Skills d'agent publiques pour Fixit, installables avec
      l'installateur `skills` ; désormais remplacées par la skill servie par
      l'application.
    year: 2026
    last_active: 2026-08
    language: Markdown
    archived: true
    tags:
      - agents
      - skills
      - claude-code
---

Fixit est la plateforme de collecte de retours de Matrice Technologies pour les applications web, hébergée à l'adresse fixit.matricetechnologies.com. Un widget placé dans un coin du site permet à quiconque repère un problème de le désigner, de dessiner dessus et de l'envoyer. Le rapport qui arrive dans la boîte de réception du projet contient la note, l'élément désigné, la sortie de la console, les requêtes en échec, une capture d'écran et un rejeu du DOM. Les équipes trient les rapports dans un tableau de bord, et les agents de code les traitent avec une CLI et sa skill Claude Code.

## What

Connecter un dépôt demande une CLI installée depuis l'application, une connexion dans le navigateur et `/fixit setup` dans Claude Code, qui place le widget là où la pile technique du projet charge les scripts tiers ; la page Setup de chaque projet fournit aussi un prompt prêt à l'emploi pour un agent de code. Ensuite, un agent peut répondre à des questions à partir de la boîte de réception (« les 3 derniers rapports »), ou prendre un rapport par son identifiant, le réserver, corriger la cause, vérifier puis le libérer. L'intégration continue utilise la même CLI depuis npm, avec un jeton créé dans le tableau de bord.

## Tech

Un monorepo en TypeScript fondé sur les workspaces npm. `apps/web` est une application Next.js 16 et React 19 qui regroupe le tableau de bord, l'API de réception, l'API pour agents et l'installateur de la CLI. `packages/widget` est le script intégrable, écrit sans framework, qui enregistre les rejeux du DOM avec rrweb. `packages/shared` contient les schémas Zod et les types générés de la base de données, `packages/client` est le client REST commun à la CLI et à `packages/mcp`, un serveur MCP pour les agents. La CLI est construite avec served-tool sous la forme d'un unique script versionné, que l'application sert à `/api/cli/*` et qui est aussi publié sur npm sous le nom `@matrice-technologies/fixit-cli`, si bien que les deux copies exécutent exactement le même code. Les données sont dans un Supabase (Postgres) auto-hébergé, et l'application web est déployée sous forme d'image Docker.

## Status

Dépôt privé, créé le 10 août 2026. Début octobre 2026, la CLI a été reconstruite sur served-tool 0.2 et elle est désormais servie par l'application elle-même, ce qui a mis fin au miroir public des skills. Dernière activité en octobre 2026.

## skills

### What

Un dépôt public qui publiait la skill d'agent de Fixit, à installer avec `npx skills add matrice-technologies/skills`, compatible avec Claude Code, Cursor, Codex, OpenCode et les autres agents pris en charge par cet installateur. La skill pilote la CLI de Fixit pour la mise en place, les questions sur la boîte de réception et la correction des rapports.

### Tech

Un unique fichier `skills/fixit/SKILL.md`, synchronisé automatiquement depuis le dépôt de Fixit plutôt que modifié sur place.

### Status

Actif du 10 au 12 août 2026, puis retiré et archivé une fois la skill intégrée à la CLI servie par l'application Fixit (`fixit skill --install`).
