# inoobe.github.io

some ai generated thing too lazy to make myself

# StockBoard

A local web dashboard listing every ticker in the **S&P 500** and **NASDAQ**,
with each symbol's latest closing price, daily change, and % change.

## Run it

```bash
pip install -r requirements.txt
python app.py
```

Then open **http://127.0.0.1:5000** in your browser.

The first load fetches the ticker universe (~4,500 symbols: the full S&P 500
and the full NASDAQ listing), then streams in prices from Yahoo Finance in
batches — the table is usable immediately and prices fill in as they arrive.

## Notes

- **No API key needed.** Prices come from Yahoo Finance via the `yfinance` library.
- The full NASDAQ listing is ~3,000+ symbols, so pulling every price takes a
  minute or two and can occasionally hit Yahoo's rate limiter. To use a faster,
  lighter universe (S&P 500 + NASDAQ-100, ~600 symbols), open `app.py` and set:
  ```python
  FETCH_FULL_NASDAQ = False
  ```
- Prices are last *closing* prices and are cached for ~60 seconds. Hit
  **Refresh** to re-pull.
- Search by ticker or company name; filter by index; click any column to sort.
