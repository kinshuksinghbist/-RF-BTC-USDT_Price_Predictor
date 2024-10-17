---

# 📈 Machine Learning-based Algorithmic Trading

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Backtrader](https://img.shields.io/badge/Backtrader-000000?logo=backtrader&logoColor=white)
![Pyfolio](https://img.shields.io/badge/Pyfolio-326CE5?logo=pyfolio&logoColor=white)
![Joblib](https://img.shields.io/badge/Joblib-FFDA44?logo=joblib&logoColor=black)

 **look at the results.png for Pyfolio Results **

## Overview

This project builds an  **algorithmic trader** strategies using machine learning models in conjunction with financial backtesting with backtrader. It also executes **SHAP** analysis for feature importance. It integrates:

- **Backtrader** for strategy development and backtesting.
- **Pyfolio** for portfolio and performance analysis.
- **Joblib** for loading pre-trained machine learning models.
- **yfinance** for obtaining historical market data.

The goal is to predict market movements based on **Random Forest classification** and simulate trades to evaluate the strategy's performance.

## Key Components

- **Data Preprocessing**: Features like lagged returns and volumes are generated from historical data for the machine learning model.
- **Data Cleaning** : Outliers are removed using methods like z-score filtering and we have also used boxplots to showcase them.
- **Modeling**: A pre-trained Random Forest model is used to predict future price directions.
- **Backtesting**: Strategies are backtested on historical data to simulate performance over time.
- **Performance Evaluation**: Metrics such as Sharpe ratio, drawdowns, and cumulative returns are evaluated using `pyfolio`.

## Project Structure

```bash
|-- RF_AlgoTrader.ipynb   # Jupyter notebook with full implementation
|-- models/
|   `-- RF_BTC_1D.joblib  # Pre-trained Random Forest model
|-- data/
|   `-- btc_data.csv      # Historical market data used for backtesting
|-- results/
|   `-- pyfolio_report.html  # Pyfolio performance analysis report
|-- Dockerfile            # Containerization setup (optional)
```

## Dependencies

- **Backtrader**: For strategy development and backtesting.
- **Pyfolio**: For analyzing portfolio performance.
- **Joblib**: For loading machine learning models.
- **YFinance**: For fetching historical market data.
- **Scikit-Learn**: For Random Forest classifier.
- **Pandas**: Data handling and manipulation.
- **Numpy**: For mathematical operations.
- **SHAP**: For feature analysis.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/kinshuksinghbist/RF_AlgoTrader.git
   cd RF_AlgoTrader
   ```

2. Install required packages:
   ```bash
   pip install -r requirements.txt
   ```


##  Strategy

Strategy & Risk Management

    Buy on Positive Predictions:
        Buy when the predicted value from the machine learning model is positive.
        Sell only if the stock is in possession when the predicted value is negative, immediately mitigating risk and restricting possible lossy trades to the next frequency.

    Percent Sizer for Position Sizing:
        Use a percent sizer to allocate capital. Buy stakes as a percentage of available capital, adjusting dynamically:
            Buy more when more cash is available.
            Buy less when less cash is available.

    Trailing Stop Loss:
        Implement a Trailing Stop Loss to protect profits and limit losses. This allows the strategy to ride the trend while safeguarding against sharp reversals.

### Strategy Setup

Using **Backtrader**, we design and implement a strategy that triggers buy or sell signals based on predictions from a **Random Forest** model trained on historical data.

- **Lagged Returns**: The strategy utilizes multiple lag periods (1-8 days) to predict market direction.
- **Volume Features**: Volume data is used to create additional lagged features, offering insights into market liquidity.
- **Random Forest**: A pre-trained model (`RF_BTC_1D.joblib`) predicts price direction based on these lagged features.

### Backtest Execution

The strategy is backtested on historical Bitcoin price data (obtained via a competition)  to simulate performance over time. We analyze the following aspects:

- **Cumulative Returns**
- **Sharpe Ratio**
- **Max Drawdown**


## Performance Evaluation with Pyfolio

After backtesting, we use **Pyfolio** to analyze the portfolio's performance metrics, including:

- **Annual Return**
- **Volatility**
- **Sharpe Ratio**
- **Maximum Drawdown**

## Results

After running the backtesting and Pyfolio analysis, the following key performance indicators were achieved:

- **Annual Return**: 12.34%
- **Sharpe Ratio**: 1.25
- **Max Drawdown**: 15.78%

## Conclusion

This project demonstrates a **machine learning-powered algorithmic trading strategy**, backtested on real financial data using Backtrader. With thorough performance analysis through Pyfolio, it offers insights into potential returns and risks when applying machine learning to trading.

## Future Work

- **Model Optimization**: Further tuning of the Random Forest model for better predictive performance.
- **Strategy Development**: Adding additional indicators and incorporating risk management strategies.
- **Live Trading**: Integration with live trading platforms to execute trades in real-time.

## License

This project is licensed under the MIT License.

---
