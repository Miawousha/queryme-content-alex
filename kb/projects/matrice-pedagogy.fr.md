---
name: Cours de conception agentique pour une école d'ingénieurs
description: "Le travail de Matrice, mené à partir des premiers principes, sur ce qu'il reste à apprendre à l'ère des agents, appliqué à la conception d'un cours de conception agentique pour une école d'ingénieurs française, avec les essais et articles écrits en parallèle."
year: 2026
tags: &a1
  - education
  - agents
  - curriculum
  - writing
  - claude-code
repos:
  - name: matrice-pedagogy
    role: author
    visibility: private
    description: Espace de travail du projet pédagogique de Matrice. Fiches de
      concepts figées, établies à partir des premiers principes, conception du
      cours pour une école d'ingénieurs française, un essai sur la
      planification avec des agents et deux brouillons d'articles sur le
      travail avec des agents.
    year: 2026
    last_active: 2026-11
    language: Markdown
    archived: false
    tags: *a1
---

Matrice cherche, à partir des premiers principes, ce que les humains doivent encore apprendre maintenant que les agents prennent en charge l'essentiel de la production, et applique la réponse à la formation des ingénieurs. Le cas concret est un cours de conception agentique pour une école d'ingénieurs française, dont le cursus ne traitait encore ni de l'IA générative ni des agents en octobre 2026. Le travail a commencé comme préparation d'une intervention d'Alexandre dans cette école en novembre 2026. Il a produit trois choses : un ensemble de fiches de concepts figées (ce que veut dire apprendre, s'entraîner, et pourquoi apprendre encore quand les agents existent), une conception de cours rédigée en français pour l'école, et une série d'essais et d'articles sur le travail avec des agents. Le tout se trouve dans un dépôt privé où Alexandre travaille avec des agents Claude.

## What

**Les concepts.** Quatre définitions, chacune figée après relecture :

- **Apprendre :** garder, d'une expérience, quelque chose qui peut changer la façon dont on ressent, pense ou agit (version 10).
- **S'entraîner :** prendre part à des expériences conçues pour apprendre quelque chose de précis, dans le but de l'apprendre.
- **Apprendre et la vie bonne :** apprendre fait partie d'une vie bonne, façonne celui qui la vit, et sert de moyen. Les agents ne peuvent reprendre que le moyen.
- **Pourquoi apprendre :** une grille qui croise le bien que sert une raison (le mien, celui de mes proches, celui de la société) et ce que l'apprentissage fait pour ce bien (il en fait partie, il le permet, il le protège). Les agents peuvent fournir la colonne « le permet ». Ils ne peuvent pas faire partie de votre bien, ni vous protéger de votre dépendance envers eux. La grille donne un test pour n'importe quel cours : retirer les raisons que les agents couvrent désormais, et se demander si ce qui reste vaut le temps des étudiants.

Deux autres concepts, « juger » et « répondre de », sont prévus mais pas encore rédigés.

**La conception du cours.** Rédigée en français pour l'école, sous forme d'hypothèses de travail :

