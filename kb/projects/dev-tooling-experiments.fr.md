---
name: Dev tooling & experiments
year: 2026
tags:
  - tooling
repos:
  - name: blueprint-creator
    url: https://github.com/ION-Altergo/blueprint-creator
    role: contributor
    visibility: private
    description: CLI interactive basée sur Rich pour parcourir, étendre et convertir
      les blueprints Altergo via le SDK.
    year: 2026
    last_active: 2026-01
    language: Python
    archived: false
    tags:
      - python
      - tooling
  - name: blueprints_importer
    url: https://github.com/ION-Altergo/blueprints_importer
    role: contributor
    visibility: private
    description: App plateforme Altergo qui génère en masse des blueprints depuis un
      fichier Excel ou des dataset IDs.
    year: 2025
    last_active: 2025-10
    language: Python
    archived: false
    tags:
      - python
      - tooling
  - name: simple-app
    url: https://github.com/ION-Altergo/simple-app
    role: contributor
    visibility: private
    description: Scaffold vide pour une app sur la plateforme Altergo — entrypoint,
      settings, aucune logique.
    year: 2024
    last_active: 2024-10
    language: Python
    archived: false
    tags:
      - python
      - demo
  - name: openclaw-config
    role: author
    visibility: private
    description: Dépôt versionné de configuration et d'état pour un runtime d'agent
      personnel (OpenClaw) en continu.
    year: 2026
    last_active: 2026-02
    language: Shell
    archived: false
    tags:
      - agent
      - shell
      - infra
  - name: opus-infra
    role: author
    visibility: private
    description: Infrastructure d'OPUS — manuscrits comme objets typés au niveau de
      la claim, avec revue IA et humaine.
    year: 2026
    last_active: 2026-05
    language: TypeScript
    archived: false
    tags:
      - ai
      - nextjs
      - typescript
      - postgres
  - name: su2re
    role: author
    visibility: private
    description: "Transcripteur Electron : faster-whisper + diarisation pyannote,
      push-to-talk, nettoyage GPT-4o-mini, Google Calendar."
    year: 2025
    last_active: 2025-10
    language: JavaScript
    archived: false
    tags:
      - ai
      - desktop
      - python
  - name: article-checker
    role: author
    visibility: private
    description: Prototype CRA de 2023 qui note l'objectivité et la consistance
      logique d'articles via GPT-3.5.
    year: 2023
    last_active: 2023-03
    language: TypeScript
    archived: false
    tags:
      - react
      - typescript
      - ai
      - sandbox
      - shelved
  - name: bisque
    url: https://github.com/Miawousha/bisque
    role: author
    visibility: public
    description: Landing-page bac à sable sur Next.js 16 / React 19 / Tailwind 4 —
      un seul bouton qui ne fait rien.
    year: 2026
    last_active: 2026-02
    language: TypeScript
    stars: 0
    archived: false
    tags:
      - nextjs
      - react
      - typescript
      - ui-only
      - sandbox
  - name: saas
    role: author
    visibility: private
    description: "Jeu navigateur temps réel : serveur NestJS WebSocket couplé à un
      client Phaser 3 / Vite."
    year: 2025
    last_active: 2025-02
    language: TypeScript
    archived: false
    tags:
      - typescript
      - sandbox
---

Petits outils de développement, benchmarks d'infrastructure et prototypes.

## blueprint-creator

blueprint-creator est une CLI Python interactive (« BP Extender ») qui pilote le SDK Altergo pour gérer des blueprints sur plusieurs environnements. Le menu guide l'opérateur dans la sélection d'environnement, la recherche et la vue arborescente des blueprints, l'inspection des paramètres et schémas, la création de hiérarchies enfants depuis du JSON simspec, la conversion entre formats et la suppression en masse — avec tables, bannières et rapports de diff rendus en Rich et écrits dans `data/`. Outillage développeur interne pour l'écriture de blueprints à l'échelle.

