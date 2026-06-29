# Mean Reversion Pairs Trading Strategy

> A complete quantitative trading framework built in Python that uses statistical arbitrage on correlated stock pairs to determine whether a pair is tradeable — and how profitable it could be.

---

## Quick Start

## How to Run

When you open the notebook file on GitHub you will see the raw
code and markdown — that is normal. Do not try to run anything
from GitHub itself. Follow the steps below instead.

---

### Step 1 — Open in Colab

At the very top of the notebook preview on GitHub you will see
an orange button that says **"Open in Colab"**. Click it.

This is the only button you need to click on GitHub.
Everything else happens inside Colab.

---

### Step 2 — Make Your Own Copy

When Colab opens you will see a warning at the top saying the
notebook was not authored by Google. This is normal — just click
**"Run anyway"**.

Then make your own personal copy so your changes are saved:

1. Click **File** in the top menu
2. Click **Save a copy in Drive**
3. A new tab opens with your own copy
4. Work from this tab — not the original

---

### Step 3 — Install the Required Libraries

Before running anything for the first time you need to install
one library. Look for the first code cell at the very top of
the notebook — it starts with: !pip install yfinance ipywidgets

Click on that cell and press **Shift + Enter** to run it.
Wait about 10 seconds until it finishes.
You only need to do this once per session.

---

### Step 4 — Choose Your Stock Pair

Scroll down past the introduction until you see a form with a
dropdown menu and sliders. This is the configuration panel.

**To use a pre-loaded pair:**
- Click the dropdown and choose any pair from the list
- For example "V / MA — Payments" or "KO / PEP — Beverages"

**To test your own pair:**
- Select "Custom pair ✏️" at the bottom of the dropdown
- Two text boxes will appear
- Type the ticker symbol for each stock
  (a ticker is the short code used to identify a stock —
  for example AAPL for Apple, TSLA for Tesla, AMZN for Amazon)
- You can look up any ticker at finance.yahoo.com

**Tips for picking a good pair:**
- Both stocks should be in the same industry
- They should have an economic reason to move together
- Bad example: Apple and ExxonMobil — completely different businesses
- Good example: Visa and Mastercard — process the same payments

---

### Step 5 — Adjust the Parameters (Optional)

Below the pair selector you will find sliders. The defaults
work fine for a first run but here is what each one controls:

| Parameter | Default | What it means |
|-----------|---------|---------------|
| Entry Z | 2.0 | How unusual the spread must be before entering a trade. Higher = fewer but stronger signals |
| Exit Z | 0.5 | How close to normal the spread must return before closing the trade |
| Stop Z | 3.0 | Emergency exit if the trade moves too far against you |
| Capital $ | 10,000 | Starting portfolio size used in the backtest |
| Start date | 2020-01-01 | Beginning of the historical data period |
| End date | 2025-12-31 | End of the historical data period |

---

### Step 6 — Run the Full Analysis

1. Click the green **▶ Run Analysis** button in the config panel
2. Then click **Runtime** in the top menu bar
3. Click **Run all**
4. Scroll down and watch the full 7-step analysis appear

The notebook will download real stock data, run all the
statistical tests, build the model, backtest it, simulate
1000 futures, and give you a final YES or NO verdict.
This usually takes 1 to 3 minutes.

---

### Step 7 — Try a Different Pair

You do not need to restart to test a new pair:

1. Scroll back up to the configuration panel
2. Change the dropdown or type new tickers
3. Click **▶ Run Analysis**
4. Click **Runtime → Run all**
5. Everything updates automatically

---

### Something went wrong?

**"Runtime disconnected"**
Colab sessions time out after inactivity. Click
Runtime → Run all to restart.

**"Error" after typing a custom ticker**
The ticker is probably wrong. Check the exact symbol at
finance.yahoo.com and make sure the stock is on a US exchange.

**Most tests show FAIL**
This is not a bug — it means that pair does not have strong
enough mean reversion to trade. Try a different pair from
the suggested list.

**The charts are not showing**
Make sure you clicked ▶ Run Analysis before clicking
Runtime → Run all. The button must be clicked first to
save your settings.

---

## What This Project Does

Takes any two correlated stocks and runs a complete 7-step mean reversion analysis:

| Step | Name | What it does |
|------|------|-------------|
| 1 | Data Loading | Downloads real price data and visualizes the relationship |
| 2 | Statistical Tests | Mathematically proves whether mean reversion exists |
| 3 | AR(1) Model | Estimates the stochastic model parameters |
| 4 | Kalman Filter | Smooths the signal to reduce false trades |
| 5 | Backtest | Tests the strategy on data the model never saw |
| 6 | Monte Carlo | Simulates 1000 possible futures |
| 7 | Final Verdict | YES / NO decision with full reasoning |

---

