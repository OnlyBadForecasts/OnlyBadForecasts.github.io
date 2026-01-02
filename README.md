# Welcome to OnlyBadForecasts
## Introduction

I love time-series forecasting, to me it is the holy grail of machine learning.

My current after-hours foray into this topic is an attempt at a long term forecast of snowpack in Utah using unconventional forecasting methodology. My target is the measured using SWE (snow water equivalent) as my target and 

I have chosen to go with SWE as the target for two main reasons. 1. Snow has varying densities and 10" of snow could contain differing amounts of water, think cascade concrete vs. chunder vs. blower pow. 2. SWE is the measure available from reputable sources.

On the point of sources, all of my raw data is being sourced from the USDA's Natural Resources Conservation Service. I am starting the project with a single site, Brighton, but as I build out the project and sink more hours into it I want to expand to other sites. 

[Brighton's data can be found here](https://nwcc-apps.sc.egov.usda.gov/awdb/site-plots/POR/WTEQ/UT/Brighton.html)

## Methodology
*Coming soon...*

## Results

Below are links to interactive versions of the visualizations for each round of prediction. Moving forward from the new year, my plan is to update predictions every 7 days on Sunday evenings, but I will save out past predictions and key metrics to gauge their accuracy over time. As my stash of visualizations and metrics grows this section may evolve. 

The charts that will make up the meat and potatoes of this section are titled here using the last day of observed data e.g. a prediction that starts on 2025-12-23 will be titled "Last Observed Date: 2025-12-22".

These charts have five main components. 

1. 2025-2026 observed SWE at Brighton (solid blue)
2. Median simulated SWE (dashed purple)
3. 10th to 90th percentiles for simulated trajectories (teal band)
4. The past 20 seasons of historical data (thin solid lines of various colors)
5. A secondary chart that quantifies residuals

*just a test* [Last observed date: 2025-12-22](https://onlybadforecasts.github.io/brighton_snowpack_interactive)
