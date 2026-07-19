#  Day 11 - CASE WHEN

### Date:19 july 2026

##  Objective

- Understand `CASE WHEN`
- Learn how to apply multiple conditions
- Categorize data using SQL
- Create business-friendly reports
- Prepare for SQL interview questions

---

# What is CASE WHEN?

## Definition

`CASE WHEN` is used to apply multiple conditions and return different values based on those conditions.

It works like the **IF - ELSE IF - ELSE** statement in programming.

---

# Syntax

```sql
SELECT column_name,
       CASE
           WHEN condition1 THEN result1
           WHEN condition2 THEN result2
           ELSE result3
       END AS alias_name
FROM table_name;
```

---

# How CASE WHEN Works

SQL checks the conditions **from top to bottom**.

- If the first condition is TRUE, SQL returns that result.
- SQL stops checking the remaining conditions.
- If none of the conditions are TRUE, the `ELSE` value is returned.

---

# Example 1 - Salary Category

```sql
SELECT Name,
       Salary,
       CASE
           WHEN Salary >= 70000 THEN 'High'
           WHEN Salary >= 50000 THEN 'Medium'
           ELSE 'Low'
       END AS Salary_Level
FROM Employees;
```

### Output

| Name | Salary | Salary_Level |
|------|--------|--------------|
| Rahul | 85000 | High |
| Priya | 65000 | Medium |
| Amit | 45000 | Low |

---

# Example 2 - Student Result

```sql
SELECT Name,
       Marks,
       CASE
           WHEN Marks >= 75 THEN 'Distinction'
           WHEN Marks >= 60 THEN 'First Class'
           WHEN Marks >= 40 THEN 'Pass'
           ELSE 'Fail'
       END AS Result
FROM Students;
```

---

# Example 3 - Department Category

```sql
SELECT Name,
       Department,
       CASE
           WHEN Department = 'IT' THEN 'Technical'
           WHEN Department = 'HR' THEN 'Management'
           WHEN Department = 'Finance' THEN 'Accounts'
           ELSE 'Other'
       END AS Department_Type
FROM Employees;
```

---

# Why is Order Important?

SQL checks conditions from **top to bottom**.

As soon as one condition becomes TRUE:

- SQL returns the result.
- SQL ignores all remaining conditions.

Always write conditions in the correct logical order.

---

# Business Use Cases

## Human Resources

Categorize employees as:

- High Salary
- Medium Salary
- Low Salary

instead of displaying exact salaries.

---

## Banking

Categorize customers as:

- Premium
- Gold
- Silver
- Regular

based on account balance.

---

## E-commerce

Categorize customers based on yearly purchases.

Example:

- Gold Customer
- Silver Customer
- Bronze Customer

---

## College

Categorize students as:

- Distinction
- First Class
- Pass
- Fail

based on marks.

---

# Advantages of CASE WHEN

- Makes reports easier to understand.
- Helps categorize data.
- Protects confidential information.
- Useful in dashboards and business reports.
- Improves data analysis.

---

# Interview Questions

## 1. What is CASE WHEN?

`CASE WHEN` is used to apply multiple conditions and return different values based on those conditions.

---

## 2. Which programming concept is similar to CASE WHEN?

**IF → ELSE IF → ELSE**

---

## 3. Why is the order of WHEN conditions important?

SQL checks conditions from top to bottom.

Once a condition is TRUE, SQL stops checking the remaining conditions.

---

## 4. What happens if no condition is TRUE?

The value written in the `ELSE` block is returned.

---

## 5. Why do companies use CASE WHEN?

Companies use `CASE WHEN` to categorize data into meaningful groups, making reports easier to understand, protecting sensitive information, and supporting better business decisions.

---

# Common Mistakes

❌ Checking the wrong column.

Example:

```sql
CASE
WHEN Salary >= 70000 THEN 'Technical'
```

Incorrect because "Technical" depends on the **Department**, not the **Salary**.

✅ Correct

```sql
CASE
WHEN Department = 'IT' THEN 'Technical'
```

---

# Memory Trick

```text
CASE
↓

WHEN Condition

↓

THEN Result

↓

ELSE Default Result

↓

END
```

Think of it as:

```text
IF
↓

ELSE IF
↓

ELSE
```

---

# Key Takeaways

- `CASE WHEN` works like an IF-ELSE statement.
- SQL checks conditions from top to bottom.
- SQL stops after the first TRUE condition.
- `ELSE` is executed if no condition matches.
- `CASE WHEN` is widely used in reports, dashboards, and business analytics.
- It helps categorize data into meaningful groups.

---

# Business Thinking

Instead of showing raw numbers, companies often use `CASE WHEN` to group data into categories.

Examples:

- High / Medium / Low Salary
- Gold / Silver / Bronze Customers
- Distinction / Pass / Fail Students

This makes reports easier to read, protects sensitive information, and helps management make faster decisions.
