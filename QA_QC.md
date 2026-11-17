# Data QA/QC: Methane abatement database

Review dates: November 13, 2026 (passes 1 to 4) and November 17, 2026 (passes 5 and 6). Six passes:

- **Pass 1.** A self-review by the model's builder.
- **Pass 2.** An independent review by a separate reviewer who did not build the model. The reviewer re-derived inputs from the primary sources, read the code and workbook formulas, and traced every published number.
- **Pass 3.** A second independent review by a reviewer who had not built the model or done the earlier passes. It re-ran the whole pipeline, re-checked every pass-2 fix against its source, and tested the judgment calls.
- **Pass 4.** Verification of every item the first three passes listed as not verified, against primary sources and raw data.
- **Pass 5.** An independent review of the international data, the world-map views and the companion data Sheet, added after the cost model was settled. The US cost model is unchanged.
- **Pass 6.** Five independent reviewers covered the whole page, including the EU import rules tab added after pass 5, the companion Sheet and the public package. The US cost model re-ran with zero differences. Full report: `qa_pass6_2026-11-17.md`.

In passes 2 to 6 the builder checked each finding against the source before changing anything. This document supersedes the earlier versions.

## Bottom line

After four passes, the net cost of reaching 0.5% in 2035 is **about $2.7 billion a year** (2025 dollars). The published figure was $3.6 billion; pass 1 put it at $3.8 billion, pass 2 at $2.8 billion and pass 3 at $2.9 billion.

- **Baseline.** The 2035 baseline is 12,836 kt of methane, a 1.55% leakage rate. Today's rate (2023, wellhead to city gate) is 1.80%.
- **Cut needed.** 68% of 2035 methane (8.7 million tonnes).
- **Last tonne.** About $1,400. One measure in one basin sets it (leak repair and pneumatics at gathering stations in the Anadarko), and it moves with assumptions. Quote it as "about $1,400", with a range:
  - about $1,000 to $2,200 under most single changes;
  - far higher if the baseline is 20% higher ($5,700), plugging is ruled out ($6,500) or measures are 25% less effective ($11,100).
- **Uncertainty.** The median of 2,000 uncertainty draws is $3.8 billion; the central case sits at about the 23rd percentile.

**The main conclusions hold through all four passes.**

- A fee on every measured tonne gets closest to 0.5%. At the Waste Emissions Charge's level it reaches about 0.52%.
- The WEC as written delivers about 18% of the needed cut.
- Requiring every basin to meet 0.5% on its own costs nearly four times the national least-cost path. It is not like for like, because the national rate then ends at 0.55%.

**What pass 4 changed.** Verifying the open items found two errors, both corrected:

- **Wells per site.** The model's 1.16 wells per site has no source. It also applied EIA's share of low-producing *wells* (78%) to *sites*. Omara et al. 2022 give site-level figures: 1.2 wells per site overall, 81% of sites low-producing, and 1.03 wells per low-producing site. Plugging cost now uses 1.03 wells. Effect: −$197M.
- **Produced water.** EPA's inventory has 147.6 kt of gas-well produced water that the tanks and produced-water category (W4) left out. The well-site shares are recomputed from the GHGI 2023 annex. Effect: −$19M.

Every other open item checked out or is now bounded. See "Verification, pass 4".

**What pass 3 changed.** Pass 2's treatment of areas without a basin measurement (judgment call J3) was not robust:

- J3 grew those areas so that national production closed to AEO's Lower 48 total.
- The ×0.55 decline it produced came mostly from 2025-to-2035 growth series that did not match the basins they were applied to. It did not come from AEO's conventional decline.
- Pass 3 matches each basin to its AEO region, puts the unmeasured areas on AEO's Midcontinent series and drops the closure. That adds about $210 million.
- A smaller pass-3 fix takes off about $50 million.

**The two implementations agree.** The workbook's live formulas (revision 61) and the Python model agree to within 0.001% on every headline:

| Headline | Workbook | Python |
|---|---|---|
| Net cost | $2,712.47M | $2,712.47M |
| Marginal cost | $1,382.79 | $1,382.79 |
| Basin standard | $10,182.05M | $10,182.03M |

**Pass 3 also confirmed:**

