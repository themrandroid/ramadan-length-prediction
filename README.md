# Predicting the Length of Ramadan using Historical Data (1940–2024)

This project uses historical Hijri and Gregorian calendar data to build a machine learning model that predicts whether Ramadan will last **29 or 30 days**.

## Project Highlights

- Data scraped from [Wikipedia](https://en.wikipedia.org/wiki/Ramadan) and [Hijri.Habibur](https://hijri.habibur.com)
- Years covered: 1940–2024
- Full pipeline: Data Collection, Cleaning, EDA, Feature Engineering, Modeling, and Real-time Prediction
- Best model: **Logistic Regression** (Accuracy: 67%, F1 Score: 70%, ROC-AUC: 67%)
- Real-time prediction function that formats output clearly

## Technologies Used

- Python (Pandas, Matplotlib, Seaborn, Scikit-learn, XGBoost)
- Jupyter Notebook
- Web scraping: `requests`, `BeautifulSoup`

## Structure

- `ramadan_days_predictor.ipynb`: Main notebook
- `data/`: Raw CSV file scraped

## Future Plans

- Deploy as a small web app or automation bot
- Build a real-time version using Islamic calendar APIs

## License

This project is licensed under the MIT License.
