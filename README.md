# Mean Reversion Pairs Trading Strategy

> A complete quantitative trading framework built in Python that uses statistical arbitrage on correlated stock pairs to determine whether a pair is tradeable — and how profitable it could be.

---

## Quick Start

You can run this notebook instantly in your browser — no installation needed:

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/YOUR_REPO/blob/main/mean_reversion_interactive.ipynb)

1. Click the button above
2. Select a stock pair from the dropdown (or enter your own)
3. Adjust the strategy parameters using the sliders
4. Click **▶ Run Analysis**
5. The full analysis runs automatically — no coding required

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

## How the Strategy Works

The spread between two correlated stocks follows an **AR(1) autoregressive process**:
