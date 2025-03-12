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
![image](https://github.com/user-attachments/assets/92b26b61-7dff-43ca-b3da-8b931f160f1e)

df.isnull().sum()

![image](https://github.com/user-attachments/assets/e0b35b74-253e-4632-a734-32c048a9b208)

df.isnull().any()

![image](https://github.com/user-attachments/assets/8c6a6ed1-5ef7-4023-8723-409341bee477)

df.dropna(axis=0)

![image](https://github.com/user-attachments/assets/244566ca-dffd-49ad-ac20-58b200cea3ff)

df.fillna(0)

![image](https://github.com/user-attachments/assets/e093d08b-7dd6-4c03-bafc-e85ffff89c14)

df.fillna(method='ffill')

![image](https://github.com/user-attachments/assets/1c8455bb-bfdd-450c-9b1a-58753c55c8ea)

df.fillna(method='bfill')

![image](https://github.com/user-attachments/assets/2bfb79ad-6a60-41ed-9dc6-49b4d4af18c8)

 df_dropped = df.dropna()
 
 df_dropped

 ![image](https://github.com/user-attachments/assets/41996b8e-4df2-4e39-b5b2-7cc622384077)

 df.fillna({'GENDER':'FEMALE','NAME':'PRIYU','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})

 ![image](https://github.com/user-attachments/assets/1fb1d86d-c9cb-4846-a396-cbe7317de193)


IQR(Inter Quartile Range)

import pandas as pd

import numpy as np

import seaborn as sns

ir = pd.read_csv('iris.csv')

ir

![image](https://github.com/user-attachments/assets/88960749-a7f6-4dc8-af83-29e4251a706a)

df.describe()

![image](https://github.com/user-attachments/assets/40b6672e-57ff-4585-ad41-219337e34155)

sns.boxplot(x='sepal_width',data=ir)

![image](https://github.com/user-attachments/assets/8a0e6dc0-8bf6-448c-a234-432a4818a7d8)

c1=ir.sepal_width.quantile(0.25)

c3=ir.sepal_width.quantile(0.75)

iq=c3-c1

print(c3)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]

rid['sepal_width']

![image](https://github.com/user-attachments/assets/c85188ef-6c66-4bb4-a2e5-2c402504672d)

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]

delid

![image](https://github.com/user-attachments/assets/df4529e1-dce0-44eb-bdbc-131e2b3b27cb)

sns.boxplot(x='sepal_width',data=delid)

![image](https://github.com/user-attachments/assets/d0d243f5-9771-4fa1-af14-093717ecdb24)

Z-SCORE

import matplotlib.pyplot as plt

import pandas as pd

import numpy as np

import scipy.stats as stats

dataset=pd.read_csv("heights.csv")

dataset

![image](https://github.com/user-attachments/assets/a3590c33-20cc-45d2-922b-301ccd738c80)

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

![image](https://github.com/user-attachments/assets/f075a277-0790-460d-b9f4-821a59ab6443)


z = np.abs(stats.zscore(df['height']))

z

![image](https://github.com/user-attachments/assets/466d8e87-5ee5-46fa-b295-96aad34a2169)

df1 = df[z<3]

df1

![image](https://github.com/user-attachments/assets/7270a218-e4f0-408f-b5ca-130e27ec2376)



















                   


                     
            
# Result
Hence the data was cleaned , outliers were detected and removed.
