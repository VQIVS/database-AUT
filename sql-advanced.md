# Advanced SQL Concepts (With Examples)

## 🔑 NULL Values
- **Unknown**: e.g., date of birth not known → NULL
- **Withheld**: phone exists but user didn't share it → NULL
- **Not applicable**: last degree of someone with no degree → NULL

---

## ⚖️ Three-Valued Logic
- TRUE, FALSE, UNKNOWN (NULL-involved expressions result in UNKNOWN).

---

## 🔍 Nested Queries
Run subqueries inside WHERE or FROM clauses.

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

## 🔗 Joins
- **Inner Join**: Returns matching rows only.
- **Outer Joins**: Keeps unmatched rows from left/right/full.

---

## Σ Aggregate Functions
COUNT, SUM, AVG, MAX, MIN.

**Example:**
```sql
SELECT COUNT(*) FROM employee;
```

---

## 📋 WITH Clause (Common Table Expressions)
Define temporary result sets.

**Example:**
```sql
WITH high_salary AS (
  SELECT * FROM employee WHERE salary > 5000
)
SELECT * FROM high_salary WHERE age < 40;
```

---

## 🔄 Recursion (WITH RECURSIVE)
Express hierarchical queries.

**Example:**
```sql
WITH RECURSIVE SUP_EMP(SupSsn, EmpSsn) AS (
  SELECT SupervisorSsn, Ssn FROM EMPLOYEE WHERE SupervisorSsn IS NULL
  UNION
  SELECT E.Ssn, S.SupSsn FROM EMPLOYEE E, SUP_EMP S WHERE E.SupervisorSsn = S.EmpSsn
)
SELECT * FROM SUP_EMP;
```

---

## ✏️ ALTER
Modify table structure (e.g., add column, drop constraint).

---

## 📜 Views (Virtual Tables)
- Based on a query result.
- Reflects underlying data.
- Editable only if simple (no JOIN, no aggregation).

---

## ✈️ Conclusion
Advanced SQL concepts like nested queries, joins, and recursion empower developers to handle complex data scenarios efficiently.
