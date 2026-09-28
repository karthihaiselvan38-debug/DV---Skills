# 📈 AAPL Stock Data Analysis

## 📌 Project Overview

This project analyzes **Apple Inc. (AAPL) stock market data** using Python. The dataset contains weekly stock information such as Open, High, Low, Close, Adjusted Close, and Volume.

The main purpose of this project is to understand the stock price movement, daily changes, returns, trading volume, and basic statistical information.

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Google Colab

---

## 📂 Dataset

The dataset used in this project is **AAPL.csv**, which contains **184 rows and 7 columns**.

### Dataset Columns

| Column    | Description              |
| --------- | ------------------------ |
| Date      | Date of the stock record |
| Open      | Opening stock price      |
| High      | Highest stock price      |
| Low       | Lowest stock price       |
| Close     | Closing stock price      |
| Adj Close | Adjusted closing price   |
| Volume    | Number of shares traded  |

---

## 🔍 Data Analysis Performed

### 1. Load the Dataset

The AAPL CSV file is loaded using Pandas.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/AAPL.csv")
```

### 2. Display First Few Records

```python
print(df.head())
```

This is used to understand the structure and values of the dataset.

---

### 3. Check Dataset Shape

```python
print(df.shape)
```

**Result:**

```text
(184, 7)
```

The dataset contains **184 rows and 7 columns**.

---

### 4. Check Data Information

```python
print(df.info())
```

The dataset contains:

* 5 floating-point columns
* 1 integer column
* 1 object column (`Date`)
* No missing values

---

### 5. Statistical Analysis

```python
print(df.describe())
```

The `describe()` function provides statistical information such as:

* Count
* Mean
* Standard deviation
* Minimum value
* 25th percentile
* Median
* 75th percentile
* Maximum value

---

### 6. Missing Value Check

```python
print(df.isnull().sum())
```

The result shows that there are **no missing values** in the dataset.

```text
Date         0
Open         0
High         0
Low          0
Close        0
Adj Close    0
Volume       0
```

---

## 📊 Daily Price Analysis

A new column called **Daily Delta** is created to find the difference between the closing and opening prices.

```python
df['Daily Delta'] = df['Close'] - df['Open']
```

### Formula

```text
Daily Delta = Close Price - Open Price
```

A positive value means the closing price is higher than the opening price.

A negative value means the closing price is lower than the opening price.

---

## 💰 Average Stock Price

The average Open and Close prices are calculated.

```python
avg_open = df['Open'].mean()
avg_close = df['Close'].mean()

print(f"Average Open Price: ${avg_open:.2f}")
print(f"Average Close Price: ${avg_close:.2f}")
```

### Result

```text
Average Open Price: $127.04
Average Close Price: $127.35
```

---

## 📈 Daily Return Calculation

The percentage change between the Open and Close prices is calculated using:

```python
df["Daily_Return"] = (
    (df["Close"] - df["Open"]) / df["Open"]
) * 100
```

### Formula

```text
Daily Return = ((Close - Open) / Open) × 100
```

This helps to understand the percentage movement of the stock price during each period.

---

## 📦 Trading Volume Analysis

The trading volume is analyzed to find the average, maximum, and minimum number of shares traded.

```python
average_volume = df["Volume"].mean()
maximum_volume = df["Volume"].max()
minimum_volume = df["Volume"].min()

print("Average Volume:", average_volume)
print("Maximum Volume:", maximum_volume)
print("Minimum Volume:", minimum_volume)
```

### Results

```text
Average Volume: 191016776.11
Maximum Volume: 500363000
Minimum Volume: 38398505
```

---

## 📋 Final Dataset

After the analysis, two additional columns are added:

* `Daily Delta`
* `Daily_Return`

Therefore, the final dataset contains **9 columns**.

---

## 🔑 Key Findings

* The dataset contains **184 stock records**.
* There are **7 original columns**.
* No missing values were found.
* The average Open price was approximately **$127.04**.
* The average Close price was approximately **$127.35**.
* The average trading volume was approximately **191 million shares**.
* The maximum trading volume was **500,363,000 shares**.
* Daily Delta and Daily Return were calculated to analyze price movement.

---

## 🎯 Conclusion

This project demonstrates how Python can be used to perform basic **stock market data analysis**. Pandas was used for data loading, cleaning, and statistical analysis, while NumPy and Matplotlib were included for numerical operations and visualization.

The analysis helps understand **Apple stock price movements, daily returns, and trading volume** from the given historical dataset.

---

## 👨‍💻 Author

**Karthihai Selvan**


