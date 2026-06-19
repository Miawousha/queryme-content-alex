---
name: Altergo Battery Intelligence Platform
year: 2022
tags:
  - battery
  - energy
repos:
  - name: aging_battery_lifetime_simulator
    url: https://github.com/ION-Altergo/aging_battery_lifetime_simulator
    role: contributor
    visibility: private
    description: Simulateur de cycle de vie qui vieillit une Battery `lair` sous
      profils de puissance et d'ambiance, encadré par une machine à états de
      sécurité.
    year: 2025
    last_active: 2025-06
    language: Python
    archived: false
    tags:
      - battery
      - energy
      - python
      - simulation
  - name: altergo_platform_etl_benchmark
    url: https://github.com/ION-Altergo/altergo_platform_etl_benchmark
    role: contributor
    visibility: private
    description: Benchmark d'ingestion de données capteurs sur la plateforme Altergo
      — balaye nombre de jumeaux, de pas et fréquence d'échantillonnage.
    year: 2024
    last_active: 2024-11
    language: Python
    archived: false
    tags:
      - infra
      - python
      - data-only
  - name: altergo-strategic-docs
    role: author
    visibility: private
    description: Espace Markdown privé pour la due diligence Adani d'Altergo, la
      proposition commerciale et les docs value-delivery.
    year: 2025
    last_active: 2026-02
    archived: false
    tags:
      - docs
      - battery
      - energy
  - name: arbitrage
    url: https://github.com/ION-Altergo/arbitrage
    role: contributor
    visibility: private
    description: MILP d'arbitrage BESS pour le planning day-ahead, complété d'une
      couche d'ajustement temps réel pilotée par les prix RT/LMP.
    year: 2025
    last_active: 2025-06
    language: Python
    archived: false
    tags:
      - battery
      - energy
      - python
      - optimization
  - name: battery_capacity_sizer
    url: https://github.com/ION-Altergo/battery_capacity_sizer
    role: contributor
    visibility: private
    description: "Moteur de dimensionnement BESS : modèle
      assemblies-au-dessus-de-composants avec simulation année par année d'une
      stratégie d'augmentation."
    year: 2025
    last_active: 2025-09
    language: Python
    archived: false
    tags:
      - battery
      - energy
      - python
      - simulation
  - name: battery-digital-twin-models
    url: https://github.com/Miawousha/battery-digital-twin-models
    role: author
    visibility: public
    description: Modèles Python de référence (compteurs de cycles équivalents)
      packagés pour le runtime jumeau numérique d'Altergo.
    year: 2025
    last_active: 2025-09
    language: Python
    stars: 0
    archived: false
    tags:
      - battery
      - energy
      - python
      - library
  - name: battery_usage_analyzer
    url: https://github.com/ION-Altergo/battery_usage_analyzer
    role: contributor
    visibility: public
    description: Modèle de segmentation multi-couches qui étiquette les modes
      opératoires batterie, les points de rupture et les phases CC/CV à partir
      de séries temporelles.
    year: 2025
    last_active: 2025-09
    language: Python
    stars: 0
    archived: false
    tags:
      - battery
      - energy
      - python
      - library
  - name: bess_control_sim
    url: https://github.com/ION-Altergo/bess_control_sim
    role: contributor
    visibility: private
    description: Simulateur de dispatch BESS avec PID de régulation, pertes
      transformateur et configurateur Dash.
    year: 2025
    last_active: 2025-05
    language: Python
    archived: false
    tags:
      - battery
      - energy
      - python
      - simulation
  - name: cell-imbalance
    url: https://github.com/ION-Altergo/cell-imbalance
    role: contributor
    visibility: private
    description: Indice de dispersion cellule/module et estimateur de tendance Rdc
      par événements, déployables via le SDK Altergo.
    year: 2025
    last_active: 2025-10
    language: Python
    archived: false
    tags:
      - battery
      - python
  - name: cell-model-visualizer
    role: author
    visibility: private
    description: Outil Vite/React pour inspecter un JSON de modèle de cellule
      batterie via des onglets OCV, impédance, thermique, vieillissement et
      sécurité.
    year: 2025
    last_active: 2025-09
    language: TypeScript
    archived: false
    tags:
      - battery
      - react
      - typescript
      - tooling
  - name: cellsos
    url: https://github.com/ION-Altergo/cellsos
    role: contributor
    visibility: private
    description: Modèle de sûreté cellule avec scoring de stress et derating de
      courant 2D, déployable via le SDK Altergo.
    year: 2025
    last_active: 2025-11
    language: Python
    archived: false
    tags:
      - battery
      - python
  - name: demo-eq-cycle-model
    url: https://github.com/ION-Altergo/demo-eq-cycle-model
    role: contributor
    visibility: private
    description: Compteur de cycles équivalents pour une trace de courant batterie —
      débit en Ah divisé par 2× la capacité nominale.
    year: 2025
    last_active: 2025-09
    language: Python
    archived: false
    tags:
      - battery
      - python
      - demo
  - name: effective-capacity-benchmark-model
    url: https://github.com/ION-Altergo/effective-capacity-benchmark-model
    role: contributor
    visibility: private
    description: Scaffold function-template Altergo câblé pour un capteur de cycles
      équivalents — l'entrypoint ne calcule rien.
    year: 2024
    last_active: 2024-10
    language: Python
    archived: false
    tags:
      - battery
      - python
      - demo
  - name: hppc_analysis
    url: https://github.com/ION-Altergo/hppc_analysis
    role: contributor
    visibility: private
    description: "Pipeline HPPC : SOC par comptage coulombique, table OCV depuis les
      périodes de repos, résistances ECM physiques à constantes de temps
      fixées."
    year: 2025
    last_active: 2025-09
    language: Python
    archived: false
    tags:
      - battery
      - python
      - data-only
  - name: hydrogen
    url: https://github.com/ION-Altergo/hydrogen
    role: contributor
    visibility: private
    description: Simulation pas-à-pas d'usine hydrogène
      solaire+batterie+électrolyseur comparant un modèle batterie legacy à la
      batterie multi-échelle Lair.
    year: 2025
    last_active: 2025-03
    language: Python
    archived: false
    tags:
      - energy
      - battery
      - python
      - simulation
  - name: impedance
    url: https://github.com/ION-Altergo/impedance
    role: contributor
    visibility: private
    description: Estimateur événementiel de résistance interne DC (Rdc) avec
      tendance EWMA et dérive en pourcentage vs baseline.
    year: 2025
    last_active: 2025-10
    language: Python
    archived: false
    tags:
      - battery
      - python
  - name: model_boilerplate
    url: https://github.com/ION-Altergo/model_boilerplate
    role: contributor
    visibility: private
    description: Scaffold de référence pour construire des modèles batterie jumeau
      numérique sur le SDK Altergo.
    year: 2025
    last_active: 2025-12
    language: Python
    archived: false
    tags:
      - battery
      - python
      - library
  - name: rtbm
    url: https://github.com/ION-Altergo/rtbm
    role: contributor
    visibility: private
    description: Real-Time Battery Model — simulateur BMS physique sur le SDK
      Altergo et le cœur lair battery_iq.
    year: 2025
    last_active: 2025-09
    language: Python
    archived: false
    tags:
      - battery
      - python
      - simulation
  - name: rtbm-clone
    url: https://github.com/ION-Altergo/rtbm-clone
    role: contributor
    visibility: private
    description: Workflow jumeau numérique — réplique un asset batterie réel et
      rejoue son profil via le simulateur lair.
    year: 2024
    last_active: 2024-10
    language: Python
    archived: false
    tags:
      - battery
      - python
      - simulation
  - name: rtbm_dataset_generator
    url: https://github.com/ION-Altergo/rtbm_dataset_generator
    role: contributor
    visibility: private
    description: Framework DoE matriciel pour générer des jeux de données simulés de
      batterie avec profils de défauts contrôlés.
    year: 2026
    last_active: 2026-01
    language: Python
    archived: false
    tags:
      - battery
      - python
      - simulation
      - data-only
  - name: simple_soc_model
    url: https://github.com/ION-Altergo/simple_soc_model
    role: contributor
    visibility: private
    description: Scaffold pédagogique — function-template Altergo avec une classe
      SoC triviale en comptage coulombique.
    year: 2024
    last_active: 2024-10
    language: Python
    archived: false
    tags:
      - battery
      - python
      - demo
  - name: soc
    url: https://github.com/ION-Altergo/soc
    role: contributor
    visibility: private
    description: Estimateur SoC à double borne — comptage coulombique + table OCV
      avec Peukert et dynamique multi-RC.
    year: 2025
    last_active: 2025-10
    language: Python
    archived: false
    tags:
      - battery
      - python
      - simulation
  - name: soc-model
    url: https://github.com/ION-Altergo/soc-model
    role: contributor
    visibility: private
    description: Estimateur SoC de première génération (2024) — un script coulomb +
      OCV à double borne, remplacé par soc.
    year: 2024
    last_active: 2024-10
    language: Python
    archived: false
    tags:
      - battery
      - python
      - shelved
  - name: sop
    url: https://github.com/ION-Altergo/sop
    role: contributor
    visibility: private
    description: State-of-Power — courant max soutenable en charge/décharge sur un
      horizon 1–10 min, Thevenin + ECM.
    year: 2025
    last_active: 2025-09
    language: Python
    archived: false
    tags:
      - battery
      - python
      - simulation
  - name: supplier-data-mapping
    url: https://github.com/ION-Altergo/supplier-data-mapping
    role: contributor
    visibility: private
    description: Outillage de classification de signaux BESS — agents orchestrés par
      Cursor, outils Python et catalogues JSON.
    year: 2026
    last_active: 2026-01
    language: Python
    archived: false
    tags:
      - ai
      - agent
      - python
      - tooling
      - battery
      - energy
  - name: tsdb-benchmark
    url: https://github.com/ION-Altergo/tsdb-benchmark
    role: contributor
    visibility: private
    description: Comparatif de bases time-series — QuestDB, ClickHouse, TimescaleDB
      sur ingestion capteur simulée.
    year: 2025
    last_active: 2025-09
    language: Python
    archived: false
    tags:
      - infra
      - data-only
      - python
---

Altergo est la plateforme d'intelligence batterie d'Alexandre : modèles physiques, estimateurs d'état, simulateurs et outils de données pour surveiller et prédire le comportement des systèmes de batteries. Les dépôts ci-dessous en sont les composants.

