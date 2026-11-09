---
name: Queritae
description: "Une plateforme multi-comptes de CV interrogeables : la base de connaissances de chaque compte vit dans son propre dépôt GitHub et répond, avec citations, aux questions des recruteurs et des agents IA, via chat web et MCP."
year: 2026
stack:
  - TypeScript
  - Next.js
  - Vercel AI SDK
tags:
  - ai
  - open-source
  - personal
url: https://github.com/Miawousha/queryme
repos:
  - name: queryme
    url: https://github.com/Miawousha/queryme
    role: author
    visibility: public
    description: Application multi-comptes de CV interrogeables qui synchronise le
      dépôt de contenu de chaque compte et répond aux questions à partir de
      celui-ci, avec citations, via chat web et MCP.
    year: 2026
    last_active: 2026-11
    language: TypeScript
    archived: false
    tags:
      - ai
      - agent
      - mcp
      - typescript
      - nextjs
---

## Résumé
Un CV interrogeable. La base de connaissances d'une personne (faits structurés en YAML et récits en Markdown) et le prompt système de l'agent se trouvent dans un dépôt de contenu public sur GitHub ; l'application synchronise ce dépôt et répond aux questions des recruteurs et des agents IA via un chat web et un serveur MCP, avec des citations qui renvoient aux fichiers sources. La base de connaissances, le prompt système et le code sont tous open source. Depuis juin 2026, l'application est multi-comptes : elle ne contient aucun contenu propre et sert autant de comptes que nécessaire, chacun adossé à son propre dépôt de contenu.

## Pourquoi
Deux raisons. D'abord, les processus de recrutement passent de plus en plus par des agents IA ; un CV statique se prête mal à cette interface. Ensuite, la transparence sur ce qu'un agent « sait » de vous est un problème de confiance qui mérite d'être traité dès le départ.

## What
Chaque compte est servi sous `/{username}`, avec un compte principal à la racine du domaine. L'inscription se fait par GitHub OAuth : la première connexion crée un compte au nom de l'identifiant GitHub. Les inscriptions libres passaient d'abord par une liste d'attente validée par un super-administrateur ; depuis le 22 juin 2026, les nouveaux comptes sont actifs immédiatement, et les statuts « en attente » et « désactivé » restent disponibles comme leviers d'administration dans la console multi-comptes `/admin`. Chaque propriétaire gère son compte sous `/{username}/admin` et accepte les conditions d'utilisation lors de sa première connexion.

Une GitHub App relie un dépôt de contenu en une seule installation, après quoi chaque push le resynchronise automatiquement ; l'ancien webhook manuel par compte a été supprimé. Un compte sans contenu est guidé pas à pas : l'administration génère, pour l'agent de développement du propriétaire, un prompt qui contient un jeton de configuration à portée limitée (signé par HMAC, valable une heure), afin que l'agent puisse enregistrer le dépôt de contenu qu'il a construit sans session de navigateur. Un dépôt de contenu peut aussi déclarer ses propres collections (notes, glossaire, écrits, etc.) dans un fichier `content.config.yaml` ; sans ce fichier, un préréglage « CV » s'applique et le prompt assemblé reste identique.

Autres ajouts sur la même période : la plateforme injecte sa propre consigne de citation dans le prompt système, si bien que les réponses sourcées ne dépendent plus du prompt de chaque propriétaire ; le panneau de la base de connaissances affiche un plan où les sections citées sont signalées, avec un aperçu au survol ; chaque compte dispose d'un CV imprimable avec photo facultative et QR code ; l'utilisation est mesurée par compte, avec des quotas journaliers et mensuels et des alertes de dépenses par e-mail ; la facturation Stripe définit une offre gratuite et une offre pro (qui ajoute les domaines personnalisés). En novembre 2026, l'interface a été revue pour suivre le langage visuel de la v2 du site de Matrice.

## Tech
Next.js avec le Vercel AI SDK et la mise en cache des prompts d'Anthropic, Postgres (Neon) et Upstash Redis pour la persistance, Resend pour les e-mails, Stripe pour la facturation, et une suite d'évaluations sur des questions de référence exécutée contre le modèle réel. Le point d'accès MCP ne sert pour l'instant que le compte principal.

## Status
L'essentiel du travail a eu lieu en mai et juin 2026, suivi de la refonte visuelle de novembre 2026. La feuille de route prévoit encore, avant un lancement public, des garde-fous contre l'usurpation d'identité pour les noms d'utilisateur et les domaines personnalisés, puis du travail d'accueil des nouveaux utilisateurs, comme un dépôt de contenu modèle et un import de CV.
