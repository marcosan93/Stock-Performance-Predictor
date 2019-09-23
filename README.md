# Stock Predictor
#### Predicting if a stock will rise by 5% or more in its next quarter based on fundamental data
Marco Santos

## Table of Contents
  * [Data](#Data)
  * Modeling
  * Results/Recommendations
  * Improvements
  * Conclusion
  
## Data

The main source of data was retrieved from [Stockpup.com](http://www.stockpup.com/data/).
  * Data was downloaded from 765 different csv files.
  * Webscraping was implemented in order to automate the download process: [Retrieving Data](Retrieving_Data.ipynb).
  * Each csv file was saved as a separate Pandas DataFrame and stored in a dictionary which was pickled for later use.
  
### Data Formatting, Cleaning, and Organizing

Throughout most of the process, until all the Pandas DataFrames were combined, many functions were applied by iterating through the dictionary storing each stock's unique dataframe.
