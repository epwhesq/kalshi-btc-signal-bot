# BTC Signal · Kalshi 15m · V2 (paper mode)

A free, read-only iPhone-friendly dashboard for the Kalshi KXBTC15M market. This version adds more conservative directional filters and a fee/break-even display. It does **not** claim to have a profitable or calibrated prediction model.

## Data sources
- Kalshi market snapshot: DegenHedge public `/api/btc-window` endpoint (third-party provider; not affiliated with Kalshi).
- BTC spot and 1-minute candles: Coinbase Exchange public BTC-USD endpoints. Coinbase is a proxy, not the settlement benchmark.
- Kalshi says most crypto markets settle on CF Benchmarks indices; its 15-minute markets compare the opening-minute average with the closing-minute average. The specific market rules control. See https://help.kalshi.com/en/articles/13823838-crypto-markets

## V2 directional filters
- Requires 12 completed one-minute candles and a continuous recent 10-minute candle sequence.
- Calculates 1m, 3m, 5m and 10m momentum, 3m acceleration, and recent one-minute return volatility.
- Requires target gap and multi-horizon momentum to agree.
- Rejects unusually high volatility, wide spreads, expensive asks, missing/stale market data, and the final two minutes.
- Directional outputs are labelled `PAPER UP SETUP` / `PAPER DOWN SETUP`; they are not real-money recommendations.

## Fee and break-even display
For one contract, the displayed estimate applies the standard Kalshi taker-fee formula `round up to cent(0.07 × C × P × (1-P))`, with C=1 and P=ask price in dollars. The displayed break-even percentage is ask cents plus the estimated fee cents, divided by the $1 payout. Actual fees can vary by market, fee schedule, order type and rounding. Check https://kalshi.com/fee-schedule before trading.

The dashboard deliberately shows `NOT CALIBRATED` for win probability and withholds expected value. A technical score is not a probability. Do not trade real money based on this version. We need a properly graded paper-trade sample and out-of-sample testing before estimating probabilities or claiming positive expectancy.

## Publish update to your existing GitHub Pages site
1. Download the V2 ZIP and extract it in iPhone Files.
2. Open your existing GitHub repository in Safari.
3. Choose **Add file → Upload files**.
4. Upload all six files from this folder to the repository root, replacing the existing files when prompted: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`, and `README.md`.
5. Tap **Commit changes** on the `main` branch. GitHub Pages will redeploy automatically.
6. Open the site in Safari and refresh. If the old version remains, close the tab, reopen the site, and refresh again; the service-worker cache version was incremented.

## Limitations
- This static site only refreshes while open. It does not run 24/7 in the background.
- It does not connect to your Kalshi account or place orders.
- Coinbase is not CF Benchmarks BRTI. A close proxy value can differ from settlement.
- No strategy can guarantee profits.
