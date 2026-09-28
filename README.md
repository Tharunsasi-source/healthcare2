# Healthcare Dataset Analysis Using Python

## 1. Project Overview

This project performs basic data analysis and visualization on a healthcare dataset using Python.

The dataset contains information about patients, their medical conditions, admission and discharge dates, billing amounts, age, and admission types.

The main aim of this project is to understand patient hospital stays, billing amounts, monthly admissions, and relationships between selected numerical variables.

## 2. Dataset

The dataset used in this project is:

`healthcare_dataset (1).csv.xls`

The dataset contains information such as:

* Patient Age
* Medical Condition
* Admission Date
* Discharge Date
* Admission Type
* Billing Amount
* Other patient-related information

## 3. Technologies Used

* Python
* Pandas
* Matplotlib
* Seaborn
* Google Colab

## 4. Libraries Used

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

## 5. Loading the Dataset

The healthcare dataset was loaded using Pandas.

```python
df = pd.read_csv("/content/healthcare_dataset (1).csv.xls")
```

The first five rows were displayed using:

```python
df.head()
```

## 6. Understanding the Dataset

The shape of the dataset was checked using:

```python
df.shape
```

This gives the number of rows and columns in the dataset.

Basic statistical information was obtained using:

```python
df.describe()
```

This helps understand numerical columns such as age and billing amount.

## 7. Checking Missing Values

Missing values were checked using:

```python
print(df.isnull().sum())
```

Rows containing missing values were removed using:

```python
df = df.dropna()
```

This helps ensure that the analysis is performed using complete records.

## 8. Date Conversion

The admission and discharge date columns were converted into datetime format.

```python
df["Admission_Date"] = pd.to_datetime(
    df["Admission_Date"],
    utc=True
)

df["Discharge_Date"] = pd.to_datetime(
    df["Discharge_Date"],
    utc=True
)
```

Converting the columns to datetime makes it easier to perform date-related calculations.

## 9. Calculating Hospital Stay

The number of days each patient stayed in the hospital was calculated using the admission and discharge dates.

```python
df["Hospital_Stays"] = (
    df["Discharge_Date"] - df["Admission_Date"]
).dt.days
```

The new `Hospital_Stays` column represents the number of days spent in the hospital.

## 10. Billing Analysis

The total billing amount was grouped according to medical condition and admission type.

```python
billing = df.groupby(
    ["Medical_Condition", "Admission_Type"]
)["Billing_Amount"].sum().unstack()

billing
```

A stacked bar chart was then created to visualize the results.

```python
billing.plot(
    kind="bar",
    stacked=True,
    figsize=(10, 6)
)

plt.xlabel("Medical Condition")
plt.ylabel("Billing Amount")
plt.title("Billing Amount by Medical Condition and Admission Type")
plt.xticks(rotation=45)
plt.legend(title="Admission Type")
plt.show()
```

### Observation

The chart helps compare the total billing amount for different medical conditions and admission types.

## 11. Hospital Stay Analysis

A violin plot was used to understand the distribution of hospital stays for different medical conditions.

```python
plt.figure(figsize=(10, 6))

sns.violinplot(
    x="Medical_Condition",
    y="Hospital_Stays",
    data=df
)

plt.title("Distribution of Hospital Stays by Medical Condition")
plt.xlabel("Medical Condition")
plt.ylabel("Hospital Stays")
plt.show()
```

### Observation

The violin plot shows how hospital stay durations are distributed across different medical conditions. It helps identify conditions where stays are more widely spread or concentrated.

## 12. Monthly Admission Analysis

The admission date was converted into monthly periods.

```python
df["Admission_Month"] = df["Admission_Date"].dt.to_period("M")
```

The number of admissions for each month was calculated using:

```python
monthly_admissions = df.groupby("Admission_Month").size()
```

A line chart was created to visualize monthly admissions.

```python
monthly_admissions.index = monthly_admissions.index.astype(str)

monthly_admissions.plot(
    kind="line",
    marker="o"
)

plt.title("Monthly Admissions")
plt.xlabel("Month")
plt.ylabel("Number of Admissions")
plt.xticks(rotation=45)
plt.grid(True)
plt.show()
```

### Observation

The monthly admissions graph shows how the number of hospital admissions changes over time.

## 13. Correlation Analysis

Correlation was calculated between:

* Age
* Hospital Stays
* Billing Amount

```python
correlation_matrix = df[
    ["Age", "Hospital_Stays", "Billing_Amount"]
].corr()

correlation_matrix
```

Correlation helps identify the strength and direction of linear relationships between numerical variables. It should not be interpreted as proof that one variable causes another.

## 14. Project Workflow

The project was completed using the following steps:

1. Import Python libraries.
2. Load the healthcare dataset.
3. Display the first few records.
4. Check the dataset shape.
5. Generate descriptive statistics.
6. Check for missing values.
7. Remove rows containing missing values.
8. Convert admission and discharge dates to datetime.
9. Calculate hospital stay duration.
10. Analyze billing amounts by medical condition and admission type.
11. Visualize hospital stay distributions.
12. Analyze monthly hospital admissions.
13. Calculate correlations between numerical variables.
14. Interpret the results using graphs and tables.

## 15. Key Findings

From this analysis:

* The dataset can be used to study patient admissions and hospital stays.
* Hospital stay duration can be calculated from admission and discharge dates.
* Billing amounts can be compared across medical conditions and admission types.
* Monthly admission analysis shows changes in admission counts over time.
* Correlation analysis provides information about relationships between age, hospital stay, and billing amount.
* Visualizations make it easier to understand patterns in the healthcare data.

## 16. Conclusion

This project demonstrates how Python can be used for basic healthcare data analysis.

Pandas was used for data loading, cleaning, transformation, grouping, and correlation analysis. Matplotlib and Seaborn were used to create different visualizations such as bar charts, violin plots, and line charts.

The project provides a simple understanding of healthcare data and demonstrates important data analysis techniques using Python.

## 17. How to Run the Project

1. Open Google Colab.
2. Upload the healthcare dataset.
3. Make sure the file is available at:

```text
/content/healthcare_dataset (1).csv.xls
```

4. Run the Python code cells.
5. View the generated tables and graphs.

## 18. Project Files

```text
Healthcare-Data-Analysis/
│
├── healthcare_dataset (1).csv.xls
├── Healthcare_Analysis.ipynb
└── README.md
```

## 19. Author

**Name:** S. Tharun Sasi

**Project:** Healthcare Dataset Analysis Using Python
