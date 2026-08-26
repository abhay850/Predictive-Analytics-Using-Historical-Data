# Walmart Sales Prediction — Predictive Analytics Using Historical Data

A predictive analytics project that forecasts Walmart weekly sales using historical
data. The project combines a Python machine learning pipeline (data cleaning,
model training, evaluation, forecasting) with an interactive Power BI dashboard
for business-ready visualization.

## 📌 Project Objective

Build a predictive model to forecast future sales trends using historical Walmart
sales data, and present the results through an interactive dashboard.

## 🗂️ Dataset

**Walmart Sales Dataset** — 6,435 records across 45 stores, with the following columns:

| Column          | Description                               |
|-----------------|-------------------------------------------|
| `Store`         | Store number (1–45)                       |
| `Date`          | Week of sales record                      |
| `Weekly_Sales`  | Sales for the given store and week        |
| `Holiday_Flag`  | Whether the week included a holiday (0/1) |
| `Temperature`   | Regional temperature                      |
| `Fuel_Price`    | Regional fuel price                       |
| `CPI`           | Consumer Price Index                      |
| `Unemployment`  | Regional unemployment rate                |

## 🧰 Tech Stack

- **Python** (Google Colab) — data cleaning, feature engineering, model training
- **pandas / NumPy** — data manipulation
- **scikit-learn** — Linear Regression & Random Forest Regressor
- **Matplotlib** — exploratory visualizations
- **Power BI Desktop** — interactive dashboard

## 🔬 Workflow

### 1. Data Cleaning & Preprocessing
- Converted `Date` from text to datetime format
- Extracted `Year`, `Month`, and `Week` as additional features to capture seasonality
- Verified there were no missing values in the dataset

### 2. Exploratory Data Analysis
- Visualized total weekly sales trend across all stores
- Identified strong seasonal spikes in **November–December**, consistent with
  holiday shopping behavior

### 3. Model Building
Two models were trained and compared:

| Model                        | MAE          | RMSE         | R² Score   |
|-------------------------------|--------------|--------------|------------|
| Linear Regression              | ₹432,594.98  | ₹521,583.50  | 0.1555     |
| **Random Forest Regressor**    | **₹62,022.51** | **₹114,106.34** | **0.9596** |

Random Forest was selected as the final model due to its significantly higher
accuracy, driven by its ability to capture non-linear relationships and treat
`Store` as an effective categorical signal.

### 4. Feature Importance
The Random Forest model identified the most influential predictors of weekly sales:

1. **Store** — by far the strongest predictor (each store has its own baseline sales level)
2. **CPI**
3. **Unemployment**
4. **Week**

### 5. Forecasting
Using the trained model, sales for **Store 1** were forecasted 10 weeks into the
future, extending the historical trend into early 2013.

## 📊 Power BI Dashboard

The processed data (actual sales, model predictions, prediction error, and the
future forecast) was exported from Python and loaded into Power BI to build an
interactive dashboard featuring:

- **KPI cards** — Total Sales, Average Weekly Sales, Model Accuracy (R²), Store Count
- **Weekly sales trend** — overall seasonality across all stores
- **Store-wise sales comparison** — bar chart across all 45 stores
- **Feature importance chart** — visual ranking of predictive factors
- **Store 1: Sales History & Future Forecast** — a combined line chart showing
  actual sales, model predictions, and the 10-week future forecast in a single
  continuous view

A preview of the dashboard is included in this repository as
[`walmart_sales_dashboard.pdf`](./walmart_sales_dashboard.pdf).

## 📁 Repository Structure

```
├── Walmart.ipynb                     # Python notebook: cleaning, modeling, forecasting
├── walmart_dashboard_main.csv        # Exported historical data + predictions
├── walmart_dashboard_forecast.csv    # Exported future forecast data
├── walmart_dashboard.pbix            # Power BI dashboard file
├── walmart_sales_dashboard.pdf       # Dashboard preview
└── README.md
```

## ▶️ How to Run

1. Open `Walmart.ipynb` in Google Colab
2. Upload the Walmart Sales dataset when prompted
3. Run all cells to reproduce data cleaning, model training, evaluation, and forecasting
4. Open `walmart_dashboard.pbix` in Power BI Desktop to explore the interactive dashboard

## 📈 Key Outcome

The Random Forest model explains **~96% of the variance** in weekly sales
(R² = 0.9596), providing accurate, store-level forecasts that are presented
through a clean, interactive Power BI dashboard — demonstrating an end-to-end
predictive analytics workflow from raw data to business-ready insight.

## ✍️ Author

**Abhay Tiwari**