## aging_battery_lifetime_simulator

aging_battery_lifetime_simulator pilote une Battery électrochimique issue de la librairie interne `lair` (hiérarchie Cell / Stack / ElectroChemEntity avec un modèle de SoH attaché) à travers un profil de puissance et de température ambiante pour projeter le vieillissement du pack. La boucle principale dans `lifecycle_simulation.py` interpole la charge, fait tourner `batteryStateMachine` pour gérer le taper de charge (5 % avant le SoC max), les coupures thermiques à 55 °C avec hystérésis de 10 °C, et les arrêts haute/basse tension, puis avance chaque élément via `calculateNextStep(dt, T_amb)` sur un pas de temps adaptatif fourni par `altergo_sdk.tools.sim.update_time_step`. Les séries de SoC, SoH, vieillissement calendaire et cyclique, cycles équivalents, tension, courant et température sont enregistrées par des `Sensor` à seuil de variance, avec des seuils resserrés sur les 24 h initiales et finales — les "record days" — pour des frontières haute résolution.

### What

Prend un profil d'usage (séries temporelles de puissance demandée + température ambiante, fourni en dataset ou produit par un générateur synthétique simple) et la spécification d'un composant batterie, et retourne la projection dans le temps de SoC, SoH, vieillissement calendaire, vieillissement cyclique, tension, courant et température sur la durée de vie du pack. Les clients s'en servent pour valider qu'une chimie de cellule et un design de pack candidats survivent à un cycle de service cible avant l'achat ; le même script produit aussi les preuves de calibration qui alimentent les courbes de garantie du capacity sizer.

### Tech

Bâti sur la librairie batterie interne `lair` (`Battery` / `Cell` / `Stack` / `ElectroChemEntity` avec des modèles `Soh` interchangeables) et sur le module `altergo_sdk.tools.sim` (`Sensor`, `update_time_step`). `batteryStateMachine` (depuis `lair.components.battery_iq.clone`) impose l'enveloppe de sécurité — taper de charge à `maxSoC - 5 %`, hystérésis thermique 55 °C / 45 °C, déclenchements `lowVoltageSafetyCutoff` / `highVoltageSafetyCutoff`, écrêtage du courant. Le pas de temps est adaptatif : court pendant les transitoires, long pendant les repos. L'enregistrement passe par des `Sensor` à seuil de variance pour garder une sortie compacte sur les runs pluriannuels, avec des seuils ramenés près de zéro sur les "record days" configurés en début et en fin pour résoudre finement les fenêtres frontières. `main.py` enveloppe la boucle dans un job de plateforme Altergo qui lit `altergo-settings.json`, télécharge le dataset de profil, lance la simulation, et renvoie les résultats sous forme de graphes Plotly.

### Status

Brique active de la chaîne d'outils battery-engineering Altergo en 2025 ; tourne à la demande sur la plateforme dans le cadre des études de dimensionnement et de validation de durée de vie clients. Écrit en contributeur dans l'organisation ION-Altergo. Pas un one-shot — le code intègre le précachage de profil, des runs locaux en mode debug, et un utilitaire de répétition de profil pour stresser les chimies contre des cycles accélérés sur plusieurs années.

## altergo_platform_etl_benchmark

altergo_platform_etl_benchmark mesure l'ingestion bout-en-bout des données capteurs sur la plateforme Altergo : le débit en écriture, pas la lecture. `benchmark/main.py` balaye une grille de nombres de jumeaux numériques (10 → 100), de nombres de pas (1k → 1M) et d'intervalles d'échantillonnage (1 s → 30 min), génère des séries temporelles aléatoires et les pousse via `altergoClient.sendSensorDataToAssets`. Chaque exécution journalise les temps backend rapportés (download / processing / ingestion) à côté des temps client (processing / zipping / uploading) dans `benchmark_results.csv`, ce qui permet de régresser la latence en fonction du volume × cardinalité. Pas de README — le script et son CSV de sortie tiennent lieu de spécification.

### What

Harnais de benchmark mono-usage pour le chemin d'ingestion de la plateforme Altergo. Balaye une grille 10 × 4 × 4 de configurations (nombre de jumeaux, nombre de pas, intervalle d'échantillonnage) — 160 runs en mode par défaut — et pour chacune nettoie le workspace, instancie les blueprints, instancie les jumeaux, génère des données capteurs aléatoires, les pousse via le SDK et enregistre la mesure. La sortie est un CSV plat qu'on peut tracer pour voir comment la latence d'ingestion évolue avec la taille du payload et la cardinalité des assets.

### Tech

Python pur au-dessus du SDK Altergo (`altergoClient.sendSensorDataToAssets`, instanciation par templates de blueprints). Le driver dans `benchmark/main.py` utilise `importlib.reload` sur quatre modules d'étapes (`step_00_cleanup` → `step_03_simulate_data_and_send`) dans une boucle imbriquée, en pilotant les configurations par variables d'environnement (`DIGITAL_TWIN_NUMBER`, `TIME_STEP_IN_MILLISECONDS`, `STEP_NUMBER`). Chaque run instrumente les deux côtés du fil — temps backend rapportés (download/processing/ingestion, extraits de la réponse SDK) et durées mesurées côté client (processing/zipping/uploading) — donc on peut reconstituer depuis le seul CSV la répartition entre coût de compression client et coût d'écriture serveur.

### Status

Outil one-shot de platform-engineering fin 2024 ; pas un produit pérenne. Les CSV de sortie ont alimenté les décisions de capacity planning du chemin d'écriture Altergo. Environ 20 Ko de code, sans README ni tests — le script tient lieu de spécification. Écrit en contributeur dans ION-Altergo.

## altergo-strategic-docs

altergo-strategic-docs est un dépôt de travail en Markdown pour la mission Altergo × Adani — plans de due diligence sur trois ateliers, versions du cadre commercial, proposition de partenariat stratégique, et bibliothèque value-delivery couvrant les mécanismes de capacité utile, d'extension de durée de vie, de disponibilité et de réduction des coûts O&M avec un cadre de quantification. Contient aussi la présentation plateforme (Digital Twin, Battery Intelligence, ESS/UPS) et la réponse à l'appel d'offres logiciel BESS. Pas de code déployable ; livrables privés d'une mission client.

### What
Dix-neuf fichiers Markdown organisés en quatre dossiers : `due-diligence/`
(plan DD Adani, DD étendu avec périmètre IP et contraintes d'accès au code,
diagramme de processus Mermaid, exemple de DD), `value-delivery/` (les quatre
chapitres de mécanismes et leur cadre de quantification), `commercial/`
(proposition + v1/v2 du cadre commercial), et `platform/` (vue d'ensemble
Altergo, réponse RFQ BESS, cadre KPI capacité utile). `INDEX.md` est le point
d'entrée unique.

### Tech
Markdown brut avec un schéma d'architecture (`altergo_archi.png`) et du
Mermaid embarqué pour le flux DD. Pas de build, pas d'outillage. Versioning par
historique git (suffixe `_v2` sur le cadre commercial plutôt que des branches).

### Status
Vivant en 2025, dernière modif 2026-02. Utilisé en interne comme jeu de
livrables de travail pour la mission Adani — ateliers DD, négociation
commerciale, réponse RFQ. Dépôt privé ; pas pour redistribution.

## arbitrage

arbitrage optimise le trading d'un Battery Energy Storage System sur les marchés day-ahead et temps réel. `bess_arbitrage_optimizer.py` formule un MILP en PuLP sur un horizon de 24 h, à un pas de 15, 30 ou 60 minutes, avec des variables continues de puissance de charge/décharge et d'état d'énergie, des variables binaires d'état (charging / discharging / idle / soak — exactement une active par période), une fenêtre de "soak" d'environ 2 h au-dessus d'un SoC minimum, des plafonds de cycles équivalents complets par jour, des limites de puissance dépendantes de la SOE (interpolées à partir de tableaux), un rendement aller-retour et un retour imposé à la SOE initiale. `realtime_bess_optimizer.py` consomme ensuite le planning produit et décide de suivre, dévier ou couper en urgence en fonction de l'écart RT/DA, des limites de déviations consécutives, d'une marge de sécurité sur les FCE, du coût de transaction et des bornes de SOE. Des chargeurs pour le DAM indien et des exporteurs de plannings EMS/SCADA cohabitent ; les 40 Mo du dépôt sont surtout du HTML Plotly embarqué.

### What

Deux optimiseurs couplés qui permettent à un opérateur BESS de (a) planifier un planning charge/décharge profitable pour le lendemain face à une courbe de prix day-ahead, et (b) réagir intelligemment quand les prix temps réel divergent de ces hypothèses au cours de la journée. Le day-ahead répond à « à quoi doit ressembler le planning de demain ? » ; le temps réel répond à « avec le prix que je vois maintenant, est-ce que je suis le plan, je dévie, ou j'arrête ? ». Les sorties incluent un planning JSON compatible EMS/SCADA, un Excel détaillé du revenu, et des dashboards Plotly HTML.

### Tech

Le day-ahead est un vrai MILP (pas un LP continu) — `pulp.LpVariable.dicts(..., cat='Binary')` sur `state_charging`, `state_discharging`, `state_idle`, `state_soak` avec la contrainte d'exclusion mutuelle par période `state_charging[t] + state_discharging[t] + state_idle[t] + state_soak[t] == 1`. La physique batterie est encapsulée dans un `@dataclass BatteryConstraints` avec `max_fce_per_day`, `soak_duration_hours`, `min_soak_soc`, `aux_capacity_loss_rate`, et des tableaux de limites de puissance indexés en SOE, interpolés via `_interpolate_power_limits`. Le contrôle temps réel est une machine à états avec un enum `DeviationDecision` (`FOLLOW_SCHEDULE`, `DEVIATE_CHARGE`, `DEVIATE_DISCHARGE`, `DEVIATE_IDLE`, `EMERGENCY_STOP`) verrouillé par `max_consecutive_deviations`, une marge de sécurité FCE et un coût de transaction configurable. Des CSV DAM indiens (15 min et horaire) sont livrés pour la reproductibilité ; les exporteurs EMS/SCADA produisent le schéma JSON documenté dans `EMS_SCHEDULE_FORMAT.md`.

### Status

