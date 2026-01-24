# Python Introduction

---

## 1. Variables & Data Types

### What is a Variable?

**Technical:**
A variable is a named reference to a value stored in memory. Python variables are dynamically typed, meaning the type is decided at runtime.

---

# 📌 Rules of Variables in Python

## 🔹 What is a Variable?

A **variable** is a name given to a value so that we can **store, use, and change data** in a program.

### 🧠  Example:

Think of a variable as a **labeled box**:

* The **label** is the variable name
* The **item inside** is the value

```python
age = 25
```

Here:

* `age` → box name
* `25` → value inside the box

---

## 🔹 Rule 1: Variable name must start with a letter or underscore (_)

### ✅ Valid:

```python
name = "Ketki"
_age = 30
city1 = "Mumbai"
```

### ❌ Invalid:

```python
1name = "Ketki"   # starts with number ❌
@age = 25         # special character ❌
```

### 🧠 :

A variable name is like a **person’s name** — it cannot start with a number or symbol.

---

## 🔹 Rule 2: Variable name cannot start with a number

### ❌ Wrong:

```python
2marks = 90
```

### ✅ Correct:

```python
marks2 = 90
```

### 🧠 :

You don’t call someone **“2Ravi”** — same logic here 😉

---

## 🔹 Rule 3: No spaces allowed in variable names

### ❌ Wrong:

```python
first name = "Ketki"
```

### ✅ Correct:

```python
first_name = "Ketki"
firstname = "Ketki"
```

### 🧠 :

Python reads space as **end of a word**, so it gets confused.

---

## 🔹 Rule 4: Variable names are Case-Sensitive

```python
age = 20
Age = 30
```

✔ These are **two different variables**

### 🧠 :

Python treats **age**, **Age**, and **AGE** like **three different people**.

---

## 🔹 Rule 5: Variable name cannot be a Python keyword

### ❌ Wrong:

```python
if = 10
while = 5
class = "Python"
```

### ✅ Correct:

```python
if_value = 10
while_count = 5
class_name = "Python"
```

### 🧠 :

Keywords are **reserved words** in Python — like “VIP seats”, you can’t use them 😄

---

## 🔹 Rule 6: Use meaningful variable names (Best Practice)

### ❌ Bad:

```python
x = 5000
```

### ✅ Good:

```python
salary = 5000
```

### 🧠 :

Good names make code **self-explanatory**, like good handwriting ✨

---

## 🔹 Rule 7: Variable value can be changed (Overwritten)

```python
message = "Python"
print(message)

message = "Hi"
print(message)
```

### 🧠 Output:

```
Python
Hi
```

### 🧠 :

You reused the **same box** and put a **new item** inside — old one is gone.

---

## 🔹 Rule 8: Same variable can store different data types

```python
data = 10
data = 10.5
data = "Python"
```

### 🧠 :

The box doesn’t care what you put inside — number, decimal, or text.

---

## 🔹 Rule 9: Variables must be assigned before use

### ❌ Wrong:

```python
print(score)
```

### ✅ Correct:

```python
score = 90
print(score)
```

### 🧠 :

You can’t use a box **before putting something inside it**.

---

## 🔹 Rule 10: Use snake_case (Python Naming Convention)

```python
student_name = "Ketki"
total_marks = 95
```


---

## 🔹 Summary Table (Good for Revision)

| Rule                 | Example             |
| -------------------- | ------------------- |
| Starts with letter/_ | `name`, `_age`      |
| No numbers at start  | ❌ `1name`           |
| No spaces            | ❌ `first name`      |
| Case-sensitive       | `age` ≠ `Age`       |
| No keywords          | ❌ `if`, `while`     |
| Meaningful names     | `salary` ✔          |
| Value can change     | Overwriting allowed |
| Assign before use    | No empty variables  |

---


```python
name = "Python"
age = 25
price = 99.99
is_active = True
```
---
### Explanation:
A variable is like a **labeled box**. You put something inside it and give it a name so you can use it later.

---

### Common Data Types

| Data Type | Meaning         | Example |
| --------- | --------------- | ------- |
| int       | Whole numbers   | `10`    |
| float     | Decimal numbers | `10.5`  |
| str       | Text            | "Hello" |
| bool      | True/False      | True    |

To check the type of data types, Use following:
```python
print(type(age))
```

---

## 2. Introduction to Python Operators

### Arithmetic Operators

Used to perform mathematical calculations.

