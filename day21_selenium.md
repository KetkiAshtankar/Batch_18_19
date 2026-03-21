# 🧠 SELENIUM NOTES – LOCATORS, NAVIGATION, WINDOWS, FRAMES

---

# 🔹 1️⃣ LOCATORS (MOST IMPORTANT)

## 👉 What is a Locator?

> Locator = Address of element on webpage

Without locator → ❌ No automation

---

## ✅ Types of Locators

### 🔸 ID (Best)

```python
driver.find_element(By.ID, "user-name")
```

✔ Fast
✔ Mostly unique
✔ First preference

---

### 🔸 Name

```python
driver.find_element(By.NAME, "password")
```

✔ Simple
❗ May not be unique

---

### 🔸 Class Name

```python
driver.find_element(By.CLASS_NAME, "login-button")
```

❗ Can be duplicate → less reliable

---

### 🔸 CSS Selector (Important)

```python
driver.find_element(By.CSS_SELECTOR, "#user-name")   # ID
driver.find_element(By.CSS_SELECTOR, ".login-button") # Class
driver.find_element(By.CSS_SELECTOR, "input[name='password']")
```

✔ Flexible
✔ Industry use

---

### 🔸 XPath (Intro)

```python
driver.find_element(By.XPATH, "//input[@id='user-name']")
```

✔ Powerful
❗ Slower than CSS

---

# 🎯 Key Point:

> “If locator is wrong → entire test fails”

---

# 🔹 2️⃣ NAVIGATION & INTERACTION

---

## ✅ Basic Actions

### Click

```python
element.click()
```

### Send Keys

```python
element.send_keys("text")
```

### Get Text

```python
element.text
```

---

## ✅ Navigation Commands

```python
driver.back()
driver.forward()
driver.refresh()
```

---

# 🎯 Key Point:

> Navigation works only if there is page history

---

# 🔹 3️⃣ FORM HANDLING

---

### Fill Input

```python
.send_keys("Ketki")
```

### Clear Field

```python
.clear()
```

### Submit Form

```python
.click()
```

---

# 🎯 Key Point:

> Forms = combination of locators + actions

---

# 🔹 4️⃣ WINDOWS vs TABS

---

## 🧠 Concept

| Tabs         | Windows          |
| ------------ | ---------------- |
| Same browser | Separate browser |
| Common       | Used in popups   |

---

## ✅ Important Methods

### Current Window

```python
driver.current_window_handle
```

---

### All Windows

```python
driver.window_handles
```

👉 Returns list:

```python
['id1', 'id2', 'id3']
```

---

## ✅ Switching

```python
driver.switch_to.window(window_id)
```

---

## 🔥 Example Logic

```python
parent = driver.current_window_handle

for win in driver.window_handles:
    if win != parent:
        driver.switch_to.window(win)
```

---

# ⚠️ Mistakes

❌ Not switching before action
❌ Losing parent window
❌ Closing wrong window

---

# 🔹 5️⃣ MULTIPLE TABS HANDLING

---

## ❌ Beginner Approach (Not Reliable)

```python
tabs[1]
```

👉 Problem:

* Order may change

---

## ✅ Best Practice (Industry Level)

```python
for tab in driver.window_handles:
    driver.switch_to.window(tab)
    
    if "Facebook" in driver.title:
        print("Facebook tab")
```

---

# 🎯 Key Point:

> “Never trust index → use title or URL”

---

## 🧪 Debug Trick

```python
for i, tab in enumerate(driver.window_handles):
    driver.switch_to.window(tab)
    print(i, driver.title)
```

---

# 🔹 6️⃣ CONTROLLED SWITCHING (BEGINNER FRIENDLY)

---

```python
tabs = driver.window_handles

driver.switch_to.window(tabs[0])
driver.switch_to.window(tabs[1])
```

✔ Easy
❗ Not scalable

---

# 🔹 7️⃣ FRAMES (VERY IMPORTANT)

---

## 🧠 Concept

> Frame = webpage inside webpage

---

## ❗ Problem

Selenium cannot access elements inside frame directly

---

## ✅ Solution

### Switch to Frame

```python
driver.switch_to.frame("frame1")
```

---

### Back to Main Page

```python
driver.switch_to.default_content()
```

---

# ⚠️ Common Error

```text
NoSuchElementException
```

👉 Happens when you forget to switch

---

# 🔹 8️⃣ REAL ISSUES YOU FACED (IMPORTANT)

---

## ❌ Wrong Tab Labels

```python
print("Insta", driver.title)
```

👉 Title was actually Facebook

---

## ✅ Fix

✔ Verify using title
✔ Don’t assume index

---

# 🔹 9️⃣ DEBUGGING BEST PRACTICES

---

### Print Title

```python
print(driver.title)
```

---

### Print URL

```python
print(driver.current_url)
```

---

### Print All Tabs

```python
for i, tab in enumerate(driver.window_handles):
    driver.switch_to.window(tab)
    print(i, driver.title)
```

---

# 🔹 🔟 BEST PRACTICES

---

✅ Always store parent window
✅ Always switch before action
✅ Prefer title/URL over index
✅ Avoid hardcoding
✅ Use waits instead of sleep (advanced)

---

# fixed code:
```python
import time
from selenium import webdriver

driver = webdriver.Chrome()
driver.maximize_window()

driver.get("https://www.google.org/")
time.sleep(1)

driver.execute_script("window.open('https://www.facebook.com');")
driver.execute_script("window.open('https://www.instagram.com');")
driver.execute_script("window.open('https://www.saucedemo.com');")

time.sleep(2)

# Loop through tabs and switch based on title
for tab in driver.window_handles:
    driver.switch_to.window(tab)
    title = driver.title

    if "Google" in title:
        print("Google ", title)

    elif "Facebook" in title:
        print("Facebook ", title)

    elif "Instagram" in title:
        print("Instagram ", title)

    elif "Swag Labs" in title:
        print("Saucedemo ", title)

time.sleep(2)
driver.quit()
```
