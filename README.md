# Sales Data Analysis and Weather Prediction

This project focuses on analyzing sales data for 111 products sold at 45 different Walmart locations, and predicting daily sales figures and rainy days based on weather data. The project utilizes various data preprocessing techniques, machine learning models, and data visualization to gain insights and make predictions.

## Data Sources

The project uses three datasets:

1. `sales.csv`: Contains sales data for 111 products sold at 45 different Walmart locations from January 2012 to October 2014.
2. `key.csv`: Indicates the weather station associated with each store.
3. `weather.csv`: Contains daily weather data for each weather station.

## Data Exploration and Visualization

The data exploration and visualization phase involved creating informative plots and tables to gain insights into the data. Some key findings include:

- The number of stores associated with each weather station varies.

<img width="261" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/e1b0434c-eba5-4391-b3d8-9b5181b96131">

- Average monthly sales per year show seasonal patterns and variations across different years.

<img width="468" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/8a714df7-1d85-48e1-a2bc-ce513d44e7d1">

- Scatter plots of units sold against weather variables like snowfall, maximum temperature, and minimum temperature reveal weak relationships between sales and weather variables.

<img width="252" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/23ba9fa0-94b5-487d-a021-48ce25969e36">
<img width="256" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/b88ab52e-44f1-4456-b18b-de0f4b2b7f3f">
<img width="252" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/54b8b2ca-0a1c-4eed-b7e1-624dddad7d6f">


The weak correlations observed in the scatter plots suggest that there might not be a strong direct relationship between sales and individual weather variables. This could indicate that the relationship between sales and weather is more complex and may involve interactions between multiple variables.

## Data Preprocessing

The data preprocessing phase involved several steps:

1. **Handling Missing Values**: Columns with more than 50% missing values were dropped, and the remaining missing values were imputed using the K-Nearest Neighbors (KNN) algorithm.

2. **Outlier Detection and Removal**: Outliers in the 'units' feature were identified using the Interquartile Range (IQR) method and removed from the dataset.

<img width="286" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/3b1cd783-2f58-4eb1-93ec-19281f976ddb">
<img width="288" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/4b6990f5-45a5-487c-a495-8ac174c102dd">

3. **Feature Engineering**: Additional features like day of the week, day, month, and year were extracted from the date column.

4. **Merging Datasets**: The sales, key, and weather datasets were merged based on store and date information.

## Unit Sales Prediction

To predict the daily sales figures of the sum of units sold for products 5, 6, 9, 16, and 45 (key_sum) per store, two machine learning models were used: Gradient Boost Regressor and Decision Tree Regressor. The models were trained on data from 2012-2013 and tested on data from 2014.

- **Gradient Boost Regressor**: The model achieved an MSE of 959.98 before parameter tuning and 991.66 after tuning using GridSearchCV.

- **Decision Tree Regressor**: The model achieved an MSE of 1835.20 before parameter tuning and 1757.07 after tuning using GridSearchCV.
<img width="281" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/b32fe945-7d9f-422e-9a0e-ae1718b66869">
<img width="287" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/a3bcf670-d5f4-4eaa-a8d5-966471fdc0a1">
</br>
<img width="281" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/773f1d8d-b973-4f2d-839d-75fb0b1d2ae9">
<img width="284" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/0dd4d5d9-1ca0-472e-8805-99c037dac9a1">

The prediction plots indicate that both models struggle to capture the full range of variability in the sales data, with predictions clustering around the mean. This suggests that the models might be underfitting the data and that there could be other important factors influencing sales that are not captured in the current feature set.

Feature importance analysis was conducted for both models to identify the most influential variables in predicting unit sales. The results show that weather-related features have relatively low importance compared to other features like store and item information.
<img width="314" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/796ba2fd-0d63-4cbf-831a-f40decd70d9e">
<img width="310" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/8f61fbe1-a2f9-449e-b420-78ee837cf187">

<img width="310" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/8eac8afc-589b-4dec-b40c-842a9d5a5121">
<img width="310" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/3fb93624-8825-4499-b6d8-08742ef08424">


## Rainy Day Prediction

To predict whether it rained or not for store number 11 on a given day, two machine learning models were used: AdaBoost Classifier and Random Forest Classifier. The models were trained on data from 2012-2013 and tested on data from 2014.

- **AdaBoost Classifier**: The model achieved an accuracy of 0.602, sensitivity of 0.705, and specificity of 0.504 after parameter tuning using GridSearchCV.

<img width="160" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/c9de14d3-ab14-4f1a-8a8e-ab1b3856ad31">
<img width="211" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/dc75936a-69f2-4aec-b599-c53410df436b">

- **Random Forest Classifier**: The model achieved an accuracy of 0.606, sensitivity of 0.557, and specificity of 0.654 after parameter tuning using RandomizedSearchCV.

<img width="160" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/59a69dc0-315d-4115-9a4f-4fcbe31a75c5">
<img width="261" alt="image" src="https://github.com/mlk500/ML-Walmart-data/assets/57171298/551e031e-53b8-4503-bad0-00b8a23d98f6">

Confusion matrices and feature importance analysis were used to evaluate and interpret the model results. Both models show moderate performance in predicting rainy days, with the AdaBoost classifier having higher sensitivity (better at predicting rainy days) and the Random Forest classifier having higher specificity (better at predicting non-rainy days).

The feature importance analysis reveals that temporal features like day, month, and day of the week are more influential in predicting rainy days compared to sales-related features. This suggests that there might be seasonal patterns in rainfall that the models are capturing.

## Repository Structure

- `data/`: Contains the raw and preprocessed datasets.
- `notebooks/`: Jupyter notebooks used for data exploration, preprocessing, modeling, and analysis.
- `plots/`: Generated plots and visualizations.
- `README.md`: Overview of the project, methodology, and findings.

## Dependencies

- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

## Acknowledgements

This project was completed as part of the Machine Learning course at the University of Haifa. The dataset used in this project was obtained from [Walmart Recruiting - Sales in Stormy Weather](https://www.kaggle.com/competitions/walmart-recruiting-sales-in-stormy-weather/data).
