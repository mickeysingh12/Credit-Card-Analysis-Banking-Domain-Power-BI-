# Credit Card Analysis Dashboard 📊

## Project Overview 🚀

This project focuses on **Credit Card Usage Data Analysis** and provides insights into customer transactions, age groups, and total revenue generated. The analysis is done using **SQL**, **DAX**, and **Power BI**, where the processed data is visualized through interactive dashboards. The data is sourced from SQL, processed using DAX formulas, and represented with Power BI dashboards.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Dataset 📁

The dataset consists of **credit card transactions and customer details** from various CSV files. The key CSV files used are:

- `cc_add.csv`
- `credit_card.csv`
- `cust_add.csv`
- `customer.csv`

### Data Preparation 🛠️

- Imported raw data from CSV files.
- Cleaned and processed the data.
- Created relevant SQL tables and relations in **SQL Server**.
- Exported clean data to SQL for analysis and used for Power BI visualization.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### Data Processing and DAX 🧮

The data processing involved creating relevant metrics using **DAX** (Data Analysis Expressions) within Power BI. Below are some of the key **DAX Queries** implemented:


**Last Week's Transaction Amount**:
```
Last_Week_Amt = 
CALCULATE( 
   SUM('Credit Card Details (2)'[Total_Trans_Amt]), 
   FILTER( 
      ALL('Credit Card Details (2)'), 
      'Credit Card Details (2)'[Week_Num2] = MAX('Credit Card Details (2)'[Week_Num2]) - 1 
   ) 
)
```

**This Week's Transaction Amount**:
```
This_Week_Amt = 
CALCULATE( 
   SUM('Credit Card Details (2)'[Total_Trans_Amt]), 
   FILTER( 
      ALL('Credit Card Details (2)'), 
      'Credit Card Details (2)'[Week_Number] = MAX('Credit Card Details (2)'[Week_Number]) 
   ) 
)
```

**Revenue Calculation**:
```
Revenue = 
SUM('Credit Card Details'[Total_Trans_Amt]) + 
SUM('Credit Card Details'[Annual_Fees]) + 
SUM('Credit Card Details'[Interest_Earned])
```

**Customer Age Group Categorization**:
```
Age_Group = 
SWITCH( 
   TRUE(), 
   'Customer Details'[Customer_Age] < 30, "20-30", 
   'Customer Details'[Customer_Age] >= 30 && 'Customer Details'[Customer_Age] < 40, "30-40", 
   'Customer Details'[Customer_Age] >= 40 && 'Customer Details'[Customer_Age] < 50, "40-50", 
   'Customer Details'[Customer_Age] >= 50 && 'Customer Details'[Customer_Age] < 60, "50-60", 
   'Customer Details'[Customer_Age] >= 60, "60+", 
   "Unknown" 
)
```
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Dashboards and Insights 🖥️

The final **Power BI Dashboard** contains several visuals including:


- **Revenue Analysis**: Showcases total revenue generated through transactions, annual fees, and interest earned.
- **Transaction Trends**: Visualizations to track weekly transactions and compare them with the previous week's data.
- **Customer Segmentation**: Breakdown of customers by age groups to analyze how different age brackets use credit cards.

These insights provide valuable information for **business strategies** and decision-making.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Files 📦

- **CreditCardDashboard.pdf**: Documentation of the Power BI dashboard.
- **CreditCardInsightsPPT.pdf**: PowerPoint presentation with insights and findings.
- **Credit_card_analysis.pbix**: Power BI file containing the full analysis and visualizations.
- **README.md**: Project documentation.
- **CSV Files**: Raw data files for analysis.
  - `cc_add.csv`
  - `credit_card.csv`
  - `cust_add.csv`
  - `customer.csv`

