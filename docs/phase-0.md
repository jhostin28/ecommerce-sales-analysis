# Phase 0: Problem and phases

## The problem

A manager at Olist asks: *"I want to know how the business is doing."*

That request can't be answered as is. The job of the analyst is to turn it into concrete questions, each one tied to a decision.

## Business questions

| # | Question | Main data | Possible decision |
|---|---|---|---|
| 1 | How do sales change month over month? | Orders, payments | Plan inventory and campaigns for strong/weak months |
| 2 | Which categories generate the most revenue? | Order items, products, categories | Focus marketing on top categories |
| 3 | Which states buy the most? | Customers | Where to invest in logistics and ads |
| 4 | How many orders arrive late, and where? | Orders (delivered vs. estimated date), sellers | Talk to slow sellers, change carriers, set realistic delivery dates |
| 5 | Do late deliveries lower review scores? | Orders, reviews | Prove that fixing delivery protects customer satisfaction |

Questions 1–4 describe **what** happens. Question 5 looks for **why**, which turns a report into an analysis.

## Decisions

- **Questions before data.** Without questions, exploring 9 tables has no end and no conclusion to present.
- **Every question must lead to a decision.** If the answer doesn't change anything, it's not worth answering.
- **Questions limited to what the dataset contains.** Checked against the list of tables before writing them.
- **SQL Server instead of PostgreSQL.** Banks and government in the Dominican Republic use SQL Server + Power BI. The same project covers Data Analyst roles (dashboard, conclusions) and Database Developer roles (T-SQL, views, stored procedures).
- **One repository, not two.** In a real company this is one chain: the database developer builds tables, views and procedures; the analyst builds reports and conclusions; the manager decides. The README points each type of recruiter to their part.
- **Excel connected to SQL Server.** Managers in banks and offices live in Excel. A refreshable Excel report on top of the views is realistic, and covers the Excel essentials Data Analyst roles ask for.
- **Python for automation, not exploration.** In banks, Python is often used to run SQL and produce recurring reports automatically (`pyodbc`, `openpyxl`), not for pandas analysis. Phase 5 does exactly that.
- **Stack validated with a real data analyst** at a Dominican bank: Python, advanced SQL, advanced Excel, Power BI, corporate SaaS.
- **Scope based on real job postings.** Data Analyst and database roles in the Dominican Republic repeatedly ask for data cleaning, descriptive statistics, sales KPIs (average ticket, month-over-month growth), sales vs. target, simple forecasting, Power Pivot and presenting findings to business teams. Each of these was added to a phase. Nothing else is added; new ideas go to another project.
- **Sales targets are an assumption.** Olist has no targets, so a target table is created (e.g. 10% growth over the same month of the previous year) and documented as such.
- **Python: `pyodbc` + pandas.** `pyodbc` is how banks often run SQL from Python; pandas' `read_sql` uses that same connection and is what many postings ask for.
- **Minimal database administration.** One backup/restore, one index with its execution plan, one read-only user, one function and one trigger. Enough to explain the concepts; this is not a DBA project.
- **Business logic lives in the database.** Each question is answered by a view; Excel, Python and Power BI only read the views and procedures. If the logic changes, it changes in one place.
- **Raw CSV files are not committed.** They are downloaded from Kaggle into `data/` (ignored by git). SQL scripts are committed.

## Phases

🟢 essential for junior roles · 🔵 plus (stands out, or covers database roles)

| Phase | What | Done when |
|---|---|---|
| 0 | Problem and phases | This document exists |
| 1 | 🟢 Tables with PK/FK, load the 9 CSV files, documented cleaning · 🔵 backup/restore, read-only user | Row counts match, foreign keys hold, every cleaning step has a reason |
| 2 | 🟢 Views with CTEs and window functions, descriptive statistics, sales KPIs · 🔵 simple forecast, one index with execution plan | Each question has a view and a one-sentence answer |
| 3 | 🔵 Stored procedures with parameters and `TRY/CATCH`, one function, one trigger | Reports run with `EXEC`; procedure vs. function vs. trigger can be explained |
| 4 | 🟢 Excel report on the views: Power Query, pivot tables, formulas, sales vs. target · 🔵 Power Pivot | A manager clicks Refresh and sees current data and target achievement |
| 5 | 🔵 Python (`pyodbc` + pandas) builds the Excel report | One command produces the report |
| 6 | 🟢 Power BI dashboard on the views: relationships, DAX, KPIs, target | A manager sees the answers without knowing SQL |
| 7 | 🟢 Conclusions + 5–7 slide executive presentation (PDF) | Someone outside the project understands the findings and recommendations |

Study order if time is short: 1, 2, 4, 6, 7 first; then 3 and 5.
