# North Carolina School Access & Education Equity

An interactive GIS project exploring how geography, economic conditions, and the physical distribution of public schools shape educational access across North Carolina.

Education access is more than whether a school exists within a district. Where a family lives can affect how far students must travel, how many schools serve an area, the resources available to those schools, and the educational opportunities students can access.

This project uses publicly available education, demographic, and geographic data to examine those differences across North Carolina counties and school districts.

## Project Goal

The goal of this project is to explore a simple question:

> **How does where a student lives in North Carolina affect their access to educational resources and opportunities?**

Rather than treating education equity as a single measure, the project separates it into several dimensions that can be explored individually.

### Economic Need

Measures the economic conditions surrounding school-age children.

Current indicators include:

* School-age poverty rate
* Number of children ages 5 to 17 living in poverty
* School-age population

### Physical and Geographic Access

Examines how geography may affect the difficulty of delivering and accessing public education.

Current indicators include:

* District and county land area
* Public school locations
* School-age population density
* Land area per public school
* School-age children per public school
* Geographic access pressure
* School-site scarcity

A geographically large, sparsely populated district may face very different transportation and service-delivery challenges than a compact urban district, even when the two districts have similar enrollment or poverty rates.

### Staffing Access

Planned indicators include:

* Class size
* Student-to-teacher ratios
* Educator qualifications
* Counselor and support-staff availability where data are available
* Teacher vacancy or turnover measures where available

### Resource Access

Planned indicators include:

* Per-pupil expenditures
* State, local, and federal funding
* School-improvement funding
* Transportation expenditures
* Other available measures of district resource capacity

### Educational Opportunity

Planned indicators include:

* Arts education
* Advanced coursework
* AP, IB, or other college-level opportunities
* Career and Technical Education
* Extracurricular and athletic opportunities where reliable statewide data are available
* Chronic absenteeism as an additional indicator of students' ability to consistently access school

## Interactive Map

The interactive map allows users to switch between North Carolina school districts and counties and explore multiple measures of educational access and equity.

Current map layers include:

* School-Age Poverty Rate
* Geographic Access Pressure
* School-Site Scarcity
* Combined Access and Equity Priority Index
* Public School Locations

Clicking a district or county displays the underlying values used in the analysis.

This is intentional. The project prioritizes transparent measures over a black-box equity score.

## Combined Access and Equity Priority Index

The project includes an exploratory 0 to 100 priority index designed to identify areas where multiple access challenges overlap.

The current index incorporates three dimensions:

1. Economic need
2. Geographic access pressure
3. School-site scarcity

Each measure is converted to a statewide percentile rank within its geography type.

The current index is:

**Priority Index = (Poverty Percentile + Geographic Access Percentile + School-Site Scarcity Percentile) / 3**

Higher scores indicate areas experiencing greater relative access and equity pressure within North Carolina.

The index is an exploratory analytical tool and is not an official North Carolina or federal education-equity designation.

## School-Site Scarcity

Simply counting schools can be misleading.

Ten schools serving a small urban district represent a very different level of physical access than ten schools distributed across hundreds of square miles.

To capture this difference, the project considers:

**Land Area per School**

and

**School-Age Children per School**

These measures are ranked statewide and combined into a School-Site Scarcity measure.

Higher values identify areas where relatively few public school sites must serve either a large geographic area, a large school-age population, or both.

## Student Transportation and Travel

Student transportation is an important part of educational access, particularly in rural areas.

North Carolina DPI publishes district-level information including:

* Students transported
* Number of school buses
* Annual bus miles
* Transportation expenditures
* Cost per transported pupil
* Cost per mile

However, these aggregate statistics do not tell us the average distance or travel time experienced by an individual student.

For example, dividing total annual bus miles by the number of students transported would not produce a valid estimate of the average student's commute.

For that reason, this project does not label aggregate transportation mileage as "average student travel distance."

A future version could estimate student travel burden using school locations, smaller-area population geography, road networks, and potentially transportation route data.

## Data Sources

### U.S. Census Bureau: SAIPE

**Small Area Income and Poverty Estimates, 2024**

Used for:

* School-age poverty estimates
* Population of children ages 5 to 17
* County and school-district economic indicators

### U.S. Census Bureau: TIGERweb

Used for:

* North Carolina county boundaries
* Unified school district boundaries
* Geographic land-area calculations

### NCES EDGE

**2024-25 Public School Locations**

Used for:

* Public school point locations
* School counts
* Spatial assignment of schools to districts and counties
* School-site accessibility measures

### North Carolina Department of Public Instruction

NC DPI datasets provide or are planned to provide measures related to:

* Per-pupil expenditure
* Student transportation
* Class size
* Educator qualifications
* Chronic absenteeism
* Advanced coursework
* Arts education
* School-improvement funding
* Educational resources

### OpenStreetMap

Used as the interactive map basemap.

## Methodology

Detailed definitions, formulas, assumptions, and limitations are available in:

**`METHODOLOGY.md`**

A source inventory is available in:

**`DATA_SOURCES.md`**

## Limitations

Education equity is multidimensional and cannot be completely represented by a single map or index.

Several important limitations should be considered:

* Poverty estimates contain statistical uncertainty.
* Geographic proximity does not necessarily represent actual school assignment.
* School locations do not measure school capacity or program availability.
* Large geographic districts do not automatically mean every student experiences a long commute.
* Aggregate school-bus mileage cannot be interpreted as individual student travel distance.
* County and school-district boundaries represent different administrative and geographic systems.
* Athletics and extracurricular opportunities require additional reliable statewide data.
* Funding differences do not automatically indicate differences in educational quality.

The project should therefore be interpreted as an exploratory geographic analysis and prioritization tool, not a causal model or ranking of school quality.

## Future Development

The long-term goal is to develop a broader **North Carolina Geography of Educational Opportunity** framework.

Potential future layers include:

* Transportation burden
* Estimated school travel time
* Teacher and support-staff availability
* Per-pupil spending
* Arts education access
* Athletic and extracurricular opportunity
* AP, IB, honors, and advanced-course access
* Career and Technical Education access
* Broadband availability
* Chronic absenteeism
* College-readiness indicators
* School capacity and student-to-school ratios
* Counselor, nurse, psychologist, and social-worker availability

Ultimately, the project aims to examine where economic disadvantage, physical distance, resource limitations, and differences in educational opportunity overlap geographically.

## Running the Project Locally

Clone the repository:

```bash
git clone https://github.com/lilydouthat/NC-School-Access-Education-Equity.git
```

Move into the project directory:

```bash
cd NC-School-Access-Education-Equity
```

Start a local server:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`.

A local server is recommended because the interactive map requests geographic data from Census TIGERweb and other public services.

## Why This Project?

Educational access is inherently spatial.

Two students can live in the same state, and even experience similar economic circumstances, while having dramatically different access to schools, transportation, teachers, programs, and extracurricular opportunities.

North Carolina is particularly interesting because the state contains dense urban school systems, rapidly growing suburban communities, large rural districts, mountain communities, coastal communities, and areas of persistent economic disadvantage.

Mapping these differences provides another way to understand education equity:

> **Not simply "How good is this school?" but "What educational opportunities are realistically accessible to a child living here?"**

## Author

**Lily Douthat**

Data science, information systems, GIS, and education data.

This project is an independent exploratory analysis using publicly available data and is not affiliated with or endorsed by the North Carolina Department of Public Instruction, the U.S. Census Bureau, or the National Center for Education Statistics.
