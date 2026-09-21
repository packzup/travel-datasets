# Packzup Open Travel Data

Three open datasets for travel and country reference work: **climate**, **connectivity**
(plugs/voltage/driving side) and **airline carry-on limits**. Each is published as CSV, archived
on Zenodo with a DOI, and licensed according to where its data actually came from.

Maintained by [Packzup](https://packzup.com/). **Disclosure: packzup.com is a travel information
site that participates in affiliate programmes.** These data files are published separately from
that and carry no affiliate content.

---

## ⚠️ THIS REPOSITORY IS NOT UNDER A SINGLE LICENCE

Read this before reusing anything.

| files | licence | why |
|---|---|---|
| `packzup-climate-2026.*` | **CC BY 4.0** | derived from ERA5 via Open-Meteo (CC BY 4.0) |
| `packzup-carry-on-limits-2026-09.csv` | **CC BY 4.0** | compiled by Packzup from airline-published policies |
| `packzup-connectivity-2026.*` | **CC BY-SA 4.0** | derived from Wikipedia, which is **share-alike** |

**The connectivity data carries a share-alike obligation that the other two do not.** If you
redistribute it, or anything derived from it, you must license that under CC BY-SA 4.0. Do not
treat this repository as uniformly CC BY.

---

## 1. Travel Climate Dataset 2026

**`packzup-climate-2026.csv` · `packzup-climate-2026.json`** — 1,140 rows
**Licence: CC BY 4.0** · **DOI: [10.5281/zenodo.22873350](https://doi.org/10.5281/zenodo.22873350)**

95 destination slugs × 12 months.

| column | meaning |
|---|---|
| `slug` | Packzup destination identifier |
| `destination` | display name |
| `country_code` | ISO 3166-1 alpha-2 |
| `month` | 1–12 |
| `avg_high_c` | average daily high, °C |
| `avg_low_c` | average daily low, °C |
| `rain_mm` | average monthly rainfall, mm |
| `rain_days` | average days with rain in the month |

**Limitations — read before citing**
- **Modelled reanalysis averages, not weather-station observations.** ERA5 is a gridded
  reanalysis product; values represent a model grid cell, not a specific site.
- **Granularity is mixed.** The 95 entries are countries (Albania, Japan), cities (Amsterdam,
  Tokyo) *and* regions (Patagonia, Dolomites). 23 ISO codes appear more than once. This is not a
  country-level table.
- **No averaging period is published.** If the window matters to you, consult Open-Meteo's ERA5
  documentation rather than assuming one.
- `rain_days` has **no published mm/day threshold definition**.

**Attribution required:** *Climate data: ERA5 reanalysis via Open-Meteo (CC BY 4.0). Compiled by
Packzup.*

---

## 2. Travel Connectivity Dataset 2026

**`packzup-connectivity-2026.csv` · `packzup-connectivity-2026.json`** — 95 rows
**Licence: CC BY-SA 4.0** · **DOI: [10.5281/zenodo.22873867](https://doi.org/10.5281/zenodo.22873867)**

| column | meaning | example |
|---|---|---|
| `slug` | Packzup destination identifier | `albania` |
| `destination` | display name | `Albania` |
| `country_code` | ISO 3166-1 alpha-2 | `AL` |
| `plug_types` | comma-separated IEC plug letters | `C,F` |
| `voltage` | nominal mains voltage | `230 V` |
| `frequency` | nominal mains frequency | `50 Hz` |
| `driving_side` | `left` or `right` | `right` |

No cell in this file is empty.

**Limitations — read before citing**
- **Values are national.** Where a row is a city or region (`tokyo`, `bali`), it carries the
  parent country's national values — not a local measurement.
- **Nominal, not measured.** Voltage and frequency are published nominal standards; real supply
  varies.
- **Plug letters are the common types, not an exhaustive legal list.**
- This is a **secondary** source. For anything safety-critical, cite Wikipedia's own source or
  the relevant national standards body directly.

**Attribution required:** *Source: Wikipedia, "Mains electricity by country", CC BY-SA 4.0.
Compiled by Packzup. Derivative works must be shared under CC BY-SA 4.0.*

---

## 3. Carry-On Size Limits by Airline 2026

**`packzup-carry-on-limits-2026-09.csv`** — 106 rows
**Licence: CC BY 4.0** · **DOI: [10.5281/zenodo.22874346](https://doi.org/10.5281/zenodo.22874346)**

### ⚠️ This dataset is NOT uniformly verified

| `verification` | rows | `source_url` | `last_verified` |
|---|---|---|---|
| `primary_verified` | **21** | present | `2026-09-01` |
| `carried_forward` | **85** | **empty** | `2026-06` |

Only 21 of 106 rows were re-checked against the airline's own published policy. The other 85 are
carried forward from an earlier check and are **not individually source-linked**. **Please do not
describe this dataset as fully sourced or independently verified.**

### It is also sparse beyond one column

| column | populated / 106 |
|---|---|
| `airline`, `country`, `cabin_bag_cm`, `verification`, `last_verified` | **106** |
| `cabin_bag_kg` | 100 |
| `cabin_bag_free_on_cheapest_fare`, `source_url`, `notes` | 21 |
| `free_personal_item_cm` | 18 |
| `free_personal_item_kg` | **5** |

**Only `cabin_bag_cm` is complete for every airline.** The personal-item columns are too sparse
for cross-airline comparison.

**Other limitations:** these are *stated policy, not enforcement*; dimensions are as published
and rounded; there is no fare-class matrix (one representative allowance per airline); and
airline policies change without notice — check `last_verified` per row.

---

## Known data issue (documented, not corrected)

`korea` and `south-korea` are **two slugs for the same entity**, and their records are
**byte-identical** — in both the climate and connectivity files. So each holds **95 slugs but 94
distinct real-world entities**.

This is left exactly as published. These files are faithful copies of the live Packzup datasets,
not cleaned-up variants, so that they match the Zenodo deposits and the source pages byte for
byte.

---

## Provenance

| dataset | derived from |
|---|---|
| climate | [Open-Meteo](https://open-meteo.com/) (ERA5 reanalysis) |
| connectivity | [Wikipedia — Mains electricity by country](https://en.wikipedia.org/wiki/Mains_electricity_by_country) |
| carry-on | airlines' own published cabin-baggage policies |

Source pages: <https://packzup.com/travel-datasets/> and
<https://packzup.com/carry-on-size-checker/>
Methodology: <https://packzup.com/methodology/> · Corrections:
<https://packzup.com/corrections-policy/>

## Citation

> Packzup. *Packzup Travel Climate Dataset 2026*. Zenodo, 2026. https://doi.org/10.5281/zenodo.22873350
>
> Packzup. *Packzup Travel Connectivity Dataset 2026*. Zenodo, 2026. https://doi.org/10.5281/zenodo.22873867
>
> Packzup. *Packzup Carry-On Size Limits by Airline 2026*. Zenodo, 2026. https://doi.org/10.5281/zenodo.22874346

## Corrections

Found an error? Open an issue. Corrections are welcome and will be reflected on the source pages
and in the next Zenodo version.
