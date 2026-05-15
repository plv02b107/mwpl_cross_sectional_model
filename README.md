# MWPL-Based Cross-Sectional Stock Screening Model

## Overview

This project studies whether MWPL (Market Wide Position Limit),
Open Interest dynamics, and participant positioning contain
predictive information about future short-term stock returns.

The framework combines:

- MWPL squeeze behaviour
- Open Interest build-up and unwinding
- Ban-period dynamics
- Momentum and reversal effects
- Participant positioning as market-regime context

The objective is not to predict overall market direction,
but to rank stocks cross-sectionally based on their probability
of outperforming over the next 5 trading days.

---

# Research Hypothesis

Stocks experiencing:

- rising MWPL utilization
- increasing Open Interest
- squeeze-like positioning
- crowded derivatives exposure

may exhibit abnormal short-term return behaviour due to
positioning pressure and derivatives market dynamics.

---

# Important Market Structure Insight

Participant-wise Open Interest data published by NSE is
market-level rather than stock-specific.

Therefore:

- Participant positioning is treated as a market-regime signal
- Stock ranking is driven primarily using stock-level MWPL and OI features

This avoids introducing misleading stock-level information
from market-wide participant positioning data.

---

# Methodology

The research pipeline includes:

1. Data cleaning and consolidation
2. Participant-wise OI aggregation
3. Stock-level MWPL and OI feature engineering
4. Market-regime construction
5. Cross-sectional ranking framework
6. Purged walk-forward validation
7. Ensemble machine learning models
8. Out-of-sample backtesting

---

# Features Used

## Stock-Level Features

- MWPL velocity and acceleration
- Ban-entry and ban-exit dynamics
- Open Interest momentum
- Squeeze score
- Momentum reversal features
- Volatility and price-change features
- Cross-sectional ranking variables

## Market-Regime Features

- FII/DII/client futures positioning
- Institutional flow indicators
- Retail vs FII divergence
- Market breadth and volatility regime

---

# Models Used

- Random Forest
- Extra Trees
- Gradient Boosting

Predictions are combined using an ensemble framework.

---

# Validation Framework

To reduce look-ahead bias and leakage:

- Walk-forward validation is used
- Embargo periods are applied
- Models are evaluated fully out-of-sample

Performance metrics include:

- Out-of-sample AUC
- Cross-sectional excess return
- Long-short spread
- Sharpe ratio
- Hit rate

---

# Dataset

The dataset consists of:

- NSE MWPL data
- Stock-level OI and price features
- Participant-wise derivatives positioning data

covering approximately 67 trading days across the NSE F&O universe.

---

# Key Findings

The results suggest:

- MWPL and OI features contain weak but unstable predictive information
- Participant-wise OI data is more useful as a market-regime indicator rather than a stock-selection signal
- Squeeze-related features appear more informative than raw MWPL levels alone

The out-of-sample walk-forward validation produced:

- Mean OOF AUC ≈ 0.50
- Weak and inconsistent predictive performance across folds

This indicates that the current signal is close to noise,
and the available sample size is insufficient to establish
stable predictive power.

---

# Limitations

Main limitations of the study include:

- Limited historical sample (~67 trading days)
- No options-chain features
- No stock-level participant positioning
- Lack of funding/basis variables
- Limited ban-period observations

Financial market signals are highly noisy and generally
require much longer historical samples for stable estimation.

---

# Future Improvements

Potential extensions include:

- Expanding MWPL history to multiple years
- Adding options-chain metrics (PCR, IV percentile, max pain)
- Adding delivery percentage and short-selling data
- Incorporating futures basis and funding proxies
- Testing sector-relative and event-driven signals

---

# Final Takeaway

Although the current results do not demonstrate strong
predictive power, the project establishes a structured
research framework for studying MWPL-driven positioning effects
using leakage-aware validation and market microstructure-based
feature engineering.

The notebook is intended as a research and screening framework
rather than a deployable production trading strategy.
