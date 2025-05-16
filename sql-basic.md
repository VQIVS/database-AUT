# Complete Introduction to SQL (With Examples)

## 🌟 Overview
SQL (Structured Query Language) is a standard language used to interact with relational databases. It allows you to define structure (DDL) and manipulate data (DML).

---

## 🔧 Categories of SQL

### 1. **Data Definition Language (DDL)**
Defines database schema and structure.

Examples:
- CREATE
- ALTER
- DROP
- TRUNCATE

### 2. **Data Manipulation Language (DML)**
Manipulates and queries data.

Examples:
- SELECT
- INSERT
- UPDATE
- DELETE

---

## 🏛️ Creating a Database and Schema
- A **database** consists of physical files managed by the DBMS.
- A **schema** is a group of related database objects (tables, views, indexes).

---

## ✏️ CREATE TABLE Syntax

**Example:**
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

## 🔍 SELECT Statement

**Example:**
```sql
SELECT column1, column2 FROM tablename;
SELECT * FROM tablename;
```

Add filters:
```sql
SELECT name FROM employee WHERE age > 25;
```

---

## ➕ INSERT

**Example:**
```sql
INSERT INTO employee (name, age) VALUES ('Alice', 30);
```

---

## ✏️ UPDATE

**Example:**
```sql
UPDATE employee SET age = 31 WHERE name = 'Alice';
```

---

## ✈️ Conclusion
SQL is a powerful and standardized tool for working with relational databases. Mastering its core commands gives you strong control over data structure and manipulation.
