---
name: Gister
description: "Une mémoire locale des réunions en présentiel : enregistre la salle, transcrit et sépare les locuteurs avec Gemini, et doit tenir un plan à jour et un journal des décisions."
year: 2026
tags: &a1
  - rust
  - audio
  - tauri
  - gemini
  - local-first
  - sqlite
repos:
  - name: gister
    role: author
    visibility: private
    description: Enregistreur local de réunions en présentiel, avec un cœur audio
      en Rust et une transcription Gemini.
    year: 2026
    last_active: 2026-08
    language: Rust
    archived: false
    tags: *a1
---

Gister est une mémoire des réunions physiques, en présentiel, commencée chez Matrice Technologies en août 2026. Il enregistre la salle avec le micro d'un ordinateur portable, transcrit et sépare les locuteurs avec Gemini, et doit tenir un plan à jour et un journal des décisions accompagnées de leur justification, pour pouvoir demander des semaines plus tard quel est le plan, pourquoi une décision a été prise et ce qu'elle a remplacé. Il est local-first : la machine de l'utilisateur, sa propre clé d'API Gemini, ni compte ni serveur.

## What

La conception repose sur une question ouverte : Gemini sait-il distinguer les locuteurs à partir d'un seul micro de portable, sans modèle local d'empreintes vocales ? Le banc d'évaluation qui y répond a donc été construit avant l'interface. Il rejoue des enregistrements annotés à la main dans le découpeur de production et mesure le taux d'erreur sur les locuteurs et le taux d'erreur sur les mots ; ses seuils décident de l'architecture : sous 15 %, la conception tient ; entre 15 et 30 %, nommer les locuteurs devient obligatoire ; au-delà de 30 %, les empreintes vocales locales entrent dans la première version.

Ce qui fonctionne aujourd'hui est une petite pastille d'enregistrement, toujours au premier plan. L'audio est capté, rééchantillonné en 16 kHz mono, découpé sur les silences plutôt qu'à intervalles fixes, et écrit au fil de l'eau en Ogg/Opus. Chaque segment est mis en file sur disque, envoyé à Gemini en arrière-plan puis enregistré dans une base SQLite locale avec recherche plein texte. Un enregistrement survit à un plantage ou à la fermeture de l'application : la file reprend au lancement suivant. L'extraction des décisions, le nommage des locuteurs, les questions sur les réunions passées et la lecture des transcriptions dans l'application ne sont pas encore construits.

## Tech

Un workspace Rust de cinq crates : `audio` (capture cpal, rééchantillonnage, détection d'activité vocale Silero, découpeur attentif aux silences avec une cible de 20 s et un plafond de 35 s, écriture Opus synchronisée sur disque environ une fois par seconde, aucun code réseau), `transcribe` (le client Gemini, qui classe les échecs en réessayables, mal formés ou définitifs, avec une tentative de réparation sur une réponse mal formée), `store` (schéma SQLite et migrations, index FTS5, file de segments durable, déduplication des chevauchements et reprise au démarrage), `app` (le shell Tauri v2, la session d'enregistrement et l'envoi en arrière-plan) et `eval` (le calcul du score de séparation des locuteurs et sa CLI de validation). L'interface de la pastille est une page Next.js et React dans la webview Tauri ; l'horloge et le vu-mètre viennent de Rust, si bien que recharger la fenêtre ne fait pas perdre un enregistrement. La clé d'API est lue dans le trousseau du système, puis dans l'environnement. Le README indique 171 tests Rust réussis et 11 ignorés (périphérique ou réseau), clippy et rustfmt sans avertissement, et une suite de tests séparée pour l'interface.

## Status

Construit du 17 au 19 août 2026, dépôt privé, stade précoce. La pastille enregistre et transcrit en arrière-plan, mais le banc d'évaluation n'a pas encore tourné sur de vraies réunions, et les transcriptions ne se lisent qu'avec `sqlite3` dans la base.
