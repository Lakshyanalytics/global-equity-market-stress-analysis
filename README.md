# Global Equity Market Interdependence & Stress Scenario Analysis

**Python | Pandas | NumPy | Statsmodels | Financial Risk Analytics**

## 1. Project Overview

This project examines the interdependence of major international equity markets and evaluates the vulnerability of a global equity portfolio under historical and hypothetical market stress scenarios.

Using daily market data from January 2015 to December 2025, the analysis investigates cross-market relationships, volatility patterns, time-series properties and portfolio downside risk.

The project applies quantitative techniques used in financial market risk analysis, including correlation analysis, econometric testing, historical Value at Risk (VaR), Expected Shortfall (ES) and scenario-based stress testing.

## 2. Markets and Dataset

The analysis covers five major international equity indices:

| Market | Equity Index | Yahoo Finance Ticker |
|---|---|---|
| India | NIFTY 50 | `^NSEI` |
| United States | S&P 500 | `^GSPC` |
| United Kingdom | FTSE 100 | `^FTSE` |
| Japan | Nikkei 225 | `^N225` |
| Eurozone | EURO STOXX 50 | `^STOXX50E` |

- **Period:** January 2015 – December 2025
- **Frequency:** Daily
- **Source:** Yahoo Finance (`yfinance`)
- **Common observations:** 2,027 daily return observations across all five indices.

Different exchanges have different trading calendars. The individual price series therefore contain different numbers of observations. Portfolio-level comparisons use dates common to all five return series.

## 3. Methodology

### A. Data Collection and Preparation
- Retrieved daily closing prices for five international equity indices.
- Cleaned and consolidated market datasets.
- Examined missing observations and differences in exchange trading calendars.
- Calculated daily percentage returns.

### B. Market Interdependence Analysis
- Constructed correlation matrices to evaluate cross-market co-movement.
- Applied 60-trading-day rolling correlations against the S&P 500.
- Normalised index levels to compare relative price performance.

### C. Statistical and Econometric Analysis
- Applied the Augmented Dickey-Fuller (ADF) test to examine stationarity in price levels and daily returns.
- Applied the Johansen cointegration test to investigate potential long-run relationships between international equity indices.

### D. Portfolio Risk Measurement
- Constructed an equally weighted global equity portfolio.
- Calculated annualised returns and volatility.
- Estimated historical 95% and 99% Value at Risk (VaR).
- Calculated Expected Shortfall (ES).
- Evaluated maximum drawdown and worst rolling 10-day returns.

### E. Stress Scenario Analysis

Evaluated portfolio sensitivity under four hypothetical equity-market scenarios:

1. Broad Global Sell-off
2. US-led Market Correction
3. Asia-led Market Sell-off
4. Europe-led Market Sell-off

Additionally, examined portfolio and individual market performance during the February–March 2020 COVID-19 stress window.

## 4. Key Findings

### A. Annualised Market Risk Statistics

| Equity Index | Annualised Return | Annualised Volatility |
|---|---:|---:|
| NIFTY 50 | 14.89% | 15.63% |
| S&P 500 | 14.92% | 18.39% |
| FTSE 100 | 5.07% | 15.78% |
| Nikkei 225 | 7.49% | 20.86% |
| EURO STOXX 50 | 12.13% | 19.32% |

**Observations:**
- Nikkei 225 recorded the highest annualised volatility at 20.86%.
- NIFTY 50 recorded the lowest annualised volatility at 15.63%.
- S&P 500 and NIFTY 50 recorded similar annualised arithmetic returns over the sample period.

### B. Stationarity Analysis

The ADF tests produced the following findings:

- All five equity price-level series failed to reject the unit-root null hypothesis at the 5% significance level.
- All five daily return series rejected the unit-root null hypothesis at the 5% significance level.

This indicates that the price levels were non-stationary, while daily returns were stationary under the selected ADF specifications.

### C. Cointegration Analysis

The Johansen cointegration test did not reject the null hypotheses at the 5% significance level for any of the tested cointegration ranks.

Under the selected deterministic and lag specifications, the analysis did not find statistically significant evidence of a long-run cointegrating relationship among the five equity indices.

### D. COVID-19 Historical Stress Analysis

During the selected stress window (19 February – 23 March 2020):

| Equity Index | Cumulative Return |
|---|---:|
| EURO STOXX 50 | -30.29% |
| NIFTY 50 | -29.49% |
| FTSE 100 | -24.93% |
| Nikkei 225 | -24.79% |
| S&P 500 | -22.77% |

The equally weighted portfolio recorded a cumulative loss of **26.23%** during this period.

### E. Hypothetical Stress Scenario Results

| Scenario | Portfolio Shock |
|---|---:|
| Broad Global Sell-off | -20.00% |
| US-led Correction | -15.20% |
| Asia-led Sell-off | -20.00% |
| Europe-led Sell-off | -17.40% |

The broad global and Asia-led scenarios produced the largest portfolio shocks, each resulting in a simulated loss of 20%.

These results are deterministic sensitivity estimates based on predefined index-level shocks, rather than probability-weighted forecasts.

## 5. Technology Stack

- **Programming:** Python
- **Data Manipulation:** Pandas, NumPy
- **Statistical Analysis:** Statsmodels, SciPy
- **Visualisation:** Matplotlib, Seaborn
- **Data Collection:** yfinance
- **Development Environment:** Google Colab

## 6. Repository Structure

```text
global-equity-market-stress-analysis/
│
├── Global_Equity_Market_Stress_Analysis.ipynb
├── README.md
│
└── outputs/
    ├── global_equity_index_prices_2015_2025.csv
    ├── global_equity_daily_returns_2015_2025.csv
    ├── daily_return_correlation_matrix.csv
    ├── market_risk_summary.csv
    ├── portfolio_var_es.csv
    ├── hypothetical_scenario_results.csv
    └── johansen_cointegration_results.csv
```

## 7. How to Run

1. Clone or download the repository.
2. Open `Global_Equity_Market_Stress_Analysis.ipynb` in Google Colab.
3. Install the required Python libraries using the notebook setup cell.
4. Execute the notebook sequentially.
5. The notebook downloads the market data, performs the analysis and exports the results as CSV files.

## 8. Limitations and Assumptions

- Equity indices are analysed in their respective local currencies. Foreign exchange conversion is not incorporated.
- The analysis uses price-index data rather than consistently available total-return indices; dividends are therefore not included consistently.
- Hypothetical stress scenarios use predefined illustrative shocks and are not calibrated regulatory stress scenarios.
- Historical VaR and Expected Shortfall depend on the selected observation period and historical market conditions.
- The Johansen test results are sensitive to lag selection and deterministic-term assumptions.
- The analysis is an independent educational research exercise, not a production risk management or regulatory stress-testing framework.

## 9. Disclaimer

This project is an independent quantitative research exercise developed for educational and analytical purposes. Market data is sourced from Yahoo Finance through the `yfinance` library and is subject to data availability and applicable usage terms.
