#  Day 7 - SQL Logical Operators & LIKE

## Date:15 july 2026
##  Objective

- Learn SQL Logical Operators.
- Understand how to filter data using multiple conditions.
- Learn pattern matching using the `LIKE` operator.
- Understand the use of Wildcards (`%` and `_`).

---

# SQL Logical Operators

Logical Operators are used to combine or modify conditions in the `WHERE` clause.

---

# AND Operator

## Definition

The `AND` operator returns rows only when **all conditions are TRUE**.

## Syntax

```sql
SELECT *
FROM Employees
WHERE condition1 AND condition2;
```

## Example

```sql
SELECT *
FROM Employees
WHERE Department = 'IT'
AND Salary > 50000;
```

## Explanation

Only employees who belong to the IT department **and** have a salary greater than ₹50,000 are displayed.

## Real-World Use

Find employees from a specific department who meet a salary requirement.

---

# OR Operator

## Definition

The `OR` operator returns rows if **at least one condition is TRUE**.

## Syntax

```sql
SELECT *
FROM Employees
WHERE condition1 OR condition2;
```

## Example

```sql
SELECT *
FROM Employees
WHERE Department = 'IT'
OR Department = 'HR';
```

## Explanation

Employees belonging to either the IT department or the HR department are displayed.

## Real-World Use

Find employees working in multiple departments.

---

# NOT Operator

## Definition

The `NOT` operator reverses the condition.

## Syntax

```sql
SELECT *
FROM Employees
WHERE NOT Department = 'HR';
```

## Example

```sql
SELECT *
FROM Employees
WHERE NOT Department = 'HR';
```

## Alternative Syntax

```sql
SELECT *
FROM Employees
WHERE Department <> 'HR';
```

## Explanation

Displays employees who are **not** in the HR department.

---

# IN Operator

## Definition

The `IN` operator checks whether a value exists in a given list.

## Why Use IN?

Instead of writing multiple `OR` conditions, `IN` makes the query shorter and easier to read.

## Syntax

```sql
SELECT *
FROM Employees
WHERE Department IN ('IT', 'HR', 'Finance');
```

## Example

```sql
SELECT *
FROM Employees
WHERE Department IN ('IT', 'HR');
```

## Real-World Use

Find employees belonging to multiple departments.

---

# BETWEEN Operator

## Definition

The `BETWEEN` operator selects values within a specified range.

> **Note:** `BETWEEN` is **inclusive**, meaning it includes both the starting and ending values.

## Syntax

```sql
SELECT *
FROM Employees
WHERE Salary BETWEEN 45000 AND 70000;
```

## Equivalent Query

```sql
SELECT *
FROM Employees
WHERE Salary >= 45000
AND Salary <= 70000;
```

## Real-World Use

Find employees whose salaries fall within a given range.

---

# LIKE Operator

## Definition

The `LIKE` operator is used to search for a specific pattern in a text column.

## Syntax

```sql
SELECT *
FROM Employees
WHERE Name LIKE 'A%';
```

## Real-World Use

Search employees by name, email, city, or any text pattern.

---

# Wildcards

## `%` Wildcard

Represents **zero, one, or many characters**.

### Starts With

```sql
SELECT *
FROM Employees
WHERE Name LIKE 'A%';
```

### Ends With

```sql
SELECT *
FROM Employees
WHERE Name LIKE '%n';
```

### Contains

```sql
SELECT *
FROM Employees
WHERE Name LIKE '%ar%';
```

---

## `_` Wildcard

Represents **exactly one character**.

### Example

```sql
SELECT *
FROM Employees
WHERE Name LIKE 'R__';
```

This query returns names having exactly **three characters** and starting with **R**, such as:

- Ram
- Raj

---

# Comparison Table

| Operator | Purpose |
|----------|---------|
| AND | All conditions must be TRUE |
| OR | At least one condition must be TRUE |
| NOT | Reverses the condition |
| IN | Checks whether a value exists in a list |
| BETWEEN | Checks values within a range |
| LIKE | Searches for patterns in text |

---

# Wildcard Summary

| Pattern | Meaning |
|---------|---------|
| `A%` | Starts with A |
| `%A` | Ends with A |
| `%A%` | Contains A |
| `R__` | Starts with R and has exactly 3 characters |
| `_a%` | Second character is 'a' |

---

# Real-World Examples

### Find employees from IT and HR

```sql
SELECT *
FROM Employees
WHERE Department IN ('IT', 'HR');
```

### Find employees earning between ₹45,000 and ₹70,000

```sql
SELECT *
FROM Employees
WHERE Salary BETWEEN 45000 AND 70000;
```

### Find employees whose names start with M

```sql
SELECT *
FROM Employees
WHERE Name LIKE 'M%';
```

### Find employees whose names end with n

```sql
SELECT *
FROM Employees
WHERE Name LIKE '%n';
```

---

# Interview Questions

### 1. What is the difference between AND and OR?

- **AND** returns rows only if all conditions are true.
- **OR** returns rows if at least one condition is true.

---

### 2. Why is IN preferred over multiple OR conditions?

`IN` makes the query shorter, cleaner, and easier to read.

---

### 3. Is BETWEEN inclusive?

Yes. It includes both the starting and ending values.

---

### 4. What is the purpose of the LIKE operator?

It is used to search for patterns in text data.

---

### 5. Difference between `%` and `_`?

- `%` represents zero, one, or many characters.
- `_` represents exactly one character.

---

# Mistakes I Made

- Initially wrote `'n%'` instead of `'%n'` while finding names ending with **n**.
- Confused **Starts With** and **Ends With** pattern matching.

---

# Key Takeaways

- Use **AND** when all conditions must be true.
- Use **OR** when any one condition can be true.
- Use **NOT** to reverse a condition.
- Use **IN** instead of multiple OR conditions.
- Use **BETWEEN** to filter values within a range.
- Use **LIKE** for pattern matching.
- `%` represents many characters.
- `_` represents exactly one character.

---

# Business Scenario

A company's HR department wants to generate reports such as:

- Employees from multiple departments.
- Employees within a salary range.
- Employees whose names start with a particular letter.

Logical Operators (`AND`, `OR`, `NOT`), `IN`, `BETWEEN`, and `LIKE` help filter data efficiently and generate accurate business reports.
