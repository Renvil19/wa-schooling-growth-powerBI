# WA School Enrolment Growth Analysis (2020–2026) | Power BI

A business analysis of how Western Australian school enrolments have changed from 2020 to 2026: **where students are growing, which sectors they are moving to, and whether school capacity is keeping up.**

<!-- TODO: Replace with your own dashboard screenshot -->
![Dashboard overview](images/dashboard-overview.png)

---

## Business question

> **Is WA's school network keeping pace with enrolment growth, and where is the pressure building?**

Supporting questions:
1. How fast are total enrolments growing compared with the number of schools?
2. Is growth concentrated in metropolitan Perth or spread across country WA?
3. How is the split between public and non-government schools changing?
4. Which year levels are driving growth?

---

## Key findings

| Measure | 2020 | 2026 | Change |
|---|---:|---:|---:|
| Total students | 467,317 | 507,395 | **+8.6%** |
| Total schools | 1,129 | 1,150 | **+1.9%** |
| Students per school (average) | 414 | 441 | +27 |
| Metro students | 370,536 | 408,392 | **+10.2%** |
| Country students | 96,781 | 99,003 | **+2.3%** |
| Non-government share of students | 32.1% | 34.7% | +2.6 pts |

**1. Enrolments are outgrowing the school network.**
Student numbers rose 8.6% while schools rose only 1.9%, so the average school now serves 441 students, up from 414. Country WA added no schools at all (410 in both years).

**2. Growth is concentrated in Perth.**
Metro enrolments grew 10.2% versus 2.3% in country WA, and metro's share of all students rose from 79.3% to 80.5%. Public country enrolments actually **fell 2.7%**.

**3. Families are shifting toward non-government schools.**
Non-government enrolments grew **17.5%** versus **4.3%** for public schools. With only 6 new non-government schools, their average size jumped from 482 to 556 students (+15%).

**4. Senior secondary is the fastest-growing stage.**
Years 11–12 grew **18.9%** and Years 7–10 grew **11.5%**, while kindergarten fell 1.6%. Public kindergarten fell **8.7%**, while non-government kindergarten grew 16.0%.

---

## What this means (for planners and decision-makers)

- **Secondary capacity in metro Perth** is the most likely pressure point over the next few years, as the larger primary cohorts move up.
- **Falling public kindergarten numbers** could reduce public primary demand later in the decade and are worth monitoring alongside non-government growth.
- **Country public schools** face gradual decline in enrolments, which raises questions about resourcing and service models rather than new capacity.

*These are observations from sector-level data, not forecasts. See Limitations.*

---

## Data

| Item | Detail |
WA|DATA|GOV
| File | `wa_census_2020_2026.csv` (14 rows: 7 years × 2 sectors) |
| Source | <!-- TODO: confirm and link, e.g. WA Department of Education, Student Census (Semester 1) --> **[DATAWA.GOV]** |
| Fields | year, sector, schools, enrolments by stage (kindergarten, pre-primary, Years 1–6, 7–10, 11–12), total, metro and country schools/students |

**Data quality checks performed:**
- Year-level enrolments sum exactly to `total` for every row.
- `metro_students + country_students = total` for every row.
- `metro_schools + country_schools = schools` for every row.

---

## Approach

<!-- TODO: Edit this section so it describes exactly what YOU did in Power BI. Delete anything you didn't do. -->

   ```DAX
   Total Students = SUM(wa_census[total])
   Students per School = DIVIDE([Total Students], SUM(wa_census[schools]))
   Growth vs 2020 % =
       VAR Base = CALCULATE([Total Students], wa_census[year] = 2020)
       RETURN DIVIDE([Total Students] - Base, Base)
   Non-Gov Share % =
       DIVIDE(CALCULATE([Total Students], wa_census[sector] = "Non-government"), [Total Students])
   ```
4. **Visuals:** [list yours, e.g. KPI cards, line chart of enrolments vs schools, metro vs country comparison, stacked bar by stage, sector share trend].

---

## Dashboard

<!-- TODO: Add 2–3 screenshots to an /images folder and update the paths below -->

| Overview | Metro vs Country | Sector & Year Level |
|---|---|---|
| ![](images/dashboard-overview.png) | ![](images/metro-country.png) | ![](images/sector-stage.png) |

---

## Repository structure

```
wa-schooling-growth-powerBI/
├── README.md
├── wa_census_2020_2026.csv      # source data
├── WA_School_Growth.pbix        # Power BI report  <!-- TODO: upload -->
└── images/                      # dashboard screenshots  <!-- TODO: upload -->
```

To explore the report, download the `.pbix` file and open it in Power BI Desktop (free).

---

## Limitations

- Sector-level totals only: no school-level, regional or suburb detail, so pressure on individual schools can't be identified.
- School counts don't capture school size or capacity, so "students per school" is an indicator, not a capacity measure.
- Seven data points per sector are enough to show trends, not to forecast.

## Next steps

- Add school-level or regional data to identify specific growth corridors.
- Bring in population projections to forecast demand by stage.

---

**Author:** Renvil Furtado | Business Analyst, Perth WA
[LinkedIn](https://www.linkedin.com/in/renvilfurtado-6b419b238)
