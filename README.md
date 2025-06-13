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

# Load dataset
df = pd.read_csv("/content/titanic_dataset (1).csv")  # Replace with actual path

# Display basic info
df.info()

# Display first few rows
df.head()

# Check shape
print(f"Dataset contains {df.shape[0]} rows and {df.shape[1]} columns")
```
![Screenshot 2025-03-24 155001](https://github.com/user-attachments/assets/fec4f69b-e6b6-4f3d-bb07-80d6dd8f95ef)
```
# Set PassengerId as index
df.set_index("PassengerId", inplace=True)

# Summary statistics
df.describe()
```
![Screenshot 2025-03-24 155334](https://github.com/user-attachments/assets/ffc751e1-7428-4f21-975a-68d13f3ed903)

```
# Count unique values in categorical columns
categorical_columns = ["Survived", "Pclass", "Sex", "Embarked"]
for col in categorical_columns:
    print(f"{col} unique values:\n", df[col].value_counts(), "\n")
    
```
![Screenshot 2025-03-24 155415](https://github.com/user-attachments/assets/df772eb4-426f-445f-bd47-104de740698b)

```
sns.countplot(data=df, x="Survived")
plt.title("Survival Count")
plt.show()
```
![image](https://github.com/user-attachments/assets/93e846a5-e59d-4ad3-aae4-435b328d8e62)

```
df["Pclass"].unique()
```
![Screenshot 2025-03-24 155459](https://github.com/user-attachments/assets/c4b339d9-daa8-4831-ab04-850ff1cc213d)

```
df.rename(columns={"Sex": "Gender"}, inplace=True)
df
```
![Screenshot 2025-03-24 155534](https://github.com/user-attachments/assets/d97f9947-30eb-4fb7-b620-ff9cca6c2e99)

```
sns.catplot(x='Survived', hue='Gender', data=df, kind='count')
plt.title("Survival by Gender")
plt.show()
```
![image](https://github.com/user-attachments/assets/a0ff6e59-32a5-4f13-aed4-a0f4995c0013)

```
sns.boxplot(x="Survived", y="Age", data=df)
plt.title("Age Distribution by Survival")
plt.show()
```
![image](https://github.com/user-attachments/assets/e069fcf9-204a-4215-a911-05e49eb3d7e5)

```
sns.boxplot(x="Pclass", y="Age", hue="Gender", data=df)
plt.title("Age Distribution Across Passenger Classes and Gender")
plt.show()
```
![image](https://github.com/user-attachments/assets/8a19ca71-1ad5-4d12-b785-a64b8bc47dd9)

```
plt.figure(figsize=(10,6))

# Select only numerical columns
numerical_df = df.select_dtypes(include=["number"])

# Compute correlation and plot heatmap
sns.heatmap(numerical_df.corr(), annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Feature Correlation Heatmap")
plt.show()

```
![image](https://github.com/user-attachments/assets/0b21f748-368a-49c0-896f-21595fec8e02)

```
sns.pairplot(df, hue="Survived", diag_kind="kde")
plt.show()
```
![image](https://github.com/user-attachments/assets/acc3d577-8e2c-4fe6-977c-b4b3f2afa5e4)

# RESULT
        
Thus, the Exploratory Data Analysis on the given data set was performed successfully.
