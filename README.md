# Sales Performance Analysis

**Author:** Chinmay Kumar Gupta  
**College:** Harcourt Butler Technical University (HBTU), Kanpur  
**Tools:** Python, Pandas, Matplotlib, Seaborn  

---

## Project Overview

An end-to-end exploratory data analysis (EDA) on a retail sales dataset of 500 orders across 5 product categories and 4 regions. The goal was to identify revenue trends, profit drivers, and business improvement areas.

---

## Dataset

| Field | Description |
|---|---|
| Order_ID | Unique order identifier |
| Month | Month of order |
| Category | Product category (Electronics, Clothing, Furniture, Food, Books) |
| Region | Sales region (North, South, East, West) |
| Sales | Order revenue (₹) |
| Profit | Order profit (₹) |
| Quantity | Units sold |
| Discount | Discount applied (0–0.5) |

---

## Key Findings

1. **Books and Electronics** are the top revenue-generating categories (₹1.24L and ₹1.15L respectively)
2. **North region** leads sales with ₹1.43L — 26% of total revenue
3. **December** is the best-performing month (₹57,284) — holiday season effect
4. **38.8% of orders** have discounts above 30% — this is contributing to 16.8% loss-making orders
5. **High discounts are hurting profit margins** — scatter plot shows negative profit clusters at high discount values

---

## Business Recommendations

- **Reduce discounts above 30%** — nearly 17% of orders are loss-making, directly correlated with high discounts
- **Focus marketing spend on North and East regions** — highest revenue contributors
- **Stock up on Books and Electronics before December** — peak season demand spike observed
- **Investigate Furniture category** — lowest revenue (₹80K) and high profit variance

---

## Dashboard Preview

![Sales Dashboard](sales_dashboard.png)

---

## How to Run

```bash
git clone https://github.com/YOUR_USERNAME/sales-data-analysis
cd sales-data-analysis
pip install pandas matplotlib seaborn numpy
python analysis.py
```

---

## Skills Demonstrated

`Python` `Pandas` `Matplotlib` `Seaborn` `EDA` `Data Cleaning` `Data Visualisation` `Business Insights` `KPI Analysis`
