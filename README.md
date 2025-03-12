# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output

                                 DATA CLEANING

import pandas as pd

import numpy as np

df = pd.read_csv('SAMPLEIDS.csv')


df.head()

![image](https://github.com/user-attachments/assets/714cfede-9e05-401e-8477-aa3eb5295d49)

df.isnull().sum()

![image](https://github.com/user-attachments/assets/c6d4629e-c6f3-48d2-be24-1d51c3aa33fb)

df.isnull().any()

![image](https://github.com/user-attachments/assets/aa36b5ae-8e79-4ecb-8dc3-24a6326304ef)


df.dropna(axis=0)

![image](https://github.com/user-attachments/assets/4ed40c8c-e504-41d4-8061-d776c1a071f4)

df.fillna(0)

![image](https://github.com/user-attachments/assets/5147db68-32fe-4d83-9652-41d0f1936c31)

df.fillna(method='ffill')

![image](https://github.com/user-attachments/assets/e3a733a5-18cc-48e3-b3aa-5ae9f61891d4)

df.fillna(method='bfill')

![image](https://github.com/user-attachments/assets/07353fba-fca8-40ef-8d1a-bcc2a2bb7108)

df_dropped = df.dropna()

df_dropped

 ![image](https://github.com/user-attachments/assets/d094c9dd-27d6-4f4b-af45-5c05e02a6d69)

 df.fillna({'GENDER':'FEMALE','NAME':'PRIYU','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})

![359345548-c7e2a295-4135-4e02-951e-52e34108cb8c](https://github.com/user-attachments/assets/1b303ab5-7854-4761-b985-d3c70c5f2937)


                             IQR(Inter Quartile Range)

import pandas as pd

import numpy as np

import seaborn as sns

ir = pd.read_csv('iris.csv')

ir

![359346510-ed22d468-5c28-473b-95ae-d320a20318ed](https://github.com/user-attachments/assets/344a4651-03ed-4307-ab24-c3f0b9550089)

df.describe()

![image](https://github.com/user-attachments/assets/546f5745-86e4-4d5a-a7ae-d1f5474cc9a0)

sns.boxplot(x='sepal_width',data=ir)

![image](https://github.com/user-attachments/assets/ac1db649-fe05-4dbb-8800-9658d8050de7)

c1=ir.sepal_width.quantile(0.25)

c3=ir.sepal_width.quantile(0.75)

iq=c3-c1

print(c3)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]

rid['sepal_width']

![image](https://github.com/user-attachments/assets/1d0ba648-3a44-4784-9d6b-10b38c99af02)

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid

![image](https://github.com/user-attachments/assets/f9372d5f-5030-416f-b14c-a92ca13bf220)

sns.boxplot(x='sepal_width',data=delid)

![image](https://github.com/user-attachments/assets/8355f55c-8597-40ac-b37f-325119d11ea3)

                                       Z-SCORE

import matplotlib.pyplot as plt

import pandas as pd

import numpy as np

import scipy.stats as stats

dataset=pd.read_csv("heights.csv")

dataset

![image](https://github.com/user-attachments/assets/7454c515-f04f-429e-ae66-a3445ea387a0)

df = pd.read_csv("heights.csv")

q1 = df['height'].quantile(0.25)

q2 = df['height'].quantile(0.5)

q3 = df['height'].quantile(0.75)

iqr = q3-q1

iqr

low = q1 - 1.5*iqr

low

high = q3 + 1.5*iqr

high

df1 = df[((df['height'] >=low)& (df['height'] <=high))]

df1

![image](https://github.com/user-attachments/assets/22b3e991-713f-4ac2-a4d4-d9b98e76d507)

z = np.abs(stats.zscore(df['height']))

z

![image](https://github.com/user-attachments/assets/88580f72-0d14-45af-a0b4-63614e2ec7f2)


df1 = df[z<3]

df1

![image](https://github.com/user-attachments/assets/bf63c6bb-d62b-4d29-9f08-0014d6f197bc)

































 




# Result

Hence the data was cleaned , outliers were detected and removed.
