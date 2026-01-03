# OnlyBadForecasts
## Introduction

I love time-series forecasting. To me it is the holy grail of machine learning. But, I pretty much suck at it.

My current after-hours foray into this topic is an attempt at a long term forecast of snowpack in Utah. Currently, the project is limited to forecasting measurements of [SWE (snow water equivalent)](https://en.wikipedia.org/?title=Snow_water_equivalent&redirect=no) for Brighton, but I do want to eventually expand the scope. All of my raw data is being sourced from the [USDA's Natural Resources Conservation Service](https://nwcc-apps.sc.egov.usda.gov/awdb/site-plots/POR/WTEQ/UT/Brighton.html).



## Methodology
*Coming soon-ish...*

## Results

Below are links to interactive versions of the visualizations for each round of prediction. Moving forward from the new year (2026), my plan is to update predictions on a weekly cycle. I will save out past predictions and key metrics to gauge their relative accuracy over time. As my stash of visualizations and metrics grows this section may evolve. 

The charts that will make up the meat and potatoes of this section are organized using the last day of observed data e.g. a prediction run that starts with 2025-12-23 as the first predicted date will be listed as "Last Observed Date: 2025-12-22".

Currently, the main chart has five main components.

1. 2025-2026 observed SWE at Brighton (solid blue)
2. Median simulated SWE (dashed purple)
3. 10th to 90th percentiles for simulated trajectories (teal band)
4. The past 20 seasons of historical data (thin solid lines of various colors)
5. A secondary chart that quantifies residuals

### Median Prediction, Prediction 10th-90th Percentiles, Past 20 Seasons, and Residuals

---

***Prediction 2:*** [Last Observed Date: 2025-12-31](https://onlybadforecasts.github.io/assets/html/20251231_Brighton_Main.html)

![2025 12 31 predictions](/assets/20251231_Brighton_Img.png "2025-12-31")

I downloaded this data on the first of year, but I cut off the data used in inference at the 31st. That way I would have at least a single day for evaluation. Adding these nine days into the inference window seems to have dramatically shrank the distance between the 10th and 90th percentiles of my predictions: especially at dates farther into the future. Also, the median prediction appears to have been pulled down, and at points the median prediction now falls below historic levels. As of the time of writing (2026-01-02), most resorts in the Wasatch Front had received new snow (woo!). I am excited to see how this new snow changes predictions, but importantly affects the accuracy of this and the first run.  

---

***Prediction 1:*** [Last Observed Date: 2025-12-22](https://onlybadforecasts.github.io/assets/html/20251222_Brighton_Main.html)

![2025 12 22 predictions](/assets/20251222_Brighton_Img.png "2025-12-22")


#### *Caveats*

I feel there are few extra points worth noting. 

I don't have the time or energy to make every title, annotation, or line weight fit perfectly on every device. If the chart feels a bit cluttered and you are on desktop, then I suggest try scaling your browser's zoom down a little bit. If you are on mobile, good luck. I will try to improve the functionality/ease of use on this platform, but I make no promises as I am more focused on improving predictions. Lastly, please don't flame me for not implementing every suggestion every voice on the internet throws out. I read suggestions, but I also have only so much time and energy, and more importantly: I don't really care. 
