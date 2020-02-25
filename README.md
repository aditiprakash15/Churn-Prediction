# Churn-Prediction
Telco Customer Churn- Churn Propensity Prediction

Customer churn, also known as customer attrition, occurs when customers stop doing business with a company or stop using a company’s services. By being aware of and monitoring churn rate, companies are equipped to determine their customer retention success rates and identify strategies for improvement. We will use a machine learning model to understand the precise customer behaviors and attributes which signal the risk and timing of customer churn.

Understanding the dataset:
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

Data Preparation & Feature Engineering:
