# FRTB Internal Models Approach (IMA) – Market Risk Capital Framework

## Project Overview

This project demonstrates an educational Python implementation of key concepts and workflows associated with the Fundamental Review of the Trading Book (FRTB) – Internal Models Approach (IMA).

The objective is to understand how trading-book positions are mapped to market risk factors, how Expected Shortfall and other risk measures are explored, and how model assessment and reporting activities fit into the IMA framework.

The project uses an illustrative portfolio of 12 trades across equities, interest rates, credit, foreign exchange and commodities.

**Note:** This is an educational prototype. It is not a Basel-compliant or regulatory-approved FRTB-IMA capital calculation engine.

## Project Objectives

- Build and validate a multi-asset trading book.
- Collect and prepare historical market data.
- Map trades to relevant market risk factors.
- Demonstrate risk-factor observation screening.
- Calculate historical Expected Shortfall (ES) at the 97.5% confidence level.
- Explore liquidity horizon adjustments and stress calibration.
- Understand modellable and non-modellable risk factors.
- Demonstrate an illustrative Default Risk Charge (DRC) simulation.
- Explore backtesting and Profit and Loss Attribution Testing (PLAT).
- Consolidate the results into structured risk reports.

## Implementation Steps

### Step 1 – Trading Book Construction

Created an illustrative trading book containing 12 trades across multiple asset classes and financial instruments.

The portfolio includes:
- Cash equities
- Government and corporate bonds
- Foreign exchange forwards
- Interest rate swaps
- Futures
- Equity options

Validated trade identifiers, asset-class classifications, product types and relevant trade attributes.

**Output:** `data/trade_book.csv`

### Step 2 – Historical Market Data Collection

Collected historical market prices using Yahoo Finance (`yfinance`) for selected market instruments and proxies.

The dataset includes:
- Apple and Microsoft equities
- NVIDIA
- S&P 500 ETF
- US Treasury ETF
- Gold and Silver ETFs
- EUR/USD
- USD/INR

**Output:** `data/market_prices.csv`

### Step 3 – Risk Factor Mapping

Mapped individual trades to their relevant market risk factors.

Examples include:
- Equity price risk
- Interest rate risk
- Credit spread risk
- Foreign exchange risk
- Commodity price risk
- Implied volatility risk for options

**Output:** `data/risk_factor_mapping.csv`

### Step 4 – Risk Factor Eligibility Test (RFET) Screening

Prepared historical market observations in a structured format and performed an illustrative observation-count screening exercise.

The objective was to understand how historical observations relate to the assessment of risk-factor modellability.

**Output:** `outputs/rfet_screening_summary.csv`

### Step 5 – Expected Shortfall (ES) Calculation

Calculated historical Expected Shortfall at the 97.5% confidence level using portfolio return proxies.

Historical VaR was also calculated to provide a comparison with Expected Shortfall.

**Output:** Historical ES and VaR results within the notebook.

### Step 6 – Liquidity Horizon Adjustment

Explored the impact of different liquidity horizons on risk-factor Expected Shortfall.

Used illustrative liquidity horizons of 10 and 20 days to demonstrate how longer liquidation periods can affect risk estimates.

**Output:** `outputs/liquidity_horizon_summary.csv`

### Step 7 – Stress Calibration

Analysed historical market movements during the COVID-19 stress period (February–April 2020).

Calculated stress-period VaR and ES for individual risk-factor proxies and compared stress ES with normal-period ES.

**Output:** 
- `data/stress_period_prices.csv`
- `outputs/stress_calibration_summary.csv`

### Step 8 – Non-Modellable Risk Factors (NMRF) and SSRM

Created illustrative modellability classifications for selected risk factors.

Identified assumed non-modellable risk factors and calculated a simplified stress-based risk measure to demonstrate the concept of the Stress Scenario Risk Measure (SSRM).

**Output:** `outputs/nmrf_ssrm_summary.csv`

### Step 9 – Default Risk Charge (DRC)

Selected corporate bond trades and assigned illustrative credit ratings, probability of default and loss-given-default assumptions.

