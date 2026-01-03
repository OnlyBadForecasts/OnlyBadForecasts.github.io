# OnlyBadForecasts
## Introduction

I love time-series forecasting. To me it is the holy grail of machine learning. But, I pretty much suck at it.

This is an attempt at a long term forecast of snowpack in Utah. Currently, the project is limited to forecasting [SWE (snow water equivalent)](https://en.wikipedia.org/wiki/Snow_science#Measurement) at Brighton. All of my raw data is sourced from the [USDA's Natural Resources Conservation Service](https://nwcc-apps.sc.egov.usda.gov/awdb/site-plots/POR/WTEQ/UT/Brighton.html).

## Methodology
*Coming soon-ish...*

## Results

Below are visualizations for each round of prediction. Moving forward, my plan is to update predictions on a weekly cycle. I will save out past predictions and key metrics to gauge their relative accuracy over time.

Current
1. 2025-2026 observed SWE at Brighton (solid blue)
2. Median simulated SWE (dashed purple)
3. 10th to 90th percentiles for simulated trajectories (teal band)
4. The past 20 seasons of historical data (thin solid lines of various colors)
5. A secondary chart that quantifies residuals

### Median Prediction, Prediction 10th-90th Percentiles, Past 20 Seasons, and Residuals

---

***Prediction 2:*** [Last Observed Date: 2025-12-31](https://onlybadforecasts.github.io/assets/html/20251231_Brighton_Main.html)

![2025 12 31 predictions](/assets/20251231_Brighton_Img.png "2025-12-31")

I downloaded this data on the first of year, but I cut off the data used in inference at Dec. 31st. That way I would have at least a single day for evaluation. Adding these nine days into the first inference window had a more dramatic effect than I expected. Most resorts in the Front received new snow (woo!). I am excited to see how this changes predictions and affects the accuracy of both runs further out in the season.  

---

***Prediction 1:*** [Last Observed Date: 2025-12-22](https://onlybadforecasts.github.io/assets/html/20251222_Brighton_Main.html)

![2025 12 22 predictions](/assets/20251222_Brighton_Img.png "2025-12-22")

