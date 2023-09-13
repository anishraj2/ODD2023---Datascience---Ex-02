# Ex02-Outlier

# AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM:
# STEP 1:
Read the given Data.
# STEP 2:
Get the information about the data.
# STEP 3:
Detect the Outliers using IQR method and Z score.
# STEP 4:
Remove the outliers:
# STEP 5:
Plot the datas using box plot.
# PROGRAM:
```
DEVELOPED BY: ANISH RAJ P
REGISTER NUMBER: 212222230010

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### Removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)
#New dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### Removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
# OUTPUT:
# bhp.csv:
# df.head():
![df.head](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/c7018819-6fb3-4197-aa6c-373478cdc412)
# df.describe():
![df.describe](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/e60b83b2-c25e-474c-8097-348a71008bbf)
# df.info():
![df.info](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/03bca4ae-ec3c-4bfc-95fc-aec2c3e2fbd1)
# df.shape
![df shape](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/f9c24c60-7a00-40ee-a17b-2c6f18000848)
# BOXPLOT BEFORE REMOVING OUTLIERS
![Box plot](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/9babcdee-c559-4a95-9c4c-ff3e96655da6)
# NEWDATA USING IQR
![New data](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/181ec5c3-b6da-464a-bef0-6343bd6d6e91)
# OUTLIERS
![outliers](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/9453fb2b-c641-4bec-b18e-71de44d74352)
# newdata.shape
![new data shape](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/0dd42818-c91d-466d-a478-dd9ef75a31a7)
# BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![After](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/3fe8fe76-0d42-4a28-aa73-082817e59fae)
# Zscore of 3
# NEWDATA USING Zscore
![new data zscore](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/f6b5e3e0-3e9e-45e8-bf57-5a34ccd22b01)
# OUTLIERS
![outliers](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/418a6696-2c29-4aa4-9154-d742dfdb7477)
# newdata2.shape
![newdata2](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/2fe2c2c2-8cd9-4afa-b2dc-241c5d83e9ff)
# BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![box after](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/8beae216-f7c9-4a05-8fc7-1903ac932d76)
# height_weight.csv
![height](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/8a59d0e4-6af7-4d36-b8a3-b9db74da7bfc)
# dataset.describe()
![describe](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/036b8343-f815-4e1b-a313-ec8669e58c96)
# dataset.info()
![info](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/1dbf9011-ce15-499c-bc48-41810a0f1aea)
# BOXPLOT BEFORE REMOVING OUTLIERS
![removing](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/f508f333-19b2-47ea-a93e-cae2e4add0cf)
# HEIGHT OUTLIERS
![h](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/cd0e4151-66a6-4968-a0a3-d2254b4e8acc)
# DATASET AFTER REMOVING HEIGHT OUTLIERS
![1](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/6c043252-df5d-43be-800c-0c373f844dfe)
# BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![2](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/82209497-1199-45f7-a1f6-46a1248ce3f2)
# WEIGHT OUTLIERS
![3](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/20a85f0e-6efb-4079-996e-fcb0f336d04e)
# DATASET AFTER REMOVING WEIGHT OUTLIERS
![4](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/ecd915ae-df58-46f7-b810-6d21fba4562d)
# BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![5](https://github.com/anishraj2/ODD2023---Datascience---Ex-02/assets/119393390/3001d58b-c394-4676-80a5-749c43d6fd50)
# RESULT:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
