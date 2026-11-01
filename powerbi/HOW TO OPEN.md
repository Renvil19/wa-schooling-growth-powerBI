# How to open this report

1. Unzip this folder somewhere on your computer, such as Documents.
2. Open **Power BI Desktop**, then choose **File → Open → Browse** and pick **WA Schooling Growth.pbip**.
3. The visuals will be empty at first. Click **Home → Refresh** to load the data. It's built into the file, so there's no file path or sign-in to set up.
4. To get a single file for GitHub, choose **File → Save as**, pick **.pbix**, and name it `WA_School_Growth.pbix`.

If Power BI says it can't open the project, go to **File → Options and settings → Options → Preview features**, tick these three, restart Power BI Desktop and try again:
- Power BI Project (.pbip) save option
- Store semantic model using TMDL format
- Store reports using enhanced metadata format (PBIR)

## What's inside

- **Data (Power Query):** `CensusRaw` and `SchoolsRaw` hold the cleaned census and schools data. The other tables are reshaped from them (unpivoted stages, metro/country areas, year levels).
- **Model:** a star schema. `DimYear` and `DimSector` filter every fact table, and `Schools` filters `SchoolLevels`.
- **Measures:** in the `_Measures` table (growth, growth %, schools added, students per school, non-government share, change on the year before, stage growth, metro/country index).
- **Pages:** Overview · Growth drivers · 2026 snapshot

## Check values (no slicers applied)

| Measure | Expected |
|---|---|
| Students Latest Year | 507,395 |
| Students First Year | 467,317 |
| Student Growth % | +8.6% |
| Schools Added | +21 |
| Students per School (2020 / 2026) | 414 / 441 |
| Non-govt Share Latest Year | 34.7% |
| Stage Growth % – Years 11-12 | +18.9% |
| Area Index 2026 – Metropolitan / Country | 110.2 / 102.3 |
