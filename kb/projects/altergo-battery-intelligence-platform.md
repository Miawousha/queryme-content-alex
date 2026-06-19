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
    description: Lifecycle simulator that ages a `lair` Battery under power and
      ambient profiles with a state-machine safety envelope.
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
    description: Sensor-data ingestion benchmark for the Altergo platform — sweeps
      digital-twin count, step count and sampling rate.
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
    description: Private Markdown workspace for Altergo's Adani due-diligence,
      commercial proposal, and value-delivery docs.
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
    description: BESS arbitrage MILP for day-ahead schedules plus a real-time
      deviation layer driven by RT/LMP prices.
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
    description: "BESS sizing engine: assemblies-over-components model with
      year-by-year augmentation strategy simulation."
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
    description: Reference Python models (equivalent-cycle counters) packaged for
      Altergo's digital-twin runtime.
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
    description: Multi-layer segmentation model that labels battery operating modes,
      change points, and CC/CV phases from time series.
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
    description: BESS dispatch simulator with PID power-regulation, transformer
      losses, and a Dash configurator.
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
    description: Cell/module dispersion index plus event-driven Rdc trend estimator,
      deployable on the Altergo SDK.
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
    description: Vite/React tool to inspect a battery cell-model JSON across OCV,
      impedance, thermal, aging, and safety tabs.
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
    description: Cell-level safety and stress-scoring model with 2D current
      derating, deployable on the Altergo SDK.
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
    description: Equivalent-cycle counter for a battery current trace —
      Ah-throughput divided by 2x nominal capacity.
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
    description: Altergo function-template stub wired for an equivalent-cycles
      sensor — entrypoint never computes.
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
    description: "HPPC pipeline: coulomb-counted SOC, OCV table from rest periods,
      physics-based ECM resistances at fixed time constants."
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
    description: Time-stepped solar+battery+electrolyzer hydrogen-plant simulation
      comparing a legacy battery model against the Lair multi-scale battery.
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
    description: Event-driven DC internal-resistance (Rdc) estimator with EWMA trend
      and baseline-drift percentage.
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
    description: Reference scaffold for building battery digital-twin models against
      the Altergo SDK.
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
    description: Real-Time Battery Model — physics-based BMS simulator on the
      Altergo SDK and lair battery_iq core.
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
    description: Digital-twin clone workflow — mirrors a live battery asset and
      replays its profile through the lair simulator.
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
    description: Matrix DoE framework that generates synthetic battery simulation
      datasets with controlled fault profiles.
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
    description: Teaching scaffold — Altergo function-template with a trivial
      coulomb-counting SoC class.
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
    description: Dual-bound SoC estimator — coulomb counting + OCV lookup with
      Peukert and multi-RC dynamics.
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
    description: First-generation SoC estimator (2024) — single-script coulomb + OCV
      dual-bound, superseded by soc.
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
    description: State-of-Power — max sustainable charge/discharge current over a
      1–10 min horizon, Thevenin + ECM.
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
    description: BESS signal classification toolkit — Cursor-orchestrated agents
      plus Python tools and JSON catalogs.
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
    description: Time-series DB shootout — QuestDB, ClickHouse, TimescaleDB on
      simulated edge-device sensor ingest.
    year: 2025
    last_active: 2025-09
    language: Python
    archived: false
    tags:
      - infra
      - data-only
      - python
---

Altergo is Alexandre's battery-intelligence platform: physics-based models, state estimators, simulators, and data tooling for monitoring and predicting battery-system behaviour. The repositories below are its components.

## aging_battery_lifetime_simulator

aging_battery_lifetime_simulator drives an electrochemical Battery from the internal `lair` library (Cell / Stack / ElectroChemEntity hierarchy with an attached SoH model) through a power-and-ambient-temperature profile to project how the pack ages. The main loop in `lifecycle_simulation.py` interpolates the load, runs `batteryStateMachine` to handle charge taper (5% before max SoC), 55 °C / 10 °C-hysteresis thermal cutoffs, and high/low voltage trips, then advances each element with `calculateNextStep(dt, T_amb)` on an adaptive timestep from `altergo_sdk.tools.sim.update_time_step`. Time series for SoC, SoH, calendar and cyclic aging, equivalent cycles, voltage, current and temperature are recorded via variance-thresholded `Sensor` appends, with tightened thresholds on the first and last 24 h "record days" for high-resolution boundaries.

### What

Takes a usage profile (power demand + ambient temperature time series, either uploaded as a dataset or built from a simple synthetic generator) and a battery component specification, and returns a projection of how SoC, SoH, calendar aging, cyclic aging, voltage, current and temperature evolve over the lifetime of the pack. Customers use it to validate whether a candidate cell chemistry and pack design survive a target duty cycle before procurement; the same script also produces the calibration evidence that feeds capacity-sizer warranty curves.

### Tech

Built on the internal `lair` battery library (`Battery` / `Cell` / `Stack` / `ElectroChemEntity` with pluggable `Soh` models) and the `altergo_sdk.tools.sim` module (`Sensor`, `update_time_step`). `batteryStateMachine` from `lair.components.battery_iq.clone` enforces the safety envelope — `maxSoC - 5%` charge taper, 55 °C cut-in / 45 °C cut-out thermal hysteresis, `lowVoltageSafetyCutoff` / `highVoltageSafetyCutoff` trips, current clamping. The timestep is adaptive: short during transients, long during rest. Recording uses variance-thresholded `Sensor` appends so the output stays compact for multi-year runs, with thresholds dropped to near-zero on the configured first/last "record days" so the boundary windows are fully resolved. `main.py` wraps the loop into an Altergo-platform job that reads `altergo-settings.json`, downloads the profile dataset, runs the simulation, and ships results back as Plotly graphs.

### Status

Active component of the Altergo battery-engineering toolchain in 2025; runs on the platform on demand as part of customer sizing and lifetime-validation studies. Authored as a contributor inside the ION-Altergo organisation. Not a one-off — the codebase has profile precaching, debug-mode local runs, and a profile-repetition utility for stress-testing chemistries against multi-year accelerated cycles.

## altergo_platform_etl_benchmark

altergo_platform_etl_benchmark measures end-to-end sensor-data ingestion on the Altergo platform: write-side throughput, not query/read performance. `benchmark/main.py` sweeps a grid of digital-twin counts (10 → 100), step counts (1k → 1M) and sampling intervals (1 s → 30 min), generates random time series and pushes them through `altergoClient.sendSensorDataToAssets`. Each run logs the backend's reported download / processing / ingestion times alongside the client's processing / zipping / uploading times to `benchmark_results.csv`, so total points × cardinality can be regressed against latency. No README — the script and its CSV output are the spec.

### What

Single-purpose benchmark harness for the Altergo platform's ingestion path. Sweeps a 10 × 4 × 4 grid of (digital-twin count, step count, sampling interval) configurations — 160 runs in the default driver — and for each one cleans the workspace, instantiates blueprints, instantiates digital twins, generates random sensor data, pushes it through the SDK, and records timing. The output is a flat CSV that can be plotted to see how ingestion latency scales with payload size and asset cardinality.

### Tech

Pure Python over the Altergo SDK (`altergoClient.sendSensorDataToAssets`, blueprint-template instantiation). The driver in `benchmark/main.py` uses `importlib.reload` on four staged step modules (`step_00_cleanup` → `step_03_simulate_data_and_send`) inside a nested loop, driving configurations through environment variables (`DIGITAL_TWIN_NUMBER`, `TIME_STEP_IN_MILLISECONDS`, `STEP_NUMBER`). Each run instruments both sides of the wire — backend-reported download/processing/ingestion timings (parsed from the SDK response) and client-measured processing/zipping/uploading durations — so the breakdown between client-side compression cost and server-side write cost is recoverable from the CSV alone.

### Status

One-shot platform-engineering tool from late 2024; not a long-lived product. The CSV outputs fed into capacity-planning decisions for the Altergo write path. Roughly 20 KB of code, no README, no tests — the script is the spec. Authored as a contributor inside ION-Altergo.

