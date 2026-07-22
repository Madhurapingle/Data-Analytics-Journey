#  Day 13 - Multiple Aggregate Functions & HAVING

### Date:21 july 2026

##  Objective

- Learn to use multiple aggregate functions in one query.
- Understand the purpose of HAVING.
- Learn the difference between WHERE and HAVING.
- Build business reports using aggregate functions.
- Prepare for SQL interview questions.

---

# Multiple Aggregate Functions

Instead of creating multiple reports, companies usually create one summarized report.

Example:

```sql
SELECT
    CASE
        WHEN Salary >= 70000 THEN 'High'
        WHEN Salary >= 50000 THEN 'Medium'
        ELSE 'Low'
    END AS Salary_Level,

    COUNT(*) AS Total_Employees,
    SUM(Salary) AS Total_Salary,
    AVG(Salary) AS Average_Salary

FROM Employees

GROUP BY
CASE
    WHEN Salary >= 70000 THEN 'High'
    WHEN Salary >= 50000 THEN 'Medium'
    ELSE 'Low'
END;
```

---

# Output Example

| Salary_Level | Total_Employees | Total_Salary | Average_Salary |
|--------------|----------------:|-------------:|---------------:|
| High | 2 | 157000 | 78500 |
| Medium | 1 | 65000 | 65000 |
| Low | 2 | 75000 | 37500 |

---

# Why Use One Report?

Instead of creating:

- Employee Count Report
- Salary Report
- Average Salary Report

Companies combine everything into one report because:

- Saves time
- Easy to understand
- Easy to present
- Better dashboards
- Faster decision-making

---

# Aggregate Functions

## COUNT()

Counts the total number of rows.

Example:

```sql
COUNT(*)
```

---

## SUM()

Calculates the total of numeric values.

Example:

```sql
SUM(Salary)
```

---

## AVG()

Calculates the average.

Formula:

Average = SUM ÷ COUNT

Example:

```sql
AVG(Salary)
```

---

# WHERE vs HAVING

| WHERE | HAVING |
|--------|---------|
| Filters rows | Filters groups |
| Executes before GROUP BY | Executes after GROUP BY |
| Cannot use aggregate functions | Can use aggregate functions |

---

# Example

```sql
SELECT Department,
       COUNT(*) AS Employees
FROM Employees
GROUP BY Department
HAVING COUNT(*) > 2;
```

---

# Why HAVING?

Aggregate functions are calculated after grouping.

Since WHERE executes before GROUP BY, aggregate functions like:

- COUNT()
- SUM()
- AVG()

cannot be used inside WHERE.

HAVING is used to filter grouped results.

---

# Execution Order

1. FROM
2. WHERE
3. GROUP BY
4. Aggregate Functions (COUNT, SUM, AVG...)
5. HAVING
6. SELECT
7. ORDER BY

---

# Business Examples

## HR Department

Show only departments having more than 10 employees.

---

## Finance Department

Show departments where average salary is greater than ₹75,000.

---

## Sales Department

Show customer categories with total sales above ₹10,00,000.

---

# Business Thinking

Companies prefer summarized reports because they:

- Save time
- Reduce confusion
- Improve dashboards
- Help managers make decisions faster
- Avoid unnecessary details
- Maintain privacy

---

# Interview Questions

## 1. Difference between WHERE and HAVING?

WHERE filters rows before grouping.

HAVING filters groups after grouping.

---

## 2. Why can't aggregate functions be used in WHERE?

Because aggregate functions are calculated after GROUP BY, while WHERE executes before GROUP BY.

---

## 3. Why combine COUNT(), SUM() and AVG()?

To answer multiple business questions in one report instead of running multiple queries.

---

## 4. Why do companies use one combined report?

- Easy to understand
- Saves time
- Better reporting
- Faster decision-making

---

# Memory Tricks

WHERE

↓

Rows

↓

Before GROUP BY

---

HAVING

↓

Groups

↓

After GROUP BY

---

COUNT()

↓

How many?

---

SUM()

↓

How much?

---

AVG()

↓

Average value

---

# Common Mistakes

❌ Using aggregate functions inside WHERE

```sql
WHERE COUNT(*) > 2
```

✔ Correct

```sql
HAVING COUNT(*) > 2
```

---

# Key Takeaways

- Multiple aggregate functions can be used in one query.
- One report is better than multiple reports.
- WHERE filters rows.
- HAVING filters grouped results.
- Aggregate functions work after GROUP BY.
- HAVING is required when filtering aggregate values.
- Business reports should be concise, meaningful, and easy to understand.
