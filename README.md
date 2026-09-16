# MomentumLab

MomentumLab is an in-progress quantitative research project for building and evaluating a cross-sectional momentum strategy using historical ETF data.

The goal is to work through the research process carefully: acquire and validate market data, construct return and momentum signals, build a backtest with explicit timing, evaluate performance, test robustness, and document research limitations such as look-ahead bias, transaction costs, survivorship bias, and overfitting.

## Current Work

### 01 — Market Data Exploration

`notebooks/01_data_exploration.ipynb`

- Downloads historical market data with `yfinance`
- Inspects DataFrame structure, dates, columns, dimensions, duplicates, and missing values
- Works with adjusted closing prices for research calculations
- Establishes the data-validation workflow used in later notebooks

### 02 — Returns

`notebooks/02_returns_and_signals.ipynb`

- Calculates daily returns manually from adjusted prices
- Computes basic return statistics including mean, sample standard deviation, minimum, maximum, and valid observations
- Builds compounded growth-of-$1 calculations
- Reinforces the difference between adding returns and compounding returns

### 03 — Momentum Signal

`notebooks/03_momentum_signal.ipynb`

Current work implements the 12-1 momentum signal

```text
Momentum_i(t) = P_i(t - 21) / P_i(t - 252) - 1
```

where 21 and 252 are trading-day offsets.

The notebook currently:

- Downloads the ETF research universe over the fixed 2010-01-01 to 2026-08-31 sample
- Uses `Adj Close` with `auto_adjust=False`
- Anchors the required checkpoint at 2020-12-31
- Converts the formation date to its trading-row position
- Calculates momentum scores vectorially across the ETF columns
- Sorts scores from highest to lowest
- Selects the top six ETFs
- Visualizes the top-six momentum scores with a bar chart
- Documents the intuition behind the 12-1 signal and cross-sectional ranking

Assignment 3 is still being finalized and validated before moving to the backtest.

## Research Roadmap

1. Market data exploration and validation
2. Daily returns and compounded growth
3. Cross-sectional 12-1 momentum signal
4. Monthly backtest with next-trading-day execution
5. Performance metrics and SPY benchmark comparison
6. One-at-a-time robustness tests
7. Frozen out-of-sample evaluation
8. Research-bias documentation
9. Refactor reusable code into `src/`
10. Final research report and repository cleanup

## Tech Stack

- **Python**
- **pandas** for time-series and tabular data
- **NumPy** for numerical operations
- **Matplotlib** for visualization
- **yfinance** for historical market data
- **Jupyter Notebook** for research and diagnostics
- **Git / GitHub** for version control and reproducibility

## Repository Structure

```text
MomentumLab/
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_returns_and_signals.ipynb
│   └── 03_momentum_signal.ipynb
├── requirements.txt
├── .gitignore
└── README.md
```

## Running the Project

Clone the repository and install the Python dependencies:

```bash
git clone https://github.com/dchiang23/MomentumLab.git
cd MomentumLab
pip install -r requirements.txt
jupyter lab
```

Then open the notebook corresponding to the stage of the research you want to inspect.

## Status

**In development — currently on Assignment 3: Momentum Signal.** Backtesting has not started yet.

---

*This project is for research and educational purposes and is not investment advice.*
