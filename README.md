# Austin Housing Analysis: Time Series Forecasting

**Authors**: 

- [Emine Kesici](https://github.com/emykes)
- [Scott Schumann](https://github.com/Shoemaker703)

## Overview

The year is 2018. A real estate investment firm in Austin, TX (ATX) is interested in making some investments for the upcoming year. They have hired us at Basilisk Analytics to determine which zip codes in the area represent good potential investment opportunities. In order to accomplish this, we will use time series forecasting to find the top 5 zip codes in the ATX region based on net profit & return on investment (ROI).


## Business Understanding

Our stakeholder is a real estate investment firm in ATX, and they have hired us at Basilisk Analytics to determine which zip codes in the area represent good potential investment opportunities. We will use time series forecasting to analyze median sale price for 73 zip codes in the ATX area to determine the 5 zip codes with the highest predicted net profit & ROI.


## Data Understanding

Our data comes from Zillow's database of median real estate prices organized by zip code (https://www.zillow.com/research/data/). This is a good dataset for our project because it includes all zip codes in the ATX region along with monthly median sale prices, which provides us with a lot of data points for time series modeling.

The original dataset included 14723 zip codes with 265 monthly median sale prices for each zip code. When we filtered our dataset to only include zip codes in Texas, there were 989 zip codes. Finally, after filtering for zip codes in the Austin area, we ended up with 73 zip codes.

The original dataset included dates as far back as April 1996, but we decided to filter out everything before January 2009. We made this choice to take the subprime mortgage housing crisis into account (essentially beginning our analysis right after the crash took place) because we figured that this event was an anomaly that could affect our model’s accuracy. After filtering out these dates, we had 112 monthly data points remaining in our set (January, 2009 through April, 2018).

Our final dataset thus has 73 zip codes and 112 months worth of median sale prices. All features in the dataset we used are median sale prices for real estate in each zip code by month, which is relevant because we are doing a time series analysis forecasting sale prices.


## Modeling

For the baseline model, we calculated the average yearly return on investment for each ATX zip code over the 9 year period covered in our data. This list of zip codes is potentially useful for our stakeholders given that these zip codes have had high average returns over a 9 year period.

We used grid search ARIMA to analyze all 73 zip codes to find the best parameters for each time series model. We evaluated each based on explained variance, and found that our model was able to capture 99% explained variance for 13 of the 73 zip codes. 


## Evaluation

Our final step was to calculate the predicted ROI for each of these 13 zip codes. We took the top 5 zip codes from this list based on their predicted ROI and used these as our recommendations for our stakeholders. The final step was to calculate the net profit for these five zip codes. Here are the results of our final model:

- 78748: $35,181 (12% ROI)
- 78620: $54,155 (12% ROI)
- 78634: $21,542 (9.6% ROI)
- 78626: $16,826 (7.1% ROI)
- 78756: $31,101 (6.3% ROI)

## Conclusions

Our final time series forecast model produced better ROI than our baseline model for all five of our zip code recommendations. We are confident in these predictions given that our model accounted for 99% or more of the explained variance in each of these zip codes. These results are further bolstered by the use of a train-test split, which helps prevent overfitting. 

Given these results, here are our recommendations to the stakeholders:
- These five zip codes represent good potential investments for the upcoming year based on ROI. 
- One thing to keep in mind is that the median value for each zip code is different. Thus, we recommend our stakeholders take these relative amounts into account when deciding where to invest. For example, our model predicts that 78756 will produce the largest amount of net profit, but the median housing price in this zip code is close to \\$500K. On the other hand, 78748 is closer to \\$300K but has almost double the predicted ROI compared to 78756 (12% vs. 6.3%). In other words, investing in 78748 will potentially produce higher ROI and net profit than 78756 with a smaller initial investment rate.
- Our baseline model demonstrated that 4 of the top 5 zip codes from 2009–2018 were in the downtown ATX area, but our final model suggests that 4 of the top 5 zip codes in the next year will be in the ATX suburbs. This is perhaps not too surprising, given that the continual expansion of the city means that there are more investment opportunities outside of downtown. We want our stakeholders to be aware of these geographical differences when making their investments. 


## Information

Check out our [notebook](https://github.com/Shoemaker703/time_series_project/blob/main/Project4_Main_Notebook.ipynb) for a more thorough discussion of our project, as well as our [presentation](https://github.com/andrewwhitman/BirdConservation/blob/main/presentation.pdf).

## Repository Structure

```

├── images                              <- folder containing images for README
│   └── ...
├── notebooks                           <- folder containing additional notebooks for data exploration and modeling
│   └── ...
├── .gitignore                          <- file specifying files/directories to ignore
├── BirdConservation.ipynb              <- notebook detailing the data science process containing code and narrative
├── README.md                           <- Top-level README
├── presentation.pdf                    <- presentation slides for a business audience
└── utils.py                            <- Contains helper function for model evaluation

``` 
