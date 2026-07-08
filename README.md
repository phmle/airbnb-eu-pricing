# airbnb-eu-pricing
Airbnb prices in some of the most popular European cities. Each listing is evaluated for various attributes such as room types, cleanliness and satisfaction ratings, bedrooms, distance from the city centre
### Project Objective

Analyze what drives Airbnb listing prices across Europe and build a model that predicts a listing's price from its characteristics (room type, capacity, location, host quality). The goal is to demonstrate a complete data analyze  workflow

### Dataset

Airbnb Prices in European Cities: (https://www.kaggle.com/datasets/thedevastator/airbnb-prices-in-european-cities) — 20 CSV files covering 10 cities, each split by `weekdays` / `weekends` pricing.

### Technologies Used

- Python: pandas, NumPy 
- Matplotlib / Seaborn: visualization
- scikit-learn: Linear Regression, Decision Tree, Random Forest, preprocessing pipelines, evaluation metrics
- Jupyter Notebook: reproducible, documented workflow

### Repository Structure

airbnb/
    data/                   #original 20 .csv files
        clean_data/
    img/                    #charts
    data_cleaning.ipynb
    eda_n_models.ipynb
    README.md


### Workflow

1. Data Understanding & Cleaning - loaded and combined all 20 raw files, reviewed the data dictionary, checked dtypes/missing values, dropped duplicates, fixed data types, and removed price outliers using the IQR rule to produce `airbnb_cleaned.csv`.
2. EDA & Machine Learning  15 charts covering price distribution, room type, city-level pricing, weekday/weekend effects, capacity/bedrooms, distance to centre, superhost effect, satisfaction/cleanliness, and correlations; then trained and compared Linear Regression, Decision Tree, and Random Forest regressors to predict price, evaluated with MAE/RMSE/R², plus predicted-vs-actual, feature importance, and residual plots.


### Key Findings

- Room type and unit size (bedrooms/capacity) are the dominant price drivers — entire homes/apartments consistently command the highest prices across all 10 cities.
  <img width="640" height="480" alt="price_vs_bedrooms" src="https://github.com/user-attachments/assets/04c1a3ae-0b28-45d4-9549-c374c76b2116" />

- Amsterdam and Paris are the most expensive cities on average; Athens and Budapest the most affordable.
- Distance to the city centre has a real but modest negative effect on price; attraction/restaurant proximity indices show weaker, noisier relationships.
  <img width="640" height="480" alt="price_vs_attraction_index" src="https://github.com/user-attachments/assets/74291609-b786-444d-8831-edb1bbff640b" />

- Superhost status, cleanliness, and guest satisfaction show little direct price effect in this dataset — most active listings are already highly rated, so these feature more as trust signals than pricing levers.
- Weekend prices are slightly higher than weekday prices on average, though the effect is modest compared to room type or city.


### Model Performance

Categorical features (room_type, city, price_period) one-hot encoded with pd.get_dummies
80/20 train/test split
Compares three models: Linear Regression, Decision Tree, and Random Forest
Evaluated with MAE, RMSE, and R²
<img width="295" height="127" alt="image" src="https://github.com/user-attachments/assets/a4e51631-00ca-4fdb-8a50-973cc46ae0b3" />
Random Forest performed best
Top features: room type (entire home/apt), person capacity, and distance to city centre.
<img width="836" height="531" alt="image" src="https://github.com/user-attachments/assets/78fda29b-089a-49b2-9381-07872769566a" />


### run

in bash:
pip install pandas numpy matplotlib seaborn scikit-learn jupyter

Run data_cleaning.ipynb first to produce airbnb_cleaned.csv.
Run eda_n_model.ipynb for the EDA charts and model training/evaluation.
