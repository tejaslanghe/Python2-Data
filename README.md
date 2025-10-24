# Python2-Data
# 🪔 Python Diwali Sales Data Analysis

## 📊 Project Overview
This project performs **Exploratory Data Analysis (EDA)** on Diwali sales data to understand **customer purchasing patterns**, **spending behavior**, and **demographic insights** using Python.  
The findings aim to help businesses improve **marketing campaigns**, **targeted promotions**, and **product strategies** during festive seasons.

---

## 📁 Project Files

| File Name | Description |
|------------|-------------|
| `python diwali data Analysis.html` | Exported HTML version of Jupyter Notebook with complete analysis and visualizations. |
| `diwali_sales_data.csv` | Dataset used for the analysis. |
| `README.md` | Documentation file describing the project. |

---

## 🧠 Objectives
- Clean and preprocess raw sales data.
- Analyze customer demographics (Gender, Age, Occupation, State, etc.).
- Visualize data using Python libraries.
- Identify key patterns and actionable insights.
- Recommend strategies based on findings.

---

## 🧩 Tools and Libraries Used
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

🧹 Data Cleaning

Loading the Dataset
```python
df = pd.read_csv("Diwali Sales Data.csv", encoding='unicode_escape')
df.head()
```

Checking Missing Values
```python
df.isnull().sum()
```

Dropping Unnecessary Columns
```python
df.drop(['Status', 'unnamed1'], axis=1, inplace=True)
```

Removing Null Values
```python
df.dropna(inplace=True)
```

📊 Exploratory Data Analysis (EDA)

Gender-Based Analysis
```python
ax = sns.countplot(data=df, x='Gender')
for container in ax.containers:
    ax.bar_label(container)
plt.title("Gender-wise Purchase Count")
plt.show()
```
```python
df.groupby(['Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
```

Age Group vs Spending
```python
sns.barplot(x='Age Group', y='Amount', data=df, hue='Gender')
plt.title("Age Group vs Amount Spent")
plt.show()
```

State-wise Purchase Analysis
```python
sales_state = df.groupby('State', as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(x='State', y='Amount', data=sales_state)
plt.title("Top States by Sales")
plt.xticks(rotation=45)
plt.show()
```

Occupation-Based Spending
```python
sns.barplot(x='Occupation', y='Amount', data=df)
plt.title("Occupation vs Amount Spent")
plt.xticks(rotation=45)
plt.show()
```
