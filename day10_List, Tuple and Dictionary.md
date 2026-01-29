# Python Collections

---

## 1. Lists

### Concept ( Terms)

A **list** is like a **shopping bag** 🛍️ where you can store many items together. You can add, remove, or change items anytime.

### Key Features

* Ordered (index starts from 0)
* Mutable (values can be changed)
* Allows duplicate elements

### Example

```python
fruits = ['apple', 'banana', 'cherry']
print(fruits)
```

### Accessing Elements

```python
print(fruits[1])  # banana
```

### Modifying Elements

```python
fruits[2] = 'mango'
```

### Common Built-in Functions

* append(), extend(), insert()
* remove(), pop(), clear()
* index(), count()
* sort(), reverse()

### One-line Summary

A list is an ordered, changeable collection that allows duplicates.

---

## 2. Tuples

### Concept ( Terms)

A **tuple** is like a **locked diary** 🔒📔. You can read what is written but cannot change it.

### Key Features

* Ordered
* Immutable (cannot be changed after creation)
* Allows duplicate elements

### Example

```python
dimensions = (10, 20, 30)
print(dimensions)
```

### Accessing Elements

```python
print(dimensions[1])  # 20
```

### Trying to Modify (Error)

```python
dimensions[1] = 40  # TypeError
```

### Built-in Functions

* count()
* index()

### Duplicate Example

```python
marks = (90, 85, 90, 70)
marks.index(90)       # First occurrence
marks.index(90, 1)    # Second occurrence
```

### One-line Summary

A tuple is an ordered, unchangeable collection that allows duplicates.

---

## 3. Checking Duplicates (List / Tuple)

### Method 1: Using set()

```python
if len(data) != len(set(data)):
    print("Duplicates found")
```

### Method 2: Using count()

```python
for item in data:
    if data.count(item) > 1:
        print(item, "is duplicated")
```

### Method 3: Nested Loop (Logic Based)

```python
for i in range(len(data)):
    for j in range(i+1, len(data)):
        if data[i] == data[j]:
            print("Duplicate found:", data[i])
```

---

## 4. Dictionaries

### Concept ( Terms)

A **dictionary** is like a **contact book** 📒 where each **key** (name) has a **value** (phone number).

### Key Features

* Stores data as key-value pairs
* Mutable
* Keys are unique, values can be duplicate
* Insertion order is maintained (Python 3.7+)

### Example

```python
person = {'name': 'John', 'age': 25, 'city': 'New York'}
```

### Accessing Values

```python
print(person['name'])
```

### Modifying Values

```python
person['age'] = 26
```

### Adding New Key-Value

```python
person['job'] = 'Engineer'
```

### Built-in Functions

* keys(), values(), items()
* get(), pop(), update(), clear()

### Multiple Values for One Key

```python
student = {
    'name': 'Rahul',
    'subjects': ['Maths', 'Science', 'English']
}
```

### One-line Summary

A dictionary stores data in key-value pairs.

---

## 5. List of Dictionaries

### Example Structure

```python
students = [
    {'name': 'Sanika', 'age': 30, 'role': 'BA', 'salary': '30 lpa'},
    {'name': 'Prathmesh', 'age': 31, 'role': 'SCM', 'salary': '40 lpa'}
]
```

### Accessing Data

```python
students[0]['name']
students[1]['salary']
```

### Modifying Data

```python
students[0]['age'] = 31
```

### Adding New Student

```python
students.append({'name': 'Amit', 'age': 28})
```

### Teaching Rule

List → index → dictionary → key

---

## 6. Sets

### Concept ( Terms)

A **set** is like a bag of **unique items** 🎒. No duplicates allowed.

### Key Features

* Unordered
* Mutable
* No duplicate values

### Example

```python
numbers = {1, 2, 2, 3}
# Output: {1, 2, 3}
```

### Built-in Functions

* add(), remove(), discard(), pop(), clear()

---

## 7. Set Operations (Very Important 🔥)

```python
a = {1, 2, 3}
b = {3, 4, 5}
```

### Union (OR)

```python
a.union(b)   # {1,2,3,4,5}
```

### Intersection (AND)

```python
a.intersection(b)   # {3}
```

### Difference

```python
a.difference(b)   # {1,2}
```

### Operator Symbols

* Union: |
* Intersection: &
* Difference: -

---

## 8. Common Logical Issue (Debugging Example)

### Problem

Code runs but no expected output due to:

* Wrong function name
* Wrong variable name
* Case-sensitive keywords

### Correct Example

```python
movies = ('Inception','Avatar','Titanic','Avatar','Interstellar')
printed = []

for movie in movies:
    if movies.count(movie) > 1 and movie not in printed:
        print(movie, 'is repeated')
        printed.append(movie)
```

---

## Final One-Line Revision

* List → ordered, changeable
* Tuple → ordered, fixed
* Set → unordered, unique
* Dictionary → key-value pairs

---

```

---

STRINGS
```
### Concept (Real-life)

A **string** is text — name, city, message, password.
```
```python
name = "Python"
city = "Mumbai"
```

### Indexing

```python
# P  Y  T  H  O  N
# 0  1  2  3  4  5
print(name[0])  # P
```

### Concatenation (+)

```python
print(name + " is fun")
print(city + " is amazing")
```

### Repetition

```python
print("Hi " * 3)
```

### Slicing (Cutting text 🔪)

```python
text = "Python"
print(text[0:3])   # Pyt
print(text[::-1])  # reverse
```

### Common String Functions

```python
text.upper()
text.lower()
text.replace("Java","Python")
text.strip()
```

---


### Real-life: Shopping list 🛒

```python
fruits = ['apple','banana','cherry']
fruits.append('mango')
fruits.remove('banana')
print(fruits)
```

### Key Features

* Ordered
* Mutable
* Allows duplicates

---

 TUPLES

### Real-life: Fixed data (DOB, GPS 📍)

```python
marks = (90,85,90,70)
print(marks.count(90))
print(marks.index(90,1))
```

### Key Features

* Ordered
* Immutable
* Allows duplicates

---

 DICTIONARIES

### Real-life: Contact book 📒

```python
person = {'name':'John','age':25}
person['age'] = 26
person['city'] = 'Mumbai'
```

### Multiple values for one key

```python
student = {
    'name':'Rahul',
    'subjects':['Maths','English']
}
student['subjects'].append('Computer')
```

---

 LIST OF DICTIONARIES

### Real-life: Student database 🧑‍🎓

```python
students = [
 {'name':'Sanika','age':30},
 {'name':'Prathmesh','age':31}
]

students[0]['age'] = 31
```

---
 SETS 

### Real-life: Unique roll numbers 🆔

```python
nums = {1,2,3,2,1}
print(nums)
```

### Key Features

* No duplicates
* Unordered
* Mutable

---
 FINAL REVISION

* String → text data
* List → changeable collection
* Tuple → fixed collection
* Dictionary → key-value data
* Set → unique values only
