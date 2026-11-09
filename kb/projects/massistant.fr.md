---
name: Massistant
description: "Un pont entre WhatsApp et Claude Code sur un Mac : lancer et piloter des sessions par message, message vocal ou appel, avec un assistant personnel doté de mémoire et une application de barre des menus autour."
year: 2026
tags: &a1
  - agents
  - claude-code
  - rust
  - whatsapp
  - voice
  - macos
  - swift
repos:
  - name: matrice-assistant
    role: author
    visibility: private
    description: matrice-bridge, un unique binaire Rust qui pilote des sessions
      Claude Code sur un Mac depuis WhatsApp, appels vocaux compris, intégré à
      l'application de barre des menus Massistant.
    year: 2026
    last_active: 2026-11
    language: Rust
    archived: false
    tags: *a1
---

Massistant permet à Alexandre de piloter Claude Code sur son Mac depuis son téléphone. Un numéro WhatsApp dédié, associé comme appareil lié, reçoit ses messages, et `matrice-bridge`, un unique binaire Rust, les transforme en véritables sessions de la CLI `claude`, qui tournent sous son abonnement claude.ai plutôt qu'avec une clé d'API. Les demandes d'autorisation reviennent sur WhatsApp et s'y règlent. Le pont est livré dans Massistant, une application macOS native qui vit dans la barre des menus et dispose de sa propre fenêtre.

## What

Depuis WhatsApp, `/new api api fix the failing auth tests` lance une session nommée `api` dans un dossier de projet ; les messages suivants vont à la session courante, à une session nommée (`api: …`) ou à celle que désigne une réponse citée. `/ls`, `/peek`, `/stop`, `/fresh` et `/mv` permettent de lister, consulter, interrompre, redémarrer et renommer les sessions. Les messages vocaux sont transcrits puis traités comme du texte, les photos sont transmises avec leur légende, et les autorisations se règlent par `y`, par `n` suivi d'une raison, ou par `a` (toujours autoriser), uniquement par écrit.

En l'absence de session, les messages vont à un assistant permanent : une conversation Claude Code continue, dans son propre dossier, avec une mémoire des préférences et des engagements pris, une base de connaissances sur les personnes, les entreprises et les projets que le pont met à jour entre deux conversations, et un nom, une image, une voix et une personnalité configurables. Ses capacités sont listées et activées ou désactivées dans l'application.

Les appels forment l'autre canal. Appeler le numéro du pont, ou demander à Claude de rappeler une fois une tâche terminée, ouvre une conversation orale en français ou en anglais, avec transcription en direct et réponses prononcées phrase par phrase ; les tâches demandées pendant l'appel sont exécutées après avoir raccroché, puis un seul message résume l'appel. Les appels peuvent aussi passer par le modèle vocal GPT-Live d'OpenAI. L'assistant peut appeler ou écrire à une courte liste de contacts autorisés au nom d'Alexandre, via une session verrouillée qui ne peut que converser. Parmi les ajouts plus récents : l'enregistrement de réunions sur le Mac avec un compte rendu rédigé à partir de la transcription, une conversation vocale ouverte par raccourci clavier, des rappels, et un accès en lecture seule à son propre WhatsApp et à ses e-mails.

## Tech

Le pont est écrit en Rust sur tokio, avec la bibliothèque cliente `whatsapp-rust` pour l'appareil lié (et une version modifiée de `wacore` pour diagnostiquer les appels), `rusqlite`, `reqwest` et des WebSockets. Chaque tour Claude Code lance `claude -p` avec du stream-json en entrée et en sortie ; l'assistant et la session d'un appel gardent un processus `claude` permanent pour ne pas en relancer un à chaque tour. Un serveur MCP intégré au pont traite les autorisations via un socket Unix et donne à Claude des outils comme `call_me`, `call_contact` ou la modification de réglages. La parole passe par ElevenLabs ou OpenAI pour la transcription et la synthèse. L'application de barre des menus est en Swift. Un script de livraison compile l'application une seule fois dans un cache partagé ; un pont en cours d'exécution repère le nouveau binaire, attend qu'aucun tour ni aucune autorisation ne soit en cours, redémarre et le signale sur WhatsApp.

Les règles de sécurité sont explicites : seuls les numéros autorisés obtiennent une réponse, les sessions ne tournent que dans les dossiers de travail configurés, Claude fonctionne dans le mode d'autorisation choisi et les demandes restées sans réponse sont refusées au bout d'un délai, et toute action touchant d'autres personnes déclenchée par les propos d'un contact plutôt que par ceux d'Alexandre attend son accord. Le README recommande un numéro dédié, le client WhatsApp utilisé n'étant pas officiel.

## Status

Dépôt privé, créé le 16 octobre 2026, en service sur le Mac d'Alexandre. Il a été livré cinq fois rien que le 3 novembre 2026, date de la dernière livraison et de la dernière fusion enregistrées (pull request #16).
