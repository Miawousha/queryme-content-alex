---
name: Aune
description: "Une méthode ouverte pour lire les programmes politiques français promesse par promesse, et Cpromis, l'outil de décision civique qui s'appuie dessus pour la présidentielle de 2027."
year: 2026
tags: &a1
  - civic-tech
  - politics
  - ai-agents
  - nextjs
  - supabase
  - cli
url: https://cpromis.fr
repos:
  - name: aune
    role: author
    visibility: private
    description: Méthode Aune et site Cpromis pour lire, comparer et vérifier les
      programmes de la présidentielle 2027, avec agents externes et revue humaine.
    year: 2026
    last_active: 2026-10
    language: JavaScript
    archived: false
    tags: *a1
---

Aune est une méthode pour lire les programmes politiques français à la lettre, promesse par promesse, conçue chez Matrice Technologies pour la présidentielle de 2027. Cpromis est le site public qui l'applique : un outil de décision civique qui aide chacun à dire ce qui compte pour lui, à examiner les programmes et à faire son propre choix. La méthode, la CLI et les éditions publiées portent le nom d'Aune ; le site s'appelle Cpromis et est en ligne sur cpromis.fr. Le projet est rédigé en français et mis à l'épreuve en public, comme une méthode en construction.

## What

Chaque promesse passe par les mêmes quatre questions, à réponses fermées et selon des règles écrites, pour que tous les programmes soient lus avec la même grille. Le site s'ouvre sur trois entrées : « Promis ? » (ce qu'un programme promet, et avec quelle précision), « Et vous ? » (un court profil de ce qui compte pour le lecteur) et « D'accord ? » (les relations entre un profil et les promesses). Les programmes se lisent à six niveaux, du programme entier jusqu'à la source d'une vérification, et une page par sujet montre côte à côte les promesses de chaque programme, sans total ni classement.

Le cahier des charges fixe des limites strictes : pas de recommandation de vote, pas de classement des candidatures, pas de note globale, pas de prédiction électorale ni de jugement moral sur les personnes. Toute conclusion doit renvoyer à un passage et à un critère identifiés ; l'incertitude et l'abstention sont des résultats valides ; une édition publiée ne change jamais, et une correction en crée une nouvelle. Une personne identifiée répond de chaque publication, et les lecteurs peuvent contester un constat par un formulaire public. « Mon profil » fonctionne sans compte et compare dans la page sans rien envoyer ; un compte sert seulement à enregistrer un profil.

Les analyses sont rédigées, relues et publiées par des agents IA qui travaillent dans des sessions externes, au moyen d'une CLI et d'un skill distribués par la plateforme. Aune n'héberge aucun agent. Les contributeurs disposent d'un espace à part, avec des écrans pour le corpus, la revue, les éditions et les contestations. En octobre 2026, la feuille de route a remplacé les programmes de démonstration inventés par des échantillons de programmes réels, un par grand courant politique, avec douze promesses citées mot pour mot sur quatre sujets (santé, pouvoir d'achat, sécurité et justice, énergie et climat).

## Tech

Une application Next.js 16 et React 19 en TypeScript, avec des modules partagés et serveur en ES modules simples, shadcn sur Base UI et Tailwind 4. Elle part de la boilerplate Next.js de Matrice, dont elle garde l'authentification Supabase, les espaces de travail et la sécurité au niveau des lignes (RLS). Les éditions suivent un format versionné doté d'un JSON Schema ; des scripts les scellent par empreinte et les vérifient, et les tests tournent avec `node --test`. La CLI des agents est construite à partir d'un outil maison qui empaquette la CLI et son skill. L'estimation de l'impact des mesures a commencé avec un référentiel d'indicateurs et une preuve de concept OpenFisca. Un push sur `main` reconstruit l'instance publique sur Coolify, hébergée sur GCP à Paris.

## Status

En développement actif depuis septembre 2026 ; dernier commit en octobre 2026. Le cahier des charges en était à la version 5.2.0 le 20 octobre 2026, et les documents précisent qu'aucune règle de la méthode n'a encore été validée par une mesure. Dépôt privé ; le site est public.
