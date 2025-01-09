# Portfolio Simulation using Time Series Modeling

## Project Overview

This project simulates the performance of a financial portfolio composed of stocks from major companies including Nvidia (NVDA), Apple (AAPL), Vistra (VST), and MicroStrategy (MSTR). By utilizing time series modeling, the project forecasts stock trends over a five-year period from 2020 to 2025. The aim is to analyze the portfolio's behavior over time and provide insights into stock performance under various market conditions.

Key aspects of this problem include:
- Forecasting stock price movements using historical data.
- Simulating the portfolio's performance based on stock price predictions.
- Analyzing trends and providing insights into the portfolio's behavior over time.

## Methods Used
- **Data Preprocessing**: Cleaned, processed, and split stock data for analysis.
- **Feature Engineering**: Added additional features such as Simple Moving Average, Essential Moving Average and Relative Strength Index.
- **Time Series Forecasting**: Applied time series models to predict future stock performance based on historical data.
- **Visualization**: Used data visualizations to provide a clear understanding of stock trends and portfolio changes over time.
  
## Data Collection
Stock data for the selected companies (NVDA, AAPL, VST, MSTR) was collected from Yahoo Finance using the `yfinance` library. The data spans from January 2020 to January 2025, capturing daily stock prices, volume, and other relevant metrics for time series analysis.

Example stock symbols used:
```python
stocks = ["AAPL", "NVDA", "VST", "MSTR"]
start_date = '2020-01-01'
end_date = '2025-01-01'
```
## Model Training/Forecasting
For this project, two machine learning models were used for stock price prediction: **Random Forest Regressor** (a tree-based ensemble learning method) and **Long Short-Term Memory (LSTM)** (a recurrent neural network suitable for time series data). The models were applied to predict stock prices for each company in the portfolio.

### 1. **Random Forest Regressor**
The **Random Forest Regressor** is an ensemble learning method based on decision trees. It works by constructing multiple decision trees and averaging their predictions to provide a more robust and accurate result.

**Steps involved:**
- **Data Splitting**: First, the historical stock data was split into training and test sets. The model was trained on 80% of the data, leaving 20% for evaluation.
- **Feature Selection**: Features such as historical prices, and lagged features were used to train the Random Forest Regressor.
- **Model Training**: The Random Forest Regressor was trained to predict the next day's stock price based on these features. The model benefits from its ability to capture non-linear relationships in the data.

**Outcome**: The Random Forest model provided reasonable short-term predictions.

### 2. **Long Short-Term Memory (LSTM)**
The **LSTM** model is a type of recurrent neural network (RNN) that is particularly well-suited for sequential and time series data because it can remember long-term dependencies in the data. This makes it ideal for stock price forecasting, where historical trends and patterns are critical.

**Steps involved:**
- **Data Preparation**: The stock price data was scaled and reshaped into 3D input format required for LSTM. This included creating sliding windows of historical prices (e.g., using the last 20 days to predict the next day).


- **Prediction**: The LSTM model was trained to predict the next day's stock price using the previous 20 days of data as input. The model's ability to capture temporal dependencies made it more effective for long-term forecasts compared to the Random Forest model.

- **Outcome**: The LSTM model excelled at capturing long-term trends and patterns in stock prices, making it better suited for extended time horizons. However, the model was sensitive to hyperparameter tuning and required more computational resources than the Random Forest.

By combining these two models, the project was able to leverage the strength of **Random Forest Regressor** for short-term stock prediction and **LSTM** for long-term trend forecasting, offering a comprehensive view of potential portfolio performance over different time periods.


## Portfolio Simulation
To simulate the performance of the portfolio, we used the predicted stock prices generated by the using ensamble learning. The portfolio was composed of four stocks: Nvidia (NVDA), Apple (AAPL), Vistra (VST), and MicroStrategy (MSTR), with equal allocation of funds across all stocks.

The simulation involved the following steps:
- Initial Investment: A hypothetical initial investment was made, with equal amounts allocated to each stock.
- Daily Valuation: For each trading day, the predicted stock prices were used to estimate the portfolio's total value by calculating the sum of the predicted values of each stock.
- Cumulative Returns: We calculated the cumulative returns of the portfolio over time by tracking how the total portfolio value changed based on the predicted stock prices.

## Results
- The portfolio simulation provided an in-depth analysis of how the portfolio's value would evolve over time based on the model's predictions. We compared the actual valuation of the portfolio against the predicted valuation from the Random Forest and LSTM models:

- Actual Portfolio Performance: The actual portfolio's value fluctuated according to real stock market trends, with periods of growth and decline driven by market forces.
- Predicted Portfolio Performance: The model's predictions closely followed the general trend of the actual portfolio performance, but there were discrepancies in certain periods, particularly during volatile market conditions.

- This approach allowed us to visualize the performance of the portfolio and compare it to actual stock prices to evaluate the model's effectiveness in simulating real-world scenarios. The graph shows the difference between actual valuation of investment vs the predicted valuation. Over a 1 year period the actual valuation of the $10000 initial investment at end of January 2025 is over $26,000 where as our model predicted the investment would be worth just over $16,000.

![Portfolio Simulation](images/valuation.png)

## Limitations
While the model accurately captured historical trends and provided reasonable forecasts, it has several limitations:

- The model does not account for external factors such as economic developments, geopolitical events, innovations, or disruptions that might significantly affect stock prices.
- The predictions are based solely on historical data and do not include real-time market information or company-specific events.

## Conclusion/Improvements/Implications
This project successfully simulated portfolio performance using time series forecasting techniques. It provides valuable insights into stock price trends and portfolio behavior under different market conditions. However, there are several areas where this project can be improved:

- **Improvements**: The use of more advanced models such as ARIMA, more sophisticated LSTM architectures, or hybrid models combining Random Forest with deep learning techniques could enhance forecasting accuracy. Incorporating macroeconomic indicators, news data, and other external factors could further refine predictions.
- **Implications**: This simulation serves as a tool for understanding potential portfolio performance, but it should not be used for actual investment decisions without considering external factors that influence stock prices. With enhancements, this project could become a more robust tool for financial forecasting and portfolio management
