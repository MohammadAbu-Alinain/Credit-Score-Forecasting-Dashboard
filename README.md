# 📊 Credit Score Forecasting Dashboard

## 🧾 Project Overview

This project presents an **interactive Power BI dashboard** designed to forecast and analyze **credit scores** based on various demographic and financial indicators. The dashboard is powered by a CSV dataset that has undergone rigorous data preparation using Python and Power Query, with analytical logic implemented via **DAX functions**.

The goal is to assist financial institutions, analysts, and decision-makers in identifying patterns, risk categories, and forecasted creditworthiness among customers.

---

## 📂 Data Source

- Format: `.csv` file
- Contains demographic, financial, and credit-related attributes
- Source imported and cleaned using:
  - **Python** for preprocessing (missing values, encoding, scaling)
  - **Power Query** for model shaping and transformation inside Power BI

---

## 🧹 Data Preparation

### 🐍 Python (Pre-Processing)

Notebook: `Data preparation in python.ipynb`

Key steps:
- Handling **missing values** and outliers
- Label encoding for categorical variables
- Feature scaling (normalization or standardization)
- Exporting clean data to be imported into Power BI

### 🧪 Power Query (Transformation)

- Column renaming and type casting
- Removing null/irrelevant records
- Merging and grouping tables if needed
- Creating custom calculated columns for DAX models

---

## 📈 Dashboard Components

### 1. **Credit Score Distribution**
- Shows the proportion of customers by credit score category (Good, Average, Poor).
- Helps segment customers for marketing, risk, or lending purposes.

### 2. **Age vs Credit Score**
- Visual correlation between a customer's age and their creditworthiness.
- Helps identify age brackets with higher/lower credit risk.

### 3. **Income Level vs Credit Score**
- Reveals trends in how income brackets relate to credit scores.
- Supports segmentation of clients based on financial capacity.

### 4. **Employment Type Analysis**
- Visual breakdown of credit scores by employment type (e.g., Self-employed, Salaried).
- Supports risk analysis by employment sector.

### 5. **Forecasted Credit Score Trends**
- Time-based prediction of changes in credit scores using forecast tools in Power BI.
- Powered by DAX measures and forecasting tools.

### 6. **KPI Cards**
- Dynamic tiles showing total customers, average credit score, percentage of "Good" scores, etc.

---

## 🔢 DAX Measures and Calculations

Custom DAX functions used for:
- Creating calculated columns for score classification
- Aggregating customer segments
- Time intelligence for forecasting
- Percentage calculations and risk flags

Examples:
```DAX
Credit Category = 
SWITCH(TRUE(),
    'Data'[CreditScore] >= 700, "Good",
    'Data'[CreditScore] >= 500, "Average",
    "Poor"
)

Good Score % = 
DIVIDE(
    CALCULATE(COUNTROWS('Data'), 'Data'[Credit Category] = "Good"),
    COUNTROWS('Data')
)
```

---

## 🚀 Performance Optimization

To improve the responsiveness and efficiency of the Power BI dashboard, several visual-level filters and slicers were implemented.

### 🔧 Optimization Strategies:

- **Applied visual-level filters** to high-cost visuals like:
  - **Types of Loans by Customer Count**
  - **Distribution of Occupation**
- These filters help restrict the volume of data rendered at once, which significantly reduces query time and visual refresh duration.
- Used slicers for key attributes (e.g., customer segment, date range) to enable dynamic data scoping.
- Avoided complex DAX measures with high cardinality where possible, by pre-calculating in Power Query.

### ⏱ Before vs After (Visual Insight):

- The "Types of Loans by Customer Count" visual dropped from nearly **478ms** to a much lower refresh time after filter application.
- The "Distribution of Occupation" also improved from **195ms** to a better runtime.
- This results in a **faster, more fluid user experience** with minimized wait time on dashboard interactions.

These optimizations ensure that the dashboard scales better with growing data and maintains a responsive experience for end users.

---

## 🧠 Use Cases

- Credit scoring and loan risk analysis
- Customer segmentation
- Predictive analytics in financial services
- Executive reporting dashboards

---

## 🛠 Tools Used

- Power BI (Visualization & DAX)
- Python (Data preparation with Pandas & Scikit-learn)
- Power Query (ETL inside Power BI)
- CSV files as data sources

