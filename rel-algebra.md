# Complete Guide to Relational Algebra (With Examples)

## ✨ What is Relational Algebra?

Relational Algebra is a formal language for querying and manipulating **relational databases**. It works with **relations (tables)** and provides a theoretical foundation for SQL and other query languages.

E.F. Codd introduced relational algebra as the mathematical basis of relational databases.

---

## ✅ Six Basic Operators of Relational Algebra

### 1. **Selection (σ)**

Used to filter rows based on a condition (like WHERE in SQL).

**Syntax:**

```
σ_condition(Relation)
```

**Example:**

```
Students:
| id | name  | age |
|----|-------|-----|
| 1  | Alice | 21  |
| 2  | Bob   | 19  |
| 3  | Eve   | 22  |

σ_age > 20(Students)
```

Result:

```
| id | name  | age |
|----|-------|-----|
| 1  | Alice | 21  |
| 3  | Eve   | 22  |
```

---

### 2. **Projection (π)**

Used to select specific columns (like SELECT in SQL).

**Syntax:**

```
π_column1, column2(Relation)
```

**Example:**

```
π_name, age(Students)
```

Result:

```
| name  | age |
|-------|-----|
| Alice | 21  |
| Bob   | 19  |
| Eve   | 22  |
```

If duplicate rows occur, they are removed.

---

### 3. **Rename (ρ)**

Used to rename a relation or its attributes.

**Syntax:**

```
ρ_NewName(Relation)
```

**Example:**

```
ρ_StudentInfo(Students)
```

Renames the "Students" relation to "StudentInfo".

---

### 4. **Union (∪)**

Combines all rows from two relations (like UNION in SQL).

**Conditions:**

* Same number of columns
* Same data types (domains)

**Syntax:**

```
Relation1 ∪ Relation2
```

**Example:**

```
A:
| id | name  |
|----|-------|
| 1  | Alice |
| 2  | Bob   |

B:
| id | name  |
|----|-------|
| 3  | Eve   |
| 2  | Bob   |

A ∪ B
```

Result:

```
| id | name  |
|----|-------|
| 1  | Alice |
| 2  | Bob   |
| 3  | Eve   |
```

---

### 5. **Difference (-)**

Returns rows in one relation that are not in the other (like EXCEPT in SQL).

**Syntax:**

```
Relation1 - Relation2
```

**Example:**

```
A - B
```

Result:

```
| id | name  |
|----|-------|
| 1  | Alice |
```

---

### 6. **Cartesian Product (×)**

Combines every row of one relation with every row of another.

**Syntax:**

```
Relation1 × Relation2
```

**Example:**

```
A:
| id | name  |
|----|-------|
| 1  | Alice |
| 2  | Bob   |

B:
| course |
|--------|
| Math   |
| CS     |

A × B
```

Result:

```
| id | name  | course |
|----|-------|--------|
| 1  | Alice | Math   |
| 1  | Alice | CS     |
| 2  | Bob   | Math   |
| 2  | Bob   | CS     |
```

---

## 🔗 Join Operations

### 1. **Equijoin**

Join where attributes from two tables are compared for equality.

**Example:**

```
Students(id, name), Enrollments(student_id, course)
Students ⋈ Students.id = Enrollments.student_id Enrollments
```

Result:

```
| id | name  | student_id | course |
|----|-------|------------|--------|
| 1  | Alice | 1          | Math   |
| 1  | Alice | 1          | CS     |
```

### 2. **Natural Join**

Auto-joins tables on all common attributes with the same name.

### 3. **Theta Join**

Join with any condition, not just equality (e.g., >, <, !=).

---

## ⭐ Extended Operations

### 1. **Generalized Projection**

Supports expressions (e.g., π\_salary \* 1.1(Employee))

### 2. **Aggregate Functions & Grouping**

Operations like COUNT, AVG, MAX, SUM on groups of rows (like SQL GROUP BY)

### 3. **Left Outer Join**

Keeps all rows from the left relation; unmatched right rows are filled with NULLs.

### 4. **Outer Union**

Union of relations with different schemas (columns filled with NULLs where needed)

---

## 🌳 Query Trees

Visual representation of the order and nesting of operations. Helps with optimization.

---

## ✈️ Conclusion

Relational Algebra is the backbone of query processing in relational databases. Mastering it strengthens your foundation in database theory and practical SQL usage.
