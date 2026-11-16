# BTC Signal · Kalshi 15m

A free, read-only iPhone-friendly dashboard that checks the current Kalshi KXBTC15M window and independent BTC market data, then displays BUY UP, BUY DOWN, or NO TRADE.

## What it uses
- **Kalshi market snapshot:** DegenHedge's public `/api/btc-window` endpoint. Its docs say the market fields (ticker, strike, bid/ask, and close time) are read from Kalshi's public API. DegenHedge is independent and not affiliated with Kalshi.
- **BTC spot and 1-minute candles:** Coinbase Exchange public BTC-USD REST market-data endpoints. No API key or Kalshi login is required.
- **No order placement:** the app does not connect to a Kalshi account or submit trades.

## Signal rules
The dashboard uses the Coinbase spot-vs-Kalshi-target gap plus completed 3-minute and 5-minute candle momentum. It requires those inputs to align, requires a live market quote, skips stale/missing data, skips the final two minutes of the window, skips an ask at or above 80 cents, and skips a bid/ask spread wider than 15 cents. Everything else is NO TRADE.

This is a transparent heuristic, not a backtested or calibrated model. Kalshi's 15-minute BTC contract settles on the CF Benchmarks BRTI 60-second average, not Coinbase's spot quote. That difference can change an outcome. Do not treat the signal as a probability or guarantee.

## Publish free using GitHub Pages (iPhone friendly)
1. Download and extract `kalshi-btc-signal-bot.zip` in the iPhone **Files** app.
2. In Safari, open **https://github.com/new** and sign in.
3. Create a repository named `kalshi-btc-signal-bot`. Set it to **Public**, then tap **Create repository**.
4. In the repository, choose **Add file → Upload files**. Upload these five files from the extracted folder to the repository's top level: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, and `icon-512.png`. Tap **Commit changes**.
5. Open the repository's **Settings → Pages**. Under **Build and deployment**, select **Deploy from a branch**, choose branch **main** and folder **/(root)**, then save.
6. GitHub will show the published address. It will look like `https://YOUR-USERNAME.github.io/kalshi-btc-signal-bot/`.
7. Open that address in **Safari** on the iPhone. Tap **Share → Add to Home Screen → Add**.
8. Open the new **BTC Signal** Home Screen icon. Tap **Enable alerts** and allow notifications if iOS offers the prompt.

## Important iPhone alert limitation
This free static version refreshes every 15 seconds and can show a browser notification for a signal change **while the dashboard is open and running**. It cannot check markets or send new alerts after you fully close the app. True background push alerts require a separate always-on service that checks the market and sends Web Push; free Render web services sleep after inactivity, so this project does not pretend to offer 24/7 background alerts.

## If the page shows DATA ISSUE
Check the iPhone internet connection and tap **Refresh now**. If the market-data provider or Coinbase is temporarily unavailable, the app intentionally displays NO TRADE instead of guessing.
