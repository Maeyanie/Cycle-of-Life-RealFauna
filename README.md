# Cycle of Life: Realistic Fauna

A **content-only** overlay pack for the [Cycle of Life](https://github.com/Maeyanie/Cycle-of-Life) ecosystem mod. It
ships per-species tuning JSON under `assets/colrealfauna/config/cycleoflife/`, which Cycle of Life's
overlay loader picks up automatically (it scans `config/cycleoflife/` across every loaded mod).

## Philosophy

"Real-but-playable." Values lean on real-world biology — lifespans, breeding seasons, litter sizes,
maturation, diet, social structure, predator/prey — scaled to game time. With the server's **30-day
months** (≈360 game-days/year), that scaling lands close to literal real-life figures, so e.g. a
wolf living ~8 years ≈ ~2900 game-days.

Lifecycles are deliberately **slow** (long lifespans, modest litters, seasonal breeding, slow
maturation). Combined with realistic carrying capacities and predation, that means **populations
don't bounce back instantly** — overhunting an area has consequences. This is intentional: hunt
sustainably, or face local depletion.

## Swapping packs

This is one opinion of how the world's animals should behave. Everyone's will differ, and none are
wrong. Because it's a separate content mod, just enable/disable it (or replace it with a different
pack) without touching the core mod. Overlays only *override* what's set; anything omitted keeps
Cycle of Life's auto-discovered value.

## Structure

```
assets/colrealfauna/config/cycleoflife/
  vanilla-mammals.json    # base-game mammals
  vanilla-birds.json      # base-game birds
  ...                     # more groups / mods as added
```

Species keys must match exactly what Cycle of Life discovered — check `/col species <filter>`
in-game for the authoritative keys.

## Building / installing

No build needed (no code). For development, point the server at this folder as a mod path; for
distribution, zip the folder contents (modinfo.json at the zip root).
