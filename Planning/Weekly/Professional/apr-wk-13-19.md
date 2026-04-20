---
date: 2026-04-20
week: W16
tags: [weekly-review, professional]
---

# Professional Weekly Review - Apr 13-19, 2026

## Key Technical Work

| Project / Task | What I Did | Tech Used | Impact |
|---------------|-----------|-----------|--------|
| CAD extraction research and matching workflow | Researched tooling for extracting parts and connections from CAD files, completed matching runs for CAD datasets, and selected an extraction approach for downstream analysis. | CAD data tooling, Python, dataset evaluation | Moved the workflow from exploration into a more executable analysis process with a clearer path for implementation. |
| BOM-STEP reconciliation diagnostics | Built a post-processing pipeline around `bom_match.json` to convert raw outputs into structured diagnostics for exact matches, mismatches, fuzzy candidates, filtered STEP records, and suspected missing BOM items. | Python, JSON processing, reconciliation analysis | Made matching results easier to interpret, compare, and review systematically. |
| Match quality framework | Reframed evaluation from a simple exact-match metric into a broader coverage model spanning exact matches, quantity mismatches, naming drift, fuzzy candidates, and likely missing parts. | Analytical modeling, reporting design | Improved visibility into where reconciliation quality breaks down and what type of fix is needed. |
| Root-cause and benchmark analysis | Analyzed recurring mismatch ratios such as `0.5`, `0.25`, `0.75`, and `2.0`, added high-confidence fuzzy-match diagnostics, prioritized missing-part review by BOM quantity, and benchmarked datasets to identify `Y24 CSTN_Di` as the strongest baseline. | Data analysis, fuzzy matching diagnostics, comparative benchmarking | Clarified the difference between true coverage gaps, scope mismatches, and naming normalization issues while establishing a stable reference set for future refinement. |

---

## Skills & Learning

- **Skills exercised:** Python scripting for reconciliation analysis, JSON-based pipeline design, fuzzy-match diagnostics, comparative dataset benchmarking, and technical report design.
- **New things learned:** Quantity mismatch patterns can reflect representation-scope differences between BOMs and CAD exports rather than straightforward matching failures.
- **Courses / reading:**

---

## DS Job Search

- **Applications sent:**
- **Responses / interviews:**
- **Portfolio pieces updated:**
- **Resume-ready achievements this sprint:**
  - Built a reusable analytics workflow for BOM-to-CAD reconciliation and diagnostic reporting.
  - Developed a multi-factor evaluation framework for identifying matching, naming, and quantity-scope issues across engineering datasets.

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

- **Strongest technical contribution:** Built a structured reconciliation and diagnostic framework that made CAD-to-BOM matching results more actionable and easier to benchmark across datasets.
- **Biggest challenge:** Separating true missing-part problems from naming drift and representation-scope differences in imperfect engineering data.
- **What to focus on next two weeks:** Validate the selected extraction plan on additional datasets and reduce manual review by tightening normalization and mismatch classification rules.

---
*[[Knowledge/]] | [[Planning/Weekly/Professional/]]*
