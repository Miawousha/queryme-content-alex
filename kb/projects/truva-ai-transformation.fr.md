---
name: Transformation IA de Truva
description: "La mission de transformation IA de Matrice pour Truva, plateforme de revente de logements à Mumbai : postes de travail à agents, plateforme d'analyse des conversations, noyau de modèle opérationnel et outils associés."
year: 2026
tags: &a1
  - ai-agents
  - claude
  - consulting
  - real-estate
  - nextjs
  - typescript
repos:
  - name: truva-mapper-agent
    role: author
    visibility: private
    description: Mapper v1, un poste de travail de cartographie des résidences et
      d'estimation où des agents Claude proposent et du code déterministe
      applique, avec une console Next.js, un worker et une CLI d'opérateur.
    year: 2026
    last_active: 2026-09
    language: TypeScript
    archived: false
    tags: *a1
  - name: truva-mapping-assistant
    role: author
    visibility: private
    description: Mapper v2, un document JSON versionné par résidence, édité dans une
      application Next.js par une personne et par Claude Code via une CLI.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags: *a1
  - name: truva-intelligence
    role: author
    visibility: private
    description: Plateforme d'analyse des conversations qui transforme les échanges
      captés avec acheteurs et vendeurs en une vue des acheteurs, des biens et des
      transactions, chaque fait étant relié à sa source.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags:
      - ai-agents
      - llm-extraction
      - supabase
      - nextjs
      - typescript
  - name: truval
    role: author
    visibility: private
    description: Poste de travail d'estimation, une estimation versionnée par
      appartement, calculée par un portage de l'arithmétique d'estimation de
      Truva et travaillée dans le navigateur ou par Claude Code.
    year: 2026
    last_active: 2026-09
    language: TypeScript
    archived: false
    tags: *a1
  - name: truva-os
    role: author
    visibility: private
    description: Noyau de modèle opérationnel pour reproduire l'activité de Truva
      dans de nouveaux clusters, avec schémas JSON, fichiers de gouvernance et
      manuel consultable dans le navigateur.
    year: 2026
    last_active: 2026-08
    language: TypeScript
    archived: false
    tags:
      - operating-model
      - knowledge-base
      - json-schema
      - react
  - name: inox
    role: contributor
    visibility: private
    description: Le déploiement par Matrice, aux couleurs de Truva, de la plateforme
      open source de recherche et d'agents Onyx, l'index sur lequel repose Truva
      Intelligence.
    year: 2026
    last_active: 2026-08
    language: Python
    archived: false
    tags:
      - onyx
      - rag
      - deployment
      - docker
  - name: inox-ask
    role: author
    visibility: private
    description: CLI Node sans dépendance qui pose une question aux agents Inox
      depuis le terminal et affiche la réponse avec ses citations.
    year: 2026
    last_active: 2026-08
    language: JavaScript
    archived: false
    tags:
      - cli
      - onyx
      - nodejs
  - name: sales-playbook
    role: author
    visibility: private
    description: Guide de vente construit à partir de principes de base pour les
      appels aux vendeurs et aux acheteurs de logements, structuré pour qu'un
      coach d'appel IA puisse le citer.
    year: 2026
    last_active: 2026-09
    language: Markdown
    archived: false
    tags:
      - sales
      - docs
      - ai-agents
  - name: truva-consulting
    role: author
    visibility: private
    description: Dépôt de travail partagé de la mission, dont le contenu est publié
      en direct comme espace client de Truva sur le site de Matrice.
    year: 2026
    last_active: 2026-09
    language: HTML
    archived: false
    tags:
      - consulting
      - docs
      - knowledge-base
  - name: truva-consulting-archive
    role: author
    visibility: private
    description: Première version du dépôt de l'espace client (de juillet à début
      août), remplacée par truva-consulting.
    year: 2026
    last_active: 2026-08
    language: HTML
    archived: false
    tags:
      - consulting
      - docs
  - name: truva
    url: https://github.com/Miawousha/truva
    role: author
    visibility: public
    description: Le modèle d'organisation de Truva dans l'ontologie graybox,
      construit à partir de sources publiques et validé en CI.
    year: 2026
    last_active: 2026-07
    language: JSON
    archived: false
    tags:
      - ontology
      - graybox
      - organization-modeling
---

