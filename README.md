# Campus Water Infrastructure: Predictive Modelling & Sensor Health

## Project Overview

This project analyses historical campus water data using Python and machine learning. The data is cleaned, combined, and prepared to predict the next day's water volume and water pressure. The project also includes a sensor health check to identify water meters that may be inactive or unreliable.

The project was developed using Python, pandas, NumPy, scikit-learn, matplotlib, and Jupyter Notebook.

## Project Objectives

The main objectives of this project are to:

* Load and combine water volume and pressure data from multiple CSV files.
* Clean and prepare the data for analysis.
* Create new features to improve machine learning predictions.
* Train Random Forest models to predict the next day's water volume and water pressure.
* Evaluate the performance of the models.
* Check the health of the water meters using historical sensor readings.

## Dataset

The project uses historical water data collected from the Central University of Technology (CUT) campus.

The dataset includes:

* 545 water volume CSV files.
* 395 water pressure CSV files.
* Data collected from multiple campus water meters.
* Hourly measurements that were converted into daily values for analysis.

## Project Workflow

The project follows these main steps:

1. Import the required Python libraries.
2. Load the water volume and pressure data.
3. Clean the data and convert the dates.
4. Combine the datasets into one dataset.
5. Create time, lag, and rolling average features.
6. Train Random Forest regression models.
7. Evaluate the models using MAE and RMSE.
8. Compare feature importance.
9. Compare actual and predicted water volume.
10. Check the health of the water meters.

## Machine Learning

Two Random Forest regression models were developed.

* The first model predicts the next day's total water volume.
* The second model predicts the next day's average water pressure.

The models were evaluated using:

* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)

## Results

The project successfully:

* Predicted the next day's water volume and water pressure using Random Forest models.
* Compared feature importance to identify the most useful input data.
* Compared actual and predicted water volume.
* Identified active, partially active, and inactive water meters using historical sensor readings.

## Sensor Health Check

The project includes a sensor health check based on historical meter readings.

Each water meter is classified as:

* **Active** – regularly records non-zero values.
* **Partially Active** – records zero values more frequently.
* **Inactive (Dead Sensor)** – only records zero values.

This helps identify meters that may require maintenance or further investigation.

## Technologies Used

* Python
* pandas
* NumPy
* scikit-learn
* matplotlib
* Jupyter Notebook

## Repository Contents

* `Water_Usage_Analysis.ipynb` – Main project notebook
* `README.md` – Project documentation

## Skills Demonstrated

This project demonstrates skills in:

* Data cleaning
* Data preparation
* Feature engineering
* Time-based feature engineering
* Machine learning
* Model evaluation
* Data visualisation
* Sensor health analysis

## Author

**Monica Tenene**

BTech in Computer Systems Engineering

GitHub: @tenenem
