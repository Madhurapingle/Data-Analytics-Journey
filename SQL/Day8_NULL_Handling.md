#  Day 8 - NULL Handling in SQL

### DATE:16 JULY 2026

##  Objective

- Understand the meaning of NULL.
- Learn how to find NULL values.
- Learn how to replace NULL values.
- Understand the difference between `IFNULL()` and `COALESCE()`.

---

# What is NULL?

## Definition

`NULL` represents a missing, unknown, or unavailable value in a database.

> **Note:** `NULL` is NOT the same as:
>
> - `0` (Zero)
> - `''` (Empty String)
> - `FALSE`

It simply means **no value has been stored**.

---

# Why is NULL Important?

NULL values can affect:

- Reports
- Calculations
- Data Analysis
- Predictions
- Business Decisions

Before analyzing data, a Data Analyst should identify and handle NULL values properly.

---

# IS NULL

## Definition

`IS NULL` is used to find rows where a column contains NULL values.

## Syntax

```sql
SELECT *
FROM Employees
WHERE Manager IS NULL;
```

## Example

```sql
SELECT *
FROM Employees
WHERE Phone IS NULL;
```

## Use Case

Find employees or customers whose information is missing.

---

# IS NOT NULL

## Definition

`IS NOT NULL` is used to find rows where a value exists.

## Syntax

```sql
SELECT *
FROM Employees
WHERE Manager IS NOT NULL;
```

## Example

```sql
SELECT *
FROM Employees
WHERE Email IS NOT NULL;
```

## Use Case

Find employees or customers whose information is available.

---

# Common Mistake

 Incorrect

```sql
SELECT *
FROM Employees
WHERE Manager = NULL;
```

Correct

```sql
SELECT *
FROM Employees
WHERE Manager IS NULL;
```

### Why?

`NULL` represents an unknown value, so SQL cannot compare it using the `=` operator. We must use `IS NULL` or `IS NOT NULL`.

---

# IFNULL()

## Definition

`IFNULL()` replaces a NULL value with another value.

## Syntax

```sql
IFNULL(column_name, replacement_value)
```

## Example 1

```sql
SELECT Name,
       IFNULL(Salary, 0) AS Salary
FROM Employees;
```

## Example 2

```sql
SELECT Name,
       IFNULL(Phone, 'Not Available') AS Phone
FROM Employees;
```

## Use Case

Replace missing values in reports with meaningful values like:

- 0
- Not Available
- Unknown

---

# COALESCE()

## Definition

`COALESCE()` returns the first non-NULL value from a list of expressions.

## Syntax

```sql
COALESCE(value1, value2, value3, ...)
```

## Example

```sql
SELECT Name,
       COALESCE(Mobile, Office_Phone, Home_Phone) AS Contact_Number
FROM Employees;
```

## Explanation

SQL checks each value from left to right and returns the first value that is not NULL.

---

# Difference Between IFNULL() and COALESCE()

| IFNULL() | COALESCE() |
|-----------|------------|
| Accepts only 2 arguments | Accepts 2 or more arguments |
| Replaces NULL with one replacement value | Returns the first non-NULL value |
| Simpler function | More flexible |

---

# Real-World Examples

## Find employees without managers

```sql
SELECT *
FROM Employees
WHERE Manager IS NULL;
```

---

## Find employees with managers

```sql
SELECT *
FROM Employees
WHERE Manager IS NOT NULL;
```

---

## Replace NULL Salary with 0

```sql
SELECT Name,
       IFNULL(Salary, 0) AS Salary
FROM Employees;
```

---

## Display the first available contact number

```sql
SELECT Name,
       COALESCE(Mobile, Office_Phone, Home_Phone) AS Contact_Number
FROM Employees;
```

---

# Interview Questions

### 1. What does NULL represent?

NULL represents a missing, unknown, or unavailable value.

---

### 2. Is NULL the same as 0?

No. NULL means no value exists, whereas 0 is an actual numeric value.

---

### 3. Why can't we use `= NULL`?

Because NULL is an unknown value. SQL uses `IS NULL` and `IS NOT NULL` to check for NULL values.

---

### 4. What is the purpose of IFNULL()?

It replaces NULL values with a specified replacement value.

---

### 5. What is the purpose of COALESCE()?

It returns the first non-NULL value from a list of expressions.

---

### 6. Difference between IFNULL() and COALESCE()?

- `IFNULL()` replaces NULL using one replacement value.
- `COALESCE()` checks multiple values and returns the first non-NULL value.

---

# Business Scenario

A company's database contains missing information such as:

- Customer Phone Numbers
- Employee Managers
- Product Prices

Before preparing reports or performing analysis, a Data Analyst should identify and handle NULL values to ensure accurate insights and better business decisions.

---

# Key Takeaways

- `NULL` means no value is stored.
- `IS NULL` finds missing values.
- `IS NOT NULL` finds existing values.
- Never use `= NULL`.
- `IFNULL()` replaces NULL with a specified value.
- `COALESCE()` returns the first non-NULL value from multiple options.
- Handling NULL values is an important part of data cleaning.
