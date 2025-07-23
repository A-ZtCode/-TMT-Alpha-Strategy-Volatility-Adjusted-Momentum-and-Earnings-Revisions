# 📊 TMT Alpha Strategy: Volatility-Adjusted Momentum & Earnings Revisions

This project explores a quantitative long/short equity strategy focused on the **Technology, Media, and Telecom (TMT)** sector. The approach combines **volatility-adjusted momentum** with simulated **earnings revision signals** to generate alpha. The strategy is benchmarked against the **XLK ETF** (representing large-cap tech performance).

---

## 📈 Strategy Overview

This notebook simulates and compares the performance of three strategies:

1. **Momentum-only strategy**
2. **Earnings revision-only strategy**
3. **Combined strategy** (weighted blend of momentum and revision signals)

The goal is to determine whether blending these signals yields better risk-adjusted returns compared to using either signal alone or the XLK ETF benchmark.

---

## 🧠 Methodology

### 1. **Universe Selection**
- TMT sector tickers used: `['AAPL', 'MSFT', 'GOOG', 'META', 'NFLX', 'AMZN', 'DIS', 'CRM', 'ADBE', 'VZ']`
- Daily adjusted close prices pulled via `yfinance`

### 2. **Signal Construction**
- **Momentum**: Based on recent price performance (5-day returns)
- **Earnings Revisions (simulated)**: Also based on 5-day returns (used as a proxy for analyst activity)

Each signal is ranked daily, and stocks are assigned to quantiles (Q0 = top 20%, Q4 = bottom 20%).

### 3. **Strategy Logic**
- **Long** top quantile
- **Short** bottom quantile
- Positions are rebalanced daily

### 4. **Combined Signal**
- Weighted blend:  
  `combined_score = momentum_weight * momentum_score + (1 - momentum_weight) * revision_score`

A sweep is performed across different momentum weights (0.0 to 1.0) to find the optimal blend.

---

## 📊 Results Summary

| Strategy           | Sharpe Ratio | Max Drawdown |
|--------------------|--------------|----------------|
| Momentum-only      | 0.17         | -44.87%         |
| Revision-only      | -0.40        | -65.61%         |
| Combined           | -0.40        | -65.61%         |
| XLK ETF (Benchmark)| 0.54         | -32.42%         |

🔎 **Insight**: The momentum-only strategy performed best among the three. The combined and revision-only strategies underperformed the benchmark, possibly due to signal redundancy or market inefficiency.

---

## 📁 Files

- `TMT_Alpha_Strategy.ipynb` – main notebook with complete implementation
- `README.md` – project overview

---

## 📌 Dependencies

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `yfinance`

Install with:
```bash
pip install pandas numpy matplotlib seaborn yfinance
