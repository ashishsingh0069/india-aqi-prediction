# ARCHITECTURE: India AQI Analysis and Prediction

## 1. Tech Stack
| Purpose | Tool |
|---------|------|
| Language | Python 3.10+ |
| Environment | Jupyter Notebook |
| Data handling | pandas, numpy |
| Visualization | matplotlib, seaborn (plotly optional) |
| ML | scikit-learn, xgboost |
| Explainability | shap |
| Reporting | python-docx or manual Word doc for the final report |

## 2. Project Structure
```
india-aqi/
├── AshishSingh_IndiaAQI_Prediction.ipynb
├── requirements.txt
├── README.md
├── AshishSingh_ProjectReport.docx
├── data/
│   └── city_day.csv          # downloaded from Kaggle, not committed
├── figures/                  # saved plots used in the report
└── docs/
    ├── PRD.md
    ├── ARCHITECTURE.md
    ├── TASKS.md
    └── RULES.md
```

## 3. Pipeline (Data Flow)
```
city_day.csv
   -> Load and inspect
   -> Clean (dates, missing values, outliers)
   -> EDA and insight analysis (figures saved to /figures)
   -> Feature engineering (date, lag, city encoding)
   -> Chronological train/test split
   -> Model training (baseline, LR, RF, XGBoost)
   -> Evaluation (MAE, RMSE, R2) and comparison table
   -> Explainability (feature importance, SHAP)
   -> Conclusions and limitations
```

## 4. Notebook Sections
1. Title, objective, dataset description
2. Imports and configuration (seed = 42)
3. Data loading and overview
4. Data cleaning
5. Exploratory data analysis
6. Insight analysis (COVID lockdown, Delhi seasonality)
7. Feature engineering
8. Modeling
9. Evaluation and comparison
10. Explainability
11. Conclusion, limitations, future work

## 5. Data Cleaning Strategy
- Parse `Date` to datetime and sort by City, Date.
- Drop rows with missing target (`AQI`) for modeling.
- Drop pollutant columns with very high missingness (check the percentage first, and justify in the notebook).
- Impute remaining pollutant gaps per city (forward-fill or city median), never using the test period to fill the training period.
- Cap outliers with IQR or percentile clipping for modeling; keep raw values for EDA where appropriate.

## 6. Feature Engineering
- **Date features:** year, month, day of week, season (winter, summer, monsoon, post-monsoon)
- **Lag features (per city):** AQI and key pollutants (PM2.5, PM10) at t-1, t-2, t-3; optional 7-day rolling mean
- **City:** one-hot or target/label encoding
- All lags must be computed within each city group to avoid mixing cities.

## 7. Modeling
- **Primary task:** predict **next-day AQI** using today's pollutants and lag features. AQI is computed from same-day pollutants, so predicting it from them alone is close to a lookup. Next-day prediction is the meaningful task.
- **Secondary (optional):** same-day AQI estimation as a sanity check, and AQI bucket classification.
- **Baseline:** naive persistence (tomorrow's AQI = today's AQI). Any model must beat this.
- **Models:** Linear Regression, Random Forest, XGBoost
- **Split:** chronological (for example train on 2015-2019, test on 2020, or the last 20% of dates). No shuffling.
- **Tuning:** light hyperparameter search using time-series-aware CV (`TimeSeriesSplit`)
- **Metrics:** MAE, RMSE, R2

## 8. Explainability
- Tree-based feature importance for Random Forest and XGBoost
- SHAP summary plot for the best model

## 9. Reproducibility
- Fixed `random_state=42`
- Pinned or minimum versions in `requirements.txt`
- Notebook must run top to bottom after "Restart and Run All"
