
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


---


Object Oriented Programming (OOP) is a programming style where we organize code using **objects and classes**.

Think of it as **modeling real-world things in code**.

Example:

| Real World   | Programming |
| ------------ | ----------- |
| Car          | Class       |
| My car       | Object      |
| Driving      | Method      |
| Color, Speed | Attributes  |

---

# 1️⃣ Class

### 🧠 Easy Meaning

A **class is a blueprint or template** used to create objects.

### 🏠 Real Life Analogy

Think of a **house blueprint**.

A blueprint tells:

* number of rooms
* kitchen
* windows

But it is **not the real house**.

Similarly:

Class = design
Object = actual thing.

---

### 💻 Example

```python
class Student:
    name = ""
    age = 0
```

This only defines the structure.

---

# 2️⃣ Object

### 🧠 Easy Meaning

An **object is an instance of a class**.

It is the real thing created from the blueprint.

---

### 🏠 Analogy

Blueprint → Class
Actual House → Object

---

### 💻 Example

```python
class Student:
    pass

s1 = Student()
s2 = Student()
```

Here:

* `s1` and `s2` are objects.

---

# 3️⃣ Constructor

### 🧠 Easy Meaning

Constructor automatically runs when object is created.

Used to **initialize object data**.

---

### 🏠 Analogy

When a baby is born:

* Name assigned
* Age starts at 0

Constructor sets **initial values**.

---

### 💻 Example

```python
class Student:

    def __init__(self, name, age):
        self.name = name
        self.age = age
```

Create object:

```python
s1 = Student("Ketki", 30)
```

Constructor runs automatically.

---

# 4️⃣ Instance Method

### 🧠 Easy Meaning

Works on **object data**.

Uses `self`.

---

### 🏠 Analogy

Each person has different salary.

So method uses that person's data.

---

### 💻 Example

```python
class Employee:

    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    def show_salary(self):
        print(self.salary)
```

Here:

`show_salary()` works on specific employee.

---

# 5️⃣ Class Method

### 🧠 Easy Meaning

Works on **class-level data shared by all objects**.

Uses `cls`.

---

### 🏢 Analogy

All employees belong to same company.

If company name changes,
all employees see the change.

---

### 💻 Example

```python
class Employee:

    company = "TCS"

    @classmethod
    def change_company(cls, new_name):
        cls.company = new_name
```

Call:

```python
Employee.change_company("Infosys")
```

---

# 6️⃣ Static Method

### 🧠 Easy Meaning

A method that **does not depend on object or class data**.

Just logically belongs inside class.

---

### 🧮 Analogy

Calculator functions:

* add
* subtract
* multiply

They don’t depend on specific object.

---

### 💻 Example

```python
class Calculator:

    @staticmethod
    def add(a, b):
        return a + b
```

Call:

```python
Calculator.add(5, 3)
```

---

# 7️⃣ Inheritance

### 🧠 Easy Meaning

Child class can **reuse properties of parent class**.

---

### 👨‍👩‍👧 Analogy

Children inherit features from parents.

Example:

* surname
* property
* behavior

---

### 💻 Example

```python
class Animal:

    def eat(self):
        print("Animal eats")

class Dog(Animal):
    pass
```

Dog automatically gets `eat()`.

---

# 8️⃣ Multiple Inheritance

### 🧠 Easy Meaning

Child class inherits from **multiple parent classes**.

---

### 🧑‍🎓 Analogy

A student learns from:

* Math teacher
* Science teacher

Knowledge comes from both.

---

### 💻 Example

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

Child gets both skills.

---

# 9️⃣ Encapsulation

### 🧠 Easy Meaning

Encapsulation means:

👉 Wrapping data and methods together
👉 Restricting access to some data.

---

### 🏦 Analogy

Bank account:

You cannot directly change balance.

You must use:

* deposit
* withdraw

---

### 💻 Example

```python
class BankAccount:

    def __init__(self):
        self.__balance = 5000

    def show_balance(self):
        return self.__balance
```

`__balance` is private.

---

# 🔟 Abstraction

### 🧠 Easy Meaning

Hide complex logic.

Show only important functionality.

---

### 📺 Analogy

TV remote:

You press **Power** button.

You don't see internal circuits.

---

### 💻 Example

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):

    @abstractmethod
    def start(self):
        pass
```

Child must implement:

```python
class Car(Vehicle):

    def start(self):
        print("Car starts")
```

---

# 1️⃣1️⃣ Polymorphism

### 🧠 Easy Meaning

Same method name
Different behavior.

---

### 🔔 Analogy

Sound function:

Dog → Bark
Cat → Meow
Cow → Moo

---

### 💻 Example

```python
class Animal:

    def sound(self):
        print("Animal sound")

class Dog(Animal):

    def sound(self):
        print("Bark")

class Cat(Animal):

    def sound(self):
        print("Meow")
```

---

# 1️⃣2️⃣ Method Overriding

### 🧠 Easy Meaning

Child class **changes parent method behavior**.

---

### 💻 Example

```python
class Animal:

    def sound(self):
        print("Animal sound")

class Dog(Animal):

    def sound(self):
        print("Dog barks")
```

Dog overrides parent's method.

---

# 1️⃣3️⃣ Operator Overloading

### 🧠 Easy Meaning

Same operator behaves differently for different data.

---

### 💻 Example

```python
print(2 + 3)        # 5
print("Hi " + "AI") # Hi AI
```

Same `+` operator.

Different behavior.

---

# 1️⃣4️⃣ super()

### 🧠 Easy Meaning

Used to call **parent class methods**.

---

### 💻 Example

```python
class Animal:

    def __init__(self):
        print("Animal created")

class Dog(Animal):

    def __init__(self):
        super().__init__()
        print("Dog created")
```

---

# 1️⃣5️⃣ Method Resolution Order (MRO)

### 🧠 Easy Meaning

When multiple inheritance happens,
Python decides **which parent method to use first**.

---

### 💻 Example

```python
class A:
    pass

class B(A):
    pass

class C(A):
    pass

class D(B, C):
    pass

print(D.mro())
```

Shows method lookup order.

---

# 🏛 The 4 Pillars of OOP

These are the **most important concepts**.

| Pillar        | Meaning                        |
| ------------- | ------------------------------ |
| Encapsulation | Protect data                   |
| Abstraction   | Hide complexity                |
| Inheritance   | Reuse code                     |
| Polymorphism  | Same method different behavior |

---

# 🧠 Simple Memory Trick

Think of **building a company software system**:

Class → design of employee
Object → actual employee
Inheritance → manager inherits employee features
Encapsulation → salary protected
Abstraction → complex system hidden
Polymorphism → employees behave differently

---
