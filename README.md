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
``` py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
``` py
from google.colab import drive
drive.mount('/content/drive')
```
![image](https://github.com/user-attachments/assets/20e0afb1-68e3-4af1-bf85-2ce54e4bd204)
``` py
!ls "/content/drive/My Drive/data science"
```
![image](https://github.com/user-attachments/assets/47b850e3-12d0-43d6-97b7-c85c0444c6db)
``` py
file_path = "/content/drive/My Drive/data science/titanic_dataset.csv"
dt=pd.read_csv(file_path)
dt
```
![image](https://github.com/user-attachments/assets/9b025bd7-b9ce-49eb-a2ca-fcf2ac650236)
``` py
dt.info()
```
![image](https://github.com/user-attachments/assets/e0cdc302-e062-4090-8d6e-0af44d646f57)
``` py
print(f"Number of rows = {dt.shape[0]}")
print(f"Number of columns = {dt.shape[1]}")
```
![image](https://github.com/user-attachments/assets/189b48db-1ce0-428e-9305-a99463c4d02c)
``` py
dt.set_index('PassengerId', inplace=True)
dt
```
![image](https://github.com/user-attachments/assets/ff000ee1-8557-4a64-bcfe-c3ba7dec07c0)
``` py
dt.describe()
dt
```
![image](https://github.com/user-attachments/assets/a2521c0f-7af0-42ff-ba41-23621efd885e)
# CATEGORIAL DATA ANALYSIS
``` py
dt.nunique()
```
![image](https://github.com/user-attachments/assets/f095ff90-72ff-4d56-a88d-62091aeb78be)
``` py
dt["Survived"].value_counts()
```
![image](https://github.com/user-attachments/assets/42e499c6-1aa6-47d8-919f-7b146bceb25c)
``` py
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```
![image](https://github.com/user-attachments/assets/bfd2108b-9679-4bc9-b2a8-dd9c3da11de7)
# UNIVARIATE ANALYSIS
``` py
sns.countplot(data=dt,x="Survived")
```
![image](https://github.com/user-attachments/assets/6501e12f-106b-4217-b5f0-e3bb78fe74d2)
``` py
dt
```
![image](https://github.com/user-attachments/assets/a1eba480-f76a-4f17-8c96-b0bc24763431)
``` py
dt.Pclass.unique()
```
![image](https://github.com/user-attachments/assets/e7cfd47b-4c9e-4c34-9439-f662c321a658)
``` py
dt.rename(columns = {'Sex':'Gender'},inplace = True)
dt
```
![image](https://github.com/user-attachments/assets/1b9f6db5-11bd-4e74-aef9-7dfb477b0706)
# BIVARIATE ANALYSIS
``` py
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
```
![image](https://github.com/user-attachments/assets/8dddec4d-a538-4b59-b75d-60e28df43814)
``` py
sns.catplot(x='Survived',hue="Gender",data=dt,kind="count")
```
![image](https://github.com/user-attachments/assets/341aad0e-28e4-462f-bb21-2e4411977a70)
``` py
dt.boxplot(column="Age",by="Survived")
```
![image](https://github.com/user-attachments/assets/b610ca86-a137-44cf-a3c3-27afaae7ed73)
``` py
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
```
![image](https://github.com/user-attachments/assets/ea71bcfa-e89a-4ee5-b7a3-dbadc260b360)
# MULTIVARIATE ANALYSIS
``` py
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
```
![image](https://github.com/user-attachments/assets/b4ea53e8-699f-4633-ae08-86938d514dea)
``` py
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![image](https://github.com/user-attachments/assets/99a139f3-4b19-46b4-821e-11a880ccd178)
``` py
sns.pairplot(dt)
```
![image](https://github.com/user-attachments/assets/965d686a-1c3b-4e00-97f1-2a1a49356d16)









# RESULT
    Thus, the Exploratory Data Analysis on the given data set was performed successfully.