- The pipeline reproduces from its inputs with zero differences.
- Every pass-2 fix (F1 to F11) is implemented as described in both implementations, with no arithmetic, unit or basis error.

## Headline results

| Result (2035, 2025$) | Published | After pass 1 | After pass 2 | After pass 3 | After pass 4 |
|---|---|---|---|---|---|
| Baseline methane, no new controls | 13,316 kt | 14,153 kt | 12,927 kt | 12,836 kt | 12,836 kt |
| Baseline leakage rate | 1.74% | 1.75% | 1.55% | 1.55% | 1.55% |
| Leakage rate today (2023, wellhead to city gate) | 1.96–1.98% | 1.93% | 1.80% | 1.80% | 1.80% |
| Cut needed for 0.5% | 9,482 kt (71%) | 10,106 kt (71%) | 8,750 kt (68%) | 8,698 kt (68%) | 8,698 kt (68%) |
| Net cost, cheapest national path | $3,648M/yr | $3,798M/yr | $2,771M/yr | $2,929M/yr | $2,712M/yr |
| Average net cost | $385/t | $376/t | $317/t | $337/t | $312/t |
| Last tonne needed | $2,960/t | $2,960/t | $1,661/t | $1,568/t (quote as about $1,600) | $1,383/t (quote as about $1,400) |
| Every basin to 0.5% on its own | $10,745M | $10,765M | $10,300M | $10,505M (ends at 0.55%) | $10,182M (ends at 0.55%) |
| Uniform fee at $1,211 on every measured tonne | 0.56% | 0.57% | 0.53% | 0.53% | 0.52% |
| WEC as written | 1.51% (18% of the cut) | 1.52% (18%) | 1.35% (19%) | 1.36% (18%) | 1.36% (18%) |
| OOOOb/c 2024 rules alone | 1.18% | 1.18% | 1.05% | 1.05% | 1.05% |
| OOOOb/c October 2026 proposal alone | 1.32% | 1.33% | 1.18% | 1.18% | 1.18% |
| 3% discount rate | $2,991M | $3,178M | $2,246M | $2,352M | $2,190M |
| No well plugging | $7,791M | $8,455M | $6,289M | $6,428M | $6,228M |
| Monte Carlo net cost, P10 / P50 / P90 | $2.7B / $5.4B / $13.0B | $2.8B / $5.8B / $13.7B | $2.2B / $4.0B / $9.8B | $2.3B / $4.1B / $10.2B | $2.2B / $3.8B / $9.8B |

## What moved the headline

Each fix was applied on top of the one before it. The last row of each table reproduces that pass's final model exactly.

### Pass 2

| Step | Baseline (kt) | Rate | Net cost ($M) | Last tonne ($/t) | Basin standard ($M) |
|---|---|---|---|---|---|
| After pass 1 | 14,153 | 1.75% | 3,798 | 2,960 | 10,765 |
| F1: EPA costs already per metric tonne | 14,153 | 1.75% | 3,697 | 2,960 | 10,677 |
| F2: each basin's own methane content | 14,569 | 1.69% | 3,312 | 2,200 | 10,755 |
| F3: no distribution taken out of EI-ME rows | 14,643 | 1.70% | 3,358 | 2,400 | 10,783 |
| F4: 2023-to-2025 growth matched to basins | 14,590 | 1.70% | 3,358 | 2,417 | 10,786 |
| F5: electrification cost rebuilt from its inputs | 14,590 | 1.70% | 3,358 | 2,417 | 12,338 |
| F6: plugging inputs in 2025 dollars | 14,590 | 1.70% | 3,531 | 2,417 | 12,866 |
| F7: San Joaquin basin production | 14,599 | 1.70% | 3,544 | 2,475 | 12,899 |
| F8: EI-ME double count removed (346 kt) | 14,191 | 1.65% | 3,335 | 1,848 | 11,825 |
| F9, F10: Sherwin shares, 78% low-producing, Alaska/offshore | 14,187 | 1.65% | 3,340 | 1,911 | 11,868 |
| J4: MethaneSAT basin-boundary rates | 13,795 | 1.61% | 3,182 | 1,661 | 11,070 |
| J3: unmeasured areas closed to AEO's Lower 48 total | 12,927 | 1.55% | 2,771 | 1,661 | 10,300 |

