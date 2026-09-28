# 🏥 Healthcare Data Analysis

## 📌 Project Overview

This project analyzes a large **Healthcare Dataset** using Python. The dataset contains information about patients, medical conditions, admission details, hospitals, insurance providers, billing amounts, medications, test results, and discharge dates.

The main objective of this project is to explore healthcare data and identify useful patterns related to **medical conditions, insurance billing, patient admissions, hospital stay duration, and relationships between numerical variables**.

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

The dataset contains:

* **55,500 patient records**
* **15 columns**

### Dataset Columns

| Column             | Description                 |
| ------------------ | --------------------------- |
| Name               | Patient name                |
| Age                | Patient age                 |
| Gender             | Patient gender              |
| Blood Type         | Patient blood group         |
| Medical Condition  | Medical condition diagnosed |
| Date of Admission  | Patient admission date      |
| Doctor             | Doctor name                 |
| Hospital           | Hospital name               |
| Insurance Provider | Insurance company           |
| Billing Amount     | Amount billed for treatment |
| Room Number        | Patient room number         |
| Admission Type     | Type of admission           |
| Discharge Date     | Patient discharge date      |
| Medication         | Medication provided         |
| Test Results       | Medical test result         |

---

# 🔍 Data Analysis

## 1. Import Required Libraries

```python id="1n0a7z"
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

The libraries are used for:

* **Pandas** – Data loading and data analysis
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization

---

## 2. Load the Dataset

```python id="3kqj9p"
df = pd.read_csv("/healthcare_dataset.csv")
```

The healthcare dataset is loaded into a Pandas DataFrame.

---

## 3. Display the Dataset

```python id="7y8j0m"
df
```

The dataset contains **55,500 rows and 15 columns**.

---

## 4. Display First Five Records

```python id="5k9q2r"
df.head()
```

The `head()` function displays the first five records of the dataset.

---

# 📋 Dataset Information

## 5. Check Dataset Information

```python id="2c6m8x"
df.info()
```

The dataset contains:

* 55,500 records
* 15 columns
* 2 integer columns
* 1 floating-point column
* 12 object columns
* No missing values in the displayed dataset

The `info()` function is used to understand the data types and structure of the dataset.

---

# 💰 Billing Analysis

## 6. Billing Amount by Medical Condition and Insurance Provider

The billing amount is grouped by **Medical Condition** and **Insurance Provider**.

```python id="6p3v8a"
billing = df.groupby(
    ["Medical Condition", "Insurance Provider"]
)["Billing Amount"].sum().unstack()

billing
```

This creates a table showing the total billing amount for each medical condition and insurance provider.

### Medical Conditions

The dataset contains the following major medical conditions:

* Arthritis
* Asthma
* Cancer
* Diabetes
* Hypertension
* Obesity

### Insurance Providers

The dataset contains:

* Aetna
* Blue Cross
* Cigna
* Medicare
* UnitedHealthcare

---

## 7. Billing Visualization

A stacked bar chart is created to compare billing amounts.

```python id="9d4x1b"
billing.plot(
    kind="bar",
    stacked=True,
    figsize=(10, 6)
)

plt.title(
    "Billing Amount by Medical Condition and Insurance Provider"
)

plt.xlabel("Medical Condition")
plt.ylabel("Billing Amount")
plt.show()
```

### Purpose

This visualization helps compare:

* Total billing for different medical conditions
* Contribution of different insurance providers
* Differences in healthcare billing patterns

---


