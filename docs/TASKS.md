# TASKS: India AQI Analysis and Prediction

Work through phases in order. Mark each task done only when it runs cleanly and its output is visible in the notebook.

## Phase 0: Setup
- [ ] Create project folder structure (see ARCHITECTURE.md)
- [ ] Create virtual environment and install dependencies
- [ ] Download `city_day.csv` from Kaggle into `data/`
- [ ] Create notebook `AshishSingh_IndiaAQI_Prediction.ipynb` with section headings

## Phase 1: Data Loading and Cleaning
- [ ] Load data; print shape, dtypes, date range, number of cities
- [ ] Show missing-value percentage per column and decide what to drop or impute
- [ ] Parse dates and sort by City, Date
- [ ] Impute missing pollutant values per city (documented strategy)
- [ ] Handle outliers and document the approach
- [ ] Save a cleaned dataframe for later sections

## Phase 2: Exploratory Data Analysis
- [ ] City-wise average AQI ranking (bar chart)
- [ ] Yearly AQI trend, overall and for top cities
- [ ] Monthly/seasonal AQI pattern (heatmap or line chart)
- [ ] Pollutant correlation heatmap
- [ ] AQI bucket distribution
- [ ] Write a one-line takeaway under every chart

## Phase 3: Insight Analysis
- [ ] COVID lockdown impact: compare AQI for March-June 2020 vs the same months in 2019 (per city)
- [ ] Delhi vs other cities: seasonal comparison, highlighting winter spike
- [ ] Save key figures to `figures/`

## Phase 4: Feature Engineering
- [ ] Add date features (year, month, day of week, season)
- [ ] Add per-city lag features (t-1, t-2, t-3) for AQI, PM2.5, PM10
- [ ] Encode city
- [ ] Drop rows with NaNs created by lags
- [ ] Create next-day AQI target column

## Phase 5: Modeling
- [ ] Chronological train/test split
- [ ] Persistence baseline metrics
- [ ] Train Linear Regression
- [ ] Train Random Forest
- [ ] Train XGBoost
- [ ] Light tuning with `TimeSeriesSplit`
- [ ] Results table: MAE, RMSE, R2 for all models
- [ ] Predicted vs actual plot for best model (one or two cities)
- [ ] Optional: AQI bucket classifier with confusion matrix

## Phase 6: Explainability
- [ ] Feature importance chart
- [ ] SHAP summary plot for best model
- [ ] Short written interpretation

## Phase 7: Wrap-up in Notebook
- [ ] Conclusion, limitations, future work sections
- [ ] Restart kernel and Run All; confirm no errors
- [ ] Clear stray debug cells

## Phase 8: Submission Files
- [ ] `AshishSingh_IndiaAQI_Prediction.ipynb` final and named correctly
- [ ] `requirements.txt` generated and tested in a fresh environment
- [ ] `README.md` written: overview, dataset link, description, technologies, setup and run instructions, key results
- [ ] `AshishSingh_ProjectReport.docx` written: title page, abstract, introduction, dataset, methodology, results with figures, conclusion, references
- [ ] Final check: all four files present, names exactly as required
