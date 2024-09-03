# EXNO2DS
# AIM:
To perform Exploratory Data Analysis on the given data set.
      
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
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt=pd.read_csv('titanic_dataset.csv')
dt
```
![image](https://github.com/user-attachments/assets/1cc6045e-b3e3-4b06-939b-6ffbb2e622c7)
```
dt.info()
```
![image](https://github.com/user-attachments/assets/dc001e68-864a-4ffc-99fa-b1ebb930a4d2)
```
dt.shape
```
![image](https://github.com/user-attachments/assets/61fc7739-b553-4cd5-88b2-236a446e63b4)
```
dt.describe()
```
![image](https://github.com/user-attachments/assets/e733e78c-24e2-4bfe-8155-fc3d32cd3c38)
### Categorical Data Analysis
```
dt.nunique()
```
![image](https://github.com/user-attachments/assets/9ff6336c-5415-491c-82dc-351fadc0b9da)
```
dt["Survived"].value_counts()
```
![image](https://github.com/user-attachments/assets/9d98af75-40a8-4025-983d-cc0e772f4317)
```
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```
![image](https://github.com/user-attachments/assets/d8d4a610-1997-4f21-971e-acdb6cd1287d)
### Univariate Analysis
```
sns.countplot(data=dt,x="Survived")
```
![image](https://github.com/user-attachments/assets/591d3581-99da-40bd-8864-a02157d02bc8)
```
dt.Pclass.unique()
```
![image](https://github.com/user-attachments/assets/2595c307-bd1c-450b-b370-fcb357993815)
```
dt.rename(columns={'Sex':'Gender'},inplace=True)
dt
```
![image](https://github.com/user-attachments/assets/929359d9-308f-487f-9c09-6c991cc869df)
### Bivariate Analysis
```
sns.catplot(x='Gender',col='Survived',kind='count',data=dt,height=5,aspect=.7)
```
![image](https://github.com/user-attachments/assets/1ccf63b5-8ef3-4875-bda6-d4c5048a2070)
```
sns.catplot(x='Survived',hue='Gender',data=dt,kind='count')
```
![image](https://github.com/user-attachments/assets/1112ffe0-acbe-4f21-b5e8-a506ca04d10b)
```
dt.boxplot(column="Age",by="Survived")
```
![image](https://github.com/user-attachments/assets/9e9f72a9-53f6-4641-bfe5-ab26f62f2de7)

```
sns.scatterplot(x=dt['Age'],y=dt['Fare'])
```
![image](https://github.com/user-attachments/assets/d6d0b051-94f6-4eb9-b4a7-ddeec432ac40)
```
sns.jointplot(x=dt['Age'],y=dt['Fare'],data=dt)
```
![image](https://github.com/user-attachments/assets/803e1906-4883-4515-8d69-77e0c02bd7f1)
### Multivariate Analysis
```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
```
![image](https://github.com/user-attachments/assets/28025f83-6705-4d7d-8125-ac1277a13adb)
```
sns.catplot(data=dt,col='Survived',x='Gender',hue='Pclass',kind='count')
```
![image](https://github.com/user-attachments/assets/796dd68f-9122-4023-a2f8-1bea0acdea7e)
### Correlation
```
numdt=dt.select_dtypes(exclude=[object])
corr=numdt.corr()
sns.heatmap(corr,annot=True)
```
![image](https://github.com/user-attachments/assets/98528ae5-d3fa-41ae-8da5-71b7827f5f42)
```
sns.pairplot(dt)
```
![image](https://github.com/user-attachments/assets/0adf4a19-6a39-42f2-8476-87e322eb1bb3)









# RESULT
Hence,exploratory data analaysis is successfully performed and verified on the given dataset.
