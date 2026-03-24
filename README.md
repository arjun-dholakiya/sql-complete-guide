# SQL Interview Preparation

A structured and beginner-friendly SQL guide with examples and practice questions.
This repository is designed to build strong fundamentals for interviews.

---

## 📚 Table of Contents

1. Introduction to SQL
2. Database Basics
3. SQL Commands
4. CRUD Operations
5. Filtering Data
6. SELECT in Detail
7. Aggregation
8. Keys & Constraints
9. Advanced Commands
10. Practice Questions

---

# 🔰 1. Introduction to SQL

SQL (Structured Query Language) is used to interact with databases.

### Uses:

* Retrieve data
* Insert data
* Update data
* Delete data

---

# 🗄️ 2. Database Basics

## What is Database?

A database is a collection of organized data.

## Types of Database

* Relational (MySQL, PostgreSQL)
* NoSQL (MongoDB)
* Hierarchical
* Network

## Database Structure

Database → Tables → Rows → Columns

---

## What is Table?

A table stores data in rows and columns.

| id | name  | age |
| -- | ----- | --- |
| 1  | Arjun | 22  |

---

# ⚙️ 3. SQL Commands

## Types of SQL Commands

* DDL → CREATE, ALTER, DROP
* DML → INSERT, UPDATE, DELETE
* DQL → SELECT
* DCL → GRANT, REVOKE
* TCL → COMMIT, ROLLBACK

---

## Create Database

```sql
-- Create a new database
CREATE DATABASE company;
```

## Use Database

```sql
-- Select database to work with
USE company;
```

## Create Table

```sql
-- Create employees table
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  age INT
);
```

---

## SQL Data Types

* INT → Integer
* VARCHAR → String
* DATE → Date
* FLOAT → Decimal

---

# 🔁 4. CRUD Operations

## SELECT (Fetch Data)

```sql
-- Select all columns
SELECT * FROM employees;

-- Select specific columns
SELECT name, age FROM employees;
```

---

## INSERT (Add Data)

```sql
-- Insert single row
INSERT INTO employees (id, name, age)
VALUES (1, 'Arjun', 22);

-- Insert multiple rows
INSERT INTO employees VALUES
(2, 'Rahul', 25),
(3, 'Amit', 24);
```

---

## UPDATE (Modify Data)

```sql
-- Update age of employee
UPDATE employees
SET age = 26
WHERE id = 1;
```

---

## DELETE (Remove Data)

```sql
-- Delete specific record
DELETE FROM employees WHERE id = 1;
```

---

# 🎯 5. Filtering Data

## WHERE Clause (Filter Records)

```sql
SELECT * FROM employees WHERE age > 20;
```

---

## Operators (Apply Conditions)

```sql
-- AND operator
SELECT * FROM employees WHERE age > 20 AND age < 30;

-- OR operator
SELECT * FROM employees WHERE age < 20 OR age > 30;

-- LIKE operator (pattern matching)
SELECT * FROM employees WHERE name LIKE 'A%';
```

---

## LIMIT Clause (Restrict Number of Rows)

```sql
-- Get first 5 records
SELECT * FROM employees LIMIT 5;

-- Skip 1 record, then fetch next 2
SELECT * FROM employees LIMIT 2 OFFSET 1;
```

---

## ORDER BY Clause (Sort Data)

```sql
-- Sort ascending
SELECT * FROM employees ORDER BY age ASC;

-- Sort descending
SELECT * FROM employees ORDER BY age DESC;
```

---

# 🔍 6. SELECT in Detail (Important for Interviews)

## Sample Data Used

| id | name  | age |
| -- | ----- | --- |
| 1  | Arjun | 22  |
| 2  | Rahul | 25  |
| 3  | Amit  | 24  |
| 4  | Arjun | 25  |

---

## 1. Select All Records

```sql
SELECT * FROM employees;
```

### Output:

| id | name  | age |
| -- | ----- | --- |
| 1  | Arjun | 22  |
| 2  | Rahul | 25  |
| 3  | Amit  | 24  |
| 4  | Arjun | 25  |

---

## 2. Select Specific Columns

```sql
SELECT name, age FROM employees;
```

### Output:

| name  | age |
| ----- | --- |
| Arjun | 22  |
| Rahul | 25  |
| Amit  | 24  |
| Arjun | 25  |

---

## 3. DISTINCT (Remove Duplicate Values)

```sql
SELECT DISTINCT name FROM employees;
```

### Output:

| name  |
| ----- |
| Arjun |
| Rahul |
| Amit  |

---

## 4. WHERE Condition (Filter Rows)

```sql
SELECT * FROM employees WHERE age > 23;
```

### Output:

| id | name  | age |
| -- | ----- | --- |
| 2  | Rahul | 25  |
| 3  | Amit  | 24  |
| 4  | Arjun | 25  |

---

## 5. BETWEEN (Range Filter)

```sql
SELECT * FROM employees WHERE age BETWEEN 23 AND 25;
```

### Output:

| id | name  | age |
| -- | ----- | --- |
| 2  | Rahul | 25  |
| 3  | Amit  | 24  |
| 4  | Arjun | 25  |

---

## 6. IN Operator (Multiple Values Match)

```sql
SELECT * FROM employees WHERE name IN ('Arjun', 'Amit');
```

### Output:

| id | name  | age |
| -- | ----- | --- |
| 1  | Arjun | 22  |
| 3  | Amit  | 24  |
| 4  | Arjun | 25  |

