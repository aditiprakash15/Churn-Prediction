# Telco Customer Churn- Churn Propensity Prediction

Customer churn, also known as customer attrition, occurs when customers stop doing business with a company or stop using a company’s services. By being aware of and monitoring churn rate, companies are equipped to determine their customer retention success rates and identify strategies for improvement. We will use a machine learning model to understand the precise customer behaviors and attributes which signal the risk and timing of customer churn.

# Understanding the dataset:
We will use the Telco Customer Churn dataset from Kaggle. The raw dataset contains 7043 entries.The percentage of churn in Data set is 26%, this is some what slightly imbalanced dataset.
15% of the dataset values are missing. Columns gender,SeniorCitizen, tenure, DeviceProtection, MonthlyCharges, TotalCharges have missing values. 
Categorical variables in our dataset are: customerID, gender, partner, dependents, phone service, multiple lines, internet service, online security, online backup, device protection, tech support, streaming tv, streaming movies, contract, paperless billing, payment method, total charges, and churn.
I check the distribution of continuous variable MonthlyCharges, TotalCharges and Tenure. The histogram is left skewed.

The churn percent is almost equal in case of Male and Females.
The percent of churn is higher in case of senior citizens.
The churn rate is higher in case of customers who have phone services.
Customers with Partners and Dependents have lower churn rate as compared to those who don’t have partners & Dependents.
Customers with an electronic payment method have a higher churn rate compared to other payment methods.
Customers with no internet service has a lower churn rate.
Churn rate is much higher in case of Fiber Optic InternetServices. Customers who do not have services like OnlineSecurity, OnlineBackup, and TechSupport have left the platform in the past month.

# Data Preparation & Feature Engineering:
In this section we will clean up our dataset by dropping irrelevant data, treating missing values, and converting our variables to the proper data type. 
Treating missing values.
Dropped nulls in gender, as you cannot impute it, the column has values f and m in almost equal distribution.
Dropped nulls in SeniorCitizen, as you cannot impute it, the column has values 0 and 1 in almost equal distribution.
Mapping columns- gender, SeniorCitizen, Partner, Dependents, PhoneService, MultipleLines, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies, PaperlessBilling mapping to 1 and 0.
Tenure Variable converting continous variable to a categorical, as number of tenure periods can be binned.
From the histogram we can see that Maximum customers belong to bucket 1 0-10 tenure periods. 
One hot encoding for Variable InternetService, Contract , PaymentMethod, as these variables are categorical.
We observe we have missing values in columns tenure, MonthlyCharges, TotalCharges. We will impute MonthlyCharges, TotalCharges after train test split, as we will impute it with it's mean value. 

Using Pearson Correlation, I observed that tenure and TotalCharges are highly correlated. Also, observed that TotalCharges is highly correlated with Multiplelines, OnlineSecurity, OnlineBackup, DeviceProtection, StreamingTv, StreamingMovies.
# Splitting Dataset
After Splitting the dataset into train and test. Imputed column Tenure,MonthlyCharges with median value, as the distribution of the variable was normal. Imputed column TotalCharges with tenure* monthlycharges, imputing nulls with this calculated field. 
On hot encoding for variable tenure, after the imputation of tenure with it's median value.

First our model needs to be trained, second our model needs to be tested. Therefore it is best to have two different datasets. As for now we only have one, it is very common to split the data accordingly. X is the data with the independent variables, Y is the data with the dependent variable. The test size variable determines in which ratio the data will be split. It is quite common to do this in an 80 Training / 20 Test ratio.

## Scaling techniques
Applying MinMaxScalingtechniques produces values of range [0,1]. Our dataset has features with hard boundaries. It does not have outliers. MinMaxScaler rescales the data set such that all feature values are in the range [0,1]. MinMaxScaler is very sensitive to the presence of outliers.

# Logistic Regression & Model Testing
I will start with Logistic Regression which is used for predicting binary outcome, to predict the target variable. I will use scikit-learn (sklearn) for making different models which is an open source library for Python. 
I make use of Logistic Regression- with grid search & cross validation. I get an accuracy of 80% on test dataset.

The average bagging logistic classifier recall score is 0.49 for train and 0.54 for test. The average accuracy is 0.80 for train and 0.81 for test. Bagging is not helping us improve our logistic classifier by much percentage.

The average Adaboosting logit classifier recall score is 0.52 for train and 0.55 for test. The average accuracy for logit is 0.80 for train and 0.81 for test. The Adaboosting performance is not better than original classifier.

# KNN classification
I get an accuracy of 79% on test dataset.

# Linear SVM
I get an improved accuracy of 80.1% on test dataset.

# Decision Tree
I get an improved accuracy of 79.3% on test dataset.

I tried Bagging Classifier for Decision Tree. The average bagging decision tree classifier is recall score is 0.49 for train and 0.50 for test. The average accuracy is 0.80 for train and 0.805 for test. The bagging performance is better than decision tree classifier.

The average Adaboosting decision tree classifier recall score is 0.50 for train and 0.56 for test. The average accuracy is 0.78 for train and 0.80 for test. The Adaboosting performance is similar to original classifier.

# Kerenilzed Support Vector Machine- RBF
I get an improved accuracy of 82% on test dataset.


-----------------------------------------------------------------------------------------------------------------------------------
It can be observed that some variables have a positive relation to our predicted variable and some have a negative relation. Customers with negative values show that they are unlikely to churn while those with positive values shows they are likely to churn. 
