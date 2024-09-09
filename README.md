# EXNO2DS
# AIM: To perform Exploratory Data Analysis on the given data set.
### NAME : KEERTHIKA M P
### REG NO : 212223240071
### DATE : 09/09/2024
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
from IPython import get_ipython
from IPython.display import display

import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt


data = pd.read_csv('/content/titanic_dataset.csv')

print(data.isnull().sum())

data['Fare'].fillna(data['Survived'].median(), inplace=True)
data['Embarked'].fillna(data['Embarked'].mode()[0], inplace=True)
```
![image](https://github.com/user-attachments/assets/409f55b2-ffb9-487f-b74d-80c674356244)

```
sns.boxplot(data=data, x='Age')
plt.title('Boxplot of 	Age')
plt.show()
```
![download](https://github.com/user-attachments/assets/12f75a4b-fb7f-4654-a229-c8cf0ee0113f)

```
def remove_outliers_iqr(df, column):
    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR
    return df[(df[column] >= lower_bound) & (df[column] <= upper_bound)]


data_no_outliers = remove_outliers_iqr(data, 'Age')

sns.countplot(data=data_no_outliers, x='Age')
plt.title('Countplot of Age')
plt.show()
```
![download](https://github.com/user-attachments/assets/fb8340ae-9340-41d2-80d2-28645d359fd0)

```
sns.displot(data_no_outliers['Age'], kde=True)
plt.title('Distplot of Age')
plt.show()
```
![download](https://github.com/user-attachments/assets/4a004c35-e6c4-4e24-a167-d7ca60d605dc)

```
cross_tab = pd.crosstab(data_no_outliers['Sex'], data_no_outliers['Survived'])
print(cross_tab)
```
![image](https://github.com/user-attachments/assets/f492a58b-dfce-4ecc-aced-7fe4efb8c004)

```
sns.heatmap(cross_tab, annot=True)
plt.title('Heatmap of Pclass vs Survived')
plt.show()
```
![download](https://github.com/user-attachments/assets/9bb0a8c0-aad1-45a7-a0cf-fb88edd086de)

# RESULT
Thus the program to Perform Exploratory data analysis for the given data set is successfully performed

