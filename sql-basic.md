# Complete Introduction to SQL (With Examples)

## ✨ What is SQL?

SQL (Structured Query Language) is a standard language used to interact with relational databases. It allows you to define structure (DDL) and manipulate data (DML).

---

## 🔧 Categories of SQL

### 1. **Data Definition Language (DDL)**

Used to define database schema and structure.
Examples:

* CREATE
* ALTER
* DROP
* TRUNCATE

### 2. **Data Manipulation Language (DML)**

Used to insert, modify, and query data.
Examples:

* SELECT
* INSERT
* UPDATE
* DELETE

---

## ✅ Key Features of SQL

* Simple, descriptive, easy to learn
* Nonprocedural (you say *what* to do, not *how*)
* Standardized by ANSI and ISO
* Different dialects exist (MySQL, PostgreSQL, Oracle, etc.)

---

## 🏛 Creating a Database and Schema

* A **database** consists of physical files managed by the DBMS.
* A **schema** is a group of related database objects (tables, views, indexes).
* **Authentication** ensures only valid users can access the DB.

---

## 🔤 SQL Data Types

* **INTEGER, FLOAT, CHAR, VARCHAR**
* **BOOLEAN**: TRUE, FALSE, UNKNOWN
* **CLOB**: Large text data
* **BLOB**: Binary data
* **DATE, TIME, TIMESTAMP**

Use appropriate types for performance in sorting, indexing, etc.

---

## ✏️ CREATE TABLE Syntax

```sql
CREATE TABLE employee (
  id INTEGER NOT NULL AUTO_INCREMENT,
  dep INTEGER,
  PRIMARY KEY (id)
);

CREATE TABLE department (
  id INTEGER NOT NULL,
  manager INTEGER NOT NULL,
  PRIMARY KEY (id),
  FOREIGN KEY (manager) REFERENCES employee(id)
);

ALTER TABLE employee
ADD FOREIGN KEY (dep) REFERENCES department(id);
```

---

## 📝 Nested Tables (Oracle Only)

```sql
CREATE TYPE address_tab IS TABLE OF CHAR(50);
CREATE TABLE customers (
  id NUMBER,
  address address_tab
)
NESTED TABLE address STORE AS customer_addresses;

INSERT INTO customers VALUES (
  1, address_tab('101 First', '123 Maple')
);

SELECT c.id, u.* FROM customers c, TABLE(c.address) u;
```

---

## ⚖️ SQL Constraints

* **NOT NULL**: Value must not be null
* **UNIQUE**: No duplicate values
* **DEFAULT**: Fills in default value if none is given
* **CHECK**: Ensures values satisfy a condition

Example:

```sql
CREATE TABLE student (
  id INT,
  age INT CHECK (age >= 18)
);
```

---

## 🔢 SELECT Statement

```sql
SELECT column1, column2 FROM tablename;
SELECT * FROM tablename;
```

Add filters:

```sql
SELECT name FROM employee WHERE age > 25;
```

---

## 🔍 SELECT-PROJECT-JOIN

* **SELECT** filters rows
* **PROJECT** filters columns
* **JOIN** combines rows from multiple tables

Example:

```sql
SELECT e.name, d.name
FROM employee e
JOIN department d ON e.dep = d.id;
```

---

## 🔹 Aliasing and Ambiguity

```sql
SELECT e.name AS emp_name FROM employee e;
```

---

## 🤐 SQL vs Set Theory

* SQL tables are **multisets** (duplicates allowed)
* Removing duplicates is costly and optional

---

## 🔎 Substring and Matching

```sql
SELECT name FROM employee WHERE name LIKE '%Ali%';
```

---

## 💪 Arithmetic & Logical Operators

```sql
SELECT name, salary * 1.1 FROM employee;
```

---

## ↕ ORDER BY

```sql
SELECT * FROM employee ORDER BY age DESC;
```

---

## ➕ INSERT

```sql
INSERT INTO employee (name, age) VALUES ('Alice', 30);
```

---

## ❌ DELETE

```sql
DELETE FROM employee WHERE id = 5;
```

---

## ✍️ UPDATE

```sql
UPDATE employee SET age = 31 WHERE name = 'Alice';
```

---

## ✈️ Conclusion

SQL is a powerful and standardized tool for working with relational databases. Mastering its core commands gives you strong control over data structure and manipulation.
