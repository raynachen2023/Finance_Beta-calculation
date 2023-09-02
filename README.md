# Beta calculations for Magnificent 7 (Data range: 2021-8-1 to 2023-8-1)
The project is completed using Python Jupiter Notebook and the data source is from Yahoo Finance. 
# Beta Formula
Beta = Covariance(Return of the stock, Return of the market) / Variance(Return of the market)
​
## Retrieve data
```
symbols = ["AAPL", "AMZN", "GOOG", "META", "MSFT", "NVDA", "TSLA"]
market_symbol = '^GSPC'  # S&P 500 index symbol
stock_data = yf.download(symbols, start=start_date, end=end_date)
print(stock_data)
```
![image](https://github.com/raynachen2023/Finance_Beta-calculation/assets/128624675/fdf22a9f-cf89-46c8-827b-8e21f40cff09)

