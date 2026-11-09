---
name: Mission de conseil pour Maxwell Energy Systems (mxwl)
description: "La mission d'adoption de l'IA de Matrice pour Maxwell Energy Systems (mxwl), l'entreprise de gestion de batteries cofondée par Alexandre : une base de connaissances opérationnelle et des flux de travail à agents pour l'ingénierie embarquée, la validation et la conduite des programmes clients, cadrée dans un espace client partagé."
year: 2026
tags: &a1
  - consulting
  - ai-agents
  - battery
  - firmware
  - knowledge-base
  - docs
repos:
  - name: maxwell-consulting
    role: author
    visibility: private
    description: Dépôt de travail partagé de la mission, dont le contenu est publié en
      direct comme espace client de Maxwell sur le site de Matrice, avec la
      proposition de mission, ses documents d'appui et une présentation.
    year: 2026
    last_active: 2026-09
    language: HTML
    archived: false
    tags: *a1
---

En août 2026, Matrice Technologies, la société d'Alexandre, a préparé une mission d'adoption de l'IA pour Maxwell Energy Systems (mxwl), l'entreprise de systèmes de gestion de batteries qu'il a cofondée et dont il a été directeur technique jusqu'en mars 2025 (voir sa fiche d'expérience Maxwell). La mission a été cadrée dans un dépôt de travail partagé que Maxwell lit directement et qui est publié comme espace client sur le site de Matrice. La proposition s'appuie sur ce qu'Alexandre connaît déjà des plateformes et du code de Maxwell : il n'y a pas de phase d'audit distincte, et le premier mois sert à établir ce qui a changé depuis son départ et à choisir les plateformes et les programmes sur lesquels porte le travail. Le dépôt a été actif du 10 août au 1er septembre 2026 (67 commits) et couvre le cadrage et la conclusion de la mission, pas sa réalisation.

## What

L'objectif affiché de la mission est de réduire le coût et la durée de réalisation d'un programme client, de l'appel d'offres au démarrage de la production, en confiant à des agents le travail structuré, traçable et très documentaire d'un équipementier automobile soumis à réglementation, tout ce qu'ils produisent étant relu par une personne. Le second objectif est que les ingénieurs de Maxwell apprennent à diriger et à relire des agents sur leur propre travail, pour que la méthode continue de fonctionner après la fin de la mission.

Le plan comporte un fil conducteur et quatre chantiers :

- **Une base de connaissances opérationnelle** : une description structurée et lisible par machine des plateformes et des familles de variantes de Maxwell, de ses exigences, de ses processus, des responsabilités et des niveaux de qualité attendus, construite avec graybox (l'outil de modélisation d'organisations d'Alexandre), amorcée à partir de ce qu'Alexandre sait déjà et corrigée en séances de travail avec les responsables d'ingénierie. Elle vient en premier parce que c'est le contexte dont dépend chaque flux de travail à agents.
- **Une ingénierie embarquée qui intègre les agents** : des agents de programmation dans le travail réel de l'équipe embarquée, pour comprendre et documenter le logiciel embarqué existant, porter des variantes, migrer pilotes et plateformes, mener l'analyse statique et la mise en conformité MISRA, et relire le code, en commençant par les plateformes qui portent des programmes en cours.
- **Les livrables de validation et de sûreté** : génération et tri des cas de test, des scripts de test sur banc HIL (hardware-in-the-loop), de l'analyse des défaillances et de la traçabilité des exigences jusqu'aux tests, selon les exigences de preuve d'ISO 26262, d'AIS-156 et d'Automotive SPICE (ASPICE), chaque livrable touchant à la sûreté ou à une évaluation étant relu par une personne et cette relecture consignée.
- **La conduite des programmes clients** : analyse des cahiers des charges des clients, analyse des écarts par rapport au portefeuille de plateformes existant, dossiers de documentation et analyses d'écart de maturité ASPICE, menées sur une véritable opportunité commerciale.
- **Encadrer des agents** : une formation par métier, où chaque participant livre, sur ses propres tâches, un travail relu passé par un flux à agents.

À côté de ces chantiers figurent deux décisions qui relevaient de l'ancien périmètre d'Alexandre : une recommandation (conserver, reconstruire, abandonner ou acheter) sur les produits logiciels existants de Maxwell, et une architecture cible pour son logiciel de batteries connectées, conçue dès le départ pour les agents. L'avancement se juge sur des résultats vérifiables à l'œil (documents, flux de travail en service, travaux relus livrés par des ingénieurs nommément désignés) plutôt que sur des indicateurs de référence que Maxwell ne mesure pas, avec une revue mensuelle qui décide pour chaque chantier de le poursuivre, de le réorienter ou de l'arrêter.

Le dépôt contient une page qui explique le fonctionnement de l'espace, la proposition de mission dans ses cinq versions successives, ses documents d'appui, deux figures (les deux flux de travail à agents et le plan sur six mois) et une présentation de huit diapositives.

## Tech

Le dépôt est la source unique de la mission, pour les personnes comme pour les agents. Le site de Matrice lit son dossier `content/` sur `main` à chaque requête et l'affiche comme espace client : une fusion sur `main` est publiée en quelques secondes, et une pull request tient lieu de brouillon. Chaque fichier, nom de branche et message de commit est rédigé pour être lu par Maxwell ; les documents de travail internes de Matrice sont conservés dans un dépôt séparé, sans lien avec l'espace. `CLAUDE.md` et `AGENTS.md` renvoient tous deux au README, qui rassemble les règles de travail des personnes et des agents, et un `writing-style.md` fixe les règles de rédaction en anglais simple qui valent aussi bien pour les documents que pour les commits et les pull requests.

Un workflow GitHub Actions conditionne toute fusion sur `main` au validateur de l'espace (une copie à l'octet près de celui du dépôt du site de Matrice, qui fait référence) et vérifie que les figures sont à jour. Les figures sont conservées en SVG et intégrées au Markdown sous forme d'URI `data:` par un script, seule forme d'image qui s'affiche à la fois dans l'espace, dans son export PDF et dans la génération PDF locale. Un script Node sans dépendance imprime la proposition en PDF à la charte de Matrice via le Chrome local, et relit dans le PDF la page où tombe chaque section pour remplir une table des matières exacte. La présentation est générée à partir d'un fragment HTML par diapositive, vérifiés par rapport à un script rédigé dont les titres doivent correspondre à ceux des diapositives, avec les polices embarquées et sans aucune requête vers un tiers, puis publiée dans l'espace comme page autonome.

## Status

La proposition a été finalisée avec Maxwell fin août 2026. Le dépôt a été mis à jour pour la dernière fois le 1er septembre 2026 et ne contient aucun document de réalisation au-delà de la phase de cadrage. Privé.
