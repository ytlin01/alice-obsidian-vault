---
date: {{date:YYYY-MM-DD}}
day: {{date:dddd}}
week: W{{date:ww}}
calorie_goal: 1600
breakfast_calories: 0
lunch_calories: 0
dinner_calories: 0
snacks_calories: 0
drink_calories: 0
calorie_total: 0
water_cups: 0
water_goal_cups: 8
water_ml_per_cup: 250
tags: [daily]
---

# {{date:MMMM D, YYYY}}

## Morning Check-In

- **Sleep (hrs):**
- **Napped:** Yes / No
- **Weight:**
- **Pooped:** ==Yes== / No
- **Supplements:**
  - [ ] Vitamin K+D
  - [ ] Vitamin B
  - [ ] Vitamin C
  - [ ] Bromelain powder

---

## What I Ate Today

- **Breakfast:**
- **Lunch:**
- **Dinner:**
- **Snacks:**
- **Water:** 0 / 8 cups (0ml / 2000ml)
- **Other Drinks:**

 **Calorie Total:** 0 / 1600 kcal

---

## Tasks

=== start-multi-column: tasks
```column-settings
Number of Columns: 2
```

**Personal**
- [ ]

&nbsp;

=== column-break ===

**Work**
- [ ]

&nbsp;

=== end-multi-column

---

## Routine

- [ ] Workout - [[Health/Workouts/{{date:YYYY-MM-DD}}]]
- [ ] Skincare
- [ ] Mindfulness
- [ ] Self-Growth *(DS job search / PhD / learning)*

**Self-growth notes:**

---

## Technical Work Summary

---

## Self-Growth Log

- **What I worked on:**
- **Job apps / leads:**
- **What I learned:**

---

## Daily Wins & Reflections

- **Win of the day:**
- **One thing to carry into tomorrow:**

---
<%*
// Auto-create workout note when daily note is generated
const workoutPath = `Health/Workouts/${tp.date.now("YYYY-MM-DD")}.md`;
if (!await tp.file.exists(workoutPath)) {
  const template = tp.file.find_tfile("Workout Log");
  if (template) {
    await tp.file.create_new(template, tp.date.now("YYYY-MM-DD"), false, app.vault.getAbstractFileByPath("Health/Workouts"));
  }
}
_%>
