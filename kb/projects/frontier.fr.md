---
name: Frontier (sdlc)
description: "Une méthode propre au dépôt et un vérificateur en lecture seule pour coordonner le développement par agents, ainsi qu'un paquet commun aux applications qui fournissent leur propre CLI et leur propre skill à Claude Code."
year: 2026
tags: &a1
  - agents
  - claude-code
  - methodology
  - python
  - cli
  - developer-tools
repos:
  - name: frontier
    role: author
    visibility: private
    description: Méthode « sdlc » propre au dépôt pour coordonner le travail des
      agents (BIGPICTURE, BACKLOG), avec un vérificateur Python sans dépendance.
    year: 2026
    last_active: 2026-10
    language: Python
    archived: false
    tags: *a1
  - name: served-tool
    role: author
    visibility: private
    description: Paquet commun aux applications qui fournissent leur propre CLI et
      leur propre skill à une session Claude Code et lui délivrent sa clé par un
      device flow.
    year: 2026
    last_active: 2026-10
    language: JavaScript
    archived: false
    tags:
      - claude-code
      - cli
      - device-flow
      - nodejs
      - npm
---

Deux briques de l'outillage de Matrice Technologies pour le travail avec des agents. Frontier est une méthode légère pour coordonner plusieurs agents (et plusieurs personnes) sur un même dépôt, au moyen de documents conservés dans le dépôt lui-même. served-tool est le paquet qui permet à une application web de fournir sa propre CLI et sa propre skill Claude Code à une session d'agent.

## What

La méthode conserve l'intention produit dans `BIGPICTURE.md`, les éléments de travail dans `BACKLOG.md`, et à côté du code les décisions dont les sessions suivantes auront besoin. Les agents réservent des éléments, déclarent leurs dépendances, les fichiers qu'ils comptent toucher et leurs passations, de sorte que n'importe quelle session peut reprendre un travail sans la conversation qui l'a lancé. Le travail se découpe par résultat attendu et non par session : passé la moitié de la fenêtre de contexte, une session passe la main et une nouvelle poursuit le même élément.

Un vérificateur lit ces documents et signale le travail prêt (la « frontière »), les blocages, les chevauchements de fichiers déclarés et les erreurs de structure, avec les requêtes `--find`, `--trace`, `--progress`, `--graph` et `--json`. Il ne prétend pas prouver qu'une fonctionnalité marche ni que des modifications parallèles sont sans risque. Un projet adopte la méthode en copiant à sa racine un dossier `sdlc/` publié (`git archive vN.N.N sdlc`) ; un manifeste d'empreintes détecte les modifications locales. Frontier applique la méthode à lui-même, et stigmatic fait partie des projets qui l'intègrent.

## Tech

Le vérificateur est un unique script Python (Python 3.8+ et Git, sans dépendance), avec son propre lanceur de tests sur des jeux de données et des instances volontairement altérées. La méthode tient en trois documents : BOOT (premiers pas), PROCESS (coordination, clôture, entretien des documents) et SYNTAX (les champs), plus des modèles. L'outil n'a ni démon, ni accès réseau, ni capacité d'écriture, ni tableau de bord. Licence MIT.

## Status

Dépôt privé, créé en juillet 2026. La première version est sortie le 23 juillet 2026 et le dossier est devenu une unité versionnée à part entière avec la v1.0.0 le 30 juillet. La v6.0.0 (29 septembre et 2 octobre 2026) a ramené la méthode à un noyau léger : plans, spécifications, audits et attestations de vérification sont devenus facultatifs, et les agents choisissent eux-mêmes leurs lectures et leur planification. Dernière activité en octobre 2026.

## served-tool

### What

served-tool regroupe ce dont a besoin toute application Matrice qui fournit sa propre CLI et sa propre skill à une session Claude Code : le cœur de la CLI (`login`, `whoami`, `version`, `upgrade`, `skill --install`, `help`, plus les commandes propres au projet), la logique côté serveur d'une connexion par device flow et de son stockage de clés, et une étape de build qui assemble la CLI et y inscrit la skill et deux compteurs de version dans un seul fichier servi. Comme c'est l'application qui fournit l'outil, un déploiement et l'outil qui lui parle ne sont jamais en désaccord, et `upgrade` récupère la CLI et la skill plus récentes que sert le déploiement. La version 0.2 a ajouté des options pour qu'un outil existant (Fixit) puisse s'y appuyer : une publication sur npm en parallèle, une connexion en deux commandes (`--begin`, `--finish`) parce qu'un agent ne voit la sortie d'une commande qu'une fois celle-ci terminée, une skill installée par dépôt, et la reprise des noms de variables d'environnement et du fichier de configuration que ses utilisateurs avaient déjà.

### Tech

Un paquet en modules ES sans dépendance à l'exécution, pour Node 20 ou plus, avec quatre points d'entrée : `/cli`, `/server` (opérations de connexion et de clés au-dessus d'une interface de stockage, avec une implémentation en mémoire), `/build` (assemblage par esbuild et incrustation, plus un exécutable `served-tool`) et `/guides` (transforme les fichiers Markdown d'une skill en pages qu'une application peut afficher). Le contrat entre l'application et l'outil, y compris les routes du device flow et leurs statuts, est décrit dans `contract.md`. Les tests utilisent `node --test` avec une horloge, une plateforme et un disque simulés. Publié sur npm sous le nom `@matrice-technologies/served-tool`, sous licence MIT.

### Status

Dépôt privé, créé le 22 septembre 2026. La version 0.2.1, sortie le 3 octobre 2026, corrige la troncature à 64 Kio des sorties longues redirigées vers un pipe sous macOS. La CLI de Fixit est construite dessus.
