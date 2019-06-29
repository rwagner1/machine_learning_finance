# ml_finance

This repository contains proposed solutions to some assignments from Udacity's online course on Machine Learning in Finance https://classroom.udacity.com/courses/ud501

Please note that the code has not been verified by Udacity and there is no guarantee for 100% correctness. Instead, these are my personal suggestions how to solve the problem. Therefore any feedback is more than welcome.

Below is a summary of some technical terms that are explained throughout the course and might be used in the coding examples.

Rolling mean:
Standard moving average with chosen window size. Smoothing curve that slightly lags behind actual values. When rolling mean and actual price cross, might be a selling or buying sign. Significance can be obtained with Bollinger bands.

Bollinger bands:
Calculate rolling mean (standard moving average) and rolling std. Bollinger bands are the 2sigma rolling std from rolling mean. If crossing of rolling mean and actual values is above/below Bollinger band, probably selling/buying sign.

Daily return:
Percentage of daily changes: values[t]/values[t+1]-1. Useful tool to compare daily returns of different stock prices. Are movements of different stocks related? Plot over time periode with respective mean. Upward trend of stock values should be reflected in mean>0 and vice versa.

Filling missing data:
Forward (or backwar) fill (propagate last known value to next known value) in case of missing data. No interpolation, otherwise would "peak into the future". Use df.fillna(method=..., inplace=True). Inplace=True ensures the current df is updated

Scatter plots of daily returns (alpha, beta):
Compare daily returns of two different stocks using scatter plots (stock 1 vs stock 2 on one of each axis).

alpha = interception of line fitted in scatterplot. alpha>0: stock outperforms market
beta = slope of line fitted in scatterplot. "how reactive is stock to market?" beta=1->market goes up 1%, stock also goes up  1%
Portfolio statistics
Value of portfolio:

1) normalize dataset (including all stock prices for all assets)
2) multiply by allocations (sum of allocs = 1)
3) multiply by initial investment value, eg 1M
4) sum across rows to get daily value of portf

cumulative return: pf_value[-1]/pf_value[0]-1 (cumulated value of portfolio since start)
av daily return: daily_returns.mean()
std daily return: daily_returns.std()
sharpe ratio: sqrt(sampling)*(pf_return-riskfree_return)/pf_std (evaluating trade-off between high returns and risk, ie volatility), sampling=252 for daily sampling, 52 for weekly, 12 for monthly
daily risk free rate = (1+ annual_risk_free_rate)**(1/252)-1
