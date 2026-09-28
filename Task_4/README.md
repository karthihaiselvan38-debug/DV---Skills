# 📈 Shopify Stock Data Analysis

## 📌 Project Overview

This project analyzes **Shopify stock market data** using Python. The dataset contains historical stock information such as opening price, highest price, lowest price, closing price, adjusted closing price, and trading volume.

The main objective of this project is to understand **Shopify stock price movement and daily returns** using data visualization and statistical analysis.

---

## 🛠️ Technologies Used

* Python
* Pandas
* Matplotlib
* Seaborn
* Google Colab

---

## 📂 Dataset

The dataset used in this project is **shopify_stock.csv**.

The dataset contains historical Shopify stock market records.

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

### 1. Import Required Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

These libraries are used for:

* **Pandas** – Data loading and data manipulation
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical data visualization

---

### 2. Load the Dataset

```python
df = pd.read_csv("/shopify_stock.csv")
```

The Shopify stock dataset is loaded into a Pandas DataFrame.

---

### 3. Display the First Five Records

```python
df.head()
```

The `head()` function displays the first five rows of the dataset.

Example data includes:

* Date
* Open
* High
* Low
* Close
* Adjusted Close
* Volume

---

## 📅 Date Conversion

The date column is converted into a proper datetime format.

```python
df['date'] = pd.to_datetime(df['date'], utc=True)
```

This makes it easier to perform time-based analysis and create time-series visualizations.

---

# 📈 1. Shopify Closing Price Over Time

A line chart is created to understand how Shopify's closing price changes over time.

```python
plt.figure(figsize=(8, 5))

sns.lineplot(x='date', y='close', data=df)

plt.title('Shopify Closing Price Over Time')
plt.xlabel('Date')
plt.ylabel('Closing Price')
plt.grid(True)

plt.show()
```

### Purpose

The line chart helps to identify:

* Stock price trends
* Price increases and decreases
* Long-term movement
* Major changes in closing price

---

# 📊 2. Shopify Daily Return Distribution

A new column called `Daily_Return` is created using the percentage change in closing price.

```python
df['Daily_Return'] = df['close'].pct_change()
```

### Formula

```text
Daily Return = (Current Close - Previous Close) / Previous Close
```

The distribution of daily returns is visualized using a histogram.

```python
plt.figure(figsize=(6, 5))

sns.histplot(
    df['Daily_Return'].dropna(),
    bins=60,
    kde=True,
    color='darkred'
)

plt.title('Shopify Daily Returns')
plt.xlabel('Daily Return')
plt.ylabel('Frequency')
plt.grid(True)

plt.show()
```

### Purpose

The histogram helps understand:

* How daily returns are distributed
* Frequency of positive and negative returns
* Common return values
* Possible extreme return values

---

# 📉 3. KDE Plot of Daily Returns

A KDE (Kernel Density Estimate) plot is used to visualize the distribution of Shopify's daily returns smoothly.

```python
plt.figure(figsize=(10, 6))

sns.kdeplot(
    df['Daily_Return'].dropna(),
    fill=True,
    color='blue'
)

plt.title('KDE Plot of Shopify Daily Returns')
plt.xlabel('Daily Return')
plt.ylabel('Density')
plt.grid(True)

plt.show()
```

### Purpose

The KDE plot provides a smooth representation of the daily return distribution.

It helps identify:

* The central region of daily returns
* Distribution shape
* Concentration of returns
* Spread of daily returns

---

## 📊 Visualizations Created

This project contains three main visualizations:

### 1. Closing Price Line Chart

Shows the movement of Shopify's closing price over time.

### 2. Daily Return Histogram

Shows the frequency distribution of daily returns.

### 3. KDE Plot

Shows a smooth probability-density representation of daily returns.

---

## 🔑 Key Analysis

The project focuses on two important aspects of Shopify stock data:

### Stock Price Trend

The closing-price line chart is used to understand how Shopify's stock price changes over the selected historical period.

### Daily Returns

Daily returns are calculated using the percentage change in closing price. The histogram and KDE plot are then used to study the distribution of these returns.

---

## 🎯 Conclusion

This project demonstrates how Python can be used to analyze and visualize **Shopify stock market data**.

Pandas is used for data processing, while Matplotlib and Seaborn are used to create visualizations.

The analysis provides a simple understanding of:

* Shopify closing price trends
* Daily stock returns
* Return distribution
* Statistical patterns in stock data

Overall, the project demonstrates the use of **Python, Pandas, Matplotlib, and Seaborn for financial data analysis and visualization**.

---

## 👨‍💻 Author

**Karthihai Selvan**