### Pass 3

| Step | Baseline (kt) | Rate | Net cost ($M) | Last tonne ($/t) | Basin standard ($M) |
|---|---|---|---|---|---|
| After pass 2 | 12,927 | 1.547% | 2,771 | 1,661 | 10,300 |
| R3-1: basins matched to AEO regions; unmeasured areas on AEO Midcontinent, no closure | 12,836 | 1.551% | 2,979 | 1,561 | 10,577 |
| R3-8: EPA values for unmeasured areas scaled to the same counties as EI-ME | 12,836 | 1.551% | 2,929 | 1,568 | 10,505 |

### Pass 4

| Step | Baseline (kt) | Rate | Net cost ($M) | Last tonne ($/t) | Basin standard ($M) |
|---|---|---|---|---|---|
| After pass 3 | 12,836 | 1.551% | 2,929 | 1,568 | 10,505 |
| V1: site counts from Omara et al. 2022 (1.2 wells per site, 81% low-producing, 1.03 wells per plugged site) | 12,836 | 1.551% | 2,732 | 1,383 | 10,245 |
| V2: well-site shares recomputed from GHGI 2023, gas-well produced water added | 12,836 | 1.551% | 2,712 | 1,383 | 10,182 |

## Pass 6: whole page (November 17, 2026)

Five independent reviewers each took one area: the EU tab's inputs and maths; its fee, reach, coal and crude-by-field models; the Global Methane Map; the US model and tabs; and the Sheet, package and rendering. The full report is `qa_pass6_2026-11-17.md`.

- **US cost model unchanged.** It re-ran with zero differences, and all US headlines stand. Two disclosures were added: the WEC exemption's second statutory condition, and the fact that basin counts of low-producing sites use a national share. A dozen wording and display fixes were also made.
- **EU tab: one input error, corrected.**
  - Guyana's 13.0 Mt of crude was missing from the Eurostat download, and 11.8 Mt of crude with no named origin had been dropped.
  - After the fix, EU imports are 29.7 EJ (was 28.6), with 5.3 Mt of methane (was 5.2).
  - The EU, Japan and South Korea figure is 7.4 Mt, or 9.2% (was 7.3 Mt, 9.0%).
  - The 0.2% benchmark is now 38 g/GJ, the share-of-gas basis actually discussed (was 36 g/GJ).
  - Partial-year crude volumes are labelled, and the Basrah basin match is qualified.
  - Titles and caveats on the crude, coal and fee panels are made two-sided.
- **Global Methane Map.** All pass-5 fixes were confirmed. Fixes in this pass:
  - Source labels for five Gulf countries (Chen et al. 2023).
  - A "reply not tracked" alert status.
  - Median rather than mean leak rates.
  - EMIT detections disclosed.
  - Further legend, label and licence fixes.
- **Sheet (revision 97) and package.** The EU tabs were updated. Data issues gained four entries (59–62) and eight corrected rows. Local paths were removed from the public record, and the licences and screenshots were completed.

## Pass 5: international data and world map (November 17, 2026)

An independent review re-read every international input file (UNEP MARS sources, plumes, top-50 lists and response-rate files; OGMP 2.0; IEA Methane Tracker 2026; GHGSat 2023; UNEP Coal Methane Database; EPA subpart FF; MSHA; Carbon Mapper) and drove every world-map view at desktop and phone widths. The full report is `qa_pass5_2026-11-17.md`.

Corrected:

- **Large leaks since 2024.** Plumes are now counted one by one in the country they fall in, instead of by the country at the centre of each 1° square. US 5,248 (was 5,120), Turkmenistan 1,979 (1,701), Mexico 96 (177), Kuwait 88 (31). 67 countries and territories, 45% of plumes in the US.
- **UN alerts reply rates.** Five countries showed "0% of NaN sites"; rates and denominators now come from UNEP's response-rate file.
- **US coal mines.** Pride Mine (KY) carried a Utah mine's output; mines now use the most recent valid in-state MSHA ID (57 of 58 matched to production). One doubtful UNEP-to-EPA match dropped (18 matched mines; UNEP 356 kt vs EPA 380 kt). Gibson County status corrected to Active.
- **Workbook.** The UNEP ÷ EPA column in the US coal mines tab was blank (formula pointed at the wrong column); fixed. Data issues, Sources and the MARS snapshot footnote updated.
- **Smaller fixes.** GHGSat cells counted once where oil and gas and coal overlap; rounding noise and singular/plural in tooltips; "May 2024 to June 2025" for the MethaneSAT regions; UNEP-alerts caveat reworded; Sources list completed with licences; "less than 0.01 points" on the Fees tab.

