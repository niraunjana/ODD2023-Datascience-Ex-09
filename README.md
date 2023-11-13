# Ex-09-Data-Visualization-

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```
Developed by :  Niraunjana Gayathri G R
Reg No.      : 212222230096
```
#Load Dataset
```
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=sns.load_dataset("tips")
print(df)
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/9a292379-b060-436b-b105-91aa2df5362d)
```
df.isnull().sum()
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/2158a19a-49b0-44d3-8b3f-239e875e0a5d)
#Handling Outliers
```
plt.figure(figsize=(5,5))
plt.title("Data with Outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/2a7abc0a-0731-4c72-9f6b-112a7e3d1d17)
#Removing outliers
```
plt.figure(figsize=(9,6))
cols=["size","tip","total_bill"]
q1=df[cols].quantile(0.25)
q3=df[cols].quantile(0.75)
iqr=q3-q1
df=df[~((df[cols]<(q1-1.5*iqr))|(df[cols]>(q3+1.5*iqr))).any(axis=1)]
plt.title("dataset after removing outliners")
df.boxplot()
plt.show()
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/f5588285-d1a6-44e2-8ad6-3017cf3a4f5a)

# 1) Which day of the week has the highest total bill amount ?
```
sns.barplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="center")
plt.title("Highest Total Bill Amount by day of the week")
plt.show()
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/bcff786a-bac8-4945-97db-f18bfafc979a)

# 2) What is the average tip amount given by smokers and non-smokers?
```
sns.boxplot(x=df['smoker'],y=df['tip'],hue=df['smoker'])
plt.title("Average Tip Amount given by Smokers and Non-smokers")
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/8d4c6cc0-ec2b-4f94-81dc-275d7d4eaab4)

# 3) How does the tip percentage vary based on the size of the dining party?
```
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip Percentage by Dining Party size")
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/f13cf837-5d29-4d07-9c86-bc516b048da0)

# 4) Which gender tends to leave higher tips?
```
sns.boxplot(x=df['sex'],y=df['tip'],hue=df['sex'])
plt.title("Tips BAsed on gender")
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/dce80f56-a178-4a42-b893-7fdd70bbd850)
### 5) Is there any relationship between the total bill amount and the day of the week?
```
sns.scatterplot(x=df['day'],y=df['total_bill'],hue=df['day'])
plt.legend(loc="best")
plt.title("Total bill amount by day of the week")
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/e657d079-ac9e-400e-bfe2-e2cb0eec3154)
### 6) How does the distribution of total bill amounts vary across different time periods (lunch vs. dineer)?
```
sns.histplot(data=df,x="total_bill",hue="time",element="step",stat="density")
plt.title("Distribution of Total Bill Amounts by Time of Day")
plt.show()
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/f6aa57a2-18d3-4ca6-b94f-baaa9e947850)

# 7) Which dining party size group tends to have the highest average total bill amount?
```
sns.barplot(x=df['size'],y=df['total_bill'],hue=df['size'])
plt.title("Average total Bill amount by Dininng party size]")
plt.show()
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/db942947-d19d-46a8-941b-5a1a01e1ff1b)

# 8) What is the distribution of tip amounts for each day of the week?
```
sns.boxplot(x="day",y='tip',data=df)
plt.title("Tip amount by dy of Week")
plt.show()
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/8278f762-dd88-4d0b-9539-8872200c6904)

# 9) How does the tip amount vary based on the type of service (lunch vs. dinner)?
```
sns.violinplot(x="time",y="tip",data=df)
plt.title("Tip Amount time Of day")
plt.show()
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/e24af042-f50f-4c4a-bfef-63278703a3c9)

# 10) Is there any correlation between the total bill amount and the tip amount?
```
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correaltion between Tip Amount and Total Bill Amount")
plt.show()
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-09/assets/119395610/b4c0abbc-5cfe-4963-9cd6-280dac92a8dd)

### RESULT:
Thus, Data Visualization on a complex dataset has been performed successfully and the data is saved to a file.
