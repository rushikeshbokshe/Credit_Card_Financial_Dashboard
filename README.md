# Credit_Card_Financial_Dashboard
Powerbi Dashboard

Objective -

The objective of this project is to analyze credit card customer behavior, revenue generation, spending patterns, and customer demographics using Power BI. The dashboard helps stakeholders identify high-value customers, track revenue trends, monitor credit card usage, and make data-driven business decisions.

Tools & Technologies Used
Microsoft SQL Server
Power BI
DAX
Power Query
Excel / CSV Data Sources
Project Workflow / Steps
1. Data Collection
Imported Credit Card Transaction Data.
Imported Customer Demographic Data.
Connected datasets using Customer ID (Client_Num).
2. Data Cleaning
Removed duplicate records.
Handled null and blank values.
Standardized date formats.
Corrected data types.
3. Data Modeling
Created relationships between customer and transaction tables.
Implemented Star Schema model.
Optimized model for reporting performance.
4. DAX Calculations

Created measures for:

Revenue
Interest Earned
Weekly Revenue
Customer Count
Revenue Growth
Previous Week Revenue
Current Week Revenue
5. Dashboard Development

Created interactive dashboards containing:

Revenue Analysis
Customer Segmentation
Weekly Performance Tracking
State-wise Revenue
Gender Analysis
Income Group Analysis
Age Group Analysis
Education Level Analysis
Marital Status Analysis
Card Category Analysis
Key KPIs
KPI	Value
Total Revenue	56.5 Million
Total Income	576 Million
Total Interest Earned	8 Million
Customer Satisfaction Score (CSS)	3.19
Dashboard Insights
Revenue by Income Group
High-income customers generate the highest revenue.
Medium-income customers contribute significantly.
Low-income customers generate comparatively lower revenue.

Business Insight: Premium card offerings should target high-income customers.

Revenue by Age Group
Customers aged 40–50 contribute the highest revenue.
Age group 30–40 is the second highest contributor.
Younger customers (20–30) contribute less.

Business Insight: Marketing campaigns should focus on middle-aged customers.

Revenue by Education Level
Graduates generate the highest revenue.
High School and Post-Graduate customers also contribute significantly.

Business Insight: Educated customers tend to have higher spending behavior.

Revenue by Marital Status
Married customers generate the highest revenue.
Single customers contribute moderately.

Business Insight: Family-oriented rewards programs can increase engagement.

Revenue by Dependent Count
Customers with fewer dependents generate more revenue.
Revenue decreases as dependent count increases.
Revenue Trend Analysis
Revenue remains relatively stable throughout the year.
Seasonal fluctuations can be observed in certain weeks.

Business Insight: Promotional campaigns can be planned during low-revenue periods.

Customer Occupation Analysis

Top revenue-generating occupations:

Businessman
Government Employee
Blue Collar Workers

Business Insight: Business professionals represent the most profitable customer segment.

Card Usage Analysis

Transaction methods analyzed:

Swipe
Chip
Online

Business Insight: Swipe and Chip transactions dominate customer spending behavior.


DAX Measures Used
Total Revenue
Total Revenue =
SUM(cc_details[Revenue])
Total Interest Earned
Total Interest =
SUM(cc_details[Interest_Earned])
Total Income
Total Income =
SUM(cust_details[Income])
Customer Count
Customer Count =
DISTINCTCOUNT(cust_details[Client_Num])
Current Week Revenue
Current_Week_Revenue =
CALCULATE(
    SUM(cc_details[Revenue]),
    FILTER(
        ALL(cc_details),
        cc_details[Week_num2] =
        MAX(cc_details[Week_num2])
    )
)
Previous Week Revenue
Previous_Week_Revenue =
CALCULATE(
    SUM(cc_details[Revenue]),
    FILTER(
        ALL(cc_details),
        cc_details[Week_num2] =
        MAX(cc_details[Week_num2]) - 1
    )
)
Week-over-Week Revenue Growth %
WoW Revenue Growth % =
DIVIDE(
    [Current_Week_Revenue] -
    [Previous_Week_Revenue],
    [Previous_Week_Revenue],
    0
)
Revenue by Gender
Revenue by Gender =
SUM(cc_details[Revenue])

Used with Gender slicer for dynamic analysis.

CSS Score
Average CSS =
AVERAGE(cust_details[Cust_Satisfaction_Score])
