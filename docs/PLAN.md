# PLAN: India AQI Analysis and Prediction

## Phases

### Phase 1: Setup + Cleaning
- Create project scaffold (figures/, docs/PLAN.md, notebook with section headings)
- Load data, inspect shape/dtypes/date range/cities/missing values
- Parse dates, sort by City/Date
- Drop Xylene (61% missing)
- Impute per city: ffill → bfill → city median
- Clip outliers via IQR method
- Document every decision

### Phase 2: EDA + Insights
- City-wise average AQI ranking (bar chart)
- Yearly AQI trend (line plot)
- Monthly/seasonal AQI pattern (heatmap or line)
- Pollutant correlation heatmap
- AQI bucket distribution
- COVID lockdown impact (Mar–Jun 2019 vs 2020)
- Delhi vs other cities seasonal pattern
- One-line takeaway under every chart

### Phase 3: Feature Engineering + Modeling
- Date features: year, month, day_of_week, season
- Per-city lag features (t-1, t-2, t-3) for AQI, PM2.5, PM10
- City label encoding
- Target: next-day AQI (shift within city group)
- Chronological train/test split (~80/20)
- Models: persistence baseline, Linear Regression, Random Forest, XGBoost
- Tuning with TimeSeriesSplit
- Results table: MAE, RMSE, R²
- Predicted vs actual plots

### Phase 4: Explainability + Wrap-up
- Feature importance chart
- SHAP summary plot for best model
- Conclusion, limitations, future work

### Phase 5: Deliverables
- requirements.txt (only imported libraries)
- README.md
- AshishSingh_ProjectReport.docx
