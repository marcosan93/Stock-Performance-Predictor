# Stock Predictor
#### Predicting if a stock will rise by 5% or more in its next quarter based on fundamental data
Marco Santos

## Table of Contents
  * [Data](#Data)
  * [Data Exploration](#Exploring)
  * [Modeling](#Modeling)
  * Results/Recommendations
  * Improvements
  * Conclusion
  
## Data

The main source of data was retrieved from [Stockpup.com](http://www.stockpup.com/data/).
  * Data was downloaded from 765 different csv files.
  * Webscraping was implemented in order to automate the download process: [Retrieving Data](Retrieving_Data.ipynb).
  * Each csv file was saved as a separate Pandas DataFrame and stored in a dictionary which was pickled for later use.
  
### [Data Formatting, Cleaning, and Organizing](Cleaning_Original_Data.ipynb)

Throughout most of the process, until all the Pandas DataFrames were combined, many functions were applied by iterating through the dictionary storing each stock's unique dataframe.

__Cleaning/Formatting the Data__:
1. Index of the DataFrame was set to the dates.
2. All values containing the word "None" and the value "0" were replaced with NaN.
3. All values were then converted to numeric values.
4. NaN were then filled using `bfill()`.  This was done so the last reported values become the most recent. Future NaNs remained.
5. Functions were written to create a new column containing whether or not the price increased by >5% in the upcoming quarter and to create new features showing the percent increase/decrease from previous quarters.
6. First and last rows were removed.  The first row could not contain the information on the stock's future movement and the last row had no data in the past to compare.
7. Finally, all DataFrames in the dictionary were combined into one large DataFrame.

__Final DataFrame__:
1. All NaN values were removed.
2. Remaining values were multiplied by 100 and rounded to two decimal places.
3. Columns/features containing less than 500 unique values were removed because they did not contain enough information.
4. True and False classes were then balanced so they both had equal representation in the DataFrame.
5. The complete and clean DataFrame was exported by pickling for later.

Below is a visualization of the class balance in the dataset:

![](class_equality.png)

Jupyter notebook containing the code for this entire process: [Cleaning_Original_Data](Cleaning_Original_Data.ipynb)

## [Exploring the DataSet](Exploring_Data.ipynb)

With the final dataframe ready, the Data was then analyzed for better comprehension.

Each feature was plotted to see any class dominance when that specific feature was selected.

Example: 

![](plow.png)

Features correlation was observed using a heatmap to check if any specific features were significantly correlated.

![](featcorr.png)

Jupyter notebook containing this process: [Exploring_Data](Exploring_Data.ipynb)

## Modeling
### Models Used:
* Logistic Regression
* K Nearest Neighbors
* Decision Tree
* Random Forest
* XGBoost

Each model implemented optimized parameters using _GridSearchCV_.

#### Baseline Model:
Dummy Classifier was used as a baseline model. (Used in this notebook: [Modeling_baseline](Modeling_baseline.ipynb))

The results from runnning the Dummy Classifier on the final dataframe:
* Accuracy Score: 46%
* F1 Score: 46%

Dummy Classifier's Confusion Matrix:
![](DummyConMat.png)
