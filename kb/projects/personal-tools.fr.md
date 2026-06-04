---
name: Personal tools
year: 2026
tags:
  - productivity
repos:
  - name: toudoux
    role: author
    visibility: private
    description: App todo Next.js 15 qui fait aussi office de serveur MCP protégé
      par OAuth, pilotée depuis Claude.
    year: 2026
    last_active: 2026-04
    language: TypeScript
    archived: false
    tags:
      - productivity
      - mcp
      - nextjs
      - typescript
  - name: sirene
    url: https://github.com/Miawousha/sirene
    role: author
    visibility: public
    description: Application desktop Tauri 2 pour éditer des diagrammes Mermaid avec
      aperçu SVG en direct.
    year: 2026
    last_active: 2026-02
    language: TypeScript
    stars: 0
    archived: false
    tags:
      - desktop
      - react
      - typescript
      - tooling
  - name: roadmap
    url: https://github.com/ION-Altergo/roadmap
    role: contributor
    visibility: private
    description: Espace de roadmap interne — DSL de tâches en markdown et viewer
      Svelte Gantt/équipe.
    year: 2026
    last_active: 2026-01
    language: Svelte
    archived: false
    tags:
      - svelte
      - productivity
      - docs
---

Quelques petits outils de productivité personnels.

## toudoux

toudoux est une app todo Next.js 15 qui fait aussi office de serveur Model Context Protocol. `src/app/api/mcp/route.ts` enveloppe `mcp-handler` avec une vérification bearer OAuth par requête et enregistre quatre familles d'outils liées à l'utilisateur authentifié : todos (list/add/update/complete/delete), people (un roster avec mentions), recurrences (`add_recurring`, `list_recurring`, `stop_recurring` pilotés par rrule) et stats. Le serveur OAuth2 est codé à la main sous `src/lib/mcp/oauth` avec PKCE, enregistrement dynamique de clients et les routes de découverte `.well-known`, en parallèle de NextAuth v5 avec l'adapter Drizzle sur pg. Banc d'essai quotidien pour MCP — l'app navigateur et le serveur MCP partagent le même schéma Drizzle, et les outils sont ceux qu'Alexandre utilise vraiment depuis Claude.

### What

Deux surfaces sur une seule base Postgres. Dans le navigateur, on se connecte via NextAuth et on tombe sur un dashboard façon Trello allégé pour les todos, les contacts (mentionnables avec `@nom`) et les règles récurrentes exprimées en strings rrule. Dans Claude (ou tout client MCP), on passe l'OAuth une fois via le modal « connect Claude » du dashboard, puis on ajoute/liste/complète des todos, on cherche ou fusionne des personnes, on planifie des récurrences, on tire les stats — tout en parlant à l'agent. Les deux surfaces voient les mêmes données parce qu'elles tapent sur les mêmes tables Drizzle.

### Tech

`src/app/api/mcp/route.ts` parse l'en-tête `Authorization: Bearer` via `resolveUserFromAuthHeader`, renvoie un `401` avec `WWW-Authenticate` pointant sur `/.well-known/oauth-protected-resource` quand il manque, et construit sinon un `mcp-handler` neuf par requête, avec chaque outil enregistré contre le `userId` résolu. L'issuer OAuth2 est codé à la main — `src/lib/mcp/oauth/{issuer,clients,authz,tokens,pkce,crypto}.ts` couvrent la découverte, l'enregistrement dynamique de clients, le flow authorisation code + PKCE et la signature des tokens. Les récurrences utilisent le paquet `rrule`. Drizzle sur `pg` (`src/lib/db/`), tests via Vitest, env validée dans `src/lib/env.ts`.

### Status

Actif tout au long de 2026 — dernier commit 2026-04 (« feat(dashboard): add 'connect Claude' button with MCP setup modal »). ~175 Ko de TypeScript, privé, mono-utilisateur. Utilisé quotidiennement depuis Claude ; le dashboard sert surtout au setup et à une édition manuelle de temps en temps.

## sirene