Projet actif en 2025, écrit en contributeur dans ION-Altergo. Le dépôt porte des traces de production — `production_schedule.json`, `production_rt_decisions.json`, `realtime_decisions_log.json` — il a donc été poussé sur de vrais plannings, pas seulement en notebook. Les 40 Mo viennent quasi entièrement des rapports Plotly HTML pré-bundlés pour des scénarios commerciaux/client (volatilité haute/moyenne/basse, pas 15/30/60 min), pas du code. Les tests couvrent les contraintes FCE, l'imposition du soak, la gestion des intervalles et la logique de décision temps réel.

## battery_capacity_sizer

battery_capacity_sizer dimensionne et projette dans le temps un site BESS à partir d'une instruction de build et d'une exigence de charge. Le code superpose `assemblies/` (BESS → arbre EnergyBlock → PowerConversionUnit) au-dessus de `components/` (BatteryContainer, PCSUnit, Transformer, SwitchGear, MiniSoH, consommation auxiliaire) au-dessus de `requirements/` (profil de charge). `main.py` aiguille trois modes : `bess_summary_generation` construit le site une fois et émet un résumé nameplate / rendements pondérés / power stack validé par un `DesignRuleChecker` ; `bess_augmentation_strategy` fait tourner `BESS.simulate_time()` année par année sous une `MaintenanceStrategy` pour modéliser la décroissance de SoH, l'ajout de containers et les cibles annuelles de capacité effective ; `bess_single_degradation` simule une trajectoire de dégradation unique. Le dimensionnement est donc itératif (simulation pas-à-pas avec déclencheurs de maintenance), pas une formule fermée, et les sorties incluent les heatmaps Plotly de capacité, de puissance et de bande passante PCU livrées aux clients.

### What

Outil pré-vente et ingénierie qui transforme une exigence du type « on veut X MWh / Y MW sur Z ans avec telle garantie de SoH » en une configuration BESS buildable plus le plan d'augmentation année par année nécessaire pour la tenir. Le mode `bess_summary_generation` donne la réponse rapide (« cette configuration satisfait-elle même les règles de design ? ») ; `bess_augmentation_strategy` donne la réponse profonde (« combien d'ajouts de containers, et en quelles années, pour rester au-dessus de la courbe de garantie de capacité effective ? ») ; `bess_single_degradation` produit la trajectoire d'une stratégie choisie. Les sorties alimentent des PDF et dashboards livrés aux clients.

### Tech

Modèle objet en trois couches : `assemblies/` (`BESS`, `EnergyBlock`, `PowerConversionUnit`) compose `components/` (`BatteryContainer`, `PCSUnit`, `Transformer`, `SwitchGear`, `MiniSoH`, `auxillary/`) contre un profil de charge dans `requirements/`. Le dimensionnement n'est pas une formule fermée — `BESS.simulate_time(years)` fait tourner une boucle explicite pas-année pilotée par une `MaintenanceStrategy` (`utils.helpers.augmentation_configuration.MaintenanceStrategy`) qui décide quand ajouter des containers pour maintenir la capacité effective au-dessus de la cible annuelle. Un `DesignRuleChecker` (`utils/drc.py`) valide l'instruction de build contre la blueprint library et marque les `input_issues` avant toute simulation. La visualisation passe par des heatmaps Plotly pour la capacité, la puissance et la bande passante PCU.

### Status

Brique active de la chaîne d'outils pré-vente / ingénierie d'Altergo en 2025 (dernière activité septembre 2025). Environ 600 Ko de code, avec un dossier `tests/`, un `sandbox/`, un `CHANGELOG.md` et un `altergo_demo_builder/` — la maturité d'un vrai produit, pas d'un notebook. Écrit en contributeur dans ION-Altergo. Les sorties Plotly sont câblées dans les livrables clients, donc les changements ici se voient en aval.

## battery-digital-twin-models

battery-digital-twin-models est un package Python de référence qui montre comment livrer des modèles batterie pour le runtime jumeau numérique d'Altergo. Deux modèles aujourd'hui : `eq_cycles` (comptage simple de cycles via le débit coulombique) et `adv_eq_cycles` (un compteur de cycles équivalents calibré LFP qui pondère le débit par le C-rate soutenu, la température via un facteur Q10 cyclique et une surtaxe charge basse température, et un modèle de stress SOC en smoothstep). Chaque modèle hérite de `Model` du `altergo_sdk` et s'enregistre via `@register_model` ; `entrypoint.py` est un wrapper mince qui appelle le boilerplate `execute_altergo_models` du SDK. Open-source pour que les auteurs de modèles puissent copier le patron sans toucher aux entrailles du SDK.

### What
Deux modèles pip-installables que la plateforme Altergo exécute sur les
séries temporelles d'actifs. `eq_cycles` renvoie le cumul de cycles
équivalents standard à partir de `current` (débit Ah / 2·capacité), avec une
correction optionnelle d'efficacité coulombique et une compensation de capacité
basée SOH. `adv_eq_cycles` (enregistré comme `enhanced_equivalent_cycles`)
renvoie `std_cycle_count`, `equivalent_cycle_count` et `cycle_life_fraction` —
le même débit pondéré par un produit borné de trois multiplicateurs (C-rate,
température, SOC). Chaque dossier modèle livre son propre manifeste
`model.json` (noms logiques entrée/sortie, unités, flags `required`) et un
README ; le mode debug émet un dashboard HTML des entrées, paramètres et
sorties.

### Tech
`@register_model(name, metadata={category, complexity, computational_cost})`
publie la classe vers un registre que le SDK découvre à l'exécution — les
auteurs ne câblent jamais leur modèle dans une main loop. Les entrées
arrivent en `pandas.Series` indexées par `DatetimeIndex` ; le modèle possède
sa propre base de temps via `current.index.to_series().diff()`. Le lissage du
modèle avancé est une EMA causale du premier ordre sur un `dt` irrégulier ; le
stress SOC utilise des rampes en cubic smoothstep autour de 80–96 % (pénalité
haut-SOC dominante LFP) et une rampe faible 2–8 % bas-SOC ; la température
applique `Q10^((T-Tref)/10)` avec une surtaxe risque-plating uniquement en
charge sous 15 °C ; le multiplicateur combiné est borné à [0.2, 3.0].
`requirements.txt` se réduit à pandas + numpy + le `altergo_sdk` privé. La
configuration est en couches : défauts dans le code, manifeste dans
`model.json`, override runtime dans `altergo-settings.json`.

### Status
Construit et déployé sur des actifs clients Altergo en 2025 ; dernier commit
2025-09. Open-source sous l'organisation Altergo comme exemple canonique du
« comment écrire un modèle » — les équipes internes et partenaires
d'intégration copient la structure. Deux modèles dans ce dépôt aujourd'hui ;
la plateforme en exécute des dizaines d'autres depuis des dépôts privés
voisins suivant le même patron.

## battery_usage_analyzer

battery_usage_analyzer est l'emplacement canonique d'un modèle de segmentation multi-couches pour séries temporelles batterie, packagé au-dessus du framework `boiler_plate.Model` du SDK Altergo. À partir du courant, du SoC et des min/max de tension et température cellule, `BatteryUsageAnalyzer.process` émet une couche 0 de modes opératoires (charge / décharge / idle), une couche 1 de points de rupture pilotés par les données via un score de changement composé multi-signaux avec z-score robuste et contrainte de gap minimum, et une couche 2 de phases métier (repos, charge CC, charge CV, décharge) par étiquetage majoritaire par segment. Le dépôt suit le même gabarit en deux couches que le dépôt personnel `battery-digital-twin-models` (README, `entrypoint.py` et structure `models/` partagés), mais accueille un jeu de modèles différent — analyzer et `eq_cycles` ici, contre `eq_cycles` et `adv_eq_cycles` côté perso — donc le framework est partagé, la science ne l'est pas. Cette copie ION-Altergo est l'emplacement canonique pour l'usage analyzer.

### What

Transforme la télémétrie batterie brute (courant, SoC, extrêmes cellule de tension et température) en une timeline étiquetée — dans quel mode la batterie était à chaque instant, où son comportement a changé, et à quelle phase CC/CV/repos chaque segment appartient. Les analytics en aval (comptage de cycles, modèles de dégradation, dashboards) consomment ces étiquettes plutôt que de re-parser les signaux bruts, ce qui centralise la science.

### Tech

Bâti sur le framework `boiler_plate.Model` du SDK Altergo — `@register_model("battery_usage_analyzer")` expose la classe, `model.json` porte le manifeste, et `entrypoint.py` délègue à `execute_altergo_models`. La couche 0 est règle-based sur courant signé et delta SoC. La couche 1 calcule des dérivées par seconde sur `current`, `soc`, `v_cell_min`/`v_cell_max`, `t_cell_min`/`t_cell_max`, les lisse en EWM, applique un z-score robuste (median/MAD) via `robust_z`, compose un score de changement multi-signaux via `compose_change_score`, sélectionne les pics au-dessus d'un seuil avec `detect_peaks_over_threshold`, et impose un gap minimum via `enforce_min_gap`. La couche 2 prend les frontières de la couche 1 et attribue la phase dominante par segment via `majority_label_per_segment`. Le dépôt partage README, `entrypoint.py` et l'arborescence `models/` avec le dépôt personnel `battery-digital-twin-models` — un cousin par gabarit, pas un fork — mais chacun héberge un jeu de modèles distinct.

### Status

Emplacement canonique côté ION-Altergo pour l'usage analyzer (le dépôt personnel `battery-digital-twin-models` porte plutôt `eq_cycles` et `adv_eq_cycles`). Actif en 2025 (dernière activité septembre 2025), visibilité publique dans l'org ION-Altergo. Livré avec un `run_tests.py`, un README spécifique au modèle, un `MODEL_CREATION_GUIDE.md` qui documente comment ajouter un nouveau modèle au framework, et un dossier `documentation/`. Les étiquettes émises sont consommées par d'autres modèles de la chaîne d'outils batterie Altergo.

## bess_control_sim

bess_control_sim est un simulateur Python pour la boucle de contrôle EMS d'un site BESS multi-conteneurs. Modélise une flotte de conteneurs derrière un transformateur IDT 30 MVA à quatre entrées BT (ratings par entrée, pertes fer + cuivre, redistribution proportionnelle quand une entrée sature), des courbes de C-rate charge/décharge dépendant du SoE, un PID `PlantPowerPID` et un PID optionnel de compensation de déséquilibre. Une app Dash expose la configuration en panneau gauche (durée de simulation, conteneurs par entrée BT, rating du transformateur, toggles PID) et trace les timeseries de puissance, SoE et par entrée BT en Plotly. Bac à sable interne pour itérer sur la logique de dispatch avant qu'elle ne touche l'EMS de production.

