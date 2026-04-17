# ALGO Trading Strategy 
This repository contains multiple Python backtesting scripts for index, options, and ZigZag-based strategies. Most scripts are standalone experiments and use hardcoded CSV input paths.

## Repository Layout

- 60minconcept/: 60-minute options and signal models
- BASIC ONES/: basic equity strategy utilities
- options/: options mapping strategies driven by index signals
- zigzagstrat/: ZigZag pivot labeling and backtesting
- requirements.txt: base dependencies used by some scripts

## Important Notes Before Running

1. Most scripts use hardcoded local Windows paths such as D:/AlgoTrade/... or D:/Sushant/....
2. Update input paths in each script before execution.
3. Several scripts expect specific CSV schema, usually Date/Open/High/Low/Close (+ optional Volume/Unnamed: 0).
4. Some scripts depend on modules that are not listed in requirements.txt:
   - pandas_ta
   - TA-Lib (talib)
   - quantstats
   - Multi_Kernel_Regression (local module imported by 60min_MKR.py)

## File-by-File Overview

### 60minconcept

- 60min_MKR.py
  - Multi-kernel regression signal strategy with optimization across kernels and bandwidths.
  - Uses next-candle open execution to reduce look-ahead bias.
  - Exports best-run signals and trades to CSV.

- 60Mins_Range_Strangle_BnF.py
  - BankNifty 60-minute range-based short strangle backtest.
  - Entry around 10:15, exit around 14:45, with stop loss and MTM checks.
  - Uses India VIX filter and writes BNF_trading_data.csv.

- 60Mins_Range_Strangle_BnF_EQ.py
  - Variant of BnF strangle that rebalances CE/PE strike distance to make the structure more symmetric.
  - Uses VIX filter and writes BNF_trading_data_EQ_2023_2024.csv.

- 60Mins_Range_Strangle_NFT.py
  - Nifty 60-minute range-based short strangle version.
  - Uses Nifty options files and writes NFT_trading_data.csv.

- 60Mins_Range_IronCondor_BnF.py
  - BankNifty iron condor variant (short strikes from range and hedge wings).
  - Includes stop-loss logic and writes BNF_trading_data_IronCondor.csv.

- 60Mins_Range_IronCondor_BnF_NoSL.py
  - Iron condor variant with stop-loss disabled/modified behavior.
  - Writes BNF_trading_data_IronCondor_NoSL.csv.

- 60Mins_RSI_Optimize.py
  - Grid-search optimizer for RSI period and RSI threshold on BankNifty 60-minute data.
  - Prints best period/band and trade action sequence.

### BASIC ONES

- 52-Week_High_Breakout.py
  - Daily breakout scan for new 52-week highs with SMA alignment (10/20/50/100).
  - Exits on SMA20 breakdown and outputs trade rows.

- EMA-Crossover.py
  - 3-EMA trend-order strategy (long when fast > medium > slow, short for inverse order).
  - Includes backtest, metrics, and parameter optimization helpers.

- Breakout_Probability.py
  - Utility functions to estimate up/down breakout probabilities from historical candle behavior.
  - Provides both historical and incremental probability calculation functions.

### options

- 6_2_Options.py
  - 15-minute BankNifty index-to-options mapping strategy.
  - Builds Heikin-Ashi candles, computes Supertrend, generates Buy/Sell state, and maps to CE/PE option prices.
  - Supports CSV export for signals and trade log.

- 6_2_Options_Positional.py
  - Positional version of the Supertrend + option mapping logic.
  - Handles expiry edge cases and trade holding period stats.

- 6_2_Options_Intraday.py
  - Intraday variant for 1-minute BankNifty data.
  - Imports external Strategies module and includes similar option mapping/trade bookkeeping.
  - Some CSV export lines are currently commented.

### zigzagstrat

- ZigZag_Strategy.py
  - Non-repainting ZigZag pivot detection using adaptive threshold:
    D_t = max(alpha * ATR_t, beta * median_abs_return_t)
  - Generates breakout/exit signals from confirmed pivots and runs a next-bar execution backtest with ATR-based stop.

- ZigZag_Strategy_Buy.py
  - ZigZag + HH/HL/LH/LL labeling based long strategy backtester.
  - Supports normal and Heikin-Ashi candles and parameter grid optimization.
  - Exports all_optimization_results.csv and best_strategy_signals.csv.

- zigzag_labeler.py
  - CLI script to detect pivots and label them as HH/HL/LL/LH.
  - Optional Heikin-Ashi mode and CSV output with per-label columns.

## Dependencies

Current requirements.txt contains:

- pandas
- numpy
- matplotlib
- scipy

For full repository coverage, install additional packages used by scripts when needed:

```bash
pip install pandas_ta quantstats TA-Lib
```

If TA-Lib installation fails on your system, install the platform-specific TA-Lib binaries/libraries first.

## Typical Run Pattern

1. Open target script.
2. Update local CSV paths (spot_path/options_path/vix_path or csv_file_path).
3. Confirm expected input column names.
4. Run script:

```bash
python path/to/script.py
```

## License

MIT (see LICENSE)
