QX TERMINAL — ANALYSIS & DEMO SIMULATOR
========================================

WHAT THIS IS
- A mobile-first HTML/CSS/JavaScript market-analysis dashboard.
- Includes RSI, simple support/resistance proximity, basic price-action checks,
  a three-candle FVG heuristic, candlestick pattern heuristics and Bollinger Bands.
- Includes a demo journal and historical next-candle simulator.
- Includes PWA manifest and offline service worker.

IMPORTANT LIMITATIONS
- Built-in candles are RANDOM SYNTHETIC SAMPLE DATA, not live prices.
- This project does NOT connect to Quotex, log into accounts, place orders,
  or automate real-money trading.
- It does not include a verified free live data provider.
- OTC quotes are platform-specific and should not be assumed to match public feeds.
- The custom JSON endpoint option only works with a provider you are authorized
  to use, which permits browser CORS and returns at least 25 candle objects:
  [{"time": 1730000000000, "open": 1.1, "high": 1.2, "low": 1.0, "close": 1.15}]
  time should be a numeric timestamp in milliseconds. Values must be numeric.
- A custom endpoint may be delayed, incomplete, or unavailable. Verify its terms,
  timestamps, symbol mapping and candle timeframe yourself.
- Score is a heuristic agreement score, NOT a win probability or guarantee.
- The simplified SMC/FVG and pattern checks are educational approximations.

RUN LOCALLY
1. Extract the ZIP.
2. Open index.html in a browser. Most dashboard features work locally.
3. For PWA installation/service worker, deploy on HTTPS (GitHub Pages is free).

PHONE-FRIENDLY DEPLOYMENT (GITHUB PAGES)
1. On Android, open github.com in Chrome and sign in or create an account.
2. Create a new public repository, e.g. qx-terminal-demo.
3. Upload index.html, styles.css, app.js, manifest.webmanifest and sw.js
   to the repository root (not inside another folder).
4. Open repository Settings > Pages.
5. Under Build and deployment, choose Deploy from a branch.
6. Select main and /(root), then Save.
7. Wait for GitHub Pages to publish. Open the generated HTTPS address in Chrome.
8. Chrome menu > Add to Home screen / Install app (wording varies).
9. Reopen the app from the home screen. It can cache the app shell offline.

CSV FORMAT
time,open,high,low,close
1730000000000,1.0800,1.0810,1.0790,1.0805
...
At least 25 valid rows are required. Timestamps should be milliseconds.

CUSTOM JSON DATA
The endpoint must allow cross-origin browser requests (CORS) and return either:
- a raw array of candle objects, or
- {"candles":[...]} or {"data":[...]}
Each candle: time, open, high, low, close.
No API key is bundled. Never paste private API keys into a public repository.

TESTING NOTES
- Use enough historical candles to provide future candles for the chosen expiry.
- The demo simulator uses the next available row(s) in the imported dataset.
- This is a simple educational simulator, not an execution-quality backtester.
- Real market microstructure, payout, slippage, spread, latency and expiry rules
  are not modelled faithfully.
