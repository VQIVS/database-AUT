# Complete Guide to Relational Algebra (With Examples)

## 🌟 Overview
Relational Algebra is a formal language for querying and manipulating **relational databases**. It provides a theoretical foundation for SQL and other query languages, introduced by E.F. Codd.

---

## ✅ Six Basic Operators of Relational Algebra

### 1. **Selection (σ)**
Filters rows based on a condition (similar to WHERE in SQL).

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
Selects specific columns (like SELECT in SQL).

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

---

### 3. **Rename (ρ)**
Renames a relation or its attributes.

**Syntax:**
```
ρ_NewName(Relation)
```

**Example:**
```
ρ_StudentInfo(Students)
```

---

### 4. **Union (∪)**
Combines rows from two relations (like UNION in SQL).

**Conditions:**
- Same number of columns
- Same data types

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
Joins tables based on equality conditions.

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
Auto-joins tables on common attributes.

### 3. **Theta Join**
Joins with conditions other than equality.

---

## 🌟 Extended Operations

### 1. **Generalized Projection**
Supports expressions (e.g., π_salary * 1.1(Employee)).

### 2. **Aggregate Functions & Grouping**
Operations like COUNT, AVG, MAX, SUM on groups of rows.

---

## 🌳 Query Trees
Visual representation of the order and nesting of operations.

---

## ✈️ Conclusion
Relational Algebra is the backbone of query processing in relational databases. Mastering it strengthens your foundation in database theory and SQL usage.
