# CANSLIM-signal-booster
Quantitative Framework for CANSLIM Stock Selection
# CANSLIM Signal Booster

A lightweight toolkit that **boosts / validates CANSLIM-style breakout signals** with a small set of objective filters (trend, volume, relative strength, market regime) so you can reduce false positives and focus on the few setups that actually matter.

> Not financial advice. Educational / research project.

## What it does

* **Signal detection:** flags common breakout + continuation patterns (clean pivots, breakouts, high-tight flags, etc.)
* **Signal boosting:** applies confirming filters (trend quality, RS strength, volume signature, volatility/ATR sanity checks)
* **Market context:** optional “risk-on/risk-off” gating so you only take new entries when conditions are favorable
* **Outputs:** watchlist-ready CSV/JSON and a simple summary report you can run on a schedule (cron-friendly)

## Why it exists

Most CANSLIM scans are noisy. This project is designed to:

* keep the scan wide,
* then **tighten the decision** with consistent, explainable filters,
* and surface only the best candidates.

## Core modules (conceptual)

* `data/` – price/volume ingestion & normalization
* `signals/` – pattern detection (breakout/pivot logic)
* `boosters/` – confirmation filters (RS, volume, trend, volatility)
* `regime/` – market gating rules (optional)
* `export/` – CSV/JSON + report generation
* `jobs/` – scheduled runs / cron entrypoints

## Quick start

```bash
# 1) Install dependencies
pip install -r requirements.txt

# 2) Run the scanner (example)
python run.py --universe "watchlist.csv" --timeframe "daily" --export "out/"
```

## Example output

* `out/candidates.csv` – ranked candidates with factor columns + final score
* `out/report.md` – human-readable summary
* `out/candidates.json` – structured output for dashboards/alerts

## Configuration

Everything is configurable via a single config file:

* booster thresholds (RS, volume, MA distance, ATR bounds)
* ranking weights
* market-regime gating on/off
* universe definition (tickers, sectors, custom lists)

## Roadmap

* [ ] Add TradingView/Pine companion indicator (visual confirmation overlay)
* [ ] Add earnings-calendar proximity filter
* [ ] Add sector/industry relative strength ranking
* [ ] Add alerting (email/Slack/Telegram)
* [ ] Add backtest harness (optional, strictly for research)

## Contributing

PRs welcome:

1. Fork
2. Create a feature branch
3. Add tests if applicable
4. Open a PR with a clear description + sample output

## License

MIT (or choose your preferred license)
