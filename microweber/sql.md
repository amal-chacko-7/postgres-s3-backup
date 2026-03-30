# SQL Interview Prep

---

## 1. What is SQL?

SQL (Structured Query Language) is used to interact with **relational databases** — data stored in tables with rows and columns.

Key databases you'll hear about: **MySQL, PostgreSQL, Oracle, SQL Server, SQLite**

---

## 2. Types of SQL Commands

| Type | What it does | Commands |
|------|-------------|----------|
| **DDL** — Data Definition | Define/modify structure | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| **DML** — Data Manipulation | Work with data | `SELECT`, `INSERT`, `UPDATE`, `DELETE` |
| **DCL** — Data Control | Permissions | `GRANT`, `REVOKE` |
| **TCL** — Transaction Control | Manage transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |

---

## 3. 🔥 Basic SELECT Queries

```sql
-- Get all columns
SELECT * FROM employees;

-- Get specific columns
SELECT name, salary FROM employees;

-- With a condition
SELECT * FROM employees WHERE salary > 50000;

-- Sort results
SELECT * FROM employees ORDER BY salary DESC;

-- Limit rows
SELECT * FROM employees LIMIT 5;
```

---

## 4. 🔥 Filtering — WHERE Clause

```sql
-- Comparison operators: =, !=, >, <, >=, <=
SELECT * FROM employees WHERE department = 'HR';

-- Multiple conditions
SELECT * FROM employees WHERE department = 'HR' AND salary > 40000;

-- Range
SELECT * FROM employees WHERE salary BETWEEN 30000 AND 60000;

-- Match a list
SELECT * FROM employees WHERE department IN ('HR', 'Finance');

-- Pattern matching
SELECT * FROM employees WHERE name LIKE 'A%';   -- starts with A
SELECT * FROM employees WHERE name LIKE '%kumar'; -- ends with kumar

-- NULL checks
SELECT * FROM employees WHERE manager_id IS NULL;
```

---

## 5. 🔥 Aggregate Functions

Used to compute a value from multiple rows.

```sql
SELECT COUNT(*)          FROM employees;               -- total rows
SELECT COUNT(salary)     FROM employees;               -- non-null salaries
SELECT SUM(salary)       FROM employees;
SELECT AVG(salary)       FROM employees;
SELECT MAX(salary)       FROM employees;
SELECT MIN(salary)       FROM employees;
```

## 9. 🔥 DDL — Creating & Modifying Tables

```sql
-- Create
CREATE TABLE employees (
    id        INT PRIMARY KEY,
    name      VARCHAR(100) NOT NULL,
    salary    DECIMAL(10,2),
    dept_id   INT
);

-- Add a column
ALTER TABLE employees ADD COLUMN email VARCHAR(100);

-- Drop a column
ALTER TABLE employees DROP COLUMN email;

-- Delete all rows (keeps structure)
TRUNCATE TABLE employees;

-- Delete table entirely
DROP TABLE employees;
```

---

## 10. DML — Insert, Update, Delete

```sql
-- Insert
INSERT INTO employees (id, name, salary) VALUES (1, 'Rahul', 45000);

-- Update
UPDATE employees SET salary = 50000 WHERE id = 1;

-- Delete specific rows
DELETE FROM employees WHERE id = 1;
```

---

## 11. Constraints

Rules applied to columns to ensure data integrity.

| Constraint | Purpose |
|-----------|---------|
| `PRIMARY KEY` | Unique + NOT NULL identifier for each row |
| `FOREIGN KEY` | Links to a primary key in another table |
| `UNIQUE` | No duplicate values |
| `NOT NULL` | Value must always be provided |
| `DEFAULT` | Auto-fills a value if none given |
| `CHECK` | Custom condition must be true |

---

## 15. Key Concepts to Know (Theory)

### ACID Properties
- **Atomicity** — All or nothing
- **Consistency** — Data stays valid
- **Isolation** — Transactions don't interfere
- **Durability** — Committed changes are permanent

### Normalization (basics)
| Form | Rule |
|------|------|
| **1NF** | No repeating groups; atomic values |
| **2NF** | 1NF + no partial dependency on composite key |
| **3NF** | 2NF + no transitive dependency |

### DELETE vs TRUNCATE vs DROP
| Command | Removes | Rollback? | Keeps structure? |
|---------|---------|-----------|-----------------|
| `DELETE` | Specific rows | ✅ Yes | ✅ Yes |
| `TRUNCATE` | All rows | ❌ No | ✅ Yes |
| `DROP` | Entire table | ❌ No | ❌ No |

### WHERE vs HAVING
- `WHERE` → filters **rows** (before grouping)
- `HAVING` → filters **groups** (after GROUP BY)

---

## 16. 🔥 Common Interview Questions

1. What is a primary key vs foreign key?
2. Difference between `INNER JOIN` and `LEFT JOIN`?
3. What is normalization? Why do we do it?
4. What is the difference between `DELETE`, `TRUNCATE`, and `DROP`?
5. Can we use `WHERE` with aggregate functions? *(No — use `HAVING`)*
6. What is a view? Why use it?
7. Write a query to find the second highest salary.
8. What are indexes? Pros and cons?
9. Explain ACID properties.
10. What is a self-join?

### Bonus: Second Highest Salary
```sql
-- Method 1: Using LIMIT + OFFSET
SELECT DISTINCT salary FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;

-- Method 2: Using subquery
SELECT MAX(salary) FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

## Quick Revision Checklist

- [ ] SELECT, WHERE, ORDER BY, LIMIT
- [ ] Aggregate functions (COUNT, SUM, AVG, MAX, MIN)
- [ ] GROUP BY + HAVING
- [ ] All 4 JOINs (INNER, LEFT, RIGHT, FULL)
- [ ] Subqueries
- [ ] CREATE, ALTER, DROP, TRUNCATE
- [ ] INSERT, UPDATE, DELETE
- [ ] Constraints (PK, FK, UNIQUE, NOT NULL)
- [ ] Views and Indexes
- [ ] Transactions (COMMIT, ROLLBACK)
- [ ] ACID properties
- [ ] Normalization (1NF, 2NF, 3NF)

---

*Good luck with your interview! 🚀*
