# 🌱 Crypto HFT Bot

## What?
Headless high-frequency trading bot for crypto. Micro-trades on 15-minute timeframes, exploiting exchange inefficiencies for compounding small gains.

## Why does it interest me?
- Automation over emotion — no FOMO, no panic selling
- Compounding small edges at scale (500+ trades/week)
- Passive income potential once dialed in
- Technical challenge: low latency, market microstructure, risk management

## How it works

### Strategy
- **Timeframe:** 15-minute price direction on major coins
- **Edge:** Exchange inefficiencies — tiny price gaps or delays between/within CEXs
- **Frequency:** 500+ trades per week
- **Target:** Very small profit per trade, compounding over time

### Core principles
1. High frequency
2. Small edges
3. Strong compounding
4. Automation over emotion

## Decisions
- **Exchange:** Binance ✅
- **Market:** Spot (sin apalancamiento) ✅
- **Capital inicial:** $100-200 USD (usa todo el balance disponible) ✅

## Open questions
- Initial capital allocation?
- Risk management: max drawdown, position sizing?
- What signals/indicators? Pure price action? Order book? Funding rates?
- Backtesting infrastructure needed?
- VPS location for latency optimization?

## Notes
- Need API access with low fees (maker rebates ideal)
- Consider starting paper trading before live
- Regulatory considerations depending on jurisdiction

---
*Created: 2026-02-03*
