# Stock Price Prediction with LSTM and Technical Indicators

This project implements a deep learning model using LSTM (Long Short-Term Memory) networks and technical indicators to predict the next day's opening stock price for Microsoft (MSFT). The model leverages historical stock data and various technical indicators, such as SMA (Simple Moving Average) and MACD (Moving Average Convergence Divergence), to make accurate predictions and suggest potential buy/sell signals.

## Project Overview

This project is designed to:
1. **Process Historical Data**: Preprocess historical stock data for model input, extracting features from OHLCV (Open, High, Low, Close, Volume) data.
2. **Train a Hybrid Model**: Utilize both LSTM layers for sequential data and Dense layers for technical indicators, creating a two-branch model that predicts future prices.
3. **Generate Buy/Sell Signals**: Apply the trained model to calculate buy/sell signals based on price movement predictions.

## Table of Contents
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Model Architecture](#model-architecture)
- [Evaluation and Results](#evaluation-and-results)
- [Future Improvements](#future-improvements)

## Dataset

The model uses historical OHLCV data for MSFT stock:
1. **Historical OHLCV data** - Downloaded from Alpha Vantage API with `alpha_vantage` library.
2. **Technical Indicators** - Calculated from OHLCV data to enhance model performance.

You can replace `MSFT_daily.csv` with another stock's daily data file to train and test on a different stock.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/StockPricePrediction
   cd StockPricePrediction
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up your Alpha Vantage API key:
   - Save your key in `creds.json` as follows:
     ```json
     {
       "av_api_key": "your_alpha_vantage_key"
     }
     ```

## Usage

### Download Dataset

To download the dataset:
```bash
python main.py SYMBOL TIME_WINDOW
```
- **SYMBOL**: The stock ticker symbol (e.g., MSFT)
- **TIME_WINDOW**: The time frame, which can be `intraday`, `daily`, or `daily_adj`.

Example:
```bash
python main.py MSFT daily
```

### Train the Model

Run the main script to preprocess data and train the model:
```bash
python train.py
```

### Generate Predictions and Evaluate Model

To evaluate the model and plot real vs. predicted values:
```bash
python evaluate.py
```

This script also generates buy/sell signals and calculates potential earnings based on the model's predictions.

## Model Architecture

- **LSTM Branch**: Takes in OHLCV data for sequence learning.
- **Dense Branch**: Processes technical indicators separately.
- **Concatenation Layer**: Combines outputs of both branches to predict the next day's opening price.

## Evaluation and Results

- **Mean Squared Error**: Used to evaluate model performance.
- **Buy/Sell Signals**: Generated based on predicted price changes.
- **Visualizations**: Plot showing real vs. predicted prices, including buy and sell points.

Example output:
```plaintext
Earnings: $XX.XX
Mean Squared Error: X.XX%
```

![Real vs Predicted](example_plot.png)

## Future Improvements

1. Incorporate additional technical indicators, like Bollinger Bands and RSI.
2. Extend the model to predict multi-day trends.
3. Experiment with other architectures like Transformer models.

## License

This project is open-source under the MIT license.
