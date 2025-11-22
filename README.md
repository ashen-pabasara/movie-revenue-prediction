# Movie Box Office Revenue Prediction

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-orange)
![XGBoost](https://img.shields.io/badge/Library-XGBoost-red)

## Project Overview
This project explores the application of machine learning techniques to predict the commercial success (box office revenue) of a movie before its release. Using metadata such as budget, genre, cast, and director, the model aims to provide financial forecasting for the entertainment industry.

## Data Collection
* **Source:** The Movie Database (TMDB) API.
* **Volume:** Metadata for approximately 10,000 movies.
* **Collection Method:** Custom Python script iterating through popularity lists.

## Repository Structure
| File Name | Description |
| :--- | :--- |
| `data_extractions.py` | Script used to fetch raw data from TMDB API. |
| `dataset_1_collected_data.csv` | The raw dataset obtained from the API. |
| `preprocessing.ipynb` | Notebook for cleaning data, handling outliers, and One-Hot Encoding features (Genre, Director, Cast). |
| `dataset_1_cleaned.csv` | The final preprocessed dataset used for training. |
| `model_training.ipynb` | Notebook containing the training logic for Random Forest, XGBoost, and Linear Regression. |
| `*.pkl` files | Serialized trained models ready for deployment. |

## Methodology
1.  **Data Cleaning:** Removed duplicates and zero-values for budget/revenue. Outliers were identified and removed.
2.  **Feature Engineering:**
    * Extracted release year and month.
    * Applied **One-Hot Encoding** to high-cardinality categorical features (Top 10 Actors, Directors, Production Companies).
3.  **Modeling:** Trained and evaluated three regression algorithms:
    * Random Forest Regressor
    * XGBoost Regressor
    * Linear Regression (Baseline)

## Results
The models were evaluated using **$R^2$ Score** and **RMSE** (Root Mean Squared Error). The **Random Forest Regressor** performed the best, capturing non-linear relationships effectively.

| Model | R² Score | RMSE |
| :--- | :--- | :--- |
| **Random Forest** | **0.7810** | **103 million** |
| XGBoost | 0.7593 | 108 million |
| Linear Regression | 0.7109 | 118 million |

> **Key Insight:** Budget was found to be the strongest predictor of revenue, followed by the presence of well-known actors and directors.

## How to Run
1.  **Install Dependencies:**
    ```bash
    pip install pandas numpy scikit-learn xgboost joblib requests
    ```
2.  **Data Collection (Optional):**
    Run `data_collection.py` (Requires your own TMDB API Key).
3.  **Preprocessing:**
    Run `preprocessing.ipynb` to generate the cleaned CSV.
4.  **Train Models:**
    Run `model_training.ipynb` to reproduce the results and generate `.pkl` files.