### What
Prend en entrée une consigne de puissance plant et une configuration de site, et produit un dispatch résolu dans le temps : puissance instantanée par conteneur, SoE par conteneur, charge par entrée BT, et puissance côté transformateur après pertes. L'objectif est de répondre à « cette loi de contrôle délivre-t-elle la puissance AC demandée sans dépasser une entrée BT ni violer les enveloppes C-rate ? » avant d'accorder les gains sur l'EMS réel.

### Tech
`bess_model.py` construit la topologie (conteneurs regroupés sous quatre entrées BT, transformateur IDT avec modèle de pertes fer + cuivre, redistribution proportionnelle en saturation) ; `sim.py` intègre la boucle pas à pas avec `PlantPowerPID` au niveau plant et un second PID optionnel compensant le déséquilibre par entrée ; les courbes C-rate charge/décharge dépendant du SoE bornent chaque conteneur. `dash_app.py` câble un configurateur (durée, conteneurs par entrée BT, rating transformateur, toggles PID) aux traces Plotly de `plotting.py`. Python pur — aucune dépendance au SDK ni à la plateforme Altergo.

### Status
Bac à sable interne de logique de contrôle chez Altergo, dernière activité 2025-05. Utilisé pour prototyper les stratégies de dispatch et de compensation de déséquilibre avant leur intégration dans l'EMS de production.

## cell-imbalance

cell-imbalance est un dépôt Python qui contient deux modèles batterie bâtis sur l'`AltergoModelBoilerplate` afin de s'exécuter en jobs jumeau-numérique déployables. `CellModuleImbalanceIndexModel` dérive un écart absolu en mV à partir des agrégats `voltage_min`/`max` des cellules, un pourcentage relatif à la moyenne, un indice de déséquilibre 0–1 mis à l'échelle d'un seuil d'alarme configurable avec un exposant de shaping, et une sortie tri-état OK/Warn/Alarm, avec une compensation de température optionnelle qui retranche `|TCV| * ΔT` du ΔV brut ; les entrées au niveau module sont traitées de la même manière quand présentes. `RdcTrendEstimator` détecte les marches de courant au-dessus d'un seuil, calcule les médianes de V et I dans des fenêtres pré/post autour de chaque marche, en dérive une résistance interne DC par événement `|ΔV|/|ΔI|`, filtre optionnellement les outliers par MAD, puis suit une tendance EWMA contre une baseline.

### What
Les entrées proviennent d'un jumeau numérique BMS en direct — agrégats min/max/moyenne de tension par cellule et par module, courant pack, et optionnellement températures cellule. Les sorties sont trois flux qu'un opérateur peut alerter et tendancer : un indice de dispersion plus état OK/Warn/Alarm pour cellules et modules (attrape les cellules faibles qui dérivent avant un trip), et une tendance Rdc événementielle contre baseline avec un pourcentage de dérive (attrape la croissance lente de résistance signe de vieillissement ou de dégradation de contact).

### Tech
`models/cell_imbalance/cell_imbalance.py` calcule ΔV depuis voltage_min/voltage_max, normalise en indice 0–1 mis à l'échelle d'`alarm_threshold_mv` avec un exposant de shaping, applique une compensation de température optionnelle `|TCV| * ΔT`, et duplique le pipeline au niveau module. `models/rdc_trend_estimator/rdc_trend_estimator.py` balaye la trace de courant pour des marches au-dessus d'un seuil configurable, prend les médianes de V et I dans des fenêtres pré et post séparées par une garde, divise pour obtenir une résistance DC par événement, filtre les outliers par MAD, puis maintient une EWMA contre une baseline et rapporte un pourcentage de dérive. Tous deux héritent d'`AltergoModelBoilerplate` ; `entrypoint_simple.py` et `entrypoint_advanced.py` les enregistrent pour le déploiement SDK.

### Status
Dépôt interne de modèles jumeau-numérique Altergo, dernière activité 2025-10. Déployé contre des assets BESS en production pour remonter aux opérations les alarmes de dispersion cellule et les tendances de vieillissement Rdc.

## cell-model-visualizer

cell-model-visualizer est une appli interne Vite + React 19 pour explorer un fichier JSON de modèle de cellule batterie. L'utilisateur charge une cellule dans une bibliothèque persistée en localStorage, puis bascule entre les onglets Overview / OCV / Impédance / Thermique / Vieillissement / Sécurité — chacun affiche des vues Plotly sur le même dataset (fabricant, modèle, version, date de mise à jour, courbes de caractérisation). Import drag-and-drop via `FileHandler` ; MUI pour la coque. Outil compagnon des travaux de modélisation cellule chez Altergo ; non public.

### What
Sept onglets dans une coque MUI `AppBar` + `Tabs`. **Library** liste les
cellules importées (avec une cellule de démo LiFePO4 32700 par défaut) et
change la cellule active au clic. **Overview** affiche les fiches
caractéristiques physiques / électriques / thermiques depuis le JSON. **OCV
Curves**, **Impédance**, **Thermique**, **Vieillissement** et **Sécurité**
rendent des vues Plotly sur les tableaux de caractérisation du JSON (tables
SOC-OCV, spectres EIS, coefficients thermiques, paramètres du modèle de
vieillissement, enveloppe sécurité). Le header garde version et date de mise
à jour visibles. Le JSON est un schéma imbriqué volumineux avec
`physical_properties`, `electrical_specifications`, plage de tension, ratings
courant, etc. — ce que l'équipe modélisation d'Altergo produit à partir d'un
run de calibration.

### Tech
Vite + React 19 + MUI + Plotly. Pas de backend. L'état tient dans deux clés
`localStorage` — `cellModelVisualizer_importedCells` (la bibliothèque) et
`cellModelVisualizer_currentCell` (le dataset actif) — donc un refresh garde
votre travail, et rien ne quitte la machine. `FileHandler` accepte un JSON en
drag-and-drop et le route via `handleDataImport`, qui déduplique par
fabricant+modèle. Le design de bibliothèque permet aux ingés de comparer des
cellules sans serveur.

### Status
Construit en 2025 en parallèle des travaux de modélisation cellule d'Altergo ;
dernier commit 2025-09. Utilisé en interne pour vérifier les sorties de
calibration et pour montrer à quoi « ressemble » un modèle de cellule à des
stakeholders non-modélisation. Privé ; une cellule de démo livrée plus ce que
l'utilisateur importe.

## cellsos

cellsos est un `CellLimitsModel` Python bâti sur l'`AltergoModelBoilerplate` d'Altergo, qui surveille la tension, la température et le courant des cellules lithium contre leurs limites d'opération sûres. Les limites de courant charge et décharge dynamiques sont interpolées depuis une table de derating 2D température × SOC (`current_limits_table.json`) via `scipy.RegularGridInterpolator` ; les sorties incluent des marges de sécurité par paramètre, une marge minimale combinée, un score de stress instantané 0–100 %, un stress cumulé intégré dans le temps, et un statut global OK/Warning/Critical. Dépôt de modèle interne câblé via le SDK pour être déployé contre des assets jumeaux en production.

### What
Consomme la télémétrie cellule en direct (V, T, I) depuis un asset jumeau-numérique, plus l'enveloppe d'opération sûre de la cellule et une table de derating 2D température × SOC. Émet un flux continu de signaux de sécurité sur lesquels un opérateur peut alerter, plus un score de stress que la couche analytique peut intégrer dans le temps : à quel point chaque paramètre est proche de sa limite, où la marge combinée est la plus serrée, à quel point la cellule est stressée à l'instant, et quel stress accumulé elle a encaissé.

### Tech
`models/cell_limits/cell_limits.py` héberge l'unique `CellLimitsModel`. Les plafonds de courant charge et décharge dynamiques viennent de `current_limits_table.json` interpolé avec `scipy.interpolate.RegularGridInterpolator` sur température et SOC. Les marges par paramètre sont normalisées à la distance à la limite ; la marge de sécurité combinée est le minimum sur V/T/I ; le score de stress mappe 0 % (au fond de l'enveloppe) à 100 % (à la limite), puis s'accumule dans le temps pour la sortie de stress cumulé. Le tri-état OK/Warning/Critical sort de seuils de marge configurables. `entrypoint_simple.py` et `entrypoint_advanced.py` enregistrent le modèle pour le déploiement SDK.

### Status
Modèle jumeau-numérique interne Altergo, dernière activité 2025-11. Déployé via le SDK contre des assets cellule en production pour alimenter les tableaux de bord de sécurité et l'analytique de vieillissement.

## demo-eq-cycle-model

demo-eq-cycle-model est une petite démo Python qui calcule les cycles équivalents cumulés à partir d'une série temporelle de courant batterie : `eqCycles = cumsum(|I|·dt) / (2·Cnom)`. L'estimateur vit dans `tools/eq_cycle_estimator.py` ; `main.py` charge un CSV d'exemple, l'exécute pour une capacité nominale de 56 Ah, et trace eqCycles aux côtés de la tension avec Plotly. Démo autonome de la formule de cycles équivalents — pas déployée sur la plateforme, aucun appel au SDK Altergo.

### What
L'estimateur prend un DataFrame indexé par timestamp avec une colonne `Current`, calcule `time_diff` en heures à partir des valeurs d'index consécutives, multiplie par `|Current|` pour obtenir le débit en Ah par pas, divise par `2·Cnom` pour convertir les Ah en cycles complets équivalents, et retourne la somme cumulée. Le fichier `someCycleData.csv` fourni est une trace de cellule unique codée en dur ; exécuter `main.py` ouvre un graphique Plotly interactif avec eqCycles sur l'axe gauche et Voltage sur l'axe droit.

### Tech
Pandas + numpy + Plotly purs — 2,8 ko de code au total. Pas de SDK Altergo, pas de fichier de configuration, pas de scaffold d'entrypoint. La convention `Ah / (2·Cnom)` (comptage demi-cycle dans les deux sens) correspond à la formule utilisée en aval dans `effective-capacity-benchmark-model` et `hppc_analysis`.

### Status
Exemple pédagogique illustrant la formule eqCycles isolée, écrit en 2025 en marge du travail plus large sur les jumeaux numériques de batterie. Pas déployé, pas maintenu comme produit ; utilisé comme extrait de référence pour expliquer le comptage de cycles à d'autres ingénieurs ou parties prenantes.

