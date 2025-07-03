# SIP Inflow Forecasting

## Overview

This project provides a time series analysis and forecasting tool for Systematic Investment Plan (SIP) inflows in crores, covering the period from 2016 to 2025, with projections extending to 2028. The analysis is implemented in a Jupyter Notebook (`SIP_Forecast.ipynb`) using the Prophet library for forecasting. The notebook includes data preprocessing, visualization, decomposition, and forecasting using both linear and logistic growth models, along with performance evaluation using cross-validation and mean absolute error (MAE) metrics.

## Objectives

- **Data Preprocessing**: Load and clean SIP inflow data, handling missing values and converting dates for time series analysis.
- **Exploratory Analysis**: Visualize monthly SIP inflows and decompose the time series into trend and seasonal components.
- **Forecasting**: Apply Prophet's linear and logistic growth models to predict future SIP inflows.
- **Model Evaluation**: Assess model performance using cross-validation and MAE metrics.
- **Comparison**: Compare the performance of linear and logistic models for December 2025 predictions.

## Repository Structure

- `SIP_Forecast.ipynb`: Jupyter Notebook containing the complete analysis and forecasting pipeline.
- `sip_data.csv`: Input dataset containing historical SIP inflow data (not included in the repository; users must provide their own data).
- `sip_forecast_2028.csv`: Dataset used for forecasting (not included; users must provide or generate this file).
- `README.md`: This file, providing an overview and instructions for the project.

## Dependencies

To run the notebook, the following Python packages are required:

- `pandas`: For data manipulation and analysis.
- `matplotlib`: For data visualization.
- `statsmodels`: For time series decomposition.
- `prophet`: For time series forecasting.
- `scikit-learn`: For calculating mean absolute error.

You can install the dependencies using pip:

```bash
pip install pandas matplotlib statsmodels prophet scikit-learn
```

## Usage

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/sip-forecasting.git
   cd sip-forecasting
   ```

2. **Prepare the Data**:
   - Ensure you have the `sip_data.csv` file with columns `Month`, `Year`, and `SIP_Inflow_Crores`.
   - Optionally, provide `sip_forecast_2028.csv` with either Prophet output format (columns `ds`, `yhat`) or raw data format (columns `Date`, `SIP_Inflow_Crores`).
   - Place these files in the project directory or update the file paths in the notebook.

3. **Run the Notebook**:
   - Launch Jupyter Notebook:
     ```bash
     jupyter notebook SIP_Forecast.ipynb
     ```
   - Execute the cells sequentially to perform data loading, preprocessing, visualization, and forecasting.

4. **Key Outputs**:
   - Visualizations of monthly SIP inflows and their trend/seasonal decomposition.
   - Cross-validation results with MAE for linear and logistic models.
   - Forecasted SIP inflows for December 2025 using both models.
   - Comparison of MAE between linear and logistic models on the provided dataset.

## Methodology

- **Data Preprocessing**:
  - The dataset is loaded from `sip_data.csv`, and the `Date` column is created by combining `Month` and `Year` into a datetime format.
  - Missing values in `SIP_Inflow_Crores` are handled using forward fill.
  - The data is sorted by date and set as the index for time series analysis.

- **Visualization and Decomposition**:
  - A line plot displays the monthly SIP inflows from 2016 to 2025.
  - Seasonal decomposition is performed using an additive model with a 12-month periodicity to identify trend and seasonal components.

- **Forecasting**:
  - Two Prophet models (linear and logistic growth) are trained on the data from `sip_forecast_2028.csv`.
  - The logistic model uses a capacity cap of 50,000 crores.
  - Predictions are made for December 31, 2025, and compared.

- **Evaluation**:
  - Cross-validation is conducted with an initial training period of 1825 days, a period of 180 days, and a forecast horizon of 365 days.
  - Performance metrics, specifically MAE, are calculated to evaluate model accuracy.
  - In-sample MAE is computed to compare the fit of linear and logistic models.

## Results

- **Cross-Validation**:
  - Linear Model MAE: 1857.93 crores
  - Logistic Model MAE: 1995.86 crores
- **In-Sample MAE**:
  - Linear Model MAE: 2.21 crores
  - Logistic Model MAE: 7.25 crores
- **December 2025 Forecast**:
  - Linear Model: 22942.29 crores
  - Logistic Model: 22942.31 crores

The linear model generally outperforms the logistic model based on lower MAE values, indicating better predictive accuracy for this dataset.

## Notes

- The datasets (`sip_data.csv` and `sip_forecast_2028.csv`) are not included in the repository due to their proprietary nature. Users must provide their own data with the specified structure.
- The logistic model assumes a capacity cap of 50,000 crores, which may need adjustment based on domain knowledge or additional data.
- The notebook assumes a Python environment with the required dependencies installed. Ensure compatibility with Python 3.x.

## Contributing

Contributions to improve the analysis, add new features, or enhance documentation are welcome. Please submit a pull request or open an issue on GitHub to discuss proposed changes.