Used Monte Carlo simulation to generate default-loss scenarios and estimate a 99.9th-percentile tail loss.

**Output:** `outputs/drc_simulation_summary.csv`

### Step 10 – Capital Component Summary

Consolidated the illustrative risk measures into a summary covering:

- Historical Expected Shortfall
- Non-Modellable Risk Factor SSRM proxy
- Default Risk Charge simulation result

The components were reported separately because the prototype does not implement the prescribed regulatory aggregation methodology.

**Output:** `outputs/capital_components_summary.csv`

### Step 11 – Backtesting

Implemented a simplified historical backtesting exercise using a rolling 250-observation window.

Compared portfolio proxy losses against a 99% historical VaR threshold and identified exceptions.

Calculated the exception count and exception rate.

**Outputs:**
- `outputs/backtesting_results.csv`
- `outputs/backtesting_summary.csv`

### Step 12 – Profit and Loss Attribution Test (PLAT) Demonstration

Constructed illustrative Hypothetical P&L (HPL) and Risk-Theoretical P&L (RTPL) series.

The RTPL calculation included:
- Delta P&L
- An illustrative curvature component

Compared HPL and RTPL using daily P&L differences and correlation analysis.

The exercise demonstrates the purpose of P&L comparison but does not implement the formal regulatory PLAT methodology.

### Step 13 – Final Project Summary and Reporting

Consolidated the key results from the project into a final summary report.

The report provides an overview of the implemented risk areas, calculated measures and methodologies used.

**Output:** `outputs/final_ima_project_summary.csv`

## Technology Stack

| Technology | Application |
|---|---|
| Python | Risk calculation and analysis |
| Pandas | Data preparation and manipulation |
| NumPy | Numerical calculations and simulation |
| SciPy | Statistical analysis |
| Matplotlib | Data visualisation |
| yfinance | Historical market data collection |
| Jupyter Notebook | Project development and documentation |

## Project Structure

```text
FRTB IMA/
│
├── data/
│   ├── trade_book.csv
│   ├── market_prices.csv
│   ├── risk_factor_mapping.csv
│   └── stress_period_prices.csv
│
├── notebooks/
│   └── FRTB_IMA_Implementation.ipynb
│
├── outputs/
│   ├── rfet_screening_summary.csv
│   ├── liquidity_horizon_summary.csv
│   ├── stress_calibration_summary.csv
│   ├── nmrf_ssrm_summary.csv
│   ├── drc_simulation_summary.csv
│   ├── capital_components_summary.csv
│   ├── backtesting_summary.csv
│   ├── backtesting_results.csv
│   └── final_ima_project_summary.csv
│
└── README.md
```

## Important Methodological Limitations

This project is designed for educational purposes and to demonstrate the structure of an FRTB-IMA workflow.

The following limitations apply:

1. Historical market data uses Yahoo Finance instruments and proxies, not validated regulatory real-price observations.
2. RFET screening is illustrative and does not establish regulatory modellability.
3. Expected Shortfall and liquidity horizon calculations use simplified methodologies.
4. Options are included in the trading book but have not been fully repriced using an options valuation model.
5. NMRF classifications are assumed, and the SSRM calculation is a simplified proxy.
6. DRC uses an illustrative independent-default Monte Carlo simulation rather than the prescribed regulatory methodology.
7. Backtesting uses proxy portfolio losses rather than the prescribed regulatory P&L measures.
8. PLAT uses illustrative HPL and RTPL calculations and does not implement the formal regulatory statistical tests.
9. The project does not implement supervisory approval, model governance or the complete regulatory capital aggregation framework.

## Conclusion

This project provided practical exposure to the main concepts and analytical components of the FRTB Internal Models Approach.

It demonstrates how trade-book data, market risk factors, Expected Shortfall, liquidity horizons, stress scenarios, non-modellable risk factors, default risk and model assessment activities can be organised within a Python-based market-risk workflow.

The project is intended to strengthen understanding of FRTB-IMA concepts, Python-based financial risk analysis and the interaction between market-risk methodology and data processing.
