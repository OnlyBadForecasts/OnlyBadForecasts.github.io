# OnlyBadForecasts
## Introduction

I love time-series forecasting. To me it is the holy grail of machine learning.

My current after-hours foray into this topic is an attempt at a long term forecast of snowpack in Utah using unconventional, if naive, methodology. My target is SWE (snow water equivalent) curve for the entire remainder of the season.

I chose to go with SWE as the target for two main reasons. 1. Snow has varying densities and 10" of snow could contain differing amounts of water, and as such depth really isn't a great measure of precipitation as layers build up: think cascade concrete vs. blower pow. 2. SWE is the measure available from reputable sources.

On the point of sources, all of my raw data is being sourced from the USDA's Natural Resources Conservation Service. I am starting the project with a single site, Brighton, but as I build out the project and sink more hours into it I want to expand to other sites. 

[Brighton's data can be found here](https://nwcc-apps.sc.egov.usda.gov/awdb/site-plots/POR/WTEQ/UT/Brighton.html)

## Methodology
*Coming soon-ish...*

## Results

Below are links to interactive versions of the visualizations for each round of prediction. Moving forward from the new year (2026), my plan is to update predictions on a weekly cycle. I will save out past predictions and key metrics to gauge their relative accuracy over time. As my stash of visualizations and metrics grows this section may evolve. 

The charts that will make up the meat and potatoes of this section are titled using the last day of observed data e.g. a prediction run that starts with 2025-12-23 as the first predicted date will be titled "Last Observed Date: 2025-12-22".

Currently, the main chart has five main components.

1. 2025-2026 observed SWE at Brighton (solid blue)
2. Median simulated SWE (dashed purple)
3. 10th to 90th percentiles for simulated trajectories (teal band)
4. The past 20 seasons of historical data (thin solid lines of various colors)
5. A secondary chart that quantifies residuals

### Median Prediction, Prediction 10th-90th Percentiles, Past 20 Seasons, and Residuals

2. [Last observed date: 2025-12-31](https://onlybadforecasts.github.io/assets/html/20251231_Brighton_Main.html)

![2025 12 31 predictions](/assets/20251231_Brighton_Img.png "2025-12-31")

1. [Last observed date: 2025-12-22](https://onlybadforecasts.github.io/assets/html/20251222_Brighton_Main.html)

![2025 12 22 predictions](/assets/20251222_Brighton_Img.png "2025-12-22")


#### *Caveats*

I feel there are few extra points worth noting. 

I don't have the time or energy to make every title, annotation, or line weight fit perfectly on every device. If the chart feels a bit cluttered and you are on desktop, then I suggest try scaling your browser's zoom down a little bit. If you are on mobile, good luck. I will try to improve the functionality/ease of use on this platform, but I make no promises as I am more focused on improving predictions. Lastly, please don't flame me for not implementing every suggestion every voice on the internet suggests. I read suggestions, but I also have only so much time and energy, and more importantly I don't really care. 
