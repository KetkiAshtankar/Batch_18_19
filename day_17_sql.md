## Keys, Joins, Group By, Built-in Functions & Normalization

---

# 1. Primary Key

## Definition

A **Primary Key** is a column (or combination of columns) that uniquely identifies each record in a table.

## Rules

* Must contain **unique values**
* Cannot contain **NULL**
* One table can have **only one Primary Key**

## Real Life Analogy

In a classroom:

* Many students can have the same name.
* But **Roll Number is unique**.

Roll Number = Primary Key

---

## Example

### Create Table

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    city VARCHAR(50)
);
```

### Insert Data

```sql
INSERT INTO students VALUES (1,'Amit',21,'Mumbai');
INSERT INTO students VALUES (2,'Neha',22,'Pune');
INSERT INTO students VALUES (3,'Rohit',20,'Delhi');
```

### Duplicate Primary Key Example

```sql
INSERT INTO students VALUES (1,'Sara',23,'Nagpur');
```

Result → Error (duplicate primary key)

---

# 2. Foreign Key

## Definition

A **Foreign Key** is a column that references a Primary Key from another table.

It creates a **relationship between tables**.

## Analogy

Customer Table
Account Table

Customer ID identifies the customer.
Account Table stores Customer ID to know who owns the account.

Customer ID in Account table = Foreign Key.

---

## Example

### Create Departments Table

```sql
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50)
);
```

Insert Data

```sql
INSERT INTO departments VALUES (101,'IT');
INSERT INTO departments VALUES (102,'HR');
INSERT INTO departments VALUES (103,'Finance');
```

---

### Create Employees Table

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    salary INT,
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);
```

Insert Data

```sql
INSERT INTO employees VALUES (1,'Raj',50000,101);
INSERT INTO employees VALUES (2,'Simran',40000,102);
INSERT INTO employees VALUES (3,'Karan',60000,101);
```

Invalid Foreign Key Example

```sql
INSERT INTO employees VALUES (4,'Anu',45000,999);
```

Result → Error because department 999 does not exist.

---

# 3. SQL Joins

Joins are used to **combine data from multiple tables**.

## Analogy

Imagine two Excel sheets:

Employees Sheet
Departments Sheet

To see which employee belongs to which department we **join both sheets**.

---

# INNER JOIN

Returns only matching records from both tables.

```sql
SELECT employees.emp_name, departments.dept_name
FROM employees
INNER JOIN departments
ON employees.dept_id = departments.dept_id;
```

Result → Only employees with valid departments.

---

# LEFT JOIN

Returns:

* All records from left table
* Matching records from right table
* If no match → NULL

Example employee without department

```sql
INSERT INTO employees VALUES (4,'Pooja',45000,NULL);
```

Query

```sql
SELECT e.emp_name, d.dept_name
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.dept_id;
```

Result

| emp_name | dept_name |
| -------- | --------- |
| Raj      | IT        |
| Simran   | HR        |
| Karan    | IT        |
| Pooja    | NULL      |

Explanation
Pooja has no department so dept_name is NULL.

---

# RIGHT JOIN

Returns:

* All rows from right table
* Matching rows from left table

```sql
SELECT e.emp_name, d.dept_name
FROM employees e
RIGHT JOIN departments d
ON e.dept_id = d.dept_id;
```

If a department has no employee it will still appear.

---

# 4. Built-in Aggregate Functions

These functions operate on multiple rows and return one result.

---

## COUNT()

Counts number of rows.

```sql
SELECT COUNT(*) FROM employees;
```

---

## SUM()

Adds numeric values.

```sql
SELECT SUM(salary) FROM employees;
```

---

## AVG()

Average value.

```sql
SELECT AVG(salary) FROM employees;
```

---

## MAX()

Largest value.

```sql
SELECT MAX(salary) FROM employees;
```

---

## MIN()

Smallest value.

```sql
SELECT MIN(salary) FROM employees;
```

---

# 5. GROUP BY

GROUP BY groups rows that have the same value in specified column.

## Analogy

If a company wants to see **average salary department wise**, employees must be grouped by department.

---

Example

```sql
SELECT dept_id, AVG(salary)
FROM employees
GROUP BY dept_id;
```

Result → Average salary per department.

---

# GROUP BY Rule

When using GROUP BY:

Every column in SELECT must be either:

1. Inside GROUP BY
   OR
2. Used inside an aggregate function

---

## Incorrect Query

```sql
SELECT dept_id, emp_name
FROM employees
GROUP BY dept_id;
```

