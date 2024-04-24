# SC1015: Data Science Mini Project - Bitcoin Messiah

School of Computer Science and Engineering \
Nanyang Technological University \
Lab: FCE1 \
Group : 3

Members: 
1. Isa Bin Mohamed Yamin ([@boiwantlearncode](https://github.com/boiwantlearncode))
2. Brandon Chiu Ka Shen ([@ShyIDE](https://github.com/ShyIDE))
3. Jayakumar Thirunithiyan ([@Thiru-Nithiyan](https://github.com/Thiru-Nithiyan))

---
### Description:
This repository contains all the Jupyter Notebooks, datasets, images, video presentations, and the source materials/references we have used and created as part of our Mini Project for SC1015. 

### Datasets:
Raw
- [/datasets/data_btc.csv](https://huggingface.co/datasets/gauss314/bitcoin_daily)
- [/raw/new_inflation_rate_cpi.xlsx](https://www.usinflationcalculator.com/inflation/current-inflation-rates/)

Post-Processing
- /datasets/data_btc.csv
- /datasets/expanded2_usa_inflation_rate.csv

### Problem Definition
- How can we use volume and USA interest rate to predict bitcoin prices?
- What other factors of Bitcoin's technical indicators can help us further predict the trend of Bitcoin?
- What kind of models can we use that most accurately predicts the price of Bitcoin?


### Data Preparation and Cleaning

Initially, we sourced our datasets from 2 sources as mentioned in the **Raw** section.
Afterwards, we cleaned up the datasets manually using Excel Spreadsheet. Here's what we did:
1. **Conversion of date format:** From mm/dd/yyyy in **'raw/new_inflation_rate_cpi.xlsx'** to dd/mm/yyyy
2. **Extrapolation of data points:** The raw dataset only includes one data point per month. For a larger range of predictions, we expanded the number of data points by extrapolating each data point per month across each respective month.

Following that, we cleaned up the datasets using Python. Here's what we did:
1. **Preprocessing with `pd.to_datetime`:** The `pd.to_datetime` function converts the 'date' column in both `inflation_data` and `bitcoin_data` DataFrames to datetime objects. The parameter `dayfirst=True` specifies that the date format starts with the day, followed by the month and year.
2. **Merging DataFrames:** The code merges the `bitcoin_data` and `inflation_data` DataFrames on the 'date' column using the `pd.merge` function, performing an inner join to retain only the rows with matching dates.
3. **Handling NaN values:** Any missing values in the DataFrame (`merged_data`) are filled with the mean of their respective columns using the `fillna` method. This step is done here

### Exploratory Data Analysis

- Plotting Correlation Matrix Heatmap: Finally, a correlation matrix heatmap is plotted using seaborn (`sns`) and matplotlib (`plt`). This heatmap visualizes the correlation between different numerical variables in the dataset. The correlation coefficients are displayed as annotations on the heatmap.

- Statistical Overview: Statistical overview such as mean, median and mode of each variable.

- Plotting Statistical Overview: Boxplot, histogram and violin plots of each variable.

### Walkthrough

Model used: Linear Regression K-Fold Cross Validation Technique

**Detailed Discussion on Variable Selection:**
- Code for Correlation Analysis: Include snippets that calculate and visualize the correlations between Bitcoin prices and other variables like volume and inflation rates. 
- Feature Selection: Code showing how features were chosen based on correlation strength and practical relevance. 

**Machine Learning Techniques:**
- Data Preprocessing for Modeling: Include code snippets for any additional data transformation or scaling. 
Model Implementation: 
- Linear Regression: Code to implement and fit a simple linear regression model as a baseline. 
- Random Forest: Code for training a Random Forest model including parameter settings. 
- Gradient Boosting: Setup and training of a Gradient Boosting model. 
- XGBoost: Implementation of the XGBoost model, noting any special parameters or optimization techniques used. 

**Presentation of Insights and RMSE Discussion:**
- Model Evaluation: Code for calculating the RMSE (Root Mean Square Error) for each model. 
- Comparison Plot: Code for generating plots that compare the RMSE of different models to visualize their performance. 

**Future Directions and Recommendations:**
Suggestions for Model Enhancement: 
- Code for LSTM Implementation: If available, include a basic setup for an LSTM model as a suggestion for future exploration. 
- Code for Combining Models: Example snippets where models like XGBoost and LSTM might be combined for ensemble predictions.

### Conclusion

In summary, this research not only sheds light on the predictive relationships between Bitcoin prices and its economic and technical indicators but also demonstrates the effectiveness of advanced modeling techniques. Thank you for your attention, and I look forward to any questions or further discussion on this topic.

### What we learnt

- Different ML models concerning numeric data such as Random Forest, Gradient Boosting and XGBoost that are not within the scope of our course
- Preventing overfitting in numeric models
- Extrapolate datapoints
- Predictors that we had not known to have strong correlation with Bitcoin price
- Manipulating data such as merging dataframes

### References
1. https://machinelearningmastery.com/k-fold-cross-validation/
2. https://builtin.com/data-science/random-forest-algorithm
3. https://www.analyticsvidhya.com/blog/2021/09/gradient-boosting-algorithm-a-complete-guide-for-beginners/
4. https://www.analyticsvidhya.com/blog/2018/09/an-end-to-end-guide-to-understand-the-math-behind-xgboost/
