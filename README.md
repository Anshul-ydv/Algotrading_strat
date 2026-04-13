# AlgoTrading Strategies

A collection of algorithmic trading strategies implemented in Python using daily and intraday data.

## Strategies Included

### 1. 52-Week High Breakout
- **Universe:** Nifty 50 stocks (Daily data)
- **Signal:** Price breaks above the 52-week high with SMA alignment (10 > 20 > 50 > 100).
- **Exit:** Trailing stop using 20-day SMA.

### 2. EMA Crossover (3-EMA)
- **Signal:** Fast EMA > Medium EMA > Slow EMA for Long; Reverse for Short.
- **Features:** Includes backtesting engine, performance metrics (Sharpe, Drawdown), and a parameter optimizer.

### 3. Breakout Probability
- **Method:** Calculates the statistical probability of a breakout occurring based on historical candle patterns (Green/Red) and price levels.

## Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Ensure you have the required data files (e.g., `nifty50_daily.csv`) in the root or specified directories.

## License
MIT
