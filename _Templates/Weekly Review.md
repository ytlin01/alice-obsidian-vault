---
date: {{date:YYYY-MM-DD}}
week: W{{date:ww}}
tags: [weekly-review, personal, professional]
---

# Weekly Review - W{{date:ww}}

## Weekly Snapshot

- **Theme of the week:**
- **Main win:**
- **Main challenge:**
- **What felt most important:**
- **How complete the week felt:**

---

## Personal Review

### Body Stats

| Metric | Start of Week | End of Week | Change |
|--|--|--|--|
| Weight | | | |
| Sleep average | | | |

### Health & Routine Graphs

> Reuse the `wk13-19` / `wk20-26` chart layout here so each weekly review includes the same sleep, weight, supplement, and routine visuals.

- **Sleep trend note:**
- **Weight trend note:**
- **Supplement trend note:**
- **Routine trend note:**

### Daily Calories

```dataviewjs
const pages = dv.pages('"Planning/Daily Notes"')
  .where(p => p.week === dv.current().week)
  .where(p => p.date)
  .sort(p => p.date, 'asc');

const labels = pages.map(p => window.moment(p.date.toString()).format("MMM D"));
const totals = pages.map(p => Number(p.calorie_total ?? 0));
const goal = Number(
  pages.find(p => Number(p.calorie_goal ?? 0) > 0)?.calorie_goal
  ?? 1600
);
const maxValue = Math.max(goal, ...totals, 1);

if (!labels.length) {
  dv.paragraph("No calorie totals logged yet for this week.");
} else {
  const wrapper = dv.el("div", "", { cls: "daily-calorie-chart" });
  wrapper.style.display = "flex";
  wrapper.style.alignItems = "flex-end";
  wrapper.style.gap = "12px";
  wrapper.style.minHeight = "220px";
  wrapper.style.padding = "16px 12px 8px";
  wrapper.style.border = "1px solid rgba(120, 120, 120, 0.18)";
  wrapper.style.borderRadius = "16px";
  wrapper.style.background = "linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.03))";

  for (let i = 0; i < labels.length; i++) {
    const column = wrapper.createEl("div");
    column.style.flex = "1";
    column.style.display = "flex";
    column.style.flexDirection = "column";
    column.style.alignItems = "center";
    column.style.gap = "8px";

    const value = column.createEl("div", { text: `${totals[i]} kcal` });
    value.style.fontSize = "12px";
    value.style.color = "var(--text-muted)";

    const rail = column.createEl("div");
    rail.style.width = "100%";
    rail.style.maxWidth = "56px";
    rail.style.height = "160px";
    rail.style.display = "flex";
    rail.style.alignItems = "flex-end";
    rail.style.background = "rgba(120, 120, 120, 0.10)";
    rail.style.borderRadius = "14px";
    rail.style.overflow = "hidden";
    rail.style.position = "relative";

    const goalLine = rail.createEl("div");
    goalLine.style.position = "absolute";
    goalLine.style.left = "0";
    goalLine.style.right = "0";
    goalLine.style.bottom = `${(goal / maxValue) * 100}%`;
    goalLine.style.borderTop = "2px dashed rgba(232, 148, 62, 0.75)";

    const bar = rail.createEl("div");
    bar.style.width = "100%";
    bar.style.height = `${(totals[i] / maxValue) * 100}%`;
    bar.style.background = totals[i] > goal
      ? "linear-gradient(180deg, #f4a261, #e76f51)"
      : "linear-gradient(180deg, #7cc6fe, #5b8def)";
    bar.style.borderRadius = "14px 14px 0 0";

    const label = column.createEl("div", { text: labels[i] });
    label.style.fontSize = "12px";
  }

  dv.paragraph(`Goal line: ${goal} kcal`);
}
```

```dataview
TABLE date AS Date, breakfast_calories AS Breakfast, lunch_calories AS Lunch, dinner_calories AS Dinner, snacks_calories AS Snacks, drink_calories AS Drinks, calorie_total AS Total
FROM "Planning/Daily Notes"
WHERE week = this.week
SORT date ASC
```

### Health & Nutrition

- **Days with sleep logged:** / logged days
- **Days with weight logged:** / logged days
- **Supplement days:** / logged days
- **Days I hit my calorie goal:** / 7
- **Protein consistency:** Yes / No
- **Water intake:** Good / Needs work
- **Best meal this week:**
- **Biggest slip:**

### Logged Routine Completion

| Routine | Mon | Tue | Wed | Thu | Fri | Sat | Sun |
|---------|-----|-----|-----|-----|-----|-----|-----|
| Workout | | | | | | | |
| Skincare | | | | | | | |
| Mindfulness | | | | | | | |
| Self-Growth | | | | | | | |

### Wins This Week

1.
2.
3.

### What To Improve

1.
2.

### Diary Highlights

- 

### Plan For Next Week

- **Workout focus:**
- **Health focus:**
- **Work focus:**
- **Habit to double down on:**
- **One thing to let go of:**

---

## Key Technical Work

| Project / Task | What I Did | Tech Used | Impact |
|---------------|-----------|-----------|--------|
| | | | |
| | | | |
| | | | |

---

## Skills & Learning

- **Skills exercised:**
- **New things learned:**
- **Courses / reading:**

---

## DS Job Search

- **Applications sent:**
- **Responses / interviews:**
- **Portfolio pieces updated:**
- **Resume-ready achievements this sprint:**

---

## DS Interview Prep Progress

| Track | This Sprint | Cumulative | Target (3mo) |
|-------|-------------|------------|--------------|
| LeetCode problems | | | 100-120 |
| SQL problems | | | ~60 |
| ML concepts learned | | | 10-15 |
| System designs practiced | | | 4-6 |

- **Strongest area:**
- **Weakest area / focus next:**
- **New patterns added to** [[LeetCode Patterns]] / [[SQL Patterns]]:

---

## PhD Progress

- **What I worked on:**
- **Milestones / deadlines:**
- **Next steps:**

---

## Reflection

- **Strongest contribution this week:**
- **Biggest challenge:**
- **What to focus on next two weeks:**
- **What I want to repeat next week:**

---
*[[Planning/Daily Notes/]] | [[Health/Diet Goals]] | [[Knowledge/]]*