## effective-capacity-benchmark-model

effective-capacity-benchmark-model est un scaffold function-template Altergo : `entrypoint.py` extrait les arguments de la plateforme, initialise le client SDK et récupère l'asset par ID — puis s'arrête. L'`altergo-settings.json` le déclare comme modèle « Performance » lisant un capteur `Current` + un paramètre `Capacity` et écrivant une sortie `Equivalent Cycles`, mais la logique du benchmark elle-même est absente. Placeholder / scaffold inachevé malgré le nom.

### What
Le nom du dépôt suggère un benchmark de capacité effective (Ah mesurés vs nominal comme indicateur de SOH), mais les I/O déclarés sont des cycles équivalents, pas de la capacité. L'incohérence et le corps vide signalent ensemble qu'il s'agit d'un scaffold classé sous un titre de travail et jamais terminé. En l'état, l'exécuter ne fait rien d'utile : il s'authentifie auprès d'Altergo et tire une référence d'asset.

### Tech
Utilise `extract_altergo_parameters()` et `Client(functionArguments=altergoArguments)` depuis `altergo_sdk` pour gérer les credentials, les URLs des API factory/IoT et l'`assetId` injecté par la plateforme à l'exécution. L'`altergo-settings.json` suit l'ancien schéma mono-modèle `bp_sensors` / `bp_parameters` (antérieur au registre multi-modèles `enabled_models` utilisé dans le dépôt `impedance`). 1 ko de Python, trois imports, aucun calcul.

### Status
Créé en 2024, intouché depuis. Antérieur au pattern boilerplate (`AltergoModelBoilerplate`) standardisé par le dépôt `impedance`. Code mort de fait dans l'org ION-Altergo — à reconvertir en vrai modèle de capacité effective ou à supprimer.

## hppc_analysis

hppc_analysis est un pipeline HPPC mono-fichier (~2 kLOC) qui ajuste des cellules NMC à partir de tirages bruts du SDK Altergo en une configuration batterie prête à l'emploi. `hppc_analysis_full.py` segmente chaque cycle autour de l'inversion de courant décharge→charge, intègre le courant avec un comptage coulombique lissé par `scipy.signal.savgol_filter` pour obtenir le SOC, extrait l'OCV depuis des périodes de repos ≥ 25 minutes, et calcule R0/R1/R2 directement à partir des écarts de tension à V_before / V_2s / V_5min / V_end avec τ₁ = 5 min et τ₂ = 25 min fixées (pas de curve fit). Produit un CSV OCV, un CSV de paramètres ECM, un résumé de cycles, un rapport HTML interactif et `battery_config_from_analysis.json` consommé en aval par le code de simulation ; les 48 Mo du dépôt sont quasi entièrement ces rapports Plotly HTML embarqués.

### What
L'entrée est une cellule NMC unique (asset `NMC_CELL_1_CUSTOM_617` sur `demo.altergo.io`) sur un test HPPC d'environ 10 jours, tiré via `altergoClient.getAssetSensorData` pour `Cycle_Number`, `Voltage`, `Current`, `Temperature`. La convention est que chaque cycle commence et finit à 100 % SOC et atteint 0 % à l'inversion décharge→charge, ce qui permet d'ancrer le comptage coulombique cycle par cycle sans accumulation de dérive. Les points OCV ne sont retenus que si l'écart-type de tension pendant le repos est sous 10 mV, et les fits ECM sont filtrés pour rester physiquement plausibles (1–100 mΩ pour R0, 0,1–50 mΩ pour R1/R2). Le `battery_config_from_analysis.json` exporté est le contrat consommé par les simulateurs Lair (cf. le workflow BatteryArchitectureBuilder du dépôt `hydrogen`).

### Tech
Script unique de 74 ko, ~2 kLOC, organisé en pipeline procédural : `load_full_dataset` → `identify_hppc_cycles` → par cycle `calculate_proper_soc_for_cycle` + `find_rest_periods` + `extract_ocv_points` + `identify_pulses` → `fit_ecm_to_pulse` → `create_comprehensive_ocv_table` (21 bins SOC, fenêtre ±5 %) → `generate_battery_config`. Stack : numpy, pandas, scipy (`savgol_filter` fenêtre 51, polyorder 3 ; `interp1d` ; `curve_fit` importé mais inutilisé pour R0/R1/R2), plotly subplots pour le rapport HTML, altergo-sdk pour la récupération des données. Le dépôt embarque un arbre `archive_development_files/` et `archive_removed_files/` plus les rapports HTML — le code lui-même est petit, mais les artefacts gonflent la taille à 48 Mo.

### Status
Construit en 2025 sur des données réelles de cellule NMC dans le tenant demo Altergo. Utilisé comme étape de prétraitement hors-ligne : à exécuter une fois pour caractériser une cellule, puis déposer le JSON dans des simulations Lair. Pas un modèle Altergo déployé (pas d'`altergo-settings.json`, pas de boilerplate) — une analyse data-only autonome. Le JSON de sortie est la surface d'intégration ; tout le reste (CSV, HTML) sert à la revue humaine.

## hydrogen

hydrogen est une simulation Python d'une usine hydrogène vert couplée au solaire : un `HydrogenPlantSimulation` fait avancer pas à pas un `SolarPlant`, un `Electrolyzer` (limites de rampe, seuils d'activation/désactivation, rendement kg-H₂/kWh), une `Battery`, des charges auxiliaires statiques et un dispatcher `EMS` ligne par ligne sur un profil de puissance ou d'irradiance. `main.py` tourne en trois modes — `-legacy` (classe Battery simple), `-lair` (un `BatteryArchitectureBuilder` construit à partir d'un vrai blueprint Altergo, résolu cellule/module/stack), ou `-both` en parallèle pour comparaison — l'étage PV étant optionnellement piloté par `pvmodel.new_pv_power_generation` contre des bases CEC modules/onduleurs tirées d'Altergo. Outil R&D pour confronter le modèle batterie legacy à la batterie Lair électrochimiquement résolue sur des scénarios solaire+H₂ identiques.

### What
L'entrée est un dataset CSV (référencé par `power_profile_dataset_id` dans la config plateforme) — soit un profil de puissance précalculé, soit des données brutes d'irradiance/météo converties en puissance via `run_pv_simulation` contre des bases CEC modules + onduleurs. Le modèle de l'usine câble SolarPlant + Electrolyzer + Battery + AirCooledCondenser + deux StaticLoad (`auxPlantLoads`, aux minimal électrolyseur) à travers un dispatcher EMS ; pour chaque pas de temps, l'EMS décide des flux selon les contraintes de rampe, les seuils d'activation/désactivation et l'état batterie. Produit un `simulationDf` de toutes les variables par pas, un tableau de KPI, et optionnellement une page HTML statique ; quand `UPLOAD = True`, les résultats sont repoussés dans Altergo comme nouvel asset avec ses dashboards. La branche Lair fait tourner une batterie électrochimiquement résolue (cellule → module → stack), la branche legacy une Battery SOC simple — le mode `-both` les exécute sur les mêmes entrées pour comparer les trajectoires SOC/tension.

### Tech
Le cœur vit dans `balanced_simulation/` : `SolarPlant.py`, `Electrolyzer.py` (limites de rampe, activation/désactivation, rendements de production H₂ de base + fractionnel, conversion kg-H₂/kWh), `Battery.py` (legacy lumped), `EMS.py`, `EnergySystem.py`, et `HydrogenPlanSimulation.py` qui les compose. La branche Lair utilise `lair.components.battery_iq.battery_architecture_builder.BatteryArchitectureBuilder` contre un blueprint « Test Battery » récupéré sur Altergo, produisant une `Battery` de `Cell` / `ElectroChemEntity` résolue à `LEVEL_MODULE` / `LEVEL_STACK`. La modélisation PV vit dans `pvmodel/new_pv_power_generation.py`, alimentée par des datasets CEC modules et onduleurs tirés via URLs de téléchargement Altergo. `pyinstrument` est câblé (en commentaire) pour profiler les runs Lair, le modèle cellule-résolu étant nettement plus lent que le legacy. Les sous-dossiers parallèles `demo_simulation/`, `realtime_h2_model/` et `pvmodel/` contiennent des variantes apparentées et un entrypoint temps réel déployable.

### Status
Construit en 2024–2025, dernière activité mars 2025. Outil R&D / validation — pas un modèle client-facing. Utilisé pour valider la batterie multi-échelle Lair sur un scénario solaire+H₂ représentatif avant publication pour déploiements clients ; la comparaison legacy/lair est le contrôle principal. 356 ko de Python ; `UPLOAD` est par défaut à false pour exécuter le script hors-ligne contre un vrai blueprint Altergo sans polluer les données plateforme.

## impedance

impedance est un modèle de santé batterie qui estime la résistance interne DC à partir d'événements de saut de courant — pas un ajusteur de spectre EIS, malgré le nom du dépôt. `RdcTrendEstimator` dans `models/rdc_trend_estimator/` détecte les sauts bruts de courant au-dessus de `di_threshold_abs`, prend la médiane de V et I dans des fenêtres pré/post avec une bande de garde autour de chaque marche, calcule `Rdc = |ΔV|/|ΔI|`, rejette les valeurs aberrantes via z-score MAD, et émet une série Rdc par événement plus une tendance EWMA et un pourcentage de changement par rapport à une baseline configurable. Bâti sur le model boilerplate Altergo (`AltergoModelBoilerplate` pilote l'entrypoint), donc le modèle se déploie contre des assets jumeaux en production avec la plomberie SDK gérée par le framework.

### What
Les entrées sont des pandas Series UTC alignées pour `current` (A) et `voltage` (V), plus une `temperature` (C) optionnelle et un scalaire `baseline_rdc` (Ω). Le validateur refuse toute entrée désalignée, non-monotone ou vide — aucun ré-échantillonnage implicite. La détection utilise la première différence brute (`cur.diff().abs() >= di_threshold_abs`, défaut 10 A) ; pour chaque marche à `t*`, les médianes pré/post viennent de `[t*-guard-pre, t*-guard)` et `[t*+guard, t*+guard+post)` (défauts 60 s / 60 s / 60 s), donnant `Rdc_event = |ΔV| / |ΔI|`. Trois séries sont émises aux timestamps d'événements : `rdc` brut, `rdc_trend` (EWMA sur `ewma_span_events`, défaut 10), et `rdc_change_pct` vs baseline (initialisée depuis les `baseline_first_n` premiers événements ou un scalaire fourni en config). Un z-score robuste MAD (`outlier_sigma`, défaut 3,0) écarte les outliers quand `drop_outliers` est actif.

