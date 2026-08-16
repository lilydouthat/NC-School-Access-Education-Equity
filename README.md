# North Carolina School Access & Education Equity

An interactive GIS project comparing **North Carolina school districts and counties** on two related dimensions:

1. **Economic equity need** — the estimated share of related children ages 5–17 living in poverty.
2. **Geographic access pressure** — land area per 1,000 school-age children.
3. **School-site scarcity** — a GIS measure combining land area per public-school site and school-age children per school site.

The map also provides a **Combined Access & Equity Priority Index (0–100)** that equally weights the statewide percentile ranks of those three dimensions. Higher values indicate greater relative need.

## Live map

Open `index.html` locally or publish the repository with GitHub Pages.

## Data sources

- **U.S. Census Bureau, Small Area Income and Poverty Estimates (SAIPE), 2024**
  - 2024 School District Estimates, released February 2026.
  - 2024 State and County Estimates, released January 2026.
- **U.S. Census Bureau TIGERweb**
  - Unified School Districts, January 1, 2025 vintage.
  - Counties, January 1, 2025 vintage.
- **NCES EDGE / ArcGIS**
  - 2024-25 Public School Locations - Current; point layer updated in 2026.
- **NC Department of Public Instruction**
  - School Report Cards 2024-25 research release (source framework for staffing, opportunity, absenteeism, arts, and expenditure expansion).
  - Statistical Profile 2024-25 transportation and per-pupil expenditure tables.
- **OpenStreetMap** tiles for the basemap.

## Methodology

### Economic equity need
For districts, the poverty rate is calculated from SAIPE's published population of relevant children ages 5–17 and the estimated number of those children in poverty.

For counties, SAIPE publishes the estimated percentage of related children ages 5–17 in families in poverty directly.

### Geographic access pressure
`land area (square miles) / (school-age population / 1,000)`

This is intended as a **geographic access proxy**, not a direct travel-time measure. A district or county with a large land area and relatively few school-age children may face greater transportation, service-delivery, and physical-access challenges.

For counties, the 5–17 population denominator is approximated from SAIPE's published poverty count divided by the published rounded poverty percentage because the county file does not directly provide the 5–17 denominator.

### School-site scarcity
The map loads actual public-school point locations, assigns them to each geography, and calculates:

- land area per public-school site,
- school-age children per public-school site,
- an equal-weight percentile score from those two measures.

### Combined Priority Index
Within each geography type (districts and counties separately):

- Poverty rate → statewide percentile rank
- Geographic access pressure → statewide percentile rank
- School-site scarcity → statewide percentile rank
- Combined Priority Index = equal-weight average of the three percentile scores

The score is **relative within North Carolina**. It is not an official state or federal equity designation.

## Why two geographies?

School district boundaries reflect the administrative systems that deliver public education, while counties are useful for broader regional planning, public services, infrastructure, and community context. The map intentionally lets users compare both rather than assuming they are interchangeable.

## Run locally

Because the map requests boundary geometry from Census TIGERweb, use a small local web server rather than opening the file directly:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`.

## Publish with GitHub Pages

1. Push the repository to GitHub.
2. Open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select `main` and `/ (root)`.
5. Save.

## Limitations

- Poverty is one important dimension of education equity, not the whole concept.
- The access-pressure metric does not measure actual bus routes, travel time, broadband quality, school capacity, staffing, course availability, disability access, or school choice.
- SAIPE estimates contain uncertainty.
- County school-age population is an approximation derived from a rounded published percentage.
- District and county scores are ranked separately and should not be interpreted as directly interchangeable.

## Suggested next phase

A stronger v2 could incorporate:
- chronic absenteeism,
- school performance / growth,
- per-pupil expenditure,
- broadband access,
- student-to-school ratios,
- drive-time access to public schools,
- advanced-course availability,
- subgroup achievement gaps.

Those additions would turn the current transparent two-factor index into a more comprehensive education-equity dashboard.


## Expansion framework: geography of educational opportunity

The intended next version separates the project into five interpretable dimensions rather than forcing every variable into one opaque score:

| Dimension | Candidate measures | Source |
|---|---|---|
| Economic need | 5-17 poverty rate | Census SAIPE |
| Physical access | school-site scarcity, geographic dispersion, transportation-system burden | NCES EDGE, Census TIGER, NC DPI Statistical Profile |
| Staffing access | class size, educator qualifications, counselor/support staffing where available | NC DPI School Report Cards / Statistical Profile |
| Resource access | total/state/federal/local per-pupil expenditure, school-improvement funding | NC DPI |
| Opportunity access | arts indicator, advanced coursework, CTE/AP/IB where available | NC DPI School Report Cards |

### Important travel-distance distinction

NC DPI publishes aggregate school-bus miles and transported pupil counts, but those values **cannot be interpreted as the average number of miles an individual child travels**. The project will label them as transportation-system intensity/burden unless route-level or defensible network-distance data are obtained.
