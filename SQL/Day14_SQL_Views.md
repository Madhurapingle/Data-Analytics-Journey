# Day 14 - SQL Views

### Date:23 july 2026

##  Objective

- Understand what a View is.
- Learn why companies use Views.
- Create and use Views.
- Understand whether Views store data.
- Learn when a View can be updated.
- Prepare for SQL interview questions.

---

# What is a View?

A View is a **virtual table** created from the result of a SQL query.

It does **not** store data itself.

It only displays data from the original table.

---

# Why do Companies use Views?

Companies use Views because they provide:

- Security
- Privacy
- Simplicity
- Reusability
- Easy Reporting
- Show only required data
- Prevent unnecessary exposure of sensitive information

---

# Example

## Original Table

| Name | Salary | Aadhaar | Phone |
|------|--------|----------|--------|
| Rahul | 70000 | XXXXX | XXXXX |
| Amit | 50000 | XXXXX | XXXXX |

---

## View

| Name | Salary |
|------|--------|
| Rahul | 70000 |
| Amit | 50000 |

Only the required columns are displayed.

---

# Syntax

## Create a View

```sql
CREATE VIEW Employee_Details AS
SELECT Name, Department
FROM Employees;
```

---

## Display Data from View

```sql
SELECT *
FROM Employee_Details;
```

---

# Does a View Store Data?

❌ No.

A View is a virtual table.

The actual data remains in the original table.

Think of a View as a **saved SQL query** that displays data whenever it is used.

---

# Updating a View

Simple Views can often be updated.

Example:

```sql
UPDATE Employee_Salary
SET Salary = 80000
WHERE Name = 'Rahul';
```

The data is updated in the **original table**, not inside the View.

---

# When Can't a View be Updated?

Complex Views are generally not updatable.

Examples include Views using:

- JOIN
- GROUP BY
- Aggregate Functions (COUNT, SUM, AVG)
- DISTINCT

These make it difficult for SQL to determine how to update the original table.

---

# Advantages of Views

- Improve Security
- Protect Privacy
- Hide Sensitive Columns
- Simplify Complex Queries
- Reuse Frequently Used Queries
- Reduce Errors
- Useful for Dashboards and Reports

---

# Real-Life Examples

## HR View

Displays:

- Employee Name
- Department
- Salary

---

## Finance View

Displays:

- Employee Name
- Salary
- Bank Details

---

## Marketing View

Displays:

- Employee Name

Only the required information is shown to each department.

---

# Business Benefits

Views help companies:

- Prevent misuse of confidential data
- Reduce security risks
- Show only required information
- Make reports simple
- Improve productivity
- Maintain privacy
- Provide role-based access to data

---

# Table vs View

| Table | View |
|--------|------|
| Stores actual data | Does not store data |
| Physical object | Virtual object |
| Contains records | Displays records from a query |
| Data is stored permanently | Data is fetched from the original table |

---

# Interview Questions

## 1. What is a View?

A View is a virtual table created from the result of a SQL query.

---

## 2. Does a View store data?

No.

A View does not store data.

It displays data from the original table.

---

## 3. Why do companies use Views?

- Security
- Privacy
- Simplicity
- Role-based access
- Reporting
- Reusability

---

## 4. Can a View be updated?

Yes, simple Views can often be updated.

However, complex Views containing JOIN, GROUP BY, aggregate functions, or DISTINCT are generally not updatable.

---

## 5. Why not give employees access to original tables?

Because it may lead to:

- Data misuse
- Security breaches
- Privacy issues
- Exposure of sensitive information

Views provide only the data required for a specific role.

---

# Memory Tricks

## View

➡ Virtual Table

---

## Table

➡ Stores Data

---

## View

➡ Displays Data

---

## Company Logic

Original Table

↓

View

↓

Employee

Only required information reaches the employee.

---

# Key Takeaways

- A View is a virtual table.
- Views do not store data.
- Views improve security and privacy.
- Views simplify reporting.
- Different departments can have different Views.
- Simple Views can be updated.
- Complex Views are generally not updatable.
- Companies use Views to provide role-based access to data.
