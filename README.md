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

##
