# Credit_card_financial_dashboard
Power BI dashboard
# 📊 Credit Card Financial Dashboard

An interactive **Power BI** dashboard analyzing credit card customer and transaction data.  
The project delivers business insights into customer demographics, spending behavior, and revenue trends, helping stakeholders make data-driven decisions.

---

## 🚀 Project Overview
This dashboard integrates data from a **SQL Server** database and applies **DAX measures** for deeper analysis.  
It includes two main reports:
1. **Customer Report** – Profiling revenue by demographics and customer attributes.
2. **Transaction Report** – Tracking spending patterns, transaction volumes, and card performance.

---

## 📌 Key Insights

### **Customer Report Highlights**
- **Revenue by Income Group:** High-income customers generate the largest share of revenue (~23M).
- **Gender Split:** Female customers contribute ~31M revenue, males ~26M.
- **Top States:** TX, NY, CA, FL, and NJ lead in revenue generation.
- **Age Distribution:** Customers aged **60–70** contribute the highest revenue (~14M).
- **Education Impact:** Post-graduate and graduate customers generate the highest revenue.
- **Marital Status:** Married customers are slightly ahead in total revenue compared to single customers.

### **Transaction Report Highlights**
- **Quarterly Trends:** Revenue peaks in **Q4** at 14.5M, with stable transaction counts.
- **Expenditure Types:** Bills, entertainment, and fuel are top categories.
- **Card Category Performance:** Blue cards dominate with ~47M revenue.
- **Payment Methods:** Swipe transactions are most common, followed by chip and online.
- **Customer Job Analysis:** Businessmen generate the highest revenue (~18M).

---

## 🛠️ Tools & Technologies
- **Power BI** – Data visualization & dashboard creation
- **SQL Server** – Data extraction & transformation
- **DAX** – Custom calculations and measures


🙌 Acknowledgments
Dataset sourced from SQL Server sample credit card data.
Inspired by real-world financial analytics reporting.
---

## 📐 Key DAX Measures
```DAX
IncomeGroup = SWITCH(
    TRUE(),
    cust_detail[Income] < 35000, "Low",
    cust_detail[Income] >= 35000 && cust_detail[Income] < 70000, "Med",
    cust_detail[Income] >= 70000, "High",
    "Unknown"
)

AgeGroup = SWITCH(
    TRUE(),
    cust_detail[Customer_Age] < 30, "20-30",
    cust_detail[Customer_Age] >= 30 && cust_detail[Customer_Age] < 40, "30-40",
    cust_detail[Customer_Age] >= 40 && cust_detail[Customer_Age] < 50, "40-50",
    cust_detail[Customer_Age] >= 50 && cust_detail[Customer_Age] < 60, "50-60",
    cust_detail[Customer_Age] >= 60 && cust_detail[Customer_Age] < 73, "60-70",
    cust_detail[Customer_Age] <= 73, "73+",
    "Unknown"
)

Current_Week_Revenue =
CALCULATE(
    SUM(cc_details[Revenue]),
    FILTER(ALL(cc_details), cc_details[Week_Num2] = MAX(cc_details[Week_Num2]))
)

Previous_Week_Revenue =
CALCULATE(
    SUM(cc_details[Revenue]),
    FILTER(ALL(cc_details), cc_details[Week_Num2] = MAX(cc_details[Week_Num2]) - 1)
)

Revenue =
cc_details[Annual_Fees] + cc_details[Total_Trans_Amt] + cc_details[Interest_Earned]
📷 Dashboard Previews
Customer Report
Transaction Report

📂 How to Use
Clone the repository:

bash
Copy
git clone https://github.com/Stefan-git-web/Credit_card_financial_dashboard.git
Open Credit_Card_Dashboard.pbix in Power BI Desktop.

Ensure SQL Server database access and adjust the connection string if needed.

Refresh the dataset to load live data.

📈 Skills Demonstrated
Data modeling in Power BI

SQL query integration

Advanced DAX calculations

Data storytelling with visuals

Business insight generation

        




