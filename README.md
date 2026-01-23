# 📈 Store Item Demand Forecasting

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-%23EB4034.svg?style=for-the-badge&logo=xgboost&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Time Series](https://img.shields.io/badge/Task-Time_Series_Forecasting-success?style=for-the-badge)

## 📌 Project Overview
This project aims to build a robust machine learning model to predict future sales for different items across multiple store locations. 

Accurate demand forecasting is critical for retail operations to optimize inventory levels, reduce holding costs, and prevent stockouts, directly impacting the bottom line.

## 💼 Business Problem
Inventory management is a balancing act.
* **Overstocking:** Leads to increased storage costs and potential waste.
* **Understocking:** Results in lost revenue and dissatisfied customers.

**Objective:** Predict 3 months of item-level sales data at different store locations to assist in supply chain planning.

## 📂 Dataset
The dataset represents historical sales data.
* **Date:** Daily records of sales.
* **Store:** Store ID (Categorical).
* **Item:** Item ID (Categorical).
* **Sales:** Number of items sold (Target Variable).

## 🛠️ Tech Stack
* **Language:** Python
* **Data Manipulation:** `pandas`, `numpy`
* **Visualization:** `matplotlib`, `seaborn`
* **Time Series Analysis:** `statsmodels` (Decomposition, ADF Test, ACF/PACF)
* **Machine Learning:** `XGBoost`, `LightGBM`, `Scikit-Learn`

## ⚙️ Methodology

### 1. Exploratory Data Analysis (EDA)
* **Seasonality Analysis:** Decomposed the time series to identify yearly, monthly, and weekly sales patterns.
* **Stationarity Check:** Performed Augmented Dickey-Fuller (ADF) test to check if the data is stationary.
* **Trend Analysis:** Visualized the overall growth of sales over 5 years.

### 2. Feature Engineering (Crucial Step)
Since machine learning models (like XGBoost) do not inherently understand "time," extensive feature engineering was performed:
* **Date Features:** Extracted Year, Month, Day, DayOfWeek, Weekend flag.
* **Lag Features:** Created columns for past sales (e.g., sales 90 days ago, 365 days ago) to capture autocorrelation.
* **Rolling Window Statistics:** Calculated rolling mean and standard deviation (e.g., 7-day moving average).

### 3. Modeling Strategy
* **Baseline:** Naive approach (predicting the previous day's value).
* **Time Series Model:** SARIMA (Seasonal AutoRegressive Integrated Moving Average).
* **Machine Learning:** **XGBoost** and **LightGBM** regressors were trained using the engineered features.

### 4. Evaluation Metric
The models were evaluated using **SMAPE (Symmetric Mean Absolute Percentage Error)** and **RMSE (Root Mean Square Error)** to penalize large errors effectively.

## 📈 Results
* **Best Model:** XGBoost Regressor with hyperparameter tuning.
* **Performance:** Achieved a SMAPE score of **13.xx%** (lower is better).
* **Key Insight:** Sales are highly seasonal, with peaks in July and minimal sales in January. The "Day of the Week" feature (specifically weekends) was a strong predictor.

## 🚀 How to Run
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/store-sales-prediction.git](https://github.com/your-username/store-sales-prediction.git)
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run the notebook:**
    ```bash
    jupyter notebook Sales_Forecasting.ipynb
    ```

## 📂 Directory Structure

├── data/ # Train and test datasets ├── notebooks/ # Analysis and modeling notebooks ├── src/ # Scripts for feature engineering ├── models/ # Saved model objects (.pkl) ├── README.md # Project documentation └── requirements.txt # Dependencies

## 🤝 Contributing
Open to suggestions for improving feature engineering or trying Deep Learning approaches (LSTM/GRU).

## 📜 License
This project is licensed under the MIT License.
