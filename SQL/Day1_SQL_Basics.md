#  Day 1 - SQL Basics

##  Objective

- Understand the basic structure of an SQL query.
- Learn how to retrieve data from a table.
- Filter, sort, and limit query results.

---

# SELECT Statement

## Definition

The `SELECT` statement is used to retrieve data from one or more columns in a table.

## Syntax

```sql
SELECT column_name
FROM table_name;
```

## Example

```sql
SELECT Name, Salary
FROM Employees;
```

## Select All Columns

```sql
SELECT *
FROM Employees;
```

## Explanation

- `SELECT` specifies the columns you want to retrieve.
- `*` selects all columns from the table.

---

# FROM Clause

## Definition

The `FROM` clause specifies the table from which the data will be retrieved.

## Syntax

```sql
SELECT column_name
FROM table_name;
```

## Example

```sql
SELECT Name
FROM Employees;
```

## Explanation

Without the `FROM` clause, SQL does not know which table to read.

---

# WHERE Clause

## Definition

The `WHERE` clause filters rows based on a specified condition.

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

## Example

```sql
SELECT *
FROM Employees
WHERE Department = 'IT';
```

## Another Example

```sql
SELECT Name, Salary
FROM Employees
WHERE Salary > 50000;
```

## Common Comparison Operators

| Operator | Meaning |
|----------|---------|
| = | Equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |
| <> / != | Not equal to |

---

# ORDER BY Clause

## Definition

The `ORDER BY` clause sorts the result in ascending or descending order.

## Syntax

```sql
SELECT column_name
FROM table_name
ORDER BY column_name ASC;
```

## Ascending Order (Default)

```sql
SELECT *
FROM Employees
ORDER BY Salary;
```

or

```sql
SELECT *
FROM Employees
ORDER BY Salary ASC;
```

## Descending Order

```sql
SELECT *
FROM Employees
ORDER BY Salary DESC;
```

## Explanation

- `ASC` → Ascending order (smallest to largest / A to Z)
- `DESC` → Descending order (largest to smallest / Z to A)

---

# LIMIT Clause

## Definition

The `LIMIT` clause restricts the number of rows returned.

## Syntax

```sql
SELECT column_name
FROM table_name
LIMIT number;
```

## Example

```sql
SELECT *
FROM Employees
LIMIT 5;
```

## Explanation

Only the first 5 rows are displayed.

---

# Query Execution Order

Although we write SQL like this:

```sql
SELECT *
FROM Employees
WHERE Department = 'IT'
ORDER BY Salary DESC
LIMIT 3;
```

SQL processes it in this order:

1. FROM
2. WHERE
3. SELECT
4. ORDER BY
5. LIMIT

---

# Real-World Examples

### Display all employees

```sql
SELECT *
FROM Employees;
```

### Display only employee names

```sql
SELECT Name
FROM Employees;
```

### Display IT employees

```sql
SELECT *
FROM Employees
WHERE Department = 'IT';
```

### Display employees sorted by salary

```sql
SELECT *
FROM Employees
ORDER BY Salary DESC;
```

### Display top 5 employees

```sql
SELECT *
FROM Employees
LIMIT 5;
```

---

# Interview Questions

### 1. What is the purpose of the SELECT statement?

It is used to retrieve data from a database table.

---

### 2. What is the difference between `SELECT *` and `SELECT Name`?

- `SELECT *` returns all columns.
- `SELECT Name` returns only the Name column.

---

### 3. Why is the WHERE clause used?

It filters rows based on a specified condition.

---

### 4. What is the default sorting order in ORDER BY?

Ascending (`ASC`).

---

### 5. What is the purpose of LIMIT?

It restricts the number of rows returned by a query.

---

# Key Takeaways

- `SELECT` retrieves data.
- `FROM` specifies the table.
- `WHERE` filters rows.
- `ORDER BY` sorts data.
- `LIMIT` restricts the number of rows returned.

---

# Business Scenario

A company's HR manager wants to:

- View all employees.
- Find only employees from the IT department.
- Sort employees by highest salary.
- Display only the top 5 highest-paid employees.

These tasks are performed using `SELECT`, `FROM`, `WHERE`, `ORDER BY`, and `LIMIT`.
