# 📝 Crypto HFT Bot

High-frequency spot trading bot for Binance. Micro-trades exploiting short-term price movements and exchange inefficiencies.

## Summary

| Aspect | Decision |
|--------|----------|
| Exchange | Binance |
| Market | Spot (no leverage) |
| Capital | $100-200 USD |
| Pairs | Auto-selected by volume/volatility |
| Frequency | Target 500+ trades/week |
| Timeframe | 15-minute candles |
| Tech | Pure code, no LLM |

## Architecture

```
┌─────────────────────────────────────────────────┐
│                  CRYPTO HFT BOT                 │
├─────────────────────────────────────────────────┤
│                                                 │
│  ┌─────────────┐    ┌─────────────────────┐    │
│  │  Binance    │───▶│  Market Data Stream │    │
│  │  WebSocket  │    │  (prices, orderbook)│    │
│  └─────────────┘    └──────────┬──────────┘    │
│                                │               │
│                                ▼               │
│                     ┌─────────────────────┐    │
│                     │   Pair Selector     │    │
│                     │  (volume, volatility│    │
│                     │   spread analysis)  │    │
│                     └──────────┬──────────┘    │
│                                │               │
│                                ▼               │
│                     ┌─────────────────────┐    │
│                     │  Signal Generator   │    │
│                     │  (15m candles, RSI, │    │
│                     │   momentum, spread) │    │
│                     └──────────┬──────────┘    │
│                                │               │
│                                ▼               │
│  ┌─────────────┐    ┌─────────────────────┐    │
│  │  Binance    │◀───│   Order Executor    │    │
│  │  REST API   │    │  (position sizing,  │    │
│  └─────────────┘    │   risk management)  │    │
│                     └──────────┬──────────┘    │
│                                │               │
│                                ▼               │
│                     ┌─────────────────────┐    │
│                     │   Trade Logger      │    │
│                     │  (SQLite + metrics) │    │
│                     └─────────────────────┘    │
│                                                 │
└─────────────────────────────────────────────────┘
```

## Strategy

### Pair Selection (automatic)
```python
# Select pairs where:
volume_24h > $10M USD
volatility_15m between 0.1% and 2%
spread < 0.05%
```

### Entry Signals
- Price momentum on 15m candles
- RSI oversold/overbought reversals
- Spread compression opportunities
- Volume spikes

### Exit Rules
- Take profit: +0.3% to +0.5%
- Stop loss: -0.5%
- Time-based exit: 4 hours max hold

### Risk Management
- Max 10% of portfolio per trade
- Max 3 concurrent positions
- Daily loss limit: 5% of portfolio
- Keep BNB for fee discounts

## Tech Stack

- **Language:** Python 3.11+
- **Exchange SDK:** `python-binance`
- **Data:** WebSocket for real-time, REST for orders
- **Storage:** SQLite for trade log
- **Scheduling:** asyncio event loop
- **Deployment:** VPS (can use existing $6 droplet)

## File Structure

```
crypto-hft-bot/
├── src/
│   ├── main.py           # Entry point
│   ├── config.py         # Settings & API keys
│   ├── binance_client.py # Exchange wrapper
│   ├── market_data.py    # WebSocket handler
│   ├── pair_selector.py  # Pair filtering logic
│   ├── signals.py        # Entry/exit signals
│   ├── executor.py       # Order execution
│   ├── risk.py           # Position sizing & limits
│   └── logger.py         # Trade logging
├── tests/
├── data/
│   └── trades.db         # SQLite trade history
├── .env                  # API keys (gitignored)
├── requirements.txt
└── README.md
```

## Milestones

### M1 — Foundation
- [ ] Project setup, Binance API connection
- [ ] WebSocket price stream working
- [ ] Basic order execution (buy/sell)

### M2 — Core Logic  
- [ ] Pair selector implementation
- [ ] Signal generator (15m candles + indicators)
- [ ] Position sizing & risk limits

### M3 — Paper Trading
- [ ] Simulated trading mode
- [ ] Trade logging & metrics
- [ ] Run for 1 week, analyze results

### M4 — Live Trading
- [ ] Deploy to VPS
- [ ] Start with minimal capital ($50)
- [ ] Monitor & adjust parameters

### M5 — Optimization
- [ ] Backtest framework with historical data
- [ ] Parameter tuning (thresholds, timeframes, indicators)
- [ ] A/B test different strategies
- [ ] Scale up capital if profitable

### M6 — Deploy to Fly.io
- [ ] Dockerfile + fly.toml config
- [ ] Secrets management (API keys)
- [ ] Health checks & auto-restart
- [ ] Logging to Fly.io dashboard
- [ ] Optional: metrics endpoint

## Next Steps

1. Create repo `crypto-hft-bot`
2. Set up Binance API keys (read + trade permissions)
3. Start M1 implementation

---
*Created: 2026-02-03*
*Status: Ready to build*
