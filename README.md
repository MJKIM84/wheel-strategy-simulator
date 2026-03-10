# 🎯 Wheel Strategy Simulator

Interactive Monte Carlo simulator for SoFi Covered Call + Cash-Secured Put (Wheel) options strategy.

![License](https://img.shields.io/badge/license-MIT-blue)
![Deploy](https://img.shields.io/badge/deploy-GitHub%20Pages-green)

## Features

- **4-Strategy Comparison**: Wheel / Tax-Free / RE+Dividend / Buy & Hold
- **Monte Carlo Engine**: 5~100 runs with jump-diffusion price model
- **Interactive Dashboard**: Real-time parameter tuning with sliders
- **5 Views**: Portfolio Growth, Stock Price, Premium Income, Monte Carlo Distribution, Monthly Ledger

## Quick Start

```bash
# Clone
git clone https://github.com/YOUR_USERNAME/wheel-simulator.git
cd wheel-simulator

# Local dev
npx serve . -p 3000

# Or just open index.html in browser
```

## Deploy to GitHub Pages

```bash
# Option 1: GitHub Actions (automatic on push)
git push origin main

# Option 2: Manual
npm install
npm run deploy
```

## Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| Years | 5 | Simulation period |
| Capital | $1M | Initial investment |
| SoFi Target | $60 | 5-year price target |
| Tax Rate | 28.5% | Capital gains tax |
| Premium Offset | 0.70 | Premium realization factor |
| Vol Adjust | +30% | Extra volatility for SoFi |
| Cover Ratio | 100% | % of shares covered |
| RE Start | $700K | Real estate initial value |

## Tech

Single `index.html` — no build step required.

- React 18 + Babel standalone (CDN)
- Recharts 2.12 (CDN)
- JetBrains Mono font

## Disclaimer

For educational and simulation purposes only. Not financial advice.

## License

MIT
