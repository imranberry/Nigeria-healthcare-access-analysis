# Nigeria National Healthcare Facility Access Analysis

A national-scale geospatial portfolio project analyzing healthcare infrastructure density and functionality across all 36 Nigerian states + FCT, built on real government survey data.

## Scale

- **34,139 geocoded health facilities**
- **772 of Nigeria's 774 Local Government Areas** represented
- **37 states (36 + FCT)** compared by facility density and service quality

## What this project demonstrates

- **Large real-world dataset handling** — cleaning, validating, and spatially joining 34k+ records
- **Geospatial analysis** — CRS-correct area calculations, spatial joins, density metrics
- **Data storytelling** — raw count vs. true density as a deliberate "don't be misled by the obvious chart" narrative
- **Policy-relevant insight** — facility density AND functionality (electricity, water, skilled staffing) combined into a coherent regional story

## Data source

[NMIS Health Facility Database (2014)](https://energydata.info/dataset/nigeria-nmis-health-facility-data-2014) — collected by Nigeria's Office of the Senior Special Assistant to the President on the MDGs (OSSAP-MDGs), in partnership with Columbia University's Sustainable Engineering Lab. Published under **CC-BY 4.0** via energydata.info (World Bank ESMAP).

## Key findings

1. **Facility density varies 50x across states** — from 6.6 facilities per 1,000 km² in Borno to 345.8 in Lagos.
2. **The northeast (Borno, Yobe) is the most underserved region** by both density and functionality — likely compounded by the regional insurgency's impact on infrastructure over the past decade.
3. **Raw facility counts mislead.** States like Katsina and Niger look infrastructure-rich on a simple count map, but their actual density (accounting for land area) tells the opposite story.
4. **Facility presence ≠ facility function.** On Average only 40.2% of facilities nationally have grid electricity, and 40.5% have a skilled birth attendant on staff. The lowest-density states often double as the lowest-functionality states.

## Files in this project

| File | Description |
|---|---|
| `Nigeria_National_Healthcare_Access_Analysis.ipynb` | Full analysis notebook — load, clean, spatial join, density calc, functionality metrics, static + interactive maps |
| `healthmopupandbaselinenmisfacility.csv` | Source data: all 34,139 facilities nationally (raw NMIS export) |
| `nigeria_states_enriched.geojson` | Nigeria state boundaries used for spatial joins and choropleths |
| `state_facility_density.csv` | Computed per-state stats: area, facility count, density |
| `national_choropleth_comparison.png` | Static side-by-side: raw count vs. density |
| `national_density_map.html` | **Open this directly** — interactive national choropleth, hover any state for stats |

## Future Recommendation

1. Layer in **WorldPop** gridded population data to convert density into population-adjusted access (a far more decision-relevant metric than land-area density alone)
2. Wrap this in the **Streamlit dashboard pattern** so a planner can filter by state, facility type, or ownership and see updated stats live
3. Cross-reference against more recent facility registries (this data is from 2014) to update the baseline
4. Build a composite "facility quality index" combining electricity, water, sanitation, and staffing into a single comparable score per state or LGA

## Limitations

- Data is from **2014** — over a decade old. Facility counts have likely grown substantially since, especially private/urban facilities in cities like Lagos.
- Density (facilities per land area) is a *proxy* for access, not population-adjusted access. Nigeria's last full census was in 2006, so any "facilities per capita" claim should be treated cautiously without a verified current population source.
- All facility types are weighted equally in the density calculation — a Health Post and a Teaching Hospital count the same, though their capacity differs enormously.
