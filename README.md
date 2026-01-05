# OnlyBadForecasts
## Introduction

I love time-series forecasting. To me it is the holy grail of machine learning. But, I pretty much suck at it.

This is an attempt at a long term forecast of snowpack in Utah. Currently, the project is limited to forecasting [SWE (snow water equivalent)](https://en.wikipedia.org/wiki/Snow_science#Measurement) at Brighton. All of my raw data is sourced from the [USDA's Natural Resources Conservation Service](https://nwcc-apps.sc.egov.usda.gov/awdb/site-plots/POR/WTEQ/UT/Brighton.html).

## Methodology
*Coming soon-ish...*

## Results

Below are visualizations for each round of prediction. Moving forward, my plan is to update predictions on a weekly cycle, but, if major storms occur, I may rerun predictions on an ad-hoc basis. I will save out past predictions and key metrics to gauge their relative accuracy over time.

***Current metrics***
1. 2025-2026 observed SWE at Brighton (solid blue)
2. Median simulated SWE (dashed purple)
3. 10th to 90th percentiles for simulated trajectories (teal band)
4. 1991-2020 Historical Median (solid red)
5. The past 20 seasons of historical data (thin solid lines of various colors)
6. A secondary chart that quantifies residuals

### Median Prediction, Prediction 10th-90th Percentiles, Historical Median ('91-'20), Past 20 Seasons, and Residuals

---

***Prediction 4:*** [Last Observed Date: 2026-01-05](https://onlybadforecasts.github.io/assets/html/20260105_Brighton_Main_20260105.html)

![2025 12 31 predictions](/assets/20260105_Brighton_Main_20260105_IMG.png "2026-01-05")

---

***Prediction 3:*** [Last Observed Date: 2026-01-04](https://onlybadforecasts.github.io/assets/html/20260105_Brighton_Main_20260104.html)

![2025 12 31 predictions](/assets/20260105_Brighton_Main_20260104_IMG.png "2026-01-04")

---

***Prediction 2:*** [Last Observed Date: 2025-12-31](https://onlybadforecasts.github.io/assets/html/20260105_Brighton_Main_20251231.html)

![2025 12 31 predictions](/assets/20260105_Brighton_Main_20251231_IMG.png "2025-12-31")


---

***Prediction 1:*** [Last Observed Date: 2025-12-22](https://onlybadforecasts.github.io/assets/html/20260105_Brighton_Main_20251222.html)

![2025 12 22 predictions](/assets/20260105_Brighton_Main_20251222_IMG.png "2025-12-22")

### Notes
- On 2026/01/04 I realized I had not properly limited my training data to past seasons. The MLP was being trained on windows for the 2025-2026 season. This has been corrected, but the estimates from the first prediction round were noticeably affected. The old predictions can still be found in the repo, but will not be displayed here.

