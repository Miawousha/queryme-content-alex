---
name: Eloom
description: "Un espace de travail agentique pour le cycle de vie des produits électroniques, où des agents IA conçoivent cartes et pièces et où le modèle du produit porte les exigences, les preuves et les livraisons."
year: 2026
url: https://eloom.matricetechnologies.com
tags: &a1
  - electronics
  - kicad
  - agents
  - claude-code
  - nextjs
  - typescript
  - supabase
repos:
  - name: eloom
    role: author
    visibility: private
    description: Espace de travail agentique pour le cycle de vie des produits
      électroniques ; application web, CLI et skill servis aux agents, worker
      KiCad hébergé.
    year: 2026
    last_active: 2026-10
    language: TypeScript
    archived: false
    tags: *a1
  - name: aloud
    role: author
    visibility: private
    description: "Exemple de référence d'Eloom : un badge vocal à pince dont le
      micro n'est alimenté que lorsque son voyant d'enregistrement est allumé."
    year: 2026
    last_active: 2026-10
    language: YAML
    archived: false
    tags:
      - electronics
      - product-design
      - safety
  - name: intercom
    role: author
    visibility: private
    description: Boîtier de bureau USB-C à un bouton et un anneau lumineux, qui
      signale qu'un agent attend une réponse et permet de lui répondre à la voix.
    year: 2026
    last_active: 2026-10
    language: C
    archived: false
    tags:
      - electronics
      - kicad
      - firmware
      - rp2040
      - agents
  - name: hestia
    role: author
    visibility: private
    description: Horloge murale e-ink sur batterie qui affiche où se trouve chaque
      membre de la famille plutôt que l'heure, avec son firmware et son service.
    year: 2026
    last_active: 2026-10
    language: C
    archived: false
    tags:
      - electronics
      - kicad
      - firmware
      - esp32
      - privacy
  - name: home-battery
    role: author
    visibility: private
    description: Modèle d'exemple d'une batterie domestique LFP de 10 kWh avec
      onduleur hybride de 5 kW, découpé en modules par sous-système.
    year: 2026
    last_active: 2026-10
    language: C
    archived: false
    tags:
      - electronics
      - product-model
      - energy
  - name: trail-light
    role: author
    visibility: private
    description: Modèle d'exemple d'un feu arrière de vélo qui s'intensifie quand le
      vélo ralentit.
    year: 2026
    last_active: 2026-10
    language: YAML
    archived: false
    tags:
      - electronics
      - product-model
  - name: pocket-blinker
    role: author
    visibility: private
    description: Carte clignotante à LED sur pile bouton, conçue et livrée par un
      agent vierge qui ne disposait que de la CLI Eloom et de son skill.
    year: 2026
    last_active: 2026-09
    language: KiCad
    archived: true
    tags:
      - electronics
      - kicad
      - agents
  - name: usb-power-indicator
    role: author
    visibility: private
    description: Carte témoin d'alimentation USB conçue par un agent via la CLI
      Eloom, vérifiée avec KiCad et livrée via Eloom.
    year: 2026
    last_active: 2026-09
    language: KiCad
    archived: true
    tags:
      - electronics
      - kicad
      - agents
---

