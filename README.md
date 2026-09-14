# Food Manufacturing Business Intelligence & Analytics Dashboard

An end-to-end Power BI portfolio project demonstrating business intelligence across sales, operations, production, inventory, customer performance, and workforce planning.

> **Disclaimer:** This is an illustrative portfolio case study. The datasets, transactions, business figures, and company information are simulated and do not represent an actual organization or confidential data.

## Project Overview

The solution combines four analytical modules into one integrated Power BI project:

1. **Executive Overview** — high-level business performance
2. **Operations & Customer Insights** — production, quality, inventory, suppliers, and customer issues
3. **Growth & Sales Insights** — channels, customers, exports, salespeople, and product growth
4. **Workforce Efficiency & Manpower Planning** — workforce productivity and manpower requirements

The overall workflow is:

**Data → Cleaning & Standardization → KPI Calculation → Analysis → Visualization → Business Insights → Decision Support**

## Business Objectives

The dashboard is designed to help management answer questions such as:

- How is overall business performance trending?
- Which products and regions contribute most to revenue?
- Are sales targets being achieved?
- Which production lines and shifts perform better?
- Where are rejection, wastage, or downtime issues occurring?
- Which suppliers and customers require attention?
- Which products have higher complaint rates?
- How much workforce is required for a planned production quantity?
- Where are potential manpower shortages or surpluses?

## Dashboard Modules

### 1. Executive Overview

**KPIs:** Total Revenue, Total Profit, Profit Margin, Total Orders, Target Achievement, Production Efficiency.

**Visuals:** Monthly Revenue & Profit Trend, Revenue by Region, Revenue by Product Category, Top Products by Revenue, Sales Target vs Actual.

### 2. Operations & Customer Insights

**KPIs:** Total Production, Production Efficiency, Rejection Rate, Total Inventory, Near Expiry Stock, Customer Complaints, Customer Satisfaction.

**Visuals:** Production Trend, Rejection & Wastage Trend, Inventory Status by Category, Supplier Performance, Customer Complaints by Type, Top Products by Complaint Rate.

### 3. Growth & Sales Insights

**Visuals:** Sales Trend by Channel, Export Sales by Country, Top Customers by Revenue, Top Salespeople by Target Achievement, Revenue by Customer Type, Top Growing Products (MoM).

### 4. Workforce Efficiency & Manpower Planning

**KPIs:** Workforce Efficiency, Units per Labour Hour, Present Workers, Required Workers, Manpower Gap.

**Visuals:** Workforce Efficiency Trend, Efficiency by Production Line, Efficiency by Shift, Present vs Required Workers by Production Line, Manpower Gap by Production Line, Manpower Gap by Shift.

## Workforce Calculation Logic

**Labour Hours** = Present Workers × Production Hours

**Units per Labour Hour** = Accepted Good Quantity ÷ Labour Hours

**Workforce Efficiency** = Actual Productivity ÷ Benchmark Productivity × 100

**Required Labour Hours** = Planned Good Quantity ÷ Benchmark Productivity

**Effective Hours per Worker** = Shift Hours − Planned Downtime

**Required Workers** = Required Labour Hours ÷ Effective Hours per Worker

The prototype uses a historical **P75 productivity benchmark** as a practical high-performance benchmark. With real business data, the benchmark should be validated with operational stakeholders and refined where sufficient historical observations exist.

## Tools & Technologies

- **Power BI** — dashboard development, data modeling, DAX, interactive reporting
- **Microsoft Excel** — data preparation, validation, calculations, and manpower planning
- **SQL** — data querying and analytical workflow
- **Python** — data analysis and preprocessing
- **DAX** — KPI and business metric calculations

## Analytical Approach

1. **Data Collection** — organized sales, customer, product, production, inventory, procurement, quality, complaint, export, target, and workforce datasets.
2. **Cleaning & Standardization** — standardized dates, categories, identifiers, and analytical fields.
3. **Data Modeling** — structured fact-style data, master/reference data, and a dedicated date table.
4. **KPI Development** — created DAX measures for rates, productivity, efficiency, and comparisons.
5. **Visualization** — interactive slicers and management-focused visuals.
6. **Decision Support** — identified trends, exceptions, performance gaps, and areas requiring attention.

## Repository Structure

```text
Food-Manufacturing-BI-Analytics/
│
├── README.md
├── Data/
├── Excel/
│   └── Workforce_Manpower_Planning_Model.xlsx
├── PowerBI/
│   └── Food_Manufacturing_BI_Dashboard.pbix
├── DAX/
│   └── Measures.md
├── Screenshots/
│   ├── Executive_Overview.png
│   ├── Operations_Customer_Insights.png
│   ├── Growth_Sales_Insights.png
│   └── Workforce_Manpower_Planning.png
└── Documentation/
    └── Methodology.md
```

## Future Improvements

- Automated data refresh
- ERP/database integration
- Executive exception monitoring
- Threshold-based alerts
- Power Automate notifications
- Production capacity analysis
- Product-line-shift benchmarks
- Sales and production forecasting
- Automated management reporting
- Transaction-level drill-through

## Author

**Abhishek Sinha**  
MSc Data Science | Data Analytics | Power BI | SQL | Excel | Python
