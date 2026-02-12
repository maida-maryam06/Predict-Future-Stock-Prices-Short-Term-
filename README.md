# Stock Price Prediction Using Linear Regression

# Project Overview:
This project focuses on predicting the next day's closing price of a stock using historical market data. The goal was to apply machine learning techniques to short-term stock forecasting and understand how regression models behave on time series financial data.

For this project, I used Apple Inc. (AAPL) stock data from January 2021 to the present and implemented a Linear Regression model with proper feature engineering.

# Problem Statement
Stock prices change daily based on various factors. The objective of this project is:
-> To predict the next day's closing price
-> Using historical stock market data
-> By applying a supervised machine learning regression model
-> This helps demonstrate how machine learning can capture short-term price trends.

# Dataset
The dataset was collected using the yfinance API, which provides real-time and historical financial data.

The dataset includes:
- Open price
- High price
- Low price
- Close price
- Volume

Data range used:
January 1, 2021 – Present

## Step-by-Step Implementation
### 1. Data Loading
The stock data was fetched using the yfinance library.
This allowed automatic downloading of historical price data for Apple stock.

#### Why this step is important?
Provides real-world financial data
Ensures up-to-date and reliable information

### 2. Feature Engineering
Raw stock data alone is often not enough for accurate predictions. So additional features were created:

#### Lag Features
Close_Lag1
Close_Lag2

These represent previous days’ closing prices.
Stock prices are highly correlated with recent prices, so this improves prediction accuracy.

#### Moving Averages
5-day Moving Average (MA5)
10-day Moving Average (MA10)

These help the model understand short-term trends and smooth out noise.

#### Price Change & Returns
Daily price change (Close - Open)
Daily return percentage

These features capture volatility and momentum in stock movement.

#### Target Variable
The target variable was defined as:
Next day’s closing price

This was created by shifting the Close column forward by one day.

## 3. Data Cleaning
Rows containing missing values (created due to lag and rolling calculations) were removed using:
df.dropna()
This ensures the model trains on clean and complete data.

## Train/Test Split (Time-Series Safe)
Since this is time series data, a normal random split was avoided.

Instead:
First 80% → Training set
Last 20% → Testing set

This maintains chronological order and prevents data leakage.

## Feature Scaling
StandardScaler was used to standardize the features.

### Why scaling was needed?
Linear Regression performs better when features are on the same scale
Stock volume values are much larger than price values
Scaling ensures fair contribution from all features.

## 4. Model Selection – Linear Regression

A Linear Regression model was used because:
* It is simple and interpretable
* It helps understand relationships between features and target
* It serves as a strong baseline model

The model was trained using the training dataset and then evaluated on unseen test data.

## 5. Model Evaluation

Three evaluation metrics were used:
* R² Score: Measures how well the model explains variance in stock prices.
* MAE (Mean Absolute Error): Average prediction error in dollars.
* RMSE (Root Mean Squared Error): Penalizes larger prediction errors more heavily.

## 6. Results
### Training Performance
* R² = 0.9929
* MAE = $2.03
* RMSE = $2.72

### Testing Performance
* R² = 0.9766
* MAE = $2.82
* RMSE = $4.29

### Overcome:
- The model explains about 97–99% of the variance in stock prices.
- Average prediction error is around $2–$3, which is relatively small.
- The small gap between training and testing results indicates minimal overfitting.
- The model successfully captures short-term stock price trends.

## 7. Visualization
The project includes:
* Historical closing price plot
* Actual vs Predicted price comparison
* Model performance metrics

The predicted values closely follow the real stock trend.

## Key Learnings

Through this project I learned:
* How to handle time series financial data
* The importance of feature engineering in stock prediction
* Why chronological splitting is necessary
* How to evaluate regression models properly
*How scaling affects Linear Regression performance

## Conclusion

This project demonstrates that:
- Even a simple Linear Regression model can perform well with proper feature engineering.
- Short-term stock prices are strongly influenced by recent historical values.
- Careful preprocessing and time-series handling significantly improve model performance.
- While stock markets are inherently unpredictable, machine learning can effectively model short-term trends when structured properly.

## Technologies Used
* Python
* Pandas
* NumPy
* Matplotlib / Seaborn
* Scikit-learn
* yfinance
