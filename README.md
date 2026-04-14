# AlgoTrading Strategies

A collection of algorithmic trading strategies implemented in Python, ranging from simple equity breakouts to complex options trading systems.

## Project Structure

- `BASIC ONES/`: Core equity-based strategies (EMA Crossover, 52-Week High, etc.)
- `options/`: Advanced options trading strategies using index signals (BankNifty/Nifty).
- `requirements.txt`: Python dependencies required for the project.

## Strategies Included

### 1. Options Trading (BankNifty/Nifty)
Advanced strategies that map Index movements to Options (CE/PE) contracts.
- **Indicators:** Heikin Ashi candles and Supertrend.
- **Logic:** Generates signals on index price action and maps them to ATM/OTM options.
- **Features:** Automated strike selection, intraday/positional logic, and backtesting with option premium data.

### 2. 52-Week High Breakout
- **Universe:** Nifty 50 stocks (Daily data).
- **Signal:** Price breaks above the 52-week high with SMA alignment (10 > 20 > 50 > 100).
- **Exit:** Trailing stop using 20-day SMA.

### 3. EMA Crossover (3-EMA)
- **Signal:** Fast EMA > Medium EMA > Slow EMA for Long; Reverse for Short.
- **Features:** Includes backtesting engine, performance metrics (Sharpe, Drawdown), and a parameter optimizer.

### 4. Breakout Probability
- **Method:** Calculates the statistical probability of a breakout occurring based on historical candle patterns (Green/Red) and price levels.

## Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Configuration:
   - Ensure you have the required data files (CSV format) in the specified paths within the scripts.
   - For options strategies, ensure the options data directory is correctly mapped in the `path` variable.

## License
MIT
