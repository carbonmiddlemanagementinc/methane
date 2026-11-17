# Methane abatement database

A meta-analysis of the available data for methane leaks from both oil, gas and coal supply chains, and abatement costs for different geographies. It includes an interactive analysis of what it would cost to bring methane leakage from the US oil and gas supply chain (wellhead to city gate) down to 0.5% by 2035, and which policies would get there.

Prepared by the Carbon Management and the Transition Program, Center on Global Energy Policy (CGEP), Columbia University.

![Global Methane Map](docs/world.png)

## Key findings: United States

- **Measured leakage is about 1.8% today.** With no new controls it would still be 1.55% in 2035, based on basin-by-basin aircraft and satellite measurements applied to EIA production data and its AEO2026 outlook.
- **Reaching 0.5% means cutting 68% of 2035 methane** (8.7 million tonnes CH₄ a year).
- **The cheapest path costs about $2.7 billion a year,** net of the value of gas kept: $312 per tonne on average and about $1,400 for the last tonne needed. That is 5.4 cents per Mcf produced. The median of 2,000 uncertainty draws is $3.8 billion. The last-tonne cost is sensitive to assumptions: about $1,000 to $2,200 under most single changes, and far higher if the baseline is 20% higher, plugging is ruled out or measures underperform.
- **Policy design shapes how far a fee reaches.** A fee on every measured tonne reaches 0.5% at about $1,400 per tonne (2025 dollars), and at the Waste Emissions Charge's level ($1,211 in 2025 dollars by 2035) it reaches about 0.52%. The Waste Emissions Charge as written applies to reported emissions above facility thresholds and delivers about 18% of the needed cut; basing it on measured emissions and widening coverage would extend its reach.
- **Large leaks are concentrated.** In five of the six basins with enough aircraft and satellite data, a tenth of large-leak sites release 43–49% of the methane those sites emit (San Juan: 33%).

## What's on the page

| Tab | Contents |
|---|---|
| Global Methane Map | Oil and gas methane in 34 basins in 21 countries measured by MethaneSAT (2024–25): leak rates and measured vs. inventory; country estimates from satellites (2023 and 2019) vs. what countries report to the UN; large leaks seen since 2024; UN leak alerts (UNEP MARS sites, whether each was reported to the government or operator and whether anyone replied); coal mines from UNEP's coal methane database (mostly steel-making coal) with coal alert sites; GHGSat's 2023 site emissions on a 1° grid; IEA 2025 country estimates as an option in the country view; a close-up of each basin with its measured area, Carbon Mapper large-leak sites colored by how often they leak, days imaged, oil and gas fields and 2023 gas flares |
| United States | Measured leak rates by basin today, measured vs. EPA inventory, cost to reach 0.5% by basin, policy scenarios, low-producing wells, clean-gas supply; interstate pipelines with EPA-reported compressor stations, storage and LNG; an optional coal layer (underground mines reporting methane to EPA, 2023, with satellite coal plume sites); close-ups of large-leak sites in nine basins, colored by how often they leak or by nearest infrastructure |
| Cost of reaching 0.5% in the US | US oil and gas value chain only (coal mine methane is not included). Least-cost abatement curve across 25 measures, 14 source categories and 19 basins; target slider; sensitivities and Monte Carlo range |
| Fees and rules | US oil and gas value chain only (coal mine methane is not included). EPA's OOOOb/c rules, the Waste Emissions Charge as written and alternatives, and combinations |
| Assumptions and data | Scope, methods, benchmark comparisons, limitations, downloads and sources |

![South Caspian close-up](docs/world_closeup.png)

![UN leak alerts](docs/world_alerts.png)

![Coal mines](docs/world_coal.png)

![GHGSat 2023](docs/world_ghgsat.png)

![United States](docs/map.png)

![Permian close-up](docs/permian.png)

![Cost of reaching 0.5% in the US](docs/cost.png)

## Publish with GitHub Pages

1. Create a public repository and upload the contents of this folder (keep the folder structure).
2. In the repository, go to **Settings → Pages**, set **Source** to "Deploy from a branch", and choose `main` and `/ (root)`.
3. The site will be live at `https://<your-account>.github.io/<repository-name>/` within a few minutes.

The `.nojekyll` file tells GitHub Pages to serve the files as they are.

**Optional: add the full workbook.** Save the analysis workbook as `data/methane_leakage_workbook.xlsx`. The "Full workbook" link on the Assumptions and data tab appears automatically once that file exists, and stays hidden until then.

**Embedding.** The page sends its height to a parent window (`cgep-embed-height` message), so it can be embedded in an iframe that resizes to fit.

## View locally

Open `index.html` in any browser. Everything, including the basin close-ups and the CSV downloads, is built into that one file. The `data` folder holds the same CSVs as separate files for anyone browsing the repository.

## Files

| Path | Contents |
|---|---|
| `index.html` | The whole page: markup, styles, scripts, model results, basin close-up map layers and the CSV downloads (no build step) |
| `data/cost_curve.csv` | Every measure in every basin, with tonnes cut and net cost |
| `data/basins.csv` | 2035 baseline, leak rate, and cuts on the cheapest path and under the WEC, by basin |
| `data/policies.csv` | Rules, fees and combinations |
| `data/scenarios.csv` | Sensitivities |
| `data/large_leak_sites.csv` | Large-leak sites in nine basins, 2024–26 (Carbon Mapper data; see licensing) |
| `docs/` | Screenshots used in this README |

