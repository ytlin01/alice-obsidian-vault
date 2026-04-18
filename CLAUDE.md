# Claude Instructions for Alice's Vault

## Agents

[[Claude Agents/FOOD_AGENT]]
[[Claude Agents/REVIEW_AGENT]]
[[Claude Agents/WORKOUT_AGENT]]
[[Claude Agents/MEAL_PREP_AGENT]]

---

## Vault Structure

```
Planning/Daily Notes/YYYY-MM-DD.md   ← daily notes
Health/Workouts/YYYY-MM-DD.md        ← workout logs
Health/Meal Prep/                    ← weekly meal prep notes
Health/Diet Goals.md                 ← macro targets & body stats
Reviews/Personal/                    ← weekly & monthly personal reviews
Reviews/Professional/                ← biweekly professional reviews
Knowledge/                           ← knowledge base notes
DS-Interview-Prep/                   ← data science interview prep system
_Templates/                          ← all note templates
```

---

## Agent Routing

Use the correct agent automatically based on what Alice says — she should not have to specify which agent to use.

| Trigger | Agent |
|---------|-------|
| Mentions food, drinks, calories, or meal logging | FOOD_AGENT |
| Mentions a workout, exercises, sets/reps, or running | WORKOUT_AGENT |
| Asks about grocery list, meal planning, or meal prep | MEAL_PREP_AGENT |
| Asks to fill in / summarize a weekly or monthly review | REVIEW_AGENT |

---

## General Behavior

- **Today's date is always available from context.** Use it to resolve "today", "yesterday", "this week", etc.
- **Default to today's daily note** (`Planning/Daily Notes/YYYY-MM-DD.md`) for any logging unless Alice specifies a different date.
- **Never overwrite existing content.** Always append or update in place.
- **Never fabricate data.** If a file or field is missing, say so rather than guessing.
- **Create files from templates when they don't exist** (daily notes, workout logs) rather than refusing or erroring.
- **Keep tone casual and brief.** Confirm what was done in one line. No unsolicited advice.

---

## File Creation Rules

- **Daily note missing?** Create from `_Templates/Daily Note.md`, filling in the correct date, day name, and week number.
- **Workout log missing?** Create from `_Templates/Workout Log.md`, filling in the date.
- **Meal prep note missing?** Create from `_Templates/Meal Prep.md` for the current week.
- **Review file missing?** Create from the appropriate template in `_Templates/` before populating.

---

## Vault Maintenance

When asked to do a vault check or organize the vault:
1. Check for broken wikilinks (folders or files that are referenced but don't exist)
2. Check for missing daily notes for recent dates
3. Check for workout log files referenced in daily notes but not created
4. Flag unfilled template files (fields that are still blank/placeholder)
5. Report findings organized by severity before making any changes

---

## DS Interview Prep

The `DS-Interview-Prep/` folder is Alice's active data science job search study system. When she asks about interview prep, study progress, or practice problems:
- Reference `DS-Interview-Prep/Dashboard.md` for overall progress
- Log LeetCode problems to `DS-Interview-Prep/LeetCode Tracker.md`
- Log SQL problems to `DS-Interview-Prep/SQL Tracker.md`
- Reference `DS-Interview-Prep/ML Concepts.md` for concept review
- Study schedule: weekdays 5:30 PM, weekends 10:00 AM (from Setup Instructions)

---

## Alice's Routine (for context)

Daily tracking targets:
- Supplements: Vitamin K+D, Vitamin B, Vitamin C, Bromelain powder
- Routine: Workout, Skincare, Mindfulness, Self-Growth

Self-growth focus areas: DS job search, PhD, general learning.
