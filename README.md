# S&P 500 Historical Data Analysis and Prediction

This repository contains a Jupyter Notebook that analyzes historical data for the S&P 500 stock market index and builds a predictive model to forecast future closing prices. The code uses Yahoo Finance data and applies a RandomForestClassifier from scikit-learn to predict whether the closing price will be higher the next day.

## Table of Contents
- [Introduction](#introduction)
- [Data Collection](#data-collection)
- [Data Preprocessing](#data-preprocessing)
- [Model Training](#model-training)
- [Backtesting](#backtesting)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Introduction
This project aims to predict the movement of the S&P 500 index using historical data and machine learning techniques. The primary focus is on determining if the closing price of the S&P 500 will increase the next day.

## Data Collection
The data is fetched from Yahoo Finance using the `yfinance` package. The historical data for the S&P 500 is retrieved for the maximum available period.

## Data Preprocessing
1. **Loading Data**:
   - The S&P 500 historical data is loaded into a DataFrame.
   - The index of the DataFrame is set to the date of each record.

2. **Feature Engineering**:
   - A new column 'Tomorrow' is created to store the closing price of the next day.
   - A 'Target' column is added to indicate if the closing price will be higher the next day (1 for true, 0 for false).

3. **Data Filtering**:
   - The data is filtered to include records from January 1, 1990, to December 31, 2021.

4. **Rolling Averages and Trends**:
   - Rolling averages and trends are calculated for different horizons (2, 5, 60, 250, 1000 days).
   - New predictor columns are added based on these calculations.

5. **Handling Missing Values**:
   - Rows with missing values are removed from the dataset.

## Model Training
A `RandomForestClassifier` is used to train the model. The predictors include 'Close', 'Volume', 'Open', 'High', 'Low', and the newly engineered features.

### Training Steps:
1. Split the data into training and testing datasets.
2. Fit the model using the training data.
3. Make predictions on the test data.
4. Evaluate the model using precision score.

## Backtesting
The backtesting function iterates through the data in steps, training and testing the model on specified predictors. It returns concatenated predictions from each iteration for further analysis.

## Usage
To run the code, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/sp500-prediction.git
   cd sp500-prediction
   ```

2. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

4. Open `sp500_prediction.ipynb` and run the cells sequentially.

## Results
- The precision score and the proportion of true 'Target' values in the predictions dataset are calculated.
- The model's predictions and the actual target values are plotted for visual analysis.

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request or open an Issue if you have any suggestions or improvements.

## License
This project is licensed under the MIT License.