Eloom est l'espace de travail de Matrice pour le cycle de vie des produits électroniques, fondé sur le pari que des agents IA feront l'essentiel du travail entre un besoin exprimé et un produit prêt pour la production. Son idée centrale : l'état partagé, c'est le modèle du produit, et non la mémoire de tel ou tel agent. Besoins, exigences, conception, justifications et preuves vivent sous forme de texte structuré dans le dépôt git du produit, sont vérifiés à chaque modification comme du code, et constituent ce que chaque agent lit pour commencer et modifie pour terminer. Les personnes (le donneur d'ordre pour qui le produit est fait, les ingénieurs, les clients, les autorités) interviennent aux frontières et approuvent ce que la méthode exige. Alexandre a écrit environ 1 400 commits entre fin septembre et mi-octobre 2026 ; une instance publique tourne sur eloom.matricetechnologies.com.

## What

Un utilisateur connecté crée un produit à partir d'un cahier des charges (une description et des exigences), et son propre agent (Claude Code ou Codex) fait le travail d'ingénierie avec la CLI `eloom` et son skill : il récupère le produit dans un répertoire local, cherche des composants réels dans les bibliothèques KiCad, lit et écrit schémas et routages en s'appuyant sur les empreintes SHA-256 observées, lance l'ERC et le DRC, exporte la nomenclature, joint les vérifications comme preuves et demande une livraison. Eloom tient le registre et la barrière de livraison. Chaque preuve est liée à l'empreinte du fichier qu'elle a examiné ; toute modification la rend périmée, et la livraison est refusée, avec un motif par fichier, tant qu'un schéma ou une carte n'est pas vérifié, est périmé ou en échec.

Au-delà de la carte, un produit se compose de pièces (boîtier, composants achetés, emballage, notice), chacune réalisée par un agent dans une modification à part et dessinée par Eloom à partir de ses fichiers : une vérification d'assemblage contrôle les interférences et les jeux entre pièces placées, et l'emballage comme le boîtier sont générés à partir d'une spécification. L'interface web présente pour chaque produit son modèle, ses fichiers, ses preuves, sa nomenclature, son dossier de fabrication, ses livraisons et son partage, avec un explorateur du modèle (canevas, plan, inspecteur, historique). Une méthode écrite, le compendium, décrit la boucle appliquée à chaque niveau (besoin, conception, risque, preuve, référence figée) et est servie aux personnes comme aux agents. Les stations permettent de lancer des sessions Claude Code sur sa propre machine et de les suivre ou de les orienter depuis l'application. Une route `/demo` déroule un scénario fictif sans connexion.

## Tech

Next.js 16 (App Router), React 19 et TypeScript, Tailwind 4 avec shadcn et Base UI, Supabase pour l'authentification et les espaces de travail, PostgreSQL pour les produits, preuves, revues et tâches. Le modèle produit est un format YAML (`product.yaml`) doté d'un JSON Schema, d'un vérificateur, d'empreintes de contenu et de vues générées, écrit en modules ES simples qui tournent à l'identique dans Node et dans le navigateur. La CLI des agents est construite avec le paquet `served-tool` de Matrice et distribuée par l'application avec son skill, une connexion par appareil et des clés d'API révocables. Un worker hébergé, avec KiCad, ngspice, Chromium et OpenCascade, s'exécute à chaque push : vérifications de règles, modèles 3D, nomenclature, dossier de fabrication, simulations, documents imprimables et conversion STEP. Les vues 3D utilisent three.js, les graphes React Flow et ELK, et les PDF du registre PDFKit. Une suite d'évaluations mesure la capacité d'un agent vierge à mener de vraies tâches de conception avec ces outils, chaque essai étant noté par un vérificateur déterministe. Déployé avec Docker Compose sur Coolify.

## Status

Version 0.2.0, dernier commit en octobre 2026. Le parcours de livraison vérifiée s'appuie sur de vraies vérifications KiCad ; le scénario `/demo` reste fictif et séparé des vrais produits. Dépôt privé.

## aloud

Aloud est l'exemple de référence d'Eloom : un badge à pince qui enregistre des notes vocales quand on appuie sur son bouton et les synchronise avec une page web compagnon (Web Bluetooth) pour transcription. Sa promesse : le micro ne peut pas être alimenté si le voyant d'enregistrement est éteint. Le dépôt contient le cahier des charges, l'entretien avec le porteur du produit, le modèle et une analyse de défaillances commencée à l'étape des exigences. Conçu de bout en bout avec la méthode d'Eloom, de septembre à octobre 2026.

## intercom

Intercom est un boîtier de bureau USB-C à un bouton et un anneau lumineux, accompagné d'une application de bureau et d'une commande `intercom` que les agents appellent pour poser une question, rendre compte ou clore un fil. Le boîtier s'allume quand un agent attend ; maintenir le bouton enregistre la réponse parlée, et le micro n'est alimenté que par le circuit du bouton. Le dépôt contient la carte KiCad avec ses simulations, un firmware RP2040 (pico-sdk et TinyUSB : un périphérique audio USB, plus un bouton HID et l'anneau de LED, avec une porte testée sur l'hôte qui ne laisse passer l'audio que pendant l'appui), un boîtier validé par la vérification d'assemblage d'Eloom, et la commande d'une première série de cinq cartes prototypes assemblées. Actif en octobre 2026.

## hestia

Hestia est une horloge murale e-ink sur batterie qui affiche où se trouve chaque membre de la famille (Maison, Travail, École, En route) plutôt que l'heure, d'après la spécification d'un porteur de produit extérieur. Le téléphone calcule la zone localement et n'envoie que son nom ; le service ne garde aucun historique, seulement l'état courant de chaque membre. Le dépôt contient la conception KiCad, le firmware ESP32 de l'horloge, les pièces batterie, écran, boîtier, emballage et notice, et un service Node 24 sur PostgreSQL hébergé dans l'UE. Conçue dans Eloom en octobre 2026.

## home-battery

Un modèle d'exemple d'une batterie domestique murale LFP de 10 kWh avec un onduleur hybride monophasé de 5 kW, découpé en modules par sous-système (pack, BMS, onduleur, contrôleur, boîtier), avec des objectifs de sécurité et un firmware de BMS rattaché à son arborescence de sources. Les valeurs sont illustratives. Il est issu d'un jeu de test du vérificateur de modèle d'Eloom.

## trail-light

Un modèle d'exemple en un seul fichier : un feu arrière de vélo qui s'intensifie quand le vélo ralentit, au stade de ses premiers prototypes. Lui aussi issu d'un jeu de test du vérificateur.

## pocket-blinker

Une carte clignotante à LED autour d'un LMC555 sur pile bouton, conçue à partir d'un cahier des charges par un agent vierge qui ne disposait que de la CLI `eloom` servie et de son skill, sans dépôt ni exemple à copier. Elle a passé l'ERC et le DRC avec les réglages par défaut de KiCad 10 et a été livrée via Eloom. Archivé.

## usb-power-indicator

La première carte conçue ainsi : un connecteur USB Micro-B, une résistance de 680 ohms et une LED verte sur une carte double face de 24 x 16 mm, que l'agent a itérée jusqu'à zéro violation ERC et DRC avant de la livrer. Un script rejoue toute la boucle contre une instance en service. Archivé.
