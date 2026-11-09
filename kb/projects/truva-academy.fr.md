---
name: Truva Academy
description: "Plateforme de formation à base d'agents pour les équipes de Truva : jeux de rôle oraux où Claude incarne le client, débriefings notés, exercices et dimension ludique, en ligne sur academy.truva.matricetechnologies.com."
year: 2026
url: https://academy.truva.matricetechnologies.com
tags: &a1
  - ai-agents
  - claude
  - edtech
  - voice
  - nextjs
  - supabase
  - typescript
repos:
  - name: truva-academy
    role: author
    visibility: private
    description: Une application Next.js unique où des sessions Claude sans interface
      jouent le client, une session distincte note la transcription, et un
      historique de l'apprenant en ajout seul alimente le jeu.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags: *a1
---

Truva Academy est la plateforme de formation que Matrice a construite pour Truva, la plateforme de revente de logements de Mumbai, dans le cadre de la mission de transformation IA décrite dans la fiche Transformation IA de Truva. L'apprenant l'ouvre dans son navigateur, se connecte avec son compte Google Truva ou un lien magique, et suit le parcours de son métier : leçons, quiz, exercices et jeux de rôle oraux où Claude incarne un vendeur ou un acheteur, suivis d'un débriefing rédigé par une seconde session Claude qui note la transcription selon la grille d'évaluation du module. Points d'expérience, séries, niveaux, badges et classements sont calculés à partir d'un historique, en ajout seul, de chaque tentative. C'est le plus gros chantier de la mission : environ 2 400 commits entre le 8 août et le 12 octobre 2026, en ligne sur [academy.truva.matricetechnologies.com](https://academy.truva.matricetechnologies.com).

## What

Le point de départ était l'entraîneur aux acquisitions de Truva, une skill Claude utilisée pour s'exercer par jeux de rôle ; l'Academy en a fait une application, partant du constat que ce dont la formation a besoin (une notation qui a toujours lieu, des consignes cachées du personnage qui restent cachées, un historique qui survit à un plantage, une progression fondée sur des preuves) relève de garanties que le code peut tenir et que la prose ne peut pas tenir.

- **Jeux de rôle.** Un jeu de rôle est une conversation vocale en direct : mains libres, interruptible, le personnage répondant à voix haute avec une voix qui lui correspond. La session qui joue le rôle tient l'interlocuteur jusqu'au bout et ne se note jamais elle-même ; la session de notation lit la transcription à froid, avec la grille et une clé de notation de ce qu'il y avait à découvrir mais sans les consignes du personnage, et rend des notes par critère en trois catégories (points obligatoires, éliminatoires, et signalements qui ne décident jamais du verdict). Une séance où l'apprenant n'a jamais parlé n'est ni notée ni enregistrée. Les résultats s'affichent comme Parfait, Très bien, Bien ou À retravailler.
- **Le formateur dans la salle.** L'apprenant choisit le niveau d'aide, d'une répétition étape par étape à un coach qui intervient quand l'entretien tourne mal, jusqu'au mode solo. Le coach est une seconde voix en direct qui peut jouer le client pendant la répétition, ouvrir un échange en cours d'entretien puis rendre la main à l'apprenant sans que le client perde le fil. Les personnages que le formateur invente à la volée reçoivent un nom, un visage de remplacement et une voix constante.
- **Autres activités.** Leçons, quiz et exercices structurés, chacun avec son propre lecteur ; les réponses fermées sont notées par le code et les réponses qui demandent du jugement par une session de notation. L'apprenant peut lire les passages en hindi dans l'écriture de son choix.
- **Le jeu.** Points d'expérience, séries, niveaux, badges, une progression à travers modules et cours, historiques partagés, classements et défis, et un avatar habillé grâce à une garde-robe achetée avec ce que rapporte l'entraînement. Tout cela est calculé à partir de l'historique et jamais stocké.
- **Rédaction.** Cours, modules, personnages, grilles et bibliothèque de connaissances sont des documents Markdown dans le stockage propre de la plateforme, lus à l'exécution. Les auteurs les modifient par une API, une CLI utilisable depuis Claude Code ou des éditeurs dans la console d'administration, sans commit ni déploiement ; chaque modification est validée, conservée et réversible. Un auteur peut lancer un « drive », une séance menée par un apprenant fictif géré par la plateforme, et confier à son propre agent la lecture de la séance et la correction à proposer. Chaque activité indique son auteur principal, et une page Auteurs les recense.

## Tech

Un dépôt TypeScript contenant une seule application Next.js 16 (App Router, route handlers pour l'API, React 19, Tailwind 4, shadcn sur Base UI), avec l'orchestrateur sous `web/server/`. Chaque fichier serveur importe `server-only`, si bien qu'un composant client qui atteint l'orchestrateur fait échouer `next build` ; un test vérifie la présence de ce marqueur dans toute l'arborescence et un script `npm run boundary` prouve que la compilation échoue bien.

- **Sessions.** Chaque séance compose un espace de travail (la fiche de rôle comme instructions de l'agent, les fichiers du module à côté) et ouvre une session par un point d'entrée unique, sur l'API Anthropic ou sur Gemini de Google selon le modèle choisi dans le catalogue. Les sessions qui jouent un rôle n'ont aucun outil et la session de notation est en lecture seule ; les capacités sont fixées par les arguments de lancement, jamais par les instructions. Chaque événement est ajouté à une transcription JSONL dès son arrivée, si bien qu'un processus interrompu laisse un début de transcription complet.
- **Voix.** L'Academy maîtrise sa boucle vocale : ElevenLabs transcrit un énoncé et prononce une phrase à la fois, tandis que la conversation elle-même reste dans la session Claude de l'Academy. Une version antérieure fondée sur un agent vocal hébergé a été retirée en août 2026.
- **Activités.** Un type d'activité est du code qui respecte un contrat unique (composer, exécuter, noter, enregistrer), chaque étape étant déclenchée par la fin de la précédente. La sortie de la notation est validée par un schéma ; une note mal formée relance la demande une fois, puis la séance échoue de façon visible.
- **État.** Trois sortes : le contenu, les espaces de travail par séance (jetables) et l'historique de l'apprenant (en ajout seul, dans Supabase Postgres, qui gère aussi l'authentification). Les séances en cours sont tenues dans un registre en mémoire rattaché à `globalThis`, ce qui fait du déploiement une instance unique par conception.
- **Livraison.** Déployé sur Coolify avec Nixpacks. Vitest (329 fichiers de test) et des tests dans le navigateur, `tsc` et `next build` conditionnent chaque fusion. Le travail suit une méthode sdlc intégrée au dépôt : un document d'état cible où chaque clause non réalisée renvoie à un ordre de travail numéroté du backlog, le tout vérifié par un script.

## Status

Hébergé sur academy.truva.matricetechnologies.com depuis août 2026. Les versions R1 à R3 et R5 sont sorties entre le 9 et le 11 août (jeu de rôle écrit avec débriefing noté, puis quiz, exercices et un second parcours de formation, puis jeu de rôle oral, puis un système de composants unique aux couleurs de Truva). R6 et R7 (le formateur dans la salle comme seconde voix, sur une boucle vocale entièrement maîtrisée) sont sorties les 14 et 15 août, et R4 (le passage à une application Next.js hébergée unique, avec historiques partagés, classements et défis) le 5 septembre. En septembre et début octobre, le travail a porté sur la rédaction des contenus dans la plateforme, les séances d'apprenants fictifs, les voix des personnages et la présentation des notes ; le dernier commit date du 12 octobre 2026. Dépôt privé.
