# OnlyBadForecasts
## Introduction

I love time-series forecasting. To me, it is the holy grail of machine learning, but I pretty much suck at it.

This is an attempt at a long term forecast of snowpack in Utah. The project began with fore4cast for a single site, is limited to forecasting [SWE (snow water equivalent)](https://en.wikipedia.org/wiki/Snow_science#Measurement) at Brighton. All of my raw data is sourced from the [USDA's Natural Resources Conservation Service](https://nwcc-apps.sc.egov.usda.gov/awdb/site-plots/POR/WTEQ/UT/Brighton.html).
Below are visualizations for each model. Starting from 2026/01/04 the main models will be updated weekly as best as possible.

***Current metrics***
#### Primary Chart
1. 2025-2026 observed SWE at Brighton (solid blue)
2. Median simulated SWE (dashed purple)
3. 10th to 90th percentiles for simulated trajectories (teal band)
4. 1991-2020 historical median (solid red)
5. The past 20 seasons of historical data (thin solid lines of various colors)

#### Secondary Chart
1. Current season observed data as a percent of the historical median (dotted blue)
2. Forecast median as a percent of the historical median (dashed purple)

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

