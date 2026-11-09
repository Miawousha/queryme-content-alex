---
name: Sunrent
description: "Un modèle de solaire en location pour les ménages français : production horaire PVGIS, modèle énergétique du logement, moteur de dispatch et de finance, et Monte Carlo sur l'offre."
year: 2026
tags: &a1
  - energy
  - solar
  - simulation
  - finance
  - nextjs
  - typescript
repos:
  - name: sunrent
    role: author
    visibility: private
    description: Plateforme de solaire en location pour les ménages français, du
      toit et des factures jusqu'à l'offre de l'opérateur et au conseil au ménage.
    year: 2026
    last_active: 2026-09
    language: TypeScript
    archived: false
    tags: *a1
---

Sunrent est un modèle de solaire en location (solar-as-a-service) pour les ménages français, construit chez Matrice Technologies en septembre 2026. Dans ce modèle, Sunrent installe et reste propriétaire des panneaux, de la batterie et de l'onduleur, le client ne paie rien à l'installation, et sa facture totale (réseau plus redevance Sunrent) est garantie inférieure d'un pourcentage fixé à ce qu'elle aurait été sans solaire. Le dépôt est la plateforme qui dimensionne et chiffre cette offre pour un bâtiment donné, et conseille le ménage sur tout ce qu'il pourrait changer d'autre.

## What

Chaque projet est un bâtiment, et chaque bâtiment passe par six onglets. **Bâtiment** place le site sur une carte satellite, définit les zones où poser des panneaux (préremplies par l'API Solar de Google quand elle connaît le toit) et décrit la maison usage par usage : enveloppe, chauffage, eau chaude, cuisson, climatisation, véhicules, piscine, avec un préremplissage depuis le DPE quand le registre en contient un. **Consommation** accepte une facture, un export du compteur ou un seul chiffre, et répartit la demande horaire par usage et par énergie, calée sur les factures et comparée à des ménages semblables. **Solutions** est le conseiller du ménage : un catalogue de mesures, chacune évaluée sur sa durée de vie face au fait de ne rien faire, avec coût posé, aides selon la tranche de revenus et la zone climatique, carbone gris et entretien, une frontière de Pareto coût-carbone et un parcours recommandé (sobriété, efficacité, eau chaude, chauffage, puis panneaux dimensionnés sur ce qui reste, flexibilité, tarif, et une batterie seulement si elle se rembourse). **Simulation** fait tourner une année horaire PVGIS par zone face à la demande du bâtiment, pour chaque taille d'installation, puis compare les options d'eau chaude, de chauffage, de déplacement des usages et de tarif. **Coûts** et **Optimisation**, signalés comme la vue de l'installateur, couvrent la nomenclature et toutes les combinaisons de garantie, de taille et de batterie, classées par valeur actuelle nette au-dessus du TRI minimal de l'opérateur, puis une simulation de Monte Carlo avec diagramme en tornade.

## Tech

Une application Next.js 16, React 19 et TypeScript sur Supabase, avec Zod et Vitest. Le moteur se trouve dans `core/` (demande, thermique, énergie, flexibilité, dimensionnement, finance, Monte Carlo, mesures, impact) et expose un point d'entrée réservé aux composants côté client (libellés et types seulement), afin que les données des pays restent hors du bundle du navigateur. Le chauffage est un bilan thermique horaire, avec déperditions de l'enveloppe par composant, apports internes et solaires, inertie thermique, programmes de réduit et pompes à chaleur dont le rendement suit la température extérieure. Les données de marché (tarifs, jours fériés, facteurs d'émission dont un facteur carbone horaire du réseau pour 2024, aides, références de consommation, formats de compteur, géocodeur, registre des diagnostics) sont regroupées en paquets par pays, la France en premier ; des règles ESLint et un test refusent tout code propre à un pays en dehors de ces paquets. Un test de référence sur une maison lyonnaise et une année PVGIS enregistrée fige les chiffres. Les formats de compteur connus sont lus par un analyseur déterministe, les autres par un agent d'extraction Gemini. Le déploiement vise Coolify, avec Supabase sur le même serveur.

## Status

Construit du 24 au 27 septembre 2026 en trois itérations, chacune selon un contrat écrit et assemblée à partir de tranches développées en parallèle ; dépôt privé. Reste ouvert : le dimensionnement du moteur optimise la VAN de l'opérateur, et le parcours du ménage s'affiche à côté sans la remplacer. La prochaine étape prévue est un rapport que le client peut lire et contester, avec hypothèses, sources et sensibilités en langage clair.
