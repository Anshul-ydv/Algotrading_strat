# AlgoTrading Strategies

A collection of algorithmic trading strategies implemented in Python, ranging from simple equity breakouts to complex options trading systems.

## Project Structure

- `BASIC ONES/`: Core equity-based strategies (EMA Crossover, 52-Week High, etc.)
- `options/`: Advanced options trading strategies using index signals (BankNifty/Nifty).
- `zigzagstrat/`: Advanced ZigZag pivot-based breakout strategies (Non-repainting).
- `requirements.txt`: Python dependencies required for the project.

## Strategies Included

### 1. Options Trading (BankNifty/Nifty)
Advanced strategies that map Index movements to Options (CE/PE) contracts.
- **Indicators:** Heikin Ashi candles and Supertrend.
- **Logic:** Generates signals on index price action and maps them to ATM/OTM options.
- **Features:** Automated strike selection, intraday/positional logic, and backtesting with option premium data.

### 2. ZigZag Breakout (Non-Repainting)
- **Method:** Advanced pivot detection using dynamic price deviation $D_t = \max(\alpha \times \text{ATR}, \beta \times \text{Median Abs Return})$.
- **Signal:** 
  - Identifies price action patterns: Higher Highs (HH), Higher Lows (HL), Lower Highs (LH), and Lower Lows (LL).
  - Long on breakout of confirmed HIGH pivots or HL patterns.
  - Exit on cross-down (LH) or trailing stop.
- **Features:** 
  - **Heikin-Ashi Integration:** Supports trend filtering using Heikin-Ashi candles.
  - **Parameter Optimizer:** Built-in optimizer for depth, deviation, and backstep parameters.
  - **Performance Analytics:** Comprehensive metrics using `quantstats` (Sharpe, Sortino, Probabilistic Sharpe, Max Drawdown).
  - **Robust Backtesting:** Next-bar execution logic to prevent look-ahead bias.

### 3. 52-Week High Breakout
- **Universe:** Nifty 50 stocks (Daily data).
- **Signal:** Price breaks above the 52-week high with SMA alignment (10 > 20 > 50 > 100).
- **Exit:** Trailing stop using 20-day SMA.

### 4. EMA Crossover (3-EMA)
- **Signal:** Fast EMA > Medium EMA > Slow EMA for Long; Reverse for Short.
- **Features:** Includes backtesting engine, performance metrics (Sharpe, Drawdown), and a parameter optimizer.

### 5. Breakout Probability
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
