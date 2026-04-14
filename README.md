# 🚀 SQL Interview Preparation (Beginner → Advanced)

A complete SQL guide designed for **interview preparation** with concepts, examples, and practice questions.

---

## 📚 Table of Contents

1. Introduction to SQL
2. Database Basics
3. SQL Commands
4. CRUD Operations
5. Filtering Data
6. SELECT Deep Dive
7. Aggregation
8. Keys & Constraints
9. JOINS (Important)
10. UNION & UNION ALL
11. Subqueries
12. Views
13. Advanced Commands
14. SQL Execution Order
15. Practice Questions

---

## 🔰 1. Introduction to SQL

SQL (Structured Query Language) is used to interact with relational databases.

### Uses:

* Retrieve data
* Insert data
* Update data
* Delete data

---

## 🗄️ 2. Database Basics

### What is a Database?

A database is a structured collection of data.

### Types of Databases:

* Relational → MySQL, PostgreSQL
* NoSQL → MongoDB

### Structure:

Database → Tables → Rows → Columns

---

## ⚙️ 3. SQL Commands

| Type | Commands               |
| ---- | ---------------------- |
| DDL  | CREATE, ALTER, DROP    |
| DML  | INSERT, UPDATE, DELETE |
| DQL  | SELECT                 |
| DCL  | GRANT, REVOKE          |
| TCL  | COMMIT, ROLLBACK       |

---

## 🔁 4. CRUD Operations

### SELECT

```sql
SELECT * FROM employees;
```

### INSERT

```sql
INSERT INTO employees (id, name, age)
VALUES (1, 'Arjun', 22);
```

### UPDATE

```sql
UPDATE employees
SET age = 25
WHERE id = 1;
```

### DELETE

```sql
DELETE FROM employees
WHERE id = 1;
```

---

## 🎯 5. Filtering Data

```sql
SELECT * FROM employees WHERE age > 20;
SELECT * FROM employees WHERE name LIKE 'A%';
SELECT * FROM employees ORDER BY age DESC;
SELECT * FROM employees LIMIT 5;
```

---

## 🔍 6. SELECT Deep Dive

```sql
SELECT DISTINCT name FROM employees;

SELECT * FROM employees
WHERE age BETWEEN 20 AND 30;

SELECT * FROM employees
WHERE name IN ('Arjun', 'Amit');
```

---

## 📊 7. Aggregation

```sql
SELECT COUNT(*) FROM employees;
SELECT AVG(age) FROM employees;
SELECT MAX(age) FROM employees;
```

### GROUP BY

```sql
SELECT dept_id, COUNT(*)
FROM employees
GROUP BY dept_id;
```

### HAVING

```sql
SELECT dept_id, COUNT(*)
FROM employees
GROUP BY dept_id
HAVING COUNT(*) > 2;
```

---

## 🔑 8. Keys & Constraints

* Primary Key → Unique + Not Null
* Foreign Key → Connect tables
* UNIQUE, NOT NULL, DEFAULT

---

## 🔗 9. JOINS

### Sample Tables

**employees**

| id | name | dept_id |
| -- | ---- | ------- |

**departments**

| id | dept_name |

---

### INNER JOIN

```sql
SELECT e.name, d.dept_name
FROM employees e
INNER JOIN departments d
ON e.dept_id = d.id;
```

---

### LEFT JOIN

```sql
SELECT e.name, d.dept_name
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.id;
```

---

### RIGHT JOIN

```sql
SELECT e.name, d.dept_name
FROM employees e
RIGHT JOIN departments d
ON e.dept_id = d.id;
```

---

### FULL JOIN

```sql
SELECT e.name, d.dept_name
FROM employees e
FULL JOIN departments d
ON e.dept_id = d.id;
```

---

### SELF JOIN

```sql
SELECT A.name AS employee, B.name AS manager
FROM employees A
JOIN employees B
ON A.manager_id = B.id;
```

---

## 🔄 10. UNION

### UNION (removes duplicates)

```sql
SELECT name FROM employees
UNION
SELECT name FROM customers;
```

### UNION ALL (keeps duplicates)

```sql
SELECT name FROM employees
UNION ALL
SELECT name FROM customers;
```

---

## 🧠 11. Subqueries

### Second Highest Salary

```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

### IN Subquery

```sql
SELECT name FROM employees
WHERE dept_id IN (
  SELECT id FROM departments WHERE dept_name = 'IT'
);
```

---

### EXISTS

```sql
SELECT name FROM employees e
WHERE EXISTS (
  SELECT 1 FROM departments d
  WHERE d.id = e.dept_id
);
```

---

## 👁️ 12. Views

### Create View

```sql
CREATE VIEW emp_view AS
SELECT name, age FROM employees;
```

### Use View

```sql
SELECT * FROM emp_view;
```

### Update View

```sql
UPDATE emp_view SET age = 30 WHERE name = 'Arjun';
```

### Notes:

* Simplifies complex queries
* Not all views are updatable

---

## 🚀 13. Advanced Commands

```sql
ALTER TABLE employees ADD salary INT;
TRUNCATE TABLE employees;
```

---

## ⚡ 14. SQL Execution Order

```
FROM → JOIN → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

---

## 🧠 15. Practice Questions

### 🟢 Easy

1. Select all employees
2. Find employees with age > 25
3. Get names starting with 'A'
4. Sort employees by age
5. Get distinct names

---

### 🟡 Medium

1. Count employees in each department
2. Find average salary
3. Find duplicate records
4. Use GROUP BY + HAVING
5. Get employees between age 20–30

---

### 🔴 Hard

1. Find second highest salary
2. Find Nth highest salary
3. Employees without department
4. Highest salary per department
5. Subquery + JOIN combination

---

## 📌 Final Note

* Focus on understanding logic instead of memorizing
* Practice consistently
* Solve real interview problems

💡 SQL is one of the most important skills for backend & data roles.
