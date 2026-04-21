---
title: SQL Crash Course
created: 2026-04-21
tags: [concept, knowledge, ds-interview, sql]
topics: [sql, select, where, group-by, joins]
---

# SQL Crash Course

> Foundational SQL note for query structure, filtering, grouping, and joins.

---

## What It Is

SQL - Structured Query Language - is how you ask structured questions about data stored in tables. For interview prep, the goal is not just syntax recall. It is learning how to translate a business question into:

1. the right rows
2. the right columns
3. the right grouping level
4. the right join logic

RDBMS - Relational Database Management System - is the system that stores and manages the relational data SQL queries work with. 
- The data is stored in database objects called tables. 
- A table is a collection of related data entries and it consists of columns and rows.

---

## Why It Matters

Most analytics and data science SQL problems reduce to a few repeatable moves:

- filter the data you want
- group to the right grain
- aggregate with counts or sums
- join tables at the correct level
- use a CTE when the logic is easier in steps

Getting comfortable with these basics makes window functions, retention problems, and interview-style case questions much easier.

---

## Core Query Shape

```sql
SELECT column_or_metric
FROM table_name
WHERE condition
GROUP BY grouping_columns
HAVING aggregate_condition
ORDER BY sort_column;
```

Use only the clauses you need. The main habit is knowing the role of each one.

---

## Core Techniques

- `SELECT` chooses the output columns
- `WHERE` filters rows before grouping
- `GROUP BY` sets the level of aggregation
- `HAVING` filters grouped results after aggregation
- `JOIN` combines tables through matching keys
- `WITH` breaks a problem into easier steps

---

## Common Mistakes To Watch

- grouping at the wrong grain
- using `WHERE` when the condition belongs in `HAVING`
- joining on the wrong key and duplicating rows
- counting rows when you really need `COUNT(DISTINCT ...)`
- solving everything in one query instead of using a clean CTE

---

## Connected To

- [[Dashboard]] - DS interview prep hub
- [[SQL Patterns]] - quick SQL reference and reusable snippets
- [[SQL Tracker]] - SQL problems and weak spots

---

## Note Type

- Detailed tutorial note in `Knowledge/DS Interview Prep/`
