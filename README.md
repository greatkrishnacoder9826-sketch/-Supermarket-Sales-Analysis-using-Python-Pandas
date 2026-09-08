# 🛒 Supermarket Sales Analysis using Python & Pandas

> **Exploratory Data Analysis (EDA) project on supermarket sales transactions using Python, Pandas and NumPy.**

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge\&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge\&logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-Analysis-013243?style=for-the-badge\&logo=numpy)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge\&logo=jupyter)
![Status](https://img.shields.io/badge/Project-Completed-success?style=for-the-badge)

---

## 📌 Project Overview

This project focuses on analyzing supermarket transaction data to understand **sales performance, customer behavior, product performance, branch-level performance, payment methods, ratings, and transaction categories**.

The analysis was performed using **Python, Pandas and NumPy** in a Jupyter Notebook.

The dataset contains **1,000 supermarket transactions** with information about:

* Branch and City
* Customer Type
* Gender
* Product Line
* Unit Price
* Quantity
* Tax
* Sales Revenue
* Date & Time
* Payment Method
* Cost of Goods Sold
* Gross Income
* Customer Rating

The notebook contains multiple business-oriented questions and uses Pandas operations such as `groupby()`, `value_counts()`, `sort_values()`, `agg()`, filtering, custom functions and percentage calculations.

---

## 🎯 Objectives

The main objectives of this project are:

1. Analyze total sales across different cities.
2. Compare gross income across branches.
3. Identify the best and worst-performing product lines.
4. Analyze average unit prices.
5. Find high-value transactions.
6. Segment transactions into **Low, Medium and High** sales categories.
7. Compare Member and Normal customers.
8. Analyze sales by gender.
9. Analyze customer ratings.
10. Study product-line purchasing behavior.
11. Calculate average quantity sold.
12. Identify transactions with high unit prices.
13. Perform conditional filtering and aggregation.

---

## 🗂️ Dataset

The dataset contains **1,000 rows and 17 columns** before feature engineering.

### Important Columns

| Column                    | Description                         |
| ------------------------- | ----------------------------------- |
| `Invoice ID`              | Unique transaction identifier       |
| `Branch`                  | Supermarket branch                  |
| `City`                    | City where the transaction occurred |
| `Customer type`           | Member or Normal                    |
| `Gender`                  | Customer gender                     |
| `Product line`            | Product category                    |
| `Unit price`              | Price per product unit              |
| `Quantity`                | Number of units purchased           |
| `Tax 5%`                  | Applied tax                         |
| `Sales`                   | Total transaction sales             |
| `Date`                    | Transaction date                    |
| `Time`                    | Transaction time                    |
| `Payment`                 | Payment method                      |
| `cogs`                    | Cost of goods sold                  |
| `gross margin percentage` | Gross margin percentage             |
| `gross income`            | Gross income                        |
| `Rating`                  | Customer rating                     |

---

## 🛠️ Technologies Used

### Programming Language

* Python

### Libraries

* Pandas
* NumPy

### Development Environment

* Jupyter Notebook

---

## 🔄 Analysis Workflow

```text
Raw Dataset
     ↓
Load Dataset
     ↓
Data Exploration
     ↓
Grouping & Aggregation
     ↓
Filtering
     ↓
Sorting
     ↓
Feature Engineering
     ↓
Customer Analysis
     ↓
Product Analysis
     ↓
Sales Analysis
     ↓
Business Insights
```

---

## 📊 Key Analysis Performed

### 🏙️ Sales by City

Total sales were calculated for each city using:

```python
df.groupby('City')['Sales'].sum()
```

The analysis produced total sales values for Mandalay, Naypyitaw and Yangon.

---

### 🏢 Gross Income by Branch

Branch-level gross income was calculated using:

```python
df.groupby('Branch')['gross income'].sum()
```

This allowed comparison of the overall profitability contribution of each branch.

---

### 🛍️ Product Line Performance

Sales and quantity were aggregated for every product line:

```python
df.groupby('Product line')[['Sales', 'Quantity']].sum()
```

The analysis showed that **Food and Beverages** generated the highest total sales among the product lines in this dataset.

---

### 💰 Highest-Value Transactions

The top transactions based on sales were identified using:

```python
df['Sales'].sort_values(ascending=False).head(10)
```

The highest transaction in the notebook was approximately **1042.65** in sales.

---

## 📈 Feature Engineering

A new feature called `Division` was created to categorize transactions according to their sales value.

### Classification Rules

```text
Sales < 200       → Low
200 ≤ Sales < 700 → Medium
Sales ≥ 700       → High
```

Implemented using a custom Python function:

```python
def categorize(sales):
    if sales < 200:
        return "Low"
    elif sales < 700:
        return "Medium"
    else:
        return "High"

df['Division'] = df['Sales'].apply(categorize)
```

This feature was then used for further transaction analysis.

---

## 👥 Customer Analysis

The project compares:

* Member customers
* Normal customers

Customer counts were analyzed by city using:

```python
df.groupby('City')['Customer type'].value_counts()
```

The notebook also compares the percentage contribution of Member and Normal customers to total sales.

---

## 👨‍👩‍👧 Gender-Based Analysis

Sales contribution was also analyzed by gender:

```python
df.groupby('Gender')['Sales'].sum() / df['Sales'].sum() * 100
```

The analysis found approximately:

* **Female:** 60.28%
* **Male:** 39.72%

of total sales contribution in this dataset.

---

## ⭐ Customer Rating Analysis

Average customer ratings were compared between customer types:

```python
df.groupby('Customer type')['Rating'].mean()
```

The notebook calculated average ratings of approximately:

* Member → **6.92**
* Normal → **7.04**

---

## 📦 Quantity Analysis

Average quantity sold was calculated for each product line:

```python
df.groupby('Product line')['Quantity'].mean()
```

The project also identifies the product line with the highest average quantity sold.

---

## 💵 Unit Price Analysis

Minimum and maximum unit prices were calculated for every product line:

```python
df.groupby('Product line')['Unit price'].agg(['min', 'max'])
```

This provides a quick understanding of the price range across different product categories.

---

## 🔎 Conditional Analysis

The project also performs targeted filtering, for example identifying transactions where:

```python
df['Unit price'] > 50
```

This produced a filtered dataset of higher-priced products/transactions for further analysis.

---

## 💡 Business Questions Answered

This project explores questions such as:

* Which city generates the highest revenue?
* Which branch generates the highest gross income?
* Which product line generates the most revenue?
* Which product line generates the least revenue?
* What is the average unit price for each branch?
* What are the top 10 highest-value transactions?
* How can transactions be classified based on sales?
* How many Member and Normal customers are present in each city?
* Which customer type contributes more to sales?
* Which gender contributes more to total sales?
* Which customer type has the highest average rating?
* Which product line has the highest average quantity?
* What are the minimum and maximum product prices?
* Which transactions have unit prices above 50?

---

## 📁 Project Structure

```text
Supermarket-Sales-Analysis/
│
├── Supermarket Analysis.ipynb
├── SuperMarket Analysis.csv
├── README.md
│
└── outputs/
    └── analysis_results.csv
```

---

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/Supermarket-Sales-Analysis.git
```

### 2. Navigate into the project

```bash
cd Supermarket-Sales-Analysis
```

### 3. Install dependencies

```bash
pip install pandas numpy jupyter
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open the notebook

Open:

```text
Supermarket Analysis.ipynb
```

Make sure the CSV dataset is available in the same project directory.

---

## 📚 Skills Demonstrated

This project demonstrates practical knowledge of:

* Python
* Pandas
* NumPy
* DataFrame manipulation
* Data filtering
* `groupby()`
* `value_counts()`
* Aggregation
* Sorting
* Conditional logic
* Custom functions
* Feature engineering
* Percentage analysis
* Business-oriented data analysis
* Exploratory Data Analysis

---

## 🔮 Future Improvements

The project can be extended with:

* 📊 Matplotlib visualizations
* 📈 Seaborn statistical charts
* 📅 Time-series sales analysis
* 🏆 KPI dashboard
* 💳 Payment-method analysis
* 🧑‍🤝‍🧑 Customer segmentation
* 📍 Branch performance dashboard
* 📊 Power BI dashboard
* 🤖 Sales prediction using Machine Learning
* 🌐 Interactive Streamlit dashboard

---

## 👨‍💻 Author

**Krishna Great**

Aspiring **Data Scientist | ML/DL Engineer | GenAI Developer**

### Areas of Interest

```text
Python
Data Science
Machine Learning
Deep Learning
Generative AI
Agentic AI
Data Analytics
```

---

## ⭐ Support

If you found this project useful, consider giving the repository a ⭐ on GitHub.

---

## 📜 License

This project is created for **learning, practice and educational purposes**.
