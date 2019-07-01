# ml_finance

<p>This repository contains solutions of assignments from Udacity's online course on Machine Learning in Finance https://classroom.udacity.com/courses/ud501
</p>
<p>
Below is a summary of some technical terms and concepts that are explained throughout the course and might be used in some of the code.
</p>
<p>
<b>Rolling mean:</b><br>
Standard moving average with chosen window size. A smoothing curve that slightly lags behind the actual values. When rolling mean and actual price cross there might be a selling or buying opportunity. Significance can be obtained with Bollinger bands.
</p>
<p>
<b>Bollinger bands:</b><br>
Calculate rolling mean (standard moving average) and rolling standard deviation. Bollinger bands are the two-sigma rolling deviation from the rolling mean. If the crossing of rolling mean and the actual price is above/below Bollinger band, probably selling/buying sign.
</p>
<p>
<b>Daily return:</b><br>
Percentage of daily changes: values[t]/values[t+1]-1.<br>Useful tool to compare daily returns of different stock prices. Are movements of different stocks related? Plot over time periode with respective mean. Upward trend of stock values should be reflected in mean>0 and vice versa.
</p>
<b>Cumulative return:</b><br>
Percentage of cumulative changes: values[-1]/values[0]-1.<br>Compare the last price of a portfolio to the initial value. How much have you gained/lost since the beginning?
</p>

<p>
<b>How to fill missing data?</b><br>
Forward (or backwar) fill (propagate last known value to next known value) in case of missing data. No interpolation, otherwise would "peak into the future". Use df.fillna(method=..., inplace=True). Inplace=True ensures the current df is updated
</p>
<p>
    <b>Alpha and Beta:</b><br>
    alpha = interception of line fitted in a scatterplot. alpha>0: stock outperforms market
    beta = slope of line fitted in scatterplot. "how reactive is stock to market?" beta=1->market goes up 1%, stock also goes up  1%
</p>
<b>Portfolio statistics</b><br>
  
This is how you can obtain the value of a portfolio:
<ul>
  <ol>0) compute the daily return for all stocks</ol> 
  <ol>1) normalize dataset (including all stock prices for all assets)</ol>
  <ol>2) multiply by allocations (sum of allocs = 1)</ol>
  <ol>3) multiply by initial investment value</ol>
  <ol>4) sum across rows to get the daily return of the entire portfolio</ol>
</ul>

<p>
<b>Sharpe Ratio</b><br>
A measure to evaluate a portfolio's performance taking into account the volatility (ie risk) of the underlying assets. The higher the sharpe ratio, the higher the porfolio's value.
sqrt(sampling)*(pf_return-riskfree_return)/pf_std
</p>
 (evaluating trade-off between high returns and risk, ie volatility), sampling=252 for daily sampling, 52 for weekly, 12 for monthly
daily risk free rate = (1+ annual_risk_free_rate)**(1/252)-1