## altergo-strategic-docs

altergo-strategic-docs is a Markdown-only working repo for the Altergo × Adani engagement — three-workshop due-diligence plans, commercial framework versions, the strategic purchase proposal, and a value-delivery library covering usable-capacity, life-extension, availability, and O&M-cost mechanisms with a quantification framework. Also holds the platform overview (Digital Twin, Battery Intelligence, ESS/UPS) and the BESS-software RFQ response. Not deployable code; private artefacts from a client engagement.

### What
Nineteen Markdown files organised into four folders: `due-diligence/` (Adani DD
plan, extended DD with IP scope and code-access constraints, a Mermaid process
diagram, an example DD), `value-delivery/` (the four mechanism chapters and
their quantification framework), `commercial/` (proposal + v1/v2 of the
commercial framework), and `platform/` (Altergo overview, BESS RFQ response,
usable-capacity KPI framework). `INDEX.md` is the single entry point.

### Tech
Plain Markdown with one architecture diagram (`altergo_archi.png`) and
embedded Mermaid for the DD-process flow. No build, no tooling. Versioning is
via git history (`_v2` suffix on the commercial framework rather than branches).

### Status
Live 2025, last touched 2026-02. Used internally as the working artefact set
for the Adani engagement — DD workshops, commercial negotiation, RFQ response.
Private repo; not for redistribution.

## arbitrage

arbitrage optimises Battery Energy Storage System trading against day-ahead and real-time power markets. `bess_arbitrage_optimizer.py` formulates a MILP in PuLP over a 24 h horizon at 15-, 30- or 60-minute intervals with continuous charge/discharge/SOE variables, binary state variables for charging / discharging / idle / soak (exactly one active per period), an enforced ~2 h soak window above min SoC, FCE-per-day caps, SOE-dependent power limits (interpolated from arrays), round-trip efficiency, and an enforced return to initial SOE. `realtime_bess_optimizer.py` then consumes the resulting schedule and decides whether to follow, deviate, or emergency-stop based on RT vs DA price spreads, consecutive-deviation caps, FCE safety margin, transaction costs and SOE bounds. Indian DAM data loaders and EMS/SCADA schedule exporters live alongside; the bulk of the repo's 40 MB is bundled Plotly HTML.

### What

Two coupled optimisers that together let a BESS operator (a) plan a profitable next-day charge/discharge schedule against a day-ahead price curve, and (b) intelligently react when real-time prices diverge from those assumptions during the day. The day-ahead layer answers "what should the schedule look like for tomorrow?"; the real-time layer answers "given the price I'm seeing now, do I follow the plan, deviate, or stop?" Outputs include an EMS/SCADA-compatible JSON schedule, an Excel breakdown of revenue, and Plotly HTML dashboards.

### Tech

Day-ahead is a true MILP (not a continuous LP) — `pulp.LpVariable.dicts(..., cat='Binary')` over `state_charging`, `state_discharging`, `state_idle`, `state_soak` with a per-period mutual-exclusion constraint `state_charging[t] + state_discharging[t] + state_idle[t] + state_soak[t] == 1`. Battery physics live in a `@dataclass BatteryConstraints` with explicit `max_fce_per_day`, `soak_duration_hours`, `min_soak_soc`, `aux_capacity_loss_rate`, and SOE-keyed power-limit arrays interpolated via `_interpolate_power_limits`. Real-time control is a state machine with a `DeviationDecision` enum (`FOLLOW_SCHEDULE`, `DEVIATE_CHARGE`, `DEVIATE_DISCHARGE`, `DEVIATE_IDLE`, `EMERGENCY_STOP`) gated by `max_consecutive_deviations`, an FCE safety margin, and a configurable transaction cost. Indian DAM CSVs (15 min and hourly) ship with the repo for reproducibility; EMS/SCADA exporters emit the JSON schema documented in `EMS_SCHEDULE_FORMAT.md`.

### Status

Active 2025 project authored as a contributor inside ION-Altergo. The repo carries production traces — `production_schedule.json`, `production_rt_decisions.json`, `realtime_decisions_log.json` — so it has been driven on real schedules, not just notebooks. The 40 MB weight is almost entirely bundled Plotly HTML reports for sales/customer-facing scenarios (high/medium/low volatility, 15/30/60 min intervals) rather than code. Tests cover FCE constraints, soak enforcement, time-interval handling, and real-time decision logic.

## battery_capacity_sizer

battery_capacity_sizer sizes and forward-projects a BESS site from a build instruction and a load requirement. The codebase layers `assemblies/` (BESS → EnergyBlock tree → PowerConversionUnit) over `components/` (BatteryContainer, PCSUnit, Transformer, SwitchGear, MiniSoH, auxiliary consumption) over `requirements/` (load profile). `main.py` dispatches three modes: `bess_summary_generation` builds the site once and emits a nameplate / weighted-efficiency / power-stack summary checked against a `DesignRuleChecker`; `bess_augmentation_strategy` runs `BESS.simulate_time()` year-by-year under a `MaintenanceStrategy` to model SoH decay, container additions, and yearly effective-capacity targets; `bess_single_degradation` simulates a single degradation trajectory. Sizing is therefore iterative (year-stepped simulation with maintenance triggers), not a closed-form formula, and outputs include the Plotly HTML capacity, power-rating and PCU-bandwidth heatmaps used in customer-facing deliverables.

### What

Pre-sales and engineering tool that turns a "we want X MWh / Y MW for Z years with this SoH guarantee" requirement into a buildable BESS configuration plus the year-by-year augmentation plan needed to honour it. The `bess_summary_generation` mode is the quick answer ("does this configuration even satisfy the design rules?"); `bess_augmentation_strategy` is the deep answer ("how many container additions and in which years do we need to keep effective capacity above the warranty curve?"); `bess_single_degradation` produces the trajectory for a chosen strategy. Outputs feed customer-facing PDFs and dashboards.

### Tech

Three-layer object model: `assemblies/` (`BESS`, `EnergyBlock`, `PowerConversionUnit`) composes `components/` (`BatteryContainer`, `PCSUnit`, `Transformer`, `SwitchGear`, `MiniSoH`, `auxillary/`) against a `requirements/` load profile. Sizing is not a closed-form formula — `BESS.simulate_time(years)` runs an explicit year-step loop driven by a `MaintenanceStrategy` (`utils.helpers.augmentation_configuration.MaintenanceStrategy`) that decides when to add containers to keep effective capacity above the yearly target. A `DesignRuleChecker` (`utils/drc.py`) validates the build instruction against the blueprint library and stamps `input_issues` before any simulation runs. Visualisation uses Plotly heatmaps for capacity, power rating, and PCU bandwidth.

### Status

Active component of Altergo's pre-sales / engineering toolchain in 2025 (last touch September 2025). Around 600 KB of code, with a `tests/` directory, a `sandbox/`, a `CHANGELOG.md`, and an `altergo_demo_builder/` — the lifecycle of a real product, not a notebook. Authored as a contributor inside ION-Altergo. The Plotly outputs are wired into customer deliverables, so changes here ship visibly downstream.

## battery-digital-twin-models

battery-digital-twin-models is a reference Python package showing how to ship battery models for Altergo's digital-twin runtime. Two models ship today: `eq_cycles` (simple coulombic-throughput cycle count) and `adv_eq_cycles` (an LFP-tuned equivalent-cycle counter that weights throughput by sustained C-rate, temperature with a Q10 cyclic factor and low-T charge surcharge, and a smoothstep SOC stress model). Each model subclasses `Model` from the `altergo_sdk` and registers itself via `@register_model`; `entrypoint.py` is a thin wrapper that calls the SDK's `execute_altergo_models` boilerplate. Open-source so model authors can copy the pattern without seeing the SDK internals.

