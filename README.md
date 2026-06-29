# Mean Reversion Pairs Trading Strategy

> A complete quantitative trading framework built in Python that uses statistical arbitrage on correlated stock pairs to determine whether a pair is tradeable — and how profitable it could be.

---

## How to Run

When you open the notebook file on GitHub you will see the raw
code and markdown — that is normal. Do not try to run anything
from GitHub itself. Follow the steps below instead.

---

### Step 1 — Open in Colab

At the very top of the notebook preview on GitHub you will see
an orange button that says "Open in Colab". Click it.

This is the only button you need to click on GitHub.
Everything else happens inside Colab.

---

### Step 2 — Sign in to Google

Colab requires a Google account to run notebooks. If you have
Gmail you already have one — use the same email and password.

If you do not have a Google account:
1. Go to accounts.google.com
2. Click "Create account"
3. Follow the steps — it is free and takes about 2 minutes
4. Once done, come back and click "Open in Colab" again

When Colab opens you may see a warning saying the notebook was
not authored by Google. This is normal — just click "Run anyway".

---

### Step 3 — Make Your Own Copy

Once you are signed in, make a personal copy so your changes
are saved and do not affect anyone else:

1. Click File in the top menu
2. Click "Save a copy in Drive"
3. A new tab opens with your own personal copy
4. Work from this tab from now on — not the original

---

### Step 4 — Install the Required Libraries

Before running anything for the first time you need to install
one library. Look for the first code cell at the very top of
the notebook — it starts with:

!pip install yfinance ipywidgets

Click on that cell and press Shift + Enter to run it.
Wait about 10 seconds until it finishes.
You only need to do this once per session.

---

### Step 5 — Choose Your Stock Pair

Scroll down past the introduction until you see a form with a
dropdown menu and sliders. This is the configuration panel.

To use a pre-loaded pair:
- Click the dropdown and choose any pair from the list
- For example "V / MA — Payments" or "KO / PEP — Beverages"

To test your own pair:
- Select "Custom pair" at the bottom of the dropdown
- Two text boxes will appear
- Type the ticker symbol for each stock
  (a ticker is the short code used to identify a stock —
  for example AAPL for Apple, TSLA for Tesla, AMZN for Amazon)
- You can look up any ticker at finance.yahoo.com

Tips for picking a good pair:
- Both stocks should be in the same industry
- They should have an economic reason to move together
- Bad example: Apple and ExxonMobil — completely different businesses
- Good example: Visa and Mastercard — process the same payments

---

### Step 6 — Adjust the Parameters (Optional)

Below the pair selector you will find sliders. The defaults
work fine for a first run but here is what each one controls:

Parameter   | Default    | What it means
Entry Z     | 2.0        | How unusual the spread must be before entering a trade. Higher = fewer but stronger signals
Exit Z      | 0.5        | How close to normal the spread must return before closing the trade
Stop Z      | 3.0        | Emergency exit if the trade moves too far against you
Capital $   | 10,000     | Starting portfolio size used in the backtest
Start date  | 2020-01-01 | Beginning of the historical data period
End date    | 2025-12-31 | End of the historical data period

---

### Step 7 — Run the Full Analysis

1. Click the green Run Analysis button in the config panel
2. Then click Runtime in the top menu bar
3. Click Run all
4. Scroll down and watch the full 7-step analysis appear

The notebook will download real stock data, run all the
statistical tests, build the model, backtest it, simulate
1000 futures, and give you a final YES or NO verdict.
This usually takes 1 to 3 minutes.

---

### Step 8 — Try a Different Pair

You do not need to restart to test a new pair:

1. Scroll back up to the configuration panel
2. Change the dropdown or type new tickers
3. Click Run Analysis
4. Click Runtime → Run all
5. Everything updates automatically

---

### Something Went Wrong?

"Runtime disconnected"
Colab sessions time out after inactivity. Click
Runtime → Run all to restart.

"Error" after typing a custom ticker
The ticker is probably wrong. Check the exact symbol at
finance.yahoo.com and make sure the stock is on a US exchange.

Most tests show FAIL
This is not a bug — it means that pair does not have strong
enough mean reversion to trade. Try a different pair from
the suggested list.

The charts are not showing
Make sure you clicked Run Analysis before clicking
Runtime → Run all. The button must be clicked first to
save your settings.

---

## What This Project Does

Takes any two correlated stocks and runs a complete 7-step mean reversion analysis:

Step 1 — Data Loading: Downloads real price data and visualizes the relationship
Step 2 — Statistical Tests: Mathematically proves whether mean reversion exists
Step 3 — AR(1) Model: Estimates the stochastic model parameters
Step 4 — Kalman Filter: Smooths the signal to reduce false trades
Step 5 — Backtest: Tests the strategy on data the model never saw
Step 6 — Monte Carlo: Simulates 1000 possible futures
Step 7 — Final Verdict: YES / NO decision with full reasoning

---

## How the Strategy Works

The spread between two correlated stocks follows an AR(1) autoregressive process:

rt = μ + λ(rt-1 − μ) + σ·zt

Where:
μ  = Long-run mean — where the spread naturally wants to live
λ  = Mean reversion speed — must be negative for the strategy to work
σ  = Daily volatility
zt = Random shock drawn from N(0,1)

A negative λ means the spread gets pulled back toward the mean — this is the core of the strategy.

Trading signals are based on the z-score:

z = (spread − μ) / σ

z > +2.0  → SHORT the spread
z < −2.0  → LONG the spread
|z| < 0.5 → CLOSE — take profit
|z| > 3.0 → STOP LOSS — exit immediately

---

## Suggested Pairs to Test

V / MA    — Payments   — Process the same card transactions
KO / PEP  — Beverages  — Compete for the same consumers
GS / MS   — Banking    — Same investment banking business
XOM / CVX — Oil        — Both track global oil prices
WMT / TGT — Retail     — Same customer base and business model
JPM / BAC — Banking    — US commercial banking leaders
NEE / DUK — Utilities  — Regulated monopolies, same business model

---

## Example Results

Pair tested: Visa (V) vs Mastercard (MA) — Period: 2021–2024

Correlation  0.989   PASS
Lambda      −0.022   Mean reversion confirmed
ADF p-value  0.0009  PASS
Half life   31 days  Borderline

Key finding: Mean reversion is statistically real for this pair,
but λ = −0.022 is too weak to overcome transaction costs at standard
position sizes. The framework correctly flagged it as borderline —
a good example of the model working as intended.

---

## Project Structure

mean_reversion_interactive.ipynb — Main notebook with interactive UI
requirements.txt                 — Python dependencies
README.md                        — This file

---

## Skills Demonstrated

- Time series analysis and stationarity testing
- Statistical hypothesis testing (ADF, t-statistics)
- Stochastic processes — AR(1) and Ornstein-Uhlenbeck
- Signal processing with Kalman filter
- Monte Carlo simulation
- Financial backtesting with out-of-sample validation
- Interactive notebook UI with ipywidgets

---

## Technologies

Python 3.9 · pandas · numpy · matplotlib · statsmodels · scipy · yfinance · ipywidgets · voila

---

Data sourced from Yahoo Finance via yfinance
