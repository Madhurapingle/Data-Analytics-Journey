# Day 3 - MySQL Workbench & SQL Execution

**Date:** 11 July 2026

##  Objective

Learn how to create a database, create tables, insert records, and execute SQL queries in MySQL Workbench.

---

# 1. What is a Database?

### Definition

A database is an organized collection of data that allows users to store, retrieve, update, and manage information efficiently.

### Real World Example

A college stores student records in a database.

---

# 2. What is a Table?

### Definition

A table stores data in the form of rows and columns.

### Example

Employees Table

| Emp_ID | Name | Department | Salary |
|--------|------|------------|--------|
|101     |Rahul |     IT     |55000|

---

# 3. What is a Row?

A row represents one complete record.

Example:

101 | Rahul | IT | 55000

---

# 4. What is a Column?

A column represents one attribute of the data.

Examples:

- Name
- Salary
- Department

---

# 5. Data Types

## INT

Purpose:
Stores whole numbers.

Example:

Salary = 50000

---

## VARCHAR

Purpose:
Stores text values.

Example:

Name = Rahul

Department = IT

---

# 6. PRIMARY KEY

### Definition

A Primary Key uniquely identifies every record in a table.

Example:

Emp_ID

No two employees can have the same Emp_ID.

---

# 7. SQL Commands Learned Today

## Create Database

```sql
CREATE DATABASE madhuradb;
```

---

## Select Database

```sql
USE madhuradb;
```

---

## Create Table

```sql
CREATE TABLE Employees(
Emp_ID INT PRIMARY KEY,
Name VARCHAR(50),
Department VARCHAR(30),
Salary INT
);
```

---

## Insert Records

```sql
INSERT INTO Employees VALUES
(101,'Rahul','IT',55000);
```

---

## Display Table

```sql
SELECT * FROM Employees;
```

---

# 8. Queries Executed

- COUNT()
- SUM()
- AVG()
- MIN()
- MAX()
- WHERE
- Salary > 60000
- Department = 'IT'

---

# 9. Errors I Faced

Example:

Error:
Unknown column 'Departmrnt'

Reason:
Spelling mistake.

Solution:
Corrected it to Department.



---

# 10. What I Learned Today

- How to create a database.
- How to create a table.
- How to insert data.
- How to execute SQL queries.
- Importance of PRIMARY KEY.

---

# 11. Real World Use

A company stores employee information in a database.

A Data Analyst writes SQL queries to analyze employee data, salaries, departments, and business reports.

---

# 12. Interview Questions

### What is the difference between a database and a table?

### What is a PRIMARY KEY?

### Difference between INT and VARCHAR?

### What does CREATE TABLE do?

---

# 13. Key Takeaways

- A database contains tables.
- A table contains rows and columns.
- PRIMARY KEY must be unique.
- INT stores numbers.
- VARCHAR stores text.
- SQL is used to manage and analyze data.