### What
Two pip-installable models the Altergo platform runs against asset time-series.
`eq_cycles` returns cumulative standard equivalent cycles from `current` (Ah
throughput / 2·capacity), with optional coulombic-efficiency correction and
SOH-based capacity compensation. `adv_eq_cycles` (registered as
`enhanced_equivalent_cycles`) returns `std_cycle_count`,
`equivalent_cycle_count`, and `cycle_life_fraction` — the same throughput
weighted by a clamped product of three multipliers (C-rate, temperature, SOC).
Each model directory ships its own `model.json` manifest (logical input/output
names, units, required flags) and a README; debug mode emits an HTML dashboard
of inputs, parameters, and outputs.

### Tech
`@register_model(name, metadata={category, complexity, computational_cost})`
publishes the class to a registry the SDK discovers at execution time —
authors never wire their model into a main loop. Inputs arrive as pandas
Series indexed by `DatetimeIndex`; the model owns its time-base via
`current.index.to_series().diff()`. The advanced model's smoothing is a causal
first-order EMA over irregular `dt`, the SOC stress uses cubic smoothstep
ramps near 80–96 % (LFP-dominant high-SOC penalty) and a weak 2–8 % low-SOC
penalty, temperature applies `Q10^((T-Tref)/10)` with a charge-only
plating-risk surcharge below 15 °C, and the combined multiplier is clamped to
[0.2, 3.0]. `requirements.txt` is pandas + numpy + the private `altergo_sdk`.
Configuration is layered: defaults in code, manifest in `model.json`, runtime
override in `altergo-settings.json`.

### Status
Built and deployed to Altergo customer assets in 2025; last commit 2025-09.
Open-source under the Altergo organisation as the canonical "how to write a
model" example — internal teams and integration partners copy the structure.
Two models in this repo today; the platform runs dozens more from sibling
private repos under the same pattern.

## battery_usage_analyzer

battery_usage_analyzer is the canonical home of a multi-layer segmentation model for battery time series, packaged on top of the Altergo SDK's `boiler_plate.Model` framework. Given current, SoC, and min/max cell voltage and temperature, `BatteryUsageAnalyzer.process` emits Layer 0 operating modes (charge / discharge / idle), Layer 1 data-driven change points from a composed multi-signal change score with robust z-scoring and a minimum-gap constraint, and Layer 2 domain phases (rest, CC charge, CV charge, discharge) using majority-labelled segments. The repo follows the same two-layer template as the personal `battery-digital-twin-models` repo (shared README, shared `entrypoint.py`, shared `models/` package layout) but houses a different model set — analyzer and `eq_cycles` here, vs. `eq_cycles` and `adv_eq_cycles` on the personal side — so the framework is shared, the science is not duplicated. This ION-Altergo copy is the canonical location for the usage analyzer.

### What

Turns raw battery telemetry (current, SoC, cell-level voltage and temperature extremes) into a labelled timeline — what mode the battery was in at every instant, where its behaviour changed, and which CC/CV/rest phase each segment belongs to. Downstream analytics (cycle counting, degradation models, dashboards) consume these labels rather than parsing raw signals themselves, which keeps the science centralised.

### Tech

Built on the Altergo SDK's `boiler_plate.Model` framework — `@register_model("battery_usage_analyzer")` exposes the class, `model.json` carries the manifest, and `entrypoint.py` delegates to `execute_altergo_models`. Layer 0 is rule-based on signed current and SoC delta. Layer 1 computes per-second derivatives over `current`, `soc`, `v_cell_min`/`v_cell_max`, `t_cell_min`/`t_cell_max`, EWM-smooths them, applies robust z-scoring (median/MAD) via `robust_z`, composes a multi-signal change score via `compose_change_score`, picks peaks over threshold with `detect_peaks_over_threshold`, and enforces a minimum gap via `enforce_min_gap`. Layer 2 takes Layer 1 boundaries and assigns the dominant phase per segment via `majority_label_per_segment`. The repo shares the README, `entrypoint.py`, and `models/` layout with the personal `battery-digital-twin-models` repo — a template sibling, not a fork — but each houses a distinct model set.

### Status

Canonical ION-Altergo location for the usage analyzer (the personal `battery-digital-twin-models` repo carries `eq_cycles` and `adv_eq_cycles` instead). Active in 2025 (last touch September 2025), public visibility within the ION-Altergo org. Ships with a `run_tests.py`, model-specific README, `MODEL_CREATION_GUIDE.md` documenting how to add a new model to the framework, and a `documentation/` folder. The labels it emits are consumed by other models in the Altergo battery toolchain.

## bess_control_sim

bess_control_sim is a Python simulator for the EMS control loop of a multi-container BESS site. Models a fleet of containers behind a 30 MVA IDT transformer with four LV inputs (per-input ratings, iron + copper losses, proportional redistribution when an input saturates), SoE-dependent charge and discharge C-rate curves, and a `PlantPowerPID` controller plus an optional imbalance-compensation PID. A Dash app exposes the configuration as a left panel (sim duration, containers per LV input, transformer rating, PID toggles) and renders the resulting power, SoE, and per-LV-input timeseries in Plotly. Internal sandbox for iterating on dispatch logic before it touches the production EMS.

### What
Takes in a target plant-power setpoint plus a site configuration and produces a time-resolved dispatch: instantaneous container power, SoE per container, per-LV-input loading, and transformer-side power after losses. The aim is to answer "does this control law deliver the requested AC power without overshooting any LV-input rating or violating C-rate envelopes?" before tuning gains on the real EMS.

### Tech
`bess_model.py` builds the topology (containers grouped under four LV inputs, IDT transformer with iron + copper loss model, proportional redistribution when an input saturates); `sim.py` integrates the loop step by step with `PlantPowerPID` at the plant level and an optional second PID compensating per-input imbalance; SoE-dependent charge/discharge C-rate curves clamp each container. `dash_app.py` wires a configurator (sim duration, containers per LV input, transformer rating, PID toggles) to `plotting.py` Plotly traces. Pure Python — no Altergo SDK or platform dependency.

### Status
Internal control-logic sandbox at Altergo, last active 2025-05. Used to prototype dispatch and imbalance-compensation strategies before they land in the production EMS.

## cell-imbalance

cell-imbalance is a Python repo of two battery models built on the Altergo `AltergoModelBoilerplate` so they run as deployable digital-twin jobs. `CellModuleImbalanceIndexModel` derives absolute spread in mV from cell `voltage_min`/`max` aggregates, a relative percentage against the mean, a 0–1 imbalance index scaled to a configurable alarm threshold with an exponent shaping factor, and a three-state OK/Warn/Alarm output, with optional temperature compensation that subtracts `|TCV| * ΔT` from the raw ΔV; module-level inputs are handled the same way when present. `RdcTrendEstimator` detects current steps above a threshold, computes median V and I in pre/post windows around each step, derives an event-level DC internal resistance `|ΔV|/|ΔI|`, optionally MAD-filters outliers, then tracks an EWMA trend versus a baseline.

### What
Inputs come from a live BMS digital twin — per-cell and per-module voltage min/max/mean aggregates, pack current, and optionally cell temperatures. Outputs are three streams an operator can alert and trend on: a dispersion index plus OK/Warn/Alarm state for cells and modules (catches drifting weak cells before they trip), and an event-driven Rdc trend versus baseline with a percent drift readout (catches creeping resistance growth indicative of aging or contact degradation).

### Tech
`models/cell_imbalance/cell_imbalance.py` computes ΔV from voltage_min/voltage_max, normalises to a 0–1 index scaled by `alarm_threshold_mv` with a shaping exponent, applies optional `|TCV| * ΔT` temperature compensation, and mirrors the same pipeline at module granularity. `models/rdc_trend_estimator/rdc_trend_estimator.py` scans the current trace for steps above a configurable threshold, takes median V and I in pre- and post-step windows separated by a guard band, divides to get an event-level DC resistance, MAD-filters outliers, then maintains an EWMA against a baseline and reports a baseline-drift percentage. Both inherit `AltergoModelBoilerplate`; `entrypoint_simple.py` and `entrypoint_advanced.py` register them for SDK deployment.

### Status
Internal Altergo digital-twin model repo, last active 2025-10. Deployed against live BESS assets to surface cell-spread alarms and Rdc-aging trends to operations.

