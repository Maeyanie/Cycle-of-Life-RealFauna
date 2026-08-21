# Sources

Where the numbers in this pack come from, and how to read them.

## How to read a value

Two conversions make the overlay figures comparable to real-world data. Both are properties of
Cycle of Life and the Vintage Story world, not of this pack.

**Time.** The server this pack was authored against runs **30-day months**, so a game year is about
**360 game-days**. Divide any `lifespanDays` or `gestationDays` by 360 to get years:
`lifespanDays: 7200` is a twenty-year animal, `gestationDays: 660` is the elephant's 22 months.

**Density.** `carryingCapacity` (K) is *not* a herd size. The founding check counts every animal of
the species within 6 chunks — 169 chunks, which at 32 m per chunk is **0.173 km²** — so K is a
population density:

```
density (per km²)  =  K / 0.173          K = 1  ->  ~6/km²
K                  =  density × 0.173    K = 2  ->  ~12/km²
                                         K = 6  ->  ~35/km²
```

That makes K derivable from published wild densities rather than guessed, and where a figure was
available that is how it was set. Two caveats are worth knowing:

- For **herd species K is largely inert**. One unit grown to `MaxHerdSize` already exceeds any
  realistic K by itself, so no second unit founds nearby regardless; what sets the density you
  actually see is **herd size** and **territory radius**. K binds on solitary and small-group species.
- The grid imposes a **floor**. A solitary species still needs a breeding *pair* in one place, and
  2 animals in 0.173 km² is ~12/km² however sparse the real animal is. The saola and the kākāpō are
  both far rarer in life than this world can express.

**Herd size** is the genuinely biological number, and it comes from each mod's own `groupSize`
declaration rather than from this pack. Good mods get it right — solitary bushbuck and anoa,
20-strong Cape buffalo herds with solitary bulls, matriarchal elephant parties of 10–14. This pack
overrides `herd` only where a mod is more gregarious than the animal.

## What is sourced and what is not

Most values here rest on ordinary reference biology — gestation lengths, litter sizes, breeding
seasons, adult masses — the kind of figure that is uncontested and available in any standard account
of the species. Those are not cited individually; there would be several hundred citations and they
would all say the same thing.

The sources below were consulted where a figure was **contested, surprising, or used to override a
mod author's own value**. Those are the decisions worth being able to check.

## Consulted

### Surplus killing — the `huntWhenFull` floors
Used to decide which predators keep killing on a full stomach, and how strongly. Informs
`fotsa-cats.json`, `fotsa-canids.json`, `vanilla-mammals.json`, `cats.json`.

