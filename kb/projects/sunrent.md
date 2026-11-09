---
name: Sunrent
description: "A solar-as-a-service model for French households: PVGIS hourly production, a household energy model, a dispatch and finance engine, and Monte Carlo on the offer."
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
    description: Solar-as-a-service platform for French households, from the roof
      and the bills to the operator's offer and a household advisor.
    year: 2026
    last_active: 2026-09
    language: TypeScript
    archived: false
    tags: *a1
---

Sunrent is a solar-as-a-service model for French households, built at Matrice Technologies in September 2026. In the model, Sunrent installs and owns the panels, battery and inverter, the customer pays nothing up front, and the customer's total bill (grid plus Sunrent's fee) is guaranteed a set percentage below what it would have been without solar. The repository is the platform that sizes and prices that offer for a given building, and advises the household on everything else it could change.

## What

Each project is a building, and each building goes through six tabs. **Bâtiment** places the site on a satellite map, defines the zones where panels could go (pre-filled from Google's Solar API when it knows the roof) and describes the house use by use: envelope, heating, hot water, cooking, cooling, vehicles, pool, prefilled from the energy certificate (DPE) when the register has one. **Consommation** takes a bill, a meter export or a single figure, and splits hourly demand by use and energy carrier, calibrated to the bills and compared with similar households. **Solutions** is the household's advisor: a catalogue of measures, each scored over its lifetime against doing nothing, with installed cost, aid by income tier and climate zone, embodied carbon and upkeep, a Pareto frontier of cost against carbon and a recommended path (sobriety, efficiency, hot water, heating, then panels sized on what is left, flexibility, tariff, and a battery only if it pays for itself). **Simulation** runs a PVGIS hourly year per zone against the building's demand for every array size, then compares hot-water, heating, load-shifting and tariff options. **Coûts** and **Optimisation**, marked as the installer's view, cover the bill of materials and every guarantee, size and battery combination ranked by net present value above the operator's minimum IRR, followed by Monte Carlo with a tornado chart.

## Tech

A Next.js 16, React 19 and TypeScript app on Supabase, with Zod and Vitest. The engine lives in `core/` (demand, thermal, energy, flexibility, sizing, finance, Monte Carlo, measures, impact) and exposes a client-safe entry (labels and types only) so that country data stays out of the browser bundle. Heating is an hourly heat balance with envelope losses by component, internal and solar gains, thermal mass, setback schedules and heat pumps whose efficiency follows outdoor temperature. Market inputs (tariffs, holidays, emission factors including an hourly 2024 grid carbon factor, subsidies, benchmarks, meter formats, geocoder, certificate register) are country packages, France first; ESLint rules and a test refuse country-specific code elsewhere. A reference test on a Lyon house and a stored PVGIS year pins the figures. Known meter formats are read by a deterministic parser and the rest by a Gemini extraction agent. Deployment targets Coolify, with Supabase on the same server.

## Status

Built from 24 to 27 September 2026 in three iterations, each against a written contract and assembled from parallel slices; private repository. Still open: the engine's sizing optimises the operator's NPV, and the household's path sits beside it rather than replacing it. The next planned step is a report the customer can read and contest, with assumptions, sources and sensitivities in plain language.
