# Data licenses and attribution

This repository combines original analysis with third-party data. Each third-party source keeps its own terms.

## Carbon Mapper (large-leak sites and imaging coverage)

Files: `data/large_leak_sites.csv`; the site and imaging-coverage layers in the basin close-ups built into `index.html`.

Data by Carbon Mapper®. Carbon Mapper data is provided for non-commercial purposes under the Carbon Mapper Modified Creative Commons Attribution ShareAlike 4.0 International Public License:
https://assets.carbonmapper.org/documents/Carbon-Mapper-Modified-Creative-Commons-License-21-11-09.pdf

Terms of use: https://carbonmapper.org/terms

- Use is limited to non-commercial purposes.
- Any use, reproduction or adaptation must credit "Data by Carbon Mapper®".
- Adapted versions of these files must be shared under the same license.

Retrieved from the Carbon Mapper API (sources and scenes endpoints) on November 12, 2026, covering observations from January 2024 to October 2026.

## Global Methane Map tab

- **Carbon Mapper plumes, sites and imaging coverage** (world map and basin close-ups): oil and gas plumes, sources and scene outlines from the Carbon Mapper API (annotated plumes, sources and annotated scenes endpoints), retrieved November 17, 2026, January 2024 onward. Same license and attribution as above: non-commercial, "Data by Carbon Mapper®", share-alike.
- **Oil and gas fields and 2023 gas flares** (basin close-ups): EDF / MethaneSAT LLC OGIM v2.7 (CC BY 4.0, see below); flares are VIIRS satellite detections as compiled in OGIM.
- **MethaneSAT regions:** region outlines and values from the supplementary data of Omara et al. 2026, "Satellite-derived methane emissions reveal persistent gaps in global oil and gas mitigation performance" (Research Square preprint). Published summary values and outlines, cited with attribution; check the preprint page for its license before reusing them beyond this page. These are not MethaneSAT Level 3 or Level 4 gridded data.
- **Country estimates:** East et al. 2025, Nature Communications 16, 11004 (2023 values, Supplementary Data S1) and Shen et al. 2023, Nature Communications 14, 4948 (2019 values), both open access, with national reports to the UNFCCC. Figures are cited from the papers' published tables.
- **UN leak alerts** (world map view and close-up overlay): UNEP International Methane Emissions Observatory (IMEO), Methane Alert and Response System (MARS) detected-sources file and October 2026 snapshot, methanedata.unep.org. Licensed under Creative Commons BY-NC-SA 4.0 (non-commercial, share-alike): credit "UNEP's International Methane Emissions Observatory" and note changes. Changes here: oil and gas sources only, country names harmonized, counts aggregated by country; reply rates use only sources for which UNEP tracks feedback. Alert contacts and confirmed fixes are read from the October 2026 snapshot's charts; reply rates come from UNEP's response-rate files.
- **Coal mines** (world map coal view): UNEP (2026), International Methane Emissions Observatory's Coal Methane Database, May 2026 (V2) release, CC BY 4.0, with data from Global Energy Monitor and Ember. Coal alert sites from the MARS sources file (CC BY-NC-SA 4.0, as above).
- **Company reporting:** OGMP 2.0 company performance file (UNEP), counts of upstream members and Gold Standard status by headquarters country. Credit "OGMP 2.0 / UNEP"; no license statement in the file.
- **2025 country intensities:** IEA (2026), Global Methane Tracker 2026, CC BY 4.0, values read from the chart "MethaneSAT and IEA estimates of methane emissions intensities by country, 2025" (MethaneSAT intensities provided to the IEA by EDF).
- **IEA country estimates, 2025:** IEA (2026), Methane Tracker data (emissions by production source and oil and gas abatement), CC BY 4.0. Values shown as published; "IEA ÷ reported" ratios are our calculation.
- **GHGSat 2023:** Jervis et al. 2025, Science; data on Dryad (doi:10.5061/dryad.rxwdbrvkp), CC0. The 0.2° grid is summed into 1° squares and, for country totals, assigned to countries by Natural Earth borders.
- **UN response rates:** UNEP IMEO MARS response-rate files (rolling 12-month windows, Jan 2025–Aug 2026), CC BY-NC-SA 4.0.
- **Borders:** Natural Earth 1:50m (public domain).

## US coal mines layer (map tab)

- **Methane by mine:** EPA Greenhouse Gas Reporting Program, subpart FF (underground coal mines), reporting years 2011–2023, via EPA Envirofacts. US government work, public domain.
- **Coal mined and mine status:** Mine Safety and Health Administration open government data (Mines and MinesProdYearly files). Public domain.
- **Coal plume sites:** Carbon Mapper sources, sector 1B1a (same license and attribution as above: non-commercial, "Data by Carbon Mapper®", share-alike) and UNEP IMEO MARS sources (CC BY-NC-SA 4.0).

## EDF / MethaneSAT LLC, OGIM database v2.7 (well density)

Files: the well-density layers and infrastructure matches in the basin close-ups built into `index.html`.

O'Brien, M., Omara, M., Himmelberger, A., and Gautam, R. (2025). Oil and Gas Infrastructure Mapping (OGIM) database (OGIM_v2.7). Zenodo. https://doi.org/10.5281/zenodo.15103476

Licensed under Creative Commons Attribution 4.0 (CC BY 4.0). Well counts here exclude wells listed as abandoned or proposed and are aggregated to grid cells.

## US Energy Information Administration (pipelines, production, prices)

Interstate natural gas pipeline routes (via the DOT National Transportation Atlas Database) and Annual Energy Outlook 2026 data are US government works in the public domain.

## US Environmental Protection Agency (compressor stations, storage, LNG)

Greenhouse Gas Reporting Program subpart W facility data, reporting year 2023, from EPA Envirofacts. US government work in the public domain.

## US Census Bureau (state and county boundaries)

Boundaries from Census cartographic files, as packaged by us-atlas (ISC license). Census data is in the public domain.

## Published studies

Basin leak rates and Texas/New Mexico totals are figures reported in the published studies listed in the README. They are cited, not redistributed as datasets.

## MethaneSAT gridded data

Not included. MethaneSAT Level 3 and Level 4 data may not be redistributed in raw form under its terms of use.
