# Time-Series

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


