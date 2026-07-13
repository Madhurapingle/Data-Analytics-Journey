# Day 5 - INNER JOIN

## Date: 13  july 2026

## Objective

Understand why JOINS are needed and learn how to combine data from two related tables using INNER JOIN.

## What is INNER JOIN?

(Definition)

## Syntax

```sql
SELECT Employees.Name,
       Departments.Department_Name
FROM Employees
INNER JOIN Departments
ON Employees.Dept_ID = Departments.Dept_ID;
```

## Real World Use

Companies store related data in separate tables and use INNER JOIN to combine them when generating reports.

## Interview Questions
1. What is an INNER JOIN?
2. Why do we use JOINS?
3. What is the purpose of the ON clause?

## Business Scenario

A manager wants to see each employee along with the department they belong to. Since the information is stored in two different tables, an INNER JOIN is used.
