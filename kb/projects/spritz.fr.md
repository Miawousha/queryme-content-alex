---
name: Spritz
year: 2025
tags:
  - productivity
repos:
  - name: spritz
    url: https://github.com/ION-Altergo/spritz
    role: contributor
    visibility: private
    description: Gestionnaire de tâches Altergo d'origine — tâches markdown, collab
      Firebase temps réel, animations GSAP.
    year: 2025
    last_active: 2025-04
    language: JavaScript
    archived: false
    tags:
      - productivity
  - name: spritz-modern
    url: https://github.com/ION-Altergo/spritz-modern
    role: contributor
    visibility: private
    description: Réécriture React + TS de spritz — Redux Toolkit, Styled Components,
      React Spring, Vite.
    year: 2025
    last_active: 2025-04
    language: TypeScript
    archived: false
    tags:
      - react
      - typescript
      - productivity
  - name: spritz-svelte
    role: author
    visibility: private
    description: "App SvelteKit de gestion de tâches : collaboration temps réel Yjs,
      auth/data Firebase, offre Premium Stripe."
    year: 2025
    last_active: 2026-02
    language: Svelte
    archived: false
    tags:
      - svelte
      - typescript
      - productivity
---

Spritz est le gestionnaire de tâches d'Alexandre, décliné dans plusieurs stacks. Les dépôts ci-dessous en sont les implémentations.

## spritz

spritz est le gestionnaire de tâches d'équipe Altergo d'origine, une SPA en pur HTML/CSS/JS avec GSAP pour le mouvement et Firebase Realtime Database pour l'état partagé. Un éditeur markdown à gauche se rend en liste de tâches interactive à droite — clic gauche pour basculer, clic droit sur une tâche complétée déclenche une suppression sonorisée, et les tâches inactives se mettent lentement à « couler » via un filtre SVG goo après 24 h. La collab temps réel est réellement câblée : chaque board a une URL `?taskId=`, et `database.ref('taskLists/' + id).on('value', ...)` pousse les modifications à tous ceux qui ont le lien. Hébergé sur Firebase App Hosting ; supplanté en interne par `spritz-modern`.

### What
Les utilisateurs écrivent les tâches en lignes markdown (`[ ] Fix bug @alice p**`) — le suffixe `@owner` désigne l'assigné et `p*` / `p**` / `p***` règle la priorité, rendue en badges colorés. Le panneau d'édition reste la source de vérité ; le panneau de droite est une liste rendue depuis le modèle, cliquable, avec un son sur toggle et une animation de destruction par filtre goo sur le clic droit. Un lien de partage en bas porte le `?taskId=` du board ; ouvrir l'URL dans un autre onglet ou appareil rejoint en live le même nœud Firebase.

### Tech
JS vanilla découpé en modules ciblés : `markdownParser.js` parse les lignes en modèle de tâches, `modelRenderer.js` peint la liste interactive, `animations.js` pilote les timelines GSAP et le filtre SVG goo, `skinManager.js` permute les bundles CSS+JS de skins (default et dark-blue livrés dans `js/skins/`), et `share.js` gère le setup Firebase SDK v8, le `?taskId=` d'URL, les sauvegardes `database.ref('taskLists/' + id).set(...)` et les abonnements `.on('value', ...)`. L'« ooze » des tâches inactives compare les timestamps serveur `lastUpdated` à maintenant et fait monter le filtre goo au-delà des 24 h. Déployé via `apphosting.yaml` sur Firebase App Hosting ; `database.rules.json` laisse la realtime DB ouverte à quiconque détient un task ID.

### Status
Construit et utilisé par l'équipe Altergo jusqu'en 2025, dernière activité avril 2025. Supplanté en interne par `spritz-modern` (la réécriture React) puis par la version personnelle SvelteKit d'Alexandre. Codebase gelée en pur JS ; le projet Firebase (`spritz-31ad5`) et les URLs live résolvent encore.

## spritz-modern

spritz-modern est la réécriture React + TypeScript du gestionnaire de tâches Altergo spritz, construite sur Vite avec Redux Toolkit (slices theme et tasks), Styled Components, React Spring, react-dnd et Firebase pour la persistance et la présence. Le périmètre d'origine est repris — éditeur markdown, liste de tâches interactive, collaboration par URL via les hooks `useCollaboration` et `useTaskData`, skinning thémé via un `ThemeProvider` styled-components. Atteint la parité de fonctionnalités avec `spritz` et ajoute un système de skin typé par composants qui rend l'ajout de thèmes trivial. Suite interne ; supplantée plus tard par la version personnelle en SvelteKit.