- [Surplus killing — Wikipedia](https://en.wikipedia.org/wiki/Surplus_killing) — the species list and
  the specific incidents used for tiering: a red fox killing 74 penguins, a leopard 51 sheep in one
  pen, a spotted hyena clan 82 Thomson's gazelle while eating 16% of them.
- [Kruuk, *Surplus killing by carnivores*, J. Zoology 1972](https://zslpublications.onlinelibrary.wiley.com/doi/10.1111/j.1469-7998.1972.tb04087.x)
  — the origin of the term, from work on spotted hyenas and red foxes.
- [Surplus killing: the myth of mustelid "bloodthirst"](https://www.genuinemustelids.org/articles/surplus-killing/)
  — caching as the reason, which is why the arctic fox carries the same floor as the red.
- The same Wikipedia article supplies the two felid cases behind `fotsa-felinae.json`: two caracals in
  Cape Province killing 22 sheep in one night and eating part of the buttock of one, and lynx recorded
  surplus-killing sheep in Norway. Hence the caracal's 0.3 floor and a modest one on the lynxes.

### Body masses — vanilla weight corrections
Vanilla Vintage Story declares one weight per genus *file*, so several species inherit a figure meant
for a much larger relative. These three were checked before overriding. Informs `vanilla-mammals.json`.

- [Eurasian wolf](https://animalia.bio/eurasian-wolf) — averages ~39 kg in Europe (32–50 typical,
  69–80 kg records). Vanilla ships 76 kg, the record end; corrected to 40.
- [Thomson's gazelle — Animal Diversity Web](https://animaldiversity.org/accounts/Eudorcas_thomsonii/)
  — 15–35 kg (males 20–35, females 15–25). Vanilla ships 67 kg; corrected to 23.
- [Mouflon](https://animalia.bio/mouflon) — 25–55 kg. Vanilla gives every sheep 130 kg, right for a
  bighorn ram and roughly three times a mouflon; corrected to 42.

### Population density — deriving K
- [African buffalo density, Chebera Churchura National Park, Ethiopia](https://onlinelibrary.wiley.com/doi/full/10.1111/aje.12411)
  — 4.3/km², the anchor for the Cape buffalo's K=2 and the reference point the rest of
  `fotsa-bovinae.json` is scaled against.

### Megaloceros giganteus — the giant deer's diet
Used to override the mod's own `Fruit/Vegetable` browser diet. Informs `fotsa-cervinae.json`.

- [Dental wear evidence for browsing and grazing in the giant deer](https://kernsverlag.com/en/dental-wear-evidence-for-browsing-and-grazing-dietary-traits-in-the-giant-deer-from-the-late-pleistocene-of-central-europe/)
  — mesowear and microwear across Middle-to-Late Pleistocene populations show generalised mixed
  feeding tending toward grazing.
- [Megaloceros overview](https://grokipedia.com/page/Megaloceros) — stable isotopes (δ¹³C/δ¹⁸O) from
  Irish molar enamel indicating grass and forbs supplemented with browse, the Irish late-glacial
  population being the most graze-dominated.

### Rhinoceros feeding — the grazer/browser split
Used to split the mod's uniform Fruit/Grain/Vegetable across all six rhinos. Informs
`fotsa-rhinocerotidae.json`.

- [Grazers versus browsers — International Rhino Foundation](https://rhinos.org/blog/oppositeday-grazers-versus-browsers/)
  and [White rhinoceros — National Geographic](https://www.nationalgeographic.com/animals/mammals/facts/white-rhinoceros)
  — the white rhino feeds almost exclusively on grass and its wide square lip crops it; the black
  rhino's hooked, prehensile lip strips leaves and fruit from twigs. Their older names, square-lipped
  and hook-lipped, encode the difference.
- [Browsers, grazers or mix-feeders? Diet of *Stephanorhinus kirchbergensis* and *Coelodonta
  antiquitatis*](https://www.sciencedirect.com/science/article/abs/pii/S1040618220305048) — δ¹³C/δ¹⁵N
  isotope and mesowear work placing the woolly rhinoceros as mainly a grazer of steppe grasses,
  forbs, lichens and mosses, with seasonal browse on top.

### Australian flightless birds — cassowary diet, nativehen mass
Used to override mod values in `fotsa-casuariidae.json`.

- [Southern cassowary diet — Birds of the World](https://birdsoftheworld.org/bow/species/soucas1/cur/foodhabits)
  and [Save the Cassowary — Rainforest Rescue](https://www.rainforestrescue.org.au/explore-the-rainforest/save-the-cassowary/ecology-habitat/)
  — overwhelmingly frugivorous, fallen fruit forming the bulk of the diet across 240+ plant species,
  swallowed whole and passed intact. A keystone seed disperser for large-seeded rainforest trees that
  have no other disperser. The mod's Grain (grass) category was dropped on that basis.
- [Tasmanian nativehen — Australian Museum](https://australian.museum/learn/animals/birds/tasmanian-native-hen/)
  — 725–1260 g. The mod ships 0.28 kg, roughly three and a half times light; corrected to 1.0.

### New Zealand flightless birds — extreme life histories
Informs `fotsa-dinornithidae.json`, where the lifecycle values are the whole point of the file.

- [Turvey, Green & Holdaway, *Cortical growth marks reveal extended juvenile development in New
  Zealand moa*, Nature 2005](https://pubmed.ncbi.nlm.nih.gov/15959513/) — up to nine growth rings in
  moa leg bones; roughly a decade to reach adult size, exceptionally slow for a bird, and a large
  part of why moa could not absorb hunting.
- [Kiwi life cycle — Save the Kiwi](https://savethekiwi.nz/about-kiwi/kiwi-facts/kiwi-life-cycle/) —
  70–80 day incubation, about the gestation of a similar-sized mammal, for an egg up to a fifth of
  the female's mass.
- [Kākāpō breeding — NZ Department of Conservation](https://blog.doc.govt.nz/2025/06/27/kakapo-breeding-season-2026/)
  — 60–90 year lifespan, and breeding only when the rimu masts, every two to four years.

### Dromaeosaurid body masses — Birds of Prey

The mod declares a flat `weightByType` of **1000 kg for every adult**, across a family that really
spans from a ~300 kg Utahraptor to a ~600 g Rahonavis. Weight is load-bearing in this simulation —
it drives forage demand, grazing range, territory radius and the satiation reserve — so a 1 kg
Microraptor rated at a tonne would roam and eat like megafauna. Each species is therefore given a
published mass estimate, taken mid-range where sources disagree:

| Species | Mass used | Published range / note |
| --- | --- | --- |
| *Utahraptor ostrommaysorum* | 300 kg | 280–500 kg; the largest dromaeosaurid known |
| *Dakotaraptor steini* | 250 kg | 220–350 kg |
| *Achillobator giganticus* | 250 kg | 250–350 kg |
| *Austroraptor cabazai* | 250 kg | ~300 kg, but slender and long-snouted |
| *Deinonychus antirrhopus* | 70 kg | commonly cited ~73 kg |
| *Adasaurus mongoliensis* | 20 kg | reduced sickle claw |
| *Dromaeosaurus albertensis* | 15 kg | stouter, more crushing skull |
| *Velociraptor mongoliensis* | 15 kg | turkey-sized |
| *Atrociraptor marshalli* | 12 kg | known from little more than jaws |
| *Pyroraptor olympius* | 12 kg | fragmentary; family-scaled estimate, not measured |
| *Saurornitholestes langstoni* | 10 kg | |
| *Buitreraptor gonzalezorum* | 3 kg | long slender snout, small teeth |
| *Microraptor zhaoianus* | 1 kg | 0.5–1.2 kg, four-winged and arboreal |
| *Rahonavis ostromi* | 0.6 kg | close enough to birds that its placement is argued |

Three prey bands are set from evidence rather than scaled from mass:

- **Deinonychus** gets an upper bound well above its own mass (200 kg) on the strength of the
  *Tenontosaurus* association — the closest the fossil record comes to evidence of group predation
  on much larger prey.
- **Velociraptor**'s upper bound comes from the Fighting Dinosaurs specimen, locked with a
  *Protoceratops* of comparable mass.
- **Microraptor**'s band is unusually well grounded: its diet is read directly from gut contents —
  birds, fish and small mammals.
- **Austroraptor** is given a deliberately narrow band despite its size. Conical, unserrated teeth
  and a long snout read as fish-eating rather than the family's usual slashing bite.

These are estimates from a contested literature, not measurements. They are recorded here so the
numbers can be argued with rather than merely trusted.

## Corrections welcome

If a number here is wrong, the fix is usually one value in one file, and the file will say what the
figure was meant to represent. Values that came from a mod's own declaration rather than from this
pack are noted as inherited in the relevant file header — those want reporting upstream instead.