```python
print(10 + 5)   # Addition
print(10 - 5)   # Subtraction
print(10 * 5)   # Multiplication
print(10 / 5)   # Division
print(10 % 3)   # Remainder
print(10 // 3)  # Floor Division
print(2 ** 3)   # Power
```

**:** Operators are like buttons on a calculator.

---

### Comparison Operators

Compare two values and return True or False.

```python
print(5 > 3)
print(5 == 3)
print(5 != 3)
```

**:** Like asking yes/no questions.

---

### Logical Operators

---

## 🔹 Logical Operators with Truth Table

Logical operators work on **True / False** values and give a **final decision**.

---

## 1️⃣ `and` Operator

👉 **All conditions must be True**

### Truth Table – `and`

| Condition A | Condition B | A and B  |
| ----------- | ----------- | -------- |
| True        | True        | **True** |
| True        | False       | False    |
| False       | True        | False    |
| False       | False       | False    |

### Code Example

```python
print(True and True)    # True
print(True and False)   # False
```

🧠 **:**
You pass the exam **only if** theory **AND** practical are passed.

---

## 2️⃣ `or` Operator

👉 **Any one condition can be True**

### Truth Table – `or`

| Condition A | Condition B | A or B   |
| ----------- | ----------- | -------- |
| True        | True        | **True** |
| True        | False       | **True** |
| False       | True        | **True** |
| False       | False       | False    |

### Code Example

```python
print(True or False)   # True
print(False or False) # False
```

🧠 **:**
If today is **Saturday OR Sunday**, it’s a holiday.

---

## 3️⃣ `not` Operator

👉 **Reverses the result**

### Truth Table – `not`

| Condition | not Condition |
| --------- | ------------- |
| True      | False         |
| False     | **True**      |

### Code Example

```python
print(not True)   # False
print(not False)  # True
```

🧠 **:**
If it is **NOT raining**, no umbrella needed ☀️

---

## 📌 Super-Easy Summary 

* `and` → **All true**
* `or` → **Any one true**
* `not` → **Opposite**

---


```python
print(5 > 3 and 3 > 1)
print(5 > 10 or 3 > 1)
print(not(5 > 3))
```

**:** Used when making decisions involving multiple rules.

---

## 3. String Manipulations

### What is a String?

A string is a sequence of characters enclosed in quotes.

```python
text = "Python"
name = 'Sri'
```

Strings are **immutable** → once created, they cannot be changed.

---

## 🔹 String Indexing

Each character in a string has a position called an **index**.

### ✅ Positive Indexing

Starts from **0** (left to right)

```python
text = "Python"
print(text[0])   # P
print(text[3])   # h
```

Index positions:

```
P  y  t  h  o  n
0  1  2  3  4  5
```

---

### ✅ Negative Indexing

Starts from **-1** (right to left)

```python
print(text[-1])  # n
print(text[-3])  # h
```

Index positions:

```
P   y   t   h   o   n
-6  -5  -4  -3  -2  -1
```

---

## 🔹 String Slicing

Slicing is used to extract part of a string.

### 📌 Syntax

```python
string[start : stop : step]
```

⚠️ `stop` index is **not included**.

---

### ✅ Positive Slicing Examples

```python
text = "Python"
print(text[0:3])   # Pyt
print(text[2:5])   # tho
print(text[:4])    # Pyth
print(text[2:])    # thon
```

---

### ✅ Negative Slicing Examples

```python
print(text[-4:-1])  # tho
print(text[-5:-2])  # yth
```

---

### ✅ Reverse String Using Slice

```python
print(text[::-1])   # nohtyP
```

---

### ❌ Why this gives blank output?

```python
print(text[-1:-5])
```

Because:

* Default step is `+1`
* Start index must be smaller than stop index

✔ Correct way:

```python
print(text[-1:-5:-1])
```

---

## 🔹 String Concatenation (+)

Used to **join strings**.

```python
first = "Hello"
second = "World"
print(first + " " + second)
```

Output:

```
Hello World
```

---

## 🔹 String Repetition (*)

Used to repeat a string.

```python
print("Hi " * 3)
```

Output:

```
Hi Hi Hi
```

---

## 🔹 Common String Methods

| Method      | Use                    |
| ----------- | ---------------------- |
| `lower()`   | Convert to lowercase   |
| `upper()`   | Convert to uppercase   |
| `strip()`   | Remove extra spaces    |
| `replace()` | Replace text           |
| `split()`   | Convert string to list |

