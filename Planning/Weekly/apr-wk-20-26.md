---
date: 2026-04-26
week: W17
tags: [weekly-review, personal, professional]
---

# Weekly Review - Apr 20-26, 2026

## Weekly Snapshot

- **Theme of the week:**
- **Main win:**
- **Main challenge:**
- **What felt most important:**
- **How complete the week felt:**

---

## Personal Review

### Body Stats

| | Start of Week | End of Week | Change |
|--|--------------|------------|--------|
| Weight | 65.43 kg | 64.40 kg | -1.03 kg |

---

### Health & Routine Graphs

=== start-multi-column: weekly-graphs
```column-settings
Number of Columns: 2
```

#### Sleep Trend

```advanced-chart
{
  "type": "line",
  "data": {
    "labels": ["Apr 20", "Apr 21", "Apr 22"],
    "datasets": [
      {
        "label": "Sleep Hours",
        "data": [6.5, 6.5, 6],
        "borderColor": "#5B8DEF",
        "backgroundColor": "rgba(91, 141, 239, 0.18)",
        "pointBackgroundColor": "#5B8DEF",
        "pointBorderColor": "#ffffff",
        "pointRadius": 4,
        "pointHoverRadius": 6,
        "borderWidth": 3,
        "fill": true,
        "tension": 0.35
      }
    ]
  },
  "options": {
    "plugins": {
      "legend": {
        "display": false
      },
      "title": {
        "display": true,
        "text": "Sleep Hours"
      }
    },
    "scales": {
      "y": {
        "min": 0,
        "max": 10,
        "ticks": {
          "stepSize": 2
        },
        "grid": {
          "color": "rgba(120, 120, 120, 0.12)"
        }
      },
      "x": {
        "grid": {
          "display": false
        }
      }
    }
  }
}
```

#### Weight Snapshot

```advanced-chart
{
  "type": "bar",
  "data": {
    "labels": ["Apr 20", "Apr 21", "Apr 22"],
    "datasets": [
      {
        "label": "Weight",
        "data": [65.43, 65.10, 64.40],
        "backgroundColor": [
          "rgba(51, 168, 132, 0.60)",
          "rgba(51, 168, 132, 0.68)",
          "rgba(51, 168, 132, 0.78)"
        ],
        "borderColor": ["#33A884", "#33A884", "#33A884"],
        "borderWidth": 2,
        "borderRadius": 12,
        "barThickness": 30
      }
    ]
  },
  "options": {
    "plugins": {
      "legend": {
        "display": false
      },
      "title": {
        "display": true,
        "text": "Weight Trend"
      }
    },
    "scales": {
      "y": {
        "min": 63,
        "max": 66,
        "grid": {
          "color": "rgba(120, 120, 120, 0.12)"
        }
      },
      "x": {
        "grid": {
          "display": false
        }
      }
    }
  }
}
```

&nbsp;

=== column-break ===

#### Supplement Balance

```advanced-chart
{
  "type": "doughnut",
  "data": {
    "labels": ["Vitamin K+D", "Vitamin C", "Vitamin B", "Bromelain"],
    "datasets": [
      {
        "data": [1, 1, 0, 1],
        "backgroundColor": [
          "#F4A261",
          "#E9C46A",
          "rgba(160, 160, 160, 0.35)",
          "#D26B8A"
        ],
        "borderColor": [
          "#F4A261",
          "#E9C46A",
          "rgba(160, 160, 160, 0.35)",
          "#D26B8A"
        ],
        "borderWidth": 1,
        "hoverOffset": 6
      }
    ]
  },
  "options": {
    "plugins": {
      "legend": {
        "position": "bottom"
      },
      "title": {
        "display": true,
        "text": "Supplement Checkmarks"
      }
    },
    "cutout": "62%"
  }
}
```

#### Routine Radar

```advanced-chart
{
  "type": "radar",
  "data": {
    "labels": ["Workout", "Skincare", "Mindfulness", "Self-Growth"],
    "datasets": [
      {
        "label": "Completed Days",
        "data": [0, 0, 0, 1],
        "backgroundColor": "rgba(210, 107, 138, 0.2)",
        "borderColor": "#D26B8A",
        "pointBackgroundColor": "#D26B8A",
        "pointBorderColor": "#ffffff",
        "pointRadius": 4,
        "borderWidth": 2.5
      }
    ]
  },
  "options": {
    "plugins": {
      "legend": {
        "display": false
      },
      "title": {
        "display": true,
        "text": "Routine Completion"
      }
    },
    "scales": {
      "r": {
        "min": 0,
        "max": 3,
        "ticks": {
          "stepSize": 1,
          "backdropColor": "transparent"
        },
        "grid": {
          "color": "rgba(120, 120, 120, 0.16)"
        },
        "angleLines": {
          "color": "rgba(120, 120, 120, 0.14)"
        }
      }
    }
  }
}
```

&nbsp;

=== end-multi-column

- **Sleep trend note:** Sleep has been steady but short, sitting in a narrow `6.0-6.5 hr` range across Apr 20-22.
- **Weight trend note:** Logged weight moved down from `65.43 kg` to `64.40 kg` over the first three days of the week.
- **Supplement trend note:** Supplements were taken on `2 / 3` logged days, with coverage still inconsistent.
- **Routine trend note:** `Self-Growth` has one completion so far; workout, skincare, and mindfulness are still at zero.

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

- **Days with sleep logged:** 3 / 3 logged days
- **Days with weight logged:** 3 / 3 logged days
- **Supplement days:** 2 / 3 logged days
- **Days I hit my calorie goal:** 2 / 2 logged intake days
- **Protein consistency:** Mixed
- **Water intake:** Good / Needs work
- **Best meal this week:** Apr 21 lunch was the strongest logged meal of the week so far and still kept the day within calorie range.
- **Worst slip:** Apr 22 intake logging is still incomplete, so the weekly calorie picture is only partial right now.

---

### Logged Routine Completion

| Routine | Mon | Tue | Wed | Thu | Fri | Sat | Sun |
|---------|-----|-----|-----|-----|-----|-----|-----|
| Workout | | | | | | | |
| Skincare | | | | | | | |
| Mindfulness | | | | | | | |
| Self-Growth | | | | | | | |

---

### Wins This Week

1.
2.
3.

### What To Improve

1.
2.

---

### Diary Highlights

-

---

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