The US cost model and its outputs are unchanged since pass 4.

Not verified: values read from chart images (IEA intensities, the IEA top-10 notification chart, MARS focal points and confirmed mitigations), which are labelled as chart readings; Leer South has no MSHA production match.

## Verification, pass 4

| Item | Result | Source |
|---|---|---|
| 1.16 wells per site | **Error, corrected (V1).** No source gives 1.16. The model also applied EIA's share of low-producing wells to sites | Omara et al. 2022, Nature Communications 13:2085: 842,978 active onshore wells (2019); 565,000 low-production sites, 81% of sites; 1.03 wells per low-production site, 1.9 per other site, 1.2 overall |
| 78% of wells at 15 BOE/d or less | Verified, but it is a share of wells. The model now uses Omara's 81% share of sites | EIA, Distribution and Production of Oil and Gas Wells (December 2025): 78% of more than 918,000 wells in 2024 |
| Well-site source shares | **Error, corrected (V2).** Gas-well produced water (147.6 kt) was missing from W4 | GHGI 2023 annex Table 3.6-1; new shares W2 0.495, W3 0.216, W4 0.143, W5 0.024, W6 0.122 |
| Raimi et al. 2021, $76,000 | Verified as the mean of plugging plus surface reclamation, 2019 dollars (n = 1,527); the median is $52,629. The abstract's "median" label is wrong | Raimi et al. 2021, ES&T 55:10224, Table 2 |
| Williams et al. (MethaneSAT) | Now published. Every rate the model uses is unchanged: Permian 2.6% domain and 2.5% basin; Eagle Ford 2.4% and 1.9%; San Joaquin 12.1% and 15.5%; Texas 338 t/h (3.1%); New Mexico 67 t/h (1.3%) | Williams et al. 2026, Atmospheric Chemistry and Physics 26, 5961–5981 (May 5, 2026) |
| Reeves County, 49 t/h, about 10 times EPA's gridded inventory | Verified | Williams et al. 2026, sections 3.3 and 4 |
| CRS R48906 | Verified: April 15, 2026 (Ramseur) | The report confirms that P.L. 119-21 moved the WEC to 2034; that H.J.Res. 35 (P.L. 119-2, March 14, 2025) disapproved EPA's WEC rule; and that EPA's suspension of subpart W reporting to 2034 is still a proposal |
| EPA policy status | Verified | April 9, 2026 final rule on temporary flaring (72 hours) and net heating value, 91 FR 18056. October 29, 2026 proposal, 91 FR 68234; comments due December 16, 2026. The GHGRP reconsideration is not finalized; reporting for 2025 is extended to March 10, 2027 |
| EPA gridded allocation to basins | Reproduced exactly from raw data: every EPA upstream and midstream value in Basin Baseline (columns G and H). National upstream 4,567 kt plus Alaska and offshore 193.5 kt equals the GHGI's 4,760.5 kt. Still the builder's method, not an EPA product | EPA 2020 gridded GHGI (NetCDF); GHGI 2023 annex Tables 3.5-14 and 3.6-18 |
| Study boundaries (R3-7) | Bounded both ways (see below) | MacKay et al. 2026 (EIA basin boundaries; Enverus production); AMI 2025 section 3.1.2; subpart W 2023 production by AAPG basin |

**Study boundaries.** MacKay et al. take basin boundaries from EIA and production from Enverus, and neither boundary file is public. But each study's production total can be compared with subpart W production by AAPG basin, which is what the overlap removal uses:

