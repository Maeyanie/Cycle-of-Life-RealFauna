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

## Where the numbers come from

[SOURCES.md](SOURCES.md) records the evidence base: how to convert an overlay value back to
real-world units (game-days to years, and `carryingCapacity` to animals per km²), and the sources
consulted wherever a figure was contested, surprising, or used to override a mod author's own value.
Most values rest on ordinary uncontested reference biology and are not cited individually; the ones
worth checking are.

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
  fotsa-bovinae.json         # Fauna of the Stone Age: Bovinae (cattle, buffalo, antelope)
  fotsa-cervinae.json        # Fauna of the Stone Age: Cervinae (Old World deer)
  fotsa-elephantidae.json    # Fauna of the Stone Age: Elephantidae (elephants, mammoths)
  fotsa-dinornithidae.json   # Fauna of the Stone Age: Dinornithiformes Plus (NZ flightless birds)
  fotsa-rhinocerotidae.json  # Fauna of the Stone Age: Rhinocerotidae (rhinoceroses)
  fotsa-casuariidae.json     # Fauna of the Stone Age: Casuariidae Plus (Australian flightless birds)
  fotsa-manidae.json         # Fauna of the Stone Age: Manidae (pangolins)
  fotsa-thylacinidae.json    # Fauna of the Stone Age: Thylacinidae Plus (carnivorous marsupials)
  fotsa-viverridae.json      # Fauna of the Stone Age: Viverridae Plus (civets, genets, binturong)
  fotsa-meiolaniidae.json    # Fauna of the Stone Age: Meiolaniidae (horned turtles)
  fotsa-vombatidae.json      # Fauna of the Stone Age: Vombatidae Plus (wombats, Zygomaturus, Thylacoleo)
  fotsa-spheniscidae.json    # Fauna of the Stone Age: Spheniscidae (penguins)
  fotsa-felinae.json         # Fauna of the Stone Age: Felinae (caracal, lynxes)
  feverstone-horses.json     # Feverstone's Horses
  feverstonewilds.json       # Feverstone Wilds (excludes golems + fish)
  pegasus.json               # Pegasus
  monoceros.json             # Monoceros: Ancient Unicorns
  moreanimals.json           # More Animals (game birds)
  cats.json                  # Cats (house/ocelot/serval/European wildcat)
  thecritterpack.json        # The Critter Pack (songbirds, waterfowl, small mammals, inverts)
  hieronymus-reptiles.json   # Hieronymus Reptiles Collection (~164 species; see its header)
  fowlmod.json               # Sonya's Quality Fowl (ducks)
  primitivesurvival.json     # Primitive Survival
  archosaur.json             # ARCHOSAUR! (ferocidon + its nest chain; invented values, see header)
  lop-dromaeosauridae.json   # Legacy of the Phanerozoic: Birds of Prey (14 raptors + nests)
  lop-abelisauridae.json     # Legacy of the Phanerozoic: Carnivorous Bull (18 abelisaurids + nests)
  lop-pachycephalosauria.json# Legacy of the Phanerozoic: Domed Head (16 pachycephalosaurs + nests)
  lop-ankylosauria.json      # Legacy of the Phanerozoic: Fused Body (8 ankylosaurs + nests)
  lop-ceratopsidae.json      # Legacy of the Phanerozoic: Horned Crown (15 ceratopsians + nests)
  lop-ornithomimosauria.json # Legacy of the Phanerozoic: Horrible Hands (14 ostrich mimics + nests)
  lop-macronaria.json        # Legacy of the Phanerozoic: Long Neck (15 sauropods + nests)
  lop-stegosauria.json       # Legacy of the Phanerozoic: Plated Back (12 stegosaurs + nests)
  lop-spinosauridae.json     # Legacy of the Phanerozoic: Sailed Spine (6 spinosaurids + nests)
```

### Mods that need no entries

Some requested mods are already invisible to Cycle of Life, so the pack has nothing useful to say
about them. Recorded here so the reasoning does not have to be re-derived each time someone asks:

| Mod | Why there is no file |
| --- | --- |
| **Seikret** (Monster Hunter mount) | Nothing in it spawns naturally. The birds declare no spawn conditions at all, and the egg (`igg`) has a runtime chance of `0.0` for every type with no worldgen block. Eggs are bought from the treasure-hunter trader, so a Seikret is player property, not wildlife. |

Note that an `exclude` entry would achieve nothing for these. `SpeciesCatalog.Build` reads spawn
conditions **first** and only consults the exclusion list for entities that actually spawn, so a
creature that never spawns is dropped before exclusions are considered. Such mods are never
discovered, never adopted, never spawn-vetoed and never despawned — including once tamed or ridden.

### Verification status

Files are marked below by how their species keys were confirmed. A key that is wrong is *inert*, not
harmful: an overlay entry matching no species is ignored and the animal simply keeps its
auto-discovered values. The one exception is an `exclude` pattern, which is why the aquatic
exclusions in `feverstonewilds.json` are deliberately belt-and-braces.

| Verified against a live roster | Derived from the mod's entity JSON only |
|---|---|
| vanilla, FotSA (cats/canids/cervids), Feverstone Horses, Pegasus, Primitive Survival, territories | Feverstone Wilds, More Animals, Cats, The Critter Pack, Monoceros, Hieronymus Reptiles, Sonya's Quality Fowl, FotSA Bovinae, FotSA Cervinae, FotSA Elephantidae, FotSA Dinornithiformes, FotSA Rhinocerotidae, FotSA Casuariidae, FotSA Manidae, FotSA Thylacinidae, FotSA Viverridae, FotSA Meiolaniidae, FotSA Vombatidae, FotSA Spheniscidae, FotSA Felinae |

The right-hand column covers mods the pack author does not run. Their keys were computed by
replicating Cycle of Life's own key derivation (domain + base code + non-demographic variants,
honouring `spawnconditionsByType` gating) against the mod archives, and cross-checked both ways —
but nothing beats seeing them in a roster. If you run one of those mods, `/col species` and the
startup roster dump list the authoritative keys, and anything mistyped will simply be missing from
them. Corrections are welcome.

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
