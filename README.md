import vectorbt as vbt
import pandas as pd

# Parameters
symbol = 'AAPL'
rsi_window = 14
sma_fast_window = 10
sma_slow_window = 30

# 1. Get closing prices
price = vbt.YFData.download(symbol).get('Close')

# 2. Calculate RSI manually
delta = price.diff()
gain = delta.where(delta > 0, 0)
loss = -delta.where(delta < 0, 0)

avg_gain = gain.rolling(window=rsi_window).mean()
avg_loss = loss.rolling(window=rsi_window).mean()
rs = avg_gain / avg_loss
rsi = 100 - (100 / (1 + rs))

# 3. Moving Averages
sma_fast = price.rolling(window=sma_fast_window).mean()
sma_slow = price.rolling(window=sma_slow_window).mean()

# 4. Entry/Exit Logic
entries = (sma_fast > sma_slow) & (rsi < 30)
exits = (sma_fast < sma_slow) | (rsi > 70)

# 5. Portfolio Backtest
portfolio = vbt.Portfolio.from_signals(price, entries, exits)

# 6. Results
print(portfolio.stats())
portfolio.plot().show()


