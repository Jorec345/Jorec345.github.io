# Event Study: Measuring Market Reaction to News

In financial markets, news moves prices. That is positive or negative news can either drive up prices or cause a decline in the asset prices of a particular stock. But how can we **quantify** the impact of a news event, such as an earnings announcement, merger,policy change, pandemics or event death of a key shareholder on stock prices?

The **Event Study Methodology** is a methodology often used to analyze the markets reaction to new information assuming perfect markets where there is free flow of information. It helps determine whether an event leads to **abnormal returns**, and whether these reactions are **statistically significant**.




## Defining an event study

An event study is a statistical method used to **measure the effect of a specific event on the value of a firm**. This effect is estimated by taking the difference between the expected returns and the actual returns which is called the abnormal returns. 

Then we aggregate abnormal returns around the event, we get the **cumulative abnormal return (CAR)**, which reflects the total market reaction to the event.



## Why event study?

Importance of event study:
- It helps in testing for market efficiency.
- It helps in Understanding investor behavior and sentiment.
- It aids in evaluating the impact of policy announcements.
- It helps in assessing corporate decisions like dividend changes or acquisitions


## The Event Study Process

### 1. **Define the Event**
Identify a clearly defined event, such as:
- Earnings release
- Dividend announcement
- CEO resignation
- Regulatory policy announcement
- M&A activity

*Example: Apple announces a new product on day t = 0.*

### 2. **Choose the Event Window**
This includes:
- **Estimation window**: Used to calculate the "normal" returns (e.g., -250 to -30 trading days before the event)
- **Event window**: The period during which we expect the market to react (e.g., -1 to +1 days around the event)


### 3. **Estimate Normal Returns**
We estimate the expected return using models like:

####  The Market Model
A linear regression model:
$$
R_{it} = \alpha_i + \beta_i R_{mt} + \epsilon_{it}
$$

Where:
- \( R_{it} \): return of stock \( i \) on day \( t \)
- \( R_{mt} \): return of the market index on day \( t \)
- \( \alpha_i, \beta_i \): firm-specific regression coefficients
- \( \epsilon_{it} \): error term (abnormal return)

Other models:
- Constant Mean Return Model
- CAPM
- Fama-French 3-factor Model (for multi-factor risk-adjusted return estimation)


### 4. **Calculate Abnormal Returns (AR)**
Subtract the expected return from the actual return:
$$
AR_{it} = R_{it} - \hat{R}_{it}
$$


### 5. **Compute Cumulative Abnormal Returns (CAR)**
Add abnormal returns across the event window:
$$
CAR_{i}(t_1, t_2) = \sum_{t=t_1}^{t_2} AR_{it}
$$

For a sample of firms/events, calculate the **Average CAR (ACAR)** across firms.



### 6. **Test for Statistical Significance**
Use t-tests to check whether:
- \( AR_t \neq 0 \)
- \( CAR_{(t_1, t_2)} \neq 0 \)


## Event Study implementation

Here’s a simple example using Python with the market model:

```python
import pandas as pd
import numpy as np
import statsmodels.api as sm

# Load daily returns data
stock_returns = pd.read_csv("AAPL_returns.csv")  # Stock returns
market_returns = pd.read_csv("SP500_returns.csv")  # Market index returns

# Step 1: Estimation window (e.g., first 200 days)
est_window = 200
X = sm.add_constant(market_returns['Return'][:est_window])
y = stock_returns['Return'][:est_window]
model = sm.OLS(y, X).fit()
alpha, beta = model.params

# Step 2: Event window (e.g., day 201 to 203)
event_days = [201, 202, 203]
expected_returns = alpha + beta * market_returns['Return'][event_days].values
actual_returns = stock_returns['Return'][event_days].values
abnormal_returns = actual_returns - expected_returns
CAR = abnormal_returns.sum()

print("Cumulative Abnormal Return (CAR):", CAR)
