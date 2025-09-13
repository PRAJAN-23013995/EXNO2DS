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
df=pd.read_csv("/content/titanic_dataset.csv")
df
```

<img width="1536" height="571" alt="Screenshot 2025-09-13 104236" src="https://github.com/user-attachments/assets/8ed4d93f-82ff-47b6-85bf-22a1c77b71dd" />

```
df.info()
```
<img width="1647" height="497" alt="Screenshot 2025-09-13 104248" src="https://github.com/user-attachments/assets/d3f26fb9-d532-44ae-b963-4c729b4fac85" />

```
df.descripe()
```

<img width="1666" height="432" alt="Screenshot 2025-09-13 104255" src="https://github.com/user-attachments/assets/2efb7216-8467-4280-8b7b-aba8aca8ea42" />

```
df.dtypes
```


<img width="1666" height="598" alt="Screenshot 2025-09-13 104303" src="https://github.com/user-attachments/assets/86b45ba0-28dc-4bfa-bb8c-547338b33989" />

```
df.shape
```
<img width="973" height="129" alt="Screenshot 2025-09-13 110545" src="https://github.com/user-attachments/assets/0a57d4bb-ec99-4da6-93b1-536077b8f017" />

```
df.value_counts()
```

<img width="1423" height="579" alt="Screenshot 2025-09-13 110601" src="https://github.com/user-attachments/assets/ce8a968f-546d-4f19-bd87-b685143be3e2" />

```
df['Age'].value_counts()
```
<img width="1686" height="630" alt="Screenshot 2025-09-13 104324" src="https://github.com/user-attachments/assets/756d2051-a00e-4603-a2cb-21fd2a077c80" />

```
df.set_index("PassengerId", inplace=True)
df
```
<img width="1713" height="617" alt="Screenshot 2025-09-13 104332" src="https://github.com/user-attachments/assets/11c52395-4c58-4dbf-8769-8bf0781da199" />


df.nunique()
```

<img width="1645" height="513" alt="Screenshot 2025-09-13 105652" src="https://github.com/user-attachments/assets/1fa3a6de-cb01-4cae-bb4a-124136efa7dc" />

```
sns.countplot(data=df,x='Survived')
```

<img width="1607" height="575" alt="Screenshot 2025-09-13 105725" src="https://github.com/user-attachments/assets/b7943688-49f2-43d7-b2ae-5dcc9a9b1e3d" />

```
df.rename(columns={'Sex':'Gender'},inplace=True)
df
```

<img width="1645" height="584" alt="Screenshot 2025-09-13 105743" src="https://github.com/user-attachments/assets/a7fef9fe-4837-4c02-b119-ad88bbdb91e2" />

```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```

<img width="1364" height="613" alt="Screenshot 2025-09-13 112448" src="https://github.com/user-attachments/assets/385d26c5-d599-4396-b573-46c751eb9e5e" />

```
df.boxplot(column="Age",by="Survived")
```

<img width="1316" height="582" alt="Screenshot 2025-09-13 112457" src="https://github.com/user-attachments/assets/e01372e6-1a38-49c3-b833-aa6a0903c48e" />

```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```

<img width="1382" height="547" alt="Screenshot 2025-09-13 112505" src="https://github.com/user-attachments/assets/eacf4995-5c6e-44d5-aed2-9f54acf80b1f" />

```
fig, axl=plt.subplots(figsize=(8,5))
plt=sns.boxplot(ax=axl,x='Pclass',y='Age',hue='Gender',data=df)
```

<img width="1368" height="576" alt="Screenshot 2025-09-13 112515" src="https://github.com/user-attachments/assets/d5278d05-ae53-4d89-a8ab-bf3fde4a4664" />

```
plt=sns.boxplot(x='Pclass',y='Age',hue='Gender',data=df)
```

<img width="1380" height="539" alt="Screenshot 2025-09-13 112523" src="https://github.com/user-attachments/assets/aaae6d20-85c2-4377-8027-72947105b8c9" />

```
import seaborn as sns
sns.catplot(x='Pclass',y="Age",hue="Gender",col="Survived",kind="box",data=df)
```

<img width="1264" height="598" alt="Screenshot 2025-09-13 114305" src="https://github.com/user-attachments/assets/2c1ea789-b3ac-49b0-bc1b-b8ab2e008b2f" />

```
sns.catplot(data=df,col="Survived",x="Gender",hue='Pclass',kind="count")
```

<img width="1265" height="610" alt="Screenshot 2025-09-13 114325" src="https://github.com/user-attachments/assets/10b03a6d-27af-4eb2-8999-d8c0da04b5e9" />

```
corr=df.corr(numeric_only=True)
sns.heatmap(corr,annot=True)
```

<img width="1274" height="514" alt="Screenshot 2025-09-13 114333" src="https://github.com/user-attachments/assets/0f9884c1-30c2-4bd1-911a-34372f36a1af" />

```
corr=df.select_dtypes(include=np.number).corr()
sns.heatmap(corr,annot=True)
```

<img width="1267" height="533" alt="Screenshot 2025-09-13 114343" src="https://github.com/user-attachments/assets/fbc563b6-a79e-495a-96b6-1b63366a4494" />

        
# RESULT
        <<INCLUDE YOUR RESULT HERE>>
