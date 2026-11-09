---
name: Polish
description: "Une application de la zone de notification qui réécrit le texte sélectionné dans n'importe quelle application avec Claude ou un autre modèle, avec un raccourci global par prompt."
year: 2026
tags: &a1
  - desktop
  - electron
  - typescript
  - llm
  - open-source
  - productivity
url: https://github.com/matrice-technologies/polish
repos:
  - name: polish
    url: https://github.com/matrice-technologies/polish
    role: author
    visibility: public
    description: Application de la zone de notification qui retravaille avec
      Claude le texte sélectionné dans n'importe quelle application, puis colle
      le résultat à sa place.
    year: 2026
    last_active: 2026-11
    language: TypeScript
    archived: false
    tags: *a1
---

Polish est une application de bureau de Matrice Technologies qui vit dans la zone de notification : on sélectionne du texte dans n'importe quelle application, on appuie sur un raccourci, et le texte revient réécrit. Chaque prompt (« Polish », « Shorter », « Professional », et ceux de la personne) a son propre raccourci global ; les autres sont accessibles depuis un sélecteur. Elle fonctionne sans compte et sans le serveur de Polish : le texte part directement de l'ordinateur vers le fournisseur de modèle choisi.

## What

Un appui sur un raccourci copie la sélection de l'application active, l'envoie au modèle avec les instructions du prompt, colle le résultat à la place de la sélection et rétablit le presse-papiers. Trois types de fournisseurs sont pris en charge : l'abonnement Claude de la personne, via Claude Code installé sur la même machine (sans clé d'API), une clé d'API Anthropic, OpenAI, Google Gemini ou xAI Grok, ou tout point d'accès compatible OpenAI, y compris des modèles locaux via Ollama ou LM Studio. La connexion est facultative et n'ajoute que la synchronisation des prompts, raccourcis et réglages entre machines, ainsi que leur modification sur le web. Les clés des fournisseurs restent sur chaque appareil.

## Tech

Un monorepo en TypeScript fondé sur les workspaces npm. `apps/desktop` est l'application Electron (zone de notification, raccourcis globaux, sélecteur, cycle copie, réécriture et collage) ; `apps/web` est une application Next.js pour la connexion, l'éditeur de prompts, les réglages, la connexion de l'application de bureau et le site ; `packages/shared` contient les schémas des prompts et des réglages, l'analyse des raccourcis, la fusion de synchronisation et le prompt système ; Supabase stocke les comptes avec sécurité au niveau des lignes. La sélection est lue via le presse-papiers à l'aide d'une valeur sentinelle, et les frappes sont simulées avec `uiohook-napi`. Sous macOS, un petit utilitaire Swift enregistre des raccourcis Carbon par position de touche, pour qu'ils fonctionnent sur des dispositions autres que QWERTY, comme l'AZERTY. Le mode abonnement lance `claude -p` sans outils, sans réglages, sans serveurs MCP ni session enregistrée, dans un dossier vide. La synchronisation privilégie le hors-ligne : le fichier local fait foi et les prompts sont fusionnés un par un, la modification la plus récente l'emportant, avec des marqueurs de suppression. L'application de bureau se connecte par un device flow. Les clés sont chiffrées avec le trousseau du système. Les versions sont compilées par GitHub Actions pour Windows et macOS (Apple Silicon et Intel), et les copies installées se mettent à jour d'elles-mêmes.

## Status

Dépôt public sous licence MIT, créé le 30 octobre 2026, avec une instance hébergée à l'adresse polish.matricetechnologies.com. La version 0.1.3 est la première compilation macOS signée et notarisée ; la 0.1.5, sortie le 1er novembre 2026, est la plus récente. Reste à faire : la prise en charge de Wayland sous Linux et la signature du code sous Windows.
