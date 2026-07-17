#  Day 9 - Subqueries in SQL
## Date:17  july 2026
##  Objective

- Understand what a Subquery is.
- Learn why Subqueries are used.
- Learn Single-Row and Multi-Row Subqueries.
- Understand when to use `=` and `IN` with Subqueries.

---

# What is a Subquery?

## Definition

A **Subquery** is a query written inside another SQL query.

It is also called an **Inner Query** or **Nested Query**.

The result of the subquery is used by the outer (main) query.

---

# Execution Order

SQL always executes the **Inner Query first**, then the **Outer Query**.

```text
Inner Query
     ↓
Returns Result
     ↓
Outer Query
```

---

# Why Do We Use Subqueries?

Subqueries help us:

- Perform complex queries in a single statement.
- Avoid writing multiple queries manually.
- Make queries dynamic (they automatically adapt when data changes).
- Reduce manual work and chances of errors.

---

# Single-Row Subquery

## Definition

A Single-Row Subquery returns **only one value**.

In this case, use the **`=`** operator or other single-value comparison operators (`>`, `<`, `>=`, `<=`).

## Example

Display employees earning more than the average salary.

```sql
SELECT *
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);
```

### How It Works

Step 1

```sql
SELECT AVG(Salary)
FROM Employees;
```

Suppose the result is:

```text
55000
```

Step 2

SQL automatically executes:

```sql
SELECT *
FROM Employees
WHERE Salary > 55000;
```

---

# Another Example

Display employees working in the HR department.

```sql
SELECT *
FROM Employees
WHERE Dept_ID =
(
    SELECT Dept_ID
    FROM Departments
    WHERE Department_Name = 'HR'
);
```

The subquery returns only one Dept_ID, so `=` is used.

---

# Multi-Row Subquery

## Definition

A Multi-Row Subquery returns **multiple values**.

In this case, use the **`IN`** operator.

---

## Example

Display employees working in the IT and HR departments.

```sql
SELECT *
FROM Employees
WHERE Dept_ID IN
(
    SELECT Dept_ID
    FROM Departments
    WHERE Department_Name IN ('IT', 'HR')
);
```

The subquery returns multiple department IDs, so `IN` is required.

---

# Another Example

Display employees working in the Finance and Marketing departments.

```sql
SELECT *
FROM Employees
WHERE Dept_ID IN
(
    SELECT Dept_ID
    FROM Departments
    WHERE Department_Name IN ('Finance', 'Marketing')
);
```

---

# Business Scenario

The company wants to display employees working in departments located in Mumbai.

```sql
SELECT *
FROM Employees
WHERE Dept_ID IN
(
    SELECT Dept_ID
    FROM Departments
    WHERE City = 'Mumbai'
);
```

The subquery finds all department IDs located in Mumbai.

The main query displays employees belonging to those departments.

---

# Difference Between Single-Row and Multi-Row Subqueries

| Single-Row Subquery | Multi-Row Subquery |
|----------------------|--------------------|
| Returns one value | Returns multiple values |
| Uses `=` or comparison operators | Uses `IN` |
| Example: AVG(), MAX(), MIN() | Example: Multiple Department IDs |

---

# Why Can't We Use AVG() Directly in WHERE?

❌ Incorrect

```sql
SELECT *
FROM Employees
WHERE Salary > AVG(Salary);
```

Aggregate functions cannot be used directly in the `WHERE` clause.

Instead, calculate the aggregate in a subquery.

✅ Correct

```sql
SELECT *
FROM Employees
WHERE Salary >
(
    SELECT AVG(Salary)
    FROM Employees
);
```

---

# Interview Questions

### 1. What is a Subquery?

A Subquery is a query written inside another SQL query.

---

### 2. Which query executes first?

The Inner Query executes first.

---

### 3. Why do we use Subqueries?

They simplify complex queries, reduce manual work, and automatically use updated data.

---

### 4. When should we use `=`?

Use `=` when the subquery returns only one value.

---

### 5. When should we use `IN`?

Use `IN` when the subquery returns multiple values.

---

### 6. Why can't we use AVG() directly in WHERE?

Because aggregate functions cannot be used directly in the `WHERE` clause.

---

### 7. Why do companies prefer Subqueries?

Subqueries automate calculations, reduce manual work, save time, and always use the latest data.

---

# Key Takeaways

- A Subquery is a query inside another query.
- The Inner Query executes first.
- Single-Row Subqueries return one value and use `=`.
- Multi-Row Subqueries return multiple values and use `IN`.
- Subqueries make SQL queries dynamic and efficient.
- They reduce manual work and are widely used in real-world databases.

---

# Business Thinking

Instead of:

1. Calculating a value manually.
2. Writing another query.

A Subquery performs everything in a single SQL statement.

This makes reports faster, more accurate, and automatically updated whenever the database changes.
