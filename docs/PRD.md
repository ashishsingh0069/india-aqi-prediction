# PRD: India AQI Analysis and Prediction

## 1. Overview
A data analytics and machine learning project that analyzes air quality across major Indian cities (2015-2020) and builds models that predict the Air Quality Index (AQI). Submitted as the project for the **IBM SkillsBuild Data Analytics with AI Academic Internship Program** (BharatCares, in association with AICTE).

- **Author:** Ashish Singh
- **Project name:** India AQI Analysis and Prediction
- **Primary deliverable:** a single Jupyter Notebook, plus requirements, report and README

## 2. Problem Statement
Air pollution in Indian cities is severe and varies sharply by city and season. Raw pollutant readings are hard to interpret and contain many gaps. This project cleans the data, finds patterns in it, and builds predictive models so that pollution levels can be understood and anticipated.

## 3. Goals
1. Clean and prepare the city-level daily air quality dataset.
2. Run exploratory analysis that produces clear, evidence-backed insights (city ranking, seasonality, pollutant relationships, 2020 lockdown effect).
3. Build and compare ML models for AQI prediction.
4. Explain model behavior (feature importance, SHAP) so results are interpretable.
5. Deliver all four required submission files, correctly named and complete.

## 4. Non-Goals
- No real-time data ingestion or live API integration.
- No web app or deployment (an optional Streamlit demo is out of scope unless time remains).
- No deep-learning forecasting as a requirement (LSTM/Prophet is optional stretch only).

## 5. Dataset
- **Source:** Kaggle, "Air Quality Data in India (2015-2020)"
- **File used:** `city_day.csv` (daily, city-level)
- **Key columns:** City, Date, PM2.5, PM10, NO, NO2, NOx, NH3, CO, SO2, O3, Benzene, Toluene, Xylene, AQI, AQI_Bucket
- The dataset is not committed to the repo. The README links to it and explains where to place the file.

## 6. Users / Audience
- Internship evaluators reviewing the notebook, report and README.
- Anyone reproducing the analysis from the README.

## 7. Functional Requirements
| ID | Requirement |
|----|-------------|
| FR1 | Load data and summarize structure, dtypes, date range, missing values |
| FR2 | Clean data: parse dates, handle missing values per column with a documented strategy, treat outliers |
| FR3 | EDA: city-wise average AQI ranking, yearly/monthly/seasonal trends, pollutant correlation heatmap, AQI bucket distribution |
| FR4 | Insight analysis: (a) impact of the 2020 COVID lockdown on AQI, (b) Delhi vs other cities seasonal pattern |
| FR5 | Feature engineering: date features (month, season, day of week), lag features (previous-day AQI and pollutants), city encoding |
| FR6 | Model training: baseline plus at least three models (Linear Regression, Random Forest, XGBoost) |
| FR7 | Evaluation: MAE, RMSE, R2 on a time-based test set, with a results comparison table and prediction-vs-actual plots |
| FR8 | Explainability: feature importance and SHAP summary plot for the best model |
| FR9 | Optional: AQI bucket classification (Good to Severe) with confusion matrix |
| FR10 | Conclusions and limitations section in the notebook |

## 8. Success Metrics
- Notebook runs top to bottom without errors on a clean environment.
- Best model clearly beats the baseline on the test set, with metrics reported.
- At least 5 distinct, labeled visualizations that each support a stated insight.
- All four submission files present and correctly named.

## 9. Deliverables
| File | Format | Required name |
|------|--------|---------------|
| Code | .ipynb | `AshishSingh_IndiaAQI_Prediction.ipynb` |
| Dependencies | .txt | `requirements.txt` |
| Report | .docx | `AshishSingh_ProjectReport.docx` |
| README | .md | `README.md` |

## 10. Constraints
- Runs on a normal laptop (dataset is small).
- Python 3.10+; libraries limited to those in `requirements.txt`.
- Notebook must be reproducible (fixed random seeds).

## 11. Risks and Mitigations
| Risk | Mitigation |
|------|------------|
| Many missing values in some cities/pollutants | Document strategy; drop columns with excessive missingness (e.g., Xylene) rather than imputing blindly |
| AQI is computed from pollutants, so same-day prediction can look artificially accurate | Make next-day AQI prediction (lag features) the primary task, and state this clearly in the report |
| Random train/test split leaks future info in time series | Use a chronological split |
| Uneven data coverage across cities | Report city coverage; consider restricting to cities with sufficient data |
