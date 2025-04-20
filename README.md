# 📊 RSI + SMA Trading Strategy using vectorbt

This project demonstrates a simple trading strategy that combines the **Relative Strength Index (RSI)** and **Simple Moving Averages (SMA)**, using the powerful [vectorbt](https://github.com/polakowo/vectorbt) library for backtesting and visualization.

## 💡 Strategy Logic
- **Buy Signal**:  
  - Short-term SMA crosses **above** long-term SMA (**bullish crossover**)  
  - RSI is **below 30** (indicating oversold conditions)

- **Sell Signal**:  
  - Short-term SMA crosses **below** long-term SMA  
  - RSI is **above 70** (indicating overbought conditions)

## 🛠️ Features
- Pulls historical stock data via Yahoo Finance
- Manually calculates RSI using pandas
- Computes fast and slow SMAs with rolling averages
- Generates entry/exit signals based on RSI + SMA logic
- Backtests the strategy using `vectorbt.Portfolio`
- Visualizes trade entries, exits, and performance

## 📁 Files
- `vectorbt.ipynb` – Jupyter notebook containing the full code, logic, and visual output

## 📦 Requirements
- `vectorbt`
- `pandas`
- `yfinance`  
Install them using:
```bash
pip install vectorbt pandas yfinance
