# Stock Price Analysis Using Sentiment and LSTM

This project evaluates the effect of financial news on stock trends. It utilizes **FinBERT**, a financial sentiment analysis model, to extract sentiment scores from financial news and combines them with stock price trends to forecast future stock movements using **LSTM**.

## Features
- **Sentiment Analysis with FinBERT**: Extracts sentiment scores from financial news articles.
- **Stock Trend Prediction**: Uses LSTM to analyze past stock prices and sentiment data for trend forecasting.
- **Automated Data Processing**: Parses stock and news data, normalizes features, and prepares datasets for training.

## Code Flow
### 1. Data Collection
- **Stock Data**: We use historical stock price data acquired from AlphaVantage, stored in `AAPL_historical.csv`. This data is processed to derive trends, which are then stored in `AAPL_trend.csv`. This file includes closing prices and trend labels (increase, decrease, stable).
- **News Data**: Financial news articles are stored in `newsData.json`, where each entry contains the title, description, and content of an article.
- Data is extracted for the period from February 2024 to February 2025.

### 2. Sentiment Analysis
- The **FinBERT** model is used to analyze the sentiment of financial news articles.
- Sentiment scores are calculated based on the article title as **Positive Sentiment - Negative Sentiment**.
- Sentiment scores for all articles on a given date are averaged to generate a single sentiment score per day.

### 3. Feature Engineering
- Training features are created using **stock prices from the past 7 days** and **the sentiment score from 1 day**.
- The stock trend (increase, decrease, stable) serves as the label for training.
- The dataset is split into training and testing sets using `train_test_split`.

### 4. Model Training
- The **LSTM-based neural network** is structured as follows:
  - **Input**: A feature vector comprising stock prices and sentiment scores.
  - **Hidden Layers**: LSTM layers to capture time-series dependencies.
  - **Output**: A classification layer predicting the stock trend (increase, decrease, stable).
- The model is trained using **CrossEntropyLoss** and the **Adam optimizer** for 30,000 epochs.

### 5. Model Evaluation
- The trained model is evaluated on the test dataset.
- Accuracy is measured by comparing predicted trends with actual trends.

## Results and Discussion
After training for 30,000 epochs, the LSTM model achieved a test accuracy of **70%**. Key observations include:
- Sentiment scores played a role in some cases but did not generalize well across all instances.
- There was no significant improvement in accuracy compared to a model using only past stock prices.
- This limitation is attributed to the news headline collection process, as our data sources only allow keyword-based extraction rather than direct retrieval of relevant stock-related headlines.
- Stock prices are influenced by numerous additional factors (e.g., political events) that are difficult to incorporate into the model.

## Future Work
- Implementing **Stochastic Differential Equation (SDE)**-based models for stock price prediction.
- Enhancing news extraction methods, expanding the dataset, and improving sentiment analysis techniques.
- Incorporating additional external factors that influence stock prices to improve predictive accuracy.
