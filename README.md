# India AQI Analysis and Prediction

**Author:** Ashish Singh  
**Program:** IBM SkillsBuild Data Analytics with AI Academic Internship (BharatCares + AICTE)

## Overview
This project analyzes daily air quality data across 26 major Indian cities from 2015 to 2020. It uncovers seasonal trends, identifies the impact of the 2020 COVID-19 lockdown, and builds machine learning models to predict the next-day Air Quality Index (AQI).

## Dataset
- **Source:** [Kaggle - Air Quality Data in India (2015-2020)](https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india)
- **File Used:** `city_day.csv` (contains daily pollutant readings like PM2.5, PM10, NO2, etc., and the computed AQI).
- **Note:** The dataset is not included in the repository. Please download `city_day.csv` from Kaggle and place it in the `data/` directory.

## Project Description
The analysis follows a structured pipeline:
1. **Data Cleaning:** Handling missing values via per-city forward-filling, back-filling, and median imputation. Extreme outliers are clipped using the IQR method.
2. **Exploratory Data Analysis (EDA):** Visualizing city-wise pollution rankings, yearly trends, monthly seasonality (highlighting the severe winter smog in North India), and pollutant correlations.
3. **Insight Analysis:** Quantifying the improvement in AQI during the 2020 COVID-19 lockdown, and comparing Delhi's severe winter AQI spike against coastal cities.
4. **Feature Engineering:** Extracting date components, encoding categorical features, and computing past 3-day lags for AQI and key pollutants.
5. **Modeling:** Predicting next-day AQI using a chronological train/test split (Train: 2015-2019, Test: 2020).
6. **Explainability:** Interpreting model decisions using XGBoost feature importance and SHAP summary plots.

## Technologies Used
- Python 3.10+
- Jupyter Notebook
- pandas, numpy (Data Manipulation)
- matplotlib, seaborn (Visualization)
- scikit-learn, xgboost (Machine Learning)
- shap (Explainability)

## Setup and Run Instructions
1. Clone the repository and navigate to the project root (`india-aqi/`).
2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Download `city_day.csv` from Kaggle and place it in the `data/` folder:
   ```
   india-aqi/
   ├── data/
   │   └── city_day.csv
   ```
5. Launch Jupyter Notebook and run `AshishSingh_IndiaAQI_Prediction.ipynb` top-to-bottom:
   ```bash
   jupyter notebook
   ```

## Key Results
The machine learning models were evaluated on the 2020 test set to predict the next-day AQI. 

| Model | MAE | RMSE | R² |
|-------|-----|------|----|
| Persistence Baseline | 19.20 | 41.10 | 0.754 |
| Linear Regression | 18.60 | 37.34 | 0.797 |
| Random Forest | 16.78 | 34.14 | 0.830 |
| XGBoost | 19.98 | 37.19 | 0.799 |

**Random Forest** achieved the best performance, significantly outperforming the naive persistence baseline (where tomorrow's AQI is assumed to equal today's). Feature importance and SHAP analysis confirmed that today's AQI (`AQI`), yesterday's AQI (`AQI_lag1`), and the specific `City_Encoded` were the strongest predictors of tomorrow's air quality.