Sirene est une application desktop Tauri 2 pour éditer des diagrammes Mermaid avec un aperçu en direct. La coque Rust embarque les plugins clipboard, fs et dialog autour d'un renderer React 19 où CodeMirror 6 s'installe dans un split-pane Allotment à côté d'un aperçu SVG Mermaid 11, avec arborescence de fichiers, onglets multiples et huit modèles de démarrage (flowchart, sequence, class, state, ER, gantt, pie, gitGraph). Ctrl+S/O/N/W/C correspondent à sauvegarder, ouvrir, nouvel onglet, fermer onglet et copier-en-PNG ; le rendu PNG passe par un canvas off-screen dans `src/lib/clipboard.ts`. shadcn/ui + Tailwind 4 pour l'habillage, thèmes clair/sombre câblés via un hook `useTheme`.

### What

Éditeur mono-fenêtre : on choisit un modèle dans la toolbar ou on ouvre un fichier `.mmd` depuis l'arbre, on tape le source Mermaid à gauche, le SVG se redessine à droite à chaque frappe. Les onglets multiples permettent de basculer entre diagrammes ; les fichiers récents persistent entre sessions ; l'aperçu est zoomable (molette, Alt-drag, bouton fit-to-view). Ctrl+C sur l'aperçu copie un PNG 2x retina directement dans le presse-papiers — collable dans Word ou Google Docs sans étape d'export.

### Tech

Le crate Rust dans `src-tauri/` est mince — `tauri-plugin-clipboard-manager`, `tauri-plugin-fs`, `tauri-plugin-dialog`, `tauri-plugin-log` et la feature Tauri `image-png`. Toute l'UX vit côté React : `App.tsx` câble les raccourcis clavier, `hooks/useTabs.ts` porte l'état multi-document, `hooks/useFileTree.ts` la vue répertoire, `lib/templates.ts` les huit diagrammes seed, `lib/preprocessor.ts` quote automatiquement les labels à caractères spéciaux, `lib/clipboard.ts` rastérise le SVG en PNG via canvas off-screen plus `DOMParser` pour injecter `xmlns` et width/height explicites. CodeMirror 6 avec un mode Mermaid maison dans `lib/mermaid-lang.ts`.

### Status

Démarré début 2026, dernier commit 2026-02 (« Auto-close tabs when files are deleted or renamed »). Installeur ~3 Mo, Windows + macOS (Intel + Apple Silicon), version 0.2.0. Outil perso, utilisé pour faire les diagrammes des notes et decks d'Alexandre.

## roadmap

roadmap est l'espace interne de planification produit d'ION-Altergo, principalement du markdown (`Adani/overview.md`, `Adani/tasks.md`, snapshots archivés, docs de référence SBOM/certification) animé par un petit viewer Svelte 4 + Vite dans `Adani/viewer/`. Le viewer parse une DSL de tâches maison (`++X` effort, `~X` lead time, `@W` ancrage semaine, suffixe owner) en diagramme de Gantt et en vue d'allocation par membre d'équipe ; il charge `tasks.md` au runtime ou accepte un upload de fichier. Outil fonctionnel côté navigateur, sans backend ; ce n'est pas une app SvelteKit.

### What
Le contenu utile du repo est le markdown — l'overview de l'engagement Adani BESS, la liste vivante `tasks.md`, les rapports d'allocation d'équipe hebdomadaires, les snapshots d'archive datés, et le matériel de référence (overview plateforme Altergo, SBOM, matrice de certification) sous `reference/`. Les tâches suivent un jeu de règles strict : tâches dans une section séquentielles haut-en-bas, sections sœurs en parallèle, même owner dans la même section ne peut pas chevaucher, sections imbriquées héritent de la semaine de départ du parent sauf override, `*m` marque les milestones de matrice de certification. Le viewer Svelte en fait un Gantt + dashboard de capacité pour les syncs hebdo.

### Tech
Svelte 4 + TypeScript + Vite, pas de SvelteKit, pas de backend — `index.html` + `src/main.ts` montent `App.svelte`. Le parser DSL vit dans `src/lib/`, produit des tâches avec semaines start/end calculées qui respectent les règles d'héritage et d'ordre, et alimente deux vues : un timeline Gantt et un graphique d'allocation par owner. Charge `tasks.md` via `fetch` en dev/preview ou via upload de fichier en fallback. Pur côté client ; se déploie en fichiers statiques au besoin.

### Status
Actif en 2026-01 pour l'engagement BESS ADANI sur 24 mois — pilote les syncs hebdo et le suivi de certification. Rôle contributeur — Alexandre a construit le viewer et le parser DSL, écrit la liste de tâches, possède la majeure partie du markdown de planification. Outil mono-utilisateur aujourd'hui ; partageable en équipe dans le navigateur sans infra.
