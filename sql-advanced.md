# Advanced SQL Concepts (With Examples)

## 🔐 NULL Values

* **Unknown**: e.g., date of birth not known → NULL
* **Withheld**: phone exists but user didn't share it → NULL
* **Not applicable**: last degree of someone with no degree → NULL

---

## ⚖️ Three-Valued Logic

* In SQL: TRUE, FALSE, UNKNOWN (NULL-involved expressions result in UNKNOWN)
* Used in conditions (e.g., WHERE, CASE)

---

## 🔍 Nested Queries

Used to run subqueries inside WHERE or FROM clauses.

**Example:**

```sql
SELECT name FROM employee
WHERE dept_id IN (SELECT id FROM department WHERE name = 'IT');
```

---

## ▶️ Comparison in Nested Queries

Used with ALL, ANY, IN, EXISTS, etc.

**Example:**

```sql
SELECT name FROM employee WHERE salary > ALL (SELECT salary FROM employee WHERE dept_id = 1);
```

---

## 🔘 EXISTS Clause

Returns TRUE if subquery returns rows.

```sql
SELECT name FROM employee e WHERE EXISTS (
  SELECT * FROM department d WHERE d.id = e.dep
);
```

---

## 🔹 EXCEPT (Set Subtraction)

Find rows in one query not in another.

**Example:**

```sql
SELECT name FROM employee
EXCEPT
SELECT name FROM employee e JOIN project p ON e.id = p.emp_id WHERE p.dept_no = 5;
```

---

## ↔ Explicit Sets

```sql
SELECT * FROM employee WHERE department IN ('IT', 'HR');
```

---

## 📝 Inner vs Outer Joins

* **Inner Join**: returns matching rows only
* **Left/Right Outer Join**: keeps unmatched rows from left/right
* **Full Outer Join**: keeps all rows, fills NULL where no match

---

## Σ Aggregate Functions

* COUNT, SUM, AVG, MAX, MIN

```sql
SELECT COUNT(*) FROM employee;
```

---

## 👥 GROUP BY

Used to group rows and apply aggregates:

```sql
SELECT dept_id, AVG(salary)
FROM employee
GROUP BY dept_id;
```

---

## ⛔ GROUP BY + HAVING

Filters groups (like WHERE filters rows):

```sql
SELECT dept_id, COUNT(*)
FROM employee
GROUP BY dept_id
HAVING COUNT(*) > 5;
```

---

## 📄 WITH Clause (Common Table Expressions)

Used to define temporary result sets:

```sql
WITH high_salary AS (
  SELECT * FROM employee WHERE salary > 5000
)
SELECT * FROM high_salary WHERE age < 40;
```

---

## ↔ CASE Statement

Used for conditional expressions in queries.

```sql
SELECT Ssn, Salary,
  CASE
    WHEN Salary > 3000 THEN 'Above average'
    WHEN Salary = 3000 THEN 'Borderline'
    ELSE 'Below average'
  END AS salary_status
FROM EMPLOYEE;
```

---

## 🧰 Recursion (WITH RECURSIVE)

Used to express hierarchical queries:

```sql
WITH RECURSIVE SUP_EMP(SupSsn, EmpSsn) AS (
  SELECT SupervisorSsn, Ssn FROM EMPLOYEE WHERE SupervisorSsn IS NULL
  UNION
  SELECT E.Ssn, S.SupSsn FROM EMPLOYEE E, SUP_EMP S WHERE E.SupervisorSsn = S.EmpSsn
)
SELECT * FROM SUP_EMP;
```

---

## ❗ Assertion

Constraints applied to entire DB when CHECK on a single table isn't enough.
Used on INSERT/UPDATE.

---

## ⚡ Trigger

Automatically executes code on events like INSERT/UPDATE.

```sql
CREATE TRIGGER upd_check
BEFORE UPDATE ON employee
FOR EACH ROW
BEGIN
  IF NEW.Salary < 1000 THEN SET NEW.Salary = 1000;
  ELSEIF NEW.Salary > 10000 THEN SET NEW.Salary = 10000;
  END IF;
END;
```

---

## 📃 Views (Virtual Tables)

* Based on a query result
* Always reflects underlying data
* Can be queried like a table
* Editable only if simple (no JOIN, no aggregation, no NOT NULL violation)

---

## ❌ DROP

```sql
DROP SCHEMA COMPANY RESTRICT;
DROP TABLE DEPENDENT RESTRICT;
```

* RESTRICT: prevents drop if dependent objects exist
* CASCADE: forces deletion (dangerous)

---

## ✏️ ALTER

Used to modify table structure (e.g., add column, drop constraint, etc.)
