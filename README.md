# E-commerce Sales Analysis (Olist)

Business analysis of a Brazilian e-commerce marketplace using the public [Olist dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (~100k orders, 2016–2018).

The goal is not to explore data, but to answer concrete business questions a manager would ask, and turn the answers into decisions.

**One pipeline, end to end:** raw CSV → SQL Server (tables, views, stored procedures) → Excel and Power BI reports → conclusions for a manager.

| If you're hiring for... | Look at |
|---|---|
| **Database roles** (DB Developer, Analista Programador) | [`sql/`](sql/): schema with keys, views, stored procedures |
| **Data Analyst / BI roles** | [`excel/`](excel/), [`powerbi/`](powerbi/) and the [Conclusions](#conclusions) |

## Business questions

1. **Are we growing?** How do sales change month over month?
2. **What sells the most?** Which product categories generate the most revenue?
3. **Where are our customers?** Which states buy the most?
4. **Are we delivering on time?** How many orders arrive late, and where?
5. **Are customers happy?** Do late deliveries lower review scores?

## Stack

- **SQL Server** (T-SQL) + **SSMS**: data model, loading, views and stored procedures
- **Excel**: refreshable report connected to the SQL Server views (pivot tables, formulas)
- **Power BI**: dashboard connected to the SQL Server views (relationships, DAX measures)

## Phases

| Phase | Description | Status |
|---|---|---|
| 0 | Problem definition and project phases | ✅ Done |
| 1 | SQL Server database: tables with keys, load and validate the 9 CSV files | ❌ To do |
| 2 | One T-SQL view per business question | ❌ To do |
| 3 | Stored procedures with parameters and error handling | ❌ To do |
| 4 | Excel report connected to the views | ❌ To do |
| 5 | Power BI dashboard connected to the views | ❌ To do |
| 6 | Conclusions and recommendations | ❌ To do |

Details for each phase are in [`docs/`](docs/).

## Conclusions

_Coming in phase 6._
