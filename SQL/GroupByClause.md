
# GROUP BY in MySQL

## Introduction
The `GROUP BY` clause in MySQL is used to group rows that have the same values in specified columns into summary rows, like "total sales per customer" or "average salary by department." It is typically used with aggregate functions such as `COUNT()`, `SUM()`, `AVG()`, `MAX()`, and `MIN()` to perform operations on grouped data.

---

## Syntax
```sql
SELECT column1, column2, aggregate_function(column3)
FROM table_name
WHERE condition
GROUP BY column1, column2
ORDER BY column1, column2;
```

- **`column1, column2`**: Columns used for grouping.
- **`aggregate_function`**: Operations like `SUM`, `COUNT`, `AVG`, etc.
- **`ORDER BY`**: Optional, to sort grouped results.

---

## Key Points
1. Columns in the `SELECT` clause must be part of the `GROUP BY` clause or used in aggregate functions.
2. If `GROUP BY` is omitted, all rows are considered as a single group.
3. `GROUP BY` is often used with `HAVING` to filter grouped data.

---

## Examples with Different Conditions

### 1. Basic Grouping
Group employees by their `JOB_ID` and count the number of employees in each job.
```sql
SELECT JOB_ID, COUNT(*) AS EmployeeCount
FROM emp_details
GROUP BY JOB_ID;
```
**Output:**
| JOB_ID    | EmployeeCount |
|-----------|---------------|
| DEV       | 5             |
| HR        | 3             |

---

### 2. Using Aggregate Functions
Calculate the total salary for each department.
```sql
SELECT DEPARTMENT_ID, SUM(SALARY) AS TotalSalary
FROM emp_details
GROUP BY DEPARTMENT_ID;
```
**Output:**
| DEPARTMENT_ID | TotalSalary |
|---------------|-------------|
| 10            | 50000       |
| 20            | 75000       |

---

### 3. Grouping with Multiple Columns
Group employees by department and job, then find the average salary for each group.
```sql
SELECT DEPARTMENT_ID, JOB_ID, AVG(SALARY) AS AvgSalary
FROM emp_details
GROUP BY DEPARTMENT_ID, JOB_ID;
```
**Output:**
| DEPARTMENT_ID | JOB_ID    | AvgSalary |
|---------------|-----------|-----------|
| 10            | DEV       | 60000     |
| 20            | HR        | 45000     |

---

### 4. Grouping Without Aggregate Functions
List unique combinations of departments and jobs.
```sql
SELECT 
    DEPARTMENT_ID, JOB_ID
FROM
    emp_details
GROUP BY DEPARTMENT_ID , JOB_ID
ORDER BY DEPARTMENT_ID;;
```
**Output:**
| DEPARTMENT_ID | JOB_ID    |
|---------------|-----------|
| 10            | DEV       |
| 20            | HR        |

---

## Best Practices
1. Use `HAVING` for filtering grouped data, not `WHERE`.
2. Always include non-aggregate columns in the `GROUP BY` clause.
3. Combine `GROUP BY` with `ORDER BY` for better readability.
