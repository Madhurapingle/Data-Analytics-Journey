## DAY 4 - Clauses: GROUP BY and HAVING Clause

## DATE: 12 JULY 2026

## OBJECTIVE:
Learn how and where to use GROUP BY and HAVING Clause.

## GROUP BY CLAUSE:
The GROUP BY clause in SQL is used to group rows that have the same values in one or more columns
  
### SYNTAX:
```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name;
```

### Example:
SELECT Department, AVG(Salary)
FROM Employees
GROUP BY Department;

## HAVING Clause:
The HAVING clause is used to filter groups created by the GROUP BY clause based on a condition, usually involving aggregate functions.

### SYNTAX:
```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name
HAVING condition; 
```

### Example:
SELECT Department, AVG(Salary)
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 55000;

##  INTERVIEW QUESTIONS:
1. What is GROUP BY?
2. What is HAVING?
3. Difference between WHERE and HAVING?
4. Can HAVING be used without GROUP BY?

###  MISTTAKES MADE:

MISTAKES WERE VERY SILLY FEW SPEELING ERORRS .
AND I ADDED COMMA IN THE SALARY WHILE I WAS GIVEING THE CONDITION LIKE AVG(SALARY) >60,000 WHICH I SHOULD NOT REPEAT AND CHANGE IT TO AVG(SALARY)>60000
Lesson:
SQL numbers should not contain commas.

  ## Business Scenario

Imagine you are a Data Analyst at a company.

Problem:
The HR manager wants to know the average salary of each department.

Solution:

```sql
SELECT Department, AVG(Salary)
FROM Employees
GROUP BY Department;


### Explanation:
I used AVG() because the manager wanted the average salary.

I used GROUP BY because the calculation was required for each department.