| Basin row | Study production (Bcf, 2023) | Subpart W reporters, AAPG basins (Bcf) |
|---|---|---|
| Haynesville-Bossier | 5,898 | 5,895 (AAPG 230 + 260) |
| Anadarko | 2,052 | 1,973 (360) |
| Bakken | 1,200 | 1,176 (395) |
| Denver-Julesburg | 1,098 | 1,100 (540) |
| Piceance, Uinta | 438, 276 | 430, 240 (595, 575) |
| Appalachia (AMI) | 13,002 | 12,863 (160 + 160A) |
| Eagle Ford | 2,922 | 2,731 (220) |
| Barnett | 864 | 367 (420); 801 with Strawn (415) |
| Arkoma-Fayetteville | 378 | 603 (345) |

For most rows the study totals match the whole AAPG basin. So the counties pass 3 doubted in Kansas, south Arkansas, Louisiana and Nebraska sit inside the production the rates are applied to, and removing their EI-ME emissions is right.

- **Narrower than assumed.** About 119 kt in New York and the southern fringe of Appalachia (Tennessee, Kentucky, Virginia, Alabama, Georgia, Maryland, New Jersey) may lie outside AMI's Marcellus–Utica boundary. AMI says that boundary extends into New York, Kentucky and Virginia. Arkoma is also narrower than AAPG 345 (6.8 kt).
- **Wider than assumed.** The Barnett row is wider than AAPG 420. It probably includes the Bend Arch, which holds 109 kt of EI-ME emissions that are not removed now.
- **Effect.** Restoring the 119 kt gives $2.78B. Removing the 109 kt gives $2.65B. The page now gives both.

## Corrections, pass 3

**R3-1. Growth matched to AEO regions (high; replaces J3).**

- **The problem.**
  - Pass 2 matched the 2023-to-2025 growth to whole-basin series but not the 2025-to-2035 growth.
  - J3 then closed national production to AEO's Lower 48 total, so every mismatch landed on the unmeasured areas.
  - Their ×0.551 was the difference of two large numbers: 50,025 less 48,358 Bcf.
  - A 1% change in Appalachia's 2035 production would have moved the residual to ×0.617 and the net cost by 3%.
- **The fix.** Rows that make up an AEO region (AEO2026 cb2026, Table 59) now add up to it:

| Row | 2025-to-2035 growth | Basis |
|---|---|---|
| Permian | ×1.058 | Southwest less Barnett: (9.449 − 0.587) ÷ (8.965 − 0.589) |
| Eagle Ford | ×0.894 | Gulf Coast less the Haynesville row (which keeps ×1.140) |
| Greater Green River, Piceance, Uinta, San Juan, Powder River | ×0.431 | Rocky Mountain less the DJ row (which keeps Niobrara ×1.117) |
| Other basins and areas with no reporters | ×1.038 | AEO Midcontinent, 2.957 ÷ 2.848, no closure |

- **The judgment that remains.** Unmeasured areas have no AEO series of their own, so the growth assigned to them is a choice. On pass-4 numbers the alternatives are:
  - AEO conventional gas (×0.44): $2.22B;
  - AEO Lower 48 onshore (×1.15): $2.78B;
  - five Rockies rows at the regional rate (×0.66): $2.85B.
- **A pass-2 sentence was wrong.** Pass 2 said the ×0.55 was "consistent with AEO's falling conventional and coalbed output". It came from the closure, not from those series.

**R3-8. EPA values for unmeasured areas (low).** F8 cut the measured emissions for the two unmeasured rows by 19%, but the EPA values that set their emission-density ratio still covered all the counties. Both EPA values are now scaled by the same 0.809. Effect: −$50M.

**Page, package and workbook fixes.**

