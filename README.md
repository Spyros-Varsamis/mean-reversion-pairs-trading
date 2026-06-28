# mean-reversion-pairs-trading
"Statistical arbitrage pairs trading strategy  using AR(1) model Kalman filter and  Monte Carlo simulation"
# Mean Reversion Pairs Trading Strategy

A complete quantitative trading strategy built in Python
using statistical arbitrage on correlated stock pairs.

## What This Project Does

Takes any pair of correlated stocks and runs a complete
mean reversion analysis to determine if the pair is
tradeable using statistical arbitrage.

## Methodology

- **AR(1) Model**: Models spread dynamics using
  autoregressive process
- **Statistical Tests**: ADF test cointegration
  analysis and lambda significance testing
- **Kalman Filter**: Signal smoothing to reduce
  false trading signals
- **Backtesting**: Out of sample performance evaluation
- **Monte Carlo**: 1000 path simulation for probability
  of profit estimation

## Mathematical Foundation

The spread follows an AR(1) process:

rt = mu + lambda(rt-1 - mu) + sigma * zt

where lambda < 0 confirms mean reversion exists.

Trading signal uses z-score:

z = (spread - mu) / sigma

- z > +2: SHORT the spread
- z < -2: LONG the spread
- |z| < 0.5: CLOSE position
- |z| > 3.0: STOP LOSS

## Results

Pair tested: Visa (V) vs Mastercard (MA)
Period: 2021-2024

Statistical Tests:
- Correlation: 0.989 PASS
- Lambda: -0.022 (mean reversion confirmed)
- ADF p-value: 0.0009 PASS
- Half life: 31 days

Key Finding: Mean reversion statistically confirmed
but lambda too weak (-0.022) to overcome transaction
costs in the test period. Framework correctly
identified pair as borderline tradeable.

## Technologies Used

- Python 3.9
- pandas, numpy, matplotlib
- statsmodels, scipy
- Kalman filter implementation
- yfinance for data

## How to Run

1. Clone this repository
2. Install requirements: pip install -r requirements.txt
3. Open mean_reversion.ipynb in Jupyter
4. Change TICKER1 and TICKER2 to test different pairs
5. Run all cells top to bottom

## Skills Demonstrated

- Time series analysis
- Statistical hypothesis testing
- Stochastic processes (AR(1), Ornstein-Uhlenbeck)
- Signal processing (Kalman filter)
- Monte Carlo simulation
- Financial backtesting methodology
- Out of sample validation
