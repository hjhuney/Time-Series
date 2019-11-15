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

## Simple Moving Average (SMA) / Rolling Mean


In Pandas, we can use timeseries.rolling().mean()

```
# Simple moving (rolling) calculations
# Note: the rolling methods are applicable only on pandas Series and DataFrame objects
def plot_rolling(timeseries, window):
    rol_mean = timeseries.rolling(window).mean()
    rol_std = timeseries.rolling(window).std()
    
    fig = plt.figure(figsize = (12, 8))
    og = plt.plot(timeseries, color = "blue", label = "Original")
    mean = plt.plot(rol_mean, color = "red", label = "Rolling Mean")
    std = plt.plot(rol_std, color = "black", label = "Rolling Std")
    plt.legend(loc = "best")
    plt.title("Rolling Mean and Standard Deviation (window = "+str(window)+")")
    plt.show()
```

SMA with minimum number of periods. 

```
# Simple rolling calculation with minimum number of periods
def plot_rolling2(timeseries, window):
    rol_mean = timeseries.rolling(window, min_periods = 1).mean()
    rol_std = timeseries.rolling(window, min_periods = 1).std()
```


## Exponentially Weighted Moving Average (EWMA)

```
# Exponentially Weighted Moving Average
# Note: the ewm method is applicable on pandas Series and DataFrame objects only
def plot_ewma(timeseries, alpha):
    expw_ma = timeseries.ewm(alpha=alpha).mean()

    fig = plt.figure(figsize = (12, 8))
    og_line = plt.plot(timeseries, color = "blue", label = "Original")
    exwm_line = plt.plot(expw_ma, color = "red", label = "EWMA")
    plt.legend(loc = "best")
    plt.title("EWMA (alpha= "+str(alpha)+")")
    plt.show()
```

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

## Smoothers

Flattens out data in time series dataset. Very common with stock market pricing data. For instance, the "Simple Moving Average" (SMA) of a stock price over 50 days. You create this smoother by taking observations surrounding your data point and averaging them.

There is also an Expotentially Weighted Moving Average (EWMA) that gives more weight to latest observations. 


## Autoregressive Integrated Moving Average (ARIMA)

