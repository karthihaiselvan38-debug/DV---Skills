# 📊 Superstore Sales Data Analysis

## 📌 Project Overview

The **Superstore Sales Data Analysis** project is a data analysis and visualization project developed using **Python, Pandas, NumPy, Matplotlib, and Seaborn**.

The project analyzes sales transaction data to understand **sales performance, profitability, discount impact, category performance, and delivery time**.

The analysis uses exploratory data analysis (EDA) techniques and different visualization methods such as **bar plots, box plots, scatter plots, histograms, and correlation heatmaps** to identify meaningful patterns and business insights.

---

## 🎯 Objectives

The main objectives of this project are:

* Analyze overall sales and profit performance.
* Compare sales across different product categories.
* Compare profit across different categories.
* Understand the distribution of sales values.
* Analyze profit variation and identify potential outliers.
* Study the relationship between discount and profit.
* Analyze correlations between numerical variables.
* Calculate delivery time using order and shipping dates.
* Identify important business patterns from the dataset.
* Present findings using clear and informative visualizations.

---

## 🗂️ Dataset

The project uses the **Superstore Sales Dataset**.

### Dataset Information

* **Number of Records:** 10,194
* **Number of Columns:** 21 original columns
* **Additional Column Created:** `Delivery Days`
* **Final Number of Columns:** 22

### Original Columns

| Column         | Description                        |
| -------------- | ---------------------------------- |
| Row ID         | Unique row identifier              |
| Order ID       | Unique order identifier            |
| Order Date     | Date when the order was placed     |
| Ship Date      | Date when the order was shipped    |
| Ship Mode      | Shipping method used for the order |
| Customer ID    | Unique customer identifier         |
| Customer Name  | Name of the customer               |
| Segment        | Customer segment                   |
| Country/Region | Country or region of the customer  |
| City           | Customer city                      |
| State/Province | Customer state or province         |
| Postal Code    | Postal code of the customer        |
| Region         | Sales region                       |
| Product ID     | Unique product identifier          |
| Category       | Product category                   |
| Sub-Category   | Product sub-category               |
| Product Name   | Name of the product                |
| Sales          | Sales amount                       |
| Quantity       | Number of products ordered         |
| Discount       | Discount applied to the order      |
| Profit         | Profit generated from the order    |

### Derived Column

| Column        | Description                                         |
| ------------- | --------------------------------------------------- |
| Delivery Days | Number of days between the order date and ship date |

---

## 🛠️ Technologies Used

The following technologies and Python libraries were used:

* **Python**
* **Pandas** – Data loading, cleaning, transformation, and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical data visualization
* **Google Colab / Jupyter Notebook** – Development environment

---

## 📁 Project Structure

```text
Superstore-Sales-Data-Analysis/
│
├── samplesuperstore.csv
├── Superstore_Sales_Analysis.ipynb
├── README.md
└── requirements.txt
```

---

## 🔄 Project Workflow

The project follows the following data analysis workflow:

```text
Dataset
   ↓
Data Loading
   ↓
Data Understanding
   ↓
Data Cleaning
   ↓
Data Type Conversion
   ↓
Feature Engineering
   ↓
Exploratory Data Analysis
   ↓
Data Visualization
   ↓
Correlation Analysis
   ↓
Business Insights
```

---

# 🔍 Data Analysis

## 1. Import Required Libraries

The required Python libraries are imported using:

```python
import pandas as pd
import numpy as np

import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 2. Load the Dataset

The Superstore dataset is loaded using Pandas:

```python
df = pd.read_csv("/content/samplesuperstore.csv")
```

The first five records are displayed using:

```python
df.head()
```

---

## 3. Understand the Dataset

The `info()` function is used to understand:

* Number of rows
* Number of columns
* Column names
* Data types
* Non-null values

```python
df.info()
```

The dataset initially contains:

* **10,194 rows**
* **21 columns**

---

## 4. Statistical Summary

The `describe()` function is used to generate descriptive statistics for numerical columns.

```python
df.describe()
```

The analysis includes:

* Count
* Mean
* Standard deviation
* Minimum
* 25th percentile
* Median
* 75th percentile
* Maximum

---

# 🧹 Data Preprocessing

## 5. Convert Date Columns

The `Order Date` and `Ship Date` columns are converted from object/string format to datetime format.

```python
df['Order Date'] = pd.to_datetime(df['Order Date'])