### Tech
Sous-classe `altergo_sdk.boiler_plate.Model`, déclarée dans `models/rdc_trend_estimator/model.json` (I/O logiques) et câblée dans `altergo-settings.json` (noms de capteurs plateforme : `Current` / `Maximum Voltage` / `Temperature` → `RDC Trend/DC Internal Resistance` + `RDC Trend/Rdc Trend` + `RDC Trend/Rdc Change %`). Le dépôt embarque un registre multi-modèles (`enabled_models = "eq_cycles,adv_eq_cycles,soc_eq_cycles,rainflow_cycles,rdc_trend_estimator"`), mais seul `rdc_trend_estimator` y est implémenté. Deux entrypoints — `entrypoint_simple.py` appelle `boilerplate.execute()` une fois pour le chemin auto, `entrypoint_advanced.py` expose les quatre phases (prepare → execute → debug → upload) pour les pré/post-traitements personnalisés. Les valeurs par défaut vivent dans `model.json` ; `compute_type` supporte `incremental` / `full` / `manual` avec `max_days_period_compute` pour plafonner chaque run.

### Status
Actif en 2025, dernière retouche en octobre. Modèle de qualité production — se déploie contre des jumeaux numériques batterie Altergo en production, calcule les tendances Rdc en incrémental, peut pousser les résultats vers les dashboards plateforme. Le pattern boilerplate ici (`AltergoModelBoilerplate` qui pilote tout) est le template Altergo moderne ; le dépôt `effective-capacity-benchmark-model` est un scaffold mono-modèle plus ancien qui n'a pas franchi cette génération.

## model_boilerplate

model_boilerplate est le scaffold Python canonique pour construire des modèles batterie jumeau numérique sur la plateforme Altergo. Encapsule le cycle de vie `AltergoModelBoilerplate` du SDK (préparation des données, exécution, dashboards de debug, upload des sorties) dans une paire `entrypoint_simple.py` / `entrypoint_advanced.py`, avec un pattern de registre `models/` (classes enregistrées par décorateur plus manifest `model.json` par modèle) et quatre exemples travaillés — `eq_cycles`, `adv_eq_cycles`, `soc_eq_cycles`, `rainflow_cycles`. Fondation interne que les nouveaux modèles (SoC, SoH, impédance, déséquilibre cellules, etc.) forkent au lieu de recréer la plomberie SDK.

### What
Les entrées sont un asset Altergo et une liste de séries capteurs déclarées en JSON (courant, tension, température, SoC) ; les sorties sont de nouvelles séries temporelles capteurs ré-uploadées sur le même asset. `altergo-settings.json` choisit quels modèles tournent (`enabled_models`), comment les données sont récupérées (`compute_type`, `max_days_period_compute`), et s'il faut générer des dashboards Plotly de debug ou pousser les résultats. Consommé par les workers Altergo en production et par les auteurs de modèles localement via les credentials `dev-parameters.json`.

### Tech
`entrypoint_simple.py` tient en une ligne : `AltergoModelBoilerplate(extract_altergo_parameters()).execute()`. `entrypoint_advanced.py` éclate le cycle de vie en `prepare_models_data` / `execute_models` / `show_debug_dashboards` / `upload_models_output` pour que les auteurs puissent injecter des inputs custom entre les phases. Chaque modèle sous `models/<name>/` hérite de `altergo_sdk.boiler_plate.Model`, s'enregistre via `@register_model(name, metadata=...)`, déclare son contrat d'I/O dans `model.json`, et implémente `process(data) -> dict`. Les quatre exemples livrés couvrent des compteurs de cycles équivalents et un compteur rainflow — références concrètes pour les nouveaux contributeurs. Les tests vivent sous le dossier `tests/` de chaque modèle.

### Status
Scaffold de référence actif dans la flotte de modèles batterie ION-Altergo au 2025-12. Maintenu par l'équipe plateforme ; les repos de modèles individuels (rtbm, modèles clients custom) forkent tous ce layout. Rôle contributeur — Alexandre a étendu les modèles exemples et le pattern de registre en construisant rtbm et le générateur de datasets par-dessus.

## rtbm

rtbm (Real-Time Battery Model) est un modèle enregistré dans Altergo qui simule un système batterie pas à pas à partir de séries d'entrée de puissance, courant, température et SoC. `models/rtbm/rtbm.py` construit des objets Battery/Cell/Stack à partir d'un `simspec.json` via `lair.components.battery_iq`, exécute les transitions de `batteryStateMachine` avec checks de sécurité et logique de refroidissement, et renvoie tension, température, courant, SoC et puissance sous forme de pandas Series. `entrypoint.py` récupère l'asset depuis Altergo, dérive le simspec via `BatteryArchitectureBuilder`, et délègue l'exécution à `altergo_sdk.boiler_plate.execute_altergo_models`.

### What
Entrées : quatre séries temporelles sur un asset Altergo — `power`, `current`, `temperature`, `soc`. Sorties : cinq séries simulées — `voltage`, `temperature`, `current`, `soc`, `power` — ré-uploadées comme capteurs jumeau numérique sur le même asset. Le modèle existe pour que la plateforme produise des diagnostics attendu-vs-réel sur des flottes de batteries réelles : l'écart entre tension/SoC mesurés et simulés signale dégradation, anomalies ou défauts capteur. Consommé par les workers Altergo ; une exécution par asset par fenêtre planifiée.

### Tech
`Rtbm` hérite de la classe `Model` du SDK et s'enregistre via `@register_model("rtbm", metadata={category: "Performance", complexity: "Simple", computational_cost: "Low"})`. La boucle de simulation vient de `lair.components.battery_iq.clone.batteryStateMachine` — pas de temps adaptatif piloté par `update_time_step`, logique de refroidissement, cutoffs de sécurité thermique, mode sim depth-1 (`SIM_TARGETED_DEPTH = 1`, granularité stack). `BatteryArchitectureBuilder` parcourt la hiérarchie blueprint de l'asset pour construire la `Battery` lair de `Stack`s de `Cell`s et émettre un `simspec.json`. Les capteurs de sortie sont agrégés via `dataframeFromSensors`. Dashboards Plotly de debug disponibles quand `debug_mode` est actif.

### Status
Actif en 2025 comme point de départ canonique pour les nouveaux modèles batterie sur Altergo — les modèles client plus récents (impédance, SoH, déséquilibre cellules) forkent ce layout. Dernière activité 2025-09. Rôle contributeur — Alexandre possède le code du modèle rtbm et le wiring de l'entrypoint ; l'équipe plateforme maintient le SDK et lair sous-jacents.

## rtbm-clone

rtbm-clone est la fonction Altergo qui maintient un asset "clone" jumeau numérique pour une batterie réelle. `main.py` récupère l'asset source via le SDK Altergo, construit son modèle lair `Battery` avec `BatteryArchitectureBuilder`, get-or-create un asset clone associé, charge et interpole les datasets récents puissance/température/SoC de la source, puis exécute `rtbm_clone.sim_setup.run_sim` contre le moteur de simulation lair (`GlobalSettings` / `ScenarioSettings` / `SimulationStepSettings`) avant de réécrire les capteurs simulés stack et battery via `process_simulation_results`. Pas une copie du boilerplate — un workflow de production distinct.

### What
Entrée : un asset batterie réel sur Altergo avec capteurs Current/Voltage/SoC/Temperature/Power/Ambient Temperature mesurés sur une fenêtre récente (par défaut 24h avant maintenant). Sortie : un asset clone séparé `RTBM-<source-sn>-DEMO`, fraîchement créé ou nettoyé à chaque run, peuplé de Voltage/Temperature simulés par stack plus les capteurs batterie agrégés. Le workflow existe pour que la plateforme publie un "jumeau parfait" à côté du vrai — tout ce que l'asset réel fait, le clone le rejoue à travers la physique, et les diagnostics aval les comparent.

### Tech
`get_or_create_clone_asset` gère le cycle de vie de l'asset : match par numéro de série, efface optionnellement les données ou supprime-et-recrée les assets-avec-enfants, puis assemble les stacks depuis l'interface `Stacks` du blueprint source. `prepare_simulation_data` charge les capteurs via `getAssetSensorData`, forward-fill, et passe par `interpolateValue`. La config runtime de simulation vient de `configurationValues.globalSettings` / `simulationSteps` / `runTimeSettings` mappés vers les lair `GlobalSettings` / `SimulationStepSettings` / `ScenarioSettings` par `lair_override.py`. `sim_setup.run_sim` pilote `lair.components.battery_iq.clone.run_clone_simulation`. `simulation_output.process_simulation_results` éclate le dataframe de sortie multi-stacks (`Voltage|0`, `Temperature|0`, ...) par asset enfant et pousse via `dataUpdateMethod`.

### Status
Workflow de production livré comme fonction Altergo en 2024, démontré sur l'asset Rikuti (`RK-WIT-001`). Dernière activité 2024-10 ; précède le pattern de registre model-boilerplate. Rôle contributeur — Alexandre possède `sim_setup.py`, `simulation_output.py`, `lair_override.py` et la gestion du cycle de vie d'asset. Référence architecturale pour les workflows un-asset-par-défaut ultérieurs comme rtbm-dataset-generator.

## rtbm_dataset_generator

rtbm_dataset_generator est un framework de Design-of-Experiment matriciel pour synthétiser des jeux de données d'entraînement batterie. `main_matrix.py` parcourt le produit cartésien profils de puissance × scénarios de défaut (un asset par combinaison profil-défaut, plus des baselines), charge-et-étend chaque profil CSV à une durée cible, construit la `Battery` lair depuis un simspec via `BatteryArchitectureBuilder`, exécute la simulation via `batteryStateMachine` avec `check_and_apply_anomalies` injectant des défauts contrôlés (pics d'impédance, etc.), et écrit des datasets parquet + JSON par asset plus un résumé DoE. Bâti sur `altergo_sdk` et `lair.components.battery_iq` ; alimente les données d'entraînement du modèle batterie temps réel.

