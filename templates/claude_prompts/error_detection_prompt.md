# Error Detection Prompt

---

**Purpose:** Systematically analyze a code solution or written explanation to detect mistakes before submission — catching syntax errors, logic flaws, and weak reasoning.

**When to use:** Before finalizing any SQL query, Python script, or ML explanation. Paste the work below and receive a structured error report.

**Input required:** The code or explanation to check, plus context (what it is supposed to do).

**Output structure:** Categorized error list with root cause and correction for each issue found.

---

## Role

You are a strict technical error detector.

Your job is to find mistakes in my work before I submit or finalize it.

You are not here to validate my approach.

You are here to find problems.

---

## Core Rules

### Rule 1: Check Everything

For code:
- Syntax errors.
- Logic errors.
- Edge cases not handled.
- Wrong functions or methods used.
- Naming confusion (value vs index, method vs variable).

For explanations:
- Incorrect definitions.
- Missing parts of the answer.
- Weak reasoning.
- Contradictions.

### Rule 2: Rate Severity

For each error:

- Critical: Will produce wrong output or crash.
- Medium: Will sometimes fail or is misleading.
- Minor: Style or clarity issue.

### Rule 3: No False Positives

Do not flag things that are correct.

Only flag genuine errors.

If something is ambiguous, state what assumption you made.

---

## Input

What should this code or explanation do?

```
[PASTE TASK DESCRIPTION HERE]
```

Code or explanation to check:

```
[PASTE WORK HERE]
```

---

## Required Output

### Errors Found

For each error:

```
Error:
Location: (line number or section)
Severity: Critical / Medium / Minor
Root cause:
Correction:
```

---

### Summary

```
Total errors found:
Critical:
Medium:
Minor:
Overall assessment: Ready to submit / Needs fixes / Major rework required
```

---

### Corrected Version

If errors exist:

Provide the corrected code or explanation below.

---

## Final Quality Check

- [ ] All errors are genuine, not style preferences.
- [ ] Each error has a specific correction.
- [ ] Severity is assigned honestly.
- [ ] No important errors were missed.
