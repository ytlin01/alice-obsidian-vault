# 🟢 SQL Tracker

## Stats
- **Total solved:** 0
- **Mode Tutorial:** 0 / 9 lessons
- **DataLemur:** 0 problems
- **StrataScratch:** 0 problems

---

## Curriculum Checklist

### Month 1 — Core SQL (Mode Tutorial)
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

### Month 2 — Analytical SQL
- [ ] Window functions — ROW_NUMBER, RANK, DENSE_RANK
- [ ] PARTITION BY
- [ ] LAG / LEAD
- [ ] Rolling averages
- [ ] Retention queries
- [ ] Funnel analysis
- [ ] Cohort analysis
- [ ] Date functions

### Month 3 — Interview Mocks
- [ ] 10 StrataScratch problems (company tagged)
- [ ] 10 DataLemur problems
- [ ] Timed sessions (3 problems / 60 min)

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

### Window function — rank
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

## Problem Log

| # | Platform | Problem | Topic | Date | Difficulty |
|---|----------|---------|-------|------|------------|
| 1 | | | | | |

---

## Mistakes to Review
- 