### What
Même UX à deux panneaux que l'original — éditeur markdown à gauche, liste de tâches interactive à droite avec toggles, badges de priorité, mentions d'assigné et drag-and-drop pour réordonner via react-dnd. Le partage passe toujours par une URL `?taskId=` adossée à Firebase Realtime Database ; ouvrir le lien ailleurs rejoint le même board en live, avec un `CollaborationIndicator` qui affiche les autres utilisateurs actifs. Le changement de thème est exposé dans le header et permute toute la surface (couleurs, polices, animations de drop, icônes) sans recharger.

### Tech
Layout sous `src/` : `components/{Layout,TaskInput,TaskDisplay,Shared}` pour l'UI, `hooks/useTaskData.ts` et `hooks/useCollaboration.ts` enveloppent les lectures/écritures Firebase et la présence, `store/` contient les slices Redux Toolkit (`themeSlice`, tasks), `skins/themes/` livre les thèmes `default`, `darkBlue` et `altergo` plus un contrat `ThemeType` dans `types.ts` que tout nouveau skin implémente (`colors`, `text`, `animations`, `icons`). Styled Components lit le thème actif via `ThemeProvider` ; React Spring pilote les animations physiques de drop et destruction déclarées par thème. Vite + ESLint + TS strict ; Firebase SDK v9 modulaire ; échantillons et notes de migration conservés dans `samples/`.

### Status
Continuation interne du spritz d'origine, dernière activité avril 2025. Atteint la parité de fonctionnalités puis stagne — la version personnelle SvelteKit (`spritz-svelte`) prend le relais comme surface préférée d'Alexandre. Non déployée publiquement ; vit dans le GitHub de l'organisation comme référence React canonique pour l'idée du système de skins.

## spritz-svelte

spritz-svelte est une app SvelteKit 2 + Svelte 5 organisée en spaces et boards, avec édition riche collaborative dans les cartes via Yjs (provider Firestore `y-fire`, `y-quill`, `quill-cursors`). Firebase gère l'auth et les données via des services dédiés sous `src/lib/services/firebase` ; Stripe verrouille une offre Premium à 3,99 €/mois (le tier gratuit est plafonné à 1 space) avec les routes webhook + checkout + portal sous `src/routes/api/stripe`. SendGrid et Resend envoient les invitations, et l'app s'expédie via l'adaptateur Vercel. Expérience produit personnelle — la collab temps réel et le parcours d'upgrade sont câblés de bout en bout, pas en stub.

### What

Chaque utilisateur a une liste de spaces ; un space contient des boards ; un board contient des cartes rangées en listes, avec drag-and-drop (`svelte-dnd-action`, `sortablejs`) et descriptions en rich-text. La carte s'ouvre sur un éditeur plein écran où plusieurs utilisateurs peuvent taper simultanément, voir le curseur de l'autre, et ne pas écraser leurs modifications mutuelles. On invite par email, on accepte via lien tokenisé, on passe Premium depuis le dashboard quand le plafond gratuit d'1 space coince.

### Tech

Les documents Yjs sont persistés directement dans Firestore via `y-fire`, sans serveur websocket séparé. Quill 2 héberge l'éditeur, `y-quill` le binde à un `Text` Yjs, `quill-cursors` rend l'awareness. Firebase Admin (`firebase-admin`) porte les routes serveur ; la stack Stripe est répartie entre client (`@stripe/stripe-js`) et routes serveur checkout/portal/webhook sous `src/routes/api/stripe`. Les emails passent par `@sendgrid/mail` et `resend` avec `nodemailer` en fallback. Déploiement via `@sveltejs/adapter-vercel`. Vitest + `@testing-library/svelte` pour les tests unitaires.

### Status

Démarré en 2025, dernier commit 2026-02 (« Remove SpotifyPlayer component from SpaceHeader »). ~920 Ko de source Svelte, privé. L'embed Spotify a été retiré en fin de course ; la surface produit reste la boucle spaces/boards/cartes avec édition collaborative et tier payant, câblée bout en bout mais jamais lancée.
