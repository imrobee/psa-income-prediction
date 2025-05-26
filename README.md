Machine Learning Approach to Per Capita Income Prediction in the Philippines

# Introduction to the Task and Dataset

The chosen regression task for the models in this project is to predict the **Per Capita Income** (PCINC) of a household  given:
- the number of family members (FSIZE)
- salaries and wages from employment in non-agricultural sectors (NONAGRI_SAL)
- salaries and wages from employment in all sectors (WAGES)
- total financial assistance from abroad (CASH_ABROAD)
- total food expenditure (T_FOOD)
- total non-family disbursements (T_OTHER_DISBURSEMENT)
- total non-food expenditure (T_NFOOD)
- total expenditure (T_TOTEX)
- total disbursements (T_TOTDIS)
- highest grade completed of the family head (HGC)
- main source of water supply of the family (WATER)

These features were chosen due to their being sufficiently correlated to the target variable.

# Description of the Dataset

## Brief Description of the Dataset
The dataset comes from the Philippine Statistics Authority. It contains data about expenditures and other disbursements, housing characteristics, social protection, Income and other receipts and Entrepreneural Activities.

## Data Collection Process
The dataset was collected through two face-to-face survey visits, conducted in 2012 and 2013, with data covering two phases of the year to capture seasonal variations in income and expenditure. The process was closely supervised by regional and provincial staff from the Philippine Statistics Authority (PSA) to ensure accurate data collection, with supervisors conducting random re-interviews and checking the quality of enumerator work. Trained enumerators collected detailed information on family income sources and expenditures. While the thorough supervision and structured approach likely ensured data reliability, challenges such as non-response, deferment of interview, lack of forms, problem area, and accidents or injuries could have impacted data completeness. The researchers, however, did have protocols for each of these potential enumeration and related problems. The method’s strength lies in its ability to capture nuanced, seasonal financial patterns, though potential biases from interviewees' reluctance to disclose sensitive financial information must be considered when interpreting the dataset.

## Structure of the Dataset
The dataset is composed of 40171 rows (instances) and 119 columns (features). Each row represents a case while each column represents a variable.

# Insights
The model optimization process and performance summary revealed key insights about how different machine learning models behave in certain circumstances. After optimizations, the decision tree regressor perfomed the best on the dataset with better error metrics across the board, followed by KNN and Linear Regression.

In terms of the models themselves, Decision Trees could have performed better due to several factors. For one, Decision Trees can handle multicollinearity (high correlation among independent variables) better than KNN and Linear Regression because of its splitting criteria, which is not affected by correlated variables. Further reading for this can be viewed here: https://www.geeksforgeeks.org/solving-the-multicollinearity-problem-with-decision-tree/
Additionally, Decision Trees works better against skewed data when compared to KNN and Linear Regression. The Decision Tree Regressor creates splits that adapt to the data's skewness, making it more robust against the constraints of our dataset.

# Conclusion
In conclusion, this notebook was a valuable experience in terms of applying machine learning to real-world problems. The use of a real-world dataset provided by the Philippine Statistics Authority helped in giving a glimpse as to how working on data provided by a third-party is like and the advantages and challenges brought by it.

Given the machine learning task, Linear Regression's performance on unseen data scored last in terms of R^2 score at 0.72 after optimizations, followed by KNN in second at a score of 0.84, and Decision Tree in first with a score of 0.86. To summarize, the Decision Tree Regressor worked best for the regression task given the constraints of the dataset, followed by KNN then Linear Regression. In terms of their performance to difficult instances caused by the skewness of the data, the Decision Tree Regressor performed best when optimized, followed by KNN and Linear Regression.

Based on error analysis of all the models, most of the difficult to predict instances were usually those that had high values. The higher the value of the target label, the more difficult it was for the model to predict. This was true for all three of the models. This could be because many of the features, as well as the target label, had a positively skewed distribution. It should be noted however, that when removing some of these lower correlated features in the KNN model, it’s performance decreased.

When performing hyperparameter tuning on the models, only one model had significant improvement. Performing Stochastic GD & Batch GD on Linear Regression & Grid Search on KNN, the models had minimal, if any, improvement. Further improvements to the models could be done by performing more in depth feature engineering to include features that may have been overlooked. As well as to collect more data to possibly address the skewness of the target label or to at least have more difficult instances for the model to train on.
