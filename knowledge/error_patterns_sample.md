# Error Patterns (Sample)

*This is a representative excerpt from a larger, private error-pattern taxonomy — 5 of 15+ tracked patterns, shown to illustrate the structure and rigor rather than the full accumulated knowledge base.*

---

## Quick Reference Table

| Pattern | Category | Status | Frequency | Last Seen |
|---|---|---|---|---|
| Blank Page Coding Execution | Python | Active | High | 2026-07-14 |
| WHERE vs HAVING Confusion | SQL | Improving | Medium | 2026-07-14 |
| Subquery instinct (Window) | SQL | Active | High | 2026-07-16 |
| Variance Understanding | ML | Improving | Low | 2026-07-14 |
| Understanding vs Execution Gap | Learning | Active | Consistent | 2026-07-14 |

---

# Python

---

## Blank Page Coding Execution

| Field | Value |
|---|---|
| Status | Active |
| First observed | 2026-07-14 |
| Last seen | 2026-07-14 |
| Last reviewed | 2026-07-14 |
| Frequency | High |

**Pattern:** Understanding the logic but making syntax errors when writing from scratch.

**Common examples:**
- Missing `:`
- Incorrect indentation
- Missing parentheses
- Incorrect function syntax

**Root cause:** Conceptual understanding is ahead of implementation fluency. Recognition (understanding shown code) is not the same as recall (writing from memory).

**Why this matters:** Interviews test recall and execution, not understanding after seeing corrections.

**Correction rule:** Practice writing solutions without looking at examples. Track how many attempts were needed.

---

# SQL

---

## WHERE vs HAVING Confusion

| Field | Value |
|---|---|
| Status | Improving |
| First observed | 2026-07-14 |
| Last seen | 2026-07-14 |
| Last reviewed | 2026-07-14 |
| Frequency | Medium |

**Pattern:** Using WHERE for aggregate conditions.

**Wrong:**
```sql
WHERE SUM(amount) > 500
```

**Correct:**
```sql
HAVING SUM(amount) > 500
```

**Mental model:** WHERE filters individual rows (before grouping). HAVING filters groups (after grouping).

**Why this matters:** This distinction appears frequently in SQL interviews.

**Correction rule:** Ask: "Has aggregation already happened?" → Before: WHERE. After: HAVING.

---

## Subquery instinct (Window)

| Field | Value |
|---|---|
| Status | Active |
| First observed | 2026-07-16 |
| Last seen | 2026-07-16 |
| Last reviewed | 2026-07-16 |
| Frequency | High |

**Pattern:** Defaulting to subqueries when window functions are more efficient.

**Correction rule:** If the task involves ranking, running totals, or comparing rows to neighbors, check if a window function can replace a subquery.

---

# Machine Learning

---

## Variance Understanding

| Field | Value |
|---|---|
| Status | Improving |
| First observed | 2026-07-14 |
| Last seen | 2026-07-14 |
| Last reviewed | 2026-07-14 |
| Frequency | Low |

**Pattern:** Incomplete or incorrect initial understanding of variance.

**Old (incorrect) understanding:** Variance means prediction spread.

**Corrected understanding:** Variance measures how sensitive a model is to changes in training data. High variance = model changes significantly with different datasets = learns noise = overfits.

**Mental shortcut:** "How much does my model change if my training data changes slightly?"

**Why this matters:** Bias and variance questions are common in ML interviews.

**Correction rule:** Always connect variance to: different training samples, model stability, generalization.

---

# Learning Process

---

## Understanding vs Execution Gap

| Field | Value |
|---|---|
| Status | Active |
| First observed | 2026-07-14 |
| Last seen | 2026-07-14 |
| Last reviewed | 2026-07-14 |
| Frequency | Consistent |

**Pattern:** Can understand concepts after explanation but cannot reproduce them independently.

**Evidence:**
- SQL improves after corrections but errors return when writing from scratch.
- ML concepts become clearer through examples but explanations remain shallow.
- Coding syntax errors appear consistently during independent attempts.

**Root cause:** Recognition ability is ahead of recall ability. Understanding shown work is not the same as producing work from memory.

**Why this matters:** Interviews require producing answers under time pressure without external guidance.

**Correction rule:** Increase blank-page coding, timed practice, explaining concepts without notes, and repeated retrieval practice. Track first-attempt rate.
