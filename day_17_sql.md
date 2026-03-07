# 📘 MySQL Subqueries – Session Notes

## 1️⃣ What is a Subquery?

### Technical Definition

A **subquery** is a query nested inside another SQL query.

It is enclosed inside **parentheses `()`** and executed **before the outer query**.

It is also called:

* Nested Query
* Inner Query

The main query is called:

* Outer Query

---

## 2️⃣ Layman Analogy

Imagine a teacher asking:

> “Which student scored more than the **class average**?”

Steps happening:

1. Calculate **class average** → Subquery
2. Compare each student's marks with that value → Outer query

So:

```
Outer Query
     ↑
Uses the result of
     ↓
Subquery
```

---

# 3️⃣ Database Setup (Used Throughout Session)

## Step 1: Create Database

```sql
CREATE DATABASE ShopDB;
USE ShopDB;
```

---

## Step 2: Create Customers Table

```sql
CREATE TABLE customers (
customer_id INT PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(100),
city VARCHAR(100)
);
```

Insert data

```sql
INSERT INTO customers (name,city) VALUES
('Alice','Mumbai'),
('Bob','Delhi'),
('Charlie','Mumbai'),
('David','Pune'),
('Eva','Delhi');
```

---

## Step 3: Create Orders Table

```sql
CREATE TABLE orders (
order_id INT PRIMARY KEY AUTO_INCREMENT,
customer_id INT,
total_amount DECIMAL(10,2),
order_date DATE,
FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

Insert data

```sql
INSERT INTO orders (customer_id,total_amount,order_date) VALUES
(1,1500,'2024-01-02'),
(2,300,'2024-01-05'),
(1,700,'2024-02-01'),
(3,1200,'2024-02-10'),
(2,450,'2024-03-02');
```

---

# 4️⃣ Visual Representation of Tables

### Customers

| customer_id | name    | city   |
| ----------- | ------- | ------ |
| 1           | Alice   | Mumbai |
| 2           | Bob     | Delhi  |
| 3           | Charlie | Mumbai |
| 4           | David   | Pune   |
| 5           | Eva     | Delhi  |

---

### Orders

| order_id | customer_id | total_amount | order_date |
| -------- | ----------- | ------------ | ---------- |
| 1        | 1           | 1500         | 2024-01-02 |
| 2        | 2           | 300          | 2024-01-05 |
| 3        | 1           | 700          | 2024-02-01 |
| 4        | 3           | 1200         | 2024-02-10 |
| 5        | 2           | 450          | 2024-03-02 |

---

# 5️⃣ Types of Subqueries

There are **3 main types**.

| Type       | Returns                | Usage        |
| ---------- | ---------------------- | ------------ |
| Single-row | One value              | =, >, <      |
| Multi-row  | Multiple values        | IN, ANY, ALL |
| Correlated | Depends on outer query | EXISTS       |

---

# 6️⃣ Single Row Subquery

### Definition

Returns **only one row and one column**.

Usually used with:

```
=
>
<
>=
<=
```

---

### Example

Find the **customer who placed the highest order**.

```sql
SELECT name
FROM customers
WHERE customer_id =
(
SELECT customer_id
FROM orders
ORDER BY total_amount DESC
LIMIT 1
);
```

---

### Execution Flow

```
Step 1 (Subquery runs first)

SELECT customer_id
FROM orders
ORDER BY total_amount DESC
LIMIT 1

Result → 1

Step 2 (Outer query runs)

SELECT name
FROM customers
WHERE customer_id = 1

Result → Alice
```

---

# 7️⃣ Multi Row Subquery

### Definition

Returns **multiple rows**.

Used with operators like:

```
IN
ANY
ALL
```

---

### Example

Find customers who **placed orders**.

```sql
SELECT name
FROM customers
WHERE customer_id IN
(
SELECT customer_id
FROM orders
);
```

---

### Execution Flow

Subquery result

| customer_id |
| ----------- |
| 1           |
| 2           |
| 3           |

Outer query checks:

```
customer_id IN (1,2,3)
```

Result:

| name    |
| ------- |
| Alice   |
| Bob     |
| Charlie |

---

### Example 2

Find customers **who never placed orders**

```sql
SELECT name
FROM customers
WHERE customer_id NOT IN
(
SELECT customer_id
FROM orders
);
```

Result:

David
Eva

---

# 8️⃣ Correlated Subquery

### Definition

A **correlated subquery depends on the outer query**.

It runs **once for every row of the outer query**.

---

### Layman Explanation

Imagine asking:

> For every customer → check if they placed an order greater than ₹1000

So the query runs **for each customer**.

---

### Example

```sql
SELECT name
FROM customers c
WHERE EXISTS
(
SELECT *
FROM orders o
WHERE o.customer_id = c.customer_id
AND o.total_amount > 1000
);
```

---

### Execution Logic

```
Check Alice
   ↳ any order > 1000? YES

Check Bob
   ↳ any order > 1000? NO

Check Charlie
   ↳ any order > 1000? YES
```

Result

Alice
Charlie

---

# 9️⃣ Subquery in SELECT Clause

Subquery can also appear in **SELECT**.

Example: total spent by each customer.

```sql
SELECT name,
(
SELECT SUM(total_amount)
FROM orders
WHERE orders.customer_id = customers.customer_id
) AS total_spent
FROM customers;
```

---

Result

| name    | total_spent |
| ------- | ----------- |
| Alice   | 2200        |
| Bob     | 750         |
| Charlie | 1200        |
| David   | NULL        |
| Eva     | NULL        |

---

# 🔟 Subquery in FROM Clause

Subquery can act as a **temporary table**.

Example:

```sql
SELECT customer_id, total_spent
FROM
(
SELECT customer_id, SUM(total_amount) AS total_spent
FROM orders
GROUP BY customer_id
) AS spending;
```

---

# 1️⃣1️⃣ Subquery vs JOIN

Students often confuse this.

| Subquery           | JOIN                   |
| ------------------ | ---------------------- |
| Query inside query | Combine tables         |
| Good for filtering | Good for relationships |
| Sometimes slower   | Usually faster         |

---

Example using JOIN

```sql
SELECT c.name,o.total_amount
FROM customers c
JOIN orders o
ON c.customer_id = o.customer_id;
```

---

# 1️⃣2️⃣ Advantages of Subqueries

✔ Easy to understand
✔ Good for complex filtering
✔ Useful in nested calculations

---

# 1️⃣3️⃣ Disadvantages

❌ Can be slower than joins
❌ Harder to debug if deeply nested

---

# 1️⃣4️⃣ Common Mistakes Students Make

### Mistake 1

Subquery returning multiple rows with `=`.

❌ Wrong

```sql
WHERE customer_id =
(
SELECT customer_id FROM orders
)
```

✔ Correct

```sql
WHERE customer_id IN
(
SELECT customer_id FROM orders
)
```

---

### Mistake 2

Forgetting parentheses

Subqueries **must be inside `()`**

---

---

# 🧠 Final Summary

| Concept            | Meaning                    |
| ------------------ | -------------------------- |
| Subquery           | Query inside another query |
| Single row         | Returns one value          |
| Multi row          | Returns multiple values    |
| Correlated         | Runs once per outer row    |
| Subquery in SELECT | Used to calculate column   |
| Subquery in FROM   | Acts as temporary table    |

---

