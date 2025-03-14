# Stock Price Analysis using Sentiment and LSTM

This project integrates financial news sentiment analysis with stock trend prediction using an LSTM (Long Short-Term Memory) neural network. It utilizes **FinBERT**, a financial sentiment analysis model, to extract sentiment scores from financial news and combines them with stock price trends to forecast future stock movements.

## Features
- **Sentiment Analysis with FinBERT**: Extracts sentiment scores from financial news articles.
- **Stock Trend Prediction**: Uses LSTM to analyze past stock prices and sentiment data for trend forecasting.
- **Automated Data Processing**: Parses stock and news data, normalizes features, and prepares datasets for training.

## Repository Structure
```
├── data/                    # Contains stock price and news datasets
│   ├── AAPL_trend.csv       # Historical stock data for Apple
│   ├── newsData.json        # Financial news articles
├── models/                  # Saved models (if needed)
├── notebooks/               # Jupyter Notebooks for experimentation
├── src/                     # Source code
│   ├── sentiment_analysis.py # FinBERT-based sentiment processing
│   ├── lstm_model.py         # LSTM model for stock trend prediction
│   ├── train.py              # Training script
│   ├── evaluate.py           # Model evaluation script
├── README.md                # Project documentation (this file)
└── requirements.txt          # Required Python packages
```

## Code Flow
### 1. Data Collection
- **Stock Data**: We use historical stock price data stored in `AAPL_trend.csv`. This file includes closing prices and trend labels (increase, decrease, stable).
- **News Data**: Financial news articles are stored in `newsData.json`. Each entry contains the title, description, and content of an article.

### 2. Sentiment Analysis
- We use the **FinBERT** model to analyze the sentiment of financial news articles.
- Each article's sentiment score is calculated as **Positive Sentiment - Negative Sentiment**.
- Daily sentiment scores are averaged for each day to generate a single sentiment score per date.

### 3. Feature Engineering
- We prepare training features using **past 3 days of stock prices** and **1 day of sentiment score**.
- The stock trend (increase, decrease, stable) is used as the label for training.
- Data is split into training and testing sets using `train_test_split`.

### 4. Model Training
- We define an **LSTM-based neural network** with:
  - Input: Stock prices and sentiment scores
  - Hidden layers: LSTM layers to capture time-series dependencies
  - Output: A classification layer predicting the stock trend (increase, decrease, stable)
- The model is trained using **CrossEntropyLoss** and the **Adam optimizer** for 50 epochs.

### 5. Model Evaluation
- The trained model is evaluated on the test dataset.
- Accuracy is computed by comparing predicted trends with actual trends.


