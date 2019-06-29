# ml_finance


This repository contains proposed solutions to some assignments from Udacity's online course on Machine Learning in Finance https://classroom.udacity.com/courses/ud501


Below is a summary of some technical terms that are explained throughout the course and might be used in proposed solutions.

<b>Rolling mean:</b>
Standard moving average with chosen window size. A smoothing curve that slightly lags behind the actual values. When rolling mean and actual price cross there might be a selling or buying opportunity. Significance can be obtained with Bollinger bands.

<b>Bollinger bands:</b>
Calculate rolling mean (standard moving average) and rolling standard deviation. Bollinger bands are the two-sigma rolling deviation from the rolling mean. If the crossing of rolling mean and the actual price is above/below Bollinger band, probably selling/buying sign.

<b>Daily return:</b>
Percentage of daily changes: values[t]/values[t+1]-1. Useful tool to compare daily returns of different stock prices. Are movements of different stocks related? Plot over time periode with respective mean. Upward trend of stock values should be reflected in mean>0 and vice versa.

<b>How to fill missing data?</b>
Forward (or backwar) fill (propagate last known value to next known value) in case of missing data. No interpolation, otherwise would "peak into the future". Use df.fillna(method=..., inplace=True). Inplace=True ensures the current df is updated

<b>Alpha and Beta:</b>
alpha = interception of line fitted in a scatterplot. alpha>0: stock outperforms market
beta = slope of line fitted in scatterplot. "how reactive is stock to market?" beta=1->market goes up 1%, stock also goes up  1%

<b>Portfolio statistics</b>
  
This is how you can obtain the value of a portfolio:
<ul>
  <li>0) compute the daily return for all stocks</li> 
  <li>1) normalize dataset (including all stock prices for all assets)</li>
  <li>2) multiply by allocations (sum of allocs = 1)</li>
  <li>3) multiply by initial investment value</li>
  <li>4) sum across rows to get the daily return of the entire portfolio</li>
</ul>

cumulative return: pf_value[-1]/pf_value[0]-1 (cumulated value of portfolio since start)
av daily return: daily_returns.mean()
std daily return: daily_returns.std()
sharpe ratio: sqrt(sampling)*(pf_return-riskfree_return)/pf_std (evaluating trade-off between high returns and risk, ie volatility), sampling=252 for daily sampling, 52 for weekly, 12 for monthly
daily risk free rate = (1+ annual_risk_free_rate)**(1/252)-1
