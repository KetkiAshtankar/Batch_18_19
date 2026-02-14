
# 🟣 Introduction to Python OOPS

## 🔹 What is OOPS?

OOPS = **Object Oriented Programming System**

It is a way of writing code using:

* Real-world objects
* Properties (data)
* Behavior (functions)



## 🏠 Real Life Analogy

Think about a **Car**

A car has:

* Color
* Brand
* Speed

And it can:

* Start()
* Stop()
* Accelerate()

So:

| Real Life       | Programming |
| --------------- | ----------- |
| Car             | Class       |
| My Honda City   | Object      |
| Color, Brand    | Variables   |
| Start(), Stop() | Methods     |

---

## 🔹 Why OOPS?

✔ Organizes code
✔ Reusable
✔ Scalable
✔ Easy to maintain

In automation frameworks → OOPS is heavily used.

---

# 🟣 Classes & Objects

## 🔹 Class

A class is a **blueprint**.

Like a house blueprint — it defines structure but is not a real house.

```python
class Car:
    def __init__(self, brand, color):
        self.brand = brand
        self.color = color
```

---

## 🔹 Object

An object is a **real instance of class**.

```python
car1 = Car("Honda", "Red")
car2 = Car("BMW", "Black")
```

Now:

* car1 and car2 are objects
* They have real values

---

# 🟣 Python Method Types

There are 3 types of methods:

1️⃣ Instance Method
2️⃣ Class Method
3️⃣ Static Method

---

# 🟢 1. Instance Method

## 🔹 What is it?

* Works with object data
* Uses `self`
* Most commonly used

### Analogy:

Each student has their own marks.

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def display(self):
        print(self.name, self.marks)
```

`display()` is instance method.

✔ Works on object data
✔ Needs object to call

---

# 🟢 2. Class Method

## 🔹 What is it?

* Works with class-level data
* Uses `cls`
* Uses decorator `@classmethod`

### Analogy:

School name is same for all students.

```python
class Student:
    school_name = "ABC School"

    @classmethod
    def change_school(cls, name):
        cls.school_name = name
```

✔ Affects entire class
✔ Not specific to one object

---

# 🟢 3. Static Method

## 🔹 What is it?

* Does not use `self`
* Does not use `cls`
* Just utility method
* Uses `@staticmethod`

### Analogy:

Calculator inside school — doesn't depend on student or school.

```python
class MathUtility:

    @staticmethod
    def add(a, b):
        return a + b
```

✔ Independent logic
✔ Used for helper functions

---

# 🟣 Inheritance

## 🔹 What is Inheritance?

Child class reuses parent class properties.

### Analogy:

Child inherits father's property.

```python
class Vehicle:
    def start(self):
        print("Vehicle started")

class Car(Vehicle):
    def drive(self):
        print("Car driving")
```

Car gets `start()` automatically.

✔ Code reuse
✔ Clean architecture

---

# 🟣 Multiple Inheritance

One child inherits from multiple parents.

### Analogy:

Child inherits qualities from both mother and father.

```python
class Father:
    def skill1(self):
        print("Driving")

class Mother:
    def skill2(self):
        print("Cooking")

class Child(Father, Mother):
    pass
```

Child can use both methods.



---

---

# 🟣 MINI-PROJECT 1: Uber Price Calculation App 🚕

## 🎯 Goal:

Calculate ride price based on:

* Distance
* Base fare
* Surge multiplier

---

## 🔹 Real Logic

Uber price =
Base Fare + (Distance × Rate per km) × Surge

---

## 🧠 OOPS Design

### Class: Ride

```python
class Ride:
    base_fare = 50

    def __init__(self, distance, rate, surge):
        self.distance = distance
        self.rate = rate
        self.surge = surge

    def calculate_price(self):
        return Ride.base_fare + (self.distance * self.rate) * self.surge
```

---

### Usage

```python
r1 = Ride(10, 12, 1.5)
print(r1.calculate_price())
```

---

## Concepts Used:

✔ Class
✔ Instance method
✔ Class variable
✔ Object

---

# 🟣 MINI-PROJECT 2: Restaurant Ordering System 🍽

## 🎯 Goal:

Customer orders food → calculate bill → apply tax

---

## 🧠 Design

### Class: MenuItem

```python
class MenuItem:
    def __init__(self, name, price):
        self.name = name
        self.price = price
```

---

### Class: Order

```python
class Order:
    tax = 0.05

    def __init__(self):
        self.items = []

    def add_item(self, item):
        self.items.append(item)

    def calculate_total(self):
        total = sum(item.price for item in self.items)
        return total + total * Order.tax
```

---

### Usage

```python
burger = MenuItem("Burger", 120)
pizza = MenuItem("Pizza", 200)

order = Order()
order.add_item(burger)
order.add_item(pizza)

print(order.calculate_total())
```

---

## Concepts Used:

✔ Classes
✔ Objects
✔ Instance methods
✔ Class variable (tax)
✔ Encapsulation
✔ Aggregation

---

# 🟣 Quick Revision Summary

| Concept              | Easy Meaning             |
| -------------------- | ------------------------ |
| Class                | Blueprint                |
| Object               | Real instance            |
| Instance Method      | Works on object          |
| Class Method         | Works on class           |
| Static Method        | Utility method           |
| Inheritance          | Code reuse               |
| Multiple Inheritance | Multiple parents         |
| Operator Overloading | Custom operator behavior |

---
