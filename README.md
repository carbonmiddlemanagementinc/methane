# The cost of a 0.5% methane leakage rate

An interactive analysis of what it would cost to bring methane leakage from the US oil and gas supply chain (wellhead to city gate) down to 0.5% by 2035, and which policies would get there.

Prepared by the Carbon Management and the Transition Program, Center on Global Energy Policy (CGEP), Columbia University.

![Cost of reaching 0.5%](docs/cost.png)

## Key findings

- **Measured leakage is about 2% today.** With no new controls it would still be 1.74% in 2035, based on basin-by-basin aircraft and satellite measurements applied to EIA's AEO2026 production outlook.
- **Reaching 0.5% means cutting 71% of 2035 methane** (9.5 million tonnes CH₄ a year).
- **The cheapest path costs about $3.6 billion a year,** net of the value of gas kept: $385 per tonne on average and $2,960 for the last tonne needed. That is 7.3 cents per Mcf produced.
- **The Waste Emissions Charge as written would not get there.** A uniform fee on every measured tonne would need to be about $2,960 per tonne (2025 dollars) to reach 0.5%.
- **Large leaks are concentrated.** In five of the six basins with enough aircraft and satellite data, a tenth of large-leak sites release 43–49% of the methane those sites emit (San Juan: 33%).

## What's on the page

| Tab | Contents |
|---|---|
| Cost of reaching 0.5% | Least-cost abatement curve across 25 measures, 14 source categories and 19 basins; target slider; sensitivities and Monte Carlo range |
| Map | Measured leak rates by basin today, measured vs. EPA inventory, cost to reach 0.5% by basin, policy scenarios, low-producing wells, clean-gas supply with interstate pipelines; close-ups of large-leak sites in nine basins |
| Fees and rules | EPA's OOOOb/c rules, the Waste Emissions Charge as written and alternatives, and combinations |
| Assumptions and data | Scope, methods, benchmark comparisons, limitations, downloads and sources |

![Map](docs/map.png)

![Permian close-up](docs/permian.png)

## Publish with GitHub Pages

1. Create a public repository and upload the contents of this folder (keep the folder structure).
2. In the repository, go to **Settings → Pages**, set **Source** to "Deploy from a branch", and choose `main` and `/ (root)`.
3. The site will be live at `https://<your-account>.github.io/<repository-name>/` within a few minutes.

The `.nojekyll` file tells GitHub Pages to serve the files as they are.

**Optional: add the full workbook.** Save the analysis workbook as `data/methane_leakage_workbook.xlsx`. The "Full workbook" link on the Assumptions and data tab appears automatically once that file exists, and stays hidden until then.

**Embedding.** The page sends its height to a parent window (`cgep-embed-height` message), so it can be embedded in an iframe that resizes to fit.

## View locally

The basin close-ups load their data from `data/closeup/`, which browsers block when a page is opened straight from disk. Serve the folder instead:

```
python3 -m http.server 8000
```

then open http://localhost:8000.

## Files

| Path | Contents |
|---|---|
| `index.html` | The whole page: markup, styles, scripts and model results (no build step) |
| `data/cost_curve.csv` | Every measure in every basin, with tonnes cut and net cost |
| `data/basins.csv` | 2035 baseline, leak rate, and cuts on the cheapest path and under the WEC, by basin |
| `data/policies.csv` | Rules, fees and combinations |
| `data/scenarios.csv` | Sensitivities |
| `data/large_leak_sites.csv` | Large-leak sites in nine basins, 2024–26 (Carbon Mapper data; see licensing) |
| `data/closeup/*.json` | Map layers for each basin close-up |
| `docs/` | Screenshots used in this README |

## Methods in brief

- **Baseline.** Each basin's latest measured loss rate (MethaneSAT, MethaneAIR, AMI or EDF EI-ME) is held at today's level and applied to its 2035 production from EIA AEO2026. Scope covers production, gathering, processing, and transmission and storage, including unburned fuel from compressor engines; local distribution is excluded.
- **Costs.** Twenty-five measures cut emissions in sequence within each source category and basin. Costs are annualized at 7% (3% as a sensitivity), start from today's equipment with no rules assumed, and net out the value of gas kept at AEO2026 2035 regional prices. Plugging low-producing wells is allowed.
- **Policies.** EPA's rules are mapped to the share of each measure they force. The Waste Emissions Charge is modeled on reported (subpart W) emissions with facility-level intensity thresholds and netting.
- **Basin close-ups.** Large-leak sites are Carbon Mapper "sources" observed January 2024 to October 2026 (aircraft and the Tanager-1 satellite). Dot size is the average rate when seen; color is the share of imaged days a site was leaking. The dots cover large leaks only and should not be summed into basin totals. Imaging coverage is approximate, counted from scene outlines.

Full assumptions, benchmark comparisons and limitations are on the page's Assumptions and data tab.

## Sources

- **Measurement:** Omara et al. 2024; Sherwin et al. 2024; MacKay et al. 2026; Williams et al. 2026 (MethaneSAT); Ravikumar et al. 2025 (AMI, Appalachia); EDF EI-ME 2023
- **Inventory:** EPA Greenhouse Gas Inventory 2023; GHGRP subpart W
- **Production and prices:** EIA Annual Energy Outlook 2026
- **Large-leak sites and imaging coverage:** Carbon Mapper, Inc.
- **Well locations:** EDF / MethaneSAT LLC, Oil and Gas Infrastructure Mapping (OGIM) database v2.7
- **Pipelines:** EIA natural gas interstate pipelines, via DOT National Transportation Atlas Database
- **Costs:** EPA regulatory impact analyses for OOOOb/c (2024) and the Waste Emissions Charge (2024); ICF for EDF (2014); ICF for ONE Future (2016)
- **Policy status:** CRS R48906 (April 2026); Holland & Knight on EPA's October 29, 2026 proposal
- **Base maps:** US Census Bureau boundaries via us-atlas

## Licensing

Third-party data in this repository carries its own license terms; see [DATA_LICENSES.md](DATA_LICENSES.md). In particular, the Carbon Mapper data (`data/large_leak_sites.csv` and the site layers in `data/closeup/`) is for non-commercial use under Carbon Mapper's Modified CC BY-SA 4.0 license, and any reuse must carry the same license and the attribution "Data by Carbon Mapper®".
