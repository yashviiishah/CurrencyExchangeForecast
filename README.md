# CurrencyExchangeForecast
This repo provides insights into USD-INR forex forecasting on simple univariate USD-INR historical prices using Time series analysis

Project Introduction:
This project develops a classical time series forecasting pipeline to predict the USD/INR exchange rate using historical data. The goal is to implement a robust forecasting model.

Methodology:

The project is structured into three distinct phases, each documented in a separate Jupyter Notebook:

1_datacollection.ipynb (Data Sourcing):
- Objective: To fetch and inspect the raw historical daily exchange rate data.
- Source: The data is sourced using the yfinance library for financial market data.
- Data Period: Daily USD/INR closing prices were collected for the period from 2015-10-27 to 2025-10-24.
- Dataset is automatically fetched from yfinance for the last 10 years(starting the date of running cell to 10 years back)

2_eda.ipynb (Exploratory Data Analysis)
- Objective: To understand the statistical properties, trends & seasonality of the time series data.
-  Key Findings:

   a) The time series plot reveals a strong, consistent appreciation of the USD against the INR with a visible acceleration in recent years.

   b) Initial checks indicate the series is non-stationary, which is common in financial data requiring transformation before modeling.

   c) Techniques used include time series plots, rolling statistics & seasonal decomposition.

3_stationarity.ipynb (Modeling and Forecasting)
-  Objective: To preprocess the data, achieve stationarity, build a suitable time series model & generate forecasts.
-  Data Preprocessing:
  
    a) The time series index was standardized to Business Day ('B') frequency.
  
   b) Missing values (introduced by re-indexing for business days) were filled using time-based linear interpolation (method="time").
  
   c) To achieve stationarity, the data was transformed using log differencing. Stationarity was verified using the Augmented Dickey-Fuller (ADF) and KPSS tests.
- Modeling:

  a) Classical time series models, specifically Autoregressive Integrated Moving Average (ARIMA) models, were explored.
  
  b) Model orders (p, d, q) were determined by analyzing the Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) plots of the differenced series.
  
  c) The data was split into training and testing sets to evaluate model performance.


Libraries:

pandas: Data manipulation and time series indexing

numpy: Numerical operations 

matplotlib & seaborn: Data visualization (plots, ACF, PACF)

statsmodels: Time series analysis, stationarity tests (ADF, KPSS) & ARIMA modeling

yfinance: Data collection from financial markets (exchange rate)

datetime & timedelta Handling date and time operations

Future Work:

1. The project sets the stage for several future enhancements:

2. Use of Bivariate  and Multivariate Data for better results and prediction.

3. Model Selection: Systematically compare the performance of various time series models (e.g., SARIMA, Prophet, LSTM) against the fitted ARIMA model.

4. Deployment: Implement the trained model using a web framework like FastAPI or Streamlit to create an interactive forecasting tool.

5. Volatility Modeling: Explore GARCH-family models to account for the time-varying volatility observed in the financial data's residuals.