---

### Examples

```python
text = "  Python Language  "

print(text.lower())
print(text.upper())
print(text.strip())
print(text.replace("Python", "Java"))
print(len(text))
```

---

## 🔹 Looping Through a String

```python
name = "Sri"

for ch in name:
    print(ch)
```

---

## 🔹 Reverse String Using Loop

```python
name = "Sri"

for i in range(-1, -len(name)-1, -1):
    print(name[i], end="")
```

---

## 🔹 String Comparison

```python
if "python" == "Python":
    print("Same")
else:
    print("Not Same")
```

---

## 🔹 Masking Example (Aadhar-like)

```python
aadhar = "123456789012"
masked = "XXXX-XXXX-" + aadhar[-4:]
print(masked)
```

---

## ⚠️ Important Rules

* Strings are immutable
* Index starts from 0
* Stop index is excluded in slicing
* Negative step means reverse direction

---


**String manipulation allows us to access, modify, and process text using indexing, slicing, loops, and built-in methods.**

---

## 4. Conditions (if-else)

### What are Conditions?

Conditions allow programs to make decisions.

```python
age = int(input("Enter age: "))

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

**:** If situation A happens, do X; otherwise, do Y.

---

### Real-life Example

```python
raining = "yes"

if raining == "yes":
    print("Take umbrella")
else:
    print("Enjoy sunshine")
```

---

## 5. Loops

### For Loop

Used when the number of repetitions is known.

```python
for i in range(1, 6):
    print("Python", i)
```

**:** Do something a fixed number of times.

---

### While Loop

Used when repetition depends on a condition.

```python
count = 1
while count <= 3:
    print("Learning loops")
    count += 1
```

**:** Repeat until a condition changes.

---

## 6. Nested Loops

A loop inside another loop.

```python
for i in range(1, 4):
    for j in range(1, 4):
        print(i, j)
```

**Technical Flow:**

* Outer loop controls rows
* Inner loop controls columns

**:** For each row, go through all columns.

---

## 7. GAME: examples 🎮

---

# 🎮 1️⃣ Reverse Scrambled Word Game

### 🔹 Game Logic

1. A word is scrambled
2. User must **reverse the scrambled word**
3. If reversed word matches original → WIN

---

## ✅ Easy Python Code

```python
import random

word = "python"

scrambled = "".join(random.sample(word, len(word)))
print("Scrambled word:", scrambled)

reverse_guess = input("Reverse the scrambled word: ").strip().lower()

if reverse_guess == scrambled[::-1]:
    print("🎉 Correct! You reversed it right.")
else:
    print("❌ Wrong!")
    print("Correct reverse is:", scrambled[::-1])
```

---

### 🧠 Concepts Used

* String slicing `[::-1]`
* Random shuffle
* Input + condition

---

### 🔍 Sample Run

```
Scrambled word: nhtopy
Reverse the scrambled word: ytopth
🎉 Correct! You reversed it right.
```

---

# 🎲 2️⃣ Guess the Dice Game (Very Easy)

### 🔹 Game Logic

* Dice rolls a number (1 to 6)
* User guesses the number
* Check win or lose

---

## ✅ Easy Python Code

```python
import random

dice = random.randint(1, 6)

guess = int(input("Guess the dice number (1 to 6): "))

if guess == dice:
    print("🎉 You Win! Dice was:", dice)
else:
    print("❌ You Lose! Dice was:", dice)
```

---

### 🔍 Sample Run

```
Guess the dice number (1 to 6): 4
❌ You Lose! Dice was: 2
```

---

## 🧠  Explanation 

* Dice = random number
* User guesses
* Match → win
* No match → lose

---

# ⭐ Bonus: Dice Game with 3 Attempts (Optional)

```python
import random

dice = random.randint(1, 6)
attempts = 3

while attempts > 0:
    guess = int(input("Guess the dice number (1 to 6): "))

    if guess == dice:
        print("🎉 You Win!")
        break
    else:
        attempts -= 1
        print("Wrong! Attempts left:", attempts)

if attempts == 0:
    print("❌ Game Over! Dice was:", dice)
```

---

## 📌 Concepts Covered 

| Game             | Concepts         |
| ---------------- | ---------------- |
| Reverse Scramble | slicing, strings |
| Dice Guess       | random, if-else  |
| Attempts         | while loop       |

---

