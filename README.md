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
  vanilla-mammals.json       # base-game mammals (incl. wolf/fox/moose, for servers without FotSA)
  vanilla-birds.json         # base-game birds
  territories.json           # home-range opt-ins for large herd herbivores
  fotsa-cats.json            # Fauna of the Stone Age: Pantherinae + Machairodontinae
  fotsa-canids.json          # Fauna of the Stone Age: Caninae
  fotsa-cervids.json         # Fauna of the Stone Age: Capreolinae
  feverstone-horses.json     # Feverstone's Horses
  feverstonewilds.json       # Feverstone Wilds (excludes golems + fish)
  pegasus.json               # Pegasus
  monoceros.json             # Monoceros: Ancient Unicorns
  moreanimals.json           # More Animals (game birds)
  cats.json                  # Cats (house/ocelot/serval/European wildcat)
  thecritterpack.json        # The Critter Pack (songbirds, waterfowl, small mammals, inverts)
  hieronymus-reptiles.json   # Hieronymus Reptiles Collection (~164 species; see its header)
  primitivesurvival.json     # Primitive Survival
```

Species keys must match exactly what Cycle of Life discovered — check `/col species <filter>`
in-game for the authoritative keys.

## Building / installing

No build needed (no code). For development, point the server at this folder as a mod path; for
distribution, zip the folder contents (modinfo.json at the zip root).

## License

Licensed under the [Apache License 2.0](LICENSE.txt) — use, modify, and redistribute freely; retain
attribution and mark any files you change (Apache §4). See [NOTICE.txt](NOTICE.txt).

This pack is tuning **data**. It references entities from other Vintage Story mods (such as 
the [Fauna of the Stone Age](https://mods.vintagestory.at/show/user/2ABE1C9265B6B2CFEFAE) series,
[Feverstone's Horses](https://mods.vintagestory.at/feverstonehorses),
Feverstone Wilds, [Pegasus](https://mods.vintagestory.at/pegasus), Monoceros, More Animals, Cats,
The Critter Pack, the Hieronymus Reptiles Collection,
and [Primitive Survival](https://mods.vintagestory.at/primitivesurvival)) by their entity codes for
interoperability only — it contains **none of those mods' assets**, and they remain under their own
licenses.
