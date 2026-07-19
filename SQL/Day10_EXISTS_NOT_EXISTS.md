#  Day 10 - EXISTS & NOT EXISTS

### Date: 18 july 2026

##  Objective

- Understand `EXISTS`
- Understand `NOT EXISTS`
- Learn the difference between `IN`, `EXISTS`, and `NOT EXISTS`
- Learn real-world business use cases

---

# What is EXISTS?

## Definition

`EXISTS` checks whether a subquery returns **at least one row**.

It does **not** check the value.

It only checks whether a matching row exists.

---

# Syntax

```sql
SELECT *
FROM Table1
WHERE EXISTS
(
    SELECT *
    FROM Table2
    WHERE condition
);
```

---

# How EXISTS Works

1. SQL executes the subquery.
2. If the subquery returns **one or more rows**, `EXISTS` returns **TRUE**.
3. If no rows are returned, `EXISTS` returns **FALSE**.

---

# Example

## Employees

| Emp_ID | Name | Dept_ID |
|--------|------|---------|
| 1 | Rahul | 1 |
| 2 | Priya | 2 |
| 3 | Amit | 3 |

## Departments

| Dept_ID | Department_Name |
|---------|-----------------|
| 1 | IT |
| 2 | HR |

Query

```sql
SELECT *
FROM Employees E
WHERE EXISTS
(
    SELECT *
    FROM Departments D
    WHERE D.Dept_ID = E.Dept_ID
);
```

### Output

| Name |
|------|
| Rahul |
| Priya |

Amit is not displayed because there is no matching department.

---

# What is NOT EXISTS?

## Definition

`NOT EXISTS` checks whether the subquery returns **no matching rows**.

It returns **TRUE** when the subquery returns zero rows.

---

# Syntax

```sql
SELECT *
FROM Table1
WHERE NOT EXISTS
(
    SELECT *
    FROM Table2
    WHERE condition
);
```

---

# Example

```sql
SELECT *
FROM Employees E
WHERE NOT EXISTS
(
    SELECT *
    FROM Departments D
    WHERE D.Dept_ID = E.Dept_ID
);
```

### Output

| Name |
|------|
| Amit |

Rahul and Priya are not displayed because matching departments exist.

---

# Difference Between EXISTS and NOT EXISTS

| EXISTS | NOT EXISTS |
|---------|------------|
| Returns TRUE if matching rows exist | Returns TRUE if no matching rows exist |
| Used to find existing records | Used to find missing records |

---

# Difference Between IN and EXISTS

| IN | EXISTS |
|----|---------|
| Checks values | Checks rows |
| Compares a value with a list | Checks whether the subquery returns any rows |
| Best when comparing a list of values | Best when checking for related records |

---

# Real-World Business Examples

## EXISTS

Find employees whose department exists.

```sql
SELECT *
FROM Employees E
WHERE EXISTS
(
    SELECT *
    FROM Departments D
    WHERE D.Dept_ID = E.Dept_ID
);
```

---

## NOT EXISTS

Find customers who have never placed an order.

```sql
SELECT *
FROM Customers C
WHERE NOT EXISTS
(
    SELECT *
    FROM Orders O
    WHERE O.Customer_ID = C.Customer_ID
);
```

---

## Other Business Uses of NOT EXISTS

- Customers who never placed an order.
- Products that were never sold.
- Employees without departments.
- Students who never submitted assignments.

---

# Interview Questions

### 1. What does EXISTS check?

`EXISTS` checks whether a subquery returns at least one row.

---

### 2. Does EXISTS check values?

No.

It checks whether matching rows exist.

---

### 3. What happens if the subquery returns zero rows?

`EXISTS` returns FALSE.

---

### 4. What does NOT EXISTS check?

It checks whether no matching rows exist.

---

### 5. When does NOT EXISTS return TRUE?

When the subquery returns zero rows.

---

### 6. Difference between EXISTS and IN?

- `IN` checks values.
- `EXISTS` checks whether matching rows exist.

---

### 7. Difference between EXISTS and NOT EXISTS?

- `EXISTS` returns rows with matches.
- `NOT EXISTS` returns rows without matches.

---

# Memory Trick

```text
IN
↓

Checks VALUES

-------------------------

EXISTS
↓

Matching row exists?

YES → TRUE

-------------------------

NOT EXISTS
↓

No matching row exists?

YES → TRUE
```

---

# Key Takeaways

- `EXISTS` checks for matching rows.
- `NOT EXISTS` checks for missing rows.
- `IN` checks values, while `EXISTS` checks rows.
- `EXISTS` returns TRUE if at least one row exists.
- `NOT EXISTS` returns TRUE when no matching rows exist.
- `EXISTS` and `NOT EXISTS` are commonly used in business reports and SQL interviews.

---

# Business Thinking

Instead of checking values manually, companies use `EXISTS` and `NOT EXISTS` to quickly identify:

- Existing records
- Missing records
- Customers with or without orders
- Employees with or without departments

This makes reports more efficient and helps businesses make informed decisions.
