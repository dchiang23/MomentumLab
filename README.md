# MomentumLab

MomentumLab is an in-progress quantitative research project for exploring, building, and evaluating momentum-based trading strategies using historical market data.

The goal of the project is to work through the full research process: acquiring and validating data, defining signals, constructing a backtest, evaluating performance, and testing whether a strategy remains robust across assets and market environments.

## Current Work

The repository currently contains the first stage of the project: market-data exploration and validation.

`notebooks/01_data_exploration.ipynb`:

- Downloads daily historical data for **SPY, QQQ, and IWM** using `yfinance`
- Works with data spanning **2010 through 2026**
- Examines dataframe structure, columns, dimensions, and date indexing
- Checks that observations are chronologically ordered and that the date index contains no duplicates
- Establishes the data pipeline that later strategy research and backtesting will build on

## Research Roadmap

Planned development includes:

- Calculate and analyze asset returns
- Construct momentum and trend-following signals
- Develop a reproducible backtesting framework
- Compare strategy performance against buy-and-hold benchmarks
- Evaluate return, volatility, drawdown, and risk-adjusted performance
- Incorporate transaction costs and realistic trading assumptions
- Test robustness across different ETFs, parameter choices, and market regimes
- Investigate sources of bias such as look-ahead bias and overfitting

## Tech Stack

- **Python**
- **pandas** for data manipulation
- **NumPy** for numerical analysis
- **Matplotlib** for visualization
- **yfinance** for historical market data
- **Jupyter Notebook** for exploratory research

## Repository Structure

```text
MomentumLab/
├── notebooks/
│   └── 01_data_exploration.ipynb
├── requirements.txt
└── README.md
```

## Running the Project

Clone the repository and install the Python dependencies:

```bash
git clone https://github.com/dchiang23/MomentumLab.git
cd MomentumLab
pip install -r requirements.txt
jupyter notebook
```

Then open `notebooks/01_data_exploration.ipynb`.

## Status

**In development.** The project currently focuses on data preparation and exploratory analysis. Strategy implementation, backtesting, and performance analysis are the next stages of development.

---

*This project is for research and educational purposes and is not investment advice.*
