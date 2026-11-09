---
name: Apparent (Matrice Sail)
description: "Un jeu de voile jouable en réalité virtuelle dans le navigateur : une simulation physique déterministe en Rust compilée en wasm, avec un rendu Three.js et WebXR et des régates en équipage."
year: 2026
url: https://apparent.matricetechnologies.com
tags: &a1
  - rust
  - wasm
  - threejs
  - webxr
  - simulation
  - game
repos:
  - name: matrice-sail
    role: author
    visibility: private
    description: "Apparent : jeu de voile jouable en réalité virtuelle ; simulation
      Rust, wasm, Three.js et WebXR, avec un serveur d'équipage WebSocket."
    year: 2026
    last_active: 2026-11
    language: Rust
    archived: false
    tags: *a1
---

Apparent est un jeu de voile qui tourne dans le navigateur et dans les casques de réalité virtuelle comme le Quest. La physique est une simulation Rust indépendante de tout moteur de jeu, et l'application web n'est qu'une fine couche de rendu Three.js et WebXR par-dessus. Les bateaux sont un dériveur ILCA, l'AP75 (un monocoque volant AC75 conforme à la jauge AC75 V3.01) manœuvré poste par poste par un équipage, et le J-Class Ranger ; une planche à voile existe dans la simulation seulement. Le décor par défaut est la baie de San Francisco, avec son relief, son vent et sa marée modélisés. Plusieurs personnes peuvent naviguer ensemble sur un même bateau grâce à un serveur d'équipage, en réseau local ou sur play.apparent.matricetechnologies.com. Alexandre a écrit environ 250 commits la première semaine, en novembre 2026.

## What

La simulation vise à paraître juste à des régatiers et des pratiquants du foil expérimentés, pas seulement vraisemblable : le comportement découle d'une physique confrontée à des données de référence et à des scénarios assortis de tolérances, et non de réglages au cas par cas. Sur l'AP75, chaque poste d'équipage (deux barreurs, régleur de vol, régleur de voile, P5) peut être tenu par une personne en réalité virtuelle ou dans un navigateur, ou laissé à un équipier simulé. En régate, un parcours est mouillé face au vent, avec procédure de départ, portes, limites de zone et pénalités selon les règles de course de l'America's Cup, contre un adversaire piloté par l'IA ou un autre équipage, avec l'affichage du tacticien, le chronomètre de course et les résultats. Le son est procédural, y compris le vent aux oreilles du marin.

## Tech

Un espace de travail Rust en quatre crates : `sail-sim`, la simulation pure sans dépendance (vent, vagues de Gerstner, coque, foils, voiles, équipages, régates), cadencée à 120 Hz fixes en `f64` et donc déterministe ; `sail-wasm`, une enveloppe wasm-bindgen qui partage l'état via des tampons en mémoire wasm ; `sail-lab`, des outils sans interface pour les polaires, la stabilité, les scénarios de ressenti, les conceptions d'AC75, les régates et la relecture de journaux ; et `sail-server`, le serveur d'équipage, qui fait tourner un bateau en temps réel et en remplit les postes via WebSocket. L'application web utilise Vite, TypeScript et Three.js avec WebXR ; le décor intégré de la baie (relief, ville, fonds marins) est stocké dans Git LFS, et les tuiles 3D de Google sont une option. Les conceptions d'AC75 sont des fichiers TOML. Le serveur d'équipage est déployé avec Docker Compose et Caddy sur un VPS, et la page d'accueil est une page statique publiée depuis le même dépôt.

## Status

Commencé début novembre 2026, en développement actif. Une feuille de route de la simulation suit le travail phase par phase (cœur multicorps, surfaces portantes, champs de vent et de mer, le marin comme corps physique, nouveaux engins, monde, prédiction de nouvelles conceptions, banc d'essai, entraînement d'équipage). Le plan de match racing a atteint son cinquième jalon en novembre 2026 : un ami à bord de son bateau via Internet grâce au serveur d'équipage déployé, puis un ami à bord du bateau adverse. Dépôt privé.