## cell-model-visualizer

cell-model-visualizer is an internal Vite + React 19 app for inspecting a battery cell-model JSON file. Users load a cell into a localStorage-backed library, then flip between Overview / OCV Curves / Impedance / Thermal / Aging / Safety tabs — each rendering Plotly views over the same dataset (manufacturer, model, version, last-updated, characterisation curves). Drag-and-drop import via `FileHandler`; MUI for chrome. Companion tool for cell-modelling work at Altergo; not public.

### What
Seven tabs in a single MUI `AppBar` + `Tabs` shell. **Library** lists cells the
user has imported (with a default demo LiFePO4 32700) and switches the active
cell on click. **Overview** prints physical / electrical / thermal spec sheets
from the JSON. **OCV Curves**, **Impedance**, **Thermal**, **Aging**, and
**Safety** render Plotly views over the characterisation arrays in the JSON
(SOC-OCV tables, EIS spectra, thermal coefficients, aging-model parameters,
safety envelope). The header keeps the active cell's version and last-updated
visible. The JSON is a large nested schema with `physical_properties`,
`electrical_specifications`, voltage range, current ratings, etc. — what
Altergo's modelling team produces from a calibration run.

### Tech
Vite + React 19 + MUI + Plotly. No backend. State lives in two
`localStorage` keys — `cellModelVisualizer_importedCells` (the library) and
`cellModelVisualizer_currentCell` (the active dataset) — so a refresh keeps
your work, but nothing leaves the machine. `FileHandler` accepts drag-and-drop
JSON and routes it through `handleDataImport`, which dedupes by
manufacturer+model. The library design lets engineers compare cells without a
server.

### Status
Built 2025 alongside Altergo's cell-modelling work; last commit 2025-09. Used
internally to sanity-check calibration outputs and to demo what a cell model
"looks like" to non-modelling stakeholders. Private; one shipped demo cell
plus whatever the user imports.

## cellsos

cellsos is a Python `CellLimitsModel` built on the Altergo `AltergoModelBoilerplate`, monitoring lithium cell voltage, temperature, and current against their safe operating limits. Dynamic charge and discharge current limits are interpolated from a 2D temperature × SOC derating lookup (`current_limits_table.json`) via `scipy.RegularGridInterpolator`; outputs include per-parameter safety margins, a combined minimum margin, an instantaneous 0–100 % stress score, time-integrated cumulative stress, and an overall OK/Warning/Critical safety status. Internal model repo wired through the SDK to deploy against live digital-twin assets.

### What
Consumes live cell-level telemetry (V, T, I) from a digital-twin asset along with the cell's safe-operating envelope and a 2D temperature × SOC derating table. Emits a continuous stream of safety signals an operator can alert on and a stress score the analytics layer can integrate over time: how close each parameter sits to its limit, where the combined margin is tightest, how stressed the cell is right now, and how much accumulated stress it has taken on so far.

### Tech
`models/cell_limits/cell_limits.py` holds the single `CellLimitsModel`. Dynamic charge and discharge current ceilings come from `current_limits_table.json` interpolated with `scipy.interpolate.RegularGridInterpolator` over temperature and SOC. Per-parameter margins are normalised to their distance from the limit; the combined safety margin is the minimum across V/T/I; the stress score maps 0 % (deep inside the envelope) to 100 % (at the limit), then accumulates over time for the cumulative stress output. Tri-state OK/Warning/Critical falls out of configurable margin thresholds. `entrypoint_simple.py` and `entrypoint_advanced.py` register the model for SDK deployment.

### Status
Internal Altergo digital-twin model, last active 2025-11. Deployed via the SDK against live cell assets to feed safety dashboards and aging analytics.

## demo-eq-cycle-model

demo-eq-cycle-model is a small Python demo that computes cumulative equivalent cycles from a battery current time series: `eqCycles = cumsum(|I|·dt) / (2·Cnom)`. The estimator lives in `tools/eq_cycle_estimator.py`; `main.py` loads a sample CSV, runs it against a 56 Ah nominal capacity, and plots eqCycles alongside voltage with Plotly. Standalone demo of the equivalent-cycle formula — not platform-deployed, no Altergo SDK calls.

### What
The estimator takes a DataFrame indexed by timestamp with a `Current` column, computes `time_diff` in hours from consecutive index values, multiplies by `|Current|` to get per-step Ah throughput, divides by `2·Cnom` to convert Ah into equivalent full cycles, and returns the cumulative sum. The included `someCycleData.csv` is a single hard-coded cell trace; running `main.py` opens an interactive Plotly chart with eqCycles on the left axis and Voltage on the right.

### Tech
Pure pandas + numpy + Plotly — 2.8 kB of code total. No Altergo SDK, no configuration file, no entrypoint scaffold. The convention `Ah / (2·Cnom)` (half-cycle counting both directions) matches the formula used in `effective-capacity-benchmark-model` and `hppc_analysis` downstream.

### Status
Teaching example showing the eqCycles formula in isolation, written 2025 alongside the larger battery-digital-twin work. Not deployed, not maintained as a product; used as a reference snippet when explaining cycle counting to other engineers or stakeholders.

## effective-capacity-benchmark-model

effective-capacity-benchmark-model is an Altergo function-template scaffold: `entrypoint.py` extracts platform arguments, initializes the SDK client, and fetches the asset by ID — then stops. The `altergo-settings.json` declares it as a "Performance" model reading a `Current` sensor + `Capacity` parameter and writing an `Equivalent Cycles` output, but the actual benchmark logic is missing. Placeholder / unfinished scaffold despite the name.

### What
The repo name suggests an effective-capacity benchmark (measured Ah vs nominal as a SOH indicator), but the declared I/O is equivalent cycles, not capacity. The mismatch and the empty body together signal this is a scaffold that was filed under a working title and never finished. As-is, running it does nothing useful: it just authenticates against Altergo and pulls an asset reference.

### Tech
Uses `extract_altergo_parameters()` and `Client(functionArguments=altergoArguments)` from `altergo_sdk` to handle credentials, factory/IoT API URLs, and the `assetId` injected by the platform at execution time. The `altergo-settings.json` schema follows the older single-model `bp_sensors` / `bp_parameters` style (pre-dating the multi-model `enabled_models` registry used in the `impedance` repo). 1 kB of Python, three imports, no computation.

### Status
Created 2024, untouched since. Predates the boilerplate-based pattern (`AltergoModelBoilerplate`) that the `impedance` repo standardized on. Effectively dead code in the ION-Altergo org — either to be repurposed as a real effective-capacity model or deleted.

## hppc_analysis

hppc_analysis is a single-file (~2 kLOC) HPPC pipeline that fits NMC cells from raw Altergo SDK pulls into a ready-to-use battery configuration. `hppc_analysis_full.py` segments each cycle around the discharge→charge current reversal, integrates current with `scipy.signal.savgol_filter`-smoothed coulomb counting to get SOC, extracts OCV from ≥25-minute rest periods, and computes R0/R1/R2 directly from voltage deltas at V_before / V_2s / V_5min / V_end with τ₁=5 min and τ₂=25 min fixed (no curve fit). Outputs an OCV CSV, ECM-parameter CSV, cycle summary, interactive HTML report, and `battery_config_from_analysis.json` consumed downstream by simulation code; the 48 MB repo size is almost entirely those bundled Plotly HTML reports.

