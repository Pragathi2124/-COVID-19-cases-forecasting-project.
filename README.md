# COVID-19-cases-forecasting-project
## **COVID-19 Daily Confirmed Cases Forecasting using ARIMA**

### **Project Overview**
This project focuses on time series analysis and forecasting of daily new confirmed COVID-19 cases in the US. The primary goal is to build and evaluate an ARIMA (AutoRegressive Integrated Moving Average) model to predict future daily cases. The project involves extensive data cleaning and preparation, exploratory data analysis to identify trends and seasonality, and rigorous hyperparameter tuning to find the optimal ARIMA model.

**Dataset 📊**
The dataset used is 
covid_wikipedia_tables.csv, which contains daily COVID-19 statistics for various US states and territories, scraped from Wikipedia tables. The key feature used for forecasting is the number of new confirmed cases per day

**Methodology 👨‍💻**
The project follows a standard time series analysis workflow, from data ingestion to model evaluation and forecasting.

**1. Data Loading and Initial Exploration**
First, the necessary libraries are imported. An initial look at the data's shape and a sample of the first few rows reveals a raw and untidy format that requires significant cleaning
Of course. Although you mentioned a "Pneumonia prediction" project, the files you've uploaded are for a COVID-19 cases forecasting project. I have analyzed the provided notebook and CSV file and created a detailed README.md for your GitHub repository based on the project you shared.

**2. Data Cleaning and Preprocessing**
The raw dataset contains multiple tables and misplaced headers. The following steps were taken to clean and structure the data for time series analysis:
**Isolating Case Data:** A copy of the original DataFrame is created to work with the case data specifically.
**Header Correction:** The first row, which contains misplaced headers, is dropped. An extra date column is also removed.
**Column Renaming:** The columns are programmatically renamed based on the second row of the raw data. Key columns like 'Confirmed New', 'Confirmed Cml' (Cumulative), 'Deaths New', etc., are manually renamed for clarity. A final 'Active Cml' column is added.
**Row Cleaning:** Rows containing redundant headers and summary data are dropped.
**Handling Missing Values:** NaN values are filled with 0, as they represent no new cases on a given day.
**Date Conversion:** The 'Date' column is converted from a string format to datetime objects.
**Final Touches:** The DataFrame is re-indexed, the 'Date' column is set as the index, and all data types are converted to float for numerical analysis.

**3. Exploratory Data Analysis (EDA)**
To understand the trend of new confirmed COVID-19 cases, the daily numbers and a 7-day rolling mean are plotted. The rolling mean helps to smooth out daily fluctuations and highlight the underlying trend

**4. Time Series Analysis:** ACF and PACF
To determine the parameters (p, d, q) for the ARIMA model, the Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) plots are generated. These plots help identify the correlation of the time series with its own lagged values.
**ACF Plot:** Shows the correlation of the series with its lags. A sharp drop-off suggests a Moving Average (MA) model.
**PACF Plot:** Shows the correlation of the series with its lags after removing the effect of intermediate lags. A sharp drop-off suggests an AutoRegressive (AR) model.

**5. ARIMA Model Hyperparameter Tuning**
A grid search approach is used to find the optimal order (p, d, q) for the ARIMA model. The model is trained on the first 66% of the data, and its performance is evaluated on the remaining 34% by calculating the Root Mean Squared Error (RMSE). The combination of (p, d, q) values that yields the lowest RMSE is selected as the best model.
The best parameters found were 
**ARIMA(8, 0, 2) with an RMSE of 4461.648**

**6. Forecasting and Final Evaluation**
Using the best model parameters, the final ARIMA model is trained on a larger portion of the data (all but the last 60 days) and used to forecast the confirmed new cases for the test period. The predicted values are then plotted against the actual values to visually assess the model's performance. Additionally, forecasts are made for different time horizons (5, 10, 20 days, etc.), and their respective RMSEs are calculated and plotted to understand how prediction accuracy changes over time

**Results and Conclusion 📈**
The ARIMA model proved to be effective for short-term forecasting of new COVID-19 cases. The hyperparameter tuning process identified 

ARIMA(8, 0, 2) as the optimal model configuration based on the lowest RMSE. The final visualizations demonstrate that the model captures the trend of the data reasonably well for shorter forecast horizons. The analysis of RMSE over different prediction windows confirms that the model's accuracy decreases as the forecast period increases, which is typical for time series models. This project showcases a practical application of time series forecasting in a real-world public health context.
