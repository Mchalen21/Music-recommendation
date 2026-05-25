# Music Recommendation Algorithm

This project uses KMeans clustering to recommend songs based on a user's listening history. The dataset contains songs from 1950 to 2019 with lyrical feature scores.

## Project Structure

```
├── notebooks/
│   ├── 01_eda.ipynb           — Exploratory Data Analysis
│   ├── 02_preprocessing.ipynb — Data Cleaning & Scaling
│   ├── 03_modeling.ipynb      — KMeans Clustering
│   └── 04_prediction.ipynb    — Recommendations for New User
├── data/
│   └── recommend - recommend.csv  — Test dataset (user's listening history)
├── README.md
└── report.md
```

## How to Run

1. Place `train.csv` in the root project folder
2. Install dependencies: `pip install pandas numpy scikit-learn matplotlib seaborn`
3. Open and run the notebooks **in order** from the `notebooks/` folder

## Results

The model found 12 clusters based on lyrical themes. See `report.md` for the full write-up.
