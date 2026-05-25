# FUCK YO TRADE
### Quant Terminal v3.3 — Mobile-First Paper Trading & AI Analysis

> **Not financial advice. Educational and entertainment purposes only. Never trade money you cannot afford to lose.**

[![Live App](https://img.shields.io/badge/LIVE%20APP-gitbuell.github.io%2FaiStockMan-00d4a0?style=for-the-badge)](https://gitbuell.github.io/aiStockMan/)
[![PWA](https://img.shields.io/badge/PWA-Installable-a78bfa?style=for-the-badge)](#install)
[![License](https://img.shields.io/badge/License-MIT-f5a623?style=for-the-badge)](LICENSE)

---

## What It Does

FUCK YO TRADE is a fully client-side quant trading terminal that runs entirely in the browser — no backend, no API keys, no subscriptions. Install it on your phone like a native app.

### Features

- **Live Ticker Tape** — scrolling prices for 18+ stocks and crypto with real-time jitter
- **3-Phase Analysis Pipeline** — Research → Execute → Journal (based on institutional quant workflow)
- **Fibonacci Retracement + Extensions** — 23.6%, 38.2%, 50%, 61.8%, 78.6% levels with 127.2% and 161.8% extension targets
- **Full Technical Suite** — EMA 20/50, RSI(14), MACD(12,26,9), Volume signal with 1.5x rule
- **Billionaire Cycle Lens** — Wyckoff market phases, psychological sentiment cycle, crypto halving cycle, presidential macro cycle
- **Paper Trading** — $100,000 simulated portfolio, full order execution, position management, P&L tracking
- **Risk Engine** — hardcoded 5% max position rule, 2% stop-loss, automatic order scaling
- **Compliance Journal** — every analysis and trade logged with full quantitative + qualitative reasoning
- **PWA Installable** — works offline, installs on iOS and Android home screen

---

## Supported Assets

### Stocks
`AAPL` `TSLA` `NVDA` `MSFT` `AMZN` `GOOGL` `META` `SPY`

### Crypto
`BTC` `ETH` `XRP` `XLM` `SOL` `BNB` `DOGE` `ADA` `AVAX` `LINK` `DOT` `LTC`

---

## Install

### Mobile — iPhone (iOS)

1. Open **Safari** and go to `https://gitbuell.github.io/aiStockMan/`
2. Tap the **Share** button (box with arrow pointing up)
3. Scroll down → tap **Add to Home Screen**
4. Tap **Add** — the FYT icon appears on your home screen
5. Launch from home screen — runs full screen, no browser UI

> iOS requires Safari. Chrome/Firefox on iOS cannot install PWAs.

### Mobile — Android

1. Open **Chrome** and go to `https://gitbuell.github.io/aiStockMan/`
2. Tap the **Install** banner at the bottom of the screen
3. Or tap the 3-dot menu → **Add to Home Screen**
4. Tap **Install** in the confirmation dialog

### Desktop — Chrome / Edge

1. Go to `https://gitbuell.github.io/aiStockMan/`
2. Click the **install icon (⊕)** in the address bar
3. Click **Install** — opens in its own window like a native app

---

## Run Locally

### Python (zero install on Mac/Linux)
```bash
git clone https://github.com/gitbuell/aiStockMan.git
cd aiStockMan
python3 -m http.server 8080
# Open http://localhost:8080
```

### Node.js
```bash
npm install -g serve
cd aiStockMan
serve -l 8080
# Open http://localhost:8080
```

### Nginx
Copy `index.html` to your Nginx web root and start Nginx. Default serves at `http://localhost`.

---

## Architecture

The entire analysis engine runs locally in JavaScript — no external API calls during analysis.

```
Analysis Pipeline
├── Phase 1: Research Script
│   ├── genBars()      — synthetic 60-bar OHLCV series
│   ├── ema()          — true exponential moving average (EMA 20, EMA 50)
│   ├── rsi()          — RSI(14) with proper gain/loss averaging
│   ├── macd()         — MACD(12,26,9) with signal line and histogram
│   ├── fib()          — Fibonacci retracement + 127.2%/161.8% extensions
│   └── billCycles()   — Wyckoff phase, psych cycle, halving/presidential cycle
│
├── Phase 2: Execution Script
│   ├── Direction scoring (EMA cross, RSI, MACD, volume, Fib, cycle)
│   ├── Risk rules (5% equity cap, 2% stop-loss, 1.5x volume gate)
│   ├── Position sizing
│   └── Signal generation (BUY / SELL / HOLD)
│
└── Phase 3: Journal Script
    ├── EMA narrative
    ├── RSI narrative
    ├── Fibonacci narrative
    ├── Volume narrative
    ├── Billionaire cycle narrative
    └── Compliance decision log
```

### Billionaire Cycle Engine

Inspired by how institutional players approach markets at scale:

| Layer | What It Analyzes |
|---|---|
| **Wyckoff Phase** | Where price sits in the accumulation → markup → distribution → markdown cycle |
| **Psychological Cycle** | RSI-mapped sentiment: Euphoria → Optimism → Hope → Anxiety → Capitulation |
| **Crypto Halving Cycle** | 4-year Bitcoin halving cycle position (pre-halving, halving year, bull peak, bear, late bear) |
| **Presidential Macro Cycle** | 4-year US election cycle effects on equity markets |

---

## Risk Rules (Hardcoded — Never Removed)

- **Max position size**: 5% of total equity per trade (auto-scales oversized orders)
- **Stop-loss**: 2% below execution price on every order
- **Volume gate**: BUY signals suppressed if volume is below 1.5x 20-day average
- **Paper first**: System designed for paper trading — always validate weeks of results before any live deployment

---

## File Structure

```
aiStockMan/
├── index.html        # Complete app — single file, zero dependencies
├── manifest.json     # PWA manifest — icons, display mode, theme
├── README.md         # This file
└── LICENSE           # MIT
```

---

## Roadmap

- [ ] Connect Alpaca MCP for live stock data and paper order execution
- [ ] Connect CoinGecko MCP for real-time crypto prices
- [ ] Persistent portfolio storage across sessions (IndexedDB)
- [ ] Export journal as Markdown / CSV
- [ ] Watchlist with alerts
- [ ] Backtesting mode against historical price series
- [ ] Additional cycle indicators: Gann, Elliott Wave, lunar cycle (experimental)

---

## Disclaimer

**FUCK YO TRADE does not provide investment advice.** All signals are simulated using synthetic price data. Paper trading uses fake money. Past performance does not predict future results. Billionaire cycle analysis is observational and historical — not predictive. Always consult a licensed financial advisor before making any real investment decisions. Trading involves substantial risk of loss. Never invest money you cannot afford to lose completely.

---

## License

MIT — use it, fork it, build on it.

---

*Built with the 3-phase quant pipeline methodology. Always paper trade first.*
