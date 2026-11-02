# E-commerce Sales Analysis (Olist)

Business analysis of a Brazilian e-commerce marketplace using the public [Olist dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (~100k orders, 2016–2018).

The goal is not to explore data, but to answer concrete business questions a manager would ask, and turn the answers into decisions.

**One pipeline, end to end:** raw CSV → SQL Server (cleaning, views, stored procedures) → Excel report, automated with Python → Power BI dashboard → executive presentation with recommendations.

## Project structure

| Area | Where |
|---|---|
| **Database development** | [`sql/`](sql/): schema with keys, views, stored procedures, functions, triggers, indexing, backup · [`python/`](python/): report automation |
| **Data analysis & BI** | [`excel/`](excel/), [`powerbi/`](powerbi/), [`presentation/`](presentation/) and [Conclusions](#conclusions) |

## Business questions

1. **Are we growing?** How do sales change month over month?
2. **What sells the most?** Which product categories generate the most revenue?
3. **Where are our customers?** Which states buy the most?
4. **Are we delivering on time?** How many orders arrive late, and where?
5. **Are customers happy?** Do late deliveries lower review scores?

## Stack

- **SQL Server** (T-SQL) + **SSMS**: data model, cleaning, views, stored procedures, functions, triggers
- **Excel**: refreshable report connected to the views (Power Query, pivot tables, Power Pivot, sales vs. target)
- **Python**: `pyodbc` + pandas (`read_sql`, `to_excel`) to automate the Excel report
- **Power BI**: dashboard connected to the views (relationships, DAX, KPIs)

## Phases

| Phase | Description | Status |
|---|---|---|
| 0 | Problem definition and project phases | ✅ Done |
| 1 | SQL Server database: tables with keys, load, documented data cleaning, backup | ❌ To do |
| 2 | One view per question: CTEs, window functions, descriptive statistics, sales KPIs, simple forecast | ❌ To do |
| 3 | Stored procedures with error handling, a function and a trigger | ❌ To do |
| 4 | Excel report connected to the views, with sales vs. target | ❌ To do |
| 5 | Python automation of the Excel report | ❌ To do |
| 6 | Power BI dashboard connected to the views | ❌ To do |
| 7 | Conclusions and executive presentation | ❌ To do |

Details for each phase are in [`docs/`](docs/).

## Conclusions

_Coming in phase 7._
