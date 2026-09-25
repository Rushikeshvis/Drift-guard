# Concepts (Sample)

*This is a representative excerpt from a larger, private concepts knowledge base — 4 of 25+ documented concepts, shown to illustrate the entry structure (Definition, Intuition, Example, Common Confusion) rather than the full base.*

---

# SQL

---

## Window Functions

### Definition

Window functions perform calculations across a set of rows related to the current row, without collapsing those rows into a single group output the way GROUP BY does.

### Intuition

GROUP BY destroys individual rows — you only see the aggregate. Window functions add an aggregate column *alongside* each row. Every row stays visible.

Think of it as: "Calculate something across a group, but show the result on each row individually."

### Example

```sql
SELECT
  customer_id,
  order_date,
  amount,
  SUM(amount) OVER (PARTITION BY customer_id) AS customer_total,
  ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY order_date) AS order_rank
FROM orders;
```

- `PARTITION BY` defines the group (like GROUP BY)
- `ORDER BY` inside the window defines ranking or sequence
- Every original row is preserved

### Common Confusion

Thinking PARTITION BY is the same as GROUP BY. PARTITION BY keeps all rows. GROUP BY reduces them.

---

## GROUP BY

### Definition

GROUP BY combines rows with the same values into groups so aggregate calculations can be performed on each group.

### Intuition

GROUP BY creates buckets. Each unique value of the grouped column becomes its own bucket. Then aggregation asks a question about everything inside each bucket.

### Example

| Customer | Amount |
|---|---|
| A | 100 |
| A | 200 |
| B | 300 |

`GROUP BY customer` creates:
- Bucket A → [100, 200] → SUM = 300
- Bucket B → [300] → SUM = 300

### Common Confusion

Thinking GROUP BY sorts rows. It doesn't. It creates groups. ORDER BY is responsible for sorting the output.

---

# Machine Learning

---

## Overfitting

### Definition

Overfitting occurs when a model learns the training data too specifically and performs poorly on unseen data.

### Intuition

The model memorizes answers instead of learning the pattern. Like a student who memorizes previous exam answers without understanding the subject — they fail any new question.

### Signs

- Very high training accuracy
- Significantly lower validation/test accuracy

### Example

A decision tree with no depth limit will memorize every training example. Training accuracy: 100%. Test accuracy: much lower.

### Common Confusion

Thinking high training accuracy is always good. High training accuracy with low validation accuracy is a red flag — it means the model memorized instead of generalized.

---

## Variance

### Definition

Variance measures how sensitive a model is to changes in the training data.

### Intuition

Train the same model architecture on slightly different datasets. If the model produces very different results each time, it has high variance — it's unstable and learned the specific noise in the training data.

High variance → model is too complex → overfits.

Mental shortcut: "How much does my model change if my training data changes slightly?"

### Common Confusion

Thinking variance means the spread of predictions. In the ML context, variance means sensitivity to training data variation, not the spread of a single model's output.
