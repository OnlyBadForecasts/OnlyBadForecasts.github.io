# OnlyBadForecasts
## Introduction

I love time-series forecasting. To me it is the holy grail of machine learning, but I pretty much suck at it.

This is an attempt at a long term forecast of snowpack in Utah. Currently, the project is limited to forecasting [SWE (snow water equivalent)](https://en.wikipedia.org/wiki/Snow_science#Measurement) at Brighton. All of my raw data is sourced from the [USDA's Natural Resources Conservation Service](https://nwcc-apps.sc.egov.usda.gov/awdb/site-plots/POR/WTEQ/UT/Brighton.html).

## Methodology
*In depth write-up coming soon-ish...*

In the meantime, my methodology is inspired by [this paper](https://proceedings.mlr.press/v48/gal16.pdf). My first attempt broke historical data up into chunks built around 60 day windows and 2 cyclical features built using cos and sin to help the model understand that 10-01 and 09-30 are actually very close (even though their day_of_season values are 0 and 365 respectively). These examples were fed into a simple MLP with a single dropout layer. I then used feed forward prediction to create 300 possible futures while keeping dropout live to introduce uncertainty. From these 300 trajectories I calculate the 10th and 90th percentiles as well as the median: these figures essentially become my prediction.


One thing that is starting to worry me is how similarly my prediction curves seem to match with the shape of the historical median. Even without being fed it explicitly, I am worried that the model essentially learned the easiest way to minimize loss was to just use the median, and no matter when and at what value of SWE the prediction starts the model sort of "runs home to mama". With the recent dumping on 2026/01/05, there is a very real possibility that true values for this season will move above the historical median, and I am very interested to see if the model begins predicting down to the median even after this. I also think maybe the model will just predict the median +/- the last observed value: I will have to build out a way to monitor this. Some of this scree may fit better in the results/conclusions section, but for the moment it stays here.

As my first alternative/sensitivity analysis, I created a similar workflow using LSTM layers (To reviewer #3: I am still avoiding auto-regressive options like ARIMA, SARIMA, or SARIMAX). Initial results only use 20 predicted trajectories, as prediction is massively slower. On my machine, the MLP approach takes about 5 minutes to create all 300 paths, but the LSTM approach will likely take 4+ hours to complete 300. Regardless, attached below the ***notes*** section is a chart that shows the results when using just 20 predicted paths. To my eye, the most striking differences are related to how much tighter the bastardized confidence interval appears, how little the 10th and 90th percentiles seem to vary in their distance from the median prediction regardless of how far in the future predictions are, and the jagged more inconsistent shape of the entire path. We will see what happens when I let the code build all 300 paths and data accumulates.

For both approaches, I want to add in a new feature: day distance (positive or negative) from the expected peak day. The raw data contains a marker showing that the median peak day across years is YYYY-04-10. I think the model would benefit from this as it would add in signal about where in the accumulation/peak/melt phase each observation is, and this might work in concert with the cyclical features to improve performance. I will work on this later, but it should be an easy add.

## Results

Below are visualizations for each round of prediction. Moving forward, my plan is to update predictions on a weekly cycle starting from 2026-01-04, but if major storms occur I may rerun predictions on an ad-hoc basis. I will save out past predictions and key metrics to gauge their relative accuracy over time.

***Current metrics***
1. 2025-2026 observed SWE at Brighton (solid blue)
2. Median simulated SWE (dashed purple)
3. 10th to 90th percentiles for simulated trajectories (teal band)
4. 1991-2020 historical median (solid red)
5. The past 20 seasons of historical data (thin solid lines of various colors)
6. A secondary chart that quantifies residuals

### Median Prediction, Prediction 10th-90th Percentiles, Historical Median ('91-'20), Past 20 Seasons, and Residuals

---

***Prediction 4:*** [Last Observed Date: 2026-01-05](https://onlybadforecasts.github.io/assets/html/20260105_Brighton_Main_20260105.html)

![2026 01 05 predictions](/assets/20260105_Brighton_Main_20260105_IMG.png "2026-01-05")

---

***Prediction 3:*** [Last Observed Date: 2026-01-04](https://onlybadforecasts.github.io/assets/html/20260105_Brighton_Main_20260104.html)

![2026 01 04 predictions](/assets/20260105_Brighton_Main_20260104_IMG.png "2026-01-04")

---

***Prediction 2:*** [Last Observed Date: 2025-12-31](https://onlybadforecasts.github.io/assets/html/20260105_Brighton_Main_20251231.html)

![2025 12 31 predictions](/assets/20260105_Brighton_Main_20251231_IMG.png "2025-12-31")


---

***Prediction 1:*** [Last Observed Date: 2025-12-22](https://onlybadforecasts.github.io/assets/html/20260105_Brighton_Main_20251222.html)

![2025 12 22 predictions](/assets/20260105_Brighton_Main_20251222_IMG.png "2025-12-22")

### Notes
- On 2026/01/04 I realized I had not properly limited my training data to past seasons. The MLP was being trained on windows for the 2025-2026 season. This has been corrected, but the estimates from the first prediction round were noticeably affected. The old predictions can still be found in the repo, but will not be displayed here.

---

***LSTM Test (20 predictions)***

![2025 01 05 predictions](/assets/20260105_Brighton_Alt_LSTM_20260105_IMG.png "2025-01-05 LSTM Predictions")
