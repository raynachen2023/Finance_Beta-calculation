# Beta calculations for Magnificent 7 (Data range: 2021-8-1 to 2023-8-1)
The project is completed using Python Jupiter Notebook and the data source is from Yahoo Finance. 

## Retrieve data
symbols = ["AAPL", "AMZN", "GOOG", "META", "MSFT", "NVDA", "TSLA"]
market_symbol = '^GSPC'  # S&P 500 index symbol
stock_data = yf.download(symbols, start=start_date, end=end_date)
print(stock_data)
