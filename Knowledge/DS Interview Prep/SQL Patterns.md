---
title: SQL Patterns
created: 2026-04-17
tags: [knowledge, ds-interview, sql]
topics: [sql, analytics]
---

# SQL Patterns

> Quick-reference note for SQL pattern recognition and reusable snippets. Use [[SQL Tracker]] for problem logs and weak spots.

---

## How To Use This Note

1. Identify the question type: filtering, aggregation, joins, ranking, time-series, retention.
2. Find the grain: one row per user, order, date, or event.
3. Match the problem to a concept family below.
4. If the query gets messy, split it into steps with a CTE.

---

## Concept Map

### Core Query Logic

| Concept | Reach for it when... | Common move |
|---|---|---|
| `SELECT` + `WHERE` | need the right rows and columns first | filter early |
| `GROUP BY` + aggregates | need counts, sums, averages, or grouped metrics | define the grain first |
| `HAVING` | need to filter grouped results | apply condition after aggregation |
| `CASE WHEN` | need buckets, labels, or conditional metrics | build logic inside `SELECT` |

### Combining Data

| Concept | Reach for it when... | Common move |
|---|---|---|
| `INNER JOIN` | only keep matched rows | join on business key |
| `LEFT JOIN` | keep all rows from the main table | check for nulls on the right side |
| Subquery / CTE | logic is easier in steps | build intermediate result first |

### Analytical SQL

| Concept | Reach for it when... | Common move |
|---|---|---|
| Window functions | need ranking or row-level metrics without collapsing rows | use `OVER (...)` |
| `LAG` / `LEAD` | need previous or next row comparisons | order within a window |
| Rolling metrics | need moving averages or cumulative values | define window frame carefully |
| Retention / cohort logic | need repeat behavior over time | anchor users to a first event/date |

---

## Study Checklist

### Month 1 - Core SQL (W3WSchools Crash Course)
- [ ] SELECT, WHERE, LIMIT
- [ ] Comparison operators
- [ ] Logical operators (AND, OR, NOT)
- [ ] ORDER BY
- [ ] GROUP BY & aggregate functions (COUNT, SUM, AVG, MIN, MAX)
- [ ] HAVING
- [ ] INNER JOIN
- [ ] LEFT / RIGHT / FULL JOIN
- [ ] Subqueries
- [ ] WITH (CTEs)

### Month 2 - Analytical SQL
- [ ] Window functions - ROW_NUMBER, RANK, DENSE_RANK
- [ ] PARTITION BY
- [ ] LAG / LEAD
- [ ] Rolling averages
- [ ] Retention queries
- [ ] Funnel analysis
- [ ] Cohort analysis
- [ ] Date functions

### Month 3 - Interview Mocks
- [ ] 10 StrataScratch problems (company tagged)
- [ ] 10 DataLemur problems
- [ ] Timed sessions (3 problems / 60 min)

---

## Recognition Cues

- `count by ...` -> `GROUP BY`
- `filter grouped result` -> `HAVING`
- `include users with no match` -> `LEFT JOIN`
- `rank within each group` -> window function
- `compare to previous row` -> `LAG`
- `build in steps` -> CTE
- `first day / first purchase / cohort` -> subquery or CTE + date logic

---

## Key Snippets

### CTE
```sql
WITH cte AS (
  SELECT user_id, COUNT(*) AS cnt
  FROM events
  GROUP BY user_id
)
SELECT * FROM cte WHERE cnt > 5;
```

### Window function - rank
```sql
SELECT
  user_id,
  score,
  RANK() OVER (PARTITION BY cohort ORDER BY score DESC) AS rnk
FROM scores;
```

### LAG / LEAD
```sql
SELECT
  date,
  revenue,
  LAG(revenue, 1) OVER (ORDER BY date) AS prev_revenue,
  revenue - LAG(revenue, 1) OVER (ORDER BY date) AS change
FROM daily_revenue;
```

### Rolling 7-day average
```sql
SELECT
  date,
  AVG(revenue) OVER (ORDER BY date ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) AS rolling_avg
FROM daily_revenue;
```

### Retention (Day 1)
```sql
WITH first_day AS (
  SELECT user_id, MIN(DATE(created_at)) AS first_date
  FROM events GROUP BY user_id
)
SELECT
  f.first_date,
  COUNT(DISTINCT e.user_id) AS retained
FROM first_day f
JOIN events e
  ON f.user_id = e.user_id
  AND DATE(e.created_at) = DATE_ADD(f.first_date, INTERVAL 1 DAY)
GROUP BY f.first_date;
```

---

## Connected To
- [[Dashboard]]
- [[SQL Tracker]]
- [[SQL Crash Course]]
- [[LeetCode Patterns]]
- [[ML Concepts]]
- [[Resources]]