---

## 7. LIKE Operator (Pattern Matching)

```sql
-- Starts with 'A'
SELECT * FROM employees WHERE name LIKE 'A%';
```

### Output:

| id | name  | age |
| -- | ----- | --- |
| 1  | Arjun | 22  |
| 3  | Amit  | 24  |
| 4  | Arjun | 25  |

---

## 8. ORDER BY (Sorting Results)

```sql
SELECT * FROM employees ORDER BY age DESC;
```

### Output:

| id | name  | age |
| -- | ----- | --- |
| 2  | Rahul | 25  |
| 4  | Arjun | 25  |
| 3  | Amit  | 24  |
| 1  | Arjun | 22  |

---

## 9. LIMIT (Restrict Output)

```sql
SELECT * FROM employees LIMIT 2;
```

### Output:

| id | name  | age |
| -- | ----- | --- |
| 1  | Arjun | 22  |
| 2  | Rahul | 25  |

---

## 10. Tricky Query (Second Highest Age)

```sql
SELECT MAX(age)
FROM employees
WHERE age < (SELECT MAX(age) FROM employees);
```

### Output:

| MAX(age) |
| -------- |
| 24       |

---

# 📊 7. Aggregation

## Aggregate Functions

```sql
-- Count total records
SELECT COUNT(*) FROM employees;

-- Average age
SELECT AVG(age) FROM employees;

-- Maximum age
SELECT MAX(age) FROM employees;
```

---

## GROUP BY (Group Data)

```sql
SELECT age, COUNT(*)
FROM employees
GROUP BY age;
```

---

## HAVING (Filter Groups)

```sql
SELECT age, COUNT(*)
FROM employees
GROUP BY age
HAVING COUNT(*) > 1;
```

---

# 🔑 8. Keys & Constraints

## Keys

* Primary Key → Unique + Not Null
* Foreign Key → Connect tables
* Unique Key

## Constraints

* NOT NULL
* UNIQUE
* DEFAULT

---

## Foreign Key Example

```sql
CREATE TABLE orders (
  id INT,
  user_id INT,
  FOREIGN KEY (user_id) REFERENCES users(id)
);
```

## Cascading (ON DELETE / ON UPDATE CASCADE)

### What is Cascading?

**Cascading** is a feature in SQL that automatically applies changes from a **parent table** to its related **child table**.

👉 It is mainly used with **Foreign Keys**.

When you perform operations like:

* DELETE
* UPDATE

on the parent table, the same changes are automatically reflected in the child table.

---

### Why do we use Cascading?

Without cascading:

* You may get errors when deleting parent data
* Or you may leave **orphan records** (invalid data)

With cascading:

* Data stays **consistent**
* No manual cleanup required

---

### Example Tables

#### Parent Table: `users`

| id | name  |
| -- | ----- |
| 1  | Arjun |
| 2  | Rahul |

#### Child Table: `orders`

| id  | user_id |
| --- | ------- |
| 101 | 1       |
| 102 | 1       |
| 103 | 2       |

---

### Creating Tables with Cascading

```sql id="cas1"
CREATE TABLE users (
  id INT PRIMARY KEY,
  name VARCHAR(50)
);

CREATE TABLE orders (
  id INT PRIMARY KEY,
  user_id INT,
  FOREIGN KEY (user_id) REFERENCES users(id)
  ON DELETE CASCADE
  ON UPDATE CASCADE
);
```

---

## ON DELETE CASCADE

### What it does?

When a row is deleted from the **parent table**,
all related rows in the **child table** are automatically deleted.

---

### Example

```sql id="cas2"
DELETE FROM users WHERE id = 1;
```

### Result:

#### users table

| id | name  |
| -- | ----- |
| 2  | Rahul |

#### orders table

| id  | user_id |
| --- | ------- |
| 103 | 2       |

👉 All orders with `user_id = 1` are automatically deleted.

---

## ON UPDATE CASCADE

### What it does?

When a value in the parent table (usually primary key) is updated,
it automatically updates related values in the child table.

---

### Example

```sql id="cas3"
UPDATE users SET id = 10 WHERE id = 2;
```

### Result:

#### users table

| id | name  |
| -- | ----- |
| 10 | Rahul |

#### orders table

| id  | user_id |
| --- | ------- |
| 103 | 10      |

👉 `user_id` automatically updated from 2 → 10

---

### Important Notes

* Cascading works only with **Foreign Keys**
* Helps maintain **referential integrity**
* Use carefully to avoid accidental data loss

---

# 🚀 9. Advanced Commands

## ALTER (Modify Table)

```sql
ALTER TABLE employees ADD COLUMN salary INT;
```

---

## MODIFY (Change Column Type)

```sql
ALTER TABLE employees MODIFY age INT;
```

---

## TRUNCATE (Delete All Records)

```sql
TRUNCATE TABLE employees;
```

---

## SQL Execution Order

SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY → LIMIT

---

# 🧠 Practice Questions

## Easy

1. Select all records
2. Insert 5 records
3. Use WHERE

## Medium

1. Find average age
2. Count employees
3. Use GROUP BY

## Hard

1. Find second highest salary
2. Find duplicate records
3. Use HAVING with GROUP BY

---

## 📌 Final Note

Practice regularly and focus on understanding queries with outputs.
SQL is one of the most important skills for interviews.
