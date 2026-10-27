# Malaria Incidence by Region — Kenya Poisson Regression Analysis

An epidemiology project modelling malaria incidence across all 47 Kenyan counties
using ecological surveillance data, Poisson regression, and incidence rate ratios.

## Study Design

| Feature | Description |
|---|---|
| Design | Ecological panel study |
| Unit of analysis | County-year observation |
| Geography | All 47 Kenyan counties |
| Period | 2017 to 2022 (6 years) |
| Observations | 282 county-year records |
| Outcome | Annual malaria case counts (offset: log population) |
| Data sources | DHIS2/KHIS, KEMRI MIS 2020, KNBS 2019 Census |

## Research Questions

1. Which ecological zones carry the highest malaria incidence in Kenya?
2. What is the incidence rate ratio for each zone relative to the low-transmission Highlands baseline?
3. Is there a secular declining trend in malaria incidence over 2017 to 2022?
4. Does overdispersion of case counts warrant a Negative Binomial model over Poisson?

## Key Findings

| Analysis | Finding |
|---|---|
| Highest burden zone | Lake Victoria basin (Homa Bay, Kisumu, Siaya) |
| IRR Lake Victoria vs Highlands | 80 to 120 times higher (p < 0.001) |
| Coastal IRR | 50 to 80 times higher than Highlands |
| Annual trend | Approximately 2.5% decline per year |
| Spike years | 2018 and 2020 (high-rainfall El Niño years, 10 to 30% above trend) |
| Model fit | Overdispersion checked; Negative Binomial compared |

## Analytical Pipeline

1. Synthetic panel data generation calibrated to DHIS2/KEMRI surveillance estimates
2. Descriptive statistics: incidence by ecological zone and year
3. Top 10 counties ranked by crude incidence rate
4. Incidence bar chart by zone
5. All-county ranked choropleth (lollipop approximation, no shapefile required)
6. Annual trend lines by ecological zone with rainfall spike annotation
7. Poisson GLM with log(population) offset
8. Incidence rate ratio table with 95% CI and significance
9. IRR forest plot
10. Overdispersion test (Pearson chi-squared / df)
11. Negative Binomial GLM for comparison
12. Poisson vs Negative Binomial IRR comparison chart
13. National malaria burden by zone
14. Epidemiological interpretation with Kenya NMCP policy context

## Quick Start (Google Colab)

Open `Malaria_Incidence_Kenya.ipynb` in Google Colab. All required libraries
are pre-installed in Colab (numpy, pandas, scipy, statsmodels, matplotlib).

## Tech Stack

`Python 3.10+` · `numpy` · `pandas` · `scipy` · `statsmodels` · `matplotlib`

## Epidemiological Background

Malaria remains one of Kenya's leading causes of morbidity and mortality,
with an estimated 3.5 million clinical cases annually. Transmission is highly
heterogeneous: the Lake Victoria basin is holoendemic with year-round intense
transmission, while the arid north and central highlands have low or epidemic-prone
transmission patterns.

The Kenya National Malaria Control Programme (NMCP) has achieved substantial
reductions in malaria burden through scale-up of LLINs, IRS, and ACT since
2000. Ecological surveillance analysis using DHIS2 routine health information
data is a core tool for programme monitoring and resource allocation under the
Kenya Malaria Strategy 2019 to 2023.

## Data Sources

Synthetic data calibrated to:
- Kenya Health Information System (DHIS2/KHIS): routine malaria case reporting
- KEMRI Malaria Indicator Survey (MIS) 2020: parasite prevalence by county
- KNBS 2019 Kenya Population and Housing Census: county population denominators
- WHO AFRO malaria seasonal transmission calendars for East Africa

---

*ZENIK.AI · github.com/Mwauramos*