### What
Piloté par `doe.json` : liste de profils de puissance (fichiers CSV indexés par timestamp), spécifications batterie (chemins de simspec, noms de blueprints), cutoffs de simulation, conditions initiales (plages SoC/SoH/température avec distributions), paramètres thermiques, et définitions de défauts (impedance_spike_early/mid, random_impedance_degradation, plus une baseline sans défaut). Total assets = profils × défauts × multiplicateur. Pour chaque combo, il produit `datasets/asset_<profile>_<fault>_NNN_data.csv` (capteurs + colonne `anomaly_status`), un fichier JSON de métadonnées, les timeseries brutes, et un `doe_matrix_summary.json` global — plus des plots HTML Plotly interactifs surlignant les périodes anormales.

### Tech
La boucle de simulation est un while-loop avec `update_time_step` adaptatif, alignée sur la référence rtbm-clone. `utils/anomaly_utils.check_and_apply_anomalies` patche l'état de la batterie en cours de run pour injecter des pics d'impédance ou de la dégradation stochastique ; `utils/doe_config.DoEConfiguration` parse `doe.json` et déploie la matrice ; `utils/simspec_generator` et `altergo_sdk.utils.blueprints.simspec` (`parse_simspec`, `calculate_cascade`, `extend_from_simspec`) construisent le modèle batterie depuis le JSON datasheet sans avoir besoin d'un asset live. `utils/dataset_generator` écrit les fichiers par asset et le résumé ; `utils/asset_service.AssetService` upload optionnellement les assets synthétisés vers Altergo. La capture de capteurs utilise `Sensor` / `dataframeFromSensors` avec `significantAppend` pour borner la taille des fichiers. Reproductible via `random_seed` configurable.

### Status
Actif en 2026-01, le plus gros des cinq repos (~170 kB de code). Génère les corpus d'entraînement pour les modèles ML de la plateforme — dégradation, détection d'anomalies, futures variantes SoH — en produisant des paires défaut-vs-baseline étiquetées qui demanderaient sinon des mois de données terrain. Rôle contributeur — Alexandre est l'auteur principal du design DoE matriciel, de la couche d'injection d'anomalies et du writer de datasets.

## simple_soc_model

simple_soc_model est le scaffold function-template d'Altergo avec un algorithme SoC placeholder — `my_soc.py` est une classe de 10 lignes qui décrémente le SoC par `current * dt / capacity * 100` (comptage coulombique de base, sans OCV, sans température, sans bornes d'erreur). `entrypoint.py` le câble au SDK, écrit un `hello.txt` et enregistre une sortie de tâche. Exemple pédagogique pour la structure function-template, pas un vrai estimateur.

### What
Montre à un développeur à quoi ressemble de bout en bout une fonction Altergo de type "model" : init du client SDK, lookup `assetId` et `programTaskId`, extraction des paramètres, une classe d'algorithme triviale, une sortie à effet de bord, et l'enregistrement d'un résultat de tâche "Visualize C-Rate" pour que l'UI plateforme reçoive un lien cliquable vers les données de l'asset. Deux frères vides (`my_model.py`, `model-validation.json`) sont là comme emplacements qu'un vrai modèle remplirait.

### Tech
`my_soc.py` est une classe `SOC(capacity, SOC)` avec une seule méthode `update_SOC(current, dt)` — `delta_SOC = current*dt/capacity*100; SOC -= delta_SOC; clamp à 0`. Pas de clamp supérieur, pas de température, pas de correction OCV, pas de gestion du sens de courant. `entrypoint.py` monte le client SDK depuis `apiKey`/`factoryApi`/`iotApi`, écrit `hello.txt`, récupère la tâche par id, fixe `task.output = [{name, icon, description, url}]` pointant vers `/assets`, et appelle `updateTask`. Le README est le mode d'emploi générique du template.

### Status
Dernier commit 2024-10. Utilisé comme exemple pédagogique canonique pour les nouveaux développeurs plateforme — couplé à `simple-app` pour montrer les deux familles de fonction. Non déployé ; la vraie implémentation SoC est passée à `soc-model` (2024) puis `soc` (2025).

## soc

soc est l'estimateur State-of-Charge actuel de la plateforme jumeau numérique Altergo — un algorithme à double borne qui fait tourner en parallèle un comptage coulombique et une lecture de table OCV avant de les fusionner, avec des marges d'erreur asymétriques pour qu'à chaque pas il émette un SoC et son intervalle d'incertitude. Bâti sur le scaffold model-boilerplate (`register_model("soc")`) ; le cœur gère compensation Peukert en décharge, modèle de tension dynamique multi-RC avec constantes de temps compensées en température, filtrage médian + passe-bas de l'OCV, contraintes directionnelles, détection de repos, et capacité effective mise à l'échelle par le SoH. Remplace `soc-model` (2024) ; livre aussi une variante historical-SoC pour le rejeu itératif sur données passées en plus de l'estimateur temps réel.

### What
Le modèle `soc` temps réel consomme des séries `voltage`/`current`/`temperature` plus un blob `battery_config` (table OCV(SoC,T), valeurs RC, exposant Peukert) et une série `soh` optionnelle ; il émet un `soc` principal, une largeur d'incertitude `soc_bounds`, l'`ocv_estimated` reconstruit, et quatre bornes de debug (`soc_coulomb_high/low`, `soc_ocv_high/low`). La variante `historical_soc` dans le même dépôt résout un autre problème : détecter des "ancres" de repos de qualité (`|I|` petit et `|dV/dt|` petit pendant ≥N minutes), mapper la tension de chaque ancre à un SoC via des courbes OCV validées en laboratoire, puis ajuster la capacité effective entre ancres consécutives pour que le comptage coulombique tombe pile sur les deux SoC d'ancres — un RANSAC fusionne les capacités par paire d'ancres en une série continue `C_eff(t)` et un SoH, avec la règle explicite que les courbes OCV viennent du labo, jamais apprises sur le terrain, pour éviter la dérive circulaire.

