# TMT Alpha Strategy: Volatility-Adjusted Momentum and Earnings Revisions

This project explores a quantitative long/short equity strategy focused on Technology, Media, and Telecommunications (TMT) sector stocks. The model combines **volatility-adjusted momentum** and **earnings revision signals** to generate alpha over a benchmark (XLK ETF).

## Strategy Overview

The notebook implements and evaluates three signal-driven strategies:
- **Momentum-only strategy** (using 60-day returns)
- **Earnings revision-only strategy** (using 5-day returns)
- **Combined strategy** (blended signal of both)

Each strategy ranks stocks daily and forms long/short portfolios from the top and bottom quantiles. Performance is benchmarked against the XLK ETF.

## Key Features

- **Universe**: TMT stocks (e.g., AAPL, MSFT, AMZN, GOOG, META, etc.)
- **Signal Construction**:
  - *Momentum*: Past 60-day return
  - *Revisions*: Short-term (5-day) return to simulate analyst sentiment changes
- **Volatility Adjustment**: Returns scaled by standard deviation to improve signal stability
- **Portfolio Formation**:
  - Daily ranking into quantiles
  - Long top quantile, short bottom quantile
- **Backtest Period**: Jan 2022 – Dec 2024
- **Performance Metrics**:
  - Sharpe Ratio
  - Max Drawdown
  - Cumulative Return

## Final Results

| Strategy        | Sharpe Ratio | Max Drawdown |
|----------------|--------------|---------------|
| Momentum-only  | 0.17         | -44.87%       |
| Revision-only  | -0.40        | -65.61%       |
| Combined       | -0.40        | -65.61%       |
| XLK (Benchmark)| 0.54         | -32.42%       |

> Note: While the revision and combined strategies underperformed, the momentum-only strategy showed positive alpha and lower volatility than XLK during the period.

## Tools & Libraries

- Python, pandas, numpy
- yfinance (for data)
- matplotlib, seaborn (visualisation)

## Files

- `TMT_Alpha_Strategy.ipynb` — Main notebook with strategy logic, simulation, and evaluation
- `README.md` — Project description and methodology

## Future Enhancements

- Introduce sector-neutral or market-neutral weighting
- Use real earnings forecast changes instead of short-term returns
- Add transaction cost simulation
- Explore machine learning for signal blending

---

## About

This project was built to develop and evaluate systematic alpha strategies within a clearly defined equity universe. It can serve as a template for further quantitative research or interview demonstrations.
