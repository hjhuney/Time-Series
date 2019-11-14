# Time-Series Data

# Coding in Python

## Time Series Range in Pandas

In Pandas, you can create a time series range.

```
mylynxts = pd.Series(mylynx_df['trappings'].values,
                     index = pd.date_range('31/12/1821' ,
                                           periods = 114,
                                           freq = 'A-DEC'))
```

In the above example, the frequence argument allow us to specify time period ("A" is annual) and "DEC" means we use the last day of December. 

Other options:

* "D" for day
* "B" for business day
* "H" for hour
* "T" for minutes
* "S" for seconds


# Statistical Concepts


## Homoscedastic vs Heteroscedastic

Homoscedestic means the variance stays relatively constant in time-series data. Heteroscedestic means the variance changes over time; for instance maybe the variance is lower from 1960 - 1980 and increases from 1980 - 2000 in a dataset. 

In time-series data, dataset could have low variance but appear to be "high variance" due to seasonality. 

## Stationarity

Does data have same statistical properties throughout the time series?

* Variance
* Mean
* Autocorrelation

Most models require stationairty. Can you use transformations and differencing to change data. Used extensively in ARIMA.

To test whether data is stationary, can use Augmented Dickey-Fuller Test. 

## Autocorrelation

Can only be present in ordered data. It is the similiarity between observations based on the time lag between them (i.e. repeating patterns). Trend and seasonality are a product of autocorrelation. 

ACF and PACF plots show autocorrelation. 
