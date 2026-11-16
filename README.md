# BTC Signal · Kalshi 15m (V3)

A free, read-only, iPhone-friendly dashboard for public BTC and Kalshi market data.

## V3 paper-trading tracker
- Records the first qualifying PAPER UP / PAPER DOWN setup seen for each market ticker while the dashboard is open.
- Stores records in this browser's localStorage on this device.
- Tracks entry ask, estimated one-contract taker fee, break-even cost, pending/settled status, win rate, net paper P/L and maximum peak-to-trough drawdown.
- Attempts to verify settlements using Kalshi's public market endpoint. If the endpoint is unavailable or blocked by browser CORS, the trade remains pending; the app never guesses a result.
- Exports the recorded history as CSV.

## Deploy
Upload the contents of this folder to the root of a GitHub Pages repository and commit to `main`. Keep the existing Pages setting `main` / `/(root)`.

## Important limitations
- The dashboard only captures signals while open and refreshing. It does not run 24/7 in the background.
- Paper history is local to this browser/device. Clearing Safari website data or using another browser/device can lose or separate the history. Export CSV regularly.
- One paper entry is recorded per market ticker, at the first qualifying signal seen; it is not a backtest and may miss signals while closed.
- Settlement verification depends on the public Kalshi endpoint being reachable from the browser. Pending entries are not counted in win rate or P/L.
- Coinbase BTC data is a proxy, not the CF Benchmarks BRTI settlement index.
- This is not a proven profitable strategy and does not place orders or access a Kalshi account.