- **La carte des rôles.** Deux axes : voir (savoir juger la preuve qui fonde une décision) et signer (en répondre). La cible est l'ingénieur qui voit et signe. Le danger est celui qui signe sans voir : la faute retombe alors sur l'humain le plus proche, qui n'avait pas les moyens de juger. Les agents ne signent jamais. L'école ne peut faire progresser les étudiants que sur l'axe « voir », et elle le doit désormais, car les agents prennent en charge l'exécution, là où les jeunes ingénieurs apprenaient à voir.
- **Le cycle en V et la ligne du suffisant.** L'ingénieur garde trois actes : posséder le besoin et les critères d'acceptation, juger la preuve, décider de livrer. Partout, il lit la spécification et les preuves un niveau sous sa décision. Là où c'est nécessaire, il mène des vérifications approfondies ciblées (des « carottages »), choisies selon la gravité, selon qu'un composant est poussé hors des conditions couvertes par sa fiche technique, et selon la faiblesse de la preuve. Le document propose aussi une échelle d'indépendance pour vérifier le travail des agents, du même agent qui écrit le code et ses tests jusqu'à une autre famille de modèles avec un contexte vierge, complétée par des vérifications humaines, ainsi qu'un « exercice retourné » : les étudiants partent du dossier de conception d'un agent dans lequel on a glissé un défaut, et sont notés sur leur décision de livrer ou non, et sur leurs raisons.
- **Deux cas d'épreuve, avec les trois mêmes gestes (spécifier, conduire, valider).** En aval, un refuge de montagne à 2 500 m qui remplace son groupe diesel par des panneaux solaires et une batterie, et dont la radio de secours ne doit jamais s'éteindre avec les lampes. En amont, le choix d'un MOSFET pour un convertisseur : les étudiants construisent le jeu d'évaluation à partir de fiches techniques publiques, puis comparent un modèle de pointe doté d'un bon contexte, un modèle ouvert avec recherche documentaire et un petit modèle ouvert ajusté, et argumentent pour savoir si une entreprise doit entraîner le sien.
- **Une répétition du cas du refuge** avec quatre agents neufs (Claude Opus 5.5, contexte vide, sans outils), sur deux énoncés lancés deux fois chacun. Les quatre ont rejeté le chiffre de consommation du client, donné à la radio sa propre alimentation et refusé de signer « conforme » sans réserves. Seuls ceux qui disposaient des notes de visite sur place ont relié la tempête, le refuge plein et la radio. Chaque passage s'est terminé par une liste d'étapes que seuls des humains pouvaient boucler. Il en est sorti le déroulé d'une démonstration de 30 minutes.
- **Cinq idées de cours,** de la plus rapide à la plus ambitieuse : passer le cursus en revue cours par cours (garder, transformer ou réduire), des ateliers où les enseignants résolvent leur propre sujet d'examen avec un agent, un projet d'équipe semestriel qui va du besoin réel d'un porteur de projet jusqu'à un prototype construit avec des agents (noté sur la spécification, un journal de ce qui a été délégué et pourquoi, une soutenance orale et un jugement du résultat au regard du besoin, plus une petite partie faite à la main), un laboratoire sur les jeux d'évaluation et l'opportunité d'entraîner son propre modèle, et un tuteur qui guide sans faire le travail à la place de l'étudiant.
- **Le périmètre retenu** après la première séance de travail avec l'école (16 octobre 2026) : un projet d'étudiants « à tiroirs », la conception d'un convertisseur de puissance, par exemple un chargeur ou un disjoncteur statique, avec des outils d'IA générative. Les étudiants les plus à l'aise travaillent en haut du cycle en V : ils rédigent les spécifications et vérifient les résultats, dans la peau du responsable qui signe sans avoir fait les travaux lui-même. D'autres construisent les agents dont la tâche a besoin, qui enrichissent la base de départ d'une année sur l'autre.
- **Le premier support de l'intervention,** une « matrice de compréhension récursive » (9 octobre 2026) : sept capacités en trois groupes (comprendre, juger, agir), avec pour chacune la raison pour laquelle l'IA ne la rend pas inutile, la façon de l'enseigner et de l'évaluer, et un exemple tiré des domaines de l'école. Le dépôt la signale comme dépassée, car elle précède les fiches de concepts.

**Les textes.**

