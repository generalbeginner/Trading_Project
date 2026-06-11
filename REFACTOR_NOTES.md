# Pine Script v6 Refactor Notes

## Library

- `MPBGTradingLibrary.pine` contains reusable calculation functions for:
  - EMA/DEMA/TEMA/HMA/EHMA/zero-lag weak/SuperSmoother smoothing
  - MACD Platinum-style MACD
  - QQE lines and QMP signal logic, including RSI, Stochastic RSI, and Ehlers' RSIH variants
  - Bollinger Bands
  - manual RSI, stochastic, weighted green-red count
  - Ehlers Synthetic Oscillator helpers
  - small Fib/display helpers

Publish this library in TradingView first. The indicator scripts currently import:

```pine
import michaelpbgilbride/MPBGTradingLibrary/1 as mpbg
```

If TradingView uses a different username, library title, or version number after publication, update that line in each importing script.

## Composite Indicators

- `MQRSWSA Composite - Library.pine`: refactored version of `_originals/MQRSWSA [13-05-26].txt`.
- `Double QMP Filter Composite - Library.pine`: refactored overlay composite for Double QMP, moving averages, Bollinger Bands, Auto Fibonacci Retracement, and custom-source divergence.

The divergence section now focuses on MACD Platinum, QQE Advanced, RSI, Stochastic, Weighted Green-Red Count, plus an optional external source. Each has editable settings and a selector for the exact line/value used for divergence calculations. The RSI divergence source can use normal RSI, Stochastic RSI, or Ehlers' RSIH.

## Single-Purpose Indicators

- `QMP Filter.pine`
- `MACD Platinum.pine`
- `QQE Advanced.pine`
- `RSI plus Stochastic.pine`
- `Weighted Green-Red Count.pine`
- `ATR.pine`
- `Bollinger Bands.pine`
- `Moving Average Stack.pine`
- `Auto Fibonacci Retracement.pine`
- `Divergence for Many Indicators.pine`: standalone custom-source divergence using MACD Platinum, QQE Advanced, RSI, Stochastic, Weighted Green-Red Count, and optional external source.
