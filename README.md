# Stock Sentiment Analysis with LSTM

This project integrates financial news sentiment analysis with stock trend prediction using an LSTM (Long Short-Term Memory) neural network. It utilizes **FinBERT**, a financial sentiment analysis model, to extract sentiment scores from financial news and combines them with stock price trends to forecast stock movements.

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

## Installation
```sh
# Clone the repository
git clone https://github.com/your-repo/stock-sentiment-lstm.git
cd stock-sentiment-lstm

# Install dependencies
pip install -r requirements.txt
```

## Usage
### 1. Process Sentiment Data
```sh
python src/sentiment_analysis.py
```
### 2. Train the LSTM Model
```sh
python src/train.py
```
### 3. Evaluate the Model
```sh
python src/evaluate.py
```

## Dependencies
- Python 3.8+
- PyTorch
- Transformers (Hugging Face)
- Pandas & NumPy
- Scikit-learn

## Future Improvements
- Integrate real-time stock and news data
- Experiment with different deep learning architectures
- Improve feature selection for better prediction accuracy

## License
This project is licensed under the MIT License.

---
🚀 Happy Coding!