Problem
One department has multiple employees so MySQL cannot decide which name to show.

---

## Correct Query

```sql
SELECT dept_id, COUNT(*)
FROM employees
GROUP BY dept_id;
```

---

# HAVING Clause

HAVING filters grouped data.

WHERE filters rows before grouping.

Example

Find departments where average salary > 45000

```sql
SELECT dept_id, AVG(salary)
FROM employees
GROUP BY dept_id
HAVING AVG(salary) > 45000;
```

---

# DISTINCT

DISTINCT removes duplicate values.

Example

```sql
SELECT DISTINCT city FROM students;
```

If many students belong to same city only unique cities are returned.

---

# 6. Normalization

## Definition

Normalization is the process of organizing database tables to:

* Reduce redundancy
* Avoid anomalies
* Improve data integrity

---

# Problems Without Normalization

## Insertion Anomaly

Cannot insert data without other data.

## Update Anomaly

Same value must be updated in multiple places.

## Deletion Anomaly

Deleting a row removes important information.

---

# Unnormalized Table Example

```sql
CREATE TABLE student_course (
student_id INT,
student_name VARCHAR(50),
course_id INT,
course_name VARCHAR(50),
instructor_name VARCHAR(50),
instructor_phone VARCHAR(15)
);
```

Insert Data

```sql
INSERT INTO student_course VALUES
(1,'Amit',101,'SQL','Rahul','9991112222'),
(1,'Amit',102,'Python','Neha','8882223333'),
(2,'Priya',101,'SQL','Rahul','9991112222'),
(3,'Rohit',101,'SQL','Rahul','9991112222');
```

Problems

Instructor repeated
Course repeated
Phone repeated

---

# First Normal Form (1NF)

## Rules

* No repeating groups
* Atomic values
* Each row uniquely identified

Example

```sql
CREATE TABLE student_course_1nf (
student_id INT,
course_id INT,
student_name VARCHAR(50),
course_name VARCHAR(50),
instructor_name VARCHAR(50),
instructor_phone VARCHAR(15),
PRIMARY KEY (student_id, course_id)
);
```

---

# Second Normal Form (2NF)

Rules

* Must be in 1NF
* Remove partial dependency

Partial dependency occurs when column depends on only part of composite key.

Example

Composite Key
(student_id, course_id)

But

student_name depends only on student_id
course_name depends only on course_id

Solution → Split tables.

---

## Students Table

```sql
CREATE TABLE students (
student_id INT PRIMARY KEY,
student_name VARCHAR(50)
);
```

---

## Courses Table

```sql
CREATE TABLE courses (
course_id INT PRIMARY KEY,
course_name VARCHAR(50),
instructor_name VARCHAR(50),
instructor_phone VARCHAR(15)
);
```

---

## Enrollment Table

```sql
CREATE TABLE enrollment (
student_id INT,
course_id INT,
PRIMARY KEY (student_id, course_id),
FOREIGN KEY (student_id) REFERENCES students(student_id),
FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

---

# Third Normal Form (3NF)

Rules

* Must be in 2NF
* Remove transitive dependency

Transitive dependency

A → B
B → C

Example

course_id → instructor_name
instructor_name → instructor_phone

Solution → separate instructor table.

---

## Instructor Table

```sql
CREATE TABLE instructors (
instructor_id INT PRIMARY KEY,
instructor_name VARCHAR(50),
instructor_phone VARCHAR(15)
);
```

---

## Courses Table

```sql
CREATE TABLE courses_3nf (
course_id INT PRIMARY KEY,
course_name VARCHAR(50),
instructor_id INT,
FOREIGN KEY (instructor_id) REFERENCES instructors(instructor_id)
);
```

---

# Final Normalized Structure

Students
Courses
Instructors
Enrollment

Each table stores only related data.

---

# Query to Retrieve Complete Data

```sql
SELECT 
s.student_name,
c.course_name,
i.instructor_name,
i.instructor_phone
FROM enrollment e
JOIN students s ON e.student_id = s.student_id
JOIN courses_3nf c ON e.course_id = c.course_id
JOIN instructors i ON c.instructor_id = i.instructor_id;
```

---

# Summary

Primary Key
→ Uniquely identifies record

Foreign Key
→ Connects tables

Joins
→ Combine tables

GROUP BY
→ Groups rows

HAVING
→ Filter grouped results

DISTINCT
→ Remove duplicates

Normalization
→ Organize tables and remove redundancy

---
