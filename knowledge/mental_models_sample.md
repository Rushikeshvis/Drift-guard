# Mental Models (Sample)

*This is a representative excerpt from a larger, private mental-models file — 3 of 15+ documented models, shown to illustrate the entry structure (Situation, Wrong Model, Better Model, Decision Rule) rather than the full set.*

---

# Learning & Meta-Thinking

---

## Recognition vs Recall

**Situation:** Evaluating whether you actually know something, or just recognize it when you see it.

**Wrong Mental Model:** "If I understand the explanation, I know it."

**Better Mental Model:** Understanding and being able to produce are completely different skills. They require separate practice.

Levels of mastery:
1. Recognize the answer when shown.
2. Understand the answer when explained.
3. Solve with hints.
4. Solve independently.
5. Solve under time pressure.

Interview readiness requires level 4 and 5. Most studying only builds level 1 and 2.

**Decision Rule:** After studying something, ask: "Can I reproduce this from scratch right now, without looking?" If no, it's not learned — it's recognized.

---

# Debugging

---

## Code Is Expressing Assumptions

**Situation:** When code produces unexpected results or errors.

**Wrong Mental Model:** "My code is wrong because I made a mistake."

**Better Mental Model:** "My code is correctly expressing an assumption I made — but that assumption may not match reality."

This reframe forces you to find the assumption instead of just staring at the syntax.

**Application:** When something fails, ask in order:
1. What did I assume would happen here?
2. What did the computer actually do?
3. Where did those two things diverge?

**Decision Rule:** Before blaming the language or the library, state your assumption out loud. Then verify the assumption is actually true.

---

# SQL

---

## Window Function vs Subquery

**Situation:** When you need to calculate an aggregate but keep the original row count.

**Wrong Mental Model:** "I need to aggregate, so I must collapse rows (GROUP BY) or use a subquery."

**Better Mental Model:** "Window functions are 'side-calculations' that preserve the original table dimensions."

**Decision Rule:** If the output requires the same number of rows as the input, do NOT use a subquery. Use OVER().
