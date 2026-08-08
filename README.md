# MIS 443 – Finance Analysis with PostgreSQL

A compact PostgreSQL practice project built around a **retail banking database**. The repository is designed so other students can quickly understand the schema, recreate the dataset, attempt the finance questions themselves, and compare their work with a completed solution.

## Project Overview

The database represents a retail bank that manages **customers, branches, accounts, and financial transactions**. The SQL analysis answers practical management questions about customer portfolios, deposit balances, branch performance, and transaction activity.

The project progresses from basic SQL to analytical techniques such as multi-table joins, aggregate functions, subqueries, tie-aware ranking, window functions, and a Common Table Expression (CTE).

## What You Can Practise

- Creating and validating a PostgreSQL relational database
- Filtering and sorting business data
- `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX`
- `INNER JOIN` and `LEFT JOIN`
- `GROUP BY` and aggregate analysis
- Subqueries
- `FETCH FIRST ... WITH TIES`
- `DENSE_RANK()` window functions
- Common Table Expressions (`WITH`)
- Translating business questions into SQL queries

## Database at a Glance

| Table | Purpose | Rows |
|---|---|---:|
| `customers` | Customer names and locations | 6 |
| `branches` | Branch names and locations | 15 |
| `accounts` | Ownership, branch assignment, account type, and balance | 15 |
| `transactions` | Transaction dates and amounts | 15 |

Positive account balances represent customer funds. Negative Credit Card balances represent amounts owed. Positive transaction amounts are credits, while negative amounts are debits.

## Entity–Relationship Diagram

![Finance Database Entity–Relationship Diagram](Entity_Relationship_Diagram.png)

Main relationships:

- `accounts.customer_id` → `customers.customer_id`
- `accounts.branch_id` → `branches.branch_id`
- `transactions.account_id` → `accounts.account_id`

This creates three one-to-many relationships: **Customer → Accounts**, **Branch → Accounts**, and **Account → Transactions**.

## Analysis Questions

The completed solution answers 12 analysis tasks across 6 examination questions:

| Area | Examples |
|---|---|
| Customer overview | New York customer list, account portfolio size |
| Balance analysis | Total Checking balance, Los Angeles customer portfolios |
| Branch performance | Highest average balance, highest total balance |
| Customer value | Highest-balance account, highest deposit balance |
| Activity analysis | Most active customers, most active branches |
| Advanced SQL | Dense ranking and CTE-based branch analysis |

## Selected Results

- **Total accounts:** 15
- **Total Checking balance:** 31,000.00
- **Largest customer portfolio:** Michael Lee – 60,000.00
- **Highest single account balance:** Michael Lee – Savings – 50,000.00
- **Highest average branch balance:** North Beach – 30,000.00
- **Highest total branch balance:** North Beach – 60,000.00
- **Most active customers:** Jane Doe and Alice Johnson – 4 transactions each
- **Most active branches:** Main and South Bay – 4 transactions each

## Repository Structure

```text
MIS443_Finance_Analysis_GitHub/
│
├── codes/
│   ├── MIS443_Finance_PostgreSQL.sql
│   └── MIS443_Finance_Analysis_Solutions.sql
│
├── report/
│   └── MIS443_DoanPhanMinhVu_Finance_Analysis_Report.docx
│
├── Entity_Relationship_Diagram.png
└── README.md
```

A separate `data/` folder is not needed for this project because the supplied PostgreSQL script already creates and inserts the full practice dataset.

## How to Run the Project

1. Open PostgreSQL and pgAdmin 4.
2. Create a new database.
3. Connect to the new database.
4. Run `codes/MIS443_Finance_PostgreSQL.sql` to create the schema and load the data.
5. Confirm the expected row counts:
   - `accounts`: 15
   - `branches`: 15
   - `customers`: 6
   - `transactions`: 15
6. Try solving the finance questions yourself.
7. Run `codes/MIS443_Finance_Analysis_Solutions.sql` to compare your queries with the completed answers.
8. Open the Word report for screenshots, explanations, and business interpretation.

## Try It Yourself

For the best practice experience, **do not open the solution file immediately**. Load the dataset first and try to answer the questions using your own SQL. Then compare your approach with the completed solution.

Useful questions to think about while practising:

- When should a `LEFT JOIN` be used instead of an `INNER JOIN`?
- How can tied maximum values be returned safely?
- Why is `DENSE_RANK()` more suitable than `ROW_NUMBER()` when equal balances must share a rank?
- Why does the branch-activity question benefit from a CTE?

## Tools Used

- PostgreSQL
- pgAdmin 4
- SQL
- Microsoft Word
- GitHub

## Author

**Doan Phan Minh Vu**  
Student ID: **2232300049**  
GitHub: [kenphan303](https://github.com/kenphan303)

---

*Educational project for MIS 443 – Business Data Management.*