De juillet à octobre 2026, Matrice Technologies, la société d'Alexandre, a mené une mission de transformation IA pour Truva, une plateforme de revente de logements basée à Mumbai. La mission a commencé par une phase de découverte : un modèle d'organisation de Truva rédigé dans l'ontologie graybox d'Alexandre à partir de sources publiques, et un espace client partagé où chaque document de la mission était publié pour que Truva puisse le lire. À partir d'août, le travail s'est organisé en plusieurs chantiers, chacun livré chaque semaine : Truva Intelligence, qui enregistre les conversations avec acheteurs et vendeurs et en tire une vue des acheteurs, des vendeurs, des biens et des transactions où chaque fait renvoie à sa source, avec Inox (un déploiement de l'outil open source Onyx) qui indexe les données de Truva en dessous ; Truva Academy, une plateforme de formation pour les équipes de Truva (qui a sa propre fiche) ; Truva OS, le modèle opérationnel mis par écrit sous forme de noyau versionné ; et des postes de travail à agents pour cartographier les résidences et estimer les appartements, qui ont connu trois dépôts successifs (mapper v1, mapper v2 et truval). Autour de ces chantiers s'ajoutent un client en ligne de commande pour les agents Inox et un guide d'appels de vente destiné à un coach d'appel IA. Quelques règles valent pour tous les chantiers : ce que produit un agent est une proposition, appliquée par du code déterministe et validée par une personne ; les données de production de Truva sont lues par une connexion en lecture seule et protégée, et jamais modifiées sans la signature d'une personne ; les déploiements tournent sur Coolify derrière une connexion Google ; et chaque dépôt fixe dans un `CLAUDE.md` ses règles de travail pour les sessions Claude Code.

## truva-mapper-agent et truva-mapping-assistant

Le cartographe de résidences, en deux versions. L'inventaire de Truva est organisé par résidence (tours, colonnes d'appartements, plans, lots), et constituer ce référentiel à la main à partir des plaquettes, des plans et des dossiers RERA est lent. Les deux dépôts sont des postes de travail pour cette tâche ; la v1 (`truva-mapper-agent`, du 24 août au 16 septembre, environ 1 380 commits) faisait tourner les agents sur un serveur, et la v2 (`truva-mapping-assistant`, du 16 septembre au 12 octobre, environ 540 commits) a déplacé le travail des agents dans une session Claude Code sur la machine de la personne qui cartographie.

### What

**La v1** est un poste de travail où opèrent deux agents. Le cartographe de résidences passe d'un nom de résidence à un inventaire cartographié : une passe de collecte cherche les sources de la résidence sur le web et dans le registre RERA, une étape de rendu extrait le texte, les tableaux et les figures de chaque PDF, une passe de vision lit les planches de plans, un juge construit la vue tour par tour, et un vérificateur la contrôle à partir des mêmes sources figées. Une personne retouche ensuite cette vue sur la fiche de la résidence et la publie jalon par jalon (la liste des tours d'abord, puis chaque tour). L'agent d'estimation fait passer un lot cartographié par l'assemblage, le jugement et la vérification jusqu'à une proposition qu'une personne approuve. Chaque décision qui revient à une personne devient une ligne dans une boîte de revue, et tout résultat reste une proposition tant qu'une personne ne l'a pas signé.

**La v2** garde le domaine et abandonne les agents côté serveur. Chaque résidence est un document JSON, versionné sur la plateforme : chaque envoi crée une nouvelle version avec un message et un auteur, un envoi portant sur des entités nommées n'est refusé que si quelqu'un a modifié ces mêmes entités depuis la version de départ, et rien n'est supprimé. Une session Claude Code travaille la résidence via la CLI `truva-mapper` et une skill `society-mapper` fournie avec elle, une entité à la fois et avec une source sur chaque ligne ; une personne lit et modifie le même document dans l'application, dont les tableaux s'éditent comme un tableur et dont les dessins montrent chaque tour étage par étage. L'application initialise une nouvelle résidence à partir des données existantes de Truva et compare à tout moment la version cartographiée avec elles, et une étape de relecture conditionne la publication. En octobre, l'application a été renommée Tru Storey et a reçu son propre logo.

### Tech

