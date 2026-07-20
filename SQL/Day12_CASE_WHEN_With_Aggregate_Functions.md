# Day 12 - CASE WHEN with Aggregate Functions & ORDER BY

##  Objective

- Learn to combine `CASE WHEN` with aggregate functions.
- Create summarized business reports.
- Use `CASE WHEN` with `ORDER BY`.
- Understand real-world business use cases.
- Prepare for SQL interviews.

---

# CASE WHEN + COUNT()

## Purpose

Used to count how many records belong to each category.

### Example

```sql
SELECT
    CASE
        WHEN Salary >= 70000 THEN 'High'
        WHEN Salary >= 50000 THEN 'Medium'
        ELSE 'Low'
    END AS Salary_Level,
    COUNT(*) AS Total_Employees
FROM Employees
GROUP BY
    CASE
        WHEN Salary >= 70000 THEN 'High'
        WHEN Salary >= 50000 THEN 'Medium'
        ELSE 'Low'
    END;
```

### Output

| Salary_Level | Total_Employees |
|--------------|----------------:|
| High | 2 |
| Medium | 1 |
| Low | 2 |

---

# Why COUNT(*)?

`COUNT(*)` counts the number of rows in each group.

Example:

High Salary Employees = 2

Medium Salary Employees = 1

Low Salary Employees = 2

---

# Why GROUP BY?

`GROUP BY` groups similar records together.

Without `GROUP BY`:

- SQL returns one total count.

With `GROUP BY`:

- SQL returns separate counts for each category.

---

# CASE WHEN + SUM()

## Purpose

Calculate the total value for each category.

### Example

```sql
SELECT
    CASE
        WHEN Salary >= 70000 THEN 'High'
        WHEN Salary >= 50000 THEN 'Medium'
        ELSE 'Low'
    END AS Salary_Level,
    SUM(Salary) AS Total_Salary
FROM Employees
GROUP BY
    CASE
        WHEN Salary >= 70000 THEN 'High'
        WHEN Salary >= 50000 THEN 'Medium'
        ELSE 'Low'
    END;
```

### Output

| Salary_Level | Total_Salary |
|--------------|-------------:|
| High | 157000 |
| Medium | 65000 |
| Low | 75000 |

---

# CASE WHEN + AVG()

## Purpose

Find the average value for each category.

### Example

```sql
SELECT
    CASE
        WHEN Salary >= 70000 THEN 'High'
        WHEN Salary >= 50000 THEN 'Medium'
        ELSE 'Low'
    END AS Salary_Level,
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

# Difference Between COUNT(), SUM() and AVG()

| Function | Purpose |
|----------|---------|
| COUNT(*) | Counts the number of rows |
| SUM() | Adds all values |
| AVG() | Calculates the average value |

---

# CASE WHEN with ORDER BY

Normally SQL sorts text alphabetically.

Example:

```text
High
Low
Medium
```

This is not always useful in business reports.

Instead, assign priorities.

```sql
SELECT Name,
       Salary,
       CASE
           WHEN Salary >= 70000 THEN 'High'
           WHEN Salary >= 50000 THEN 'Medium'
           ELSE 'Low'
       END AS Salary_Level
FROM Employees
ORDER BY
CASE
    WHEN Salary >= 70000 THEN 1
    WHEN Salary >= 50000 THEN 2
    ELSE 3
END;
```

### Output

High

↓

Medium

↓

Low

---

# Why Use Numbers in ORDER BY?

SQL sorts numbers correctly.

Assign:

High → 1

Medium → 2

Low → 3

This creates business priority instead of alphabetical order.

---

# Real Business Use Cases

## Human Resources

- High Salary Employees
- Medium Salary Employees
- Low Salary Employees

---

## Banking

- Premium Customers
- Gold Customers
- Silver Customers

---

## E-commerce

- Platinum Customers
- Gold Customers
- Silver Customers
- Bronze Customers

---

## Amazon

Sort orders by priority.

Critical Orders

↓

Urgent Orders

↓

Normal Orders

---

# Business Thinking

Managers do not want to read thousands of records.

They prefer summary reports like:

- Number of employees
- Total salary
- Average salary
- Customer categories
- Order priorities

This helps them make faster business decisions.

---

# Interview Questions

## 1. Why do we use COUNT(*)?

To count the total number of rows in each group.

---

## 2. Why is GROUP BY required?

To group similar records before applying aggregate functions.

---

## 3. Difference between COUNT(), SUM() and AVG()?

COUNT()

Counts rows.

SUM()

Adds values.

AVG()

Calculates the average.

---

## 4. Why use CASE WHEN with ORDER BY?

To create custom business priority instead of alphabetical sorting.

---

## 5. Why do companies use summarized reports?

- Easier to understand.
- Saves time.
- Better dashboards.
- Faster decision-making.
- Maintains privacy.
- Improves business analysis.

---

# Common Mistakes

❌ Using ORDER BY Salary_Level

This sorts alphabetically.

✅ Use

```sql
ORDER BY
CASE
WHEN Salary_Level='High' THEN 1
WHEN Salary_Level='Medium' THEN 2
ELSE 3
END;
```

---

# Memory Tips

## Aggregate Functions

COUNT → Count rows

SUM → Add values

AVG → Average

---

## ORDER BY Priority

1 = Highest Priority

2 = Medium Priority

3 = Lowest Priority

---

# Key Takeaways

- `COUNT()` counts records.
- `SUM()` calculates total values.
- `AVG()` calculates average values.
- `GROUP BY` creates separate groups.
- `CASE WHEN` can classify data.
- `CASE WHEN` with `ORDER BY` creates custom business sorting.
- Companies use summary reports for faster analysis and decision-making.