| ID | What was wrong | Fix |
|---|---|---|
| R3-2 | Map said plugging the highest-emitting fifth of low-producing sites is "on the cheapest path everywhere" | Now "in most basins", naming the exceptions |
| R3-3 | README Permian screenshot showed the pre-J4 rate (2.6%, 386 t/h) | Re-shot (2.4%, 353 t/h) |
| R3-4 | Basin-by-basin standard compared with the national path as if both reach 0.5% | Page says it is not like for like and ends at 0.55% nationally |
| R3-5, R3-6 | Workbook Scenarios shortfall column and Results C26 note stale | Refreshed |
| R3-10 | Low-gas-price scenario mixed $/MMBtu and $/Mcf, and 16 of 19 prices had no source | Now uses AEO2026 Table 59 2025 regional prices |
| R3-11 | Observation-domain reversal paired San Joaquin's domain rate with basin production | Reversal now covers Permian and Eagle Ford only |
| R3-12 | $0.075/kWh undisclosed against the 2025 US industrial average (8.49¢, STEO Table 7c) | Disclosed; at 8.5¢ the national cost is unchanged and the basin standard is about 9% higher |
| R3-13 | Old "+130%, Enverus" label still shipped in the page data | Removed |
| R3-14 | AMI and MethaneSAT citations misdated or misattributed; STEO missing from the page's sources | Corrected (see Sources below) |
| R3-15 | Last-tonne range left out the +20% baseline case | All three high cases named |
| R3-16 | Permian close-up shows the basin at 353 t/h beside Texas 338 + New Mexico 67 t/h | Caveat: state figures are MethaneSAT's whole 2024–25 observation area, past the basin edge |

**Disclosed, not changed.**

- **R3-7, EI-ME overlap.** Pass 3 called the 346 kt removed in F8 an upper estimate. Pass 4 compared each study's production with AAPG basin production and found the uncertainty runs both ways: −119 kt to +109 kt, or $2.65B to $2.78B (see "Verification, pass 4").
- **R3-9, well-site shares.** Corrected in pass 4 (V2).
- **R3-17, reporter-only production.** San Juan, Powder River and other basins with reporters use reporters' production only. The national path is unaffected; the basin standard is affected. Disclosed on the page.
- **R3-18, GHGRP Other row.** It is 117.5 kt against 119.3 kt in the raw data. This has no effect on results and is left as is.

## Corrections, pass 2 (all confirmed in passes 3 and 4)

**F1. EPA costs were already per metric tonne (high).**

- Every EPA figure reproduces as RIA Table 5-6 present-value cost ÷ Table 5-5 short tons × 1.2598 × 1.10231.
- The 1.2598 is undiscounted ÷ present-value tonnes at 2% (Table 2-9; reproduced at 1.25978). The 1.10231 converts short tons to metric tonnes.
- The pass-1 "short ton" conversion counted the conversion twice and was reversed.
- Transmission and storage use $565, derived the same way.

**F2. Each basin's own methane content (high).**

- MacKay et al. 2026 Table S2 values run from 0.47 in the Bakken to 0.96 in Arkoma; the model had used 0.80 everywhere.
- For Appalachia, AMI's figures imply 0.914.
- MethaneSAT rates keep Williams et al.'s 0.80 convention to recover emissions. The Eagle Ford denominator uses MacKay's 0.73.

**F3. Distribution.** Distribution is no longer subtracted from EI-ME rows, which exclude it. Appalachia removes AMI's own 10.8 kt.

**F4. 2023-to-2025 growth.** It now uses STEO Table 5a whole-basin series and state ratios; the 2025-to-2035 leg was fixed in pass 3 (R3-1).

**F5. Electrification cost.**

- It is rebuilt from its inputs: ($700/hp × CRF(7%, 20) + 6,280 kWh × $0.075) ÷ 0.0386 t = $13,914/t.
- Capital is about 12% of that cost.

**F6. Plugging in 2025 dollars.**

- Raimi et al. 2021's $76,000 is the mean, in 2019 dollars (confirmed in pass 4), now ×1.24.
- The second-tier lost margin of $25,000 is from EPA RIA Table 4-9, now ×1.054.
- Pass 1 called the older-dollar figure "conservative". That was wrong.

**F7. San Joaquin production.** It now uses EIA California 2023 gross withdrawals from oil and shale wells (109.9 Bcf).

**F8. EI-ME double count.**

- Emissions in counties inside measured AAPG basins are removed: 346 kt, assigned with EPA's subpart W basin-county table.
- See R3-7 and pass 4: the overlap is uncertain both ways.

**F9. Sherwin shares.** They now come from each basin's latest campaign, with partial detections.

**F10. Small corrections.**