**La v1** est un monorepo pnpm d'une douzaine de paquets dont les dépendances vont dans un seul sens : `@mapper/core` (schémas des changements, grammaire des étages, échelle des jalons, aucune entrée-sortie), `@mapper/corpus` (un stockage de captures adressé par contenu et le rendu des documents), `@mapper/db` (Prisma sur sa propre base MySQL de 34 modèles, plus un lecteur limité aux SELECT pour la base produit de Truva), `@mapper/valuation` (un portage déterministe du calcul de prix et de la notation des comparables de Truva, dont la parité avec l'original est vérifiée), `@mapper/harness`, `@mapper/sessions` (chaque nœud qui appelle un modèle), `@mapper/applier`, `@mapper/evals`, `@mapper/market` et `@mapper/desk`. La console est en Next.js 15 avec NextAuth, shadcn sur Base UI et Cesium pour les cartes ; `aidesk` est un client HTTP sans dépendance pour l'API de la console, avec 54 commandes. La pile déployée compte six conteneurs sur Coolify : la base des agents, le worker, la console, un tunnel SSH vers la base produit, docling-serve pour les PDF et Crawl4AI pour les captures de pages.

**La v2** se compose d'une application Next.js 15 (`web/`), d'un paquet pur `@v2/society` (schéma, grammaire des étages, validation, normalisation, diff et initialisation à partir des données de Truva) et d'une CLI en un seul fichier, avec son installateur et sa skill intégrée. Le stockage est en SQLite (better-sqlite3) sur le volume de l'application ; la base de Truva est atteinte par un lecteur protégé qui n'autorise qu'un `SELECT` ou un `SHOW` à la fois. Un banc d'évaluation note une résidence cartographiée par rapport aux propres données de Truva. Vitest et TypeScript strict (`noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`) dans les deux versions.

### Status

La v1 a tourné sur sa pile déployée jusqu'au deuxième des cinq jalons sur une résidence de référence, et sa chaîne d'estimation a été construite jusqu'au vérificateur ; ni l'une ni l'autre n'a écrit dans le système de Truva, l'applicateur n'ayant jamais reçu d'identifiants en écriture. La v2 lui a succédé mi-septembre ; elle est déployée comme application Coolify derrière une connexion Google, et son dernier commit date du 12 octobre 2026. Les deux dépôts sont privés.

## truva-intelligence

### What

La plateforme qui tient à jour une vue étayée des acheteurs, des vendeurs, des biens et des transactions de Truva, et en tire les analyses et les actions recommandées qui aident à vendre un bien. Ses principes affichés : les conversations brutes sont conservées telles quelles et chaque fait dérivé renvoie à sa source ; l'extraction est versionnée et rejouable ; rien n'est écrit dans le CRM tant que la précision de l'extraction n'a pas été mesurée ; la capture est passive, pour que personne n'ait à changer sa façon de travailler pour l'alimenter ; et la plateforme recommande tandis que les personnes décident. Début octobre, le travail livré comprenait le socle de l'application et des comptes sur invitation avec des rôles, la capture WhatsApp pour que chaque chargé de clientèle voie ses propres fils, un catalogue d'analyses, les préférences des acheteurs lues comme « impératif » ou « souhait » avec le texte d'où elles viennent, un moteur de rapprochement entre acheteurs et biens, les lieux proches de chaque résidence, et un éditeur de zones où une personne trace, contrôle et arbitre les contours des quartiers.

### Tech

Une application Next.js 15 sur Supabase (Postgres avec PostGIS, 89 migrations), MapLibre et Cesium pour les cartes, et un ensemble de services Node : un worker, un moteur d'analyses où chaque analyse appuyée sur un modèle est une définition typée et versionnée et où chaque exécution est enregistrée à l'identique, l'extraction des préférences avec son propre banc de notation, des tests de transcription, un service Slack et une preuve de concept d'agent LangChain. Les appels aux modèles passent par le SDK Anthropic et par Gemini. Une CLI `truva-intel` accompagnée d'une skill Claude donne accès aux lectures des acheteurs depuis le terminal. La conception repose sur quatre couches : capture brute, fils normalisés et reliés, extraction versionnée, et un modèle d'entités vivant dont l'état courant est le repli d'un journal de transitions. Le travail est planifié dans un backlog d'ordres de travail numérotés, rapportés à un document décrivant l'état cible, selon une méthode sdlc intégrée au dépôt.

