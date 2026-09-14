# Methodology

## 1. Business Problem

The objective was to create an integrated business intelligence solution for a food manufacturing business covering executive performance, sales, operations, customer insights, and workforce planning.

## 2. Data Preparation

Illustrative datasets were created for:

- Products
- Customers
- Sales
- Production
- Inventory
- Procurement
- Quality
- Customer complaints
- Export sales
- Sales targets
- Workforce

Data was standardized before analysis.

## 3. Data Modeling

Power BI uses a structured analytical model with:

- Transaction/fact-style datasets
- Master/reference datasets
- Date dimension
- Relationships between relevant business entities

## 4. KPI Development

DAX measures were used for:

- Revenue
- Profit
- Profit margin
- Production efficiency
- Rejection rate
- Customer satisfaction
- Workforce productivity
- Workforce efficiency
- Required workers
- Manpower gap

## 5. Workforce Planning Method

Historical accepted production was divided by labour hours to calculate productivity.

A P75 historical productivity benchmark was used in the prototype to represent a practical high-performing benchmark.

Required labour hours were calculated from the planned good production quantity and benchmark productivity.

Required workers were then estimated using effective working hours after planned downtime.

## 6. Dashboard Design

The dashboard was organized into four management-focused modules:

1. Executive Overview
2. Operations & Customer Insights
3. Growth & Sales Insights
4. Workforce Efficiency & Manpower Planning

## 7. Decision Support

The objective is not simply to display data. The dashboard is designed to help identify:

- Trends
- Performance gaps
- Operational exceptions
- Sales opportunities
- Quality issues
- Inventory risks
- Workforce planning requirements

## 8. Limitations

The dataset is simulated and therefore the numerical results should not be interpreted as real company performance.

The workforce benchmark is a prototype assumption and should be validated against actual operational standards and historical company data.

## 9. Future Enhancements

- ERP/database integration
- Automated refresh
- Executive alerts
- Power Automate integration
- Forecasting
- Production capacity planning
- More granular workforce benchmarks
