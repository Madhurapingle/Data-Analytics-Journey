# Day 6 - SQL JOINS, Aliases & String Functions

##  Objective

- Understand SQL JOINS and their types.
- Learn why JOINS are used in databases.
- Learn Aliases (`AS`) for better query readability.
- Learn basic String Functions used in SQL.

---

# SQL JOINS

## Why are JOINS Needed?

### Definition

JOINS are used to combine data from two or more related tables using a common column. They help retrieve complete information stored in separate tables.

### Why Companies Use JOINS

- Avoid duplicate data (Data Redundancy)
- Keep the database organized
- Make updates easier
- Improve data consistency
- Retrieve related information from multiple tables

---

# INNER JOIN

## Definition

INNER JOIN returns only the matching records from both tables based on a common column.

## Syntax

```sql
SELECT column1, column2
FROM Table1
INNER JOIN Table2
ON Table1.CommonColumn = Table2.CommonColumn;
```

## Example

```sql
SELECT Employees.Name,
       Departments.Department_Name
FROM Employees
INNER JOIN Departments
ON Employees.Dept_ID = Departments.Dept_ID;
```

## Output

| Name | Department_Name |
|------|-----------------|
| Rahul | IT |
| Priya | HR |

## Explanation

Only rows with matching values in both tables are displayed.

## Real-World Use

Used to generate reports showing employees with their departments.

## Key Points

- Returns only matching records.
- Unmatched records are excluded.

---

# LEFT JOIN

## Definition

LEFT JOIN returns all records from the left table and the matching records from the right table. If no match exists, NULL is displayed.

## Syntax

```sql
SELECT column1, column2
FROM Table1
LEFT JOIN Table2
ON Table1.CommonColumn = Table2.CommonColumn;
```

## Example

```sql
SELECT Employees.Name,
       Departments.Department_Name
FROM Employees
LEFT JOIN Departments
ON Employees.Dept_ID = Departments.Dept_ID;
```

## Output

| Name | Department_Name |
|------|-----------------|
| Rahul | IT |
| Priya | HR |
| Riya | NULL |

## Explanation

All records from the left table are displayed even if there is no matching record in the right table.

## Key Points

- Returns all rows from the left table.
- Displays NULL for unmatched records.

---

# RIGHT JOIN

## Definition

RIGHT JOIN returns all records from the right table and the matching records from the left table. If no match exists, NULL is displayed.

## Syntax

```sql
SELECT column1, column2
FROM Table1
RIGHT JOIN Table2
ON Table1.CommonColumn = Table2.CommonColumn;
```

## Example

```sql
SELECT Employees.Name,
       Departments.Department_Name
FROM Employees
RIGHT JOIN Departments
ON Employees.Dept_ID = Departments.Dept_ID;
```

## Output

| Name | Department_Name |
|------|-----------------|
| Rahul | IT |
| Priya | HR |
| NULL | Finance |

## Explanation

All records from the right table are displayed even if there is no matching record in the left table.

## Key Points

- Returns all rows from the right table.
- Displays NULL for unmatched records.

---

# FULL OUTER JOIN (Concept)

## Definition

FULL OUTER JOIN returns all matching and non-matching records from both tables. If no match exists, NULL is displayed.

> **Note:** MySQL does not support FULL OUTER JOIN directly. It can be achieved using `LEFT JOIN`, `RIGHT JOIN`, and `UNION`.

---

# Comparison of JOINS

| JOIN Type | Returns |
|-----------|---------|
| INNER JOIN | Only matching records |
| LEFT JOIN | All rows from the left table + matching rows from the right table |
| RIGHT JOIN | All rows from the right table + matching rows from the left table |
| FULL OUTER JOIN | All rows from both tables |

---

# SQL Aliases (AS)

## Definition

An Alias is a temporary name given to a column or table to improve readability.

## Why is Alias Needed?

- Makes output easier to read.
- Makes long queries shorter.
- Improves query readability.

## Column Alias

```sql
SELECT AVG(Salary) AS Average_Salary
FROM Employees;
```

## Table Alias

```sql
SELECT E.Name,
       D.Department_Name
FROM Employees AS E
INNER JOIN Departments AS D
ON E.Dept_ID = D.Dept_ID;
```

## Key Points

- Temporary name only.
- Does not change the database.
- Makes SQL queries cleaner.

---

# SQL String Functions

## UPPER()

### Definition

Converts text into uppercase.

```sql
SELECT UPPER(Name)
FROM Employees;
```

**Example**

```
Rahul → RAHUL
```

---

## LOWER()

### Definition

Converts text into lowercase.

```sql
SELECT LOWER(Name)
FROM Employees;
```

**Example**

```
RAHUL → rahul
```

---

## LENGTH()

### Definition

Returns the number of characters in a string.

```sql
SELECT LENGTH(Name)
FROM Employees;
```

**Example**

```
Rahul → 5
```

---

## CONCAT()

### Definition

Combines two or more strings into one.

```sql
SELECT CONCAT('Employee: ', Name)
FROM Employees;
```

**Output**

```
Employee: Rahul
```

---

## TRIM()

### Definition

Removes leading and trailing spaces from a string.

```sql
SELECT TRIM(Name)
FROM Employees;
```

**Example**

```
"   Rahul   " → Rahul
```

---

# Real-World Uses

- Combine data from multiple tables using JOINS.
- Improve readability using Aliases.
- Standardize text using UPPER() and LOWER().
- Remove unwanted spaces using TRIM().
- Generate custom text using CONCAT().

---

# Interview Questions

### 1. What is a JOIN?

A JOIN combines data from two or more related tables using a common column.

### 2. Difference between INNER JOIN and LEFT JOIN?

- INNER JOIN returns only matching records.
- LEFT JOIN returns all records from the left table and matching records from the right table.

### 3. Why are JOINS needed?

They combine related data stored in separate tables while keeping the database organized.

### 4. What does NULL represent in a JOIN result?

NULL indicates that no matching record was found in the other table.

### 5. What is an Alias?

An Alias is a temporary name given to a table or column to improve readability.

---

# Mistakes I Made

- Initially used INNER JOIN instead of LEFT JOIN.
- Forgot to use single quotes in CONCAT().

---

# Key Takeaways

- JOINS combine data from related tables.
- INNER JOIN returns only matching records.
- LEFT JOIN returns all rows from the left table.
- RIGHT JOIN returns all rows from the right table.
- FULL OUTER JOIN returns all rows from both tables (concept).
- Aliases make SQL queries cleaner.
- String functions help manipulate and clean text.

---

# Business Scenario

A company stores employee details and department details in separate tables. To generate a report showing each employee along with their department, SQL JOINS are used. Aliases improve query readability, while String Functions help clean and format data before reporting.
