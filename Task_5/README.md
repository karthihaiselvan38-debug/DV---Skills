# 🏥 Healthcare Dataset Analysis

## 📌 Project Overview

This project analyzes a **Healthcare Dataset** using Python. The dataset contains patient information such as gender, age, medical condition, admission type, medical code, billing amount, admission date, and discharge date.

The main objective of this project is to understand **patient demographics, admission patterns, hospital stay duration, and billing information** using data analysis techniques.

---

## 🛠️ Technologies Used

* Python
* Pandas
* Matplotlib
* Seaborn
* Google Colab

---

## 📂 Dataset

The dataset used in this project is **healthcare_dataset.csv**.

The dataset contains **500 patient records and 9 columns**.

### Dataset Columns

| Column            | Description                                 |
| ----------------- | ------------------------------------------- |
| Patient_ID        | Unique identification number of the patient |
| Gender            | Gender of the patient                       |
| Age               | Age of the patient                          |
| Medical_Condition | Medical condition diagnosed                 |
| Admission_Date    | Date when the patient was admitted          |
| Admission_Type    | Type of admission                           |
| Medical_Code      | Medical diagnosis code                      |
| Billing_Amount    | Amount billed for treatment                 |
| Discharge_Date    | Date when the patient was discharged        |

---

# 🔍 Data Analysis

## 1. Import Required Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

The libraries are used for:

* **Pandas** – Data loading, cleaning, and analysis
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization

---

## 2. Load the Dataset

```python
df = pd.read_csv("/healthcare_dataset.csv")
```

The healthcare dataset is loaded into a Pandas DataFrame.

---

## 3. Display the Dataset

```python
df
```

This displays the complete dataset.

The dataset contains **500 rows and 9 columns**.

---

## 4. Display First Five Records

```python
df.head()
```

The `head()` function displays the first five records of the dataset.

---

# 📋 Dataset Information

## 5. Check Dataset Information

```python
df.info()
```

The dataset contains:

* 500 records
* 9 columns
* 1 integer column
* 1 floating-point column
* 7 object columns

There are no missing values in the original dataset.

---

## 6. Statistical Summary

```python
df.describe()
```

The `describe()` function provides statistical information for numerical columns.

### Age

| Statistic |  Value |
| --------- | -----: |
| Mean      | 50.106 |
| Minimum   |     22 |
| Maximum   |     78 |
| Median    |     50 |

### Billing Amount

| Statistic |    Value |
| --------- | -------: |
| Mean      | 7249.001 |
| Minimum   |     2300 |
| Maximum   |    14200 |
| Median    |     6950 |

---

# 🧹 Data Cleaning

## 7. Check Missing Values

```python
df.isnull().sum()
```

The result shows that there are **no missing values** in any column.

```text
Patient_ID           0
Gender               0
Age                  0
Medical_Condition    0
Admission_Date       0
Admission_Type       0
Medical_Code         0
Billing_Amount       0
Discharge_Date       0
```

---

## 8. Fill Missing Values

Object-type columns are checked and missing values are filled with `"not gather"`.

```python
for column in df.select_dtypes(include='object').columns:
    df[column] = df[column].fillna('not gather')

print("Missing values after filling:")
print(df.isnull().sum())
```

After filling, all columns contain **zero missing values**.

---

# 📅 Date Conversion

## 9. Convert Admission and Discharge Dates

The `Admission_Date` and `Discharge_Date` columns are converted into datetime format.

```python
df['Admission_Date'] = pd.to_datetime(
    df['Admission_Date'],
    dayfirst=True
)

df['Discharge_Date'] = pd.to_datetime(
    df['Discharge_Date'],
    dayfirst=True
)
```

The `dayfirst=True` option is used because the dataset uses the **DD-MM-YYYY** date format.

After conversion, both columns have:

```text
datetime64[ns]
```

---

# 🏥 Admission Type Analysis

## 10. Check Medical Code Values

```python
df['Medical_Code'].isnull()
```

This checks whether any medical code values are missing.

The dataset contains **no missing Medical_Code values**.

---

## 11. Admission Type Distribution

```python
print(df['Admission_Type'].value_counts())
```

### Original Admission Type Counts

| Admission Type | Number of Patients |
| -------------- | -----------------: |
| Routine        |                196 |
| Emergency      |                188 |
| Urgent         |                116 |

---

## 12. Convert Admission Type to Lowercase

```python
df['Admission_Type'] = df['Admission_Type'].str.lower()
```

This converts the admission type values into lowercase for consistent data processing.

For example:

```text
Routine → routine
Emergency → emergency
Urgent → urgent
```

---

# 🏨 Hospital Stay Analysis

## 13. Calculate Hospital Stay Duration

A new column called `Hospital_Stay_Days` is created.

```python
df['Hospital_Stay_Days'] = (
    df['Discharge_Date'] - df['Admission_Date']
).dt.days
```

### Formula

```text
Hospital Stay Days = Discharge Date - Admission Date
```

This calculates the number of days each patient stayed in the hospital.

---

## 📊 Hospital Stay Statistics

```python
df['Hospital_Stay_Days'].describe()
```

### Results

| Statistic |      Value |
| --------- | ---------: |
| Count     |        500 |
| Mean      | 2.744 days |
| Minimum   |      1 day |
| Maximum   |    10 days |
| Median    |     2 days |

The average hospital stay is approximately **2.74 days**.

---

# 💰 Billing Analysis

The billing amount is analyzed using the `describe()` function.

```python
print(df['Billing_Amount'].describe())
```

### Billing Statistics

| Statistic |    Value |
| --------- | -------: |
| Count     |      500 |
| Mean      | 7249.001 |
| Minimum   |     2300 |
| Maximum   |    14200 |
| Median    |     6950 |

The average billing amount is approximately **7249.00**.

---

# 📊 Final Analysis

The final analysis includes:

* Patient demographic information
* Age statistics
* Medical conditions
* Admission types
* Medical codes
* Billing amounts
* Admission and discharge dates
* Hospital stay duration
* Missing-value checking
* Date conversion
* Data cleaning

---

# 🔑 Key Findings

* The dataset contains **500 patient records**.
* There are **9 columns** in the original dataset.
* No missing values were found.
* The average patient age is approximately **50.11 years**.
* Patient ages range from **22 to 78 years**.
* The average billing amount is approximately **7249.00**.
* Billing amounts range from **2300 to 14200**.
* The dataset contains **Routine, Emergency, and Urgent** admissions.
* Routine admissions: **196**
* Emergency admissions: **188**
* Urgent admissions: **116**
* The average hospital stay is approximately **2.74 days**.
* Hospital stays range from **1 to 10 days**.

---

# 🎯 Conclusion

This project demonstrates how Python can be used for **healthcare data analysis**.

Pandas was used for loading, cleaning, transforming, and analyzing the dataset. Date conversion was performed to calculate hospital stay duration, while statistical analysis was used to understand patient age, billing amount, and admission patterns.

The project provides a basic understanding of **patient information, hospital admissions, treatment billing, and hospital stay duration** using Python data analysis techniques.

---

## 👨‍💻 Author

**Karthihai Selvan**