- 78% of wells are low-producing (replaced in pass 4 by Omara's 81% of sites).
- Alaska and offshore use AEO's ×1.043.
- The deflator is 1.384.
- Marketed ÷ gross is 0.971.

**F11. WEC threshold basis.**

- Thresholds now apply to gas volume, as CAA §136(f) sets them, not methane. Gas sent to sale is 0.971 of gross.
- Sigma and the revision factor (×1.72) are recalibrated to EPA's targets.
- On 2023 reported emissions, the method gives 862 kt above threshold and 647 kt after netting, against EPA's 890 and 670 kt for 2024.

**J4. MethaneSAT basin-boundary rates (judgment, confirmed sound in pass 3).**

- The rates are Permian 2.5%, Eagle Ford 1.9% and San Joaquin 15.5%. They match the basin-wide production they are applied to.
- MethaneSAT observed about 66% of Eagle Ford production, so applying its rate to the whole basin extrapolates over about a third.
- Domain rates for Permian and Eagle Ford give $2.84B on pass-4 numbers.

## Corrections, pass 1 (re-checked in passes 2 to 4)

| ID | What | Status |
|---|---|---|
| P1-1 | 2023 emissions grown with 2025-to-2035 growth only | Kept; series refined (F4, R3-1) |
| P1-2 | MethaneSAT rates converted from marketed to gross gas (TX 0.932, NM 0.992, CA 0.990; Permian 0.952) | Kept; ratios verified |
| P1-3 | "EPA costs are per short ton" | **Reversed (F1)** |
| P1-4 | Gathering-station cost weighted by tonnes ($746) | Kept; verified |
| P1-5 | Plugging uses 1.16 wells per site | **Replaced in pass 4 (V1):** 1.03 wells per low-producing site; $76,000 now in 2025 dollars (F6) |
| P1-6 | Electrification capital share 15% | Replaced by 12% (F5) |
| P1-7 | WEC reporting-revision factor | Recalibrated to ×1.72 (F11); a calibration, not an EPA number |
| P1-8 | Map "today" figures exclude distribution | Kept |

## Assumptions without a direct source, disclosed on the page and in the workbook

- **Rates held flat.** Measured rates stay flat to 2035. A 20% lower baseline gives $1.9B; a 20% higher one gives $4.7B.
- **Growth of unmeasured areas.** These areas follow AEO Midcontinent (R3-1). The alternatives run from $2.2B to $2.9B.
- **Plugging.** Plugging is costed as accelerating an obligation: interest on $97,000 per site over 15 years (1.03 wells per site), plus lost margin.
  - The first tier's $1,000 per site-year lost margin is an assumption. At EPA's average for low-producing gas wells ($5,950), the cost is $3.12B.
  - The least-cost path plugs about 88,000 sites (91,000 wells).
- **EPA inventory by basin.** This is the builder's allocation, not an EPA product: EPA's 2020 gridded inventory, assigned by reporter counties, trended to 2023 and scaled to EPA's 2023 totals. It sets the source mix and cost rescaling within basins.
- **Site counts.** Site counts are held at 2023 well counts. The wells-per-site ratios are Omara et al.'s, from 2019 data.
- **Thin measurements.** Bakken, Arkoma and Barnett rest on one aircraft flight each. San Juan uses TROPOMI 2018–20.
- **Measures without a direct cost study.** These are W1b, W3b, W6a, G3a, T3a, G4b, T4b, M1a and M1b. Five more blend EPA and ICF figures into round numbers.
- **Rules and fee.** Shares forced by EPA's rules and the WEC reporting credits are assessments of the rule text. "As finalized, 2024" does not include EPA's April 2026 amendments.
- **Uncertainty draws.** Half the Monte Carlo draws switch off the emission-density adjustment.
- **Power price.** $0.075/kWh sits between the West South Central (6.3¢) and Mountain (7.9¢) industrial averages, below the US average (8.5¢).

## Verified against primary sources (any pass)

- **Measurements.**
  - MacKay et al. 2026: Tables 1, 3 and S2.
  - AMI 2025 field campaign report: 1,214.2 kt, 235,458 kt, 0.52%, 10.8 kt distribution, Table 3-3.
  - Williams et al. 2026 (MethaneSAT), published version: domain and basin-boundary rates, Texas 338 t/h (3.1%), New Mexico 67 t/h (1.3%), Reeves County 49 t/h.
  - Omara et al. 2022: wells per site and the share of low-producing sites.
  - Shen et al. 2022 (San Juan).
  - Sherwin et al. 2024 Table 24.
  - EDF EI-ME 2023, recomputed from the NetCDF.
- **EIA and AEO.**
  - EIA gross, marketed and dry production 2020–2025.
  - STEO November 2026 Tables 5a, 7c and 10b.
  - AEO2026 cb2026 Tables 13, 14, 59 and 60, including the 2025 regional prices used in the low-price scenario.
  - Henry Hub 2025 $3.52/MMBtu.
  - Waha 2025 $1.15/MMBtu.
- **EPA.**
  - OOOOb/c RIA Tables 2-5, 2-9, 3-3, 4-9, 5-5 and 5-6.
  - WEC RIA Tables 1-1, 2-1, 4-3 and 8-1.
  - GHGI 2023 annex Tables 3.5-2 and 3.6-1, including all five well-site shares.
  - EPA 2020 gridded inventory, re-run to reproduce every basin allocation.
  - Subpart W basin-county table.
- **New in pass 3.**
  - GHGRP reported emissions by basin (Basin Baseline column K), recomputed from 49,948 raw subpart W rows: all named rows match to 0.1 kt.
  - Gathering, processing and transmission category shares reproduce exactly.
  - 713 stations and 163 kt on the map.
  - The "too few for a close-up" counts.
  - Texas and New Mexico t/h.
  - Social cost of methane ($2,800, 2019$).
- **Costs and prices.**
  - ICF for EDF 2014.
  - Raimi et al. 2021, Table 2.
  - BEA GDP price index.
  - IPCC AR6 GWP100 29.8.
- **Policy.**
  - WEC statute.
  - P.L. 119-21.
  - CRA disapproval of EPA's WEC rule (March 14, 2025).
  - EPA's April 9, 2026 final rule and October 29, 2026 proposal.
  - CRS R48906 (April 15, 2026).
  - The GHGRP reconsideration is still a proposal.
- **New in pass 4.**
  - EIA well distribution: 78% of wells at 15 BOE/d or less (2024).
  - Study production totals compared with subpart W production by AAPG basin.

## Not verified

- **Exact study boundaries.** MacKay's basin polygons and Enverus production are not public. The comparison of production totals bounds the effect at $2.65B to $2.78B.
- **Measures without a direct cost study, and the assumptions listed above.** These are disclosed as assumptions; there is no source to verify them against.

Recommendation: before formal publication, have a second reader spot-check the pass-4 changes and the boundary comparison.

## Sources cited for measurement

- MacKay et al. 2026.
- Williams et al. 2026, Atmospheric Chemistry and Physics 26, 5961–5981 (MethaneSAT).
- Appalachian Methane Initiative 2nd Annual Report, prepared by SLR International with EEMDL, March 2026.
- Sherwin et al. 2024.
- Omara et al. 2022 (low-production well sites) and 2024.
- EDF EI-ME 2023.

## Files updated in pass 4

- **Python model.** model.py (wells per site, low-producing share of sites, plugging cost, well-site shares) and build_outputs.py (records the central case's percentile).
- **Workbook (revision 61).**
  - Measures B18, B19, C31:C35, K59:K60 and the notes.
  - All snapshot sheets.
  - Read Me.
- **Web page.** Model and map data, figures, methods and limitations, benchmark table, sources and CSVs.
- **GitHub package.** index.html, README, CSVs, screenshots and this file.

## Files updated in pass 3

- **Python model.** model.py, scen_defs.py (new), build_outputs.py, scen_full.py, fee_detail.py and make_csvs.py.
- **Workbook (revision 59).**
  - 2035 Baseline growth column.
  - Basin Baseline G29, H30.
  - All snapshot sheets, including Scenarios with the shortfall column and the extra scenario rows 31–35.
  - Read Me, Results C23 and C26, and the Measures power-price note.
- **Web page.** Model and map data, figures, methods and limitations, sources, CSVs.
- **GitHub package.** index.html, README, CSVs, all four screenshots and this file.
