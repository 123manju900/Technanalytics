# Technanalytics
# Data Preprocessing for Case Competition - Technanalytics, IIT Banaras

This markdown document outlines the data preprocessing steps performed as part of the **Technanalytics Case Competition** organized by **IIT Banaras**. The dataset was prepared for analysis by addressing missing values and combining relevant columns.

## 1. Imputation of Missing Values
The dataset contained some missing values in specific columns. These were handled using the following techniques:
- **Numerical Columns:** Missing values were imputed using statistical methods such as mean or median, depending on the distribution of the data.
- **Categorical Columns (if any):** Missing values were filled with the mode (most frequent value).

This ensured that the dataset was complete and ready for further analysis.

## 2. Concatenation of Date and Time Columns
The dataset initially had separate columns for `Date` and `Time (Local)`. These were combined into a single column named `Datetime` to streamline time-based analysis. The resulting column was formatted as `YYYY-MM-DD HH:MM:SS`, which is a standard datetime format suitable for analysis and visualization.

## 3. Dataset Overview Post-Processing
After preprocessing, the dataset includes:
- A new `Datetime` column that replaces the separate `Date` and `Time (Local)` columns.
- Cleaned data with no missing values, ensuring consistency and readiness for further steps like exploratory data analysis (EDA), feature engineering, and modeling.

This preprocessing is a critical step in preparing the dataset for delivering actionable insights as part of the competition requirements.
# Solution to Question 1: Highest Number of Completed Trips in a 24-Hour Period

This document outlines the steps taken to determine the highest number of completed trips within a 24-hour period as part of the **Technanalytics Case Competition** organized by **IIT Banaras**.

## Steps Followed

1. **Data Preparation**:
   - Preprocessed the dataset by imputing missing values and combining `Date` and `Time (Local)` into a single `Datetime` column for easier time-based analysis.

2. **Rolling Sum Calculation**:
   - Calculated the rolling sum of the `Completed Trips` column over a 24-hour window using the `rolling` function with a window size of 24 (assuming hourly data).
   - This provided a new column, `Rolling_24hr_Trips`, which represents the total number of completed trips for each hour, considering the previous 23 hours.

3. **Finding the Maximum**:
   - Identified the maximum value in the `Rolling_24hr_Trips` column to determine the highest number of completed trips within any 24-hour period.

4. **Result Extraction**:
   - Extracted the corresponding time period and value for reporting purposes.

## Outcome
The highest number of completed trips within a 24-hour period was successfully identified and is **248**. 

