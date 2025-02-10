# ML-EDA
# GenZ Dating App Dataset

# Overview
This dataset contains information related to user activities, preferences, and interactions on a GenZ-focused dating app. It includes categorical, numerical, and timestamp data, which can be used for user behavior analysis, trend predictions, and recommendation system development.

# Data Dictionary
Here  is a table describing the dataset's columns, including their data types and descriptions.

| Column Name        | Data Type  | Description |
|--------------------|-----------|-------------|
| user_id         | Integer   | Unique identifier for each user. |
| age             | Integer   | Age of the user. |
| gender          | Object    | Gender of the user (e.g., Male, Female, Non-binary). |
| location        | Object    | User's geographical location. |
| sign_up_date    | DateTime  | The date the user registered on the platform. |
| last_active     | DateTime  | The last recorded activity timestamp of the user. |
| subscription    | Object    | Type of subscription plan (e.g., Free, Premium). |
| messages_sent   | Integer   | Total number of messages sent by the user. |
| matches_count   | Integer   | Total number of matches made by the user. |
| profile_complete| Float     | Percentage of profile completion (0-100). |


# Data Cleaning Steps
The following cleaning steps have been performed:

# 1. Checked for Duplicate Rows
- Used .duplicated().sum() to check for duplicate entries.
- If duplicates exist, they can be removed using data.drop_duplicates(inplace=True).

# 2. Identified Inconsistencies in Categorical Data
- Retrieved unique values using data[column].unique() to check for spelling variations, case sensitivity, and whitespace inconsistencies.
- Standardized categorical values by converting them to lowercase and stripping extra spaces:  
  python
  data['gender'] = data['gender'].str.lower().str.strip()
  

# 3. Handled Missing Values
- Checked for missing values using data.isnull().sum().
- Filled missing categorical values with mode and numerical values with median where appropriate.

# 4. Detected Outliers in Numerical Data
- Used box plots and the *Interquartile Range (IQR) method* to identify outliers:
  python
  Q1 = data[numerical_cols].quantile(0.25)
  Q3 = data[numerical_cols].quantile(0.75)
  IQR = Q3 - Q1
  outliers = ((data[numerical_cols] < (Q1 - 1.5 * IQR)) | (data[numerical_cols] > (Q3 + 1.5 * IQR))).sum()
  
- Considered removing or capping extreme values based on analysis.



# How to Use This Dataset
1. Clone this repository:
   sh
   git clone https://github.com/your-repo/genz-dating-app-data.git
   
2. Load the dataset in Python:
   python
   import pandas as pd
   data = pd.read_csv("GenZ_DatingApp_Data.csv")
   
3. Explore the dataset:
   python
   print(data.head())
   print(data.info())
   

# Next Steps
- Further cleaning and normalization of categorical values.
- Feature engineering for user engagement analysis.
- Exploratory Data Analysis (EDA) to find patterns and trends.
- Building a recommendation system based on user behavior
