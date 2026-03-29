---

# 🧪 XPATH COMPLETE NOTES 

---

# 📌 1. What is XPath?

👉 XPath = **Language to locate elements in DOM**

### 🧠 Analogy:

* DOM = City 🏙️
* Elements = Buildings 🏢
* XPath = Directions 🗺️

---

# 🌳 2. DOM Structure

HTML follows a **tree structure**

```
html
 └── body
      └── div
           └── input
```

### 🧠 Analogy:

Family Tree 👨‍👩‍👧

* Parent
* Child
* Ancestor
* Descendant

---

# 🧭 3. Types of XPath

## ❌ Absolute XPath

```
/html/body/div/input
```

* Starts from root
* Breaks easily

---

## ✅ Relative XPath

```
//input[@id='user-name']
```

* Starts from anywhere
* Flexible & stable

---

# 🔍 4. Basic XPath Syntax

## By tag

```
//input
```

## By attribute

```
//input[@id='password']
```

## Multiple attributes

```
//input[@id='user-name' and @type='text']
```

## OR condition

```
//input[@id='user-name' or @id='password']
```

---

# 🧬 5. XPath Relationships (Very Important)

## Parent

```
//input[@id='user-name']/parent::div
```

## Child

```
//form/input
```

## Ancestor

```
//input[@id='password']/ancestor::form
```

## Descendant

```
//form/descendant::input
```

---

# 🔄 6. XPath Axes

---

## 🔹 preceding

```
//input[@id='password']/preceding::input
```

👉 Selects **ALL input elements before password in DOM**

### 🧠 Analogy:

Book 📖 → all pages before current page

⚠️ Not just siblings — entire DOM

---

## 🔹 preceding-sibling

```
//input[@id='password']/preceding-sibling::input
```

👉 Selects only **elements at same level before**

### 🧠 Analogy:

Classmates in same class

---

## 🔹 following

```
//input[@id='user-name']/following::input
```

👉 Everything after element

---

## 🔹 following-sibling

```
//label/following-sibling::input
```

👉 Next element at same level

---

# ⚔️ preceding vs preceding-sibling

| Feature     | preceding | preceding-sibling |
| ----------- | --------- | ----------------- |
| Scope       | Whole DOM | Same parent       |
| Performance | Slow      | Faster            |
| Usage       | Rare      | Common            |

---

# 🎯 7. Text-Based XPath

## Exact text

```
//button[text()='Login']
```

## Contains text

```
//button[contains(text(),'Log')]
```

---

# 🧪 8. Contains & Starts-With

## Contains

```
//input[contains(@id,'user')]
```

## Starts-with

```
//input[starts-with(@id,'user')]
```

---

# 🔢 9. Indexing

```
(//input)[1]
(//input)[2]
```

⚠️ Index starts from **1**

---

# 🧠 10. Advanced XPath

## Chained XPath

```
//div[@class='login-box']//input[@id='user-name']
```

---

## normalize-space

```
//button[normalize-space()='Login']
```

---

## NOT condition

```
//input[not(@type='hidden')]
```

---

# 🧪 11. Real Examples (SauceDemo)

## Login Page

```
Username → //input[@id='user-name']
Password → //input[@id='password']
Login → //input[@id='login-button']
```

---

## Using Axes

### Get username using password

```
(//input[@id='password']/preceding::input)[1]
```

---

### Better approach

```
//input[@id='password']/preceding-sibling::input
```

---

### Precise targeting

```
//input[@id='password']/preceding::input[@id='user-name']
```

---

# 🧠 12. Real SDET Scenarios

## Label → Input

```
//label[text()='Password']/following::input[1]
```

---

## Reverse mapping

```
//input[@id='password']/preceding::label[1]
```

---

## Product → Button mapping

```
//div[text()='Sauce Labs Backpack']/ancestor::div[@class='inventory_item']//button
```

---

# ⚠️ 13. Common Mistakes

❌ Using absolute XPath
❌ Overusing index
❌ Ignoring relationships
❌ Using preceding instead of sibling

---

# ⚡ 14. Performance Tips

* XPath is slower than ID/CSS
* Axes like `preceding::` are **expensive**

### Prefer:

✔ ID
✔ Name
✔ CSS
✔ preceding-sibling over preceding

---

# 🏆 15. Golden Rules

✔ Always prefer relative XPath
✔ Use unique attributes
✔ Use contains for dynamic elements
✔ Use relationships for complex DOM
✔ Avoid long XPath

---

# 🧠 Final Mental Model

Think like a **detective 🕵️**

* Attribute = Identity proof
* Text = Name
* Relationship = Family
* Axes = Movement direction

---
