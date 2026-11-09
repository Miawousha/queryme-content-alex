---
name: Graybox
description: "Une méta-ontologie ancrée dans la littérature pour modéliser les organisations sous forme de données typées et validées, avec une CLI locale, un explorateur de graphe et une visionneuse hébergée."
year: 2026
tags: &a1
  - ontology
  - typescript
  - zod
  - cli
  - nextjs
  - d3
repos:
  - name: graybox
    role: author
    visibility: private
    description: Une méta-ontologie ancrée dans la littérature pour modéliser les
      organisations sous forme de données typées et validées, avec une CLI
      locale, un explorateur de graphe et une visionneuse hébergée.
    year: 2026
    last_active: 2026-08
    language: TypeScript
    archived: false
    tags: *a1
---

Graybox est une méta-ontologie ancrée dans la littérature pour les entreprises et les organisations : un vocabulaire typé (agents, ressources, activités, objectifs, relations, frontières, plus huit facettes couvrant la structure, le flux de valeur, les opérations, les capacités, l'environnement, la gouvernance, la délégation et la connaissance) qui permet de décrire n'importe quelle organisation sous forme de données vérifiées et lisibles par machine. Les modèles d'organisation sont des fichiers JSON conservés dans un dépôt git qui appartient à l'utilisateur. On les rédige et on les interroge avec une CLI locale, qu'il s'agisse d'un humain ou d'un agent local comme Claude, on les explore dans un explorateur React/D3, et on peut les consulter dans une visionneuse Next.js hébergée qui les lit depuis GitHub sans les stocker.

## What

L'unité de base est le modèle d'organisation : un ensemble de fichiers JSON qui décrit une organisation à travers des entités de base typées et huit facettes d'analyse (la facette opérations s'appelait coordination jusqu'en juillet 2026). Depuis juin 2026, le schéma s'est enrichi des facettes gouvernance, délégation et connaissance, des droits de décision, et d'une « colonne des finalités » pour les objectifs (type d'objectif, responsable, parties prenantes servies) qui relie la mission aux objectifs stratégiques et opérationnels, puis aux activités. Les modèles sont validés contre un schéma strict, contrôlés par des règles de lint (par exemple une approbation sans approbateur, un objectif sans responsable, une boucle de contrôle sans opérateur) et interrogés par des questions comme : qui est responsable d'une activité, qui décide, quelles règles s'appliquent à une activité, ou quelles sont les conséquences d'un changement sur une ressource. Une commande `report` produit un diagnostic en Markdown avec des sections sur les finalités, les droits de décision, la supervision, la préparation à la délégation et la fraîcheur des données. Un fabricant d'électronique fictif, Voltforge, sert d'organisation de démonstration de référence. Graybox a servi à modéliser l'organisation d'un client lors d'une mission de conseil de Matrice.

## Tech

Un monorepo TypeScript/ESM. La source de vérité est `@graybox/ontology` : un schéma Zod avec types inférés, `validateOrg`, `ingest`, des fonctions de lint et de requête, et une génération `toJsonSchema()` à la demande ; chaque objet est `.strict()`, donc tout champ inconnu fait échouer la validation. `@graybox/cli` fournit la commande `graybox`, qui fonctionne hors ligne : création, liste et affichage des organisations, verbes d'édition (`add`, `set`, `rm`, `link`, `unlink`, `rename`) qui revalident le modèle après chaque écriture, verbes de requête, `lint`, `report`, et `init-repo`, qui crée un dépôt par organisation avec des compétences d'agent pour extraire (`extract-org`) ou concevoir (`design-org`) un modèle. Les deux paquets sont publiés sur npm. `viz` est un explorateur React/D3 qui affiche un modèle sous forme de graphe, avec un mode de navigation qui suit la hiérarchie des objectifs à travers le modèle opérationnel. `web` est une application Next.js (App Router) pour la visionneuse hébergée : connexion via une GitHub App, sélecteur de dépôt, assemblage de l'organisation à partir de l'archive du dépôt (lue en flux, plafonnée en taille et mise en cache selon le dernier push), route `/demo` accessible sans connexion sur Voltforge, limitation de débit par IP et en-têtes de sécurité. Elle tourne dans un conteneur Docker sur Coolify, et sa seule base de données est une table de liste d'attente facultative. L'outillage repose sur vitest + tsx et requiert Node >= 20.

## Status

La contrainte initiale « local-first, sans backend hébergé » a été revue fin juin 2026 : les données d'organisation restent uniquement dans le dépôt git de l'utilisateur et la CLI fonctionne sans réseau, mais une visionneuse hébergée se place désormais devant ces dépôts. Les derniers travaux, en août 2026, ont fait de Voltforge une organisation de démonstration consultable dans la visionneuse sans connexion. Dépôt privé.
