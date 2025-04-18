# 💳 Credit Card Financial Analytics Dashboard – SQL + Power BI

## 📊 Project Overview

This project focuses on analyzing credit card customer and transaction data using SQL for data transformation and Power BI for dashboard creation. The goal is to draw actionable business insights, monitor weekly performance, and understand customer behavior across demographics and geographies.

---

## 🛠 Tools & Technologies

- **SQL** (Data Cleaning & Transformation)
- **Power BI** (Data Visualization & Dashboarding)
- **DAX** (Calculated Columns & Measures)

---

## 🔄 Data Pipeline

1. **SQL Data Cleaning**
   - Removed nulls, duplicates, and inconsistent formats
   - Standardized income and age formats
   - Created joins between customer and credit card transaction tables

2. **Data Connection**
   - SQL views loaded directly into Power BI for live dashboarding

3. **Power BI Dashboards**
   - Two dashboards: **Transaction Dashboard** and **Customer Dashboard**
   - Utilized DAX to create custom insights

---

## 🧮 Key DAX Calculations

dax
-- Age Group Classification
AgeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)

-- Income Group Classification
IncomeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low",
    'public cust_detail'[income] < 70000, "Med",
    'public cust_detail'[income] >= 70000, "High",
    "unknown"
)

-- Weekly Revenue Calculation
week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

Current_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(ALL('public cc_detail'), 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))
)

Previous_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(ALL('public cc_detail'), 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) - 1)
)


------------------------
#Year-to-Date Highlights
💰 Total Revenue: $57M

💸 Total Interest Earned: $8M

🔁 Total Transaction Amount: $46M

🧍‍♂️ Revenue by Gender:

Male: $31M

Female: $26M

💳 Card Performance: Blue & Silver cards account for 93% of all transactions

🌍 Top States: TX, NY, CA → 68% contribution

✅ Activation Rate: 57.5%

⚠️ Delinquency Rate: 6.06%

#🚀 Future Scope
Add monthly/quarterly performance trends

Implement customer segmentation via clustering models

Predictive modeling for churn and delinquency risk

📁 Folder Structure
bash
Copy
Edit
.
├── SQL/
│   └── data_cleaning_queries.sql
├── PowerBI/
│   └── dashboards.pbix
├── README.md
#🙌 Acknowledgments

Dataset inspired by simulated credit card financial and customer data

Built with a focus on real-world dashboarding and financial reporting use cases

##📬 Contact
For any queries, suggestions or collaboration ideas:
[Arshaan khan] – [www.linkedin.com/in/arsh44n]