df['Ship Date'] = pd.to_datetime(df['Ship Date'])
```

This conversion makes it easier to perform date-based calculations and analysis.

---

## 6. Calculate Delivery Days

A new feature called `Delivery Days` is created.

```python
df['Delivery Days'] = (
    df['Ship Date'] - df['Order Date']
).dt.days
```

This calculates the number of days taken between placing and shipping an order.

---

## 7. Check Product Categories

The unique product categories are identified using:

```python
df['Category'].unique()
```

The dataset contains three main categories:

* Furniture
* Office Supplies
* Technology

---

## 8. Check Missing Values

Missing values are checked using:

```python
df.isnull().sum()
```

### Result

No missing values were found in the dataset.

Therefore, no missing-value treatment was required for this analysis.

---

# 📊 Exploratory Data Analysis

## Part 1: Sales by Category

Sales are grouped by product category:

```python
category_sales = df.groupby('Category')['Sales'].sum()

print(category_sales)
```

### Category Sales

| Category        |  Total Sales |
| --------------- | -----------: |
| Furniture       | 754,747.7613 |
| Office Supplies | 731,893.3140 |
| Technology      | 839,893.2790 |

### Visualization

A bar plot is used to compare total sales across categories.

```python
category_sales.plot(
    kind='bar',
    figsize=(8,5)
)

plt.title("Sales by Category")
plt.ylabel("Total Sales")
plt.show()
```

### Insight

**Technology** generates the highest total sales among the three categories.

---

# 📈 Part 2: Sales Distribution

A histogram is used to understand the distribution of sales values.

```python
plt.figure(figsize=(8,5))

sns.histplot(
    df['Sales'],
    bins=30
)

plt.title("Sales Distribution")
plt.show()
```

### Purpose

The histogram helps identify:

* Distribution of sales
* Frequently occurring sales values
* Skewness
* Potential extreme sales values

---

# 📊 Part 3: Profit by Category

A bar plot is created to compare profit across categories.

```python
sns.barplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit by Category")
plt.show()
```

### Purpose

This visualization helps determine which product category has better average profitability.

---

# 📊 Part 4: Sales by Category

Sales are also visualized directly using a Seaborn bar plot.

```python
sns.barplot(
    data=df,
    x="Category",
    y="Sales"
)

plt.title("Sales Distribution by Category")
plt.show()
```

This visualization provides a category-level comparison of average sales per transaction.

---

# 📦 Part 5: Profit Distribution Using Box Plot

A box plot is used to analyze the distribution of profit values.

```python
sns.boxplot(
    data=df,
    y="Profit"
)

plt.title("Profit Distribution")
plt.show()
```

### Box Plot Helps Identify

* Median profit
* Quartiles
* Data spread
* Potential outliers
* Variability in profit

The dataset contains significant variation in profit values, including both negative and positive profits.

---

# 📦 Part 6: Profit Variation Across Categories

A category-wise box plot is created:

```python
sns.boxplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit Variation Across Categories")
plt.show()
```

### Purpose

This visualization helps compare:

* Profit distribution
* Median profit
* Profit variation
* Outliers

across different product categories.

---

# 💰 Part 7: Discount vs Profit Analysis

The project analyzes whether discounts have an impact on profitability.

The unique discount values are identified using:

```python
df["Discount"].unique()
```

A scatter plot is used to visualize the relationship between discount and profit.

```python
sns.scatterplot(
    data=df,
    x="Discount",
    y="Profit"
)

plt.title("Impact of Discount on Profit")
plt.show()
```

### Analysis

The scatter plot helps examine whether higher discounts are associated with lower profitability.

The analysis indicates a **negative relationship between discount and profit**, meaning that higher discounts tend to be associated with lower profit.

However, discount alone does not determine profit because other factors such as sales value, product category, quantity, and product-level pricing also influence profitability.

---

# 🔥 Part 8: Correlation Analysis

Correlation analysis is performed to understand relationships between numerical variables.

Numerical columns are selected using:

```python
numeric_df = df.select_dtypes(
    include="number"
)
```

The correlation matrix is calculated using:

```python
corr = numeric_df.corr()
```

### Correlation Matrix

| Variable      |  Sales | Quantity | Discount | Profit | Delivery Days |
| ------------- | -----: | -------: | -------: | -----: | ------------: |
| Sales         |  1.000 |    0.198 |   -0.028 |  0.481 |        -0.007 |
| Quantity      |  0.198 |    1.000 |    0.007 |  0.066 |         0.021 |
| Discount      | -0.028 |    0.007 |    1.000 | -0.219 |        -0.002 |
| Profit        |  0.481 |    0.066 |   -0.219 |  1.000 |        -0.004 |
| Delivery Days | -0.007 |    0.021 |   -0.002 | -0.004 |         1.000 |

---

## 🌡️ Correlation Heatmap

A heatmap is created to visually represent the correlation matrix.

```python
sns.heatmap(
    corr,
    annot=True
)

