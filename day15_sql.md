
---

## **Introduction to MySQL**

MySQL is a popular open-source relational database management system (RDBMS) used to store and manage structured data. It supports SQL (Structured Query Language) for querying and managing databases.

---

## **Basic MySQL Commands with CRUD Operations**

CRUD stands for **Create, Read, Update, Delete**, which are the fundamental operations performed on a database.

---

### **1. Creating a Database and Using It**

```sql
CREATE DATABASE school;
USE school;
```

**Explanation:**

* `CREATE DATABASE school;` → Creates a new database named **school**.
* `USE school;` → Switches to the **school** database to perform operations.

---

### **2. Creating a Table**

```sql
CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    age INT,
    grade VARCHAR(10)
);
```

**Explanation:**

* `id INT PRIMARY KEY AUTO_INCREMENT` → Unique identifier for each student (increments automatically).
* `name VARCHAR(50)` → Stores student names (up to 50 characters).
* `age INT` → Stores the student's age.
* `grade VARCHAR(10)` → Stores the grade (e.g., "A", "B", "C").

---

### **3. Inserting Data (CREATE)**

```sql
INSERT INTO students (name, age, grade) VALUES ('Alice', 14, 'A');
INSERT INTO students (name, age, grade) VALUES ('Bob', 15, 'B');
INSERT INTO students (name, age, grade) VALUES ('Charlie', 16, 'A');
```

**Explanation:**

* `INSERT INTO students (name, age, grade) VALUES (...);` → Adds a new record to the table.

---

### **4. Retrieving Data (READ)**

```sql
SELECT * FROM students;
```

**Explanation:**

* `SELECT * FROM students;` → Retrieves all records from the **students** table.

#### **Filtering Results**

```sql
SELECT name, grade FROM students WHERE grade = 'A';
```

**Explanation:**

* Retrieves only **name** and **grade** where the grade is **'A'**.

---

### **5. Updating Data (UPDATE)**

```sql
UPDATE students SET grade = 'A+' WHERE name = 'Bob';
```

**Explanation:**

* `UPDATE students` → Updates records in the **students** table.
* `SET grade = 'A+'` → Changes the grade to **'A+'**.
* `WHERE name = 'Bob'` → Applies the change only to Bob.

---

### **6. Deleting Data (DELETE)**

```sql
DELETE FROM students WHERE name = 'Charlie';
```

**Explanation:**

* `DELETE FROM students` → Removes records from the **students** table.
* `WHERE name = 'Charlie'` → Deletes only **Charlie’s** record.
* If you remove `WHERE`, all rows will be deleted (but table remains).

---

### **7. Truncating a Table (TRUNCATE)**

```sql
TRUNCATE TABLE students;
```

**Explanation:**

* `TRUNCATE TABLE students;` → Removes **all rows** from the table instantly.
* Faster than DELETE.
* Cannot use `WHERE`.
* Resets `AUTO_INCREMENT` back to 1.
* Table structure remains.

👉 Difference from DELETE:

* `DELETE` removes rows one by one.
* `TRUNCATE` removes all rows at once.

---

### **8. Dropping a Table or Database**

```sql
DROP TABLE students;
DROP DATABASE school;
```

**Explanation:**

* `DROP TABLE students;` → Deletes the **students** table structure and its data permanently.
* `DROP DATABASE school;` → Deletes the **school** database permanently.

---
