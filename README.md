# Beta Calculations for Magnificent 7 (Date range: 2021-8-1 to 2023-8-1) 
The project is completed using Python Jupiter Notebook and the data source is from Yahoo Finance. 
# Beta Formula
Beta = Covariance(Return of the stock, Return of the market) / Variance(Return of the market)
​
## Retrieve data
```
start_date = "2021-08-01"  
end_date = "2023-08-01"  
data = yf.download('^GSPC', start=start_date, end=end_date)
symbols = ["AAPL", "AMZN", "GOOG", "META", "MSFT", "NVDA", "TSLA"]
market_symbol = '^GSPC'  # S&P 500 index symbol
stock_data = yf.download(symbols, start=start_date, end=end_date)
print(stock_data)
```

```
# Dictionary to store beta values for each symbol
beta_values = {}

# Fetch historical price data for each symbol and the S&P 500 index
for symbol in symbols:
    stock_data = yf.download(symbol, start=start_date, end=end_date)['Adj Close']
    market_data = yf.download(market_symbol, start=start_date, end=end_date)['Adj Close']

    stock_df = pd.DataFrame(stock_data)
    market_df = pd.DataFrame(market_data)

    stock_returns = stock_df.pct_change().dropna()
    market_returns = market_df.pct_change().dropna()

    covariance = stock_returns['Adj Close'].cov(market_returns['Adj Close'])
    market_variance = market_returns['Adj Close'].var()

    beta = covariance / market_variance
    beta_values[symbol] = beta

# Print the beta values
print("Beta Values:")
for symbol, beta in beta_values.items():
    print(f"{symbol}: {beta}")
```
![image](https://github.com/raynachen2023/Finance_Beta-calculation/assets/128624675/19c43282-84e2-42ef-9289-c6c6c16db780)

## Visualization
```
plt.figure(figsize=(10, 6))
plt.bar(beta_values.keys(),beta_values.values(), color='skyblue')
plt.axhline(y=1, color='r', linestyle='--', label='Market (Beta = 1)')
plt.title('Beta Values for Mentioned Symbols')
plt.xlabel('Stock Symbols')
plt.ylabel('Beta')
plt.legend()
plt.grid(axis='y', linestyle='--', alpha=0.7)
for symbol, beta in beta_values.items():
    plt.text(symbol, beta + 0.05, f'{beta:.2f}', ha='center', va='bottom', fontsize=10)

plt.show()
```

![image](https://github.com/raynachen2023/Finance_Beta-calculation/assets/128624675/9ae005a9-b3fa-473a-88a0-d3829d879173)

