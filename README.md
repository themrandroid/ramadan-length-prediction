# Predicting the Length of Ramadan (1940–2024)

A reproducible data-science project that uses historical Hijri and Gregorian calendar data to predict whether a given Ramadan will last 29 or 30 days. The project includes data collection (web scraping), cleaning, exploratory analysis, feature engineering, and model evaluation. The final deliverable is a trained classifier (Logistic Regression selected) and a small prediction routine.


Project overview
This repository demonstrates a complete machine-learning pipeline for a binary classification problem: predicting Ramadan length (29 vs 30 days) using historical calendar features (start month/day, Sha'ban length, and year). The notebook contains scraping code for data collection and multiple model experiments; the best-performing, simplest model (Logistic Regression) was chosen for final predictions.

Key results
- Best model: Logistic Regression
- Reported evaluation (notebook): Accuracy ≈ 61%, F1 ≈ 63%, ROC-AUC ≈ 61%
- Confusion matrix and model comparisons are recorded in the main notebook.

Dataset
- Primary CSV: [data/Ramadan_Length_Prediction_data.csv](data/Ramadan_Length_Prediction_data.csv) — historical records from 1940 to 2024 (Hijri Year, Gregorian Year, Ramadan start month/day, Sha'ban length, Ramadan length).

How it works
1. Data collection: scrape dates and month lengths from Wikipedia and hijri.habibur.com.
2. Cleaning: parse and merge scraped tables, convert month lengths to numeric, filter year range.
3. Features: Start_Month, Start_Day, Year, Sha'ban_Length (Hijri_Year dropped to avoid multicollinearity).
4. Target encoding: Ramadan_Length encoded as binary (1 => 29 days, 0 => 30 days).
5. Modeling: train/test split, scale features, train several classifiers (Logistic Regression, Decision Tree, Random Forest, Gradient Boosting, XGBoost).
6. Evaluation: accuracy, F1, ROC-AUC, confusion matrix. Logistic Regression selected based on balanced performance.

Reproducing the analysis
Prerequisites
- Python 3.8+; recommended packages: pandas, numpy, scikit-learn, matplotlib, seaborn, xgboost, requests, beautifulsoup4

Install (example)
```
pip install pandas numpy scikit-learn matplotlib seaborn xgboost requests beautifulsoup4
```

Run
- Open and run the notebook: [ramadan_days_predictor.ipynb](ramadan_days_predictor.ipynb) in Jupyter or VSCode.
- The notebook performs entire pipeline and saves/reads the CSV at [data/Ramadan_Length_Prediction_data.csv](data/Ramadan_Length_Prediction_data.csv).

Notable implementation details (symbols referenced in the notebook)
- main dataframe: [`df`](ramadan_days_predictor.ipynb) — merged and cleaned dataset used for modeling.
- trained logistic model: [`logistic_regression`](ramadan_days_predictor.ipynb) — final selected classifier.
- scaled train/test arrays: [`X_train_scaled`](ramadan_days_predictor.ipynb), [`X_test_scaled`](ramadan_days_predictor.ipynb).
- example prediction input: [`prediction_df`](ramadan_days_predictor.ipynb) — a sample row used to demonstrate a 2025 prediction.

File structure
- [ramadan_days_predictor.ipynb](ramadan_days_predictor.ipynb) — primary Jupyter notebook with all code, EDA, modeling, and results.
- [data/Ramadan_Length_Prediction_data.csv](data/Ramadan_Length_Prediction_data.csv) — processed dataset used by the notebook.
- [README.md](README.md) — this file.

Limitations
- Small dataset (≈ 85 observations) limits model generalization.
- Dataset contains rare anomalies (years with two Ramadans) which can affect some model behaviors.
- The model uses historical calendar patterns only; it does not ingest live astronomical data or regional moon-sighting reports.

Future work
- Integrate astronomical APIs to improve accuracy.
- Add cross-validation and probabilistic calibration.
- Deploy a lightweight web service that serves predictions and uncertainty estimates.

License
This project is licensed under the MIT License. See the repository for full terms.

Author
Muhammed Abdulrasheed — contact via the repository profile.
