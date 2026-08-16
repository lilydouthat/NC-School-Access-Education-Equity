# Methodology Notes

## Purpose

This project is designed as an exploratory statewide GIS view of where **economic disadvantage** and **geographic service-delivery pressure** overlap in North Carolina.

It intentionally avoids presenting a single black-box definition of “education equity.” Instead, it surfaces raw measures in every popup and lets the user switch between:

- school-age poverty rate,
- geographic access-pressure percentile,
- combined priority index.

## Formulas

### District poverty rate

For each unified school district:

`poverty_rate = children_5_17_in_poverty / relevant_children_5_17 * 100`

### County poverty rate

Use the SAIPE-published percentage of related children ages 5–17 in families in poverty.

### Access pressure

`access_pressure = land_area_sq_miles / (school_age_population / 1000)`

Higher values mean more land area per 1,000 school-age children.

### Percentile ranking

For both poverty and access pressure, areas are ranked against other North Carolina areas of the same geography type.

### Combined index

`priority_index = (poverty_percentile + access_percentile) / 2`

Equal weighting keeps the index easy to interpret and prevents unsupported claims that one dimension is more important than the other.

## Interpretation

A high combined score identifies a place that is relatively high in both economic need and geographic access pressure. It should be treated as a **screening / prioritization tool**, not a causal model or an official designation.

## Geography notes

Census TIGERweb's current unified school district layer is January 1, 2025 vintage, aligning with the school-district mapping vintage underlying the 2024 SAIPE school district estimates.

Some specialized districts can overlap other school systems. Users should interpret district polygons as Census statistical/administrative geography rather than as student-level attendance-zone boundaries.


## School-site access layer

The interactive map now loads the NCES EDGE **2024-25 Public School Locations - Current** feature layer and assigns public-school points to North Carolina counties and unified school-district polygons.

Two transparent site-access measures are calculated:

- **Area per school site:** district/county land area divided by the number of public-school locations.
- **School-age children per school site:** estimated 5-17 population divided by public-school locations.

The **School-Site Scarcity percentile** is the equal-weight average of the statewide percentile ranks of those two measures.

The updated combined priority index is the equal-weight average of:

1. school-age poverty percentile,
2. geographic access-pressure percentile,
3. school-site scarcity percentile.

This remains a screening tool. A school point does not imply that every student in the surrounding geography can attend that school.

## Transportation: what we can and cannot claim

NC DPI's Statistical Profile publishes a 2024-25 **Student Transportation on Public School Buses** table by LEA with buses, pupils transported, annual miles, total cost, cost per bus, cost per pupil, and cost per mile.

Those fields are useful for a future **transportation-system burden** layer. They should **not** be labeled "average child commute distance" or "average bus ride time": aggregate bus-system miles do not identify the distance or duration experienced by an individual student.

A defensible child-level distance proxy would require smaller-area student population geography or actual route/stop data, then a network-distance model to likely school destinations.

## Opportunity, staffing, and resources expansion

NC DPI's 2024-25 School Report Card research release confirms public reporting for:

- advanced course enrollment,
- class size,
- chronic absenteeism,
- educator qualifications,
- school improvement funding,
- use of funds,
- per-pupil expenditure,
- arts education.

These are the preferred sources for the next factor layers. Athletics/extracurricular participation is not fully captured in the School Report Card and should not be inferred from unrelated finance fields.
