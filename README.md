# ml_finance

This repository contains solutions (.py files and Jupyter notebooks) of assignments from Udacity's online course on Machine Learning in Finance https://classroom.udacity.com/courses/ud501

Correctness is not guaranteed, these are suggestions how to solve the problems but have not been revistited by Udacity course teachers.



Below is a summary of some technical terms and concepts that are explained throughout the course and might be used in some of the code.

<b>Rolling mean:</b><br>
Standard moving average with chosen window size. A smoothing curve that slightly lags behind the actual values. When rolling mean and actual price cross, it might be interpreted as a selling or buying sign depending on the significance. Whether or not the buy/sell opportunity is significant can be calculated with Bollinger bands.


<b>Bollinger bands:</b><br>
Calculate rolling mean (standard moving average) and rolling standard deviation. Bollinger bands are the two-sigma rolling deviation from the rolling mean. If the crossing of rolling mean and the actual price is above/below Bollinger band, it's probably a "significant" selling/buying sign (don't quote me on this!).


<b>Daily return:</b><br>
Percentage of daily changes: values[t]/values[t+1]-1.<br>Useful tool to compare daily returns of different stock prices. Are movements of different stocks related? Plot over time periode with respective mean. Upward trend of stock values should be reflected in mean>0 and vice versa.


<b>Cumulative return:</b><br>
Percentage of cumulative changes: values[-1]/values[0]-1.<br>Compare the last price of a portfolio to the initial value. How much have you gained/lost since the beginning?


<b>How to fill missing data?</b><br>
A stock might have missing values for certain dates it didn't trade. Those can be either forward or backward filled.<br>Forward fill: We propagate the last known value to the next known value, hence obtain a straight line. <br>Backward fill: Similar. We propagate the first known value back to the first missing one.<br> Any kind of interpolation is not recommended, otherwise we could "peak into the future".


<b>Alpha and Beta:</b><br>
    Choose an asset x and compare it to a reference (the market) y, e.g. S&P500. Plot x, y in a scatter plot and fit a line.<br>
    <p>
    <i>alpha</i>:<br>interception of the fitted line. If alpha > 0, the asset x outperforms the market.</p>
    <p>
    <i>beta</i>:<br>slope of the fitted line. A measure of "how reactive" the stock is to the market. If beta = 1, as the market goes up by 1%, the stock follows linearily, hence goes up by 1% too.</p>


<b>Portfolio statistics</b><br>
  
This is how you can obtain the value of a portfolio:
<ul>
  <ol>0) compute the daily return for all stocks</ol> 
  <ol>1) normalize dataset (including all stock prices for all assets)</ol>
  <ol>2) multiply by allocations (sum of allocs = 1)</ol>
  <ol>3) multiply by initial investment value</ol>
  <ol>4) sum across rows to get the daily return of the entire portfolio</ol>
</ul>


<b>Risk free rate</b><br>
Estimated return for a zero-risk investment strategy (leaving your money in the bank account). We calculate the daily risk free rate from the annual rate as follows (there are 252 trading days each year):<br>
daily risk free rate = (1+ annual_risk_free_rate)<sup>(1/252)</sup>-1


<b>Sharpe Ratio</b><br>
A measure to evaluate a portfolio's performance taking into account the volatility (ie risk) of the underlying assets. It allows us to consider the trade-off between high returns and high risks.<p>The lower the standard deviation (std) of daily returns (volatility) and the higher the daily return average, the higher the sharpe ratio. The higher the sharpe ratio, the higher the porfolio's value.</p>

Hence the formula for the annualized sharpe ratio is:<br>sharpe = <span>&#8730;</span>252*(average_daily_return-daily_risk_free_rate)/std_daily_return

