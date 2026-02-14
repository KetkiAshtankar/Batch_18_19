---

# 1️⃣ Lambda Function

## 🧠 Simple Meaning

A **lambda function** is a small, anonymous (no-name) function written in one line.

---

## 🏠 Analogy

Normal function is like:

> A full kitchen where you cook properly.

Lambda is like:

> Making instant Maggi 🍜 — quick and small.

---

## 🧾 Syntax

```python
lambda arguments: expression
```

---

## 🔹 Example

Normal function:

```python
def square(x):
    return x * x
```

Lambda version:

```python
square = lambda x: x * x
```

---

## 🔹 Where Used?

Mostly used with:

* `map()`
* `filter()`
* `sorted()`
* `reduce()`

---

## ⚠️ Important

* Only one expression allowed.
* Automatically returns value.
* No multiple lines.

---

# 2️⃣ Map Function & Filter Function

---

# 🔹 Map Function

## 🧠 Meaning

Applies a function to **every item** in a collection.

---

## 🏠 Analogy

Imagine:
You have 5 shirts 👕
You send all to ironing machine.

Machine applies same process to all.

That’s `map()`.

---

## 🧾 Syntax

```python
map(function, iterable)
```

---

## 🔹 Example

```python
numbers = [1, 2, 3, 4]

squares = list(map(lambda x: x*x, numbers))
```

Output:

```
[1, 4, 9, 16]
```

---

# 🔹 Filter Function

## 🧠 Meaning

Selects items based on condition.

---

## 🏠 Analogy

Security guard 🚨
Only people above 18 allowed inside.

That’s `filter()`.

---

## 🧾 Syntax

```python
filter(function, iterable)
```

---

## 🔹 Example

```python
numbers = [1, 2, 3, 4, 5]

evens = list(filter(lambda x: x % 2 == 0, numbers))
```

Output:

```
[2, 4]
```

---

# 🔥 Difference Between Map & Filter

| Map                 | Filter                |
| ------------------- | --------------------- |
| Modifies every item | Selects some items    |
| Transformation      | Selection             |
| Output same size    | Output may be smaller |

---

# 3️⃣ Iterator

---

## 🧠 Meaning

An iterator is an object that allows you to go through items one by one.

---

## 🏠 Analogy

TV remote 📺

Each time you press next → you go to next channel.

Iterator works same way.

---

## 🔹 Example

```python
numbers = [10, 20, 30]

it = iter(numbers)

print(next(it))  # 10
print(next(it))  # 20
print(next(it))  # 30
```

---

## 🔹 Important Concepts

* `iter()` → converts iterable to iterator
* `next()` → gives next value
* Raises `StopIteration` when finished

---

## 🧠 Iterable vs Iterator

| Iterable            | Iterator                  |
| ------------------- | ------------------------- |
| List, Tuple, String | Object returned by iter() |
| Can loop over it    | Gives one value at a time |

---

# 4️⃣ Generator

---

## 🧠 Meaning

A generator is a special type of iterator created using `yield`.

---

## 🏠 Analogy

Water tank 🚰

Instead of filling 100 buckets at once,
you open tap and water comes when needed.

Generator produces values **on demand**.

---

## 🔹 Why Important?

Saves memory.

Normal function stores all values.
Generator produces one at a time.

---

## 🔹 Example

```python
def count_up_to(n):
    for i in range(n):
        yield i
```

Using it:

```python
gen = count_up_to(3)

print(next(gen))  # 0
print(next(gen))  # 1
print(next(gen))  # 2
```

---

## 🔥 Generator vs Normal Function

| Normal Function   | Generator              |
| ----------------- | ---------------------- |
| Uses return       | Uses yield             |
| Stores all values | Produces one at a time |
| Uses more memory  | Memory efficient       |

---

# 5️⃣ Decorators

---

## 🧠 Meaning

A decorator is a function that modifies another function’s behavior.

---

## 🏠 Analogy

Gift wrapping 🎁

Original gift = function
Wrapper = decorator

Gift remains same, but presentation changes.

---

## 🔹 Example

```python
def decorator_func(original_func):
    def wrapper():
        print("Before function runs")
        original_func()
        print("After function runs")
    return wrapper
```

Usage:

```python
@decorator_func
def say_hello():
    print("Hello!")
```

Output:

```
Before function runs
Hello!
After function runs
```

---

## 🔥 Why Used?

* Logging
* Authentication
* Timing functions
* Access control
* Retry mechanism



---

# 6️⃣ Introduction to Regex (Regular Expressions)

---

## 🧠 Meaning

Regex is used to match patterns in text.

---

## 🏠 Analogy

Think of it like a **search template** 🔍

Instead of searching exact word,
you search pattern.

Example:

* All emails
* All numbers
* All dates

---

## 🔹 Import

```python
import re
```

---

## 🔹 Example 1 – Find Numbers

```python
import re

text = "My number is 9876543210"
result = re.findall(r"\d+", text)

print(result)
```

Output:

```
['9876543210']
```

---

## 🔹 Common Regex Symbols

| Symbol | Meaning        |
| ------ | -------------- |
| `\d`   | Digit          |
| `\w`   | Word character |
| `.`    | Any character  |
| `+`    | One or more    |
| `*`    | Zero or more   |
| `^`    | Starts with    |
| `$`    | Ends with      |

---

## 🔹 Example – Email Pattern

```python
pattern = r"\w+@\w+\.\w+"
```

Matches:

```
abc@gmail.com
```

---

# 🧠 Final Big Picture

| Concept   | Core Idea                       |
| --------- | ------------------------------- |
| Lambda    | Small one-line function         |
| Map       | Apply function to all items     |
| Filter    | Select items based on condition |
| Iterator  | Go one-by-one                   |
| Generator | Memory-efficient iterator       |
| Decorator | Modify function behavior        |
| Regex     | Pattern matching in text        |

---