### Tech
Deux modèles cohabitent : `models/soc/soc.py` (`SOCEstimator(Model)`, ~1500 lignes) et `models/historical_soc/historical_soc.py` (`HistoricalSOCEstimator`, basé ancres avec `sklearn.linear_model.RANSACRegressor`). L'estimateur temps réel maintient des compteurs coulombiques high/low séparés avec erreurs courant asymétriques (`I*(1±rel_err) ± abs_err`), n'applique Peukert que si `|I|` dépasse un seuil de repos, fait tourner une pile RC `V_terminal = OCV - R0*I - Σ V_RCᵢ` où chaque `V_RCᵢ` décroît en `exp(-Δt/τᵢ)` recalculé à chaque pas, filtre l'OCV reconstruit avec une médiane sur 16 échantillons, puis applique un passe-bas et lit le SoC dans une table OCV(SoC,T) bilinéaire avec sélection charge/décharge par hystérésis. Les mises à jour sont gatées : comptage continu, recalcul SoC complet seulement quand la charge accumulée dépasse `soc_update_threshold` (0,1% de capacité) ou que `max_soc_update_interval` (60 s) s'écoule ou qu'un repos est détecté (`|I| < 0,05 A` pendant ≥30 min). La config retombe des paramètres blueprint `BP/OCV_LookupTable` / `BP/Cell_Config` vers le `battery_config.json` local. L'entrypoint est une coquille de 45 lignes qui appelle `execute_altergo_models(altergo_arguments)` depuis `altergo_sdk.boiler_plate` — toute la plomberie plateforme (résolution des entrées, décimation des sorties, remontée d'erreurs) est centralisée dans le SDK.

### Status
Modèle en production depuis 2025 ; version 1.0 actuellement sur la plateforme. Vit dans `/models/soc/` (temps réel, recalibration par OCV) et `/models/historical_soc/` (rejeu offline par ancres avec trois variantes : `historical_soc.py`, `_iterative.py`, `_simple.py`). Le dépôt embarque ~230 kB de code plus datasets de calibration, scripts de debug (`debug_anchors.py`, `debug_historical_soc.py`, `debug_iterative_fitting.py`), sorties de tests d'auto-décharge (`self_discharge_factors.png`), et un `model_creation_guide.md`. Précision annoncée ±2–5% SoC en conditions normales, avec `soc_bounds` exposant la confiance temps réel aux consommateurs en aval. Dernier commit 2025-10.

## soc-model

soc-model est l'estimateur State-of-Charge de première génération (2024) pour la plateforme Altergo — une seule classe `Estimator` (`estimator/soc_estimator.py`) qui implémente la même idée double-borne comptage coulombique + lecture OCV, avec Peukert en décharge, tension dynamique RC et OCV filtré médian. L'entrypoint récupère tension/courant/température sur la fenêtre d'une activité via le SDK Altergo, ré-échantillonne à 1 Hz, exécute l'estimateur ligne par ligne et réécrit `SoC`, `SoC Voltage High` et `SoC Voltage Low`. Remplacé par `soc` (2025), qui est passé au scaffold model-boilerplate et a ajouté tau compensé en température, mise à l'échelle SoH et contraintes directionnelles sur l'OCV.

### What
Job batch de rejeu : pour un asset cellule et une activité nommée, calcule le SoC sur cette fenêtre et le réécrit comme nouvelles séries capteurs pour que l'UI plateforme puisse les tracer à côté de la tension/courant mesurés. Lit `bp_sensors` (noms tension/courant/température), `bp_parameters` (capacité), et un JSON cell-model dans `bp_datasets` (table OCV, valeurs RC, exposant Peukert) depuis le blueprint ; émet cinq séries — `[Altergo] SoC`, `SoC Current High/Low`, `SoC Voltage High/Low` — plus une sortie de tâche "Visualize" cliquable qui deep-link dans la factory.

### Tech
L'`Estimator` porte les doubles `ocvH/ocvL`, `socIH/socIL` (bornes côté courant), `socVH/socVL` (bornes côté tension), et les comptages `ccH/ccL`. À chaque pas il appelle `countCoulomb(I, dt)` (facteur Peukert `(|I|/I_ref)^(n-1)` appliqué en décharge), `updateSOCI()` quand la charge accumulée dépasse `chargeAcceptanceAh*10`, puis `calculateNextOcvs(V, I, T=25°C)` qui soustrait la somme de trois chutes RC `vDyns[0..2]` de la tension borne pour retrouver l'OCV, applique un filtre médian, et lit le SoC dans la table OCV. La température est figée à 25°C — limitation connue que la nouvelle génération `soc` corrige. Piloté ligne par ligne par `df.apply` ; ré-échantillonnage en `cell_asset.df.resample('S').asfreq().ffill().bfill()` ; résultats renvoyés via `sendSensorDataToAssets(updateMethod=REPLACE)`.

### Status
Dernier commit 2024-10. Premier modèle SoC déployé sur Altergo ; a vécu sur des assets clients tout au long de 2024 avant d'être remplacé par `soc` (2025). Code archivé pour référence — le trafic production passe désormais par le successeur basé sur le boilerplate.

## sop

sop est le modèle State-of-Power de la plateforme jumeau numérique Altergo — sur un horizon configurable de 1 à 10 minutes, il calcule le courant maximal que le pack peut soutenir en charge et en décharge avant de buter sur une limite de tension, courant, puissance, SoC ou température. La physique est une relation Thevenin `V = OCV ± I*R` imposée au SoC de fin d'horizon, avec tables OCV(SoC,T) et R(SoC,T) en interpolation bilinéaire, ECM optionnel à 3-RC donnant `R_eff(τ) = R0 + Σ Rᵢ(1 − exp(−τ/τᵢ))` avec mise à l'échelle en SoC, température et SoH, plus les caps PCS en kW projetés en courants équivalents et des gates SoC en base coulomb ou énergie. Bâti sur le scaffold model-boilerplate, partage le dépôt avec un modèle `eq_cycles`.

### What
Émet quatre séries : `sop_continuous_discharge_kw`, `sop_continuous_charge_kw`, `sop_continuous_net_kw` (décharge positif, charge négatif), et un entier `sop_limiter_code` dont le signe et la valeur identifient quelle contrainte est active à chaque instant (±1 tension, ±2 courant matériel, ±3 puissance PCS, ±4 fenêtre SoC, ±5 thermique, ±6 table de sécurité, 0 = non borné). Les consommateurs sont des systèmes EMS et des optimiseurs de dispatch qui ont besoin de savoir "combien de kW puis-je offrir au réseau dans les 5 prochaines minutes" sans risquer de déclencher une limite. Le modèle `eq_cycles` livré dans le même dépôt est sans rapport : il intègre `|I|*dt / (2*capacity)` en cycles équivalents avec compensation optionnelle de rendement et de SoH.

### Tech
`models/sop/sop.py` est un `StateOfPowerModel(Model)` d'environ 2000 lignes. À chaque timestamp il : (1) interpole `OCV_now`, `R_now` depuis les tables bilinéaires OCV(SoC,T) et R(SoC,T), (2) exécute `iterations` (défaut 2) passes de point fixe sur `SOC_end = SOC_now ± I*τ/(3600*capacity)` pour converger vers l'OCV de fin d'horizon, (3) résout l'équation tension contraignante `V_min = OCV_end - I*R_eff(τ)` pour le courant de décharge et `V_max = OCV_end + I*R_eff(τ)` pour la charge, (4) prend le min/max contre les caps courant matériels, la série de limite courant thermique, les caps PCS en kW (convertis par `I = P/V`), et les caps de fenêtre SoC issus de gates coulomb ou énergie. La voie optionnelle `ecm_enable` construit `R_eff(τ) = R0 + Σᵢ Rᵢ*(1 − exp(−τ/τᵢ))` en 1-, 2- ou 3-RC, avec chaque `Rᵢ` mis à l'échelle par facteur SoC × facteur température × `(1 + soh_coeff*(1-SoH))`. Une table `sop_safety_enable` permet aux opérations d'appliquer un derate multiplicatif 0–1 par cellule (SoC, T). L'entrypoint fait 13 lignes : `execute_altergo_models(...)` depuis le boilerplate, comme `soc`.

### Status
Modèle en production depuis 2025. Utilisé par les consommateurs EMS / dispatch qui ont besoin de l'enveloppe d'exploitation prédite ; le code de limiteur permet aux dashboards d'expliquer *pourquoi* un pack ne peut pas délivrer plus (contrainte active exposée, pas seulement écrêtée). Dépôt dernier commit 2025-09, version 1.1.0. Le modèle co-résident `eq_cycles` est en v2.1, faible coût de calcul, utilisé pour le suivi durée de vie / garantie sur budgets de cycles équivalents.

## supplier-data-mapping

supplier-data-mapping est l'outillage qu'ION-Altergo utilise pour transformer les listes de signaux fournisseurs (CSV, Excel, JSON venus des fabricants de stockage batterie) en mappings de capteurs standardisés pour la plateforme de jumeau numérique. Les « agents » sont des runbooks markdown (`AGENT_CLASSIFIER.md`, `ADD_SENSOR_TOOL.md`) qu'un orchestrateur LLM — Cursor en pratique — suit, soutenus par des outils Python réellement exécutables : `ai_batch_processor.py` découpe les données et appelle le SDK Anthropic, `agent_io_tool.py` gère les I/O tabulaires, `add_sensor_to_catalog.py` et `check_design_compliance.py` modifient et valident le catalogue. L'état vit dans `sensor_catalog.json` et `blueprint_catalog.json` ; la doc associée fixe les classes de signaux, les conventions de nommage et la conception des modèles de capteurs, pour que humains et agents partagent une seule source de vérité. Produit interne en développement actif.

### What
Un nouveau fournisseur BESS livre une liste de signaux — SVOLT, Sunwoda, équivalents — et l'objectif est un mapping un-à-un de leurs tags bruts (avec leurs propres conventions de polarité, échelles de sévérité d'alarme, encodages) vers une hiérarchie de blueprints partagée (`ESRack`, `ESContainer`, `HVAC`, `Cooling`, `FireSafety`, etc.) afin que le jumeau numérique compare les flottes pomme à pomme. L'agent classifier lit chaque ligne fournisseur, infère la clé capteur standard et la classe de signal, propose des éditions du catalogue et écrit le `supplier_mapping.json` résultant avec ses transforms (`value * scale + offset`) et les remaps de sévérité d'alarme. Les ingénieurs pilotent l'agent depuis Cursor ; l'humain reste dans la boucle sur les changements cassants via les vérifications de conformité.

### Tech
Deux couches : runbooks markdown déclaratifs sous `agents/` que n'importe quel LLM peut suivre, et outils Python sous `tools/` et `scripts/` que le runbook invoque. `tools/ai_batch_processor.py` est délibérément agnostique au domaine — il découpe un fichier d'entrée, appelle `anthropic.Anthropic()` avec le prompt fourni par l'orchestrateur, et streame métadonnées structurées sur stdout et logs humains sur stderr. `tools/agent_io_tool.py` gère l'I/O CSV/JSON/Excel ; `scripts/add_sensor_to_catalog.py` mute `sensor_catalog.json` en place, `scripts/check_design_compliance.py` applique les règles de nommage et de blueprint, `scripts/verify_catalog_completeness.py` et `json_to_excel.py` complètent validation et export. Source de vérité : deux fichiers JSON (`sensor_catalog.json` avec son architecture hybride blueprint + group_id, `blueprint_catalog.json`) ; `docs/` codifie classes de signaux et fréquences, conventions de nommage et conception des modèles de capteurs comme référence lisible par agent.

### Status
Produit actif au 2026-01 (v0.5.0 dans le CHANGELOG), avec les mappings SVOLT et Sunwoda livrés et la phase 2 de la roadmap visant deux fournisseurs de plus, PCS et catalogues de transformateurs. Utilisé en interne par les ingénieurs d'intégration onboardant des fournisseurs ; les agents catalogent et valident, les humains revoient les PR. Dépôt GitHub privé sur l'organisation ION-Altergo.

## tsdb-benchmark

tsdb-benchmark est le dépôt de due diligence ayant comparé QuestDB, ClickHouse et TimescaleDB pour la charge d'ingestion capteur de la plateforme Altergo. Le vrai travail vit dans `benchmark/` : scripts d'ingestion par moteur (`questdb-infinite-flow-real-mono.py`, `clickhouse-batch-ingestion.py`, `timescaledb-infinite-flow-real-mono.py`) qui poussent des lignes capteur synthétiques en boucle serrée en mesurant les rows/sec, accompagnés d'un `multi_device_launcher.py` qui lance N processus d'edge devices sur des plages d'identifiants disjointes. Chaque moteur a un `docker/*.yaml` pour un démarrage en une commande, Metabase compris ; un `data_explorer_app/` façon Streamlit relit les résultats. Aucun compte-rendu de résultats dans le dépôt — le README se résume à des snippets shell et (à noter) à des tokens GitHub PAT exposés à révoquer.

### What
La forme de la charge est fixée par la plateforme : beaucoup de capteurs (cardinalité en milliers), chacun émettant une valeur numérique à la seconde ou plus vite, ingérés en continu par des edge devices et requêtés pour les dashboards. Le benchmark pilote chaque moteur candidat sur le même schéma `(sensorId, timestamp, value)`, affiche les rows/sec en glissant, et laisse l'opérateur scaler via `multi_device_launcher.py` à N processus d'écriture parallèles — chacun possédant une plage d'IDs disjointe — pour trouver où chaque moteur commence à saturer. Les vérifications côté lecture passent par le conteneur Metabase contre les tables live.

### Tech
QuestDB écrit via `questdb.ingress.Sender` avec `SYMBOL CAPACITY 131072 NOCACHE` pour `sensorId` et `PARTITION BY DAY WAL` ; ClickHouse utilise un `MergeTree` avec `ORDER BY (sensorId, timestamp)` partitionné par jour, alimenté par `clickhouse-batch-ingestion.py` via le client HTTP ; TimescaleDB utilise une variante hypertable dans le flux `timescaledb-infinite-flow-real-mono.py`. Cardinalité et taille de batch sont réglées par script (défaut 100 capteurs à 1 Hz) ; le launcher passe `START_SENSOR_ID`, `CARDINALITY`, `BATCH_SIZE` via env et redirige les logs par device dans `logs/device_N.log`. `docker/{questdb,clickhouse,timescaldedb,metabase}.yaml` donnent des stacks en une commande ; `data_explorer_app/` est un petit lecteur Python pour les résultats ; `requirements.txt` épingle les SDK.

### Status
Dernière activité septembre 2025, dépôt GitHub privé sur l'organisation ION-Altergo. Utilisé en interne pour étayer le choix de la base time-series de la plateforme Altergo ; aucun compte-rendu formel dans le dépôt. Le README laisse fuir des PAT GitHub `ghp_…` dans les URLs de clone — à révoquer.
