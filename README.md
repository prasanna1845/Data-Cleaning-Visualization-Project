# Data-Cleaning-Visualization-Project

DESCRIPTION 

1. Import Libraries
Python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
Description:
pandas is used to load and manipulate the dataset.
matplotlib.pyplot is used to create graphs.
seaborn is used to create attractive statistical visualizations.
2. Load the Dataset
Python
df = pd.read_csv("data.csv")
Description:
Reads the dataset (data.csv) and stores it in a DataFrame named df.
3. Display the First Five Rows
Python
print(df.head())
Description:
Displays the first five rows of the dataset to understand its structure.
4. Display Dataset Information
Python
print(df.info())
Description:
Shows:
Number of rows and columns
Column names
Data types
Missing values
5. Check Missing Values
Python
print(df.isnull().sum())
Description:
Counts the number of missing values in each column.
6. Fill Missing Values
Python
numeric_cols = df.select_dtypes(include='number').columns
df[numeric_cols] = df[numeric_cols].fillna(df[numeric_cols].mean())
Description:
Selects all numeric columns.
Replaces missing values with the mean of each column.
7. Remove Duplicate Rows
Python
df = df.drop_duplicates()
Description:
Removes duplicate records from the dataset.
8. Remove Outliers
Python
for col in numeric_cols:
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR
    df = df[(df[col] >= lower) & (df[col] <= upper)]
Description:
Uses the Interquartile Range (IQR) method.
Removes values that are too high or too low (outliers).
9. Save the Cleaned Dataset
Python
df.to_csv("cleaned_data.csv", index=False)
Description:
Saves the cleaned dataset as cleaned_data.csv.
10. Create Histogram
Python
plt.figure(figsize=(8,5))
df[numeric_cols[0]].hist()
plt.title("Histogram")
plt.xlabel(numeric_cols[0])
plt.ylabel("Frequency")
plt.show()
Description:
Displays the frequency distribution of the first numeric column.
11. Create Boxplot
Python
plt.figure(figsize=(8,5))
sns.boxplot(x=df[numeric_cols[0]])
plt.title("Boxplot")
plt.show()
Description:
Displays a boxplot to identify the spread of data and outliers.
12. Create Correlation Heatmap
Python
plt.figure(figsize=(8,6))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap="coolwarm")
plt.title("Correlation Heatmap")
plt.show()
Description:
Shows the correlation between numeric columns.
Correlation values range from -1 to +1:
+1 → Strong positive relationship
0 → No relationship
-1 → Strong negative relationship
13. Completion Message
Python
print("Data cleaning and visualization completed successfully!")
Description:
Displays a confirmation message after the program completes successfully.

OUTPUT 📌
<img width="1536" height="1024" alt="Image" src="https://github.com/user-attachments/assets/591238ab-7e20-47ac-996a-68ec8763be18" />
