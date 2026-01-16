# OnlyBadForecasts
## Introduction

I love time-series forecasting. To me it is the holy grail of machine learning, but I pretty much suck at it.

This is an attempt at a long term forecast of snowpack in Utah. Currently, the project is limited to forecasting [SWE (snow water equivalent)](https://en.wikipedia.org/wiki/Snow_science#Measurement) at Brighton. All of my raw data is sourced from the [USDA's Natural Resources Conservation Service](https://nwcc-apps.sc.egov.usda.gov/awdb/site-plots/POR/WTEQ/UT/Brighton.html).

## Methodology
My methodology is inspired by [this paper](https://proceedings.mlr.press/v48/gal16.pdf).

My first attempt broke historical data up into chunks of 60 day windows, 2 cylical features, and a target. Examples were fed into a simple MLP with a single dropout layer that was trained to predict the next day in the season. Feed forward prediction was used to create 300 futures paths. As per [Gal and Ghahramani](https://proceedings.mlr.press/v48/gal16.pdf), I kept dropout layers live to during inference. From these 300 trajectories I calculate a 10th and 90th percentile as well as a median: these figures essentially become my prediction. 

Looking at the charts, I am starting to worry about how similarly prediction curves seem to match with the shape of the historical median. Even without being fed it explicitly, I am worried that the model essentially learned the easiest way to minimize loss was to use the median, and that no matter when in the season or at what value of SWE the prediction starts, the model sort of "runs home to mama". With the storm around 2026/01/05, there is a very real possibility that true values will move above the historical median, and I am very interested to see if the model begins predicting down to the median even after this.

As my first alternative/sensitivity analysis, I created a similar workflow using LSTM layers (To reviewer #3: I am still avoiding auto-regressive options like ARIMA, SARIMA, or SARIMAX). Initial tests only used 20 predicted trajectories, as prediction is massively slower. On my machine, the MLP approach takes about 5 minutes to create all 300 paths, but the LSTM approach takes about 4.5+ hours to complete 300. Although, my first runs were limited to 20 paths, but I have since expanded this to 250. 

## Results

Below are visualizations for each round of prediction. Moving forward, my plan is to update predictions on a weekly cycle starting from 2026-01-04, but if major storms occur I may rerun predictions on an ad-hoc basis. I will save out past predictions and key metrics to gauge their relative accuracy over time.

***Current metrics***
#### Primary Chart
1. 2025-2026 observed SWE at Brighton (solid blue)
2. Median simulated SWE (dashed purple)
3. 10th to 90th percentiles for simulated trajectories (teal band)
4. 1991-2020 historical median (solid red)
5. The past 20 seasons of historical data (thin solid lines of various colors)

#### Secondary Chart
1. Current seasons observed data as a percent of the historical median (dotted blue)
2. Forecast median as a percent of the the historical median (dashed purple)

#### Tertiary Chart
1. Residuals (Forecast Median - Obsereved)

### Median Prediction, Prediction 10th-90th Percentiles, Historical Median ('91-'20), Past 20 Seasons, and Residuals

---

***MLP approach with a high learning rate (original)***

![2026 01 11 predictions](/assets/Brighton_Main_loop.gif "2026-01-11")

[Last Observed Date: 2026-01-11](https://onlybadforecasts.github.io/assets/html/20260112_Brighton_Main_20260111.html)

[Last Observed Date: 2026-01-04](https://onlybadforecasts.github.io/assets/html/20260112_Brighton_Main_20260104.html)

[Last Observed Date: 2025-12-22](https://onlybadforecasts.github.io/assets/html/20260112_Brighton_Main_20251222.html)

---

***MLP approach with a low learning rate*** 

![2025 12 22 predictions](/assets/Brighton_Main_lowLearnRate_(1e-4)_loop.gif "2025-12-22")

[Last Observed Date: 2026-01-11](https://onlybadforecasts.github.io/assets/html/20260115_Brighton_Main_lowLearnRate_(1e-4)_20260111.html)

[Last Observed Date: 2026-01-04](https://onlybadforecasts.github.io/assets/html/20260115_Brighton_Main_lowLearnRate_(1e-4)_20250104.html)

[Last Observed Date: 2025-12-22](https://onlybadforecasts.github.io/assets/html/20260115_Brighton_Main_lowLearnRate_(1e-4)_20251222.html)


---

***LSTM Test (250 predictions)***

![2025 12 22 predictions](/assets/20250105_Brighton_Alt_LSTM_20251222_IMG.png "2025-12-2 LSTM Predictions")

[Last Observed Date: 2025-12-22](https://onlybadforecasts.github.io/assets/html/20260106_Brighton_Alt_LSTM_250_20251222.html)

### Notes
- On 2026/01/04 I realized I had not properly limited my training data to past seasons. The MLP was being trained on windows for the 2025-2026 season. This has been corrected, but the estimates from the first prediction round were noticeably affected. The old predictions can still be found in the repo, but will not be displayed here.