## Methods in brief

- **Baseline.** Each basin's latest measured loss rate (MethaneSAT, MethaneAIR, AMI or EDF EI-ME) is held at today's level and applied to its 2035 production: EIA actual production from 2023 to 2025, then the AEO2026 Counterfactual Baseline to 2035, with each basin matched to its AEO region so basins in a region add up to its total; areas without a basin measurement follow AEO's Midcontinent region. Each basin's methane content of produced gas follows the measurement study (MacKay et al. 2026, Table S2; AMI for Appalachia). MethaneSAT basin-boundary rates, reported against gas sold, are converted to a share of gas produced. EDF EI-ME emissions in counties of basins that already carry a basin-wide rate are removed to avoid double counting. Scope covers production, gathering, processing, and transmission and storage, including unburned fuel from compressor engines; local distribution is excluded.
- **Costs.** Twenty-five measures cut emissions in sequence within each source category and basin. Costs are in 2025 dollars per metric tonne, annualized at 7% (3% as a sensitivity), start from today's equipment with no rules assumed, and net out the value of gas kept at AEO2026 2035 regional prices. Plugging low-producing wells is allowed, with site counts from Omara et al. 2022 (1.2 wells per site; low-producing sites average 1.03 wells).
- **Policies.** EPA's rules are mapped to the share of each measure they force. The Waste Emissions Charge is modeled on reported (subpart W) emissions with facility-level intensity thresholds and netting.
- **Basin close-ups.** Large-leak sites are Carbon Mapper "sources" observed January 2024 to October 2026 (aircraft and the Tanager-1 satellite). Dot size is the average rate when seen; color is the share of imaged days a site was leaking. The dots cover large leaks only and should not be summed into basin totals. Imaging coverage is approximate, counted from scene outlines.
- **Infrastructure matching.** Each large-leak site is matched to the nearest mapped infrastructure: a compressor station or plant within 200 m, else a well or tank battery within 100 m, else a pipeline within 50 m. The same sites moved 1–2 km in a random direction give the share expected by chance. OGIM maps gathering lines almost only in Texas.
- **Stations.** Transmission compressor stations, storage fields and LNG terminals are sized by methane reported to EPA for 2023. No measured leak rate exists for individual pipelines.

Full assumptions, benchmark comparisons and limitations are on the page's Assumptions and data tab. Three QA/QC passes (November 13, 2026), the second and third independent reviews, checked inputs against their sources and every calculation, a fourth pass verified the items the reviews could not, and a fifth independent review (November 17, 2026) checked the international data and every world-map view (`docs/qa_pass5_2026-11-17.md`); `docs/QA_QC.md` lists what was verified, what was corrected, what rests on judgment and what could not be checked.

## Sources

- **Measurement:** Omara et al. 2022 and 2024; Sherwin et al. 2024; MacKay et al. 2026; Williams et al. 2026, Atmospheric Chemistry and Physics 26, 5961–5981 (MethaneSAT); Appalachian Methane Initiative 2025 field campaign report (SLR International and EEMDL, March 2026); EDF EI-ME 2023
- **Inventory:** EPA Greenhouse Gas Inventory 2023; GHGRP subpart W
- **Production and prices:** EIA Annual Energy Outlook 2026 (Counterfactual Baseline); EIA Short-Term Energy Outlook (November 2026) and Natural Gas Annual/Monthly state gross withdrawals for 2023 to 2025
- **Large-leak sites and imaging coverage:** Carbon Mapper, Inc.
- **International basins:** Omara et al. 2026, Research Square preprint, Supplementary Data 1 (MethaneSAT regions); East et al. 2025, Nature Communications 16, 11004 and Shen et al. 2023, Nature Communications 14, 4948 (country estimates); Carbon Mapper plumes, sites and imaging; EDF OGIM v2.7 fields and flares; UNEP IMEO MARS sources, monthly top-50 lists and October 2026 snapshot (CC BY-NC-SA 4.0); UNEP IMEO Coal Methane Database (CC BY 4.0); OGMP 2.0 company file; IEA Global Methane Tracker 2026 and Methane Tracker data (CC BY 4.0); GHGSat 2023, Jervis et al. 2025 (CC0); Natural Earth borders
- **Well, station and pipeline locations:** EDF / MethaneSAT LLC, Oil and Gas Infrastructure Mapping (OGIM) database v2.7
- **Transmission compressor stations, storage and LNG facilities:** EPA Greenhouse Gas Reporting Program, subpart W, reporting year 2023 (Envirofacts)
- **Gathering-line emission factor:** Yu et al. 2022, Environmental Science & Technology Letters
- **Pipelines:** EIA natural gas interstate pipelines, via DOT National Transportation Atlas Database
- **Costs:** EPA regulatory impact analyses for OOOOb/c (2024) and the Waste Emissions Charge (2024); ICF for EDF (2014); ICF for ONE Future (2016)
- **Policy status:** CRS R48906 (April 2026); Holland & Knight on EPA's October 29, 2026 proposal
- **Base maps:** US Census Bureau boundaries via us-atlas

## Licensing

Third-party data in this repository carries its own license terms; see [DATA_LICENSES.md](DATA_LICENSES.md). In particular, the Carbon Mapper data (`data/large_leak_sites.csv` and the site layers built into `index.html`) is for non-commercial use under Carbon Mapper's Modified CC BY-SA 4.0 license, and any reuse must carry the same license and the attribution "Data by Carbon Mapper®".
