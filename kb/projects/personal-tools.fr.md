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
  - name: xblock
    url: https://github.com/matrice-technologies/xblock
    role: author
    visibility: public
    description: Extension Chrome pour bloquer rapidement sur X, avec des listes de
      blocage partageables et un serveur auto-hébergeable.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags:
      - browser-extension
      - typescript
      - express
      - prisma
      - open-source
  - name: book1doc
    url: https://github.com/Miawousha/book1doc
    role: author
    visibility: public
    description: Montre les créneaux Doctolib réellement réservables par un nouveau
      patient, via une extension, une application web et une CLI. Non affilié à
      Doctolib.
    year: 2026
    last_active: 2026-08
    language: HTML
    archived: false
    tags:
      - browser-extension
      - python
      - healthcare
      - open-source
  - name: papylantir
    role: author
    visibility: private
    description: Agent de veille nocturne pour la porte d'entrée d'un proche âgé,
      avec analyse de scène, conversation vocale et alertes silencieuses.
    year: 2026
    last_active: 2026-09
    language: Python
    archived: false
    tags:
      - python
      - ai-agents
      - computer-vision
      - voice
      - gemini
  - name: matrice-osint-fisc
    role: author
    visibility: private
    description: Outils OSINT sur sources publiques françaises pour le journalisme
      d'investigation en matière fiscale et financière.
    year: 2026
    last_active: 2026-10
    language: Python
    archived: false
    tags:
      - osint
      - python
      - cli
      - open-data
      - journalism
  - name: coolify-cli
    url: https://github.com/matrice-technologies/coolify-cli
    role: author
    visibility: public
    description: CLI légère pour piloter une instance Coolify v4 auto-hébergée
      (déploiement, variables d'environnement, inspection), pensée pour des
      déploiements menés depuis une conversation.
    year: 2026
    last_active: 2026-07
    language: TypeScript
    archived: false
    tags:
      - cli
      - devops
      - typescript
      - open-source
  - name: nextjs-boilerplate
    role: author
    visibility: private
    description: Socle SaaS Next.js avec authentification Supabase, espaces de
      travail, membres et invitations, projets et paramètres.
    year: 2026
    last_active: 2026-08
    language: TypeScript
    archived: false
    tags:
      - nextjs
      - supabase
      - typescript
      - boilerplate
  - name: ionenergy-website
    role: author
    visibility: private
    description: Site vitrine réalisé pour ION Energy avec Next.js et shadcn/ui.
    year: 2026
    last_active: 2026-09
    language: TypeScript
    archived: false
    tags:
      - nextjs
      - website
      - typescript
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

## xblock

XBlock est une extension Chrome pour bloquer rapidement des comptes sur X (anciennement Twitter), avec des listes de blocage que l'on peut partager et auxquelles on peut s'abonner. Matrice Technologies l'a publiée en open source sous licence MIT en octobre 2026, avec son serveur d'API auto-hébergeable et un site public.

### What

Depuis le site de X, l'utilisateur bloque un compte en un clic et l'ajoute à sa propre liste. Une liste se partage par un code ; ses abonnés bloquent alors automatiquement tous les comptes qu'elle contient, ce qui se prête à la modération communautaire. L'extension et le site existent en sept langues (anglais, français, espagnol, allemand, japonais, portugais du Brésil, indonésien), et l'extension est disponible sur le Chrome Web Store. Le blocage s'accompagne d'animations propres à l'extension, dont un mode « Samurai » où le message est découpé en morceaux ; le haut de la page d'accueil du site en propose une démonstration jouable sur un faux fil d'actualité.

### Tech

Un dépôt en trois parties. `chrome_extension/` est une extension Manifest V3 construite avec webpack, traduite au moyen des fichiers de messages i18n de Chrome. `server/` est une API Express 5 avec Prisma sur SQLite et une limitation du débit ; un secret côté serveur transforme le jeton de chaque utilisateur en identifiant par HMAC, les origines d'extension autorisées sont déclarées pour CORS, et des points d'accès d'administration facultatifs donnent des statistiques d'usage et des listes sélectionnées. Le serveur est livré sous forme d'image Docker qui applique les migrations au démarrage. `website/` est un site Next.js avec Tailwind et shadcn/ui, avec un dictionnaire par langue vérifié par un script, et les visuels du Chrome Web Store sont générés à partir du site. `DEPLOY.md` explique comment héberger son propre serveur.

### Status

Publié en open source le 30 octobre 2026 en version 1.6.4 ; version 1.7.1, avec les sept langues, le même jour. Dépôt public.

## book1doc

book1doc montre les créneaux Doctolib qu'un nouveau patient peut réellement réserver. La page de recherche de Doctolib affiche, pour chaque praticien, la prochaine disponibilité du motif de consultation retenu par son moteur, et pour les spécialistes il s'agit souvent d'un suivi ou d'un examen technique qu'un patient qui n'a jamais consulté n'a pas le droit de réserver, ce qu'on ne découvre que plusieurs clics plus loin. Non affilié à Doctolib ; projet personnel, publié sur le compte GitHub personnel d'Alexandre.

### What

Trois interfaces partagent la même logique. DoctoBook, une extension pour Chrome, Edge et Firefox, ajoute à chaque fiche de la page de résultats Doctolib une ligne indiquant ce qu'un nouveau patient peut réserver, et quand. Une petite application web prend une URL de recherche collée et range les praticiens en trois groupes : réellement réservable, affiché mais pas pour un nouveau patient, et rien en ligne. Une CLI Python lance la même recherche avec export HTML et JSON, des filtres sur le secteur de conventionnement et l'âge, et une recherche élargie autour des coordonnées. Le README donne un exemple mesuré : pour une spécialité dans une ville, le 28 août 2026, 10 praticiens listés, 8 affichés comme disponibles, et 1 seul réellement réservable pour une première consultation.

### Tech

L'outil appelle les points d'accès publics et non authentifiés de Doctolib (recherche, informations du parcours de réservation, disponibilités) et réimplémente la règle, appliquée côté navigateur, qui décide si un motif de consultation est ouvert aux nouveaux patients, ainsi que les restrictions de conventionnement et d'âge ; les noms des motifs servent seulement à étiqueter et à ordonner les résultats. L'extension envoie les requêtes depuis la session du navigateur de l'utilisateur, sans serveur central. L'application web n'a besoin d'un backend que parce que Doctolib n'envoie pas d'en-tête CORS : un serveur Node sans état, à quatre routes validées, déployable sur Cloudflare Workers avec Wrangler. La CLI n'utilise que la bibliothèque standard de Python et `certifi`.

### Status

Publié le 31 août 2026 sous licence MIT. Dépôt public.

## papylantir

Papylantir est un agent de veille nocturne pour la porte d'entrée du domicile d'un proche âgé, construit en septembre 2026. Quand quelqu'un bouge devant la porte la nuit, l'agent lui parle par un haut-parleur, écoute, évalue s'il semble réveillé et orienté, l'invite doucement à retourner se coucher, et prévient la famille si nécessaire.

### What

La conception part de l'hypothèse qu'un passage nocturne est ordinaire, et cherche à rester calme et bref. Un agent de vision décrit la scène environ une fois par seconde sous une forme JSON fixe (qui est présent, ce qu'il fait, un niveau de risque), et une règle codée n'ouvre une conversation que sur des signes concrets de sortie, comme une main sur la poignée, des clés, des chaussures ou un manteau. Un agent superviseur relit le journal de la nuit toutes les quelques secondes pour repérer ce qu'une image isolée ne montre pas, comme une longue immobilité ou des allers-retours, et c'est le seul chemin vers une alerte ; une porte d'entrée ouverte déclenche une alerte urgente par une règle écrite en dur. L'agent vocal se présente comme l'assistant de la maison, jamais comme un proche, et ne dit jamais à voix haute qu'il prévient quelqu'un. La surveillance ne fonctionne que pendant les heures de nuit configurées et démarre en pause.

### Tech

Python 3.12. Détection de mouvement avec OpenCV (ou détection de personne en option), compréhension de scène avec Gemini Flash-Lite, et un superviseur Claude dont la sortie JSON est contrainte par un schéma. Deux chaînes vocales interchangeables : Silero VAD, faster-whisper et réponses Claude en streaming lues par ElevenLabs ; ou une seule session Gemini Live pilotée par une machine à états explicite, dans laquelle c'est le code, et non le modèle, qui décide de chaque transition. Les alertes partent vers ntfy ou un webhook. Un tableau de bord FastAPI sur le réseau local affiche la vidéo en direct, l'état des agents, les images analysées et le journal des événements, et rejoue les épisodes enregistrés à partir d'un journal d'état ; chaque épisode est enregistré avec la vidéo qui précède le déclenchement, les deux pistes audio et l'ensemble des échanges avec l'IA. Caméra, micro et haut-parleur se changent par configuration, d'une webcam à une caméra RTSP.

### Status

Construit du 8 au 10 septembre 2026 ; une première version qui tourne sur un PC local. Dépôt privé.

## matrice-osint-fisc

matrice-osint-fisc est un ensemble d'outils OSINT sur sources publiques françaises, construit chez Matrice Technologies en octobre 2026 pour appuyer le journalisme d'investigation en matière fiscale et financière. Il est pensé pour être utilisé avec Claude : le journaliste pose sa question, Claude appelle l'outil `fisc`, recoupe les résultats et tient le dossier d'enquête selon des règles de méthode écrites.

### What

La CLI `fisc` recherche, pour une personne, les mandats sociaux, les annonces légales et les déclarations d'intérêts des responsables publics ; dresse la fiche d'une société et de ses dirigeants ; construit le réseau de sociétés et de holdings autour d'une personne, avec en option les biens immobiliers détenus par ces sociétés ; compare les déclarations d'intérêts au registre des entreprises ; interroge les bases de fuites offshore et les listes de sanctions ; et passe au crible tous les déclarants nationaux pour repérer les mandats absents de leurs déclarations, classés par niveau de confiance. Une commande de banc d'essai rejoue des affaires déjà jugées. Un dossier peut être présenté sous forme de page de synthèse avec une version anonymisée, et exporté en un seul fichier chiffrable par phrase de passe. L'outil ne qualifie rien : il dit ce que contiennent les registres publics, où et quand, et à quel point un enregistrement correspond à la personne recherchée.

### Tech

Python, géré avec uv, avec httpx, DuckDB (qui lit à distance des fichiers Parquet publiés par l'administration fiscale) et PyYAML. Les sources comprennent l'API de l'Annuaire des Entreprises (RNE et SIRENE), le BODACC, la HATVP, les données de la DGFiP sur les biens des personnes morales, les Offshore Leaks de l'ICIJ et OpenSanctions. Les réponses brutes peuvent être archivées dans le dossier d'enquête avec URL, date et empreinte SHA-256, et chaque commande dispose d'une sortie JSON destinée à Claude. Les graphes de réseau s'exportent en JSON, Mermaid, GraphML et en vue HTML consultable hors ligne, construite avec Cytoscape.js. Un skill Claude Code décrit la démarche d'enquête.

### Status

Construit les 22 et 23 octobre 2026. Dépôt privé.

## coolify-cli

coolify-cli est un petit outil en ligne de commande pour piloter une instance Coolify v4 auto-hébergée, écrit chez Matrice Technologies en juillet 2026 pour pouvoir lancer des déploiements depuis une conversation avec un agent.

### What

Les commandes couvrent les profils (`config set`, `config use`, `config ls` avec jetons masqués), la liste des applications, services, bases de données, projets et serveurs, l'inspection d'une ressource par nom ou UUID, le déploiement avec suivi de son état, et la consultation, la définition ou la suppression de variables d'environnement avec redéploiement en option. Les commandes de lecture acceptent `--json` pour une sortie exploitable par machine, et `COOLIFY_URL` et `COOLIFY_TOKEN` l'emportent sur les profils enregistrés.

### Tech

TypeScript avec commander, construit avec tsup, testé avec Vitest, avec un résolveur nom vers UUID, des utilitaires de sortie en tableau et en JSON, et un workflow GitHub Actions qui teste et construit à chaque push et pull request.

### Status

Version 0.1.1 publiée le 13 juillet 2026. Dépôt public.

## nextjs-boilerplate

nextjs-boilerplate est le point de départ de Matrice Technologies pour ses produits Next.js, créé en août 2026 : les briques dont tout produit a besoin, tirées d'un produit qui fonctionne, dont on a retiré le produit.

### What

Authentification par lien magique et Google OAuth via Supabase ; espaces de travail avec logo, que l'on crée, change, renomme et supprime ; membres avec rôles propriétaire, administrateur et membre, invitations par e-mail qui expirent et un garde-fou qui empêche un espace de perdre son dernier propriétaire ; projets, avec une page presque vide où vient se loger le produit ; et une section de paramètres pour le profil, l'apparence, l'espace de travail et les membres. Aune est construit sur cette base et en garde la trace.

### Tech

Next.js 16, React 19, TypeScript, shadcn sur Base UI et Tailwind 4, avec thèmes clair et sombre. Le schéma Supabase tient en trois migrations (tables et déclencheurs, politiques de sécurité au niveau des lignes et droits, espaces de stockage), et le README détaille les pièges de la combinaison entre droits et RLS. Le déploiement repose sur un serveur Coolify qui héberge à la fois Supabase et l'application, mené par un agent Claude selon une procédure écrite.

### Status

Créé les 12 et 13 août 2026. Dépôt privé.

## ionenergy-website

ionenergy-website est le site vitrine qu'Alexandre a réalisé pour ION Energy, éditeur de logiciels d'intelligence batterie pour les flottes de véhicules électriques et le stockage à l'échelle du réseau.

### What

Un site d'une seule page, avec un composant par section, des études de cas en PDF à télécharger et une image d'aperçu pour les réseaux sociaux générée à la compilation. Tous les textes, chiffres et liens se trouvent dans un seul fichier de contenu, pour être modifiés au même endroit.

### Tech

Next.js (App Router), React 19, Tailwind CSS 4, shadcn/ui et les icônes lucide, avec les couleurs de la marque définies en variables CSS.

### Status

Réalisé d'abord en juillet 2026 comme une reconstruction en Next.js de l'ancien site d'Altergo conçu avec Framer, puis adapté à la marque ION Energy en septembre 2026. Dépôt privé.