### What
L'opérateur lance `run.py`, choisit un environnement dans `envs/`, et atterrit dans un menu numérique rendu en Rich — ce n'est pas une CLI à flags. Depuis là il recherche des blueprints par nom ou ID, parcourt l'arbre des enfants, inspecte les définitions de paramètres et de schémas, génère une hiérarchie enfant depuis un JSON simspec, convertit d'anciens blueprints au format courant, ou supprime une liste en masse. Les rapports de diff et de conversion atterrissent dans `data/` pour être revus avant publication.

### Tech
`bp_extender/cli.py` porte la boucle de menu ; `client.py` enveloppe le SDK Altergo avec une auth scopée par environnement (`envs/<env>.json`) ; `extender.py` construit les hiérarchies enfants depuis simspec ; `converter.py` gère la migration de format ; `schema.py` introspecte les schémas de blueprint ; `cli_reports.py` écrit les artefacts de diff. Rich pilote chaque table, bannière et indicateur de progression. Le support multi-env permet à un même opérateur de passer entre dev, staging et prod sans cérémonie de ré-authentification.

### Status
Outillage développeur actif chez Altergo, dernière mise à jour 2026-01. Utilisé par l'équipe modélisation pour maintenir les catalogues de blueprints synchronisés entre environnements et amorcer de nouvelles hiérarchies d'assets sans éditer du JSON à la main.

## blueprints_importer

blueprints_importer est une app Python packagée pour la plateforme Altergo (déclarée dans `altergo-settings.json` comme app de catégorie Simulation) qui ingère un classeur Excel de composants batterie et non-batterie et les matérialise en blueprints plateforme. Le pipeline `main.py` télécharge le classeur, extrait les entrées en CSV et images, génère des templates JSON de blueprints, puis supprime et régénère les blueprints ciblés et leurs datasets via le SDK Altergo ; une branche « new_format » construit à la place les blueprints directement à partir des `datasetIds` référencés. Filtre par nom ou par catégorie (Battery, Stack, Module, Cell) et supporte les modes d'import `all`, `only_new_blueprints`, `only_specified_blueprints`, `only_specified_categories`, `new_format`.

### What
L'entrée est un classeur Excel stocké dans un partage, une feuille par famille de composants (Battery, Stack, Module, Cell, plus pièces non-batterie). La sortie est un jeu rafraîchi de blueprints plateforme et leurs datasets sous-jacents, visibles par toutes les apps de simulation aval. Les opérateurs déclenchent l'app depuis l'UI plateforme Altergo ; le run filtre par nom ou catégorie et choisit un mode d'import pour borner le rayon d'impact (tout régénérer, only-new, only-specified, only-categories, ou la voie new_format pilotée par dataset IDs).

### Tech
`main.py` orchestre le pipeline ; `src/download_xlsx.py` télécharge le classeur ; `src/inputs_extractor_from_excel.py` écrit les artefacts CSV et images par composant ; `src/generate_json_bp_battery_templates_from_csv.py` et son équivalent non-batterie produisent les JSON de blueprint ; `src/generate_bp_battery.py`, `src/generate_bp_non_battery.py` et `src/create_bps_from_datasets.py` appellent le SDK Altergo pour supprimer et recréer atomiquement blueprints et datasets ; `src/delete_bps.py` gère la passe de nettoyage. `altergo-settings.json` l'enregistre comme app plateforme de catégorie Simulation avec son schéma de paramètres.

### Status
Outil d'import en masse interne d'Altergo, dernière activité 2025-10. Lancé quand le tableur de composants amont change et que le catalogue plateforme doit être reconstruit. `requirements.txt` embarque un token d'accès Bitbucket en dur — déjà signalé au propriétaire ; à rotater et déplacer dans la configuration d'environnement.

## simple-app

simple-app est le scaffold vide d'une "app" sur la plateforme Altergo (par opposition à un modèle) — `entrypoint.py` initialise le client SDK Altergo, lit les `configurationValues`, et s'arrête sur un commentaire `# Your logic here`. Pas de README, pas de vraie logique ; `altergo-settings.json` déclare un seul paramètre placeholder. Scaffold de référence, pas un projet.