- **« My take on Planning with Agents »** (25 octobre 2026), une réponse à un essai publié sur la planification avec des agents. Il soutient que le temps humain doit aller aux extrémités du travail : une image partagée de l'objectif, construite à partir de prototypes riches auxquels chacun peut réagir et de choix entre des paires de variantes produites par des agents ; une vue de convergence qui montre d'un coup d'œil si les équipes d'agents se rapprochent du but ; et des critères d'acceptation écrits avant le début du travail, dont une partie reste hors de portée des agents. Il s'appuie sur des exemples historiques (la maquette en argile dans la conception automobile, une carte du XIXe siècle d'une campagne militaire ratée, le prix de la longitude du XVIIIe siècle, la direction par l'intention dans la doctrine militaire).
- **« Stages of delegation »,** une série prévue de quatre articles. L'article 1, « Work 2.0 », décrit six étapes du travail avec l'IA (seul, avec un chat, avec un agent, avec plusieurs, via un agent orchestrateur, via un arbre d'agents) et ce qui reste à la personne à chaque étape : décider de ce qu'on veut, juger si on l'a obtenu, et en répondre. Il est publié sur le site de Matrice. Les articles 2 à 4 (passer à l'étape suivante, travailler à grande échelle, équipes et institutions, écoles comprises) sont à l'état de plan, appuyés sur des notes de travail qui modélisent cette évolution par trois moteurs : combien de temps un agent peut travailler seul, combien coûte la vérification de son travail, et l'environnement réutilisable que la personne construit.
- **« Tools before agents »** (titre de travail « From Excel to Agents orchestration »), un article pour consultants et ingénieurs sur la démarche commune à cinq outils de Matrice (truva-mapper, Eloom, Truva Academy, truva-intel et Fixit) : construire pour les experts une application métier et une CLI d'un seul tenant, les amener à l'adopter, apprendre le domaine aux agents et les mesurer par des évaluations, puis déléguer et renvoyer vers l'outil ce sur quoi humains et agents butent. Le brouillon l'organise en quatre phases.
- Un court texte en français sur l'IA et la production intellectuelle, qui soutient que les agents font disparaître la valeur marchande de la production intellectuelle mais pas sa valeur intrinsèque, et que la reconnaissance et les décisions collectives deviennent les questions ouvertes.

## Tech

Le dépôt est un espace d'écriture plutôt qu'un logiciel. Alexandre y travaille avec des agents Claude, selon quelques règles écrites :

- **Les fiches de concepts sont figées.** Chacune porte une ligne de statut avec une version et une date. Les modifications sont proposées dans la conversation et appliquées seulement après l'accord d'Alexandre.
- **Les concepts restent généraux.** Le dossier du cours les applique à l'école et y renvoie, sans jamais les redéfinir.
- **Une langue par public.** L'anglais par défaut, le français pour les documents destinés à l'école.
- **Tout dossier de plusieurs fichiers a un README qui les recense,** mis à jour à chaque ajout.

Chaque fiche de concept suit la même forme : une définition en une ligne, une dérivation numérotée à partir de ce qui vaut pour tous les cas, un tableau des cas limites, les conséquences, et des sources en philosophie, en psychologie et en recherche sur l'automatisation. Les documents du cours portent leur propre ligne de statut et sont illustrés par des figures SVG. Les figures de l'essai et des articles (un schéma de la répartition du temps humain, le choix entre deux cartes, trois versions de la vue de convergence, une carte des tâches) sont tracées par des scripts Python qui produisent du SVG, du PNG et du HTML dans le langage visuel du site de Matrice. Les versions de référence des essais sont des Claude Docs, avec des copies locales en Markdown dans le dépôt. Les présentations de la première séance de travail ont été construites sous forme de diapositives HTML. Les affirmations de « Tools before agents » viennent de notes de travail tirées du dépôt de chaque projet le 3 novembre 2026, avec la liste des lacunes.

## Status

Le travail s'est étalé du 9 octobre au 5 novembre 2026, puis a été rassemblé dans le dépôt en un seul commit le 5 novembre. Les quatre fiches de concepts ont été figées entre le 11 et le 15 octobre ; « juger » et « répondre de » restent à écrire. La conception du cours est un ensemble d'hypothèses de travail : le périmètre a été arrêté sur le principe lors de la première séance de travail, le 16 octobre, et aucun cours n'a encore été donné. L'intervention est prévue en novembre 2026 ; le dépôt ne donne pas de date précise et n'indique pas qu'elle a eu lieu. Côté écriture, l'essai sur la planification est terminé, « Work 2.0 » est publié, les articles 2 à 4 de la série sont à l'état de plan, et « Tools before agents » est un premier brouillon daté du 3 novembre. Dépôt privé.
