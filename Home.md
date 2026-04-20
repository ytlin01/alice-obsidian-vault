---
tags: [dashboard]
---

# Home

> `= dateformat(date(today), "cccc, MMMM d, yyyy")`

## Today

`= link("Planning/Daily Notes/" + dateformat(date(today), "yyyy-MM-dd"), "Daily note")`  ·  `= link("Health/Workouts/" + dateformat(date(today), "yyyy-MM-dd"), "Workout log")`  ·  [[Knowledge/DS Interview Prep/Dashboard|DS Prep]]

---

=== start-multi-column: home
```column-settings
Number of Columns: 2
Column Size: Standard
Border: off
```

### Planning

- [[Planning/Daily Notes/|Daily Notes]]
- [[Planning/Weekly/|Weekly]]
- [[Planning/Monthly/|Monthly]]

&nbsp;

=== column-break ===

### Health

- [[Health/Workouts/|Workouts]]
- [[Health/Meal Prep/|Meal Prep]]
- [[Health/Diet Goals|Diet Goals]]

&nbsp;

=== end-multi-column

---

=== start-multi-column: home-2
```column-settings
Number of Columns: 2
Column Size: Standard
Border: off
```

### Knowledge

- [[Knowledge/DS Interview Prep/Dashboard|DS Interview Prep]]
- [[Knowledge/|Knowledge Base]]

&nbsp;

=== column-break ===

### Templates

- [[_Templates/Daily Note|Daily Note]]
- [[_Templates/DS Study Weekly|DS Study Weekly]]
- [[_Templates/|All Templates]]

&nbsp;

=== end-multi-column

## Recent

```dataview
LIST
FROM "Planning/Daily Notes"
SORT file.name DESC
LIMIT 3
```
