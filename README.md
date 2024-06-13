# Sales Analysis and Forecasting
(Check the report file for complete analysis)

An analysis of the sales of Walmart stores was conducted to provide insights into store performance and to check the effect of various factors on sales. Additionally, predictions of store performance for the next 12 weeks were made to assist in inventory management.

## Features of the Dataset

The dataset includes the following features for 45 stores over 143 weeks:
- **Store**: Store number
- **Date**: Week of sales
- **Weekly_Sales**: Sales for the given store in that week
- **Holiday_Flag**: Indicates if it is a holiday week
- **Temperature**: Temperature on the day of the sale
- **Fuel_Price**: Cost of the fuel in the region
- **CPI**: Consumer Price Index
- **Unemployment**: Unemployment rate

## Data Pre-processing Steps

1. **Data Types Check**: All features have either integer or float values except the date feature, which is an object type.
2. **Converting to datetime**: The date feature was converted to datetime format for proper use in subsequent steps.
3. **Null and Duplicate Values**: There are no null or duplicate values.

### Outlier Inspection

Outliers were found in:
- **Weekly_Sales**: 34 outliers, distributed across various stores:
  - Store 20: 7 outliers
  - Store 4: 6 outliers
  - Store 13: 6 outliers
  - Store 10: 5 outliers
  - Store 14: 4 outliers
  - Store 2: 2 outliers
  - Store 27: 2 outliers
  - Store 6: 1 outlier
  - Store 23: 1 outlier
- **Unemployment**

Despite the presence of outliers, no changes were made as the data per store was less and number of outliers compared to storewise sales data was insignificant.

## Insights from Analysis

### Weekly Sales vs Unemployment Rate
- Sales are concentrated where the unemployment rate is between 6 and 9.
- Higher total sales in regions with an unemployment rate greater than 9 compared to regions with a rate less than 6, likely due to a higher number of stores.
- Statistically significant correlation between unemployment and sales.
- Store-specific insights:
  - Store 36 shows a strong positive correlation between sales and unemployment rate.
  - Store 35 shows a similar but less pronounced trend.
  - Stores 38 and 44 show a strong negative correlation, indicating higher sales with a lower unemployment rate.

### Weekly Sales vs Temperature
- Maximum sales occur between 40 and 80 degrees.
- Sales reduce in extreme temperatures, suggesting better sales in pleasant weather.
- Statistically significant correlation between temperature and sales.
- Store-specific insights:
  - Most stores show a negative effect on sales with a rise in temperature, though the effect is not very pronounced.

### Weekly Sales vs Consumer Price Index (CPI)
- Three main clusters of CPI with respect to sales:
  - Cluster 1: CPI <= 143
  - Cluster 2: 181 <= CPI <= 200
  - Cluster 3: CPI >= 202
- Higher sales are seen in low and high CPI regions.
- Statistically significant correlation between CPI and sales.
- Store-specific insights:
  - Store 36 shows decreased sales with increased CPI.
  - Stores 14, 35, 30, and 43 show similar trends but less pronounced.
  - Stores 38 and 44 show increased sales with increased CPI.

### Weekly Sales vs Fuel Price
- Sales decrease at higher fuel prices, suggesting that higher fuel prices inconvenience customers.
- Statistically insignificant correlation between fuel price and sales.
- Store-specific insights:
  - Stores 36 and 35 are most negatively affected by rising fuel prices.
  - Stores 30, 14, and 43 show similar trends but less pronounced.
  - Stores 38 and 44 are positively affected by rising fuel prices.

### Seasonal Trends
- Seasonal increase in sales during the last two months of every year due to holidays and festivals.
- Over 90% of stores exhibit this seasonal trend in 2010 and 2011.

## Store-wise Prediction of Future Sales

Three algorithms were implemented:
- **ARIMA**: Effective for time series data by examining differences between values.
  - Components: Autoregression (AR), Integrated (I), Moving Average (MA)
- **SARIMA**: An extension of ARIMA that includes seasonal components.
  - Seasonal component accounted for observed seasonality in sales data.
- **Prophet**: Forecasts time series data with strong seasonal effects.
  - Handles missing data and outliers well.

### Parameters Evaluation

- **ARIMA and SARIMA Parameters**:
  - **Value of d**: Determined through statistical (ADFuller and KPSS tests) and visual methods (rolling mean plots).
  - **Values of p and q**: Determined using AutoCorrelation and Partial AutoCorrelation plots, and AIC scores.
  - **Seasonality (m)**: Set to 52 (weekly data).
- **Prophet Model**:
  - Auto-detected parameters, with interval width set to 0.95.

### Prediction Evaluation

- Time series data divided into train and test samples.
- All models trained using the train sample and predictions evaluated on the test sample.
- Predictions evaluated by plotting actual vs. predicted values and calculating RMSE.

### Example Predictions

#### Store 1
- Best model: SARIMA
- Predicted an increase in sales at year-end.
- Recommended moderate stocking of inventory.

#### Store 20
- Best model: SARIMA
- Predicted an increase in sales at year-end.
- Recommended moderate stocking of inventory.

## Future Scope

- Include factors like holidays and temperatures for more accurate predictions.
- Optimize locations for new stores based on unemployment, temperature, CPI, and fuel price factors.

