# 📊 Superstore Sales Data Analysis using Python

## 📌 Project Overview

This project performs Exploratory Data Analysis (EDA) on the Superstore Sales dataset using Python. The goal is to understand sales performance, analyze different product categories, calculate delivery times, and visualize important business insights through charts.

---

## 🎯 Objectives

- Load and explore the Superstore dataset.
- Understand the dataset structure and data types.
- Convert date columns into datetime format.
- Calculate the delivery time for each order.
- Check for missing values.
- Analyze total sales by product category.
- Visualize sales distribution and category-wise sales.

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Google Colab / Jupyter Notebook

---

## 📂 Dataset Information

The dataset contains **10,194 records** and **21 columns**, including:

- Order ID
- Order Date
- Ship Date
- Ship Mode
- Customer Name
- Segment
- City
- State
- Region
- Category
- Sub-Category
- Product Name
- Sales
- Quantity
- Discount
- Profit

---

## 📋 Project Workflow

### 1. Import Required Libraries

The following libraries are imported:

- pandas
- numpy
- matplotlib.pyplot
- seaborn

---

### 2. Load the Dataset

The Superstore dataset is loaded using:

```python
pd.read_csv()
```

---

### 3. Explore the Dataset

The following functions are used:

- `head()`
- `info()`
- `describe()`

These provide an overview of the data, data types, and statistical summary.

---

### 4. Data Preprocessing

- Converted **Order Date** and **Ship Date** into datetime format.
- Created a new column named **Delivery Days** by calculating the difference between shipping date and order date.

```python
Delivery Days = Ship Date - Order Date
```

---

### 5. Data Validation

Checked for missing values using:

```python
df.isnull().sum()
```

Result:
- No missing values were found.

---

### 6. Sales Analysis

Calculated the total sales for each product category using:

```python
df.groupby('Category')['Sales'].sum()
```

Categories:

- Furniture
- Office Supplies
- Technology

---

### 7. Data Visualization

#### Sales by Category
- Bar chart showing total sales for each product category.

#### Sales Distribution
- Histogram displaying the distribution of sales values.

---

## 📈 Key Findings

- The dataset contains no missing values.
- Technology has the highest total sales.
- Furniture is the second highest-selling category.
- Office Supplies also contributes significantly to overall sales.
- Delivery days were successfully calculated for each order.
- Sales values are unevenly distributed, with many small sales and a few very high sales.

---

## 📁 Files Included

```
Superstore_Sales_Analysis.ipynb
samplesuperstore.csv
README.md
```

---

## ▶️ How to Run

1. Open Google Colab or Jupyter Notebook.
2. Upload the dataset (`samplesuperstore.csv`).
3. Open the notebook.
4. Run all cells in sequence.
5. View the generated tables and visualizations.

---

## 📊 Output

The project generates:

- Dataset preview
- Dataset information
- Statistical summary
- Delivery Days calculation
- Missing value analysis
- Category-wise sales summary
- Sales by Category bar chart
- Sales Distribution histogram

---

## 🚀 Future Enhancements

- Monthly sales trend analysis
- Regional sales analysis
- Profit analysis
- Customer segmentation
- Discount impact on profit
- Interactive dashboards using Plotly or Power BI

---

## 👨‍💻 Author

**Karthihai Selvan**

