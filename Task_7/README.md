# 📊 Students Performance Analysis

## 📌 Project Overview

This project analyzes **student performance data** using Python. The dataset contains information about gender, race/ethnicity, parental education, lunch type, test preparation, and student scores.

The main aim of this project is to analyze student marks and calculate **total marks and percentage**.

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Google Colab

## 📂 Dataset

The dataset contains **1000 student records and 8 original columns**.

Main columns include:

* Gender
* Race/Ethnicity
* Parental Level of Education
* Lunch
* Test Preparation Course
* Math Score
* Reading Score
* Writing Score

## 🔍 Data Cleaning

The categorical columns were cleaned by removing extra spaces and standardizing the text format.

```python
for col in categorical_columns:
    df[col] = df[col].str.strip().str.title()
```

This makes values more consistent for analysis.

## 📈 Score Analysis

The project analyzes:

* Math Score
* Reading Score
* Writing Score

The average scores are:

| Subject | Average |
| ------- | ------: |
| Math    |   66.09 |
| Reading |   69.17 |
| Writing |   68.05 |

The scores range from 0–100 for Math and up to 100 for Reading and Writing.

## 🧮 Total Marks

A new column called `total marks` is created to calculate the student's total score.

```python
df['total marks'] = df["math score"] + df["reading score"] + df["reading score"]
```

## 📊 Percentage

A percentage column is calculated using:

```python
df['percentage'] = (df['total marks'] / 300) * 100
```

This gives the student's percentage based on the calculated total marks.

## 🧹 Missing Value Check

The dataset was checked for missing values.

```python
df.isnull().sum()
```

There are **no missing values** in the analyzed columns.

## 📊 Outlier Analysis

The **IQR method** was used to identify outliers in Math scores.

```python
Q1 = df['math score'].quantile(0.25)
Q3 = df['math score'].quantile(0.75)

IQR = Q3 - Q1

outliers = df[
    (df['math score'] < (Q1 - 1.5 * IQR)) |
    (df['math score'] > (Q3 + 1.5 * IQR))
]
```

The analysis found **8 outliers** in the Math Score column.

## 🎯 Conclusion

This project demonstrates how Python can be used to analyze student performance data.

The analysis includes:

* Data cleaning
* Score analysis
* Total marks calculation
* Percentage calculation
* Missing value checking
* Outlier detection

Overall, the project provides a simple understanding of student academic performance using **Pandas, NumPy, Matplotlib, and Seaborn**.

## 👨‍💻 Author

**Karthihai Selvan**


