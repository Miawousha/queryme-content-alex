---
name: Oxide
description: "Un atelier macOS natif pour les dépôts git de markdown : lecteur, éditeur avec aperçu en direct, interface git et couche IA s'appuyant sur la CLI Claude Code."
year: 2026
url: https://github.com/Miawousha/oxide-releases
tags: &a1
  - desktop
  - tauri
  - rust
  - svelte
  - markdown
  - git
  - claude-code
repos:
  - name: oxide
    role: author
    visibility: private
    description: Atelier markdown macOS natif sur Tauri 2 ; lecture, édition, git,
      carte du dépôt et IA, avec des versions publiques signées.
    year: 2026
    last_active: 2026-10
    language: Rust
    archived: false
    tags: *a1
---

Oxide est une application macOS native et locale pour les dépôts composés surtout de markdown : documentation, spécifications, notes, bases de connaissances, instructions pour agents. Elle ouvre un dossier, idéalement un dépôt git, et réunit un lecteur à la typographie soignée, un éditeur où la mise en forme apparaît pendant la frappe tandis que le fichier sur disque reste du markdown brut, une interface git pour l'état, les différences, les commits et la synchronisation, et une carte du dépôt sous forme de graphe. Une couche IA s'appuie sur la CLI Claude Code installée par l'utilisateur, donc sans clé d'API ni facturation séparée, et chaque suggestion arrive sous forme de différence à relire. Alexandre l'a commencée en juillet 2026 et y a écrit environ 1 100 commits ; les versions signées sont publiées sur github.com/Miawousha/oxide-releases.

## What

La lecture couvre CommonMark et GFM, avec liens wiki, liens relatifs, coloration du code, une fiche pour le frontmatter YAML, images locales et une table des matières flottante. L'éditeur est un aperçu en direct hybride sur CodeMirror 6 : le markdown brut réapparaît sur la ligne en cours d'édition, l'enregistrement automatique écrit de façon atomique, et un test de propriétés garantit qu'ouvrir puis enregistrer un fichier sans le modifier le laisse identique à l'octet près. La navigation offre une ouverture rapide approximative, une palette de commandes, une recherche dans tout le dépôt et les rétroliens.

L'interface git indexe par fichier ou par bloc de modifications (par paragraphe dans la prose), affiche pour le markdown des différences mot à mot ancrées sur les paragraphes, synchronise en un bouton (fetch, puis push ou rebase avec autostash), change de branche et en crée, résout les conflits dans l'application et montre l'historique avec blame. Abandonner un fichier non suivi l'envoie à la Corbeille au lieu de lancer `git clean`.

La couche IA a deux niveaux. Les actions en ligne (améliorer, resserrer, corriger la grammaire, poursuivre l'écriture) diffusent des propositions modifiables attachées à leur passage, produites par un sous-processus qui ne peut ni lire ni écrire de fichiers. Un agent conversationnel propre à chaque dépôt peut lire et modifier l'arbre de travail et cite ses sources ; ses modifications arrivent comme des changements ordinaires de l'arbre de travail, relus dans l'interface git, avec les commandes shell et les écritures dans `.git` interdites. Les messages de commit peuvent être rédigés à partir des changements indexés, et un interrupteur par dépôt est appliqué dans l'adaptateur.

La carte construit en direct un graphe de connaissances à partir des dossiers, des liens et du frontmatter, avec un schéma versionné facultatif pour les types et les relations, des vues d'exploration par niveaux et des signaux de santé (documents orphelins, liens cassés, documents sans type). Une CLI `oxide` fournie avec l'application donne aux agents accès au même cœur : requêtes de structure, un contrôle `check` avec des codes de sortie adaptés à l'intégration continue, et des écritures sûres, comme un déplacement qui réécrit tous les liens entrants.

## Tech

Tauri 2 avec un cœur en Rust et une interface Svelte 5 + TypeScript + Vite dans WKWebView. L'espace de travail Rust comprend une bibliothèque indépendante de Tauri (`oxide-core` : modèle du dépôt, écritures atomiques, index des liens, recherche, rendu et assainissement du markdown, sous-processus git, moteur de différences, analyse des conflits, adaptateurs IA), le crate de l'application et celui de la CLI. La WebView n'accède jamais au disque, à git ni au réseau : elle appelle des commandes IPC typées dont les liaisons TypeScript sont générées depuis Rust et contrôlées en intégration continue. L'intégration continue vérifie le formatage, clippy, les tests Rust, svelte-check et Vitest sous Linux et macOS, et publie une version à chaque tag. Les versions sont signées, et l'application cherche les mises à jour au lancement puis toutes les quatre heures.

## Status

Tous les jalons de la v1 sont clos, dont le jalon « Ship » (typographie, budgets de performance, prise en main, fiabilisation des livraisons) en août 2026 ; le travail restant est suivi dans un backlog. Dernière version publique : 0.8.2 (octobre 2026). Cible macOS 14 et plus sur Apple Silicon. Le code source est privé ; le dépôt des versions est public.
