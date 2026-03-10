# Portfolio Analysis Project

This Jupyter notebook analyzes and backtests a stock portfolio using historical data from major tech and financial stocks. It fetches data via yfinance, computes returns, and generates performance metrics with pyfolio for comprehensive evaluation. 

## Key Features

- Downloads adjusted close prices for NVDA, GS, MSFT (1999-2026) and SPY benchmark (1993-2026).
- Calculates daily returns using pct_change().
- Benchmarks against SPY for alpha/beta computation.
- Creates tearsheets showing cumulative returns, drawdowns, and risk metrics. 

## Technical Concepts

Pandas handles DataFrames for price alignment and return calculations via .pct_change() for log returns approximation. Pyfolio generates tearsheets with Sharpe ratio (risk-adjusted return), Sortino (downside risk), and Calmar (return/max drawdown). Weights (NVDA:40%, GS:40%, MSFT:20%) are applied via matrix multiplication for portfolio returns. 

## Financial Concepts

**Portfolio Returns**: Weighted sum of asset returns; portfolio return = Σ (weight_i * asset_return_i). **Sharpe Ratio**: (portfolio_return - risk_free)/volatility; measures excess return per risk unit. **Max Drawdown**: Largest peak-to-trough decline, e.g., -78.84% during 2008 crisis. **Alpha/Beta**: Alpha is excess return over benchmark (0.04 overall); beta (1.33) indicates higher market sensitivity. 

| Metric | In-Sample | Out-of-Sample | All Periods |
|--------|-----------|---------------|-------------|
| Annual Return | 8.271% | 35.705% | 11.196%   |
| Sharpe Ratio | 0.40 | 1.24 | 0.47   |
| Max Drawdown | -78.844% | -30.896% | -78.844%   |

## Setup Instructions

1. Install dependencies: `pip install yfinance pyfolio pandas matplotlib`.
2. Run notebook cells sequentially; data auto-downloads via yf.Ticker(ticker).history(period="max")["Close"].
3. Customize tickers/weights in later cells for new portfolios. 

## Results Summary

Portfolio outperforms benchmark in out-of-sample (Sharpe 1.24 vs. implied market ~0.5) but shows high volatility/drawdowns. Cumulative returns reach 1617% overall, driven by NVDA/GS exposure. 