plt.title("Correlation Heatmap")
plt.show()
```

### Important Observations

* **Sales and Profit:** Positive correlation of approximately **0.481**.
* **Discount and Profit:** Negative correlation of approximately **-0.219**.
* **Sales and Quantity:** Positive correlation of approximately **0.198**.
* **Delivery Days and Profit:** Very weak correlation.
* **Delivery Days and Sales:** Very weak correlation.

Correlation indicates the strength of a linear relationship and does **not** necessarily imply causation.

---

# 📌 Key Business Insights

Based on the exploratory analysis, the following insights were identified:

### 1. Technology has the highest total sales

Technology generated approximately **839,893.28** in total sales, making it the highest-selling category in the dataset.

### 2. Furniture and Office Supplies also contribute significantly

Furniture generated approximately **754,747.76**, while Office Supplies generated approximately **731,893.31** in total sales.

### 3. Sales and profit have a moderate positive relationship

The correlation between Sales and Profit is approximately **0.481**, indicating that higher sales are generally associated with higher profit, although the relationship is not perfect.

### 4. Discount has a negative relationship with profit

The correlation between Discount and Profit is approximately **-0.219**. This suggests that higher discounts are generally associated with lower profitability.

### 5. Profit contains significant variation

The box plots show substantial variation in profit, including negative-profit transactions and extreme positive-profit values.

### 6. Delivery time has little linear relationship with sales and profit

The correlation values involving Delivery Days are close to zero, indicating a very weak linear relationship with Sales, Quantity, Discount, and Profit in this dataset.

---

# 📊 Visualizations Included

The project includes the following visualizations:

1. Sales by Category – Bar Plot
2. Sales Distribution – Histogram
3. Profit by Category – Bar Plot
4. Sales Distribution by Category – Bar Plot
5. Profit Distribution – Box Plot
6. Profit Variation Across Categories – Box Plot
7. Impact of Discount on Profit – Scatter Plot
8. Correlation Heatmap

---

# 📦 Installation

Clone the repository:

```bash
git clone https://github.com/your-username/Superstore-Sales-Data-Analysis.git
```

Navigate to the project directory:

```bash
cd Superstore-Sales-Data-Analysis
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

---

# 📋 Requirements

Create a file named `requirements.txt` with the following dependencies:

```text
pandas
numpy
matplotlib
seaborn
jupyter
```

---

# ▶️ How to Run the Project

### Option 1: Google Colab

1. Open Google Colab.
2. Upload `Superstore_Sales_Analysis.ipynb`.
3. Upload `samplesuperstore.csv`.
4. Update the CSV file path if required.
5. Run the notebook cells sequentially.

### Option 2: Jupyter Notebook

Install Jupyter:

```bash
pip install jupyter
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```text
Superstore_Sales_Analysis.ipynb
```

Run all cells sequentially.

---

# 📁 Files in This Repository

### `samplesuperstore.csv`

Contains the Superstore sales transaction data used for analysis.

### `Superstore_Sales_Analysis.ipynb`

Contains the complete Python code, data preprocessing, exploratory data analysis, statistical analysis, and visualizations.

### `requirements.txt`

Contains the Python libraries required to run the project.

### `README.md`

Provides project documentation, methodology, analysis, insights, and execution instructions.

---

# 🚀 Future Enhancements

The project can be further improved by:

* Creating an interactive **Power BI dashboard**.
* Performing time-series analysis of monthly and yearly sales.
* Analyzing sales by state and city.
* Identifying the most profitable products.
* Identifying loss-making products.
* Performing customer-level analysis.
* Creating sales and profit KPIs.
* Applying machine learning for sales or profit prediction.
* Adding interactive Plotly visualizations.
* Performing RFM customer segmentation.

---

# 🎓 Learning Outcomes

Through this project, the following skills were developed:

* Data loading using Pandas
* Data cleaning and preprocessing
* Date-time manipulation
* Feature engineering
* Exploratory Data Analysis (EDA)
* GroupBy operations
* Statistical analysis
* Correlation analysis
* Data visualization
* Business insight generation
* Python-based data analysis

---

# 👨‍💻 Author

**Karthihai Selvan**

This project was developed as a **Python Data Analysis and Exploratory Data Analysis project** using the Superstore dataset.

---

# ⭐ Conclusion

The Superstore Sales Data Analysis project demonstrates how Python can be used to transform raw sales data into meaningful business insights.

The analysis identifies category-level sales performance, profit variation, discount-profit relationships, delivery-time behavior, and correlations between numerical variables.

The project provides a strong foundation for further development into an **interactive business intelligence dashboard or predictive analytics project**.

---

## ⭐ If you found this project useful

If you find this project useful, consider giving the repository a **⭐ Star** on GitHub.