### Status

Actif du 7 août au 2 octobre 2026, environ 330 commits. Déployé et en première version ; les appels et leur transcription étaient les prochaines sources de capture. Privé.

## truval

### What

Un poste de travail d'estimation : une estimation JSON par appartement, versionnée dans l'application, travaillée par une personne dans le navigateur ou par une session Claude Code via la CLI `truval`, chacune pouvant faire tout le travail seule. Toutes deux renseignent des données d'entrée (les faits, les ventes comparables retenues et pourquoi, les ajustements laissés à l'estimateur, le niveau de confiance, les règles) et le moteur calcule le prix. Seules les entrées sont écrites ; la plateforme recalcule le détail du calcul dans chaque version enregistrée, si bien que l'historique montre l'effet de chaque modification sur le prix, et une écriture sur un chiffre calculé est refusée en indiquant l'entrée à renseigner à la place.

### Tech

C'est la v2 du cartographe reconstruite pour les estimations : une application Next.js 15 sur SQLite, un paquet pur `@truval/valuation` (schéma, validation, diff, initialisation à partir des données de Truva et `price.ts`, l'arithmétique d'estimation de Truva reproduite à la roupie près et vérifiée sur ses estimations finalisées par une évaluation de parité), et une CLI empaquetée par le paquet `served-tool` de Matrice et servie par l'application elle-même. Les scripts tournent sous `TZ=Asia/Kolkata`, car le calcul des mois du moteur dépend de l'heure locale. Déployé sur le même hôte que l'assistant de cartographie, derrière une connexion Google, avec poppler pour afficher les plans conservés en PDF.

### Status

Construit du 28 au 30 septembre 2026 (environ 150 commits). Privé.

## truva-os

### What

