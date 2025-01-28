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
   ## Outcome
The highest number of completed trips within a 24-hour period was successfully identified and is **248**.

# Solution to Question: Percentage of Zeroes Occurring on Weekends

This document outlines the steps taken to calculate the percentage of all zeroes during the two-week period that occurred on weekends (defined as Friday at 5 PM to Sunday at 3 AM). 

## Steps Followed

1. **Filter Weekend Data**:
   - Extracted rows where the `Datetime` falls between Friday at 5 PM and Sunday at 3 AM for each week in the dataset.
   - Counted the number of zeroes (`Weekend Zeroes`) in this filtered weekend data.

**Calculate Percentage**:
   - Computed the percentage of weekend zeroes using the formula:
     ```
     Percentage of Weekend Zeroes = (Weekend Zeroes / Total Zeroes) * 100
     ```

## Results
- **Total Zeroes**: 1429  
- **Weekend Zeroes**: 641  
- **Percentage of Weekend Zeroes**: 44.86%
## Question 3: Weighted Average Ratio of Completed Trips Per Driver

### Steps Followed:
1. **Calculate Total Trips and Drivers**:
   - Aggregated the total number of `Completed Trips` and `Unique Drivers` for each hour over the two-week period.
   
2. **Compute Weighted Average**:
   - Used the formula:
     ```
     Weighted Average Ratio = (Sum of (Completed Trips * Unique Drivers)) / (Sum of Unique Drivers)
     ```
   - This ensures that hours with more drivers are weighted appropriately in the calculation.

### Result:
- **Weighted Average Ratio**: 0.515

---

## Question 4: Busiest 8-Hour Shift Based on Unique Requests

### Steps Followed:
1. **Aggregate Data into 8-Hour Shifts**:
   - Divided the dataset into consecutive, non-overlapping 8-hour shifts starting at midnight, 8 AM, and 4 PM each day.
   - Calculated the total `Unique Requests` for each shift.

2. **Identify Busiest Shift**:
   - Compared the total `Unique Requests` across all shifts to find the one with the highest value.
![image](https://github.com/123manju900/Technanalytics/blob/d8c2d6bd79ec3c6baf5cee828f0651356f85cdaf/plots/Q4.png)

### Result:
- **Busiest Shift**: The busiest 8-hour shift is from **4 PM to midnight**, based on unique requests over the two-week period.
## Question 5: True or False - Driver Supply Always Increases When Demand Increases?

### Steps Followed:
1. **Visualize Supply vs. Demand**:
   - Plotted a time-series graph comparing `Unique Requests` (demand) and `Driver Supply` over the two-week period.
   - Analyzed trends to identify instances where supply did not increase with demand.

2. **Identify Exceptions**:
   - Highlighted specific time periods where:
     - Requests spiked, but driver supply did not increase proportionally.
     - Driver supply exceeded requests.

### Result:
- **Answer**: False  
  There were instances, such as on **11th September**, where driver supply was higher than requests, and times when requests spiked but supply did not increase proportionally.

---

## Question 6: In Which 72-Hour Period is the Ratio of Zeroes to Eyeballs the Highest?

### Steps Followed:
1. **Calculate Ratios for Rolling 72-Hour Periods**:
   - Used a rolling window of 72 hours to compute the ratio of `Zeroes` (unsuccessful requests) to `Eyeballs` (total requests).
   - Stored the ratio for each rolling period.

2. **Identify Maximum Ratio**:
   - Found the maximum ratio and recorded the corresponding start time of the 72-hour period.
   ![image](https://github.com/123manju900/Technanalytics/blob/d8c2d6bd79ec3c6baf5cee828f0651356f85cdaf/plots/Q6.png)

### Result:
- **Answer**: The highest ratio of Zeroes to Eyeballs is `{max_ratio:.2f}`, occurring during the 72-hour period starting at `{max_ratio_time}`.

---

## Question 7: If You Could Add 5 Drivers to Any Single Hour of Every Day, Which Hour Should You Add Them To?

### Steps Followed:
1. **Calculate Driver Shortages**:
   - For each hour of the day, calculated the total shortage of drivers (i.e., `Unique Requests` minus `Driver Supply`) over the two-week period.

2. **Identify Hour with Maximum Shortage**:
   - Found the hour with the highest cumulative shortage across all days.

3. **Simulate Adding Drivers**:
   - Simulated adding 5 drivers to this hour daily and recalculated shortages to confirm improvement.
   ![image](https://github.com/123manju900/Technanalytics/blob/d8c2d6bd79ec3c6baf5cee828f0651356f85cdaf/plots/Q7.png)

### Result:
- **Answer**: The best hour to add 5 drivers is **23:00**, with a total shortage of 65 drivers over two weeks.

---

## Question 8: Best Hour to Add Drivers Based on Total Shortage

### Steps Followed:
1. **Analyze Hourly Shortages**:
   - Similar to Question 7, analyzed hourly shortages across all days during the two-week period.

2. **Determine Optimal Hour**:
   - Identified the hour with the maximum cumulative shortage and confirmed it as the best hour for adding drivers daily.
![image](https://github.com/123manju900/Technanalytics/blob/d8c2d6bd79ec3c6baf5cee828f0651356f85cdaf/plots/Q8.png)
### Result:
- **Answer**: The best hour to add 5 drivers is **23:00**, with a total shortage of 65 drivers over two weeks.


4. **Result Extraction**:
   - Extracted the corresponding time period and value for reporting purposes.

 

