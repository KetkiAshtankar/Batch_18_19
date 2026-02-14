
---

# 📘 1️⃣ Functions

## 🧠 What is a Function?

### 🔹 Simple Meaning:

A function is a **reusable block of code** that performs a specific task.

---

## 🏠 Analogy: Kitchen Recipe

Think of a function like a **recipe**.

* Recipe name → Function name
* Ingredients → Parameters
* Cooking steps → Function body
* Final dish → Return value

You don’t rewrite the recipe every time.
You just call it.

---

## 🔹 Syntax

```python
def function_name(parameters):
    # code
    return value
```

---

## 🔹 Example

```python
def greet(name):
    return f"Hello {name}"
```

Calling it:

```python
print(greet("Ketki"))
```

---

## 🔹 Key Concepts

| Term           | Meaning                     |
| -------------- | --------------------------- |
| `def`          | Keyword to define function  |
| Parameter      | Input variable              |
| Argument       | Actual value passed         |
| `return`       | Sends value back            |
| Local variable | Exists only inside function |

---

## 🎯 Why Functions?

✔ Code reuse
✔ Better readability
✔ Easy debugging
✔ Modular programming

---

# 📘 2️⃣ Closure Functions

## 🧠 What is a Closure?

A **closure** is a function inside another function that remembers the outer function’s variables — even after the outer function has finished executing.

---

## 🏠 Analogy: Backpack Memory

Imagine:

You pack snacks in a backpack (outer function variable).
Then you give the backpack to your friend (inner function).

Even after you leave, your friend still has the snacks.

That “remembering” is closure.

---

## 🔹 Example

```python
def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function
```

Now:

```python
add_10 = outer_function(10)
print(add_10(5))   # 15
```

### What happened?

* `x = 10` is remembered.
* Even though `outer_function` finished,
* `inner_function` still remembers `x`.

That memory = **Closure**

---

## 🔍 Technical Definition

A closure:

* Is a nested function
* Captures variables from outer scope
* Retains them even after outer function ends

---

## 🎯 Why Use Closures?

✔ Data hiding
✔ Creating customized functions
✔ Functional programming
✔ Avoid global variables

---

# 📘 3️⃣ Callback Function

## 🧠 What is a Callback?

A **callback function** is a function that is passed as an argument to another function, and then called inside that function.

---

## 🏠 Analogy: Ordering Food

You order pizza and give your phone number.

When pizza is ready → restaurant calls you.

Your phone number = callback
Restaurant = main function

---

## 🔹 Example

```python
def greet(name):
    return f"Hello {name}"

def process_user(callback_function):
    print(callback_function("Ketki"))
```

Call:

```python
process_user(greet)
```

---

## 🔹 Real-Life Example in Python

```python
numbers = [1, 2, 3, 4]

squares = list(map(lambda x: x*x, numbers))
```

Here:

* `lambda x: x*x` → callback
* `map()` → main function

---

## 🎯 Why Use Callbacks?

✔ Flexible code
✔ Event handling
✔ Async programming
✔ Used in automation frameworks

---

# 📘 4️⃣ File Handling

## 🧠 What is File Handling?

File handling means:
Reading from or writing to files stored on the system.

---

## 🏠 Analogy: Notebook

Think of a file like a notebook.

* Open notebook
* Write something
* Read something
* Close notebook

Same in Python.

---

## 🔹 Basic Syntax

```python
file = open("filename.txt", "mode")
```

---

## 🔹 File Modes

| Mode | Meaning            |
| ---- | ------------------ |
| `r`  | Read               |
| `w`  | Write (overwrites) |
| `a`  | Append             |
| `r+` | Read + Write       |

---

## 🔹 Writing to File

```python
file = open("data.txt", "w")
file.write("Hello World")
file.close()
```

---

## 🔹 Reading from File

```python
file = open("data.txt", "r")
content = file.read()
print(content)
file.close()
```

---

## 🔹 Best Practice (Using `with`)

```python
with open("data.txt", "r") as file:
    content = file.read()
    print(content)
```

✔ Automatically closes file
✔ Cleaner code
✔ Prevents memory leaks

---

## 🔍 Important File Methods

| Method        | Purpose                |
| ------------- | ---------------------- |
| `read()`      | Read full file         |
| `readline()`  | Read one line          |
| `readlines()` | Read all lines in list |
| `write()`     | Write text             |
| `close()`     | Close file             |

---

## 🎯 Why File Handling is Important?

✔ Log storage
✔ Test reports
✔ Reading test data (CSV, JSON)
✔ Saving outputs

---

# 🧠 Quick Comparison Summary

| Concept       | Core Idea                           |
| ------------- | ----------------------------------- |
| Function      | Reusable block of code              |
| Closure       | Function remembering outer variable |
| Callback      | Function passed to another function |
| File Handling | Reading/writing data to files       |

---
