# ⚙️ Setup Instructions

Follow these steps to get everything working in Obsidian.

---

## 1. Import the vault folder

Drop the entire `DS-Interview-Prep` folder into your Obsidian vault. All notes will appear in your file explorer.

---

## 2. Set up the Weekly Template (Templater plugin)

1. Open **Settings → Templater**
2. Set your **Template folder** to `DS-Interview-Prep/Templates`
3. To create a new weekly note: open command palette → `Templater: Create new note from template` → select `📅 Weekly Template`
4. The template uses these Templater variables — make sure Templater is enabled:
   - `{{date:YYYY-[W]WW}}` — current week number
   - `{{monday:YYYY-MM-DD}}` — date of Monday this week
   - `{{tuesday:YYYY-MM-DD}}` through `{{sunday:YYYY-MM-DD}}`

> **Note:** If you use the **Calendar** plugin, you can link weekly notes directly. In Calendar settings, set the weekly note template to `DS-Interview-Prep/Templates/📅 Weekly Template`.

---

## 3. Tasks plugin

The Dashboard uses Tasks plugin queries. These will auto-populate once you start checking off tasks in your weekly notes.

Tasks use this format throughout the weekly template:
```
- [ ] #study Task description 📅 YYYY-MM-DD
```

- `#study` tag lets the dashboard filter only study tasks
- `📅 YYYY-MM-DD` is the due date (Tasks plugin format)

To mark a task done, click the checkbox or use `Tasks: Toggle task done` from the command palette.

---

## 4. Calendar plugin

- The weekly notes created from the template will appear in your Calendar sidebar automatically
- Click any week in the calendar to open that week's note
- Saturday and Sunday sessions are included — they'll show up on weekend dates

---

## 5. Recommended folder structure

```
DS-Interview-Prep/
├── 🏠 Dashboard.md          ← Your home base
├── 📚 Resources.md
├── 🔵 LeetCode Tracker.md
├── 🟢 SQL Tracker.md
├── 🟣 ML Concepts.md
├── 🟡 System Design Notes.md
├── ⚙️ Setup Instructions.md  ← This file
├── Templates/
│   └── 📅 Weekly Template.md
└── Weekly Notes/             ← Create this folder for your weekly notes
    ├── Week 1 (2024-W01).md
    ├── Week 2 (2024-W02).md
    └── ...
```

---

## 6. Daily workflow

1. **5:30 PM weekdays / 10:00 AM weekends** — open Obsidian
2. Navigate to your current weekly note (or create one from the template)
3. Find today's session, complete the tasks, fill in the notes
4. Check off each task as you go
5. On **Sunday**, update the stats table and the progress tracker in `🏠 Dashboard`

---

## 7. Optional: Pin the Dashboard

Right-click `🏠 Dashboard.md` in the file explorer → **Pin** — so it's always one click away.
