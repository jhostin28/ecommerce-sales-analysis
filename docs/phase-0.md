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
- **Business logic lives in the database.** Each question is answered by a view; Excel and Power BI only read the views. If the logic changes, it changes in one place.
- **Raw CSV files are not committed.** They are downloaded from Kaggle into `data/` (ignored by git). SQL scripts are committed.

## Phases

| Phase | What | Done when |
|---|---|---|
| 0 | Problem and phases | This document exists |
| 1 | SQL Server tables with PK/FK, load the 9 CSV files, validate | Row counts match the CSV files and foreign keys hold |
| 2 | One view per business question | Each question has a view and a one-sentence answer |
| 3 | Stored procedures with parameters and `TRY/CATCH` | Reports by date range or state run with `EXEC` |
| 4 | Excel report connected to the views | A manager opens the file, clicks Refresh and sees current data |
| 5 | Power BI dashboard on top of the views | A manager sees the answers without knowing SQL |
| 6 | Conclusions and recommendations | Someone outside the project understands the findings |
