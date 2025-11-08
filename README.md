# Energy Efficiency Prediction

This project uses an XGBoost regression model to predict the **Heating Load** and **Cooling Load** of residential buildings based on their physical characteristics.

The model is built and evaluated in the `engery_efficiency_prediction.ipynb` Jupyter Notebook.

## 📈 Dataset

This project uses the **Energy Efficiency** dataset from the UCI Machine Learning Repository (`ENB2012_data.xlsx`).

* **Instances:** 768
* **Features (X):** 8 features describing the building, such as `relative_compactness`, `surface_area`, `wall_area`, `roof_area`, and `glazing_area`.
* **Targets (y):** 2 continuous variables: `heating_load` and `cooling_load`.

## 🛠️ Approach

1.  **Data Loading & EDA:** The data is loaded, and a correlation heatmap is generated to understand feature relationships.
2.  **Preprocessing:** A `ColumnTransformer` is used to:
    * **Standardize** numerical features (e.g., `surface_area`).
    * **One-hot encode** categorical features (`orientation` and `glazing_area_distribution`).
3.  **Modeling:**
    * An `XGBRegressor` is used as the base estimator.
    * `MultiOutputRegressor` is wrapped around the XGBoost model to predict both target variables (Heating and Cooling Load) simultaneously.
    * The entire process (preprocessing and modeling) is streamlined using a Scikit-learn `Pipeline`.
4.  **Evaluation:** The model is trained on 80% of the data and evaluated on the 20% test set.

## 📊 Results

The model performs with high accuracy on the unseen test data:

* **R² Score:** 0.990
* **Mean Absolute Error (MAE):** 0.527
* **Root Mean Squared Error (RMSE):** 0.970

The notebook also includes visualizations for feature importance and a scatter plot of actual vs. predicted values.

## 🚀 How to Run

1.  Ensure you have Python 3 installed.
2.  Install the required libraries:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn xgboost
    ```
3.  You will also need a library to read Excel files:
    ```bash
    pip install openpyxl
    ```
4.  Open and run the Jupyter Notebook `engery_efficiency_prediction.ipynb`.