### What
Point de départ qu'un client Altergo ou un développeur interne fork pour construire une "app" plateforme custom — une unité de code que la plateforme planifie et exécute contre des assets, distincte du type "model". Le dépôt fournit un client SDK fonctionnel et le câblage des paramètres ; tout le reste est à remplir.

### Tech
Quatre fichiers : `entrypoint.py` (`extract_altergo_parameters` → `Client(functionArguments=…)`), `altergo-settings.json` (déclare `type: "app"`, un seul placeholder `parameter1`), `dev-parameters.json` (shim d'exécution locale), `requirements.txt` (épingle `altergo-sdk` depuis la branche bitbucket `release/alpha`). Pas de tests, pas de logique, pas de README.

### Status
Dernier commit 2024-10. Vit comme template de référence aux côtés du scaffold function-template (`simple-soc-model`) ; les deux couvrent les côtés "app" et "model" de l'ABI fonction Altergo. Pas un livrable, utilisé par d'autres dépôts comme point de départ.

## openclaw-config

openclaw-config est le répertoire de configuration et d'état d'OpenClaw, un runtime d'agent personnel tournant en continu — registres de providers/modèles, profils d'auth, workspaces par agent (main, inbox, robin), appareils appairés, jobs cron, complétions shell et mémoire SQLite, le tout en fichiers versionnés. Ce n'est pas un codebase déployable ; c'est le substrat sur lequel l'agent lit et écrit. Comprend la configuration d'un canal WhatsApp et une petite page canvas HTML de test. Privé, modifié en continu au fil de l'apprentissage de l'agent.

### What

Le repo est le répertoire `~/.openclaw/` d'un hôte d'agent personnel, capturé dans git pour rendre les changements de config inspectables et réversibles. Au premier niveau : `openclaw.json` est la config centrale ; `agents/` contient un sous-dossier par agent (`main`, `inbox`, `robin`), chacun avec ses propres `auth.json`, `auth-profiles.json` et `models.json` ; `cron/jobs.json` planifie les tâches récurrentes ; `devices/paired.json` et `pending.json` suivent les appareils qui ont complété un pairing Ed25519 avec des tokens scope opérateur ; `identity/` détient la keypair et l'état d'auth du device ; `memory/main.sqlite` est la mémoire persistante ; `completions/` livre les complétions shell pour bash/zsh/fish/PowerShell ; `canvas/index.html` est une petite page JS de test qui exerce `webkit.messageHandlers.openclawCanvasA2UIAction` (iOS) et l'équivalent Android pour valider le canal d'actions UI de l'agent depuis une webview.

### Tech

`openclaw.json` est un document JSON unique que le runtime fusionne avec ses défauts. Sections : `meta` (timestamps de version), `wizard` (état d'onboarding), `auth.profiles` (tuples provider × mode), `models` en mode `merge` listant des providers OpenAI-compatibles custom (par ex. nexos.ai, le `moonshotai/kimi-k2.5` hébergé par NVIDIA), `agents.defaults` (modèle primaire, workspace, `compaction.mode: safeguard`, `maxConcurrent: 4`, `subagents.maxConcurrent: 8`) plus une `agents.list` qui override par agent, `hooks.internal` (boot-md, session-memory), `channels.whatsapp` (`dmPolicy: pairing`, `groupPolicy: allowlist`, `mediaMaxMb: 50`) et `gateway` (HTTP loopback port 18789 avec auth token-mode et toggle Tailscale, plus `nodes.denyCommands` qui bloque `camera.snap`, `screen.record`, `calendar.add`, etc.). Des backups `openclaw.json.bak.1..4` sont conservés à chaque écriture significative. Le `auth-profiles.json` par agent stocke les clés OpenRouter avec `usageStats` (lastUsed, errorCount) pour la sélection de fallback.

### Status

Privé. Reflète une install personnelle active — `lastTouchedVersion: 2026.2.17`, `lastTouchedAt: 2026-02-19`. La liste `cron/jobs.json` est vide (`[]`) ; WhatsApp est le seul plugin activé. La mémoire SQLite est petite (~68KB). Le repo existe pour que les éditions de config OpenClaw — fréquentes au fil de l'apprentissage de l'agent — aient un historique.

## opus-infra

opus-infra est l'application Next.js 16 + Supabase qui soutient OPUS, une revue scientifique où les manuscrits sont traités comme des objets typés plutôt que des PDF — contenu versionné, extraction de claims (contribution / résultat / méthode / limite avec références d'évidence et de citation), et un workflow de statuts qui fait passer une soumission de brouillon à revue IA par rubrique, appariement de reviewers, revue humaine et consensus, jusqu'à greenlit ou refus. La revue IA et l'extraction de claims appellent toutes deux Claude (`claude-opus-4-7`) via le SDK Anthropic en tool-use ; l'éditeur rend markdown + KaTeX et les diffs de versions. Des tests d'intégration Vitest couvrent articles, revue, revue IA, claims et supervision admin. Privé, à un stade précoce mais déjà substantiellement câblé.

### What

L'unité, c'est la soumission, pas le PDF. L'auteur rédige son manuscrit en markdown + math, le soumet, et l'article entre dans une machine à états explicite : `draft → ai_review → ai_passed → matching → in_human_review → greenlit | declined`. Pendant `ai_review`, le système lance en parallèle deux appels Claude en tool-use — un scorer par rubrique et un extracteur de claims — et expose les deux résultats sur le manuscrit. Les claims sont typés (`contribution`, `result`, `method`, `limitation`), portent des `evidence_refs` (locateurs de section / figure / table / équation) et des `citation_refs` (texte brut + DOI optionnel), et peuvent être `suggested` (IA), `accepted` ou `dismissed` par l'auteur. Les éditeurs apparient ensuite les reviewers humains aux tags du sujet, collectent les revues, et la logique de consensus décide. Il existe une surface publique `/published` et une surface d'oversight admin pour les éditeurs.

### Tech

La revue IA (`src/lib/ai-review/reviewer.ts`) appelle `claude-opus-4-7` via `@anthropic-ai/sdk` avec un unique outil `submit_rubric_review` dont le schéma impose un `summary` plus une entrée par critère (`structure`, `clarity`, `methodology`, `integrity`, chacun avec seuil de passage à 70). L'extracteur de claims (`src/lib/claims/extract.ts`) suit le même pattern avec un outil `submit_claims` dont le JSON Schema énumère les quatre types de claim et les quatre kinds d'evidence ref. Les deux system prompts sont envoyés avec `cache_control: { type: "ephemeral" }` pour profiter du prompt-cache au-delà des retries. Les versions sont stockées en lignes séparées dans `article_versions` et rendues via un pipeline markdown + KaTeX + remark-math, plus `diff` pour les vues entre versions. L'appariement de reviewers (`src/lib/review/matching.ts`) est une intersection de tag-sets lowercase scorée par cardinalité, triée descendante. Les tests d'intégration sous `tests/integration/` (`articles`, `human-review`, `ai-review`, `profiles`, `public-access`, `admin-oversight`) tournent contre un vrai Supabase via `db-helpers.ts`.

### Status

Privé au 2026-05 ; pas encore ouvert aux auteurs. Schéma, workflow de statuts, pipeline IA, modèle de claims, appariement, consensus et surfaces admin sont en place avec couverture d'intégration — substantiellement au-delà du prototype, mais aucune vraie soumission en cours. Deux scripts de seed (`seed:accounts`, `seed:articles`) bootstrappent un environnement dev.

## su2re

su2re est un transcripteur Electron multiplateforme couplé à un backend Python. Le processus main Electron enregistre un raccourci global push-to-talk et lance un des trois points d'entrée Python — `transcriber_backend.py` pour la transcription brute, `..._diarization.py` pour `pyannote/speaker-diarization-community-1` au-dessus de `faster-whisper`, ou `streaming_transcriber.py` — la communication passant par des lignes `STATUS:` sur stdout. Côté JS, `ai-improver.js` appelle OpenAI `gpt-4o-mini` pour nettoyer les transcriptions et extraire les événements de calendrier en JSON ; `calendar-scheduler.js` enveloppe `googleapis` pour s'OAuth dans Google Calendar et y insérer les événements. Cibles Windows NSIS/portable, macOS DMG, Linux AppImage via electron-builder.

### What

On presse Ctrl+Shift+Space depuis n'importe où sur le desktop, on parle, on relâche : l'audio est transcrit localement et atterrit en texte dans l'onglet actif. On dépose un fichier audio (MP3/WAV/M4A/FLAC/OGG/OPUS/MP4/AVI/MKV) sur l'app pour une transcription plus longue avec choix de taille de modèle (tiny à large-v2). Avec la diarisation activée, les speakers sortent codés couleur et leurs labels sont éditables. L'onglet IA propose des presets de nettoyage (ton pro, concis, bullets, résumé) ; l'onglet calendrier extrait les événements de la transcription, demande confirmation à l'utilisateur, puis les insère dans le calendrier Google principal.

### Tech

Architecture en deux processus : `main.js` Electron porte le cycle de vie, `globalShortcut.register`, `spawn('python', ...)` et parse les lignes `STATUS:` + payloads sur stdout ; les renderers (`renderer.js`, `renderer-tabs.js`, `renderer-diarization.js`, `renderer-improvement.js`, `renderer-calendar.js`) découpent l'UI par feature. Côté Python, `faster-whisper` pour l'inférence Whisper et `pyannote.audio` avec `speaker-diarization-community-1` pour la diarisation, tous deux 100 % locaux. `ai-improver.js` appelle OpenAI `gpt-4o-mini` deux fois en mode calendrier — une pour nettoyer, une pour extraire les événements en tableau JSON strict. `calendar-scheduler.js` stocke credentials et tokens OAuth dans `electron-store` et appelle `google.calendar('v3').events.insert`. Les modèles peuvent être bundlés dans l'installeur via `extraResources` pour éviter à l'utilisateur de télécharger plusieurs gigaoctets au premier lancement.

### Status

Construit en octobre 2025 — dernier commit 2025-10-17 (« Implement calendar scheduling and speaker diarization features »). ~175 Ko de JS + Python, electron-builder produit du NSIS + portable Windows, DMG macOS, AppImage Linux. Utilitaire personnel, non distribué.

## article-checker

article-checker est une esquisse Create-React-App de 2023 : on colle un article dans un textarea, l'appli l'envoie à GPT-3.5 avec un system prompt « professeur de journalisme », puis affiche la réponse JSON structurée sous forme de radar et de jauges Plotly (répartition du but, score d'objectivité, consistance logique). Construit avec React 18, react-bootstrap et le client openai appelé directement depuis le navigateur — la clé API était commitée dans le code, raison parmi d'autres pour laquelle le projet n'est jamais sorti. Abandonné.

### What
Une page. L'utilisateur colle un texte d'article dans un textarea
(`QuestionForm`) ; `chatGPTService` appelle GPT-3.5-turbo avec un system prompt
unique embarqué dans le bundle et le schéma JSON de la réponse attendue. Le
résultat est parsé puis routé vers un `RadarChart` (but : Teach / Inform /
Persuade / Entertain / Evaluate, somme à 100 %), deux `GaugeChart` (objectivité
en %, consistance logique en %), et un `AnswerCard` listant les figures
rhétoriques et sophismes repérés. Un `cannedResponse.json` est livré pour le
travail d'UI hors-ligne.

### Tech
CRA + React 18 + react-bootstrap, `openai@3.2.1` instancié côté client. Un
`news_extractor.ts` à base de cheerio est présent mais non branché. Pas de
backend, pas d'auth. La clé OpenAI est en dur dans
`src/services/chatGPTService.ts` — quiconque a le bundle a la clé.

### Status
~3 semaines de travail le soir début 2023, abandonné en mars 2023. Jamais
déployé, jamais partagé. Tué par la clé commitée, l'absence de moat sur
« demander à GPT de noter un article », et la perte d'intérêt. Conservé comme
trace de l'idée.

## bisque

Bisque est une landing teaser d'une seule page sur Next.js 16 et React 19. Toute l'appli tient sur une page : un bouton « this button does nothing » qui incrémente un compteur de clics et révèle une suite de messages sur le thème du homard (« told you. », « 🦞 », « nothing, but with intention. »), un toggle clair/sombre via next-themes et une lueur orangée. Construit avec les primitives shadcn/ui sur Tailwind 4, en placeholder pour `bisque.life` ; « v0.0.1 — the primordial soup ».

### What
Un seul fichier (`src/app/page.tsx`). Titre « bisque.life », une accroche
(« something useful and delicious is brewing. swarms of lobster agents are
assembling. »), le bouton, la ligne de whisper, un compteur de clics qui
apparaît à partir de 3 clics, et un blurb de teasing qui se révèle à 5 clics.
Toggle de thème en haut à droite, emoji homard, blurs orangés en arrière-plan.

### Tech
Next.js 16, React 19.2, Tailwind 4, `next-themes`, un `Button` shadcn. Pas de
backend, pas d'analytics, pas d'état au-delà de `useState`.

### Status
Placeholder v0.0.1 pour `bisque.life`. Construit en février 2026. Pas déployé
publiquement.

## saas

saas est un bac à sable en deux packages pour un jeu navigateur temps réel (le nom du slug est un reliquat d'une ancienne idée — ce n'est pas un SaaS). `game-server` est une application NestJS 11 dont le `GameGateway` fait tourner une boucle WebSocket socket.io qui suit les joueurs, reçoit des messages `inputUpdate` et diffuse l'état ; `game-client` est un client Phaser 3 + Vite en TypeScript avec une logique de missiles/radar/ciblage (vaisseaux, symboles de lock, starfield) montée dans Phaser Editor. Expérience personnelle d'architecture multijoueur temps réel ; non déployé.

### What

Le joueur charge une scène Phaser (une scène `Level` préchargée par `Preload`) et arrive dans une arène spatiale 2D avec son propre vaisseau, quelques drones seedés, un système de missiles à lock-on et un HUD (`PlayerStatus`) par-dessus un starfield. L'input passe par WebSocket en messages `inputUpdate` ; le serveur résout déplacements, cooldowns de tir, comportement des drones et locks de cible, puis re-broadcaste l'état autoritatif à tous les clients. Le ciblage se fait via un événement `toggleTarget` que le client envoie pour accrocher ou lâcher un lock missile sur un autre vaisseau.

### Tech

Deux packages, pas d'outil monorepo — juste des dossiers frères partageant un `package-lock.json` à la racine. `game-server` est NestJS 11 avec `@nestjs/platform-socket.io` et `@nestjs/websockets` ; le `GameGateway` (`src/game/game.gateway.ts`) ouvre CORS uniquement à `http://localhost:3001` et délègue à `GameService` (`src/game/game.service.ts`), qui détient le monde (`ships`, `missiles`, `lastMissileFireTimes`) et tick via `setInterval` à un `fixedDelta` de `1/30` s — boucle serveur à 30 Hz. Les vaisseaux se déclinent en `PlayerShip` et `DroneShip` sur une base `Ship` commune ; les missiles ont une durée de vie de 5000 ms et une poussée de 25. `game-client` est le template Phaser 3.80 + Vite TypeScript avec `socket.io-client@4`, scènes éditées en `.scene` à côté de leur `.ts` dans Phaser Editor.

### Status

Bac à sable personnel. Dernière activité 2025-02. Non déployé, sans cible de production — construit pour explorer la boucle d'un serveur WebSocket autoritatif pilotant un client Phaser. Le slug `saas` trompeur est le seul reliquat d'une ancienne idée.