### What
Input is one NMC cell (asset `NMC_CELL_1_CUSTOM_617` on `demo.altergo.io`) over a ~10-day HPPC test, pulled via `altergoClient.getAssetSensorData` for `Cycle_Number`, `Voltage`, `Current`, `Temperature`. The convention is that each cycle starts and ends at 100% SOC and hits 0% at the discharge→charge current reversal, so coulomb counting can be anchored cycle-by-cycle without drift accumulation. OCV points are only accepted when the rest-period voltage standard deviation is below 10 mV, and ECM fits are filtered for physical plausibility (1–100 mΩ for R0, 0.1–50 mΩ for R1/R2). The exported `battery_config_from_analysis.json` is the contract consumed by Lair-based simulators (cf. the `hydrogen` repo's BatteryArchitectureBuilder workflow).

### Tech
Single 74 kB script, ~2 kLOC, organized as a procedural pipeline: `load_full_dataset` → `identify_hppc_cycles` → per-cycle `calculate_proper_soc_for_cycle` + `find_rest_periods` + `extract_ocv_points` + `identify_pulses` → `fit_ecm_to_pulse` → `create_comprehensive_ocv_table` (21 SOC bins, ±5% window) → `generate_battery_config`. Stack: numpy, pandas, scipy (`savgol_filter` window 51, polyorder 3; `interp1d`; `curve_fit` imported but unused for R0/R1/R2), plotly subplots for the HTML report, altergo-sdk for data fetch. The repo carries an `archive_development_files/` and `archive_removed_files/` tree plus bundled HTML reports — code itself is small, but the artifacts blow the size to 48 MB.

### Status
Built 2025 against real NMC cell data on the Altergo demo tenant. Used as an offline pre-processing step: run once to characterize a cell, drop the JSON into Lair-based simulations. Not a deployed Altergo model (no `altergo-settings.json`, no boilerplate) — a standalone data-only analysis. Output JSON is the integration surface; everything else (CSVs, HTML) is for human review.

## hydrogen

hydrogen is a Python simulation of a solar-coupled green-hydrogen plant: a `HydrogenPlantSimulation` time-steps a `SolarPlant`, `Electrolyzer` (ramp limits, activation/deactivation thresholds, kg-H₂/kWh efficiency), `Battery`, static aux loads, and an `EMS` dispatcher row-by-row over a power or irradiance profile. `main.py` runs in three modes — `-legacy` (simple Battery class), `-lair` (a `BatteryArchitectureBuilder` built from a real Altergo blueprint, cell/module/stack-resolved), or `-both` for side-by-side comparison — with the PV stage optionally driven by `pvmodel.new_pv_power_generation` against CEC module/inverter databases pulled from Altergo. R&D tool for cross-checking the legacy lumped battery model against Lair's electrochemical-aware battery on identical solar+H₂ scenarios.

### What
Input is a CSV dataset (referenced by `power_profile_dataset_id` in the platform config) — either a precomputed power profile or raw irradiance/weather that gets converted to power via `run_pv_simulation` against CEC module + inverter databases. The plant model wires SolarPlant + Electrolyzer + Battery + AirCooledCondenser + two StaticLoads (`auxPlantLoads`, electrolyzer minimum aux) through an EMS dispatcher; for each timestep, EMS decides what flows where given electrolyzer ramp constraints, activation/deactivation thresholds, and battery state. Outputs a `simulationDf` of all per-step variables, a KPIs array, and optionally a static HTML simulation page; when `UPLOAD = True`, results are pushed back into Altergo as a fresh asset with dashboards. The Lair path runs an electrochemically-resolved battery (cell → module → stack), the legacy path a simple SOC-based Battery — the `-both` mode runs them on identical inputs so the two SOC/voltage trajectories can be diffed.

### Tech
Core sits in `balanced_simulation/`: `SolarPlant.py`, `Electrolyzer.py` (ramp limits, activation/deactivation, base + fractional H₂-production efficiency, kg-H₂/kWh conversion), `Battery.py` (legacy lumped), `EMS.py`, `EnergySystem.py`, and `HydrogenPlanSimulation.py` which composes them. The Lair branch uses `lair.components.battery_iq.battery_architecture_builder.BatteryArchitectureBuilder` against a "Test Battery" blueprint fetched from Altergo, yielding a `Battery` of `Cell` / `ElectroChemEntity` resolved at `LEVEL_MODULE` / `LEVEL_STACK`. PV modeling lives in `pvmodel/new_pv_power_generation.py`, driven by CEC module and inverter datasets pulled as Altergo dataset download URLs. `pyinstrument` is wired (commented out) for profiling Lair runs because the cell-resolved model is much slower than legacy. Parallel subdirs `demo_simulation/`, `realtime_h2_model/`, and `pvmodel/` contain related variants and a deployable real-time entrypoint.

### Status
Built 2024–2025, last active 2025-03. R&D / validation tool — not a customer-facing model. Used to validate Lair's multi-scale battery on a representative solar+H₂ scenario before publishing it for client deployments; the legacy/lair comparison is the headline check. 356 kB of Python; `UPLOAD` is gated false by default so the script runs cleanly offline against a real Altergo blueprint without polluting platform data.

## impedance

impedance is a battery-health model that estimates DC internal resistance from current-step events — not an EIS spectrum fitter, despite the repo name. `RdcTrendEstimator` in `models/rdc_trend_estimator/` detects raw current jumps above `di_threshold_abs`, takes median V and I in pre/post windows with a guard band around each step, computes `Rdc = |ΔV|/|ΔI|`, rejects MAD-based outliers, and emits a per-event Rdc series plus an EWMA trend and percent-change versus a configurable baseline. Built on the Altergo model boilerplate (`AltergoModelBoilerplate` driving the entrypoint), so the model deploys against live digital-twin assets with the SDK plumbing handled by the framework.

### What
Inputs are aligned UTC-indexed pandas Series for `current` (A) and `voltage` (V), plus optional `temperature` (C) and a scalar `baseline_rdc` (Ω). The validator refuses anything misaligned, non-monotonic, or empty — no implicit resampling. Detection uses raw first-difference (`cur.diff().abs() >= di_threshold_abs`, default 10 A); for each step at `t*`, pre/post medians come from `[t*-guard-pre, t*-guard)` and `[t*+guard, t*+guard+post)` (defaults 60 s / 60 s / 60 s), giving `Rdc_event = |ΔV| / |ΔI|`. Outputs three series at event timestamps: raw `rdc`, `rdc_trend` (EWMA over `ewma_span_events`, default 10), and `rdc_change_pct` versus baseline (seeded from the first `baseline_first_n` events or from a config-provided scalar). MAD-based robust z-score (`outlier_sigma`, default 3.0) drops outliers when `drop_outliers` is on.

### Tech
Subclasses `altergo_sdk.boiler_plate.Model`, declared in `models/rdc_trend_estimator/model.json` (logical I/O) and wired in `altergo-settings.json` (platform sensor names: `Current` / `Maximum Voltage` / `Temperature` → `RDC Trend/DC Internal Resistance` + `RDC Trend/Rdc Trend` + `RDC Trend/Rdc Change %`). The repo ships a multi-model registry (`enabled_models = "eq_cycles,adv_eq_cycles,soc_eq_cycles,rainflow_cycles,rdc_trend_estimator"`), but only `rdc_trend_estimator` is implemented here. Two entrypoints — `entrypoint_simple.py` calls `boilerplate.execute()` once for the auto path, `entrypoint_advanced.py` exposes the four phases (prepare → execute → debug → upload) for custom pre/post-processing. Config defaults live in `model.json`; `compute_type` supports `incremental` / `full` / `manual` with `max_days_period_compute` to cap each run.

### Status
Active 2025, last touched October. Production-grade model — deploys against live Altergo battery digital twins, computes Rdc trends incrementally, optionally uploads to platform dashboards. The boilerplate pattern here (`AltergoModelBoilerplate` driving everything) is the modern Altergo model template; the `effective-capacity-benchmark-model` repo is an older single-model scaffold that didn't make it to this generation.

## model_boilerplate

model_boilerplate is the canonical Python scaffold for building battery digital-twin models on the Altergo platform. Wraps the Altergo SDK's `AltergoModelBoilerplate` lifecycle (prepare data, execute, debug dashboards, upload output) into a `entrypoint_simple.py` / `entrypoint_advanced.py` pair, with a `models/` registry pattern (decorator-registered classes plus per-model `model.json` manifest) and four worked examples — `eq_cycles`, `adv_eq_cycles`, `soc_eq_cycles`, `rainflow_cycles`. Internal foundation that new models (SoC, SoH, impedance, cell imbalance, etc.) fork instead of recreating SDK plumbing.

### What
Inputs are an Altergo asset plus a JSON-declared list of sensor series (current, voltage, temperature, SoC); outputs are new sensor time series uploaded back to the same asset. `altergo-settings.json` selects which models run (`enabled_models`), how data is fetched (`compute_type`, `max_days_period_compute`), and whether to render debug Plotly dashboards or push results. Consumed by Altergo workers in production and by model authors locally via `dev-parameters.json` credentials.

### Tech
`entrypoint_simple.py` is one-liner: `AltergoModelBoilerplate(extract_altergo_parameters()).execute()`. `entrypoint_advanced.py` splits the lifecycle into `prepare_models_data` / `execute_models` / `show_debug_dashboards` / `upload_models_output` so authors can inject custom inputs between phases. Each model under `models/<name>/` subclasses `altergo_sdk.boiler_plate.Model`, registers with `@register_model(name, metadata=...)`, declares its I/O contract in `model.json`, and implements `process(data) -> dict`. The four shipped examples cover equivalent-cycle counters and a rainflow cycle counter — concrete references for new contributors. Tests live under each model's `tests/` folder.

### Status
Active reference scaffold across the ION-Altergo battery model fleet as of 2025-12. Maintained by the platform team; individual model repos (rtbm, custom client models) all fork this layout. Contributor role — Alexandre extended example models and the registry pattern while building rtbm and the dataset generator on top.

## rtbm

rtbm (Real-Time Battery Model) is an Altergo-registered model that simulates a battery system step-by-step from input series of power, current, temperature, and SoC. `models/rtbm/rtbm.py` builds Battery/Cell/Stack objects from a `simspec.json` using `lair.components.battery_iq`, runs `batteryStateMachine` transitions with safety checks and cooling logic, and returns voltage, temperature, current, SoC, and power as pandas Series. `entrypoint.py` pulls the asset from Altergo, derives the simspec via `BatteryArchitectureBuilder`, and delegates execution to `altergo_sdk.boiler_plate.execute_altergo_models`.

### What
Inputs: four time series on an Altergo asset — `power`, `current`, `temperature`, `soc`. Outputs: five simulated series — `voltage`, `temperature`, `current`, `soc`, `power` — uploaded back as digital-twin sensors on the same asset. The model exists so the platform can produce expected-vs-actual diagnostics on real battery fleets: deviation between measured and simulated voltage/SoC flags degradation, anomalies, or sensor faults. Consumed by Altergo workers; one execution per asset per scheduled window.

### Tech
`Rtbm` subclasses the SDK `Model` base class and registers via `@register_model("rtbm", metadata={category: "Performance", complexity: "Simple", computational_cost: "Low"})`. The simulation loop comes from `lair.components.battery_iq.clone.batteryStateMachine` — adaptive time-stepping driven by `update_time_step`, cooling logic, thermal safety cutoffs, depth-1 sim mode (`SIM_TARGETED_DEPTH = 1`, stack-level granularity). `BatteryArchitectureBuilder` walks the asset's blueprint hierarchy to build the lair `Battery` of `Stack`s of `Cell`s and emit a `simspec.json`. Output sensors are aggregated via `dataframeFromSensors`. Plotly debug dashboards available when `debug_mode` is on.

### Status
Active in 2025 as the canonical starting point for new battery models on Altergo — newer client-specific models (impedance, SoH, cell imbalance) fork this layout. Last active 2025-09. Contributor role — Alexandre owns the rtbm model code and the entrypoint wiring; the platform team maintains the underlying SDK and lair.

## rtbm-clone

rtbm-clone is the Altergo function that maintains a digital-twin "clone" asset for a real battery. `main.py` fetches the source asset via the Altergo SDK, builds its lair `Battery` model with `BatteryArchitectureBuilder`, gets-or-creates a paired clone asset, pulls and interpolates the source's recent power/temperature/SoC datasets, and runs `rtbm_clone.sim_setup.run_sim` against the lair simulation engine (`GlobalSettings` / `ScenarioSettings` / `SimulationStepSettings`) before writing simulated stack and battery sensors back through `process_simulation_results`. Not a copy of the boilerplate — a distinct production workflow.

### What
Input is one live battery asset on Altergo with measured Current/Voltage/SoC/Temperature/Power/Ambient Temperature sensors over a recent window (default 24h before now). Output is a separate `RTBM-<source-sn>-DEMO` clone asset, freshly created or wiped per run, populated with simulated per-stack Voltage/Temperature plus aggregate battery sensors. The workflow exists so the platform can publish a "perfect twin" alongside the real one — anything the real asset does, the clone replays through physics, and downstream diagnostics compare them.

### Tech
`get_or_create_clone_asset` handles asset lifecycle: matches by serial number, optionally erases data or deletes-and-recreates assets-with-children, then assembles stacks from the source blueprint's `Stacks` interface. `prepare_simulation_data` fetches sensors with `getAssetSensorData`, forward-fills, and runs through `interpolateValue`. Sim runtime config comes from `configurationValues.globalSettings` / `simulationSteps` / `runTimeSettings` mapped to lair `GlobalSettings` / `SimulationStepSettings` / `ScenarioSettings` by `lair_override.py`. `sim_setup.run_sim` drives `lair.components.battery_iq.clone.run_clone_simulation`. `simulation_output.process_simulation_results` splits the multi-stack output dataframe (`Voltage|0`, `Temperature|0`, ...) per child asset and pushes via `dataUpdateMethod`.

### Status
Production workflow shipped as an Altergo function in 2024, demoed against the Rikuti (`RK-WIT-001`) asset. Last active 2024-10; predates the model-boilerplate registry pattern. Contributor role — Alexandre owns `sim_setup.py`, `simulation_output.py`, `lair_override.py` and the asset-lifecycle handling. Architectural reference for later one-asset-per-fault workflows like rtbm-dataset-generator.

## rtbm_dataset_generator

rtbm_dataset_generator is a matrix Design-of-Experiment framework for synthesizing battery training datasets. `main_matrix.py` walks the cross-product of power profiles × failure scenarios (one asset per profile-fault combination, plus baselines), loads-and-extends each CSV profile to a target duration, builds the lair `Battery` from a simspec via `BatteryArchitectureBuilder`, runs the simulation through `batteryStateMachine` with `check_and_apply_anomalies` injecting controlled faults (e.g. impedance spikes), and writes per-asset parquet + JSON datasets plus a DoE summary. Built on `altergo_sdk` and `lair.components.battery_iq`; powers training data for the real-time battery model.

### What
Driven by `doe.json`: a list of power profiles (CSV files indexed by timestamp), battery specifications (simspec paths, blueprint names), simulation cutoffs, initial conditions (SoC/SoH/temperature ranges with distributions), thermal parameters, and failure definitions (impedance_spike_early/mid, random_impedance_degradation, plus a no-failure baseline). Total assets = profiles × faults × multiplier. For each combo it produces `datasets/asset_<profile>_<fault>_NNN_data.csv` (sensor + `anomaly_status` column), a JSON metadata file, raw timeseries, and a global `doe_matrix_summary.json` — plus interactive Plotly HTML plots highlighting anomalous periods.

### Tech
The simulation loop is a while-loop with adaptive `update_time_step`, matching the rtbm-clone reference. `utils/anomaly_utils.check_and_apply_anomalies` patches battery state mid-run to inject impedance spikes or stochastic degradation; `utils/doe_config.DoEConfiguration` parses `doe.json` and expands the matrix; `utils/simspec_generator` and `altergo_sdk.utils.blueprints.simspec` (`parse_simspec`, `calculate_cascade`, `extend_from_simspec`) build the battery model from datasheet JSON without needing a live asset. `utils/dataset_generator` writes per-asset and summary files; `utils/asset_service.AssetService` optionally uploads synthesized assets back to Altergo. Sensor capture uses `Sensor` / `dataframeFromSensors` with `significantAppend` to keep file sizes bounded. Reproducible via configurable `random_seed`.

### Status
Active 2026-01, the largest of the five repos (~170 kB code). Generates training corpora for the platform's ML models — degradation, anomaly detection, future SoH variants — by producing labelled fault-vs-baseline pairs that would otherwise require months of field data. Contributor role — Alexandre is the primary author of the matrix DoE design, the anomaly injection layer, and the dataset writer.

## simple_soc_model

simple_soc_model is the Altergo function-template scaffold with a placeholder SoC algorithm — `my_soc.py` is a 10-line class that decrements SoC by `current * dt / capacity * 100` (basic coulomb counting, no OCV, no temperature, no error bounds). `entrypoint.py` wires it into the SDK, writes a `hello.txt`, and registers a task output. Teaching example for the function-template structure, not a real estimator.

### What
Walks a developer through what an Altergo "model"-flavoured function looks like end to end: SDK client init, `assetId` and `programTaskId` lookup, parameter extraction, a trivial algorithm class, side-effect output, and registering a "Visualize C-Rate" task result so the platform UI gets a clickable link back to the asset's data. Two empty siblings (`my_model.py`, `model-validation.json`) sit alongside as slots a real model would fill.

### Tech
`my_soc.py` is a `SOC(capacity, SOC)` class with one `update_SOC(current, dt)` method — `delta_SOC = current*dt/capacity*100; SOC -= delta_SOC; clamp at 0`. No upper clamp, no temperature, no OCV correction, no charge-direction handling. `entrypoint.py` builds the SDK client from `apiKey`/`factoryApi`/`iotApi`, writes `hello.txt`, fetches the task by id, sets `task.output = [{name, icon, description, url}]` pointing at `/assets`, and calls `updateTask`. README is the template's "how to use this template" instructions.

### Status
Last touched 2024-10. Used as the canonical teaching example for new platform developers — paired with `simple-app` to show both function flavours. Not deployed; the real SoC implementation moved to `soc-model` (2024) and then `soc` (2025).

## soc

soc is the current State-of-Charge estimator for the Altergo digital-twin platform — a dual-bound algorithm that runs coulomb counting and OCV-table lookup in parallel and merges them, with asymmetric error margins so each step emits SoC plus an uncertainty band. Built on the model-boilerplate scaffold (`register_model("soc")`); the core handles Peukert compensation on discharge, multi-RC dynamic voltage with temperature-compensated time constants, median + low-pass OCV filtering, directional constraints, rest detection, and SoH-scaled effective capacity. Supersedes `soc-model` (2024); ships a historical-SoC variant for iterative backfit on past data alongside the realtime estimator.

### What
The realtime `soc` model consumes `voltage`/`current`/`temperature` time series plus a `battery_config` blob (OCV(SoC,T) table, RC values, Peukert exponent) and an optional `soh` series; it emits a primary `soc`, an uncertainty width `soc_bounds`, the back-computed `ocv_estimated`, and four debug bounds (`soc_coulomb_high/low`, `soc_ocv_high/low`). The `historical_soc` variant in the same repo solves a different problem: detect high-quality rest "anchors" (`|I|` small and `|dV/dt|` small for ≥N minutes), map each anchor's voltage to a SoC via lab-validated OCV curves, then fit the effective capacity between consecutive anchors so coulomb counting hits both anchor SoCs exactly — RANSAC fuses anchor-pair capacities into a continuous `C_eff(t)` and SoH series, with the explicit rule that OCV curves come from lab data, never field-learned, to avoid circular drift.

### Tech
Two models share the repo: `models/soc/soc.py` (`SOCEstimator(Model)`, ~1500 lines) and `models/historical_soc/historical_soc.py` (`HistoricalSOCEstimator`, anchor-based with `sklearn.linear_model.RANSACRegressor`). The realtime estimator keeps separate high/low coulomb counters with asymmetric current errors (`I*(1±rel_err) ± abs_err`), applies Peukert only when `|I|` exceeds a rest threshold, runs an RC stack `V_terminal = OCV - R0*I - Σ V_RCᵢ` where each `V_RCᵢ` decays as `exp(-Δt/τᵢ)` recomputed per timestep, median-filters the back-computed OCV with a 16-sample window, then low-pass-filters and looks up SoC in a bilinear OCV(SoC,T) table with charge/discharge hysteresis selection. Updates are gated: continuous coulomb counting, full SoC recompute only when accumulated charge crosses `soc_update_threshold` (0.1% of capacity) or `max_soc_update_interval` (60 s) elapses or rest is detected (`|I| < 0.05 A` for ≥30 min). Configuration falls back from blueprint params `BP/OCV_LookupTable` / `BP/Cell_Config` to local `battery_config.json`. The entrypoint is a 45-line shell that just calls `execute_altergo_models(altergo_arguments)` from `altergo_sdk.boiler_plate` — all platform plumbing (input lookup, output decimation, error reporting) is centralized in the SDK.

### Status
Production model since 2025; current version 1.0 on the platform. Lives in `/models/soc/` (realtime, OCV-based recalibration) and `/models/historical_soc/` (offline anchor-fit with three variants: `historical_soc.py`, `_iterative.py`, `_simple.py`). Repo carries ~230 kB of code plus calibration datasets, debug scripts (`debug_anchors.py`, `debug_historical_soc.py`, `debug_iterative_fitting.py`), self-discharge test outputs (`self_discharge_factors.png`), and a `model_creation_guide.md`. Quoted accuracy ±2–5% SoC under normal conditions, with `soc_bounds` exposing real-time confidence to downstream consumers. Last commit 2025-10.

## soc-model

soc-model is the 2024 first-generation State-of-Charge estimator for the Altergo platform — a single `Estimator` class (`estimator/soc_estimator.py`) doing the same coulomb-counting plus OCV-lookup dual-bound idea, with Peukert on discharge, RC dynamic voltage, and median-filtered OCV. The entrypoint pulls voltage/current/temperature from an activity window via the Altergo SDK, resamples to 1 Hz, runs the estimator row by row, and writes back `SoC`, `SoC Voltage High`, and `SoC Voltage Low`. Superseded by `soc` (2025), which migrated to the model-boilerplate scaffold and added temperature-compensated tau, SoH scaling, and directional OCV constraints.

### What
Batch backfit job: given a cell asset and a named activity window, compute SoC over that window and write it back as new sensor series so the platform UI can plot it next to measured voltage/current. Reads `bp_sensors` (voltage / current / temperature names), `bp_parameters` (cell capacity), and a `bp_datasets` cell-model JSON (OCV table, RC values, Peukert exponent) from the blueprint; emits five series — `[Altergo] SoC`, `SoC Current High/Low`, `SoC Voltage High/Low` — plus a clickable "Visualize" task output deep-linking into the factory UI.

### Tech
The `Estimator` carries dual `ocvH/ocvL`, `socIH/socIL` (current-based bounds), `socVH/socVL` (voltage-based bounds), and `ccH/ccL` coulomb counts. Per step it calls `countCoulomb(I, dt)` (Peukert factor `(|I|/I_ref)^(n-1)` applied on discharge), `updateSOCI()` when accumulated charge passes `chargeAcceptanceAh*10`, then `calculateNextOcvs(V, I, T=25°C)` which subtracts a sum of three RC voltage drops `vDyns[0..2]` from terminal V to back out OCV, runs a median filter, and reads SoC from the OCV table. Temperature is hardcoded to 25°C — a known limitation the next-gen `soc` fixes. Driven row-by-row via `df.apply`; resampling is `cell_asset.df.resample('S').asfreq().ffill().bfill()`; results pushed back with `sendSensorDataToAssets(updateMethod=REPLACE)`.

### Status
Last touched 2024-10. Was the first SoC model deployed on Altergo; lived on customer assets through 2024 before being replaced by `soc` (2025). Code archived for reference — current production traffic goes through the boilerplate-based successor.

## sop

sop is the State-of-Power model on the Altergo digital-twin platform — over a configurable 1–10 minute horizon, it computes the maximum current the pack can sustain in charge and discharge before hitting a voltage, current, power, SoC, or thermal limit. The physics is a Thevenin terminal relation `V = OCV ± I*R` enforced at end-of-horizon SoC, with bilinear OCV(SoC,T) and R(SoC,T) lookup tables, optional 3-RC ECM giving `R_eff(τ) = R0 + Σ Rᵢ(1 − exp(−τ/τᵢ))` with SoC/temperature/SoH-dependent scaling, plus PCS kW caps mapped to equivalent currents and coulomb- or energy-based SoC-window gates. Built on the model-boilerplate scaffold, alongside an `eq_cycles` model in the same repo.

### What
Outputs four time series: `sop_continuous_discharge_kw`, `sop_continuous_charge_kw`, `sop_continuous_net_kw` (discharge positive, charge negative), and an integer `sop_limiter_code` whose sign and value identify which constraint binds at each instant (±1 voltage, ±2 hardware current, ±3 PCS power, ±4 SoC window, ±5 thermal, ±6 safety table, 0 = unbounded). Consumers are energy-management systems and dispatch optimisers that need to know "what's the most kW I can offer to the grid for the next 5 minutes" without risking a limit trip. The `eq_cycles` model shipped in the same repo is unrelated: it integrates `|I|*dt / (2*capacity)` into equivalent full-cycle counts with optional efficiency and SoH compensation.

### Tech
`models/sop/sop.py` is a `StateOfPowerModel(Model)` ~2000 lines. For each timestamp it: (1) interpolates `OCV_now`, `R_now` from the bilinear OCV(SoC,T) and R(SoC,T) tables, (2) runs `iterations` (default 2) fixed-point passes on `SOC_end = SOC_now ± I*τ/(3600*capacity)` to converge end-of-horizon OCV, (3) solves the binding voltage equation `V_min = OCV_end - I*R_eff(τ)` for discharge current and `V_max = OCV_end + I*R_eff(τ)` for charge, (4) takes the min/max against hardware current caps, thermal current limit series, PCS kW caps (converted via `I = P/V`), and SoC-window caps from coulomb or energy gates. The optional `ecm_enable` path builds `R_eff(τ) = R0 + Σᵢ Rᵢ*(1 − exp(−τ/τᵢ))` for 1-, 2-, or 3-RC, with each `Rᵢ` scaled by SoC factor × temperature factor × `(1 + soh_coeff*(1-SoH))`. A `sop_safety_enable` table lets ops apply a multiplicative 0–1 derate per (SoC, T) cell. Entrypoint is 13 lines: `execute_altergo_models(...)` from the boilerplate, same as `soc`.

### Status
Production model since 2025. Used by EMS / dispatch consumers that need predicted operating envelope; the limiter code is what lets dashboards explain *why* a pack can't deliver more (binding constraint surfaced, not just clipped). Repo last touched 2025-09, version 1.1.0. Co-resident `eq_cycles` model is v2.1, low computational cost, used for lifetime / warranty tracking against equivalent full-cycle budgets.

## supplier-data-mapping

supplier-data-mapping is the toolkit ION-Altergo uses to turn supplier signal lists (CSV, Excel, JSON from battery-storage vendors) into standardized sensor mappings for the digital-twin platform. The "agents" are markdown runbooks (`AGENT_CLASSIFIER.md`, `ADD_SENSOR_TOOL.md`) that an LLM orchestrator — Cursor in practice — follows, backed by genuinely executable Python tooling: `ai_batch_processor.py` chunks data and calls the Anthropic SDK, `agent_io_tool.py` handles tabular I/O, `add_sensor_to_catalog.py` and `check_design_compliance.py` mutate and validate the catalog. State lives in `sensor_catalog.json` and `blueprint_catalog.json`; supporting docs codify signal classes, naming conventions, and sensor-model design so humans and agents share one source of truth. Active internal product.

### What
A new BESS vendor ships a signal list — SVOLT, Sunwoda, and equivalents — and the goal is a one-to-one mapping from their raw tags (with their own polarity conventions, alarm-severity scales, encodings) into a shared blueprint hierarchy (`ESRack`, `ESContainer`, `HVAC`, `Cooling`, `FireSafety`, etc.) so the digital twin compares fleets apples-to-apples. The classifier agent reads each supplier row, infers the standard sensor key and signal class, proposes catalog edits, and writes the resulting `supplier_mapping.json` with transforms (`value * scale + offset`) and alarm-severity remaps. Engineers drive the agent from Cursor; the human stays in the loop on schema-breaking changes through compliance checks.

### Tech
Two layers: declarative markdown runbooks under `agents/` that any LLM can follow, and Python tools under `tools/` and `scripts/` that the runbook invokes. `tools/ai_batch_processor.py` is deliberately domain-agnostic — it chunks an input file, calls `anthropic.Anthropic()` with the orchestrator-supplied prompt, streams structured metadata to stdout and human logs to stderr. `tools/agent_io_tool.py` handles CSV/JSON/Excel I/O; `scripts/add_sensor_to_catalog.py` mutates `sensor_catalog.json` in place, `scripts/check_design_compliance.py` enforces naming and blueprint rules, `scripts/verify_catalog_completeness.py` and `json_to_excel.py` round out validation and export. Source of truth is two JSON files (`sensor_catalog.json` with hybrid blueprint + group_id architecture, `blueprint_catalog.json`); `docs/` codifies signal classes and polling rates, naming conventions, and sensor-model design as agent-readable reference.

### Status
Active product as of January 2026 (v0.5.0 in CHANGELOG), with SVOLT and Sunwoda mappings shipped and the Phase 2 roadmap targeting two more suppliers, PCS, and transformer catalogs. Used internally by integration engineers onboarding suppliers; agents catalog and validate, humans review PRs. Private GitHub repo on the ION-Altergo org.

## tsdb-benchmark

tsdb-benchmark is the due-diligence repo that compared QuestDB, ClickHouse, and TimescaleDB for the Altergo platform's sensor ingest workload. The actual work is in `benchmark/`: per-database ingestion scripts (`questdb-infinite-flow-real-mono.py`, `clickhouse-batch-ingestion.py`, `timescaledb-infinite-flow-real-mono.py`) push synthetic sensor rows in tight loops while measuring rows/sec, alongside a `multi_device_launcher.py` that spawns N edge-device processes against split sensor-ID ranges. Each engine has a `docker/*.yaml` for a one-command bring-up, Metabase included; a Streamlit-style `data_explorer_app/` reads results back out. Results aren't written up in the repo — the README is shell snippets and (notably) leaked GitHub PAT tokens that should be revoked.

### What
The shape of the workload is fixed by the platform: many sensors (cardinality in the thousands), each emitting a numeric value every second or faster, ingested continuously by edge devices and queried back for dashboards. The benchmark drives each candidate engine with the same `(sensorId, timestamp, value)` schema, prints rolling rows/sec, and lets the operator scale up `multi_device_launcher.py` to N parallel writer processes — each owning a disjoint sensor-ID range — to find where each engine starts to choke. Read-side spot checks use the Metabase container against the live tables.

### Tech
QuestDB writes go through `questdb.ingress.Sender` with `SYMBOL CAPACITY 131072 NOCACHE` for `sensorId` and `PARTITION BY DAY WAL`; ClickHouse uses a `MergeTree` with `ORDER BY (sensorId, timestamp)` partitioned by day, fed by `clickhouse-batch-ingestion.py` over the HTTP client; TimescaleDB uses a hypertable variant in the `timescaledb-infinite-flow-real-mono.py` flow. Cardinality and batch size are set per script (default 100 sensors at 1 Hz); the launcher passes `START_SENSOR_ID`, `CARDINALITY`, `BATCH_SIZE` via env and tees per-device logs into `logs/device_N.log`. `docker/{questdb,clickhouse,timescaldedb,metabase}.yaml` give one-command stacks; `data_explorer_app/` is a small Python reader for results; `requirements.txt` pins the SDKs.

### Status
Last active September 2025, private GitHub repo on the ION-Altergo org. Used internally to back the time-series DB choice for the Altergo platform; no formal write-up in the repo itself. The README leaks `ghp_…` GitHub PATs in clone URLs — these need to be revoked.