La base de connaissances dont Truva se servirait pour reproduire son activité dans de nouveaux clusters : chaque nouvelle agence, dirigée de bout en bout par un Cluster CEO, suit le même noyau versionné et construit par-dessus sa propre base locale. Le noyau décrit une boucle de transaction en huit étapes, les rôles et équipes responsables de chaque étape, sept schémas JSON, des fichiers de gouvernance (des limites et un registre d'indicateurs qui associe chaque indicateur à son lecteur) et un vocabulaire figé que chaque document et chaque agent doit employer. Chaque fichier indique s'il s'appuie sur les documents de Truva ou sur la conception de Matrice, et un guide d'exploitation précise quels domaines sont étayés et lesquels restent provisoires.

### Tech

Du Markdown et du JSON sous `kernel/`, un validateur Python pour toute l'arborescence, et une visionneuse React 19 / Vite 8 lancée par la commande `truvaos`, qui affiche le noyau comme un manuel dans le navigateur, avec des tests de contraste des couleurs et de taille minimale des polices. Un banc de simulation d'agences, où des agents font tourner des agences fictives pour tester le noyau de bout en bout, est spécifié mais pas encore construit.

### Status

Rédigé du 13 au 18 août 2026 (90 commits) et consulté comme un dépôt, sans application déployée. La suite attendait des documents de la part de Truva. Privé.

## inox et inox-ask

### What

Inox est le déploiement par Matrice d'[Onyx](https://github.com/onyx-dot-app/onyx), une plateforme open source de recherche et d'agents IA, aux couleurs de Truva et utilisée comme index sous Truva Intelligence : elle indexe les sources GitHub, Notion, Slack et WhatsApp de Truva et expose des agents qui répondent avec citations. Onyx est un projet tiers ; le fork limite ses modifications à de petits ajouts pour que les fusions avec la version amont restent simples. Ces modifications sont l'habillage Truva sous forme de surcharge de variables de thème, un connecteur en lecture seule pour la messagerie WhatsApp qui indexe les conversations par tranches de temps fixes afin que les identifiants de documents ne bougent jamais, une archive brute qui conserve les données sources qu'Onyx jette habituellement, un explorateur de conversations sur cette archive, et la correction de trois bogues de la version amont. La part d'Alexandre est le déploiement et la configuration de l'instance, pas le code du fork ni Onyx.

`inox-ask` est le client en ligne de commande d'Alexandre pour cette instance : `inox-ask "question"` envoie une question à un agent Onyx et affiche la réponse synthétisée avec ses citations sous forme de liens markdown, pour qu'une personne ou une session Claude Code puisse demander comment Truva procède sans quitter le terminal. Il interroge l'agent plutôt que l'index brut, parce que l'agent renvoie environ un kilo-octet de réponse là où la recherche dans l'index renvoie chaque document correspondant en entier.

### Tech

Inox tourne à partir du déploiement Docker Compose d'Onyx, avec une surcouche pour le développement local ; les ajouts du fork sont un connecteur Python et une migration Alembic côté serveur, et quelques fichiers TypeScript dans l'application web Next.js. `inox-ask` est un unique script Node 20 sans dépendance : il liste les agents visibles avec une clé d'API (en indiquant si chacun peut accéder au web), poursuit une session en se rattachant au dernier message de l'assistant, et analyse la réponse en flux d'Onyx en suivant la profondeur des accolades d'un fragment à l'autre, avec un autotest qui rejoue un flux découpé à chaque position possible.

### Status

Inox a été forké et configuré à la mi-août 2026 et sert d'index à Truva Intelligence. `inox-ask` a été écrit le 17 août 2026. Les deux dépôts sont privés.

## sales-playbook

### What

Un guide court, à lire en une vingtaine de minutes, pour deux types d'appels : les propriétaires qui envisagent de vendre et les acheteurs qui se sont renseignés sur une annonce. Sept principes valent pour tous les appels ; chaque type d'appel a ensuite un déroulé, une liste de qualification (ce qu'il faut apprendre et une bonne question pour l'obtenir) et un tableau des objections. Il est rédigé pour qu'un coach IA qui écoute un appel en direct puisse suggérer l'étape suivante en citant la section d'où elle vient.

### Tech

Du Markdown, une idée par titre pour que chaque titre soit une section citable, plus un fichier `coach.yaml` qui déclare les étapes, les champs de qualification et les objections que le coach suit pour chaque type d'appel.

### Status

Rédigé le 30 septembre 2026. Privé.

## truva-consulting

### What

Le dépôt de travail partagé de la mission, rédigé pour être lu par Truva. Son dossier `content/` est affiché en direct comme espace client de Truva sur le site de Matrice : une fusion sur `main` vaut publication, et une pull request tient lieu de brouillon. Il contient les documents de découverte, de démarche et de réalisation, une présentation construite à partir d'un script, dont les diapositives sont vérifiées par rapport à un storyboard relu avant d'être assemblées, des explications interactives en HTML, un script qui prépare les notes de version de chaque semaine à partir des changements de code dans chaque dépôt, et la spécification d'un entraîneur aux jeux de rôle d'acquisition qui a précédé Truva Academy. Le modèle d'organisation graybox y est inclus comme sous-module et affiché sous forme de graphe interactif. `truva-consulting-archive` est la première version du même espace client, de juillet à début août, conservée comme archive.

### Tech

Du Markdown avec en-têtes conformes au contrat de rédaction de l'espace client, des scripts de génération Node et Python pour la présentation et les contenus intégrés (polices embarquées, aucune requête vers un tiers dans le résultat), et un script de validation de l'espace.

### Status

Actif du 11 juillet au 10 septembre 2026 (environ 130 commits) ; l'archive couvre la période du 6 juillet au 7 août. Les deux dépôts sont privés.

## truva (modèle graybox)

### What

Le modèle d'organisation de Truva dans graybox, l'ontologie d'Alexandre pour décrire les organisations sous forme de données typées et validées. Le modèle a été construit à partir de sources publiques et ne contient aucune donnée confidentielle du client. Il couvre 45 activités, 30 ressources, 10 agents et 9 objectifs, ainsi que des facettes de structure, de flux de valeur, de gouvernance et de capacité, dont les droits de décision pour les activités soumises à approbation.

### Tech

La disposition en fichiers séparés de graybox : `org/org.json` plus un fichier JSON par entité. `graybox validate` vérifie l'intégrité référentielle et le schéma, `graybox lint` signale la dette de rédaction, et `graybox report` produit un diagnostic. Un workflow GitHub Actions lance le validateur à chaque push et à chaque pull request, dès que la CLI graybox sera publiée.

### Status

Créé le 26 juin 2026 et mis à niveau vers l'ontologie 0.2.0 le 13 juillet 2026. Public, et utilisé comme sous-module de l'espace client.
