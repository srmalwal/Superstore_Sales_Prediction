# Superstore_Sales_Prediction

**Superstore Sales Prediction** is a machine learning project that estimates outlet sales from product and store characteristics. It includes a Jupyter Notebook for data preparation and model experimentation, a trained K-Nearest Neighbors (KNN) regression model, and a Streamlit dashboard for single and batch predictions.

The web interface is branded **RetailPulse AI — Super Store Sales Intelligence**.

## Features

- Predict estimated outlet sales for a product using store and product attributes.
- Interactive Streamlit dashboard with a dark-themed interface.
- Single-item sales prediction.
- Batch prediction by uploading a CSV file.
- Download batch predictions as a CSV file.
- View prediction summaries and a sales distribution chart.
- Explore model information through the Model Analytics section.

## Tech Stack

- **Language:** Python
- **Data processing:** Pandas, NumPy
- **Machine learning:** Scikit-learn
- **Web application:** Streamlit
- **Visualizations:** Plotly
- **Model persistence:** Pickle
- **Development:** Jupyter Notebook

## Dataset

The project uses `KNN_reg_outlet_sales.csv`, a retail outlet sales dataset. The target column is `Item_Outlet_Sales`.

The dataset includes fields such as:

- `Item_Weight`
- `Item_Fat_Content`
- `Item_Visibility`
- `Item_Type`
- `Item_MRP`
- `Outlet_Identifier`
- `Outlet_Establishment_Year`
- `Outlet_Size`
- `Outlet_Location_Type`
- `Outlet_Type`
- `Item_Outlet_Sales`

The notebook handles missing values, standardizes inconsistent item-fat-content labels, encodes categorical columns, and scales features during model experimentation.

## Machine Learning Model

The deployed application loads a saved **K-Nearest Neighbors Regressor**. The app's model configuration describes:

- **Number of neighbors (K):** 7
- **Distance parameter (`p`):** 1 (Manhattan distance)
- **Feature scaling:** `MinMaxScaler`

The notebook `KNN Regression(1).ipynb` contains data preprocessing, train/test splitting, regression experiments, hyperparameter search with `GridSearchCV` and `RandomizedSearchCV`, and evaluation using MAE, MSE, RMSE, and R².

Use the notebook outputs for the actual evaluation scores; this README does not claim a particular performance score.

## Repository Structure

```text
Superstore_Sales_Prediction/
├── app.py
├── KNN_reg_outlet_sales.csv
├── KNN Regression.ipynb
├── knn_regression_model.pkl
├── minmax_scaler.pkl
├── features.pkl
├── requirements.txt
└── README.md
```

The uploaded application file may have a timestamp in its filename. Rename it to `app.py` when adding it to the repository, or update the run command to match the filename. Likewise, rename `KNN Regression(1).ipynb` to `KNN Regression.ipynb` if you want to use the structure shown above.

## Installation

Use a compatible Python environment. Install the required packages:

```bash
pip install streamlit pandas numpy scikit-learn plotly jupyter
```

If you maintain a `requirements.txt`, list the packages above in that file. Check that the file contains package requirements rather than unrelated content before using `pip install -r requirements.txt`.

## Run the Application

Place the following files in the same project directory:

- `app.py`
- `knn_regression_model.pkl`
- `minmax_scaler.pkl`
- `features.pkl`

Then run:

```bash
streamlit run app.py
```

Open the local URL printed by Streamlit in your browser.

## How to Use

### Single Sales Prediction

1. Open the application.
2. Select **Single Sales Predictor** from the sidebar.
3. Enter the product and outlet details in the tabs.
4. Click **Calculate Estimated Sales**.
5. Review the estimated sales value and displayed summary.

### Batch Prediction

1. Select **Batch Prediction (CSV)**.
2. Upload a CSV containing all required feature columns.
3. Review the predicted sales and summary metrics.
4. Download the results using the CSV download button.

The uploaded CSV must contain every feature listed in `features.pkl`; the application reports missing required columns.

### Model Analytics

Select **Model Analytics** to view the model information and the feature-weightage-style chart provided by the application. Note that the current chart uses randomly generated values for its displayed scale factors, so it should not be interpreted as genuine model feature importance.

## Project Files

| File | Purpose |
|---|---|
| `app.py` | Streamlit dashboard and prediction logic |
| `KNN_reg_outlet_sales.csv` | Dataset used for model development |
| `KNN Regression.ipynb` | Data preprocessing, training experiments, tuning, and evaluation |
| `knn_regression_model.pkl` | Saved KNN regression model |
| `minmax_scaler.pkl` | Fitted feature scaler |
| `features.pkl` | Feature names and expected input order |
| `requirements.txt` | Python dependency list |
| `README.md` | Project overview and setup instructions |

## Important Notes

- The model, scaler, and feature list must be compatible with one another.
- For batch predictions, use the same feature names and preprocessing conventions as the training pipeline.
- Predictions are estimates based on the training data, not guaranteed future sales.
- Only load Pickle files from trusted sources.
- The uploaded file named `requirements.txt.txt` should be checked: its contents appear to be HTML rather than a Python package list. Create a proper `requirements.txt` before installing dependencies from it.

## Future Improvements

- Add model performance metrics to the dashboard using verified test-set results.
- Add stronger validation for missing or invalid input values.
- Replace the randomly generated analytics chart with meaningful analysis.
- Add feature-importance or feature-sensitivity analysis appropriate for the model.
- Compare KNN with other regression models using the same test split and metrics.
- Deploy the application to a hosting platform.

## Conclusion

`Superstore_Sales_Prediction` demonstrates a retail sales regression workflow, from dataset preprocessing and model experimentation to saved model artifacts and an interactive Streamlit application for single and batch sales predictions.
