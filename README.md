# drift-guard

A structured behavioral system for directing an AI assistant through a multi-week, high-stakes learning process — designed to catch the specific ways LLM-based agents drift, forget context, or produce shallow answers when instructions are ambiguous or underspecified.

> This repo shows a representative slice of the system — templates and sample knowledge-base entries, not the complete private files (personal logs, full knowledge base, and the core behavioral rule set are kept private). Shared for portfolio/review purposes. All rights reserved — not licensed for reuse.

---

## The problem this solves

Generic chat sessions with an AI assistant don't hold up over weeks of use. Three failure modes show up reliably:

1. **Context loss** — the assistant re-explains things already covered, or contradicts earlier guidance.
2. **Drift on ambiguity** — when instructions are incomplete, the assistant fills gaps with its own assumptions instead of flagging them, and those assumptions silently compound.
3. **No mistake memory** — the same error gets corrected, forgotten, and re-made, because nothing tracks that it happened before.

drift-guard is a set of files and explicit behavioral rules that give the assistant persistent, structured context across sessions, and force it to distinguish between *recognizing* an explanation and actually *reproducing* the underlying skill.

## How it works

```
templates/     → structured intake forms (daily/weekly/monthly) that force specific,
                  falsifiable input instead of vague self-assessment
knowledge/     → a living taxonomy of recurring errors, stable concepts, and reasoning
                  patterns, each with a status (Active / Improving / Fixed)
progress/      → dated logs that feed the knowledge base — nothing is added to
                  knowledge/ until it's shown up more than once
```

The assistant operates under an explicit rule set (kept private, described below) that governs:

- **How to handle a "stuck" state** — a graded escalation sequence (clarifying question → directional hint → partial structure → full explanation) rather than jumping straight to answers.
- **How to grade understanding** — a four-level mastery model (Recognition → Recall → Application → Transfer), so "I understand" is never accepted as evidence on its own.
- **When to intervene on a repeated mistake** — the assistant is required to name a recurring error explicitly by pattern, not just correct it silently, so the same root cause doesn't get re-diagnosed from scratch each time.
- **When to switch modes** — Socratic/probing behavior is the default for deliberate practice, but the same system explicitly defines when the assistant should switch to direct, non-Socratic help (debugging, documentation requests, brainstorming) instead of forcing every interaction into a quiz.

## A concrete example

From a real logged session: a recurring mistake ("defaulting to subqueries instead of window functions") was flagged for the second time. Rather than just supplying the corrected query, the system's rules required:

1. Naming the pattern explicitly ("Subquery instinct — this is the second time this has shown up").
2. Stating the root cause (defaulting to a familiar `GROUP BY` mental model instead of recognizing when a row-preserving calculation was needed).
3. Producing a specific, falsifiable correction rule ("if the output needs the same row count as the input, don't use a subquery — use `OVER()`").
4. Logging it to the error-pattern taxonomy with a status, so the *next* occurrence gets checked against this one instead of being treated as new.

See [`progress/daily/2026-07-16_sample.md`](./progress/daily/2026-07-16_sample.md) for the unedited log this was pulled from, and [`knowledge/error_patterns_sample.md`](./knowledge/error_patterns_sample.md) for how it was formalized into the taxonomy.

## What's in this repo vs. what's private

| Included | Why |
|---|---|
| `templates/` (sample) | Shows the intake structure without exposing the full rule engine |
| `knowledge/*_sample.md` | 3–5 real entries per file, enough to show the taxonomy's shape |
| `progress/daily/2026-07-16_sample.md` | One real, unedited session log |

| Excluded | Why |
|---|---|
| Core behavioral rule set / system instructions | This is the actual mechanism — the part that took the most design work |
| Full knowledge base | Accumulated over months; the samples here are representative, not exhaustive |
| Personal profile / goals / full logs | Personal data, not relevant to evaluating the system design |

## Why I built this

I wanted an AI assistant that could hold me to a standard over weeks, not just answer questions in isolation — and building it required thinking carefully, in detail, about exactly how these agents fail: where they over-assume, where they take a vague instruction and quietly narrow or widen it, and where "sounds right" gets accepted in place of "is verified." That's the same lens I'd bring to reviewing task and dataset quality for training material.
